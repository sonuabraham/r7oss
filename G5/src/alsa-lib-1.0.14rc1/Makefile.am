SUBDIRS=doc include src modules
if BUILD_PCM_PLUGIN_SHM
SUBDIRS += aserver
endif
if BUILD_MIXER
if BUILD_ALISP
SUBDIRS += alsalisp
endif
endif
SUBDIRS += test utils
EXTRA_DIST=ChangeLog INSTALL TODO NOTES configure hgcompile libtool depcomp version MEMORY-LEAK
AUTOMAKE_OPTIONS=foreign

INCLUDES=-I$(top_srcdir)/include

rpm: dist
	$(MAKE) -C utils rpm

dist-hook:
	-chmod -R a+r $(distdir)
	@if ! test -z "$(AMTAR)"; then \
		$(AMTAR) --create --verbose --file=- $(distdir) | bzip2 -c -9 > $(distdir).tar.bz2 ; \
	else \
		$(TAR) --create --verbose --file=- $(distdir) | bzip2 -c -9 > $(distdir).tar.bz2 ; \
	fi

doc-dummy:

doc: doc-dummy
	$(MAKE) -C include all
	$(MAKE) -C doc doc

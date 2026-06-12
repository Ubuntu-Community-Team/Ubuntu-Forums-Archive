---
title: "Install error : install: missing destination file operand after `/usr/share/pixmaps/F"
date: 2015-02-02
forum: Programming Talk
---

### Post by harkirat_singh on 2015-02-02
while i make install FBReader it gives error.
  [HTML]install: missing destination file operand after `/usr/share/pixmaps/FBReader'
[/HTML]  basically it is missing DESTDIR i.e. destination directory coz echo DESTDIR in makefile gives blank.

  So,i searched on the Internet somebody says 
  ```
Please set destination directory to make to install files: `make install  
DESTDIR=%{buildroot}` or `make INSTALL_ROOT=%{buildroot} install`. You  
should check for the correct variable at makefile or documentation.

```  when i declared DESTDIR to %{buildroot} it gives this error.
  ```
 missing destination file operand after `%{buildroot}/usr/share/pixmaps/FBReader'

```  what is the **buildroot** how to configure that.
  it is missing the destination directory.
  For convenience i am attaching the make file.

[HTML]ROOTDIR = $(CURDIR)/..

MAKEFILESDIR = $(ROOTDIR)/makefiles

include $(MAKEFILESDIR)/config.mk

TARGET = FBReader
target = fbreader

ALL_SUBDIRS = src src/database src/database/sqldb src/database/sqldb/implsqlite src/database/booksdb src/database/booksdb/runnables src/migration src/options src/library src/bookmodel src/formats src/formats/fb2 src/formats/docbook src/formats/css src/formats/html src/formats/pdb src/formats/txt src/formats/tcr src/formats/chm src/formats/xhtml src/formats/oeb src/formats/rtf src/formats/openreader src/formats/pdf src/formats/dummy src/formats/util src/external src/fbreader src/encodingOption src/network src/network/authentication src/network/authentication/basic src/network/atom src/network/opds src/network/authentication/litres src/blockTree src/libraryActions src/libraryTree src/networkActions src/networkTree src/optionsDialog src/optionsDialog/bookInfo src/optionsDialog/library src/optionsDialog/network src/optionsDialog/system src/optionsDialog/reading src/optionsDialog/lookAndFeel
ALL_ARCHSUBDIRS = desktop pdaxrom opie zaurus maemo openzaurus pma400 win32

SUBDIRS = src/database src/database/sqldb src/database/sqldb/implsqlite src/database/booksdb src/database/booksdb/runnables src/migration src/options src/library src/bookmodel \
    src/formats src/formats/fb2 src/formats/css src/formats/html src/formats/pdb src/formats/txt src/formats/tcr src/formats/chm src/formats/xhtml src/formats/oeb src/formats/rtf src/formats/openreader src/formats/util \
    src/external src/fbreader src/encodingOption src/network src/network/authentication src/network/authentication/basic src/network/atom src/network/opds src/network/authentication/litres \
    src/blockTree src/libraryActions src/libraryTree src/networkActions src/networkTree src/optionsDialog src/optionsDialog/bookInfo src/optionsDialog/library src/optionsDialog/network src/optionsDialog/system src/optionsDialog/reading src/optionsDialog/lookAndFeel

all: .resources
    @for subdir in $(SUBDIRS); do \
        if ! $(MAKE) -C $$subdir -f $(MAKEFILESDIR)/subdir.mk; then \
            exit 1; \
        fi; \
    done;

    @echo -n 'Linking $(TARGET) ...'
    @$(LD) $(LDFLAGS) -o $(TARGET) `find src -name *.o` -L$(ROOTDIR)/zlibrary/text $(TEXT_LIBS) $(CORE_LIBS) -lsqlite3
    @echo ' OK'

FBSHAREDIR = $(DESTDIR)$(SHAREDIR)/FBReader
VARIANT = $(TARGET_ARCH)
ifneq "$(RESOLUTION)" "" 
  VARIANT = $(TARGET_ARCH)_$(RESOLUTION)
endif

APPIMAGEDIR_REAL = $(subst %application_name%,$(target),$(subst %APPLICATION_NAME%,$(TARGET),$(APPIMAGEDIR)))

do_install:
    @install -d $(DESTDIR)$(BINDIR)

    @install $(TARGET) $(DESTDIR)$(BINDIR)/FBReader
    @install -d $(FBSHAREDIR)
    @install -d $(FBSHAREDIR)/help
    @./scripts/install_help.sh $(VARIANT) $(FBSHAREDIR)/help

    @install -d $(FBSHAREDIR)/network
    @install -m 0644 $(wildcard data/network/*.xml) $(FBSHAREDIR)/network
    @install -d $(FBSHAREDIR)/network/certificates
    @install -m 0644 $(wildcard data/network/certificates/*.crt) $(FBSHAREDIR)/network/certificates
    @install -d $(FBSHAREDIR)/formats/html
    @install -m 0644 data/formats/html/html.ent $(FBSHAREDIR)/formats/html
    @install -d $(FBSHAREDIR)/formats/xhtml
    @install -m 0644 $(wildcard data/formats/xhtml/*.ent) $(FBSHAREDIR)/formats/xhtml
    @install -d $(FBSHAREDIR)/formats/fb2
    @sed "s/VERSION/$(VERSION)/" data/formats/fb2/FBReaderVersion.ent > $(FBSHAREDIR)/formats/fb2/FBReaderVersion.ent
    @install -m 0644 data/formats/fb2/fb2genres.xml $(FBSHAREDIR)/formats/fb2
    @install -d $(FBSHAREDIR)/default
    @./scripts/install_toolbar_and_menu.sh $(VARIANT) $(UI_TYPE) $(FBSHAREDIR)/default
    @./scripts/install_config.sh $(VARIANT) $(UI_TYPE) $(FBSHAREDIR)/default
    @install -m 0644 data/default/external.$(TARGET_ARCH).xml $(FBSHAREDIR)/default/external.xml
    @if [ -f data/default/messages.$(TARGET_ARCH).xml ]; then \
        install -m 0644 data/default/messages.$(TARGET_ARCH).xml $(FBSHAREDIR)/default/messages.xml; \
    fi
    @install -d $(FBSHAREDIR)/resources
    @install -m 0644 $(wildcard data/resources/*.xml) $(FBSHAREDIR)/resources
    @install -d $(DESTDIR)$(APPIMAGEDIR_REAL)
    @install -m 0644 $(wildcard data/icons/toolbar/$(VARIANT)/*.*) $(DESTDIR)$(APPIMAGEDIR_REAL)
    @echo ' Munish2'
    @install -m 0644 $(wildcard data/icons/filetree/$(VARIANT)/*.*) $(DESTDIR)$(APPIMAGEDIR_REAL)
    @install -m 0644 $(wildcard data/icons/booktree/new/*.*) $(DESTDIR)$(APPIMAGEDIR_REAL)
    @make -C $(TARGET_ARCH) RESOLUTION=$(RESOLUTION) install

clean:
    @for subdir in $(ALL_SUBDIRS); do \
        $(MAKE) -C $$subdir -f $(MAKEFILESDIR)/subdir.mk clean; \
    done;
    @for subdir in $(ALL_ARCHSUBDIRS); do \
        cd $$subdir; make clean; cd ..; \
    done;[/HTML]

---


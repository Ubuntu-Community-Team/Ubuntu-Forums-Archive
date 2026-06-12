---
title: "gtk error FB reader: cannot access `gtk': No such file or directory"
date: 2015-02-02
forum: Programming Talk
---

### Post by harkirat_singh on 2015-02-02
make install of FB reader give this error.

> chmod: cannot access `gtk': No such file or directory
make[1]: *** [do_install] Error 1


gtk version installed:

 > $ pkg-config --modversion gtk+-3.0
3.4.2

here is the make file makefile.mk:


> 
ROOTDIR = $(CURDIR)/..

MAKEFILESDIR = $(ROOTDIR)/makefiles

include $(MAKEFILESDIR)/config.mk
include $(MAKEFILESDIR)/target.mk
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
    chmod +x . /home/harkirat/Downloads/FBReader-master/fbreader/scripts/install_help.sh $(VARIANT) $(FBSHAREDIR)/help
    #@./scripts/install_help.sh $(VARIANT) $(FBSHAREDIR)/help
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
    chmod +x . /home/harkirat/Downloads/FBReader-master/fbreader/scripts/install_toolbar_and_menu.sh $(VARIANT) $(UI_TYPE) $(FBSHAREDIR)/help
    #@./scripts/install_toolbar_and_menu.sh $(VARIANT) $(UI_TYPE) $(FBSHAREDIR)/default
    chmod +x . /home/harkirat/Downloads/FBReader-master/fbreader/scripts/install_config.sh  $(VARIANT) $(UI_TYPE) $(FBSHAREDIR)/help
    #@/scripts/install_config.sh $(VARIANT) $(UI_TYPE) $(FBSHAREDIR)/default
    chmod +x . /home/harkirat/Downloads/FBReader-master/fbreader/scripts/install_toolbar_and_menu.sh $(VARIANT) $(UI_TYPE) $(FBSHAREDIR)/help
    #@./scripts/install_toolbar_and_menu.sh $(VARIANT) $(UI_TYPE) $(FBSHAREDIR)/default
    chmod +x . /home/harkirat/Downloads/FBReader-master/fbreader/scripts/install_config.sh  $(VARIANT) $(UI_TYPE) $(FBSHAREDIR)/help
    #@./scripts/install_config.sh $(VARIANT) $(UI_TYPE) $(FBSHAREDIR)/default
    @install -m 0644 data/default/external.$(TARGET_ARCH).xml $(FBSHAREDIR)/default/external.xml
    @if [ -f data/default/messages.$(TARGET_ARCH).xml ]; then \
        install -m 0644 data/default/messages.$(TARGET_ARCH).xml $(FBSHAREDIR)/default/messages.xml; \
    fi
    @install -d $(FBSHAREDIR)/resources
    @install -m 0644 $(wildcard data/resources/*.xml) $(FBSHAREDIR)/resources
    @install -d $(DESTDIR)$(APPIMAGEDIR_REAL)
    @install -m 0644 $(wildcard data/icons/toolbar/$(VARIANT)/*.*) $(DESTDIR)$(APPIMAGEDIR_REAL)
    @install -m 0644 $(wildcard data/icons/filetree/$(VARIANT)/*.*) $(DESTDIR)$(APPIMAGEDIR_REAL)
    @install -m 0644 $(wildcard data/icons/booktree/new/*.*) $(DESTDIR)$(APPIMAGEDIR_REAL)
    @make -C $(TARGET_ARCH) RESOLUTION=$(RESOLUTION) install

clean:
    @for subdir in $(ALL_SUBDIRS); do \
        $(MAKE) -C $$subdir -f $(MAKEFILESDIR)/subdir.mk clean; \
    done;
    @for subdir in $(ALL_ARCHSUBDIRS); do \
        cd $$subdir; make clean; cd ..; \
    done;
    @$(RM) $(TARGET) err

---

### Post by schragge on 2015-02-02
I'm not quite sure what are you trying to do. To compile the latest version of *fbreader* (currently 0.99.4 beta) from source? But it uses Qt4 and doesn't support GTK anymore. To compile from source the version in Ubuntu repository (0.12.10)? But why? It can be installed with *apt-get*.

As to the makefile you listed: it's only the first level makefile that invokes other makefiles with
```

@for subdir in $(SUBDIRS); do \
if ! $(MAKE) -C $$subdir -f $(MAKEFILESDIR)/subdir.mk; then \
exit 1; \
fi; \
done;

```
Besides, it includes other snippets with
```

include $(MAKEFILESDIR)/config.mk
include $(MAKEFILESDIR)/target.mk

```
You should first find out what makefile gets the directory *gtk* referenced from.

---

### Post by harkirat_singh on 2015-02-02
done.
thank you

---


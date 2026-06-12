---
title: "Makefile for Thunderbird extension"
date: 2010-07-03
forum: Packaging and Compiling Programs
---

### Post by rubenverweij on 2010-07-03
Hi all!
I'm trying to setup a PPA for an extension for Thunderbird. I thought I needed a Makefile to copy the files to TB's extension folder. I came up with the following Makefile:
```
APP = libnotify-mozilla
FILES = "content translations defaults locale python chrome.manifest install.rdf LICENSE README"

all: $(APP)

$(APP): ;@echo "Done. Run 'make install' to install the extension"

install: $(APP)
	cd ~/.thunderbird/*.default/extensions
	mkdir libnotifypopups@patrik.dufresne
	cd $(FILES) libnotifypopups@patrik.dufresne
	done
```
This, unfortunately, doesn't work as the cd command doesn't switch to the profile directory and if it would have switched, it would have been unable to find the $(FILES) for they are in a different directory.
So now I'm stuck. How can I make a PPA for my Thunderbird extension?
I hope anyone can help. Thanks in advance!
Ruben

---

### Post by SevenMachines on 2010-07-05
do you have a link to the ppa? using user relative paths(~) in a ppa build will not work. there will be a standard directory for thunderbird extensions in the system dirs, something like /usr/lib/thunderbird/extensions or something like that i imagine, which will be the one you want to install to

[EDIT] just to add, 'packages dont install to user directories' was the point i was struggling to make in the above post :)

---


---
title: "HOWTO: Fix ugly icons in Human theme on Dapper/Edgy"
date: 2007-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by dbbolton on 2007-06-18
the Human icon theme is somewhat incomplete on Dapper and Edgy. you may find that certain icons (like apply, cancel, etc.) are particularly unbearable. this tutorial explains how to use the much nicer Tango equivalents.

first, you can simply use a shell script that i wrote (see attached files).

1. download the archive, and extract the contents (1 file) to your home folder.
2. make the script executable: ```
chmod +x iconimprov
```3. run the script: ```
 ./iconimprov
```since i probably made that script wrong, here is a list of commands that you can run (as root) in order to achieve the same effect: ```
cp '/usr/share/icons/Tango/scalable/actions/dialog-apply.svg' '/usr/share/icons/Human/scalable/actions/dialog-apply.svg'
cp '/usr/share/icons/Tango/scalable/actions/dialog-apply.svg' '/usr/share/icons/Human/scalable/actions/gtk-apply.svg'
cp '/usr/share/icons/Tango/scalable/actions/dialog-apply.svg' '/usr/share/icons/Human/scalable/actions/gtk-ok.svg'
cp '/usr/share/icons/Tango/scalable/actions/dialog-apply.svg' '/usr/share/icons/Human/scalable/actions/stock-apply.svg'
cp '/usr/share/icons/Tango/scalable/actions/dialog-apply.svg' '/usr/share/icons/Human/scalable/actions/gtk-yes.svg'
cp '/usr/share/icons/Tango/scalable/actions/dialog-cancel.svg' '/usr/share/icons/Human/scalable/actions/dialog-cancel.svg' 
cp '/usr/share/icons/Tango/scalable/actions/dialog-cancel.svg' '/usr/share/icons/Human/scalable/actions/gtk-cancel.svg'
cp '/usr/share/icons/Tango/scalable/actions/dialog-cancel.svg' '/usr/share/icons/Human/scalable/actions/stock-cancel.svg' 
cp '/usr/share/icons/Human/scalable/actions/dialog-cancel.svg' '/usr/share/icons/Tango/scalable/actions/dialog-close.svg' 
cp '/usr/share/icons/Human/scalable/actions/gtk-cancel.svg' '/usr/share/icons/Tango/scalable/actions/dialog-close.svg' 
cp '/usr/share/icons/Human/scalable/actions/stock-cancel.svg' '/usr/share/icons/Tango/scalable/actions/dialog-close.svg' 
cp '/usr/share/icons/Human/scalable/actions/stock-quit.svg' '/usr/share/icons/Tango/scalable/actions/dialog-close.svg' 
cd /usr/share/icons
gtk-update-icon-cache --force Human
```

---

### Post by dbbolton on 2007-06-19
before and after:

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/oldicons.png[/IMG]
=========
[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/iconimprov.png[/IMG]

---


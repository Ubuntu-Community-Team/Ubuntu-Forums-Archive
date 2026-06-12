---
title: "gedit won't save setting of 'autocheck spelling checked'"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by adagdag on 2008-11-22
Hi,

I've been using gedit, and when I check 'Autocheck Spelling', then close/reopen, it reverts to being unchecked every time.

I've looked in /home/adagdag/.gconfg/apps/gedit-2 and only saw the preferences folder and empty .gconf.xml files. Also I searched to find this here: [http://ubuntuforums.org/showthread.php?t=704829&highlight=auto+spellcheck](http://ubuntuforums.org/showthread.php?t=704829&highlight=auto+spellcheck) and saw that this was reported as a bug.

Does anyone know if this has been fixed/how to fix this? Or am I missing something?

---

### Post by jimmy the saint on 2008-11-22
the bug report and fix is here

[http://bugzilla.gnome.org/show_bug.cgi?id=305055](http://bugzilla.gnome.org/show_bug.cgi?id=305055)

---

### Post by adagdag on 2008-11-22
Thank you, I did what it said to do as a 'temp fix':
```
gconftool-2 --type bool --set /apps/gedit-2/plugins/spellcheck/value true
```
And it makes an xml file in /plugins/spellcheck which says to set autospell check to on. But I think it'll only work with the older gedit .rpm's he posted on there. For me, this fix doesn't work in gedit 2.24.1

---


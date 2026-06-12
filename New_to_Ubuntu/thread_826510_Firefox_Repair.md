---
title: "Firefox Repair"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-06-11
I have a problem with Firefox. It keeps pauseing, and sometimes I have to force quit. It goes to a wierd gray colour?? Isn't there some way I can go into the terminal and give it some sort of repair command?

---

### Post by kaibob on 2008-06-12
I don't know of any repair mode. You can enter safe mode to trouble shoot the problem:

[http://kb.mozillazine.org/Safe_mode](http://kb.mozillazine.org/Safe_mode)

Extensions can often cause a problem, so you may want to disable these temporarily to see if this helps.

In addition, Firefox can appear unresponsive when fetching updates to the site-forgery and malware lists contained in the file, urlclassifier3.sqlite. To see if this is the case, you can temporarily disable this feature by unchecking the following Firefox security preferences:

* Tell me if the site I'm visiting is a suspected attack site

* Tell me if the site I'm visiting is a suspected forgery

---

### Post by MmmmJoel on 2008-06-12
> **Andrew79 said:**
> I have a problem with Firefox. It keeps pauseing, and sometimes I have to force quit. It goes to a wierd gray colour?? Isn't there some way I can go into the terminal and give it some sort of repair command?

The easiest but most invasive thing to do would be to delete your Firefox profile and give Firefox a fresh start. Backup your bookmarks.
```
rm -r ~/.mozilla/firefox
```

---

### Post by kaibob on 2008-06-12
> **MmmmJoel said:**
> The easiest but most invasive thing to do would be to delete your Firefox profile and give Firefox a fresh start. Backup your bookmarks....

Good point--I forgot about profiles. You can do as MmmmJoel suggests, or you can simply create a new profile for troubleshooting purposes by entering "firefox -ProfileManager" in a terminal window. 

[http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

---

### Post by Paqman on 2008-06-12
The grey colour is just the system's way of saying that the window is idle. Normally if you give them a few seconds they come back.

---

### Post by aeshanw on 2008-07-16
I've got a problem with FF3.after a routine upgrade.my FF browser lost all its icons!No back/fwd buttons visible.tried reinstalling FF , but no cigar :(
Thanks

---

### Post by alienexplorers on 2008-07-16
rebuild your profile folder.  In terminal do:
> firefox -profilemanager
follow the prompts and boot from profilemanager.
Next time you boot using an icon or menu into firefox it should use the new profile.

---


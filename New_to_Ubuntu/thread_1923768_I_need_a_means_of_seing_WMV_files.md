---
title: "I need a means of seing WMV files"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by sahc on 2012-02-11
Is there a program available to allow me to look at .WMV files in Ubuntu. If so how do I get it.

sahc

---

### Post by ikt on 2012-02-11
VLC

Open the ubuntu software centre (orange bag) and search for VLC, install, then right click on the wmv files and open with VLC.

However I think even opening the wmv files with the default movie viewer should ask you to download some codecs if it can't play the file, just install those and it should work.

---

### Post by sahc on 2012-02-11
Thank you. Most helpful.

---

### Post by drmrgd on 2012-02-11
You might consider installing ubuntu-restricted-extras available in the Software Center.  These will have some of the codecs and things you need to view the WMV files in VLC Player.  Here's a link to the [Ubuntu Documentation]("https://help.ubuntu.com/community/RestrictedFormats") on that for a little more info.

---

### Post by Cheesemill on 2012-02-11
> **drmrgd said:**
> These will have some of the codecs and things you need to view the WMV files in VLC Player.

Not really.

It will install the codecs that you need to play WMV files with any other video player but not VLC.

VLC uses its own internal codecs for everything it can play.

---

### Post by Scott Baker on 2012-02-11
Here's a command that I found in a previous posting and that I use. It's worked every time without fail. In a terminal, enter the following; [ sudo /usr/share/doc/libdvdread4/install-css.sh ] Remember, it's all lower case. Once installed, it will allow you to view .wmv files on whatever viewer you choose to use. Good luck  :KS

( The above advice will allow you to load certain codecs that some members of the community consider questionable, based on ethics. As such, there may be some responses to the suggestion made here. Use your own best judgment when deciding if you want to load the aforementioned package, or not  )

---


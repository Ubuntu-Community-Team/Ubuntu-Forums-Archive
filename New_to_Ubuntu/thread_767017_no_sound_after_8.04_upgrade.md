---
title: "no sound after 8.04 upgrade"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by catroaring on 2008-04-25
I get this message from volume control "No volume control GStreamer plugins and/or devices found."

I am running from onboard sound on a LeadTek WinFast K7nCR18G PRO

I just upgraded last nite too 8.04, sound worked fine out of the box on 7.10

tx for any help

---

### Post by otrojake on 2008-04-25
It could be a permissions thing.  Open up a terminal and type in "groups" without quotations and see if you're in the audio group.

---

### Post by catroaring on 2008-04-25
this is what i get from groups in terminal

human adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin

---

### Post by otrojake on 2008-04-25
Okay, you're in the appropriate group, so it's not a permissions issue.  I'll admit I'm not too knowledgeable about audio, so someone else with more experience that way is going to have to help out here.

---

### Post by martrn on 2008-04-25
I have no sound either after an upgrade to 8.04.  You are not alone, and I can not get sound working at all 
[http://ubuntuforums.org/showthread.php?t=766220]("http://ubuntuforums.org/showthread.php?t=766220")

[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems")

doesn't help, either.

---

### Post by martrn on 2008-04-25
OK I got my sound back.  Here is what I did.  I looked up my sound driver on the following page ( I have an alsa driver).  [http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main") and then found the correct driver for my sound card, and noted this...

Then I visited [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") and followed the steps through.  This guide works although is written by somebody who knows how to compile code so isn't in lay-mans terms but it works.

If you ever find yourself at stage -- Using alsa-source * then note that .... ".. Open up a shell: (note: module-assistant is optional, it will compile the package for you) ..."....

means open up a terminal and type :
> module-assistant
This is not really optional as it will compile, build and install the module for you.  If you do not want to compile, build and install just run this and the (optional part) will complete the compile build and install process for you.

This guide works.
Cool I have sound.. (again)....

---


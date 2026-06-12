---
title: "found driver for Canon printer but cannot install"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by ddz7 on 2008-05-23
Hi, 

I'm hoping someone will take source files and build a working .deb package for me.

I have a Canon ImageCLASS MF6530 printer (copier, scanner). Linux printers page doesn't list this. Canon USA ph tech support was worthless. But Canon Asia support pages offer a CUPS driver download for the MF6550 (and the ReadMe says it will work with the 6530 and many other Canon printers). It's located here:

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100093101.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100093101.html)

(link at bottom of page below the legalize)

The Guide in the documents folder tells one how to instal the two required .deb packages -- but there are no .deb packages. 

In the Sources folder I did find subfolders labeled 'debian' with control folders in them. So I changed the name to DEBIAN and tried running dpkg -b to build one of them.

I am utterly a newbie. I had fun playing around, using apropos and info, editing the control file with no understanding just to see if I could get past the syntax error messages. But of course I could not create a package that would actually install.

Could someone please create this package, and if possible actually try following the installation instructions in the supplied Guide to see if other surprises lurk there?

Thanks so much. If this works, it could be a great resource to many users (truly, the readme lists a lot of canon printers this is supposed to work with)

(ps. my first post -- I thought I'd sent this earlier, but it didn't show up. Hope it works this time without duplication)

---

### Post by HotShotDJ on 2008-05-23
Oh dear.  This is NOT really a newbie friendly procedure.  Let me look for other options first.

EDIT:  Ok.  I search for precompiled versions for these things, and was unsuccessful.  You'll need to compile by hand, which is not my area of expertise.  This is a zebra and I'm a horses kind of guy. :)  You might have better luck getting help over in the [General Support]("http://ubuntuforums.org/forumdisplay.php?f=331") forum rather than here in Absolute Beginners.  Be sure to give your thread there a suitable title like: Need Help Compiling Custom Package

---

### Post by ddz7 on 2008-05-24
Yes, after messing around a bit it became clear it's not a newbie procedure -- that's why I'm hoping someone will leap forward to do it for me :)

So if this belongs in General Support Forum, what's the protocol. As new forum users we are cautioned against posts to multiple forums with the same problem -- does some administrator transfer the thread to another forum, or do I consider this thread done and start a new one there?

---

### Post by philinux on 2008-05-24
You'll need a package called build-essential from synaptic.

Extract all the folders and get to one with the driver and the readme.txt which has the install instruction. There are only three commands to execute. In terminal you have to be in the drivers directory.

Quick install:
==============
  To build and install modules, run make at the top-level
 directory of this package source trees as follows:

 $ make gen
 $ su
 # make install

---

### Post by spec-chum on 2008-05-24
Just note that su won't work in Ubuntu as the root account is locked.  You need to use sudo for the last line, i.e.
```

sudo make install

```
so the full thing for Ubuntu would be

Quick install:
==============
To build and install modules, run make at the top-level
directory of this package source trees as follows:

$ make gen
$ sudo make install

then enter your password.

---

### Post by ddz7 on 2008-05-31
Thanks for the good guidance, but so far no go.

I'm having to do this at a site with flaky internet connection (and I'm elsewhere now, on a non-linux site for this communication), so it took me a while to succeed in synapticing build-essentials.

When I did, the make command generated an error asking for something else which i also got

then trying to run 
make gen 
gave an error about no rule for target gen -- I tried it one level up and one level down the path from where I believe I was supposed to be.

Is there something simple and stupid I'm missing here, being the complete n00b?
I'll be happy to be told so if it will fix this. Has someone out there actually downloaded this and succeeded in creating this driver, so we'd know it is possible with what Canon supplied?

---

### Post by IanW on 2008-05-31
Try this:-
```

./configure
make
sudo make install

```

---


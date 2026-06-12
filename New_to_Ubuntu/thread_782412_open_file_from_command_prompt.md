---
title: "open file from command prompt"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by fraswesseltet on 2008-05-04
Okay, so I was trying to enable 3D acceleration and I followed the instructions on this site, culminating with the command "sudo nvidia-glx-config enable."  When doing this, it gave me a command to type in if I needed to revert.  Stupidly, I saved this as a document on my PC, so is there a way for me to open that office file from the command prompt, which is the only thing I can boot into?  I really, really hope that's possible because I feel like a complete idiot for not writing it down.

---

### Post by tamoneya on 2008-05-04
if you just saved it as a text file you can do```
nano /my/directory/myfile
```

---

### Post by lazyart on 2008-05-04
Try```
sudo xfix
```if in Hardy Heron, or```
sudo dpkg-reconfigure xserver-xorg
```for older ubuntu.

---

### Post by fraswesseltet on 2008-05-04
nano /my/directory/myfile

I saved it as a file in that openoffice program.  Would that still work?

sudo dpkg-reconfigure xserver-xorg

Is this to reconfigure the display/driver setting that I clearly messed up?

Thanks for your quick help.

---

### Post by tamoneya on 2008-05-04
That will not work for open office files.  It will just look like a big mess.  As i said earlier it would need to be saved in a text format.  There isnt a good command line way to read that file unfortunately.  You are probably best of trying to have the forum debug your problem from scratch. 

Yes that will help you reconfigure what you messed up.  If that doesnt work then you should post the errors and we will work from there.

---

### Post by sam_delta on 2008-05-04
> **fraswesseltet said:**
> nano /my/directory/myfile

I saved it as a file in that openoffice program.  Would that still work?

sudo dpkg-reconfigure xserver-xorg

Is this to reconfigure the display/driver setting that I clearly messed up?

Thanks for your quick help.

yes,as lazyart stated "sudo dpkg-reconfigure xserver-xorg" will work BUT only on older versions of ubuntu (x-7.10) but if your using hardy (8.04) use "sudo xfix"

EDIT, my bad, nano dosnt work for docs

sam

---

### Post by tamoneya on 2008-05-05
> **sam_delta said:**
> yes,as lazyart stated "sudo dpkg-reconfigure xserver-xorg" will work BUT only on older versions of ubuntu (x-7.10) but if your using hardy (8.04) use "sudo xfix"

if you have a document, nano will be able to open it, ull see some strange characters at the beggining of the document, but scroll down and youll eventually see your text

sam

I just tried it on one of my ODT files and it was complete jibberish.

---

### Post by sam_delta on 2008-05-05
you could also copy the .doc file into a usb drive and read it in another computer

cp ~/Desktop/file.doc /media/<name of usb>

where "~/Desktop/file.doc" is the path of your .doc and "/media/<name of usb>" is the path to your usb

sam

---

### Post by sam_delta on 2008-05-05
> **tamoneya said:**
> I just tried it on one of my ODT files and it was complete jibberish.

yeah, i just tryed it and found that out, i duno for some reason i though that was possible. my bad . thx for pointing that out

sam

---

### Post by tamoneya on 2008-05-05
it is true for some files but ODT's do not fall into that catagory.

---

### Post by fraswesseltet on 2008-05-05
I'm really new to this.  In attempting to reconfigure, should I go with 'vesa' (that's what I read somewhere)?  Or should it be nv or nvidia?  Also, after doing so, how do I save changes and exit out of xorg?

---

### Post by lazyart on 2008-05-06
vesa should work with anything.  nv is the open source nvidia driver, nvidia is the proprietary one.  Work your way backwards till one works.

---

### Post by om1 on 2008-05-06
vesa is the safe bet but nv will give you better display if you have a nvidia card... but if you are going to try to reinstall the drivers for your card go ahead and use vesa because it should work with no issues..

---

### Post by sam_delta on 2008-05-06
i personally has never used this command

try in ubuntu 8.04 to fix your screen

```
sudo xfix
```

tell us how it goes
sam

---

### Post by fraswesseltet on 2008-05-16
Thanks everybody, I got a display back.  Afterward, I tried running the command given me to revert (cp /var/backups/xorg/xorg.conf.2008-05-04-20:33:12 /etc/X11/xorg.conf) and it said permission denied.  I only tried running it because the display settings don't seem to be correct (too big and stretched) as compared to before.  Any suggestions?

---

### Post by H.Callahan on 2008-05-16
I suspect that you need to "sudo" that command.  IE,

```
sudo cp /var/backups/xorg/xorg.conf.2008-05-04-20:33:12 /etc/X11/xorg.conf
```

---

### Post by fraswesseltet on 2008-05-19
Yup, that was it.  I probably should know that by now.  Thanks.

---


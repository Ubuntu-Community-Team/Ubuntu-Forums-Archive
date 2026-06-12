---
title: "xsane image scanner problem"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by kahram.yoon on 2008-08-08
My printer HP Deskjet F4180 works perfectly fine and the scanner DOES work because I tried copying something and it scanned it and printed it out.  When I try to use Xsane image scanner, I press scan and it does NOT scan it.  The resulting scanned image is just a blank white square or just a blank image.  I believe this problem might have occurred after the new update a while ago.  I just don't scan things often.  How can I solve this problem?

---

### Post by oldsoundguy on 2008-08-08
You could try the old Windows trick of un installing the unit and re installing.  For sure, you can't make it worse.
Not sure at all if it will work that way, but worth a shot rather than starting to muck around in terminal first .. 
also check your cables and connections.

---

### Post by kahram.yoon on 2008-08-08
> **oldsoundguy said:**
> You could try the old Windows trick of un installing the unit and re installing.  For sure, you can't make it worse.
Not sure at all if it will work that way, but worth a shot rather than starting to muck around in terminal first .. 
also check your cables and connections.

How do i uninstall and install my printer?  And I don't really feel like doing that... will take a lot of time.  My printer is defintely connected because when I press scan, the printer reacts and does something but it seems like it doesn't scan it, it just moves around and goes back and stops.

---

### Post by alienexplorers on 2008-08-08
You may want to try using an older version of the SANE backends.  I don't think your problem has to do with xsane.  Try loading from the SANE site the version 18 scanner backends.  Go to this page to download the version 18 drivers: [http://alioth.debian.org/frs/?group_id=30186]("http://alioth.debian.org/frs/?group_id=30186")

It seems that the version 19 drivers that shipped with hardy 8.04 are not all that great.  Try using one of the lower versions.  You will have to compile these files.

---

### Post by kahram.yoon on 2008-08-08
> **alienexplorers said:**
> You may want to try using an older version of the SANE backends.  I don't think your problem has to do with xsane.  Try loading from the SANE site the version 18 scanner backends.  Go to this page to download the version 18 drivers: [http://alioth.debian.org/frs/?group_id=30186]("http://alioth.debian.org/frs/?group_id=30186")

It seems that the version 19 drivers that shipped with hardy 8.04 are not all that great.  Try using one of the lower versions.  You will have to compile these files.

I tried opening      sane-backends-1.0.17-1.0.18.diff.gz	
    sane-backends-1.0.18.tar.gz
 and an error window popped up for both of these file types
/tmp/sane-backends-1.0.17-1.0.18.diff-1.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences.

i couldnt even open this one - sane-backends-1.0.18.tar.gz.md5

im sorry for being such a complete noob at ubuntu but wut do u mean by compile?

---

### Post by kahram.yoon on 2008-08-08
is there any other scanner program i could use that might work better?

---

### Post by kahram.yoon on 2008-08-08
well just found and installed Scanner Utility and it does not work
it says that its looking for devices than it just freezes up my firefox and music and than the scanner utility is gone and everything comes back to normal

---

### Post by nesnahnhoj on 2012-09-06
I have exactly the same problem with my HP410 photosmart premium.
It appeared after the recent wave of updates to 12.04.
My scanning goes fine with "simple-scan" but I need the quality of Xsane.
I have reinstalled Xsane with synaptic and reinstalled my printer with "hp-setup"
and the result is just the same.
A quick buzz about by the scanner and a blank "View" page. The system does the normal notifications about the job going to the scanner and being completed, but the view page and the saved file are blank.
Ubuntu updates have done something strange to driving HP printers.

---

### Post by kurt18947 on 2012-09-06
I can't promise this will help but you're welcome to try; it has helped me with Xsane problems in the past.  Navigate to this folder ~/.sane (note this is a hidden file)/xsane/   and look for configuration files.  Mine has an .drc suffix but I suspect this varies between machines.  I delete that file but if you want to be safe you could rename it something.old and restart.  A new configuration file will be created using default values.  As I said, I can't promise but it might be worth a try.

---

### Post by pqwoerituytrueiwoq on 2012-09-06
what does this give you
```
scanimage -L
```edit: noticed you said it worked with simple scan so clearly the backend works, if you don't like simple scan yuo may like the one i have linked in my signature
and if you don't want remote access use a firewall ([gufw](apt:gufw))

---


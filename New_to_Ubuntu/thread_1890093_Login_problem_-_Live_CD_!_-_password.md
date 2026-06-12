---
title: "Login problem - Live CD ! - password?"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by aka-John99 on 2011-12-02
How do I reset, override, or discover the password ?

I have previously managed to use the Live CD for i386 32 bit Lucid on Windows XP

Now when I try I get a login screen.

I do not recall ever setting a user name or password on ubuntu, what do I do now?

The next question would have been asking about how to set up the live cd with persistence of settings, it appears it is already somehow doing that.

---

### Post by mikewhatever on 2011-12-02
The live CD/USB default username is 'ubuntu' and the password is just blank. Also, by default, the live CD doesn't show the login screen, but goes straight to the desktop.

Persistence is only possible on live USB, the setup program has a setting for it.

---

### Post by I2k4 on 2011-12-02
> **aka-John99 said:**
> The next question would have been asking about how to set up the live cd with persistence of settings, it appears it is already somehow doing that.

I'm a fan of testing various versions using Persistent Live USB - my experience has been they are a little slower than running of the hard drive but that is an excellent performance test in itself.  The problem is, regardless of which version, they start out running fine but go a little flaky after some weeks of use.

The "Show me how" instructions here are excellent, but don't include the Persistence feature which would be at Step 2:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

The Pendrive installer gives you a slider to set Persistence.  You need about 1.5GB for the Ubuntu 11.x OS, with all the rest of the drive set to Persistence.  That is, on a 4GB USB drive, set about 2.5GB Persistence to run the OS and install a reasonable amount of additional software.  (I've comfortably run the earlier 10.x Ubuntu on a 2GB Live USB split 1GB OS and 1GB Persistence.)

My only other advice would be 
a) try various versions, including Mint 11.x or the 10.x Ubuntu or Lubuntu if you're running an older machine or a netbook (the 11.x is noticeably more demanding and doesn't do much more), 
b) you'll probably have to "mount" your main hard drive by accessing it through the file manager, but should use it for caches and swap files wherever possible in programs that need them, e.g. GIMP, DropBox,
c) don't try to install or delete more than one or two packages at a time on Live USB, it is too slow to reliably deal with it, 
c) there's a good little program called Bleachbit that helps keep a little USB drive clean and your installation small enough to fit on it.

I've found running Live USB fun and interesting.

---

### Post by aka-John99 on 2011-12-03
Thanks for the replies. I have no idea why Ubuntu was presenting a login screen, but it has just booted as normal to the Desktop, so I had no need to test out the login. No doubt I will see the login screen again at some time.

It is likely to be a few weeks before I try some other install method, and I probably will then install Gimp, I already have Gimp on Windows. If I need to ask about persistence or install problems, I will start another thread, so that I try to keep discussions on topic with the thread title.

Currently using the Live CD of 10.04.3 LTS,

---

### Post by aka-John99 on 2011-12-03
I have just deliberatly logged out and 'ubuntu' with a null password did work.

---

### Post by coffeecat on 2011-12-03
> **aka-John99 said:**
> I have no idea why Ubuntu was presenting a login screen, but it has just booted as normal to the Desktop,

> **aka-John99 said:**
> I have just deliberatly logged out and 'ubuntu' with a null password did work.

Sounds like a bit of dust on the CD which has now gone if "ubuntu" and blank now work

If you see the login screen when booting up the live CD or if "ubuntu" and a blank for password do not work, then you have a bad burn CD or the downloaded ISO is corrupted. Or perhaps even something as simple as a bit of dust on the CD.

If you get repeated problems again, it's a good idea to check the integrity of the CD. When you next start the CD tap the space bar when the two small icons of a stick figure and keyboard appear at the bottom of the screen. You will be taken to a text menu where you can do a disk integrity check from the third choice on the menu or thereabouts.

---

### Post by aka-John99 on 2012-01-09
Thanks for the reply coffeecat,

I had not noticed the integrity test so thanks for the tip.

The machine in question is rather low spec and maybe it did have dust on  the CD or the CD Drive is on its last legs (not sure if there are any  free test /diagnostics for cd drives). It does now usually boot from the  live cd, and I am considering installing Ubuntu on the machine.

The ISO images were  MD5 checked, and then the CD burner did verify the  CD s after burning. They were burnt on the drive I am using to load  them; I thought that, and burning at a low speed was likely to help.  Oddlfreey I burnt a couple of copies, they both show no errors on a  laptop when the Ubuntu self test is run from the live cd, but if I run  the self test on the problem desktop they each report *1 file errors found *unfortunately further detail is provided.I will play around with different dives, I have some I can swap  around, and I will try burning more disks on another drive to see if  they prove more reliable.

---

### Post by linuxkathirvel on 2012-01-10
> **aka-John99 said:**
> How do I reset, override, or discover the password ?
 
I have previously managed to use the Live CD for i386 32 bit Lucid on Windows XP
 
Now when I try I get a login screen.
 
I do not recall ever setting a user name or password on ubuntu, what do I do now?
 
The next question would have been asking about how to set up the live cd with persistence of settings, it appears it is already somehow doing that.
 
The Live CD password is empty  if the login screen show,  just hit enter only.  you no need give any password.

---


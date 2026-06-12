---
title: "Uninstall"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by drcoracle on 2008-08-30
Aside from blowing away the drive I put Ubuntu on, how do I get rid of the boot selection list?
I have 
1. Windows XP Professional
2. Ubuntu INstaller
3. Ubuntu

I want to dump it all and start over

---

### Post by cariboo on 2008-08-30
Use you XP Proe cd and go to a recovery console and enter **fixmbr**. This will restore you master boot record to the way it was before you installed ubuntu.

THe easier way would be to just install ubuntu again, this will change the boot menu during the installation.

Why do you need to re-install, that's the windows way to do things. If you explained your problem here, I'm sure we can help you repair your installation.

Jim

---

### Post by drcoracle on 2008-08-30
> **cariboo907 said:**
> Use you XP Proe cd and go to a recovery console and enter **fixmbr**. This will restore you master boot record to the way it was before you installed ubuntu.

THe easier way would be to just install ubuntu again, this will change the boot menu during the installation.

Why do you need to re-install, that's the windows way to do things. If you explained your problem here, I'm sure we can help you repair your installation.

Jim

Well I figured it would be the best way.
First I did not install from a CD. No CD to burn the ISO file on and I am in an area where they are hard to get.
I tried install first with Grub and now I have a boot selection that says 
2. Ubuntu 6.06 installer
When I select it I get an error message about a missing windows file.

Then i tried unetbootin.. no go
Then i tried instlux... it puked
Then i tried Wubi.. which installed Ubuntu...with no problems..
added a third boot menu selection.. 
3. Ubuntu

and the video worked fine during the install..
but on first boot after install the video went south
looks like thousands of pieces of the windows flying all around.
So aside from the install issues... there is the video issue..
hence... ala windows.. <<<long time windows user.. since the version called (286) blow away... try again...it's programmed into the brain...:lolflag:

---

### Post by kansasnoob on 2008-08-30
Do you have the Win XP reinstall disc?

---

### Post by kansasnoob on 2008-08-30
Also Ubuntu 6.06 is very outdated!

---

### Post by starcannon on 2008-08-30
If your starting it all over, be sure to go get the Ubuntu 8.04 install disk. Have fun!

---

### Post by drcoracle on 2008-08-30
> **kansasnoob said:**
> Also Ubuntu 6.06 is very outdated!

I did not try to install 6.06
I was trying to install 8.04 without a CD
Just the ISO file on HD 0 trying to install to HD 1
I do not have a CDR to burn to right now.

---

### Post by drcoracle on 2008-08-30
> **kansasnoob said:**
> Do you have the Win XP reinstall disc?

Yes.

Just tried FIXMBR from the Recovery console..
It did not remove selection 2

1. Windows XP Professional
2. Ubuntu Installer 6.06

---

### Post by drcoracle on 2008-08-30
Just tried fixmbr from the recovery console.
It did not remove the 6.06 installer :-(

---


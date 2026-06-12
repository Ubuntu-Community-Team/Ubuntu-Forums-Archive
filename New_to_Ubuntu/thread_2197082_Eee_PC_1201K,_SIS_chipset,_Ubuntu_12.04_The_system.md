---
title: "Eee PC 1201K, SIS chipset, Ubuntu 12.04: The system is running in low-graphics mode"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by kaninsh on 2014-01-02
hello!
i have here a problem with an older asus netbook..
its the [Eee PC 1201K]("http://hothardware.com/News/Asus-Reveals-121-Eee-PC-1201K-With-AMD-Geode-CPU/") un which i tried to install [Ubuntu 12.04]("http://www.ubuntu.com/download/desktop") using [YUMI!]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/")

soon after the installation begins i get the **"The system is running in low-graphics mode” **error message!

(then theres an option to switch to console, but i not very strong with "sudo apt-get install")

i suppose its the SiS 741GX/966L chipset why i get this(are there any drivers needed?)

how/where can i get them?

---

### Post by chkneater on 2014-01-02
Yes, you need drivers.  Depending on your Grub version, you can install proprietary drivers from there, or install ubuntu-restricted-extras from synaptic.  Also in synaptic there is a section that should allow you to install the proprietary drivers.  Is this Nvidia or ATI?

---

### Post by squakie on 2014-01-02
It's SIS as they mentioned in their post.  Not sure on drivers for it.  I've been looking as well to try to help them.

---

### Post by squakie on 2014-01-02
I haven't found anything for linux to help you in the way of a driver.  The closest thing I could find was actually on the SIS download page, but they are OLD (11 years old!) and for RedHat.  Things have changed SO much in that time I wouldn't think they  would even work or compile.

There is another possibility - perhaps there is a way to use the VESA driver - it may be what is running now but I don't know.  I don't beleive you can do 3d with it.  Since xorg.conf went away a few releases back, I don't know how to specify that now.

I let google translate a very recent German thread on this very model of Eee pc and they pretty much said it won't work in linux.  If you do a google search on the sis igp you can look thru the posts.  Just be forwarned - I don't know what type of people were posting on that German site, but it is WAY beyond politically correct.  It appears to be racist.

---

### Post by chkneater on 2014-01-02
Actually I just found in synaptic there are drivers for Sis chips: xserver-xorg-video-sis.  Just look up Sis in synaptic.

---

### Post by squakie on 2014-01-03
Great!  That should help the OP!!  I had searched the net with linux <card it here> driver and basically it came up with nothing.  Glad you found it and hope it works for the OP.  I haven't found anything describing what the driver supports, so lets hope it works for them.  A google search of xorg <card id here> turns up nothing.  I did find[ this]("http://manpages.ubuntu.com/manpages/raring/man4/sis.4.html") entry that describes a driver I believe is probably the same one.

Good job!

---

### Post by kaninsh on 2014-01-03
ok, thanks [URL="http://ubuntuforums.org/member.php?u=647840"][B][COLOR=#000000]chkneater ;)
[/COLOR][/B][/URL]wonna try it one more time..hope it works!

ps. asus support just answered(after ~2 days):

"Thank you for contacting the Asus Support team. We are sorry to hear you are having difficulty with your PC Eee PC 1201K.

I am sorry but we do not fully support Ubuntu operating system. If Ubuntu is not fully working on this unit,  you may wish to try Lubuntu which is a more lightweight Linux operating system.

Please do not hesitate to contact us if you require any further help or support."

(i suppose he didnt really get my problem?)

pss.

**ehmm.how do i write it?? just "xserver-xorg-video-sis" or is there something more to add?**

---

### Post by squakie on 2014-01-03
> **kaninsh said:**
> ok, thanks [**[COLOR=#000000]chkneater ;)[/COLOR]**]("http://ubuntuforums.org/member.php?u=647840")....
**ehmm.how do i write it?? just "xserver-xorg-video-sis" or is there something more to add?**....

Follow the link in my last post - it's a how-to.  If you have problems following that or if something doesn't work please post back.  It also has a direct link for downloading the driver.

Also, [this]("http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there") link can help you set up the file needed.

---

### Post by kaninsh on 2014-01-03
ok, once more and abit slower..

ubuntu is bootin in and i get the splash screen [B]"The system is running in low-graphics mode&#8221;

[/B]i press **OK **and get 4 options..the last ist "exit to console login"please, step bu step from this point on![B]

what must i do/tipe to get sis driver working?
[/B]

---

### Post by chkneater on 2014-01-03
Do you have and desktop at all?  Low graphics mode usually just means you still have desktop but poor quality.  And what are the four options?  Synaptic is just a graphical front end for "apt-get" but it checks for dependencies and is more reliable than doing it by command line.  Are you only able to get to a terminal or do you have a desktop??

---

### Post by Bashing-om on 2014-01-03
kaninsh; et al;

Maybe of some help:
[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967) 
[http://ubuntuforums.org/showthread.php?t=2172375&page=8](http://ubuntuforums.org/showthread.php?t=2172375&page=8)

sis graphics can be problematic, but, there may be alleviation .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by kaninsh on 2014-01-03
@chkneater
no desktop at all! after the ubuntu logo(with the loading dots) the screen blinks..turns black..and i get the low graphics thing..
(is the error log important here? i can try to post it..)

---

### Post by mörgæs on 2014-01-04
> **chkneater said:**
> Synaptic is just a graphical front end for "apt-get" 
Correct.

> **chkneater said:**
> but it checks for dependencies and is more reliable than doing it by command line.

Apt checks for dependencies, too, else the front end (Synaptic) wasn't able to display them. Talking of being reliable nothing beats the command line, if you thereby mean 'apt'.


Ok, back on topic which is SIS graphics.

---

### Post by kaninsh on 2014-01-05
any ideas why the slax distro worked on this netbook???
(ok, i havent it installed yet, just booted up from flashdrive..but it works!!)

---

### Post by squakie on 2014-01-09
The instructions in the link I posted are pretty straight forward.  If you have specific questions, post those questions.  slax probably worked because they probably included the driver or are using the vesa driver.

---

### Post by chkneater on 2014-01-16
This is what is says in synaptic about the driver :  

This package provides the driver for all SiS and XGI Volari cards.

More information about X.Org can be found at:
<URL:http://www.X.org>

This package is built from the X.org xf86-video-sis driver module.

This package is built from the X.org xf86-video-sisusb driver module.



It also has a usb compatible file callled xf86-video-sisusb.  

You should be able to do "sudo apt-get install X.org xf86-video-sis" that way if you can get to a terminal.

---

### Post by squakie on 2014-01-16
May still need to create the pieces of a xorg.conf to set some of the options - that's why the other link is posted.

---

### Post by chkneater on 2014-01-16
I can't help you if you can't give me a better idea what your options are... what are the four options that are given when you very first see the words 'Ubuntu"??

---


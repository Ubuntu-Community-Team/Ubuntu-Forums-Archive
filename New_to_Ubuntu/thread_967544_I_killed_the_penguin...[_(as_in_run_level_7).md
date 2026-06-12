---
title: "I killed the penguin...:[ (as in run level 7)"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by slicepunk1 on 2008-11-02
I started off by updating 8.04 to 8.10 (8.04 ran with no problems). I have a Nvidia Geforce 6200 so once I upgraded I got the restricted drivers. Then I read around all the different forums looking for a quick fix because I was trying to get a res of 1280x768. So I Edited my xorg.conf file, then when I rebooted startx wouldn't work, just flashed and returned to the bash(not sure if this is the correct term?). Then I tried to reconfig, hide, remove, detect xorg but none of those worked. Now when I login my system I don't start the graphical interface successfully and go into text mode, and info says I have 77 processes 1 zombie process(I have no idea what that means), and I have no clue where to go from here.

Oh and when I login and type startx I get

(EE) NV(0): No valid modes found
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error
no screens found
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.

I tried to do everything I could find or think of before I made my own help me post, but now I'm out of things to do. So if you have any ideas please let me know because I'm fresh out.....:confused:

---

### Post by taqkavar on 2008-11-02
try : 
sudo apt-get install envyng-core
envyng -t
Then follow through the steps and install the appropriate driver, see if that fixes it.

If that one did nothing after as reboot :

sudo apt-get install links2
links2 
then use links2 ( press g to enter an URL ) and go to nvidia's website and download the proper driver for your card. then do:
sudo sh <name of the driver you just downloaded>
follow through and when asked to reconfigure X setting answer yes.

After you have done either of those, your card should start to work, to change the resolution, do:
sudo nvidia-settings (sudo is important here )
then choose the screen you have. click advance and change the resolution to exactly what you want. should work.
If you ever going to edit your xorg.conf , remember to make a backup of it first :

cp /etc/X11/xorg.conf /etx/X11/xorg.bak01.conf


If non of those work, make a copy of your xorg.conf file and post it here.

---

### Post by slicepunk1 on 2008-11-02
Ok awesome thanks for helping me but it's still broken because I thuroughly killed it.

The response for both commands were Failed to fetch, then E: unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

so I try sudo apt-get update and I get

W: a error occurred the repository is not updated and the previous index files will be used.GPG error [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release: the following signatures were invalid: NODATA 1 NODATA 2

says that message twice then fails to fetch the other archives as well

then says W: Some index files failed to download, they have been ignored, or old ones used instead.

W: You may want to run apt-get update to correct these problems

my xorg.conf consists of

Section "Device"
Identifier "configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Oh and I live in a dorm room and usually sign in with username and pass when I open a web browser to get internet. I also tried fresh installs with both 8.04 and 8.10, but once I got to where startx should kick in I got and I/O error with increasing numbers at the end....

Thanks alot for helping me out btw :)

---

### Post by slicepunk1 on 2008-11-02
"Bump"

---

### Post by lsutiger on 2008-11-02
Are you getting an IP address? Type ifconfig and post the response here.
That may be why you can not d/l anything w/ apt-get.

---

### Post by slicepunk1 on 2008-11-02
Okie Dokie logged in put ifconfig and here are my results:

UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:23 Base address:0x4000

eth1
Link encap:Ethernet  HWaddr 00:0d:88:6b:af:3e
inet addr:131.94.146.32  Bcast:131.94.147.255 Mask:255.255.254.0
UP BROADCAST RUNNING MULTICAST MTU:576 Metric:1
RX packets:7309 errors:0 dropped:0 overruns:0 frame:0
TX packets:63 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:1000
RX bytes:929729 (929.7 KB) TX bytes:7042 (7.0 KB)
Interrupt:16

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:488 errors:0 dropped:0 overruns:0 frame:0
TX packets:488 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:30672 (30.6 KB) TX bytes:30672 (30.6 KB)

whew takes a while for a two finger typer like me to hand type those :]
Usually when I logged into 8.04 before my upgrade I would open firefox with google as my homepage, then I would be redirected to the school's login page, login and then I'd have internet and I would only have to login again if I plugged my internet into my xbox or shut down my computer for a while...:confused:

---

### Post by lsutiger on 2008-11-02
> inet addr:131.94.146.32
You are getting an IP, so thats not the problem. But being on a restricted access line like you are it may be causing problems. Is this a laptop or a desktop?
If it is portable, you could try to set it up on a friends internet and see what happens there.
OR...I hate to say this, you could try to do another install. It's quick and nearly painless.

Question: did you backup your xorg file (make a copy of it) before fiddling with it? If so you could just copy over the backup.

---

### Post by lsutiger on 2008-11-02
Just thought of something...there is a text based browser you can run from CLI. 
Do you know the address that you get redirected to in order to use the campus' internet? If so use w3m
type w3m <URL> (<URL> being the address you get redirected to)

---

### Post by slicepunk1 on 2008-11-02
Awesome! so i used w8m to access google, got redirected, navigated to login, logged in, accepted agreement, and now I wanna know how to leave this w8m interface so I can try to do those updates again. Is there a command I can do to get back to just basic command line?

---

### Post by slicepunk1 on 2008-11-02
nevermind got out of it and am doing updates now I'll let you know how it goes in a sec

---

### Post by slicepunk1 on 2008-11-02
Ok did apt-get update fetched some stuff but when I rebooted when the login screen is supposed to come up I get kinit: No resume image, doing normal boot...

so then I tried sudo nvidia-settings and this was displayed

ERROR: The control display is undefined; please run 'nvidia-settings --help' for usage information.

This is a desktop pc, the xorg.conf is just the one I typed earlier, and there aren't any hidden xorg.conf with ~ at the end.

---

### Post by HyperHacker on 2008-11-02
That just means X can't start for some reason. Post your /etc/X11/xorg.conf file.

---

### Post by slicepunk1 on 2008-11-02
> Section "Device"
Identifier "configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

I just looked and it's the same as it was before

---

### Post by lsutiger on 2008-11-02
Seems you are missing a bit in your xorg file. For one there is no driver listed.
I am not sure I can help you out much more. I am far from being a guru at video settings ad my self have an ATI card.

I will be following and try to help if I come up with a brain fart :)

---

### Post by slicepunk1 on 2008-11-02
Ok awesome! I run a nvidia Geforce 6200 btw. It seems I'm not the only person with this problem and an nvidia card. Some people on other forums are saying the xorg.conf is different in 8.04 vs. 8.10 but I know very little about linux...

---

### Post by lsutiger on 2008-11-02
I found [this link]("http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html") in ubuntugeek. I didn't read through it all, but it is specific to nvidia and 8.10
Hope it helps!

OT - I think one of Ubuntu's bad sie is the lack of documentation/availability of documentation of changes 'under the hood'. A lot of us get used to fixing a problem one way, then that solution doesn't work on the upgrade...DOCUMENT IT!!!
Thats my only gripe! Other than that, Ubuntu has been a great fresh air to my computing life.

---

### Post by slicepunk1 on 2008-11-02
Ok gonna check it out and see where I can get. I gotta say I love the community and the product equally, and I don't miss the magic fix it buttons at all. I want to learn alot more so I can be semi non retarded about linux..

---

### Post by slicepunk1 on 2008-11-02
Well, it looks like he's doing most things graphically but that web page did help me figure out that I already have nvidia-glx-177 installed and the newest version. But still no graphical Interface login when I start up. Any other ideas as to what I could do?

---

### Post by lsutiger on 2008-11-02
Well, if you have your home folder on a separate partition, I would just reinstall then go back to the site I referred. The install takes a lot less time than what we have spent so far on the subject. I understand the want to learn, but hey, fi you want a working system, go with the easiest solution.

As far as learning, one of the things I have done is just read posts here and use google a hell of a lot. The difference between Ubuntu and MS is that you don't have as many problems. :) And the ones you do have, there is always a solution out there.

---

### Post by slicepunk1 on 2008-11-02
Ok tried to do a fresh install of 8.04 and I get this error
[  189.545253] Buffer I/O error on device fd0, logical block 0

This message keeps appearing down the screen the only thin that changes are the numbers in the []. I think this is related to my current problem....possibly?:confused:

---

### Post by lsutiger on 2008-11-02
Do you have a floppy disk drive installed? If so, do you have a disk in it?

---

### Post by slicepunk1 on 2008-11-02
Nope I don't have a floppy driv or a floppy disk...weird....You think my computer thinks I have one?

---

### Post by slicepunk1 on 2008-11-02
Any ideas anyone? I'm not trying to be pushy or anything, it just stinks doing a project for my upper level marketing class on my 1999 compaq laptop running gutsy \\:D/

Could I somehow switch to the 173 driver or does my problem have nothing to do with my graphics card?

---

### Post by slicepunk1 on 2008-11-03
Bump

---

### Post by :) Smiley :) on 2008-11-03
I recommend backing up all your data and then installing ubuntu 8.10 from the CD, erasing the partition you're going to install on to get rid of anything that might have got stuffed up, then once you have it installed (and hopefully have X running) go to System > Administration > Hardware Drivers. This should give you a list of drivers you can install. This is what I've always done for my nvidia card and it works fine for me.

---

### Post by slicepunk1 on 2008-11-03
Thanks for the advice but I get the I/O error I listed above if I try to install either 8.10 or 8.04 and I haven't even come close to seeing the graphical interface on my other computer in days.

---

### Post by HittingSmoke on 2008-11-03
When exactly does the message appear? Between what steps in the install.

---


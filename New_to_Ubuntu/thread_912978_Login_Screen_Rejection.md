---
title: "Login Screen Rejection"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by JumpForJoy on 2008-09-07
Ok.  I just installed Ubuntu today.  I can get to the login screen on my commputer but as I type in my name and password it begins to log me in, but then my moniter goes into a powersaving mode and turns back on a couple seconds latter back at the login screen.  I can login in the fail safe mode but only that.  I am compleatly new to Linux and Ubuntu so any help will be greatly appriciated.  Thanks.

---

### Post by sharks on 2008-09-07
on ur login screen, at the left bottom  there will be options and select sessions and gnome fail session or safe mode and try.

---

### Post by JumpForJoy on 2008-09-07
Yes.  I can get into the fail safe mode of gnome but that is all.  If I try to run it normally my moniter shuts off and a few seconds later it's back on, but the screen returns to the login screen.

---

### Post by d79457 on 2008-09-07
> **JumpForJoy said:**
> Yes.  I can get into the fail safe mode of gnome but that is all.  If I try to run it normally my moniter shuts off and a few seconds later it's back on, but the screen returns to the login screen.

I am a fresh to ubuntu too, sorry i can't help you~

---

### Post by Bucky Ball on 2008-09-07
When you boot to the grub menu, try going into the recovery kernel (should be second on the list) and see if that throws an error or fixes anything on its check through. Let us know how you go.

---

### Post by JumpForJoy on 2008-09-07
Yes.  I went to the secont opption and everyting said ok next to it.  I can't connect to the enternet through Ununtu so I couldn't get to the websites.  I tryed the 3 options that I had on the screen and they all finished.  I still cant get to login without the safe boot....

---

### Post by JumpForJoy on 2008-09-07
Ok.  I just tried going into safe boot, termanal and typeing

sudo cp /etc/X11 xorg.conf.bak

sudo rm /etc/X11/xorg.conf

It didn't change anything

---

### Post by Bucky Ball on 2008-09-07
There is a screen setting in your Gnome setup which is causing this I am imagining. As this is a fresh install and you haven't played around with much, I can't see why it should be doing this but ...
Something new everyday. 

Have you *ever* been able to login normally? Could you post the specs of your machine please so we know what we're dealing with. Could be a known bug with a workaround.

As it is a fresh install, you can try the advice here:

[http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/](http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/)

I would say be*** very*** wary of anything that tells you to **rm -rf** as you are removing files and if you don't know what, you can get in real trouble. In this instance though, you are only removing settings, not the applications so safe. Have a good read of that and maybe a look about.

* ***Update!!!*** My point exactly. You have just removed your xorg.conf file. You do have a backup thankfully. That is if you typed 

**sudo cp /etc/X11/xorg.conf.bak**

and not 

**sudo cp /etc/X11 xorg.conf.bak** (you have a / missing) 

See if you can still log in gnome failsafe or any other way, please. :)

---

### Post by JumpForJoy on 2008-09-07
Ok thanks.  I'll look at that website.  I can still login in the fail-safe mode only.  How should I get my settings back to defult?

---

### Post by JumpForJoy on 2008-09-07
I have also **never** been able to login normaly

---

### Post by Djanvk on 2008-09-07
I'm also new to linux and was having the same problems as you described.  It has something to do with the gnome desktop what I did that worked to use Linux I went to the bottom left and selected the menu to go into a console, and I did this:

sudo apt-get install xubuntu-desktop

or

sudo apt-getinstall icewm

and then in the bottom left menu selected either the icewm or the xfcd (something like that) and those GUI desktops work for me.

Hope this helped.  It's something with the Gnome desktop.

---

### Post by Bucky Ball on 2008-09-07
Okay, try the instructions on that site and see if that gets you any joy. \\:D/

---

### Post by Bucky Ball on 2008-09-07
> **Djanvk said:**
> I'm also new to linux and was having the same problems as you described.  It has something to do with the gnome desktop what I did that worked to use Linux I went to the bottom left and selected the menu to go into a console, and I did this:

sudo apt-get install xubuntu-desktop

or

sudo apt-getinstall icewm

and then in the bottom left menu selected either the icewm or the xfcd (something like that) and those GUI desktops work for me.

Hope this helped.  It's something with the Gnome desktop.

That doesn't fix the original problem at all, of course, just means you are using a different desktop. You would be better off finding out why this is happening because basically, you won't be able to use a straight gnome desktop until you do. Xubuntu is a pared down version for lower spec machines and icewm is even more lightweight. You can add apps as you go, but you get my meaning. If you consider that a solution why not load KDE, Openbox, Fluxbuntu ... there are a million apt-get take_your_pick options to choose from.   ;(

I imagine it is a screen setting in your original gnome or something along those lines ... it is trying to load the gnome desktop, it is too large to fit and therefore is defaulting back to login again to try and get you to fix it or choose another.

Will post again on this tomorrow when I am awake! It is 3am here. :-s

---

### Post by sanemanmad on 2008-09-07
> **JumpForJoy said:**
> Ok.  I just tried going into safe boot, termanal and typeing

sudo cp /etc/X11 xorg.conf.bak

sudo rm /etc/X11/xorg.conf

It didn't change anything

Did you reboot or restart the X-server by chance?

---

### Post by sanemanmad on 2008-09-07
You may also consider running through the dpkg util.

sudo dpkg-reconfigure xserver-xorg

---

### Post by JumpForJoy on 2008-09-07
> **sanemanmad said:**
> Did you reboot or restart the X-server by chance?
I'm not sure.  I restarted my commputer.


@Djanvk: I tryed your advice,thanks, but it didn't help me.  I still couldn't log in.

@Bucky Ball: Thanks.  I will, Good night.

---

### Post by Bucky Ball on 2008-09-07
BTW[B]

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf[/B]

Should put a copy of your original back into the appropriate place. You should be able to do this by dropping to a shell from you login screen as shown below rather than having to load Live CD each time.

First, type:

**dir /etc/X11**

To make sure your backup copy is there.

dir = directory. cp = copy. mv = move. rm = **remove!**

**** Dropping to a shell from login screen ***
At your login screen before logging in try this:

1/ **CTL/ALT/F1** - (this will take you to a shell)
2/ Enter user name and password
3/ Type: **nano /etc/X11/xorg.conf** (this should show you the xorg.conf file)

Have a look in there and check out the section that is about your screen. Does it say 'Default Screen'?

Let us know how you went and maybe scribble down some details and post them here.

4/ Type: **start X** (may need to type **sudo start X**, not sure from memory) 

That should boot. Do you get the same result and wind up at the login screen again?


sudo: su = super user; do = do! superuser do (or make me root for this command only).


 :)

---

### Post by sanemanmad on 2008-09-08
> **Bucky Ball said:**
> There is a screen setting in your Gnome setup which is causing this I am imagining. As this is a fresh install and you haven't played around with much, I can't see why it should be doing this but ...
Something new everyday. 

Have you *ever* been able to login normally? Could you post the specs of your machine please so we know what we're dealing with. Could be a known bug with a workaround.

As it is a fresh install, you can try the advice here:

[http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/](http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/)

I would say be*** very*** wary of anything that tells you to **rm -rf** as you are removing files and if you don't know what, you can get in real trouble. In this instance though, you are only removing settings, not the applications so safe. Have a good read of that and maybe a look about.

* ***Update!!!*** My point exactly. You have just removed your xorg.conf file. You do have a backup thankfully. That is if you typed 

**sudo cp /etc/X11/xorg.conf.bak**

and not 

**sudo cp /etc/X11 xorg.conf.bak** (you have a / missing) 

See if you can still log in gnome failsafe or any other way, please. :)
How would removing the *xorg.conf* file prevent someone from logging into Gnome? last I checked the xorg settings are applied during boot. So having user ***rm ***that file would start with a scratch file [Which I have done NUMEROUS times]. In fact, I could not get dualhead to work, so I removed my xorg.conf file.... and voila! I had dualmonitors. Of course some of the settings my need to be altered but it worked. 

This may not be the case in this thread... Of course from looks this case may not be resolved.


*UPDATE to all who are having this issue*

Does this sound like your problem? You get to the login... it looks normal. So you enter your username... now your password.... You can hear the Ubuntu start-up screen.... you see the desktop..... Wait everything just went dark and my screen is going to sleep.....Shoot. Im back at the login. YES. This fixed my problem. ....... removing my xorg file and if it is still acting up then you will need to sudo dpkg-reconfigure xserver-xorg

---

### Post by Bucky Ball on 2008-09-08
[quote=sanemanmad]This fixed my problem. ....... removing my xorg[/quote]

Didn't fix this one.

[quote=sanemanmad]How would removing the *xorg.conf* file prevent someone from logging into Gnome?[/quote]

It wouldn't. But you would lose any settings you have in there. Seeing as this is a fresh install, not much to be lost. Point I was trying to make to a new user was that rm-ing is not a good idea until you know what you are doing (some people think it is funny to tell new users to rm vital files thus screwing their system). You will note the instructions followed were from another page and they included backing up xorg.conf .

[quote=sanemanmad]
if it is still acting up then you will need to sudo dpkg-reconfigure xserver-xorg[/quote]Agreed, by all means, give it a shot and see how you go.

---

### Post by JumpForJoy on 2008-09-09
Ok.  Big news.  I was able to log into Ubuntu normaly for the first time.  How I did it:
I went into failsafe gnome
I rigtclicked on the desktop and changed the desktop background to a single color.
This allowed me to login to ubuntu but it did not fix the overall problem.  I still don't know why I wasn't able to log in.  I wasn't using any transparenty like in the article.  I'll try the other thing that all you guys sujested and see if that lets me have any background?

---

### Post by JumpForJoy on 2008-09-09
Any Idea why the background was messing me up?

---

### Post by JumpForJoy on 2008-09-10
All right.  I fee like an idiot.  I can't login anymore.  I've tried everything that I did befor but I can't login...  What should I do?

---

### Post by JumpForJoy on 2008-09-11
> **Bucky Ball said:**
> BTW[B]

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf[/B]

Should put a copy of your original back into the appropriate place. You should be able to do this by dropping to a shell from you login screen as shown below rather than having to load Live CD each time.

First, type:

**dir /etc/X11**

To make sure your backup copy is there.

dir = directory. cp = copy. mv = move. rm = **remove!**

**** Dropping to a shell from login screen ***
At your login screen before logging in try this:

1/ **CTL/ALT/F1** - (this will take you to a shell)
2/ Enter user name and password
3/ Type: **nano /etc/X11/xorg.conf** (this should show you the xorg.conf file)

Have a look in there and check out the section that is about your screen. Does it say 'Default Screen'?

Let us know how you went and maybe scribble down some details and post them here.

4/ Type: **start X** (may need to type **sudo start X**, not sure from memory) 

That should boot. Do you get the same result and wind up at the login screen again?


sudo: su = super user; do = do! superuser do (or make me root for this command only).


 :)

Big problem.  I just discovered that my xorg.conf file is gone.  I typed dir .etc/X11
It showed a few files and two files that were:
1. xorg.conf.20089907071733
2. xorg.conf.20080907073446

No just xorg.conf file
therefor when I typed sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf it did nothing.  I beleive that this could be my problem now.  How can I get this file back?

---

### Post by Bucky Ball on 2008-09-11
[quote=JumpForJoy]Ok.  I just tried going into safe boot, termanal and typeing

sudo cp /etc/X11 xorg.conf.bak

sudo rm /etc/X11/xorg.conf

It didn't change anything[/quote]

Yea, that is when you removed it, remember?


Okay, make sure you are in /etc/X11 dir:

**cd /etc/X11**

Then, create an empty file there:

**sudo mkdir xorg.conf**

Run 'dir' to make sure you have successfully created the empty file. Also, check to make sure the backup file we created is in there. I wonder about this as in your quote above, this command:

**sudo cp /etc/X11 xorg.conf.bak**

Should have been:
[B]
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak[/B]

Which would have copied your original xorg.conf file into the same directory under the name xorg.conf.bak. If it is there, then:

[B]sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

[/B]That should put it back.

If it is not there, you could try:

**sudo dpkg-reconfigure xserver-xorg**

... and/or

  **sudo dpkg-reconfigure -phigh xserver-xorg**

Let us know how you go.

---

### Post by handydan918 on 2008-09-11
> **Bucky Ball said:**
> Yea, that is when you removed it, remember?


Okay, make sure you are in /etc/X11 dir:

**cd /etc/X11**

Then, create an empty file there:

**sudo mkdir xorg.conf**


Unless the devs have created a weird alias for mkdir, the correct command here should be ```
sudo touch xorg.conf
```


mkdir makes an empty directory. 
touch creates an empty file.

---

### Post by tarps87 on 2008-09-11
It sounds like it could be resolution problem, I don't know why changing the background fixed it temporally.
try:```

sudo dpkg-reconfigure xserver-xorg
```
and select only the resolution 800x600 and see if this solves it.
Under system -> preferences -> screen resolution (in safe mode) what resolution does it say its using

---

### Post by Bucky Ball on 2008-09-11
[quote=handydan]mkdir makes an empty directory. 
touch creates an empty file.[/quote]

Of course, handydan. Thanks. Studying for an exam so brain elsewhere. Might get back to it. 8-[

That is naturally what I was getting at. :)

---

### Post by handydan918 on 2008-09-12
> **Bucky Ball said:**
> Of course, handydan. Thanks. Studying for an exam so brain elsewhere. Might get back to it. 8-[

That is naturally what I was getting at. :)

I understand. I recently directed some hapless soul to look for his xorg.conf in /etc/xserver....
duh. 

:)

---

### Post by JumpForJoy on 2008-09-12
Ok...  I deleted the xorg.conf dir and replaced it with a nano xorg.conf.  I then ran both sudo dpkg-reconfigure xserver-xorg and dpkg-reconfigure -phigh xserver-xorg.  It created backup files.  I still can't login.  I changed my screen resolution to 600x800.  It was way higher... can't remember exactly what...  but I still cant log in?

---

### Post by crjackson on 2008-09-12
I'm guessing you have a ATI video card.  Probably and Xpress 200 or something similar.  Please confirm.  If so, I have a few things you can try that will probably fix the problem.

Have a look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/252767") I filed.

---

### Post by SHRIKEE on 2008-09-13
I have this exact same issue with an ATI onboard X200

AMD3500+, 1.5GB ram, 320GB SATAII, 17" LCD (1280x1024 @ 1024x768)

Any tips what so ever? I want to make a server and am tired of doing everything via terminal so i installed the desktop version :)

It seems i made a bad choice so far...

Failsafe mode works, Failsafe terminal also.

ctrl/alt/f1-f8 screws up the screen output and stalls until i press ctrl/alt/f9 again which brings me to the default (graphical) login prompt.

reconfiguring X didn't work. Also lowering the res in failsafe didnt, i instaleed updates via failsafe which also didn't solve the issue.

---

### Post by crjackson on 2008-09-13
> **SHRIKEE said:**
> I have this exact same issue with an ATI onboard X200

AMD3500+, 1.5GB ram, 320GB SATAII, 17" LCD (1280x1024 @ 1024x768)

Any tips what so ever? I want to make a server and am tired of doing everything via terminal so i installed the desktop version :)

It seems i made a bad choice so far...

Failsafe mode works, Failsafe terminal also.

ctrl/alt/f1-f8 screws up the screen output and stalls until i press ctrl/alt/f9 again which brings me to the default (graphical) login prompt.

reconfiguring X didn't work. Also lowering the res in failsafe didnt, i instaleed updates via failsafe which also didn't solve the issue.

I haven't tried it yet, but I'm told you can login using failsafe, and blow away compiz fusion.  I'm also told you can login failsafe, get the restricted driver installed, turn off desktop effects and that too works.

I haven't tested this yet...

---

### Post by SHRIKEE on 2008-09-13
wicked, gonna try that now..

didn't think of compiz yet...

i'll keep you posted

---

### Post by SHRIKEE on 2008-09-13
Hmm somehow with the "change the background" thing even failsafe died.

No menubars show up and all it does is load this:
[http://meandmymac.net/wp-content/uploads/img_0043.jpg](http://meandmymac.net/wp-content/uploads/img_0043.jpg)


but i thought of something else...

I'm gonna install the server edition, since i want a server anyway, and intall a basic no-nonsense Gnome on that.

I think that'll work better.
[http://www.google.com/search?q=ubuntu%20server%20gnome](http://www.google.com/search?q=ubuntu%20server%20gnome)
Many people have tried/done this already so i'm sure i can manage too...

---

### Post by JumpForJoy on 2008-09-13
Yep that's exactly the problem I have.  That link didn't help much.  I stil have no idea why this is happening.  I don't want the server ubuntu so I'm a fix.  I also can't change my grafics card, or don't know how to.  So....

---

### Post by JumpForJoy on 2008-09-14
Ok.  I droped to the shell with Ctr+Alt+F1.  I then cd to /etc/X11 then sudo startX.  I loged in fine as the root by doing that but I still couldn't login normaly only like that and failsafe.

---

### Post by JumpForJoy on 2008-09-14
What should I do once I sucsessfully start the x sever?

---

### Post by Bucky Ball on 2008-09-14
You are on the desktop but back to square one with the login merry go round - login and back to login screen? If so, try right clicking on the desktop and set background to 'solid colour' if it is not already. Set effects to normal for the moment, just to see if this works.

---

### Post by pmohr on 2008-09-14
FWIW, I'm experiencing the same problem...and, surprise:
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]

Going to try a few things now...

---

### Post by Bucky Ball on 2008-09-15
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

pmohr, is that any help?

---

### Post by JumpForJoy on 2008-09-15
I couldn't get much from that webpage.  Thanks though...  I have already changed the background and it didn't help me log in.  Thanks though...

---

### Post by crjackson on 2008-09-17
> **JumpForJoy said:**
> I couldn't get much from that webpage.  Thanks though...  I have already changed the background and it didn't help me log in.  Thanks though...

I don't have that particular box anymore.  I upgraded my video card to elimiate the issue, and gave the box to my son a few hundred miles away.  I do have another box EXACTLY like it (bought 2 for my store) that's not in use at the moment.

I'll try to clear some time later in the week to see if I can find some way to make this happen for you.  I posted the original bug report but the launchpad moderator told me he was going to close the bug since no one else seemed to have the problem, and I couldn't provide additional information.  

If you guys would look up my privious post with the link to the bug report and generate some activity, perhaps we can get the "A" team to help out with this.  Otherwise I fear the bug may carry over to the next release and so forth.

If I'm able to find a work around, I'll let you know here ASAP.

---

### Post by chaotickat on 2008-09-17
Hi,

I have the same problem and the same graphics card.  

crjackson: I went over to the bug report page and posted the files they requested. Hopefully someone can figure this out. Thanks for all your hard work.

---

### Post by JumpForJoy on 2008-09-17
Yes.  I'll let you know if I find a work around too.  This is a big bug if it carys on into the next and next ubuntu upgrads...

---

### Post by crjackson on 2008-09-17
Maybe we'll get some help now that more people are responding.  It's great how this community works together.:)

---

### Post by JumpForJoy on 2008-09-18
> **crjackson said:**
> Maybe we'll get some help now that more people are responding.  It's great how this community works together.:)

Yes, I definatly agree.  I hope that someone could find a workaround....  I find that the installation isn't the problem.  It's alctuly something wrong with Ubuntu and my computer....:confused:

---

### Post by JumpForJoy on 2008-09-18
[http://ubuntuforums.org/showthread.php?t=911497]("http://ubuntuforums.org/showthread.php?t=911497")
That link might help some people.  I don't know...

---

### Post by crjackson on 2008-09-18
> **JumpForJoy said:**
> [http://ubuntuforums.org/showthread.php?t=911497]("http://ubuntuforums.org/showthread.php?t=911497")
That link might help some people.  I don't know...
@JumpForJoy

I don't think you ever stated what video card you have.  Is it also the Radeon xpress 200 like the others have reported?

---

### Post by JumpForJoy on 2008-09-19
Computer Specs:
System:
Microsoft Windows XP
Media Center Edition
Version 2002
Service Pack 2

Registered to:


*****-***-*******-*****



Hewlett-PackardCompany
Compaq Presario
AMD Athlon(tm) 64 Processor
3500+
984 MHx, 960 MB of RAM
Phyisical Address Extention


Device:
**_ATI RADEON XPRESS 200 Series_**
Manufacturer: ATI Techologies Inc.
Chip Type: ATI RADEON XPRESS 200 Seriesm (0x5954)
DAC Type: Internal DAC(400MHz)
Approx Total Memory: 256.0 MB
Current Display Mode: 1024 x 768 (32 bit)(60Hz)
Monitor: COMPAQ FS7600 Color Monitor

DirectX Freatures
DirectDraw Acceleration: Enabled
Direct3D Acceleration: Enabled
AGP Texture Acceleration: Enabled




I thought that I should just post all my specs(so yes I am)

---

### Post by JumpForJoy on 2008-09-19
> **Djanvk said:**
> This is my video card:  ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

Is there a problem with Linux and This?  Could that be the problem

from fourm [http://ubuntuforums.org/showthread.php?t=911497](http://ubuntuforums.org/showthread.php?t=911497)

Some one else has the same problem with the same card...  interesting.  Very interesting...:(

---

### Post by crjackson on 2008-09-19
> **JumpForJoy said:**
> Computer Specs:
System:
Microsoft Windows XP
Media Center Edition
Version 2002
Service Pack 2

Registered to:


*****-***-*******-*****



Hewlett-PackardCompany
Compaq Presario
AMD Athlon(tm) 64 Processor
3500+
984 MHx, 960 MB of RAM
Phyisical Address Extention


Device:
**_ATI RADEON XPRESS 200 Series_**
Manufacturer: ATI Techologies Inc.
Chip Type: ATI RADEON XPRESS 200 Seriesm (0x5954)
DAC Type: Internal DAC(400MHz)
Approx Total Memory: 256.0 MB
Current Display Mode: 1024 x 768 (32 bit)(60Hz)
Monitor: COMPAQ FS7600 Color Monitor

DirectX Freatures
DirectDraw Acceleration: Enabled
Direct3D Acceleration: Enabled
AGP Texture Acceleration: Enabled




I thought that I should just post all my specs(so yes I am)

The system itself is fine (memory is on the low side though, so don't expect the best performance).

The main problem is the video card.  I'll try to dig into this in a few days when my "Honey-Doo" chores are done.  If I find a workaround, I'll post the solution here.

---

### Post by JumpForJoy on 2008-09-19
Thanks, I'll do the same.

---

### Post by Bucky Ball on 2008-09-19
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Any good?

Make sure you have **ubuntu-restricted-extras** installed. This can be found by copy and pasting in a search in Synaptic Package Manager.

---

### Post by crjackson on 2008-09-19
> **Bucky Ball said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Any good?

Make sure you have **ubuntu-restricted-extras** installed. This can be found by copy and pasting in a search in Synaptic Package Manager.

I assume you mean **restricted-modules** and not restricted-extras which is totally different.

```
sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```

---

### Post by Bucky Ball on 2008-09-19
[quote=crjackson]I assume you mean **restricted-modules** and not restricted-extras which is totally different.[/quote]

No, I didn't. Why? :confused::)

---

### Post by crjackson on 2008-09-19
> **Bucky Ball said:**
> No, I didn't. Why? :confused::)

Because we are discussing problems with the fglrx restricted modules and their non-working condition with the Radeon Xpress 200.  We're not discussing multimedia codecs, java, mscorettfonts, etc... So I don't see how ubuntu-restricted-extras got into the mix :confused:

---

### Post by Bucky Ball on 2008-09-20
> **crjackson said:**
> Because we are discussing problems with the fglrx restricted modules and their non-working condition with the Radeon Xpress 200.  We're not discussing multimedia codecs, java, mscorettfonts, etc... So I don't see how ubuntu-restricted-extras got into the mix :confused:

Yep, I'm with ya. Late night! Investigating the restricted-modules myself now so thanks for that. Learn something everyday. :)

---

### Post by JumpForJoy on 2008-09-21
when I type
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-friver-fglrx
sudo depmod -a

```
in the terminal the only command that works is
```
sudo depmod -a
```
because I can't talk to the internet without loging on normaly.

What should I do?

---

### Post by Bucky Ball on 2008-09-21
.

---

### Post by JumpForJoy on 2008-09-21
why "."?  how can I conect to the internet  hmmmmmmm...........

---

### Post by markbuntu on 2008-09-21
There are problems other than just the xserver that will cause this login issue. When you get in with safe mode you need to look in your log files with System/Administration/System Log. There may be a message about a missing file in the syslog or in messages or the kern.log that are preventing gdm from authenticating the user. You may also find messages about why your network connection is not working. 

You should also look in your Xorg.0.log for lines that start with (EE) which are error messages from the xserver startup sequence.

The log files are your friends. Go visit them

---

### Post by JumpForJoy on 2008-09-22
Awsome thanks
I got this screenshot.  I'll get the xorg one when I can
Thanks so much...

---

### Post by JumpForJoy on 2008-09-22
ok.  I looked at the xorg log file and there were no (EE) but there were a couple (WW) the warnigs I couldn't understand but the word Radeon was used a couple times....:confused:

---

### Post by markbuntu on 2008-09-22
OK, that was a good screenshot, you have a gdm failure which is preventing normal login. Gnome Safe mode bypasses gdm. 

You can try this to login to your normal screen. System/Administration/Login Window. It will ask for your password and then it should open. Go to Security and check Enable Timed Login. This bypasses the password checking and may get around that GLib Critical thing. Put your username in the box and set the Pause before login at 10 seconds of more. Logout and see if that works.

Do not Enable Automatic Login or you will never be able to get to gnome safe mode again.

---

### Post by JumpForJoy on 2008-09-22
Yeah, that screen shot was a little fuzy.  Thanks.  I'll try that, but I don't think that it will work because I can log into gnome safe mode but everytime I click the logout butten in the top right my computer frezzes up.  I'll try anyway.  Thanks.  Get back to you if it works or not.

---

### Post by JumpForJoy on 2008-09-22
> **JumpForJoy said:**
> ok.  I looked at the xorg log file and there were no (EE) but there were a couple (WW) the warnigs I couldn't understand but the word Radeon was used a couple times....:confused:

(just restating that because that seems like a common problem)

Ok.  so I changed it to a timed login, faild to logout of failsafe gnome.  Then I restarted the computer and the countdown to log me in started.  When it finished It loged me in then my screen went blank and it took me back to the login screen.  Any ohter ideas.  I'm stumped....[-o<why can't I figure this out!!!!! ahhhhh

---

### Post by JumpForJoy on 2008-09-23
does anyone else have any information on this problem?

---

### Post by markbuntu on 2008-09-23
Ok, that didn't work. Try running System/Administration/Update Manager from gnome safe mode so we can be sure you are all updated.

---

### Post by JumpForJoy on 2008-09-25
Ok.  So I logged into gnome safe mode.  Started to install the updates, but I couldn't because I can't connect to the internet in fail safe gnome.  There were 5 updates that I couldn't install.  I just got my version of Ubuntu like 2 weeks ago, so I'm almost positive that I have most of the important updates.

---

### Post by JumpForJoy on 2008-09-28
Do you know if I would have this same problem if I tried the server version instead of the desktop version?

---

### Post by nefnet13 on 2008-10-03
Hey everyone, 

I am a new Linux user (as of tonight-- fresh install-- hooray, I think) and I too am a victim of this issue.  And yes, my mobo has an onboard Radeon x200 graphics chipset.  

Unlike Jump for Joy, however, I do have full network access in the "safe" login (Oops I almost called it "safe mode", how's that for Windoctrination?) and I have tried a few of the fixes recommended so far in this thread (although I must confess that the command-line stuff seems like typing gibberish at this point-- kind of unsettling doing things when I have no idea what the commands I am issuing mean) but so far no dice.  

All I wanted was a nice desktop box with the Edubuntu package for my kids and wife to use.  And I already blew out the old XP install completely (but it was pretty much borked anyway, and I was using a VLK of questionable authenticity, so I guess I really didn't lose much).  

So if there's no resolution to this issue within the confines of Ubuntu, can any of you nice folks point me to a distro that is easy to set up, easy to use and would work properly with this confounded video chipset?  'Cause the whole reason I went the Linux route is because I'm cheap.  Don't want to have to buy a vid card... 

Thanks in advance for anybody's help.

---

### Post by Bucky Ball on 2008-10-03
nefnet13, you might be better to create a new thread with your problem in the suitable forum; General Help, Multimedia or this one. Give as much info as you can and a title that describes the problem as best you can. People won't find you at the end of such a long and old thread. 

ps: just copy and paste the command line stuff. :)

---

### Post by JumpForJoy on 2008-10-05
[QUOTE=Bucky Ball;5897555]nefnet13, you might be better to create a new thread with your problem in the suitable forum; General Help, Multimedia or this one. Give as much info as you can and a title that describes the problem as best you can. People won't find you at the end of such a long and old thread. 
QUOTE]

Could you post the url of your thread plz.
Thanks

---

### Post by coffeepro on 2008-10-09
I assume there is no fix or workaround for this yet?
Same card -----> Radeon xpress 200

7.04 installs fine. Tried 3 fresh installs of 8.04 but get the infinite loop to the log-in. What a hassle. Is Compiz ON by default and could that be the problem? Or is this release just not compatible with this piece-of-junk video card?

---

### Post by tarps87 on 2008-10-10
@JumpForJoy
Could you attach your xorg.confg file, I have expereanced a simular problem on the kunbuntu8.10 beta (i know its not the same version but it may work) and it was due to it using the wrong driver.
Also can you post the output of:
```
 dpkg -l | grep xserver-xorg-video
```

and also```
lspci | grep VGA
```

---

### Post by coffeepro on 2008-10-11
Strange. The Ubuntu 8.04 disk from Canonical wouldn't work no matter how many times I tried. Looping back to the log-in. A burned Xubuntu 8.04 installed without the slightest hitch. 

Not gonna question why and don't care.

---

### Post by Bucky Ball on 2008-10-11
> **coffeepro said:**
> Strange. The Ubuntu 8.04 disk from Canonical wouldn't work no matter how many times I tried. Looping back to the log-in. A burned Xubuntu 8.04 installed without the slightest hitch. 

Not gonna question why and don't care.

Neither would I. Seems to be the way it goes sometimes with Ubuntu at least for many reasons ... but it worked in the end! \\:D/

---

### Post by Keen101 on 2008-10-11
JumpForJoy, and nefnet13:

This may not solve your problems, but i figure it's worth a shot.

Try the 8.10  Ubuntu IBEX beta... It may have better graphics drivers for you. Of course it IS a beta, and things can break, but if hardy is not working for you....

I am running 8.10 IBEX on my HP Compaq dc5750, because I could not get any of the hardy 8.04 versions working with this computer. I was about to give up, but tried the IBEX alpha and it worked! The Ibex alpha/beta release seemed to have updated graphics drivers that the 8.04 hardy version did not have. I say, give it a try.

---

### Post by markonhismobile on 2008-10-11
I'm having exactly the same issue on a freshly installed 8.04 machine.
LiveCD just looped when trying to login, but as I was getting a graphical display I assumed it just might need updating!
Installed it alongside XP (it's for the sis-in-law!) and after install I have this issue.
The PC in question does have the Radeon Xpress on-board graphics, confirmed via lspci.
All updates have been installed from the failsafe session. Judging from the (lack of) activity on the bug report filed for this issue I'm guessing my best bet is to advise her to use XP for the time being until Intreprid is released and I can do a dist-update for her!

---

### Post by tarps87 on 2008-10-13
You can try ctrl+alt+f1 then login and type ```
Sudo cp /etc/X11/xorg.confg /etc/X11/xorg.confg.bck
Sudo vim /etc/X11/xorg.confg
```This will make a copy of your xorg configuration file and open it in vim. Then find the line ```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

```
change it to ```
Section "Device"
	Identifier	"Configured Video Device"
	Driver "vesa"
EndSection
```
i to start typing, then esc and
:wq to save and exit
If this doesn't help you can do ```
Sudo mv /etc/X11/xorg.confg.bck /etc/X11/xorg.confg
``` to undo the changes

---

### Post by JumpForJoy on 2009-03-03
Ok guys.  I figured that I would bump this thread back to life because I have discovered a solution :o.  I discovered this solution by giving up actually.  I decided to end my life with ubuntu, due to this problem.  Me, being foolish and unknowing, I put in my gpart live cd and selected Ubuntu then clicked delete.  Thinking that my problem was solved, I rebooted my computer when (ahhh) grub had failed me...  Grub couldn't redirect me to my windows partition due to the fact that my Ubuntu partition had been deleted.  So then I decided that I could either reinstall windows or I could reinstall Ubuntu.  Since I had many important files on windows, I went with reinstalling Ubuntu.  After that I searched for my Ubuntu installation cd, alas I couldn't find it...  I then was forced to install the new version of Ubuntu(the one after hardy) that I downloaded from another computer onto my computer to fix grub.  After I installed Ubuntu miraculously it worked fine, even with my graphic card.:popcorn:

So what I draw from this...
If you have this problem, reinstall the latest version of Ubuntu on to your machine after deleting your old partition of Ubuntu.  And now... you can log in.

You guys don't have any rules about major bumps do you?
Any questions?

---

### Post by SHRIKEE on 2009-03-03
And you tried this on various machines, numerous times? I bet you just had a lucky hit... Since it's a driver/compatibility issue, if you have removed the partition your driver is gone too. So the sollution would simply be "upgrade to the latest ubuntu version". and not "delete your partition and reinstall the latest version".

Anyway, i havea  mac mini now, which just works. According to the apple saying. And it does. So no more linux for me... yay!

---

### Post by thiha on 2011-04-20
I just ran into the same problem after upgrading from 10.04 to 10.10.  Can log in using the failsafe mode but not in the regular mode.  I was using ATI driver.  The problem was solved by not using the ATI driver.  
Not to use ATI driver:

Login as root using the failsafe session then System->Administration->Additional Drivers

From there I removed ATI/AMD driver, and rebooted the machine.  After that I was able to log in.

---

### Post by WFPokorny on 2011-06-04
Hello everyone, 
On upgrade to 10.04, I found my old gnome failsafe login for this problem no longer worked. I had to dig into the issue and for me it turned out I had a long ago created a ~/.profile file. A file of this name appears to confuse compiz on start up which causes downstream problems. 

If you cannot login after an upgrade and you think you might have a ~/.profile file, hit the esc key when the grub option prompt appears during boot. Select a recovery option and when the recovery menu appears, drop into a root prompt (it was the last of the menu selections on my recovery screen). 

As root : 

cd /home/<your user account> 
mv .profile OldDotProfile
shutdown -r now 

Hopefully of some help. 
Regards, William Pokorny

---


---
title: "Preventing screen locking when playing full screen videos"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by joetait on 2012-02-25
Hi

Is there a way to permanently prevent the screen from locking (slowly fading before going black) when watching something full screen, and only then (ie it will still lock after ten minutes or whenever unless I am watching something full screen).

If this is application specific then just firefox and vlc (or any other mainstream video player) solutions would be great.

And if the desktop environment somehow affects this then I am using Gnome 3.

Thanks in advance :)

---

### Post by d4m1r on 2012-02-25
I am wondering this as well...if I am playing a fullscreen video in VLC, it doesn't do it but if I am playing a full screen video on Hulu.com (within Firefox) my screen starts to fade after a while and then locks.

Anyone know how to fix that? :(

---

### Post by enjoijesus94 on 2012-02-25
easy just go to power options within 
System > Prefrences > Power Managment.

select your options there.

---

### Post by HeroOfCanton on 2012-02-25
I've got the same problem. Never did find a solution (other than increasing the time before screen shutdown).

---

### Post by d4m1r on 2012-02-25
> **enjoijesus94 said:**
> easy just go to power options within 
System > Prefrences > Power Managment.

select your options there.


Here's what that window looks like for me (called just "Power" in 11.10):

[IMG]http://i.imgur.com/lYXYb.png[/IMG]


](*,)

---

### Post by enjoijesus94 on 2012-02-25
hmmm never seen this before.
So you have got it disabled put it still goes black huh?

---

### Post by HeroOfCanton on 2012-02-25
Look for "screen" under system settings. If it's a lappy you can right click on the battery icon and then Preferences.

---

### Post by d4m1r on 2012-02-26
> **HeroOfCanton said:**
> Look for "screen" under system settings. If it's a lappy you can right click on the battery icon and then Preferences.

Its not a laptop but "Screen" is the application I was looking for (it's set to lock after 30min). However, VLC bypasses this somehow when playing videos fullscreen and I don't want to change this universal value...I just want Firefox to bypass the 30min limit as well when I am playing full screen videos on Hulu for example :(

---

### Post by jonoei97 on 2012-02-26
You could try Caffeine.

[https://launchpad.net/~caffeine-developers/+archive/ppa]("https://launchpad.net/~caffeine-developers/+archive/ppa")

It can automatically and temporarily prevent your screen from locking when a certain application is running. You can specify all these options. :)

---

### Post by joetait on 2012-02-26
> **jonoei97 said:**
> You could try Caffeine.

[https://launchpad.net/~caffeine-developers/+archive/ppa]("https://launchpad.net/%7Ecaffeine-developers/+archive/ppa")

It can automatically and temporarily prevent your screen from locking when a certain application is running. You can specify all these options. :)

That worked well as it has the flash option, thank you very much. I will leave it unsolved for a bit longer to see if there is a definitive answer as to whether or not one can do this for any application, but thanks again :)

---

### Post by d4m1r on 2012-02-29
> **jonoei97 said:**
> You could try Caffeine.

[https://launchpad.net/~caffeine-developers/+archive/ppa]("https://launchpad.net/%7Ecaffeine-developers/+archive/ppa")

It can automatically and temporarily prevent your screen from locking when a certain application is running. You can specify all these options. :)

Caffeine does NOT work properly, in 11.10 at least. I set it to automatically start when the process "firefox" starts and it even detects the firefox icon, but when I start firefox it doesn't...I don't want to set another process to start when I boot because I only need this feature occasionally and full screen flash videos never make my Windows 7 go to sleep....Only Ubuntu ](*,)

Maybe something missing in the linux version of Firefox?

---

### Post by Bobhuber on 2012-02-29
Add this to your xorg.conf file

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
    Option         "BlankTime" "0"
    Option         "StandbyTime" "0"
    Option         "SuspendTime" "0"
    Option         "OffTime" "0"
    Option         "NoPM" "True"
EndSection

---

### Post by d4m1r on 2012-02-29
> **Bobhuber said:**
> Add this to your xorg.conf file

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
    Option         "BlankTime" "0"
    Option         "StandbyTime" "0"
    Option         "SuspendTime" "0"
    Option         "OffTime" "0"
    Option         "NoPM" "True"
EndSection

Mind explaining what this does exactly? From what I can tell, it would set that universally for my PC? Everything is currently working for me EXCEPT for playing flash videos within Firefox, which puts my PC to sleep when it shouldn't...That's why I am thinking it is a Firefox under Ubuntu issue (same version under Windows 7 works fine) and NOT a more general Ubuntu issue.

---

### Post by Bobhuber on 2012-02-29
> **d4m1r said:**
> Mind explaining what this does exactly? From what I can tell, it would set that universally for my PC? Everything is currently working for me EXCEPT for playing flash videos within Firefox, which puts my PC to sleep when it shouldn't...That's why I am thinking it is a Firefox under Ubuntu issue (same version under Windows 7 works fine) and NOT a more general Ubuntu issue.
  It is a universal setting for Ubuntu and has nothing to do with Windows. It's not a Firefox issue but  Ubuntu and Nvidia as far as I have been able to tell. The only way I have been able to keep the computer from taking a nap due to inactivity (and I'm going back as far as Ubuntu 9.04) is to set it up in the xorg.conf no matter what I have set up in power management. In re-reading the original post it's not what the OP wanted because he wanted sleep other than full screen. I also have my box setup as a server along with the desktop which may or may not make a difference.

---

### Post by d4m1r on 2012-02-29
> **Bobhuber said:**
> It is a universal setting for Ubuntu and has nothing to do with Windows. It's not a Firefox issue but  Ubuntu and Nvidia as far as I have been able to tell. The only way I have been able to keep the computer from taking a nap due to inactivity (and I'm going back as far as Ubuntu 9.04) is to set it up in the xorg.conf no matter what I have set up in power management. In re-reading the original post it's not what the OP wanted because he wanted sleep other than full screen. I also have my box setup as a server along with the desktop which may or may not make a difference.


For me, my PC doesn't sleep in all other cases....Ex: playing a full screen video in VLC doesn't put it to sleep, but playing a full screen flash video from Firefox does. That's why I think it is a Firefox issue, NOT Ubuntu.

---

### Post by S2UIRR3L on 2012-03-01
I'm wondering if it's your screen saver settings?

Main Menu > System > Preferences > Screen Saver

---

### Post by joetait on 2012-03-01
> **S2UIRR3L said:**
> I'm wondering if it's your screen saver settings?



I can't access such a menu in gnome 3 - is this available via gconf?

---

### Post by d4m1r on 2012-03-01
> **S2UIRR3L said:**
> I'm wondering if it's your screen saver settings?

Main Menu > System > Preferences > Screen Saver

No such screen in 11.10 :-(

The only related screensaver/idle/lock application in settings available in 11.10 is called "Screen" and looks like this:

[IMG]http://i.imgur.com/Mzzh4.png[/IMG]

---

### Post by S2UIRR3L on 2012-03-03
I'm so sorry... I'm some what of a newbie to Linux and Ubuntu.
I failed to mention that I'm using Lucid Lynx 10.04 LTS (64-bit).

But still, I'd make sure that you have all your settings in all your
programs tweaked so that screen saver (or power settings) are
disabled (or set to presentation so that the monitor stays on).

This is what I did on my computer. I have set it so that it never
goes into screen saver mode or shuts off the monitor/hard drive.
The only way it will ever go to sleep is if I push the power button.

I'm very sorry that I couldn't help, but I do wish you the best!!!

---

### Post by Jackalux on 2012-03-21
Also having this problem.  Note that original post states this is ONLY to do with watching Flash movies in full screen mode.  Otherwise we don't want to have to change universal settings.  I suspect an issue with Ubuntu implementation of Flash or Firefox, whereby they don't restrain the screen dimming/locking facility, as VLC does.

Cheers to anyone who can help,
J

---

### Post by d4m1r on 2012-03-21
> **Jackalux said:**
> Also having this problem.  Note that original post states this is ONLY to do with watching Flash movies in full screen mode.  Otherwise we don't want to have to change universal settings.  I suspect an issue with Ubuntu implementation of Flash or Firefox, whereby they don't restrain the screen dimming/locking facility, as VLC does.

Cheers to anyone who can help,
J

That's exactly the issue, as I've described it above. However, I've yet to find a solution even after installing Firefox 11 :(

---


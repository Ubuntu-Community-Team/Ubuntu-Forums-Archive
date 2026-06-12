---
title: "Frustration"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by beech2000 on 2008-05-03
Hi All,

Normal boot, normal login then white screen with no response or locked up. Please Help!

Thanks Kevin

---

### Post by halitech on 2008-05-03
incorrect video driver or resolution? heat issues? 

which version of Ubuntu did you install?

---

### Post by beech2000 on 2008-05-03
> **halitech said:**
> incorrect video driver or resolution? heat issues? 

which version of Ubuntu did you install?

Hardy,

Gustsy worked fine.

Thanks


Here cut and paste from another no response thread.

just completed fresh hardy install and all went fine. Very first boot was normal login followed by white screen and stop or freezing. Not total lockup but close. (Still see HD light blinking now and again.)

The first install was clean install with empty partition and same thing. Normal login then screen goes white.

The most recent install is where I reformatted the partition clean again and installed Gutsy and and then last night upgraded to Hardy through update manager. Same thing in both scenarios and that is "Gnome freezes" right after login.

Whats so different between Gutsy and Hardy?

Also strange is the live CD works perfect.

Box is:
Lenovo thinkpad T60 with Intel 945GM express video.
2 gig mem
100 GM HD partitioned 50% with 8.04 the other half with XP Pro
Wireless LAN is Intel
Wired LAN is also Intel I believe.

Anyway Help... I miss my Ubuntu please help.

---

### Post by halitech on 2008-05-03
did it give any errors when you were doing the upgrade? what video card do you have and were you using the restricted drivers?

---

### Post by beech2000 on 2008-05-03
> **halitech said:**
> did it give any errors when you were doing the upgrade? what video card do you have and were you using the restricted drivers?

Nope,

Both clean install of hardy and upgraded version have same results. No Video restricted driver use only network card is using an restricted driver. How do I change the video driver with no boot?

---

### Post by halitech on 2008-05-03
try booting to CLI and running

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by beech2000 on 2008-05-03
> **halitech said:**
> try booting to CLI and running

```
sudo dpkg-reconfigure xserver-xorg
```

CLI?

---

### Post by beech2000 on 2008-05-03
> **beech2000 said:**
> CLI?

Not sure what you mean by boot to CLI.

---

### Post by halitech on 2008-05-03
CLI would be the command line with no graphics. I think when you boot you should have an option of command line only or it might be called safe mode.

---

### Post by GavinZac on 2008-05-03
> **beech2000 said:**
> Not sure what you mean by boot to CLI.

Command Line Interface.

Press Ctrl+Alt+F2 to take you to your second screen, which is a CLI.

---

### Post by halitech on 2008-05-03
if he's having trouble logging in, would that still work?

---

### Post by beech2000 on 2008-05-03
OK Once I am in X server what would you suggest I do at that point? 

Many thanks for your help.

---

### Post by beech2000 on 2008-05-03
> **halitech said:**
> if he's having trouble logging in, would that still work?

No trouble logging in at all. Thats whats strange.

GUI at login just turns white at password completion or next screen.

---

### Post by beech2000 on 2008-05-03
> **beech2000 said:**
> No trouble logging in at all. Thats whats strange.

GUI at login just turns white at password completion or next screen.

I think the problem is with Gnome in Hardy more than a video problem but only using Ubuntu now for about a year so not sure of behind the scenes of Linux.

---

### Post by beech2000 on 2008-05-03
push

---

### Post by halitech on 2008-05-03
if you can get into the command line you could always try to install KDE and see if your theory is correct

---

### Post by beech2000 on 2008-05-03
> **halitech said:**
> if you can get into the command line you could always try to install KDE and see if your theory is correct

Thanks 

Will KDE be recognized in command line? or will Live CD access be unnecessary?

K

---

### Post by Wim Sturkenboom on 2008-05-03
> **beech2000 said:**
> pushWhy? You did not give feedback on the suggested solution in post #7 (reconfigure)

---

### Post by halitech on 2008-05-03
would be 
```
sudo apt-get install kubuntu-desktop
```

from a command line but I think you should try to reconfigure the xserver first because all the desktops use the same basic info

---

### Post by CREEPING DEATH on 2008-05-03
> **halitech said:**
> try booting to CLI and running

```
sudo dpkg-reconfigure xserver-xorg
```

IIRC that command doesn't do much with the new(er) X.

CD

---

### Post by halitech on 2008-05-03
could have sworn that was the command I used last night when I changed monitors but I'm also still in gutsy so maybe it doesn't work in Hardy

---

### Post by beech2000 on 2008-05-03
While in X Server noticed it seemed to be more interested in my keyboard layout then video. Not sure what was supposed to do in X service config. Also it was very dos like interface. Still have same white screen problem.

---

### Post by beech2000 on 2008-05-03
> **halitech said:**
> could have sworn that was the command I used last night when I changed monitors but I'm also still in gutsy so maybe it doesn't work in Hardy

Not sure what you mean. I ran X Server at command prompt again. Still not sure what I am supposed to do in X server. I did make sure English language and US keyboard but not sure what else I needs to be done in there.

Please elaborate. Thanks

---

### Post by beech2000 on 2008-05-03
> **halitech said:**
> if you can get into the command line you could always try to install KDE and see if your theory is correct

How do I install KDE from command prompt?

---

### Post by raydeen on 2008-05-03
> **beech2000 said:**
> How do I install KDE from command prompt?

```
 sudo apt-get update

 sudo apt-get install kubuntu-desktop 
```

I've done this in the past when Gnome took a dive due to video driver issues. You'll at least be able to get into a GUI and get some work done or more easily fix your problems.

---

### Post by beech2000 on 2008-05-03
> **raydeen said:**
> ```
 sudo apt-get update

 sudo apt-get install kubuntu-desktop 
```

I've done this in the past when Gnome took a dive due to video driver issues. You'll at least be able to get into a GUI and get some work done or more easily fix your problems.

GREAT! Going to try this now and THANKS!!!

---

### Post by beech2000 on 2008-05-03
> **raydeen said:**
> ```
 sudo apt-get update

 sudo apt-get install kubuntu-desktop 
```

I've done this in the past when Gnome took a dive due to video driver issues. You'll at least be able to get into a GUI and get some work done or more easily fix your problems.

I get errors in command line when sude apt-get update and sudo apt-get install kubuntu-desktop.

Failed to fetch [http://???](http://???)
and Could not resolve errors

One thing I noticed was the fail safe gnome option which makes the screen turn black instead of white.

So confused as to what is so different between gutsy gibbons which worked and Hardy Heron which doesn't. Amazing how tough to fix this has been.

---

### Post by GavinZac on 2008-05-03
Seems like your only option is to try doing that with a Kubuntu cd in your drive. It looks like your CLI doesnt have internet access, which is very strange.

---

### Post by beech2000 on 2008-05-03
> **GavinZac said:**
> Seems like your only option is to try doing that with a Kubuntu cd in your drive. It looks like your CLI doesnt have internet access, which is very strange.

Is Kubuntu cd different then the Ubuntu 8.04 live CD?

Thought no internet access was problem. Wired connection too.

Also strange is why the Hardy live CD does allow boot to normal gnome.

Thanks for your help

---

### Post by GavinZac on 2008-05-03
Yeah there's a different CD for Kubuntu. 

If the problem goes away with the LiveCD, i wonder is there a way to 'export' the LiveCD's XOrg settings and use them with your normal installation?

---

### Post by beech2000 on 2008-05-03
I guess as a last chance question to downloading another 700mb file of another option available?

Another question is what is different as to why the Hardy live CD works and Hardy gives the white screen when installed?

---

### Post by GavinZac on 2008-05-03
> **beech2000 said:**
> I guess as a last chance question to downloading another 700mb file of another option available?

Another question is what is different as to why the Hardy live CD works and Hardy gives the white screen when installed?

Presumably when installing it decided to give you what it thought were good specific settings for your system rather than the default from the LiveCD. Thats why I suggested there might be some way of using the settings the LiveCD does.

---

### Post by beech2000 on 2008-05-03
> **GavinZac said:**
> Presumably when installing it decided to give you what it thought were good specific settings for your system rather than the default from the LiveCD. Thats why I suggested there might be some way of using the settings the LiveCD does.

Exporting settings one by one from live CD might at least help me figure out where to start. wonder if this could be realistically performed.

---

### Post by GavinZac on 2008-05-03
> **beech2000 said:**
> Exporting settings one by one from live CD might at least help me figure out where to start. wonder if this could be realistically performed.

I've never messed with the settings on the LiveCD before but you could try opening a terminal and entering 

sudo gedit /etc/X11/xorg.conf

which does the job in a normal install.

---

### Post by beech2000 on 2008-05-03
> **GavinZac said:**
> I've never messed with the settings on the LiveCD before but you could try opening a terminal and entering 

sudo gedit /etc/X11/xorg.conf

which does the job in a normal install.

Copy and pasted from live cd terminal.

Do I enter info in same way as retrieved from live cd?

---

### Post by GavinZac on 2008-05-03
> **beech2000 said:**
> Copy and pasted from live cd terminal.

Do I enter info in same way as retrieved from live cd?

when you're using the LiveCD, does the hard drive mount? If so, yes, you can open it from the last command i gave you, then save it to the corresponding location on the mounted drive.

I'm going to use this smiley for the first time as its the first time I'm very interested to see if the solution works :popcorn: :)

---


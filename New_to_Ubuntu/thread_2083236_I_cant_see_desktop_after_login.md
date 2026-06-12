---
title: "I cant see desktop after login"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by aerol36 on 2012-11-11
hi, 
i am new in lubuntu. i installed on my netbook to make my netbook faster. i used wubi to install lubuntu but after it finished its job i rebooted computer.i selected lubuntu after that i selected ubuntu and it asked me login and password . i wrote and after that it showed 4-5 lines . ( i didnt know what was these lines saying).after taht nothing happened. desktop didnt start.what should i do to start?

---

### Post by newb85 on 2012-11-11
Welcome!

Without knowing what those lines say, it's difficult to know what's going wrong.  It could be graphics-card/driver-related.  It could also be Wubi-related.

Someone might come along with real understanding of Wubi and give better advice, but I would suggest downloading the .iso file and creating a Live USB and testing Lubuntu out on your system that way.

To create the Live USB from the .iso in Windows, you'll need to install a program capable of that.  Go to [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) and click on the button that says "Download Universal-USB-Installer-1.9.1.5.exe".

---

### Post by aerol36 on 2012-11-11
thank you, i will try now i am downloading iso file.

---

### Post by aerol36 on 2012-11-12
i tried i booted from usb and installed but nothing happened.windows started. i rebooted again and i choosed try lubuntu without installing and now it is saying:

startin crash report submission daemon.   [ok]
stopping system v runlevel compatibility.   [ok]
starting.   [ok]
starting.   [ok]
stopping

please help:(

---

### Post by Terl on 2012-11-12
What are the specs of the laptop?  It is helpful for us to know this.  If you are not 100% positive at least the make and model would be a start.

Are you booting from a USB or a CD?  It is confusing to me to follow what has happened exactly.  For example your last post seems to say you tried to boot from USB and nothing happened, then in the next sentence it boots but fails.

---

### Post by aerol36 on 2012-11-12
asus eee pc 101ch intel atom 1 gb ram dual core.  now i am checked for errors and it is saying cehck finished:errors found in 1 files

---

### Post by aerol36 on 2012-11-12
i am booting from usb

---

### Post by critin on 2012-11-12
> i used wubi to install lubuntu but after it finished its job i rebooted computer.**i selected lubuntu** **after that i selected ubunt**uHow many OS's do you have on the system?  Do you have Lubuntu and Ubuntu both on Wubi?

> i tried i booted from usb and installed but nothing happenedYou installed **another** copy of Lubuntu?

---

### Post by Terl on 2012-11-12
> **aerol36 said:**
> hi, 
i am new in lubuntu. i installed on my netbook to make my netbook faster. i used wubi to install lubuntu but after it finished its job i rebooted computer.i selected lubuntu after that i selected ubuntu and it asked me login and password . i wrote and after that it showed 4-5 lines . ( i didnt know what was these lines saying).after taht nothing happened. desktop didnt start.what should i do to start?

When you installed using Wubi, how did you do that?  Was it from a cd or usb?  Also, if that install is still there can you boot to it now and see what the errors are?  

If you created your own USB where/what instructions did you follow?

---

### Post by aerol36 on 2012-11-12
i used wubi. after i open wubi i choosed lubuntu. it installed but didnt open. when i booted there was 2 choice 1.windows7 2.lubuntu after i choose lubuntu 2 choice came 1. ubuntu 2. ubuntu ...generic...(sonething like that).

wubi installer 
and now there is just one os (windows7)

---

### Post by Terl on 2012-11-12
> **aerol36 said:**
> i used wubi. after i open wubi i choosed lubuntu. it installed but didnt open. when i booted there was 2 choice 1.windows7 2.lubuntu after i choose lubuntu 2 choice came 1. ubuntu 2. ubuntu ...generic...(sonething like that).

wubi installer 
and now there is just one os (windows7)

And what happened after you picked the first choice?

---

### Post by aerol36 on 2012-11-12
login and pass screen came (blackscreen) i wrote username and pass. but nothing happened . I could write something. like start --help, startx. so again nothing happened and i uninstalled . i downloaded iso file. i booted from usb but again after installation nothing happened.

---

### Post by critin on 2012-11-12
I think you should check the condition of your Windows before you do anything more.  See if you can still log in okay.  Unless of course you're planning to install over windows (deleting windows)  anyway.

---

### Post by aerol36 on 2012-11-12
yeah i checked. there is no problem abou windows.it is working normal. i am trying to install lubuntu to inside of windows
i think there is a problem about iso file because when i booted from usb i choosed check disk for errors and it said there is 1 error . but i downloaded this by 2 times with wubi and one time manually but still it iis not working

---

### Post by Terl on 2012-11-12
I agree with Critin, if you want to keep windows and dual boot, you might want to boot into windows just to make sure all is still working.

After you make your USB, do you happen to have another computer available to boot with just to see if the screens come up?

Also, after the download did you check the MD5SUM's and make sure all is well with the downloaded file?

---

### Post by aerol36 on 2012-11-12
ok iwill try on another computer .
what is the md5sum? 

thank you for your help

---

### Post by critin on 2012-11-12
I don't know which version you're trying to get, but apparently wubi exe. won't work well with 12.04 without forcing, and I don't recommend that for a new user.

[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

Try this installer below instead.  Read through the instructions throughly before doing anything.  I would advise 12.04 as a more stable system.

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

> what is the md5sum? 

If you let Wubi download it, it will check this for you.  This makes sure the entire file was downloaded, and not just part of it.

---

### Post by aerol36 on 2012-11-12
i used wubi 2 times:( so it didnt work

thanks..

---

### Post by Tonybarracuda on 2012-11-16
i got the same problem with wubi

---

### Post by newb85 on 2012-11-16
Installing using Wubi gives you a sub-optimal setup.  Many people happily use it and have no problems with it, but it's still sub-optimal.  Its advantage is ease of installation.  If you're having trouble using it, I recommend that instead you use the more traditional approach:

[list=1]
[*] Download the .iso file.  (You probably already have it.)
[*] Create bootable media from the .iso file, either USB or CD (DVD in the case of 12.10).  Note that putting the .iso *on* the media the way you would any other file is not the same.  Instead, follow the instructions on the appropriate link below.
[*] Insert/plug in the bootable media and reboot your machine.  At the initial screen with the computer manufacturer's logo, you will probably have to hit one of the function keys (F2, F12, etc.) or Shift to bring up boot options and select the USB or Optical Drive.
[*] From there, things should be pretty straight-forward.  I recommend you select the "Try Ubuntu" option and do a little test-driving before running the installer.  When you run the installer, make sure that it recognizes Windows and that you're choosing to install alongside Windows.  If that option isn't present (rare, but it happens), come back to the forums for instructions on how to manually partition so that you don't lose Windows in the process.
[/list]

The promised links:
[http://www.ubuntu.com/download/help/burn-a-dvd-on-windows](http://www.ubuntu.com/download/help/burn-a-dvd-on-windows)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
(The DVD link also applies to CDs.)

The traditional install may not look any easier, but if you run into problems, troubleshooting it using the forums is usually a lot easier.  It's the installation method used by most of the really experienced forum participants, so they're more familiar with that setup.

---


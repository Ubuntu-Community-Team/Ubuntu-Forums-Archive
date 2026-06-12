---
title: "Can i have a NOOb guide to making Beryl work"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by dingodave1990 on 2008-05-17
Hey guys im new to Linux and the forums, i downloaded the new ubuntu 8 today and ive been playing around with things and i want beryl to work so i can get exploding windows and things.

i googled beryl and managed to downloaded beryl beryl-core and all the dependencies for it and have installed beryl. i can access beryl settings manager and choose settings but they dont seem to take affect, what am i doing wrong?

ive looked at lots of other threads and well ive been very easily confused with other ways of how to install it and putting in coding into the terminal and rebooting and things, i dont have a clue what they are on about, anyone that could simply guide me through the steps needed to do from where i currently am?

thanks guys :D

dave

---

### Post by sam_delta on 2008-05-17
compiz fusion is installed by default in ubuntu 8.04 and it is in charge of the desktop effects, as far as i know beryl is no longer supported and you should not download anything, if by default, you do not have desktop effects, you need to install the correct video drivers for your video card and then youll have compiz effects

compiz fusion is beryl equivalent now these days

i assume you didnt got desktop effects by default, so, copy the output of the command (go into aplications>accessories>terminal)
```
lspci
```
so we can know your video card model, and help you activate 3d acceleration by installing the correct drivers for your card

sam

---

### Post by SlappyPappy on 2008-05-17
I think this thread will help you out:

[http://ubuntuforums.org/showthread.php?t=796794&highlight=compiz+beryl](http://ubuntuforums.org/showthread.php?t=796794&highlight=compiz+beryl)

Good luck buddy!  :)

---

### Post by dingodave1990 on 2008-05-18
Thanks guys there is only one problem, that post i left late last night i then turned my computer off and now when i try and boot up linux this morning and the loading screen came to Kubuntu in blue whereas befor it was Ubuntu in orange and then from that screen it goes to a screen with some sort of command line saying:

BusyBox V1.1.3(Debain 1:1.1.3-5ubuntu12) Built-in shell (ash)
/enter 'help' for a list of built in commands

(Initramfs)

and i dont know where to go from that :S 

It didnt happen befor when i booted up Ubuntu a few times yesterday.

oh and my card is an Nvidia Geforce 8400GS

and thanks for the replys guys:D



Dave

---

### Post by desheikh on 2008-05-18
Somehow you seem to have installed the Kubuntu desktop as well. 
Are you sent to the terminal after you type in your login info or straight off.

Regarding your original post, Beryl shouldnt be what you are looking at. Beryl was merged with Compiz into what is now knows as Compiz Fusion.
Do you know what graphics card you have? If yours isnt one of the supported cards, your out of luck :(

Regards,
Ali

---

### Post by dingodave1990 on 2008-05-18
yea i jsut realised from reading another post about KDE 3 or 4 that i may have installed it in my curiosity of certain applications and finding out what they do and things.

i cant login it goes straight to that screen straight after the Kubuntu loading screen has finished.

and yea its a Nvidia Geforce 8400GS

thanks,
dave:D

---

### Post by desheikh on 2008-05-18
Ooh bad :P

At the terminal try typing
gdm (thats the gnome desktop manager)

or
startx


Your graphics card is certainly good enough, but youll need to install the nvidia drivers first. I have an ATI, but theres plenty of howto's on the forum explaining it.

Regards,
Ali

---

### Post by dingodave1990 on 2008-05-18
okay, thanks ill try that now and givre feedback, may take a bit im dual booting windows

---

### Post by dingodave1990 on 2008-05-18
Right it didn't work i got frustrated and so i stuck my Ubuntu linux disk in and install Ubuntu again and it works :D 
so what drivers do i need to download and from where? i know about a restricted drivers manager or something sand simply that i have to enable them right?

thanks guys
dave:D

But i had to do it in the safe graphics mode or whatever it was

---

### Post by shifty_powers on 2008-05-18
```
sudo apt-get install envyng-gtk
```

type that in a terminal, then look for it in applicaitons. it will determine yourgraphics card and automatically download and install the right drivers for you ;)

---

### Post by dingodave1990 on 2008-05-18
nice one mate :D

---

### Post by dingodave1990 on 2008-05-18
thanks it work, that was nice and easy :D so now how do i got about this compize fusion and getting windows to explode :D do  i go onto add/remove and just download the app?

thanks,
dave:D

---

### Post by desheikh on 2008-05-18
You already have compiz installed.

Make sure you rebooted after installing the drivers.
System->Preferences->Apearance->Visual Effects.

If you want more options install
compizconfig-settings_manager

then
System->Preferences->Advanced Desktop Effects Settings

---

### Post by bvanaerde on 2008-05-18
Go to:
System > Preferences > Appearance
Then go to "Visual Effects"

edit: desheikh was a bit faster :)

---

### Post by dingodave1990 on 2008-05-18
How do i install/get compiz settings manager?

dave

---

### Post by shifty_powers on 2008-05-18
```
sudo apt-get install compizconfig-settings-manager
```

in a terminal ;)

---

### Post by dingodave1990 on 2008-05-18
is this right, its the code i typed in to terminal to install the manager:

sudo aptitude install compizconfig-settings-manager

thanks,
dave :D

---

### Post by shifty_powers on 2008-05-18
should be fine.

go to system>preferences>advanced desktop effects settings ;)

---


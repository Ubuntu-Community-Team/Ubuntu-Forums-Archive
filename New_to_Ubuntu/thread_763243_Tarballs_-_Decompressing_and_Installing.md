---
title: "Tarballs - Decompressing and Installing?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Shadius on 2008-04-22
I'm new to the whole Linux experience so consider me a noob. What I want to learn to do is how to decompress tarballs and install them.  I'm trying to install Compiz Fusion on Ubuntu but I can't figure out how to use the terminal to decompress the .bz2 tarball. I need help. I've seen what Linux can do and that's why I decided to give it a try but it seems that it's complicated for former Windows users that know nothing of the terminal. Help please! Teach me how to use these tarballs!

---

### Post by Can+~ on 2008-04-22
If you're new, you should don't touch tar.gz's just yet.

Besides, compiz-fusion comes preloaded from ubuntu 7.10 (Gutsy Gibbon) by default, it's on appearence > Visual Effects.

Also, please, instead of looking on google for files, first open "Add/Remove Programs" on the Applications tab, you'll have a pleasant surprise, you can install free software directly from the server, instead of scouting for .exe's in windows.

---

### Post by Tim Sharitt on 2008-04-22
To extract a bz2 tarball
```
tar -xjf file.tar.bz2
```
read the tar man page for all the options and how to extract other compression formats. Once extracted the installation varies from app to app, most will have an "install" file which should get you started. I see you're installing compize, have you tried to install it from the repositories?

---

### Post by cml21 on 2008-04-22
in a more general sense, as you find tarballs that you want to install, try the following:

1. go to command line
2. go to a temp directory, for example, type: cd /tmp
3. grab the package off the interweb, tpye: wget [http://www.website.com/package.tar.gz](http://www.website.com/package.tar.gz)
4. untar it, type: tar -zxvf package.tar.gz (or flag '-xvjf' if untarring X.tar.bz2)
5. move into the created dir, type: cd package
6. configure the package, type: ./configure
7. make the package, type: make
8. install the package, type: make install 

please post again if you have additional questions...

---

### Post by Xiong Chiamiov on 2008-04-22
I don't know about Gnome, but in KDE I just right-click -> extract here, using ark.

---

### Post by Can+~ on 2008-04-22
> **Xiong Chiamiov said:**
> I don't know about Gnome, but in KDE I just right-click -> extract here, using ark.

It's the same thing on gnome (named file-roller though). The thing is that the OP is trying to install compiz-fusion from a compressed file, which is weird, since ubuntu comes with it, and it's on the repository. 

So my guess is that he's under the typical windows philosophy of "go grab it from google", instead of looking up on the local repository.

Instead of teaching him how to uncompress a file and let him screw it up while compiling a source code, let's teach him how to use the best tools of debian, which, at the same time, are more newbie-friendly.

---

### Post by Shadius on 2008-04-22
Thank you. I didn't expect to get a reply so fast from these forums. Okay, I tried doing it from Visual Effects first but the screen just goes to showing the background wallpaper then it reverts back. What does that mean? Does that mean it's applied? Do I need to install Linux drivers for my graphics card?

---

### Post by Shadius on 2008-04-22
OP? Just a quick question, how come you guys are so helpful? I've never gotten such kind of help from users of Windows. I don't know if you guys also use Windows but you guys are amazingly helpful! Thanks to you all!

---

### Post by Can+~ on 2008-04-22
> **Shadius said:**
> Thank you. I didn't expect to get a reply so fast from these forums. Okay, I tried doing it from Visual Effects first but the screen just goes to showing the background wallpaper then it reverts back. What does that mean? Does that mean it's applied? Do I need to install Linux drivers for my graphics card?

Yes, on the restricted drivers section (System > Administration).

Could you run the following command?

```
lspci > ~/Desktop/info.txt
```

This will create a file called info.txt on your desktop with your hardware information, paste it here, for future reference. The most important thing, is an Ati video card or nVidia? Ati cards are troublesome.

---

### Post by Xiong Chiamiov on 2008-04-22
OP == Original Poster

These forums (especially the beginner forum) are very, very high traffic.  All of us here actually *enjoy* using our OS (well, most of the time), and as such, enjoy helping others get to where we are now.  I've only been using Linux since Christmas break, but I found that after I had to go through hell trying to get something to work, I wanted to help others not have to go through the same thing.  And so, I end up here.

---

### Post by Can+~ on 2008-04-22
> **Shadius said:**
> OP? Just a quick question, how come you guys are so helpful? I've never gotten such kind of help from users of Windows. I don't know if you guys also use Windows but you guys are amazingly helpful! Thanks to you all!

It's something like passing knowledge through generations. When you're a newcomer, you'll get a lot of help; 6 months / 1 year later of using ubuntu, you become an experience user and start helping other in the same way you were helped, giving back what you took.

Knowledge is to be distributed, let's keep it that way.

---

### Post by Shadius on 2008-04-22
> **Can+~ said:**
> Yes, on the restricted drivers section (System > Administration).

Could you run the following command?

```
lspci > ~/Desktop/info.txt
```

This will create a file called info.txt on your desktop with your hardware information, paste it here, for future reference. The most important thing, is an Ati video card or nVidia? Ati cards are troublesome.
Here you go. Thank you again. 

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:0b.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
02:0f.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)

---

### Post by Shadius on 2008-04-22
Well, can't thank you guys enough. No wonder everybody likes Linux so much better than Windows.

---

### Post by SunnyRabbiera on 2008-04-22
Its the community, believe me the linux community is amoung the best computer related communities out there.

---

### Post by Can+~ on 2008-04-22
> **Shadius said:**
> Well, can't thank you guys enough. No wonder everybody likes Linux so much better than Windows.

Did compiz-fusion run?
(if needed: [http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA))

If it did, install the compiz fusion advance settings manager for extra eye-candy. 

```
sudo apt-get install compizconfig-settings-manager
```

Good luck.

---

### Post by Shadius on 2008-04-22
So I've heard but never believed it until now.

---

### Post by Shadius on 2008-04-22
Umm...how do I know if it ran or not?

---

### Post by Can+~ on 2008-04-22
> **Shadius said:**
> Umm...how do I know if it ran or not?

If you installed the driver (nvidia one) on the "Restricted drivers", then you must restart to enable it.

It should login with a huge nVidia logo.

---

### Post by Shadius on 2008-04-22
How can I check if it's running?

---

### Post by Shadius on 2008-04-22
Oh okay. Give me a second please.

---

### Post by Shadius on 2008-04-22
Okay. On the restricted device manager, it says that the driver is in use so that means that the driver is installed right?

---

### Post by Can+~ on 2008-04-22
> **Shadius said:**
> Okay. On the restricted device manager, it says that the driver is in use so that means that the driver is installed right?

Yup, now try to go to appearence, visual effects, and try the "Extra effects":

If it works, windows should be "wobbly"
If it doesn't, windows will revert back to normal

---

### Post by Shadius on 2008-04-22
Whoa!!!! It Works! It Works! Thank You, Thank You Soooo Much!

---

### Post by Can+~ on 2008-04-22
> **Shadius said:**
> Whoa!!!! It Works! It Works! Thank You, Thank You Soooo Much!

You were lucky, when I used 7.04 I had to hack the xorg.conf to get it running. Install the extra configuration:

```
sudo apt-get install compizconfig-settings-manager
```

Then you go to appearence, and set it to custom, and you can pretty much set anything you want there.

Great it worked :guitar:

Also, mark your thread as solved.

---

### Post by Shadius on 2008-04-22
Whoa, this looks cooooooooooool!!! Wait, I have a problem. The screen resolution is set to 800x600, when I change it to 1280x1024, I don't see the whole screen, if I move the mouse to the sides of the screen then it moves to show the rest of the screen. That seems weird?

---

### Post by Can+~ on 2008-04-22
> **Shadius said:**
> Whoa, this looks cooooooooooool!!! Wait, I have a problem. The screen resolution is set to 800x600, when I change it to 1280x1024, I don't see the whole screen, if I move the mouse to the sides of the screen then it moves to show the rest of the screen. That seems weird?

Weird? Could you take a picture?

Also, do ["Windows Key" + MouseWheel] to make sure you're not on the zoom plugin effect.

Another possibility: If your screen has "auto-align", use it; my LCD has a little button on the back that auto adjusts the position.

---

### Post by Shadius on 2008-04-22
How do I take a picture? And no, I'm not on the zoom plugin.

---

### Post by Shadius on 2008-04-22
I pressed the auto-align button but nothing changed. Maybe I need to run the disc that came with it on Linux?

---

### Post by Can+~ on 2008-04-22
"Impr Pant", look for "F12", the key on the right of it.

Save it to the desktop, add it as an attachment here.

For the record, there other hotkeys for compiz fusion (and gnome in general):
(Ctrl+Alt)+Right/Left/Up/Down : Switch desktop
Alt+Left_Mouse : Drag window from any position.
Alt+Middle_Mouse : Resize window from any position

---

### Post by Shadius on 2008-04-22
Okay hold on, the window got stuck and started flickering and then I couldn't do anything, I had to restart. Thanks for the hotkey tips. I just discovered my mouse wheel flips the window.:)

---

### Post by Shadius on 2008-04-22
Here are the screen shots. The first one is 800x600 and the other two are 1280x1024.

---

### Post by Shadius on 2008-04-22
Now you see how the two panels show in the screen shot? They show on my screen at 800x600 but not at 1280x1024. I have to move the mouse point downwards to see the other panel.

---

### Post by Shadius on 2008-04-22
Are you still there?

---

### Post by Can+~ on 2008-04-22
I don't know about that issue, and I also use 1280x1024...

Anyway, I'll have to go.

BUT! I noticed something on your desktop, the "ccsm" I told you to download, you're doing it wrong!

do this:
[LIST=1]
[*]Alt+F2
[*]type: gnome-terminal
[*]on the recently opened console (or shell), paste the command: ```
sudo apt-get install compizconfig-settings-manager
```
It will ask for your password, notice that passwords are invisible on the shell.
[*]wait patiently, and it will be downloaded and installed.
[/LIST]

Using the console with apt-get is similar to opening Add/Remove programs. It pulls applications/libraries from an ubuntu server, and installs it automatically, so stop using google for files (unless this are scarce).

You'll have to ask someone else, start another thread with this problem about your screen.

See ya, it's late where I live.

---

### Post by Shadius on 2008-04-22
Oh Okay. Sorry for keeping you up. Thank you so much for helping me. Take care.

---


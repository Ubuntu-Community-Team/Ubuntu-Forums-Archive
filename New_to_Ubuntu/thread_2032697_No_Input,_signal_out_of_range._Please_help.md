---
title: "No Input, signal out of range. Please help"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by robbietea on 2012-07-24
I installed Ubuntu 12.04 from a Usb stick everything went fine.
Ran ubuntu first time got black screen with "no input" message after grub, then I ran ubuntu in safe mode once and it booted fine every time after that.

Then I installed the drivers for my 6870 gpu using amd catalyst now when I load up Ubuntu I get a blank screen saying "no input, signal out of range" and safe mode does not help at all.

---

### Post by QIII on 2012-07-24
How did you install the driver?  From the AMD website?  From the repo?  If from the repo, fglrx or fglrx-updates?

When you installed the ATI driver, did you do 

```
sudo aticonfig --initial
```or, if you have multiple AMD/ATI gpus

```
sudo aticonfig --adapter=all --initial
```?

Do you have hybrid graphics?

Multiple monitors?

---

### Post by robbietea on 2012-07-24
Thank you for the fast reply, I did the same thing I did for windows 7 just before.

went here [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

selected my card and Linux os then just ran the download and amd catalyst wizard came up, so I followed the instructions.

Single monitor, single gpu.

---

### Post by QIII on 2012-07-24
Sometimes, inexplicably, the following three things do not work for some users:

1.  Installing from AMD's website.

2.  Using "Additional drivers" in Ubuntu.

3.  Installing the fglrx-updates versions from the repo.

This is worth a try, but I can't guarantee it will work:

You'll have to enter the recovery mode if you can't see anything on your monitor.

At the menu, first select "Networking" to get your network up and mount the file system read-write.  Then type exit.  When you get back to the menu, select "Root".

Uninstall the driver you just installed.  (If it was from a .deb, you should be able to uninstall in the usual fashion by doing

```
sudo apt-get remove --purge fglrx fglrx-amdcccle
```Then see the ATI driver wiki in my signature and look for the section titled

"Using the Ubuntu repositories (alternate command line method, including hardware acceleration)" 

by clicking on it in the table of contents.  Note that this will install 12.4, not 12.6, since 12.4 is what was frozen in the repo at the 12.04 release.

Let me know if it helps.

There is also a really good set of instructions for installing 12.6 there if you want to try that again as tested on Ubuntu.

---

### Post by robbietea on 2012-07-24
"sudo apt-get remove --purge fglrx fglrx-amdcccle"

got to this step and it returned 
Package fglrx is not installed so not removed 
Package fglrx-amdcccle is not installed so not removed

---

### Post by QIII on 2012-07-24
OK. We'll use the aticonfig utility directly.

```
sudo aticonfig --uninstall
```

---

### Post by robbietea on 2012-07-24
sudo ati config --uninstall 

This worked I could boot into ubuntu normally. Then I installed drivers
**Using the Ubuntu repositories (recommended)**

After restarting this gave me the black screen again with "[B]No Input, signal out of range" 

[/B]I ran "sudo apt-get remove --purge fglrx fglrx-amdcccle"  in safe mode root and now I can login normally again but I have no drivers

---

### Post by QIII on 2012-07-24
OK.

A bit of explanation is in order.

Typically, this is not the PITA that you have run in to.  AMD/ATI and Canonical are nearly in bed together.  Every 4th and 10th month, AMD/ATI makes sure that the xx.4 and xx.10 drivers are available for Canonical to get into their repository even before the driver is available for general release.  Phoronix complains about that just about every time, writing headlines like "Ubuntu gets the candy again!"

So the driver is available in the Canonical repo at release time of that version of Ubuntu.  But it's frozen, so from the repo you can get xx.4 on xx.04 releases of Ubuntu and xx.10 on xx.10 releases of Ubuntu.  The intervening ones have to be installed outside of the repo.  But even that can be tailored for Ubuntu so that it will use a .deb installation and dpkg can keep track of it.  (You'll see that in one of the sections of the wiki.)

When you installed the driver with the wizard, what you go was a generic Linux installation, not an installation as it would have happened if you had used the repo -- that is an apt installation.

We had to use the aticonfig utility to remove it because apt didn't know how to.

That seems to have worked.

Then you used the "Additional Drivers" method, which, as I said, sometimes does not work.  I have no earthly idea why.

Did you do

```
sudo aticonfig --initial
```?

It's not supposed to be necessary with the Additional Drivers method, but I have my doubts.

You might try making sure you do the initial configure after trying that method again.  Your screen may not end up perfect to start with, but you adjust that using CCC.

The next try, as I said, is the section just below the one you tried, the "alternate command line method."

This seems to work nearly all the time, but nothing is ever certain.

Following that section is the "make a .deb" method for the current 12.6 driver.  That will be the next try.

There is also a note in the troubleshooting section that a 6800 series card may require the use of the Gnome Shell rather than Unity.

We'll work down the wiki and see if we can't get this working for you.  

The last option is to just use the open source Radeon driver, which is the default used when you first install Ubuntu.  It has gotten very good in the last year or so and may provide completely satisfactory performance for you.

---

### Post by robbietea on 2012-07-24
"alternate command line method."

Did not work. I am not too attached to unity so I will try gnome. Does gnome classic count? 

I will try the **Using the Ubuntu repositories (recommended)** in gnome.

---

### Post by QIII on 2012-07-24
Yes, try gnome classic.  If you run into the same issue, go back to the open source driver and give me a bit more info about the rest of your hardware, including the monitor.  I'll see if a bit of research turns up anything interesting.

Someone has a question, the wiki doesn't work, I do some research and update the wiki.  Sigh...

---

### Post by robbietea on 2012-07-24
No luck. Thanks a lot for all your help.

Here are my specs

i3 2120[B]
[/B] ASUS P8Z77-V LX
radeon sapphire 6870
8GB DDR3 Kingston (not 100% sure thats the brand) 
Hyundai x90w

---

### Post by wildmanne39 on 2012-07-24
Hi, if you are only getting that message at boot then do:
```
gksudo gedit /etc/default/grub
```
and change this line:

```
#GRUB_GFXMODE=640x480
```

to this:

```
GRUB_GFXMODE=640x480
```

Then save and exit the document.

Then do:
```
sudo update-grub
```
Reboot
Thanks

---

### Post by QIII on 2012-07-24
Thanks wildmanne39.

If that works for him I'll put it in the troubleshooting part of the wiki.

---

### Post by Robitron on 2012-07-28
Hello. Okay, so I am having a similar situation, however, i am not a coder and have never used linux.  I had heard how great linux is compared to windows and my windows is really running slowly now.  So I thought I'd switch to this "easy to install" and "easy to use" OS.  And now, it's been nearly 24 hours since I've had access to anything other than the boot up disk version of ubuntu.  

Everytime I try to start my pc I get Signal out of Range and I can do nothing.  However, before that screen comes up, I do get the option to select my boot up method.  So I choose boot from dvdr and can get to this version of ubuntu but can't change anything.

---

### Post by wildmanne39 on 2012-07-28
Hi Robitron, if you just wait ubuntu should load even though you can not see the screen.

Post 12 is the fix.

Just hit ctrl+alt+t to open the terminal then copy and paste the commands one line at a time in to the terminal and follow the direction in post 12 and it should be fixed.
Proofread carefully.
Thanks

---

### Post by Robitron on 2012-07-28
i left it sitting for over 2 hours last night and it still never loaded.  i think it was waiting for me to decide if i want to load ubuntu or windows.  since i have both on my system.  but with the signal out of range, i can't be sure.  

as for the fix, i read somewhere online about going into the terminal and changing the graphics resolution line so i finally after many many tries, figured out how to actually go in to edit that line (the only way i could find was to delete it out and insert a new line) and then, when did the sudo update-grub) it says it doesn't exist.

---

### Post by wildmanne39 on 2012-07-28
Hi, did you find a way to boot into ubuntu? I had that same issue and I could either wait for ubuntu to load or use the arrow keys to move to the next line and choose which operating system to boot even though I could not see what I was doing.

By default ubuntu should be the first boot choice.
Thanks

---

### Post by Robitron on 2012-07-28
at first, before i did the actual install of ubuntu, i had the option to choose either OS.  but after i came into it and did the actual install, that's when the problem started.  now, i can't get to the OS options.  Also, so I did the 
GRUB_GFXMODE=640x480
portion, but then, when i typed in the sudo update-grub, i got this message:

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

what does that mean?

---

### Post by wildmanne39 on 2012-07-28
Hi, this is what I got when I googled it.
[http://www.google.com/search?q=+%2Fusr%2Fsbin%2Fgrub-probe%3A+error%3A+cannot+find+a+device+for+%2F+%28is+%2Fdev+mounted%3F%29.&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs](http://www.google.com/search?q=+%2Fusr%2Fsbin%2Fgrub-probe%3A+error%3A+cannot+find+a+device+for+%2F+%28is+%2Fdev+mounted%3F%29.&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs)

When you run sudo update-grub are you booted into ubuntu? or is it before ubuntu actually loads?
Thanks

---

### Post by Robitron on 2012-07-28
the only way i can get ubuntu to load is through the dvd.  i can't get to the screen to choose the installed version.

---

### Post by wildmanne39 on 2012-07-28
Hi, that is what I thought and if you are running that command from the cd/dvd that is why it is not working.
Thanks

---


---
title: "NOOB! please help with samsung r40 plus!!!"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by jamie-e89 on 2008-09-08
hi all im really new to this unbuntu stuff, i have a samsung r40 plus laptop with pentium dual core 1.73 cpu 2 gb ram and the onboard grafix is an ati radeon express 1250, at the min im running vista 32bit but i want to give ubuntu a try as i am going to be building a new pc soon. im having trouble booting from live disk as it just sticks on a screen saying the batery state is ok and wont go any further, althought with kubuntu  i have gotten to the console not quite sure whats wrong any help would be appreciated

---

### Post by overdrank on 2008-09-08
> **jamie-e89 said:**
> hi all im really new to this unbuntu stuff, i have a samsung r40 plus laptop with pentium dual core 1.73 cpu 2 gb ram and the onboard grafix is an ati radeon express 1250, at the min im running vista 32bit but i want to give ubuntu a try as i am going to be building a new pc soon. im having trouble booting from live disk as it just sticks on a screen saying the batery state is ok and wont go any further, althought with kubuntu  i have gotten to the console not quite sure whats wrong any help would be appreciated

Hi and welcome, Have you checked the cd for errors?

Moved to ABT :)

---

### Post by jamie-e89 on 2008-09-08
hi yea i have checked it,, just installed it on my lappy, installed fine but i can only get the console, i tried startx but it says no screens found, really conffused lol

---

### Post by jamie-e89 on 2008-09-08
tried to configure with sudo dkpg-configure xserver-xorg
but got no where please help!!!!!

---

### Post by overdrank on 2008-09-08
> **jamie-e89 said:**
> tried to configure with sudo dkpg-configure xserver-xorg
but got no where please help!!!!!

Ok if you can boot into recovery mode which is usually the second choice from the grub. Then use the xfix option to see if this will correct the graphics issue.

---

### Post by thebigfatgeek on 2008-09-08
Jamie

When you get the initial screen after booting, select F6 Other Options, go to the begining of the command line that is opened, and type acpi=off (with a space between off and the next word) and see if you get any further.

See attached screenshots for further clarification (I used xubuntu, but it is the same for the other derivatives)

---

### Post by jamie-e89 on 2008-09-08
lol sorry i have no idea what grub is,,, i tried the acip thing but juist came to a screen that flashed a few times then stuck on it. it said :
starting deferred exucution schedular  (ok)
starting periodic command schedular crond (ok)
checking battery state .....   (ok)
running local boot scripts (/ect/rc/local)   (ok)


i have no idea

---

### Post by jamie-e89 on 2008-09-08
helkp please!!!!!

---

### Post by thebigfatgeek on 2008-09-08
Without access to the same hardware it is difficult to pin the problem down. Have you tried downloading and installing from the alternative CD?

---

### Post by jamie-e89 on 2008-09-09
ok i have ubuntu starting to install, it gets to the terminal, ive tried to do startx , it says its found 1 screen but it is not configured, i have ati radeon xpress 1250 intergrated, i have the driver for this on a flash drive but have no idea how to install it as i am new to this. i would like to know how to install or configure the grafix driver any help is appreciated.

---

### Post by overdrank on 2008-09-09
> **jamie-e89 said:**
> ok i have ubuntu starting to install, it gets to the terminal, ive tried to do startx , it says its found 1 screen but it is not configured, i have ati radeon xpress 1250 intergrated, i have the driver for this on a flash drive but have no idea how to install it as i am new to this. i would like to know how to install or configure the grafix driver any help is appreciated.

Ok if you are just now installing then you may try and use the F4 options at the start and install screen to set your resolution for the install.
If you have Ubuntu installed then boot into recovery mode which is usually the second choice from the grub. The grub booting is when you get to choose the operating system you wish to boot. If you only have Ubuntu on the system then you may have to press esp key when you see grub loading. then you can choose recovery mode and try the xfix option to correct the grpahics.

---

### Post by jamie-e89 on 2008-09-09
ok i willgive it a try, what i did was, installed from windows so that i have a duel boot,installed fine in windows, then rebooted, and all i can get now is the terminal.it wont start the screen, says incorrect config
ive tried sudo dpkg-reconfigure xserve-xorg  , but cant see anything to do with ATI, only the keyboard settings then after about 5 screens it goes back to terminal, is there anything im doing wrong?

---

### Post by overdrank on 2008-09-09
> **jamie-e89 said:**
> ok i willgive it a try, what i did was, installed from windows so that i have a duel boot,installed fine in windows, then rebooted, and all i can get now is the terminal.it wont start the screen, says incorrect config
ive tried sudo dpkg-reconfigure xserve-xorg  , but cant see anything to do with ATI, only the keyboard settings then after about 5 screens it goes back to terminal, is there anything im doing wrong?

It would be hard to say. I am not the familiar with WUBI installation from within windows. The xorg has changed with Hardy and the reconfigure command you are running may not be able to help. Try the xfix option and then post back.

---

### Post by jamie-e89 on 2008-09-09
i will try sorry for all the questions, how doi get to the xfix option?
sorry if it is a really noobish question lol
thanks for the help btw

---

### Post by jamie-e89 on 2008-09-09
just tried to got on the recovery option only it is not there, just safe grafix and scip of option ill keep loking though

---

### Post by thebigfatgeek on 2008-09-09
Any change of posting your xorg.conf here? You could also try to do:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```If your internet connection is working, you could try and install fluxbox or one of the lightweight Windows Managers, and once up and running start fixing your installation.

Should it be possible to get onto the internet, you can try the following:

```
sudo apt-get install x-window-system-core
``` which will reinstall the core xorg components. Once you have doen that install fluxbox to get you started with:

```
sudo apt-get install fluxbox fluxconf
```once you have done that, you can start fluxbox with

```
startfluxbox
```and you should see a simple bar at the bottom, with an empty desktop. If you can get to that point, right-click on the desktop and a simple menu will open up, where you can select to run some of the installed apps.

If you can get there, we have made progress, and will try to install the Gnome desktop thereafter.

---

### Post by applecookie on 2008-09-15
Hi.

I have the same notebook too and tried to get it work with ubuntu for six (!) months. There are several problems in compatibility cases: wlan, ati x1250 graphics card, the samsung bios.

First, the ati card problem can be solved with installing the ati graphics driver (the proprietary one).

But the main problem is: The Samsung R40Plus bios is not a standard bios - samsung wrote me in several mails, that they have modified it and because of this it's NOT LINUX COMPATIBLE!

So I got ubuntu work with it, but it hangs and freezes during startup nearly each time and can be forced to boot full only by pressing strg and alt during the complete booting till seeing the xorg - screen.
The only distribution, which works ok on this notebook is mandriva. I'm sorry to say that, because I really love ubuntu - but the samsung r40plus is not a notebook for working with linux!

You may try it with several kernel version - each of them makes different problems on this pc. The notebook is perfect for xp or vista - but linux...
The ubuntu release, which works best on it, is edgy (no, not a joke, the old releases work better, because they do not realize a "bios bug").

---

### Post by jamie-e89 on 2008-09-15
thank you very much cookie! and thank you to every 1 that has tried to help, sucks that it wont work ,  but im not overly fussed not, i have it on a desk top at home lol only wanted to try it because im building a new computer and wanted to see if it was better than windows thanks all once again!

---

### Post by applecookie on 2008-09-26
An update, if you like to give ubuntu a last try:

Intrepid Ibex runs well on the machine (Samsung R40Plus). I've tried it with the alpha 6 version.

You may need to use the desktop (live) cd to test it. For installing it on your machine you maybe need to give the extra kernel parameters "noapic nolapic acpi=off" for booting. This is only needed till you installed the system.

I have it on my samsung since I installed it yesterday and it runs smooth and fast. Also the stability is ok for an alpha version!

---


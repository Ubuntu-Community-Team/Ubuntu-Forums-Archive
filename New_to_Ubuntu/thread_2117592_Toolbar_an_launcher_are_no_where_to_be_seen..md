---
title: "Toolbar an launcher are no where to be seen."
date: 2013-02-18
forum: New to Ubuntu
---

### Post by dlejeune on 2013-02-18
Hello all, I am really new to Ubuntu, and I am trying to install it on a computer running Windows XP. I downloaded it on a machine running Windows vista and I formatted my flash drive using "LiLi USB creator". I then took it over to the machine running XP and booted up on the USB. It took me over the installation procces and then told me to boot up. When I do that, it takes me to the log on screen. When I log in, I see only this:
[IMG]https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSt6HtQVJ79nWUr7ssjrZYvfyBuWwf5efkUwiSHgwJ-xKLHkNe6xA[/IMG]
with the mouse pointer but no toolbar and laucher. I can move the mouse around AND I can't right click. Then I get an error message telling me that "Compiz has crashed". I don't know what this means but I still tell it to relaunch. Once done that, I can right click but the toolbar and launcher are still not here. Can someone please help?:)  :confused:

---

### Post by Bashing-om on 2013-02-19
dlejeune; Hi ! Welcome to the forum.

Maybe perchance a bad burn ?
As a 1st step; verify the install medium.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

If the medium is verified then I respectfully suggest to remove the ubuntu partition, and (re)install ubuntu.
[INDENT]just my opinion

[/INDENT]

---

### Post by dietfacts on 2013-02-19
I'm having the exact same issue (minus the Compiz error). I don't have any icons, menus or toolbars -- nothing but the background. I realize that I can pull up the terminal using Ctrl+Alt+T but I'm not sure where to go from there. I've reinstalled Ubuntu several times.

---

### Post by grahammechanical on 2013-02-19
Try installing without ticking Install Third Party Software. That way the install process will not install a proprietary video driver. You will get the open source Nouveau driver instead.

I have had installations break because of a buggy proprietary video driver. Once you get to a desktop you can try activating a proprietary video driver if that is your wish. You will find a selection to experiment with in Additional Drivers which you will find in the Dash if your using 12.04 but in System Settings>Software Sources>Additional Drivers tab.

The way to do this with an existing install is to select Recovery Mode at the Grub boot menu. At the next screen select Resume. That will load Ubuntu without activating a video driver.

In 12.04 Recovery Mode is in the list of kernels in the Grub menu but in 12.10 it is in the Advanced Options submenu. I am having to guess which version of Ubuntu you both are using.

Regards.

---

### Post by dietfacts on 2013-02-19
Thanks. I'm running 12.10 under VirtualBox.

---

### Post by dlejeune on 2013-02-19
Thanks so much for replying. I tried verifying my install medium but when I type the commands into the terminal it just gives me error messages. I also didn't install it using the .iso file on a disk but on a flash drive. I have tried numerous methods of installing it:
[LIST]
[*]Wubi downloaded on the computer itself 
[*]Wubi on a flash drive with the .iso file in the same directory
[*]And finally the option of formatting my flash drive and using that as a live disk.
[/LIST]
And after all of those I just get the same result. The reason I don't use disks is because my CD/DVD drive is broken.

[INDENT]Thanks so much again,
Dlejeune :D[/INDENT]
By the way, I don't know if this will help or not but I am using the same .iso file for everything.

---

### Post by Bashing-om on 2013-02-20
dlejeune;

 edit: removed post- display issue not a booting issue:

Lets see if your card  supports unity: Terminal code:
```
/usr/lib/nux/unity_support_test -p <-unity 3d test
```
All responses should be "yes" .

Else: we will research together for a solution.[INDENT][INDENT]still try'n to help

[/INDENT][/INDENT]

---

### Post by dlejeune on 2013-02-21
> **Bashing-om said:**
> dlejeune;

 edit: removed post- display issue not a booting issue:

Lets see if your card  supports unity: Terminal code:
```
/usr/lib/nux/unity_support_test -p <-unity 3d test
```
All responses should be "yes" .

Else: we will research together for a solution.[INDENT][INDENT]still try'n to help

[/INDENT][/INDENT]

Thanks again but I tried and it told me:
```
bash: -unity: No such file or directory

```
I have attached the screenshot below. The screenshot was taken from the computer called
```
daniel-Pad
```
wich is working fine. So I got the same error message on both computers, both running the same os (ubuntu) exept one is broken and the other one is fine. Maby you misspelt the code I needed to enter? Or do I need to write:
```
sudo /usr/lib/nux/unity_support_test -p <-unity 3d test
```instead of just
```
/usr/lib/nux/unity_support_test -p <-unity 3d test
```?
Thanks so much
Dlejeune

---

### Post by bogan on 2013-02-21
Hi!, **dlejeun**e,

The command you want is just: /usr/lib/nux/unity_support_test -p # without the: "<-unity 3d test".

Please Post, as well:```
lspci -nnk | grep -iA3 vga
```This will show both what video card you have and the drivers used and available.

When in the blank desktop Screen in 12 .10, Right Click and select 'Change Desktop Background', then the 'All Settings' Tab,  then the System> Software Sources Icon, and then the Additional Drivers Tab.

Choose which video driver to install and Activate it. Reboot and report how it goes.

Chao!, **bogan.**

---

### Post by Bashing-om on 2013-02-21
Apologize for that ...copy/paste -> haste makes waste ! Thanks bogan (again).....

continue on !

---

### Post by dlejeune on 2013-02-24
Thank you for your replies. Sadly,I can't try it out now as I am on holiday in France and I don't have my computer here with me. But I just want to thank every one, especially Bashing-om and began.

---

### Post by Bashing-om on 2013-02-24
dlejeune;

Enjoy your holiday. We can pick this back up at your leisure. We will be here.

---

### Post by dlejeune on 2013-03-09
> **bogan said:**
> Hi!, **dlejeun**e,

The command you want is just: /usr/lib/nux/unity_support_test -p # without the: "<-unity 3d test".

Please Post, as well:```
lspci -nnk | grep -iA3 vga
```This will show both what video card you have and the drivers used and available.

When in the blank desktop Screen in 12 .10, Right Click and select 'Change Desktop Background', then the 'All Settings' Tab,  then the System> Software Sources Icon, and then the Additional Drivers Tab.

Choose which video driver to install and Activate it. Reboot and report how it goes.

Chao!, **bogan.**

> **Bashing-om said:**
> Apologize for that ...copy/paste -> haste makes waste ! Thanks bogan (again).....

continue on !
Hi Bogan and Bashing-om,

I have put in
```
 /usr/lib/nux/unity_support_test -p #
```
and I got this back:
```
X Error of failed request: BadAlloc (insufficient resources for operation)
Major opcode of failed request: 153 (GLX)
Minor opcode of failed request: 3 (W_GLXCreateContext)
Serial number of failed request: 32
Current serial number in output stream: 33

```
I copied this down by hand but I don't think (and I hope) that there aren't any errors. I also do not have the slightest idea to what this means.

When I typed in this:

```
lspci -nnk | grep -iA3 vga
```

I got this back:

```
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)[INDENT]Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570][/INDENT]
Kernel driver in use: agpgart-intel
00:02.0 [COLOR=#ff0000]VGA [/COLOR]compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)[INDENT=2]Subsystem: Intel Corporation Desktop Board D865GLC [8086:4c43]
Kernel driver in use: i915
Kernel modules: intelfb, i915[/INDENT]

```
Once again I don't really understand much. Also, I can't right click and go to the settings. Actually, now the only thing I can do is open the calculator (Because my keyboard has a button for that) and open the terminal.

Once again thanks so much,
Dlejeune.

---

### Post by Bashing-om on 2013-03-09
dlejeune; Welcome back, Good holiday ?

Regret my error causing such problems, the correct command to see if your card supports unity is:
```
/usr/lib/nux/unity_support_test -p
``` Still need to know that the card and driver support unity.
In answer to your quiry about the "lspci" command, tells us about the card and what driver is in use.
see:```
man lspci
``` for a full description(q to quit the display).
At this time I also want to see that the driver is actually loaded, terminal command:
```
sudo lshw -C display
``` Terninal command ```
man lshw
``` for details.


I am under the impression that the i915 driver is fully compatible in the later versions and should have no problems.
So, the source of the problem is to be determined.[INDENT=2]
try'n to help

[/INDENT]

---

### Post by dlejeune on 2013-03-11
> **Bashing-om said:**
> dlejeune; Welcome back, Good holiday ?

Regret my error causing such problems, the correct command to see if your card supports unity is:
```
/usr/lib/nux/unity_support_test -p
``` Still need to know that the card and driver support unity.
In answer to your quiry about the "lspci" command, tells us about the card and what driver is in use.
see:```
man lspci
``` for a full description(q to quit the display).
At this time I also want to see that the driver is actually loaded, terminal command:
```
sudo lshw -C display
``` Terninal command ```
man lshw
``` for details.


I am under the impression that the i915 driver is fully compatible in the later versions and should have no problems.
So, the source of the problem is to be determined.[INDENT=2]
try'n to help

[/INDENT]


Hi bashing-om,

Thanks, my holiday was fantastic (skiing in the Alpes). But back to machines. I typed in 

```
sudo lshw -C display
```

and it said

```
[sudo]password for owner: 
```

I put it in and then it gave me this (get ready, it's long):

```
*-display[INDENT=2]description: VGA compatible controller
product: 82865G Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:16 memory:f0000000-f7ffffff memory:ffa80000-ffafffff ioport:ec00(size=8)[/INDENT]

```[INDENT=2]

[/INDENT]
That's all that was written. I don't want to sound suspicious, but can you please do a recap (quite simply please) of everything you have asked me to do and what we are trying to find? That would help me a lot (but once again, please do it in a simple way). Thanks a ton!!

For the 1 000 000 000 th time:
Thank you.

Dlejeune

---

### Post by AlecJ on 2013-03-11
It's a known bug with the older intel video cards.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1071530](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1071530)

Looks like a work around here
[URL="http://askubuntu.com/questions/263550/opengl-with-intel-82865g-integrated-graphics"]http://askubuntu.com/questions/263550/opengl-with-intel-82865g-integrated-graphics
[/URL]
Or download 12.04.2 that should work as it using the older Mesa.

---

### Post by Bashing-om on 2013-03-11
dlejeune;
Those commands were only to identify the chipset and graphics driver, and see if the driver is loaded.
Identified;  		AlecJ has isolated the problem and pointed you to a solution.
As I stated earlier, the i915 driver is good on later kernel/hardware, there exist work-a-rounds to maybe get it to work on older hardware/newer kernel.
Do you want to play around with your options ?  		AlecJ's link will get you up on a usable desktop.[INDENT=2]ain't ubuntu wonderful 


[/INDENT]

---

### Post by dlejeune on 2013-03-15
Hi AlecJ and Bashing-om,
Thanks for your awnsers. Yes, I think that I will ty out the option that AlecJ gave to me and I will notify you I it has worked!

And, yes, Ubuntu IS wonderful!

Dlejeune

---

### Post by dlejeune on 2013-03-26
Hello everyone, I am sorry it has taken so long to reply. I have come to the conclusion, after a lot of scratching around, that I have two choices at hand:
[LIST=1]
[*]I have to buy a VGA card (or graphics card) because the machine's one is not good enough.
[*]I can, like AlecJ said, download Ubuntu 12.04.02. The only problem is that how to I do that since I only have terminal commands?
[/LIST]

Thanks so much for all you help. Could someone please tell me how to do option 2)?

Thanks once again,
Dlejeune

---

### Post by Bashing-om on 2013-03-26
dlejeune; I continue to monitor.

Opting for "12.04.2" I like because it is a 5 year Long Term Support. 
To install on your box:
Download the .iso file;
Burn the .iso file as an "image" to a cd disk;
Back up any data from your current install that you desire to keep;
Change in bios the boot preference to boot from the desired device;
Boot up the install CD;
FIRST thing in the installCD boot is to run ubuntu in the "try ubuntu" mode, making sure that all runs good at this time -> then
Choose "install ubuntu" -> Follow the prompts in the install wizard is the simplest install method -wiping the drive and installing only 12.04.2 //

All this is easier done from a GUI // No GUI ??// How are you presently getting onto the forum -> what tools must we develop  to make the above happen(??) is what I am asking  //

Might be possible to start the Xserver (present install) and it will function to the point that FireFox and Brasero will be useabe ? - Do not know, never tried it in a situation like this. But it is worth exploring due to ease of use in the GUI.[INDENT=3]
we can do this

[/INDENT]

---

### Post by dlejeune on 2013-03-26
> **Bashing-om said:**
> dlejeune; I continue to monitor.

Opting for "12.04.2" I like because it is a 5 year Long Term Support. 
To install on your box:
Download the .iso file;
Burn the .iso file as an "image" to a cd disk;
Back up any data from your current install that you desire to keep;
Change in bios the boot preference to boot from the desired device;
Boot up the install CD;
FIRST thing in the installCD boot is to run ubuntu in the "try ubuntu" mode, making sure that all runs good at this time -> then
Choose "install ubuntu" -> Follow the prompts in the install wizard is the simplest install method -wiping the drive and installing only 12.04.2 //

All this is easier done from a GUI // No GUI ??// How are you presently getting onto the forum -> what tools must we develop  to make the above happen(??) is what I am asking  //

Might be possible to start the Xserver (present install) and it will function to the point that FireFox and Brasero will be useabe ? - Do not know, never tried it in a situation like this. But it is worth exploring due to ease of use in the GUI.[INDENT=3]
we can do this

[/INDENT]

Hi Bashing-om, 

I have one problem with the plans you are suggesting: My machine that is broken has a cd-drive that doesn't work. But can I download the Wubi.exe because there is Windows XP still installed on it. So if that would work then could you tell me? 

Thanks a lot,
Dlejeune

P.S.
I am getting onto the forum using my Laptop (running the latest Ubuntu). My laptop is working fine (GUI and all) and I can do anything I want on it. It is from my laptop that I am trying to fix the big computer that is broken.

---

### Post by Bashing-om on 2013-03-27
dlejeune;

Will the broken box support a usb flash drive ? There are many alternative ways to install- even to a complex way directly over the net.
see:[https://help.ubuntu.com/community/I](https://help.ubuntu.com/community/I)
For a list of alternative procedures and documentation on each.[INDENT=3]
hope this helps

[/INDENT]

---

### Post by dlejeune on 2013-03-28
> **Bashing-om said:**
> dlejeune;

Will the broken box support a usb flash drive ? There are many alternative ways to install- even to a complex way directly over the net.
see:[https://help.ubuntu.com/community/I](https://help.ubuntu.com/community/I)
For a list of alternative procedures and documentation on each.[INDENT=3]
hope this helps

[/INDENT]

Hi Bashing-om, 
[U][B][SIZE=5]
[/SIZE][/B][/U]
[CENTER][SIZE=7][U][B]Success !!!
[/B][/U][/SIZE][SIZE=2]
[/SIZE][/CENTER]
[SIZE=2][SIZE=2]We have managed to get it working. It is running perfectly on the machine. 
[/SIZE]
[/SIZE]

[LIST]
[*]I downloded Wubi.exe because I still had Windows xp installed.
[*][SIZE=2]
[/SIZE]
[*][SIZE=5][SIZE=2]Then I downloaded the .iso file and put it on the USB (otherwise it can't find the packages to install)[/SIZE]
[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2]After that, I rebooted the box onto Windows Xp and inserted the Usb.
[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2]I clicked on wubi.exe and followed the instructions.
[/SIZE]
[*][SIZE=2]
[/SIZE]
[*][SIZE=2]When it was installed, I rebooted onto ubuntu and Kaplam! it worked[/SIZE]
[/LIST]
[SIZE=2]
I would like to thank everyone that helped me get to this, especially Bashing-om and AlecJ.

Thanks again, 
Dlejeune

P.S.

Do I have to mark the thread as solved?[/SIZE]

---

### Post by Bashing-om on 2013-03-28
dlejeune;
Outstanding, You do good work. I am very pleased you are up and running with ubuntu on that box. As you are now happy with your solution and closing this thread; Yes, mark this thread as solved.
Interim work-a-round:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
Problem still ? -> graphical instruction: ==>[URL="https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"]https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads

[/URL][INDENT=3]Happily ubuntu'n all
[/INDENT]

---

### Post by dlejeune on 2013-03-31
[CENTER]I would like to thank everyone that helped 
me to, not only get onto a usable desktop, but 
help me understand what the problem was. I would especially
like to thank BASHING - OM for staying with me from the very beginning.
If there was anything I could do to help him, I would (although I probably couldn't).
Anyway, 
[SIZE=7]
Thanks So Much !!

[/SIZE][/CENTER]
[SIZE=7][SIZE=3]Dlejeune[/SIZE]
[/SIZE]

---

### Post by Bashing-om on 2013-03-31
dlejeune;

For your thank you(appreciated)  -> just pass it on !
[INDENT=2]
ubuntu, all for 1 and one for all

[/INDENT]

---


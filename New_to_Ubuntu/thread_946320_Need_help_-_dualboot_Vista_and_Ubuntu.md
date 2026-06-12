---
title: "Need help - dualboot Vista and Ubuntu"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by shewsbury on 2008-10-13
Hi all,

I need help here.

I have a laptop running Windows Vista and now I want to also have Ubuntu 8.04 LTS inside it and be able to dual boot with both OS.

I have read the guide from this website;
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

It seems to be easy to follow.

I have the Ubuntu 8.04 LTS Hardy Heron CD, 1 from internet and 1 I got from Ubuntu with thanks.

Then I put the CD into my machine and reboot it, then the Ubuntu Live CD screen appear, I choose what I need to choose and I stuck in the screen where it shows Ubuntu logo and that progress bar - stop at around 20%

You can see the all screen shots in my blog as below;

[http://shewsbury.blogspot.com/2008/10/need-help-with-dualboot-vista-and-linux.html]("http://shewsbury.blogspot.com/2008/10/need-help-with-dualboot-vista-and-linux.html")

It has to be note here that I have no problem "Running Live CD" and play around with the Ubuntu on my other laptop running Windows XP.

I hope you can share your opinion with me or teach me many things so that someday I can ROCK with the lovely Ubuntu.

Thanks in advance.

John

---

### Post by Orange_and_Green on 2008-10-13
Hello John :) Thank you for your interest in Ubuntu :)

Before hitting "enter" to start up, try hitting "F6" ("Other Options") and deleting the last two words ("splash" and "quiet").

That will give you verbose info about what is failing.

Good luck :)
Please post again and tell us where it gets stuck.

Also, what manufacturer and model is your laptop?

---

### Post by tarps87 on 2008-10-13
Looking at the photos it looks like there is a black square to the left of the bar, this probably means it is 'searching' your hardware and possibly looking for a resume image, try pressing ctrl+alt+f1 as soon as you can (before it freezes) and then can you post what is on the screen.
It could be incompatibly with your hardware or cd drive speed.

---

### Post by shewsbury on 2008-10-14
Hi guys,

Thanks for the fast response...

As stated by Orange_and_Green,

I did so and end up stumble in another screen...

You can see the latest screen shot in my blog as below;

[http://shewsbury.blogspot.com/2008/10/vistaubuntu-dual-boot-problem-part-two.html]("http://shewsbury.blogspot.com/2008/10/vistaubuntu-dual-boot-problem-part-two.html")

And if according to tarps87;

Hit ctrl+alt+f1 as soon as I can before it freeze... done so, still the same... still freeze.. in fact the progress bar move too fast heading to the same spot and it's just stuck

So far this two advice doesn't work but I am not giving up... thanx guys, but it seems that we have to try other alternative, look forward to your continuous support.

I am determined to get Ubuntu, the most beautiful OS outside the money thinking only Windows VISTA...

What's next? anybody...

John
Ubuntu Rock!!!

---

### Post by zxscooby on 2008-10-14
Try adding the boot flags
```
noacpi apic=off
```
.

To do this:
 1. .When loading via the LiveCD, hit F6 for more options to add the parameter above.
 2. When loading on a fresh install, (first load using the LIVECD AFTER you have installed a fresh copy of Ubuntu. Then, go into your filesystem and edit menu.lst to add the parameter permenantly to the boot loader. I think you can do without the 
apic=off after the install, especially if it is a laptop.

---

### Post by WWSmith36 on 2008-10-14
I think there was a launchpad bug report about this problem.  I believe it was was related to the 2.6.24 kernel.

For hardy you can try using some kernel boot options

noapic nolapic acpi=off irqpoll

See if this helps

This might let you boot and install, but will also disable your power management functions, probably suspend and hibernate will not be available.  From what I understand, this was fixed with the 2.6.25 kernel.

When you upgrade from Hardy to Intrepid you will be using the 2.6.27 kernel and will probably be able to regain those functions back.

Hope this helps

---

### Post by rybaxs on 2008-10-14
> **shewsbury said:**
> Hi guys,

Thanks for the fast response...

As stated by Orange_and_Green,

I did so and end up stumble in another screen...

You can see the latest screen shot in my blog as below;

[http://shewsbury.blogspot.com/2008/10/vistaubuntu-dual-boot-problem-part-two.html]("http://shewsbury.blogspot.com/2008/10/vistaubuntu-dual-boot-problem-part-two.html")

And if according to tarps87;

Hit ctrl+alt+f1 as soon as I can before it freeze... done so, still the same... still freeze.. in fact the progress bar move too fast heading to the same spot and it's just stuck

So far this two advice doesn't work but I am not giving up... thanx guys, but it seems that we have to try other alternative, look forward to your continuous support.

I am determined to get Ubuntu, the most beautiful OS outside the money thinking only Windows VISTA...

What's next? anybody...

John
Ubuntu Rock!!!

Try to Install Ubuntu directly..

---

### Post by tarps87 on 2008-10-14
Orange_and_Green suggestion showed the same as what pressing ctrl+alt+f1 should have done, but I forgot about that way. Adding the boot flag noacpi apic=off as described by zxscooby:
> **zxscooby said:**
> Try adding the boot flags
```
noacpi apic=off
```
.

To do this:
 1. .When loading via the LiveCD, hit F6 for more options to add the parameter above.

Should fix it so you can boot from the live cd

---

### Post by shewsbury on 2008-10-14
Dear zxscooby

Thank you very MUCHHHHHHHHHHHHHHHHHHH

And to all the others who have also tried to help me I want to say;

THANK YOU SO MUCHHHHHHHHHHHHHHH

I can now install Ubuntu 8.04 LTS Hardy and a new life begin's now...

A journey to a truly magnificent OS starts now...

So we manage to install it now, probably (though hopefully not) there will be other problem in the future so I will keep on coming here now and then and I will continue to post my new experience with Ubuntu in my blog (shewsbury.blogspot.com)

Next I may need to install the following;

1) Something I use in Windows called Yod'm 3D, I have read about it somewhere, the Linux communities refer to it as "Compiz Effects" - something like that. Can you guys give me the links to download this.

2) Do I need Anti virus software? Is there any free anti virus for this Ubuntu?

I think that is my wish list so far...

Thanks.... I gotta go play around with my new baby now... Yahooooooo

UBUNTU ROCKS!!!!

John

---

### Post by tarps87 on 2008-10-14
1) This is where I gets easy :) Under applications there's an option called 'add programs' This is an easy interface for the synaptic package manager, search for any program and if its in the repository click install. You can also use it from the command line, applications->assecories->terminal then```
sudo apt-get install *packageToInstall*
```e.g.```
sudo apt-get install compiz
```

2) Not really, there are some but they are mainly pick up windows viruses, if you regularly send emails to people on windows machines you can use one to help protect them. But other than that you should be fine.
I have not used one on Linux but do you AVG on a windows pc so you might want to give that a try
[http://free.avg.com/4040](http://free.avg.com/4040)

Some things to remember:
Do not login as root use sudo instead
Do not do ```
sudo rm -rf *
``` this will remove everything on you hard drive.
the command:
sudo = gives you root/ administrator privileges
rm = remove
* = wildcard/ all
Only use sudo when you know what you are doing, if you don't ask the person who suggested it and they'll explain. If they won't then don't trust them

You may want to add the restricted extras:
```
sudo apt-get install ubuntu-restricted-extras
```
This will install support for restricted formats like mp3, these are not included due something to do with copyright reasons.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

About Repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Packages can be downloaded from here but I'd suggest using synaptic:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Orange_and_Green on 2008-10-14
> **shewsbury said:**
> 
1) Something I use in Windows called Yod'm 3D, I have read about it somewhere, the Linux communities refer to it as "Compiz Effects" - something like that. Can you guys give me the links to download this.
2) Do I need Anti virus software? Is there any free anti virus for this Ubuntu?

Hello John, congratulations on your successful install. I have very good news for you:

1) If your video card is detected automatically, then Compiz Effects will be enabled by default. If it's not, then you might want to check under System->Administration->Restricted Drivers if there are drivers available, or post again and we'll help you set up a driver.

Run System->Administration->Synaptic Package Manager, search for "compizconfig-settings-manager" and install it. You  will then be able to customise your compiz settings by going System->Preferences->Advanced Desktop Settings

2)Ubuntu is happily virus and malware free. :)
There is an antivirus program called ClamAV but it's only use is to check any windows partitions against viruses (in double boot configurations).

Have fun with Ubuntu!!

---

### Post by shewsbury on 2008-10-14
Dear friends....

SORRY... but I still need help...

Perhaps I celebrate prematurely and obviously now my joy is short-lived.

Based on the advice from [COLOR="Red"]zxscooby;[/COLOR]

[COLOR="Red"]To do this:
1. .When loading via the LiveCD, hit F6 for more options to add the parameter above.
2. When loading on a fresh install, (first load using the LIVECD AFTER you have installed a fresh copy of Ubuntu. Then, go into your filesystem and edit menu.lst to add the parameter permenantly to the boot loader. I think you can do without the
apic=off after the install, especially if it is a laptop.[/COLOR]

I managed to install the Ubuntu, but I must share the following;

- Flagging OFF "acpi=off" only doesn't work.
- I also need to flag off the "noapic" and then it will works and I can proceed with "Install Ubuntu"

I follow all installation process, everything works well.

Then the computer ask me to remove the CD and press Enter.

The machine then reboot and I can see the Grub boot loader (was so excited)and I choose the first one...

Unfortunately I back to square one... still stuck at that screen with Ubuntu logo and a "stop" progress bar.

Please visit my blog again to see the detailed screen shot;

[http://shewsbury.blogspot.com/2008/10/vistaubuntu-dual-boot-problem-part.html]("http://shewsbury.blogspot.com/2008/10/vistaubuntu-dual-boot-problem-part.html")

I hope when you see all the screen shots there you can at least have some idea about my problem.

I personally feel that I probably have to the the following as advised by zxscooby;

[COLOR="Red"]2. When loading on a fresh install, (first load using the LIVECD AFTER you have installed a fresh copy of Ubuntu. Then, go into your filesystem and edit menu.lst to add the parameter permenantly to the boot loader. I think you can do without the
apic=off after the install, especially if it is a laptop.[/COLOR]

But then I don't quite understand this part.

When he mentioned the following;

[COLOR="Red"]"loading on a fresh install, (first load using the LIVECD AFTER you have installed a fresh copy of Ubuntu"[/COLOR]

Is that mean, after the installation process when my machine reboot, I still need to insert the LiveCD and when the normal menu appear I still need to select "Try Ubuntu without installing it" and after that if I manage to get in, I do the following;
[COLOR="Red"]
"Then, go into your filesystem and edit menu.lst to add the parameter permenantly to the boot loader."[/COLOR]

Look forward to all your help and advise again.... and sorry for celebrating prematurely...

I was too excited... and maybe naive...

Thanks

---

### Post by Orange_and_Green on 2008-10-14
Hello my friend. I am sorry to hear you are having these problems. Please don't give up yet, this is one of the (nowadays rather infrequent, but occasionally happening) hardware incompatibilities, which however can be worked around. You _will_ end up with a working system, that's a promise. :KS

> **shewsbury said:**
> Dear friends....The machine then reboot and I can see the Grub boot loader (was so excited)and I choose the first one...


Highlight the first entry, then press 'e' (not enter). This will let you edit the startup options. Choose the second line (the one that starts with "kernel"), press 'e' again. Add "acpi=off noapic" to the line as you did at install time. Then, press enter, then 'b' to boot.

If this works, please post again and I'll explain how to make this change permanent.

Good luck:KS

---

### Post by zxscooby on 2008-10-14
You have to make the boot flags permanent by editing 
menu.lst. A configuration file for the boot loader.
Sorry, I should have elaborated more on that.  
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu](http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu)

---

### Post by shewsbury on 2008-10-14
Based on the advice from Orange_and_Green,

Highlight the first entry, then press 'e' (not enter). This will let you edit the startup options. Choose the second line (the one that starts with "kernel"), press 'e' again. Add "acpi=off noapic" to the line as you did at install time. Then, press enter, then 'b' to boot.

Yes, I managed to finally see the beautiful chocolate color Ubuntu desktop... basically it works... thanx

So maybe now you have to teach me how to make it permanent...

As usual I have posted the screen shot in my blog;

[http://shewsbury.blogspot.com/2008/10/vistaubuntu-dual-boot-problem-part-four.html]("http://shewsbury.blogspot.com/2008/10/vistaubuntu-dual-boot-problem-part-four.html")

Or maybe it is something related with the advise from zxscooby,

You have to make the boot flags permanent by editing
menu.lst. A configuration file for the boot loader.
Sorry, I should have elaborated more on that.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://users.bigpond.net.au/hermanzo..._the_GRUB_Menu](http://users.bigpond.net.au/hermanzo..._the_GRUB_Menu)

I will try to also visit all those links given by zxscooby.

Another thing is that I notice the following;

1) Ubuntu  does not detect my USB optical mouse (very important for me as I dont like to use the laptop touchpad)

2) How to set up my WiFi internet connection? I believe I need this to get all the update and additional software or packages right?

I have check under the menu SYSTEM > ADMINISTRATION > NETWORK and also NETWORK TOOL but I cannot see anything about WiFi

3) My screen resolution is only 800 x 600 - is this normal for Ubuntu ?

Other than this, everything is OK so far, I tried the OPen Office applications it works perfectly. I tried the games, it's fun but we need to get connected to internet now...

Look forward to your next advise.

Thanks for your support

---

### Post by shewsbury on 2008-10-14
Dear zxscooby

When I read the articles in the link you gave me,

[http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu")

And I can see there he instruct to do something like this;

vga=ask

I think I will still need to read it again for the second time to really understand that part

At the moment maybe I will wait for further instructions from Orange_and_Green to make the changes permanent.

Hopefully it will works, if not, then maybe I have to try whatever I read from the articles (the link you gave me).

1 step after another... I am positive now that we can get over this slowly but surely.

Thanks

John

UBUNTU ROCK!!!

---

### Post by shewsbury on 2008-10-14
By the way, I don't know if this information is helpful

In Windows Vista, my resolution is = 1280 X 800 pixels (32 bit)

My video adapter is = SIS 307ELV

Is there anything to do with this ?

To see the detailed spec of my laptop;

[http://www.truenote.biz/productdetails/fu420.html]("http://www.truenote.biz/productdetails/fu420.html")

---

### Post by zxscooby on 2008-10-15
To make the changes permanent you will need to edit 
menu.lst
in terminal type

```
sudo nano /boot/grub/menu.lst
```
it will ask for you password

make a backup copy by pressing ctrl-o and renaming the file
menu.lstbackup or something. 

scroll down to the section that lists your kernels
it should look similar to this.
```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=428c458c-8ddc-4016-8e33-7d012db4c386 ro quiet splash noapic acpi_osi=!Linux
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=428c458c-8ddc-4016-8e33-7d012db4c386 ro single
initrd          /boot/initrd.img-2.6.22-15-generic


```

You can see above where i have added the noapic flag to the kernel line.  I would try not to use the acpi=off flag because 
you are using a laptop and that has to do with the power management. 
 
Save the file as menu.lst and exit.

For more information on the subject look here.
[http://www.rigacci.org/wiki/doku.php/doc/appunti/linux/sa/irq_acpi_apic](http://www.rigacci.org/wiki/doku.php/doc/appunti/linux/sa/irq_acpi_apic)
[http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html)

---

### Post by Orange_and_Green on 2008-10-15
Hello John,

I am glad you are making progress :) I am very happy you still think Ubuntu rocks, despite your first time at it has been made so hard by your hardware problems...

As for your questions:

+1 for zxscooby's suggestion. Click on Applications->Accessories->Terminal, this will bring up a text console where you can type in commands. Please type:
```
gksu gedit /boot/grub/menu.lst
```

Scroll down till the bottom of the text and add the famous "acpi=off noapic" magic words to the end of all the lines that start with "kernel". I agree with zxscooby that you might try just adding "noapic" and leave the acpi bit away and see if it works, but it's not guaranteed.

1)Please post the output of the command
```
lsusb
```so we can see if the mouse is being detected.

2)Please make sure the hardware switch for the wifi is on if your laptop has one, then post the output of the command
```
sudo lshw -C network
```

3)Go to System->Preferences->Screen Resolution and check if you can change resolution to a higher one. If you can't, please go to System->Administration->Restricted Drivers and check if there is a driver to enable. If this fails too, please post again and we'll discuss plan B...

I wish you the best of luck and (when this is all finished) tons of fun with Ubuntu :)

---

### Post by tarps87 on 2008-10-15
> **shewsbury said:**
> 
1) Ubuntu  does not detect my USB optical mouse (very important for me as I dont like to use the laptop touchpad)

2) How to set up my WiFi internet connection? I believe I need this to get all the update and additional software or packages right?

I have check under the menu SYSTEM > ADMINISTRATION > NETWORK and also NETWORK TOOL but I cannot see anything about WiFi

3) My screen resolution is only 800 x 600 - is this normal for Ubuntu ?


2) Can you post the output of ```
ifconfig
```
```
sudo lshw -businfo
```Edit: Try this if ```
sudo lshw -C network
``` that Orange_and_Green suggested doesn't work

3) Try looking it system->preferences->screen resolution and see if you can change it there. You may need to run the command```
sudo dpkg-reconfigure xserver-xorg
``` this will reconfigure your xorg file which contains the settings of input and output devices like you monitor. (This has changed in Ubuntu 8.10 Ibex though)

---

### Post by shewsbury on 2008-10-15
I use the command from zxscooby

sudo nano /boot/grub/menu.lst

It works till the part Ubuntu ask me for the password and any keystrokes from my keyboard doesn't seems to work... (in other word, whatever I type doesn't appear and when I press enter it say's that's wrong... something like that

So I skip

Then I use the command from Orange_and_Green

gksu gedit /boot/grub/menu.lst

It works, a new window appear asking me to key in my password

As soon as I press Enter..

The Menu.1st appear (it's a text file) - BUT IT'S BLANK / EMPTY

Nothing is there, just a plain white background, I waited for 20 minutes (as always) and nothing happen, so I just close the file without saving it.

The command to detect the USB mouse = lsusb

Also doesn't work - no changes, still can't use the USB Mouse

The command to detect the Network = sudo lshw -C network

Ubuntu ask me for the password but any keystrokes from my keyboard doesn't seems to work...

The command provided by tarps87

ifconfig

It works, I mean some notification appear, though I dont understand what is it, something like this;

eth0 Link encap: Ethernet HWaddr 00:03:od:92:40:ec

and many more...

Next the following command = sudo lshw -businfo

Ubuntu ask me for the password and any keystrokes from my keyboard doesn't seems to work... (in other word, whatever I type doesn't appear and when I press enter it say's that's wrong... something like that


>>>> So what's next ?

Thanks for all your support

Yeah... Ubuntu Rock!!! it's been a long time since I have to learn so many things like now... though I'm getting old.. it's fun to learn....

---

### Post by Orange_and_Green on 2008-10-15
Hi, welcome back!


> **shewsbury said:**
> gksu gedit /boot/grub/menu.lst__________________________________^
__________________________________|
This is a lowercase letter "L", not the digit "one".

If it helps, you can hit the "TAB" key to have the shell hint you on partially entered commands and filenames (for example, try "gksu gedit /bo[TAB]/gr[TAB]/me[TAB]")

Be sure to type everything in lowercase.


> **shewsbury said:**
> The command to detect the USB mouse = lsusb

Could you please copy and paste the RESPONSE you get from the command please? This command lists all devices connected to the USB bus, I wanted to know if the mouse is listed there or not...

> **shewsbury said:**
> Ubuntu ask me for the password but any keystrokes from my keyboard doesn't seems to work...

That's normal. Just type the password blindly and press enter. This is a feature for extra security, so that no-one can see how many characters your password is made up of.

```
eth0 Link encap: Ethernet HWaddr 00:03:od:92:40:ec
```

Good, this means that the wired network card has been detected. However, we need the exact output to understand what happened to the wireless one.

Keep us posted, good luck :KS

The desire to learn is the best indicator for the youth of a person's mind... Kudos!!

---

### Post by tarps87 on 2008-10-15
Just thinking, is it possible to connect to the internet using a wired connection as you'll probably need to do a lot of copy/pasting of the output. If not have you got a USB drive you can use? If so you can send the output to a file e.g. ```
ifconfig > ~/file.text
```
will send the output to a file called file.txt in you home directory.

When you used the command ifconfig and got eth0 did you also see eth1 or wanl0?

---

### Post by shewsbury on 2008-10-15
Orange_and_Green

OK, I think my mistake there... 

gksu gedit /boot/grub/menu.lst

it should be LST and not 1ST as type...

OK I manage to get the Grub editor.

This is the screenshot;

[IMG]http://i88.photobucket.com/albums/k190/shewsbury/Image049.jpg[/IMG]

As you can see I add the following;

no apic acpi_osi=Linux

Exactly as what I seen and as provided by zxscooby

So I then save the file and reboot... and still stuck.

As for the ifconfig this is what appear;

[IMG]http://i88.photobucket.com/albums/k190/shewsbury/Image048.jpg[/IMG]

And as for the lsusb this is it;

[IMG]http://i88.photobucket.com/albums/k190/shewsbury/Image047.jpg[/IMG]

Still it doesnt detect my USB mouse.... 

and Ubuntu can't even detect my USB Thumb Drive

So I just reboot.... and now I can't go in anymore....

Then I use the trick Orange_and_Green thaught me earlier:

Highlight the first entry, then press 'e' (not enter). This will let you edit the startup options. Choose the second line (the one that starts with "kernel"), press 'e' again. Add "acpi=off noapic" to the line as you did at install time. Then, press enter, then 'b' to boot.

And I still can't go in..

Using the same trick but this time I choose the Kernel with Recovery Mode.

Add the magic word
acpi=off noapic

Finally I go back to Ubuntu now...

So back to Grub editor... I am now changing the Grub back to it's normal state..

Basically I just delete whatever text I add just now and save them.

It's getting scary now...

Should I now add this word; acpi=off noapic

In all the lines start with the word "Kernel" as stated by Orange_and_Green earlier.

Actually what I did was, I only add it on the "first group" at the top. I didn't do it to the others.

Any comments from you Orange_and_Green ?

---

### Post by shewsbury on 2008-10-15
Dear tarps87

Sorry our office only use WiFi in network..

The Ubuntu can't detect any of my USB Thumb Drive

To activate WiFi on my laptop, I need to press Fn key + F10 key but it doesn't work... my WiFi stays OFF

It's getting scary for me now....

I just hope all this exercise - On and Off my laptop wont destroy any of the hardware..... touch wood....

---

### Post by tarps87 on 2008-10-15
Don't worry none of this should damage any hardware.
For your network try putting the cd back in once it has booted and then ```
sudo apt-get install ndiswrapper
``` This package should be on the cd, using it you can install a windows driver for the wireless. If this installs I can guide you through using it.

The command lsusb is showing one USB device connected, try disconnecting your mouse and running the command again, the top line should change, can you use any USB devices.

Try adding just noapic not acpi=!linux, if this doesn't work you can try adding acpi=off I suggest only doing it on the first kernel line, the next one it the recovery mode.

When you try to boot the pc and it freezes have you got your mouse connected?

Edit: Can you let me know if the lock problem happens if do
Highlight the first entry, then press 'e' (not enter). This will let you edit the startup options. Choose the second line (the one that starts with "kernel"), press 'e' again. Add "noapic" to the line as you did at install time. Then, press enter, then 'b' to boot.
(Like before but don't use the acpi=off command)

---

### Post by Orange_and_Green on 2008-10-15
Re. the infamous /boot/grub/menu.lst file,

my reasoning was that if you add exactly the options you used to successfully access the PC, then you know you have a safe, stable way to access your system, which you are then able to modify at your will but that you can confidently fall back to. So yes, I would delete the things you added to the menu.lst file and add the "magic words" acpi=off nopic and see if it boots; we can always try and improve things later.

+1 on tarps87's suggestion about ndiswrapper and lsusb without the mouse connected.

Good luck :KS

---


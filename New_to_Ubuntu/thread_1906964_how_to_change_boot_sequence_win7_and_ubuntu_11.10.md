---
title: "how to change boot sequence win7 and ubuntu 11.10"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by rebelbah on 2012-01-10
Good day All
i have read and every one says go to "system" or "application" to do this or that and in Ubuntu 11.10 i can not find the where to select application or system as inn other versions of Ubuntu
. i want win7 as my default to start, at present Ubuntu is.
how can i find "system" or "application" to be able to follow the rest of the instructions and change the boot sequence

---

### Post by androssofer on 2012-01-10
> **rebelbah said:**
> Good day All
i have read and every one says go to "system" or "application" to do this or that and in Ubuntu 11.10 i can not find the where to select application or system as inn other versions of Ubuntu
. i want win7 as my default to start, at present Ubuntu is.
how can i find "system" or "application" to be able to follow the rest of the instructions and change the boot sequence

i assume you mean when you start your computer and the screen that pops up that asks you select an OS too boot?

that is called grub. and here is a guide to change its order:

[http://www.unixmen.com/how-to-change-the-default-boot-order-for-grub2-in-ubuntu-1004-and-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/how-to-change-the-default-boot-order-for-grub2-in-ubuntu-1004-and-ubuntu-1010-maverick-meerkat/)

---

### Post by rebelbah on 2012-01-10
> **androssofer said:**
> i assume you mean when you start your computer and the screen that pops up that asks you select an OS too boot?

that is called grub. and here is a guide to change its order:

[http://www.unixmen.com/how-to-change-the-default-boot-order-for-grub2-in-ubuntu-1004-and-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/how-to-change-the-default-boot-order-for-grub2-in-ubuntu-1004-and-ubuntu-1010-maverick-meerkat/)

sorry for a newbie here
but this leads to the same thing
where do i get to the terminal window in Ubuntu 11.10
when i click the power button only selections i have is 
systems settings
display
startup applications
software up to date
attached devices(grayed out)
printers 
webcam
lock screen
logout
suspend
hibernate
shut down

i installed an older version before and those selections were available in the drop-down now i no longer see them

can you please direct me where to go to get to terminal window 

Thanks for your help

---

### Post by cortman on 2012-01-10
To answer your first question, there are a number of different ways to change the boot order, but I accomplished it simply by editing the grub.cfg file in /boot/grub. You can select the block containing the boot info- it starts with "menuentry" and ends with a curly brace "}". If you want to do it this way I'll post more info, but I think there are probably better methods out there.
You can open a terminal in any DE by pressing Ctrl+Alt+t. Your programs are not going to be in the user drop-down menu. If you're using Gnome-shell, mouse over the top left corner. If you're using Unity, click the button in the top left corner.

EDIT: Didn't read all of androssofer's post... his link should work great.

---

### Post by Elfy on 2012-01-10
Changing grub.cfg is ok until there is a grub update - then changes are reverted.

Apparently at the moment the use of a number to specify the default is not working.

You could use 

    GRUB_DEFAULT="Microsoft Windows XP Home Edition" (for example) 
or 
    GRUB_DEFAULT="saved"

Using the title you will need to know the exact title that appears in your grub menu

You can get that by running this in a terminal

```
cat /boot/grub/grub.cfg |grep menuentry
```

Alternatively using the saved option - the last thing you booted will be default - this will change as you sue different options.

Post back if you need help.

---

### Post by bogan on 2012-01-10
There is a very simple program that changes the default boot order, without the need to edit system files directly: 'Startup Manager', it is available via Ubuntu Software Centre.
Click on the Ubuntu symbol  [ Dash ] top left, select 'More Apps', scroll down to 'Software Center' & click to run it. Enter "startup" in the search box and select the Go Button.
Click on the Startup Manager entry and select 'Install'. 
Its Icon will now show in the Dash> More Apps display.
Run it and select 'Advanced', The default will show in a box with up-down arrows, click on that and select from the list, the entry you want as default, Close and restart to check the entry you want is highlighted.

{ In some rare cases, Startup Manager thinks that deleted entries still exist and gets it wrong, in which case count how many positions you want it to move and re-run Startup Manager.}

There is also an easy to use  program: 'Grub Customizer', that is much more complex, also allowing the selection of fonts, colours and background images for the Grub boot menu display, as well as editing names, changing the order, and hiding unwanted entries.
Getting it is a bit complex for this thread, but if you are interested, search for "Grub Customizer" in the Tips & Tutorials Forum.

**bogan**.

---

### Post by BC59 on 2012-01-10
A similar application to Startup Manager, but with more functions in tweaking the boot screen, is the Grub Customizer :
[http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html](http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html)

---

### Post by rebelbah on 2012-01-10
> **bogan said:**
> There is a very simple program that changes the default boot order, without the need to edit system files directly: 'Startup Manager', it is available via Ubuntu Software Centre.
Click on the Ubuntu symbol  [ Dash ] top left, select 'More Apps', scroll down to 'Software Center' & click to run it. Enter "startup" in the search box and select the Go Button.
Click on the Startup Manager entry and select 'Install'. 
Its Icon will now show in the Dash> More Apps display.
Run it and select 'Advanced', The default will show in a box with up-down arrows, click on that and select from the list, the entry you want as default, Close and restart to check the entry you want is highlighted.

{ In some rare cases, Startup Manager thinks that deleted entries still exist and gets it wrong, in which case count how many positions you want it to move and re-run Startup Manager.}

There is also an easy to use  program: 'Grub Customizer', that is much more complex, also allowing the selection of fonts, colours and background images for the Grub boot menu display, as well as editing names, changing the order, and hiding unwanted entries.
Getting it is a bit complex for this thread, but if you are interested, search for "Grub Customizer" in the Tips & Tutorials Forum.

**bogan**.

Thanks to ALL
and to Bogan for the detail info which got me fixed up

---

### Post by cortman on 2012-01-10
> **forestpiskie said:**
> Changing grub.cfg is ok until there is a grub update - then changes are reverted.

Apparently at the moment the use of a number to specify the default is not working.

You could use 

    GRUB_DEFAULT="Microsoft Windows XP Home Edition" (for example) 
or 
    GRUB_DEFAULT="saved"

Using the title you will need to know the exact title that appears in your grub menu

You can get that by running this in a terminal

```
cat /boot/grub/grub.cfg |grep menuentry
```

Alternatively using the saved option - the last thing you booted will be default - this will change as you sue different options.

Post back if you need help.

Thanks for the info, forestpiskie- I figured there had to be a catch to just editing grub.cfg.

---

### Post by androssofer on 2012-01-10
> **rebelbah said:**
> sorry for a newbie here
but this leads to the same thing
where do i get to the terminal window in Ubuntu 11.10
when i click the power button only selections i have is 
systems settings
display
startup applications
software up to date
attached devices(grayed out)
printers 
webcam
lock screen
logout
suspend
hibernate
shut down

i installed an older version before and those selections were available in the drop-down now i no longer see them

can you please direct me where to go to get to terminal window 

Thanks for your help

although your main problem seems solved.. it isnt right leaving you not knowing how to get the terminal!

the systems settings thing is the old way. the new easy way is:

click the ubuntu logo on the top left.

then type 'terminal'

click the icon and it will come up :-).

***note** alot of people advice the old way of doing things, as its hard to tell which version the person has. so in future if in doubt and some says click something like(this is an example of the old way):

system >> administration >> someOtherThing

then just click the ubuntu logo and type 'someOtherThing' the new way will do the rest :-)

---

### Post by waynefoutz on 2012-01-10
> **BC59 said:**
> A similar application to Startup Manager, but with more functions in tweaking the boot screen, is the Grub Customizer :
[http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html](http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html)

+1 I use this as well, it's great!

---

### Post by BNZBKK on 2012-01-10
> **bogan said:**
> There is a very simple program that changes the default boot order, without the need to edit system files directly: 'Startup Manager', it is available via Ubuntu Software Centre.
Click on the Ubuntu symbol  [ Dash ] top left, select 'More Apps', scroll down to 'Software Center' & click to run it. Enter "startup" in the search box and select the Go Button.
Click on the Startup Manager entry and select 'Install'. 
Its Icon will now show in the Dash> More Apps display.
Run it and select 'Advanced', The default will show in a box with up-down arrows, click on that and select from the list, the entry you want as default, Close and restart to check the entry you want is highlighted.

{ In some rare cases, Startup Manager thinks that deleted entries still exist and gets it wrong, in which case count how many positions you want it to move and re-run Startup Manager.}

There is also an easy to use  program: 'Grub Customizer', that is much more complex, also allowing the selection of fonts, colours and background images for the Grub boot menu display, as well as editing names, changing the order, and hiding unwanted entries.
Getting it is a bit complex for this thread, but if you are interested, search for "Grub Customizer" in the Tips & Tutorials Forum.

**bogan**.


This worked perfectly for me on 10.10 with a few small adjustments..

 ..after 'Startup Manager' installation I went to System/Administration/StartUp-Manager/Boot options - and the default was there and changed, with even a 'Timeout in seconds' option which I changed to 5 ( these Linux geniuses think of everything !)
 
 On restart Windows7 popped up as the default ....easy and a big thank you to **'bogan'**

---


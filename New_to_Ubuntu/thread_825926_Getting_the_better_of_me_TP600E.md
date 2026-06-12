---
title: "Getting the better of me TP600E"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by john collins on 2008-06-11
Hi again - my previous post refers - [http://ubuntuforums.org/showthread.php?t=815034&highlight=600e](http://ubuntuforums.org/showthread.php?t=815034&highlight=600e)

I have made little progress since my last Post - other than I have downloaded Ubuntu 7.10 and Linux Mint 4.0 - I have not installed Ubuntu 7.10 yet - but I have installed Mint 4.0 - hopeing that Mint might work as my previous version of Ubuntu did not.
Please could you tell me if I might be able to access the internet using the later version of Ubuntu. ( 7.10 )

The numerious threads I have read and taken notes on - indicate this could be something to do with acpi=off  pnp bios=off  pci=noacpi

I understand I type these commands ( in Term Window )
sudo gedit /boot/grub/menu.lst
can this go anywhere in that file & I presume once entered I can save the changes on exiting the terminal.

I acknowledge I have no sound - one error The Panel says 
"encountered a problem whilst loading OAF11D Gnome Mixer Applet"

also I need to manually turn the computer off once it has shut down - but at this stage I would rather concentrate on the connection problem if possible

Many thanks to you all - John Collins

---

### Post by Daveth on 2008-06-11
I cannot see your modem card in this list

[http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS](http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS)

or

[http://support.intel.com/support/network/sb/CS-003258.htm](http://support.intel.com/support/network/sb/CS-003258.htm)

which might suggest a lack of support for it. I suggest you try running 7.10 or Hardy as a live cd and see if it can pick up the internet that way.I must say I'm a bit of a fan of a good old router and ethernet cable stuck in the phone socket, and have never had any problems with Ubuntu finding the internet c.f windows when i used that.
Hopefully this post might rally some more support, but you definately need the most modern distros you can get to achieve the higher support levels.

---

### Post by john collins on 2008-06-11
Hi Daveth,

Im very grateful for your reply - I was beginning to think nobody cared.

I have just not had much luck with Linux - ( or the computers I load it on ) I have already down loaded 7.10 - I just need to burn it to CD - delete Mint and re install - Im not hopeful 
( dont want to be negative but -- ) I just find it all so easy with 2000 & XP - years of experience & DOS - but this is all strange & frightening.

Thanks for your reply - A lovely part of the world you live too

John C

---

### Post by john collins on 2008-06-11
Hi - you had me worried there - took me ages to find the RE100 on your list it was on mine - but it is listed on yours under the heading of "Fast Ethernet 10/100 base T adaptors.

I thought I was on to something then. Dam !!

---

### Post by Daveth on 2008-06-13
have you thought about the router and ethernet cable option? You can pick them up cheap- My BT Voyager 205 asdl router was about £25 on ebay and works well.

You probably know the next bit, but just in case....

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Feisty should just run nicely- I'm currently ironing out the odd wrinkle in Hardy.
Yes, it is rather nice over here - nice drive over the Malverns with a stormy sky today:)

---

### Post by john collins on 2008-06-21
Hi Daveth - brings back memories - I used to live in Malvern - Cottage in the Wood - one of my favourites !

Sorry for lomg gap in responce - Ive been rather fed up with Linux - and on an old slow computer takes ages to change parameters & reboot.

Sorry to be tight & not go along with your ebay suggestion I am on NTL cable here - no wireless - simplest of configuratioms I would have thought.RE100 Cat5 Router/ Modem Fiber.

I have three decent Tower Computers here running Windows 98/2000/XP - I am quite sure I would not have the same problem getting those on line with one of the Linux distros as I do have with this IBM 600E laptop.

I could just work my way through the various distrod until I find one that works as some distro's probe better than others - but I would learn nothing that way - why wont this configuration work ? 

It is my lack of knowledge of Linux - I cannot isolate at this time as to what the problem is - I have still not really resolved the ACPI=force & PCI=NOPCI - seems to make no difference
I have just down loaded the Xircom Windows driver & I now wonder how to use it with ndiswrapper

Not given up yet - not making much progress I hoping this doesn't get lost in the wilderness of weeks past.

Enjoy - John


My experience with Linux is dissapointing with the limited knowledge I have

---

### Post by cariboo on 2008-06-21
There is a module for your particular pcmcia card. could you type in a terminal:

```
lsmod | grep xirc*
```

If the modules is loaded you should see something like xirc2ps_cs as the result.

If it is not loaded in a terminal type the following:

```
sudo modprobe xirc2ps_cs
```and then try network manager again.

You do not have to reboot Ubuntu every time you make a change, Remember Linux is not Windows.

Jim

---

### Post by john collins on 2008-06-22
Hi Jim - that looks a brilliant responce - Its 0800 Sunday Morning - Im just off to ring my Bells - but really looking forward to trying that later today - Thankyou for your reply - why have I never come acros it before as the RE100 is supposedly supported by Linux - is this 600E that much of a monster ?? Thanks Jim

John C

---

### Post by john collins on 2008-06-22
Hi Jim
output of lsmod ¦ grep xirc*
xirc2ps_cs  19980  1
pcmcia      41388  1  xirc2ps_cs
pcmcia_core 40980  4  xirc2ps_cs,pcmcia,yenta_socket,
rsrc_nonstatic

I do have a choice of module selection from within nertwork manager - but I cannot be sure the driver listed is for the RE100 card.

Any suggestions gratefully received - many thanks - john C

---


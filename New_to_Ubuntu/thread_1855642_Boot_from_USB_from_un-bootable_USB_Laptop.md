---
title: "Boot from USB from un-bootable USB Laptop :/"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by ajsoulmate on 2011-10-06
An old SONY laptop with broken CD drive and UN-botable from the USB Flash Drive !!

I use Plop Boot Manager [http://www.plop.at/](http://www.plop.at/) on Windows XP OS to boot from the USB drive and it work .. so I was able to download Ubuntu 10.4 and it's work well ..
Now am trying to download Lubuntu 11.4 but I couldn't use Plop Boot Manager any more ..
So I search for a solutions to fix my issue so I can Boot from the USB again to install Lubuntu ,
in fact I found a several ways and i try it almost all but none of them could solve my problem !!

one of them were in the same program website 

[http://www.plop.at/en/bootmanager.html#intro](http://www.plop.at/en/bootmanager.html#intro)

```

Run from GRUB2

Download the current boot manager [COLOR="navy"]plpbt-5.0.13.zip[/COLOR]. Extract it to get the boot manager binary program plpbt.bin.

Copy the [COLOR="navy"]plpbt.bin[/COLOR] file to /boot.

You have to choose the correct root settings in grub.cfg for your system. 
The following is an example

menuentry "Plop Boot Manager" 
    set root=(hd0,1)
    linux16 /boot/plpbt.bin

When you reboot, you should be able to start the boot manager from your grub menu.

You can configure the file plpbt.bin with plpcfgbt.


```

During this process I have another problem which is :
how I can log in as a root So that I can copy the file and paste it in a Root folder so I search again and I found the answer ..

<snip>


so I was able to fix root issue and I log in as a root and I could copy the [COLOR="Blue"]plpbt.bin file[/COLOR] to the Boot folder as they said and I restart my laptop
But unfortunately nothing happened and it doesn't work with me ..
so any Suggestions !!

---

### Post by CaptainMark on 2011-10-06
this might not be the answer you were looking for but unless your laptop is really really really old then it probably will boot from usb, the older laptops though used to detect a usb stick as an internal drive so wouldnt list them in any quick boot menu but if you search into your bios, youll have the usual boot priority list, but often also a hard drive priority list aswell, move the usb up to the top of that list too, save and exit, the problem with laptops that do this everytime you unplug the usb it drops back to the bottom of the list 

i appreciate this may not be the case but even my first laptop (at least 10 years old) does this

---

### Post by ajsoulmate on 2011-10-06
No it's not older than 10 years i think it's about 6 or 7 years !

Any how my Boot Menu
1-Optical Drive
2-Hard Disk Drive
3-Floppy Disk Drive
4-Network

---

### Post by CaptainMark on 2011-10-06
no, a seperate menu, not the boot menu but it should be in a similar place, it should be called 'hard drive priority' or something similar like 'hard disk menu/order' and it may list your usb because many older laptops detected them as if they were actually internal hard drives, as i say its not 100% but it would save you some hassle and is worth a check

---

### Post by ajsoulmate on 2011-10-06
Okay i'll check that ..

---

### Post by racie on 2011-10-06
> **ajsoulmate said:**
> No it's not older than 10 years i think it's about 6 or 7 years !

Any how my Boot Menu
1-Optical Drive
2-Hard Disk Drive
3-Floppy Disk Drive
4-Network

Hmm... this doesn't look very promising.  :/

There are a couple of things you could try though.  First, I want you to switch floppy to #2 and hard disk to #3.  This is just in case.

Second, I want you to try making your bootable USB with [Unetbootin](http://unetbootin.sourceforge.net/).  It's a much more straightforward program than what you're using.  See if it boots this way...

If it doesn't attempt to boot after the above, I must know if you have a floppy drive inside your laptop.  If your laptop cannot boot from a USB device, we can tell it to by making it boot from the floppy first.  

*edit* Oh yeah... try CaptainMark's post first of course.

---

### Post by ajsoulmate on 2011-10-06
No i don't have a Floppy drive in my laptop :/
okay i'll change the boot menu then i'll try Unetbootin and i'll let u know ..

---

### Post by ajsoulmate on 2011-10-06
sorry but i think u got me wrong i have an Ubuntu 10.4 start up disk but i can't use it because i cann't boot from my USB Drive and According to my information there is a huge diffident between Unetbootin and Plop Boot Manager!

```


The Plop Boot Manager is a small program to boot different operating systems. The boot manager has a builtin ide cdrom and usb driver to access those hardware without the help/need of a bios. You can boot the operating systems from harddisk, floppy, CD/DVD or from USB. You can start the boot manager from floppy, CD, network and there are many more ways to start the boot manager. You can install the boot manager on your harddisk. There is no extra partition required for the boot manager.
```

so any other suggestion ..

---

### Post by ajsoulmate on 2011-10-06
> **CaptainMark said:**
> no, a seperate menu, not the boot menu but it should be in a similar place, it should be called 'hard drive priority' or something similar like 'hard disk menu/order' and it may list your usb because many older laptops detected them as if they were actually internal hard drives, as i say its not 100% but it would save you some hassle and is worth a check

sorry but I could not find anything of the above :/

---

### Post by amjjawad on 2011-10-07
> **CaptainMark said:**
> the problem with laptops that do this **everytime you unplug the usb it drops back to the bottom of the list **

Hello Mark, good to see you :)

Actually, this is the general case with each and every USB Drive. Think about it, BIOS would detect the device ONLY if it's plugged in and it wouldn't while it's unplugged so it's not a problem in fact, it's a common sense thing. This is how BIOS works.

:)

---

### Post by amjjawad on 2011-10-07
> **ajsoulmate said:**
> sorry but I could not find anything of the above :/

Hi there,

Mark was talking about this (luckily, I have lots of screenshots here ;) )

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]

There is "Device Priority" and there is "Hard Drive Priority".

Double Check your BIOS. In case you'll find something referring to "Hard Disk Boot Priority" or just "Hard Disk Priority" then please make sure to change the boot order and set USB to be first.

Some BIOS may refer to that as "USB-HDD0" 

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]

But I'm not sure about your SONY's BIOS?!

I'm sure you'll figure it out once you'll find something like "Hard Disk Priority".


If your BIOS has no such feature, then you have two approaches:

1- Either to use Plop - which you already mentioned in your first post.

2- Take the HDD outside your laptop, connect it to another machine, install Lubuntu then put it back in.


As for Plop, I think you are trying to find out HOWTO Install Plop Manager inside Ubuntu and HOWTO Configure GRUB2 to boot both Ubuntu and Plop Manager, right? I mean you want Plop to appear as a Menu Entry in GRUB2 Menu so that you can use your LiveUSB to install Lubuntu, correct?
If that's what you are looking for then unfortunately I did some search and couldn't find the right way to do that. I tried that on my Test PC too a while ago but it didn't work.
Perhaps someone more advanced than me will jump in and help :)

As for the second approach, if you DON'T KNOW how to take your HDD from your laptop and put it back in then FORGET IT please :)
I understand it's not easy for everyone, specially with an old laptop. You might break something and it's not easy to fix Hardware Parts ;)


Another advice: Always use TAGS and KEYWORDS when posting a new thread. That will help advanced users who search for specific words t jump in and help.
[drs305]("http://ubuntuforums.org/member.php?u=223945")  is specialist in GRUB2 so hope he'll jump in :)

Sorry if I couldn't be so much help to you!

---

### Post by CaptainMark on 2011-10-07
or you could ask everyone you know if someone has a usb cd drive, this will not be detected as a usb device but i cd drive and will boot before your hdd, failing that buy one from a shop use it the once and then miraculously find it doesnt work and get a refund

---

### Post by amjjawad on 2011-10-07
> **CaptainMark said:**
> failing that buy one from a shop use it the once and then **miraculously find it doesnt work** and get a refund

What an evil good idea :D LOL

---

### Post by anewguy on 2011-10-07
Direct root access is strongly discouraged in this forum.  It is recommended to use "sudo " in front of the command instead.  Please do not post how to enable the root login.

Thanks 
Dave ;)

---

### Post by nothingspecial on 2011-10-07
> **anewguy said:**
> Direct root access is strongly discouraged in this forum.  It is recommended to use "sudo " in front of the command instead.  Please do not post how to enable the root login.

Thanks 
Dave ;)

See this

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by ajsoulmate on 2011-10-07
> **nothingspecial said:**
> See this

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)



I'm so sorry, I'm not aware of this. I'm NEW here and still learning :(

---

### Post by nothingspecial on 2011-10-07
> **ajsoulmate said:**
> I'm so sorry, I'm not aware of this. I'm NEW here and still learning :(

No problem, the issue is fixed :)

---

### Post by ajsoulmate on 2011-10-07
> **CaptainMark said:**
> or you could ask everyone you know if someone has a usb cd drive, this will not be detected as a usb device but i cd drive and will boot before your hdd, failing that buy one from a shop use it the once and then miraculously find it doesnt work and get a refund


i already have tried the external CD but it didn't work !!

---

### Post by mastablasta on 2011-10-07
if oyu have no floppy drive then why is it on your boot list? could USB be recognised as floppy?
 
Also what do you mean you can't use PLOP "***anymore"***? you mean it doens't work with Lubuntu but it does work with Ubuntu? then install Ubuntu, then add LXDE (lubuntu desktop) and then remove GNOME.

---

### Post by amjjawad on 2011-10-07
> **mastablasta said:**
> if oyu have no floppy drive then why is it on your boot list? could USB be recognised as floppy?
 
As far as I have tried myself, USB never got recognized as Floppy. I have worked with much older machines that the OP's machine and still USB never got recognized as Floppy.


> Also what do you mean you can't use PLOP "***anymore"***? you mean it doens't work with Lubuntu but it does work with Ubuntu? 
OP was able to use Plop before when it was installed in Windows XP. OP used Plop to install Ubuntu successfully.

Now, OP wants to install Plop again inside Ubuntu and install Lubuntu.

> then install Ubuntu, then add LXDE (lubuntu desktop) and then remove GNOME.

I do NOT recommend that.
The menu will be missed up and perhaps fixing that will lead to other issues. Clean Install is much better IMHO.

---

### Post by ajsoulmate on 2011-10-07
> **amjjawad said:**
> Hi there,

Mark was talking about this (luckily, I have lots of screenshots here ;) )

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]

There is "Device Priority" and there is "Hard Drive Priority".

Double Check your BIOS. In case you'll find something referring to "Hard Disk Boot Priority" or just "Hard Disk Priority" then please make sure to change the boot order and set USB to be first.

Some BIOS may refer to that as "USB-HDD0" 

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]

But I'm not sure about your SONY's BIOS?!

I'm sure you'll figure it out once you'll find something like "Hard Disk Priority".


If your BIOS has no such feature, then you have two approaches:

1- Either to use Plop - which you already mentioned in your first post.

2- Take the HDD outside your laptop, connect it to another machine, install Lubuntu then put it back in.


As for Plop, I think you are trying to find out HOWTO Install Plop Manager inside Ubuntu and HOWTO Configure GRUB2 to boot both Ubuntu and Plop Manager, right? I mean you want Plop to appear as a Menu Entry in GRUB2 Menu so that you can use your LiveUSB to install Lubuntu, correct?
If that's what you are looking for then unfortunately I did some search and couldn't find the right way to do that. I tried that on my Test PC too a while ago but it didn't work.
Perhaps someone more advanced than me will jump in and help :)

As for the second approach, if you DON'T KNOW how to take your HDD from your laptop and put it back in then FORGET IT please 
I understand it's not easy for everyone, specially with an old laptop. You might break something and it's not easy to fix Hardware Parts


Another advice: Always use TAGS and KEYWORDS when posting a new thread. That will help advanced users who search for specific words t jump in and help.
[drs305]("http://ubuntuforums.org/member.php?u=223945")  is specialist in GRUB2 so hope he'll jump in :)

Sorry if I couldn't be so much help to you!

Good screen shots but as i said before i don't have such features in my BIOS and i don't prefer to take my HDD out my machine to install Lubuntu on it , so i will go to your first suggestion and try to use Plop , problem is i don't know how to configure GRUB and make it work with Plop :/

And yes you have understood Precisely the point that I want :) 

```
As for Plop, I think you are trying to find out HOWTO Install Plop Manager inside Ubuntu and HOWTO Configure GRUB2 to boot both Ubuntu and Plop Manager, right? I mean you want Plop to appear as a Menu Entry in GRUB2 Menu so that you can use your LiveUSB to install Lubuntu, correct?
```


In fact I do not want to confine myself in a narrow range, but unfortunately so far I found nothing but this program <Plop Boot Manager> is able to resolve the problem that I face ..
Any how If there were other programs, or any other solutions or suggestions i will try them all ..

About <TAGS and KEYWORDS> Thanks for the advice I will try to remember that next time ;)

---

### Post by mhgsys on 2011-10-07
read my post here 
[http://ubuntuforums.org/showthread.php?t=1749260](http://ubuntuforums.org/showthread.php?t=1749260)

#8 might be a big help for you.

---

### Post by amjjawad on 2011-10-07
> **ajsoulmate said:**
> Good screen shots but as i said before i don't have such features in my BIOS

Ok, understood but as you may know, we must check first few simple steps before we go complicated. You know, Keep It Short and Simple ;)

> and i don't prefer to take my HDD out my machine to install Lubuntu on itAgreed. If you haven't done that before and you feel you can't do it now, don't do it please :)

> so i will go to your first suggestion and try to use Plop , problem is i don't know how to configure GRUB and make it work with Plop :/
I'm sorry, I'd like to help but I haven't done that myself and I couldn't find much on Google. I hope someone like drs305 will jump in :)

> And yes you have understood Precisely the point that I want :) I'm glad I did :)

> In fact I do not want to confine myself in a narrow range, but unfortunately so far I found nothing but this program <Plop Boot Manager> is able to resolve the problem that I face ..
Any how If there were other programs, or any other solutions or suggestions i will try them all ..Plop is ALL what I know that might help in such situation.
External CD as Mark suggested earlier is good idea too but I wouldn't buy one, use it then claim it's not working, I won't do that :P hahaha.

> About <TAGS and KEYWORDS> Thanks for the advice I will try to remember that next time ;)You most welcome :)

---

### Post by ajsoulmate on 2011-10-07
> **mhgsys said:**
> read my post here 
[http://ubuntuforums.org/showthread.php?t=1749260](http://ubuntuforums.org/showthread.php?t=1749260)

#8 might be a big help for you.




Thank you very much mhgsys :D

indeed your post is very useful and I followed the steps below 

> 
copy the plpbt.bin (found in the extracted plpbt-5.0.12 > pcmcia folder to /boot
f.e
Code:
sudo cp /home/mhg/Desktop/plpbt-5.0.12/pcmcia/plpbt.bin /boot
[http://download.plop.at/files/bootmngr/plpbt-5.0.12.zip](http://download.plop.at/files/bootmngr/plpbt-5.0.12.zip) (for the files)


then you edit /etc/grub.d/40_custom 
Code:
sudo nano /etc/grub.d/40_custom
and add
Code:
menuentry "Plop Boot Manager Install"{
set root='(hd0,1)'
linux16 /boot/plpbt.bin
}
to the bottom of the file (don't forget to safe / WriteOut the file)(ctrl+o in nano> enter>ctrl+x)

(where '(hd0,1)' is the first partition on the first harddrive.. you see.. where /boot is)

then you
Code:
sudo update-grub2
, reboot.. hold down left shift so grub comes on.. and select plop


so i was able to solve the problem And finally I could instal Plop Boot Manager, and now I can boot from any USP Drive :)

---

### Post by ajsoulmate on 2011-10-07
Thank you for all to try to help me, you are very Helpful and cooperative and I appreciate it a lot :)

---

### Post by amjjawad on 2011-10-07
> **ajsoulmate said:**
> so i was able to solve the problem And finally I could instal Plop Boot Manager, and now I can boot from any USP Drive :)

Excellent, well done, ajsoulmate :)

I'm glad you managed to fix it so quickly :)

Nice Avatar by the way, I like it!

P.S.
If you need anything related to Lubuntu (since you'll be a Lubuntu User), please let me know.

---

### Post by mhgsys on 2011-10-07
> **ajsoulmate said:**
> 
Thank you very much mhgsys 

indeed your post is very useful and I followed the steps

Your welcome

---


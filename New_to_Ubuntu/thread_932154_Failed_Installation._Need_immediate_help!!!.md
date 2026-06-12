---
title: "Failed Installation. Need immediate help!!!"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Arsin on 2008-09-28
So i tried to install my Ubuntu and everything was great it got to the desktop finally so then i went to restart my computer so i got a screen that said remove disk close tray and press enter i followed the instructions:popcorn: then when my computer started booting up again after the dell screen it said it couldn't boot to the cd-rom , cause obviously i had removed it so i tried booting to my hard drive and it couldnt find it. so now i booted back to the cd and im running it live from the cd. and when i try to install it from here i get an error called like partman right after it configures the keyboard so even if i skip that i get another right after i fill out my user info (name and what not) can someone please help.

---

### Post by shadow-of-sin on 2008-09-28
What is the exact error message you get?

Also, did you verify the install CD?

---

### Post by Arsin on 2008-09-28
Verify the install cd?
im trying to bring up the error again

---

### Post by shadow-of-sin on 2008-09-28
When you boot up the Ubuntu CD, there should be an option to check the cd for errors, if you run that you can find out if your problem is caused by a bad cd.

---

### Post by muted1987 on 2008-09-28
did you have to cahnge your bios to boot from cd first maybe you will have to change it back if you did

---

### Post by Arsin on 2008-09-28
i ran that the cd was fine. but now i get this i tried to prompt the aformentioned error again by attempting to install again, and for what ever reason it worked this time i made it to the partition screen and clicked guided full hd partition. so i finished filling out the stuff and it started installing then at about 56% i got this

> The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error: '/rofs/usr/share/doc/libvolume-id0/changelog.Debian.gz'

This particular error is often due to a faulty CD/DVD disk or drive. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, or to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers).


but as i said before i did the cd check and it said it was fine. so im still currently running on live ubuntu

---

### Post by muted1987 on 2008-09-28
oh i did not understand i thought you had a succesful install then couldnt boot to grub

try installing ubuntu in text only install im not sure how to get to it from the live cd but im sure theres a menu on the start for it but be warned may get complicated at poartitioning screens

---

### Post by Arsin on 2008-09-28
i did have a successful install thats whats bothering me in successfully installed or atleast it didn't say other wise. I made it to my desktop and decided to reboot so i could remove the cd and give it a go. so when it was shutting down it prompted me to remove the cd from the cd drive close it and press enter to continue shutting down. i did this. then when i went to boot up again my computer tried to boot to the cd rom so i started over and went to the boot menue and tried the hard drive. it couldn't find anything to boot too. so restarted again trying all the other options. eventually i booted back to the cd and am now running ubuntu live from the cd

---

### Post by muted1987 on 2008-09-28
ok so my first reply still stands did you have to change anything in the bios to get the comp to boot to cd??? 

if so youll  have to change back the options to boot hdd

---

### Post by Arsin on 2008-09-28
and as i said before yes i did i changed it to boot to the cd. after the installation i asked it to boot to hdd and it said it could not be found.

---

### Post by muted1987 on 2008-09-28
oh sry misunderstood thought you said that it just didnt find it after getting to the grub.

are the hdds on the same ribbon eg primary master primary slave with cd on secondary

or primary master secondary slave with cd being secondary master <<<, this config is wrong

have these hdd's always been in there or have you just recently put one in??

---

### Post by Arsin on 2008-09-28
i don't know where you got the idea of 2 hdd's but im only opperating on one and its always been there.

---

### Post by shifty_powers on 2008-09-28
if you are havign issues with the live cd, you can try downloading and using the alternate install cd.

this has a simple text based install procedure, but is easy enough to use, and is designed to be used, amongst other things, when the live cd is having trouble.

you can download it from the same ubuntu download webpage...

---

### Post by muted1987 on 2008-09-28
sry got confused with other thread forgive me only jsut realised when i refreshed forum page 

the only other thing i can suggest is download the alternate install cd and complete the install after restore bios to default( im sure theres an option for that) and see if it loads

---

### Post by Arsin on 2008-09-28
well this all sounds moderately useful im downloading the alternate install cd or what ever. its an iso file so i don't know how this is going to help cause im still gonna have to burn it to a cd (my cd burner is terrible at this so it prolly won't work) and if the burn works i don't know how this is going to be any different from the cd i already have.

---

### Post by shifty_powers on 2008-09-28
a little tip, burn the cd at the slowest speed possible, i know it slows down the process, but it will mean that as few errors as possible will be introduced into the burn as possible, you'd be surprised the difference it can make.

good luck!

---

### Post by Arsin on 2008-09-28
well there is a major flaw in all of this. i have no disk space apparently to save this file. so idk what im going to do.

---

### Post by muted1987 on 2008-09-28
are you downloading from live cd ??

if you are then hit alt+f2 and type gksudo gparted and locate the hdd the live cd should find it and right click on the home extension and mount it to whereaveer than save the file to where it is mounted

this will only help if you have a 2 cd drives as you wont be able to burn if you dont

---

### Post by Arsin on 2008-09-28
once again major flaw single cd drive.

---

### Post by muted1987 on 2008-09-28
do you have any other cds lying around that you could install and see if the problem still arises?

can i have the model of your pc as well eg dell workstation 3943 or however the label htem

---

### Post by shifty_powers on 2008-09-28
do you have a usb pen drive?

save it to there...

---

### Post by muted1987 on 2008-09-28
shifty can you get a install to run of the usb drive?? or even the live cd to run 

this may help in the fact that theres only 1 cd drive

---

### Post by shifty_powers on 2008-09-28
[http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/)

will show how to do it for 7.04...

---

### Post by Arsin on 2008-09-28
oddly engough i do not have a pen drive due to the fact that i just moved so i dont know where they went. I'm still getting different types of errors when i boot to cd and try to install from there.


btw im running a 
dell dimension 4700 p4 3.2ghz
1g of ram
250g hdd
1 cd drive

and now i don't have windows installed anymore.

---


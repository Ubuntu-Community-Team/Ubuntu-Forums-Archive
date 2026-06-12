---
title: "external hdd ubuntu ???"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by westentertainer on 2008-05-21
hello my first thread ...i totally messed up my pc i had xp and vista dual booting great,, i then tried to partition the c drive for ubuntu but it would not reboot  so i had to do a fresh install on the both..but i do like linux i have a live cd  my question is i have a external empty 200 gig hdd is it possible to install it on there   many thanks

---

### Post by lemming465 on 2008-05-21
If your live CD can see the drive, you can install to it.  Depending on your BIOS, you may or may not be able to boot it afterwards. E.g. on a 6 year old compaq, I can install to an external firewire drive, but I can't boot it directly.  If it's a fairly new computer (<2 years old), the odds that you can boot it too are good.  The experiment is cheap; try it.

---

### Post by westentertainer on 2008-05-22
thanks for reply  so what are the steps i take if yu dont mind could you tell me the way to do this

---

### Post by bumanie on 2008-05-22
This tutorial should point you in the right direction. It works, I've done it on a usb pen drive. [http://www.pendrivelinux.com/category/install-to-usb-hard-drive/](http://www.pendrivelinux.com/category/install-to-usb-hard-drive/)

---

### Post by rraj.be on 2008-05-22
If your live cd can detect you second hard disk you can instll the os there and othere things are nothing.
just your GRUB  [bootloader] will map to ur operating systems respectively.

---

### Post by westentertainer on 2008-05-22
thanks one little thing  i have a cd of ubuntu 8.04 lts   but i cant see installer icon on the desktop when i open ubuntu  thanks

---

### Post by rraj.be on 2008-05-22
just you can brows your live cd.

you will have the installer.

else you can use terminal.

open the terminal from applications-->accesories-->terminal

just i cant get the command.
will get it for you in a minuet or two.

---

### Post by rraj.be on 2008-05-22
see this page for more information.

this will help you clearly.

```
http://www.ubuntu.com/node/691
```

```
   1. Press Alt F2 to get into the Run Application dialogue
   2. Type "gnome-terminal" and press Enter.
   3. In the resulting Terminal window, type "sudo su" and press Enter.
   4. Press Insert Q to quit Orca. At this point, you will have no speech, but focus is still in the terminal window.
   5. Type "orca --no-setup &" and press Enter. This will cause speech to resume, but Orca will now be running as root.
   6. Type "ubiquity" and press Enter.

```

if you cant get there...

you are free to ask any doubt in this forum or just PM me.

---

### Post by westentertainer on 2008-05-22
hello i am using a laptop now to send this reply as i have live cd on my main pc i still cant find installer on desktop   please help  thank you

---

### Post by westentertainer on 2008-05-22
insert Q is given me problems wont recognise it

---

### Post by pdtpatrick on 2008-05-22
Go to Applications > Accessories and click on the terminal .. and you should be able to continue from the other steps colleague wrote:

5. Type "orca --no-setup &" and press Enter. This will cause speech to resume, but Orca will now be running as root.
   6. Type "ubiquity" and press Enter.

Make sure you bios is set to boot off your External harddrive or else it would skip it and you'll be scratching your head why..

---

### Post by rraj.be on 2008-05-22
ok.
just open the terminal and then type

```
ubiquity
```

press Enter.

this will start your installer

---

### Post by westentertainer on 2008-05-22
typing in ubiquity in terminal command not found

---

### Post by rraj.be on 2008-05-22
I am extremly sorry.

There is no chance for this.

If you are using ubuntu live cd it shud work.

else try another set of ubuntu live cd.

even in ubuntu live cd documentation the command held to install ubuntu via terminal is ubiquity.

the best idea is to try another instalation live cd or alternate cd.

---

### Post by westentertainer on 2008-05-22
ok thanks i will download a new cd   any links to which cd version i should use [with installer on desktop]   thanks

---

### Post by rraj.be on 2008-05-22
here is that

```
http://www.ubuntu.com/getubuntu/download
```

but try some other go like using irc.ubuntuforums.com

or make another new post that some other members can help you too.

try to download at last because it will take time and bandwidth

---

### Post by westentertainer on 2008-05-22
im downloading at this moment 8.04 desktop 1386 iso is this ok

---

### Post by greenstar on 2008-05-22
When download is complete, you should verify the md5 checksum. Directions for [how to verify download integrity]("https://help.ubuntu.com/community/HowToMD5SUM") are in the community documentation.

Once you verify the md5sum, then burn at 2x to help ensure a good burn.

HTH,

Greenstar

---

### Post by westentertainer on 2008-05-23
tried 2 but mdsum says both are different so im trying different one now

---

### Post by westentertainer on 2008-05-23
ok i have installed to external hdd   now i need to find a way to boot from it

---

### Post by rraj.be on 2008-05-25
Just set your boot sequence in BIOS to boot from hard disk number of your external hard disk.
Im sorry...

my net connection gone wrong.
so only i cant help you

---


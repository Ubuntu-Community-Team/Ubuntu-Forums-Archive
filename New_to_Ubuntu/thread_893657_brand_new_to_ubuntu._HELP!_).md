---
title: "brand new to ubuntu. HELP! :)"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by icecloud on 2008-08-18
hey guys and gals its been a while since i've used linux...almost 10 years actually and i'm running into some issues. mainly i have a Sound Blaster Audigy SE card and i'm getting no sound out of my connections...i just get static; now when i go up and down wit volume it actually changes the volume. but thats all i get no actual sound coming through. also i've installed Wine and am trying to install World of Warcraft from the cd's and my dvd drives keep screwing up and will not open unless i use a paper clip then the o/s does not see that the either do not have a cd in them and/or dont see the new disc inside the drive. are these normal issues? also i know that linux is basically and open source o/s but are there any pointers you guys can give me before i jump in the pool of coding for my own system when something isnt working correctly? um one more issue my usb flash drive isnt reading in my new unbunto system no matter which usb connection i hook it into...is there a fix for this.
just fyi used to have a Windows Xp system.

---

### Post by freesitebuilder on 2008-08-18
Here's the hardware sound card support page:
[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs)

Can't see it listed - but is the card OK in Windows?

---

### Post by nitro_n2o on 2008-08-18
woooow you asking a lot of questions at once.. it might help if you split them in separate threads as each one is an issue by itself

It'll also be helpful to know which version of ubuntu you are currently running, because some bugs in older versions have easy solutions

as for sound make sure you have the drivers. ALSA is good sudo apt-get install alsa-mixer 

* there are many threads discussing sound issue and especially that you have a fancy card it might have its own driver! sometimes compiling alsa from source solves the problem!


as for ejecting a DVD, linux won't let you eject the DVD if it was busy! so don't force it by a paper clip

as for usb, your usb might be formatted as NTFS. If this is the case 
sudo apt-get install ntfs-3g

hope that helps

---

### Post by sneeks on 2008-08-18
have you tried the alsa firmware loaders in the synaptic package manager..
it could work for you.

---

### Post by neofreud on 2008-08-18
For the USB Flash Drive Try either of these two links. 

[http://www.linuxquestions.org/questions/debian-26/how-to-mount-a-usb-flash-drive-380376/](http://www.linuxquestions.org/questions/debian-26/how-to-mount-a-usb-flash-drive-380376/) 

OR

[http://www.linuxquestions.org/questions/ubuntu-63/manual-mount-external-usb-hard-drive-in-ubuntu-519463/](http://www.linuxquestions.org/questions/ubuntu-63/manual-mount-external-usb-hard-drive-in-ubuntu-519463/) 

You basically have to mount the drive. I am not expert in this topic BUT I did it to like 4 differnt kinds of products last weekend and it all worked fine! 

Good Luck!

---

### Post by icecloud on 2008-08-18
ok hope this helps when i open my fire fox it says welcome to Ubunto 8.04 LTS and its the hardy heron one. also what does sudo mean and all those sudo things...how do i do them..i konw i sound nieve and its irritating to me...i fix pc's for a living but i'm new to this :)

---

### Post by unutbu on 2008-08-18
sudo is the command used to give yourself administrative (root) powers. It will ask you for a password. Just type in your normal user password. It won't show any text, but that's ok. Just type it and press return.

To type commands, open a terminal: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

Example:

To install a package named conky:
```

sudo apt-get install conky
```

To edit a system file that only root can touch:```

gksu gedit /etc/fstab
```

gksu is like sudo, except that you should use gksu for graphical apps, and sudo for terminal commands.

---

### Post by icecloud on 2008-08-19
ok got the sound working "GRINS" yay for sound...never knew how quiet working on a pc is until i had no music :P

---

### Post by icecloud on 2008-08-19
still having issues mounting my usb device but that may be because that i now cannot login to my root 0.o my password is correct but it tells me its wrong yet i can restart my pc and the password works....alrighty then

---


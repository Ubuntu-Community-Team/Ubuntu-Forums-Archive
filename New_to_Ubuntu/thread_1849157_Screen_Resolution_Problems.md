---
title: "Screen Resolution Problems"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by openmynd on 2011-09-23
Hey.

Installed Ubuntu 11.04 via VirtualBox onto my 32 bit Vista Machine. I've got a 24" monitor I like to be set to 1920x1200 (16:9), on an Nvidia GeForce 8400 GS.

It took some forum perusing to get my screen size to be larger than a 3x5" card through VirtualBox's "Install Guest Additions...". Now, I have a max of 1600x1200 which is 4:3 aspect ratio. It won't detect my monitor.

In browsing forums I tried all forms of "sudo spt-get install" for Nvidia drivers that don't seem to exist anymore. I downloaded a driver from Nvidia's website and did a "sudo sh <filename>" to which I was told I did not have an Nvidia GPU and I needed to close the X server.

Not sure what that means. I looked up closing the X server and found Ctrl+Alt+F1 which only turned my screen black and I had to restart.

No, nothing whatsoever shows up in System->Administration->Additional Drivers. That would have been too easy.

Thanks in advance for the help. My apologies if the information has already been posted. I'm a firm believer that I'm not the only person who has encountered this, but 2+ hours of Googling hasn't gotten me anywhere. Yeah, I know -> :-({|=

Can anyone get me to widescreen and 1920x1200 resolution with or without a driver?

---

### Post by wolfen69 on 2011-09-23
In virtualbox, your nvidia card is essentially rendered useless because vbox emulates all of the hardware. And once guest additions is installed, that's the best you are going to do as far as video goes. Did you press *Right Ctrl + F* to toggle to full screen?

---

### Post by openmynd on 2011-09-23
Yes, at full screen the best I can get is 1600x1200 which doesn't fill my screen and has rather large text.

---

### Post by wolfen69 on 2011-09-23
How much memory did you allocate for video usage?

---

### Post by LinuxFan999 on 2011-09-24
@openmynd
How much video memory do you have allocated to your virtual machine? Do you have the guest additions installed? If you have the guest addition installed, you can adjust the guest's screen resolution by resizing the VM's window, and you can also enable. "seamless mode". Doing this intergrates the Guest's desktop with the host's desktop, and gives the guest the same screen resolution as the host.

---

### Post by openmynd on 2011-09-24
64mb.

---

### Post by openmynd on 2011-09-24
@LinuxFan999 yeah, I found Scale Mode, but when maximized it just stretches everything so it's disproportionately wide.

---

### Post by wolfen69 on 2011-09-24
> **openmynd said:**
> 64mb.

Try 128 if you have enough to spare.

---

### Post by openmynd on 2011-09-24
@wolfen69 - Just upped it. Didn't work. :(

@LinuxFan99 - Ah yeah, I see Seamless mode. It's grayed out. Hmm...I wonder if it's Ubuntu that isn't compatible...?

---

### Post by wolfen69 on 2011-09-24
> **openmynd said:**
> Hmm...I wonder if it's Ubuntu that isn't compatible...?

I can assure you ubuntu runs perfectly in vbox. I've done it many times. Did you enable 2D and 3D acceleration?

---

### Post by openmynd on 2011-09-24
Yes, they're enabled. At this point I've gone in and checked all the boxes and threw all the sliders to the right lol.

---

### Post by wolfen69 on 2011-09-24
Unless someone else has an answer, it might be worth your while to ask over at the virtualbox forums also.

---

### Post by openmynd on 2011-09-24
Alright, thanks for the ideas.

---

### Post by mikee55 on 2011-09-24
How about you install Ubuntu then run Vista in Virtualbox, then when you realise that Vista is retarded, you can just delete it :)
Sorry, just my 2 pence worth

Mike

---


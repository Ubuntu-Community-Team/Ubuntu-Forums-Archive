---
title: "Making a transition from windows.."
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Linuxperiment on 2008-11-15
Hello all. I'm transitioning from windows and I'm very new to Linux (Xubuntu). I have the most recent version of Xubuntu, and I have a few newbie questions. I've tried google searching and I can't find sufficient answers for a lot of my questions, so please bear with me. (Note: I'm typing this on my XP laptop, not on my Linux laptop, because I can't get a wireless connection)

1. How do I get to use the Power Management that you see when you hit the "Help" button? I believe it's called GNOME Power Management, and on the screen, it has settings that lets you control CPU speed and stuff. The one I have right now just has settings for dimming the screen, and shutting down when battery is low.

2. I can't seem to get it connected to the wireless network. I did a few google searches and it keeps telling me to use an fdisk command. When I open up the command prompt and type what they say in, it tells me its unrecognized. If it helps, the text before I type in the command says <grub> or something along those lines.

Thank you guys in advance.

Additional Questions: (if you guys don't mind)
4. In power management, I set the laptop to do a blank screen if I close the lid. When I close the lid is completely messes up the screen (it's not black/"blank"). Any reasons why, and if so, is there any way to fix this or should I set it to "Do Nothing" when I close the lid?

5. How do I disable the double-clicking feature on the Touch Pad? (I only want to be able to double click with the buttons)

EDIT #2: If it helps anyone with these questions, I'm using an old Latitude D400.
EDIT #3: Question 3 was answered.

---

### Post by FreewheelinFrank on 2008-11-15
1) System>Preferences>Power Management

---

### Post by jmmL on 2008-11-15
I'm afraid I might not be of much help, but I'll try anyway.

1. Try right-clicking on one of the panels. There should be an add-to-panel section, click that. Then a list of little icons should appear, and one of them should be described as a "CPU speed governor" or something like that. That at least will display your current CPU speed, but I don't know how to modify it on Xubuntu to make the CPU speed controllable by the user. A Xubuntu user is needed here..

2. I'm afraid I can't help here either

3. Finally, I can be of use! I think Xubuntu probably comes with "Pidgin". It's a multi-protocol IM client, which means it can do AIM, MSN Messenger, Jabber, Yahoo, etc. This should get you started, but there might be a better AIM-only client out there for linux, I don't know.

Pidgin can be accessed through Applications > Internet > Pidgin instant messenger

---

### Post by marshall.robert on 2008-11-15
2. fdisk and grub are in no way related to wireless, ill try and help you with that in a bit though when i get to my desktop. can you tell me what wireless card you are using?

3. there should be a program called pidgin (should be in the internet section of your apps menu) which you can use as an alternative to AIM

---

### Post by Linuxperiment on 2008-11-15
> **FreewheelinFrank said:**
> 1) System>Preferences>Power Management

Yeah when I went there, I clicked on the "Help" screen and in that image was the power management I wanted :)

---

### Post by Kevbert on 2008-11-15
Welcome to Ubuntu.
Wireless - first we need to find out what wireless card/chipset you have. Go to Applications-Accessories-Terminal and type in 
```
lshw -C network
```
Please post the product and vendor information here for the wireless interface.  From there we can work out what wireless firmware drivers are required.

---

### Post by Linuxperiment on 2008-11-15
> **Kevbert said:**
> Welcome to Ubuntu.
Wireless - first we need to find out what wireless card/chipset you have. Go to Applications-Accessories-Terminal and type in 
```
lshw -C network
```
Please post the product and vendor information here for the wireless interface.  From there we can work out what wireless firmware drivers are required.

Okay I did it, and here's what I got:

Product: NetXtreme BCM5705M Gigabit Ethernet
Vendor: Broadcom Corporation

---

### Post by Linuxperiment on 2008-11-15
Anyways, I added up some new questions if you guys are interested. Sorry for the bombardment of them, I just have a lot of them.

---

### Post by Kevbert on 2008-11-15
BCM5705M - that's the wired connection. If there isn't another network product we'll need to try another terminal command:
```
lspci
```
Please look for the line with wireless lan and report back the make, model and revision.

---

### Post by Linuxperiment on 2008-11-15
I typed it in, and it looks like there is nothing for wireless. If it helps at all, it's an old Latitude D400. I googled a question asking if latitude d400s have wireless cards, and they said yes. Now I'm not so sure...

---

### Post by handydan918 on 2008-11-15
> **Linuxperiment said:**
> I typed it in, and it looks like there is nothing for wireless. If it helps at all, it's an old Latitude D400. I googled a question asking if latitude d400s have wireless cards, and they said yes. Now I'm not so sure...

According to [this cnet review]("http://reviews.cnet.com/Dell_Latitude_D400_series/4507-3121_7-21207517.html?tag=mncol;psum")it appears that they did not come with an on-board wireless chip.

---

### Post by Linuxperiment on 2008-11-15
Thanks for that! I checked the service tag/code on my laptop and it says that my Latitude DOES have a wireless card.

---

### Post by Kevbert on 2008-11-15
I've had a look at an old review and it may have an Intel 2100 or a Broadcom BCM4318. Do either of these show up when you use
```
lspci
``` ?

---

### Post by Linuxperiment on 2008-11-15
Nope, neither of those show up. Does this mean that Linux does not recognize the drives?

---

### Post by Kevbert on 2008-11-15
It means that wireless has not been detected. Is there a front panel switch you use to turn wireless on and off ? If so, press it once and then run ```
lspci
``` again.

---

### Post by marshall.robert on 2008-11-15
a note on the wireless being switched off with a killswitch/button i have found that if i boot with my wireless switched off it will not work unless i reboot with it switched on...

moral being, you may have to reboot after switching it on...

---

### Post by Linuxperiment on 2008-11-15
Thanks for all the tips guys. I'll try these later and see if they work.

---

### Post by Kevbert on 2008-11-16
If that doesn't work please supply the output of the following:
```
lspci > hardware.txt
iwconfig > hw2.txt
```
These will be files hardware.txt and hw2.txt which will be saved in your home directory which you can copy to USB/floppy and attach to a new post. Also please give the exact model of the PC (it should be on a sticker somewhere) and I'll try and work out what the wireless is.

---


---
title: "Cannot Boot into 11.10 Get a weird error."
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Aydos on 2011-10-02
I have not used Ubuntu since 10.04 and I thought I would give it a try again.

After I install it and try to boot into it for the first time on my desktop computer I get the grub screen I pick Ubuntu and not my Win7 install. It goes to a black screen with white text that appears to be running a diagnostic or something and it says pass for anything then I get stuck at a blinking cursor and the last thing it says is Checking for running unattended-upgrades and it will not go a way from that.

It did this on multiple installs from different media and with different ISOs. I can run older versions of Ubuntu fine and I loaded Fedora 16 and OpenSUSE 12.1 just fine. I was running Fedora 15 before this.

Anyone have any ideas?

---

### Post by Aydos on 2011-10-02
Bumping from page 3

---

### Post by drs305 on 2011-10-02
The blinking cursor could mean you need to install a video driver. You can try to boot with the 'nomodeset' option from the Grub menu to see if this helps.

At the Grub menu, press 'e' to edit the menuentry.
Cursor to the end of the 'linux' line. Remove the 'quiet splash' and add 'nomodeset'.
Press CTRL-x to boot.

If it boots, try to add your video driver via "Additional Drivers" and if it finds one install it and reboot.

---

### Post by Aydos on 2011-10-03
Thank you for the suggestion.

I tried it and then when I hit ctrl and X to boot it goes back to the black screen does a couple of more things that say ok and then has the last thing saying  Checking for running unattended-upgrades.

At that point it goes to a new line with a blinking cursor and stays there forever.

Any other ideas?

---

### Post by Rubi1200 on 2011-10-03
Please post the full specifications for the computer, especially RAM and graphics card.

Thanks.

---

### Post by Aydos on 2011-10-03
i7 920 Processor
6 Gigs of Corsair XMS DDR3 Ram
NVIDIA 275GTX Video Card by EVGA
EVGA X58 Motherboard
650gb Western Digital Caviar HDD

Let me know if you need anything else.

---

### Post by Aydos on 2011-10-03
bump

---

### Post by Iowan on 2011-10-03
Moved to Ubuntu +1 (Oneiric Ocelot)
Remember - (no more than) 1 bump/24 hours is considered polite.

---

### Post by mickeyfuqinp on 2011-10-03
i had the same problem.. 

nomodeset did get me a little further! haha.. 
its most certainly a GPU/driver problem.. 

i used alt + f2 to get to a command prompt, tried to open unity, and got a bunch of errors :(

hopefully someone whom is more knowledgeable can step in and give a point in the right direction.. its been a while since i've been involved with any linux distro's, let alone ubuntu..

---

### Post by alphacrucis2 on 2011-10-03
> **mickeyfuqinp said:**
> i had the same problem.. 

nomodeset did get me a little further! haha.. 
its most certainly a GPU/driver problem.. 

i used alt + f2 to get to a command prompt, tried to open unity, and got a bunch of errors :(

hopefully someone whom is more knowledgeable can step in and give a point in the right direction.. its been a while since i've been involved with any linux distro's, let alone ubuntu..


Did you test it from the Live CD before installing?

---

### Post by Aydos on 2011-10-03
In my case it works on the live cd just not after the install.

---

### Post by cariboo on 2011-10-03
Can you start in recovery mode, and once at the menu select resume, then login, and type:

```
startx
```

It may take you to a working desktop.

If that works, start the same way, but after login type at the prompt:

```
sudo service lightdm start
```

---


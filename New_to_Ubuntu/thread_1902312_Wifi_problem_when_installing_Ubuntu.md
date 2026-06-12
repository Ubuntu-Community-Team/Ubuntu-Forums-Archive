---
title: "Wifi problem when installing Ubuntu"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by jiryan2316 on 2011-12-30
Ladies and Gentlemen;
 
I've been trying for three days now to replace my crappy windows 7 with Ubuntu Linux because I honestly believe that Microsoft may be a tool of the devil.  The problem is that when I try to load it from the disk I made, It will not get past the wifi page, even if I have it plugged into my router, as I do now.  I boot it from the disk, and basically I am getting to use it as live, but I stop and restart teh computer and it goes back to windows.
 
So, technical specs:
 
Toshiba A505D-S6987
 
AMD Turion II Ultra  Dual Core M600
 
2.4GHz
 
4 GB installed RAM
 
64 Bit
 
HL-DT-ST DVDRAM GA10F ATA
 
REALTEK RTL 8191SE Wireless LAN 802.11n PCI-E NIC
 
Please help me.  I know the truth is out there.  I want to see the matrix.  I want to be free of the shackles which Microsoft has forced upon me.  I want to take the red pill.  I WANT TO TAKE THE RED PILL!!!!!!
 
Thanks in adveance

---

### Post by Stovey on 2011-12-30
> **jiryan2316 said:**
> ...I honestly believe that Microsoft may be a tool of the devil..

Lol.  Did you select "Install Ubuntu"?

---

### Post by Megaptera on 2011-12-30
> **jiryan2316 said:**
> I boot it from the disk, and basically I am getting to use it as live, but I stop and restart teh computer and it goes back to windows.

If I read that right, you haven't installed Ubuntu, so Windows will still be there while you're booting from the live CD.

---

### Post by jiryan2316 on 2011-12-30
Yes.

---

### Post by jiryan2316 on 2011-12-30
Right.  When I click on "Install Ubuntu", then it goes until the wifi page and gets hung up on something.  It will stay there indefinitely.

---

### Post by jiryan2316 on 2011-12-30
Unless it takes more than a few hours to install Ubuntu.

---

### Post by 2F4U on 2011-12-30
I don't remember having a wifi page during installation. I think I didn't even have a page for network configuration.

---

### Post by MG&amp;TL on 2011-12-30
"Wifi page"-screenshot?

---

### Post by jiryan2316 on 2011-12-30
It would be a lot easier if someone could just telnet in and do it.  Ubuntu should offer that.

---

### Post by MG&amp;TL on 2011-12-30
```
sudo apt-get instal openssh-server
```

Done. :D

Seriously, though, that would be quite a big security risk.

---

### Post by jiryan2316 on 2011-12-30
I was just harkening back to the days when I could call tech support at my base and get them to just fix the stuff.  I would never let anyone actually into my computer.  Too much banking stuff on it.
 
But back to my problem. What can I be doing wrong?

---

### Post by NilPointer on 2011-12-30
> **jiryan2316 said:**
> It would be a lot easier if someone could just telnet in and do it.  Ubuntu should offer that.

In *nix world, there's ssh for that... And I wouldn't recommend to offer taking control of your machine to everyone over internet. Even that forums seem friendly, there always may be bad people, intending to do malicious actions to you like stealing data or planting backdoor. So, even if you want to do something like that, you'd better request help of trusted person.

---

### Post by chipbuster on 2011-12-30
Did you verify the md5sum of the disc? It might be caused by a bad install disc.   There is definitely a wifi screen for those of us with wireless cards--it asks if you'd like to connect the computer to the network now, or do it later. If I understand you correctly, the issue is that once you get to that stage in the install sequence, the installer hangs and crashes?

---

### Post by wolfen69 on 2011-12-30
I always set up my wifi from the top panel when installation first starts, then just skip past the "wifi setup" page. It doesn't let you hit "continue"?

---

### Post by nothingspecial on 2011-12-30
This is probably way off the mark but there is a bug in the installer where on some setups you can't see the bottom of the window to click ok (or apply or whatever it says).

If that is the case then you need to hold down Alt then click on the window to drag it up past the top of the screen so you can get to the bottom if you see what I mean.

---

### Post by GregA on 2011-12-30
Upon installing Kubuntu recently, I do recall one screen in the install sequence asks about network connections - and then requires you to type in the name of your network (ssid), and then to select it from a popup list, and finally, to enter your network password/key.

But I think you can still install without connecting to the internet, so perhaps you can gave that method a try.   At the end of the install (it takes 45 to 90 minutes or so), you will get a chance, after restarting your PC, to scan and setup the wireless network.

None of the above is required if in fact, you are already connected to the internet via an ethernet cable or dsl.

(edit:   so, another approach is to temporarily connect the internet via an ethernet cable.)

Hope this helps.

---

### Post by Stovey on 2011-12-30
> **wolfen69 said:**
> I always set up my wifi from the top panel when installation first starts, then just skip past the "wifi setup" page. It doesn't let you hit "continue"?

That's what I do too!  Before selecting "install Ubuntu", I click on the wireless network icon at the top right of the screen.  Then I enter my wireless network key (a ten digit number).  That way, the computer has access to wireless before and during the installation.

---

### Post by oldos2er on 2011-12-30
Changed thread title.

---


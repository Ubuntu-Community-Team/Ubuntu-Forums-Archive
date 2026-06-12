---
title: "Live CD Questions..."
date: 2008-07-27
forum: New to Ubuntu
---

### Post by NJ0E on 2008-07-27
I have downloaded the CD, Burtn the ISO and have started looking at the program.  My question concerns my USB Wireless Lan card.  Of course I own a D-Link DWL-G120 (aarrrggg).  I have managed to locate the prisma02 inf files on my windows and have copied them to a file that "I" can find.  When in Live CD I install the drivers using the ndisgt route.  I can see my wireless in the drop down menu from the available connecitons in the upper right tool bar.  However, when I click on it to connect/select to use nothing happens. The radio button does not highlight (for any of the available connections) and firefox cant find a connection.  

What have I done/not done?  

Thanks for the help.!!

Joe

---

### Post by sdowney717 on 2008-07-27
so, you see available wireless connections?
do any of them require security settings?

---

### Post by NJ0E on 2008-07-27
Of teh 4 that I can see; one is open, and three are wpa security.  Mine is one of the ones with wpa -- I tried to set upi my wpa pword, but the network "?" area wouldnt let me select my router/network at all.

---

### Post by maybeway36 on 2008-07-27
Sometimes doing wireless requires muddling around in /etc/network/interfaces. For my network (which is WEP) I did something like this:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid NameOfNetwork
wireless-key xxxxxxxxxx
```

---

### Post by caljohnsmith on 2008-07-28
Just a small question, but when you installed your wireless card windows driver with ndisgtk, did you have both the .inf and .sys file in the same directory? You mentioned you only copied over the .inf file, and both the .inf and .sys files are necessary for ndiswrapper to install the driver properly.

---

### Post by NJ0E on 2008-07-28
I copied both files.  I am currently at work, when I get home I'll am going to look at the terminal window to see if that will help.  Basically my question is/was -- while in live CD do all functions working?

---

### Post by caljohnsmith on 2008-07-28
Yes, the Live CD is fully functional. By the way, I would highly recommend that you disable encryption on your router (if you are using encryption) and try to connect that way first; once you get that working, then you can try with WEP/WPA encryption.

---

### Post by NJ0E on 2008-07-28
OK, Will try that when I get home.  Just a little leary about doing that as there are a lot of "jackers" in the area.

Thanks Joe

---


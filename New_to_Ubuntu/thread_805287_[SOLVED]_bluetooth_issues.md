---
title: "[SOLVED] bluetooth issues"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by scotcella on 2008-05-23
Hi there,

Been reading up in various bluetooth searches available on this forum.

I am still having issues with my bluetooth connection between my mobile and laptop. 
I have already paired my mobile and laptop which is working fine.

From my laptop I am able to send pictures but cannot receive anything (into the laptop).

I also noticed that when I login ubuntu there is a pop up that says that bluetooth is enabled to receive incoming files. 

I have dual booting in Vista and both incoming and outgoing bluetooth pictures work fine.

If it helps, I have a Nokia N95 and a SonyVaio laptop.

Many thanks in advance

---

### Post by scotcella on 2008-05-25
Bump...

Can anyone help me with this?

Many thanks in advance

---

### Post by Inxsible on 2008-05-25
To send files to your computer, you need to select the file to send in the phone and then search for available devices. If you have already paired your phone to the laptop and if you have saved it, it should also show up under My Devices in your phone.

Select your computer and then your laptop should receive the file. Make sure you have installed gnome-bluetooth package.

---

### Post by prshah on 2008-05-25
> **scotcella said:**
> 
From my laptop I am able to send pictures but cannot receive anything (into the laptop).
I also noticed that when I login ubuntu there is a pop up that says that bluetooth is enabled to receive incoming files. 


Right click the Bluetooth icon and select "Preferences", then ensure the following:

1) On the first Tab, ensure "Mode of operation" is "Visible and connectable for other devices"
2) Your phone appears in "Bonded devices" at the bottom, and is trusted. (Lock and Star icon)
3) In the "General" tab, "Receive files from remote devices" is enabled 
4) "Automatically authorise incoming requests" is enabled (checked).

---

### Post by scotcella on 2008-07-19
This issue was solved by downgrading the blue utiliz package to v3.19.

[http://technology-included.blogspot.com/2008/07/using-bluetooth-on-hardy-ubuntu-804.html](http://technology-included.blogspot.com/2008/07/using-bluetooth-on-hardy-ubuntu-804.html)

---


---
title: "Install Question"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by mrwilson on 2008-08-29
Completely new user to Ubuntu and Linux here.  Experienced windows user
I installed a dual boot Ubuntu and XP system that works fine.
My problem is that Ubuntu will not recognize my wireless system that works perfectly on the XP side.
On the advice of a friend I downloaded WIFI Radar to act as an intermediary between the wireless and ubuntu.  Ubuntu knows the wireless device is in the USB port, but has no interface to go with it.  The wireless roaming config section does nothing with it.  and one log file that I looked up said there was no link to the connection on startup.
Ok, got the wifi-radar file on ubuntu (desktop apparently) and what do i do now?  How to install it? (is a tar file of course.)I can extract it in archive manager, but every file I click on just opens that file and shows me the scripts inside.  Not interested in scripts, just want to install it:) In otherwords, wheres the exe file, how do you self extract or install such a file?  If I go to terminal(again apparently desktop dirctory) and type sudo make install it just laughs at me.

Really clueless here and would appreciate some help

---

### Post by Bachstelze on 2008-08-29
What kind of Wifi adapter do you have? Chances are you wil need to install drivers for it.

---

### Post by mrwilson on 2008-08-29
Its a linksys router and adapter.  A few years old.  I will give that a try, but i dont see any linux style drivers on the disk.  Of course what you say makes perfect sense.  Let me give that a try and return to this thread.  

thank you for your quick response

---

### Post by mrwilson on 2008-08-29
Unfortunely the driver disk is purely windows and doesnt run on ubuntu.  The drivers are installed on the windows side but I knw that doesnt matter.

I will check with linksys to see if there are linux drivers for that router.

thanks again

---

### Post by Bachstelze on 2008-08-29
The router doesn't need drivers, it's the adapter that does. In a terminal, run [font="Courier New"]lsusb[/font] and paste what you get.

---

### Post by mrwilson on 2008-08-29
Yes I know the adapter needs the drivers.  My mistake.

Bus 002 Device 002 ID 0D8C:0201 C-Media

Bus 001 Device 002 ID 13B1:000a Linksys

I have checked with linksys, they do not supply any linux drivers with the products I have.

---


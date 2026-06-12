---
title: "Please help a happy idiot go about his business"
date: 2006-09-12
forum: Programming Talk
---

### Post by Ace Ironballs on 2006-09-12
Hi 
I'm a total newcomer to Ubuntu [5.10] and Linux. I have installed the system and i am really impressed.
The problem i have is probably ridiculous to you guys but please be  be patient. I am trying to set up a network connection using a BT Voyager 105. Everything was going swimmingly until it got to the part where i needed to change the synch .bin file from synch o1 to synch 03 which is needed for the Voyager 105.
Are you still with me??? this is where the problem lies...
I have the synch03 file in my home folder and i want to get it into /etc/eciadls/ but every time i try this i keep getting a dialogue box popping up to tell me i don't have permission.

Any suggestions please

---

### Post by kairu0 on 2006-09-12
Open a terminal and try:
```
sudo cp /home/username/synch03.bin /etc/eciadls/
```

You, as a user, do not have permission to edit /etc files. Use sudo to temporarily get access.

---

### Post by Warbo on 2006-09-12
> **Ace Ironballs said:**
> Hi 
I'm a total newcomer to Ubuntu [5.10] and Linux.

You should really check out the help wiki at [https://help.ubuntu.com/community](https://help.ubuntu.com/community) since it explains pretty much every newbie type question (permissions, networking, etc.). You will probably want to take a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) since it explains permissions.

If you get the chance then please write a Wiki page about your modem here 
[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem) because I don't know if any of those guides include your modem. You will need a Launchpad.net account to edit the Wiki, but you might already have one if you got CDs shipped to you.  (I wrote the eagle-usb one and the ueagle-atm one, but got rid of my BT Voyager modem in favour of a BT Voyager 205 router, since it is much easier to use and by this time I became sick of software modems [I used to use a SmartLink dial-up winmodem too!])

---


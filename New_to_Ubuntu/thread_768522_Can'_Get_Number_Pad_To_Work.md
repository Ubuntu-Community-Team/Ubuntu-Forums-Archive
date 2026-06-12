---
title: "Can' Get Number Pad To Work"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by OisinT on 2008-04-26
I've tried a few different settings under Keyboard in Preferences, but seems like no matter what I try I can't get my number pad to work.
It was working fine before upgrade to Hardy.
I don't recall making any selections during upgrade that would have changed keyboard settings.
help appreciated.

---

### Post by nicedude on 2008-04-26
Are you talking about the Numpad on a standard keyboard or a stand alone keypad ( like USB one )? If you mean the standard one I am assuming you pressed the NUM lock key but I will say anyway just in case.

---

### Post by OisinT on 2008-04-26
> **nicedude said:**
> Are you talking about the Numpad on a standard keyboard or a stand alone keypad ( like USB one )? If you mean the standard one I am assuming you pressed the NUM lock key but I will say anyway just in case.
yeah I mean the number pad on the standard keyboard.  lol... and yeah, I made sure num lock was was on. :)

---

### Post by OisinT on 2008-04-26
> **OisinT said:**
> yeah I mean the number pad on the standard keyboard.  lol... and yeah, I made sure num lock was was on. :)
it seems to act as if the num lock key isn't working though.  ie when I press "5" it does this:
e standard e standard 
e standard e standard

---

### Post by didli on 2008-04-26
Same problem here. But if I Hit 5, I get the login session manager to show up :confused: ...
Strangely enough, only numbers are affected.

---

### Post by bronxbomberz41 on 2008-04-27
Hi I am having similar problems since I upgraded to Hardy.  I don't have a Num Lock key on my keyboard oddly enough (its a Logitech Bluetooth Desktop MX5000 keyboard and it has a "Clear Calc+ button instead).  It always defaulted to Num Lock being on I guess.  I can't figure it out either.  I would really appreciate some help because I hate using the numbers at the top of the keyboard.  

Also, they "+-*/" keys around the number pad aren't working either.  They seem  to occasionally act like PgUp/PgDn etc keys.

Thanks

---

### Post by didli on 2008-04-27
**Solved for me**
The solution here : [https://bugs.launchpad.net/ubuntu/+bug/197771](https://bugs.launchpad.net/ubuntu/+bug/197771)
Here's what works for me : 
> 1) System
2) Preferences
3) Keyboard (Tab: Mouse Keys)
4) **Uncheck "Allow to control pointer using the keyboard"**.
For some reason, this option was activate for me. **Desactivate as requested & Reboot** to have access again to your numpad (for some users, they also had to purge and reinstall numlockx again + the trick)
```
sudo apt-get remove --purge numlockx
sudo apt-get install numlockx 
```

---

### Post by BioGeek on 2008-04-27
I had the same problem after upgrading to 8.10.

I just wanted to confirm that the resolution described by didli worked for me (I didn't need to reinstall numlockx).

Thanks! :)

---

### Post by jubajuba on 2008-04-28
I can also confirm that the solution here worked.
I was starting to get annoyed that my numpad didn't work, wouldn't have noticed the numpad-to-stear-mouse thingy by my self. Thanks! :)

---

### Post by bronxbomberz41 on 2008-04-28
I also would like to confirm that this worked!!  However I after simply unchecking the described box I got my numpad working!!

Thanks!!

---

### Post by Butthead on 2008-04-28
Hmm, I can't seem to find this "Preferences" that the bugfix keeps referring to? :confused:

---


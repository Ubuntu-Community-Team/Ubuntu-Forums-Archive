---
title: "Tulong! My usb thumb drive won't mount anymore!"
date: 2009-01-21
forum: Philippine Team
---

### Post by randytan on 2009-01-21
Hi Guys and Gals!

I need some help!

I used to be able to use USB thumb drives in my office notebook running 8.10 (Intrepid) but it will not work now.

Everytime I plug in a USB thumb drive, I see it in the directory list but it will not mount. When I click on the icon depicting the drive, it will always generate the following message:

[INDENT]Unable to mount location
Failed to execute child process "gnome-mount"
(No such file or directory)[/INDENT]

Is there a way to fix this?

This problem started when I got a USB drive from a colleague whose workstation was apparently infected by a virus. My colleague's workstation is running XP. Even when the offending bug was deleted, it would now display the above error message everytime a USB drive is plugged in.

Any assistance will be appreciated.

Thanks.

Hope to hear from y'all soon.

---

### Post by dannybuntu on 2009-01-21
Hi, I'm just curious, sir, but I really don't know the answer to your problem. Pero have you tried using the usb in Windows? Maybe check if it the fs has been corrupted. Otherwise, di ko talaga alam.

---

### Post by randytan on 2009-01-21
Hi there.

The USB works when used with Windows and Mac.

Sa Utuntu na lang siya talaga hindi nagana.

Nakakainis na nga.

It would normally work before but now it won't! :(

---

### Post by loell on 2009-01-21
reinstall mo ang gnome-mount.

```
sudo apt-get install gnome-mount
```

---

### Post by guitar_man on 2009-01-21
nasubukan mo na ba yung force mount sa terninal?
yun madalas kop gawin...

---

### Post by kiminaiseah on 2009-01-21
try this

sudo apt-get autofs

---

### Post by Nessa on 2009-01-21
Nangyari sa akin yan minsan. Ang solution sa case ko, proper unmounting sa other OS (safely remove or eject). Good luck. :D

---

### Post by dannybuntu on 2009-01-22
> **Nessa said:**
> Nangyari sa akin yan minsan. Ang solution sa case ko, proper unmounting sa other OS (safely remove or eject). Good luck. :D

I remember now. Me too, but that was during improper shutdown naman. HD naman ang ayaw magmount.

---

### Post by randytan on 2009-01-23
> **loell said:**
> reinstall mo ang gnome-mount.

```
sudo apt-get install gnome-mount
```

Thanks loell!

That hit the spot!

It's working again! :guitar:

By the way, any idea why this happened to me?

Thanks.

---

### Post by randytan on 2009-01-23
> **guitar_man said:**
> nasubukan mo na ba yung force mount sa terninal?
yun madalas kop gawin...

Hi guitar_man,

Yep, tried this too to no avail.

The script that loell sent did the trick, it's back to normal now. :D

---

### Post by randytan on 2009-01-23
> **kiminaiseah said:**
> try this

sudo apt-get autofs

Hi kiminaiseah,

Out of curiosity, what does this script do?

---

### Post by randytan on 2009-01-23
Hi Nessa & dannybuntu,

Those weren't the cases at all, they were mounted automatically and were removed properly.

Thanks for the info though, at least now we all know to be more careful when pulling out our thumb drives ;)

---

### Post by Script Warlock on 2009-01-23
siguro nakalimutan mo unmount ang usb kaya nagkaganyan..ako ganun din ang nangyari nasira usb ko at external hard drive nadali pero pinalitan ko ng bago and everything is normal again...

---


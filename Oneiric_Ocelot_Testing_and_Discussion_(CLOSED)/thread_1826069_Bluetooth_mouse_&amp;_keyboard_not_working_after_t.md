---
title: "Bluetooth mouse &amp; keyboard not working after today's updates"
date: 2011-08-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cmccauley on 2011-08-16
Hi all,

Just updated and now my mouse and keyboard will pair but will not function. They show up in dmesg but that's about it. 

Chris

---

### Post by colorprint on 2011-08-16
I have the same problem :(

---

### Post by SoFl W on 2011-08-16
> **cmccauley said:**
> Hi all,
Just updated and now my mouse and keyboard will pair but will not function. They show up in dmesg but that's about it. 
Chris

Question, under your username it says you are still using "JauntyJackalope" is that true?
"Ubuntu Jaunty Jackalope (testing) "

---

### Post by cmccauley on 2011-08-16
> **SoFl W said:**
> Question, under your username it says you are still using "JauntyJackalope" is that true?
"Ubuntu Jaunty Jackalope (testing) "

No, that's the last time I updated that info. The sig contains more recent information. 

I've raised a bug on this because there's a segv in the bluetooth manager which may be causing it.

---

### Post by capoeirabg on 2011-08-17
My Microsoft 7000 bluetooth keyboard also stoped working. I have managed to paired it but no input information. Hcidump give me normal activity but no input on the screen. Tried with blueman ans also it pairs but with no input or so ever.

---

### Post by capoeirabg on 2011-08-18
More details. Keyboard works but only in console, if i entered Ctrl+Alt+F1/F2 then the keyboard works like a charm. But as soon as i bring the X up every things stops. Do I have to manually add keyboard in X configuration file...

---

### Post by richlyn9 on 2011-08-25
Same [roblem with me.

I ran an update yesterday and realized  today that i cannot login as the keyboard and mouse wont work(detect).

may be i need to unplug and replug and see if that works.
Else i may have to Chroot from Lucid to Oneric.

BTY what package needs to be updated to fix this issue (hoping that the update to fix this is released)?

---

### Post by richlyn9 on 2011-08-25
> **richlyn9 said:**
> Same [roblem with me.

I ran an update yesterday and realized  today that i cannot login as the keyboard and mouse wont work(detect).

may be i need to unplug and replug and see if that works.
Else i may have to Chroot from Lucid to Oneric.

BTY what package needs to be updated to fix this issue (hoping that the update to fix this is released)?



Found this on a different thread... looks like this should wor 

"[B]select recovery mode from the grub menu, then once at the menu select drop to netroot, then run the following command:

Code:

mv /run/udev /run /udev.old

If that doesn't work, you could use a live cd and chroot your Oneiric / partition, open a terminal and type the following commands:

Code:

sudo mount /dev/sdX /mnt
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt

then run the move command above.

Note: /dev/sdX = your Oneiric partition.[/B]"

---

### Post by cmccauley on 2011-08-25
I started this thread. When I updated two days ago, the mouse and keyboard both worked. I didn't need to do anything. I noticed that there was a crash in the dmesg log, reported a bug etc.

Chris

---

### Post by richlyn9 on 2011-08-26
Looks like the faulty package has been fixed..
Which ones do i need to upgrade ..?
Coz i have so many upgrades which i don't want to right now, i rather upgrade those to fix my mouse and keyboard only.

---

### Post by cariboo on 2011-08-26
> **richlyn9 said:**
> Looks like the faulty package has been fixed..
Which ones do i need to upgrade ..?
Coz i have so many upgrades which i don't want to right now, i rather upgrade those to fix my mouse and keyboard only.

When running a testing version, don't try to update selectively, do full updates at least daily. You are running a testing version to be able to report bugs, not just because it's the latest and greatest.

---


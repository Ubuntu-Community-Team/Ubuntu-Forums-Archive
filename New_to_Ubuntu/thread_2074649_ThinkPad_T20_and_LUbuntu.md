---
title: "ThinkPad T20 and LUbuntu"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by Pallottino on 2012-10-22
Hello to everyone !
I am a very beginner in Ubuntu world.
I want to try Ubuntu, so I took an old IBM ThinkPad T20: PIII at 700MHz, RAM 256 M, HDD 3 G, AGP 2x S3 Savage IX graphic card.
Following suggestions, I decided a light install, and I tryed Lubuntu 12.10 alternative. Install went OK, but at booting I have a screen with green and grey lines. The computer seems to work, because I can access the terminal, but I am not able to correctly see the screen. The graphic card seems to work, I was able to run DamnSmallLinux.
Any help to correct the problem will be very appreciated; remember I am a very newcome in Ubuntu.

Sorry for my English.

Thanks, Pallottino

---

### Post by roger_1960 on 2012-10-22
Hi

You may be very low on disk space, 3G is not much!

In terminal enter

> df -h

and post the results back here.

It could be a graphics problem.  Suggest you search these forums and google for your card + ubuntu and see what is there.

Roger

---

### Post by black veils on 2012-10-22
i would recommend trying [antix]("http://distrowatch.com/table.php?distribution=antix") (best performance) or [bodhi linux]("http://distrowatch.com/table.php?distribution=bodhi") instead.

---

### Post by genoobie on 2013-01-30
Same problem, I have not resolved to date.

---

### Post by genoobie on 2013-01-30
I found out the savage driver on 12.10 is new and it does not work.  Try 12.04 and you may want the alternate install given the age of the machine.  Do not update!  That will break the install.
 
Once you've installed use terminal to:
 
echo "xserver-xorg-savage-video hold" | dpkg --set-selections
 
Then update to your heart's content (that will prevent the new version from being installed).  Good luck!

---


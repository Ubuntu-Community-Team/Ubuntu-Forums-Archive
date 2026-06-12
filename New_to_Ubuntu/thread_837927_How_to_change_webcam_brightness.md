---
title: "How to change webcam brightness?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Bonzzai on 2008-06-23
I plugged in my webcam, and surprisingly everything worked perfect right off the bat. (Just for your information, though, it's a Logitec Quickcam.)

The only problem I'm having is that the brightness is a bit low. How could I fix this? If you need any more information, please don't hesitate to ask :]

---

### Post by AndThenWhat on 2008-06-23
[http://ubuntuforums.org/showthread.php?t=651075](http://ubuntuforums.org/showthread.php?t=651075)

If you are using the gspca driver, then post #3 is exactly what you need.

---

### Post by Bonzzai on 2008-06-23
> **AndThenWhat said:**
> [http://ubuntuforums.org/showthread.php?t=651075](http://ubuntuforums.org/showthread.php?t=651075)

If you are using the gspca driver, then post #3 is exactly what you need.

Okay, thanks bunches. I really do not have the time to test that right now, but I definitely will. Does anyone know of maybe a program that could do this? ; - ;

---

### Post by undertakingyou on 2008-06-23
I know that with cheese, the program to take pictures with you webcam there isn't a brightness option.  But with ekiga, a softphone application that can do video conferencing there is a brightness option for the video there.  Don't know if that helps. I guess what it really boils down to is what software you are using now and what you will use your webcam for.

---

### Post by Bonzzai on 2008-06-23
Well, I followed that link, and it seems to have worked, thanks a bunch. One quick, and hopefully final, question. I'm looking for the Linux equivalant of something like Windows Movie Maker? And also something that I can use to record video (with sound) from my webcam. That would be awesome, and thanks for the help :]

---

### Post by tmoney438 on 2009-05-09
> **Bonzzai said:**
> Well, I followed that link, and it seems to have worked, thanks a bunch. One quick, and hopefully final, question. I'm looking for the Linux equivalant of something like Windows Movie Maker? And also something that I can use to record video (with sound) from my webcam. That would be awesome, and thanks for the help :]



cheese can record video and sound i believe. but im positive that this program is the movie maker program...i haven't used it but at a glance it looks to be just like windows movie maker. its is called Kdenlive . it should be available in the synaptic. goodluck.

---

### Post by CarpKing on 2009-05-16
I believe PiTiVi is the chosen video editor for a GTK environment.  I haven't used it heavily, and it's still a young project, but it may already do what you need.

---

### Post by opticks on 2011-11-29
> **AndThenWhat said:**
> [http://ubuntuforums.org/showthread.php?t=651075](http://ubuntuforums.org/showthread.php?t=651075)

If you are using the gspca driver, then post #3 is exactly what you need.


I am using the ALi m5602 webcam with the gspca_m5602 module and the gspca_main module. However I have no "/sys/modules/gspca" directory, and so cannot complete the commands in the link you provided. I know this thread is ancient, but Im having lighting issues with my cam and need a way to adjust settings at the system level. I would also like to be able to view my camera feed in realtime as I make adjustments which I understand is possible with Skype, however I cannot find it in the repositories and do not know how to use a .deb file (like the one Skype.com gives you). Thanks in advance for any help!

---

### Post by no2498 on 2011-11-29
you need to make the file as sudo /etc/modprobe.d/options
copy your settings to it then save it

---


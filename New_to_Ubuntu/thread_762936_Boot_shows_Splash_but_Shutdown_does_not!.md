---
title: "Boot shows Splash but Shutdown does not!"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by The Cake is a Lie on 2008-04-22
Hello, I am currently using 8.04 beta (which seems to be running fine so far). Anyway, my issue is when I shutdown my computer, it shows a bunch of text as to what its doing. My boot shows the splash fine, but shutdown does not. I believe I saw something about network (I have a Laptop that uses wireless internet, BTW). So that maybe the issue. Any fixes? Thank you!

---

### Post by maddog39 on 2008-04-22
You should probably submit this as a bug report on launchpad.net. I searched but did not find anything right off the top that matched your problem.

---

### Post by Kalidarn on 2008-11-25
I had this same problem using Ubuntu 8.10 Intrepid Ibex.

Googling about I found: [http://groups.google.com/group/bdosn/browse_thread/thread/e45cebc1c5d2fb96](http://groups.google.com/group/bdosn/browse_thread/thread/e45cebc1c5d2fb96)

[QUOTE="Khandakar Mujahidul Islam @ Oct 19 2007, 9:09 am"]
I've faced boot splash problem in my new ubuntu 7.10. It didn't show the
bootsplash image. I've solve it here. Problem was in /etc/usplash.conf.
Resolution was 1280x1024. It should be 1024x768 or 800x600.
So edit the /etc/usplash.conf. It would be like the following
xres=800
yres=600

Then run the following command
$sudo update-initramfs -u -k `uname -r`

Happy Linuxing.

-
Suzan[/QUOTE]

This fixed my problem I found I had 2048x1600 in there for some odd reason.

---


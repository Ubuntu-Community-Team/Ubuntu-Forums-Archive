---
title: "crystal eye and brightness"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by paristhecure on 2008-04-28
I am a totally newbie-2 day ubuntu 8.04 user-. Until now, i have two questions. I have a acer aspire 7720-6374. The first problem is my crystal eye web cam is not working. I have no idea how to make it working. The second one is after each turn of, the brightness reduces. I adjust it by Fn+right, but I wanna change it permanently to a higher brightness value. How can i do it?

Thanks a lot

---

### Post by linuxwizard on 2008-04-29
For your webcam try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work with your webcam post the results of the command > lsusb

---

### Post by paristhecure on 2008-04-29
I already tried ekiga before by reading other threads. It did not work.Here is my output:

ahmet@ahmet-laptop:~$ lsusb
Bus 007 Device 002: ID 5986:0102 Bison 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ahmet@ahmet-laptop:~$ 

Thanks I liked linux

---

### Post by linuxwizard on 2008-04-29
Your webcam is listed 3 up from bottom > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) > that is the driver you need for your webcam.

---

### Post by paristhecure on 2008-04-29
but how can i install the driver?

---

### Post by linuxwizard on 2008-04-29
Look here > [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)  > Installing UVC > may help you.

---

### Post by paristhecure on 2008-05-01
I can no longer post a new thread. every time i try, i got the message:
vBulletin Message

paristhecure, you do not have permission to access this page. This could be due to one of several reasons:

   1. Your user account may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system?
   2. If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.

Do you have an idea

---

### Post by cartisdm on 2008-05-01
Did you do the email activation already?  I don't know the rules but it could only allow you like 5 posts before you need to confirm your activation.  I'm going out on a limb here though

---

### Post by paristhecure on 2008-05-01
Yes, I activated and I did it again after this problem. But, didnt work. Strange?

---

### Post by cartisdm on 2008-05-01
> **paristhecure said:**
> Yes, I activated and I did it again after this problem. But, didnt work. Strange?

Also I just remembered, you might be required to make 5 posts (which I see you now have accomplished) before creating threads.  That's a forum's way of preventing bots that just spam up the place.

Try making a thread now:wink:

---

### Post by Red-Shield on 2008-10-28
dose any one know if there is a program out there so i can video confrence to a windows box and with ekigia do you need to pay or have an account i wish there was something like ssh for web cams and video confrence

---


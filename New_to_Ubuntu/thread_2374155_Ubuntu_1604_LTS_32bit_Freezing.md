---
title: "Ubuntu 1604 LTS 32bit Freezing"
date: 2017-10-13
forum: New to Ubuntu
---

### Post by stewartrose2 on 2017-10-13
Good Morning All,

   I have an Intel i3 Shuttle 4gb Ram 500gog HDD Nviada Graphics card
   running 16.04 LTS I386 32bit software... all updates and upgrade done.

   The problem is that the OS just totally freezes, cant ssh in, or get in via
   network, or from console DEAD...

   Can anyone suggest what logs are worth looking at please....

   Or has anyone seen this problem..


All the best from Alan

---

### Post by Autodave on 2017-10-13
When it freezes, what is appearing on your screen then?

What Nvidia card do you have and did you attempt to install any driver for the card? If so, where did you get the driver from?

---

### Post by stewartrose2 on 2017-10-13
Thank you for returning to my message

  When it freezes, the screen holds the last data that was there....
 
  I have not installed any driver for the Nvidia card, I will take it apart, and find out what card it is..

All the best from Alan

---

### Post by stewartrose2 on 2017-10-14
Good Morning,

  Well I got that wrong, it is a shuttle SZ68R5 which is an in built Video system (DVI HDMI)
  
All the best from Alan

---

### Post by mörgæs on 2017-10-14
This is strong hardware. Why do you run 32 bit?

---

### Post by stewartrose2 on 2017-10-14
Good Evening,

 The reason I am using 32bit this is Ham Radio Packet BBS software it will not work on 64bit

 I have changed the Video card to Geforce 405 (Nvidia)

 Turned of the video from the bias...

All the best from Alan

---

### Post by mörgæs on 2017-10-15
Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` to the terminal, run it and post the results in CODE tags.

---

### Post by stewartrose2 on 2017-10-16
Good Morning, I found the problem it is to do with HWE, I have had to go back to 14.04.1 version of Ubuntu..
all is working fine, but I dislike being so far behind in revisions...

Thank you for you help to everyone.....

All the best from Alan

---

### Post by mörgæs on 2017-10-16
Have you tried the almost-released 17.10?

Sadly the standard 32 bit ISO has been shut down but you can install from the minimal ISO.

---

### Post by inerstellar-cowboy on 2017-10-17
Has there been water damage to your computer?  (yes dumb question)

solution might be trying 17.10 as said above

---


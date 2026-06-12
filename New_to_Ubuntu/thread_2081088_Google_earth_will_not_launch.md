---
title: "Google earth will not launch"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by vegas89 on 2012-11-05
I have installed google earth on ubuntu 12.4  When I click on the icon the google earth logo appears briefly on the screen then goes away. What must I do to get this program to launch](*,)

---

### Post by newb85 on 2012-11-05
Please describe how you installed it.

---

### Post by vegas89 on 2012-11-06
I installed it using code script through the terminal.     
wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb)  //  sudo dpkg -i google-earth-stable_current_i386.deb  //  sudo apt-get install -f  Copied and pasted from Liberian Geek

---

### Post by newb85 on 2012-11-06
Is your architecture 32- or 64-bit?

---

### Post by rafaelfri on 2012-11-06
the same for me.
Downloaded GE7 from Google's website and installed with dpkg (and tried gdebi as well). Funny thing is that GE6 worked well.

I am running Ubuntu 12.10, 64 bits on a Dell Latitude laptop (intel graphics)

Crashlog:
[email]rafa@ubu:~/.google[/email]earth/crashlogs$ more crashlog-5099317c.txt 
Major Version 7
Minor Version 0
Build Number 0001
Build Date Oct 29 2012
Build Time 19:13:39
OS Type 3
OS Major Version 3
OS Minor Version 5
OS Build Version 0
OS Patch Version 0
Crash Signal 11
Crash Time 1352216956
Up Time 0.579369

Stacktrace from glibc:
./libgoogleearth_free.so(+0x1e9cfb)[0xf7632cfb]
./libgoogleearth_free.so(+0x1e9f43)[0xf7632f43]
[0xf77dc400]

---

### Post by wsscott on 2012-11-06
I just installed google earth on Ubuntu 12.10 using instructions found in this forum posted by "Jcolyn" from approximately 3 days ago. Please see the attached screen shot.

---

### Post by Pilot6 on 2012-11-06
Google Earth installs with no problems. Just download deb from Google site and run
sudo dpkg -i google-earth<press Tab>

---

### Post by vegas89 on 2012-11-06
Sorry my post got hijacked, I am running 64 bit.

---

### Post by Pilot6 on 2012-11-06
Then why you install a 32-bit package? That is the problem.

---

### Post by vegas89 on 2012-11-07
No that is not the problem! I just did an uninstall and did a reinstall making sure to choose the 64 bit option .  Just as before the logo will briefly appear  and then nothing else happens.

---

### Post by newb85 on 2012-11-07
Did you use dpkg again, or did you switch to a method that would ensure you had all dependencies covered?

---

### Post by vegas89 on 2012-11-07
I used code script through the terminal. I can do another uninstall again and download from another source. What would you suggest I do and could you supply the information needed to accomplish a successful download. Thanks!  [-o<

---

### Post by NikTh on 2012-11-07
Hi , 

please try with 6th version of Google-Earth . The current version is 7th . 

Download from here: [http://www.ubuntuupdates.org/package/google_earth/stable/main/base/google-earth-stable](http://www.ubuntuupdates.org/package/google_earth/stable/main/base/google-earth-stable)

Thanks

---

### Post by vegas89 on 2012-11-07
Thanks nikth, once again you have solved my problem, I downloaded the 64 bit package, took all of two minutes, did an install from dash, transfered the icon to my desktop and Bam the program fired right up and seems to work fine. Thanks  again for your help ):P

---

### Post by rafaelfri on 2012-11-08
So does anyone know why GE works on version 6  but doesn't on 7?

---

### Post by rburkartjo on 2012-11-08
ni appreciate the info i too way having a problem installing version7 of google earth. appreciate the link for version6. installed like a charm.

---

### Post by rburkartjo on 2012-11-08
ni just not my day spoke too soon google earth 6.0 still crashes after open. from what i have read problem if with the tool tips that is set to start as soon as you start earth. cant find a way to disable as of yet

---


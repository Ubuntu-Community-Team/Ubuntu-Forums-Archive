---
title: "XBox360 Controller Problems."
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Kn1v3s37 on 2008-09-28
First off, I've done lots of different things to get this thing working. I've found tutorials online for setting it up, and I set it up without a hitch, but it just doesn't work.

To elaborate, well, there is no elaboration. I've set it all up according to 2-3 different tutorials, but it's still just blinking away like I've never done anything.

I'm on Hardy with a Kubuntu install using Gnome (i know, why didn't I just install Ubuntu? Answer: I'm weird.).

---

### Post by Pro-reason on 2008-09-29
Does your infrared port work with other devices?

---

### Post by Kn1v3s37 on 2008-09-29
Sorry, I should have said that it's a wired MadCatz controller.

---

### Post by Kn1v3s37 on 2008-09-30
Solved, [http://ubuntuforums.org/showthread.php?t=825464](http://ubuntuforums.org/showthread.php?t=825464).

To sum up that post, download it from here:
[http://pingus.seul.org/%7Egrumbel/xboxdrv/xboxdrv-linux-0.2.tar.bz2](http://pingus.seul.org/%7Egrumbel/xboxdrv/xboxdrv-linux-0.2.tar.bz2)

Then, slap this into the terminal: 
```
sudo apt-get install libusb-dev libboost-date-time-dev libboost-date-time1.34.1 libboost-dev libboost-doc libboost-filesystem-dev libboost-filesystem1.34.1 libboost-graph-dev libboost-graph1.34.1 libboost-iostreams-dev libboost-iostreams1.34.1 libboost-program-options-dev libboost-program-options1.34.1 libboost-python-dev libboost-python1.34.1 libboost-regex-dev libboost-regex1.34.1 libboost-signals-dev libboost-signals1.34.1 libboost-test-dev libboost-test1.34.1 libboost-thread-dev libboost-thread1.34.1 scons
```

After, cd to the folder you unzipped the .tar.gz into, and type "scons" into the terminal. When finished, put the attached .sh file into the folder, and run it in the terminal by cd'ing to the folder and typing "sh xboxdrv.sh". This will start it, and make the light on the controller light up just like if it was in an xbox.

---


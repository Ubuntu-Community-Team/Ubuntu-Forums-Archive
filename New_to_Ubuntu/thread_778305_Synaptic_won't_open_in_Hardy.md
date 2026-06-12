---
title: "Synaptic won't open in Hardy"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by captgadget on 2008-05-02
and Add & Remove won't work. At least it opens and when I checked to load a program the ball just sat and spun.

---

### Post by nowshining on 2008-05-02
try opening up synaptic thru the terminal and paste if any error messages - ie: while trying to open synaptic or after closing synaptic...

---

### Post by nefrin on 2008-05-02
I've had issues where Synaptic won't open for me either. so far, I have been able to fix the issue by opening up the system manager, killing the synaptic process (which is running even though I don't have the program open), and trying to restart the program.

---

### Post by Xiong Chiamiov on 2008-05-02
You could try using adept (the package manager for KDE), though I don't know if it requires any of the KDE libs.

---

### Post by captgadget on 2008-05-02
Using terminal it opened just fine and I was able to make changes.

---

### Post by captgadget on 2008-05-02
OK, I made changes like getting rid of the residual files, but when I did a search looking gstreamer it came back and said Synaptic was not responding.

---

### Post by captgadget on 2008-05-02
checking my log file it keeps showing lib/security/pam-smbpass.so it cannot open shared object: no such file. Suppose this is my problem?

---

### Post by captgadget on 2008-05-02
I found the solution here under daverich:[http://ubuntuforums.org/showthread.php?t=775844&highlight=unable+resolve+host](http://ubuntuforums.org/showthread.php?t=775844&highlight=unable+resolve+host)

---


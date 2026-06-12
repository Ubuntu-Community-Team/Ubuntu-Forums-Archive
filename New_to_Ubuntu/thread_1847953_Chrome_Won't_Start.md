---
title: "Chrome Won't Start"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-09-21
I just installed Google Chrome 14 from chrome.google.com but when I click it, it just pulses a little bit then settles down. Could there be a missing file?

---

### Post by MG&amp;TL on 2011-09-21
Get chromium instead (what appears to be the linux version) - it's like chrome ( I think google test their experimental stuff there, hen they put it in chrome). You can get it in software-centre or

```
sudo apt-get install chromium
```
 
And it should work fine.

---

### Post by doppel.ganger on 2011-09-21
What's the difference between Chromium and Chrome asides from the blue icon?

Anyway, its still on version 13.

---

### Post by MG&amp;TL on 2011-09-21
But a simple debugging step is to run chrome from command-line like so:

```
chrome
``` (I think this is it)
And observe any error messages and what they tell you to do.

---

### Post by MG&amp;TL on 2011-09-21
I don't notice anything myself. Really, I don't.

---

### Post by westie457 on 2011-09-21
Chrome is stable according to Google.

Chromium is very stable according to Linux

---

### Post by doppel.ganger on 2011-09-21
```
thomas@Thomas-Ubuntu:~$ chrome
chrome: command not found
thomas@Thomas-Ubuntu:~$ google-chrome
/usr/bin/google-chrome: error while loading shared libraries: libnss3.so: cannot open shared object file: No such file or directory
thomas@Thomas-Ubuntu:~$ google-chrome-stable
google-chrome-stable: command not found
thomas@Thomas-Ubuntu:~$
```
I think google-chrome is the right command, but there's something wrong.

---

### Post by doppel.ganger on 2011-09-21
Anybody know what that error means?

---

### Post by CaptainMark on 2011-09-21
google chrome is a browser made and designed by google, the source was released as an open source project called chromium, just basically a non-branded open-source browser project by google. chromium is my recommended choice but you install it with ```
sudo apt-get install chromium-browser
``` or through the software centre, 

the average user will notice little difference between the two (the only thing i notice is lack of in browser pdf support) but if you support open-source go for chromium

---

### Post by doppel.ganger on 2011-09-21
Please understand that I want the latest version of Google Chrome, not an older version of Chromium. Is there any way to fix this error?!

---

### Post by MG&amp;TL on 2011-09-21
If you want to install chrome you need to install libnss3, as stated in the error. Go into synaptic package manager and install there. Then reboot and try again.

---

### Post by MG&amp;TL on 2011-09-21
Any particular reason? Viruses aren't really an issue, there won't have been that much new since the last package of chromium.

---

### Post by CaptainMark on 2011-09-21
okay so, to use the latest version of chrome go to [this link]("http://www.google.com/chrome/eula.html?hl=en-GB&platform=linux") and download the best version for you, the top one for 32bit or the second one for 64bit, and just double click it, it should open software centre and install chrome and the stable ppa to allow it to update it,

alternatively these commands do the same for chromium, 
```
sudo add-apt-repository ppa:chromium-daily/stable
sudo apt-get update
sudo apt-get install chromium-browser
```

---

### Post by doppel.ganger on 2011-09-21
```
thomas@Thomas-Ubuntu:~$ sudo apt-get install libnss3
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libnss3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
thomas@Thomas-Ubuntu:~$
```

---

### Post by MG&amp;TL on 2011-09-21
OK...libnssn3 wasn't where chrome expected it to be...use Cpt. Mark's solution or chromium. Unless you really want to spend ages at a command-line.

---

### Post by CaptainMark on 2011-09-21
i cant recreate your error using the latest version of chrome or chromium, so hopefully if you use either of these methods to make sure your up-to-date you should have no probs

oh and your terminal command should be just google-chrome

---

### Post by RJARRRPCGP on 2011-09-21
> **doppel.ganger said:**
> ```

thomas@Thomas-Ubuntu:~$ google-chrome
/usr/bin/google-chrome: error while loading shared libraries: libnss3.so: cannot open shared object file: No such file or directory 
```


Classic signs of missing library. The first sign is that the app GUI fails to appear.

---

### Post by SavageWolf on 2011-09-21
I had this error earlier today!

Apparently someone deleted libnss3.so. 

I fixed it in a kinda hacky way...
1. Go to /var/cache/apt/archives/
2. Break open one of the libnss3 debs with the archive manager.
3. Inside there go to /usr/lib/(stuff)/libnss3.so, and copy it to your Desktop
4. Run `sudo cp ~/Desktop/libnss3.so /usr/lib/x86_64-linux-gnu/libnss3.so`

It's probably not the best solution, but it works.

This is most likely a bug in the libnss package, maybe... Could someone else experiencing this try rolling back the package to an earlier version or something before trying the steps above.

EDIT: Slow internet or something... Maybe... Delete this comment or something...

---

### Post by SavageWolf on 2011-09-21
I had this error earlier today!

Apparently someone deleted libnss3.so. 

I fixed it in a kinda hacky way...
1. Go to /var/cache/apt/archives/
2. Break open one of the libnss3 debs with the archive manager.
3. Inside there go to /usr/lib/(stuff)/libnss3.so, and copy it to your Desktop
4. Run `sudo cp ~/Desktop/libnss3.so /usr/lib/x86_64-linux-gnu/libnss3.so`

It's probably not the best solution, but it works.

This is most likely a bug in the libnss package, maybe... Could someone else experiencing this try rolling back the package to an earlier version or something before trying the steps above.

---

### Post by enceladus47 on 2011-09-21
I'm not sure if that would work but it worked for me today with another library, could you try

```
sudo apt-get install --reinstall libnss3
```

---


---
title: "Google Chrome Browser Fails to install on 11.10"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by perito on 2011-10-13
Google Chrome Browser Fails to install on 11.10 ... I downloaded it 3 times now to check for damaged package.
I also tried to run it from synaptic but didnt know how.
Whats the problem ?

---

### Post by Dangertux on 2011-10-13
What is the error you are receiving?

---

### Post by nachfolger on 2011-10-13
same problem here... "internal error" "the file XXXX could not be opened"

---

### Post by Musmanno on 2011-10-13
Are you guys getting it from the Software Center? It installed fine for me in 11.10.

---

### Post by GuitarRocker2562 on 2011-10-13
```
sudo dpkg -i /path/to/google/chrome 
```
it will fail, then
```
sudo apt-get -f install
```
will fix the problem and finish the install

---

### Post by Dangertux on 2011-10-13
**Installing Google Chrome On Oneiric Ocelot 11.10 **

This assumes you want to use GOOGLE Chrome , not Chromium which is pretty much the same thing, with less tracking features. If you wish to install Chromium browser do the following

```

sudo apt-get install chromium-browser

```If you want Google's Chrome continue reading.

[B]Step 1 : Get the debian package appropriate for you
[/B]
Download either the 32 bit or 64 bit Chrome debian package from here : [http://www.google.com/chrome](http://www.google.com/chrome)

**Step 2 : Dependencies**

Satisfy dependencies for Google Chrome. In a terminal do the following

```

sudo apt-get update && sudo apt-get install libcurl3 libnspr4-0d libxss1

```You will be prompted for your password here , provide it.

**Step 3  : Install Google Chrome**

In a terminal window change directories to where you downloaded Chrome.

example : 

```

cd /home/dangertux/Downloads

```Install Chrome by running the following

```

sudo dpkg -i google-chrome-stable_current_i386.deb

```note : your file may not be the same depending on your architecture.

You will be prompted for your password, provide it.

Enjoy Chrome :-)

EDIT : Or I can get ninja'd mid post and you can do the recommended 1 post above mine :-)

---

### Post by nachfolger on 2011-10-13
This worked! Thanks for your help GR2562

---

### Post by GuitarRocker2562 on 2011-10-13
You're welcome! I just had to do it myself lol. Please mark your thread as solved if you don't mind this way other people with the same problem can find how to fix it.

---

### Post by ChrisOfBristol on 2011-10-13
Dangertux

I had the same problem, and your solution worked for me.

In case anyone wants any more details of the problem, the download process stated that it had downloaded successfully (27.MB) and the Software Centre opened - but errored saying that the .deb file could not be opened. In case it was a problem with Software Centre not finding the file or with file permissions, I searched for and found the .deb file in /tmp, gave it all permissions to all users, then right clicked on it and selected Open with Software Centre, only to get the same message again. 

Doing it in the terminal with Dangertux's command works:
Step 1 - which I had already done but I was surprised to find the file in /tmp not ~/downloads is this new in 11.10?
Step 2 - only installed libxssl and had no effect on my attempt to use Software Centre so I don't know whether it is essential or not
Step 3 - fixed it.

---

### Post by Dangertux on 2011-10-13
> **ChrisOfBristol said:**
> Dangertux

I had the same problem, and your solution worked for me.

In case anyone wants any more details of the problem, the download process stated that it had downloaded successfully (27.MB) and the Software Centre opened - but errored saying that the .deb file could not be opened. In case it was a problem with Software Centre not finding the file or with file permissions, I searched for and found the .deb file in /tmp, gave it all permissions to all users, then right clicked on it and selected Open with Software Centre, only to get the same message again. 

Doing it in the terminal with Dangertux's command works:
Step 1 - which I had already done but I was surprised to find the file in /tmp not ~/downloads is this new in 11.10?
Step 2 - only installed libxssl and had no effect on my attempt to use Software Centre so I don't know whether it is essential or not
Step 3 - fixed it.

Glad it helped :-)

---


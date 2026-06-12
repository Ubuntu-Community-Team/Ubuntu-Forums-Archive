---
title: "i need help"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by piulitza on 2008-11-24
i am absolute beginner in linux. i have just downloaded and installed ubuntu. i had soe problems and i couldnt install it from cd (the nero i have might not be so good or the cds i bought were not so good) so i was obliged to install it using wubi, mounting the images using daemons. the installation was ok and after that i was required to reboot to ubunto to see what have i installed. i booted to ubuntu but i dont understand why dont i have graphic interface. why? i have seen on you tube and on other sources that it has graphic interface and instead of it i have just seen a comand line. is there any command that i need to write to enter ubuntu or.. do i have to install anything in oder to have graphic interface?or do i have to do something else? dont forget that i hadnt any cd in cdrom when i booted t ubuntu cause i installed it using image mounted with daemons

---

### Post by Titan8990 on 2008-11-24
Only the Server version of Ubuntu does not have GUI. Sometimes it will not even load Ubuntu or the default shell (BASH) due to hardware incompatibility. If this is the case then the command line you get will say (busybox).

Do the following:

A) Verify that you did not install the Server version

B) Verify if you shell look like:

myusername@ubuntu$

or like this:

(busybox):

Report back in this post.

---

### Post by piulitza on 2008-11-24
how do i verify the shell?

---

### Post by Titan8990 on 2008-11-24
Sorry, I can see how that might have been confusing.


Does your command prompt look like this:


yourusername@yourcomputername$


or does it look like this:


(busybox):

---

### Post by Sarmacid on 2008-11-24
To find out if you have the server try on the console```
uname -r
```

I'm using server and got ```
2.6.24-21-server
```

If this is your case, then you can either install the ubuntu desktop version or continue using the server and install the GUI.

If you're not running the server, try and starting the GUI with ```
sudo gdm start
```

---

### Post by piulitza on 2008-11-25
on command prompt it writes initramfs

---

### Post by Bucky Ball on 2008-11-25
Try:

```
sudo apt-get update
```then:

```
sudo apt-get install ubuntu-desktop
```... and let us know how you go.

---

### Post by hyper_ch on 2008-11-25
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by piulitza on 2008-11-25
i have tried these 2 codes but no one worked. but before ubuntu shows me the comand line it tells me to press esc to view menu and i pressed to see what happens and it asks me about some installation methodes. but i have already installed ubuntu using wubi. is there anything else that i need to install in order to have ubuntu interface?

---

### Post by piulitza on 2008-11-25
is there anything ishould write before these 2 codes?

---

### Post by Bucky Ball on 2008-11-25
> **piulitza said:**
> is there anything ishould write before these 2 codes?

No. What exactly is the text it is giving you after pressing escape?

---

### Post by piulitza on 2008-11-25
Guys i have looked at more videos on you tube and i think that wubi doesant a complete installation and i think i still need to burn image to cds i think i will try to buy cds from a safer source this time and try anoter nero. Daemons tools cannot help me cause i  need to complete installation after rebooting

---

### Post by piulitza on 2008-11-25
now i have seen that wubi doesant a complete installation so i was required to burn the image to cd but there is my biggest proble. Ubuntu stops during installation. i dont even know if it is the installation or it is just the preperation for installtion. I have tried both nero and alcohol(it's true that i got them using torrents i dont have them from their official sites) but .. the same. and believe me i burned images to 6 cds utnil now... both versions of unbutu for desktop and the same problem. i dont know why ... it shows to me a charging box... and when it nearly finishes.. it stops. And i had never this problem util now with windows cd so i dont think my computer has hardware roblems. but why does it stop before installing?

---

### Post by piulitza on 2008-11-25
and i scanned al these cds of errors and....no eror detected

---


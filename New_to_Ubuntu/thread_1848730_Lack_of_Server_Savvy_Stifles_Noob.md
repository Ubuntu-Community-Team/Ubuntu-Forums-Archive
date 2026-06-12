---
title: "Lack of Server Savvy Stifles Noob"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by BEEDO on 2011-09-23
I have just added **LAMP** to Ubuntu 11.04 **desktop** in **VirtualBox**. In **Terminal** I typed:

[SIZE=2]**[FONT=arial]$sudo   vi  /var/www/info.php[/FONT]**[/SIZE]

This produced a bunch of ~'s lined up vertically on the left side of the screen. I want to put:
  
**1.<?php**
**2.phpinfo();**
**3.?>**



like the example here: [http://www.unixmen.com/linux-distributions/4-ubuntu/1239-install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat](http://www.unixmen.com/linux-distributions/4-ubuntu/1239-install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat) 

I can't seem to put anything here without triggering :

E353: Nothing in register "

What am I doing wrong?:confused:

[B][FONT=arial]
[/FONT][/B]

---

### Post by MG&amp;TL on 2011-09-23
Use *nano* or *gedit* instead-it's probably easier. Vi(m) is incredible, but can get grumpy.

---

### Post by MG&amp;TL on 2011-09-23
Syntax is:

```
sudo nano /var/www.info.php

```


or

```
sudo gedit /var/www.info.php
```

---

### Post by BEEDO on 2011-09-23
This is Absolute Beginner Talk and I'm here to prove it!

I typed:

sudo nano /var/www.info.php
and created the file **/var/www,info.php**

and wrote this:

**1.<?php**
 **2.phpinfo();**
 **3.?>**

Is my syntax correct?
How do I save the file?

Thanks again!

---

### Post by Lisiano on 2011-09-23
> **MG&TL said:**
> Syntax is:

```
sudo nano /var/www.info.php

```


or

```
sudo gedit /var/www.info.php
```

I'd like to say that sudo shouldn't be used for graphical applications, use gksudo instead.
Psychocats explains it quite well well
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Also for the PHP syntax. If you didn't write the numbers, it probably is correct.

---

### Post by BEEDO on 2011-09-23
An interesting read, but I am not too fresh, so I will look at it again in the morning.

I dropped the numbers but I still don't know how to save the file and exit terminal.

Hopefully I will be able to do it and then get some sleep, for which I am about two hours overdue.... I want to accomplish some small victory first!

---

### Post by MG&amp;TL on 2011-09-23
OK, using nano, to save the file, hit Ctrl-O, edit the filename (if necessary), then press return. 

Then to exit to command-line, use Ctrl-X. There should be a tab at the bottom explaining all that.

Yeah, sorry, use gksudo instead for gedit, my bad. :)

---

### Post by bodhi.zazen on 2011-09-23
Server side, learning vim is extremely helpful.

You are asking about php / web page design however, and I highly suggest any of the online tutorials.

Google search

how to vim

how to php

how to html

for back end support start with

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by MG&amp;TL on 2011-09-23
```
sudo apt-get install vim
vimtutor
```

Should get you started.

---

### Post by dave01945 on 2011-09-23
i found running vimtutor in terminal very helpful

```
vimtutor
```

takes about half hour to run through and will show you all the basics of vim and for general use the basics are all you will need

---

### Post by MG&amp;TL on 2011-09-23
Unless, of course, you want to learn a different editor. ?

---

### Post by Lisiano on 2011-09-23
> **MG&TL said:**
> Unless, of course, you want to learn a different editor. ?

+1, nano for example. I use it for everything. Gedit/Kate only for search and replace. Too lazy to use sed.
Vi only in the rare cases when there is absolutely no alternative. Took me at least half a hour to figure out how to exit it, fubared a NAS with it, had to reinstall.

---

### Post by MG&amp;TL on 2011-09-23
...I would suggest giving it another go. But it's your choice.

Yeah, +1 for *nano*.

The best thing about a command-line editor is that you can have something like terminal and run *make* or whatever on one side, and fix errors on the other with *nano* or *Vi*

---

### Post by BEEDO on 2011-09-24
**#1.**
Lisiano wrote:
> I'd like to say that sudo shouldn't be used for graphical applications, use gksudo instead.
I am not sure how to identify graphical applications so I can use gksudo rather than sudo when appropriate.

**#2.**
in Terminal I typed:

sudo nano /var/www.info.php
and created the file **/var/www.info.php**

and wrote this:

**<?php**
 **phpinfo();**
 **?>**

Then saved it with ctrl-O

this appears: 
**File name to write: /var/www.info.php**

My question: if I change it to: **info.php** 
 will it still be located at:  /var/ ? 

and why do I need and what happens to the **www**? the **www** came from a tutorial but I don't know what function it serves.

**#3.**
I've spent the last hour learning about text editors. According to Ubuntu documentation > vim has a formidable learning curve, but by getting comfortable with vim  and its great features, you will became very efficient at manipulating  text. A pre-condition to that, is the programmer (*novice*) should learn Touch Typing to experience the power.  I like the bit about experiencing the power! Now I have to get way better at touch typing!

Some things are clearer, now. And I've learned a new word, 'Fubared'.

Thanks for the help! I will keep plugging away.

Also don't forget my questions in # 2, because next I want to open a browser in Ubunto desktop and see the php info page and for that I need to know the URL and it's synonyms and I am starting to feel my brain go a little fuzzy... (Because I am a absolute beginner!)

---

### Post by MG&amp;TL on 2011-09-24
The 'filename to write' is th 'relative path, not the absolute one.

Therefore, if I edited /etc/fstab (for instance) it would tell me the filename to write would still be fstab, not /etc/fstab.

---

### Post by Lisiano on 2011-09-24
[QUOTE=BEEDO]I am not sure how to identify graphical applications so I can use gksudo rather than sudo when appropriate.[/QUOTE]
Easy version: all graphical applications are applications that have a GUI, as in you can move them around, press buttons, type in them, etc.
Hard version: A graphical application is a application that runs inside your X server and displays it's content in its own window while possibly allowing modifications to the window in question.

[QUOTE=BEEDO]sudo nano /var/www.info.php
and created the file /var/www.info.php[/QUOTE]
I just noticed something weird. Why are you saving the file in /var/ with the name [www.info.php](www.info.php) instead of /var/www/ with the name info.php?
[QUOTE=BEEDO]
I want to open a browser in Ubunto desktop and see the php info page and for that I need to know the URL and it's synonyms and I am starting to feel my brain go a little fuzzy[/QUOTE]
By default, anything placed in /var/www is visible when you go to [http://localhost/](http://localhost/)
For your test page, you probably should save it as /var/www/info.php instead of /var/www.info.php (Probably a typo on the tutorial authors part, dot and forward slash is right next to each other) then go to this page
[http://localhost/info.php](http://localhost/info.php)

---

### Post by BEEDO on 2011-09-25
Thank you so much(!) to everyone who is helping me. I am trying to process this as quick as I can...

OK. I did not know what nano was at this time yesterday, but now it makes sense, with vim thrown in for good measure!

'Relative path" as file to write -comprehended!

Now, if I understand correctly, I have a file that I want to be called info.php under the wrong name [www.info.php]("http://www.info.php") in /var/  ... so I need to rename the file and relocate it in /var/www/     ...I definitely don't know how to do that!

If someone can help me understand how to do that (which will add a multiplier to my current abilities) I should be able to open a browser on the Ubuntu desktop, type in [http://localhost/info.php](http://localhost/info.php) and have the php info page displayed.

Since the desktop is in VirtualBox, the following step is to figure out how to access it from the host OS which means I have to make sure the port forwarding in VirtualBox is set up properly. That also seems mysterious to me.

---

### Post by Lisiano on 2011-09-26
No need to tinker with VirtualBox, you just need a IP, click the Network manager icon and press Connection Information and substitute the information you find (IP) with localhost.
Now, to move files, you want to use ```
mv <oldfile> <newfile>
```
In your case```
sudo mv /var/www.info.php /var/www/info.php
```
We are using sudo since you technically aren't the owner.
Now to to make sure Apache can read the file
```
sudo chmod 644 /var/www/info.php
```
All done. Now just go to that page, for example my current VM has an IP of 192.168.130.128 so I would go to [http://192.168.130.128/info.php](http://192.168.130.128/info.php)

---

### Post by BEEDO on 2011-09-26
Thank you Lisiano, I thought this thread had died!

I have been learning how to use Terminal and had already tried the command you suggested without sudo.

Lisiano:> We are using sudo since you technically aren't the owner.
Now to to make sure Apache can read the file
     Code:
     sudo chmod 644 /var/www/info.php 
I am not sure what you mean when you say I am not the owner. Does this mean I always use sudo? sudo chmod 644 changed the file permissions... Although I don't understand for who (or why?). Is root the owner?... this is baffling.... it worked though!

I used the browser on the desktop to look at >http://localhost/info.php<  and savored a small moment of success!

 I was unable to find a network manager icon and find a place to edit the IP address. I assume you mean in the Desktop. I looked for quite awhile! Is the IP address the same for the VM and the host?

---

### Post by alphacrucis2 on 2011-09-26
If you do decide to learn to use vi, I find a cheat sheet such as this to be handy:

[http://www.lagmonster.org/docs/vi.html]("http://www.lagmonster.org/docs/vi.html")

---

### Post by Lisiano on 2011-09-27
You aren't the owner because you probably used sudo nano or sudo vi to edit the file, this means the file is owned by root. We used chmod to make sure the owner can write and read and everyone else to read (Apache).
Also almost every file that is not in your home is usually owned by root, sometimes by other system users (www-data is Apache for example)

If you can't find the network manager or use a server install, type this```
ifconfig eth0
```

Note. I hate typing on my phones soft keyboard now.

---

### Post by BEEDO on 2011-09-28
I am still trying to figure out the correct IP address. Since that hasn't worked yet, I have been 'tinkering' with VirtualBox's network adapters. Configuring port forwarding in NAT (port 80 for Apache); Host only; Bridge Mode...; read about ifconfig. My head spins like a top! ](*,) Keep trying!

---


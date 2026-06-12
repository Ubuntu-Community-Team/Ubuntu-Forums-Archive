---
title: "[SOLVED] Problem installing screenlets( in .tar.gz files)"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by ellalan on 2008-09-11
Hi
I have downloaded two files (81694-NVidia_v0.5.tar.gz  and  another file ending .tar.bz2)
I have gone through the posts but I couldn't find a method which I could handle comfortably, in short I failed miserably.
I have downloaded to my Desktop and extracted in the Desktop. 
What is "cd" and I do not understand when people say "make cd"or similar to that.
Could someone please help me with step by step procedure. TIA.

---

### Post by john.nicholls on 2008-09-11
cd = change directory

---

### Post by ellalan on 2008-09-11
Hi john, Thank you for the reply,could you please help me a bit further.
I followed this instructions from another post:

Code:

sudo apt-get install build-essential checkinstall

To install it you would need to extract

Code:

tar -zxvf filename

change to directory then start to compile
Code:

./configure
make
sudo make checkinstall

I am stuck at the "change to directory then start to compile" instruction.
do I just put "cd" in Terminal and press enter or "cd ~./configure
make
sudo make chekinstall.
Thanks for the help.

---

### Post by SuperSonic4 on 2008-09-11
```
cd ~/Desktop
```

then

[I]./configure
make
sudo make checkinstall
[/I]

cd ~/Desktop takes you to /home/<user>/Desktop.

Edit: if it's in a folder on the desktop (I will use *[COLOR="Red"]package[/COLOR]* as an example) then you type ```
cd ~/Desktop/[COLOR="Red"]package[/COLOR]
```. It is case sensitive by the way so be careful.

---

### Post by ellalan on 2008-09-12
I am getting these errors,could you please help me with ideas.

vignes@vignes-desktop:~$ sudo apt-get install build-essential checkinstall
[sudo] password for vignes: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
checkinstall is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
vignes@vignes-desktop:~$ tar -zxvf 81694-NVidia_v0.5.tar.gz
tar: 81694-NVidia_v0.5.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
vignes@vignes-desktop:~$

---

### Post by DFlame on 2008-09-12
It doesn't look like you've changed directory to the desktop as advised. Try:

```
cd Desktop/
```

in the terminal before running that tar command.

DF

---

### Post by forger on 2008-09-12
why would you compile screenlets? 0.1.2 is here: [http://www.getdeb.net/app/Screenlets](http://www.getdeb.net/app/Screenlets)

You download the 32-bit or 64-bit packages, double-click on them to install and that's it :)

---

### Post by ellalan on 2008-09-12
Thanks DFlame, I did what youtold me to do and I get this

vignes@vignes-desktop:~$ cd ~/Desktop
vignes@vignes-desktop:~/Desktop$ tar -zxvf 81694-NVidia_v0.5.tar.gz
NVidia/
NVidia/NVidiaScreenlet.py
NVidia/COPYING
NVidia/NVidiaScreenlet.pyc
NVidia/README
NVidia/icon.svg
NVidia/themes/
NVidia/themes/default/
NVidia/themes/default/gpu_fill.svg
NVidia/themes/default/background.svg
NVidia/themes/default/nvidia_logo.svg
vignes@vignes-desktop:~/Desktop$ ./configure
bash: ./configure: No such file or directory
vignes@vignes-desktop:~/Desktop$ make
make: *** No targets specified and no makefile found. Stop.
vignes@vignes-desktop:~/Desktop$ sudo make checkinstall
make: *** No rule to make target `checkinstall'. Stop.
vignes@vignes-desktop:~/Desktop$

---

### Post by DFlame on 2008-09-12
Forgers advice may get this working faster, but should you wish to continue here...

You'll have to run the ./configure inside the directory that the tar command created. So try these in Terminal:

```
cd /Desktop/Nvidia/
./configure
```

Then continue with the instructions you originally found :)

DFlame

---

### Post by ellalan on 2008-09-12
Hi Guys Thank you all for your help,I have managed to get this fixed by installing screenlets in Synaptics, then Alt+F2->gksudo nautilus->screenlets.
I have extracted tar.gz file to my Desktop and copied that to screenlets folder. I don't know whether this is the right way to do it but it works.
Thanks again to you all.

---

### Post by DFlame on 2008-09-12
If it's working, don't question it ;) That's my take. Good to know all's well

DFlame

---


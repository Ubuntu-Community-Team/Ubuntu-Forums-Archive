---
title: "[SOLVED] Cannot install applications"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by marktebbutt on 2008-09-24
I'm new to Ubuntu and I really can't work out what I'm doing wrong. Sorry if this has been answered before, but I've spent ages on the forum and cannot find this issue specifically.

Firstly, update manager just seems to do nothing. It opens in the GUI form, and I select install updates; it seems to be doing something, but then just stops and returns to its original form. 

Secondly, when I try to install other applications, they fail to install. I have attached a screen shot from an attempted install of 7zip, although it is the same with all applications I have tried.

If I use the terminal and 'sudo' then the updates are performed, but I do not understand why I cannot do it the other way? Sadly, I am not yet able to do much with the terminal, so could really do with being able to install things easily.

I have also tried opening Synaptic Package Manager, and this will not open. The small window appears for a second or two, as though it is going to start, but then disappears...

Any help would be much appreciated!

Thanks.

---

### Post by Elfy on 2008-09-24
Can you open a terminal and run

```
sudo apt-get update
```

post the resulting output here please

---

### Post by cotcot on 2008-09-24
Do you get an error message when you start synaptic from terminal ? 
```
sudo synaptic
```

---

### Post by marktebbutt on 2008-09-24
Yes, terminal runs and the screen print is attached - I hope this is what you were asking for?

---

### Post by Elfy on 2008-09-24
What happens if you install from terminal

```
sudo apt-get install p7zip
```

---

### Post by marktebbutt on 2008-09-24
Yes - a segmentation fault(?) I have attached the print...

> **cotcot said:**
> Do get an erro message when you start synaptic from terminal ? 
```
sudo synaptic
```

---

### Post by marktebbutt on 2008-09-24
It installs ok - 

mark@mark-desktop:~$ sudo apt-get install p7zip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  p7zip-full
The following NEW packages will be installed
  p7zip
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 317kB of archives.
After this operation, 942kB of additional disk space will be used.
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe p7zip 4.57~dfsg.1-1 [317kB]
Fetched 317kB in 7s (44.9kB/s)                                                 
Selecting previously deselected package p7zip.
(Reading database ... 99748 files and directories currently installed.)
Unpacking p7zip (from .../p7zip_4.57~dfsg.1-1_i386.deb) ...
Setting up p7zip (4.57~dfsg.1-1) ...
mark@mark-desktop:~$ 


> **forestpixie said:**
> What happens if you install from terminal

```
sudo apt-get install p7zip
```

---

### Post by Mariane on 2008-09-24
I don't understand where you see a segmentation 
fault, as all these outputs seem fine to me. You 
can try to remove and re-install synaptic:

sudo apt-get --purge remove synaptic

then
sudo apt-get install synaptic

then you relaunch it:
sudo synaptic &

(The "&" means you can still use your terminal before 
closing synaptic)

Mariane

---

### Post by marktebbutt on 2008-09-24
Thanks Mariane, I'm trying that now.

The segmentation fault can be seen in the file attached to post #6 - the bottom 3 lines are where I tried to sudo synaptic, and the response is segmentation fault.

I'm hoping this might work before I pull out the last of my hair! 



> **Mariane said:**
> I don't understand where you see a segmentation 
fault, as all these outputs seem fine to me. You 
can try to remove and re-install synaptic:

sudo apt-get --purge remove synaptic

then
sudo apt-get install synaptic

then you relaunch it:
sudo synaptic &

(The "&" means you can still use your terminal before 
closing synaptic)

Mariane

---

### Post by marktebbutt on 2008-09-25
Thanks Mariane!
Did as you suggested, and then install update-manager, and everything seems to work fine. :)

---


---
title: "Davinci Resolve.. having troubles installing it."
date: 2024-10-19
forum: New to Ubuntu
---

### Post by shadowtabby on 2024-10-19
Heyo guys,

I am having trouble with installing davinci resolve 19.

Missing or outdated system packages detected.


Please install the following missing packages:
    libapr1 libaprutil1 libasound2 libglib2.0-0
    
When I do sudo apt install libapr1


I get:


Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'libapr1t64' instead of 'libapr1'
libapr1t64 is already the newest version (1.7.2-3.1ubuntu0.1).
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

And it does the same with the others too.  How can I install this?

---

### Post by shadowtabby on 2024-10-20
Anyone know anything with this?

---

### Post by ian-weisser on 2024-10-20
Does it need to be Davinci Resolve?

There are other good video editors that are much easier to install available in the Ubuntu Software application.

New users who start there first will find great software that is not frustrating to install.

---

### Post by shadowtabby on 2024-10-20
Heyo,

I have been using davici since windows.  I know how to use that software.  I tried kden and I can't figure out the transitions like I can with capcut and davici.

---

### Post by bobunderwood99 on 2024-10-21
Hello,

Check out [Cinelerra]("https://www.cinelerra-gg.org/").

I'd install the Appimage version.

---

### Post by bobunderwood99 on 2024-10-21
See both videos regarding installation of DVR 19 on Ubuntu 24.04

[https://www.youtube.com/watch?v=Y87MFmcy3lc](https://www.youtube.com/watch?v=Y87MFmcy3lc) 

[https://www.youtube.com/watch?v=FHnNqtAwJ6M](https://www.youtube.com/watch?v=FHnNqtAwJ6M)

---

### Post by shadowtabby on 2024-10-22
Heyo,

Thank you I will take a look now.

---

### Post by shadowtabby on 2024-10-22
Sorted.

---

### Post by bobunderwood99 on 2024-10-22
Hello,

Sorted how?

---

### Post by shadowtabby on 2024-10-22
Heyo,

Yes it's sorted.  I reinstalled windows.

---

### Post by thephatle on 2024-10-23
i know this is marked as sorted, but on Davinci you need to move davinci installed dependencies on dummy folder to start using system ones

```
cd /opt/resolve/libssudo mkdir disabled-libraries
sudo mv libglib* disabled-libraries
sudo mv libgio* disabled-libraries
sudo mv libgmodule* disabled-libraries
```
[COLOR=#E6E6E6][FONT=Consolas]


[/FONT][/COLOR]

---


---
title: "VirtualBox Problems"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by jaydenop on 2008-07-25
I get the below error when trying to load a virtual machine. I know my user account is part of the vboxusers group so what else can I do? Do I have to download the kernal driver?


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by adult swim on 2008-07-25
from a terminal try
```
sudo apt-get install virtualbox-ose-modules-generic
```
then try to open and run virtualbox

---

### Post by Cresho on 2008-07-25
if this does not work do this.

You need to add you user to the vboxuser group :

go to System -> Administration -> Users and Groups

Select the "Manage Groups" -> Scroll down to vboxusers -> select (click) the group vboxusers -> Click "Properties" -> tick off you user box

Close out Users an groups,

Log off and back in.

basically you need to tell virtualbox you want your username with it.  There is another trick.  you can make virtualbox look like if it is running on the linux desktop.

[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linuxRun](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linuxRun)

if you are running compiz, you will need to autorun the calculator in the window start menu.  this is because windows and linux fight for the desktop.

One last thing I am having problem with is sharing the desktop.  I can access single files but not files in a folder.

never mind on that last problem.  It's all solved.

---

### Post by jaydenop on 2008-07-25
OK entering the code:

sudo apt-get install virtualbox-ose-modules-generic

got the virtual box to get by the error i was having but now i have a new one:

"FATAL: No bootable medium found! system halted"

I have my windows vista cd in the cd rom and if i press F12 while the virtual machine is booting to try and load vista I get this error:

FATAL: could not read from the boot medium! System halted.


Any ideas of how i can load vista on this virtual machine without getting these errors?

---


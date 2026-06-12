---
title: "Where for art though wireless......?????"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Immolatus on 2008-04-28
So I've been following this how to:
[http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+wireless+1395](http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+wireless+1395)

and so far it has not worked for me. I get to the point where is says "driver installed device present", I reboot and nothing happens. I think this has something to do with the fact that the driver and ndiswrapper are both installed in my home folder. This doesn't seem right to me, not to mention very messy. 

All this having been said, I am about to install ndiswrapper from the repos but I still need to know where to extract and install the driver so that it functions. Any thoughts would be greatly appreciated.:popcorn:

---

### Post by anewguy on 2008-04-28
Where you actually put the driver files isn't important.  Either specifying the path to them or (best way) set your default directory to it before you do the ndiswrapper -i.  Most people just put the driver files on their desktop, then they do something like the following:

sudo ndiswrapper -l <= lower case "L" for list

If anything is returned above:

sudo ndiswrapper -e xxxxxx <= where xxxxxx is the name returned above

repeat the above until nothing is returned - now you have a clean slate.

cd ~/Desktop

sudo ndiswrapper -i xxxxxx.inf <= lower case "I" for install, xxxxxx is the name of the .inf file for your driver (be sure all of the .sys files it requires are there as well)

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

sudo gedit /etc/modules

add this line to the bottom of that file:

ndiswrapper

then save the file and exit the editor

IF you adaptor is based on certain chipsets, you may need to blacklist the "default" driver (blacklisting it will stop if from loading).  My experience has mainly been with the ubiquitous broadcom bcm43xx series - in which case you do the following:

sudo gedit /etc/modprobe.d/blacklist

Add the following to the end of that file:

blacklist bcm43xx

save the file and exit the editor

Now, in all cases, it's best just to reboot your PC.

Hope that helps in some way.

:)

EDIT:  BTW - don't worry about uninstalling and then downloading and compiling ndiswrapper.  I have not run into an instance yet where the ndiswrapper and utilities you get via synaptic package manager have not worked.

---

### Post by Immolatus on 2008-04-28
when i do "sudo ndiswrapper -l" it returns "driver installed device present" should I still do "ndiswrapper -e"?

---

### Post by Immolatus on 2008-04-28
Sorry, for reposting I should have read all the way through. I'll try it all out and post back, thanks.:guitar:

---

### Post by Immolatus on 2008-04-28
:confused:Go fish. How would I go about "setting my default directory to it"?? 

I distinctly recall installing firmware for the ipw2200 in my old machine when fedora didn't support it and it went in /lib/firmware. I assume this is different on account of ndiswrapper, no?](*,)

---

### Post by Immolatus on 2008-04-28
bump......
So I found another post in another forum with a "fix" for the same problem. Now I've got the driver in it's own directory called ~/.drivers, much neater this way. 
I do however believe I have rooted out the problem. On the of chance I might find something of interest, I took a look in the system logs under usr.log and here is what it says 

"load_driver(358): couldn't load driver bcmwl6" 

Waiter!!!!There's something wrong with the soup!!!!!

now to find out why not I suppose. As always any thoughts are greatly appreciated.:lolflag:

---

### Post by someguy2000 on 2008-04-28
Do you have the Dell Wireless 1395 card?
I have the same card and have figured out how to get it working.
You need to get this driver here ( [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174291&SystemID=INS_PNT_PM_1520&servicetag=&os=WW1&osl=en&deviceid=15680&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=236819](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174291&SystemID=INS_PNT_PM_1520&servicetag=&os=WW1&osl=en&deviceid=15680&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=236819) ) and extract it wherever. I just have it in a folder in my home folder.
Go to Synaptic Package Manager and install ndiswrapper.
Go to Administration -> Windows wireless Drivers, and browse for the bcmwl5.inf file which is in the DRIVER_US folder.
Oh yeah, and make sure **blacklist bcm43xx** is in /etc/modprobe.d/blacklist
That's all I had to do, I now have flawless wireless connectivity.

edit: just to clarify, this is on a fresh Ubuntu 8.04 installation. If you've been messing about with things trying to get it to work, you might have problems. I would suggest a clean re-install of Ubuntu if all else fails, and try my method.

---

### Post by Immolatus on 2008-04-28
:popcorn::popcorn::popcorn::popcorn::guitar::guitar::guitar:
I know you can't see it but I just danced one loud jig over that. 
Than you sooo freaking much. How the hell did I mis the menu entry???!!
I've been using ubuntu for almost two years now and for the last two days have felt like a complete dolt.

Thanks again.:)

---

### Post by anewguy on 2008-04-29
> **Immolatus said:**
> :confused:Go fish. How would I go about "setting my default directory to it"?? 

I distinctly recall installing firmware for the ipw2200 in my old machine when fedora didn't support it and it went in /lib/firmware. I assume this is different on account of ndiswrapper, no?](*,)

Looks like you got things working with ndiswrapper, the Windows drivers, and blacklisting bcm43xx as I mentioned.  As far as "setting my default directory to it", when you open a terminal window you are by default placed in your home directory.  When you "cd" to another folder, you are changing that instance of your default folder to the new folder.  EX:  cd ~/Desktop  will change your default (working) directory to the Desktop folder within your home folder.

---


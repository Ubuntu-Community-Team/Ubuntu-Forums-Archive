---
title: "Is this script correct??"
date: 2012-10-12
forum: Programming Talk
---

### Post by Mohan1289 on 2012-10-12
Hey guys i want to shut down my System at a particular time automatically..

is this script sufficient???

```

#!/bin/bash
date=$date+%X
if(date==6.30.00) then 

init 0

fi

```then using **contrab -e** i wil set it to perform automatically..

are there any flaws in my code??
correct me if i am wrong

---

### Post by pqwoerituytrueiwoq on 2012-10-12
```
#!/bin/bash
date=`date +%X`
if [ "$date" == "6.30.00" ]; then
   init 0
fi
```BTW X is not the letter you want

do you want it to shut down at 6:30 pm?

---

### Post by Mohan1289 on 2012-10-12
> **pqwoerituytrueiwoq said:**
> ```
#!/bin/bash
date=`date +%X`
if [ "$date" == "6.30.00" ]; then
   init 0
fi
```BTW X is not the letter you want

do you want it to shut down at 6:30 pm?

yes Exactly

---

### Post by pqwoerituytrueiwoq on 2012-10-12
sudo crantab -e 
```
30 18 * * * poweroff
```

---

### Post by Mohan1289 on 2012-10-12
> **pqwoerituytrueiwoq said:**
> sudo crantab -e 
```
30 18 * * * poweroff
```

So there is no need to write a script at all???

or can just write a script 

#!/bin/bash

init 0

and execute that at 18.30
??

---

### Post by pqwoerituytrueiwoq on 2012-10-12
correct
crantab is a program for scheduled processes so there is no need for a script to made sure the time is right since a cron job runs at a specific time
edit:
why do you want to complicate it with a script?

---

### Post by Mohan1289 on 2012-10-12
> **pqwoerituytrueiwoq said:**
> correct
crantab is a program for scheduled processes so there is no need for a script to made sure the time is right since a cron job runs at a specific time
edit:
why do you want to complicate it with a script?

i don't want to complicate it just wondering is possible that's all


instead of **poweroff** can i give the command **init0** at crontab and do i have to save the filename as crontab as well??

---

### Post by pqwoerituytrueiwoq on 2012-10-12
[FONT=Courier New]crontab[/FONT] is a program it will open a file in a text editor of your choosing, just go to the bottom and add the line
you can make it ran any command you want, if you want it to run [FONT=Courier New]init0[/FONT] you are welcome to, but idk if that is a shutdown command, [FONT=Courier New]poweroff[/FONT] needs to be root which is why i said [FONT=Courier New]sudo crontab -e[/FONT] and not [FONT=Courier New]crontab -e[/FONT]

---

### Post by Mohan1289 on 2012-10-12
> **pqwoerituytrueiwoq said:**
> [FONT=Courier New]crontab[/FONT] is a program it will open a file in a text editor of your choosing, just go to the bottom and add the line
you can make it ran any command you want, if you want it to run [FONT=Courier New]init0[/FONT] you are welcome to, but idk if that is a shutdown command, [FONT=Courier New]poweroff[/FONT] needs to be root which is why i said [FONT=Courier New]sudo crontab -e[/FONT] and not [FONT=Courier New]crontab -e[/FONT]


Oh okay 

i don't know the difference.. Thank you

---

### Post by Lars Noodén on 2012-10-12
[shutdown](http://manpages.ubuntu.com/manpages/precise/en/man8/shutdown.8.html) takes a time as an argument and will shutdown the system at that give time.  The time can be absolute (HH:MM) or relative  (+MM)

```

sudo /sbin/shutdown -h 18:30 "Done for the day" &

```

---

### Post by Mohan1289 on 2012-10-12
While i am trying install VLC or any other Software from Ubuntu Software Center i am getting an error saying 

**The action would require the installation of packages from not authenticated sources.**

When i click the details

**liba52-0.7.4 libaacs0 libass4 libbluray1 libcddb2 libcrystalhd3 libdc1394-22 libdca0 libdirac-encoder0 libdirectfb-1.2-9 libdvbpsi7 libdvdnav4 libdvdread4 libebml3 libenca0 libfaad2 libgsm1 libiso9660-8 libkate1 libmad0 libmatroska5 libmodplug1 libmpcdec6 libmpeg2-4 libresid-builder0c2a libschroedinger-1.0-0 libsdl-image1.2 libsidplay2 libtar0 libts-0.0-0 libtwolame0 libupnp3 libva-x11-1 libva1 libvcdinfo0 libvpx1 libx264-120 libxcb-composite0 libxcb-keysyms1 libxcb-randr0 libxcb-xv0 libzvbi-common libzvbi0 tsconf**


why can't i install from Ubuntu S/w center and same goes with Synaptic Package Manger and sometimes when i tried to install using "apt-get" command it halts abruptly saying same 
" [B]The action would require the installation of packages from not authenticated sources."

[/B]Why is that and how can solve this error??

---

### Post by Lars Noodén on 2012-10-12
That would best be the topic of a new thread.  It has little to do with shutdown.  (Try sudo apt-get update)

---

### Post by Mohan1289 on 2012-10-12
But how can i install softwares from Software Center or Synaptic Package manager if that is showing the Error???

---


---
title: "suddenly computer not reading disk drives 10.10"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by okkie on 2012-03-05
for some reason my computer cant read dvd or cd disks put into the drives.The little light on the drives flash as normal like its reading but nothing appears on the desktop as usual.None of the cd/dvd creators can detect the disks ,blank or otherwise,in the disk drives either.Not an Ubuntu problem I have'nt had yet,but this is a first.
Please help.I need to put my holiday photos on dvd.

---

### Post by Script Warlock on 2012-03-06
check the cd/dvd rom if it's working properly to some of your spare pc check/change the sata cable or etc before hunting down the software errors.

---

### Post by winh8r on 2012-03-06
Can you open a terminal (press control +alt + T)

and enter the following command:

```
sudo lshw
```

and copy/paste the *- cdrom section in your next post .

---

### Post by Splooshie123 on 2012-03-06
Are you using a dual boot system? If you are, see if you can access the drive from there to find out if its the drive thats faulty of an Ubuntu bug.

---

### Post by Splooshie123 on 2012-03-06
Are you using a dual boot system? If you are, see if you can access the drive from there to find out if its the drive thats faulty of an Ubuntu bug.

---

### Post by okkie on 2012-03-06
thanks,all cablesin order.Only hard disk is sata.below is the requested info  *-cdrom:0
                description: DVD reader
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd
                configuration: status=nodisc
           *-cdrom:1
                description: CD-R/CD-RW writer
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio cd-r cd-rw
                configuration: status=open

---

### Post by okkie on 2012-03-06
singleboot system Ubuntu only

---

### Post by maniandram on 2012-03-06
Try this in a terminal:
```

sudo mkdir /media/xxx
sudo mount /dev/cdrom /media/xxx

```
Try going to /media/xxx.
You should see your cd's files there.
:popcorn:

---

### Post by okkie on 2012-03-07
It says the file exists.

Surely this cannot be such a big problem?

---

### Post by winh8r on 2012-03-07
Disconnect the dvd reader drive but leave the cd/dvd writer drive connected, restart and put a standard commercial audio cd in the drive and see if it reads it.


Have you tried booting the machine using a Ubuntu Live cd?

---

### Post by djembeing on 2012-03-07
I am having a similar problem.  I tried what maniandram said.  
terminal came back with this.

mount: /dev/sr0: unknown device

here's my thread with some more info on my problem.  
[http://ubuntuforums.org/showthread.php?t=1889538 ]("http://ubuntuforums.org/showthread.php?t=1889538")


hope we can all get this resolved.

(btw: love zappa)

---

### Post by okkie on 2012-03-08
thanks it reads it properly but does not show on the desktop as usual,you go places computer and there it is.I must tell you I have just had a long struggle to get the places menu working again which I discovered is a maverick built in problem.
Any suggestions for the dvd drive still disconnected ?

---

### Post by winh8r on 2012-03-08
Reconnect the other drive now, as from your last post I have gathered that the problem is not as the title suggests "suddenly computer not reading disk drives 10.10" but is infact, "suddenly computer does not show icons on desktop when cd/dvd is inserted".

This is an entirely different problem.

open a terminal and enter:

```
gconf-editor
```

navigate using the left hand menu to 

apps > nautilus > desktop

look down the left for the entry that reads 

volumes_visible

and make sure it is selected

close gconf editor

then run in terminal

```
sudo updatedb
```

icons should now appear on desktop.

Hope this helps

---

### Post by okkie on 2012-03-09
with dvd disconnected it reads the normal cd drive.I had places menu problems which is now solved.I think I need a launcher or program to open the dvd drive but my knowledge too little.
What should the next step be ?

I go to places-computer and then right click on the DVD icon,select brasero disk burner.I can see it wants to open the dvd drive for a split second ,but cannot.

The normal cd drive now working properly

---

### Post by winh8r on 2012-03-09
Ok, now that we know that the cd drive is working for sure, and works with the dvd drive disconnected. Try doing the reverse. Disconnect the cd drive, but leave the dvd drive connected. Restart the computer and check to see if the dvd drive will function properly by inserting a dvd and allow it to detect the disk and display an icon on the desktop.

---

### Post by okkie on 2012-03-09
no go ! detecting light when putting in a DVD works,open and close no problem but brasero or similar still fails to read the disk.

I don't know if this could be relevant but for a few days now firefox keeps crashing from time to time

---

### Post by winh8r on 2012-03-09
Go to the Ubuntu Software Centre

search for brasero

click on remove

search for CD/DVD Creator

click on install

put a blank DVD in the drive and restart the computer.

Check if it recognises it and offers to let you burn files to it.

Also try putting a cd (preferably a commercially recorded audio cd ) in the dvd drive and see if it will play.


I do not think the issue with Firefox crashing is directly related to this problem, but it does seem to indicate that along with the other issues you have had, that your system has had some problems recently.

You could also run these commands:

```
sudo apt-get check
```

```
sudo apt-get update
```

```
sudo updatedb
```

in that order.

report any errors.

---

### Post by okkie on 2012-03-09
dvd drive reads commercial music cd and rythmbox plays it.
Still does not read blank dvd.
sudo apt-get updatedb is an illegal operation according to my computer
I uninstalled brasero as you suggested and only devede dvd/cd cretor is now in use

---

### Post by winh8r on 2012-03-09
I apologise, that was a typo, which I have corrected. it should have read:

```
sudo updatedb
```

also enter these commands:

```
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4
```

then

```
sudo apt-get install avidemux devede todiscgui tovidgui
```

then run

```
sudo apt-get update
```


try the dvd drive again, both playing a dvd film and try to allow burning on a blank disc.

At least we have ruled out the drive being faulty now!

Hope this works.

---

### Post by okkie on 2012-03-10
Not working but I think we are going to kill this problem now
The computer is reading everything, but has nothing set-up to open it with
Remember we uninstalled Brasero and installed devede cd/dvd extractor,
I now went to places.....computer and tried to open dvd rom with first "open" and then  "open with" option and nothing happened.I then realised there is nothing on my "open with"list that can open the either of the roms.
I attach a screenshot of the list and now also realise that we are back to the Ubuntu 10.10 places menu built-in problem which I have read so much about and somebody at Canonical wrote 'will probably never receive attention'.
My confidence in you however will prove the contrary and I know there are many folks out there with the same problem.
Your help is still very appreciated.
Thanks

PS
even more close,screenshot can not be opened and will also not upload to here.

---

### Post by winh8r on 2012-03-10
Ok,

we will try gnomebaker 

```
sudo apt-get install gnomebaker
```
 when it is installed open it and go to Edit > Preferences > Devices

does it show the drive there?

If not , select the "Scan for devices option"

If it still does not show up , select the "add Device option and navigate to the location of the drive and set it there.

Close gnomebaker

Then insert a dvd (blank dvd-rw) and see if gnomebaker detects it .

if not, open gnomebaker from the menu (or from the terminal if it is not appearing in the menu under sound and video)

```
gnomebaker
``` will start it from the terminal.

---

### Post by okkie on 2012-03-10
dvd combo reads movies from dvd and any music cd or music dvd.
Will not read any blank dvd because no burning program is available to open it.
Places.....computer....cd/dvd right click then open with just doesn't offer an application to open a dvd with.Also not gnomebaker which is now installed.
how can I get brasero,dvd/cd creator and gnomebaker back into the 'open with list'?that seems to be the problem.

---

### Post by winh8r on 2012-03-10
Not 100% sure on 10.10 but I think you can right click on Applications, then select "edit menu"

and from there you can choose what to include in menu.

You should also be able to select any program to open a cd/dvd by right clicking on cd/dvd menu and where it says "open with another application"

at the bottom of the window it says "custom command" , if you click there and put gnomebaker in the box it should cause gnomebaker to be associated with opening blank media.

---

### Post by okkie on 2012-03-11
I have with some trouble managed to get gnomebaker to open.I added some photos to the burning list to burn them to dvd but unsuccessful as it cannot read the blank dvd.
The problem is definitely the places menu and I will now find out if there  is a patch that can possibly restore the "open with" menu.
Will report if I am sucessful and will check from time to time if you found some solution.
Thanks

---


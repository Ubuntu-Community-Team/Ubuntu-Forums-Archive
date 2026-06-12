---
title: "major ipod trouble. please help!!!"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Captain Cole on 2008-10-05
I have an apple ipod 80g classic. and no matter what i do i can not get the Ipod to read the music files; it reads all the files as "other" except for the music files. I have tried Aramok, Banshee, gtkpod, and other programs (sudo apt-get install ubuntu-restricted-extras)  but nothing seams to work. Any ideas would be extremely helpful.

---

### Post by markbuntu on 2008-10-05
If you are having trouble getting your Ipod to work, try this guide:

[http://ubuntuforums.org/showthread.php?t=906217](http://ubuntuforums.org/showthread.php?t=906217)

---

### Post by HellNoire on 2008-10-05
Which generation iPod is it?

---

### Post by Captain Cole on 2008-10-05
sixth generation.

---

### Post by Captain Cole on 2008-10-05
Markbuntu, I went to the thread you suggested... It looks lie it is for Hardy... I am using Gutsy 7.10

---

### Post by shifty_powers on 2008-10-05
it should still work fine, wouldn't worry about that...

only thing you need to change in that is

> 
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

to

> 
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

---

### Post by Captain Cole on 2008-10-05
Ok... I'm a little confused here. Do I start following the commands from the beginning of this link or where it starts with 'Hack' for the model 6 generation 80 GB Classic ?

---

### Post by shifty_powers on 2008-10-06
> [SIZE="2"]**Ipod Models list and status**[/SIZE]

**1st and 2nd Gen.                    **Works out of the box
**3rd Gen. 	                    **Works out of the box
**4th Gen. Greyscale 	            **Works out of the box
**4th Gen. Photo/Color 	            **Works out of the box
**Mini 1st Gen. 	                    **Works out of the box
**Mini 2nd Gen. 	                    **Works out of the box
**Nano 1st Gen. 	                    **Works out of the box
**Nano 2nd Gen. 	                    **Needs hack
**Nano 3rd Gen. 	                    **Needs hack
**5th Gen. (Video) 	            **Works out of the box
**5.5th Gen. 30 GB (Late 2006 Video)  **Works out of the box
**5.5th Gen. 80 GB (Late 2006 Video)  **Works out of the box
**6th Gen Classic 	            **Needs hack
**Shuffle 	                    **Unknown (info needed)

[SIZE="2"]**Update your sources**[/SIZE]
Download the file [COLOR="Red"]sources.txt[/COLOR] located at the end of this topic on your desktop.

Open a terminal window and type:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.ORIGINAL
```
```
sudo mv ~/Desktop/sources.txt /etc/apt/sources.list
```
Then do:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
(accept the updates if any)

Add now the Medibuntu (Media & Distractions) sources:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
You may be asked to accept this package even though it cannot be authenticated. This is normal; typing "Yes" means you trust Medibuntu.

Then do again:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
(accept the updates if any)

Your sources now are complete and the system is full upgraded.

[SIZE="2"]**Hack Ipod (see your model from the list at the top)**[/SIZE]
Plug and mount (usually automounting) the ipod to your box, then do:
```
sudo lsusb -v | grep -i Serial
```
The output should be something like:
```
iSerial [COLOR="Red"]000A2700133125F5[/COLOR]
```

Edit (or create) this file on your ipod:
```
nano [COLOR="Red"]/media/IPOD[/COLOR]/iPod_Control/Device/SysInfo
```

* note: the [COLOR="Red"]/media/IPOD[/COLOR] is the default mounting point of Ipod in Ubuntu (change with yours if different)

Add to SysInfo file the following line and save the file (ctrl+x using nano):
```
FirewireGuid: 0x[COLOR="Red"]ffffffffffffffff[/COLOR]
```

* change the [COLOR="Red"]ffffffffffffffff[/COLOR] value with the value grabbed above with the lsusb (iSerial) command

Unmount the ipod (right click on Ipod icon on desktop choose: safely remove).

Good. Ipod is "hacked".

[SIZE="2"]**Install the software**[/SIZE]
```
sudo apt-get install amarok libgpod3 gtkpod-aac
```
Note: I suggest to use Amarok as audio player/ipod manager (is for KDE env but works good in Gnome too), but if you wish you can use also or instead:
- rhythmbox
- exaile
- banshee

Plug back your Ipod, now you can use it with your favourite program or, for a quick check you can try gtkpod, so in a terminal window type:
```
gtkpod
```

Enjoy you Ipod on Ubuntu Hardy.

Update 20/10/2008
**Quick trick for Amarok annoyance**
If you have the problem to see the Ipod under Amarok, you should follow these steps:

   1. Mount ipod
   2. Open Amarok and configure the Ipod manually under menu Options
   3. Close (quit) Amarok
   4. Umount the Ipod
   5. Mount the Ipod again
   6. Open Amarok... you should see the Ipod under devices

is what you need to do...

---

### Post by Captain Cole on 2008-10-06
i started to d/l this program over 2 hr. ago and so far it is up to only 55%. is there something wrong with it, or is it OK?

---


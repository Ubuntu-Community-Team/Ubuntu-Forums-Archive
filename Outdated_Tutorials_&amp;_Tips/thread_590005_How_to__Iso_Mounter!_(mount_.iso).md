---
title: "How to : Iso Mounter! (mount *.iso)"
date: 2007-10-24
forum: Outdated Tutorials &amp; Tips
---

### Post by UK-Wobbie on 2007-10-24
Hello all i been looking for some good ISO Image mounters to mount some ISO game files of mine.. And i seen this one!

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

Am going to put this all down.. Because the guy who made that topic on that site did not put it in right!    
It did not work. :(


Right where to start? :lolflag:

You have to download 2 files what are called "mount" and "unmount"... 
You can get this from the site link at the top or here.

[mount.sh]("http://www.debianadmin.com/images/iso/mount.sh") - [unmount.sh]("http://www.debianadmin.com/images/iso/unmount.sh")

Save the 2 files on to your desktop.
And here are the commands for Terminal... Put your user name in where is says user name.:lolflag:



sudo chmod +x /home/USER NAME/Desktop/mount.sh

sudo chmod +x /home/USER NAME/Desktop/unmount.sh



This is for changing the permissions!


Then what we do is put this in... Using the same user name in user name!



sudo mv /home/USER NAME/Desktop/mount.sh ~/.gnome2/nautilus-scripts/

sudo mv /home/USER NAME/Desktop/unmount.sh ~/.gnome2/nautilus-scripts/



This is for setting all of it up and moving "mount" and "unmount" In to the setup folder.


Thats it all done :mrgreen:

Right click on a ISO and go to scripts you will see in scripts "mount" and "unmount"... When you click on mount it will ask for your password put it in and click on ok!

Then when that is all done you will see a  message saying 
"Successfully mounted"  click ok.

Now it will open a drive.. In the drive will be your files! 

And a drive icon will be on your desktop. 

In your system computer folder will be a drive icon to!


The drive can play some Computer ISO games for Wine to play!


For more info go to -> [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

---

### Post by shoaibi on 2007-11-19
great!!!!

---

### Post by shoaibi on 2007-11-19
I tried this for a ISO file that did have spaces in the file name, is that matters, and it gave me this on mount:

ISO Mounter
 e /media/sda5/Academics/Co-Curricular/Video Lectures/Linux tutorial/Shell 
Fundamentals.iso
<OK>


and then


ISO Mounter
Cannot mount !
<OK>


can you tell me why?

---

### Post by danevans29 on 2007-11-20
Thanks for the script, however I'm getting the same error as shoaibi.  Where are we going wrong?

---

### Post by rbmorse on 2007-11-20
If your filename has spaces (bad practice in general) it needs to be enclosed in " marks.  In  this case it is probably easier to rename the .iso file to something without spaces.

---

### Post by Roobin on 2007-11-20
I tried Gmount-Iso...and didn't like the French. Now I use AcetoneISO and it works really well!

---

### Post by Keith Hedger on 2007-11-20
Put these two files in your nautilus scripts folder ie:
/home/YOURUSERNAME/.gnome2/nautilus-scripts
change the password in them (or dont use sudo use gksudo)
set the exec flag and then just right click on an iso to mount it and right click on the desktop icon to unmount it:)

---

### Post by bodhi.zazen on 2007-11-20
> **shoaibi said:**
> I tried this for a ISO file that did have spaces in the file name, is that matters, and it gave me this on mount:

ISO Mounter
 e /media/sda5/Academics/Co-Curricular/Video Lectures/Linux tutorial/Shell 
Fundamentals.iso
<OK>


and then


ISO Mounter
Cannot mount !
<OK>


can you tell me why?

he he he ...

that is why you should quote your variables in bash scripts.

If the variable is embeded in text, use brackets.

echo /media/"${i}"

> The "$" character introduces parameter expansion, command substitution, or arithmetic expansion. The parameter name or symbol to be expanded may be enclosed in braces, which are optional but serve to protect the variable to be expanded from characters immediately following it which could be interpreted as part of the name.

so ...

> #!/bin/bash

PASS="YOUR PASSWORD"
echo "$PASS" | sudo -S mkdir /media/"${1}"
echo "$PASS" | sudo -S mount -o loop "${1}" /media/"${1}"

In addition , you need to quote or escape the spaces if you run that script from the command line :

> bodhi@host:~/test$ ls
[color=green] script[/color]

bodhi@host:~/test$ [color=red]sh script iso with spaces.iso[/color]
bodhi@host:~/test$ ls
[color=red]iso[/color] [color=green] script[/color]

bodhi@host:~/test$ rm -rf iso/

bodhi@host:~/test$ [color=blue]sh script "iso with spaces.iso"[/color]
bodhi@host:~/test$ ls
[color=blue]iso with spaces.iso[/color] [color=green] script[/color]

bodhi@host:~/test$

:guitar:

---

### Post by bluemech on 2007-11-20
Wow this works really well. Don't need a big interface like AcetoneISO when I can do it like this.

Thanks!

---

### Post by Keith Hedger on 2007-11-21
brackets are only needed when there may be confusion about the variable name ie:

avar="some data "

echo $avarsomeotherdata

would not work (theres no variable called avarsomeotherdata)
so echo ${avar}someotherdata
would produce "some data someotherdata"
You also need bracets when string slicing
so "${1}" /media/"${1}" as above does no harm but is redundant
as "$1" /media/"$1" does not cause any variable name confusion

---

### Post by bodhi.zazen on 2007-11-21
Keith Hedger: Thanks for the information.

I was trying to pass on some knowledge (about {} and " " with variables) and appreciate your clarification.

---

### Post by danevans29 on 2007-11-22
Perfect! Thanks so much.

---

### Post by Jeremy_Kyle_Vanhorn on 2008-03-30
> **UK-Wobbie said:**
> Hello all i been looking for some good ISO Image mounters to mount some ISO game files of mine.. And i seen this one!

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

Am going to put this all down.. Because the guy who made that topic on that site did not put it in right!    
It did not work. :(


Right where to start? :lolflag:

You have to download 2 files what are called "mount" and "unmount"... 
You can get this from the site link at the top or here.

[mount.sh]("http://www.debianadmin.com/images/iso/mount.sh") - [unmount.sh]("http://www.debianadmin.com/images/iso/unmount.sh")

Save the 2 files on to your desktop.
And here are the commands for Terminal... Put your user name in where is says user name.:lolflag:



sudo chmod +x /home/USER NAME/Desktop/mount.sh

sudo chmod +x /home/USER NAME/Desktop/unmount.sh



This is for changing the permissions!


Then what we do is put this in... Using the same user name in user name!



sudo mv /home/USER NAME/Desktop/mount.sh ~/.gnome2/nautilus-scripts/

sudo mv /home/USER NAME/Desktop/unmount.sh ~/.gnome2/nautilus-scripts/



This is for setting all of it up and moving "mount" and "unmount" In to the setup folder.


Thats it all done :mrgreen:

Right click on a ISO and go to scripts you will see in scripts "mount" and "unmount"... When you click on mount it will ask for your password put it in and click on ok!

Then when that is all done you will see a  message saying 
"Successfully mounted"  click ok.

Now it will open a drive.. In the drive will be your files! 

And a drive icon will be on your desktop. 

In your system computer folder will be a drive icon to!


The drive can play some Computer ISO games for Wine to play!


For more info go to -> [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)





i tried this but i keep getting
"chmod: cannot access `/home/jeremy/desktop/mount.sh': No such file or directory" 

i have the mount and unmount files saved to the desktop. i need help

---

### Post by Jose Catre-Vandis on 2008-03-30
If you want a gui ISO mounter, try gmountiso, it's in the repos, requires python

---

### Post by phetre on 2008-03-30
Jeremy, try capitalizing Desktop in those two chmod commands.

---

### Post by trannypunk on 2008-05-07
Amazing. Thanks!

---

### Post by bulletxt on 2008-05-08
all this mess for a stupid ISO? install AcetoneISO, it does not mount just ISO and does waaaaaaaaay more things. it's just so easy and fast, I really don't understand what's the point of an only ISO script while there are better things that support all formats and has a cool UI. ok anyone can choose anything he wants of course!

oh and by the way, it does not require admin password to mount images!

a quick link to acetoneiso 2.0.2 deb for 32bit:
[http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_20080508-1_i386.deb?use_mirror=garr](http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_20080508-1_i386.deb?use_mirror=garr)

---

### Post by nisseblink on 2008-05-09
> **bulletxt said:**
> all this mess for a stupid ISO? install AcetoneISO, it does not mount just ISO and does waaaaaaaaay more things. it's just so easy and fast, I really don't understand what's the point of an only ISO script while there are better things that support all formats and has a cool UI. ok anyone can choose anything he wants of course!

oh and by the way, it does not require admin password to mount images!

a quick link to acetoneiso 2.0.2 deb for 32bit:
[http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_20080508-1_i386.deb?use_mirror=garr](http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_20080508-1_i386.deb?use_mirror=garr)

Works perfect!

---

### Post by powerpleb on 2008-05-09
> **bulletxt said:**
> all this mess for a stupid ISO? install AcetoneISO, it does not mount just ISO and does waaaaaaaaay more things. it's just so easy and fast, I really don't understand what's the point of an only ISO script while there are better things that support all formats and has a cool UI. ok anyone can choose anything he wants of course!

oh and by the way, it does not require admin password to mount images!

On the contrary, why would I download and install a new program when I can already do what I need it to with a simple script.

Thanks!

---

### Post by marcusfurius on 2008-05-14
You could try [this application]("http://www.marcus-furius.com/?page_id=14"). It is designed specifically for Ubuntu, installs via a deb installer, has a simple to use GUI and mounts ISO, IMG, BIN, MDF and NRG Images, and doesn't require a password to mount images.

---

### Post by stinger30au on 2008-05-14
awesome!

thanks

---

### Post by Gourgi on 2008-05-17
> **marcusfurius said:**
> You could try [this application]("http://www.marcus-furius.com/?page_id=14"). It is designed specifically for Ubuntu, installs via a deb installer, has a simple to use GUI and mounts ISO, IMG, BIN, MDF and NRG Images, and doesn't require a password to mount images.

looks really nice but i don't see a amd64.deb :(

i filled a question for it @ launchpad
[https://answers.launchpad.net/furiusisomount/+question/33383](https://answers.launchpad.net/furiusisomount/+question/33383)

---

### Post by nabilalk on 2010-01-27
I'm using Thunar not Nautilus. Is there any way to apply these scripts to Thunar? Thanks.

---


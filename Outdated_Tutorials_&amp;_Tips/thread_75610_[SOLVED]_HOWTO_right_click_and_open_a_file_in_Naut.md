---
title: "[SOLVED] HOWTO: right click and open a file in Nautilus with gedit as root"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-13
we often need to edit files as root in a text editor. Now we can do this with a right click in Nautilus (no big deal about opening in terminal but what the heck!)
```
gedit ~/.gnome2/nautilus-scripts/gedit-root
```
Copy the following lines into the file and save it and close it.
```
#created by arnieboy
foo=`gksudo -u root -k -m "enter your password for gedit root access" /bin/echo "Do you have root access?"`
sudo gedit $NAUTILUS_SCRIPT_SELECTED_URIS
```
Then make it executable with
```
chmod +x ~/.gnome2/nautilus-scripts/gedit-root
```
thats it you are all set. Now right click on any file in nautilus and under "scripts" u will find "gedit-root"
click and enjoy!
U can even select multiple files and open them in gedit as root in tabbed windows just by right clicking and using this script. The possibilities are endless.

---

### Post by MButterman on 2005-10-14
Thanks Arnie,
Breezy has been doing great. I have a question off topic though. Since I have k3b for my cd burning, how would I change the default player for mp3's from sound juicer to xmms. I have all codecs installed. thanks for the script. I've been looking for a way to do this without terminal. 

My Best,
MButterman

---

### Post by Nomearod on 2005-10-14
Tanks for the how-to. This is really going to help me ^_^ 

 i'm a noob at Linux. and sometimes I need to edit some files and I don't like go to the terminal and do the things there..

---

### Post by mgor on 2005-10-14
great tip!

---

### Post by arnieboy on 2005-10-14
[QUOTE=MButterman]Thanks Arnie,
Breezy has been doing great. I have a question off topic though. Since I have k3b for my cd burning, how would I change the default player for mp3's from sound juicer to xmms. I have all codecs installed. thanks for the script. I've been looking for a way to do this without terminal. 

My Best,
MButterman[/QUOTE]
open nautilus, right click on any mp3 hit properties and change the default player from there.

---

### Post by manicka on 2005-10-14
Thanks arnieboy, this script since you made it available in hoary, has been something I have used extensively.

---

### Post by arnieboy on 2005-10-14
[QUOTE=manicka]Thanks arnieboy, this script since you made it available in hoary, has been something I have used extensively.[/QUOTE]
thank u for all the appreciation manicka :)

---

### Post by oldlucky on 2005-10-15
Thankyou so much arnieboy that is a great tip.This is such a great forum you learn so much on here.:smile: 

Cheers oldlucky

---

### Post by hanzj on 2005-10-15
how about a nautilus hack that allows sudo access to moving/renaming/et cetera of restricted folders/files?

---

### Post by Omnios on 2005-10-16
Cool Im also looking for right click open file as root. Used mostly to play abound with and update games with hacks and patches.

 Edit re: does it work in 5.10 noticed that before end edited while you where posting. I was doing a bunch of searches and confused it with a 5.04 post

---

### Post by arnieboy on 2005-10-16
[QUOTE=Omnios]Does this work properly in Breezy[/QUOTE]
if it hadnt, i wudnt post it here.. wud I?

---

### Post by Jaivaz on 2005-10-17
A quick little question here. I enjoy using Mousepad more than gEdit, so if I changed a few things in the script to "mousepad" it should still work the same, correct?

---

### Post by arnieboy on 2005-10-17
[QUOTE=Jaivaz]A quick little question here. I enjoy using Mousepad more than gEdit, so if I changed a few things in the script to "mousepad" it should still work the same, correct?[/QUOTE]
since I dont use (and have never used Mousepad) i cant say. u can test and find out.

---

### Post by lucaas on 2005-10-17
The script seems doesn't work in Breezy, i choose the gedit-root script in the right-click menu, but there is no response.
Thanks your work all the same


lucaas

---

### Post by arnieboy on 2005-10-17
[QUOTE=lucaas]The script seems doesn't work in Breezy, i choose the gedit-root script in the right-click menu, but there is no response.
Thanks your work all the same


lucaas[/QUOTE]
"doesn't work in breezy" is wrong. "doesn't work for u" is more correct.
did u follow all the steps that I outlined? and are u sure u pasted the correct contents in the script and made it executable?

---

### Post by lucaas on 2005-10-17
I must make sth. wrong that i don't know.
I have followed your guide, just copy and paste the codes, but it still doesn't work for me. :-(
I type ~/.gnome2/nautilus-scripts/gedit-root in the terminal, gedit can run as root 
Is there other thing I have to be careful? 
THANKS for your help

---

### Post by pminetti on 2005-10-18
Arnieboy:
It works very well but I like if you can explain a little how it works

thanks

---

### Post by arnieboy on 2005-10-18
[QUOTE=pminetti]Arnieboy:
It works very well but I like if you can explain a little how it works

thanks[/QUOTE]
which part of the script could you not understand?

---

### Post by tomski on 2005-10-19
thank you for the tip arnieboy cheers

---

### Post by mcrosmar on 2005-10-21
Great tip arnieboy. Thank you.....

---

### Post by monotux on 2005-10-21
Great tip!
Thanks :)

---

### Post by LinuxWiz83 on 2005-10-25
What if that file is missing and you have gedit?

---

### Post by arnieboy on 2005-10-25
[QUOTE=LinuxWiz83]What if that file is missing and you have gedit?[/QUOTE]
it will refer u to an IQ test.

---

### Post by mjkey on 2005-10-27
Thank you for the great tip. A folder of great tips would sure help a simpleton like myself.

---

### Post by Sionide on 2005-10-28
Quality, nautilus scripts are one of those awesome features which aren't shown off enough.

---

### Post by hanzj on 2005-10-28
what other nautilus scripts would be handy?
what other nautilus scripts are available?

:-({|=

---

### Post by Sionide on 2005-10-28
Loads, check out; [http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php)

---

### Post by dez on 2005-10-28
This is slightly off topic , but I am having a really dumb moment. 

How can I edit my right click context menu. In Hoary, it use to have "New Terminal", but in Breezy  its gone. I want it back. 


Thanks

---

### Post by 23meg on 2005-10-28
Those who found this handy may also be interested in this trick: [http://ubuntuforums.org/showthread.php?t=24008](http://ubuntuforums.org/showthread.php?t=24008)

---

### Post by hanzj on 2005-10-28
The thread which 23meg refers to (and is original poster of) is handy, but I recommend you follow [the instructions of alexp (post #8 ) ]("http://ubuntuforums.org/showpost.php?p=128057&postcount=8") to get that hack going.

:-({|=

---

### Post by manicka on 2005-11-03
This How-To is also available at the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page")

---

### Post by LinuxWiz83 on 2005-11-10
[QUOTE=arnieboy]it will refer u to an IQ test.[/QUOTE]

hey now you did not have to say it like that. I just was not awake obviously that day but thank you for the tip.

---


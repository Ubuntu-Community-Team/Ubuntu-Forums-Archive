---
title: "Change Display Driver and Resolution"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Darthape on 2008-11-01
How would I change the driver for my video card to increase my resolution. I only have 800x600 or 640x480. Thanks

---

### Post by overdrank on 2008-11-01
> **Darthape said:**
> How would I change the driver for my video card to increase my resolution. I only have 800x600 or 640x480. Thanks

Hi and a little more info would help, what is the model of the graphics card and what version of Ubuntu are you using, Hardy, Intrepid?

---

### Post by oldsoundguy on 2008-11-01
What video card are you using and what type of monitor? CRT or LCD?

---

### Post by Darthape on 2008-11-01
I am using 8.10 and an S3 (I think) card. I have installed 7.10 and there was a menu item that allowed you to change your resolution and driver for your card but I can't find it.

---

### Post by Darthape on 2008-11-01
CRT monitor that get up to 1280x1024

---

### Post by Darthape on 2008-11-01
Bump

---

### Post by oldsoundguy on 2008-11-01
may be time to upgrade the monitor. (LCD's are like ***, once you try it, you never want to go back! LOL)
And you will be surprised at just how much space you have on your WORK DESK!

---

### Post by krtica on 2008-11-01
I have S3 / VIA Chrome9 HC graphic. I tried everything i could find on google and forum, but i didn't solve problem with graphic on 8.10. I can't even get to gui. :( But i'm absolute beginner on Ubuntu and i hope that someone will find solution. Now i'm back to 8.04 and 2D.

---

### Post by Darthape on 2008-11-01
I wish i had money to get one but i don't. Any way i could change the resolution?

EDIT: I searched the forum and used ```
 sudo dpkg-reconfigure xserver-xorg 

``` 
to create the config file but i can't put a modeline that was created in the specified place in the xorg.conf file.

---

### Post by krtica on 2008-11-01
Did you try this:

[http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/](http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/)

---

### Post by Darthape on 2008-11-01
Cant log in as root to edit the file

---

### Post by krtica on 2008-11-01
Did you try with?

> sudo gedit /etc/X11/xorg.conf

I'm sorry if this is stupid question - i'm noob. :D

And then in Section "Screen" adding something like

> 	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

Use this link for details: [http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/](http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/)

---

### Post by Darthape on 2008-11-02
Tried that and it broke X. I fixed X and and again back with a 800x600 resolution. How do i write my own xorg.conf file to get the correct resolution again?

---

### Post by bscbrit on 2008-11-02
[http://ubuntuforums.org/showpost.php?p=6085570&postcount=5](http://ubuntuforums.org/showpost.php?p=6085570&postcount=5)

This might help.

---

### Post by Darthape on 2008-11-02
The openchrome driver crashes my videocard and the vesa driver doesn't let it load x. Any suggestions?

---


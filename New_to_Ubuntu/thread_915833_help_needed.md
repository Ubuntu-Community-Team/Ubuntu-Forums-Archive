---
title: "help needed"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by satya_18948 on 2008-09-10
i just downloaded an os (image file)having mdf format i wanted to burn it on a cd and make it bootable can anyone help me
 plsss help needed desperately

---

### Post by Sef on 2008-09-10
What exactly are you wanting to burn?  GNU/Linux oses are iso files.

---

### Post by graben3 on 2008-09-10
I dont think you can burn directly a .mdf

One solution is to convert your image to iso with mdf2iso
[http://freshmeat.net/projects/mdf2iso/](http://freshmeat.net/projects/mdf2iso/)

Or open a terminal window and type :

sudo apt-get install mdf2iso

Then, to convert it using this utility, in a terminal type : 

mdf2iso /pathto/sourcefile.mdf /pathto/destfile.iso

That should do it unless your MDF file is too large...

---

### Post by graben3 on 2008-09-10
Also found this :

[http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html](http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html)

Seems more user friendly than my previous method !

---

### Post by hyper_ch on 2008-09-10
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by graben3 on 2008-09-10
Just convert your MDF to iso using Acetone

To install Acetone : 

32 bits Hardy :
[http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_2.0.2-20080602_i386.deb?use_mirror=osdn](http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_2.0.2-20080602_i386.deb?use_mirror=osdn)


64 bits hardy : 
[http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_2.0.2_amd64.deb?use_mirror=garr](http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_2.0.2_amd64.deb?use_mirror=garr)

To burn the iso :
use Basero Disc Burning that comes with your Ubuntu installation in the Applications -> Sound and video menu

---

### Post by satya_18948 on 2008-09-10
alredy tried converting the mdf to iso file but it just doesn't work it give an  could not find ntld error  i am trying to install an xp sp3 unattended silent

---

### Post by graben3 on 2008-09-10
1. 
Did you try Acetone iso ????


2. If yes and it did not work, 
Try k3b :

Go to Applications -> Add remove

Search for k3b. Check and apply

That is supposed to burn MDF files as many people say on other forums tell me if that does it. I dont have a MDF file so I cant test this for you...

---


---
title: "[SOLVED] help"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by sosalini on 2008-07-03
hi all newbies , Im needing help. I have installed ubuntu 8.04 last weekend after a few problems it finally worked . Im more than satisfied with it , its fast , looks good and everything looks better than xp . However Ive had a few problems and got a few questions I hope someone can answer for me . 
1 I set it up to partition the drive to run both xp and ubuntu just so I could get used to it before removing xp . Well it looks like Ive completely removed xp , no problem , as I was going to anyway in time , Ive been to partition manager and cant see any partition , but not sure , not very geeky here , how do you tell , Im totally unfamiliar with what Im looking for and the help pages dont load so cant tell if I have still got xp or not .
2 I saved my music and pictures to an outboard hard drive , can I just turn it on and will ubuntu read the drive and download the music and pictures , or will it cause problems , as the pics are on xn view , which Ive tried unsuccesfully to install on ubuntu , and the music is all mp3 , which Im told ubuntu cant read due to copyright issues . 
The installation of non linux programs is a big mystery to me , not being used to terminal and writing codes , given it a go but keep getting error messages . getting nowhere fast , any help would be greatly appreciated .
I like ubuntu a lot , its exciting seeing new programs Ive never heard of , but want to download things like flash player and havnt a clue how to .
Any replies will need to be in plain english please , no abbreviated terms or words like sticky ! what is that , I dont like xp , but it was easy to go to xn views site click download and get the program set up for me . Im interested in what I can do , not become a computer programmer .
Thanks for reading this and once again any help will be very greatly appreciated , Im not going back to microsoft whatever happens but need help here to get a grip on what to do and how , in very plain english .
Thanks .

---

### Post by hyper_ch on 2008-07-03
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by jolx on 2008-07-03
with no. 2
run this in a terminal (Applications -> Accessories -> Terminal):
```
sudo apt-get install ubuntu-restricted-extras
```

and u might want to see [this]("https://help.ubuntu.com/community/Medibuntu") so u can play dvd's

and then u can just turn on ur external hdd and copy the files to whatever folders u want

---

### Post by chewearn on 2008-07-03
> **sosalini said:**
> 
1 I set it up to partition the drive to run both xp and ubuntu just so I could get used to it before removing xp . Well it looks like Ive completely removed xp , no problem , as I was going to anyway in time , Ive been to partition manager and cant see any partition , but not sure , not very geeky here , how do you tell , Im totally unfamiliar with what Im looking for and the help pages dont load so cant tell if I have still got xp or not .

Ubuntu has a partition manager, called "Gparted".  To install:
1. search for "gparted" in Add/Remove, or
2. click this [link]("apt://gparted"), or
3. run this command in a command-line terminal
```
sudo apt-get install gparted
```> 2 I saved my music and pictures to an outboard hard drive , can I just turn it on and will ubuntu read the drive and download the music and pictures , or will it cause problems , as the pics are on xn view , which Ive tried unsuccesfully to install on ubuntu , and the music is all mp3 , which Im told ubuntu cant read due to copyright issues . Open pictures should definitely not be a problem, as long as it's not an unusual format.  Common formats like jpg, gif, tif, bmp, png and many others are supported.

mp3 is not supported by default, but installing the package ubuntu-restricted-extras will solve it.

> 
The installation of non linux programs is a big mystery to me , not being used to terminal and writing codes , given it a go but keep getting error messages . getting nowhere fast , any help would be greatly appreciated .We need the specifics of the program you want to install to be able to give a good guide.

> 
I like ubuntu a lot , its exciting seeing new programs Ive never heard of , but want to download things like flash player and havnt a clue how to .Installing ubuntu-restricted-extras (as mentioned above) will also give you flash player.



Welcome to ubuntu, and hope you enjoy your stay.

---

### Post by nothingspecial on 2008-07-03
It is possible to use some windows programs with a program called wine. However there is usually a linux alternative.
 Go to System >Administration >Software sources and tick all the boxes in the first tab. Then you can search Synaptic Package Manager for Ubuntu supported software.
 Also follow this [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It`s just a matter of copy and pasting.Once you`ve done that you can listen to and watch anything you like.

---

### Post by bobbob94 on 2008-07-03
ok, for you first problem, open a terminal (follow this route on the menu applications>accessories>terminal). the type " sudo fdisk -l " without the quotations marks. it will ask for your password, enter it and then reply here with the results it gives you.

your external hard drive should work fine, but the only way to know is to plug it in and try it! if there are problems, come back to the forums with your difficulties and theres probably a solution. Ubuntu can read Mp3's fine, it just isn't allowed to distribute them onthe install disk, but the first time you click on an mp3 file a wizard should pop up and help you install the software you need to play them. You might want to check out [this page]("https://help.ubuntu.com/community/RestrictedFormats") for information about multimedia formats like mp3, dvd etc...
if you want to install xnview from their website thats possible but why not try the image viewing application installed in ubuntu default first. if that suits your needs, problem solved. if not, you can ask here for help in insatlling the linux version of xnview. 
many many programs (around 20,000) can be installed though the synaptic package manager (system>administration>synaptic package manager) with a couple of clicks. i recommend checking for what you need here before you start trying to dowload software from websites and install it (though i already looked for xnview and that isn't available unfortunately)

---

### Post by sosalini on 2008-07-04
Thank you all very much for your help , just logged on and will try all the ideas , Thanks again , very kind of you to take the trouble to advise me , very much appreciated .

---

### Post by sosalini on 2008-07-04
Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a964a95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4777    38371221   83  Linux
/dev/sda2            4778        4870      747022+   5  Extended
/dev/sda5            4778        4870      746991   82  Linux swap / Solaris
this is what shows up , looks like no windows xp , no problem dont want it anyway but nice to know if I have lots of space for ubuntu or not , dont want to download my music and pics from outboard hard drive and find no space to install it .
Thanks again , cant believe the kindness of people here , very kind of you to take time to help a stranger out here .

---

### Post by chewearn on 2008-07-04
Feel free to ask any question, happy to be one of the people who can help.


[SIZE=1]The main reason I hang around here for so long is the Ubuntu Spirit: humanity towards others.  [http://www.ubuntu.com/community/conduct](http://www.ubuntu.com/community/conduct)[/SIZE]

---

### Post by akiratheoni on 2008-07-04
> **sosalini said:**
> Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a964a95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4777    38371221   83  Linux
/dev/sda2            4778        4870      747022+   5  Extended
/dev/sda5            4778        4870      746991   82  Linux swap / Solaris
this is what shows up , looks like no windows xp , no problem dont want it anyway but nice to know if I have lots of space for ubuntu or not , dont want to download my music and pics from outboard hard drive and find no space to install it .
Thanks again , cant believe the kindness of people here , very kind of you to take time to help a stranger out here .

Yup yup, Windows is gone. Anyway glad to see your problem is solved, be sure to mark your thread as SOLVED... click on Thread Tools -> Marked as Solved. BTW, and thank you too for being helpful as well... support goes both ways, if both sides are helpful and nice then problems are solved faster.

---


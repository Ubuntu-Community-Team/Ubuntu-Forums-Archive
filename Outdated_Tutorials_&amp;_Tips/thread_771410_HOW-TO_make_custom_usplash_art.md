---
title: "HOW-TO make custom usplash art"
date: 2008-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Bodsda on 2008-04-27
After only being able to find posts of people asking this question i decided to explore and find out how to do it. Great thanks to garry for his tuto at -- [http://ubuntusatanic.org/forum/comments.php?DiscussionID=21&page=1]("http://ubuntusatanic.org/forum/comments.php?DiscussionID=21&page=1")

So first things first, create an image you wont to use for usplash
  try and keep the colours to a minimum

1.) Make the image 1024x768.

2.) Flatten the image so it only has one layer.
 -- in GIMP do this by {Image-->flatten image}.

3.) Reduce the colours by doing
 {Image-->Mode-->Indexed} Select "Generate optimum palette" and set the number of colours to 256.

4.) Play around with dithering to set optimum appearance, then save as a .png

5.) Repeat this for sizes -- 800x600, 1365x768, 640x480 & 640x400

------------------------------section 2 ---------------------------------

- Install some build utilities

1.) ```
sudo apt-get install cdbs debhelper dpkg-dev fakeroot devscripts autotools-dev
```

- Install the build dependencies for the usplash stuff

2.)```
sudo apt-get build-dep usplash-theme-ubuntu
```

- Get the source code - I'd base it on the xubuntu usplash.

3.)```
cd && apt-get source xubuntu-artwork-usplash
```


- Make sure you have permission to overwrite everything

4.)```
user=$(whoami) ; sudo chmod -R 777 /home/$user/xubuntu-artwork-0.19*
```

- Build the package

5.)```
user=$(whoami) ; cd /home/$user/xubuntu-artwork-0.19/ && dpkg-buildpackage -rfakeroot
```

Installation. The compilation process generates a .so file. Copy it
to /usr/lib/usplash. To install it, run

6.)```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-xubuntu.so 10
```

- Finally

7.)```
sudo update-alternatives --config usplash-artwork.so && sudo update-initramfs -u
```

- Test it with

8.)```
sudo usplash -c
```

Enjoy!!!

---

### Post by monolux on 2008-05-02
Been looking a long time for this topic big txs!!!
:)

---

### Post by Bodsda on 2008-05-06
No probs m8, the only thing i would say is when designing your art for usplash make sure your only using a 16 bit colour palette, keep colour to a minimum, try and make do with bold colours and not many different shades -- usplash is fairly limited to the amount of colour you can use.

---

### Post by Het Irv on 2008-06-11
Thanks for Writing this, It was really needed.  Wiki version?

---

### Post by ellaguno on 2008-06-19
Great post Bodsda. You have a typo in step 6

where it says ..../usr/lib/usplash/usplash-them-xubuntu.so 10

should say ..../usr/lib/usplash/usplash-theme-xubuntu.so 10

I used a 256 image (fairly big) with no problem in my laptop.

---

### Post by theozzlives on 2008-09-07
I tried this and wound up with an Xbuntu theme, I wanted my own theme

---

### Post by zakeytech on 2008-09-07
You are really something.

---

### Post by Bodsda on 2008-09-07
> **zakeytech said:**
> You are really something.

What something am i??

> I tried this and wound up with an Xbuntu theme, I wanted my own theme 
Can you paste all the commands you typed in please -- you were meant to substitute some of the names for your own ones.

> Great post Bodsda. You have a typo in step 6

where it says ..../usr/lib/usplash/usplash-them-xubuntu.so 10

should say ..../usr/lib/usplash/usplash-theme-xubuntu.so 10

I used a 256 image (fairly big) with no problem in my laptop. 
Glad i could help -- Typo fixed, thanks

---

### Post by soxs on 2008-09-07
/home/$USER and user=$(whoami) can be replaced by $HOME ;-)
nice tutorial btw

---

### Post by Bodsda on 2008-09-07
> **soxs said:**
> /home/$USER and user=$(whoami) can be replaced by $HOME ;-)
nice tutorial btw

Cheers -- i know bout the $HOME and things now, i wrote this tut quite a while back when i was less knowledgable -- maybe i should rewrite it :)

---

### Post by llelectronics on 2008-09-09
I have made a little Video Tutorial explaining and showing how to customize your usplash. (a little bit different then explained here) 
Its also based on modifying an existing usplash theme and uses almost the same method as described here.

Hope you enjoy it. This is the first of my [Ubuntu Switcher Videotutorials]("http://leszek.lesner.googlepages.com/ubuntu-switcher") in english. 

[http://blip.tv/file/1245974/](http://blip.tv/file/1245974/)

---

### Post by boob11 on 2008-10-03
Thanks

---

### Post by Mrall on 2008-10-22
Found your post very well written.  It has answered (in plain english) alot of questions I have. I am still lost as to how progress bar works though.

Where can I place it? 
How do I specify what colors of the 256 to scroll accross? 
Is the scroll bar another file? 
Can the scroll be dots or some other shape?
Just what specifies that this part of the image is the scroll bar?

I'm sorry if I seem ignorant in this matter. But, I have not seen any post that answer any of these questions. It appears that everyone assumes that everyone knows the answers to this. Maybe I'm missing something which is quite clear?

Thanks for any light you can shed on this
Mrall

---

### Post by Bodsda on 2008-10-24
> **Mrall said:**
> Found your post very well written.  It has answered (in plain english) alot of questions I have. I am still lost as to how progress bar works though.

Where can I place it? 
How do I specify what colors of the 256 to scroll accross? 
Is the scroll bar another file? 
Can the scroll be dots or some other shape?
Just what specifies that this part of the image is the scroll bar?

I'm sorry if I seem ignorant in this matter. But, I have not seen any post that answer any of these questions. It appears that everyone assumes that everyone knows the answers to this. Maybe I'm missing something which is quite clear?

Thanks for any light you can shed on this
Mrall

Your not missing anything :) I dont go into it because I dont really know how the scrollbar works myself. I may do some research over the weekend but for now its all about the pictures :)

---

### Post by AZorin on 2008-11-07
If you make the usplash images in the file browser and store it as a folder and I have the .dsc as well (not in the folder). Can anyone please tell me how to install the usplash from here:confused:

---

### Post by AZorin on 2008-11-19
U can also download the xubuntu artwork in nautilus and then open terminal, find the file ```
cd xubuntu-artwork_0.20*
``` and then just make the file ```
sudo make
``` and in the directory you should find the .so file:KS

---

### Post by dmatthys on 2008-12-13
I'm sorry everyone know this is getting to be kinda of an old thread but its such a great how to i had too

one question though is it possable to change the name of the finished product so we can use the same process to make additional usplash themes by simply changing the name or will that not work

---

### Post by begemot. on 2008-12-17
Awesome usefull HowTo, many thanks to the author!

---

### Post by yuchi on 2008-12-19
hey, I've followed the instructions to the button, and my machine restarts, which i assume is expected. the thing that confuses me is that it takes forever (over an hour...) and i just manually restart my machine. i've previously looked at many other solutions to customising my usplash theme and found the StartUp Manager, which comes with warnings of possible problems with restarting. i don't know if this tutorial has anything to do with my long restarts or whatever, was just wondering if anyone knows of any solutions?
also, when i manually restart the machine, the usplash remains as default, which means that i'm failing dismally! :(

---

### Post by smirnoff76 on 2008-12-19
FANTASTIC!!

I have been looking for a how to on this for ages and have not been able to find one, will give this a go when I get home!!

Thanks for the tutorial!!!

---

### Post by yuchi on 2008-12-19
never mind about my previous post, i managed to sort out my problem...

thanks to Bodsda for a great tutorial...it's been a great load of help!

---

### Post by edog76 on 2009-01-05
I also sucessfully made my usplash, which while not perfect, is good enough for now. One poster above asked about how to make a custom theme rather than the xubuntu theme. There should be a step between 4 and 5, call it 4.5 where you swap out your images for those in the xubuntu-artwork file. Otherwise, when you makefile, you just use the xubuntu images. llelectronics video tutorial is helpful there and also for sharing any theme you create. I think you can simply rename the .so file when finished to change it from xubuntu (I didn't do this, but will when I try to create another usplash).

---

### Post by dmatthys on 2009-01-06
once its made is the .so file all thats needed so if i wanted to install it on my wifes desktop or if i make one for her i can use our shared folders to get it to her computer however would i need to transfer the whole folder or could i just cp the .so

i still have yet to try the change of the filename either if i do i will post my findings

---

### Post by edog76 on 2009-01-06
I think it's just the .so file. I say this because I downloaded a theme from gnome-look and the only file extracted from the archive was the .so. Also when you install a theme using the startup-manager app, you select only the .so files.

---

### Post by dmatthys on 2009-01-06
right but if the .so is just a file with instructions then it needs the other files or else the instructions are void. The one that you downloaded did that work? were you able to install and use it?

---

### Post by edog76 on 2009-01-07
Yes, the downloaded theme worked. That was surprising to me, because I assumed, like you that the artwork files were also needed. Perhaps they are needed only for the making of the .so file.

---

### Post by dmatthys on 2009-01-13
>hi sorry for the length in time im in school full time right now and working full time >and my classes started up after the holidays again i still have not tried the changing >of the file name yet
>
>I am having a new issue with the instructions and ive been using these for a while now >with out a hitch the line that obtains the xubuntu source is not working i get returned >the error
>
> Unable to find a source package for xubuntu-artwork
>
>any ideas on what happened to the art work did the package go through an update is >there >another way to do this im going to attempt to use the same command only with >ubuntu >instead of xubuntu and see if that works but i like the scroll bar of the >xubuntu theme


ok I found that during the upgrade to intrepid my software sources were changed

I had to open software sources

system>administration>software sources and select the checkbox for source which was not the in harty

anyway thought i would edit this to let anyone else know that this is how it can be changed in case someone else hits this error

---

### Post by dmatthys on 2009-01-13
Success changing the file name of the .so that is created allows you to build a new .so after just changing the images so the first few steps only have to be completed once

note: after the name is changed you have to go into startup manager and remove the xubuntu-usplash and re-add using the new name

note: if you followed the instructions above for installation rather than using startup manager all you have to do is follow the instructions again using the new .so name

also i have figured out that the usplash-theme-xubuntu.c file if you double click that and select display it will show you the file contents via text editor and you can edit the position of the progress bar as you go through the file you will find a section that looks like the one below

    	.background             = 0,
  	.progressbar_background = 73,
  	.progressbar_foreground = 168,
	.text_background        = 0,
	.text_foreground        = 168,
	.text_success           = 128,
	.text_failure           = 227,

	/* Progress bar position and size in pixels */
  	.progressbar_x      = 212,
  	.progressbar_y      = 265,
  	.progressbar_width  = 216,
  	.progressbar_height = 8,

	/* Text box position and size in pixels */
  	.text_x      = 96,
  	.text_y      = 246,
  	.text_width  = 360,

where it says progress bar position in pixels you can adjust the pixel position number for x axis and y axis to determine where you want to place it using gimp image editor as this is what i did you open up each of the images one at a time and hover the mouse over the position you want the progress bar to start 

with the mouse in that position dont move it but look at the lower left corner of the image screen in gimp and youll see two numbers seperated by a comma 

     ex. 390.0 , 500.0

this is your x,y axis in that order 

     ex. x=390.0 , y=500.0

simply change that in the file above and save you have to rebuild the package after making that change

if you know which image your computer uses at boot usually your screen resolution that is set you will only have to find that section of the file and change that one however if you intend to share your usplash with others i would recomend adjusting all of them so this way it will show up no matter what screen resoltuion your friends or anyone else may use

note: each image will have a different pixel placement so you will have to adjust each one seperatly

sorry for the long post but i figured i cant be the only one asking these questions and so in light of helping others decided i would post my findings

---

### Post by nikolaibelkin on 2009-11-26
> **Bodsda said:**
> Cheers -- i know bout the $HOME and things now, i wrote this tut quite a while back when i was less knowledgable -- maybe i should rewrite it :)

Why can't you just use the good old ~ char?

---

### Post by jacobs444 on 2009-11-26
I have read the same crap 1 million times, what it doesn't list specifically is how to put your images at these resolutions into the compilations other than editing the already existing images?

---


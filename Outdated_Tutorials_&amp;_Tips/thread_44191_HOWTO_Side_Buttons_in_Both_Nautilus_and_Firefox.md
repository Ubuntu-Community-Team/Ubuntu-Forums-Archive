---
title: "HOWTO: Side Buttons in Both Nautilus and Firefox"
date: 2005-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by doans on 2005-06-24
I have been attempting to get my USB Microsoft Wireless IntelliMouse Explorer to completely work in Firefox and Nautilus for years now. I followed all of the guides on this and other forums and nothing was able to get the back and forward buttons to work in both Firefox and Nautilus.](*,) The side buttons would work in Firefox but not in Nautilus...until now! Here's how I did it (with the help of numerous forum posts which I have lost the links to now). Hopefully this will help someone else out. 
 
 1.  Install imwheel from Synaptic[indent]Make sure Universe is enabled to find this package.
[/indent]2. Edit /etc/X11/xorg.conf[indent]Change protocol to ExplorerPS/2, define number of buttons as 7, and reorder ZAxisMapping, by making your xorg.conf file like the one below.
  
Backup first:[indent] ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` 
  [/indent]sudo gedit /etc/X11/xorg.conf
   
Sample Mouse section from xorg.conf:
      ```
Section "InputDevice"
 	   Identifier	"Configured Mouse"
 	   Driver		"mouse"
 	   Option	   "CorePointer"
	 Option	 "Device" 			 "/dev/input/mice"
	 Option	 "Protocol"			 "ExplorerPS/2"
	 Option	 "Buttons" 			 "7"
 	 Option	   "ZAxisMapping"	 "6 7"
 	EndSection
```
 Your mouse section may be slightly different I am not sure.
   [/indent]3.  Create file .imwheelrc in /home/username[indent]gedit /home/username/.imwheelrc
[/indent][indent]Paste in this code:
[/indent][indent] ```

".*"
None, Up, Alt_L|Left
 None, Down, Alt_L|Right
  
 "(null)"
 None, Up, Alt_L|Left
 None, Down, Alt_L|Right
``` 
[/indent]4.  Backup and edit existing file /etc/X11/imwheel/startup.conf[indent] sudo cp /etc/X11/imwheel/startup.conf /etc/X11/imwheel/startup.conf.bak
sudo gedit /etc/X11/imwheel/startup.conf
  
Find this line:
[/indent][indent] IMWHEEL_START=0
  
 And replace with:
  
 IMWHEEL_START=1 
  
[/indent]5.  This is the final piece in the puzzle:[indent] sudo gedit /etc/X11/Xsession.d/63xmodmap 
  
 and paste in this code:
  
 ```
  
killall imwheel
 xmodmap -e "pointer = 1 2 3 6 7 4 5"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "67"
``` 
[/indent][indent]The Wiki site recommended creating file 57xmodmap that would startup before imwheel but this only ever worked for me in Firefox. Never worked for me in Nautilus. This has to start AFTER imwheel for some reason.
[/indent]6.  Save this file and then change the permissions so that it can be executed:[indent] ```
 sudo chmod 777 /etc/X11/Xsession.d/63xmodmap 
``` 
[/indent]7. Restart x server with Control+Alt+Backspace, re-login to X, and the mouse buttons and wheel should be working in Firefox and Nautilus!
 
 I love it when a plan comes together! \\:D/

---

### Post by programgeek on 2005-06-25
Dude, Wow.

Thank you for making a great tutorial...  I did run into some trouble:

etc/X11/imwheel/startup.conf < this doesn't seem to exist for me.  Neither does the directory..  Maybe I'm skipping something?  I don't know. Hehe.

Again, Thanks.  :)

---

### Post by BKonkle on 2005-06-25
This works great for me in Firefox, but it still doesn't work for me in Natulius.  *shrug*  I love the Firefox support though!  Thanks!

---

### Post by doans on 2005-06-26
[QUOTE=programgeek]
etc/X11/imwheel/startup.conf < this doesn't seem to exist for me. Neither does the directory.. Maybe I'm skipping something? I don't know. Hehe.

Again, Thanks.  :)[/QUOTE]

/etc/X11/imwheel/startup.conf is a installed file with imwheel.  Did you first install imwheel from synaptic?

 > This works great for me in Firefox, but it still doesn't work for me in Natulius. *shrug* I love the Firefox support though! Thanks! 

You created the .imwheelrc file in your user directory? Do you also have a Microsoft mouse? Getting it to work in Firefox and Nautilus was the desired effect.

---

### Post by bigcletus on 2005-06-28
I previously was able to get my mouse buttons to work in Firefox so I thought I would give this a try to make Nautilus work as well.  Well it kinda does.  The forward and backward buttons just move the selection in the nautilus window between the highlighted files.  Is this the intention of this?  I figured it would move up and down within the folders instead.

---

### Post by doans on 2005-06-28
[QUOTE=bigcletus]I previously was able to get my mouse buttons to work in Firefox so I thought I would give this a try to make Nautilus work as well.  Well it kinda does.  The forward and backward buttons just move the selection in the nautilus window between the highlighted files.  Is this the intention of this?  I figured it would move up and down within the folders instead.[/QUOTE]
 No, definetely not the intention of this.  With my mouse the side buttons go back and forward in Firefox and Nautilus.  This must not work on all mice.  I am not really sure why it doesn't work for everyone.

---

### Post by afonit on 2005-06-28
Thank you so much for this.  Worked like a charm.

Hopefully this will become automatic in the next release.

---

### Post by doans on 2005-06-28
[QUOTE=afonit]Thank you so much for this.  Worked like a charm.

Hopefully this will become automatic in the next release.[/QUOTE]
 Glad it worked for you. 

Yes, I would think this is something that should be configured on install and not have the user doing various tweaks after already being installed.

---

### Post by bassMonkey on 2005-06-28
Incredible, I never ever tought I would see this working... =)
Thank YOU!

---

### Post by benplaut on 2005-06-28
i think i'll pass...

i want to get my extra buttons working (Intellimouse Explorer 3.0), but i'm on a thnkpad.

5 buttons in the Ultranav, plus 5 on the USB mouse. aint gonna happen.


 ](*,)

---

### Post by thoffland on 2005-06-28
This is excellent!! Thank you for taking the time to post this... newbies like me need all the help we can get!

---

### Post by doans on 2005-06-29
[QUOTE=thoffland]This is excellent!! Thank you for taking the time to post this... newbies like me need all the help we can get![/QUOTE]
Glad that this helped you. I share your feelings for needing more help, I am a newbie also and have benefited from the help of numerous people on this forum. I posted this thread hoping that I could help one person get the satisfaction of having a fully functional mouse! Sounds simple, but it is a huge deal when you use the computer all day.

Ubuntu is great! I am not even sure the last time I started up WinXP.

---

### Post by bigcletus on 2005-06-29
[QUOTE=doans]No, definetely not the intention of this.  With my mouse the side buttons go back and forward in Firefox and Nautilus.  This must not work on all mice.  I am not really sure why it doesn't work for everyone.[/QUOTE]

hmmmm....I have the same mouse you have though :-?  I used another howto originally to setup my thumb buttons to work in firefox and then followed your howto afterwards to try and make nautilus work.  It works, but like I said the functions don't work as I want.  I wonder if there is a way to bind certain functions to the buttons?  Maybe I will give it a try and start over from the begining again.

---

### Post by doans on 2005-06-29
[QUOTE=bigcletus]hmmmm....I have the same mouse you have though :-?  I used another howto originally to setup my thumb buttons to work in firefox and then followed your howto afterwards to try and make nautilus work.  It works, but like I said the functions don't work as I want.  I wonder if there is a way to bind certain functions to the buttons?  Maybe I will give it a try and start over from the begining again.[/QUOTE]
 I would start over from the beginning. Maybe a step has been duplicated or omitted.

Let me know if you get this working and how you did it.  Don't give up.

---

### Post by thoffland on 2005-07-01
[QUOTE=doans]Glad that this helped you. I share your feelings for needing more help, I am a newbie also and have benefited from the help of numerous people on this forum. I posted this thread hoping that I could help one person get the satisfaction of having a fully functional mouse! Sounds simple, but it is a huge deal when you use the computer all day.

Ubuntu is great! I am not even sure the last time I started up WinXP.[/QUOTE]

Actually, I was still getting HAL errors when I booted, but... all I had to do was use the 57xmodmap instead and everything is hunky dory. 

I've only been on Ubuntu for about a week, but I'm learning a ton! Now that I've got it so it doesn't fail to load in some way or another, I'm really getting into it! I still have to login to WinXP to work on websites, but otherwise I'm completely converted. 

I still can't believe all of this is FREE!!

---

### Post by Majlo on 2005-07-04
Thank you so much . .
Work perfect for me . .
:-)

---

### Post by orac7000 on 2005-07-20
Wow, Excellent work, thanks heaps for this fix

---

### Post by wellery on 2005-07-20
Why don't they work from the start? Is this going to be fixed in Breezy?

---

### Post by doans on 2005-07-21
[QUOTE=orac7000]Wow, Excellent work, thanks heaps for this fix[/QUOTE]

Glad it worked for you. \\:D/

> Is this going to be fixed in Breezy?

It would be nice if this was accomplished out of the box with Breezy, but I have not heard if this is indeed fixed for the next release.

---

### Post by tioaboa on 2005-07-22
Works a treat - thanks man  :) 

Ian

---

### Post by horsefactory on 2005-07-23
Thanks, works with Epiphany too.

---

### Post by fabiuu on 2005-07-23
[QUOTE=programgeek]Dude, Wow.

Thank you for making a great tutorial...  I did run into some trouble:

etc/X11/imwheel/startup.conf < this doesn't seem to exist for me.  Neither does the directory..  Maybe I'm skipping something?  I don't know. Hehe.

Again, Thanks.  :)[/QUOTE]

I also didn't have this files/directories, but it works anyways.

Really nice man, worked fine for me!
 \\:D/

---

### Post by jadugarr on 2005-07-23
Great guide.  The thumb buttons not working in nautilus and ephiphany where really bugging me.  Thanks :).

---

### Post by dude2425 on 2005-07-24
Nice, I had firefox working with other guides already, but ever since the upgrade between warty and hoary it just refused to work for me in nautilus. I'm glad somebody could figure it out.

---

### Post by vdorta on 2005-07-28
This has to be a first for me in Linux: it worked perfectly the first time both in Firefox and in Nautilus, without any screen warnings.

Thanks!

---

### Post by doans on 2005-07-28
[QUOTE=vdorta]This has to be a first for me in Linux: it worked perfectly the first time both in Firefox and in Nautilus, without any screen warnings.

Thanks![/QUOTE]

Perfect! That is exactly what I thought when I finally got this working.:)

Most glad it worked for you.

---

### Post by Dr Bill on 2005-07-31
Thanks.  I have just switched from SimplyMepis to try Ubuntu out and had to relearn most of what I had done to get the Intellimouse Explorer working.  This mouse actually has 9 "Buttons" if you include L/R middle button clicks. In WinXP, I'm used to using the middle button down click to show the desktop and the L/R middle button clicks for horizontal scroll.  Any ideas?

One big difference between the two distros is that with Mepis I can log in as root.  This makes doing things like mouse button mapping much easier, e.g., never having to sudo, using a file browser to move, modify, files, etc.  In addition, with a MS Desktop Elite keyboard, I could configure various special keys with their manager.  I haven't found anything similar in Ubuntu.

Thanks again, Bill

---

### Post by the_purulent on 2005-08-02
Thank you thank you thank you!!
FINALLY GOT IT!
It only took 4 days of ploughing through this forum hehehe

---

### Post by mellowyllw6 on 2005-08-09
THANK YOU DUDE I LOVE YOU!

I've had this mouse for years now (MS Intellimouse 3) and couldn't think of losing my forward/back keys for browsing the intarwebs! Thanks man!

---

### Post by Synner on 2005-08-12
Same problem here as a few others, apparently.  The thumb buttons scroll, and the scroll wheel goes forward/back.  Any solutions yet?

---

### Post by qkslvr221 on 2005-08-14
[QUOTE=Synner]Same problem here as a few others, apparently.  The thumb buttons scroll, and the scroll wheel goes forward/back.  Any solutions yet?[/QUOTE]

HELP!! 

I did this fix, and I have the exact same problem.

Scroll wheel up goes BACK
Scroll wheel down goes FORWARD

Forward side button scrolls down
Back side button scrolls up

 ](*,)

---

### Post by dude2425 on 2005-08-14
alter you're xorg.conf, where it says ZAxisMapping "6 7", change it to "4 5"
(it might be from "4 5" to "6 7", I can't remember.)

There's no xmodmap in breezy anymore (I hope that gets fixed soon) so now my scroll wheel does nothing, side buttons scroll no matter what I do, my middle button's still middle, and the extra button on my MX310 goes back (I cant seem to find the forward though.) I changed it though so that I use evdev instead of ExplorerPS/2 though. I'm trying to get my extra button to do something.

I might extract xmodmap from an older xbase-clients later till the problem's fixed.

---

### Post by jackmacokc on 2005-10-18
another quick "thanks" for a great post. this worked like a charm for my wireless intellimouse explorer 2.0

---

### Post by ad noiseam on 2005-10-19
Does anybody know how to have the side buttons do something else than back / forward in Firefox? I had configured my mouse to copy / paste with them in Hoary, but can not get it to work in Breezy.

---

### Post by SuSUntu on 2005-11-27
I don't really have much to add here, except that Doans' instructions worked for me in getting Nautilus-mouse functionality working and that any little coding mistake can lead to unexpected results (but we all knew that, didn't we). 

As an example, I originally found instructions claiming to fix the FireFox / Nautilus mouse issues at the site linked below and applied them:

Matt's Blog
HOWTO: Microsoft Intellimouse in Linux
[http://dotnet.org.za/matt/articles/39097.aspx](http://dotnet.org.za/matt/articles/39097.aspx)
[http://dotnet.org.za/matt/articles/category/1137.aspx](http://dotnet.org.za/matt/articles/category/1137.aspx)


However, those instructions fixed FireFox mouse functionality, but left Nautilus somewhat lacking: the scroll wheel worked in Nautilus, but the side buttons scrolled the pane contents either left or right one small increment with each click (basically, the side buttons functioned as a slow alternative to just sliding the pane's horizontal scroll bar ... not exactly what I was looking for).

The wording and the instructions at "Matt's Blog" are virtually IDENTICAL to Doans' post #1 in this thread, so much so that either:

- Doans is "Matt"; or
- Doans should be upset with "Matt" for not giving Doans due credit and for screwing up the instructions. :)

Matt's error (typo, cut & paste gone awry, or whatever) is small and nearly unnoticeable, and I almost brushed Doans' post aside thinking I had tried the same instructions already and they didn't work. However, because Doans was insistent that it worked and others here claimed it worked, I slowed down to see what the difference was between Matt's instructions (which I had followed) and Doans', which appeared initially to be identical.

Here it is:

Matt's instructions (which don't fix Nautilus side-button functionality):

```

5. This is the final piece in the puzzle:
 sudo gedit /etc/X11/Xsession.d/63xmodmap

and paste in this code:

killall imwheel
xmodmap -e "pointer = 1 2 3 6 7 4 5"
BINARY=$(which imwheel)
$BINARY -k -p -b "6 7"

```


Doans' Instructions (which do work):
```

5. This is the final piece in the puzzle:

    sudo gedit /etc/X11/Xsession.d/63xmodmap

    and paste in this code:

    killall imwheel
    xmodmap -e "pointer = 1 2 3 6 7 4 5"
    BINARY=$(which imwheel)
    $BINARY -k -p -b "67"

```

Note the space between "6 7" in Matt's instructions and no space between "67" in Doans' instructions. Follow Doans' instructions and all should be good.

Anyway, if nothing else, maybe my comments will be cause to try again for some who think they have already done this without success based on other sources of similar instructions, or it will point out that any little variation in following the instructions will lead to unwanted results. Slowing down and trying again might be the order of the day.

Thanks Doans.
--------------
Mouse used: MS Wireless Intellimouse Explorer 2.0
OS: Ubuntu Breezy 5.10

---

### Post by dude2425 on 2005-11-27
Actually, a lot of people have their own prefered way of these kinds of things in Linux, some work, some not so much, and when combined with other peoples "way" they work even better. Most guides have their similarities, and not-so-similarities, but they all produce exactly the same, or similar results.

---

### Post by SuSUntu on 2005-11-27
[QUOTE=dude2425]Actually, a lot of people have their own prefered way of these kinds of things in Linux, some work, some not so much, and when combined with other peoples "way" they work even better. Most guides have their similarities, and not-so-similarities, but they all produce exactly the same, or similar results.[/QUOTE]

I understand there is more than one way to skin a Linux cat. But in this particular case, my main point was to bring to light a single-character difference in posted instructions that would either cause failure or success for the particular mouse that I referenced in my post (MS Wireless Intellimouse Explorer 2.0). I wasn't trying to suggest that this works for all systems and all mice, but was suggesting that it might be beneficial to take a careful second look if one had used other instructions or was perhaps a bit hasty in following Doans' instructions.

And, by the way if you checked the links I provided, Doans' and Matt's posts aren't just similar regarding the instructions, they are exactly the same in every way except for the aforementioned critical, single-character difference. To wit, look at the opening paragraph of both posts:

> I have been attempting to get my USB Microsoft Wireless IntelliMouse Explorer to completely work in Firefox and Nautilus for years now. I followed all of the guides on this and other forums and nothing was able to get the back and forward buttons to work in both Firefox and Nautilus. The side buttons would work in Firefox but not in Nautilus...until now! Here's how I did it (with the help of numerous forum posts which I have lost the links to now). Hopefully this will help someone else out.

Because even the personal experiences (not just the code) were EXACTLY the same, I almost blew off reading Doans' post because I was sure that I had already read it before from another source, and it had not worked. Had I blown it off and not looked more carefully, I still would be without a working mouse in Nautilus. :)

Otherwise, I have little care or interest in who the original author was, who copied from who or anything along those lines.

---

### Post by treris on 2005-11-28
I've been setting up my intellimouse all morning and it just doesn't seem to wanna work properly, 
right now my scroll wheel for some reason works as a back and forward button, while the back and forward buttons on the side of my mouse do absolutely nothing. 
I've also had it that my back and forward buttons were working but then my scroll wheel wasnt working, 

why is something that should be so simple, so hard to do?

---

### Post by thehamburgian on 2005-12-08
thanks for the tip. i did all of the above, but ubuntu still does not recognize my ms intellimouse explorer. am i missing something really basic?

device manager recognizes usb microsoft bluetooth device. batteries are in the mouse...

a newbie's newbie,

thehamburgian

---

### Post by thehamburgian on 2005-12-08
do i need to alter the /proc/bus/unput/devices file?

it seems that the other users didn't mention this at all. their mice worked after installation except for wheels and buttons. i get no functions, though device manager recognizes the bluetooth usb stick. 

thehamburgian

---

### Post by ErikL on 2006-01-04
Thanks for a great guide!

Just installed Ubuntu last night, so I'm completely new to this. Have browsed quite a few guides to change things to suit me.. but the "missing" buttons on my mouse were driving me crazy. This took care of it, and simple step-by-step instructions like these are perfect for us newbs ;)

---

### Post by mabster on 2006-01-08
I've got a similar problem to others here.  My mouse back/forward work fine.  However, my scroll wheel now acts like back/forward.

I tried changing my "ZAxisMapping" from "6 7" back to "4 5" but that didn't appear to fix it either.

Any ideas?

I vaguely remember running some app that would display the button values as you click them on the mouse but I can't remember what it was called...  Anyone?

---

### Post by mabster on 2006-01-08
Ok, never mind.  I put the 63xmodmap in /etc/X11 rather than /etc/X11/Xsession.d...  Oops.

And now it works great :D

---

### Post by algernon on 2006-01-14
Are there any downsides to setting it up this way? I guess what i'm getting at is if this is a reliable means for getting the mouse buttons working, why doesn't it work like this by default? 

Thanks for the guide.

---

### Post by Bretls on 2006-02-07
[FONT="Verdana"]I've been waiting a long for this. Works perfect. I Tried to set it up in the past, but i gave up. 
Thanks alot for making my life just a little easier.[/FONT]

---

### Post by fangorious on 2006-02-23
This doesn't seem to work for me in dapper with my Logitech M-BA47. Worked perfect in breezy. I've tried it using this HOWTO, the Wiki, using evdev, nothing works.  :( I think I'm close though. I've discovered that the xmodmap command I used in breezy doesn't work in dapper, it seems to expect 11 buttons in dapper. And I can get the scroll wheel to do forward/back, in either direction I want. But I can't get the thumb button to go back and keep the wheel scrolling the document.

---

### Post by fangorious on 2006-02-23
well, through sheer blind luck I have the thumb button working, but now the scroll wheel doesn't do anything.

xmodmap -e "pointer = 1 2 3 x x 8 9 x x x"

I haven't figured out how to arrange the x's to get the scroll wheel working. I'll keep trying.

---

### Post by palomar on 2006-02-24
[QUOTE=fangorious]well, through sheer blind luck I have the thumb button working, but now the scroll wheel doesn't do anything.

xmodmap -e "pointer = 1 2 3 x x 8 9 x x x"

I haven't figured out how to arrange the x's to get the scroll wheel working. I'll keep trying.[/QUOTE]
Have you already found a sollution? I do have the same problem in Dapper :(

**UPDATE**
I think i've found it. I have editted the file to:

xmodmap -e "pointer = 1 2 3 10 11 4 5 6 7 8 9"

note: i just have a 7 button mouse, but xmodmap wants 11 buttons, so it gets 11 buttons ;)

---

### Post by jswan on 2006-05-01
To get mine to work I had to use the 
```
xmodmap -e "pointer = 1 2 3 10 11 4 5 6 7 8 9"
```
as mentioned above and I also had to take out the Up and Down from .imwheelrc so it looks like this 
```
".*"
None, Alt_L|Left
 None, Alt_L|Right

 "(null)"
 None, Alt_L|Left
 None, Alt_L|Right
```

---

### Post by nomail on 2006-05-29
Guys, I've been trying to solve this one for few months now but had no luck...till now. I'm using IntelliMouse Explorer 3.0A USB mouse...well I was able to use sidebuttons when I changed /etc/X11/Xsession.d/63xmodmap


 ```
killall imwheel
 xmodmap -e "pointer = 1 2 3 6 7 4 5"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "67"
```


to use buttons 8 and 9 instead 6 and 7, so it would look like this:

```
killall imwheel
 xmodmap -e "pointer = 1 2 3 6 7 4 5"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "89"
```

Man, I'm happy to use these buttons again

Best regards,
nomail

P.S. sorry for my rubbish english

edit: somehow imwheel doesn't start with X server for me.....i have to type in terminal ```
imwheel -p -k -b "89"
```

---

### Post by chopsuey on 2006-05-31
WOOHOO.. Its finally working with my Intellimouse Explorer 3.0

But i had to change a few things...

In the xorg.conf:
Option      "ButtonMapping"      "1 2 3 6 7 4 5"
Option	   "ZAxisMapping"	 "4 5"

and in the 63xmodmap:
xmodmap -e "pointer = 1 2 3 4 5 6 7"
BINARY=$(which imwheel)
$BINARY -k -p -b "67"

yippie!

---

### Post by Schalken on 2006-06-19
Okay I followed the instructions and restarted my computer, and the side buttons don't do anything. :( However, now my scrollwheel makes Firefox and Nautilis go Back and Forward like the side buttons are supposed to!!! :o

Is there maybe a way to swap the keys for the scroll wheel with the keys of the side buttons, leaving my scroll wheel doing it's usual thing?

**Edit: I got it working!**

Here's how for the IntelliMouse Optical (USB/PS2 compatible, mine's connected through PS2) or other-mouse-with-similar-configuration:

You follow the normal instructions, BUT:

Instead of setting the "ZAxisMapping" to "6 7" in your xorg.conf, keep it as "4 5", that way your scroll wheel will still work. ;)

Instead of being mapped to buttons 4 and 5 or 6 and 7 like you would think, the IntelliMouse Optical has it's side buttons at 8 and 9. (I found this out by typing 'xev' in the terminal and pressing the side buttons in the test window.) So, in your "63xmodmap" file, change the line

xmodmap -e "pointer = 1 2 3 **6 7 4 5**"

to

xmodmap -e "pointer = 1 2 3 **4 5 8 9**"

and the line

$BINARY -k -p -b **"67"**

to

$BINARY -k -p -b **"89"**

Hopefully your IntelliMouse Optical or other-mouse-with-similar-configuration will work like mine!

Yeppers.

---

### Post by s3ppel on 2006-07-06
For my Razer Diamondback I found the easiest solution to be changing just the /etc/X11/xorg.conf file. No Xmodmap or IMWeel needed for me.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
        Option          "Resolution"            "1600"
	Option		"ZAxisMapping"		"4 5"
	Option		"ButtonMapping"		"1 2 3 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by globexispower on 2006-08-04
I think I have the intellimouse optical it has .  To get this to work I had to change one thing from the steps at the beginning of this post

here is the mouse section in file /etc/X11/xorg.conf

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "Buttons" "7"
        Option      "ZAxisMapping" "4 5"        #this was changed
        Option      "ButtonMapping" "1 2 3 6 7" #this line was added
EndSection

Now my back/foward buttons work in both nautilus and firefox

---

### Post by Angry penguin on 2006-09-04
This works! Just a couple minor modifications:
 
63xmodmap
```

killall imwheel
   xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "89"
```
And the xorg.conf
```
Section "InputDevice"
 	   Identifier	"Configured Mouse"
 	   Driver		"mouse"
 	   Option	   "CorePointer"
	 Option	 "Device" 			 "/dev/input/mice"
	 Option	 "Protocol"			 "ExplorerPS/2"
	 Option	 "Buttons" 			 "7"
 	 Option	   "ZAxisMapping"	 "4 5"
 	EndSection

```

thanks.\\:D/

---

### Post by ilovenicotine on 2006-12-08
for those with the buttons acting like they are simply the left right keys, try uncommenting the last line in the /etc/X11/imwheel/startup.conf file...

---

### Post by johneedoe on 2006-12-11
This is how I got my Microsoft Wireless Laser Mouse 6000 to work.  Well, everything except the side scroll buttons.  I don't use them anyway so not a problem.  Thanks for the help everybody!

xorg.conf

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option          "CorePointer"
	Option          "Device" "/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons"		"7"
	Option          "ZAxisMapping" "6 7"
	Option		"ButtonMapping"		"1 2 3 4 5"
EndSection

63xmodmap

killall imwheel
xmodmap -e "pointer = 1 2 3 6 7 4 5"
BINARY=$(which imwheel)
$BINARY -k -p -b "6 7"

---

### Post by CaptSaltyJack on 2007-02-24
This doesn't work in Ubuntu 6.10 on my Razer Copperhead.  The side buttons do nothing, and plus now my mouse is on crack and moves at the speed of light.

---

### Post by fredespi on 2007-03-08
For Ubuntu Edgy 6.10 with a Logitech Mx310 Optical mouse it works with the following changes:

In xorg.conf:

```

Option     "Buttons"          "9"
Option	   "ZAxisMapping"     "4 5"

```

In 63xmodmap:

```
xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"
```

and

```
 $BINARY -k -p -b "6 7"
```

---

### Post by ruimoura on 2007-03-08
> **fredespi said:**
> For Ubuntu Edgy 6.10 with a Logitech Mx310 Optical mouse it works with the following changes:

In xorg.conf:

```

Option     "Buttons"          "9"
Option	   "ZAxisMapping"     "4 5"

```

In 63xmodmap:

```
xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"
```

and

```
 $BINARY -k -p -b "6 7"
```

Dude, with that conf, on my mx310,  left and right side buttons act like mouse wheel up/down, to scroll pages. I'm on feisty, but i guess the conf would be the same ... Put here your entire conf (the xorg part), please ...

---

### Post by alliantdevil on 2007-03-15
> **globexispower said:**
> I think I have the intellimouse optical it has .  To get this to work I had to change one thing from the steps at the beginning of this post

here is the mouse section in file /etc/X11/xorg.conf

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "Buttons" "7"
        Option      "ZAxisMapping" "4 5"        #this was changed
        Option      "ButtonMapping" "1 2 3 6 7" #this line was added
EndSection

Now my back/foward buttons work in both nautilus and firefox

Following the OP guide didnt work but making this one slight change made my intellimouse 3.0 work:guitar:

---

### Post by IronWolve on 2007-03-19
Using imwheel -c, to see my default mappings, I was able see my intellimouse buttons where mapped to left/right not up/down. Up down is mapped to my scroll wheel.

Creating a .imwheelrc just for firefox and nautilus works perfect.

```

"^Firefox-bin$"
None,Left,Alt_L|Left
None,Right,Alt_L|Right

"^nautilus$"
None,Left,Alt_L|Left
None,Right,Alt_L|Right

```

---

### Post by hakankaynar on 2007-05-09
> **ruimoura said:**
> Dude, with that conf, on my mx310,  left and right side buttons act like mouse wheel up/down, to scroll pages. I'm on feisty, but i guess the conf would be the same ... Put here your entire conf (the xorg part), please ...

May be this helps:

xorg.conf:

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "false"
        Option      "Buttons" "7"
        Option      "ButtonMapping" "1 2 3 6 7"
EndSection

with the startup script :

xmodmap -e "pointer = 1 2 3 4 5" &
exec imwheel -k -b "6 7" &
exec $REALSTARTUP

---

### Post by ruimoura on 2007-05-27
> **hakankaynar said:**
> May be this helps:

xorg.conf:

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "false"
        Option      "Buttons" "7"
        Option      "ButtonMapping" "1 2 3 6 7"
EndSection

with the startup script :

xmodmap -e "pointer = 1 2 3 4 5" &
exec imwheel -k -b "6 7" &
exec $REALSTARTUP

That worked pretty fine, thank you so much :)

---

### Post by MasDom on 2007-08-04
Hi,

I tried your tutorial and it worked in some wy. I was going back and forth in Firefox but with my mousewheel. What did I do wron???

Cheers

Masdom

---

### Post by eOgas on 2008-05-11
You are my hero!  Worked like a charm in Hardy with my Logitech v400.  All the buttons work without any sort of configuring.  Thanks.

---

### Post by shamusl on 2008-07-10
I ended up having to delete imwheel, and the script because it was preventing ubuntu from starting properly, I don't know what I did wrong, but I guess I would try later on at some point.

---

### Post by traffas on 2008-10-08
Does anyone have a current solution for Hardy or Intrepid? The xorg.conf mod mentioned here no longer seems to work.

---

### Post by Lexicon101 on 2008-10-11
I'm disappointed.. I guess the feature freeze means no automatic support for this kind of thing, eh?

---

### Post by HamHamT on 2009-01-03
so i got the original thread title to work following the OP's instructions but now my scroll mouse up+down doesnt do anything and is there a way to enable the scroll wheel click to pan the browser?

thanks!

---


---
title: "HOWTO easy video conversion/encode"
date: 2006-12-03
forum: Outdated Tutorials &amp; Tips
---

### Post by binks on 2006-12-03
This is a **HOWTO convert video files to DVD **SVCD or VCD
we will use tovid and a GUI wizard i wrote called **tovidwiz** to convert an avi to a DVD folder that can be burnt using k3b
**Added the ability to select subtitles**
if you choose to add subs be aware that the subs are burt into the movie and are not selectable.

A big thanks to the **tovid team** and to **eric1397** from whom i have stolen all the good ideas and most of erics text and his script #you get the idea

1. Before you do anything, you will want to have the **universe/multiverse repositories enabled**, so go [here]("http://www.psychocats.net/ubuntu/sources.php").

---
BIG EDIT the wiz now can run using the 0.30 official release so install tovid using the new script as provided by ubuntuman001 cheers dude

2. **Download the scrpt installtovid.sh** and run by 

```
chmod +x installtovid.sh && ./installtovid.sh
```
**NOTE:** This script does the following: It downloads and installs all the dependencies for tovid, downloads and installs tovid, downloads the tovid icon, the mkiso script, and the tovid menu entry, and places all of these in their corresponding folders.

3.Test tovid
now that should be tovid installed  you can test it by typing  tovid  into a shell and you should get something like this


binks@binks-desktop:~$ tovid
--------------------------------
tovid
DVD and (S)VCD video conversion script
**Version svn-r1406**
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
tovid command-line used:

=========================================================

Using config file /home/binks/.tovid/tovid.config, containing the following options:
-noask
binks@binks-desktop:~$


4. **Download the 2nd file tovidwiz** at the bottom to your home dir and then

```
sudo chmod 0700 tovidwiz
```

5. Open up a terminal and type **./tovidwiz**
the todisc wizard should open up

box1. in the first box we choose the video we need to encode

box2. we get 5 options since we want a dvd we choose the radio button next to the dvd option

box3. we choose our region coding ie usa will be ntsc europe will be pal 

box4. we set the screen aspect ratio we require, this is up to you and your tv needs

box5. Quality settings will affect the output size of the dvd we make you will be ok with 8 most of the time but its there for you if you need some tweaking

box6. **new** choose yes if you want to add a subtitle file see man tovid for valid sub  files
if yes then se the file selection to navigate to the **sub file to burn into the film**


box7. This is where we set the text to be displayed on the menu screen of the dvd     

box8. In the project name box we name our project and our dvd structure will be created in a folder in your home dir with what ever text you choose here

EDIT 06/01/07 renamed file inside compressed installtovid{svn} as i had it wrong sorry
enjoy and please give feedback good or bad

---

### Post by user1397 on 2006-12-05
binks, tried it, and it worked great for me.  apparently, you're using todisc to do all the work, correct?

just to let you know, everything went well for me.

one suggestion: could you rename your tovid svn installation script to **installtovidsvn.sh** or something, so that people don't get it confused with my tovid installation script?

---

### Post by binks on 2006-12-06
well yes i run the todisc command but its the tovid suite that controlls it all 
and i updated the name of the install script for you :);)

binks

---

### Post by user1397 on 2006-12-06
> **binks said:**
> well yes i run the todisc command but its the tovis suite that controlls it all 
and i updated the name of the install script for you :);)

binksalrite man, thanks.
and btw, i think your gui might replace the current tovidgui maybe, because that isn't being developed like at all (or at least very little), and yours is so easy and small.

we should talk to wapcaplet about it.

---

### Post by buildid on 2006-12-06
possible to implement adding subs into tovidwiz ?

---

### Post by binks on 2006-12-07
yes i can implement subs but do i want to well hmmm 
it would complicate the script as it stands atm (i would need to learn some more zenity bash stuff) because if people didnt have a sub file it would crash the tovid command as it stands.
i will loook into it for you but it wont be before the weekend
but i will :)

---

### Post by buildid on 2006-12-07
thank you

---

### Post by binks on 2006-12-11
nearly done it m8 just getting a small error when run should post tuesday evening :) i have more time then

---

### Post by binks on 2006-12-13
i have added subtitle support can someone test this for me and report your findings cheers 
binks

---

### Post by buildid on 2006-12-14
i will test this in a few minutes

ill get this error wit tovid :

/usr/local/bin/todisc: line 3573:  9818 Segmentation fault      (core dumped) dvdauthor -x "$DVDAUTHOR_XML"

---

### Post by binks on 2006-12-16
try to update your svn tovid with these cmd's

```
$ cd ~/tovid
$ svn update
$ ./bootstrap
```
let me no if it still happens 
:)

---

### Post by lime4x4 on 2006-12-22
how can i change the chapter points? I did a 2 hour movie the other day and only got 6 chapters
would like to have a few more

---

### Post by binks on 2006-12-23
ok will add a box for selection of number of chapters 
i may tyr to get it to create a sub menu with the chapters listed if i can get it to work


ps i am now starting a  new gui for tovid written in python if anyone has any ideas for it please say so   ta mateys
binks ;);)

---

### Post by DagMan on 2006-12-23
With the current interface, the cancel button does nothing.  The script continues on to the next selection instead of exiting or prompting for an exit.

As for ideas, I find the aspect of DeVeDe that allows for a bitrate selection and a progress bar for how much room a file estimates (although it is not accurate, it's still usefull) to be, handy and better than selecting a quality setting in with radio buttons.

A back button would be good too.

I haven't tested it yet.  I tried another GUI with this program before and was impressed but it ended up not working under the hood because it was not encoding the entire length of a file.  I'll give this a try again though.  The previous GUI had features that were really impressive, specifically automating the whole process of setting up multiple titles and making a menu.  If these featured aren't accessable in your current GUI, I recommend adding it.


EDIT:  It installed everything into /usr/local/bin which isn't desireable for a lot of people.  I removed everything when I saw that.  I'll give it a go again and look at putting things in a better place if I get time.  It was a large number of files was the problem.

---

### Post by binks on 2006-12-23
if you install tovid from svn then you can use the full feature gui by running **tktodisc** , this wizard is meant as a simply intro to tovid to newbies and simple dvd creation 
i agree the srcipt is not finnished yet thats why i havent coded theexit or cancel buttons its christmas im spending time with the kids so sorry itll have to wait till early jan but i will do it
this is only meant to be a learning curve for me o get me into gui programming 
thanks for looking at the app and your comments 
:):) binks

---

### Post by lime4x4 on 2006-12-31
here is the error i'm getting after updating tovid thru svn

john@john-edgy:~$ ./tktodis
bash: ./tktodis: No such file or directory
john@john-edgy:~$ tktodis
bash: tktodis: command not found

---

### Post by binks on 2007-01-02
the command id **tktodisk** for the multi menu gui
or run **./tovidwiz** for the 1 input file quick dvd wizard

---

### Post by toGoq on 2007-01-04
Tried your script on ***Dapper***[COLOR=Black].  [/COLOR]Got the following errors:

./bootstrap: line 32: aclocal: command not found

Do you think it is a Dapper-problem? Has anybody else tried this on Dapper?

---

### Post by binks on 2007-01-06
yes what is the newest version of automake available in dapper as the script tries to install 1.9 please check what you have installed and try to update to the latest version available 
binks

---

### Post by Jongi on 2007-01-11
Hmmm. Will give this a go.

---

### Post by xopher on 2007-01-11
Wow, this is exactly what I've been looking for. Thanks a lot! Will help me tremendously.

---

### Post by adjman on 2007-01-25
Excellent work - it's fantastic and SO EASY! :)

---

### Post by ejstacey on 2007-02-17
Hi!

Thanks for the scripts/howto.  A few things have changed since this was written, though:

[LIST]
[*]0.30 seems to be out.  An Ubuntu deb for it exists here: [http://tovid.sourceforge.net/download/ubuntu/tovid_0.30-1_i386.deb](http://tovid.sourceforge.net/download/ubuntu/tovid_0.30-1_i386.deb)
[*]The SVN version now requires automake1.10 to compile.  Edgy doesn't include this in it's normal repos, so the svn method will only work for Feisty or above.
[*]The mkiso script is now missing.  wgetting gives a 404.  The chmod and mv commands then  fail.
[*]After selecting the movie file, I have an "OK" box pop up with no text and just a exclamation mark icon in it.
[*]The menu title and project name can't be multiple words (can't have spaces).  I think this is just a case of putting "" around the argument so it shows up as one to the commands (the terminal window gives a "Too many arguments" error).  The process still seems to run.. I imagine it just uses the first word.
[/LIST]


This script is great otherwise.  I'm running it now so I'm not sure how badly the missing mkiso will screw me up, but I guess I'll see ;)  If I end up with just the proper VOB files, that'll be fine.  Thanks for all your work!

---

### Post by binks on 2007-02-18
will look at issues arrising from the release of v 0.30 and fix them :)

as for the first box with ok on its just a info screen telling you what fps the input file is for some reason idvid cannot determin the fps ??  ill ask in #tovid about that  

cheers binks ps i am tring to create the wizard now in python using PyQt4 but tutorials are thin for PyQt4 so its taking me a while

---

### Post by Omnios on 2007-02-18
Hi I tryed the script but this part is 404 
```
http://tovid.sourceforge.net/download/ubuntu/install_script/mkiso
```

 Ill try again later

---

### Post by binks on 2007-02-18
install script now installs latest version 0.30 so you will also need to install zenity manually

```
sudo apt-get install zenity
```

---

### Post by mrjohnston on 2007-04-01
Can I change the directory it uses to convert from /tmp?  

I have a partition specifically for video with lots of room, but little room on my root partition.  I don't see any options to change the directory and was wondering if there was a way I could modify the script to override the directory used.

Thanks

---

### Post by lime4x4 on 2007-04-08
how can i make this into a script? I've tried the following file in my script folder so that all i have to do is right click the video and select scripts then tovidwiz but nothing happens

#!/bin/bash
./tovidwiz

---

### Post by user1397 on 2007-04-18
Uh, sorry for not mentioning anything binks, but I have changed things around.  I guess you should update your script or just point people to the tovid install guide page.

I uploaded the .30 ubuntu deb to the tovid site, and I uploaded the whole /install_script directory and all its contents.

I have since removed the entire /install_script folder, because I basically decided the install script was kinda dumb/unneeded/unnecessary.

Now I just point people to the main tovid install page, which is clear, easy, and fast enough.


So I don't know what you want to do binks, just get rid of the install script, modify it, or I don't know, whatever you want to do.

---

### Post by binks on 2007-05-06
ok ok so i let the pages get old i will lokk into re writing the whole lot on tues evening as i will have some time 
ive been offfline as i have a whole lot of crap to deal with at home but things settling down now so i will have a look 
have fun binks

---

### Post by jbayone on 2007-05-16
I just burned a movie with this script, but the sound is out of sync.  Any ideas?

---

### Post by gkjohn on 2007-08-20
Hi,

I was wondering how I can use the Tovid GUI to put multiple movies on one disc?

I followed the installation procedure in the first message of this thread...

---

### Post by craigsn on 2007-08-24
Hi Binks,
I see this entry, but where do I download the script from. I cannot find it on ubunut or on [http://tovid.wikia.com](http://tovid.wikia.com) anyplace. 

Also, I'm running Feisty AMD64, does that change anything?


> 

2. **Download the scrpt installtovid.sh** and run by 



Thanks
Craig

---

### Post by iamah on 2007-09-13
that works but the subtitles are huge,  taking half of my screen... is there a way to specify subtitle size? meanwhile I have to use ConvertXToDVD in damn windows

---

### Post by c-m on 2007-11-25
this no longer works

when using the command chmod +x installtovid.sh && ./installtovid.sh i get the following error:


> 
-22:56:14--  [http://tovid.sourceforge.net/download/ubuntu/tovid_0.30-1_i386.deb](http://tovid.sourceforge.net/download/ubuntu/tovid_0.30-1_i386.deb)
           => `tovid_0.30-1_i386.deb'
Resolving tovid.sourceforge.net... 66.35.250.209
Connecting to tovid.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:56:15 ERROR 404: Not Found.



---

### Post by Bodifar on 2009-03-08
This tutorial still works great, thanks! 

I was looking for a tool to burn .avi's with subtitles to DVD in Ubuntu ... I'm encoding my first test-vid as I'm writing this. I'll give you guys an update as soon as I'm ready with it. Fingers crossed! 

Thusfar: 

[1] Installation went great. 
[2] GUI was a bit strange (you'd expect 1 window, instead of several popups :-) but if it works, it works!)

---

### Post by Bodifar on 2009-03-12
> **Bodifar said:**
> This tutorial still works great, thanks! 

I was looking for a tool to burn .avi's with subtitles to DVD in Ubuntu ... I'm encoding my first test-vid as I'm writing this. I'll give you guys an update as soon as I'm ready with it. Fingers crossed! 

Thusfar: 

[1] Installation went great. 
[2] GUI was a bit strange (you'd expect 1 window, instead of several popups :-) but if it works, it works!)

At the very end, encoding failed on the file. I couldn't quite put my finger on it, so I just reverted to ConvertXtoDVD. Works very well under Wine, and does everything I need it to do ...

---


---
title: "Ubuntu Wallpaper Stacks Creator"
date: 2009-11-07
forum: Programming Talk
---

### Post by rubenverweij on 2009-11-07
Hi all,

I'm trying to create an editor that allows you to create an xml file needed by Preferences->Appearance to create a wallpaper stack. You can see the source code here: [https://launchpad.net/wallpaper-stacks](https://launchpad.net/wallpaper-stacks).
I'm planning to make a ppa soon, but first I would like to have some feedback, positive or negative.
Please let me know what you think!

Cheers,

Ruben

---

### Post by ackey on 2009-11-07
It is great that someone has done this!

I tried to run it and saving didn't work.  There were just "open" and "cancel" buttons, without the ability to select location or give a filename. It would be helpful if the default location it looked for an image was the location the last image came from, rather than the home directory.

I've found some discussion (albeit, old) [here]("http://www.mail-archive.com/ubuntu-art@lists.ubuntu.com/msg05440.html"), where some timing aspects are discussed.

---

### Post by rubenverweij on 2009-11-07
Woops, made a mistake with the saving indeed. It works if you just type in some name and click the open button. I will fix it though. :P
Thanks for that link, I will look into that!

---

### Post by rubenverweij on 2009-11-07
Okay, I fixed the dialog.
If you are using my ppa you should get an update soon. ;)

---

### Post by avdzm on 2009-11-07
Hey, this is great!!!

My suggestion would be to keep it simple.
The app would have an "Adds folder", "Adds File(s)" it should show all the pictures in a list.

There can be two ways on how it should rotate:

Slide show
The user may be able to rearrange the list of pictures.
The user can select the time interval of when the pictures should switch every 5 mins.

Hour (time)
For example in the morning to show picture1, at noon (12:00) to show picture2, at 18:00 to show pic3, at 21:00 to show pic4, etc.

Those are my ideas.
Hope it helps.

---

### Post by Shpongle on 2009-11-07
> **avdzm said:**
> hey, this is great!!!

My suggestion would be to keep it simple.
The app would have an "adds folder", "adds file(s)" it should show all the pictures in a list.

There can be two ways on how it should rotate:

Slide show
the user may be able to rearrange the list of pictures.
The user can select the time interval of when the pictures should switch every 5 mins.

Hour (time)
for example in the morning to show picture1, at noon (12:00) to show picture2, at 18:00 to show pic3, at 21:00 to show pic4, etc.

Those are my ideas.
Hope it helps.

+1

---

### Post by avdzm on 2009-11-07
oh, i just found ur ppa,
will try it out and let you know.

---

### Post by rubenverweij on 2009-11-07
Thanks for your excellent advice avdzm!
This will need some time though, I will post back again if I've got some results.
Though I don't know if this function was implemented under Appearances in 7.10?

---

### Post by avdzm on 2009-11-07
hey rubenverweij,
sorry my signature is out of date.
I am using karmic n loving it.

out of curiosity does ubuntu one work for you?

---

### Post by wolterh on 2009-11-07
Ruben, how about if I compile the 64-bit package? I couldn't find the amd64 binary in your ppa.

---

### Post by wolterh on 2009-11-07
The Makefile is giving me problems.. I installed libgtkmm-2.4 and libxml++2.6 but now I get some boost file not found error (and boost isn't even included in the pkg-config include.

---

### Post by rubenverweij on 2009-11-08
@woli: you don't have to bother about compiling. If you are using karmic, just add ppa:ruben-verweij/wallpaper-stacks to your system's Software Sources. Then run the following command to get the key for signing the packages: 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FA2725F5
```
If you are using anything less up to date than karmic, add this line to your Software Sources:
```
deb http://ppa.launchpad.net/ruben-verweij/wallpaper-stacks/ubuntu lucid main
``` and obtain the key in the same suit. Then you can just:
```
sudo apt-get install wallpaper-stacks
``` or search in Synaptic for "wallpaper-stacks".
Thanks for your interest, though!

@avdzm: Oh, ok, I just wondered. ;) Yes, Ubuntu One is working quite well for me, actually.

---

### Post by wolterh on 2009-11-08
Don't worry, I know what I am talking about. Did you read the post prior to the one you just replied to?

I had already added your key and ppa source, but this is what apt-get tells me when I try to update
```
$ sudo apt-get update
(...)
W: Failed to fetch http://ppa.launchpad.net/ruben-verweij/wallpaper-stacks/ubuntu/dists/karmic/main/binary-amd64/Packages.gz
```
Thus, I infered you had no amd64 package compiled and tried to compile one myself, but failed, as I explained in post #11.

---

### Post by rubenverweij on 2009-11-08
Strange... it says the amd64 package is successfully compiled too... Could you please try another time? :D
If you still want to compile the package, you have to install the libboost1.38-dev package (as listed in the control file of the deb, though I don't know if you can download that anywhere from my ppa ;)).
Could you please let me know if it worked?

BTW: I'm working hard on the changes, they are almost implemented. Thanks all for your interest! ):P

---

### Post by wolterh on 2009-11-08
Oh my.. sorry but I will not download a 330MB package hahaha

---

### Post by rubenverweij on 2009-11-08
No, you shouldn't because the .deb file is only 33.5 kb...
You can find it here: [https://launchpad.net/~ruben-verweij/+archive/wallpaper-stacks/+files/wallpaper-stacks_0.1-2_amd64.deb](https://launchpad.net/~ruben-verweij/+archive/wallpaper-stacks/+files/wallpaper-stacks_0.1-2_amd64.deb).
Though I find it strange that you can't download it via the ppa...

---

### Post by ackey on 2009-11-08
I hadn't gotten the PPA to work when you first posted, so I just got the *.deb.

I tried adding it today and got an error message,

```
Failed to fetch http://ppa.launchpad.net/ruben-verweij/wallpaper-stacks/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

I'm running 32bit karmic.

---

### Post by rubenverweij on 2009-11-08
Whoops, I already know what is causing the problem, it's a stupid mistake of mine.
I will fix it when the new version comes out (soon).

---

### Post by rubenverweij on 2009-11-08
It should be fixed now.
I also have a new version available, so could you please provide me with some feedback?
Thanks in advance! ;)

EDIT: I can't seem to get the PPA sorted out right now, for the moment just add: ```
deb http://ppa.launchpad.net/ruben-verweij/wallpaper-stacks/ubuntu lucid main
``` to your Software Sources until I found out how to set it up for karmic, too.

---

### Post by avdzm on 2009-11-09
Hey ruben,

I just got your new version,
very nice, it's a lot easier to create a stack now.
thanks for your work.

I just wanted to ask, are we sure the duration is in seconds?
I created a xml, with 60 secs n 5 secs transition, but the wallpaper hasn't changed.

I know it reconizes it as a stack because i added the xml itself. 
In the background settings, it shows my pics like cosmos.

Maybe it's in minutes? i'll let u know what happens in an hour.
thanks

looks really great now

---

### Post by avdzm on 2009-11-09
the background hasn't changed.
i will try editing the xml and let you know.

---

### Post by avdzm on 2009-11-09
Hey Ruben,

I got it switching pics,
what i changed in the xml was the duration time,
from 60 to 61.0.

Anything less than or equal to 60 will not rotate the backgrounds.
And for some reason it needs ".0" at the end of the duration.

Also i noticed when you add a folder, it will also add none pictures in your list I took a screen-shot.

---

### Post by avdzm on 2009-11-09
I also noticed that the xml is missing the last transition, it needs to go from the last pic to the first pic.

now everything is working fine for me.

---

### Post by rubenverweij on 2009-11-09
Thanks for the comments!
I will build in a check for that higher than 60.0 duration then.
I was already aware of the issue that non-images get added too, right now I can't think of anything else to do than filter by extension...
I will process your comments and post back again! ;)

---

### Post by rubenverweij on 2009-11-09
I tested it a bit for myself, but the transitions are working for me if the time is set to 61 or higher, regardless of decimal places etc.
I will edit the program to display the last to first transition and file filter though.

---

### Post by avdzm on 2009-11-10
hey ruben,

tell me after a few cycles, does ur background stop changing?
With me they seem to stop in the middle of the transition.

I have provided a screenshot.

Maybe that is why cosmos changes every 30 mins.

---

### Post by ackey on 2009-11-10
I see the same behaviour with "stuck" transitions.  This is with a hand-written XML file, so it is independent from the wallpaper stacks creator.

There must be nuances to the timing.  I tried making transitions really long and it still looked like one background just "flashed" to another.  I changed the transition to be of type "overlay" and nothing seems to have changed.  I don't think I saw the overlapping images before I had overlay specified though.  

My best (uneducated) guess is that the total time needs to be a divisor of 24 hours.  If the total amount is 13 minutes, for instance, perhaps there is a difference between how it determines the initial parameters and how the changes occur.  I just changed the timings in my file to see if it fixes the problem.

---

### Post by avdzm on 2009-11-11
Hey guys,

Well I have changed the rotation to every 15 mins,
and for the last 17 hours everything has worked fine.

:D

cheers

---

### Post by rubenverweij on 2009-11-11
Has the stuck transition something to do with the last to first image transition that is missing in your file? I have modified the program to add it as well and it seems to work fine now. I can't speak of a real transition though, it sort of jumps to the next image.

---

### Post by avdzm on 2009-11-11
It didn't get stuck at the last transition, 
it was getting at random transitions. 

Maybe per minute was too much load for the background.
now that I have it every 15 mins, I no longer have a problem,

Everything works fine. 
How about u guys?

---

### Post by ackey on 2009-11-11
Switching from 5 to 20 minutes resulted in no stuck transitions today.  So it sounds like there is a minimum display time issue - 1 and 5 minutes don't work, but 15 and 20 do.

---

### Post by avdzm on 2009-11-12
Hey Ruben,

I got 2 suggestions,
1. Rearrange the pictures in the list? Either with click n drag or buttons, move up, move down, move first and move last.
2. To have 2 text fields to set the overall durations. This will make it easier for the user instead of setting each picture, I have attached a image to show what i mean.

Great work so far...
thanks

---

### Post by airtonix on 2009-11-29
this really needs to be part of the appearance manager.

While I'm choosing the images for the background I've always been able to drag n drop images onto the background selector list and have it be included in the list of possible background wallpapers... same is true with a selection of many images.

Now what needs to happen is if you drag n drop a folder onto the background image selector list, then it should prompt you : 

"Make slideshow background? yes/no"

yes -> 
1. ask for title
2. silenty copy pictures to ~/Pictures/Backgrounds/<title>/
3. create ~/Pictures/Backgrounds/<title>/background.xml

no ->
add images to list as standard backgrounds.

---

### Post by airtonix on 2009-11-29
sigh... double post

---

### Post by rubenverweij on 2009-11-30
@avdzm: Thanks again for your most excellent suggestions. I really appreciate your advice! ;)
I implemented the changes in trunk, I will push it to my PPA ASAP.

---

### Post by ozhoo on 2009-12-03
Very cool

Here is a bash script that generates the file [http://ubuntuforums.org/showthread.php?t=1344787&highlight=backgrounds+xml](http://ubuntuforums.org/showthread.php?t=1344787&highlight=backgrounds+xml)

Takes "dir1 dir2 dir3" as arguments, and scans each recursively for jpg's

---

### Post by batubolu on 2009-12-19
wow, glad found this.

---

### Post by ogromano on 2009-12-29
Hi...

Just wanted to add a couple of requests to this great solution...

1. Drag and drop would make this an extremely useful program. I'm not so much a fan of adding whole folders due to the fact that neither I nor the owners of the pix I have are professional photographers and therefore not all shots are very good nor do I want to see a series of attempts at getting the perfect shot in full 1440x900!! :shock:

2. A small help file with a few simple steps to follow just for the sake of having it and not having people wondering what to do... (yes I know it is dead simple, but there will always be someone that won't get it, believe me!! ](*,)) Or maybe even an about window with the links to your launchpad site and/or to this thread.

3. The possibility of reloading a created XML file to delete/add one or various pictures without having to remake the list from scratch or opening it with gedit to add the missing lines... (this happened to me because some of the portrait pix I included wouldn't show nicely on my laptops' wide screen so I edited the XML by hand by just changing the file names of those pix to different landscape ones)

Thank you very much for making this program =D> ... will continue to use it and report on any weirdness I may encounter.

Cya,

 - Ogro -

---

### Post by rubenverweij on 2010-01-17
Thanks for your excellent suggestions. I have already implemented point 1, and I'm working on the other two.

---

### Post by Cuco3 on 2010-04-10
big fan of your software. thanks! :guitar:

---

### Post by rubenverweij on 2010-04-10
Thanks for your compliment!
There is a new version available here: [http://ubublogger.wordpress.com/2010/03/31/new-version-of-wallpaper-stacks-creator-0-3/](http://ubublogger.wordpress.com/2010/03/31/new-version-of-wallpaper-stacks-creator-0-3/).
If you have any suggestions, please post a comment or file a bug on launchpad!

---

### Post by MrAntonB on 2012-07-12
His launchpad PPA doesn't seem to work anymore. If anyone still wants this app, you can download the .deb installer here:

[http://wallpaper-stacks.softonic.com/linux](http://wallpaper-stacks.softonic.com/linux)

---

### Post by nothingspecial on 2012-07-12
Thanks for the info, but this thread is old.

Closed.

---


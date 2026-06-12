---
title: "Gnome Power Manager Config... no free space... TOTAL NEWBIE so old posts not helping"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by WyvernAldyth on 2012-01-24
**Re: Problem with gnome power manager** 
            
                                                                Ok guys...

Let's say I really AM an absolute beginner, so I am definitely in the right forum area.
Lets say that when people say RAM,I think they own a dodge truck and  that megabites are what I take on a 30 minute lunch break so that I have  time left for a smoke.

That being said... I DID finally figure out how to get into terminal (by  following link on other posts marked "solved"), and that I definitely do have the same problem  with having no free space. I even figured out how to do df -h and see  it! (I take pride in my little accomplishments). 

I even did cd /var/log and then removed with rm anything possible that  was simply a log - hoping this might make just the tiniest bit of room  so that my ungeekified self might be able to get in there and delete  something the "normal" way.

I still cannot boot.

Keeping in mind that I hold geeks in the highest regard (to point of  telling my 16 year old daughter to date someone on the computer club...  not that it would help, her school has a designated computer instructor  and has to call Geek Squad to fix THEIR system and he admits he knows  nothing of Linix and has only heard of Red Hat in passing and NEVER  heard of ubuntu!).

**[COLOR=SeaGreen]Exactly how, play by play, do I find something to  delete through terminal? Then... how do I delete it - rm (filepath)? Is  there something safe to delete that you can just give me some code and I  can just hit enter (that would be GREAT!) and I could just reinstall  later?[/COLOR]**

And just as important... once I do delete something (if I ever figure THAT out)... how do I keep this from rehappening?

This is on a Lenovo 20013 Notepad (thinkpad?) computer with 80G HD that has a 7G partition for ubuntu (hope that helps). Ubuntu is the ONLY operating system. I thought this a GOOD thing as it is my 16yo's computer and would be less likely to get viruses from all those wonderful networking sites and teen hangouts she goes to.

Gods knows the HD is big enough to handle what is on it as it is  practically new... just seems to have been set up wrong to begin with.  And as the shop I bought it at actually charges people $90 to convert a  Windows computer TO ubuntu (which is of course a FREE program)... you  can imagine what they charge for repairs!

Please help! Living with a 16yo that cannot go to twitter and facebook is becoming a matter of life and death (she claims she will die without... and if she whines about it one more time I may kill her!) 

Pretend you are talking to your grandmother that cannot program the time on her microwave here. I am a bit better than that... but do need more explicit directions than "go to root and delete something".

THANK YOU!

edited to add: that I DO know to put sudo before the rm to get it to actually delete. It DID delete the log files... but was not enough. Where do I find something else to delete?

Also...as it is notebook, could not use cd if had one. CAN put on a USB from my crappy home computer (hey man... it has 128RAM, when i say crappy I MEAN it!)... but no clue what command to put in terminal to get it to run from the flash drive. And would still need answer on how to keep from happening again. Repartition? How?

---

### Post by SuaSwe on 2012-01-24
Hello WyvernAldyth!

From your post, I take it you have received some message from somewhere that you do not have sufficient free space. I have a couple of questions.

1. Where are you seeing this, e.g what do you do to produce the error?
2. Can you post the output of 'df -h' here for us to have a look at?

Deleting things in /var/log seems like something of a waste of time to be honest; the logs in there are not likely to take up a lot of space.

Something you could do - provided you have root access - is run the following line in Terminal (accessed via Applications > Accessories > Terminal):

```

sudo find / -size +10M

```

This will basically find any file larger than 10MB in size within the root directory (which includes all home directories); you can adjust the number according to the size of file you want to find. You can then judge whether the files in questions are ones you want to remove, and then when required simply remove them by doing 'rm /path/to/file'.

---

### Post by jerrrys on 2012-01-24
In terminal:

sudo apt-get clean

that should open up some space

Is this a WUBI install?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=increase+wubi&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=increase+wubi&sa=Search&cof=FORID:9)

125K of ram?  check out puppy

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

---

### Post by WyvernAldyth on 2012-01-25
df -h produces the following:

Filesystem         Size          Used          Avail          Use%          Mounted on
/dev/sdal1        7.1G          6.8G            0             100%            /
none                 493M         292K         492M          1%              /dev
none                 497M           0             497M          0%              /dev/shm
none                 497M         184K         497M          1%              /var/run
none                 497M         292K         497M          0%              /var/lock
none                 497M         292K         497M          0%              /dev/lib/init/rw

So that 100% basically is causing the gnome power manager configuration error from what I understand.

sudo apt-get get clean does nothing

Have no idea what a WUBI install even is. Notebook came this way (without the error of course - used to work great)

Notebook has LOTS of RAM. Home desktop is in need of it. 

sudo find / -size +10M

This gives me a bunch of choices. Firefox and skype are recognizable. As is adobe/flashplugin. 
Some odd ones are:
find: '/proc/2281/task/2281/fd/5' : No such file or directory
find: '/proc/2281/task/2281/fdinfo/5' : No such file or directory
find: '/proc/2281/fd/5' : No such file or directory
find: '/proc/2281/fdinfo/5' : No such file or directory

Also /home/user/.cache/rhythmbox files show up more than once.

Would any of these be safe to delete and reinstall after fixed problem?

If so... how do I fix partition or storing defaults so this does not reoccur?

---

### Post by jerrrys on 2012-01-25
sudo apt-get autoremove

also:

rm /home/[COLOR=Black]your login name/.thumbnails

You must fill in the "your login name" part and use with care.  Once a folder is removed this way, its gone for good.
[/COLOR]

---

### Post by WyvernAldyth on 2012-01-25
OK... removed a huge rhythmbox file.

THE BEAUTIFUL SOUND OF UBUNTU PLAYED!!!!!!

Large GUI on desktop screen is very clearly warning me! Says:

[SIZE=3]**This computer has only 89.0 MB disk space remaining.**[/SIZE]

So... NOW WHAT?

Once again has 80G HD with 7G partition. 
[B][COLOR=SeaGreen]1) How can I increase partition?
2) Will I lose info when I do this?
3) Do I somehow need to tell this computer to store things somewhere other than this partition?Is there way to do that?
[/COLOR][/B]
It lets me have option to "examine". When I do it gives me a LONG list. this is under DISK USAGE ANALYZER

Total filesystem capacity: 7.0 GB (used: 6.6 GB GB  available: 454.7 MB)

_Folder Usage Size Contents_
> usr 47.6% 3.1GB 9 items
> home 35.5% 2.3GB 1 item
> lib 10.5% 690.5MB 116 items
> var 4.4% 290.6MB 13 items
> boot 1.5% 101.2MB 44 items
> etc 0.2% 13.9MB 232 items

Everything else so small I assume it is not really a problem. 

You guys have been great so far... I can boot ubuntu and gnome up and work out of terminal...
**[COLOR=Red]NOW WHAT?[/COLOR]**

Because if i do nothing... I KNOW it is going to happen again!

---

### Post by WyvernAldyth on 2012-01-25
ok... may be getting closer to problem... or may just be confused.

She has a folder on her desktop that is simply labeled "personal".
In it is everything from all her Nook books, audio books, audio files (music), tons of graphic files... and all the other crap teens are constantly snagging from internet and media devices. It has over 2GB of crap in it.

Is this what is causing the problem? Do I simply need to do a little housecleaning and move these to the appropriate folders under "places" on top toolbar? Into "Documents", "Music", "Pictures", "Videos", "Dowloads"... etc?

---

### Post by jerrrys on 2012-01-25
I use "gparted" for this.  If you have a Ubuntu Live CD; you have gparted.  If not you need a gparted live cd or usb.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

also a real good idea to back up your personal files.

EDIT: Moving files around will not resolve the problem.  Your out of space.

---

### Post by WyvernAldyth on 2012-01-25
OK... but GParted says it is 120+MB and computer is yelling at me that I only have 89.6MB available. Wont trying to install or run it just cause that nasty Gnome Power Manager error to pop up and refuse to let me boot up and log in again? Can put on USB... cd would not work as it is a notebook so has no CD drive thingy (very technical... aren't I?)

And we now have a new problem... danged thing will not connect to internet. Does not even search for available connections. Does not list connections used in past anymore. Even tried left clicking networkmanager applet and chosing Create New Connection and entering info from my Fios box just like Fios tells me to. No dice. Will not connect. Any clue what I screwed up and how to fix IT? (sigh) Prob has to do with logs I rm removed... those and a rhythmbox file were only things I rm removed. Al;so tried doing Update Manager... but it says I am all updated.

Thank you for having so much patience with me. I swear if I can just get this thing running and out of danger I am going to go buy an ubuntu or linux for dummies book tomorrow when out! Just PLEASE bear with me and help me get it to point that a book might do me some good!

THANK YOU!!!!!!!

---

### Post by jerrrys on 2012-01-26
There has been reports (bug) of gparted reading the wrong size.  Just to verify, open a terminal and enter:

df

That will tell you the size, but gparted can still be used regardless of what it says.

About your other problems; put those on the back burner for now and resize your partition.

As for having patience; not a problem.  I will be in and out today and will try to keep up with your post, so have some patience with me too. :)

---


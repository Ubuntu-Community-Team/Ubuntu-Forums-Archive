---
title: "Ubuntu won't run because of barely any space on disk and messed up openbox removal"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by nano-oscuro on 2014-02-07
**Level of expertise**: So-so, used this for a few years but not to the maxim of it's potential at all.

Hey fellas!
 
My Ubuntu laptop won't boot properly because there's no space on it's small, 8-gig disk... After I login in the login screen, everything goes dark and the desktop won't show. This is when I remember some old tip to press CTRL+ALT+F1 and go to a terminal, run ```
sudo unity --replace
``` and hit CTRL+ALT+F6 to go back to the desktop, where it runs crappily. From there I ran Ubuntu Tweak's Janitor tool, it used to do the trick and free up enough space for the laptop to run again... Unfortunately it's stopped happening.

Someone told me to ```
sudo apt-get install openbox
``` but then it locked up when I tried logging in with Openbox/GNOME selected so I ```
sudo apt-get remove openbox
``` to free up some precious space.

From here on, **logging into the system via the login screen** will make it freeze and make me realize I went 2 steps backward instead of any of them forward.

Then that same friend told me to try ```
sudo apt-get upgrade
``` but I don't know if it will even upgrade (stuff's been downloaded and depackaged though :-k) because well, going back to where I started, this hard disk has no more space! The command that lists space available (I think it was df or du or something) says 100% on /dev/sda1 so... Yeah...

So right now I'm waiting for it to finish "upgrading"... Let's see what happens, just gonna use this post to start getting help because I doubt this will fix it... If it does fix it though I'll mark it as solved.

I'll patiently wait for your answer.

[COLOR=#a9a9a9][SIZE=1]Wish there was some way to list Hardware Info and version and such, I bet you guys need it...


[/SIZE][/COLOR]

---

### Post by deadflowr on 2014-02-07
The first command 
```
sudo unity --replace
```
is something I would not recommend running.
If only because the sudo makes it run as root.
you can run that command with a simple
```
unity --replace
```
The openbox install and removal command are fine.
However, you really should run 
```
sudo apt-get update
```
and ```
sudo apt-get upgrade
```
before installing anything, so that your system is completely up to date.
Up to date system seem to have the best chance of least risk.

Being that you have only 8GB of disk space(?) you're going to need to be extra vigilante.
 You can first try cleaning a little with
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```
the last command (autoremove) should be looked at and used carefully, sometimes it might try removing something important.
(But that's rare in most cases)
You might also look at removing any old kernels
This fun link explains a very helpful command to so
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

As far as getting a functional desktop, I no nothing about the basics of the machine you're running so more info on the box would help.
A lighter desktop might help.
openbox can be a little advanced, maybe something like xfce would work better,
Again I don't know about the box, so...

---

### Post by nano-oscuro on 2014-02-07
Hey I think I've ran all of those in these situations... Will check out that link later and see if I can do anything... I gotta go to bed so I'll keep posting here once I'm ready for some more troubleshooting.

Oh, I once ran ```
unity --replace
``` alone and the Ubuntu Tweak Janitor wouldn't let me clear the files after selecting them, after adding the sudo, it worked...

---

### Post by deadflowr on 2014-02-07
Odd, sorry I didn't notice the command was unity --replace.
I don't even think that's a viable command in the first place.
On older version(12.04) you can reset unity to the defaults with
```
unity --reset
```
and if you wanted to run the compiz window manager(which unity uses anyway)
```
compiz --replace
```
more here
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by nano-oscuro on 2014-02-07
Alright I did all of that and I still cannot login... ```
unity --replace
``` doesn't work cause it isn't initialized as it is when I get to login... 

So what now, game over? I mean, I still got the CTRL+ALT+F1 terminal available, so I guess I can still drop some mad commands and make this work... Just don't know what exactly.

---

### Post by nano-oscuro on 2014-02-09
Help? Anyone?

---

### Post by bc.haynes on 2014-02-09
You might post your machine's specs while waiting for help: Model, CPU, RAM, and VGA.

```
lspci | grep VGA
```

---

### Post by nano-oscuro on 2014-02-09
All that came out of that was: ```
00:02.0 VGA compatible controlelr: Inter Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics controller
```


...Hope it helps.

---

### Post by deadflowr on 2014-02-09
I think now it's time to get back to the basics of this thread and see how much space on the disk you have
post the output of
```
df -h
```
Let's see how much space you have to work with at the moment.

For the record, you graphics card seems fine as is.
I'm doubtful that's in any way the problem.

---


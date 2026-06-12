---
title: "404 errors when using Synaptic script"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by puzzledinportorchard on 2013-01-31
As I have an offline computer running Xubuntu 12.04.1 LTS and an online LiveCD of 10.04 I am using the excellent instructions I've found here to add software through Synaptic Package Manager taking the shell script and its results back and forth on a USB drive, and using Cortman's brilliant instructions on this site I've updated the repositories (if that's the right word) to keep Synaptic updated.  Everything has worked wonderfully, though of course it's a cumbrous process; still, it works.

Except for some reason when I use it to download VLC.  The script gets many '404' errors, not, for some reason, finding the links active.  I opened a terminal on this connected liveCD session and repeated the first wget instruction of the shell, and this is what I get:

ubuntu@ubuntu:~$ wget -c [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.4-0ubuntu0.12.04.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.4-0ubuntu0.12.04.1_amd64.deb)
--2013-01-31 23:14:40--  [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.4-0ubuntu0.12.04.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.4-0ubuntu0.12.04.1_amd64.deb)
Resolving us.archive.ubuntu.com... 91.189.91.15, 91.189.91.13, 91.189.91.14
Connecting to us.archive.ubuntu.com|91.189.91.15|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-01-31 23:14:41 ERROR 404: Not Found.

Obviously, since I'm here typing this, it's not a connectivity problem.  I know how easy it is to overlook some small typo on the command line but this is the command exactly as it appears in the script Synaptic made.  Can anyone see what I'm doing wrong?

---

### Post by Cheesehead on 2013-01-31
> **puzzledinportorchard said:**
> As I have an offline computer running Xubuntu 12.04.1 LTS and an online LiveCD of 10.04 I am using the excellent instructions I've found here to add software through Synaptic Package Manager taking the shell script and its results back and forth on a USB drive, and using Cortman's brilliant instructions on this site I've updated the repositories (if that's the right word) to keep Synaptic updated.  Everything has worked wonderfully, though of course it's a cumbrous process; still, it works.

Except for some reason when I use it to download VLC.  The script gets many '404' errors, not, for some reason, finding the links active.  I opened a terminal on this connected liveCD session and repeated the first wget instruction of the shell, and this is what I get:

ubuntu@ubuntu:~$ wget -c [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.4-0ubuntu0.12.04.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.4-0ubuntu0.12.04.1_amd64.deb)
--2013-01-31 23:14:40--  [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.4-0ubuntu0.12.04.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.4-0ubuntu0.12.04.1_amd64.deb)
Resolving us.archive.ubuntu.com... 91.189.91.15, 91.189.91.13, 91.189.91.14
Connecting to us.archive.ubuntu.com|91.189.91.15|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-01-31 23:14:41 ERROR 404: Not Found.

Obviously, since I'm here typing this, it's not a connectivity problem.  I know how easy it is to overlook some small typo on the command line but this is the command exactly as it appears in the script Synaptic made.  Can anyone see what I'm doing wrong?

Your package index is out of date and needs to be updated.
The missing packages have been replaced in the repositories by newer packages. For example, libavutil51_0.8.4-0ubuntu0.12.04.1_amd64.deb has been replaced by libavutil51_0.8.5-0ubuntu0.12.04.1_amd64.deb

---

### Post by meteorrock on 2013-01-31
If you are getting errors in the terminal on updating the apt-get, try these commands if you are comforable in using the terminal.

```
sudo rm /var/lib/apt/lists/* -vf
```

Then update your apt-get to get rid of those 404s and other errors. This will update your links and packages through the terminal. 

```
sudo apt-get update
```

I hope this helps you. This is what I did to fix errors I was getting. Its old school but fast. Sometimes the update package manager is hard to fish through on deleting your outdated links and headers giving you problems ;)

---

### Post by puzzledinportorchard on 2013-02-01
I am actively terrified of the command line.  I killed a computer once using the command line.  Killed it good and dead.  And though I greatly appreciate the kind attempt to help, I have not a clue what the 'rm' command means, what that asterisk is doing there, or if you mean on the online or the offline computer (offline, I'd guess) or what kind of process 'then update your apt-get' refers to at all.

Not your fault whatsoever; it's good of you to try.  I'm sure those things should mean something to me, but this is exactly why I've suggested elsewhere on this site that they should have a forum titled "Absolute Klunkhead" just for people like me.  Thanks anyway; you've given significant information suggesting that the process I'd gone through just before generating the script did not in fact update the package list in Synaptic, which program I cling to like a frightened child.  Thanks.  

I think now I'll go back to the tutorial thread.  It does seem, after all, the answer is there: I only started this thread because I thought it wasn't pertinent to that thread and I didn't want to be rude.  Should I do something to close this thread?

---

### Post by varunendra on 2013-02-02
> **puzzledinportorchard said:**
> Should I do something to close this thread?
You can not close a thread. Only Admins and Mods can. Like I can do it for you. But I don't see a need for it here.

Instead, I would recommend you try whatever is convenient to you, and post back here. If it is a success, you should consider posting in detail the method you tried, and mark the thread as **[Solved]** using "**Thread Tools**" link above the top post. Doing so benefits others who are looking for solution to similar problem.

On the other hand, if you are stuck somewhere, post back the details and hopefully someone would come up with a solution.

Hope you get it all sorted :)

---

### Post by audiomick on 2013-02-02
> **puzzledinportorchard said:**
> I am actively terrified of the command line....

I wont try and talk you into using the command line if you don't want to, but I can try and explain a few things.

Regarding killing your system: the way Ubuntu is set up with the sudo mechanism, if you try and do anything that bears the risk of killing your system "good and dead", you *will* be asked at some point for your password. I find that a good indicator of when I have to start paying attention properly to what I am doing... ;)


Finding out what a command does: you should be aware of the man pages. To find out what they are, do
```
man man
```
This is absolutely harmless. All it does is calls a page with information about the function that calls the information page.

To find out about rm
```
man rm
```

the general usage is
```
man <command name>
```

Regarding the suggested rm command: what it will do is remove the contents of the directory /var/lib/apt/lists which is where the list of packages that the package management uses is stored.
The asterisk is a joker. It means "any character". If you told it to do
bu*
it would "see" bunnies, burritos,burrows and so on, but not barnacles, bannanas, or chimpanzees. Using the asterisk alone causes the command to "see" all files regardless of their name. There are a large number of commands that will accept * as a joker.

Very little thought will bring you to the conclusion that this can indeed be a dangerous option ***if*** used with root privileges (sudo) and in a directory containing system files. There is a combination that is not allowed to be posted here that will erase every file on your system. Having said that, if you are paying proper attention to which directory you point it at it is a very useful tool. If you are using it as root (no sudo),it is fairly harmless.

So, that command removes the contents of the directory containing the package lists. The following command
```
sudo apt-get update
```
refreshes the list. You would have noticed that this command comes with a sudo, and will require a password to be carried out. You might want to do
```
man apt-get
```
to have a look at what apt-get does, and what the option -update does. 

In synaptic, there is an option in the edit menu to reload (or refresh? My system doesn't speak English...) the package information. I believe that should do exactly the same thing as those commands are intended to do, i.e. clear out your package list and refresh it to get rid of old or corrupted information.

I don't know the process you referred to of obtaining packages and then transferring them to another computer with a USB stick, so I can't say if this step should be done on the online or the offline system. However, it will not harm the system that is online. Given that the package lists are updated out of the internet, the function wont work on a machine that is not online.

---

### Post by puzzledinportorchard on 2013-02-02
> **varunendra said:**
> You can not close a thread. Only Admins and Mods can. Like I can do it for you. But I don't see a need for it here.


Thank you.  What had happened was, I thought I'd solved the offline package update problem through the excellent tutorial Cortman had written and that the scripts not working was indicating some other problem; and not wanting to be guilty of a faux pas - highjacking a thread, I think you would put it - started a new one.  But this does belong, as it turns out, to that thread: Synaptic did't update as I thought it had, so now I'm back to focusing on that thread.

However, from the post audiomick has kindly contributed below (well, it will be 'above' once I post this) I'm now glad I started this.  I'm determined to get the Synaptic problem solved, but I now have all the most current parts, collected as it were by hand, of ubuntu-restricted-extras to solve my original reason for seeking this site out- failure of Parole to play anything - and don't know what to do with them.  Without Synaptic's help, or getting Ubuntu Software Center to install something from the hard drive (which I have read that it won't) I'm all at sea. 

I now will immerse myself in the depths of his post and hope I don't drown.

And thanks for the help.

---

### Post by puzzledinportorchard on 2013-02-02
> **audiomick said:**
> I wont try and talk you into using the command line if you don't want to, but I can try and explain a few things.
. . .
Very little thought . . .


HA!  Now you appeal to my strength!  I can think as very little as anybody!

The computercide I'd commited was in Ubuntu 8, using what turned out to be out-of-date howtos to change a partition.  Instead I wiped out Grub.

I've already looked at the man pages to apt.  I understood almost none of it: it's filled with jargon.  That's the rotten thing about Linux of all flavors.  You start out with one seemingly small thing you're trying to do, but to do it you need to understand another thing, and to understand that thing you need yet another obscure thing understood, and soon you are lost in a never-ending nesting-Russian-dolls nightmare, with every swamp slogged through leading only to another swamp.  Which is just fine if swamp-wading is what you enjoy, but not so much otherwise.  Still, I slog on.

If I understand your point, an answer would be to do manually what I'm trying to get Synaptic to do for me - point to file:/home/[me]/dists/precise/main (and ...universe etc)/binary-amd64/ as the source of the Packages.gz that I've put there manually, since it can't be done on the internet.  Then I could use Synaptic to generate a script that would work to -

No, that seems illogical, having to feed by hand a program that's meant to protect me from having to feed it by hand.  In that direction lies madness.  It would make more sense to abandon the front end entirely, and learn apt -

Which means learning the bash, and the filing system, and who knows what other anciliary but vital operations that lurk, hidden, unsuspected, alligator-like, to drag me under the mud.  (Of the swamp, you see.  I do so love allegory.  It's a disease, metaphorically.  I think I'm becoming giddy.)

However, I will look into the file you mention, and see where that leads me.  Thank you greatly for the time and patience.  On through the swamp!  (Yes, I've become giddy.  Time to let this go for awhile.)

---

### Post by puzzledinportorchard on 2013-02-03
Does anyone know what Synaptic uses to read the most recent package lists (usually, unless I'm misunderstanding, from "http:/whatever-mirror-you-use/.../binary-amd64/Packages.gz", but in my case, "file:/home/[me]/ .../Packages.gz" because of the offlinedness)?  To solve a problem I've reached - Synaptic can find the manually-updated package lists before generating a script for me to take to an online computer, but it seemingly won't read them, which is why it's generating the out-of-date calls that caused the problems that started this thread.

I'm trying to learn if Synaptic unpacks those .gz files or just reads into them to get the new package lists it uses.  Anybody know?  I'm wondering if there's something like 'unrar' or the like, or something that reads into unpacked .gz files, that Synaptic is supposed to have but doesn't.

And then an admission, quietly.  (As frustrating as this all has been, I'm kinda enjoying it.  Don't tell anybody.)

---

### Post by Zill on 2013-02-03
> **puzzledinportorchard said:**
> As I have an **[COLOR="Red"]offline[/COLOR]** computer running Xubuntu 12.04.1 LTS...
My understanding is that "offline" is the main problem here!

Ubuntu, as with most (if not all!) current Linux systems, is designed to run, and be maintained, *online*.  This ensures that the system can be easily updated regularly and reliably.

I suggest that you use an ethernet cable to connect your offline computer to a router that allows connection to the internet and then simply update and upgrade as required to bring the system up to date.

If there are any security implications with leaving the computer connected to the internet then you could remove the ethernet cable after updating.  Just reconnect it occasionally to upgrade as necessary.

---

### Post by puzzledinportorchard on 2013-02-03
Not possible.  The offline is absolutely, unalterably offline.  Not by any means can I put it online.

Besides, the only reason I would do so, if I could, would be to solve this one problem of Parole not playing.  Everything else on it is now just as I want it to be.  And I don't go online much anyway.  Wouldn't be online now but for this uncompleted task, in which one small thing lead into another and another and another . . .

Besides, I talk too much.  And I know what the real problem is - I'm afraid to try this by command line.  I've already discovered that if I had tried that already, I'd have messed things up because I'd have installed the wrong packages.  I thought this was about getting the newest, so I took the scripts that were making bad calls, followed the links, got what looked like the newest packages for the calls that got '404' errors and copied them to the offline.

But that's the wrong idea.  Only last night did it occur to me to actually unpack all the latest Packages.gz and see what they were.  Four reeeeealy long lists.  So I looked for what these lists were pointing to - and in most cases it was older files, things that appear to have been put there a year or more ago.  Not what I was expecting.  Had I put the packages I'd found onto the 'puter, in every case I would have been wrong.

See?  Alligators.  Also: See?  I talk too much.

---

### Post by Zill on 2013-02-03
> **puzzledinportorchard said:**
> Not possible.  The offline is absolutely, unalterably offline.  Not by any means can I put it online...
Fair enough - it's your machine and if you choose to do things the hard way then that is your prerogative.  Good luck.

---

### Post by puzzledinportorchard on 2013-02-03
Well, that's it.  No more.  Done.

I decided that Synaptic is simply not going to read the fresh package lists, so I downloaded and unpacked fresh copies of all four Packages.gz files from Oakland, found the twenty packages pointed to in ubuntu-restricted-extras, put them in a folder in /home, and using the syntax indicated (sudo dpkg -iR folder-name, if I now remember correctly) which looked, as far as I could tell, successful except for one (something about flashplug).

Now the picture-viewer doesn't seem to know the names of any .jpgs.  It will display about five or six, then crash.  The whole desktop sort of flinches from time to time.

And Parole's behavior is unchanged: it works only for .mpegs.

I could vent, but to what end?  Linux is, quite simply, not an operating system for anyone not willing to completely immerse themselves in arcane minutia.  Also, rocks are hard, and bananas, unless they are green, are yellow.  Such is life.

Adios.

---

### Post by varunendra on 2013-02-04
For others to see, (I assume) this is the method you are following : [http://ubuntuforums.org/showthread.php?t=1901446](http://ubuntuforums.org/showthread.php?t=1901446)

Answer to your question in post #9 (from my own understanding, not from any authentic source) -

Synaptic (or apt command or Ubuntu Software Center) uses "sources.list" file and "sources.list.d" directory (located in /etc/apt directory) to decide 'Where' to look for packages.

Once the compressed package list (the .gz files) is found, the individual package list (to track updates and resolve dependency issues) is maintained in /var/lib/apt/lists directory.

Last, you DON't have to uncompress the .gz files manually, it is done automatically by the package manager (apt or synaptic or USC..)

Now my understanding of your problem - um.. well.. I'm simply afraid to make a guess ;)

Maybe I'd like to make a few, hopefully easy & straightforward, attempts if you could post the **[COLOR="DarkRed"]download script[/COLOR]** you generated, and the contents of your [COLOR="DarkRed"]**sources.list**[/COLOR] file (use the following command *(oops!)* or simply copy-paste the file itself) -
```
cat /etc/apt/sources.list
```

And the outputs of the following commands *(again oops!! ;))* just so I can confirm your kernel's version & architecture -
```
lsb_release -d
uname -mr
```

Let's hope we can make it a bit easy this time :)

---


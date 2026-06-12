---
title: "I can't get rid of Eclipse Indigo"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-12-28
Hi,

I'm running Ubuntu 10.04 LTS and have tried the solutions I found to completely remove Eclipse but the icon is still in my menu; and, when I click it, Eclipse still starts up. Apparently it is still on the system.

The information I've found and followed is this:

> 
[http://askubuntu.com/questions/31846/completely-uninstall-reinstall-eclipse-and-add-support-for-php-and-jquery](http://askubuntu.com/questions/31846/completely-uninstall-reinstall-eclipse-and-add-support-for-php-and-jquery)

And

[http://ubuntuforums.org/showthread.php?t=1755453](http://ubuntuforums.org/showthread.php?t=1755453)




The first thing I did was go into synaptic (on my own) and do a search on "eclipse". This brought up two installed packages. If I remember correctly they were both java libraries (that's all that was there). I marked them both for complete removal and did an "apply" - which went through successfully. After that I went into Applications > Programming and I saw that the entry for Eclipse was still there. When I clicked it, Eclise started up.

That was when I did an internet search and found the above links. WHen I attempted to run the first line of code shown at the first link...

```

sudo apt-get purge eclipse

```


I was told in the terminal that something was accessing the directory so it couldn't carry out the action (not the exact words but that's what it said). I restarted the machine then ran it again.

After the first line of code at the first link (as above) I was told it did not remove anything because there was nothing to remove (again not the exact words but that's what it said). Then I ran the second line of code at that first link...

```

rm -r ~/.eclipse/

```


It appeared to succeed as I got a new line with no complaints. Again, eclipse is still in the menu and it starts up (indicating it's still instaled).

Then I find the information at the second link. I run the second command given...

```

sudo apt-get autoremove

```


which revealed a lot of junk in my system (not just to do with eclipse). I ran it. Again, Eclipse is still there and still starts up.

What do I do to get rid of this thing?

---

### Post by hansdown on 2011-12-28
Hi,ClientAlive.

A quick fix, is...

cick ststem>preferences>startup applications.

Uncheck eclipse.

Restart computer.

Someone should be along, to help with the complete removal.

---

### Post by ClientAlive on 2011-12-28
> **hansdown said:**
> Hi,ClientAlive.

A quick fix, is...

cick ststem>preferences>startup applications.

Uncheck eclipse.

Restart computer.

Someone should be along, to help with the complete removal.


Right on. Thanks but I'm really more concerned with removing it entirely to free up space for something different. Thanks for your help.

---

### Post by lolpenguin on 2011-12-28
Try [FONT="Courier New"]sudo apt-get purge *[/FONT] again and post the results.

---

### Post by ClientAlive on 2011-12-28
> **lolpenguin said:**
> Try [FONT="Courier New"]sudo apt-get purge *[/FONT] again and post the results.


Results of running "sudo apt-get purge eclipse"

```

sudo apt-get purge eclipse
[sudo] password for shine: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

-----------------------------------------

Edit:

I'm sorry, I'm a dumbass. I had Synaptic open. With it closed the resulting output is:

```

sudo apt-get purge eclipse
[sudo] password for shine: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package eclipse is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by LinuxFan999 on 2011-12-28
The only other possible solution is to back up and do a clean reinstall of Ubuntu.

---

### Post by lolpenguin on 2011-12-28
Try removing all Eclipse packages:
```
sudo apt-get purge eclipse-*
```

---

### Post by ClientAlive on 2011-12-29
> **lolpenguin said:**
> Try removing all Eclipse packages:
```
sudo apt-get purge eclipse-*
```


Ok, well here's the output I get from that:

```

sudo apt-get purge eclipse-*
[sudo] password for shine: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting eclipse-ecj for regex 'eclipse-*'
Note, selecting eclipse-cvs for regex 'eclipse-*'
Note, selecting eclipse-jdt-gcj for regex 'eclipse-*'
Note, selecting eclipse-common-nls for regex 'eclipse-*'
Note, selecting eclipse-source for regex 'eclipse-*'
Note, selecting eclipse-jdt for regex 'eclipse-*'
Note, selecting eclipse-pde for regex 'eclipse-*'
Note, selecting eclipse-platform-common for regex 'eclipse-*'
Note, selecting eclipse-rcp for regex 'eclipse-*'
Note, selecting eclipse-plugin-cvs for regex 'eclipse-*'
Note, selecting libeclipse-jni for regex 'eclipse-*'
Note, selecting eclipse-ecj-gcj for regex 'eclipse-*'
Note, selecting eclipse-pde-gcj for regex 'eclipse-*'
Note, selecting eclipse-platform-data for regex 'eclipse-*'
Note, selecting eclipse-platform-gcj for regex 'eclipse-*'
Note, selecting eclipse for regex 'eclipse-*'
Note, selecting eclipse-platform-nls for regex 'eclipse-*'
Note, selecting libcommons-jci-eclipse-java for regex 'eclipse-*'
Note, selecting eclipse-platform for regex 'eclipse-*'
Note, selecting eclipse-rcp-gcj for regex 'eclipse-*'
E: Couldn't find package eclipse-*

```


It probably couldn't hurt to redo my system but it is somthing I try to avoid. It's just so time consuming - you know? I really, really wish I could find a solution to this that doesn't involve that. Even if I had to go in and manually remove certain files or directories.

What doesn't make sense is how it could still start up and run after everything I did before starting the thread here. It takes a lot for a program to work/ run correctly. I could understand if there were some remnats around and it would make sense if it tried to start up then failed - that would make sense. But no, this thing appears to be in tact, like nothing phases it! What the heck Eclipse! How did they design this thing, like a virus? Like some malicious root kit, did they have the code hide/ install to some chip in my system? It's just crazy!

---

### Post by westie457 on 2011-12-29
Hi

**_This has the risk of completely breaking your system._**

From a terminal ```
gksudo nautilus
``` go to File System then search for 'eclipse'. Select all and 'Shift+Del' to avoid filling Root Trash.

Close the window and the terminal as well to be slightly safe.
Then run 'Computer Janitor' to remove any left over dependent files.


Hope this helps.

---

### Post by cortman on 2011-12-29
Nobody's tried/recommended

```
sudo apt-get remove eclipse
```

That's the only way I usually remove software...?

---

### Post by ClientAlive on 2011-12-29
> **cortman said:**
> Nobody's tried/recommended

```
sudo apt-get remove eclipse
```

That's the only way I usually remove software...?

> **cortman said:**
> Nobody's tried/recommended

```
sudo apt-get remove eclipse
```

That's the only way I usually remove software...?


For some reason, when I used synaptic (in the beginning) I connected that in my mind with have done the removal step. Really though, it was just the two java libraries that even showed up in synaptic - which I did remove (back then at the start).

So here's what happens:

Ran

```

sudo apt-get remove eclipse

```

which resulted in the following output:

```

sudo apt-get remove eclipse
[sudo] password for shine: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package eclipse is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Then I went in and found eclipse is still there in the menu, clicked it; and, again, eclipse starts up and runs like a champ.

Then it occured to me that I may not have restarted the computer since this all began and how, don't ask me why, it might make a difference. So I restart the computer, go back into the menu; again, eclipse is still there, I click it, it starts.

Gonna run through westie457's suggestion right now and will report back on it.

Thanks

---

### Post by ClientAlive on 2011-12-29
> **cortman said:**
> Nobody's tried/recommended

```
sudo apt-get remove eclipse
```

That's the only way I usually remove software...?


For some reason, when I used synaptic (in the beginning) I connected that in my mind with having done the removal step. Really though, it was just the two java libraries that even showed up in synaptic - which I did remove (back then at the start).

So here's what happens:

Ran

```

sudo apt-get remove eclipse

```

which resulted in the following output:

```

sudo apt-get remove eclipse
[sudo] password for shine: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package eclipse is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Then I went in and found eclipse is still there in the menu, clicked it; and, again, eclipse starts up and runs like a champ.

Then it occured to me that I may not have restarted the computer since this all began and how, don't ask me why, it might make a difference. So I restart the computer, go back into the menu; again, eclipse is still there, I click it, it starts.

Gonna run through westie457's suggestion right now and will report back on it.

Thanks
------------------

Edit:

You know, it's been a while since I installed eclipse, and I never really used it except to open it a couple times and poke around - it's possible I didn't install it through the package manager. I may have compiled the source or somthing similar. I wonder if that could have some affect on things - perhaps there was no record of it created in the package manager even though it is on the system.

---

### Post by ClientAlive on 2011-12-29
> **westie457 said:**
> Hi

**_This has the risk of completely breaking your system._**

From a terminal ```
gksudo nautilus
``` go to File System then search for 'eclipse'. Select all and 'Shift+Del' to avoid filling Root Trash.

Close the window and the terminal as well to be slightly safe.
Then run 'Computer Janitor' to remove any left over dependent files.


Hope this helps.

Yup! That did er!! Thank you westie457.

I had to try and remember where user applications are stored. What I recalled was they go into either /usr/bin or /usr/sbin (usually but not always). Turns out that this one is in /usr/bin  It appeared to all be contained in one directory. I...

~ Deleted that directory
~ Looked also in /usr/sbin as well as for outlying files (files outside of the
  program's directory) in both /usr/bin and /usr/sbin
~ Ran computer janitor but saw the only 3 entries don't pertain to eclipse (what
  does come up is pretty straigt forward and is things I wish to keep)
~ Went into the gnome menu and found that the icon and entry for eclipse is still
  present

However, when I click that entry I get a small window containing the following in it:

> 
Could not launch 'eclipse'

Failed to execute child process "/usr/bin/eclipse/eclipse-linuxtools-indigo-SR1-incubation-linux-gtk/eclipse/eclipse" (No such file or directory)


Please correct me if I'm wrong but this seems to reveal that eclipse is no longer on the system.

As far as the icon and menu entry - I do recall having to create the entry after I had installed eclipse. I think I can remove it the same way and be golden.

Yup! You right click on the little, white ubuntu icon in the far upper left hand corner of the screen (I'm running Ubuntu 10.04 w/ gnome) and get a drop down menu - clicking "edit menus" takes you to where you can select and delete the entry.

Now...  This is a very small thing and would not bother me too much either way. I recall when I set the menu entry up I had to search for the icon to use. The question occured to me how the icon (the eclipse icon) could show up in the menu after the eclipse folder and everything in it had been deleted. It made me wonder how that menu edit thing works. Did it create a copy of the icon somewhere rather than just link to the source?

Like I said, it's a very small thing and I wouldn't be concerned about a little icon hanging around somewhere. It's just one of those curious things I wondered about.

Thanks again for your help - we figured out how to get rid of eclipse.

:D

---

### Post by ClientAlive on 2011-12-29
I just restarted the computer and nothing appears to be broken - well it starts and seems to work anyhow. So far so good.

:popcorn:

---


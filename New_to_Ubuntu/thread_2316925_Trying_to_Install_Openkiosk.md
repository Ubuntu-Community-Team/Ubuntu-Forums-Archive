---
title: "Trying to Install Openkiosk"
date: 2016-03-12
forum: New to Ubuntu
---

### Post by lauri.hirn on 2016-03-12
I'm at work, and I installed Ubuntu on one of the PC's here. I've never used Ubuntu before, but since my work involves me sitting around half the time, I thought I'd take this time to learn something about this OS.

The install was simple enough, and it connected to the internet by itself, and it didn't even take that long (compared to the Win 7 I installed on this machine first, which didn't even work in the end).

The first issue however, was with installing a program.

I tried installing Open Kiosk, since we need it at work. I know it's possible to turn this PC into a kiosk without open kiosk, but it became personal after a while of trying (4 hours). And also, I wanted to learn what was wrong, and how to do it.


Here's what happened:

I downloaded a compressed folder from their website, made for Linux. I unpacked it on the desktop. The instructions there said that I should run a file called install-icon.sh, then double click on the new Open Kiosk icon that would appear on the desktop, and proceed from there.

I had to learn how to do that. First I used the "sudo apt-get install install-icon.sh" command.

After writing that command, it asked me for a password. I give it my pass, and then this happens:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package install-icon.sh
E: Couldn't find any package by regex 'install-icon.sh'

I tried this a few times, I tried to use the command "cd foldername" to open up the desktop directory where the folder for this program was, but it didn't work.

I tried to update the package list, or at least I think that's what it's called, this happened yesterday so I can't remember the exact terms right now. I also copy pasted the name of the file from a list of files on the terminal, just to make sure that the "-" symbol wasn't something else.

Then I tried dragging the "install-icon.sh" onto the terminal. A wild Open Kiosk icon appeared on the desktop,

Double clicking it brings me this error:

There was an error launching the application.

Details: Failed to execute child process "/home/username/Desktop/openkiosk/openkiosk" (No such file or directory)

Now, the way I see it, this pc is correct, there is no such thing as an openkiosk file in the /openkiosk folder, except for an image picture.

So next I tried changing where the icon on the desktop takes me to. There was little logic to it, but I tried changing it to the "install-icon.sh" file, but nothing happened.

This is pretty much the gist of it. 

Where did I go wrong, what did I do to deserve this?

_______________________

SOLVED:

What we can all learn from this is, that trying to install a 32-bit program on a 64-bit system in Ubuntu will have the terminal give you an error

```


no such file or directory


```

even if the files do exist. 


If however, there is more to this, perhaps even a solution, please do write a comment on this thread and I will add it to this first post!

---

### Post by Bucky Ball on 2016-03-12
Maybe try again from the start. Delete the cruft you now have and the downloaded file and download the file again to the Downloads folder. Open a terminal and these two commands:

```
cd Downloads
dir
```

The first command should put you in the Downloads folder where your downloaded file is. The 'dir' command will give you a list of what's in that folder. Check that the name of what you're supposed to be installing is there (your command needs to include it exactly as you have it in the folder).

It didn't come down in a compressed folder and you're not uncompressing? Anyway, it helps us help you if you provide links to where you've downloaded things from and to what you've tried. Difficult to tell you what you've done wrong when we don't know what the page is telling you to do right. 

You will probably want to be posting back some code if you get errors. Please use code tags when doing so. See the link in my signature at the bottom of this post. Good luck.

---

### Post by lauri.hirn on 2016-03-12
A quick reply, thanks!

Here is the link I'm using:
- [URL="http://openkiosk.mozdevgroup.com/install.html"]http://openkiosk.mozdevgroup.com/install.html

[/URL]I deleted all the files that I had downloaded previously.

I used the codes you gave me, brings me back to my childhood memories of working with computers.

The "dir" command gave me this:

```
 openkiosk-2.5.3-2014-03-12.tar.bz2 
```

This is the compressed file that I downloaded, that I've done nothing to.


I'm going to the shop so will be returning in 30 min or so!

---

### Post by Bucky Ball on 2016-03-12
[See here]("http://ubuntuforums.org/showthread.php?t=926018"). Don't forget, there's lots of Linux community and millions of pages about unzipping tar.bz2 files and many other things. Just search for 'my issue ubuntu'. :)

So while you are in Downloads (and make sure you are there by checking to the left of the cursor in terminal), run:

```
sudo tar -xjvf openkiosk-2.5.3-2014-03-12.tar.bz2
```

The poster on the thread in the link actually got it right first time. They just forgot the 'sudo'; super user do! Makes you root temporarily so you can run commands that can seriously break your system. :)

After that command you should be back at the cursor. Run 'dir' again. You see the .sh file there now? I *think* you now only need:

```
install-icon.sh
```

... without the 'run'. Double click the icon that appears on the desktop if it does. If you cop some errors, they may be caused by something to do with the [Linux system requirements here]("http://openkiosk.mozdevgroup.com/system-requirements.html"), namely the dependencies and required software OpenKiosk needs to run.

* Just for your info, and not that you had much choice here, but the best line of attack when looking for software is the Software Centre then a third-party .deb file if you can get it. After that you're looking at adding PPAs, compiling yourself, or .sh, among others. 

Good luck. Out of here for awhile.

---

### Post by lauri.hirn on 2016-03-12
SORRY FOR DOUBLE POST, I DON'T KNOW WHAT HAPPENED!

I unpacked the folder using the commands you gave me, and now there is a folder with a lock on it in the Downloads folder.

I typed in 

```
 
cd Downloads
dir

```

The dir gave me the original download folder, and the new openkiosk folder

I typed in ```
 install-icon.sh 
```

just to test it, but it said ```


install-icon.sh: command not found

```

I also tried the ```


sudo apt-get install install-icon.sh

```

but to no prevail. I get the same error
```


E: Unable to locate package install-icon.sh
E: Couldn't find any package by regex 'install-icon.sh'


```

I then moved to the actual openkiosk folder. I wrote dir, and it gave me all the files in that folder, including the "install-icon.sh" file.

I wrote the same codes; 
```


install-icon.sh



```

and

```
 

sudo apt-get install install-icon.sh


```

and I tried copy pasting it as well, but to no prevail, I still get the same errors.

I then dragged the install-icon.sh from the folder onto the terminal. An icon appeared on the desktop, but double clicking it gives me the exact same error I posted in the original post.


I wrote ```
 find 
``` on the terminal in the "openkiosk" folder, and the "install-icon.sh" file was in that list. I also wrote "dir", and the file is in that list as well.



I'm gonna be here for another 8 hours so any help would be greatly appreciated. I think I've exhausted all the options I found online that made sense to me.

_____________

EDIT:

Ok, after hours if working on this, I got SOMETHING to happen.

I had thought of this before but thought, nah, that's not going to work. Not sure if it did work, since there is still no icon on my desktop, but..
I changed the name of the .sh file from "install-icon.sh", to "isntallicon.sh".

After that I did this;

```
 

cd Downloads/openkiosk

sudo apt-get install installicon.sh


```

Then a whole lot of stuff happened in the terminal. I can't see it all, but in the end there's a whole lot of text, and after each line it says 

was not found

As an example:

 ```
 

E: Release 'installicon.sh' for 'nvidia-modprobe' was not found".


```

At least something else happened than the usual error, but not sure if this helped.

____________________

EDIT 2:

Ok, now I type in ```


sudo apt-get install isntallicon.sh


```

and I get the same error I originally got....

I am completely lost.

_______________

EDIT 3:

I wrote

```


sudo apt-get install ./installicon.sh


```

That did the same thing as last time, with everything in the terminal list saying "was not found".

An icon appeared on the desktop however, but clicking on it gives me the same error as in the original post, so I am still at square 1.

Here's a screen cap:

[http://postimg.org/image/v6f7dwlrj/](http://postimg.org/image/v6f7dwlrj/)

---

### Post by Bucky Ball on 2016-03-12
Change the name of the file back to what it was originally, please. The '-' was not your issue and changing it may cause other problems that just make this harder to resolve.

---

### Post by steeldriver on 2016-03-12
Please (for now) forget about the command 'sudo apt-get install ...', it's only appropriate for installing software direct from online repositories, not for 3rd-party software that you have downloaded as a compressed archive from a website

If you've unpacked the archive successfully then you should just need to type

```

./install-icon.sh

```

The leading ./ is important here - it tells the shell to look for the file in the current directory - otherwise you will get "command not found"

---

### Post by Bucky Ball on 2016-03-12
I have changed the title of this thread to reflect your issue and thus give you a better chance of support.

---

### Post by lauri.hirn on 2016-03-12
I changed it back before, realized it didn't matter but I did something else differently.

So basically my problem culminates in the error I get from the desktop icon. Is there any chance you could try and install this program and see if you get the same error? I have found nothing through google on this specific issue, with this specific program.

What I really should be looking for is the Ubuntu's version of the .exe file, right? What could that be?

The "install-icon.sh" is most likely just the script to install an icon on the desktop, and the icon it self should lead to the actual executable file right? But there is no executable file by the name of "openkiosk", like what the desktop icon is trying to find.

There is another .sh file, called run-mozilla.sh, but I can't execute that, even when it has premission to be executable. the only way I get anything out of the files is by running them through the ```
 

sudo apt-get install ./install-icon.sh

sudo apt-get install ./run-mozilla.sh


```

if I simply use the ```


./install-icon

./run-mozilla.sh

[code]

the first one giving me the faulty icon, and the second one giving me an error saying 

[code]

cannot execute .


```

What I find odd about that error is that the period has a space in front of it.

---

### Post by howefield on 2016-03-12
> **lauri.hirn said:**
> ....Is there any chance you could try and install this program and see if you get the same error? 

Which version of Ubuntu are you using ?

---

### Post by Bucky Ball on 2016-03-12
Sorry, don't really have an install or box for experiments of this kind at the moment.

---

### Post by lauri.hirn on 2016-03-12
Ubuntu version 14.04

Ok, I almost got the tech guy here, he walked in, and then he walked back out again. 

I have one day to finish this problem. It's not even about getting it to work for the festival, it's about me over coming an obstacle and living to tell the tale about it to my grand kids.

____

EDIT:

Ok, so, I found an item called "openkiosk", and "openkiosk-bin".

If I've understood it correctly, these two files are executables. So the desktop icon is actually aiming to start these files. I don't know how I missed them before, but I guess I misunderstood the .sh files as the ones that would actually be running the program.

So the question now is, why doesn't the desktop icon start the program, when these two executables, especially the one called "openkiosk" can actually be found where it's supposed to be. They are both marked as executable files in the properties.

I have a feeling a conclusion is soon to be had.

_____

EDIT2:

So there is no actual ".bin" at the end of those files. I tried running the files without the .bin at the end, and I tried adding it to the end of the file but it gives me an error that this file doesn't exist either way, when it msot certainly does exist, since I can see it when I type in "dir" in the terminal.

___________

EDIT3:

Ok, the only thing I could find and can think of, is that maybe the program is for a 32-bit system, and I'm running a 64-bit system. Could that  give me the error of "file or directory doesn't exist"?

_____

Quest Log, Final Entry

Ok, it must be that the program is only for a 32 bit system. Windows can run a 32 bit program on a 64 bit system, but apparently Ubuntu cannot? 

I feel I have come to an end of an adventure.

---

### Post by Bucky Ball on 2016-03-12
Ubuntu can. :)

You need the 32bit executables installed I think and I know nothing about that. As far as I'm aware they are installed by default in Ubuntu.

Good luck in any case. Maybe try again further down the track and when you have a bit more time.

---

### Post by lauri.hirn on 2016-03-12
Nooooooooooooo you opened this wound for me again! :D

Well damn it, still got 1,5 hours to figure this out, and then tomorrow when they pack these machines up, I will say farewell to my worthy adversary, whether I suffer a defeat, or it does.


_____

EDIT:

Ok, here we go guys. I installed 32 bit libraries from 

```


sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0



```

Now, when I create the icon, there is no more error message, but alas, nothing happens when I click it, or try to run it.

I am one step closer to the goal, help me out here!

_____

EDIT7001:

Oh my god.. I think I have messed something up bad.. Some of the files say they have invalid encoding and their names are all messed up..

I redownloaded the file but it still says that.

_____

EDIT2,000,561:

Ok, reboot helped with the weird bug with the file names. 

But the desktop icon still does nothing. no error, nothing.

---

### Post by howefield on 2016-03-12
Just to confirm, works out of the box in 32 bit installation.

No errors or problems.

---

### Post by lauri.hirn on 2016-03-13
Alright, so now I just have to figure out how to run this on a 64-bit system. I have a few more hours before these computers are packed away.

Any suggestions would be greatly appreciated.

______

EDIT:

Seems this quest is over. I'm about to wrap this up, but I think I can safely say the final conclusion is, that Open Kiosk will not work on a 64-bit machine, even if you download the libraries etc.

Thanks for the help guys!

After this experience, though it was a gruelling one, I will seriously consider installing Ubuntu on my own PC.

---

### Post by joe_wong on 2016-03-26
I'm late to this thread but I was able to install and run open kiosk on a 64 bit Linux Mint (cinnamon desktop environment) without any problems. It's the only distro I've had success with. I've tried Ubuntu (Unity and Mate) and received the same errors as you. If anyone has any solutions on how to get this working on Ubuntu, I'm all ears.

---


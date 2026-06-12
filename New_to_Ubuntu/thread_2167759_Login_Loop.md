---
title: "Login Loop"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by jim_collins2 on 2013-08-14
I have used Mythbuntu for at least 5 years now with very few problems.  I am running 12.04 and everything was running very slow so I rebooted the computer (runs both front and back end).  I came to the general login screen and entered my password and after a few seconds the screen turned blank, then a few seconds of that, then back to the login screen.  I can login as guest, but I have no permissions to do anything (like start the front end).  I don't know all that much about ubuntu, so please reply as though I know very little.  Thank you in advance for your help!

---

### Post by Petro Dawg on 2013-08-14
Does this seem like what is going on....

[http://ubuntuforums.org/showthread.php?t=2167760](http://ubuntuforums.org/showthread.php?t=2167760)

I just had a log-in loop issue myself, I solved it after reading this...

[http://askubuntu.com/questions/146137/login-screen-loops-unless-you-login-as-guest](http://askubuntu.com/questions/146137/login-screen-loops-unless-you-login-as-guest)

---

### Post by jim_collins2 on 2013-08-14
I tried the solution listed in the second thread.  When I tried to login as user what do I type.  On my main login screen it says JC-Myth under the icon of the computer.  The user is JC (my initials).  I tried both of those as the user and it told me the password was incorrect.  I know the password was correct.

---

### Post by jim_collins2 on 2013-08-14
OK, tried again with different results.  I am not sure if I got to the home user, but it rebooted at sudo reboot. and then it did the same as before. login loop

---

### Post by varunendra on 2013-08-14
Does the partition have enough available space on it? Check with -
```
df -h
```

You may try logging into one of the virtual consoles with Ctrl+Alt+F1 to run above command. Alternatively, you may try the recovery mode or a live session.

---

### Post by jim_collins2 on 2013-08-14
Alright I may have something useful to someone who knows what they are doing.  I have to type this in as I am on a laptop and the system is on a desktop and I'm not sure how to transfer this any other way.  I scrolled down and tried the next solution on the second thread.  I typed sudo apt-get install --reinstall xorg  then it asked for my password and accepted it.  the following is what appeared: (I think this is correct, but I cannot see the first character, something with the display on the TV, it works fine when I am in Ubuntu I used my best guess or put a question mark)
Reading package lists... Done
building dependency tree
reading state information... Done
you might want to run 'apt-get -f install' to correct these:
the following packages have unmet dependencies:
?libvlccore5 : Depends: vlc-data (= 2.0.8-0ununtu0.12.04.1) but 2.0.5-0ubuntu0.?.04.1 is to be installed
?vlc : Depends: vlc-nox (= 2.0.8-0ubuntu0.12.04.1) but 2.0.5-0ubuntu0.12.04.1 is to be installed
?vlc-plugin-notify : Depends: vlc-nox (= 2.0.8-0ununtu0.12.04.1) but 2.0.5-ubuntu0-12.04.1 is to be installed
?vlc-plugin-pulse : Depends: vlc-nox (= 2.0.8-0ubuntu0.12.04.1) but 2.0.5-0ubuntu0.12.04.1 is to be installed
: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Petro Dawg on 2013-08-14
Are you comfortable with terminal??

If so, have you tried using the terminal in a live boot CD or USB, mount your Hard Drive, navigate to **/home/"user"/** and then delete the hidden **.Xauthority **file in your home directory?


If you use an Ubuntu live CD/USB you will probably have to navigate to the home directory on the Linux partition.  

Once you are in the correct directory, use the terminal command...

```
sudo rm -rvf ./.Xauthority
```

It should provide a verbose output of "removed './.Xauthority'" if successful.



Otherwise you can just use Puppy Linux (which runs in root), mount the harddrive (by clicking on the Hardrive's Icon on the Desktop), and navigate to the home folder using GUI.  You can then "show hidden folders" and then delete the .Xauthority file.

Otherwise you will need to wait for someone else's help with this issue.  Those are the only ways I know how do it.

---

### Post by jim_collins2 on 2013-08-14
typed in df -h and got:
filesystem       Size     Used   Avail   Use%  Mounted on
dev/sda1        12G      11G        0    100%  /
dev               491M    4.0K     491M    1%  /dev
mpfs             201M     1.1M     200M  1%   /run
one              5.0M      0          5.0M   0%   /run/lock
one               501M    0          501M   0%   /run/shm
overflow         1.0M     244K     780K   24% /tmp
dev/sda6        920G     849G      71G   93% /var/lib

---

### Post by Petro Dawg on 2013-08-14
> **jim_collins2 said:**
> Alright I may have something useful to someone who knows what they are doing.  I have to type this in as I am on a laptop and the system is on a desktop and I'm not sure how to transfer this any other way.  I scrolled down and tried the next solution on the second thread.  I typed sudo apt-get install --reinstall xorg  then it asked for my password and accepted it.  the following is what appeared: (I think this is correct, but I cannot see the first character, something with the display on the TV, it works fine when I am in Ubuntu I used my best guess or put a question mark)
Reading package lists... Done
building dependency tree
reading state information... Done
you might want to run 'apt-get -f install' to correct these:
the following packages have unmet dependencies:
?libvlccore5 : Depends: vlc-data (= 2.0.8-0ununtu0.12.04.1) but 2.0.5-0ubuntu0.?.04.1 is to be installed
?vlc : Depends: vlc-nox (= 2.0.8-0ubuntu0.12.04.1) but 2.0.5-0ubuntu0.12.04.1 is to be installed
?vlc-plugin-notify : Depends: vlc-nox (= 2.0.8-0ununtu0.12.04.1) but 2.0.5-ubuntu0-12.04.1 is to be installed
?vlc-plugin-pulse : Depends: vlc-nox (= 2.0.8-0ubuntu0.12.04.1) but 2.0.5-0ubuntu0.12.04.1 is to be installed
: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Are you logged in as Guest doing this???

---

### Post by jim_collins2 on 2013-08-14
I cic Ctrl+Alt+F1 and got a prompt.  To do that I was asked for a password that seemed to work (I only use one password for not financial things).  So I was in the proper user.

---

### Post by Petro Dawg on 2013-08-14
At this point, when you try to log-in normally, are you getting an Incorrect Password error or does it try to log-in but spit you back out to the log in screen after a couple seconds?

Also I wouldn't be trying to [COLOR=#000000]**sudo apt-get install --reinstall xorg** at this point.[/COLOR]

---

### Post by jim_collins2 on 2013-08-15
it spits me back to the login screen.  i did login as guest, create another user, (it asked me for the password for the main user), then tried logging in as the new user and got the same result ( for the new user I said do not ask for password on login).  Still looped back to the login page.

---

### Post by jim_collins2 on 2013-08-15
when I checked the memory it seemed that the first directory was full.  Could that do it?  And if so, how can I make room?

---

### Post by Petro Dawg on 2013-08-15
I highly suggest using a live boot CD/USB of some sort and verify if you actually deleted the[COLOR=#000000] [/COLOR]**.Xauthority **file in your home directory.

---

### Post by jim_collins2 on 2013-08-15
I'll have to make one.  do you have the best link that I can try?

---

### Post by varunendra on 2013-08-15
Hold on guys, the partition is full, deleting .Xauthority file, I suspect, isn't going to fix anything until this is resolved first (and most probably this is the only thing that needs to be resolved) -
> **jim_collins2 said:**
> typed in df -h and got:
```
filesystem       Size     Used   Avail   Use%  Mounted on
**dev/sda1        12G      11G        [COLOR="#FF0000"]0[/COLOR]    100%  [COLOR="#FF0000"]/[/COLOR]**
*<snip>*
dev/sda6        920G     849G      71G   93% /var/lib
```

Use a live CD/USB to boot and see what files you can move/delete from your Home directory to make room in the root partition (/).

---

### Post by Petro Dawg on 2013-08-15
> **jim_collins2 said:**
> when I checked the memory it seemed that the first directory was full.  Could that do it?  And if so, how can I make room?


I'm not sure if I would trust that reading if it was run within a virtual terminal.  Unless you specifically remember only assigning yourself a 12G partition during install.  Do you dual boot, or did you install Ubuntu to the entire hard drive?

---

### Post by Petro Dawg on 2013-08-15
> **jim_collins2 said:**
> I'll have to make one.  do you have the best link that I can try?

I personally find [Puppy]("http://puppylinux.org/main/Download%20Latest%20Release.htm") to be the easiest to use for this kind of stuff.  You can of course use the same media you used to install Ubuntu and run as a live session.  But then you will have to deal with **sudo** user stuff to get permission to delete files.  Be careful though, without the sudo protection you can easily delete anything on your hard drive, even the stuff you shouldn't (treat it like windows).

---

### Post by jim_collins2 on 2013-08-15
I believe the partition is full also.  I ran sudo 'apt-get -f install' and it seemed to be working, but then I got the message can't write to /var/cache/man/3346: No space left on device errors were encountered while processing:

So I need to boot from a CD or flash drive, navigate to this directory, delete things?  Can you tell me what in that directory should not be deleted?  Also to prevent this from happening again, can I change the size of that partition?

---

### Post by varunendra on 2013-08-15
> **Petro Dawg said:**
> I'm not sure if I would trust that reading if it was run within a virtual terminal.
Command outputs in a virtual terminal are no less or more reliable than what you get in the normal terminal (gnome-terminal) in the GUI.

> **jim_collins2 said:**
> 
So I need to boot from a CD or flash drive, navigate to this directory, delete things?

Recommended ^ but not necessary. You may try deleting thing from terminal. For starters, try -
```
sudo apt-get clean
sudo apt-get autoremove
```

**PS:**
I can help, but I am a very slow typist and my connection is slow too (read - super slow, snail pace etc.). I can't win the blitz race you guys are putting here ;)

---

### Post by jim_collins2 on 2013-08-15
thank you all for your help - I will download Puppy now!

---

### Post by Petro Dawg on 2013-08-15
> [COLOR=#000000]I believe the partition is full also. I ran sudo 'apt-get -f install' and it seemed to be working, but then I got the message can't write to /var/cache/man/3346: No space left on device errors were encountered while processing:[/COLOR]

[COLOR=#000000]So I need to boot from a CD or flash drive, navigate to this directory, delete things? Can you tell me what in that directory should not be deleted? Also to prevent this from happening again, can I change the size of that partition?[/COLOR]

Er, if you are getting into that situation I would use live boot just to back up whatever important documents you might have in your Home directory and then just do a fresh install.   (if you only have a 12 G partition it should be easy to back it all up)

I don't know how the virtual environment works, it may not be correctly reading the available space (I could be wrong). 

If you are sharing a HD with Windows, you will probably have to shrink the windows partition from within windows (Google it to find out how) to give your self some more room and then reinstall Ubuntu.  If it is a 100% dedicated Ubuntu hard-drive then do a "delete everything and re-install".

---

### Post by jim_collins2 on 2013-08-15
Varun, ANY and ALL help is greatly appreciated.  I am downloading both the latest CD and Puppy and I have at least 1 hour before they are downloaded.  I will try to do the sudo apt-get clean and autoremove and let you know the results.

---

### Post by jim_collins2 on 2013-08-15
I have no problem starting over, but can I save the shows that have been recorded?  If not then my wife will be most displeased.  I cannot overstate the level of her displeasure.  I NEED to save those shows!!!!!

---

### Post by varunendra on 2013-08-15
> **jim_collins2 said:**
> I will try to do the sudo apt-get clean and autoremove and let you know the results.

You can run those (and all) commands from both the virtual consoles or the recovery mode > drop to root shell. I'm assuming you may have more than a hundred MB in the /var/cache/apt/archives directory which will get cleaned up by the "apt-get clean" command.

Once you have about 100-200 MB space available, you can boot normally into GUI mode and can check > delete/move files to make more room.

And yes, for a normal installation of Ubuntu, **at least** 20-26 GB space is recommeded, not sure about mythbuntu though. In any case, your first priority is to get the GUI again, then you can try whatever you are comfortable with to expand the partition.

---

### Post by jim_collins2 on 2013-08-15
If I do start over, what would the best partition size be?  I have a 1TB hard drive.  This computer is the only one used for Myth.  It is both the back end and front end.  I have limited music stored on the computer, limited pictures also.

---

### Post by jim_collins2 on 2013-08-15
I ran the get clean and after hitting return I saw nothing - just returned to the next line.  the autoremove would not work, I got the same error as before (the long post I had earlier).  I believe booting form the CD is my best option at this point.

---

### Post by varunendra on 2013-08-15
Simple maths :

Size of $Home = Size of expected User Data + some more (about 100-200 MB).
Size of root (/, if the Home is on a separate partition, which currently is not) = 2 GB or more

If the Home directory is within the root (/), then,
Size of root (/) = Size of expected User Data + 2 GB or more

Even easier maths :
Size of root = as much as you can comfortably allocate, and not less than 26 GB.

A separate 2 GB or more swap partition is always a recommended thing that goes without saying.


That being said, you can do it all without starting over, although backing up data > starting over is usually a better option if you don't have too many programs to install and not too much configuration to do afterwards.

---

### Post by varunendra on 2013-08-15
> **jim_collins2 said:**
> I ran the get clean and after hitting return I saw nothing - just returned to the next line.
..means it did its job successfully. Now check the free space again -
```
df -h
```

---

### Post by jim_collins2 on 2013-08-15
still 100% used in the first directory.

---

### Post by varunendra on 2013-08-15
Next thing to check is if you have too many older kernels installed. Please post the output of -
```
dpkg -l | grep linux-image
```

We can (and should) delete all but the two latest kernels.

---

### Post by jim_collins2 on 2013-08-15
I forgot how to make the line after -1.  Or is that -l lowercase L?

---

### Post by varunendra on 2013-08-15
It is a lowercase "L" in "dpkg -l", then pipe symbol "|" between "dpkg -l" and "grep...".

The pipe symbol (|) is on the same key as the backspace (\) on my US-104 style keyboard, and is located above the "Enter" an below the "Backspace" key. (is also located in the left of the backspace key in some keyboards).

---

### Post by jim_collins2 on 2013-08-15
rc  linux-image-2.6.28-11-generic              2.6.28-11.42                              Linux kernel image for version 2.6.28 on x86/x86_64
rc  linux-image-2.6.28-15-generic              2.6.28-15.52                              Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-2.6.28-16-generic              2.6.28-16.55                              Linux kernel image for version 2.6.28 on x86/x86_64
rc  linux-image-2.6.31-14-generic              2.6.31-14.48                              Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-16-generic              2.6.31-16.53                              Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-19-generic              2.6.31-19.56                              Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-20-generic              2.6.31-20.58                              Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-21-generic              2.6.31-21.59                              Linux kernel image for version 2.6.31 on x86/x86_64
ii  linux-image-2.6.31-22-generic              2.6.31-22.67                              Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.32-25-generic              2.6.32-25.45                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-26-generic              2.6.32-26.48                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-27-generic              2.6.32-27.49                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-28-generic              2.6.32-28.55                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-29-generic              2.6.32-29.58                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-30-generic              2.6.32-30.59                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-31-generic              2.6.32-31.61                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-32-generic              2.6.32-32.62                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-33-generic              2.6.32-33.72                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-34-generic              2.6.32-34.77                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-35-generic              2.6.32-35.78                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-36-generic              2.6.32-36.79                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-37-generic              2.6.32-37.81                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-38-generic              2.6.32-38.83                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-39-generic              2.6.32-39.86                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-40-generic              2.6.32-40.87                              Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-41-generic              2.6.32-41.94                              Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-2.6.32-42-generic              2.6.32-42.96                              Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-3.2.0-30-generic               3.2.0-30.48                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-31-generic               3.2.0-31.50                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic               3.2.0-32.51                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic               3.2.0-33.52                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic               3.2.0-34.53                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic               3.2.0-35.55                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-36-generic               3.2.0-36.57                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-generic               3.2.0-37.58                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-38-generic               3.2.0-38.61                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic               3.2.0-39.62                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-generic               3.2.0-40.64                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-41-generic               3.2.0-41.66                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-43-generic               3.2.0-43.68                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-44-generic               3.2.0-44.69                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-45-generic               3.2.0-45.70                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-48-generic               3.2.0-48.74                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iU  linux-image-3.2.0-51-generic               3.2.0-51.77                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iU  linux-image-generic                        3.2.0.51.61                               Generic Linux kernel image

---

### Post by jim_collins2 on 2013-08-15
I have downloaded the Puppy Linux and made a CD.  Do you wish to proceed with the CD or as we are currently?

---

### Post by varunendra on 2013-08-15
Whoa!! :-o

And what is the output of -
```
uname -mr
```
??
Just to be extra safe ;)

---

### Post by jim_collins2 on 2013-08-15
3.2.0-30-generic i686

---

### Post by varunendra on 2013-08-15
> **jim_collins2 said:**
> 3.2.0-30-generic i686

Hmm.. odd! I would have expected it to be "linux-image-**[COLOR="#800000"]3.2.0-51-generic[/COLOR]**". Looks like you are booted in an older kernel for some reason.

Anyway, there is still a lot of garbage you can safely remove. You can purge all the "2.6..." versions with "sudo apt-get purge" command. Precisely (based on your output) -
```
sudo apt-get purge linux-image-2.6.28-11-generic
sudo apt-get purge linux-image-2.6.28-15-generic
sudo apt-get purge linux-image-2.6.28-16-generic
sudo apt-get purge linux-image-2.6.31-14-generic
sudo apt-get purge linux-image-2.6.31-16-generic
sudo apt-get purge linux-image-2.6.31-19-generic
sudo apt-get purge linux-image-2.6.31-20-generic
sudo apt-get purge linux-image-2.6.31-21-generic
sudo apt-get purge linux-image-2.6.31-22-generic
sudo apt-get purge linux-image-2.6.32-25-generic
sudo apt-get purge linux-image-2.6.32-26-generic
sudo apt-get purge linux-image-2.6.32-27-generic
sudo apt-get purge linux-image-2.6.32-28-generic
sudo apt-get purge linux-image-2.6.32-29-generic
sudo apt-get purge linux-image-2.6.32-30-generic
sudo apt-get purge linux-image-2.6.32-31-generic
sudo apt-get purge linux-image-2.6.32-32-generic
sudo apt-get purge linux-image-2.6.32-33-generic
sudo apt-get purge linux-image-2.6.32-34-generic
sudo apt-get purge linux-image-2.6.32-35-generic
sudo apt-get purge linux-image-2.6.32-36-generic
sudo apt-get purge linux-image-2.6.32-37-generic
sudo apt-get purge linux-image-2.6.32-38-generic
sudo apt-get purge linux-image-2.6.32-39-generic
sudo apt-get purge linux-image-2.6.32-40-generic
sudo apt-get purge linux-image-2.6.32-41-generic
sudo apt-get purge linux-image-2.6.32-42-generic
```

This should give you a lot more than sufficient space to boot normally. Then we can figure out why you are not booted into the latest installed kernel (not necessary, but a mystery for me nevertheless, unless you have intentionally chosen to boot into an older one).

---

### Post by jim_collins2 on 2013-08-15
guest-0C4Iai@JC-Myth:~$ sudo apt-get purge
sudo: unable to change to sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [122, -1, -1]: Operation not permitted
guest-0C4Iai@JC-Myth:~$

---

### Post by jim_collins2 on 2013-08-15
tried them all together and tried them separately and got the same error each time.

---

### Post by jim_collins2 on 2013-08-15
guest-0C4Iai@JC-Myth:~$ sudo apt-get purge linux-image-2.6.28-11-generic
sudo: unable to change to sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [122, -1, -1]: Operation not permitted
guest-0C4Iai@JC-Myth:~$

---

### Post by varunendra on 2013-08-15
> **jim_collins2 said:**
> guest-0C4Iai@JC-Myth:~$ sudo apt-get purge
sudo: unable to change to sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [122, -1, -1]: Operation not permitted
guest-0C4Iai@JC-Myth:~$

Hmm... that is a different issue then. I'm not sure about the reason, but you can surely run the commands from the recovery console (reboot > press 'Shift' (or 'Esc' key in some cases) to get the grub menu > choose "recovery mode" > drop to root shell > run the commands there.

Once we have the space problem solved, we can focus on these extra issues.

By the way, the command is not just "sudo apt-get purge" if that's what you tried. It has to be the full line as posted in the code box (for example - **sudo apt-get purge linux-image-2.6.28-11-generic**) - one line at a time > let it finish its job > run next line of command.

---

### Post by jim_collins2 on 2013-08-15
I really appreciate your help, but I must be getting to bed, it is 1:20 a.m. here and I have to be at work in 6 hours.  I will try to do the recovery mode and remove the kernels and let you know tomorrow evening.  Thank you again!

---

### Post by varunendra on 2013-08-15
No problem. Good Night !! :)

---

### Post by jim_collins2 on 2013-08-15
Ok, I'm back.  Should I try to use Puppy LInux or another way? I have that CD right here.

---

### Post by Petro Dawg on 2013-08-15
try puppy first, of course ;)

---

### Post by jim_collins2 on 2013-08-15
so I'm not a linux pro by any means but should i reboot, and change the boot sequence to CD first - then is it pretty self explanitory?  I'm going to try to get into that directory and delete a few things right?

---

### Post by Petro Dawg on 2013-08-15
When you first start the computer you should be able to access a "Boot Options" menu by pressing one of your function keys or esc.  Select the DVD with puppy to boot.  It will start up and in the lower left corner of the desktop you should see icons for all attached hard-drives.  Right click on the hard-drive with your linux partion with the problem and select "show location" (I think) and navigate to your affected HOME directory.  Find the .Xauthority file and delete it.

Then you hopefully will be able to log back into unity after you restart the computer.

---

### Post by jim_collins2 on 2013-08-15
thanks - doing it now!

---

### Post by jim_collins2 on 2013-08-15
OK, positive I deleted the file(s) there was a backup also and I deleted that.  Still the same problem.  I can navigate in the /dev/sda1 directory with puppy, but don't know what to delete to give me enough room to login.

---

### Post by Petro Dawg on 2013-08-15
make sure you are viewing hidden files "control + H" (I think) when in the /home/"usr" directory

puppy also has an application installed (at least the last version I used) called GdMap (graphical disk map) which will show you what programs are taking up the most space easily.

---

### Post by jim_collins2 on 2013-08-15
Sorry - you just confused me.  Are you talking about in Puppy or in a terminal? And either way I still do not know what to delete.

---

### Post by Petro Dawg on 2013-08-15
read my updated last post about gdmap.


Also I mean **in puppy** to be sure to show hidden files.  You do not need terminal to do this.

---

### Post by jim_collins2 on 2013-08-15
This machine is dedicated to mythbuntu.  So there is nothing aside from the recordings I need to keep for myself.  I just do not want to delete anything that ubuntu needs to function correectly.  Sorry, but I know so little I would not know by looking what is needed and what is not needed.  What should I be looking for.  It appears that partition is 12G and I am using 100% of it and I'm also using 100% of the 1G overflow directory.  Can I just delete everytthing in overflow?

---

### Post by Petro Dawg on 2013-08-15
Well, only delete things in your home directory, and try not to delete hidden things except the one possibly broken .Xauthority (which you believe you already deleted).

Are any of the recordings you want to keep on your 12 G partition?

Also it just sank in that you mentioned earlier that you deleted the **backup** .Xauthority file also.  I don't remember telling you to do that. 

Edit..

after a quick internet search I think you are OK with deleting both.

---

### Post by jim_collins2 on 2013-08-16
that's a relief - I will go back in and tell you what I see.  I knkow my recordings are not on this partition as they are on the /dev/sda6 (largest partition).  And even if I lose some it will be worth it.

---

### Post by jim_collins2 on 2013-08-16
here are the things in the directory
fd (folder) files in this folder are numbered 1-9
pts (empty folder)
shm (empty folder)
agpgart
apm_bios
audio
audio1
audio2
audio3
audioctl
console
core (this icon is a yield sign)
dsp
dsp1
dsp2
dsp3
full
kmem
loop0
loop1
loop2.....loop7
mem
midi0
midi00
midi01
midi1
midi02
midi2
midi03
midi3
mixer
mixer1...mixer3
mpv401data
mpv401stat
null
port
ptmx
ram
ram0
ram1...ram16
random
rmidi0
rmidi1
rmidi2
rmidi3
sequencer
smpte0..smpte3
srdstat
stderr
stdin
stdout
tty
tty0....tty9
urandom
xconsole
zero

those are all the files i can see in the directory.

---

### Post by Petro Dawg on 2013-08-16
how are you viewing these files and generating the list, in terminal? or in puppy GUI?   And which "the directory" are you referring to?

---

### Post by jim_collins2 on 2013-08-16
i was viewing them in puppy.  I typed them in on my laptop - no cut and paste!  I am referring to the /dev/sda1 directory that was showing 100% usage in an earlier post.

---

### Post by Petro Dawg on 2013-08-16
Unfortunately its getting late and I have to call it a night.  I'm sure there is a simple fix to your issue, but if you can't get a mythbuntu expert to help you out, it may just be faster to do a fresh install.

Good luck.

---

### Post by jim_collins2 on 2013-08-16
thanks for your help - one last question - ou can reply tomorrow if you wish.  can i save my recordings and do a clean install?

---

### Post by varunendra on 2013-08-16
> **jim_collins2 said:**
> thanks for your help - one last question - ou can reply tomorrow if you wish.  can i save my recordings and do a clean install?

Yes you can do so, and is probably a good idea if you can do it easily.

Just curious though, could you boot into recovery mode in the installed Ubuntu? I believe purging the older kernels from there should also be a piece of cake, although I can't say at this point what else (if) may be needed to fix the sudoers gid issue that you encountered yesterday.

---

### Post by steeldriver on 2013-08-16
I agree with varunendra, it should be straightforward to boot into the recovery console (or a virtual terminal via Ctrl-Alt-F1 etc) and purge old kernels from there. You may need to manually delete a couple first to have enough headroom even to run apt-get, but that's not really a showstopper - I've done it and it doesn't seem to break anything (you can rm the actual initrd.img-2.x.x files and then run 'apt-get purge' after to update the package management system - see [http://ubuntuforums.org/showthread.php?t=2098490&page=2&p=12424317#post12424317](http://ubuntuforums.org/showthread.php?t=2098490&page=2&p=12424317#post12424317) for example)

From the recovery root shell you will need to remember to remount the  root filesystem with read-write permissions before you do anything

```

# mount -o remount,rw /

```

then navigate to /boot and do what you need to do. This will probably get you back up and running quicker than having to back up and restore many GB of recordings.

The inability to setgid is a normal feature of the guest account, I think:

```

guest-R9xkPT@lap-t61p:~$ sudo ls /root
sudo: unable to change to sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [122, -1, -1]: Operation not permitted
guest-R9xkPT@lap-t61p:~$ 
guest-R9xkPT@lap-t61p:~$ su steeldriver
Password: 
setgid: Operation not permitted

```

---

### Post by jim_collins2 on 2013-08-16
I am going to go out for lunch in a few hours to buy a 4TB hard drive (my family pushes the limit of the 1TB drive).  I was thinking of starting new with the new hard drive and then once that is working transferring the recordings from the old hard drive to the new one.  I have a couple newbie questions.  Is Ubuntu and Mythbuntu the same?  I have found the Ubuntu download, but is that what I want?  As you can see I am able to use Puppy Linux to view the files in the directory.  Would you use that to try to delete individual files?  I don't know why I was unable to delete the kernels previously.  I have not tried everything in the post that was recently posted as I am at work - would you suggest I do that first.  I'm looking for the easiest way.  My goal is to have the 4TB drive in sooner or later.  Maybe get the current drive working correctly then mirror the drive and make partition changes???  If I go that route can I change the partition sizes afterwards?  Can I mirror a 4TB from a 1TB drive?  I know there were many many questions here - I'm just looking for your suggestions.  Thanks again for your help.  I think I may purchase Linux for dummies as well.  It never hurts to be more educated.

---

### Post by jim_collins2 on 2013-08-16
I will read the post on how to boot into the recovery console and try that first.

---

### Post by jim_collins2 on 2013-08-16
I just read the thread.  If I read this correctly I can type in the following commands:
$ sudo rm /boot/initrd.img-3.2.0-33-generic-pae 
$ sudo apt-get remove --purge linux-image-3.2.0-33-generic-pae
then it should calculate how much this will free and ask me if I wish to proceed. This may/should free up enough memory to login correctly.  Then later in the thread is shows how to remove old kernels.  Do you recommend the last post in that thread?  Does it remove all old kernels?

---

### Post by jim_collins2 on 2013-08-20
OK, so I really screwed it up!  I figured I would start over.  I purchased the 4TB drive and was going to install mythbuntu onto that drive, then when it was working correctly I was going to copy the stored recordings from my old 1TB drive to the new one.  So I was installing the new drive and the heat sink and fan from the processor was n the way so I had to pull that assembly out.  Got the drives back in and then when I put the processor back in I bent a couple pins.  While straightening them one broke!  So Ebay, and a few bucks later the new processor should be here in a couple days.  I also ordered more RAM memory while I was shopping.  SO thank you all again and I will update you on my progress.  I was quite frustrated to say the least.  I am currently downloading mythbuntu-12.04-2.  Will try to install that to the new drive.  Is there anything I need to do prior to installation?  I haven't had to install it for 5 years.  I have HD HomeRun tuners and a decent graphics card, but may upgrade that soon as well.  Thanks in advance for any suggestions and thanks again for all the previous help.

---

### Post by Petro Dawg on 2013-08-21
I hope you remembered to get thermal paste as well.

---

### Post by jim_collins2 on 2013-08-21
I am grabbing it here at work - we have in in abundance - thanks.

---

### Post by jim_collins2 on 2013-08-21
I am grabbing it here at work - we have in in abundance - thanks.

---

### Post by jim_collins2 on 2013-08-21
Alright, I installed the latest version of mythbuntu.  It said installation complete.  Please remove disc and close tray.  I did this and restarted the computer as asked.  It started to boot and then came up with this:
verifying DMI Pool Data .............
error: out of disk.
grub rescue>

Come on - I thought I was home free...............................

---

### Post by jim_collins2 on 2013-08-21
P.S. I can type after it says grub rescue>  but have no idea what to type.  Also I am assuming that it says grub rescue> as I cannot see the first letter, but grub makes as much sense as anything else I can think of.  Should I put the disc back in and try to re-install or run from the disc????

---

### Post by varunendra on 2013-08-22
Ugh ! This is certainly getting unexpectedly long.

Let's see what is going on there.. Please try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") and see if it can automatically repair the booting. If not, please use its "Create BootInfo Summary" button to generate a boot-info summary, then post back its pastebin link here (if you are connected to internet while running it), or the boot-info file itself, so we can see what is where and hopefully suggest the fix.

---

### Post by jim_collins2 on 2013-08-22
I'm at work now - I will do this tonight - thank you.  Do you feel that the partition sizes have anything to do with the latest error?

---

### Post by jim_collins2 on 2013-08-23
I guess we can mark this thread as solved, but the original problem never actually was corrected.  I am up and running (almost).  See New Setup/Old Recordings thread.  I have a new hard drive and new install.  There was a problem with that install (the partitions in particular).  I tried the default settings, but they did not give me enough room for the boot partition or leave any free space on the disc.  One thing when I re-installed mythbuntu I had to actually delete the main partition and then when free space was available I could make the other partitions the correct size.  The login loop never was fixed.  I am now a bit better using the boot CD and may be able to fix it, but now that I have a larger hard drive I will just copy the files to the new drive and then reformat the old drive.  Does anyone have any cool suggestions for a 1TB drive hooked up to mythbuntu?  Games? Movies? Music?  Thanks to all that helped.  I don't know how to mark this solved so can someone tell me or do this?

---

### Post by Petro Dawg on 2013-08-23
I believe "Mark as Solved" is an option under "Thread Tools"

---


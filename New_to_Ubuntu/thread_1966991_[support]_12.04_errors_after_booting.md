---
title: "[support] 12.04 errors after booting"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by J6Remy on 2012-04-27
Hello all, 

I was hoping to solve my problem without asking, but was not able to find what I was looking for. I recently, last night, installed Ubuntu 12.04  dual boot with Wubi.exe and the process was flawless. After getting accustom to the UI I felt comfortable enough to start my development workspace. installed JDK 7 and Android SDK. (worked good) Then I had to sent an email out with some attachments from vista. So I shut Ubuntu down and booted vista. Did what I had to do hoping to get back to my new found OS to play with when this happened. 

In the boot chooser screen, I selected Ubuntu, still going good. then instead of going to the sign in screen the screen was black. It asked me to enter my username and password. So I did. 

it sort of logged me in following that was some error codes to which I was unable to find and explanation on throughout the web.

I quote.

"[...] command not found
-bash: /home/jeremyray/.profile: line 25: unexpected EOF while looking for matching "'" 

and,


"-bash: /home/jeremyray/.profile: line 26 Syntax Error: unexpected End of File"

I cannot acquire root either, I did try "sudo apt-get update" and sudo apt-get upgrade"

I have no idea what to do. If this has been answered point me in the direction, and sorry for a double posted question. Thank you for any and all help in advance. 

-J6

---

### Post by josephmills on 2012-04-27
> **J6Remy said:**
> Hello all, 

I was hoping to solve my problem without asking, but was not able to find what I was looking for. I recently, last night, installed Ubuntu 12.04  dual boot with Wubi.exe and the process was flawless. After getting accustom to the UI I felt comfortable enough to start my development workspace. installed JDK 7 and Android SDK. (worked good) Then I had to sent an email out with some attachments from vista. So I shut Ubuntu down and booted vista. Did what I had to do hoping to get back to my new found OS to play with when this happened. 

In the boot chooser screen, I selected Ubuntu, still going good. then instead of going to the sign in screen the screen was black. It asked me to enter my username and password. So I did. 

it sort of logged me in following that was some error codes to which I was unable to find and explanation on throughout the web.

I quote.

"[...] command not found
-bash: /home/jeremyray/.profile: line 25: unexpected EOF while looking for matching "'" 

and,


"-bash: /home/jeremyray/.profile: line 26 Syntax Error: unexpected End of File"

I cannot acquire root either, I did try "sudo apt-get update" and sudo apt-get upgrade"

I have no idea what to do. If this has been answered point me in the direction, and sorry for a double posted question. Thank you for any and all help in advance. 

-J6

in tty1 do 
```
sudo apt-get install pastebinit 
```

then run 
```
cat /home/jeremyray/.profile| pastebinit 
```

then post link here thanks

---

### Post by J6Remy on 2012-04-27
> **josephmills said:**
> in tty1 do 
```
sudo apt-get install pastebinit 
```then run 
```
cat /home/jeremyray/.profile| pastebinit 
```then post link here thanks

```
http://paste.ubuntu.com/950791
```

what is the pasted link?

---

### Post by josephmills on 2012-04-27
you have no " at the end of you android stuff fix that please 
should look like this 

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
[...]
PATH="$HOME/android/tools:$HOME/android/platform-tools:$PATH"
export PATH="$HOME/android/tools:$HOME/android/platform-tools:$PATH"
```

**EDIT**
plz take a moment to look at this also 
[http://ubuntuforums.org/showthread.php?t=1523315&page=2](http://ubuntuforums.org/showthread.php?t=1523315&page=2)
why this is not in .bashrc ?? 
notice the " at the end. 
then reboot

---

### Post by J6Remy on 2012-04-27
> **josephmills said:**
> you have no " at the end of you android stuff fix that please 
should look like this 

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
[...]
PATH="$HOME/android/tools:$HOME/android/platform-tools:$PATH"
export PATH="$HOME/android/tools:$HOME/android/platform-tools:$PATH"
```notice the " at the end. 
then reboot

Please excuse my ignorance, how would I change that? and place it back to where it needs to be?

---

### Post by josephmills on 2012-04-27
Use nano vi emacs ect I will make video tutorial of how to use nano

---

### Post by J6Remy on 2012-04-27
Make video tutorial? That would be awesome of you.

---

### Post by josephmills on 2012-04-27
OHH and you are **NOT**ignorant   Please feel free to ask any questions that you like we try not too judge people around here. We understand what it is like to be made fun of because we just want to learn. that is one of the great things about the ubuntu community  we are big we are fast and we are smart because we learn for each other, there is a great video that I think you should see(these are my views only and (well mine and FZ)not ubuntu 's or any one related that I know about in ubuntu. ) [http://www.youtube.com/watch?v=JHOWadT0UCg](http://www.youtube.com/watch?v=JHOWadT0UCg) 



Tutorial on how to use nano 

[http://www.youtube.com/watch?v=rfwCQLomWpU](http://www.youtube.com/watch?v=rfwCQLomWpU)

---

### Post by Paddy Landau on 2012-04-27
> **josephmills said:**
> why this is not in .bashrc ?
.bashrc is valid only in a terminal,
.profile is valid throughout the entire session, including for GUI programs.

If you need it only while running a terminal, .bashrc is fine.
But if you need it for non-terminal programs, you need .profile.

The PATH command is there twice, which will cause the new paths to be put on twice.
Remove the first one, leaving only the one beginning with *export*.

---

### Post by J6Remy on 2012-04-27
> **josephmills said:**
> OHH and you are **NOT**ignorant   Please feel free to ask any questions that you like we try not too judge people around here. We understand what it is like to be made fun of because we just want to learn. that is one of the great things about the ubuntu community  we are big we are fast and we are smart because we learn for each other, there is a great video that I think you should see(these are my views only and (well mine and FZ)not ubuntu 's or any one related that I know about in ubuntu. ) [http://www.youtube.com/watch?v=JHOWadT0UCg](http://www.youtube.com/watch?v=JHOWadT0UCg) 



Tutorial on how to use nano 

[http://www.youtube.com/watch?v=rfwCQLomWpU](http://www.youtube.com/watch?v=rfwCQLomWpU)


Thank you for the video, and the inspiring one as well,lol. 

So I will use nano to create a file, then execute it to replace the one I fudged up?

(I have to jump back and forth between ubuntu/vista to check your post.) hope I dont spread any unneeded inconveniences for you.

---

### Post by J6Remy on 2012-04-27
> **Paddy Landau said:**
> .bashrc is valid only in a terminal,
.profile is valid throughout the entire session, including for GUI programs.

If you need it only while running a terminal, .bashrc is fine.
But if you need it for non-terminal programs, you need .profile.

The PATH command is there twice, which will cause the new paths to be put on twice.
Remove the first one, leaving only the one beginning with *export*.

What? I have no idea what that means, guess my noobness is showing..

---

### Post by josephmills on 2012-04-27
> **J6Remy said:**
> What? I have no idea what that means, guess my noobness is showing..

I think that he/she was talking to me saying that about my comment why not in .bashrc a couple of posts back.  And now I know why it is not in bashrc and is in profile :) 

See We learn from each other

---

### Post by josephmills on 2012-04-27
> **J6Remy said:**
> Thank you for the video, and the inspiring one as well,lol. 

So I will use nano to create a file, then execute it to replace the one I fudged up?

(I have to jump back and forth between ubuntu/vista to check your post.) hope I dont spread any unneeded inconveniences for you.


Or you could just fix the one that you already have. 
by using nano like 
```

nano /home/jeremyray/.profile  

```

---

### Post by J6Remy on 2012-04-27
> **josephmills said:**
> I think that he/she was talking to me saying that about my comment why not in .bashrc a couple of posts back.  And now I know why it is not in bashrc and is in profile :) 

See We learn from each other


Ohh ok, thanks for resolving that for me. Ok I hate to nag, but back to the nano thing. I still feel unsure as to what I need to do to get my system to run again. I understand the nano thing, but what exactly do I need to do?

EDIT.. ok you just posted..

---

### Post by J6Remy on 2012-04-27
So I just need to add the " to the end of the path? correct?

---

### Post by josephmills on 2012-04-27
> **J6Remy said:**
> So I just need to add the " to the end of the path? correct?

yes and you could remove the other one like Paddy Landau said his post 
> The PATH command is there twice, which will cause the new paths to be put on twice.
Remove the first one, leaving only the one beginning with export.

---

### Post by J6Remy on 2012-04-27
ok going to go try this now. I will post back soon! don't go anywhere lol I'm sure Im gonna need some more help.

Thanks again.

---

### Post by J6Remy on 2012-04-27
> **josephmills said:**
> yes and you could remove the other one like Paddy Landau said his post

Ok so this is what I did.

```
http://paste.ubuntu.com/950987
```

it says the " [...] command not found"

also, I guess something else was messed up to, I just noticed this. when I boot into ubuntu it says this at the top before I get to put in my username/password

```
 Ubuntu login: [18.033802] [drm:drm_crtc_helper_set_config] *Error* failed to set mode o n [CRTC:6]
```

mybad for not finding this earlier.

---

### Post by josephmills on 2012-04-27
So Close it should look like this 
```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
export PATH="$HOME/android/tools:$HOME/android/platform-tools:$PATH"

```


In other words Remove the [...] part and you are good too go ! 
congrats on getting this far 

:guitar:

As far as the error goes I will google that.

---

### Post by J6Remy on 2012-04-27
> **josephmills said:**
> So Close it should look like this 
```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
export PATH="$HOME/android/tools:$HOME/android/platform-tools:$PATH"

```
In other words Remove the [...] part and you are good too go ! 
congrats on getting this far 

:guitar:

As far as the error goes I will google that.


My gut told me to remove the [...] lol thanks, I also tried google'ing that code..I didn't find anything.

---

### Post by josephmills on 2012-04-27
ok so after hitting up google it comes down to this. 

lets see a ```
lspci -nn | grep VGA |pastebinit
```
grab the link (too post here) 
then run 
```
lsmod | grep -e nvidia -e nouveau|pastebinit 
```
then paste both links back here.

---

### Post by J6Remy on 2012-04-27
Ok, thus far..

When I boot ubuntu, it doesnt go into the sign in screen. Its black it says the code mentioned above. it ask for username and password.

Once I put the username/password in it just gives me

"jeremyray$~"

i can run commands, but the UI never comes up. booting issue? did I forget something?


EDIT.. Ok going to try that now. thanks again.

---

### Post by josephmills on 2012-04-27
lol it is funny when two people post at one time :)

---

### Post by J6Remy on 2012-04-27
lol Isn't it! brb

---

### Post by J6Remy on 2012-04-27
1st one

```
http://paste.ubuntu.com/951124
```

2nd one

```
http://paste.ubuntu.com/951127
```

---

### Post by josephmills on 2012-04-27
And bingo was his name Ohh 

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
then 
press y  then  enter when it asks if you want to add the repository. 
then 
```
sudo apt-get update
```
then 
```
sudo -i 
```
then 
```
rmmod nouveau
```
then 
```
echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf 

```
then 
```
exit 
```
then 
```
sudo apt-get update 
```
then 
```
sudo apt-get install nvidia-current
```
then 
```
sudo reboot
```

Then mark thread as solved
because you should have gui now.

---

### Post by J6Remy on 2012-04-27
> **josephmills said:**
> And bingo was his name Ohh 

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```then 
press y  then  enter when it asks if you want to add the repository. 
then 
```
sudo apt-get update
```then 
```
sudo -i 
```then 
```
rmmod nouveau
```then 
```
echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf 

```then 
```
exit 
```then 
```
sudo apt-get update 
```then 
```
sudo apt-get install nvidia-current
```then 
```
sudo reboot
```Then mark thread as solved
because you should have gui now.

Holy pancakes batman! I shall return! hopefully.. in ubuntu 12.04 to mark this baby SOLVED! brb

---

### Post by J6Remy on 2012-04-27
uhh.. it didn't work. not did it just not work. the error I was having showed three times. Now I am not able to type anything.

It was myfault. 

the first command came back as : not found. 

but I continued. with following commands.

i guess my only option is to re-install right? Since i am not able to type any commands. :(

---

### Post by J6Remy on 2012-04-27
On my cell, alt-ctrl-f1 worked. Guess I messed up a command . I'm now at rmmod nouveau. But it says the module is in use.

---

### Post by Johnny3 on 2012-04-27
From and old man that is bad a spelling and remembering. Try running sudo nautilus or gksu nautilus in the terminal then it will open up you file system and go to view show all files and it is easier for me to find what I want to change. But I have a couple of hard drive so I don't like more than one OS on a hard drive and sometimes(OK a lot of the times) I get things so messed up I is easier to do a clean install.
Good Luch and God Bless Johnny3 65+++ and still ticking.

---

### Post by Paddy Landau on 2012-04-28
> **J6Remy said:**
> What? I have no idea what that means, guess my noobness is showing..> **josephmills said:**
> I think that he/she was talking to me saying that about my comment why not in .bashrc a couple of posts back.
Sorry, J6Remy. josephmills is correct. (BTW, I'm a "he".)

To explain:

When you log in, the computer runs a few commands to set up your environment. The file .profile in your home folder specifies some of those commands.

When you open a terminal, the computer also runs any commands in the file .bashrc. This happens every time you open a terminal, so if you have three terminals open, the commands are run three times.

So, if you place a command in .bashrc, it is available in the terminal but not in your general session. But if you place a command in .profile, it is available throughout your entire session.

I hope that doesn't confuse you too much.

(Files and folders beginning with a dot -- such as .bashrc -- are "hidden" files. You don't see them unless you ask to see hidden files.)

---

### Post by josephmills on 2012-04-28
> **Johnny3 said:**
> From and old man that is bad a spelling and remembering. Try running sudo nautilus or gksu nautilus in the terminal then it will open up you file system and go to view show all files and it is easier for me to find what I want to change. But I have a couple of hard drive so I don't like more than one OS on a hard drive and sometimes(OK a lot of the times) I get things so messed up I is easier to do a clean install.
Good Luch and God Bless Johnny3 65+++ and still ticking.

So I helped the person on IRC (chat room) and was able too get things up and going. It was his nvidia card and it did not support Unity 3d. So once he tried unity 2d bam everything started too work. Johnny3 you should never give up. :) keep on pushing forward and you can fix anything !    :KS:KS:KS

---


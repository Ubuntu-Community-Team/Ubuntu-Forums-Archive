---
title: "Update Manager Won't Work"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by TerokNor on 2012-10-11
Whenever I try to open it I get this

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 61 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

I have been ALL over the internet ALL day trying to figure out how to fix it and I can't find anything...

---

### Post by zhogan85 on 2012-10-11
Try commenting out line 61 /etc/apt/sources.list

Type the following, and put a # at the start of line 61

```
sudo nano /etc/apt/sources.list
```

Then run 

```
sudo apt-get update
sudo apt-get upgrade
```

And let us know if that fixes the problem. Also, see the link below.

[http://askubuntu.com/questions/101955/e-the-list-of-sources-could-not-be-read-while-trying-to-update]("http://askubuntu.com/questions/101955/e-the-list-of-sources-could-not-be-read-while-trying-to-update")

---

### Post by Bashing-om on 2012-10-11
TerokNor; Hi ! Welcome to the forum.

As there are problems in your /etc/apt/sources.list file, Move it out of the way (keeping copy for general purposes); terminal code:
```
sudo mv /etc/apt/sources.lst /etc/apt/sources.old
```then regenerate the file automagically:
```
sudo apt-get update
```then to update packages:
```
sudo apt-get upgrade
```Try this and advise of any other errors.[INDENT]warm regards <==BDQ

[/INDENT]

---

### Post by TerokNor on 2012-10-11
Maybe I'm completely stupid or something, but neither of those options work for me. I try step one but...You said to put a # in front of line 61 but I see NOTHING that says that..I'm completely confused.

By the way I'm running version 10.04

---

### Post by zhogan85 on 2012-10-11
What do you mean you see "NOTHING"? Do you mean the sources.list file does not exist?

---

### Post by TerokNor on 2012-10-11
When I type it in this is what I get


  GNU nano 2.2.2          File: /etc/apt/sources.list                           




















                                  [ New File ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by zhogan85 on 2012-10-11
Type

```
ls /etc/apt
```

And see if there is a sources.list file.

---

### Post by TerokNor on 2012-10-11
Yes there is

---

### Post by zhogan85 on 2012-10-11
Try opening it again, with nano or a different text editor.  If it is empty,  we'll have to add the sources manually.

---

### Post by TerokNor on 2012-10-11
And how do you open it? I'm sorry, I'm completely new at this.

Okay, wait, I typed in 

sudo nano /etc/apt/sources.list



But it's still blank

---

### Post by zhogan85 on 2012-10-11
Either type
```
sudo nano /etc/apt/sources.list
```
Or type 
```
sudo gedit
```

And once gedit is open, through the file menu, open file, and navigate to the /etc/apt directory and open the sources.list file.

---

### Post by TerokNor on 2012-10-11
Okay I'm there.

---

### Post by zhogan85 on 2012-10-11
Is it blank?

---

### Post by TerokNor on 2012-10-11
Aye

---

### Post by zhogan85 on 2012-10-11
Well it looks like it is blank for some reason. This website will generate what should be in that file, just select the appropriate choices on that link and then paste them into the sources.list file.
[http://repogen.simplylinux.ch]("http://repogen.simplylinux.ch")

Then run the sudo apt-get update command again and report back.

The other option is if this was a new install anyway, try reinstalling.

---

### Post by TerokNor on 2012-10-11
All right I copy and pasted the list then ran it again and it's still blank =(

---

### Post by zhogan85 on 2012-10-11
Where exactly did you copy the sources list from the website? And did you save it?

What exactly was the output when you ran 

```
sudo apt-get update
```

---

### Post by TerokNor on 2012-10-11
How do you save it? 

Um this is what it says

ubuntu@ubuntu:~$ sudo apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg      
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Ign [http://ppa.launchpad.net/webupd8team/java/ubuntu/](http://ppa.launchpad.net/webupd8team/java/ubuntu/) lucid/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release          
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [1,973B]
Fetched 16.3kB in 0s (18.6kB/s)
Reading package lists... Done

---

### Post by TerokNor on 2012-10-11
Oh wait! It's working now!!!

Another question though if I may?

I upgraded to the newest version on a different computer I have and lost the wifi, is that going to happen again?

---

### Post by zhogan85 on 2012-10-11
OK, I think you selected the wrong release from the website (unless you are running 10.04?) Those messages shouldn't say lucid, they should say precise if you are running 12.04.

Run 

```
lsb_release -a
```to verify what release you are running.

If you are running 10.04, then I think you are fixed, and can upgrade your software with the update manager, or from the command line with

```
sudo apt-get upgrade
```

Let me know.

---

### Post by TerokNor on 2012-10-11
Yes I'm running 10.04

I want to upgrade but I did on a different computer and completely lost my wifi so I'm hesitant to do so with this computer

---

### Post by zhogan85 on 2012-10-11
> **TerokNor said:**
> Yes I'm running 10.04

I want to upgrade but I did on a different computer and completely lost my wifi so I'm hesitant to do so with this computer

That is a risk, though with Ubuntu, a minor one. You are running a Long Term Support release, so not updating will be OK. If you want to upgrade to 12.04, the current release (and also a LTS release), the best method would be a new install, as that is 4 versions newer than you are currently running.

If you update and the wifi doesn't work after, just start a new thread here, and I or someone else will try to help you. Start a thread for the machine that has lost wifi already too, and we can try to get it fixed.

But I think your updating problem is fixed. If you are able to update, please mark this thread SOLVED.

Cheers!

---

### Post by TerokNor on 2012-10-11
I'll let you know how it goes. Thank you so much for all your help!!

---

### Post by zhogan85 on 2012-10-11
My pleasure!

---

### Post by NikTh on 2012-10-11
Hi , 
please open a terminal with [Ctrl]+[Alt]+[t] combo keys and copy-paste from here the bellow command. 

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
``` 

Then press [Enter] and copy-paste again the FULL results back here. 
DO NOT FORGET to put the results between the brackets [noparse]```
Here
```[/noparse]

I just want to check your sources.list . (cuz are seemed to me not right). 

Thanks

---

### Post by TerokNor on 2012-10-12
Nope. Took me 3 hours to upgrade and the wifi is gone as I suspected would happen. Please tell me there's a way to fix this!

---

### Post by zhogan85 on 2012-10-12
> **TerokNor said:**
> Nope. Took me 3 hours to upgrade and the wifi is gone as I suspected would happen. Please tell me there's a way to fix this!

I would advise starting a new thread, specifically addressing the loss of wifi, something like "just upgraded, no wifi".

Just to check, run 

```
lsb_release -a
```

to verify what release you are running.

---

### Post by TerokNor on 2012-10-12
> **zhogan85 said:**
> I would advise starting a new thread, specifically addressing the loss of wifi, something like "just upgraded, no wifi".

Just to check, run 

```
lsb_release -a
```

to verify what release you are running.

It says version 12.04 LTS but it also says no lsb modules are available that doesn't sound good. I'll start a new thread though.

---

### Post by zhogan85 on 2012-10-12
OK, well the 3 hours is to be expected as that was a major upgrade you went through.

And regarding the no wifi problem, a quick google search revealed some similar problems. With more details about your specific system I'm sure me or someone else here can help you. But do it in a new thread and mark this one solved.

---


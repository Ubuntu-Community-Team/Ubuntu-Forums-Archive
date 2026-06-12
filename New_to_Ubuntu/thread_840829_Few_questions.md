---
title: "Few questions"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by munja100 on 2008-06-25
I installed Ubuntu yesterday. My first impression is that it's generally faster than Windows (switching between video clips is much slower than in Windows, for example) and that many (maybe too many) things work the same way they do in Windows. However, there are some things that I can't figure out. The problem with Ubuntu is that there is to much help on it, so I can't find my way through it, and even when I read many pages to solve a simple problem, it turns out that solution doesn't work in my case...

1. I can't figure the logic that terminal is based on. For example, I see that many commands are the same as in DOS. So this is what I get when I try to switch directories:

munja100@ubuntu-123321:~$ cd /home
munja100@ubuntu-123321:/home$ dir         
fres  munja100                                    #it's OK so far#
munja100@ubuntu-123321:/home$ cd /munja100        
bash: cd: /munja100: No such file or directory    #no such directory, and yet it is listed in the line above#
munja100@ubuntu-123321:/home$ cd munja      
bash: cd: munja: No such file or directory  
munja100@ubuntu-123321:/home$ cd
munja100@ubuntu-123321:~$ cd /home/munja
bash: cd: /home/munja: No such file or directory
munja100@ubuntu-123321:~$ 

So, on surface it is the same as DOS, and still I can't force it to switch to a subdirectory, whatever logic I apply... 

2. I installed Wine and under it Counter Strike. It really works much faster then in Windows (I have a moderately old computer), but graphics look a little different, and mouse movement is not so smooth. So I unsuccessfully  tried to install graphic drivers from nvidia site. Is it possible to install that drivers with Ubuntu, and if it is, where can I find a tutorial?

---

### Post by Xerp on 2008-06-25
Just do

```
cd ~
``` or ```
cd $HOME
``` :)

The absolute path is:

cd /home/munja100

You forgot the "100" on the end :)

Or, if you want to use two commands:

```
cd /home
``` ```
cd munja100
```

I use EnvyNG to install the Nvidia/ATi drivers for my machines. Its super simple :)

---

### Post by dominiquec on 2008-06-25
Can't speak for your #2, but for your #1, I suggest you look up a good Unix or Linux command line tutorial. [http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/), for example.

---

### Post by wolfen69 on 2008-06-25
munja100@ubuntu-123321:~$ cd /home
munja100@ubuntu-123321:/home$ dir 
fres munja100 #it's OK so far#
munja100@ubuntu-123321:/home$ cd /munja100 
bash: cd: /munja100: No such file or directory #no such directory, and yet it is listed in the line above#
munja100@ubuntu-123321:/home$ cd munja 
bash: cd: munja: No such file or directory 
munja100@ubuntu-123321:/home$ cd
munja100@ubuntu-123321:~$ **cd /home/munja**
bash: cd: /home/munja: No such file or directory
munja100@ubuntu-123321:~$

you could have just did cd munja100

---

### Post by Joeb454 on 2008-06-25
I find ```
cd ~/
``` to be easier to change to the home directory of the current user :) Sometimes I have to do ```
cd ~otheruser
``` to get to the home directory of "otheruser" :)

Bash shortcuts are great things once you learn them :)

---

### Post by iaculallad on 2008-06-25
> **munja100 said:**
> 
1. I can't figure the logic that terminal is based on. For example, I see that many commands are the same as in DOS. So this is what I get when I try to switch directories:

Yes do, same command to change directories with windoze.

> **munja100 said:**
> 
munja100@ubuntu-123321:~$ cd /home
munja100@ubuntu-123321:/home$ dir         
fres  munja100                                    #it's OK so far#


You got that right. That would be the correct way to change directory to your /home since YOU are outside the main directory named **home** where you're user profiles resides.

> **munja100 said:**
> 
munja100@ubuntu-123321:/home$ cd /munja100        
bash: cd: /munja100: No such file or directory    #no such directory, and yet it is listed in the line above#

This time, you got it wrong. You can directly change directory to your **munja100** user directory since it is a sub-directory of your /home directory. Using **cd /munja100** command would translate that it does not belong to your /home directory already, meaning, it's located outside the main directory (/home) you're in.

> **munja100 said:**
> 
munja100@ubuntu-123321:/home$ cd munja      
bash: cd: munja: No such file or directory  
munja100@ubuntu-123321:/home$ cd
munja100@ubuntu-123321:~$ cd /home/munja
bash: cd: /home/munja: No such file or directory
munja100@ubuntu-123321:~$ 


That cannot be possible because you're trying to open a directory that's non-existing (**munja**). When you issue the command ls in your /home directory, it displays **munja100** and not **munja**.

> **munja100 said:**
> 
So, on surface it is the same as DOS, and still I can't force it to switch to a subdirectory, whatever logic I apply... 

On the surface, we could say that both are similar commands but they execute differently. You could try to view what directory you're currently in by issuing the command **pwd** (Print Working Directory) on your terminal.

---

### Post by RomeReactor on 2008-06-25
Hi. Let's take the examples one by one:
> **munja100 said:**
> munja100@ubuntu-123321:~$ cd /home
munja100@ubuntu-123321:/home$ dir         
fres  munja100                                    #it's OK so far#
As you can see, the terminal opens in your home directory. The you issued **cd /home**. By using a slash before 'home' you're telling it to look for a folder named 'home' in the *root directory*.



> munja100@ubuntu-123321:/home$ cd /munja100        
bash: cd: /munja100: No such file or directory    #no such directory, and yet it is listed in the line above#
Here you are in the /home directory; the command you're issuing is telling the terminal to look for a folder named 'munja100' in the root directory (due to the slash before 'munja').



> munja100@ubuntu-123321:/home$ cd munja      
bash: cd: munja: No such file or directory
This didn't work because the correct name of the directory is 'munja100'; pressing TAB as you type autocompletes the name. This would be the correct way to go down the tree, only this time it didn't work because the correct name is 'munja100'.
  


> munja100@ubuntu-123321:/home$ cd
Issuing 'cd' alone will take you to your home folder.

EDIT: Too slow to post...

---

### Post by ksbalaji on 2008-06-25
Just adding one more information to what others have suggested very nicely. ¨cd /¨ means - change to your root directory in the file system, something like cd ¨c:\¨ in windows. You may also use Places>Home Folder from the panel to view the said directory.

---

### Post by munja100 on 2008-06-26
Thank you all for quick and thorough help. I finally managed to find where was the misunderstanding between me and Linux:
```

munja100@ubuntu-123321:/$                    #I'm in the root
munja100@ubuntu-123321:/$ cd home            #switch to home
munja100@ubuntu-123321:[COLOR="Red"]/home$[/COLOR] cd munja100   # I'm now in dir home, which Linux prints (red letters)
munja100@ubuntu-123321:~$ dir                # after I switch to "munja100", Linux doesn't print /home/munja100, so I thought that it keeps directing me to root. Now I see that Linux doesn't always print current address, the way DOS does #
ctrike	 desktop.conf  Documents  Music     Public     test
Desktop  desktop.pci   Examples   Pictures  Templates  Videos
```

@Xerp

I downloaded EnvyNG and it is really user friendly, and does the job. Thanx


p.s. When I started using Windows, I crashed it a few times during the process of learning how it works (for example, I wanted to know what will happen if I delete those files on c:, such as config.sys). Since I'm still very curious, I'll certainly crash Linux too (actually, I was already a few times near to reinstalling, since I didn't know how to reverse changes I made to the system)

---

### Post by django0909 on 2008-06-26
> bash: cd: /munja100: No such file or directory

Remove the colons.... :)

---

### Post by drjonze on 2008-06-26
> **dominiquec said:**
> Can't speak for your #2, but for your #1, I suggest you look up a good Unix or Linux command line tutorial. [http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/), for example.

Great! I've been looking for a good tutorial for linux commands. Thanks!

I've been inspired by another poster in the forum who said he's going to use nothing but command lines for 30 days. I think that's a great idea, an excellent way to learn.

---

### Post by hyper_ch on 2008-06-26
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---


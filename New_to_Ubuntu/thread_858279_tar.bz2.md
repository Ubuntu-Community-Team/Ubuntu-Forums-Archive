---
title: "tar.bz2"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by elzorroviejo on 2008-07-13
Hi, I am having a problem with getting Second Life up and running on my new Linux box. I am running Ubuntu v8.04 over the most recent Linux kernel on a Gateway MX8738 notebook. Here's my problem:

The Second Life package comes as a *tar.bz2* file (specifically  *SecondLife_i686_1_19_1_4.tar.bz2*). When I went to System/help and support on the task bar, it told me to open packages downloaded from individual web sites using  **tar xfvz tarball_name**. However, when I did so, I got this as a repsonse: 
[I]tar: SecondLife_i686_1_19_1_4.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors[/I]
So, what did I do wrong...or what is the correct method for opening tar.bz2 packages? 

Thanks for your help.

Jim

---

### Post by unutbu on 2008-07-13
You need to cd (change directory) to where the tar.bz2 file resides first. When you downloaded SecondLife,
it might have been saved in your home account directory, or perhaps the Desktop subdirectory.

If the tar.bz2 file is in Desktop, then the commands to use are

```
cd ~/Desktop
tar xvjf SecondLife_i686_1_19_1_4.tar.bz2
```

Edit: note xvjf is for tar.bz2 files, xfvz is for tar.gz files. Instead of trying to remember these arcane things, you could do this:

Run 

gedit ~/.bashrc

Add
```

op () {
     if [ -f $1 ] ; then
        case $1 in
                *.tar.bz2)   tar xvjf $1        ;;
                *.tar.gz)    tar xvzf $1     ;;
                *.bz2)       bunzip2 $1       ;;
                *.rar)       rar x $1     ;;
                *.gz)        gunzip $1     ;;
                *.tar)       tar xvf $1        ;;
                *.tbz2)      tar xvjf $1      ;;
                *.tgz)       tar xvzf $1       ;;
                *.zip)       unzip $1     ;;
                *.Z)         uncompress $1  ;;
                *.7z)        7z x $1    ;;
                *)           echo "'$1' cannot be extracted via extract()" ;;
        esac
     else
        echo "'$1' is not a valid file"
     fi
}
```

To the end of that file.
Then, whenever you need to use the command line to open any of the standard archive formats just type

```
op path/to/archive/file
```
Or in this case,

```
op  SecondLife_i686_1_19_1_4.tar.bz2
```

---

### Post by nowshining on 2008-07-13
when u mention most recent terminal do u mean - vanilla from kernel.org or ubuntu kernel? The most recent one as of this post of the linux kernel 2.6.25.11. :)

---

### Post by elzorroviejo on 2008-07-14
I used the quick fix to extract the tarball and it worked just fine. However, I now have the SecondLife folder sitting on my desktop, and I want to move it somewhere less conspicuous...like ./user. But there is a problem: when I try to drag and drop into /usr, I am told I don't have the proper permissions. So, does this mean I have to do it from the terminal? I thought one of the purposes of a GUI was to allow the user to do things like this without having to write code. 

I guess what I really want is for Ubuntu (or Gnome, as the case may be) to allow me super user privileges when I need to do things like move files from one directory to another...

---

### Post by sbassett on 2008-07-14
As far as the all powerful gui, you could add something along the lines of 

gksu nautilus

(right click panel and click add to panel, Custom Application Launcher.)

to your panel. JUST PLEASE remember to always close this out AS SOON AS YOU ARE DONE. You can really mess things up.

Also, you can move stuff off of the desktop to your other folders (Documents, etc.)

---

### Post by nowshining on 2008-07-14
to compile a kernel without being root install fakeroot and add it into the front of the command to install the kernel, etc..

---

### Post by madjr on 2008-07-14
get second life installer here>

[http://getdeb.net/search.php?keywords=second+life](http://getdeb.net/search.php?keywords=second+life)

---

### Post by cariboo on 2008-07-14
You shouldn't try to move the folder to /usr as you haven't installed the game yet If you move it anywhere it should be in your home directory. I have a directory called source where I move all the directories  of programs that can't be installed the normal way. The reasoning behind this, is, that if I ever want to uninstall one of those programs I have the source directory so I can do "make uninstall"

Jim

---

### Post by nowshining on 2008-07-14
caribon why didn't u use checkinstall to create the deb files, :)

```
sudo checkinstall -D make install
```


that way u can install thru apt-get or synaptic.

---

### Post by ChameleonDave on 2008-07-14
> **unutbu said:**
> 

```
ex path/to/archive/file
```Or in this case,

```
ex  SecondLife_i686_1_19_1_4.tar.bz2
```
The problem with that is that "ex" is already a command (a synonym for "vim" by default).

It would be best to choose another name for the function.

---


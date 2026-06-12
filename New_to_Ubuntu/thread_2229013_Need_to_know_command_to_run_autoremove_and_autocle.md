---
title: "Need to know command to run autoremove and autoclean"
date: 2014-06-10
forum: New to Ubuntu
---

### Post by elvis6 on 2014-06-10
I have about zero knowledge on how to run commands from the Terminal, and somehow I was able to find the proper command to install autoremove and autoclean. But I cannot figure out how to actually run them. I tried googling, and I tried typing in "sudo" in front of both autoremove and autoclean, and cannot seem to find the answer.
Could someone provide me the full command on how to run these programs ?
And also provide me with a general help source to get familiar with basic commands in the Terminal ?

---

### Post by Vladlenin5000 on 2014-06-10
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```

Obs.: You don't install either of them as they're options/arguments for apt-get.

---

### Post by elvis6 on 2014-06-10
Ok that's what I typed in originally, and I thought that installed them, but did not run them.
So, are you saying I need to type in that same above command every time I want to clean the system ?

---

### Post by slickymaster on 2014-06-10
> **elvis6 said:**
> Ok that's what I typed in originally, and I thought that installed them, but did not run them.
So, are you saying I need to type in that same above command every time I want to clean the system ?

What do you mean exactly by cleaning the system?

I strongly recommend you to have a read through the man apt-get pages. Run the following in a terminal window```
man apt-get
```

---

### Post by sammiev on 2014-06-10
> **elvis6 said:**
> Ok that's what I typed in originally, and I thought that installed them, but did not run them.
So, are you saying I need to type in that same above command every time I want to clean the system ?

I run this about once every 3 to 6 months.

```
echo "Cleaning Up" &&
sudo apt-get -f install &&
sudo apt-get autoremove &&
sudo apt-get -y autoclean &&
sudo apt-get -y clean
```

edit: Sorry I see  slickymaster replied.

---

### Post by monkeybrain20122 on 2014-06-10
Or get bleachbit

Either from software centre or synaptic or
```
sudo apt-get install bleachbit
```

---

### Post by elvis6 on 2014-06-10
> **slickymaster said:**
> What do you mean exactly by cleaning the system?


I just remember reading somewhere that those functions were recommended maintenance

> **monkeybrain20122 said:**
> Or get bleachbit

Either from software centre or synaptic or


I installed bleachbit previously, but it's a very confusing software to operate for me, as far as understanding the terminology to run it properly, and I cannot seem to find a Help section on it

---

### Post by slickymaster on 2014-06-10
> **elvis6 said:**
> I just remember reading somewhere that those functions were recommended maintenance

I installed bleachbit previously, but it's a very confusing software to operate for me, as far as understanding the terminology to run it properly, and I cannot seem to find a Help section on it

With Ubuntu you do not need to worry with defragmentation because it uses ext4 file system which is less prone to defragmentation.

If you enjoy installing many software packages and applications to test, you may end up with a mass of unused software on your system. While this will not produce substantial slow-down in everyday use, it can be useful to keep Ubuntu as lean as possible for simplicity as well as performance. The default method for removing software is to open the Ubuntu Software Centre, click on the 'Installed' tab near the top and use the 'remove button' after selecting an individual application. A good rule of thumb is to only uninstall applications that you have either installed yourself or are certain are safe to remove, i.e. default programs such as Firefox that you have already replaced with alternatives, as there is some core functionality that can be accidentally removed.

If you have used third-party repositories to install software that you no longer wish to keep, you may decide to remove those repositories to speed up installing and updating via the apt-get command. The safest way to remove these repositories is to open the Dash and type 'Software Sources' and open the program which appears. The Software Sources program has an 'Other Software' tab, which will list all your third-party repositories and has a 'Remove' button at the bottom of the Window. It is extremely important that you are sure that you want to remove the repository in question, you should keep in mind that repositories may have a unusual name and may not reference the software which you used it to install.

As for additional files and cruft which may accumulate on a frequently used and modified Ubuntu system you have autoclean, autoremove and clean functions associated with the 'apt-get'.

---

### Post by elvis6 on 2014-06-10
So, would it be accurate to say that if my PC is still running slow, after doing all of the above, that I either have a virus, or my hardware needs to be upgraded ?

---

### Post by LastDino on 2014-06-11
Likelihood of you getting virus on Linux is far less than me winning marathon, so yeah, post your specs and we could help better.

---

### Post by mastablasta on 2014-06-11
pc doesn+t run slow and wont' get faster by using the mentioned commands. all you would do is free up some disk space and make it "cleaner". sounless you are seriously low on root (/) disk space  you won't benefit much from remove commands.

by the way it is very easy to write short script to run these commands then you make it executable. if you come from ms-dos background it would be similar to creating a batch (.bat) file.

---

### Post by slickymaster on 2014-06-11
> **mastablasta said:**
> pc doesn+t run slow and wont' get faster by using the mentioned commands. all you would do is free up some disk space and make it "cleaner". sounless you are seriously low on root (/) disk space  you won't benefit much from remove commands.

by the way it is very easy to write short script to run these commands then you make it executable. if you come from ms-dos background it would be similar to creating a batch (.bat) file.

+1 on that.

Here is a script written a couple of years ago by a former forum member. You can either use it or grab a few pointers as examples for your own script.```
#!/bin/sh

CUR=$(uname -r)
PREV=$(readlink /vmlinuz.old) && PREV=${PREV#*-} || PREV=@
KEEPKERNELS="^linux-(headers|image|image-extra)-($CUR|$PREV)"
ALLKERNELS='^linux-(headers|image|image-extra)-[0-9]'

YELLOW='\33[1;33m'
RED='\33[0;31m'
ENDCOLOR='\33[0m'

err () echo $RED"$@"
msg () echo $YELLOW"$@"$ENDCOLOR

if [ root != "$USER" ]; then
  err Error: must be root
  msg Exiting...
  exit 1
fi

msg Cleaning apt cache...
apt-get autoclean

msg Removing no longer needed automatically installed packages...
apt-get autoremove --purge

msg Removing old config files...
dpkg --get-selections | sed -n 's/\<deinstall$/purge/p' | dpkg --set-selections
dpkg -Pa

msg Removing old kernels...
apt-get purge "$ALLKERNELS" "$KEEPKERNELS"+

msg Cleaning bash history
rm ~/.bash_history

msg Emptying every trashes...
rm -rf /home/*/.local/share/Trash/*/* >/dev/null 2>&1
rm -rf /root/.local/share/Trash/*/*   >/dev/null 2>&1

msg Script Finished!
```

---

### Post by elvis6 on 2014-06-11
> **LastDino said:**
> Likelihood of you getting virus on Linux is far less than me winning marathon, so yeah, post your specs and we could help better.

Well I'm mainly wondering if I have enough RAM, which is only 496.
Could that be a major slowdown ?

---

### Post by LastDino on 2014-06-11
Ouch! I would think twice before installing even the lowest of all Buntu variants: Lubuntu. Whats the processor? 

Your system needs something as lighter as Bodhi.

---

### Post by Vladlenin5000 on 2014-06-11
Lubuntu and even Xubuntu should be fine (sort of...). You actually have 512MB but 16MB of those have been reserved to act as VRAM (Video RAM) for your integrated graphics chipset. In itself not a bad thing but certainly not good either. The CPU can compensate the other shortcomings but don't expect miracles (they don't exist/never happened anyway). And the bottom line is the bad performance you're probably experiencing is due to an old & limited hardware, not due to something you can "fix" by cleaning the system.

---

### Post by LastDino on 2014-06-11
I would go with the Bodhi rather than Lubuntu though.

---

### Post by mastablasta on 2014-06-12
16 MB GPU and less than 512MB
Xubuntu
Lubuntu
Bodhi
Ubuntu minimal with Windows manager only (e.g with icewm)

if you want to go debian Chrunchbang will give you an easy to setup and low system usage.
another option debian/mepis based and very light is AntiX

if you want to be more up to date try Manjaro (arch based) with XFCE.

---


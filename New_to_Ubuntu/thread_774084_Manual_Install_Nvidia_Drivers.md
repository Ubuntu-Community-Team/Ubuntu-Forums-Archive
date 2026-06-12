---
title: "Manual Install Nvidia Drivers?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by AStaley on 2008-04-29
I've just installed kubuntu 8.04 onto my PC to give it a run and see what it's like, so I'm new to Linux.

I'm looking to install the nvidia drivers from their website, v173.xx which are supposed to fix a few problems with the 2.6xx kernel.

Each time I try to install them I get an error message saying the libc headers are missing, following several guides I've checked my system and they are already installed.

Can anyone give me any pointers as to where I am going wrong with this?  This is my current method;

Drivers are downloaded to desktop.  I'm starting my machine directly into the command prompt so no gui loaded.
I then use sudo sh nvidia-driver.run and it runs through trying to compile stuff for the kernel, which is when it then errors about the libc files.

I need to do this on two machines, one of which has a nvidia 8800gts card in it and Kubuntu doesn't recognise.

Thanks in advance, AStaley.

---

### Post by skymera on 2008-04-29
Ok this is how i install my Nvidia drivers.

```
 sudo apt-get update
 sudo apt-get install envyng-gtk 
```

(i think thats the package name)

After thats installed run Envy from Applications -> System Tools -> Envy

Choose Nvidia and auto, it will download all pakcages needed and update your Xorg.

When you reboot, if you res is wrong run ```
 sudo nvidia-xconfig 
``` from the terminal which should rectify any problems.

Let us know how you get on! :)

---

### Post by thedarkwinter on 2008-04-29
Hi

You are probably missing libc6-dev
```

sudo apt-get install libc6-dev

```

Generally, if you are trying to compile anything, you should run the following to install compiler software and headers

```

sudo apt-get install build-essential

```

And usually, you need to install the kernel headers too

```

sudo apt-get install linux-headers-`uname -r`

```

Remember though, if you are compiling you nvidia drivers (rather than using the packaged version in the repo) you may need to recompile everytime there is a kernel update. This means that you have no X (gnome/kde)... and you will have to do so from the CLI.

Cheers,
thedarkwinter

---

### Post by fs3rp4 on 2008-04-29
> **AStaley said:**
> I've just installed kubuntu 8.04 onto my PC to give it a run and see what it's like, so I'm new to Linux.

I'm looking to install the nvidia drivers from their website, v173.xx which are supposed to fix a few problems with the 2.6xx kernel.

Each time I try to install them I get an error message saying the libc headers are missing, following several guides I've checked my system and they are already installed.

Can anyone give me any pointers as to where I am going wrong with this?  This is my current method;

Drivers are downloaded to desktop.  I'm starting my machine directly into the command prompt so no gui loaded.
I then use sudo sh nvidia-driver.run and it runs through trying to compile stuff for the kernel, which is when it then errors about the libc files.

I need to do this on two machines, one of which has a nvidia 8800gts card in it and Kubuntu doesn't recognise.

Thanks in advance, AStaley.


Go to synaptic. Search the word Nvidia and remove the installed packages.

I recommend installing the Nvidia drivers thought the Ubuntu way...

---

### Post by Calash on 2008-04-29
Envy does not list the 173.xx drivers, and the Ubuntu drivers do not support all the cards.

I know for my 9600 I had to download the 173 to get it working...have to redo it every kernel update as well.

Not sure about the error, but some of the other posts have good suggestions.

---

### Post by AStaley on 2008-04-29
Okay I used envy to install the drivers as per  the 1st reply, and all is working well.

Bit of a pain to setup the twin monitors, Windows is a lot simpler.  Just a difference in methodology to get used to I guess.

Thanks for the assist, AStaley :guitar:

---

### Post by Calash on 2008-04-29
Did you get 173.xx from Envy?  I tried last week and it was not listed.

If so my post is in error, sorry about that.

---

### Post by AStaley on 2008-04-30
I didn't get the 173.xx drivers to install.  But your post was helpfull in that the drivers it downloaded 196.xx did the job I needed.

Thanks for the reply, AStaley.

---


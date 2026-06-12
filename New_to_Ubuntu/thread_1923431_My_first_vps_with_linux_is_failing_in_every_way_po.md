---
title: "My first vps with linux is failing in every way possible"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by artego on 2012-02-10
Ok so I got an ubuntu 11.04 32-bit vps.
I followed this tutorial so I could connect to it with VNC

[http://www.youtube.com/watch?v=i3asugvuyqY](http://www.youtube.com/watch?v=i3asugvuyqY)

Now the problem is I got to connect and the first time I connected not to root but to my account maarten. I got the screen but there was one problem, it said I didn't have enough harware for unity and should use gnome classic. Ok so the first time I got a grey screen.
So I thought no problem, let me just recconect. So I did and I got the grey screen again. After a very long time of waiting I got at my desktop. I didn't have any bars. I tried to find a solution, but before I did I wanted to reboot for some reason. Ok so I keep getting a grey screen now I can access the root via connection too but there the only thing that is somerthimes open is the terminal, and you can't do much else. 

This is a screenshot of how my logged in account still looks after a long time of waiting: [http://www2.picturepush.com/photo/a/7541465/1024/Anonymous/ubuntu.png](http://www2.picturepush.com/photo/a/7541465/1024/Anonymous/ubuntu.png)

---

### Post by savanna on 2012-02-10
Since you're using a vps, you're probably not going to have the resources to run Unity. And really you shouldn't be using a GUI at all - the command line is "where it's at" with Linux - Google on "ssh".

If you're learning Linux, it's probably cheaper and easier to setup a Linux VM on an existing computer - checkout VMWare.

---

### Post by artego on 2012-02-10
> **savanna said:**
> Since you're using a vps, you're probably not going to have the resources to run Unity. And really you shouldn't be using a GUI at all - the command line is "where it's at" with Linux - Google on "ssh".

If you're learning Linux, it's probably cheaper and easier to setup a Linux VM on an existing computer - checkout VMWare.

So I should just keep using putty to do things? and not use virtualisation at all?

---

### Post by Penguinnerd on 2012-02-10
All too often it seems, people who don't know the solution to a problem just tell people to do something else instead of helping them. If someone wants to use VNC, let them use VNC.

Unfortunately, I've never done anything with VNC myself, so I don't know what's wrong. I just thought I'd comment on the recurring issue of people telling others "not to bother" and to try something else instead of helping them achieve their goal.

There's a way to make the VNC work, I just don't know what it is.

Good luck.

---

### Post by CharlesA on 2012-02-10
Sure, they can use VNC, but it's pathetically insecure. FreeNX would be a better solution if they needed remote access to a GUI. It goes over SSH, so it is encrypted. VNC isn't encrypted unless you tunnel it over SSH.

@OP: Are you running a virtual machine or a [Virtual Private Server (VPS)]("http://www.linode.com/") ?

---

### Post by artego on 2012-02-10
> **CharlesA said:**
> Sure, they can use VNC, but it's pathetically insecure. FreeNX would be a better solution if they needed remote access to a GUI. It goes over SSH, so it is encrypted. VNC isn't encrypted unless you tunnel it over SSH.

@OP: Are you running a virtual machine or a [Virtual Private Server (VPS)]("http://www.linode.com/") ?

The cheapest plan of [http://fastvps.co/home.php](http://fastvps.co/home.php)
I bought it just to host files to update my game off. IT has 128 gb ram and 256 burstable.

---

### Post by CharlesA on 2012-02-10
Ok, that answers that.

I would still suggest using FreeNX instead of VNC and see if you have the same problem. I'm not quite sure why a VPS would be running Unity though. If you wanted a GUI, you could have just installed 10.04 and went with Gnome 2/LXDE/XFCE.

If it only has 128MB of memory, I'd go with a minimal install CentOS and use sftp to transfer files back and forth.

---

### Post by savanna on 2012-02-10
Putty is the windows version of ssh. You could use it to connect to *either* a vps or a vm running on your Windows machine.

A "vm" or virtualisation (eg VMWare) is where you run 2 or more operating system on top of your existing o/s. Eg 2 Linuxes on a Windows machine, Windows and Linux on a Mac, etc.

---

### Post by artego on 2012-02-10
> **savanna said:**
> Putty is the windows version of ssh. You could use it to connect to *either* a vps or a vm running on your Windows machine.

A "vm" or virtualisation (eg VMWare) is where you run 2 or more operating system on top of your existing o/s. Eg 2 Linuxes on a Windows machine, Windows and Linux on a Mac, etc.

Yea sorry, with virtualisation I ment watching the screen I connect to. I wasn't really thinking when I posted it.

---

### Post by artego on 2012-02-10
> **CharlesA said:**
> Ok, that answers that.

I would still suggest using FreeNX instead of VNC and see if you have the same problem. I'm not quite sure why a VPS would be running Unity though. If you wanted a GUI, you could have just installed 10.04 and went with Gnome 2/LXDE/XFCE.

If it only has 128MB of memory, I'd go with a minimal install CentOS and use sftp to transfer files back and forth.

It uses 4% memory when nothing is done to it, so that should be engough to transfer files left no?

---

### Post by CharlesA on 2012-02-10
Probably.

---

### Post by artego on 2012-02-11
Ok so I got it working now, The problem is just that it doesn't have enough ram to load much up. It loaded the bar one time but >I can use applications anyways since it can't allocate enough ram. Guess ill have to use the terminal.

---

### Post by artego on 2012-02-11
It uses 6% ram when I am using the terminal and 97-99% when I use vnc plus I heard it isn't secure. Now that I know how to install files with wget and where the www directory is located I won't need the vnc anymore.

---

### Post by CharlesA on 2012-02-12
The www directory should be in /var/www/

Why use wget when you can just use sftp or rsync?

---


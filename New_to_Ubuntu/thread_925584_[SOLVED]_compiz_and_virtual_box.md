---
title: "[SOLVED] compiz and virtual box"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-09-20
i have been dual booting ubuntu with windows vista for a long time now

recently i came across this video where someone has setup a virtual box with its own designated side of the compiz cube

see here
[http://www.youtube.com/watch?v=kQtaFlZuleE]("http://www.youtube.com/watch?v=kQtaFlZuleE")

i think this looks like an awesome idea but i have no idea how to set it up

(ive never used a virtual box)

my first question is performance

i have a gateway laptop with an intel pentium dual @1.47GHz and 1GB Ram

how would the performance of windows XP SP3 (with performance tweaks)  in a Virtual box compare to using vista SP1(no tweaks) as a dual boot?


my second question is where do i start?

does anyone know any good links that could help me get this setup?

---

### Post by Pro-reason on 2008-09-20
They've just run VirtualBox in full screen mode.  In that way, it occupies a side of the cube.

Get the full version of VirtualBox.

Do this in a terminal:

```

gksu gedit /etc/apt/sources.list

```

Add this line to the file:

```

deb http://download.virtualbox.org/virtualbox/debian hardy non-free

```

Save and close.  Do this in the terminal:

```

sudo apt-get update && sudo apt-get install **v**irtual**b**ox
**V**irtual**B**ox

```

Use the GUI to set up a virtual machine, and install XP on it.

---

### Post by ThrobbingBrain66 on 2008-09-20
> **tjwoosta said:**
> 
my second question is where do i start?

does anyone know any good links that could help me get this setup?

If you have a retail version of XP, using [nLite]("http://www.nliteos.com/") will help performance a lot.  I was able to trim XP down to a 1.5 GB base install.  Performance is really good, though not quite as good as a normal installation.

---

### Post by tjwoosta on 2008-09-20
> Get the full version of VirtualBox.

i tried adding the repository you gave me but i get this error when i try to do apt-get update

```

W: GPG error: http://download.virtualbox.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE

```

---

### Post by Pro-reason on 2008-09-20
> **tjwoosta said:**
> i tried adding the repository you gave me but i get this error when i try to do apt-get update

```

W: GPG error: http://download.virtualbox.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE

```

Ah, I should have warned you.

That message is normal, because VirtualBox don't seem to offer a public key.  Just ignore the &#8220;error&#8221;, and proceed to install the program.

Actually, I've just noticed that the repository includes two packages: *virtualbox* and *virtualbox-2.0*.  It appears that they have released a new version.  I'm going to give it a try.

---

### Post by tjwoosta on 2008-09-20
ok 

so i installed it but how do i open it?

i tried just typing virtualbox in the terminal but it says its not installed

also there is no menu entry

EDIT: nevermind it must not have installed correctly the first time, i just reinstalled and now it works


**EDIT AGAIN:**  ok nevermind lol, i still can't figure out how to open it

---

### Post by ThrobbingBrain66 on 2008-09-20
```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

You can download the repo key and register Virtualbox with that command.  It's located at the bottom of this page:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by tjwoosta on 2008-09-20
thanks 

that key worked


but i still cant figure out how to start the virtualbox GUI

also how do i make myself part of the vboxusers group

---

### Post by ThrobbingBrain66 on 2008-09-20
System > Administration > Users and Groups

Unlock it with your password, then click manage groups, scroll to vboxusers, click properties and add yourself.

Virtualbox puts it's launcher in Applications > System Tools.  That menu isn't enabled by default so you may have to edit the menu to show it.  Otherwise, to launch virtualbox from the terminal, you just type ```
VirtualBox
```

---

### Post by tjwoosta on 2008-09-20
yea well i installed the one that pro-reason sugested but it did not make a menu entry

also that command gave me an error saying that i dont have virtualbox installed


so i did sudo apt-get remove virtualbox

then i installed one of the .deb's from the site that ThrobbingBrain gave me and all is working now

---

### Post by tjwoosta on 2008-09-21
ok so now virtual box is all setup

how do i connect to the internet with XP in virtualbox


i figured i would need to plugin the ethernet cord because i dont have the wireless drivers installed in the virtualbox yet, but even with the ethernet cord i still cannot connect


how does that work anyway?

can i use my wireless card in the virtualbox at the same time as Ubuntu is using it?

---

### Post by ThrobbingBrain66 on 2008-09-21
Have you had any luck getting things to work?

VirtualBox sets up a NAT for your virtual machine and uses the host's abilities to connect to the Internet.  Basically, whether you're using a wireless or wired connection in the host OS, your guest OS will show that you have wired ethernet connection.  You shouldn't need to install any drivers; wireless or otherwise.

It seems odd to me that your Internet connection wasn't set up properly after your XP installation.

---

### Post by tjwoosta on 2008-09-21
yea i got the internet working


i did not realize that there were aditional settings that i should setup in the virtualbox manager

i was looking for settings within XP but it turns out that the Virtual box settings are what i needed

the only thing i have left to setup is the screen resolution

i posted my question regaurding the resolution on the virtualbox forums and they said i need to install virutalbox guest additions  (whatever that is)

---

### Post by howefield on 2008-09-21
In your virtual machine window, go to the Devices menu, you'll find the option to install guest additions.

---

### Post by tjwoosta on 2008-09-21
awesome.. thanks


it worked perfectly


now i have the right resolution


the only thing i wish were different is the way i cant change sides on my compiz cube unless i un-capture the mouse

but thats no big deal

---

### Post by howefield on 2008-09-21
> **tjwoosta said:**
> ..only thing i wish were different is the way i cant change sides on my compiz cube unless i un-capture the mouse..

err,..no, if you have installed guest additions you shouldn't have to capture/uncapture the mouse.

---

### Post by ThrobbingBrain66 on 2008-09-21
> **howefield said:**
> err,..no, if you have installed guest additions you shouldn't have to capture/uncapture the mouse.

Unless he has Vitualbox in fullscreen mode.  In that case, the keybindings to rotate the cube won't work.  As a work around, I set up Compiz so that I can move my mouse to either edge of the screen and right-click to spin the "cube".  I only use two sides...one of Ubuntu and the other for XP.

---

### Post by tjwoosta on 2008-09-21
yea i am using it in fullscreen mode because if i set it to seamless mode then AWN covers my windows start bar

i dont really like the way the cube rotates when you move the mouse to the edge so what i did as a workaround is disable the auto-capture mouse from the menu in virutalbox

that made it so i can hit the right-ctrl to uncapture the mouse, after uncapturing the mouse the key-bindings work for the cube (ctrl-alt right mouse button)

---


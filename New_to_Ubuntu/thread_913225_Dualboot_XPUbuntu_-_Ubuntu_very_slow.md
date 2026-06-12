---
title: "Dualboot XP/Ubuntu - Ubuntu very slow"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by OnsMa_Gianni on 2008-09-07
Hi ever1

I have another question. I have a 2.8Ghz and 1024MB RAM desktop wich is running a dualboot with XP/ubuntu.

Whilst using XP, my pc works flawlessly and at good speed. But when I boot in Ubuntu, it works very very slowly and jams constantly(boot process very slow, much slower than XP and Firefox-crashes and so on). Does any1 have any suggestions on where that problem can be situated? I am a Ubuntu noob.

Also, programs that I installed (wolfenstein ET and VMWare) are installed, but they won't start. I suspect these problems are related, since if i try running wolfet thru terminal, it sais (received signal 11, exiting) and nothing further and VMWare gives me an error which in short sais that there's something wrong with my linux kernel and that it failed building a new one.

A friend of mine is running OpenSuse and he's pretty satisfied about it.

In short, so far not really a big Ubuntu-fan yet.:(

BTW I ordered 2Gib of RAM

Thanks in advance for your replies

Greetz Gianni :guitar:

---

### Post by diwas on 2008-09-07
Well...did u download the "official ubuntu iso" from the site? (ubuntu.com)
Or is it one of the many hacked version?

---

### Post by OnsMa_Gianni on 2008-09-07
It's an "official one". i downloaded it thru a link in this forum, burned it to a cd and installed it whilst selecting "install ubuntu inside windows".

Greetz Gianni

---

### Post by diwas on 2008-09-07
"install ubuntu inside windows" where do u get that?? I mean is it the xact line of wat u get...or an xpression?
If its the line, at which point do u get it?

---

### Post by Xiong Chiamiov on 2008-09-07
> **diwas said:**
> "install ubuntu inside windows" where do u get that?? I mean is it the xact line of wat u get...or an xpression?
If its the line, at which point do u get it?
That's from [Wubi]("http://wubi-installer.org/").

---

### Post by OnsMa_Gianni on 2008-09-07
If you run the cd from windows it gives you 3 options.

1. test and install
2. install inside windows
3. others

If I remember correctly.

Greetz Gianni

---

### Post by kjohansen on 2008-09-07
so are you dual booting or did you install ubuntu through wubi or a virtual machine?

if you are running ubuntu through wubi or through a virtual machine it is going to be slow since you are running an operating system ontop of an operating system.

if you use a pure dual boot where they are seperate you will have a better ubuntu.

---

### Post by Xiong Chiamiov on 2008-09-07
Wubi does not run Ubuntu as a virtual machine.  It allows you to boot up Ubuntu by itself; the difference is that the files themselves are stored on the Windows partition, and you can uninstall it through add/remove in Windows.

To the OP:
Do you have Compiz turned on?

---

### Post by OnsMa_Gianni on 2008-09-07
When i boot, i can choose between xp and ubuntu. I have 3 partitions, 1 windows, 1 ubuntu and 1 data.

I don't know wether or not it is Wubi, it didn't say. 

Greetz Gianni

---

### Post by diwas on 2008-09-07
Xactly...i did suspect virtual OS...but >  Dualboot XP/Ubuntu - Ubuntu very slow clearly says dual boot...and i dont remember that line, u know! hehe

So yes, are u dual bootin or is it the virtual one?

---

### Post by diwas on 2008-09-07
> **Xiong Chiamiov said:**
> Wubi does not run Ubuntu as a virtual machine.  It allows you to boot up Ubuntu by itself; the difference is that the files themselves are stored on the Windows partition, and you can uninstall it through add/remove in Windows.



Sorry, i ddnt know that!! Thank you!

---

### Post by OnsMa_Gianni on 2008-09-07
> **Xiong Chiamiov said:**
> Wubi does not run Ubuntu as a virtual machine.  It allows you to boot up Ubuntu by itself; the difference is that the files themselves are stored on the Windows partition, and you can uninstall it through add/remove in Windows.

To the OP:
Do you have Compiz turned on?

It is installed in the synaptics manager. But i don't know wether or not it's on. how do i check that?

Greetz Gianni

---

### Post by OnsMa_Gianni on 2008-09-07
A good example about the slowness, when i scroll down in a thread, my music stops playing until it's loaded. It does that when I start a program, click on a thread in the forum, etc.

Greetz Gianni

---

### Post by paul101 on 2008-09-07
right, instead of quibbling over partitions and whether ubuntu is installed via wubi, lets try to get a solution.

Go to System > Preferences > Appearance

In Appearance Preferences select the Visual Effects tab. 

Then, select "none"

---

### Post by Xiong Chiamiov on 2008-09-07
It would also be helpful to know what kind of video card (if any) you have.

---

### Post by OnsMa_Gianni on 2008-09-08
I am dualbooting. I have experience with virtual machines, but even when ubuntu is in a virtual machine inside windows, it works much better and faster than this way

Greetz Gianni

---

### Post by ronnielsen1 on 2008-09-08
The compiz and all that shouldn't matter. Ubuntu should fly on that box. He's got 1G of ram. I'd be more inclined to think he's running under windows

---

### Post by PierreDeKat on 2008-09-08
Because your Ubuntu is installed on your Windows partition -- NTFS (?) and not a native Linux partition, BTW -- it is subject to fragmentation issues associated with Windows partitions in general. So defragmenting your Windows partition could help.

But I myself would go the route of reinstalling Ubuntu on a native Linux partition, if for no other reason than the fact that Ubuntu only does a fair job of dealing with NTFS files. There are a few bugs that show up from time to time, even when you have everything set up the best that they can be set up.

And then there's always the possibility that Windows has trashed one of your Ubuntu files. It certainly wouldn't be the first time that Windows trashed a file that it had ready access to.

I would start with a fresh install on a native partition, see where that gets you, and address the possibility of a hardware issue later, if you're still having problems.

---


---
title: "First Package and Synaptic"
date: 2017-09-01
forum: New to Ubuntu
---

### Post by electrosteam on 2017-09-01
I used a Windows XP machine connected to the internet (online) to download a Lubuntu iso image onto a USB and installed Lubuntu on an old Dell laptop not connected to the internet (offline), no dramas at all.

The offline machine is destined for CAD duties and I would like to install a Cad package, librecad.
Got a librecad.deb file via the online machine, together with a text list of dependencies, onto a USB stick.

Opened Synaptic Package Manager on the offline machine and pointed it at the .deb file.
Synaptic shows the .deb file in ghost-out form, will not mark it or open it.
The file manager reads the file Ok.
I expected Synaptic to open/use the .deb file in some way, realize there were dependencies and stop with error messages, I got nothing.

I started in on downloading the various dependent files using the online machine, but the bewildering range leaves me stunned.

Just requesting a couple of pointers to what I should do, terminal commands are Ok.
Should I have got error messages from Synaptic ?
Do I just need to read further on how to use Synaptic ?
Is there a 'smart' way to acquire the dependencies ?

The offline machine will eventually be connected to the net, but I figure this is a good learning opportunity.

John

---

### Post by Autodave on 2017-09-01
Is it possible to do what you want? Possibly. But I would never want to try it. You are talking about a *huge *amount of work. Get it hooked to the internet: even if only for awhile and get what you need. Soooooo much easier.

---

### Post by Bucky Ball on 2017-09-01
> **Autodave said:**
> Get it hooked to the internet: even if only for awhile and get what you need. Soooooo much easier.

+1. You are trying to catch fish with a chopstick at the moment. Rather than a Ubuntu learning curve, more like a lesson in frustration. You are not going to learn much by this exercise except about how to find needles in a haystack.

If you get online, double click that .deb file, appropriate dependencies will be found, downloaded and installed and all done in a jiffy.

Then you can get on with enjoying your Linux learning curve. What you're trying to do now, finding and installing required dependencies, is boring, repetitive graft that a machine can do much quicker. There may be hundreds of required dependencies, some/many of which may only be available online anyway (which means you will need to get on an online machine, download, transfer to offline machine, etc.). :)

(PS: Synaptic is pretty useless if you don't have the dependencies already on the machine somewhere, as you've probably discovered. It will go onlines and look for them, but in your case, can't. Another tip: if you install Gdebi, you can simply double click the file and Gdebi will open, find dependencies and install.)

---

### Post by wheatpenny2 on 2017-09-01
Also, I just checked and LibreCad is in the Ububtu software repository, (I've never tried Lubuntu, but I assume all the flavours have the repository), so the easiest thing to do would be to find it in the repository and install from there.

---

### Post by again? on 2017-09-01
You could try the method I outlined [**HERE**]("https://ubuntuforums.org/showthread.php?t=2369249&p=13678751#post13678751").
Just substitute your package for "lsb" used in the link.

---

### Post by linuxissuperawesome on 2017-09-02
Try Going To Where You Downloaded The.deb File And Try 

```
sudo dpkg -i <filename>
```

You Seem To Be In A Jam In Any Case.:(
If You're Desperate You Can Boot-up A LiveCD (On The Networked PC) And Run The Below Code

```

#Make Sure You Don't Install Any Other Application On The LiveCD
sudo add-apt-repository ppa:librecad-dev/librecad-stable
sudo apt-get update
sudo apt-get install librecad
sudo pcmanfm #Root File Manager

```

Then , Using The File Manager Navigate To ```
[COLOR=#242729][FONT=Consolas]/var/cache/apt/archives
``` And Copy All The Files There To A Pendrive And Move The Files To The Laptop And Install Them.
[/FONT][/COLOR]Good Luck!:guitar:

---

### Post by oldos2er on 2017-09-02
> **linuxissuperawesome said:**
> Try Going To Where You Downloaded The.deb File And Try 

```
sudo dpkg -i <filename>
```

Or Try This

```

sudo add-apt-repository ppa:librecad-dev/librecad-stable
sudo apt-get update
sudo apt-get install librecad

```

The add-apt-repository command isn't going to work without an internet connection.

@electrosteam Synaptic doesn't work with local *.deb files; it's a limitation of the program and not anything you're doing wrong. I agree with the recommendations to try to get an internet connection for the computer, it will make things so much easier in the long run.

---

### Post by electrosteam on 2017-09-02
Thanks for the comments and good advice.
I will try today to get Firefox running with a cable to the modem.
John.

Edit: Firefox up and running, librecad tar.gz file downloaded from Github and installed on desktop.
 Not quite running, getting an error message about invalid path, perhaps the desktop was a poor choice.
Thanks

Edit: Librecad removed and re-installed - all good, very happy.

---


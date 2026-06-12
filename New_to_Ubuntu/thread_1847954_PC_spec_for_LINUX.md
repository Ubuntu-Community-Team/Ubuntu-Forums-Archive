---
title: "PC spec for LINUX?"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by JellyDust on 2011-09-21
Hi all

Complete and utter newbie here who's been using Windows for as long as I can remember, so be gentle with me...  :)

I'm wanting to set up a test environment for learning PHP so am looking to set up a Linux server. I've got an ancient old PC that's got a Pentium II processor in it. My first question is basically, is it at all feasible to do this or should I start with a more powerful piece of kit? From what I can see, the normal Ubuntu installation needs at least a Pentium 4 but doesn't the Server version work on a lesser spec?

Thanks

Darren

---

### Post by MG&amp;TL on 2011-09-21
As a test for a server, fine. If you actually intend to use it as a server, get something bigger.

Linux will run on ANYTHING that's made out of silicon. As far as I can tell, anyway. I have a *floppy disk* with the linux kernel on and a command-line. So I don't think there's a minimum requirement.

---

### Post by doppel.ganger on 2011-09-21
Cool! Can you tell me how to get the Linux Kernel 3.0 on a CD for emergency purposes?

---

### Post by mörgæs on 2011-09-21
If you want to run a headless server (no GUI) you can run on almost anything. Installation might take a while, though.

With more than 512 MB memory you can run Ubuntu with a GUI. If less then Xubuntu or Lubuntu are better choices.

---

### Post by quadproc on 2011-09-21
Recent versions of Linux require that the CPU support the CMOV instruction; this instruction did not exist until sometime during the 686 era.  If your processor doesn't do cmov then you would need an older version of Ubuntu.

quadproc

---

### Post by MG&amp;TL on 2011-09-21
doppel.ganger, JUST a kernel won't do much. Just sit there managing your system. You need a shell as well.

For emergencies, I use Puppy linux on a cd. [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

For DIRE emergencies, I use TOMSRTBT Linux on a floppy.

[http://www.toms.net/rb/]("http://www.toms.net/rb/")

---

### Post by JellyDust on 2011-09-21
I have to say, most of these replies are baffling me! :)

Am currently attempting to install the Ubuntu Server on the PC. It's already getting further than my first attempt (I was trying to install Kubuntu but it just got errors and was sluggish as hell..)

---

### Post by MG&amp;TL on 2011-09-21
KU-buntu on a PentiumII?? :shock: no wonder...Kubuntu is designed to be pretty and heavy. Not on a pentium. ;)

---

### Post by JellyDust on 2011-09-21
> **MG&TL said:**
> KU-buntu on a PentiumII?? :shock: no wonder...Kubuntu is designed to be pretty and heavy. Not on a pentium. ;)

Yeah, forgive my ignorance, I was following this page that I found via Google search... :)

[http://www.linuxjournal.com/node/1005985](http://www.linuxjournal.com/node/1005985)

:popcorn:

---

### Post by MG&amp;TL on 2011-09-21
"Complete and utter newbie"....Ubuntu server might not be for you...it's a command-line. Which isn't very helpful oftentimes.

Try lubuntu instead, you should still be able to install same packages as Ubuntu server has already.

[http://lubuntu.net/]("http://lubuntu.net/")

---

### Post by MG&amp;TL on 2011-09-21
Previous versions of KDE (Kubuntu) have been MUCH lighter, so the guy may not be mistaken...just out-of-date.

---

### Post by JellyDust on 2011-09-21
> **MG&TL said:**
> "Complete and utter newbie"....Ubuntu server might not be for you...it's a command-line. Which isn't very helpful oftentimes.

Try lubuntu instead, you should still be able to install same packages as Ubuntu server has already.

[http://lubuntu.net/]("http://lubuntu.net/")

Ok, will do.

Ubuntu is practically installed now. Will I need to wipe my hard drive and start again with Lubuntu?

---

### Post by JellyDust on 2011-09-21
Bah, I'm getting nowhere here. I'm trying to install Lubuntu now and it's telling me that I don't have a "cmov" feature present on my CPU and to use an appropriate kernel.

](*,)

---

### Post by mörgæs on 2011-09-22
Then I guess you are better off discarding the gear. A 3-4 years old computer should not cost you much, and the speed compared to a 13-14 years old one (like the present)...

If you still want to experiment, here are some light alternatives: [http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027) 
I don't think many of them run without CMOV, though.

By the way, are you aware that you can build PHP on any kind of computer? It does not have to be a dedicated server.

---

### Post by technosysind on 2011-09-22
I think if you are new to Linux, Server is not for you right now. Maybe first get acquainted with basic linux commands and operations and then go for the server version.

Just a suggestion!!

---

### Post by Jagoly on 2011-09-22
although tasksel on ubuntu server automates alot of things.

---

### Post by mastablasta on 2011-09-22
hmm if it doesn't run on 586 processor then why the requirements says that server verison works on 
 
300 MHz x86 processor 
 
also i would say go with 10.04 for server

---

### Post by JellyDust on 2011-09-22
Thanks for all the replies so far folks :)

Just to clarify where I'm coming from, I've been doing quite a bit of work learning PHP from scratch recently and have made a lot of headway using the EasyPHP software installed on my Windows 7 PC so, that's not a problem.

I've always been interested in having a go at Linux purely because I've never used it before and want to see what it's all about. I also at some point in the future want to be a bit adept at doing LAMP development so this seems like a good time to start on the long road towards it.

So, to clarify, if I go away and get a slightly more powerful PC and start again by installing Ubuntu on it, will I then at some point be able to start adding on all the "Server" software so I can start building a home network (or even a server that can be accessed by anyone on the internet)?

cheers

---

### Post by MG&amp;TL on 2011-09-22
Sure. As I understand it, all the server packages can be installed on regular ubuntu/other variants thereof.

It's just not recommended to have a desktop, so Ubuntu server doesn't. If you want one, you can always

```
sudo apt-get install <desktoppackage>
```

or whatever.

So, two choices:

1. Get Ubuntu server, add a GUI.
2. Get regular Ubuntu/Xubuntu/Lubuntu, get the server packages.

Hope this is what you are after. :)

---

### Post by mörgæs on 2011-09-22
If you are new in Buntu, go for a Xubuntu 11.04 or Ubuntu 10.04 desktop installation. When that works we can add server packages.

Running a headless server is not recommended as a first step.

---

### Post by perspectoff on 2011-09-22
You will spend far more time trying to set things up on an outdated computer than it's worth. Your time would be better spent begging for quarters on a street corner to afford a $75 686 computer which can run Ubuntu Lucid 10.04.

A noob should never start with a command-line system (only datacenters should use command-line servers these days, IMO). All the server packages can be installed quickly and run with the regular desktop version of Ubuntu.

I went the road you are suggesting and would never do it again. Heck I even installed DSL (Damn Small Linux) and Puppy (before it changed to Ubuntu). Not worth the effort.

Besides, as this very thread indicates, Linux kernels are not uniform. While "Linux" can "run on any machine", not every kernel (version) of Linux can run on every machine. You can spend a lot (!) of time finding out which kernel of Linux will run on your machine and that is only by trial and error. You can get grey hair doing that (and then eventually become an Ubuntu Forums greybeard regular, giving rather arcane advice, lol).

Besides, most PHP programming is done with the GUI user experience in mind. How are you going to test that unless you have a GUI environment?

Ok, so you're an 11 year old kid whose parents won't give you money for a computer. Ask grandma or something.

Further, if your intent is to learn server dynamics for datacenter deployment, you'll want to have hardware that can support the extensions for virtual machines, etc. Older hardware has none of that. 

Lastly, schools get donated computers all the time. (Even though schools are underfunded, companies dump slightly used computers on schools aplenty). You can often pick up a 3 year old computer from a school because they've just gotten a load of 2 year old computers from some company. Ask your school's IT advisor.

---

### Post by technosysind on 2011-09-22
Perspectoff is very right.  Maybe too straight forward but he has hit the nail on it's head....;)

---

### Post by JellyDust on 2011-09-22
cheers guys, stay tuned for my next attempt! :)

---

### Post by quadproc on 2011-09-22
I had an old computer which I could have either scrapped or used as a standby machine so I chose the standby approach.  My first attempt was Xubuntu; it was incredibly slow and most applications would crash.  Later, i found Puppy Linux and found that it works well on that 256 MB system.

There is one very important consideration with Puppy Linux - it is a single user system and that user, of course, is root.  It would not be appropriate for your intended purpose.

quadproc

---

### Post by JellyDust on 2011-09-26
Hi again folks, OK, I've gotten hold of a better PC with a Pentium 4 processor and 1GB of Ram. I'm installing Ubuntu at the moment and it seems to be firing up all fine now.

So, can someone point me in the direction of getting some software so I can start the process of turning this into a server?

cheers :)

---

### Post by mörgæs on 2011-09-26
Maybe - if you tell which kind of server you would like to run.

---

### Post by JellyDust on 2011-09-26
Well, I'd like to start with something that can run PHP and MySQL so I can physically host test sites and develop them at home....

---

### Post by mörgæs on 2011-09-27
```
sudo apt-get install tasksel

sudo tasksel install lamp-server
```

---

### Post by HermanAB on 2011-09-27
Hmm, you should be able to get a half decent computer for free or almost free (like $50) at your municipal dump or recycling centre.  Every town with more than two horses or wind mills has one!

---

### Post by mörgæs on 2011-09-27
1 GB memory is fine for LAMP, especially if you pick Xubuntu and not Ubuntu.

---


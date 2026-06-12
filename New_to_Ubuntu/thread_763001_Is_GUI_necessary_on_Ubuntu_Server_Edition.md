---
title: "Is GUI necessary on Ubuntu Server Edition"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by sampaguy on 2008-04-22
I am completly new with linux so please bare with me. I have read great threads from experienced ubuntu users saying that my server will not be as productive if I install the desktop gui version on ubuntu server edition. Needless to say I installed it (I dont know any linux commads)and added gui version. It was very simple. I hosted website and was able create network in my home. ( I set up my server evolution as well) My question is why the recomendation to not use gui? are there limitations and if so what are they. I appreciate your help.

---

### Post by Oldsoldier2003 on 2008-04-22
> **sampaguy said:**
> I am completly new with linux so please bare with me. I have read great threads from experienced ubuntu users saying that my server will not be as productive if I install the desktop gui version on ubuntu server edition. Needless to say I installed it (I dont know any linux commads)and added gui version. It was very simple. I hosted website and was able create network in my home. ( I set up my server evolution as well) My question is why the recomendation to not use gui? are there limitations and if so what are they. I appreciate your help.

there is no need to install a gui in the server edition. Some people may find it to their liking to install the Gui, but by default, the server edition is meant to be run in the "headless" mode. meaning without a monitor and keyboard attached. Noramlly you would access the server by SSH for administration, or install and use a web control panel such as ISPadmin.

With all that siad its entirely up to you. The gui really doesn't add anything to a server setup, but may ease the learning curve.

---

### Post by Joeb454 on 2008-04-22
It's because the GUI uses up extra CPU cycles, and RAM, which could - quite obviously ;) - be used by the server for other tasks.

If you want a server but aren't confident with the CLI, then installing the desktop is *definitely* the way to go :) If you read my server specs (below) you'll see why I just stuck with the CLI ;)

1Ghz Intel P3, 256Mb RAM, 20Gb HDD - It's an active LAMP server with Samba on the side ;) Works fine :D

---

### Post by Confuzius on 2008-04-22
I'm pretty sure the reason people reccomend running the server without the GUI is simply to get the most possible out of your resources.  If you don't mind your server taking a hit on the ammount of available RAM and Processor speed then it shouldn't be a problem running the GUI.

---

### Post by Shiva88 on 2008-04-22
There's only two reasons to not run a GUI, afaik.  First, it's unnecessary, since you can accomplish everything and more through the CLI that you could through the GUI.  Second,  having the GUI running all the time sucks up resources that (theoretically) can be better used for other server-type things.  Other than consuming those resources, there aren't any "limitations" that I'm aware of. 


Oh, and using the GUI will probably limit/slow your learning of the command line.  In fact, that's probably the biggest drawback, now that I think about it.

---

### Post by sampaguy on 2008-04-22
Thank you all for fast replies. I kind of get the feeling it has to do within system resources being sucked up. My machine did fine with gui and I will keep learning it more, I think as soon as I feel a little more confidednt I will start learning it on CLI only. Once again thanks for prompt replies.

---

### Post by mlentink on 2008-04-22
Just compare the two. You will find that the GUI takes up an inordinate amount of resources, that could much better be used for server processes. If you are looking for an easy way to administer your server, look for a tool like Webmin, which takes up just a little bit of space and allows you to administer your server from any computer in your network.

---

### Post by theDaveTheRave on 2008-04-22
SampaGuy.

I'm no guru but here is my take on your question.

A server should only really be "serving" requests for information from remote machines.

There shouldn't really be any need to have a GUI interface for administration purposes as they are all relatively easily done via the command line (eg adding users, changing permissions, adding shares, access to printers).

I can understand however that a nice GUI can make things feel more "normal". As you become more "happy" with the maintenance / admin of the system you should try to learn the command to perform the same actions (they are less prone to variations).

As an example, there are many different ways within windows to add new users - you can do it via the management console or navigate your way to the same info via the "my computer". Using the linux command prompt means you can perform the task in a fraction of the time, without any issues of worrying if the OS has put in some "unwanted" setting on the user profile.

Modern servers are often designed with the idea of focusing their energy on  the service they are most often serving. Also unless you are using your terminal as a "working terminal" and running the server underneath you probably don't require the level of resources to run a GUI.

Personally I am trying to set up and "old" 386 as a mail and print server, the only problem is getting the wireless key to work, so I can access the printer remotely! I have thought of the idea of using a VNC to access the server from remote sites but I'm not sure how useful that will be... and I haven't really had the time to get it set up properly yet either!

a little amusing story to highlight the issue with any server.

A large computer company was hired to establish a network within a new office for a client.

The office was still "under construction" and reasonably sensibly they adde all the required cabling etc before the decorating was complete, and added in the main server and router boxes etc. Tested the system with a few terminals to ensure that everything worked as they had expected. Success it did - everyone was very happy.

So the full move of the client into the new office didn't occur for another few weeks, whilst furniture was acquired and all other required equipment was installed.

When the first workers arrived at their desks with the computers and plugged them into the network ports nothing worked, no netword access to printers, shared drives etc... but just a few weeks prior everything was "working". The engineers couldn't even gain access to their lovely shiny newly installed adaptive servers, everyone was scratching thier heads.

So after a while an engineer was sent to the server room, and there was the server. Happily whirring away with the Windows "flying toasters" screen saver. All the lights and dials suggested that the system was working as it should and so the engineer logged in to the server whilst sat in front of it.

After running a few "diagnostic" tests and reading some log files engineer noticed that the server was running at 99.9% capacity. But only he was logged onto the network.

He checked the running services and there was him, and the screensaver!

He realised that the adaptive server software was giving resources over to the process that was being used the most and as such was serving the screensaver will all it's processing power! and nothing else could jump over it unles they moved the local mouse.

That is one reason not to have a GUI running, eventually if there is no activity the server will decide that the local GUI is the most important thing that it is running and give more and more processor time to it.

---

### Post by stream303 on 2008-04-22
I love the cli - but in some cases, depending on your hardware, a very light gui that runs nothing but terminals can come in handy.

The lcd monitors on Apple iMacs for instance in a pure cli mode, don't look that great, and unless you have excellent eyesight, it can produce a bit of strain if you spend a lot of time behind the monitor.

Sometimes a super-light build of nothing more than xorg and xterm and a very light window manager could be useful.  I tend to favor LWM as my window manager in this case.  You can build up a very tiny gui system here if you want:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by hums07 on 2008-04-22
I installed Dapper server editon and a lightweight GUI, i.e. IceWM and it said the computer had about 60 processes running. Then I installed xubuntu desktop, and now when I go to IceWM session it says the computer has about 130 processes running.
This proves that GUI swallow resources a lot.

---

### Post by Joeb454 on 2008-04-22
> **stream303 said:**
> The lcd monitors on Apple iMacs for instance in a pure cli mode, don't look that great, and unless you have excellent eyesight, it can produce a bit of strain if you spend a lot of time behind the monitor.


Actually, I never log onto my server locally, I admin it through ssh all the time. All that's connected is a power lead, and an ethernet cable.

So the font size isn't an issue, it's just a terminal open on my laptop :)

---

### Post by Frequent Modulation on 2008-04-24
> **Joeb454 said:**
> Actually, I never log onto my server locally, I admin it through ssh all the time. All that's connected is a power lead, and an ethernet cable.

So the font size isn't an issue, it's just a terminal open on my laptop :)

hey joe, can ssh be used with windows xp as the client? is there something i can read to learn more about ssh (ive read the wiki)...

---

### Post by Joeb454 on 2008-04-24
If by client you mean connect to your Ubuntu server from a Windows XP machine...yes

**BUT**

You will need to install something such as Putty to do so, as Windows doesn't support ssh by default. Google is your friend on this one, I'm sure there are plenty of free ssh utilities out there for Windows :)

---


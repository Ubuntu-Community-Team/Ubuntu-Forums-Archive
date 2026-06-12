---
title: "Reboot Ubuntu using a site"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by Yves_W on 2013-08-01
Hiya,

I'm not sure wether this is the right section for such topic, but my knowledge of Ubuntu isn't that great, so I thougth it was appropriate. I'm running a Teamspeak 3 server on a Ubuntu 12.04 server (128MB). Sometimes the TS3 server crashes (I couldn't find anything important in my mail, just something with appache2), so I wanted to give my TS users the ability to restart the Ubuntu server. Teamspeak automatically starts when my Ubuntu server starts, because I added

```
sleep 5
su teamspeak -c '/home/teamspeak/teamspeak/ts3server_minimal_runscript.sh inifile=ts3server.ini' &
```

to my * /etc/rc.local*.

I don't want to give them my root password though and tell them to use SSH, because none of them knows how to use it and there's a chanche that they screw something up. So I wanted to make a webpage that they can visit that makes the Ubuntu server execute the command *sudo reboot*. Do you guys know any way how to do that?

Thanks in advance!

---

### Post by matt_symes on 2013-08-01
Hi

First i should say that i have absolutely no experience with Teamspeak at all.

Second, please don't give reboot capability for a server via a web page over the internet. I would also seriously question it over an intranet as well.

Why have you added Teamspeak to rc.local ? I assume you are following some tutorial like this ?

[http://forum.teamspeak.com/showthread.php/74883-TUTORIAL-Teamspeak3-Server-w-MySQL-Databse-on-Debian-Ubuntu](http://forum.teamspeak.com/showthread.php/74883-TUTORIAL-Teamspeak3-Server-w-MySQL-Databse-on-Debian-Ubuntu)

I would investigate using upstart to start Teamspeak as that can respawn processes that crash or stop.

It looks like this person as already started looking at the idea.

[http://forum.teamspeak.com/showthread.php/68553-upstart-init-scripts](http://forum.teamspeak.com/showthread.php/68553-upstart-init-scripts)

Kind regards

---

### Post by Yves_W on 2013-08-01
Hm, would giving them that ability be such a problem? Well, I added it to rc.local because that was the easiest way to make it bootable. The problem with using upstart is that I'm not sure what exactly happens when the server doesn't work anymore. Does Teamspeak crash, does MySQL crash, does the internet crash for a second etc.?

---

### Post by matt_symes on 2013-08-01
Hi

> **Yves_W said:**
> Hm, would giving them that ability be such a problem? Well, I added it to rc.local because that was the easiest way to make it bootable.

I was thinking of the security considerations and implications of allowing server reboot via a web page.

> The problem with using upstart is that I'm not sure what exactly happens when the server doesn't work anymore. 

What exactly do you mean by this ? What currently happens when the "sever doesn't work anymore" ?

Are you talking about a kernel crash, loss in network connectivity (locally or to the internet), daemon or process crash ?

Are you talking about a hardware, or software failure ?

Why do you currently have to reboot your server ? Is it just Teamspeak that is going down or is something far more serious happening ? 

When teamspeak stops working, can't you just restart it as a process ? 

> Does Teamspeak crash, does MySQL crash, does the internet crash for a second etc.?

Only you can answer that at the moment as you need to specify exactly what is happening to your server when things crash.

Personally, I would much, much prefer to try and restart a crashed process on a server (including any cleanup that may be required to do so) than allow anybody (even if they are trusted users) to restart the server. 

Why is Teamspeak crashing in the first place ? Do you know ?

Kind regards

---

### Post by Yves_W on 2013-08-01
Hm, I don't care that much at giving them that right, looking at security reasons. The server just goes down; the VPS is still reachable. Hm, guess I gotta look if TS makes logs.

---

### Post by matt_symes on 2013-08-01
Hi

If the VPS is still reachable and it's just the teamspeak server that has gone down then....

What i would try to do first is to identify why Teamspeak is crashing.

After that i would look at using upstart and init scripts to spawn/respawn the Teamspeak process.

I would really, really try to disuade you from putting a reboot button on a web page. 

I think it's not the best way to do what you are trying to achieve, but if you really need to; after having a quick glance at this page, i think it's what you should investigate.

[http://stackoverflow.com/questions/2794505/creating-a-php-web-page-that-enables-you-to-reboot-the-server-in-linux](http://stackoverflow.com/questions/2794505/creating-a-php-web-page-that-enables-you-to-reboot-the-server-in-linux)

Kind regards

---

### Post by Yves_W on 2013-08-01
Yeah, it's only the TS server. I looked through the logs and the only thing I could find was:
```

2013-08-02 01:36:53.832480|ERROR   |Accounting    |   | failed to register local accounting service
2013-08-02 01:36:53.832584|ERROR   |ServerLibPriv |   | Server() error while starting servermanager, error: instance check error
2013-08-02 01:36:53.832632|CRITICAL|Time          |   | Assertion "m_instance != __null" failed at common/time/customtime.cpp:115;


```

So I did this: [https://support.teamspeakusa.com/index.php?/Knowledgebase/Article/View/51](https://support.teamspeakusa.com/index.php?/Knowledgebase/Article/View/51)

I'm not sure if this actually fixed it, but I guess we're gotta have to wait. What kind of advantages does upstart have?

Edit: [http://forum.teamspeak.com/showthread.php/85663-Server-attempts-to-start-then-encounters-error-Ubuntu-11-10-64-bit](http://forum.teamspeak.com/showthread.php/85663-Server-attempts-to-start-then-encounters-error-Ubuntu-11-10-64-bit) The link leading me to the above link.

I did not get any message after mounting, is that correct?

---

### Post by tgalati4 on 2013-08-01
How can you run a 12.04 server with only 128MB?  Am I missing something?  You normally need a minimum of 256MB RAM with a 256MB swap, and even then you will run slow.  Perhaps the TS3 crash is related to lack of RAM or speed (due to excessive swapping)?

---

### Post by ssam on 2013-08-02
there is a handy program called watchdog that can be used to reboot a machine when services fail. (be very careful setting up on a remote machine though, because you can get it stuck in a reboot loop)

---

### Post by matt_symes on 2013-08-02
Hi

> [COLOR=#000000]I'm not sure if this actually fixed it, but I guess we're gotta have to wait. What kind of advantages does upstart have?[/COLOR]

[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

It's the standard way to start processes when the server is starting up or rebooting. It is replacing the old System V method.

It is an event based system and can start processes based on events such as the file system mounted or the network up. This allows processes to be started in parallel, decreasing boot time.

It has other benefits but, the main benefit for you is it can also respawn processes.

> [COLOR=#000000]I did not get any message after mounting, is that correct?[/COLOR]

You should only get a message on an error so no message is fine.

Kind regards

---

### Post by Yves_W on 2013-08-02
> **tgalati4 said:**
> How can you run a 12.04 server with only 128MB?  Am I missing something?  You normally need a minimum of 256MB RAM with a 256MB swap, and even then you will run slow.  Perhaps the TS3 crash is related to lack of RAM or speed (due to excessive swapping)?

It's a server with 128 MB ram and 256MB swap.

Specs from the site:

[LIST]
[*]128MB RAM
[*]10GB Disk Space
[*]Unlimited Bandwidth
[/LIST]

[LIST]
[*]Instant Setup
[*]OpenVZ Virtualization
[*]Linux OS
[/LIST]

> **ssam said:**
> there is a handy program called watchdog that can be used to reboot a machine when services fail. (be very careful setting up on a remote machine though, because you can get it stuck in a reboot loop)

Very intereseting, but it sounds quite dangerous indeed if I'd screw it up :P.

> **matt_symes said:**
> Hi



[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

It's the standard way to start processes when the server is starting up or rebooting. It is replacing the old System V method.

It is an event based system and can start processes based on events such as the file system mounted or the network up. This allows processes to be started in parallel, decreasing boot time.

It has other benefits but, the main benefit for you is it can also respawn processes.



You should only get a message on an error so no message is fine.

Kind regards

That means that there's been no error (: Do normal codes work in upstart too, or is upstart based on a programming language? The only languages I'm able to code are Java, batch and AHK.

---


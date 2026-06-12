---
title: "Transmission questions"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by johncroc on 2013-04-27
Hello all,

I'm super happy to be an Ubuntu user.  I am VERY pleased with it and rarely go back Win 7 for anything.

 So part of my process is to force myself to use unfamiliar things until I am familiar with them before I make critical comparisons with anything I was using before.  In this vein I have been using Transmission as my BT client and I am officially fed up with the interface.  It simply does not present my torrents in a way thet is useful to me.  So I started looking for alternative and found an old favorite, Azureus (now VUZE). and some others that looked promising (e.g. qBittorrent).

In my search I found a "remote UI" for Transmission and I thought, "Oh!  The guts of Transmission must be a daemon and I can just get this MUCH better UI and replace the UI that comes bundled in Ubuntu."  A little further checking seemed to confirm this so I downloaded the Transmission Remote GUI from the Software Center and proceeded to configure it for "localhost", etc.

Couldn't get it to connect though, no matter what I did.  Did some further exploration and tried ```
sudo service transmission-daemon start
``` and got this back ```
transmission-daemon: unrecognized service
``` which implies to me that the version of Transmission that comes with Ubuntu is not split into a daemon and a UI, but is just one monolithic program.

Is my diagnosis correct?  Before I start the process of trying to figure out how to get all my torrents moved to another client I want to make sure there's not some easier way.  For instance installing the daemon and having it just "see" all my existing torrents and their respective states and going from there.

---

### Post by DuckHook on 2013-04-28
I don't torrent much, so may be wrong on this one. However, my understanding of transmission-daemon is that it is actually Transmission compiled to run in the background. It is not a stub or backend, but the full-fledged app. Obviously, this means that it won't have its graphical component, but by daemonizing it, it can now be added to your startup script and run silently whenever you turn your box on. I also believe that it then can be accessed and managed by firing up the familiar Transmission GUI front-end. All GUIs are just front-ends for the real app anyway, which is why for most apps the command line offers so many more options and finer level of control than the GUIs.

Azureus and qBittorrent are not just different GUIs for Transmission. They are independent apps of their own and, to my knowledge, cannot be configured to run with Transmission (i.e transmission-daemon).

I know nothing about configuring transmission-daemon, so someone else needs to help you there.

I should add that I run an old box as a strictly command line console server in the basement. This box acts as a torrent server on such occasions as I need it to torrent. Since my torrents are exclusively ISOs of other FOSS OSes, I don't have anything close to the torrent requirements of most torrenters. My simple needs are served by running rtorrent (a simple but powerful command line torrent client) long enough to contribute back what I download. Once I reach about a 1.5 upload/download ratio, I will shut it down. I find it easier (and more secure) to ssh into this single-use box, fire up screen, run rtorrent, detach the screen session and run rtorrent as a background process for a limited time, than to fiddle around with it as a daemon. Call me paranoid, but I try to run as few daemons and services as possible, and even torrent only to the extent necessary to return what I receive.

If your torrenting needs are more extensive, then a daemon may be the best solution for you. If so, you should take special care to guard your ports, configure your firewall properly, apparmor everything (especially the daemon) and harden your server. You may also wish to keep nothing else of value on the machine that you will be using for torrenting purposes. I'll stop now before I get to the tin-foil hat.

<edit>

Apologies. Just looked it up and you cannot control transmission-daemon from the GUI. You need to do so from its web interface (didn't even know it had one!) or *rpc* commands or *transmission-remote*. I hate *rpc*s because I consider them awful security risks a la Windows, and a web interface means another open port--though I suppose that since so many ports are opened by the very act of torrenting, one more doesn't really make much of a difference. The more I delve into it, the more I'm reaching for aforementioned tin-foil hat, but it's your box and your call.

</edit>

---

### Post by claracc on 2013-04-28
> **johncroc said:**
> Hello all,

I'm super happy to be an Ubuntu user.  I am VERY pleased with it and rarely go back Win 7 for anything.

 So part of my process is to force myself to use unfamiliar things until I am familiar with them before I make critical comparisons with anything I was using before.  In this vein I have been using Transmission as my BT client and I am officially fed up with the interface.  It simply does not present my torrents in a way thet is useful to me.  So I started looking for alternative and found an old favorite, Azureus (now VUZE). and some others that looked promising (e.g. qBittorrent).

In my search I found a "remote UI" for Transmission and I thought, "Oh!  The guts of Transmission must be a daemon and I can just get this MUCH better UI and replace the UI that comes bundled in Ubuntu."  A little further checking seemed to confirm this so I downloaded the Transmission Remote GUI from the Software Center and proceeded to configure it for "localhost", etc.

Couldn't get it to connect though, no matter what I did.  Did some further exploration and tried ```
sudo service transmission-daemon start
``` and got this back ```
transmission-daemon: unrecognized service
``` which implies to me that the version of Transmission that comes with Ubuntu is not split into a daemon and a UI, but is just one monolithic program.

Is my diagnosis correct?  Before I start the process of trying to figure out how to get all my torrents moved to another client I want to make sure there's not some easier way.  For instance installing the daemon and having it just "see" all my existing torrents and their respective states and going from there.

Using synaptic, I see there is a transmission-daemon, you can see if you have it installed.

Consulting man for service command, I read that it assumes "service  runs  a  System V init script or upstart job in as predictable
       environment as possible, removing most environment variables  and  with
       current working directory set to /. "

So perhaps the problem is you have to start indicating the path for transmission-daemon program(/usr/bin/ ?).

---

### Post by johncroc on 2013-04-28
Thank you DuckHook and claracc.

I'm comfortable with the security issues (I'm a noob to Ubuntu, but a 30+ yrs IT pro).  And I understand that Azureus, etc. are not front-ends for the Transmission daemon.  Also, I think the failure when attempting to start the Transmission daemon service, tells me that the daemon is not even installed,  which fully explains why I can't connect to it with the Remote GUI.  Please correct me if I'm wrong.

Let me see if I can rephrase my question:
I need a bit torrent client with interface features like being able to position things in the queue quickly and easily, being able to sort on any column in the queue list, etc.  In the past I have used Azureus, and uTorrent and have been happy with the interfaces of both of these.  The Transmission BT client that comes with Ubuntu does not have the features I want, but it looks as if the Transmission Remote GUI might.  Am I correct in my assessment that the Transmission BT client that comes with Ubuntu does NOT rely on the Transmission daemon?

Also, If I have to install new software I will probably just go with something that's familiar like Azureus (VUZE), but I wonder if there are advantages to the "Transmission daemon w/ Transmission Remote GUI" setup.  One advantage I can think of is that I could control my daemon (and by extension, my torrents) from any machine on which the TR GUI is installed.  Are there other advantages?

Thanks for any and all ideas that come my way.

---

### Post by DuckHook on 2013-04-28
If you are comfortable with it security-wise, then ignore my tin-foil hat. As already mentioned, I am unfamiliar with Transmission in daemon form, so my info should not be considered of much value: mainly what I glean from the man page. If you call up the page, it will tell you everything I've already mentioned.

What I do know is: Transmission BT client does not rely on transmission-daemon. You are correct in this conclusion.

Not in the realm of knowledge, but a decent educated guess: the transmission-daemon/transmission-remote combo should give you the benefit of controlling your daemon from a remote machine. There is also mention of a web page, similar, I suppose, to ntop, which might prove the most versatile way of all. You would have to configure your firewall properly and have access to the right port, but that's how I read the man page too. Can't help you at all on the config part, I'm afraid.

Beyond this, I don't know enough about transmission-daemon to be able to provide any further useful advice.

---


---
title: "Question about Reading and Understanding System Log Ubuntu 20.04"
date: 2021-12-03
forum: New to Ubuntu
---

### Post by bhubunt on 2021-12-03
Hi there,
I have some basic questions about some of the info in my recent system logs of Ubuntu 20.04. Though I did some research on knowledgeable websites, some of the explanations can get to be too technical, so I'd be grateful for some simple, clarifying answers from a knowledgeable person.  My questions are about a laptop that is *not* connected to the internet, as I have a second laptop that I use online.
Here goes:
-Is it normal for the virtual filesystem service to start on login? I do not have VPN and, as I said, this is a laptop not connected to the internet;
-What does "stopped manager wait online" mean? Is it a program that always starts up on any Ubuntu 20.04 or only if you are trying to make a connection to the internet or to a server?
-What does "supervising 4 threads of 2 processes of 2 users mean"? Who or what is the second user besides the local user, me?
-What does "Activity service name="org.gnome.OnlineAccounts" requested by ':1.9'" refer to?
-What is "X server :0.NL"?
Thanks for your time.

---

### Post by grahammechanical on 2021-12-03
I will have a go. Or, at least start off the discussion. And a discussion is what this thread will turn into.

> -What does "supervising 4 threads of 2 processes of 2 users mean"? Who or what is the second user besides the local user, me?

There are always two users. Root and Me. Whoever Me is. In your case Me is you. In my case Me is me, myself. Have you not noticed that you (the user) do not get involved until after Linux has loaded and in turn loaded a display manager that presents on the display a login screen? Root had the authority to do all that.

> -What is "X server :0.NL"?

In Linux X is the video server. Hence X-Server. It has been around for years but is being replaced by video servers or compositors built according the Wayland protocol. With Ubuntu 20.04 we get the option at login to select either X-Server or Ubuntu on Wayland. The system defaults to X-Server. From Ubuntu 21.04 onwards Wayland is the default with the option to load Ubuntu on X-Server. 

The ":0.NL" part refers to the display number. One display = :0. As for "NL" I can only guess. 

> so I'd be grateful for some simple, clarifying answers from a knowledgeable person

That is asking a lot. The more knowledge a person has the harder it is to give simple, clear answers.

Regards

---

### Post by bhubunt on 2021-12-03
Thanks very much for your quick and knowledgeable reply.

Can I ask a follow-up question about this quote:

> **grahammechanical said:**
> 

In Linux X is the video server. Hence X-Server. It has been around for years but is being replaced by video servers or compositors built according the Wayland protocol. With Ubuntu 20.04 we get the option at login to select either X-Server or Ubuntu on Wayland. The system defaults to X-Server. From Ubuntu 21.04 onwards Wayland is the default with the option to load Ubuntu on X-Server. 

The ":0.NL" part refers to the display number. One display = :0. As for "NL" I can only guess. 



I am still not clear about what the function of the video server is. I did a quick google search and most posts refer to it for live streaming on the web. 

Regards.

---

### Post by Bashing-om on 2021-12-03
bhubunt; Hello

Please allow me to introduce you to the package manager.
> 
what the function of the video server is


In your terminal execute the command:
```

apt show xserver-xorg-video-nouveau

```
where here the example is the nouvea driver for Nvidia cards.
to see what your video device is, run:
```

sudo lshw -C display

```
and make the suitable substitution for "nouvea".

Then we can continue this discussion.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Holger_Gehrke on 2021-12-03
> **bhubunt said:**
> 
-Is it normal for the virtual filesystem service to start on login? I do not have VPN and, as I said, this is a laptop not connected to the internet;

The Virtual File System service has nothing in common with a Virtual Private Network except the word "Virtual". It's purpose is to make things that are not really file systems look like they are. An example would be a connection through USB to your phone for transferring files. It looks like a mounted file system but is actually a connection using the Media Transfer Protocol. There are quite a few other things like that.
> **bhubunt said:**
> 
-What does "Activity service name="org.gnome.OnlineAccounts" requested by ':1.9'" refer to?

The Gnome Desktop Environment has a component for managing all your online accounts (user names, passwords ...). When Gnome starts, this component gets started. It's a rather deeply integrated into the rest of the system and I don't know of a way to use Gnome and not have it around.
> **bhubunt said:**
> 
I am still not clear about what the function of the video server is. I  did a quick google search and most posts refer to it for live streaming  on the web.

Actually it's not a video server it's the display server. It sits between the user's input devices and display and the application programs. You can find an overview of X on [Wikipedia]("https://en.wikipedia.org/wiki/X_Window_System").

Holger

---

### Post by bhubunt on 2021-12-04
Bashing-Om, Thanks very much for the command lines. I will definitely get to it later today.

* * *

Holger, Thanks very much for the following explanation:

> **Holger_Gehrke said:**
> The Virtual File System service has nothing in common with a Virtual Private Network except the word "Virtual". It's purpose is to make things that are not really file systems look like they are. An example would be a connection through USB to your phone for transferring files. It looks like a mounted file system but is actually a connection using the Media Transfer Protocol. There are quite a few other things like that.

Pardon me for asking for further clarification: the media transfer protocol also showed up in the system log. Is that just because services like the virtual file system and the media transfer protocol get activated any time I boot ubuntu 20.04 or would I have to execute a specific action/command for them to get activated? 

Regards to all

---

### Post by bhubunt on 2021-12-04
Hi all,

I just combed through some of my system logs again and found more of the following:

-Leaving MDNS multicast group on interface lo.IPv4 with address 127.0.0.1
-Stopped Network Manager wait online
-Stopped Network Name Resolution
-Stopping WPA Supplicant (Wifi Protected Access)

And I found several references to local service cookies (or authentication cookies)

The lines read:
Server startup complete [name of my laptop] local service cookie [number]

This to me looks like my laptop connected to a server?

---

### Post by Holger_Gehrke on 2021-12-04
127.x.x.x in IP4 is the loopback interface. It's there for the machine to 'talk to itself'. For example all printing goes through that 'network'. The advantage to this should be obvious: as far as the rest of the system is concerned, there's no difference in printing to a locally connected printer or a remote one. A lot of subsystems on a Linux machine are like this, up to and including the GUI: the X-server can take request and send responses from and to other machines; that way you can have a program running on one machine and displaying it's GUI on another.

Holger

---

### Post by bhubunt on 2021-12-04
Thanks for the info about the loopback interface. But I have no printer attached to the laptop nor any other machine. The laptop I am using is not connected to the internet. 

That is why I am interested in knowing more about the other parts of my query: the reference to the MDNS multicast group and especially the cookies in my system logs:

Quote:
[COLOR=#000000]""And I found several references to local service cookies (or authentication cookies)[/COLOR]

[COLOR=#000000]The lines read:[/COLOR]
[COLOR=#000000]Server startup complete [name of my laptop] local service cookie [number][/COLOR]

[COLOR=#000000]This to me looks like my laptop connected to a server?"[/COLOR]

---

### Post by Holger_Gehrke on 2021-12-04
Even if you have no printer connected and no printer driver installed the printing *system* is installed and - probably - running. Try opening [http://localhost:631](http://localhost:631) in a browser. You should get connected to the CUPS (Common Unix Printing System) web-frontend on your machine.

MDNS is a system for machines to find each other on a network without having a dedicated server just for connecting IP-addresses and hostnames, similar to Microsoft's Zeroconf and Apple's Bonjour. On the loopback interface this system doesn't make much sense (you won't find other machines on that network), so it left the multicast group for it.

Cookies aren't limited to the web. The small bit of data the X-Server gives you as identification is called a cookie, too. You can see it with 'xauth list' (you'll probably get more than one, because there's more than one way a program can connect to the X-Server).

The (abstract) connection between your user session (the collection of all the programs running under your account at a given time) and the OS is also managed with a cookie generated through PAM. PAM stands for **P**luggable **A**uthentication **M**odules and is the part of the system which gets your username and password from whatever you use to login and returns either OK and a cookie or not OK (and no cookie for you ...) to the program trying to log you in. This might be the text based 'login' or the greeter part of the graphical login ... And of course - as the name implies - this is a modular system and there are modules which will hand off the username/password combo to a server on your network for checking so you can have the same username and password across all machines on your LAN and possibly also get a home directory mounted from some file server so you have the same working environment no matter from which of your machines you login.

If you run some administrative commands with 'sudo', you'll find notices in your logfile about the system starting another session for 'root' as the administrator account is called on Unix-like Systems. And 'sudo' also uses a cookie to see whether that session has timed out and it needs to ask for the password again.

So yes, you are on a network ... with exactly **one** node which is acting as both server and client.

Holger

---

### Post by TheFu on 2021-12-05
> **bhubunt said:**
> [COLOR=#000000]This to me looks like my laptop connected to a server?"[/COLOR]

Could this be the X/Client talking to the X/Server?

Some background follows ... 

X or X11 or X/Windows (those are synonyms) uses a client-server architecture.  The server runs on the system we side behind and gets connections and requests to handle from clients (X/clients or X-apps).  Almost every GUI program on any Unix/Linux system is an X-app, so it needs an X/server to actually be displayed.  The fact that the client and the server can run on the  same physical device doesn't matter.  They don't need to.   The confusion comes from the reverse nature of this client-server setup.  Most of the time, the "server" is remote and the client is on our machine ... that's how a website works. They run a web-server and we connect from our browsers (the client).  X works backwards to that normal way.

X/Windows has been around since the 1980s and it has been the de-facto standard for all Linux/Unix display programs and desktops. It has a number of flaws or "features" depending on your perspective. Some of the main "features" fixed in the replacement are screen capture and video capture.  A team of Linux-centric people, many from the X11 development team, have been working on a replacement for the last 10 yrs or so.   That's called Wayland.

Wayland is still a client-server architecture, but the server and local programs try to avoid the network-agnostic layers of X11 and try to be very fast when everything runs on the same machine.  There is an Xwayland that tries to make it so remote X-client (X-apps) can still be used.  Wayland has some issues and "fixes" some security issues that have been part of X11 forever.  They broke most screen and video capture programs, for example, by closing a security flaw in X11.

Anyways, there's a wikipedia page on X/Windows that does a better job at explaining.  [https://en.wikipedia.org/wiki/X_Window_System](https://en.wikipedia.org/wiki/X_Window_System)

So the first, basic, question is which display system are you using, Wayland or X11?  In 17.10, Canonical made Wayland the default, with X11 a backup.  That didn't go well. Wayland wasn't ready for many needs.  In 20.04, Wayland became the default, with an automatic X11 fallback if Wayland failed. There are probably easier ways to determine which is actually being used, but **inxi** is just so handy ... 
```
$ inxi -G
Graphics:  Card: NVIDIA GP108 [GeForce GT 1030]
[COLOR="#008000"]           Display Server: x11 (X.Org 1.20.8 ) driver: nvidia
[/COLOR]           Resolution: 1920x1200@59.95hz
           OpenGL: renderer: N/A version: N/A
```
I'm using X11 with a native nvidia driver.  I'm sure there are environment variables for WAYLAND which would be easy to check.  If you do everything local on the same machine and don't need screen capture/video capture or some X-specific automation tools (xdotool, cnee), then Wayland should be a little faster (to many times faster) than X11. Lots of the problem programs are being ported to Wayland.  Many tools will never be ported, however.

I doubt most of that was actually helpful.  Just background.

---

### Post by bhubunt on 2021-12-05
Thanks, TheFu, for the clarification. I am still learning about Ubuntu, at this point...

Holger, thanks so much for your elucidations about the one node network and the X-server cookies. That is very helpful to know.

I wonder if you'd have time to explain the following lines as well. 

[COLOR=#000000]-Stopped Network Manager wait online[/COLOR]
[COLOR=#000000]-Stopped Network Name Resolution[/COLOR]
[COLOR=#000000]-Stopping WPA Supplicant (Wifi Protected Access)

[/COLOR]From googling entries on the WPA supplicant, it seemed to me that this feature is not a standard component of the Ubuntu 20.04 OS but rather needs to be added or activated by me?

---


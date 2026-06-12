---
title: "torrent file server"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by Samuez on 2012-03-08
It's a bit more complicated than that.

------Long Version, Skip to get Short Version----

I'm got a small mini-itx computer for cheap and thinking of using it as a torrent file server that's remotely controlled from my desktop while also headless. But I would prefer it with an GUI.

My idea was to have it using either transmission or utorrent alpha for any ubuntu variant (probably go for xubuntu) where I can use the IP block list. I'll be streaming the contents of the drive that the file are in from my main desktop, like video or such so that my main computer would take care of having the require hardware for it. 

But I would want to download torrent on that, but I store the .torrent file and its content on the mini-itx while I browse and download from my main computer. So, to do that, I wanna remotely control it or in someway configure it to do so.

Chances are that I'm not going to leave it on 24/7 so when I turn it on, it'll just boot up and ready to go without a monitor or keyboard or such thing. And I will not be using an monitor or keyboard/mouse afterward since I don't really have an another monitor to use.

I heard that SAMBA with OpenSSH would do so, but would that be doable with GUI on ubuntu while being headless or would I need the ubuntu server edition to be headless but wouldn't that be command-line only? If possible, I prefer to install the least amount of software and I'm not that greatly skill with linux as I am with windows. Oh ya, I'm using windows 7 on my main desktop.

-----Short Version------
I want a ubuntu distribution and software that can start headless with GUI interface so I can use it as a torrent file server where I can remotely add torrent from my main desktop and be store in the mini-itx while also being able to access the drive from my main computer to stream its content. I'll hook up with cat6 for network, and using the least amount of software. The main desktop will be an window 7. Is it doable without much work?

Sam

Edit: Of course, if it's a bit too complicated, I might as well try WHS or FreeNas (though no extra USB to install/boot from).

---

### Post by papibe on 2012-03-08
I use transmission-daemon on my headless Ubuntu home server (no GUI). Transmission-daemon has a [web interface]("http://www.vanutsteen.nl/wp-content/uploads/2008/12/transmission_screenshot.png") that allow you to load, pause, restart torrents and magnet links.

I use both nfs and samba to share files over my network. One of the clients is running XBMC and it plays media from the server.

Just some thoughts.
Regards.

---

### Post by Munk3y on 2012-03-08
I second Transmission-daemon. Use "Transgui" on your Workstations. What it will do is appear to be a and act as a regular Torrent program locally but it will be storing all data on the Server.

For my HTPC/"Server", I just run Unity and use the built in VNC "Remote Desktop" feature to connect to it when needed. Otherwise, it just starts up and runs XBMC all the time. Then Transmission-daemon saves torrents to a directory that Samba shares.

Transgui Link: [http://code.google.com/p/transmisson-remote-gui/](http://code.google.com/p/transmisson-remote-gui/)

---

### Post by Samuez on 2012-03-08
Transmission seem pretty popular.

I'm not that keen on an web interface for tranmission as I probably won't use it other than checking the torrent while either outside of my network or don't wanna check the torent remotely. Or something like that.

Transgui seem like what I needed! And might use the built-in VNC so I can select where the torrent download will go and/or make any changes to the system.

I'd look up XBMC but I'm not sure what it exactly does. I can't watch the file from the server cause it's a pretty low-end atom cpu and graphics but I wanted to do so on my main desktop. Do anyone know any good guide out there for it?

Thanks for the response guy.

---

### Post by Samuez on 2012-03-09
Does anyone know of a good ubuntu distibution? m not sure I'll be able to configure Ubuntu Server edition cause I'm not that great with commands nor knowledgeable about it. But I do want headless, so can I use xubuntu (prefer) and somehow do 'headless' on it?

Thanks.

---

### Post by papibe on 2012-03-09
Maybe.

First of all: you can have the same services running in any Ubuntu flavor. For delivering services from a GUI distro I would choose something light like Lubuntu (but I guess Xubuntu would be fine too).

The problem may lay in the hardware. Some systems won't boot if they can't initialize the graphics mode. Without a monitor physically connected  is anybody's guess if that would work or not. May be you can hardcode some modes on the X config file.

Note that you won't need the monitor for the system to run, just to boot.

Hope that helps.
Regards.

---

### Post by Samuez on 2012-03-09
Cool thanks. I got all week with spring break to deal with this and make it work.

I just gotta get the mini-itx to work first...-_-

Anyone know if having unsupported ram, say ddr2-4200 instead of 6400/5300, would have on the computer? It won't show anything on monitor though everything boot...If I take ram out, it'll beep continuously so I assume it's RAM that's causing the issue of not seeing anything on monitor.

Thanks

---

### Post by JackandJohn on 2012-08-12
I'll add that you can set up dropbox, even on ubuntu server, and have Transmission (or another client) watch a torrent folder.

I have this, use it on iOS, laptops, and share the folder with a couple people: any torrent file dropped in to the local folder is started on the server and deleted (great for confirmation)

---

### Post by Cheesemill on 2012-08-12
I would go for Ubuntu server and Deluge.

The advantage of using Deluge is that you can run the backend on your headless server, but then use the regular Deluge GUI running on your main computer to control it, it appears as if you are just running Deluge normally but all of the work is being done on your server.

---


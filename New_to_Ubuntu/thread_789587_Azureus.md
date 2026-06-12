---
title: "Azureus"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by System Monitor on 2008-05-10
I am downloading *really* slowly for Azureus and don't know what to do about.

I tried changing the port around but that didn't help much.

It says that I have a firewall on even though I don't?

What should I do to get better download speeds?

Thank you!

---

### Post by CAsurfer on 2008-05-10
Are you behind a router? If so, it may be blocking ports, and you will need to go into the router's config to let through the port you want to use.

---

### Post by dorkdork777 on 2008-05-10
Also, some torrents are simply slow. Look on the tracker's web page, and find the torrent you're downloading. If there's way less "seeds" than "leechers", then it may be just a slow torrent.

---

### Post by bouta on 2008-05-10
i installed firestarter and played around with it ..and opened some ports safely

---

### Post by grannyw on 2008-05-10
1.Check if you run any firewall software in the background,check it the sessions.If you find one you should check the firewall reaction to the port connections and play abit with the configuration.
2.May be its just a slow torrent file.
3.And if you figure out that its nither 1. nor 2. try to download the file with another application.

---

### Post by System Monitor on 2008-05-10
How can I tell if I am behind a router?

---

### Post by System Monitor on 2008-05-10
:bump:

---

### Post by bred on 2008-05-10
[COLOR="Blue"]install firestarter for ubuntu and open the port u need to use for your p2p[/COLOR]

---

### Post by warbread on 2008-05-10
> **System Monitor said:**
> How can I tell if I am behind a router?

If you have one, it will be connected to your cable/dsl modem.  This generally doesn't apply to dial up internet.

---

### Post by System Monitor on 2008-05-11
Installed firestarter and allowed it, didnt change anything.

I am almost 100% sure that I have a router but I don't know how to configure it. Is there a menu that I should go to for editing some preferences?

Thanks for the help!

---

### Post by nynoah on 2008-05-11
Try Deluge over Azur........Azur just runs slow all the time when I used it.

---

### Post by warbread on 2008-05-11
Go into terminal and type 'route'.  Wait a second for it to finish, and when it lists "default", that's your router's IP address.  Then, go into your web browser and in the address bar type that address and nothing else.  It will bring up a screen asking for a username and password.  What this is depends on the model of your router, but you could try putting "admin" in either of the two fields and leaving the other blank, or putting it in both and see what happens.  This will get you into the router config screen, which also differs from model to model.  

However, I'm not sure that you will be getting much better speeds doing that.  What speeds are you getting and what are you expecting to get?

---

### Post by Nikunj93 on 2008-05-11
Well firstly
set up an Static IP
then open firefox
then type
192.168.1.1 [if u connect ur router using ethernet and type 192.168.1.2 if u use USB to connect ur router]
then go to nat entries and create an entry to Allow Azureus


BUT I SAY USE DELUGE
TOO LIGHT ON THE SYSTEM!!

---

### Post by System Monitor on 2008-05-11
All I can say so far is THANK YOU

I got a screen that asked for my username and password, and I have no idea what they are. Are there any default passwords or such?

Edit: I have a Arescom NetDSL 800 Modem/Router

---

### Post by warbread on 2008-05-11
Yeah, try "admin" as the user name with no password.  If that doesn't work, try "admin" as the password with no user name.  If that doesn't work, try "admin" in both.  And if none of those work, post what kind of router you have here.

---

### Post by System Monitor on 2008-05-11
Arescom NetDSL 800 Modem/Router

---

### Post by DarkDancer on 2008-05-11
The default username appears to be left blank and the password is atc123.

---

### Post by System Monitor on 2008-05-11
Ok, I got it to work but how do I open a certain port?

This is what the config looks like

---

### Post by shifty_powers on 2008-05-11
download utorrent, (google it), run it through wine and make sure that uPnP is enabled on the the router.

Will make your life a lot easier. utorrent is much better than azureus anyways ;)

---

### Post by DarkDancer on 2008-05-11
Or Deluge, no need for wine.

---

### Post by CAsurfer on 2008-05-15
Don't worry; you have a very common and well understood problem.

You need to enable "port forwarding". When you use bittorrent, part of the role of the bittorrent client is to act as a server, meaning it provides files for other users. When another user attempts to get a file from your computer, a request is sent to your computer. The request is associated with a label, called a port, which helps your computer figure out what to do with the request. Usually, the request will get to your computer, and everything will be happy.

That's not what's happening in your case. You're behind a router (a Linksys WRT54G by the screenshot). Your router is the device hooked directly up to the internet connection, not your computer. So when other users attempt to send bittorrent requests to your computer, they're actually being sent to the router. Thus your router has to be configured to forward those requests to your computer.

There are 3 steps to get this to work:
1) Give your computer a static IP address. Otherwise, the computer's address will frequently shift, and the router won't know where to forward requests to.

If you are in Hardy, this may be as easy as clicking on the network manager applet -> manual configuration -> wired/wireless connection (properties). Under configuration, select "static IP address", choose the address you want (e.g. "192.168.1.200"), and accept the defaults.

2) Tell your router to forward ports to your computer. You can get by with forwarding only the ports that bittorrent needs, but it's probably easiest to just forward all requests to your computer.

A port forwarding howto is here: [http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/default.htm](http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/default.htm)

3) Make sure you don't have a firewall blocking ports you need to have open. I would uninstall firestarter if you have it.


This may seem a little crazy, but once you do it, it seems natural. Also, if you ever want to run a server from your computer (web-server, ssh-server), you'll have to do something like this.

---

### Post by CAsurfer on 2008-05-15
deleted: network lag caused multiple postings

---

### Post by kcox5342 on 2008-05-15
It is also possible that your ISP firewalls you - I am on Verizon and they do and there's nothing to be done about it, port forwarding does nothing.  I had used port forwarding successfully on AT&T and Comcast so I know how to do it, but Verizon won't allow any incoming connections no matter what.

---


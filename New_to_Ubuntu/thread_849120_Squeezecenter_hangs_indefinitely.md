---
title: "Squeezecenter hangs indefinitely"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by mihaitha on 2008-07-04
Hi all.

I installed the latest stable Squeezecenter (7.0.1) thru apt-get from the slimdevices repository, on Ubuntu Hardy Server x86 (actually Gutsy with dist-upgrade to Hardy). What I want with it is to stream my music from home to my work office. All ok, the squeezecenter daemon is running, I can connect thru 9000 port from FF, yet it's not working as expected. I have 2 problems with it:
1. the web interface is very scarsely styled (just the 2 panels left and right, with only Times text in them). It's nothing like the screenshots I saw on Google of the SC web interface.
2. SC did detect all the music on the partition, yet when I try to play an album/song or add it to a playlist, the web interface hangs indefinitely after I click on the link, and allthough Winamp connects to the stream, it plays nothing at all.

Anybody else had this problem? Any help is appreciated. Thanks in advance.

---

### Post by nothingspecial on 2008-07-04
The default theme in squeezecenter is text and buttons only. Click on settings (bottom right) then in the new webpage click on the interface tab and choose your new skin/theme/interface.
 I`ve had no luck getting my amarok downloaded artwork to show yet. Do you know how it`s done?

---

### Post by mihaitha on 2008-07-04
Thankx, seems I missed the 'Settings' link there.

About the artwork, I'll have to get the streaming to work first, then I'll worry about that. I'll keep you posted if I get it working.

---

### Post by chimiasanchi on 2008-07-04
I'm running gutsy, and I haven't gotten SqueezeCenter to work yet.
Here are the steps I took:

1) added the apt line

```
deb http://debian.slimdevices.com stable main
```

to the list of 3rd party repos 

2) installed squeezecenter in synaptic

3) started squeezecenter with the command
```

sudo /etc/init.d/squeezecenter start
```

(i get a permissions error when i use that command without sudo)

4) on the same machine running SqueezeCenter, I use firefox to try connecting to the squeezecenter webapp:

[http://192.168.0.113:9000/](http://192.168.0.113:9000/)

Firefox complains:
Firefox can't establish a connection to the server at 192.168.0.113:9000.

I'm certain that the IP address is correct. It seems like the port 9000 must be wrong. Does anyone know how to set or determine which port SlimCenter server connects to?

---

### Post by cariboo on 2008-07-04
you can use nmap to see whet ports are open. It is available from the repositories and you can use synaptic to install it. You can also check to see what ports are listening using the command:

```
netstat -l
```

Jim

---

### Post by chimiasanchi on 2008-07-04
something was messed up with my network settings. I was having general problems connecting to my wireless router. So I'm not sure what exactly was the problem, but after cycling power on my wireless router and PC, everything now works fine. I suppose my above post is a good set of instructions for someone wanting to install SqueezeCenter on their Gutsy machine.

@cariboo907
i'm glad to know that command now.

---


---
title: "Messenger that can send and receive files from and to Google Talk clients"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Meph1st0 on 2008-07-16
The gloves are off!!!  

I work with 30 or 40 guys who've all conspired to communicate over Google Talk on their Windoesn't machines.  I've been able to join in on the fun with the ability to communicate with them over pidgin, kopete, and psi.  But I can't transfer files and they're giving me crap about it.  I need a client that works with xmpp/jabber that can transfer files to these crap heads that are using google talk.

file transfers over pidgin to google talk doesn't work.
I might have Kopete configured wrong, but so far I can't get it to transfer files either.
PSI also appears as though it's supposed to work but I can't get it to work.

I need to prove to these guys that there's a messenger program on Linux that's good enough to at least talk to them and transfer files over Google talk.

---

### Post by jesterthejedi on 2008-07-16
Wish I could help you. Also would love to have an easier way to transfer than constantly requesting people email me files. Maybe we should come up with a universal drag and drop file transfer only protocol/service.

---

### Post by Meph1st0 on 2008-07-16
I would love to come up with our own universal drag and drdop file transfer only protocol/service.  The next step for me would be to...learn how.  I am currently going to school to learn to be a programmer.  But what really chaps my hide is the school will likely put more emphasis on microsoft programming.  VB.NET, C++, ASP.NET, etc.  I wouldn't know the first thing about php, C, or any of the programming languages in Linux.  I wouldn't even know which programming languages to start with to develop something for Linux.  I'm a fresh Linux noob, recently converted as of March of this year.  But I've become a very strong supporter of Ubuntu.  It's fricken awesome!

Anyway, anybody else know of a messenger program I can use to transfer files to a coworker running the google talk client?  Or does anyone know what steps I need to take to configure PSI or Kopete to be able to transfer files?

---

### Post by Meph1st0 on 2008-07-20
so....nobody else has any ideas?  Are we gonna let these windows guys get the best of me?

I've tried Kopete, PSI, Pidgin, and Gajim.  It's just gotta be a setting or something that I need to set in either PSI, Kopete, or Gajim.

---

### Post by jamesrfla on 2008-07-20
If you want the Google talk client in Ubuntu you can get Wine and then run Google talk under Wine. Also during the weekend there is more people on this forum site that can help you with your problem.

---

### Post by UbuntuNerd on 2008-07-20
I think this link got all the different messengers out there I just read through all of them and some of them support Linux and gmail/gtalk good luck!!


[http://www.nirmaltv.com/2008/04/19/18-multi-protocol-im-clients-for-windows-mac-and-linux/]("http://www.nirmaltv.com/2008/04/19/18-multi-protocol-im-clients-for-windows-mac-and-linux/")

---

### Post by UbuntuNerd on 2008-07-20
and if you absolutely have to have it you can try  VMWARE and install xp just to use with Gtalk

---

### Post by jesterthejedi on 2008-07-20
Well if your gonna study C++, then that&#347; all you need really. Instead of compiling it into a .EXE you just output it to a .BIN file. All the program really needs to do it just capture your IP address and the person to send it to, and it could default a save to a home or desktop folder. As for a temporary solution, I have installed Gyachi, which seems to be the better Yahoo client with extra features in it. Just wished Pidgin could do it, its the better one for chat anyway.

---

### Post by jamesrfla on 2008-07-20
[http://www.openwengo.org/](http://www.openwengo.org/) might be bale to do what you want to do.....or not.

---

### Post by hansdown on 2008-07-21
Hi Meph1st0. Does gmail.com work where you are?

---

### Post by jamesrfla on 2008-07-21
I don't think you can transfer files through gmail.com unless you e-mail it.

---

### Post by Meph1st0 on 2008-07-21
Yeah, I can get to gmail.com just fine and use their web based chat client, but I can't transfer files through it.  Mind you, I can use all of these chat programs to chat with google talk folks, I just can't transfer files with them. :(

I also checked out that openwengo website and it appears to be a tool built to be used for VOIP and Internet telephony type applications.

---

### Post by a0u on 2008-07-21
Sorry, but Google Talk in Wine is [rated garbage]("http://appdb.winehq.org/appview.php?iAppId=2398").
The official client uses [libjingle]("http://code.google.com/apis/talk/libjingle/index.html") for file transfer, and attempts are underway to implement it in 3rd party IM clients. However, looking at [a list of clients supporting Jingle]("http://en.wikipedia.org/wiki/Jingle_(protocol)") (courtesy Wikipedia), everything seems mostly experimental and unsuitable for daily use. I suppose it's a matter of time...
 
If your contacts use GTalk, surely they must have a Gmail account. If the files aren't too large, couldn't you just attach and send them by email?

---

### Post by amendt on 2008-07-22
I have been banking on Google's 2008 summer of code which has Mike Ruprecht helping [solve]("http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo") this bug.  I have added Empathy via Third-Party Software Sources [[http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main] and with telepathy working I can see the light at the end of the tunnel.  I wish I could donate more money to this also.

---

### Post by sazawal on 2011-10-02
Hi, did any one find a way to do this file transfer? I guess libjingle api can be used to develop an application for linux to gtalk file transfer. Anybody has any idea how to make it work?

---


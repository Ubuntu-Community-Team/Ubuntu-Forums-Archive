---
title: "a program like logmein for ubuntu (and not vnc)"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by y_garti on 2011-12-20
hello everyone
i am looking for a web program like logmein for windows
that i can use to see my Ubuntu in my home without the need to open ports in my switch at home
and to use the browser to see it (basically a look like logmein for Ubuntu)

thank you very much

---

### Post by dargaud on 2011-12-20
So basically you want to introduce huge security risks on your home system ? Better stay with ssh+vnc combination. Advantages are: secure, compatibility (you can access from Windows, Linux, even Android)...

---

### Post by satanselbow on 2011-12-20
Logmein is nothing more than a poorly implemented bling web GUI for VNC (with regards to security etc etc)

Sounds like a great service - not only are you using a relatively insecure service but you are sharing all you private transactions with a 3rd party - nice work if you can get it :popcorn:

---

### Post by y_garti on 2011-12-20
i deeply disagree with you
vnc as known vulnerability and as far as i know logmein (or any other program based like that)

has 0 vulnerability as for know and is working on secure tunnels (https) and the only way to logon to the computer is to logon to the site and then to the client (2 way authentication) vnc most of the time use just password and there are plenty of brute-force for vnc this is why you never see organization that use vnc for accessing the client nobody open the port to the Internet and you have got much more capablities with logmein then vnc security and usability

so if anyone know of a good logmein program like i'll be glad 

thanks

---

### Post by MartijnNL on 2011-12-20
[Teamviewer]("https://www.teamviewer.com") can probably be used for this purpose.

---

### Post by y_garti on 2011-12-20
can i use team viewer as a service/daemon so i don't need to open it and accept every time i logged in ?

---

### Post by mastablasta on 2011-12-20
as i know logmein data transfers are supposed to be encrypted (travel via tunnel). yes they go through 3rd party, but what does that matter? the whole "internet" goes through ISP (=3rd party)!!!
> 
LogMeIn remote access products use a proprietary remote desktop protocol that is transmitted via [SSL]("http://en.wikipedia.org/wiki/Secure_Sockets_Layer"). An [SSL certificate]("http://en.wikipedia.org/wiki/SSL_certificate") is created for each remote desktop and is used to cryptographically secure communications between the remote desktop and the accessing computer.[[SIZE=2][2][/SIZE]]("http://en.wikipedia.org/wiki/LogMeIn#cite_note-lmisecuritywhitepaper-1")
Users access remote desktops using either the *LogMeIn Ignition* stand-alone application or a [web portal]("http://en.wikipedia.org/wiki/Web_portal"). The web portal requires either an ActiveX plugin for Internet Explorer, or an extension for Firefox (the LogMeIn plug-in for Firefox), or an extension for Safari (the LogMeIn plug-in for Safari), failing that it falls back to requiring Java in order to run a Java program,[[SIZE=2][3][/SIZE]]("http://en.wikipedia.org/wiki/LogMeIn#cite_note-2") and failing that it falls back to "a screen-shot based HTML remote control".[[SIZE=2][4][/SIZE]]("http://en.wikipedia.org/wiki/LogMeIn#cite_note-3") The web portal also provides status information for the remote computers and, optionally, remote computer management functions.
The service connects the remote desktop and the local computer using SSL over [TCP]("http://en.wikipedia.org/wiki/Transmission_Control_Protocol") or [UDP]("http://en.wikipedia.org/wiki/User_Datagram_Protocol") and utilizing [NAT traversal]("http://en.wikipedia.org/wiki/NAT_traversal") techniques to achieve [peer-to-peer]("http://en.wikipedia.org/wiki/Peer-to-peer") connectivity when available
 
 
 
Maybe OpenVPN (it's cross platform)? But i don't think it's as user friendly. however if all computers are in same home LAN network all this is not necessary. they can share data between themselves without anything like Logmein

---

### Post by MartyBuntu on 2011-12-20
> **dargaud said:**
> Better stay with ssh+vnc combination.

Seconded.

---

### Post by howefield on 2011-12-20
> **y_garti said:**
> can i use team viewer as a service/daemon so i don't need to open it and accept every time i logged in ?

Yes, it can if you are logged in to your session.

Not sure if it can start with no user logged on.

---

### Post by satanselbow on 2011-12-20
> **mastablasta said:**
> as i know logmein data transfers are supposed to be encrypted (travel via tunnel). yes they go through 3rd party, but what does that matter? the whole "internet" goes through ISP (=3rd party)!!!

True. My point was rather that the OP was after a "Logmein alt but not VNC" when Logmein is nothing more than a VNC GUI - tunnelled or not.

SSH+VNC 3rd'ed

---

### Post by mastablasta on 2011-12-20
quite correct. Logmein is a VNC :-)

---

### Post by MartijnNL on 2011-12-20
> **mastablasta said:**
> quite correct. Logmein is a VNC :-)


I assume the OP meant that he didn't want to setup a complete VNC server. Even if Logmein (and Teamviewer) are VNC's. These kind of solutions are much easier to implement than a normal VNC, especially if you're behind a router.

---


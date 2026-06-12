---
title: "Problems with apt-get, synaptic, codecs"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Ultimate_goblin on 2008-10-15
Hi everyone! I'm the newest here, I'm sure, and I just had a friend of mine setting the internet connection for me. He set up the wireless card that wasn't recognized by the OS, but now another problem comes by: when I try to run the command apt-get, or when (more generally) the pc tries to download codecs or packages, he will fail.
This is the answer of the terminal after a sudo apt-get update:
```

Err http://security.ubuntu.com hardy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://security.ubuntu.com hardy-security/main Translation-en_US           
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US     
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/universe Translation-en_US       
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
  Unable to connect to security.ubuntu.com http:
Err http://it.archive.ubuntu.com hardy Release.gpg                             
  Could not connect to it.archive.ubuntu.com:80 (193.206.140.37), connection timed out [IP: 193.206.140.37 80]
Err http://it.archive.ubuntu.com hardy/main Translation-en_US
  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]
Err http://it.archive.ubuntu.com hardy/restricted Translation-en_US
  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]
Err http://it.archive.ubuntu.com hardy/universe Translation-en_US
  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]
Err http://it.archive.ubuntu.com hardy/multiverse Translation-en_US
  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]
Err http://it.archive.ubuntu.com hardy-updates Release.gpg
  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]
Err http://it.archive.ubuntu.com hardy-updates/main Translation-en_US
  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]
Err http://it.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]
Err http://it.archive.ubuntu.com hardy-updates/universe Translation-en_US
  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]
Err http://it.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]
Reading package lists... Done                            
W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to it.archive.ubuntu.com:80 (193.206.140.37), connection timed out [IP: 193.206.140.37 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to it.archive.ubuntu.com http: [IP: 193.206.140.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

This is really funny, especially the last line of the answer!:lolflag: Thanx a lot, Heron! I'll try to follow your advice if I can..

I saw a lot of threads like this, but no one seemed able to solve this problem. I am a bit discouraged. The proxy pac address is [http://proxy.ucd.ie/proxy.pac](http://proxy.ucd.ie/proxy.pac) in case you wanted to go and give it a look.
Anyone?

---

### Post by hyper_ch on 2008-10-15
can you ping the servers? If not then (a) the servers are down or (b) the routing to them doesn't work for you right now.
If it's (a) then try later again
If it's (b) try also later again or try to change dns server and clear your dns cache

---

### Post by ByteJuggler on 2008-10-15
What is your internet setup like?  Any firewalls/routers in between your machine and the internet? Anyway, it appears that your internet name resolution is working, but that other connectivity is not working, which is strange. (You'd think that if your name resolution is working that your internet connection would be fine, but apparently not so.)

Can you try the following in a terminal and paste the output here:

```
ping www.google.com
```

---

### Post by thunk77 on 2008-10-15
Looks to me like your internet connection is down..
Can you browse sites normally?

---

### Post by Ultimate_goblin on 2008-10-15
> **thunk77 said:**
> Looks to me like your internet connection is down..
Can you browse sites normally?

Yes, I can browse normally as I am doing it now... my ping feedback is
```
ping www.google.com
PING www.l.google.com (66.102.9.99) 56(84) bytes of data.

```

I am in an university which (of course) uses a proxy, and I am using wireless routers owned by the university. Again, no problems in browsing, it's as the proxy will stop programs from connecting to the internet. Mind it: I can work normally with Windows Vista, so the problem must be somewhere in Linux! :mad:

---

### Post by drs305 on 2008-10-15
If you are sure the server is working, check your settings in synaptic or software sources: settings, preferences, network. You may need to either configure the proxy or try 'direct connection to the internet', depending on your setup.

---

### Post by ByteJuggler on 2008-10-15
> **Ultimate_goblin said:**
> Yes, I can browse normally as I am doing it now... my ping feedback is
```
ping www.google.com
PING www.l.google.com (66.102.9.99) 56(84) bytes of data.

```

I am in an university which (of course) uses a proxy, and I am using wireless routers owned by the university. Again, no problems in browsing, it's as the proxy will stop programs from connecting to the internet. Mind it: I can work normally with Windows Vista, so the problem must be somewhere in Linux! :mad:

OK, try the following:
1) Open up a terminal
2) Enter:
```
export http_proxy=http://http://proxyaddress:proxyport
```
replacing proxyaddress with your universities proxy address and proxyport with the port used.  If you need to authenticate, then thet line is "http://myuname:mypass@myproxy:myport", replacing myuname:mypass with your user and pass.
3) Now try 
```
sudo apt-get update
```

If you can get that to work, you should be able to modify the /etc/apt/apt.conf file to permanently set up the proxy spec for apt-get.

---

### Post by Ultimate_goblin on 2008-10-15
Mmm... still nothing, but something has changed. Firstly, when I tried ```
sudo apt-get update
``` it kept me waiting for a long time before giving me the message error. Now it answered me instantly:
```
Ign http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com hardy-security Release
Ign http://security.ubuntu.com hardy-security/main Packages
Ign http://it.archive.ubuntu.com hardy Release.gpg
Ign http://it.archive.ubuntu.com hardy/main Translation-en_US
Ign http://it.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://it.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://it.archive.ubuntu.com hardy/multiverse Translation-en_US
Ign http://it.archive.ubuntu.com hardy-updates Release.gpg
Ign http://it.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://it.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://it.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://it.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Packages
Ign http://security.ubuntu.com hardy-security/main Sources
Ign http://security.ubuntu.com hardy-security/restricted Sources
Ign http://security.ubuntu.com hardy-security/universe Packages
Ign http://security.ubuntu.com hardy-security/universe Sources
Ign http://security.ubuntu.com hardy-security/multiverse Packages
Ign http://security.ubuntu.com hardy-security/multiverse Sources
Ign http://it.archive.ubuntu.com hardy Release 
Ign http://it.archive.ubuntu.com hardy-updates Release
Err http://security.ubuntu.com hardy-security/main Packages
  403 Forbidden [IP: 193.1.172.166 80]
Err http://security.ubuntu.com hardy-security/restricted Packages
  403 Forbidden [IP: 193.1.172.166 80]
Err http://security.ubuntu.com hardy-security/main Sources
  403 Forbidden [IP: 193.1.172.166 80]
Err http://security.ubuntu.com hardy-security/restricted Sources
  403 Forbidden [IP: 193.1.172.166 80]
Err http://security.ubuntu.com hardy-security/universe Packages
  403 Forbidden [IP: 193.1.172.166 80]
Err http://security.ubuntu.com hardy-security/universe Sources
  403 Forbidden [IP: 193.1.172.166 80]
Err http://security.ubuntu.com hardy-security/multiverse Packages
  403 Forbidden [IP: 193.1.172.166 80]
Ign http://it.archive.ubuntu.com hardy/main Packages
Ign http://it.archive.ubuntu.com hardy/restricted Packages
Ign http://it.archive.ubuntu.com hardy/main Sources
Ign http://it.archive.ubuntu.com hardy/restricted Sources
Ign http://it.archive.ubuntu.com hardy/universe Packages
Ign http://it.archive.ubuntu.com hardy/universe Sources
Ign http://it.archive.ubuntu.com hardy/multiverse Packages
Ign http://it.archive.ubuntu.com hardy/multiverse Sources
Err http://security.ubuntu.com hardy-security/multiverse Sources
  403 Forbidden [IP: 193.1.172.166 80]
Ign http://it.archive.ubuntu.com hardy-updates/main Packages
Ign http://it.archive.ubuntu.com hardy-updates/restricted Packages
Ign http://it.archive.ubuntu.com hardy-updates/main Sources
Ign http://it.archive.ubuntu.com hardy-updates/restricted Sources
Ign http://it.archive.ubuntu.com hardy-updates/universe Packages
Ign http://it.archive.ubuntu.com hardy-updates/universe Sources
Ign http://it.archive.ubuntu.com hardy-updates/multiverse Packages
Ign http://it.archive.ubuntu.com hardy-updates/multiverse Sources
Err http://it.archive.ubuntu.com hardy/main Packages
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy/restricted Packages
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy/main Sources
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy/restricted Sources
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy/universe Packages
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy/universe Sources
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy/multiverse Packages
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy/multiverse Sources
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy-updates/main Packages
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy-updates/restricted Packages
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy-updates/main Sources
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy-updates/restricted Sources
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy-updates/universe Packages
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy-updates/universe Sources
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy-updates/multiverse Packages
  403 Forbidden [IP: 193.1.172.188 80]
Err http://it.archive.ubuntu.com hardy-updates/multiverse Sources
  403 Forbidden [IP: 193.1.172.188 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz  403 Forbidden [IP: 193.1.172.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz  403 Forbidden [IP: 193.1.172.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz  403 Forbidden [IP: 193.1.172.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz  403 Forbidden [IP: 193.1.172.166 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.gz  403 Forbidden [IP: 193.1.172.188 80]

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  403 Forbidden [IP: 193.1.172.188 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
The string you can see now is a bit different from the previous one. Something has changed, but still... it's not making the difference for now.
Anyway, I really appreciate your support, who makes you screw your brain over noobs' problems? :)

---

### Post by ByteJuggler on 2008-10-15
> **Ultimate_goblin said:**
> The string you can see now is a bit different from the previous one. Something has changed, but still... it's not making the difference for now.
Anyway, I really appreciate your support, who makes you screw your brain over noobs' problems? :)

Hmmm, strange.  Did you use authentication/specify a proxy/network username and password in the proxy spec?  Anyway, if it was an authentication issue I'd have expected a 407 (authentication required) not a 403 (forbidden).  That kind of implies that site is blocked... (but why would it be blocked?) Strange.

Anyway, this is almost certainly a network/proxy issue as others have also pointed out.  Have you tried just configuring Synaptic with the proxy settings and using that instead of "apt-get"?

To answer your last question:  I like helping people and I like Linux, that's why. :)  (Oh and I like getting thank-you clicks :P )

---

### Post by Ultimate_goblin on 2008-10-15
All I know is that I have the same problem also with cGmail, that can't gain access to the internet, or with screenlets that need access to the internet (like weather or finance) or audio\video devices that need web access to download codecs.
Yes, it is clearly a proxy problem. I can't get it to work with Synaptic either. There is a similar [thread]("http://ubuntuforums.org/showthread.php?t=828557&highlight=installing+packages+problem+proxy") here in the forum, do you suggest me to try that and good luck?:confused:
(Another thread [here]("http://ubuntuforums.org/showthread.php?t=929092&highlight=proxy"))
P.s.: no authentication required in this process... weird!

---

### Post by ByteJuggler on 2008-10-15
> **Ultimate_goblin said:**
> All I know is that I have the same problem also with cGmail, that can't gain access to the internet, or with screenlets that need access to the internet (like weather or finance) or audio\video devices that need web access to download codecs.
Yes, it is clearly a proxy problem. I can't get it to work with Synaptic either. There is a similar [thread]("http://ubuntuforums.org/showthread.php?t=828557&highlight=installing+packages+problem+proxy") here in the forum, do you suggest me to try that and good luck?:confused:
(Another thread [here]("http://ubuntuforums.org/showthread.php?t=929092&highlight=proxy"))
P.s.: no authentication required in this process... weird!

Do you know what type of proxy is being used?  Is it IIS or Squid on Windows or Squid on Linux or what?

---

### Post by Ultimate_goblin on 2008-10-15
No, I don't know... the only thing I can tell is that there is this .pac file at [http://proxy.ucd.ie/proxy.pac](http://proxy.ucd.ie/proxy.pac) that contains some information, like the port of the proxy and some other stuff.

---

### Post by ByteJuggler on 2008-10-15
> **Ultimate_goblin said:**
> No, I don't know... the only thing I can tell is that there is this .pac file at [http://proxy.ucd.ie/proxy.pac](http://proxy.ucd.ie/proxy.pac) that contains some information, like the port of the proxy and some other stuff.

Hmm, that's not opening from here.  

Anyway, what happens when you enter some of the "blockd" url's in your browser?  Does tha that also generate 403 errors or does the URLs open?

---

### Post by Ultimate_goblin on 2008-10-15
Not opening? Have you tried to save it and then open it? Worked for me, a bit strange tho.
anyway, I tried to connect to [http://it.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://it.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2) (if that was what you asked) and tells me error 404 Not Found > The requested URL /ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2 was not found on this server.
Apache/2.2.3 (Debian) Server at it.archive.ubuntu.com Port 80
Is that it?
I have to leave now, I'll log in tomorrow. Thanx a million for your help!

---

### Post by Earl_Maroon on 2008-10-30
I was experiencing the same problem. I saved my .pac and copied the proxy address and port into Synaptic's proxy configuration. Now everything seems to be working.

---

### Post by Ultimate_goblin on 2008-11-01
YOU ARE A GENIUS.
I just inserted [http://proxy.ucd.ie/proxy.pac](http://proxy.ucd.ie/proxy.pac) instead of proxy.ucd.ie!! Now everything works, thanks a mil!!!

---


---
title: "Proxy authentication error in update manager"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by mgmoore on 2008-08-11
When i run the update manager
Here is the error I'm getting:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/po...8.04.3_all.deb](http://security.ubuntu.com/ubuntu/po...8.04.3_all.deb)
407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied. )


W: Failed to fetch [http://security.ubuntu.com/ubuntu/po...ntu2.1_all.deb](http://security.ubuntu.com/ubuntu/po...ntu2.1_all.deb)
407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied. )

when I do an "export" on command line I get:
...
declare -x http_proxy="http://:8080/"
declare -x no_proxy="localhost,127.0.0.0/8,*.local"

in system -> pref -> networking proxy I'm using the correct proxy with the correct port, I've tried with and without "details" having information in there.

When I run apt-get it fails. I've tried changing http_proxy to
http_proxy="domain\\user.password@proxy:port"
but still no luck.

Help? :D

---

### Post by mgmoore on 2008-08-18
Anyone? Help?

---

### Post by Riffer on 2008-08-18
Is this a home setup?  If it is why do you have a proxy?

Things to try and you could always go back if they don't work.  Turn off the proxy settings.  And try another server, found in drop down menu System > Administration > Software Sources.

---

### Post by mgmoore on 2008-08-18
I'm running ubuntu on a spare work computer to see if I can get nagios working, and so I can just getting better with linux and help get my workplace more involved with non-windows solutions. So thats why I have to go through a proxy.

I tried changing to the "main" server, with still no luck. Can you confirm that I have the right format in my export file?
Any other ideas?

btw, here is the error I get when I try a different server and run the 'reload" it immediately asks for, it gets to 36/66
then error:
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/Release.gpg)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/Release.gpg](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/Release.gpg)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Riffer on 2008-08-18
> **mgmoore said:**
> 
When I run apt-get it fails. I've tried changing http_proxy to
http_proxy="domain\\user.password@proxy:port"
but still no luck.

Help? :D

Shouldn't the slash's be // instead of \\.

And shouldn't the @proxy:port be something like 

@192.156.1.1:3128? Or something like that?

---

### Post by Riffer on 2008-08-18
BTW I generally set my proxy in the GUI supplied found under System > Preferences > Network Proxy.

---

### Post by mgmoore on 2008-08-18
I've tried changing the slashes and I get the same error. I do have the proxy set in the gui to what it should be.

When I apt get I notice that it's having problems trying to talk to the proxy server correctly from what looks like formatting to me.
To pick a random line of error:
W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'mypassword@proxyserverip'

Where "mypassword" is my actual password, and "proxyserverip" is the actual ip of the proxy server.

---

### Post by Riffer on 2008-08-18
Like you I'm at a bit of lose here.  I wonder though if you have your computer's ip correctly set.  Off the top of my head I would think have that set in one of two ways.  Either a static IP address or DNS.

Check to see what you have on your Windows machine and then check to see what you have on your Ubuntu machine.

It seems to me that the server is looking for a password and that is generally done when you login. 

Hmmmm.  That could also mean that your login isn't recognized by the server.  If your Ubuntu comp has a different name and password then your windows account that could explain why you can't get out.  Try setting a user with your windows login name and password.  Log off and switch to the new user.

---

### Post by mgmoore on 2008-08-18
I'm getting an ip automatically on my ubuntu, it's in the correct range of ips. BTW, I can browse just fine, it's only the apt-get functions which are not working.
Tried making account with the same info as windows login, su'ed into that account, tried apt get, same error.

---

### Post by Riffer on 2008-08-18
> **mgmoore said:**
> I'm getting an ip automatically on my ubuntu, it's in the correct range of ips. BTW, I can browse just fine, it's only the apt-get functions which are not working.
Tried making account with the same info as windows login, su'ed into that account, tried apt get, same error.

Like you I'm a bit at lose also, I would hazard that your proxy is fine and that its something at the server side.  Try  using the "main server" or if need be a few others.

I did get those type errors due to the server I had chosen.

---

### Post by appier on 2008-08-18
In System -- Administration -- Synaptic Package Manager, select Settings, then the Network tab.  Have you set up the proxy server there?

---

### Post by Riffer on 2008-08-18
[http://ubuntuforums.org/showthread.php?t=400210](http://ubuntuforums.org/showthread.php?t=400210)
[https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1320](https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1320)
[http://www.linuxquestions.org/questions/ubuntu-63/problems-with-apt-get-synaptic-and-proxy-454026](http://www.linuxquestions.org/questions/ubuntu-63/problems-with-apt-get-synaptic-and-proxy-454026)

Noticed in a few of the threads people forgot to do a 

sudo apt-get update

in the terminal

Anyway here are a few solutions I found by doing a google with 

"ubuntu update 407 Proxy Authentication Required"

---

### Post by mgmoore on 2008-08-18
I've tried several different servers they all do the same exact thing. If it helps, my boss said when he tried the same thing I'm doing he had the same issues. He believes it to be some sort of error occurring because we're having to get past a firewall that requires authentication. I don't understand why I can browse just fine, but can't run apt-get or use the update manager.
I'll take a look at your most recent post. Thanks for the info.

---

### Post by mgmoore on 2008-08-18
Appier- it was blank, I put my proxy info in there, put in username/pass  ... still no workie. Same exact error.

---

### Post by appier on 2008-08-20
Wow, given the thorough advice from Riffer and the proxy, I thought you would probably succeed. I am at a loss.

If you set up the proxy with the appropriate IP address and port, it is possible that your firewall has some of the protocols blocked.  Does your company have a specific person that configures your firewall?  If so, contact him to make sure these protocols are permitted through your firewall.

---

### Post by appier on 2008-08-22
If all else fails, is this a computer you can get permission to take home with you, and use your direct connection to the internet to bypass all of the proxy problems?  Another potential solution is if your IT guys have a direct connection somewhere you can use temporarily to get not have to deal with the proxy for a few minutes.

---

### Post by robin2538 on 2009-11-16
I also have the same problem, but I noticed that update manager tried to get the file from cache first. So I copied all the files the update manager wanted from the error message and manually got them. I could do it with wget with proxy setting. Then I moved those file into /var/cache/apt/archives and rerun the update manager again. Viola!!! It worked.

So the concept is to get those files and put them into /var/cache/apt/archives.  It doesn't matter how you get them. :p

---


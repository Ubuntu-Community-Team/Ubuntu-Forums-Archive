---
title: "New ISP. I must use windows?"
date: 2008-06-03
forum: Other OS Talk
---

### Post by whitefang5412 on 2008-06-03
Anyone in the united states use AT&T? I'm switching because comcast wont fix a 2 month old problem. The lady at AT&T told me I must have windows. I don't know if thats for them to install the internet or what. I went ahead and re-installed it for now, and when they leave my house tuesday from hooking up my new internet, I guess I will run a live disk of fedora and see if my internet works. Funny how people don't know about other OS's and tell you its required that you use windows.

---

### Post by SunnyRabbiera on 2008-06-03
A lot of them only like windows, thats why i stick with comcast as even though they want people to use windows at least they partially support other operating systems.

---

### Post by wolfen69 on 2008-06-03
i have at&t and have no problems with dsl. just open your browser and type: 192.168.0.1

then user name and password. you should have no problems. those people at att have no clue sometimes.

---

### Post by whitefang5412 on 2008-06-03
> **wolfen69 said:**
> i have at&t and have no problems with dsl. just open your browser and type: 192.168.0.1

then user name and password. you should have no problems. those people at att have no clue sometimes.
True. Like I said. I will just let them do their thing with windows, and I assume you somehow got my I.P. write there, that is mine right? If so I will right it down. Comcast never fixed this like, 2 month old problem in my area, and I'm tired of being without internet almost daily. Got AT&T u300 cable coming, and elite DSL. w00t! I think another thing cool about AT&T is the fact that they have those wifi hot spots around the nation.

---

### Post by DreamcastJack on 2008-06-03
It doesnt matter, I had AT&T and used Ubuntu.. so it doesnt really matter.

---

### Post by wdaniels on 2008-06-03
They usually say that they only support Windows because Linux is too variable - their technicians would need a lot greater knowledge of things to be able to support everybody using all the various Linux distros and different ways of doing stuff. Basically, it's not conducive to being able to develop "capability" through processes in the way these corporations like to do. So the official line is always that you need Windows, just because Linux is such a small market for them that they can do that, even though it's not technically a requirement.

The address 192.168.0.1 is just part of a standard range of IP address reserved for [private networks]("http://en.wikipedia.org/wiki/Private_network") - it is the one typically used by a network router by default, but depending on the exact make/model it could be slightly different. Just make sure you ask whoever comes to install the equipment for the IP address of the router and the login credentials. But almost certainly they will set it up as a simple DHCP network so Ubuntu will be able to join the network automatically anyway - you would only need the router's IP address if you wanted to change some settings.

---

### Post by 4Orbs on 2008-06-04
I have had at$t dsl for nearly six months. They give you a cd that guides you through the initial account setup including username, password, mail, disclaimers and legal b.s. I honestly don't see how its possible to activate your new account without using the cd which means (in my opinion) that running the cd in Windows is mandatory. Now that my account with at?t is established, I think I could probably erase Windows and use Linux exclusively, but if something happens to break my connection and it becomes necessary to run the setup cd again, then reinstalling Windows would also be required. Thus I will probably be dual booting forever. Am I mistaken in my assumptions?

---

### Post by wdaniels on 2008-06-04
> **4Orbs said:**
> if something happens to break my connection and it becomes necessary to run the setup cd again, then reinstalling Windows would also be required. Thus I will probably be dual booting forever. Am I mistaken in my assumptions?

Well, if they don't provide any other mechanism to setup the account, recover/modify such details etc. then probably, yes, you will need to keep your Windows partition, or keep a Windows VM in Linux for that purpose. But if you take the time to look into it, I'd be surprised if this setup CD is *strictly* the only way. Maybe they have a web interface? Or perhaps they would be prepared to do it over the phone?

In any case, you might want to test whether the application on the CD runs through Wine - most simple programs do these days. It's important to let AT&T know that you would like the possibility of setting up your account using Linux, even though it might seem pointless - it's only through customer demand that these things will ever change.

---

### Post by MaxIBoy on 2008-06-04
I don't know, installers don't always work under WINE, because Unix-like OSs don't have C drives. That's what I ran into, anyway.



As for Comcast, that's what we have, and they always throttle us down. I'm usually getting less than a tenth what we're paying for. My dad doesn't notice, he only checks email, but I am truly suffering here. The only way to get them to stop is to complain loudly, and my dad refuses.

---

### Post by whitefang5412 on 2008-06-04
I'm staying home from work next tuesday. I'm going to tell them I'm running linux. I don't think anything would happen for me to have to run the installer. I think running the installer is just to set up the modem and get it working, and after that everything is presto. I will ask for the I.P.

---

### Post by chris4585 on 2008-06-04
I have DSL from AT&T no problems, works great.

---

### Post by eriqjaffe on 2008-06-05
I set up my AT&T DSL without putting the CD in at all.  In fact, I never even took the CD out of the little cardboard envelope it came in.

I just hooked the modem up and navigated to 192.168.0.1 and set it up direclty on the modem.  IIRC, AT&T even provided instructions for doing it.

---

### Post by stream303 on 2008-06-06
Unless your ISP's *TOS*, terms-of-service prohibit using Linux there should be no problem - BUT as we've seen, they only officially support Windows and in some cases Apple OSX if problems during setup or operations happen, otherwise you are on your own.

There is good networking support here in the forums, and you may also want to visit other sites like dslreports.com for further information.

---

### Post by mivo on 2008-06-06
> **whitefang5412 said:**
> True. Like I said. I will just let them do their thing with windows, and I assume you somehow got my I.P. write there, that is mine right? 

No, that is one of the common IPs of DSL routers, If you use it in a web browser, it is likely to bring up the configuration of the router (in the browser). That is not dependent on the operating system. You don't need Windows for DSL. :) 192.xxx.xxx.xxx is always a local IP address (or within a local network), it's not "real" internet address. (It is, but not in the way most people understand it.)

---

### Post by CREEPING DEATH on 2008-06-06
Do NOT use AT&T!!!!!
You're in Houston, here are two very good locally owned alternatives:
[http://www.oplink.net/](http://www.oplink.net/)
[http://www.aldridge.com/](http://www.aldridge.com/)
I use Aldridge but I've worked for them before, they're mainly commercial and don't provide any support or email.  Oplink has a great reputation among those that use it, the computer store I worked at referred a lot of people there (from Comcrap/TWC and SBC/AT&T) and they all had really good luck with it.

CD

---

### Post by ChameleonDave on 2008-06-06
Just tell them to run you through what they would tell someone who has Windows.  You can then translate that into Linux practice.  It's just a matter of the correct numbers to input.

I'm with AAPT in Australia.  They send out Windows CDs etc, but they're not necessary.

---

### Post by Barriehie on 2008-06-06
Here in Las Vegas COX pretty much is the only broadband supplier and they get all flustered if not windows.  I was fortunate enough on my last tech support call to get a tech that also uses Ubuntu and my issue wasn't OS related.  My cable modem was fried!  With windows I had to use the install CD but with Ubuntu I didn't have to load any drivers.  It worked right out of the box with all of the installed hardware.  Also, won't **[COLOR=Blue][whatismyipaddress.com]("http://whatismyipaddress.com")[/COLOR]** work for finding your IP???

Barrie

---

### Post by 3rdalbum on 2008-06-06
> **Barriehie said:**
> Also, won't **[COLOR=Blue][whatismyipaddress.com]("http://whatismyipaddress.com")[/COLOR]** work for finding your IP???

Yes, it will find the IP address of the router *as seen from the Internet*. What the person needs is the IP address of the router as seen from the local network. It's always in the router's manual, or if that fails just do a Google search online.

---

### Post by ch_123 on 2008-06-06
Perhaps they meant that you need Windows to use a USB connection. In reality, most modems are stand alone devices that send out a connection over the LAN. It doesn't matter whats connected to them or what OS they are running as long as they can support LAN.

---

### Post by DigitalDuality on 2008-06-06
> **whitefang5412 said:**
> Anyone in the united states use AT&T? I'm switching because comcast wont fix a 2 month old problem. The lady at AT&T told me I must have windows. I don't know if thats for them to install the internet or what. I went ahead and re-installed it for now, and when they leave my house tuesday from hooking up my new internet, I guess I will run a live disk of fedora and see if my internet works. Funny how people don't know about other OS's and tell you its required that you use windows.

Comcast operates slightly different in various locations.    Where i'm at they require windows as well.  You have to run some win or os x proprietary software to connect your pc directly to the modem on initial setup.   After that it's cake.

This is what i did: 
Ran Windows in a VM, ran their crappy software while connected directly to the modem.

Hooked my router to the modem, cloned the IP from the VM Windows Machine.

Voila.

I was told the reason they do this is because they want you to pay extra to hook up a router, about $5 a month more called a networking fee or some crap like that.  Screw em.  I haven't had a win box on my network for over a year and i'm running 10 machines on a 24 port switch, including hosting my own email and webserver.

---


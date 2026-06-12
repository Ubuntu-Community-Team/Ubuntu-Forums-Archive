---
title: "Firewall settings"
date: 2013-09-28
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-09-28
I am facing a problem with one multiplayer game that needs the firewall (ufw) to have a few open ports. My firewall is usually in deny all mode. When i open those ports, i can use the application well. When they are closed it can not be used. I am concerned about security issues in such cases. Can any one kindly advise me any better option say a better firewall tweeking for such cases.

---

### Post by 1clue on 2013-09-28
Is there a specific server on the other end?  You could open them only for that server.

---

### Post by 3dmatrix on 2013-09-28
I am not sure about any specific server. Usually most games like on Steam or Urban Terror mention certain ports to be opened. They do not mention anything else. In that way i will have to keep a lot of ports open and that is unsafe. So what is a better alternative ?

---

### Post by 1clue on 2013-09-29
Sorry if I'm absolutely, completely ignorant of current gaming.

Maybe you should google the game and "security" together, to see how people configure their firewalls.

I can think of these ways to reduce the likelihood of badness with open ports:
[LIST=1]
[*]Reduce the number of locations you accept connections from.  This means only open them to the remote box, not to the world.
[*]Set up a proxy.  This is complicated.  The proxy needs to understand what protocol is being used, and know when it's not correct.  Then it can block that traffic.
[*]Alter the port number.  This requires that the remote system know what the new ports are, which might not be practical with a central server or with random strangers at the other end.
[/LIST]

The proxy will introduce a latency.  You're adding a host in the middle, and that host is processing data.  That might also be incompatible with gaming.  However it gives you an extreme control over networking and security in general, assuming you know how to configure it and have appropriate filters.

---

### Post by gerowen on 2013-09-29
If you need a certain port to be open, especially for a gaming service like Steam where you might connect to a dozen different servers across those same ports, you're kind of limited as to how tightly you can lock it down.  However, if you know specifically what IP addresses you will be connecting to across those ports, and you're confident those IPs won't change, such as when you and your buddies set up a Quake server and you only want that server to be allowed to access you on a specific port, or if you're hosting the server and you know what IP addresses your friends will be connecting from, then you can designate IP addresses that are allowed to access those ports.  You can also tell it whether or not to log access requests on those ports so you can review your logs to see who has and has not been using those ports.

Using GUFW, also known as "Firewall Configuration" in the Ubuntu "System Settings" application, you can set up and tweak firewall rules to your heart's content.  Be aware of this though.  Unless you are running a game server, and you have forwarded those ports on your router to the computer running the server, then when anybody on the internet tries to access you, all they see is your router, and not your computer.  Opening those ports on your local firewall allows applications you run to establish connections to outside computers, and once a line of communication is open then your programs will function fine, but your router plays the role of traffic cop in that instance.  All the remote end sees is your router's IP address, and it sends the traffic to that IP address.  Your router then does its job by "routing" that traffic to the appropriate machine on its local network.  The only way people would be able to look directly at your computer would be if they compromised your router, if they were on the same network as you, or if you configured your router to specifically forward certain ports to your computer.  Because of this, routers can also be referred to as hardware firewalls, because it is a device that physically separates you from the internet, gives you a private IP address, and can be programmed to perform certain actions on traffic that goes through it as it passes between the internet and your internal network.

Anyway, I've babbled enough.  Just poke around in gufw and I'm sure you'll find all the options you need.  Here's a screenshot of some of the "Advanced" options available.
[ATTACH=CONFIG]246579[/ATTACH]

---

### Post by 3dmatrix on 2013-09-29
Thanks for your reply. I am ofcourse behind a router. But for steam can you tell me which port to open so that i do not have trouble accessing the servers.
On this page : [https://support.steampowered.com/kb_article.php?ref=8571-GLVN-8711](https://support.steampowered.com/kb_article.php?ref=8571-GLVN-8711)
It mentions a lot of servers, rather a full range of servers. When i open the first range i still find that during login it gets stuck. But after login it can work. So may be it uses multiple ports to work. Can you kindly give some advise regarding this. Moreover, i would like to know if it is possible (in gufw) to restrict only the Steam client to access that port, if so how and will it be of any use (added security) ?

---

### Post by 3rdalbum on 2013-09-29
> **3dmatrix said:**
> Thanks for your reply. I am ofcourse behind a router.

Then you've already got a firewall in the router, and you don't need to be using a personal firewall too. Simply turn GUFW off (or "Allow all") and you'll remain just as safe.

Also, just because a port isn't explicitly blocked, doesn't mean that it's "open"; let me use an analogy.

Using a router's firewall AND a personal firewall is like unplugging your phone, AND THEN taking the phone off the hook. Obviously, taking the unplugged phone off the hook is not going to help, you're already not going to receive any phone calls because the phone is unplugged!

If the phone was plugged in and on the hook, you can receive phone calls. There's nothing blocking that. But if the phone rings and nobody's at home, or nobody's listening, then nobody will pick up the phone and so the call won't actually be connected. Same thing with the firewall - if a port is not blocked, but there's no program currently listening on that port, there will not be a connection to your computer. The end result, really, is the same as if you had the port blocked, or if you had your telephone unplugged.

Just because somebody can dial the number and make your phone ring, doesn't mean that they can speak to you. They can only speak to you if you're home, and currently listening for an incoming call, and actually pick up the receiver. If any of these things is not true, they can't speak to you. If the program isn't running, or the program isn't listening for an incoming call, or the program decides not to pick up, then no attacker can connect to your computer on that port.

If in doubt, you should read up a bit more about what a firewall actually does and how network connections ("sockets") work. I'm sure Google can hook you up with an article.

---

### Post by 1clue on 2013-09-29
First, I disagree with 3rdalbum's statement that redundant firewalls are unnecessary.  Defense in depth.  If they get through your router and hit some other box on your LAN then having that second firewall right on the box helps a bunch.  EVERY medium or large business has at least two firewalls, and then some of them want your server to have its own security complete with an audit by a different IT office inside the company.  IBM was like that when I worked there.  They had a firewall protecting their demilitarized zone, then they had another one protecting their normal network.  The normal network rules were that no connections could originate from outside.

Second, if you're using a cloud VM or real hardware at linode or similar AND your users are all known to you, they might have two-factor authentication as an option with your hosting company.  Then before you connect your game, you connect the VPN.  The hosting service calls your cell phone, you enter a code and then you get access.  If you have a limited number of users, you can give each user a VPN account and register their phones.

In this option, you don't have ANY ports open to the net.  You're exposing a VPN endpoint, which is designed to be pretty secure and would be handled by somebody else anyway, but not your game and not directly on your server.

---

### Post by 3dmatrix on 2013-09-29
I am just an ordinary user, not a corporate but i would certainly not like any one to barge in to my system. So i am a little concerned about my privacy. Is it possible in any way to configure GUFW to allow only the Steam client to use the port open for it ? Does that makes it secure in any way ?

---

### Post by 3rdalbum on 2013-09-29
> **1clue said:**
> First, I disagree with 3rdalbum's statement that redundant firewalls are unnecessary.  Defense in depth.  If they get through your router and hit some other box on your LAN then having that second firewall right on the box helps a bunch.

Dude, this is a guy wanting to do some online gaming, and he's posted to Absolute Beginners Section. We're not talking about a corporate network holding industrial secrets, we're talking about a desktop user with maybe a little home network. If the user's router is set up to forward the desired port(s) and deny incoming connections on all the others, there's no "getting past the router and targetting another box on the LAN".

3dmatrix:  No, there's no application-level capabilities in the Linux firewall. However, you might be making things more difficult than they really need to be. Your computer will not listen for any incoming connections, unless a program is specifically listening on a particular port. If you're talking about an outgoing port, then just allow all outgoing ports. Outgoing connections can only be initiated from within your computer anyway, and if you don't trust everything running on your computer then you'd better wipe it and reinstall.

---

### Post by 1clue on 2013-09-30
@3rdalbum: Telling beginners there's nothing to worry about is destructive.  He asked a question in a way that leads me to believe he's at least sort of aware of the issues.  I told the truth.  And it's not just that the game system might be compromised to attack other systems on the LAN, but other systems on the LAN might be vulnerable and attacked, which might in turn be used to attack the game system.  My home network has defense in depth for every device.

@3dmatrix: I'll get out of the way.  People who tell people to not worry about security make me really cranky.  [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) has the start of what you need to know.

---

### Post by 3dmatrix on 2013-09-30
Thanks, I am not a expert in firewall setup so would just like to tell you about my firewall setup and need your advise.
My firewall is usuall in deny all mode and reject incoming and outgoing.
Just those few necessary ports are kept open, for general surfing and online gaming.
Do you think it is good enough ?

---

### Post by 1clue on 2013-09-30
The best defense is an educated evaluation of the system and its needs.  You know the situation more than I do.  [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

I know that's hugely unsatisfying, but you gotta learn sometime.  Google around and see what others are doing, see if anyone complains of security issues.  I'm not a gamer, and I don't know how this stuff is used or what vulnerabilities it has.

My advice is to not put anything on this system not related to the game, and definitely don't put any sort of financial information on it.  Do the best you know how for security, it can be an ongoing process.

As I said before, I have defense in depth for everything in my home.  I'm not saying that's good enough, but most people I know think it's overkill.  I'm not claiming to be any sort of expert, but personally I wouldn't stick with a SOHO router's firewall as the only protection for anything.

I HAVE been hacked in the past on Linux, and I thought I had a secure system at the time.  If I hadn't had monitoring tools installed or hadn't been watching them, I would never have known.  I suspect a few Linux users on this forum have malware or have had security breaches and don't know.

---

### Post by 3dmatrix on 2013-09-30
Thanks all of you

---

### Post by DuckHook on 2013-09-30
I can appreciate both points of view. Like *1clue*, I defend in depth with both a router firewall and a further firewall on each Linux box. I block not only incoming ports but outgoing too, and open only exactly those that I need. Moreover, I don't trust the impenetrability of commercial routers, so have replaced their firmware with DD-WRT. Add in apparmor profiles, a totally locked-down browser (no scripts, no cookies), disable password SSH access on all devices from routers to printers to NASes, use of truly randomized 512-bit keys and encryption of all significant partitions, and it's reasonably hardened. And yet, I have no illusions about the fact that a truly dedicated cracker could crack my system in little more than an hour. Although *1clue* referred to a heavy-duty corporate environment, all I have is a little home network with a handful of nodes and I find that implementing a more stringent level of security is not hard and definitely need not be the purview of only corporate environments.

Having said all that, I also understand *3rdalbum's* point: There are times when a focus on security becomes so bloody-minded that the system is rendered unusable to the intended user. For years, my wife simply could not abide a locked-down browser. I cringed every time she blithely clicked on whatever dialogue box a website brought up, but it was either bite my tongue and look the other way, or get an earful about how awful, cussed and useless Linux was. A hardened browser was simply not in the discussion until she started getting eerily targeted spam that seemed to know exactly what sites she had been visiting. She's more open to hardening her browser now, but every additional security measure is like a root canal, so it's not as simple as lecturing her about "defending in depth".

Every security setup is a personal matter. At least, in the non-corporate environment it is. You weigh the heightened security against the inconvenience, and, depending on your risk tolerance, you decide where on the security spectrum your own preferences fall. For *1clue* and me, our comfort zone is well towards the maximum "paranoid" end. For people like most of my friends and my wife, it is closer to the "what me worry?" end. The OP has to determine how much risk he/she is willing to tolerate. My guess is that any Linux user is open to hardening their system far beyond the norm (as defined by Windows), else they would not have gravitated to Linux.

---

### Post by 1clue on 2013-09-30
@DuckHook,

I agree totally with your post.  There must be a balance between security and utility.  Frankly I can't abide a locked-down browser, certainly my wife can't.

Moreover, you can't just go into it green and get defense in depth that makes sense.  That's why I linked to [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) so many times.  You gotta start somewhere.  You can start with just the basics, set up a basic Linux firewall and learn how it works.

You can't be so paranoid you can't use the computer, but you also can't be totally ignorant of the risks associated with what you do.

Start out with blocking everything.  Then open a port or two you need, google the security risks associated with the application and see what you can do about them.

Most, install some sort of scanner and configure it correctly right away, and READ THE REPORTS!

---

### Post by 3dmatrix on 2013-10-05
If i think of creating a script that i will execute to open certain ports just before playing games and then close them with another script after playing games then can that be of any help ? If so what commands should i use ?

---

### Post by 3dmatrix on 2013-10-10
Any suggession ?

---

### Post by 3rdalbum on 2013-10-10
I'll probably get shouted at again if I reply, but read my telephone analogy again. The port can't be opened if there is no program currently listening to it, making your idea very redundant and unneccessary. Just like how someone can dial your phone number but not actually get connected unless someone is at home to pick up your phone.

It doesn't matter if the firewall is blocking the port or not, if there is no program currently running to listen for connections on that port, then there will be no connection. Full-stop. You might want to take a quick look at a simple explanation of how sockets and firewalls work as I'm sure qualified people can explain it better than me.

TL;DR: Your script idea is totally unnecessary - with it or without it, an attacker will not be able to connect when your game is not running.

---

### Post by 3dmatrix on 2013-10-11
I do understand your point but i am not an expert so how do i know if an application or malware is using a port or not. I do not wish to behave like a security guard all the time.

---

### Post by fantab on 2013-10-12
> **3dmatrix said:**
> I am facing a problem with one multiplayer game that needs the firewall (ufw) to have a few open ports. My firewall is usually in deny all mode. When i open those ports, i can use the application well. When they are closed it can not be used. I am concerned about security issues in such cases. Can any one kindly advise me any better option say a better firewall tweeking for such cases.

What happens if you 'allow' the application in UFW? [http://manpages.ubuntu.com/manpages/raring/en/man8/ufw.8.html#contenttoc7](http://manpages.ubuntu.com/manpages/raring/en/man8/ufw.8.html#contenttoc7), If you are running the game via Wine then perhaps you will have to allow Wine (I am not sure). Also there is a possiblity of Windows Virus entering you system through Wine.
```
sudo ufw allow application/game
```

Or you can allow the 'Service' the game represents. You can find this out from 'System Monitor' GUI. [https://help.ubuntu.com/community/UFW?action=show&redirect=Uncomplicated_Firewall_ufw#Services](https://help.ubuntu.com/community/UFW?action=show&redirect=Uncomplicated_Firewall_ufw#Services)
```
sudo ufw allow service
```

Also if you can find out what port your game uses or its IP or subnet then perhaps we can work to just allow those.

Security is a personal thing. It depends on your level of paranoia and the kind of data you are protecting. You can either use a simple Lock to lock your house or deploy thousands of Dollors worth 'elaborate' security systems. For a simple Home computer two firewalls, in my opinion, is an overkill. Ubuntu on its own, without a firewall, is safe enough for simple home computing.

My two cents....

---

### Post by 3rdalbum on 2013-10-12
> **3dmatrix said:**
> I do understand your point but i am not an expert so how do i know if an application or malware is using a port or not. I do not wish to behave like a security guard all the time.

Easy. On a default Ubuntu install, nothing listens for incoming connections from the internet (only from the local network, which is no problem). The chances of you getting malware on desktop Linux are not even worth thinking about for an ordinary desktop user; of course if you were a sysadmin running a network of business computers things would be different, but you're not doing that. So, the only things listening will be things you've installed yourself that are running and have some sort of obvious internet/network server function. It's not like your file manager listens for incoming connections, or Gimp, or anything like that. Only servers like file servers, web servers, database servers, and game servers will listen for incoming connections.

There are over 65,000 ports in each direction so the chances of a collision with your game are remote, to say the least. Well-known types of servers use standard ports - for example, web servers always default to port 80 - but games will pretty much just have a randomly-selected port.

My point really is that you don't have to behave like a security guard; you're not a sysadmin, you're a desktop user. Ubuntu provides a secure desktop for ordinary users and a good starting point for people with more complex needs. You seem to qualify as "ordinary user" so you really don't need to do anything else but keep your system up-to-date, don't download random software from the internet, and don't enable any servers that you don't need (and if you need them, learn how to configure them correctly).

---


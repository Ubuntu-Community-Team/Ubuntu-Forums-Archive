---
title: "virus in ubuntu"
date: 2010-11-01
forum: Recurring Discussions
---

### Post by dhiman33 on 2010-11-01
Hey, I want to know exactly why people tell that there'sno need for an antivirus in ubuntu(or any linux distro). Is the sole reason is that ubuntu is much much MUCH more secure than windows?

Or the reason is that share of linux in the market is very small compared to windows, for that most people and companies use windows, and for that the makers of viruses target mainly windows, not linux or mac? :guitar:

---

### Post by TNT1 on 2010-11-01
Woo Hoo!

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by bumanie on 2010-11-01
Here's another page worth reading that will help answer your query.
[http://linuxmafia.com/~rick/faq/index.php?page=virus](http://linuxmafia.com/~rick/faq/index.php?page=virus)

---

### Post by Jakiejake on 2010-11-01
> **dhiman33 said:**
> Hey, I want to know exactly why people tell that there'sno need for an antivirus in ubuntu(or any linux distro). Is the sole reason is that ubuntu is much much MUCH more secure than windows?

Or the reason is that share of linux in the market is very small compared to windows, for that most people and companies use windows, and for that the makers of viruses target mainly windows, not linux or mac? :guitar:

Linux won't run .bat which are commonly virus files on Windows
There are a lot of other reasons too!

---

### Post by gandaran on 2010-11-01
windows virus don't work on linux and linux virus aren't known to exist in the wild yet and if they did you would have to do something stupid to actually infect the computer! 
what you should be concerned about is browser malware which is cross platform and can infect any browser.
[see this]("http://www.omgubuntu.co.uk/2010/10/father-of-social-networking-worms-comes-to-linux-and-mac-os-x-via-java/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+d0od+(Omg!+Ubuntu!)&utm_content=FaceBook")

---

### Post by rjbl on 2010-11-01
> **dhiman33 said:**
> Hey, I want to know exactly why people tell that there'sno need for an antivirus in ubuntu(or any linux distro). Is the sole reason is that ubuntu is much much MUCH more secure than windows?

Or the reason is that share of linux in the market is very small compared to windows, for that most people and companies use windows, and for that the makers of viruses target mainly windows, not linux or mac? :guitar:

Basically, all UNIX-like OSes are more or less immune to Windows-type viruses and malwares. The UNIX execution model simply does not allow the vast majority of them to become established. Over the years there have been a couple of viruses coded up which will establish themselves in UNIX, GNU/Linux or Mac OS - if, and only if, the victim is has a really eccentric OS configuration and is playing as Root.

No, it ain't preferential targeting of the biggest market share - its simply that all the MS OSes that have ever been rolled out are grossly vulnerable and they have always been an easy, and fun, target for the mischievous spirits in this world. Why bust a gut failing to hit a UNIX system when you can succeed against millions of Windows boxes?

rjbl

---

### Post by coffeecat on 2010-11-01
> **dhiman33 said:**
> Or the reason is that share of linux in the market is very small compared to windows

That is only true for desktop systems. Out there on the big wide internet, Linux has the majority share of servers. Estimates vary, but it's probably about 60%. Think about that - 60% of all internet servers in the world. That's quite a target for malware coders.

And there are some interesting big names using Linux.

[Yahoo.]("http://toolbar.netcraft.com/site_report?url=yahoo.com")

[BBC.]("http://toolbar.netcraft.com/site_report?url=http%3A%2F%2Fwww.bbc.co.uk%2F")

[Wikipedia]("http://toolbar.netcraft.com/site_report?url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FMain_Page"). I believe it uses Ubuntu.

[Ubuntu.]("http://toolbar.netcraft.com/site_report?url=http%3A%2F%2Fwww.ubuntu.com%2F") :wink:

And possibly the biggest name:

[Google]("http://toolbar.netcraft.com/site_report?url=www.google.com")

---

### Post by HermanAB on 2010-11-01
The small market share of Linux is Microsoft FUD.

In reality, there are billions more Linux machines out there than Windows machines.  Linux dominates the Embedded, Cell Phone, Router, Server and Super Computer markets. Microsoft only dominates the small desktop market.

Put another way, Microsoft's total installed base is about equal to two years worth of Linux device sales and devices last 5 to 7 years.

---

### Post by dhiman33 on 2010-11-01
Hmmm, it seems I shouldn't run programs as root,is it. Does that mean I shouldn't run commands using sudo? But almost 70% of the commands I use starts with sudo! Am I in danger then?:shock:

Also, I am the only user of my pc, does that mean I am the root? Should I create another non-root account?(I'm a noob I can't understand all these things!:oops:)

---

### Post by ronnielsen1 on 2010-11-01
Ubuntu won't let you create a root account by default. You created an user didn't you? sudo is a temporary root. You're fine

---

### Post by dhiman33 on 2010-11-01
:twisted:So if I run a virus meant to destroy ubuntu using sudo what will happen? Do I have to reinstall then?:tongue:

---

### Post by migs73 on 2010-11-01
Yes.

You will have destroyed your system, more likely you shall have done so by running a malicious command than a virus though.

Please remember you allowed it to get access to the root, it cannot do so on its own.

---

### Post by dhiman33 on 2010-11-01
:-sI am confused. I mean, I have to use sudo to connect to internet and to install or uninstall anything. What if a virus gets executed in these processes? Once again I'd like to tell I see most of the commands used in terminal starts with sudo. Now if I connect to the net using sudo command/s then I become the root right, and so after entering any sudo command I become the root, and then become vulnerable.

For example, let's say I use sudo dpkg -i anypackage. After I execute this command, I become the root for the rest of the session. Now if I go to a site which contains linux viruses I can become infected!(just like windows!!!!@$%!!!):shock:

---

### Post by Elfy on 2010-11-01
How are you connecting to the internet as root?

When you install something - it does that and stops - it does not then go off and do anything else without you telling it to do so.

I think you are getting confused.

---

### Post by dhiman33 on 2010-11-01
To connect to net, I have to execute these----
sudo ifconfig wlan0 192.168.1.2
sudo iwconfig wlan0 essid WA1003A
sudo pon dsl-provider

So when I execute any sudo command, it gives me a momentary privelege, is it? Then once again I become the unprivileged user.

Ok, let us consider another situation.Let's say I've just executed sudo to do something and for this I've provided my password. Now to execute the next sudo command I wouldn't require a password for some time. Within this time period, can someone compromise my system as root since they wouldn't need the password?:-\"

---

### Post by coffeecat on 2010-11-01
> **dhiman33 said:**
> To connect to net, I have to execute these----
sudo ifconfig wlan0 192.168.1.2
sudo iwconfig wlan0 essid WA1003A
sudo pon dsl-provider

Why? Is network manager not working?


> **dhiman33 said:**
> Within this time period, can someone compromise my system as root since they wouldn't need the password?:-\"

Who? Someone in the same room as you?

---

### Post by Boondoklife on 2010-11-01
When you execute sudo it gives that process elevated privs, not the user. The only way that this could be hijacked is if that process in turn executed a malicious script or some kind of bug in the application executed some arbitrary code passed to it by you.

As far as someone else not needing root, they would. First of all you should never allow a ssh login as root, secondly even if someone logged in as you again it would not work as the sudo is tied to your session. If you are really paranoid, you can turn the timeout off in the /etc/sudoers file (just google it).

---

### Post by 3rdalbum on 2010-11-01
> **dhiman33 said:**
> To connect to net, I have to execute these----
sudo ifconfig wlan0 192.168.1.2
sudo iwconfig wlan0 essid WA1003A
sudo pon dsl-provider

So when I execute any sudo command, it gives me a momentary privelege, is it? Then once again I become the unprivileged user.

Ok, let us consider another situation.Let's say I've just executed sudo to do something and for this I've provided my password. Now to execute the next sudo command I wouldn't require a password for some time. Within this time period, can someone compromise my system as root since they wouldn't need the password?:-\"

Theoretically, yes, it can be done. Easier than that, actually. However, you're focussing too much on 'sudo' itself and less on what sudo allows.

Sudo allows you to have only a very limited amount of code that runs as root, and run everything else as user. A security flaw in anything running as user will not automatically mean that an attacker has complete control over your system - the attacker would also need to 'get root' in some way, which would be pretty hard if that particular user was not an administrator.

Most people don't need to run 'sudo' to start their internet connection - Network Manager uses "Policykit" to allow controlled access to certain parts of the system that used to be root-only. Software installation in Ubuntu Software Center is done through Policykit as well, not Sudo. Eventually everything will move over to Policykit, which doesn't have Sudo's limitation.

Security on Linux doesn't end with sudo, of course. Users are prevented from running just any executables, by use of the executable flag. Anyone knowledgeable enough to be able to set the executable flag is more likely to be careful with its use.

You might also have heard about security problems caused by "maliciously-crafted PDF files" and similar. The AppArmour (Ubuntu, SUSE) and SELinux (Fedora, Red Hat) systems prevent programs from being able to be exploited to do anything other than their basic functions, and system-wide Address Space Randomisation also helps to prevent the programs from being controlled in the first place.

Most Linux systems come either with a configured firewall, or no outward-listening programs by default (Ubuntu's approach).

Look at it this way: Ten years ago there were a few Linux viruses and very few Linux users. Today, there are many more Linux users, and no Linux viruses. Linux is on the front line of implementing new security systems.

---

### Post by 3rdalbum on 2010-11-01
> **dhiman33 said:**
> :-sI am confused. I mean, I have to use sudo to connect to internet and to install or uninstall anything. What if a virus gets executed in these processes? Once again I'd like to tell I see most of the commands used in terminal starts with sudo. Now if I connect to the net using sudo command/s then I become the root right, and so after entering any sudo command I become the root, and then become vulnerable.

For example, let's say I use sudo dpkg -i anypackage. After I execute this command, I become the root for the rest of the session. Now if I go to a site which contains linux viruses I can become infected!(just like windows!!!!@$%!!!):shock:

No you do not, that's not how sudo works. Sudo makes the program/command root, NOT you.

You also say "What if a virus gets executed in these processes". No virus can touch *ifconfig*, *iwconfig* or *pon* without root access already! These are root-owned files!

---

### Post by dhiman33 on 2010-11-01
I couldn't find out how to connect to net using network manager, coffeecat. It's a bb connection requiring username/passrd. First, I've to connect to wireless router, then I need to put username/password somewhere. I couldn't figure out how to do that and found out the terminal commands from some site one/two years ago.

I use these commands----
   sudo ifconfig wlan0 192.168.1.2
   sudo route add default gw 192.168.1.1
   sudo iwconfig wlan0 essid WA1003A
   sudo vi /etc/resolv.conf
then, sudo pppoeconf to put username/passwrd
         sudo pon dsl-provider to trigger connection.

Ur 2nd question makes me feel good.So it means my pc is invulnerable from outside?

And   'As far as someone else not needing root, they would. First of all you  should never allow a ssh login as root, secondly even if someone logged  in as you again it would not work as the sudo is tied to your session.  If you are really paranoid, you can turn the timeout off in the  /etc/sudoers file (just google it).'------

What does this mean?

---

### Post by mikewhatever on 2010-11-01
> **dhiman33 said:**
> ...

So it means my pc is invulnerable from outside?

...

That's a step too far. No computer is invulnerable.

---

### Post by janpol on 2010-11-01
Other reasons besides the ones mentioned:

1. Distros: since there are lots of distros, is hard for you to make a virus that installs and works on ALL the distros out there, such amount of work is pointless. 

2. Updates: most successful Windows viruses (like confiker) exploits old-already patched vulnerabilities. There are tons of pirated copies of Windows out there, that doesn't get updates. Also, Microsoft has a fixed update cycle (second tuesday of the month), so, if a vulnerability is found, you have to wait for the second Tuesday of the month to get a fix (unless it's a REALLY serious vuln).

3. Software origin: In Windows, in order to get software, you download it from different sites, in Ubuntu (and most distros) you get software from the repositories.

Still, I think the main reason is that Windows has a huge marketshare, and bad guys do it for the money ;)

---

### Post by migs73 on 2010-11-01
> **dhiman33 said:**
> 

Ok, let us consider another situation.Let's say I've just executed sudo to do something and for this I've provided my password. Now to execute the next sudo command I wouldn't require a password for some time. Within this time period, can someone compromise my system as root since they wouldn't need the password?:-\"

When you say that you don't need the password for some time, this (I am pretty sure I am correct here) only applies to the terminal you are running at that time. If you open two terminals run a sudo command in one, you do not get the sudo privileges in the other. Also run a sudo command in terminal and then try to open Synaptic.... It asks for your password (gksudo). Only if a person or piece of code could hijack your currently open terminal could they run as sudo in that time period. If you left a terminal open after using it with elevated privileges still intact, then again, the fault is yours.

BTW you need to get Network Manager working ASAP.

---

### Post by janpol on 2010-11-01
> **migs73 said:**
> When you say that you don't need the password for some time, this (I am pretty sure I am correct here) only applies to the terminal you are running at that time. If you open two terminals run a sudo command in one, you do not get the sudo privileges in the other. Also run a sudo command in terminal and then try to open Synaptic.... It asks for your password (gksudo). Only if a person or piece of code could hijack your currently open terminal could they run as sudo in that time period. If you left a terminal open after using it with elevated privileges still intact, then again, the fault is yours.

BTW you need to get Network Manager working ASAP.
If a bad guy hijacks a terminal with sudo privilegies they can create an account with root privileges (or with sudo capabilities) and game over.

But the fact is that is hard to get there (remotely) and really harder compared to windows.

---

### Post by migs73 on 2010-11-01
> **janpol said:**
> If a bad guy hijacks a terminal with sudo privilegies they can create an account with root privileges (or with sudo capabilities) and game over.

But the fact is that is hard to get there (remotely) and really harder compared to windows.

Exactly, so unless someone physically has access to the computer it would be virtually impossible. As always on any computer 'physical access is root access'. That's in someones sig and is worth remembering for any security conscious individuals.

---

### Post by dhiman33 on 2010-11-01
Hmmm, now another question. Can someone run a process on my pc from a remote site/remote pc? If he can, and if he knows my password, then will I be doomed?:lol:

---

### Post by dhiman33 on 2010-11-01
migs73, if I use sudo in a terminal, don't close it and open another terminal and use sudo in that, I need to provide passwrd once again.

however, if I close the terminal after entering sudo, open a fresh terminal, then it wont require a passwrd to execute sudo commands.

---

### Post by Yougo on 2010-11-01
> **dhiman33 said:**
> Hmmm, now another question. Can someone run a process on my pc from a remote site/remote pc? If he can, and if he knows my password, then will I be doomed?:lol:
if someone wants to get remote acces to your computer, you'd have to actually give him permission.

once he is in, you're in for it, but then it'd still be your own fault :)

if someone other than you knows your passwords, it means you must've told him, or allowed him physical access to your system. still your own fault

it all keeps coming down to the user being the biggest security problem ;)

---

### Post by migs73 on 2010-11-01
> **dhiman33 said:**
> migs73, if I use sudo in a terminal, don't close it and open another terminal and use sudo in that, I need to provide passwrd once again.

however, if I close the terminal after entering sudo, open a fresh terminal, then it wont require a password to execute sudo commands.

But how do they open the terminal to run it?

In answer to your other query, if they know your password then yes you could be doomed (once they pass the firewall that does not accept incoming connections). But they need to know your password. Then it doesn't matter if you have a terminal with temporary sudo BECAUSE THEY KNOW YOUR PASSWORD.

---

### Post by migs73 on 2010-11-01
> **Yougo said:**
> if someone wants to get remote acces to your computer, you'd have to actually give him permission.

once he is in, you're in for it, but then it'd still be your own fault :)


And that ^^^^^

---

### Post by kaldor on 2010-11-01
> **coffeecat said:**
> That is only true for desktop systems. Out there on the big wide internet, Linux has the majority share of servers. Estimates vary, but it's probably about 60%. Think about that - 60% of all internet servers in the world. That's quite a target for malware coders.

And there are some interesting big names using Linux.

[Yahoo.]("http://toolbar.netcraft.com/site_report?url=yahoo.com")

[BBC.]("http://toolbar.netcraft.com/site_report?url=http%3A%2F%2Fwww.bbc.co.uk%2F")

[Wikipedia]("http://toolbar.netcraft.com/site_report?url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FMain_Page"). I believe it uses Ubuntu.

[Ubuntu.]("http://toolbar.netcraft.com/site_report?url=http%3A%2F%2Fwww.ubuntu.com%2F") :wink:

And possibly the biggest name:

[Google]("http://toolbar.netcraft.com/site_report?url=www.google.com")

Add universities and other important organizations to the list. The local universities here are powered by RHEL and SLED, I believe.

---

### Post by janpol on 2010-11-01
> **dhiman33 said:**
> Hmmm, now another question. Can someone run a process on my pc from a remote site/remote pc? If he can, and if he knows my password, then will I be doomed?:lol:
For this to happen, a bad guy needs a way to access you PC remotely (they can just do that per se). If you keep your system up to date, don't install anything that will open a port without securing it, you use NAT and a router firewall, this won't happen. The only ones in danger here are servers, that need to open a port to be accessed from the outside, but most regular users won't open anything to the internet.

But, if you install software from unverified sources (and also it has to be closed source software, otherwise someone will notice malware code or at least you can know what it does and how to remove it) or clic on links sent by spam...you can be infected by something that opens a backdoor....buuuuut, this is really unlikely to happen, since most viruses target Windows (because of the reasons previoulsy discussed).

So, if someone installs a rootkit in your pc, yes you are doomed, but that takes you back to the "virus in ubuntu" discussion ;)

---

### Post by jfbooth on 2010-11-01
I am NO Linux expert and I have read the pros and cons of having an antivirus product running on Linux.  Mostly ... don't need it.  One thing I read lately is that a Windows virus can 'pass through' a Linux machine .. can't infect the machine, but can invade, then move through and on to other Windows machines.  FOR THAT REASON, an antivirus has been recommended by some 'Nix people .. who know a lot more about it all than I ever will.

---

### Post by Boondoklife on 2010-11-01
> **jfbooth said:**
> I am NO Linux expert and I have read the pros and cons of having an antivirus product running on Linux.  Mostly ... don't need it.  One thing I read lately is that a Windows virus can 'pass through' a Linux machine .. can't infect the machine, but can invade, then move through and on to other Windows machines.  FOR THAT REASON, an antivirus has been recommended by some 'Nix people .. who know a lot more about it all than I ever will.

This is very true, if you have a shared drive that a windows box can connect to then you could transmit a virus to it when it gets files from you. The logic behind this is the files will prolly not run in linux or atleast the malicious code will not. But it is still dangerous to your windows partner.

The moral of the story is to use a virus scan if you are worried about this, you can use clamav with samba I believe which will be a great benefit. I personally dont do this as I have an AV on my windows box and im not gonna waste ticks on my linux box.

---

### Post by migs73 on 2010-11-01
Surely the windows people should have the AV? We are not their protectors!!
They should look after their own systems appropriately!

---

### Post by coffeecat on 2010-11-01
> **dhiman33 said:**
> will I be doomed?

We're all doomed - sooner or later. :(

---

### Post by Chronon on 2010-11-01
> **jfbooth said:**
>  One thing I read lately is that a Windows virus can 'pass through' a Linux machine .. can't infect the machine, but can invade, then move through and on to other Windows machines.  FOR THAT REASON, an antivirus has been recommended by some 'Nix people .. who know a lot more about it all than I ever will.

Windows viruses are not active in a Linux environment, so they can "pass through" a Linux machine just like any file can "pass through" a machine.  I find it inaccurate, however, to say that the Windows virus actually does anything like invading [the Linux system] and moving through onto another Windows machine.  It will just be a dormant file.  Somebody has to actively transfer it to a Windows system, where it can come to life and begin to act as a virus.

Depending on what sort of services you're running it can be a good policy to run antivirus software on a Linux system.  For example, if you run a file server and have Windows clients that connect to it, then it would behoove you to run antivirus checks on a regular basis to protect Windows users.

---

### Post by Chronon on 2010-11-01
> **migs73 said:**
> Surely the windows people should have the AV? We are not their protectors!!
They should look after their own systems appropriately!

Yes, they should run AV.  However, if you provide a service it makes sense that you would want to take steps to avoid inadvertently passing an infection to your users.

---

### Post by uRock on 2010-11-01
With the reading of the link in post #2, you'll find the answer to all of these questions.

Here's the link again in case it was missed. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Moved to Recurring Discussions.

---

### Post by del_diablo on 2010-11-01
A good ol' good post:
[http://ubuntuforums.org/showpost.php?p=9737647&postcount=10](http://ubuntuforums.org/showpost.php?p=9737647&postcount=10)

---

### Post by aysiu on 2010-11-01
The simple answer is antivirus itself is a flawed approach to security, regardless of operating system. It is mainly retroactive instead of proactive, and when it is proactive it produces so many false positives as to make it useless.

Imagine if you had a security guard without a brain. The security guard had a list of criminals and wouldn't let in the criminals on that list, but there are new criminals appearing all the time, and so the list is constantly outdated. Not only that but the security guard would every now and then try to guess if someone was a criminal or not based on what the potential criminal said she was going to once inside your building... half the time the guesses are wrong.

Sound like a great security guard? It's antivirus.

In other words, totally useless.

If you want to secure your installation, use something like AppArmor and/or NoScript. Use strong passwords, disable remote logins, install system updates regularly, back up your important documents weekly or daily as needed.

But running antivirus is just a waste of time, and that goes for Windows and Mac, too. Every single malware-infected computer I've seen has had an administrator account in Windows and the latest expensive antivirus installed.

---

### Post by Chame_Wizard on 2010-11-01
A virus/malware in *buntu?

Where...Where is it?:)

---

### Post by dhiman33 on 2010-11-02
:mrgreen:Does ubuntu by default has zero open ports? Is that the reason why noone can infiltrate my system from outside world?

But once again I get confused.(since I'm a noob ofcourse!:oops:) What is a port(noob's question!)? Don't I need atleast one open port to connect myself to internet and to send/receive data?:---)

---

### Post by oldos2er on 2010-11-02
> **dhiman33 said:**
> :mrgreen:Does ubuntu by default has zero open ports? 

You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Oops: this has already been posted twice. Maybe third time's the charm.  :)

---

### Post by 3rdalbum on 2010-11-03
> **dhiman33 said:**
> :mrgreen:Does ubuntu by default has zero open ports? Is that the reason why noone can infiltrate my system from outside world?

Correct.

> But once again I get confused.(since I'm a noob ofcourse!:oops:) What is a port(noob's question!)?

 Don't I need atleast one open port to connect myself to internet and to send/receive data?:---)

There are two sets of ports: Incoming and outgoing. Outgoing ports are no danger* to yourself, because they start at your computer and end at their destination. Data can travel both ways along this port. This is how your web browser works - it starts an outgoing connection to the computer that holds the website you want.

Incoming ports are what firewalls block. You wouldn't want any other computer to open a connection to your computer, without good reason. You wouldn't know who the other computer belonged to, or if you could trust it, or what the other computer wants to do.

When a program wants to receive an incoming connection, it listens to a particular incoming port, that is numbered. If you request a web page, your computer sends the request to the destination computer's Port 80. The server software on the destination computer is listening to Port 80 and will send back a reply through that same connection.

A connection cannot be opened to a port that is not being listened to. That's why attackers can't attack Ubuntu out-of-the-box - there's nothing listening. And incoming ports are different to outgoing ports, that's why you don't need to poke holes in your firewall just to check your e-mail.

*The contents of the data you receive through the outgoing connection might be malicious, so there's never ZERO danger in outgoing connections, but at least they don't let "just anyone" send data to your applications.

---

### Post by janpol on 2010-11-03
> **3rdalbum said:**
> There are two sets of ports: Incoming and outgoing. Outgoing ports are no danger* to yourself, because they start at your computer and end at their destination. Data can travel both ways along this port. This is how your web browser works - it starts an outgoing connection to the computer that holds the website you want.

Incoming ports are what firewalls block. You wouldn't want any other computer to open a connection to your computer, without good reason. You wouldn't know who the other computer belonged to, or if you could trust it, or what the other computer wants to do.

When a program wants to receive an incoming connection, it listens to a particular incoming port, that is numbered. If you request a web page, your computer sends the request to the destination computer's Port 80. The server software on the destination computer is listening to Port 80 and will send back a reply through that same connection.

A connection cannot be opened to a port that is not being listened to. That's why attackers can't attack Ubuntu out-of-the-box - there's nothing listening. And incoming ports are different to outgoing ports, that's why you don't need to poke holes in your firewall just to check your e-mail.

*The contents of the data you receive through the outgoing connection might be malicious, so there's never ZERO danger in outgoing connections, but at least they don't let "just anyone" send data to your applications.


When you open a connection with your web browser, you connect to port 80 on the server, and the server connects to a random port (not port 80) in your machine in order to send you the data you requested. A firewall lets this connection pass through because it's a connection you negotiated(but it's an incoming connection from the outside using a random incoming port). But, if your PC receives a connection from the outside that you have not started (negotiated), it blocks it.

Actually, this is why reverse connection trojans exist. **Also, maybe that's what you ment, but I thought it wasn't entirely clear** :)

@dhiman33: don't worry, somebody can't get into your pc because you oppened a port to surf the web ;)

---

### Post by dhiman33 on 2010-11-03
:-PThat was crystal clear,3rdalbum. One more question now.

"A source of confusion sometimes occurs when users feel the need to be  running firestarter/Guarddog for their firewall to be active. **This is untrue !**  Keep in mind that these applications are not firewalls, but rather  configuration tools for ip tables. These applications should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*.  firestarter will monitor traffic, but it runs as root and there are  better monitoring programs, so configure you firewall, shut down  firestarter/grauddog, and let IP tables do the rest :twisted:. "

The portion above is written in the link "http://ubuntuforums.org/showthread.php?t=510812".This says that the iptable/firewall has to configured once to make it active. Does that mean ubuntu has a dormant firewall in the default state and I have to activate it in order to have closed ports?#-o

---

### Post by dhiman33 on 2010-11-03
Thnks for reply, janpol:KS.

---

### Post by dhiman33 on 2010-11-03
:-kHmmm, so if I start a connection to a server, the server can make an incoming connection to me. Can the server now send some linux virus to my machine?(Though they remain dormant till I run them.)

Also, I think I never asked this. If I've a linux virus in my ubuntu in dormant state, and if I run it without sudo:tongue:, what kind of infection can happen? What'll be the worst case? Should I be able recover then?If yes, how?(creating another user account or somethng like that?):guitar:

---

### Post by Boondoklife on 2010-11-03
> **dhiman33 said:**
> :-PThat was crystal clear,3rdalbum. One more question now.

"A source of confusion sometimes occurs when users feel the need to be  running firestarter/Guarddog for their firewall to be active. **This is untrue !**  Keep in mind that these applications are not firewalls, but rather  configuration tools for ip tables. These applications should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*.  firestarter will monitor traffic, but it runs as root and there are  better monitoring programs, so configure you firewall, shut down  firestarter/grauddog, and let IP tables do the rest :twisted:. "

The portion above is written in the link "http://ubuntuforums.org/showthread.php?t=510812".This says that the iptable/firewall has to configured once to make it active. Does that mean ubuntu has a dormant firewall in the default state and I have to activate it in order to have closed ports?#-o
I think you have an incorrect view as to what a firewall does. It does not "Close" your ports, instead think of it as "Blocking" your ports. Ports have a few states, "Open" and "Close" are your main concern. All ports are in a "Close" state until an application listens on it, at which time it becomes "Open".

If you think of a firewall as its name sake, it stands between you and a hostile environment. In short no matter if your ports are open, closed, etc.; if you have a firewall up and have it set to block all unsolicited incoming packets then all or your ports will be effectively "Blocked". The Status of "Open" / "Close" becomes irrelevant as there is a middle man saying what gets in or not.

---

### Post by Boondoklife on 2010-11-03
> **dhiman33 said:**
> :-kHmmm, so if I start a connection to a server, the server can make an incoming connection to me. Can the server now send some linux virus to my machine?(Though they remain dormant till I run them.)

Also, I think I never asked this. If I've a linux virus in my ubuntu in dormant state, and if I run it without sudo:tongue:, what kind of infection can happen? What'll be the worst case? Should I be able recover then?If yes, how?(creating another user account or somethng like that?):guitar:
Instead of giving you a long list of examples, I think you should just look into getting a good doc on user privileges and permissions ([https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)). This will help you understand the possible impact of malicious code on Linux (and other) boxes. You could also check this site out for a high level view of viruses and how they work [(http://www.howstuffworks.com/virus.htm)]("http://www.howstuffworks.com/virus.htm")

---

### Post by janpol on 2010-11-03
> **dhiman33 said:**
> :-kHmmm, so if I start a connection to a server, the server can make an incoming connection to me. Can the server now send some linux virus to my machine?(Though they remain dormant till I run them.)

The only thing that server would be able to do is to exploit some vulnerability on your web browser (or it's plugins) and then get you infected. They can't just "pass a linux virus" because the firewall also recognises which app opened the connection (in this case the web browser), unless they make you download something, but if you clic in a link to download something you don't know where it's coming from.....that's your fault (and like everybody said, it's hard to make a virus that works well on ALL linux distros and also have a big impact on your system).

And don't worry about iptables in Ubuntu, your ports are closed by default.

If you wanna be really safe about linux viruses (the few that are out there), read about AppArmor and SELinux and try to configure one of them.

---

### Post by Zlatan on 2010-11-03
> **dhiman33 said:**
> Hey, I want to know exactly why people tell that there'sno need for an antivirus in ubuntu(or any linux distro). Is the sole reason is that ubuntu is much much MUCH more secure than windows?

Or the reason is that share of linux in the market is very small compared to windows, for that most people and companies use windows, and for that the makers of viruses target mainly windows, not linux or mac? :guitar:

[link]("https://help.ubuntu.com/community/Linuxvirus")

---

### Post by dhiman33 on 2010-11-03
Can't understand your saying,boondoklife.#-oLet me ask it like this.If I've run a virus in ubuntu WITHOUT sudo and it makes my user account a crap, how to recover?(should I consider I'll be able to login after the infection?)

---

### Post by janpol on 2010-11-03
> **dhiman33 said:**
> Can't understand your saying,boondoklife.#-oLet me ask it like this.If I've run a virus in ubuntu WITHOUT sudo and it makes my user account a crap, how to recover?(should I consider I'll be able to login after the infection?)
You should login as the root user, or with another user acount. If you haven't set a root password and haven't created another user acount, you can boot with a livecd, recover your data, and then restore your account (maybe deleting it and creating it again).

---

### Post by aysiu on 2010-11-03
> **janpol said:**
> You should login as the root user, or with another user acount. If you haven't set a root password and haven't created another user acount, you can boot with a livecd, recover your data, and then restore your account (maybe deleting it and creating it again).
Correction: there is absolutely no reason to set a root password.

If you need to recover your files, you can use a live CD.

If *sudo* somehow becomes messed up, you can boot into recovery mode (which logs you in as root but without a password).

---

### Post by janpol on 2010-11-03
> **aysiu said:**
> Correction: there is absolutely no reason to set a root password.

If you need to recover your files, you can use a live CD.

If *sudo* somehow becomes messed up, you can boot into recovery mode (which logs you in as root but without a password).
I was talking about linux in general, sorry about that.

@dhiman33: listen to aysiu xD

---

### Post by dhiman33 on 2010-11-04
Hey, aysiu, can u tell me how to recover using live cd?:P

And (err..) do u all think I'm boring people with this long discussion?:oops::oops::-\":-\"

---

### Post by DirtyPC on 2010-11-04
There are VERY Few viruses in ubuntu, and as the distro is updated every 6 months, viruses find it hard to keep up, but if you worry that much just have a search in ubuntu software centre.

---

### Post by dhiman33 on 2010-11-04
harrylucas1, I'm going to never install some antivirus on ubuntu[-X.(Also won't like to install a firewall). I'm discussing all these 'cause I believe ubuntu(linux) is an os which is very much immune to virus or hack attacks:evil: and I'm getting ur opinions to make sure what I think is right! That's why I'm asking all those "if" and "let" questions to assume some worst situations concerning virus attacks and asking people to comment on those. And so far all these comments have only made my belief grow stronger.:guitar:

---

### Post by Spice Weasel on 2010-11-04
> **harrylucas1 said:**
> There are VERY Few viruses in ubuntu, and as the distro is updated every 6 months, viruses find it hard to keep up, but if you worry that much just have a search in ubuntu software centre.

It doesn't really matter how old or new the software is.

To be on topic, if you're stupid enough to type "sudo chmod a+x ./pr0n" in to a terminal then you will get a virus.

---

### Post by 3rdalbum on 2010-11-04
> **dhiman33 said:**
> :-PThat was crystal clear,3rdalbum. One more question now.

"A source of confusion sometimes occurs when users feel the need to be  running firestarter/Guarddog for their firewall to be active. **This is untrue !**  Keep in mind that these applications are not firewalls, but rather  configuration tools for ip tables. These applications should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*.  firestarter will monitor traffic, but it runs as root and there are  better monitoring programs, so configure you firewall, shut down  firestarter/grauddog, and let IP tables do the rest :twisted:. "

The portion above is written in the link "http://ubuntuforums.org/showthread.php?t=510812".This says that the iptable/firewall has to configured once to make it active. Does that mean ubuntu has a dormant firewall in the default state and I have to activate it in order to have closed ports?#-o

Re-read what you were replying to. Your ports are closed unless there is something actually listening to them. If a program is listening for incoming connections, it's usually only on one port.

But yes, Ubuntu's firewall does not block incoming connections unless you configure it to do so.

And no, the server can't just "send a Linux virus". It's not like the server sends data and the computer just blindly decides to execute this data or store it on disk. A server could send back a maliciously-crafted web page that attempts to exploit a security hole in your browser, for instance; but then it's your fault for surfing for underage dog pornography :P

---

### Post by dhiman33 on 2010-11-06
> **3rdalbum said:**
> 

But yes, Ubuntu's firewall does not block incoming connections unless you configure it to do so.



:-|So I have to configure a firewall to close ports. I prefer gufw firewall, but it doesn't run at startup. Is the firewall permanently set once I run gufw.(I mean, the nxt time when I boot up my laptop and haven't yet enabled gufw, is my firewall active and has zero open ports?):guitar:

---

### Post by janpol on 2010-11-06
> **dhiman33 said:**
> :-|So I have to configure a firewall to close ports. I prefer gufw firewall, but it doesn't run at startup. Is the firewall permanently set once I run gufw.(I mean, the nxt time when I boot up my laptop and haven't yet enabled gufw, is my firewall active and has zero open ports?):guitar:
Wait a second there, first of all, you don't have any opened ports unless you install a service like Apache (that opens a port in order to receive incoming connections). Otherwise, your ports are inaccessible from the outside.

I can just say, hey! let's connect into dhiman33's computer at port X if you don't have a service listening in that port (and you would have to configure your router to redirect connections too).

I think this thread is making a mess of the terms open and closed xD

Just don't worry about a firewall unless you install a service that listens at outside connections, you are not in Windows anymore :).

About your Gufw question: Gufw, like many tools out there, is just a GUI interface of iptables, your firewall is iptables and is active all the time, you just have to configure it the way you want.

Tell us witch service you are going to install that opens a port, and we'll help you with the configuration, otherwise, get ride of that "Windows firewall need" stress and be happy ;)

---

### Post by Siph0n on 2010-11-06
I am also confused about this. Can't I have a program that creates a root account, and say it is some other kind of program that requires root to run. So when someone does sudo nameofmyprogram , it really creates a root account... right? How is linux safe from this?

---

### Post by aysiu on 2010-11-06
> **Siph0n said:**
> I am also confused about this. Can't I have a program that creates a root account, and say it is some other kind of program that requires root to run. So when someone does sudo nameofmyprogram , it really creates a root account... right? How is linux safe from this? Yes, you can have a program like this. For that program to be effective, you have to trick the user into actually installing it and giving away her admin (it's not really root in Ubuntu, but it allows for root-like powers) user password.

All operating systems are vulnerable to this trojan attack, because it relies on weakness in the **user** and not the **operating system**. If the user can be tricked into compromising the system, it doesn't matter how well the system is set up.

It's like having a mighty fortress with laser sensors, barbed wire, armed guards... and the person who turn off all the sensors and call off the guards is gullible and can be tricked into doing so by someone just saying "Hey, I'm okay. Let me into the fortress."

---


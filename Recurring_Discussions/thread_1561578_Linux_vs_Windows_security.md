---
title: "Linux vs Windows security"
date: 2010-08-26
forum: Recurring Discussions
---

### Post by OpenOS on 2010-08-26
is it true linux is more secure and why and can you explain in simple terms please its not for me im just proving a point to my family friends

---

### Post by realzippy on 2010-08-26
This might be interesting for you:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by spynappels on 2010-08-26
In over-simplified terms:

No viruses
Security Holes are documented and fixed more quickly
Permissions

There are others, but those three spring to mind immediately.

---

### Post by uRock on 2010-08-26
Ubuntu/Linux requires a password for installing and/or administering the system
There are no known active viruses for Linux.
Secure repositories for upgrading installing and/or upgrading softwares.
The linux kernel gets updated as holes in the code are found.

You can find a lot of info in the [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") thread which covers the ins and outs of the security model as well as how to use the functions for optimum security.

---

### Post by sikander3786 on 2010-08-26
> **uRock said:**
> Ubuntu/Linux requires a password for installing and/or administering the system
There are no known active viruses for Linux.
Secure repositories for upgrading installing and/or upgrading softwares.
The linux kernel gets updated as holes in the code are found.


+1
+1
+1
+1
And no ports left open on public interfaces by default.

---

### Post by Thelinuxgeek on 2010-08-26
Windows is crap. Over 6 million people get a virus on windows every day. And on Ubuntu...umm, I've never even heard of ANYONE ever getting a virus on Ubuntu. Windows most critical files are are easy-to-modify .dlls in a folder labeled "Kick Me." (A.K.A Windows). Ubuntu was designed with much more thought put into it.

---

### Post by rookcifer on 2010-08-26
Waiting for this to be moved to "Recurring Discussions" in 3...2...1...

---

### Post by OpSecShellshock on 2010-08-26
Security isn't an absolute, stable state; it's a position relative to a given specific risk or set of risks. There are risks present for users of Windows that do not exist for users of Linux. The reverse is also true, but those are quite different and are not encountered nearly as often.

---

### Post by meskes on 2010-08-26
The only 100% secure machine is one which is unplugged, turned off and stored behind a lock and key. That being said, there are quite a few things that make linux more secure than windows. While there are "no active viruses" for linux, there are rootkits, which you can think of as backdoor that's installed by a malicious party. However, they have to gain access to your computer by another method such as a bug that allows someone to gain root privs. etc. 

While linux is harder to compromise than windows, it's really about the end user/ administrator's due diligence in keeping the system system safe by not going to outside sources, untrusted sources for your software and installing all security updates when they are published and really, just not doing anything stupid that would get you into said position to being with.

---

### Post by cariboo on 2010-08-26
I have to agree with rookcifer, this has been asked and answered several times. Moved to Recurring.

---

### Post by libssd on 2010-08-26
> **OpenOS said:**
> is it true linux is more secure and why and can you explain in simple terms please its not for me im just proving a point to my family friends
A good start would be to google for "why linux is secure".

Read, then decide. Although I'm in the camp that believes that *nix is inherently more secure, by design, I think the main reason is market share: Windows is where the action is. The last time I had a virus problem on a Mac (before OS X) was 1992. How many desktop Windows users do you know who have had to reinstall because of a security problem?

You can also look at Linux security from two different perspectives: desktop Linux and server Linux. The former rarely has problems; the latter is a much bigger target, and therefore more attractive, largely because so many servers run Linux, and servers tend to have good connections and lots of disk space. I have direct knowledge of a Linux server that was hacked, taken offline, cleaned, OS re-installed, and hacked again within 5 minutes of coming back online.

---

### Post by jroa on 2010-08-26
I have to agree with everyone that Ubuntu is a lot more secure than Windows.  With Ubuntu, if you can not figure how to do stuff, like download software, run software, or even get connected to the Internet, then you will never have security issues.  Windows is just too easy to do things with.  You can really mess up your computer by doing stuff with it.  Plus, you run the chance of accidentally being productive with Windows while you are screwing around.

I am just kidding, of course.

---

### Post by libssd on 2010-08-27
I can't recall the exact words, but I saw a quote similar to this once: "All you have to do to break Windows is to use Windows."

---

### Post by ST3ALTHPSYCH0 on 2010-08-27
Fact is, with the newer versions of Windows, if you'll put a little thought into your setup you can enhance the security off the rip. Password the first account you set up. Setup your machine with that account. Create a standard user. Use the second user for your daily activities. The biggest sources of security problems in Windows are click happy users with admin accounts, a preinstalled web browser that allows scripts to run by default (or it used to, I quit using IE except when websites require it around 5.5) in an admin account, and the absolute proliferation of malware available.

Fact is, the biggest 2 things that keep desktop Linux more secure are the repository systems and obscurity. I actually read a page that gave a step by step to write a Linux trojan, and even how to give it root access if you felt like it needed it (but seriously, a borked OS(which would need root)? No problem, back up the files to external media with a Live CD and reinstall. Delete the entire /home/user/ directory (which doesn't need root)? Much tears). This site, BTW didn't actually give any of the scripting needed, only the basic concept. 

My point is, if Linux is brought to the masses as a desktop OS, the average user is in just as much, if not more trouble than they are with Windows. More? You ask. Yes, because they now have this "invincible" OS and they'l be even more likely to download binary or script files from the web and run them. Some of you will remember the "screensaver" that was hosted on Gnome-do last year or two years ago.... 'nuff said. That's proof of concept right there. I realize that the threat was picked up by the community within hours and the offending file taken down that day.... but what if this same trojan had a mailer script? Sends itself to all of the user's contacts with a subject line read either a) "Linux attack vector found, click this file to install patch now" or b) "check out this cool screensaver I found on *some website or whatever* (you'll have to install it to check it out". Odds are that a Linux user is gonna have email contacts who also use Linux. Odds are also that some of those people will be naive enough to run this file.... This is the kind of thing that perpetuates malware....

Keep in mind that the "average" Windows user who will install and use Limewire *shudder* and who will try every game in the ad column of their fb page, will be looking for crap to install directly form the 'net..... and malware writers will be all too happy to oblige, if the user base gets large enough.

---

### Post by rjbl on 2010-08-27
**@libssd**[I]

You can also look  at Linux security from two different perspectives: desktop Linux and  server Linux. The former rarely has problems; the latter is a much  bigger target, and therefore more attractive, largely because so many  servers run Linux, and servers tend to have good connections and lots of  disk space. I have direct knowledge of a Linux server that was hacked,  taken offline, cleaned, OS re-installed, and hacked again within 5  minutes of coming back online.         [/I]

Not as easy as you think, but do-able nevertheless. Depends upon the server being protected by a badly configured firewall, or none at all, and offering a service with exploitable vulnerabilities which is running with root privilege. Given the very large number of GNU/Linux servers on the global internet they are certainly out there to find - if that's what floats your boat. Windows? Rather easier because you are after end-users' systems which are more likely to be configured, and maintained, by the innocent, the kind-hearted and, frankly, the clueless.

Will it get bad for GNU/Linux users as the user base grows? Who knows. My guess is that it probably will. The threat signature has changed radically in about the last 5 years. Today's cracker is looking to persuade the end user to do something legal but naive, or even plain dumb, largely by social engineering means. Yesterday's cracker sought, by surreptitious means, some exploitable vulnerability in the target system silently to enter that system and there to have his wicked way. I can't think of any way of configuring or protecting any GNU/Linux system, nor Windows for that matter, to give sensible protection against attacks based upon social-engineering the naive user.

Be afraid, be very afraid.

rjbl

---

### Post by del_diablo on 2010-08-27
[To quote:]("http://ubuntuforums.org/showpost.php?p=9737647&postcount=10")
> Nope, there aren't. There really aren't.

If you need proof; disable Ubuntu firewall and all security features. Go to p2p websites and download a load of files. Go to pr0n sites and click everything you see. Download "freemovie.exe" files on Limewire. 

I guarantee nothing will happen. 

Got to get out of this "windows mentality". I'm not saying Linux is unattackable, I'm saying as of right now there are no viruses. It isn't a "too good to be true" thing.

Also, if you manage to get a virus, for the love of god tell everyone. It'll be a historic moment in the FOSS world.

[QUOTE]Viruses and Spyware... They do exist on Linux. Not as much but there are some out there. 

They do? Like I said, *please* report them immediately.

> That is obviously a wrong statment 

Gotta love what happens when one company has total influence over 95+ percent of the population.[/QUOTE]

---

### Post by Peter09 on 2010-08-27
I think the issue really is not - how easy is it to break a Linux or Windows box - but how easy is it to break many boxes. Virus writers are not really interested in breaking one box, they need mechanisms that can be automated and target many boxes. Thats were Linux is very strong compared to windows, its just not easy to write something that can jump from one Linux box to many others.

---

### Post by linux18 on 2010-08-27
> **Peter09 said:**
> I think the issue really is not - how easy is it to break a Linux or Windows box - but how easy is it to break many boxes. Virus writers are not really interested in breaking one box, they need mechanisms that can be automated and target many boxes. Thats were Linux is very strong compared to windows, its just not easy to write something that can jump from one Linux box to many others.
+1 
and re-stating that a little better:

"If they are targeting YOU and only YOU, then no amount of protection will save you. However, if they are targeting EVRYONE then you will be safe on linux 99.999% of the time, if your not a server."

after 3 years with no antivirus and only a router firewall, nothing has happened to my linux desktop and probably never will.

---

### Post by ral0r3us on 2010-08-27
> **spynappels said:**
> In over-simplified terms:

No viruses
Security Holes are documented and fixed more quickly
Permissions

There are others, but those three spring to mind immediately.

Well there are viruses, i have made some for example, but the point
is people that make 'em dont distribute them simply because it takes
an idiot to attack open source. If you find a loophole you report it
and simply gets fixed. Nothing is impenetrable but in this case there
is a lack of volition to penetrate... it feels like braking and 
entering in our own home... simply pointless!

cheers

---


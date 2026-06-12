---
title: "why linux doesent get viruses..true or false?"
date: 2008-06-08
forum: Recurring Discussions
---

### Post by gatorbowls on 2008-06-08
I heard one reason linux does not get viruses is because 96% of people use windows. Is that a true statement?

---

### Post by RequinB4 on 2008-06-08
[http://librenix.com/?inode=21](http://librenix.com/?inode=21)  Sums it up nicely.

Basically, it helps, but its not THE end all reason.

---

### Post by Rocket2DMn on 2008-06-08
It is true that there aren't currently any viruses in the wild for linux.  It isn't just because Windows has a majority market share, it is because of the way linux is structured.  Different distributions are all a little different some a virus for one may not affect another, but even if one is released, the nature of open source software renders the virus useless in a very short period of time - updates are released very often, and with so many eyes on the source code, it has become very secure.  So basically, if somebody DOES create a virus, it won't have time to make its way across the internet because fixes will be released very quickly.

---

### Post by ThreeLies on 2008-06-08
Generally speaking in my opinion I would agree that most viruses will target Windows due to it being commonly used and since Windows Vista there security was lacking now its just annoying.

---

### Post by gatorbowls on 2008-06-08
And what about hackers? Does file permissions take care of that?

---

### Post by lisati on 2008-06-08
> **RequinB4 said:**
> [http://librenix.com/?inode=21](http://librenix.com/?inode=21)  Sums it up nicely.

Basically, it helps, but its not THE end all reason.

A reason I'd add to the article is that it would take some ingenuity to get a binary file to execute on both Linux & MS-DOS/Windows system. I'm thinking of the equivalent of a .EXE file here - it's not likely to happen.

---

### Post by DonnyB4e56 on 2008-06-08
> **Rocket2DMn said:**
> It is true that there aren't currently any viruses in the wild for linux.  It isn't just because Windows has a majority market share, it is because of the way linux is structured.  Different distributions are all a little different some a virus for one may not affect another, but even if one is released, the nature of open source software renders the virus useless in a very short period of time - updates are released very often, and with so many eyes on the source code, it has become very secure.  So basically, if somebody DOES create a virus, it won't have time to make its way across the internet because fixes will be released very quickly.



Arent you a smart cookie, thanks for the information. I thought that there were a lot of linux viruses but nobody coded antivirus program's to help you protect yourself or heal the infected packages, im new to ubuntu altough I have been useing it for the past year and a half, I would relly like to try and get all my stuff working again after I downloaded my new ubutnu 8.04 LTS and burned it in windows, all is going well so far accept for one of my Restricted Drivers were "in use" but not "enabled" so I had to remove the package completely and re-install it. Back on topic, if somebody was to release a virus for ubuntu linux or any linux distribution that could affect or harm ubuntu could it be harmful to the system or would it reamin useless after the next update? Could somebody hack your xorg.conf file and change the update manager path's and have it download a new virus everytime it was patched? Thease are the questions one maust ask themselfs. Well I ask myself that but im just a bit paranoid.

---

### Post by Rocket2DMn on 2008-06-08
> **gatorbowls said:**
> And what about hackers? Does file permissions take care of that?

Hackers can still break into linux systems, but it can be very difficult because of the built in firewall called iptables.  However, if you have SSH or remote desktop enabled, all they need is your username and password which is why you should always use strong passwords (and don't write them down to store at a work desk or give them to friends!).

More on Ubuntu Security - [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Sef on 2008-06-08
> And what about hackers? Does file permissions take care of that?

GNU/Linux can get hacked.  That is why to run as a user and not as root.  Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo").  It is harder to hack GNU/Linux than Windows, but you still need a good password, and be careful of sites that tell you to log in as root.

---

### Post by Sef on 2008-06-08
> Generally speaking in my opinion I would agree that most viruses will target Windows due to it being commonly used and since Windows Vista there security was lacking now its just annoying.

That is incorrect.  Web servers are about 2/3 GNU/Linux and 1/5 Windows.  Guess which one has more viruses and gets hacked more.

---

### Post by Rocket2DMn on 2008-06-08
> **DonnyB4e56 said:**
> Back on topic, if somebody was to release a virus for ubuntu linux or any linux distribution that could affect or harm ubuntu could it be harmful to the system or would it reamin useless after the next update? Could somebody hack your xorg.conf file and change the update manager path's and have it download a new virus everytime it was patched? Thease are the questions one maust ask themselfs. Well I ask myself that but im just a bit paranoid.

If somebody were to release an effective virus, it could affect your system.  A security fix would be released very quickly (sometimes zero-day or at least within a few days), but if you don't keep your computer up to date, you may remain at risk.  Hacking xorg.conf doesn't do much good since all it does is break X (the GUI), but they could potentially change your source.list file for apt (and the update manager).  However, that would require them to have superuser/root/sudo privileges through their hacking at which point your system is completely vulnerable.

Remember, security isn't just installed and left to be, it is an active process.  Again, see [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by WBL on 2008-06-08
> **Rocket2DMn said:**
> Hackers can still break into linux systems, but it can be very difficult because of the built in firewall called iptables.  

Is iptables turned on by default, or does it have to be configured?

-WBL

---

### Post by Scheater5 on 2008-06-08
Linux is safer by design.  That's no myth.  But at the same time, it's not invulnerable.  "Linux doesn't get hacked" is a myth, too.  The account policies of most distros helps alot, in addition to iptables and firewalls as other people have mentioned.  If you're  conscious about security, Linux can be a fortress - and even by default you can without much exaggeration ignore viruses.  The open source nature of Linux means there are less vulnerabilities.  Even if there were as many people targeting Linux as there are targeting Windows, they would have less to work with.

---

### Post by Rocket2DMn on 2008-06-08
> **WBL said:**
> Is iptables turned on by default, or does it have to be configured?

-WBL

iptables should be enabled by default.

---

### Post by Grishka on 2008-06-08
Linux is not 100% virus free, but very rarely will this problem be of any concern to an average user. perhaps this Wikipedia article will shed some light on this matter: [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware).
oh yeah, remember that Windows viruses CAN spread through e-mail or such, only they won't do anything to your system.

---

### Post by cardinals_fan on 2008-06-08
> **WBL said:**
> Is iptables turned on by default, or does it have to be configured?

-WBL
> **Rocket2DMn said:**
> iptables should be enabled by default.
Iptables is **installed** by default, but not configured.  You can follow these instructions to enable it graphically: [http://www.howtogeek.com/howto/ubuntu/install-the-firestarter-firewall-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-the-firestarter-firewall-on-ubuntu-linux/)

---

### Post by Rocket2DMn on 2008-06-08
That is true, it is not configured, but you really only need to screw with configuration if you are enabling or disabling some specific programs.  Firestarter is a good starting place, but it's not perfect.  Also see [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by dynamethod on 2008-06-08
Personally i feel its just due to the market share, if linux was as big as windows, i dont see why it wouldnt be such a target


this whole idea about privileged accounts etc, so what happens when someone writes a program that will brute the root password then store the password, then  for it to access/excecute root files just to call "sudo whatever"?  everytime the virus would need to.  Wouldnt that just by-pass the whole 'as long as your not root your safe' thing?

---

### Post by Rocket2DMn on 2008-06-08
> **dynamethod said:**
> Personally i feel its just due to the market share, if linux was as big as windows, i dont see why it wouldnt be such a target


this whole idea about privileged accounts etc, so what happens when someone writes a program that will brute the root password then store the password, then  for it to access/excecute root files just to call "sudo whatever"?  everytime the virus would need to.  Wouldnt that just by-pass the whole 'as long as your not root your safe' thing?

It is certainly not that simple.  It was mentioned (quite correctly) earlier that linux has a huge percentage of the server market share, especially on the web, so it is a fairly large target for hackers.  Brute forcing the password is possible (esp. if you enable SSH), which is one of the reasons the root account is disabled by default in Ubuntu.  In any system, if a hacker has your username and password, then your system is 100% at risk, that is why you use strong passwords and don't share them or store them in places that aren't safe.
There is more discussion earlier in this thread, and a couple of useful links to follow which you should consider reading and possibly bookmarking.  Again, remember that security is an active process, not an install-and-forget deal.

---

### Post by Sonic Reducer on 2008-06-08
> **dynamethod said:**
> this whole idea about privileged accounts etc, so what happens when someone writes a program that will brute the root password then store the password, then  for it to access/excecute root files just to call "sudo whatever"?  everytime the virus would need to.  Wouldnt that just by-pass the whole 'as long as your not root your safe' thing?

notice how there is a little half-second or so delay between entering the password and reprompting if you made a typo?

say hypothetically the virus entered the password instantly, then you could get two attempts in a second.

if someone used a password 8 characters long, that means the brute force would have to work through all the passwords 1 character long all the way up through every 7 digit password before it was even in the correct league for the root password.

that doesn't sound like much, but in order to be effective it would require every symbol to be run. oh yeah, case-sensitive too

52 letters
10 numbers
32 basic symbols (the ones above the numbers and the ones to the right of the letters)
thats 94 basic possibles, do you really want to include ALL the possible characters you can type on a keyboard?

that means the virus would have to work through over (if my math is right) 3.75 Million (3,790,080) possible passwords

3,790,080 attempts at 2/second is about 22 days worth of numbers. normal users turn their computers off at night. i have owned call of duty 4 since christmas but and haven't been online that long.

ultimately it comes down to the user. you aren't using linux because you click every attachment that comes your way. where most "nerds" would know they have a Linksys WMP54G wireless card they put in their computer, i know i have the 4th revision with the RaLink RT2500 chip in it. as a general rule if you're using linux you know about computers enough to be fairly safe.

PS if you want to see how not-easy it is to crack something using brute force check out rarcrack on sourceforge. make a password protected rar with your root password (or hell, for security's sake scramble the letters) and try to crack it. i had some password protected "movies" that i was trying to crack (i did not know, but i went to school with a girl who does porn now) and it took a week running 24/7 to crack the files.

worst part of it all, she was unattractive.

---

### Post by Rocket2DMn on 2008-06-08
I use a program called john the ripper ("john" in the repositories).  You can use it to try and brute force your own passwords.  It doesn't use a two second delay, it just generates passwords and their hashes, then checks them agsinst the hashes in the file you provide.  example:
```
sudo john /etc/shadow
```
It will then try and crack your passwords, but can take days/weeks/months/years to run depending on the strength of your password.  You can just press any key in the terminal to see what it's doing.

---

### Post by unutbu on 2008-06-08
94^8 is about 6.1*10^15 passwords. At 2/sec, it would take about 96 million years to try them all.

---

### Post by aysiu on 2008-06-08
The biggest danger with the increase in consumer market share (not servers but desktops and laptops) is social engineering, which can be successful on any platform, because it takes advantage of a weakness in the user, not the platform itself.

Just trick someone into double-clicking a .deb and entering her *sudo* password, and the entire system is compromised.

---

### Post by Sonic Reducer on 2008-06-09
> **aysiu said:**
> Just trick someone into double-clicking a .deb and entering her *sudo* password, and the entire system is compromised.
[COLOR="White"]
thats easy enough to fix. we just won't let women use computers.

or vote.[/COLOR]

.:EDIT:. apparently i offended someone, so i'm whiting this post out. don't highlight and read if there are children in the house or you have a sensitive stomach

FYI, i put ubuntu on my moms computer to cut down the time i spend going over and fixing her computer
[COLOR="White"]
even though the cynic in me has to notice that even though she said herself that she uses the feminine singular form in order to (among other things) elicit a feeling of "*slight discomfort for men.*" but when i say something absurdly sexist (that i intended in no way to be taken seriously) i get yelled at.[/COLOR]

---

### Post by LaRoza on 2008-06-09
> **Sonic Reducer said:**
> thats easy enough to fix. we just won't let women use computers.

or vote.

[Why (s)he says "she"]("http://ubuntucat.wordpress.com/2006/07/29/why-i-say-she/")

You will find that the overwhelming majority of hypothetical people references on this forum are male. No one feels compelled to say such things in those cases.

Joanna, fire.

---

### Post by pmlxuser on 2008-06-09
> **gatorbowls said:**
> And what about hackers? Does file permissions take care of that?

true that file permission takes care of alot of things, but still that doesn't mean that if you are running linux you computer can't be hacked

check this [http://www.zdnet.com.au/news/security/soa/Debian-server-hacked/0,130061744,139263270,00.htm](http://www.zdnet.com.au/news/security/soa/Debian-server-hacked/0,130061744,139263270,00.htm) if you don't believe me.

the only thing is that fewer hacks have been made on Linux machines than on windows

---


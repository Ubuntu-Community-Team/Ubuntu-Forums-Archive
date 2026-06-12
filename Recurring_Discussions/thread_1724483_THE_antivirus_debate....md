---
title: "THE antivirus debate..."
date: 2011-04-08
forum: Recurring Discussions
---

### Post by rvboutin on 2011-04-08
Hi,
Being new to Ubuntu, and being a "paranoid Windows user" as I have read in many forum... I was looking for antivirus protection on Ubuntu.
On some forums, I found that antivirus on Linux are useless because of the way the system works (using stricter permissions to read/write/execute files), etc.. on some forums, I read that using antivirus protection is always a good idea whatever the system is.
So I'd like some opinions/advices here.
Being a new user of Ubuntu, when I had some trouble installing my new graphic cards, or some software that I needed for work, I had to use command lines to download/install and run some programs on my Ubuntu... on many occasion not knowing exactly what the several lines of codes meant... but granting them access to the Holy Root!!! Am I alone in that situation? I'd guess not, as many new user of Ubuntu will also very likely to help found on forums.
Then it came tome... what prevent someone to insert a rogue code in some legitimate software, or even create a file name that look legitimate but will actually be a keylogger or a virus? Since I don't truly always understand what several lines of codes mean and even if I know... how can I be sure that it is not happening?? I can't! An correct me if I am wrong, but nobody can, unless you are good enough to check the code of the program provided? This means that you can trust @ 100% that the guys, who freely and kindly, put stuff online for everyone to use is a good guy... well can I? shall I?
Who is checking that all linux software are good? If for some (most?) no company can be held responsible for it? Or if no software can actually check that there is no rogue software being unwillingly/unknowingly installed on my PC?
I know that I am kicking a bit the big "free-all-nice-and-peaceful" philosophy of Linux here... which I like by the way (both Ubuntu and the philosophy O:)), but is it all real? for free and 100% secure? or is it too good to be true?
Or shall restrict myself in using Canonical or Companies provided software on Linux/Ubuntu to avoid any problem?
Looking forward to read other people opinion here...
Have a good week-end all!!
Cheers,
Rv

---

### Post by uRock on 2011-04-08
There isn't much to debate. If you feel that you need AV, then install it. [BitDefender]("https://help.ubuntu.com/community/BitDefender") is free to single users on Linux.

---

### Post by SeijiSensei on 2011-04-08
If you limit the software you install to that available through the repositories (Ubuntu Software Center or package managers like apt-get, Synaptic, or KPackageKit) you don't need to worry as those programs have all been reviewed.  Following random suggestions on the Internet when you don't know what you're doing is as dangerous for Linux as it is for Windows.  Suggestions here are generally pretty safe because the forums are moderated, and because knowledgeable users would know right away if a posting suggests a dangerous practice and have the posting removed.

Read the [security stickies]("http://ubuntuforums.org/forumdisplay.php?f=338") if you want more information.

---

### Post by d3v1150m471c on 2011-04-08
it's not impossible for linux to get a virus. It is however extremely unlikely just due to the nature of the beast. if you're going to do filesharing with windows machines i recommend clamav. You can use rkhunter but it's notorious for false positives. I didn't much care for it. The best thing you can do is use trusted software, almost always open source software, and have a good firewall/router setup.

---

### Post by galacticaboy on 2011-04-08
> **rvboutin said:**
> Hi,
Being new to Ubuntu, and being a "paranoid Windows user" as I have read in many forum... I was looking for antivirus protection on Ubuntu.
On some forums, I found that antivirus on Linux are useless because of the way the system works (using stricter permissions to read/write/execute files), etc.. on some forums, I read that using antivirus protection is always a good idea whatever the system is.
So I'd like some opinions/advices here.
Being a new user of Ubuntu, when I had some trouble installing my new graphic cards, or some software that I needed for work, I had to use command lines to download/install and run some programs on my Ubuntu... on many occasion not knowing exactly what the several lines of codes meant... but granting them access to the Holy Root!!! Am I alone in that situation? I'd guess not, as many new user of Ubuntu will also very likely to help found on forums.
Then it came tome... what prevent someone to insert a rogue code in some legitimate software, or even create a file name that look legitimate but will actually be a keylogger or a virus? Since I don't truly always understand what several lines of codes mean and even if I know... how can I be sure that it is not happening?? I can't! An correct me if I am wrong, but nobody can, unless you are good enough to check the code of the program provided? This means that you can trust @ 100% that the guys, who freely and kindly, put stuff online for everyone to use is a good guy... well can I? shall I?
Who is checking that all linux software are good? If for some (most?) no company can be held responsible for it? Or if no software can actually check that there is no rogue software being unwillingly/unknowingly installed on my PC?
I know that I am kicking a bit the big "free-all-nice-and-peaceful" philosophy of Linux here... which I like by the way (both Ubuntu and the philosophy O:)), but is it all real? for free and 100% secure? or is it too good to be true?
Or shall restrict myself in using Canonical or Companies provided software on Linux/Ubuntu to avoid any problem?
Looking forward to read other people opinion here...
Have a good week-end all!!
Cheers,
Rv


With Linux, anti-virus is not needed. It has security like crazy that protects you. The only way to get a virus is if you install it yourself. Linux has what I like to call "DUH" security, which means, DUH this is how you do it windows. windows leaves everything open to hackers and viruses and linux is like I DONT THINK SO. But if you want to install virus protects you can, look in Synaptic, I found some there. Good luck!

---

### Post by bodhi.zazen on 2011-04-08
Linux is not Windows and the only people who advocate antivirus on LInux are :

1. New users from Windows.

2. Antivirus companies trying to sell you a product.

The valid user cases for running antivirus on Linux are:

1. If you are running a file server (samba) with windows clients, probably a good idea to scan the samba share from time to time.

2. If you are running a mail server.

3. If you are sharing files with Windows, although IMO you are better off skipping antivirus on Linux and running it on windows only.

The way Linux handles viruses is to patch the code, thus you are invulnerable to the known viruses.

Microsoft is either unwilling or unable to patch the code, thus Windows remains vulnerable to known exploits (most of the windows viruses are variations of a set of known exploits) and thus you need a 3rd party antiviurs to clean up.

---

### Post by teejay17 on 2011-04-08
Just to further extend the discussion, I am curious as to the AV software people use on Ubuntu.  
I've seen Linux versions of Avast, AVG and BitDefender. Anyone want to weigh in on those? 
I personally don't use AV on my Ubuntu machines, but I do use Avast when I use Windows.

---

### Post by CharlesA on 2011-04-08
I've been using BitDefender to scan the files I am sharing with Windows. I've only had a couple false positives, but those were dealt with easily but reporting the file and having them test it.

Tried clamav, but it threw up more false positives then not.

Anyhow, bodhi covered the reasons to use AV on a linux box. :)

---

### Post by jdunn on 2011-04-18
I've heard Wine is a valid user case for anti-virus.

---

### Post by sevenflo on 2011-04-18
Yes, WINE can introduce viruses to the Linux ecosystem.

Generally, the way you should look at this issue is that for a virus to get where it needs to be on a linux system, it'll likely need your root password.

But you bring up a good point which questions something we all overlook, drivers, applications and so on. And truthfully, you cannot just trust anything because anything can have that very piece of code that you're trying to avoid. I HIGHLY suggest you see this link, which I stole from someone's signature on the forum (canot remember who), but it talks exactly about your point : [http://cm.bell-labs.com/who/ken/trust.html]("http://cm.bell-labs.com/who/ken/trust.html")

In the general case, no you do not need one. In all likelihood, it is your paranoia from Windows. That was my case. 

Linux "does" have security like crazy to protect you - but it's not just that simple. Linux is far more secure than Windows in a variety of ways but often times it has to be set up correctly and may not be straight out of the box. For example, remote connections through SSH remain at a default port of 22 - until changed. And so on.

My recommendation would be to try ease into the notion that trusted software is mostly, well, trusted. If you find you use WINE, SAMBA servers, or frequent places that may expose you to viruses....well uRock said it best:
> There isn't much to debate. If you feel that you need AV, then install it.

---

### Post by bodhi.zazen on 2011-04-18
> **sevenflo said:**
> Linux is far more secure than Windows in a variety of ways but often times it has to be set up correctly and may not be straight out of the box. For example, remote connections through SSH remain at a default port of 22 - until changed. And so on.

By default, Ubuntu has no listening services, so port 22 (ssh) is NOT open.

Also, ssh security is another topic, but, if you use keys, and disable passwords, there is nothing wrong with port 22. If it makes you feel better you can install additional services (denyhosts, fail2ban) or change the port, but changing the port from 22 to a non-default port does little to increase security, IMHO and in my experience. Sure the logs will be quieter, but any hits you get are more serious threats.

---

### Post by ankspo71 on 2011-04-18
Hi,
When in doubt, you can upload suspicious files to virustotal.com to have the files scanned with over 40 antivirus tools. 

I bulk scan the files I don't completely trust with bitdefender. The files I scan are typically my browser cache, wine directories, and my storage partitions that contain files that I might share with other computers. I normally don't scan my system directories, because I install software from places I feel I can trust. If a file seems suspicious I will upload a file to virustotal.

Ubuntu's software can be trusted to be free from malware and viruses, because Ubuntu has a large scale community with many people who can read source code. I'm sure Ubuntu has good security measures in place for their repositories too.

As for downloading packages from 'elsewhere' on the internet, there is a bigger problem of downloading malicious scripts in software for Linux  than there is any having actual viruses. Only download software from places you feel you can trust and always do a checksum (whenever possible) to guarantee the file is complete and not tampered with.

---

### Post by Jive Turkey on 2011-04-18
> **bodhi.zazen said:**
> Linux is not Windows and the only people who advocate antivirus on LInux are :

1. New users from Windows.

2. Antivirus companies trying to sell you a product.

The valid user cases for running antivirus on Linux are:

1. If you are running a file server (samba) with windows clients, probably a good idea to scan the samba share from time to time.

2. If you are running a mail server.

3. If you are sharing files with Windows, although IMO you are better off skipping antivirus on Linux and running it on windows only.

The way Linux handles viruses is to patch the code, thus you are invulnerable to the known viruses.

Microsoft is either unwilling or unable to patch the code, thus Windows remains vulnerable to known exploits (most of the windows viruses are variations of a set of known exploits) and thus you need a 3rd party antiviurs to clean up.

I would add to this, that the primary reason there are so many viruses for windows is that it has the most market share and forms one big homogeneous target.  It makes a lot of economic sense for criminal malware R&D to focus on coding for windows.  The same effort could be put toward exploiting linux OSes but the return on their efforts would be much much smaller.

I came across some interesting commentary can be found on Win32 v. *nix security from Crispin Cowan (Formerly a linux coder now with MS) at this podcast: [http://media.risky.biz/auscert2010/RB2-AC-cowan.mp3](http://media.risky.biz/auscert2010/RB2-AC-cowan.mp3)

---

### Post by Graham-W on 2011-04-18
> **uRock said:**
> There isn't much to debate. If you feel that you need AV, then install it. [BitDefender]("https://help.ubuntu.com/community/BitDefender") is free to single users on Linux.

He's got it covered. But you don't need it, no ones going to target the small group of us, and it'd be a lot of work to make an effective virus for linux. Well I shouldn't say no one...

---

### Post by Timmer1240 on 2011-04-18
Ive been running linux for over a year havent needed antivirus yet It just keeps on running fast as all heck and no problems at all except for me messing it up a few times!

---

### Post by Frogs Hair on 2011-04-19
This list is from 2008.[http://technews.in/news/software/list_of_linux_viruses_-_trojans_-_worms/](http://technews.in/news/software/list_of_linux_viruses_-_trojans_-_worms/)

---

### Post by mynameisnotbob on 2011-04-19
Just to be fair to Windows, the reason that I've heard for not needing antivirus on Ubuntu or Macs is that since Windows is the mainstream OS, the *vast* majority of viruses written are for that platform. There are pieces of code written to exploit Ubuntu security flaws, but there are patches quickly written for them and put up by Ubuntu. That's what a security update is. There are so many for Windows that their security department just can't keep up with them. 

However, it is true that UNIX is more secure, due to the 'root' concept.

---

### Post by aysiu on 2011-04-19
This goes against conventional wisdom, and I know some on the forums here would strongly disagree with me, but apart from maintaining a file or mail server, I don't think anyone should be using antivirus, regardless of the platform (Windows, Mac, or Linux).

I basically have just seen it add zero protection to installations in many use cases. And I often see it backfire in several ways (so that it not only doesn't *add* protection but, in fact, practically *takes away* protection): [list=1][*]Antivirus in terms of comparing lists of known viruses is reactive instead of proactive by nature so will always miss the latest threats.[*]Antivirus when trying to be "smart" inevitably identifies false positives. This means that either a power user is forced to examine the file herself anyway (rendering antivirus useless) or the ordinary user is made paranoid, thinking every legitimate file is a virus or a "tracking cookie" (not even knowing what that is).[*]Power users are pretty good about not installing random files downloaded off the internet unless they're from trusted sources.[*]Ordinary users will gain a false sense of security from having "antivirus" installed and thus install things willy-nilly, thus being more susceptible to trojans.[*]A reliance on "antivirus" makes ordinary users all the more prone to rogue virus attacks (pop-up windows pretending to be antivirus alerts).[/list]

I highly advocate (and this goes for Mac, Windows, and Linux) using the built-in permission separations and authentication methods, using common sense, and something like NoScript for Firefox.

More details here:
[The antivirus paranoia culture](http://www.psychocats.net/ubuntucat/antivirusculture/)

---

### Post by mynameisnotbob on 2011-04-19
Indeed that is true. But as you said it is helpful when you run a fileserver. Besides, for the people that are power users, antivirus does keep out old viruses still making the rounds of the internet. But don't go out and buy it. There are plenty of good free ones.

---


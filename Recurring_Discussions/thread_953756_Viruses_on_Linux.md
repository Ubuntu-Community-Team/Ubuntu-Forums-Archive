---
title: "Viruses on Linux?"
date: 2008-10-20
forum: Recurring Discussions
---

### Post by Gennn89 on 2008-10-20
Is it possible to get viruses or spyware on linux operating systems by installing/downloading from internet, downloading from cd, using wine?

---

### Post by perlluver on 2008-10-20
There are some viruses for Linux, but not likely to get them.  However you can get viruses through wine, but they won't affect your entire system.  I recommend reading this: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by toasty_ghosty on 2008-10-20
Through my own experiences I've noticed a few things:

One, yes you can *get* a virus. However, as they viruses are typically (99.9%) of the time made for Windows, they will not run or do anything on Linux. So yes you can "get" one, but it will do nothing. Make sense?

Second, Wine is a replacement for Windows API. It is separate from Linux. So if you were to download a virus to your home folder, it would not transfer to Wine. But if you were to download one using an Internet Browser in Wine that could be a whole different story. I don't know if that is possible, it may as well be, but I would not worry about it. And as I said before since Linux is separate from Wine, even if it did somehow infect Wine, it would not do anything to your Linux system.

Someone who knows more feel free to correct me.

---

### Post by beno1990 on 2008-10-20
A Windows virus which you catch through using Wine will affect Wine and only Wine, since Wine is what is emulating the Windows API, not the rest of your Linux system. The simple solution in the event of catching a virus on Wine would be to uninstall Wine, remove all config files, and reinstall. But that's far less than optimal.

---

### Post by NewJack on 2008-10-20
Here is a good article from Security Focus on the subject:

[http://www.securityfocus.com/columnists/188](http://www.securityfocus.com/columnists/188)

Also, here is the Wiki regarding Linux Viruses:

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

Someone can correct me if I am wrong, but since viruses require root access it makes it tougher for them to propagate on your system, unless you specifically allow it.  

Just make sure you are running as a normal user and you should be fine and only use your admin account when necessary (making system changes, etc).  That way if you do happen to contract a virus the worst that should happen is you screw up your /home directory.

Some people (myself included) also install A/V software if they are dealing with Windows users regularly to catch any Win Viruses that may be attached to any files to be used in Windows.  That is just to be a "good neighbor" to your Windows counterparts  :)

---

### Post by gn2 on 2008-10-20
This is worth reading: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Gennn89 on 2008-10-20
So I'm understanding that noone really cares about checking for viruses or even finding some sort of program that scans because thats only a windows issue?

---

### Post by perlluver on 2008-10-20
Right, basically unless you install the virus yourself, it is basically impossible.

---

### Post by ./. on 2008-10-20
> **Gennn89 said:**
> So I'm understanding that noone really cares about checking for viruses or even finding some sort of program that scans because thats only a windows issue?
There are actually a few anti-virus solutions available to install on Linux.  It's worth scanning for viruses if you happen to share files among other Windows users.

[http://www.clamav.net/](http://www.clamav.net/)
[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)
[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)
[http://www.f-prot.com/download/home_user/download_fplinux.html](http://www.f-prot.com/download/home_user/download_fplinux.html)

---

### Post by perlluver on 2008-10-20
Right there is Clam-AV or Avast free for Linux, both will scan for viruses that you can transfer to Windows.

---

### Post by NewJack on 2008-10-20
Not that no one cares, but if you are careful and take preventive measures you should not be affected by one.  There are precautions to be taken to keep you from getting one.  Maybe as Linux/Ubuntu grabs more of the market share things may change, but for now I wouldn't worry too much.

I don't know if you read the link that gn2 provided to bodhi.zazen's thread on Ubuntu Security, but this is right from the beginning of the thread:

> Basics


This advice is fairly generic and applies to almost any OS. These simple steps offer a solid foundation that you should be able to implement almost immediately.

    * Enforce strong passwords [http://en.wikipedia.org/wiki/Password_strength](http://en.wikipedia.org/wiki/Password_strength)
    * In general, do not write your passwords down, and if you must, keep them in a secure place (Do not put them on a sticky note attached to your monitor for example).
    * Limit root access (Do not log in or run programs as root). Ubuntu accomplishes this by locking the root account and the use of sudo.
          o Consider creating an account without sudo access for "daily use".
    * Physical access (physical access = big security hole). Physical access allows root access to your system (via a live CD if necessary).
    * Do not install software or add repositories from untrusted sources (See also "Social engineering" below).
          o This includes running scripts that modify your /etc/apt/sources.list Take care not to let the "need" to run the newest/latest/greatest compromise security.
    * Likewise, do not run code or enter commands into the terminal from untrusted sources. If you are unsure of what a command might do best do a google search first.
    * Keep your system up to date. Updates, particularly security updates, bring you the newest and latest fixes.
    * If you run a server, it is your responsibility to learn how to secure it.


That thread has a great deal of information on how to protect yourself.

---

### Post by NewJack on 2008-10-20
> **perlluver said:**
> Right there is Clam-AV or Avast free for Linux, both will scan for viruses that you can transfer to Windows.

Also, I believe AVG offers a linux client as well


Edit:

They do offer a .deb file.  Check out this link: 

[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

---

### Post by gn2 on 2008-10-20
> **Gennn89 said:**
> So I'm understanding that noone really cares about checking for viruses or even finding some sort of program that scans because thats only a windows issue?

Can't speak for everyone, but I'm of the opinion that Operating Systems that are vulnerable to viruses should look out for themselves.

Currently there are no viruses for Linux in the wild, so there is no need to run A-V software in a Linux PC.

---

### Post by NE Key on 2008-10-20
I am guessing that you are a beginner, like me.

Others will give you a more technical answer but here are a few points;

The virus is probably written for windows - so it will be in the wrong language and will not be "understood" by linux.

When you use windows you will (almost invariably) have full administrator privileges. In linux you will not - to understand what this means try to edit or delete one of the boot programs in linux - the system should say that you do have permission to do this. So if you bring in a virus with an e-mail in linux, it will not be allowed to write itself to desk and do its virus thing unless you actually give it permission. You will have to install it yourself.

What you can do quite easily (accidentally) is save a virus to a thumb-drive/pen-drive/USB-drive - whatever they are called this week. It will do nothing to your linux computer but when you plug that drive into a USB port on a windows computer the virus can be copied into the windows computer where it will do its thing.

One of the ideas behind linux is that it was designed for many users. Each user on the computer cannot "mess" with another user's "stuff" and only 'root' has the power to do anything he wants and alter all of the files.

So a virus can only save itself to disc and start running and alter other files if it has been given permission to do so, by _you_. That is the biggest thing that makes linux more secure than windows.
 
Now that was the non-technical version from a beginner. Others will give a better answer but you can use this to explain to windows users why linux is less susceptible to virus problems.

---

### Post by NewJack on 2008-10-20
> **ne key said:**
> i am guessing that you are a beginner, like me.

Others will give you a more technical answer but here are a few points;

the virus is probably written for windows - so it will be in the wrong language and will not be "understood" by linux.

When you use windows you will (almost invariably) have full administrator privileges. In linux you will not - to understand what this means try to edit or delete one of the boot programs in linux - the system should say that you do have permission to do this. So if you bring in a virus with an e-mail in linux, it will not be allowed to write itself to desk and do its virus thing unless you actually give it permission. You will have to install it yourself.

What you can do quite easily (accidentally) is save a virus to a thumb-drive/pen-drive/usb-drive - whatever they are called this week. It will do nothing to your linux computer but when you plug that drive into a usb port on a windows computer the virus can be copied into the windows computer where it will do its thing.

One of the ideas behind linux is that it was designed for many users. Each user on the computer cannot "mess" with another user's "stuff" and only 'root' has the power to do anything he wants and alter all of the files.

So a virus can only save itself to disc and start running and alter other files if it has been given permission to do so, by _you_. That is the biggest thing that makes linux more secure than windows.
 
Now that was the non-technical version from a beginner. Others will give a better answer but you can use this to explain to windows users why linux is less susceptible to virus problems.

+1

---

### Post by sethvath on 2008-10-20
> **NE Key said:**
> 
So a virus can only save itself to disc and start running and alter other files if it has been given permission to do so, by _you_. That is the biggest thing that makes linux more secure than windows.
 

The biggest vulnerability is between the desktop and chair, does not matter whether its linux or windows. You can have the best fortified castle and it wont matter if someone in the castle is dumb enough to open the door for a single infiltrator.

---

### Post by bodhi.zazen on 2008-10-20
> **Gennn89 said:**
> So I'm understanding that noone really cares about checking for viruses or even finding some sort of program that scans because thats only a windows issue?

Basically, yes that is true. Do you know anyone who scans their windows computers for Linux vulnerabilities ?

Linux is not windows and you will need to learn how Linux security works as there are both similarities and major differences then Windows.

---

### Post by NE Key on 2008-10-20
> **bodhi.zazen said:**
> Basically, yes that is true. Do you know anyone who scans their windows computers for Linux vulnerabilities ?

What a superb comment.

---

### Post by hopesdevid on 2008-10-20
hi friend,
             There are virus, but they are extremely rare, so not much to be worried about.
never needed to install any AV on a linux system though, usualy it crashes of free will before a virus can get to it. X org is a pain in the.... for doing that.

---

### Post by ITAndrew on 2008-10-20
As stated earlier you can be infected by a Windows virus if you use emulation such as Wine or any other Win32 based libraries. I have actually had a virus infect me via an installer that I had downloaded and ran via Wine and infect Windows executable files I had on external and internal hard drives, which I'm sure could have easily spread over the network to my other Win32 clients.

In my opinion, you should always be AWARE of what you are doing and if something seems strange (including the source) just scan the file.

---

### Post by nubdora on 2008-10-21
If you do a lot of file sharing, especially P2P, having a virus scanner on your linux system is appreciated by those who use a windows system. They can transfer through your Zune, Ipod, Thumbdrive, etc to Windows machines you connect these peripherals to, but the peripherals are not affected as there are few, if any, viruses written for them. This concept applies to Linux web and mail servers as well. 

In relation to the linux kernel, there are very few viruses written for it and active in the wild. To attain one you would have to manually install it and run as root to damage your system.

---

### Post by MaxIBoy on 2008-10-21
[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)
Could be instructive.

---

### Post by Twitch6000 on 2008-10-21
*falls out of his chair*

People are now realizing there is atleast one virus for Linux and not lying holy cow someone has listened to me LOL.[/badjoke]

For real though @op/topic starter Linux does have viruses,but is very unlikely for you to get them.

If you are not running a server I wouldn't really think about getting a anti virus.

If you are running a server though get ClamAV to scan files and you are all good :).

---

### Post by sethvath on 2008-10-21
You can get viruses on a linux system, be it a compromised .exe file with a payload or a .py script designed to steal sudo access whenever you do a gksu. They are both viruses except the former will not harm you as much as the latter on a linux system.

So yes anyone can get a virus on a linux system just like how Simian immunodeficiency virus transferred to bush hunters from wild monkeys would lay dormant for years in the human host before it finally found a way to mutate into HIV.

---

### Post by Grant A. on 2008-10-21
> **sethvath said:**
> You can get viruses on a linux system, be it a compromised .exe file with a payload or a .py script designed to steal sudo access whenever you do a gksu. They are both viruses except the former will not harm you as much as the latter on a linux system.

So yes anyone can get a virus on a linux system just like how Simian immunodeficiency virus transferred to bush hunters from wild monkeys would lay dormant for years in the human host before it finally found a way to mutate into HIV.

Well, anything that destroys or harms data is a virus. Ex. a .sh script containing:

*DANGER! DO NOT ATTEMPT!*

the code to delete files specified to /

ran as root is a virus technically. A simple one, but a virus nonetheless by definition.

---

### Post by cardinals_fan on 2008-10-21
> **Grant A. said:**
> Well, anything that destroys or harms data is a virus. Ex. a .sh script containing:

*DANGER! DO NOT ATTEMPT!*

the code to delete files specified to /

ran as root is a virus technically. A simple one, but a virus nonetheless by definition.
Actually, that's wrong.  "Virus" is the most commonly misused computer term out there.  It actually means "a computer program that can copy itself and infect a computer without permission or knowledge of the user".

Almost all malware nowadays is based on social engineering, and plays off user incompetence rather than weaknesses in the system.

---

### Post by sethvath on 2008-10-22
> **Grant A. said:**
> Well, anything that destroys or harms data is a virus. Ex. a .sh script containing:

*DANGER! DO NOT ATTEMPT!*

the code to delete files specified to /

ran as root is a virus technically. A simple one, but a virus nonetheless by definition.

Read the definition of a virus by the guy who invented computer virus defense techniques. 

[http://all.net/books/virus/part2.html](http://all.net/books/virus/part2.html)

Anything that harms data is NOT A VIRUS. Its called a malware.

---

### Post by billgoldberg on 2008-10-22
> **Gennn89 said:**
> Is it possible to get viruses or spyware on linux operating systems by installing/downloading from internet, downloading from cd, using wine?

As far as I know, there are no viruses on the internet that can infect a linux box without any help from the user itself.

Those viruses have been patched out of existance.

That doesn't mean you are save from malware, it does mean the changes of you getting infecting from browsing the web or downloading stuff is extremely small.

Just to be safe, use the same rules when download/browsing as you would on a Windows pc.

For example, don't open virus attachments unless you asked for them, ...

--

If you are really paranoid, install rkrootkit and run it.

--

Also it might be a good idea to change the sudo timeout to 0.

[http://linuxowns.wordpress.com/2008/10/21/change-gksudo-timeout/](http://linuxowns.wordpress.com/2008/10/21/change-gksudo-timeout/)

--

Also only download software from trusted places.

Don't just give any script you download from the web the privileges it needs.

---

### Post by RATM_Owns on 2008-10-22
Why GNU/Linux Viruses are fairly uncommon...
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

---


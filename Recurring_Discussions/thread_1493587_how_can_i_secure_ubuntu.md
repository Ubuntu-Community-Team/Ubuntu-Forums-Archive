---
title: "how can i secure ubuntu"
date: 2010-05-26
forum: Recurring Discussions
---

### Post by neilmaclennan on 2010-05-26
i have downloaded klam av and firestarter firewall whatb next. i saw a site that mentioned altering some file but etc/sshd does not exist ssh does but no entry for changing root login to no instead of yes and when i added extra line of code to fstab i could not get it to save as i did not have the correct permissions even when i changed "click to make changes" in the user groups err thingy (sorry i'm very green" but know windows well so if you can give me a step by step i can follow it also i wanted to install snort but was not able to figure it out and avg too but then went to klam instead but when i tried to remove avg it said it wasn't installed but i extracted/ran it but then couldn't find it in the file menus anywhere. sorry i is err dumb about this but smart like paint chip honnest guv. ok enough playin please help i don't want to be hacked and used as a zombie mailer. oh and i would like to install backtrack too if that would help my situation. ty

---

### Post by Sef on 2010-05-26
> i have downloaded klam av and firestarter firewal.... 

First you do not need an anti-virus, unless you run an email client, and then only to keep from infecting your friends who run windows.  Firestarter is dead project; better to download UFW from the repositories.  Applications > Ubuntu Software Center

---

### Post by cbbnewbie on 2010-05-26
i think ubuntu is secure enough no need to install antivirus programs..just my opinion from what i read about linux.

---

### Post by mastablasta on 2010-05-26
Can't help you with Antivirus (yet) but as i knwo firewall is already installed in linux by default. What you actually need is a graphics interface to communicate with it. Mint comes with one and i think you can use that one in ubuntu as well. Forgot the name at the moment :-)
 
EDIT: 
> **cbbnewbie said:**
> i think ubuntu is secure enough no need to install antivirus programs..just my opinion from what i read about linux.
  
 
Kernel yes, but user GUI not really. Anyway there is always that dumb moment we newbies could have and run something nasty... :-)

---

### Post by neilmaclennan on 2010-05-26
thanks i did that i got ufw now. should i ununstall Klam if i send blogs to someone that is buying them or will ki be ok? and i still want to install snort etc...

---

### Post by neilmaclennan on 2010-05-26
how do i acces the ufw i can't find it in any of the pull down menus "applications places system"
thanks for the quick replies i am amazed way quicker than any other forum i been to

---

### Post by wilee-nilee on 2010-05-26
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Nythain on 2010-05-26
i keep hearing a lot of "linux doesnt need anti-virus" stuff... if i had to guess, i would say most desktop linux users (especially ubuntu ones) are just one computer on a home network with at least one other Windows machine... i run clam-av to make sure that im not a "carrier", just because i can't get infected doesnt mean someone else in my home cant get infect from something i download

---

### Post by 3rdalbum on 2010-05-26
Ubuntu is secure out-of-the-box. You don't even need a firewall; a firewall stops programs from recieving remote connections, and on Ubuntu there are no programs that listen for remote connections anyway (unless you change their settings to listen).

Ordinary users cannot modify files outside their home directory - this includes you. In order to modify system files that are owned by root (the administrator account) you need to make the modifications as root.

The easiest way is to install the 'nautilus-gksu' package from Synaptic Package Manager. When you next log in, you'll be able to right-click any file or folder and choose "Open as Administrator".

However, I can't think of any modifications to /etc/fstab that will enhance security in any meaningful sense; if you don't understand exactly what the modification does, DO NOT DO IT.

---

### Post by neilmaclennan on 2010-05-26
[LIST]
[*]*Disabling SSH root login*
Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:PermitRootLogin yes
to
PermitRootLogin no


i went to the site [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)
and I could not find sshd_config only ssh_config and there was no permitrootlogin no   in the file. should I add that to the file or not?


oh and i did get the run as admin to work so i could save this line of text in fstab tmpfs /dev/shm tmpfs defaults,ro 0 0 



was that ok to do?




[/LIST]

---

### Post by neilmaclennan on 2010-05-26
[LIST]
[*]*Limiting access to the "su" program*
Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:sudo chown root:admin /bin/su  sudo
chmod 04750 /bin/su


and is it ok to go ahead and do this too?


[/LIST]

---

### Post by AcidMoon on 2010-05-26
If your not a hardcore iptables fan take a look at: [http://mauroandres.wordpress.com/?s=ufw](http://mauroandres.wordpress.com/?s=ufw).

---

### Post by bodhi.zazen on 2010-05-26
You should NOT be editing or changing system files without understanding what and why you are doing these things.

You are starting to follow bad or at best incomplete advice. I have seen the link you got the information from and I would not suggest you start with the advice on that page.

For Example, by default , openssh-server is not installed, so there is no file to edit.

The security link was already posted, I suggest you stop and read through that first.

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

There is a reason that link is a sticky ^^

From there you can read the hardening Debian guide, at least that explains what and why you would be editing system files :

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

[http://wiki.debian.org/Hardening](http://wiki.debian.org/Hardening)

As has been indicated earlier, Linux is not windows and your system is already secure. Editing or changing security / system files without understanding what you are doing and how to undo changes will either break your system or lower your security.

---

### Post by AcidMoon on 2010-05-26
> **bodhi.zazen said:**
> As has been indicated earlier, Linux is not windows and your system is already secure. Editing or changing security / system files without understanding what you are doing and how to undo changes will either break your system or lower your security.

Bam! Well said! I hope you're not unhappy with my post. The link about securing UFW is probably the best on the net :)

---

### Post by bodhi.zazen on 2010-05-26
> **AcidMoon said:**
> Bam! Well said! I hope you're not unhappy with my post. The link about securing UFW is probably the best on the net :)


Moved to recurring discussions.
I am partial to my own, but I would not claim they are the best on the net :lolflag:

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

### Post by neilmaclennan on 2010-05-26
> **bodhi.zazen said:**
> You should NOT be editing or changing system files without understanding what and why you are doing these things.

You are starting to follow bad or at best incomplete advice. I have seen the link you got the information from and I would not suggest you start with the advice on that page.

For Example, by default , openssh-server is not installed, so there is no file to edit.

The security link was already posted, I suggest you stop and read through that first.

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

There is a reason that link is a sticky ^^

From there you can read the hardening Debian guide, at least that explains what and why you would be editing system files :

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

[http://wiki.debian.org/Hardening](http://wiki.debian.org/Hardening)

As has been indicated earlier, Linux is not windows and your system is already secure. Editing or changing security / system files without understanding what you are doing and how to undo changes will either break your system or lower your security.

OK I undid the one change I was able to do and am going to look at the link you provided. Ya know if this was windows i would be more cautious about doing stuff like that. as it's linux i am a little or was a little too trusting when it came to that sort of thing. thanks for your help i will read through that text from your link thanks again

---

### Post by AcidMoon on 2010-05-26
> **bodhi.zazen said:**
> Moved to recurring discussions.
I am partial to my own, but I would not claim they are the best on the net :lolflag:


Actually: [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/) seems excellent. Bow to the ubuntu forum Gods [-o<

---

### Post by neilmaclennan on 2010-05-26
i forgot i did enter neil@neil-laptop:~$ chmod 0700 /home/neil
should i revert this and how do i do that?
also i have installed thunderbird i think but can only find the run link in the extracted folder to start it is it somewhere in the aplications places system drop menus? if so where and i would like to have a desktop link that shows the tbird icon like in windows if possible. oh and if this is in the wrong place then let me know where to post it to get the answer ty

---

### Post by AcidMoon on 2010-05-26
> **neilmaclennan said:**
> i forgot i did enter neil@neil-laptop:~$ chmod 0700 /home/neil
should i revert this and how do i do that?


I'd recommend the command                                         [FONT=URW Gothic L]**chmod 700 $HOME**[/FONT]

---

### Post by neilmaclennan on 2010-05-26
> **AcidMoon said:**
> I'd recommend the command                                         [FONT=URW Gothic L]**chmod 700 $HOME**[/FONT]

what does that do?

---

### Post by AcidMoon on 2010-05-27
> **neilmaclennan said:**
> what does that do?

Hi it confirms that only you can read, write to and execute things in your home dir. There may be better links on chmod but take a look here to start with. [http://www.december.com/unix/ref/chmod.html](http://www.december.com/unix/ref/chmod.html) 
Hope this helps :)

---

### Post by Shining Arcanine on 2010-05-29
As far as I know, Linux does not need a firewall or antivirus. You can run them if you want, but they are unnecessary. A firewall is unnecessary because Linux by default does not run any services that listen on ports like Windows, and any services that you configure it to run are things that you will both want to be available and properly maintain. An antivirus is unnecessary because anything on your system cannot execute as root, so it cannot do much and virii tend not to be written for Linux.

---

### Post by neilmaclennan on 2010-05-29
> **Shining Arcanine said:**
> As far as I know, Linux does not need a firewall or antivirus. You can run them if you want, but they are unnecessary. A firewall is unnecessary because Linux by default does not run any services that listen on ports like Windows, and any services that you configure it to run are things that you will both want to be available and properly maintain. An antivirus is unnecessary because anything on your system cannot execute as root, so it cannot do much and virii tend not to be written for Linux.

man! you have absolutely no idea how happy that makes me guess I will just have to accept that as that's all I seem to hear no matter how against the grain that sounds to me coming from windows and I just wish they made call of duty 1, 2, 4, 5, 6 in Linux then I would never use windows again. Linux is sooooo much faster than windows even after I have had it installed and run it after installing other components and software windows is and has only been so quick after a fresh install without anything else once you install other stuff it begins to get slllooowwwerrr and slower not so from what I see from Linux and no I'm not paid to say that. Open office still could use a grammatic and voice recognition like Microsoft Office which I like unless there is and I just didn't find the install for it and if there is then please let me know and for the call of duty games too. 

But I still would stay with this Linux OS now I have taken the time to learn it a bit more and seen that apart from the super tweaking it isn't all that hard to get the hang of except from having to build drivers etc... which I still have to do because of my damn Atheros driver and toshiba laptop, unless I have to just activate wifi which in that case please let me know how to do that then my Windows drive can just be the fancy game system I know it should be. bla blah bla sorry for ramblin I had some beers. Thanks Linux comunity I love this new OS I took the time too implement Please help the newbies like me and maybe Windows will fall

---

### Post by Shining Arcanine on 2010-05-29
If compiling software manually is difficult for you, you might want to consider a distribution that does it for you:

[http://www.gentoo.org/doc/en/handbook/](http://www.gentoo.org/doc/en/handbook/)
[http://www.gentoo.org/doc/en/gnome-config.xml](http://www.gentoo.org/doc/en/gnome-config.xml)

It is a bit more advanced than Ubuntu Linux, but if you follow the handbook and then the appropriate documentation for installing your choice of desktop environment, it is fairly easy to install and use afterward is not much different than Ubuntu Linux. Gentoo Linux installs everything from source code and automates the process of compiling software for you, so the more mundane details are things you can ignore.

With that said, it appears that there are instructions for installing wireless drivers for your card on the Ubuntu Wiki, although they are somewhat dated:

[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

Compiling them appears to be unnecessary, depending on the version of Ubuntu Linux you use, although I imagine that they are available on all versions of Ubuntu Linux and that the Wiki page simply has not been updated.

---

### Post by ubun2warrior on 2010-05-29
i use firestarter to keep track of my net usage

---

### Post by bodhi.zazen on 2010-05-29
> **ubun2warrior said:**
> i use firestarter to keep track of my net usage

That is not such a good idea nor is it secure.

Use Wireshark and/or monitor the logs and or use iptables, depending on your needs.

---

### Post by chascon on 2010-12-08
> **AcidMoon said:**
> Actually: [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/) seems excellent. Bow to the ubuntu forum Gods [-o<

Don't apologize AcidMoon. I happen to think you're right, I did write the best two articles/HowTos on ufw on the net, at least at the time ;

I even explicitly state that I wrote them because the material out there on the net (HowTos and wikis) and in the man just suck, to put it politely. I tried to write a comprehensive guide addressing common with real life security issues in a manner that people with little line command experience can understand. Since people think line command utilities are hard to use, this demands clearly written guides (no uncertain terms and concise explaining & modelling). I think I was more than successful in providing this. Most of my articles/HowTos lack pretty pictures that others incorporate, though --if you feel you need that sort of thing.


The third instalment may suck, a little, if and when I get around to posting it (it's on a dead computer). It may not be of the same "quality" but really it's just a list of interesting non-essentials and was never meant to be much more. Actually, it was never planned upon and sort of "emerged" out of the research I was doing into ufw.


As for those claiming that Gnu-linux desktop systems don't need a firewall, I'm not so sure. Considering all of the needless and suspicious pings and other traffic that I've noticed coming in and the coming of age of Gnu-linux as a de facto OS and thus becoming the target of all sorts of malware, this makes me justify my paranoid stance. Besides, I personally haven't noticed a humanly perceivable performance hit for running a firewall (on a linux based system, anyways ... Windows is/can be another story).

I guess what these people are saying is that linux is like a house, and a firewall is like a door/gate/window. If you don't have anything that can entice someone to break in (and the weather is ideal), you don't need protection and if you have valuables (that make it easy to decide to break in), then you do need protection. 

Hmm, I still rather have protection regardless of the contents of my house. It's called security by layers. Not running needless software that makes one vulnerable is one layer of protection, and running a firewall is another --just in case of anything.

As for, those claiming the coming of the apocalypse just because people modify things on their system, take those with a grain of salt. It all depends on what you're doing. Installing/enabling a firewall is not anything out of this world. And barring you don't block your connectivity to local or area networks (assuming you want connectivity), you should be fine. You can't be any worse off than running with all your ports open (a house with holes for windows, and doors), can you? Think about it.

My first firewall HowTo is basically ufw for dummies, so if you're worried about screwing things up there's that. Otherwise there's gufw --but don't get me started on gui utilities.

[http://mauroandres.wordpress.com/2009/12/14/build-a-secure-desktop-firewall-with-ufw-part-i/](http://mauroandres.wordpress.com/2009/12/14/build-a-secure-desktop-firewall-with-ufw-part-i/)
[http://mauroandres.wordpress.com/2010/01/28/build-a-secure-desktop-firewall-with-ufw-part-ii/](http://mauroandres.wordpress.com/2010/01/28/build-a-secure-desktop-firewall-with-ufw-part-ii/)

---

### Post by chascon on 2010-12-11
> **Shining Arcanine said:**
> If compiling software manually is difficult for you, you might want to consider a distribution that does it for you:

[http://www.gentoo.org/doc/en/handbook/](http://www.gentoo.org/doc/en/handbook/)
[http://www.gentoo.org/doc/en/gnome-config.xml](http://www.gentoo.org/doc/en/gnome-config.xml)

It is a bit more advanced than Ubuntu Linux, but if you follow the handbook and then the appropriate documentation for installing your choice of desktop environment, it is fairly easy to install and use afterward is not much different than Ubuntu Linux. Gentoo Linux installs everything from source code and automates the process of compiling software for you, so the more mundane details are things you can ignore.


There's no need to move off to Gentoo which is philosophically incompatible with Debian/based distros, and what most us have become accustomed to or accepted.

Wajig, a Debian utility, (which should be available on Ubuntu) handles this sort of stuff and much more. See the following.
[http://web.archive.org/web/20080617204657/http://wiki.xtronics.com/index.php/Wajig](http://web.archive.org/web/20080617204657/http://wiki.xtronics.com/index.php/Wajig)
[http://lwn.net/Articles/223288/](http://lwn.net/Articles/223288/)
[http://www.togaware.com/linux/survivor/Wajig_Overview.html](http://www.togaware.com/linux/survivor/Wajig_Overview.html)

hint:
"build -- Retrieve/unpack sources and build .deb for the named packages"

Recommendation: wean off of gui utilities to gain access to other possibilities, fine grained control among other things.

---


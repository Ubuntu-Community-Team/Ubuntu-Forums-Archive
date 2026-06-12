---
title: "Am I Safe?"
date: 2008-08-22
forum: Recurring Discussions
---

### Post by jozmoz on 2008-08-22
Hi,
I want to view my banking details, but am i safe using ubuntu? Do I need a firewall? :confused:

---

### Post by jerome1232 on 2008-08-22
Firewall has nothing to do with it.

If the banks website uses encryption your fine, and of course look out for phishing scams or dns poisoning (redirection to a phishing site) (I believe openDNS is patched against the recent DNS weakness some isp's DNS servers aren't)

---

### Post by t0p on 2008-08-22
> **jozmoz said:**
> Hi,
I want to view my banking details, but am i safe using ubuntu? Do I need a firewall? :confused:

If the connection was insecure for some reason, it would not be down to you using ubuntu.

---

### Post by jozmoz on 2008-08-22
So I don't need a firewall, anti-virus, and anti-spyware software in Ubuntu?

---

### Post by halitech on 2008-08-22
need no, required no, if you want to ptotect your windows using friends, maybe. check here for more info: [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

---

### Post by t0p on 2008-08-22
> **jozmoz said:**
> So I don't need a firewall, anti-virus, and anti-spyware software in Ubuntu?

I don't know of any spyware problem in ubuntu.  The os is also "virus-proof", though some users use ClamAV to check they haven't picked up a windows virus. (a windows virus won't affect ubuntu, but some folks check because they don't want to inadvertently send a windows virus to a windows-using friend.

I can't comment on firewalls, as I don't know much about them.

---

### Post by jerome1232 on 2008-08-22
You only need a firewall if you plan on runing servers on your computer like sshd ftpd telnetd, none of are installed by default, without programs listening for incoming connections, there's really nothing to hack.

There are a few, very difficult to get Linux virii out there, impossible to get if you install programs from trusted/well known sources and of course the repos. 

Other than cross platform java/flash/script based attacks, you don't have much to worry about, the ones i've seen are minor (a flash script that keeps copying things into your clipboard thus not allowing you to copy/paste) can be eliminated by using the add-on 'noscript', which disables java/flash/scripts for everything other than trusted sites, (like your bank for example).

You might want to check this sticky on ubuntu securtiy if you want to read up. [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421) it's pretty good.

---

### Post by halitech on 2008-08-22
> **t0p said:**
> I don't know of any spyware problem in ubuntu.  The os is also "virus-proof", though some users use ClamAV to check they haven't picked up a windows virus. (a windows virus won't affect ubuntu, but some folks check because they don't want to inadvertently send a windows virus to a windows-using friend.

I can't comment on firewalls, as I don't know much about them.

no OS is virus proof unless the computer it is installed on is turned off. Virus resistant due to the security model that *nix employs would be a better way of putting it because viruses do exist but unless you run as root (in which case you deserve to have your system blown up on you) or run the virus file yourself, *nix is pretty secure.

---

### Post by jerome1232 on 2008-08-22
> **halitech said:**
> no OS is virus proof unless the computer it is installed on is turned off. Virus resistant due to the security model that *nix employs would be a better way of putting it because viruses do exist but unless you run as root (in which case you deserve to have your system blown up on you) or run the virus file yourself, *nix is pretty secure.

not to mention you'd probably have to compile said virus from source :)

---

### Post by halitech on 2008-08-22
that too :D

---

### Post by iansane on 2008-08-22
> **halitech said:**
> no OS is virus proof unless the computer it is installed on is turned off. Virus resistant due to the security model that *nix employs would be a better way of putting it because viruses do exist but unless you run as root (in which case you deserve to have your system blown up on you) or run the virus file yourself, *nix is pretty secure.

That's usually the case in windows too. People using admin account or downloading a virused file and clicking on it. I must say I find it funny that vista UAC is very similar to linux security. (asking for admin/root password). However, no body has yet been able to explain to me in detail what it is about the linux architecture that keeps it from getting infected by other means like windows will even with a restricted account. I guess it's cause the community keeps holes patched better than windows? Don't know why someone can't just write an exploit for linux as easy as they can for windows.

---

### Post by jimbean on 2008-08-22
ubuntu has not lockedup for me because of a virus in 3 years {its the site you visit and the {scripts u run in ubuntu} ubuntu is goooood

its as good as any other code out there {operating systems} if you trust microsoft and linux and att and the, your us congressmen and senator  {paranoid}

then your ok

free is good
the rest is bs sorry ubuntu
i love america

---

### Post by kwilliam on 2008-08-22
Unless you think your banking website is going to attack your computer, you don't need a firewall. I have a firewall on my laptop, because I sometimes use it in places with public Wi-Fi and want to be on the safe side. I think Linux has a built-in firewall system, but you use programs like Firestarter (for Gnome) or Guarddog (for KDE) to turn it on and configure it.

But back to bank websites. Before visiting bank websites (or any website where you transfer money, like Ebay or PayPal) you need to be aware of a few things:
[LIST=1]
[*]First, don't visit such sites by clicking on links in emails, because the emails could be fake and take you to a copy-cat site that looks like the real website, but just steals your passwords.
[*]Second, make sure you use an up to date web browser. Any banking website worth its stuff uses encryption - I can't imagine one that wouldn't - and you can usually verify that by looking for a color change in the address bar or a padlock icon.
[*]Third, don't use an unencrypted wireless connection to visit banking sites, because people could steal your password from the air! For instance, most public Wi-Fi hot spots (like Starbucks cafes, or Panera bread) don't use encryption, so I wouldn't log into your bank website from there. If you use Wi-Fi at home, make sure it's encrypted with WPA or WPA2. (That's worth another post, but it's not hard.)
[*] Lastly, like jerome1232 mentioned, DNS attacks where you type in the correct web address but are taken to a fake page *are* possible, although they're not very common. **Edit: [This is changing very quickly]("http://news.cnet.com/8301-1009_3-10022303-83.html?part=rss&subj=news&tag=2547-1009_3-0-20") (It was Slashdotted today.) I cannot in good conscience make light of it as I did originally.** I had been too lazy to worry about it until he mentioned [OpenDNS]("https://www.opendns.com/start"), but I looked into it - turned out to be a simple one step fix for my wireless router.
[/LIST]

To summarize, visiting a bank website in Ubuntu is no different from visiting one from a PC or a Mac. What matters is: not clicking on links from emails, using an up to date web browser, not using unencrypted Wi-Fi, and <strike>possibly what DNS server you use</strike> **using a quickly patched, up-to-date DNS server**.

---

### Post by jerome1232 on 2008-08-22
> **iansane said:**
> That's usually the case in windows too. People using admin account or downloading a virused file and clicking on it. I must say I find it funny that vista UAC is very similar to linux security. (asking for admin/root password). However, no body has yet been able to explain to me in detail what it is about the linux architecture that keeps it from getting infected by other means like windows will even with a restricted account. I guess it's cause the community keeps holes patched better than windows? Don't know why someone can't just write an exploit for linux as easy as they can for windows.

Yes mostly because when exploits are found they are patched quickly, usually before they are known in general.

Take for example the big security flaw that was discovered in debian with ssl, it wasn't generating very random keys. It was present for a long time but was patched the day they figured it out and before keys were getting mass hacked by bots trying the vulnerable keys.

In Windows Vista unprivileged users still have waaay to many privileges, where's in Unix like systems, the only thing a regular user can do is delete his own private files.

I guess it kinda comes from their uses too, Linux is primarily used in a multi-user server environment where security is very important, Windows is primarily and started off as a single user Desktop environment where ease of use is very important.

I know it's not a technical explanation at all, but you can google that and even check the security threads sticky which is pretty good.

---

### Post by halitech on 2008-08-22
> **iansane said:**
> That's usually the case in windows too. People using admin account or downloading a virused file and clicking on it. I must say I find it funny that vista UAC is very similar to linux security. (asking for admin/root password). However, no body has yet been able to explain to me in detail what it is about the linux architecture that keeps it from getting infected by other means like windows will even with a restricted account. I guess it's cause the community keeps holes patched better than windows? Don't know why someone can't just write an exploit for linux as easy as they can for windows.

a big part of it is because holes are patched quickly for the different versions of *nix compared to windows. Also, because of all the different distros and the way they work, what will run on a debian based system won't run on redhat based systems or slack based distros and vice versa. 

Linux by default is designed as a multi-user operating system so the root system is seperated from the users. Another thing with *nix is that fact that most people are conditioned against simply clicking on things without knowing what it is they are clicking on. 

It's not that they can't write an exploit for *nix as easily as they can for windows, its just plain harder to find an exploit and make something to run across all the different distros makes it less worthwhile. Plus, the vast majority of people are still using windows so the targets are more plentiful so why work harder for a small number of targets when you can write something easily for a large number of easy targets.

---

### Post by jerome1232 on 2008-08-22
Eh I dissagree with you on one point halitech, that linux doesn't have enough of a user base.

In the Desktop world yes Linux is small but.. in the server world.

ALOT of servers run various Unix like systems (BSD, GNU/Linux, others) and by alot I believe somewhere near the 50% range (not heavily researched just a number I remember off the top of my head)

---

### Post by kwilliam on 2008-08-22
> **iansane said:**
> Don't know why someone can't just write an exploit for linux as easy as they can for windows.

Part of the reason may be increasing use of [AppArmor]("https://help.ubuntu.com/community/AppArmor") and SELinux. I don't know much about the architecture either; I'm just glad it's more secure. It's painful to watch my brother endure Norton Anti-Virus/Firewall pop up and annoy/block him all the time.

---

### Post by Crafty Kisses on 2008-08-22
> **jozmoz said:**
> So I don't need a firewall, anti-virus, and anti-spyware software in Ubuntu?

No you have iptables, and it all depends on the website and how secure it is.

---

### Post by Sef on 2008-08-22
> 
Quote:
Originally Posted by jozmoz View Post
So I don't need a firewall, anti-virus, and anti-spyware software in Ubuntu?
No you have iptables, and it all depends on the website and how secure it is. 

IPTables is firewall that comes installed on Ubuntu Linux.  It is command line based.  If you want a GUI front end, there is Firestarter.

---

### Post by halitech on 2008-08-22
> **jerome1232 said:**
> Eh I dissagree with you on one point halitech, that linux doesn't have enough of a user base.

In the Desktop world yes Linux is small but.. in the server world.

ALOT of servers run various Unix like systems (BSD, GNU/Linux, others) and by alot I believe somewhere near the 50% range (not heavily researched just a number I remember off the top of my head)

I'll give you the server world has a very heavy presence and they are attacked there quite often (not successfuly but they are attacked) but for the point of this discussion, I was keeping things in the desktop world where most of us are at the moment where our user base (all *nix distros combined) is decent but if you break it down by distro, makes it even less of a target where you would need numerous versions of the same software to run on everything (almost impossible if you take into account those running linux from scratch where its hard to say what they've included or not included) where as with windows, pretty much write 1 script and you hit 95% of all windows users.

---

### Post by Gregmond on 2008-08-22
Sorry I think the whole attitude of "virus proof" is rubbish.
Yes there are very few. Yes there are harder to get installed. Not impossible.

Having something like CLAMAV installed and run it once every few weeks is good.
By default *nix is locked down reasonably well so adding FIRESTARTER is only going to let you look at your firewall and open up the holes.
If you want to see what is hitting your PC install MOBLOCK & MOBLOQUER (similar to peerguardian2).
Firefox tends to be a lot safer than IE, however as both can be installed on Linux.
Look at the site name and confirm with your bank that it is the correct location. Make sure any screen that wants a username or password is a secure site (https:// rather than [http://)](http://))

Do all that and you will be as safe as you can be without being over paranoid and under prepared imo.

---

### Post by skymera on 2008-08-22
Note: A virus can be install, it can be run and it can do damage. Just like windows.

But as said

- The virus probably needs to be compiled.
- To do REAL damage it will need root priveledges.
- People who run unknown scripts/programmes as root need a slap with a trout.
- There are very few.
- Linux can be patched very fast against new threats.

Don't worry yourself.

---

### Post by elmoosecapitan on 2008-08-22
I would say, baring personally compiling a malicious piece of code as root, you are fine. Just look over the 'Absolute Beginner's' stickies.

As for surfing the series of tubes we call the internet, if you are on an foreign, unsecured, i.e., not password protected, then you are taking your chances.

---

### Post by kwilliam on 2008-08-22
[COLOR="Red"][SIZE="5"]Correction: DNS poisoning is becoming a serious problem,[/SIZE][/COLOR] [SIZE="3"]and I probably should have recommended using [[SIZE="6"]OpenDNS[/SIZE]]("https://www.opendns.com/start") more strongly. See [this Slashdot article]("http://it.slashdot.org/article.pl?sid=08/08/21/2343250").[/SIZE]

---

### Post by kwilliam on 2008-08-22
> **elmoosecapitan said:**
> I would say, baring personally compiling a malicious piece of code as root, you are fine.

Why is everyone obsessed with "it would have to be compiled"? A python program or bash script certainly wouldn't need to. Plus, it a pre-compiled binary that was Ubuntu-only could still do significant damage.

---

### Post by anjilslaire on 2008-08-22
You can also install & run rkhunter & ckrootkit to check your system for rootkits if yuo're really concerned.

---

### Post by jerome1232 on 2008-08-22
[rant]
Ok, just for the sake of argument show me a pre-compiled binary that's on a site that would make me think, "okay I'll run this as root". 

That being said we are talking about a virus, not malicious scripts, which is what some of you are discussing.

Viruses have one attribute, they try to replicate themselves and spread to other computers. That is difficult on Unix like systems.[/rant]

I feel safe in saying that if you only install software from the repositories you will never get a Linux virus. There isn't much you can't do with the available software in the repositories.

That being said I've never said Linux is Immune, no OS is immune to social engineering. What Linux does do is encourage (over and over) safe computing practices. Such as avoiding running scripts as root.

I'm kinda thinking this thread should be moved to recurring discussions lol

---

### Post by cardinals_fan on 2008-08-22
> **jerome1232 said:**
> 
I'm kinda thinking this thread should be moved to recurring discussions lol
I'm kinda thinking that this thread is already in Recurring Discussions ;)

---

### Post by jerome1232 on 2008-08-22
> **cardinals_fan said:**
> I'm kinda thinking that this thread is already in Recurring Discussions ;)

Hey what do ya know :D

---

### Post by jamesrfla on 2008-08-22
You don't need a firewall unless you are hosting a web site or something else outside your network. You don't need a anti-virus unless you are sharing files between windows comps.

---

### Post by cprofitt on 2008-08-23
First:
Your chance of being attacked with Linux is low; though it increases if you host web sites or MySQL databases.

Second:
I recommend using the [UFW]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") controls for IP tables built-in with Ubuntu 8.04.; UFW is easy to use and will provide protection. While some will argue that you have no need for a firewall... I can not see not running one because it protects your computer.

---

### Post by SunnyRabbiera on 2008-08-23
> **jozmoz said:**
> So I don't need a firewall, anti-virus, and anti-spyware software in Ubuntu?

Not really, but be careful none the less;.
The best way to stay safe is to go to trusted sites and wipe your cookies when home banking

---

### Post by iansane on 2008-08-29
> **skymera said:**
> Note: A virus can be install, it can be run and it can do damage. Just like windows.

But as said

- The virus probably needs to be compiled.
- To do REAL damage it will need root priveledges.
- People who run unknown scripts/programmes as root need a slap with a trout.
- There are very few.
- Linux can be patched very fast against new threats.

Don't worry yourself.

Yes you are right but that means a lot of newbs being slapped with a trout including myself. LOL

The first thing I did when starting with Ubuntu was come here to the forums and get all kinds of advice from other newbs in the absolute beginner section about work arounds, downloadable scripts, and adding repos. And I see warnings about bad commands that will kill your system so it's not like everyone here can be trusted. Most of them can be though.

Now that I know better and have actually spent time reading the documentation, I get second opinions and think things through before I just take someones advice and run a script or install something like automatix or envy, which are frowned upon by some but worked fine when I used them.

Call it luck, all the bad things I did, I still never got a virus.

---

### Post by jimbean on 2008-09-01
just dont let me spook you



just type script in the search box in the top right hand corner
of ubuntu forums and read the posting that come up 
 

one that says script in the discription
the forum guru guys can explain it better than i could


my explanation would be its like an autoexec.bat or a config.sys or an *.exe
file in windows or dos, or a deb and or script file in {debian linux}

it tells the operating system and or computer what to do
it can install programs delete programs fix programs delete your whole harddrive


you personally contacted me and this is the only way i know how to contact you back

---

### Post by halitech on 2008-09-01
> **jimbean said:**
> my explanation would be its like an autoexec.bat or a config.sys or an *.exe
file in windows or dos, or a deb and or script file in {debian linux}

it tells the operating system and or computer what to do
it can install programs delete programs fix programs delete your whole harddrive

yes and no. yes a script can install programs and delete files but unless it is run as root, it can't touch any folder outside your /home folder so deleting the whole hard drive is unlikely. 

now, if someone had been foolish enough to enable the root account and was regularly logging in as root then I might be tempted to say they got what they deserved but that would be mean

---

### Post by doas777 on 2008-09-01
> **jozmoz said:**
> Hi,
I want to view my banking details, but am i safe using ubuntu? Do I need a firewall? :confused:


simply put, yes. 
theres a lot more you can do to heighten security, but you should be ready for online banking straight out of the gate.

have fun,
frank

---

### Post by Amarsingh0793 on 2008-09-02
Ubuntu is very secure. The only way to get malicious programs on ubuntu would be if you added an untrusted repository. As long as you stick to the official stuff, your system should be untouchable. I've had ubuntu since the begininng of 7.04 and have never had any problems with viruses, spyware, rootkits e.t.c.

---


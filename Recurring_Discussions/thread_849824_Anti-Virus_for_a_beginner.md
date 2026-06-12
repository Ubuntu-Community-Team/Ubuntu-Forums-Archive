---
title: "Anti-Virus for a beginner"
date: 2008-07-04
forum: Recurring Discussions
---

### Post by Bigpom on 2008-07-04
I am an absolute beginner with Ubuntu Linux Dual booting with WinXP. I wish to download a free anti-virus program and will need assistance installing. Please use plain English, I am not yet familiar with the Linux files, folders, and terminology............Regards.............Bigpom:KS

---

### Post by Dr Small on 2008-07-04
Why do you need an anti-virus? You are running linux.

---

### Post by natman on 2008-07-04
My understanding is that ani virus is not that big a deal in linux, 80% of the market is MS pc's so most virus's are written to infect the most amount of things ie MS ps.
saying that i have heard of linux virus, but i have no anti virus that i know of running ( perhaps its bundled in there ) and ive been online and safe for 2+ years
MS =microsoft

---

### Post by sam_delta on 2008-07-04
as sayd by Dr small, linux is way safer than windows, so you do not need an antivirus in linux.

sam

---

### Post by jamesrfla on 2008-07-04
I heard that thier was curently no know viruses for linux. I don't even think you can get a anti-virus for linux.

---

### Post by Captain panda on 2008-07-04
I don't know how likely it is to get a virus on Linux, but [Wikipedia says]("http://en.wikipedia.org/wiki/Linux_malware") that there are 863 viruses for Linux. I suppose that's nothing compared to the tens of thousands or so of viruses for Windows, but I think saying that Linux is invunerable is a bit risky. 

On the other hand, I don't know of any Linux anti-virus tools myself. *shrugs*

---

### Post by ethoxyethaan on 2008-07-04
> **jamesrfla said:**
> I heard that thier was curently no know viruses for linux. I don't even think you can get a anti-virus for linux.

its because you can't just press a button to execute something. a virus (something that spreads and duplicates) is harder to find in linux because you will need to grant the virus root privileges. a uninformed user might do this but will leave his pc infected alone because the chance of spreading it to other linux users is very small because of the small community.

---

### Post by bhadotia on 2008-07-04
But If you do want an anti virus , you can install clamav from the repositries.
You said you are new so I will put it as plainly as I can:
First of all open the synaptic package manager. It can be found in System>Administration>Synaptic Package Manager.
Now in the window that opens click settings>repositries in the menu bar . Tick everything (check all the boxes) in all the tabs and close it. 
Now click reload in the toolbar.
After the reload is complete search for clamav and clamtk and check the box next to it - the package manager might ask you to mark additional changes to resolve the dependencies - do it
Finally click apply in the tool bar.This will install the anti virus backend clamav and frontend clamtk.

Now we will configure the AV . Open a terminal (Application>Accessories>Terminal) and type the following command (just copy and paste):
```
sudo dpkg-reconfigure clamav-base
```Give your root password if required (as you type it it will not  be shown on the screen).Follow the prompts and configure your anti-virus as you like it. If you don't understand something go with the default option.

Now we will configure the automatic AV updater freshclam (it is installed by default as a dependency with clamav - if not , install it as we installed clamav above):
In the terminal do:
```
sudo dpkg-reconfigure clamav-freshclam
```As above configure it.
Now you can launch the front end to clamav from Applications>System Tools>Virus Scanner.
The front end launched from the menu cannot update your database. If you want to manaually update your virus signatures do this:
Press alt+f2 and in the dialog box type : gksudo clamtk
Now in the virus scanner click help in the menu bar and then update signatures . It will then  check for updates and update the database if required.
Good Luck.

---

### Post by hayden92 on 2008-07-04
If you really want to get anti-virus software there area several programs.

Keep in mind though what everyone else has said. Most anti-virus programs scan primarily for Windows viruses so they will be of little use to you.

Never-the-less:

Click on 'Applications'
Open 'Add/Remove'
You should see a search bar near the top. In it, type 'clam' and wait

Tick the box that is to the left of the only program that appears
Click on the green button 'Apply Changes'

You will find the clam program in the menu.

I haven't used it personally, but it should be easy to use.
Hope that puts your mind to rest.

Hayden

---

### Post by vikramaditya on 2008-07-04
Even in xp, I've never had a single invader.  I just keep my hosts file high & tight and never *ever* open attachments in email without verifying the source.  I've also begun using Sandboxie to run IE sessions.

---

### Post by Dr Small on 2008-07-04
Basically, an Anti-virus is only needed if say you are running a mailserver or public FTP server and you wanted to do a good favor and protect your windows friends.

All anti-virus software scan for virus / trojan signatures, and windows viruses can't run on Linux anyhow (except in wine). So running a anti-virus software on Linux does not protect you from any "Social-Engineering" attacks.

---

### Post by aysiu on 2008-07-04
Instead of wasting your time with antivirus, use strong passwords, don't install any kind of server software unless you know what you're doing, use NoScript, and don't install software from outside the Ubuntu repositories.

In other words, concern yourself with real security, not placebo security.

---

### Post by Dr Small on 2008-07-04
> **aysiu said:**
> In other words, concern yourself with real security, not placebo security.

You mean, [Security Theater]("http://en.wikipedia.org/wiki/Security_theater")

---

### Post by aysiu on 2008-07-04
> **Dr Small said:**
> You mean, [Security Theater]("http://en.wikipedia.org/wiki/Security_theater")
Totally the term I was looking for. I hadn't known of that phrase before. Thanks for the link.

**Edit**: On second thought, *placebo* may more appropriately describe this situation, since *security theater* appears to actually have some positive inadvertant or temporary security benefits and sometimes can be effective against attackers or criminals who are fooled by it. Any digital threat will not be fooled by antivirus.

I'm still grateful for the link, though. It was a great read, and now I have a new term at my disposal.

---

### Post by gameryoshi600 on 2008-07-04
You don't need an antivirus for linux. all you need is a good firewall. Read [this]("https://help.ubuntu.com/8.04/keeping-safe/C/firewall.html") guide on setting up a firewall.

---

### Post by stalkier on 2008-07-04
> **jamesrfla said:**
> I heard that thier was curently no know viruses for linux. I don't even think you can get a anti-virus for linux.

Wrong on both counts. There are a few viruses out for Linux/UNIX systems and even a couple for MacOSX. 

Also there are several different AV software apps for Linux. Avast offer a free "Home" version for linux. 

Not throwing this in your face or trying to prove you wrong bud. Just giving good info for you. It never hurts to have to protection just in case.

---

### Post by napzilla on 2008-07-04
Here, this xkcd comic puts it best:

[IMG]http://imgs.xkcd.com/comics/linux_user_at_best_buy.png[/IMG]

[http://forums.xkcd.com/viewtopic.php?f=20&t=23856&start=0&st=0&sk=t&sd=a#p721240](http://forums.xkcd.com/viewtopic.php?f=20&t=23856&start=0&st=0&sk=t&sd=a#p721240)

---

### Post by smartboyathome on 2008-07-05
> **stalkier said:**
> Wrong on both counts. There are a few viruses out for Linux/UNIX systems and even a couple for MacOSX. 

Also there are several different AV software apps for Linux. Avast offer a free "Home" version for linux. 

Not throwing this in your face or trying to prove you wrong bud. Just giving good info for you. It never hurts to have to protection just in case.

[These are all the viruses for Linux]("http://en.wikipedia.org/wiki/Linux_Viruses"). It seems that there aren't that many, and even less in the wild. I would say catching a virus has a chance of next to nothing, so at this stage anti-virus won't matter.

---

### Post by aysiu on 2008-07-05
> **smartboyathome said:**
> [These are all the viruses for Linux]("http://en.wikipedia.org/wiki/Linux_Viruses"). It seems that there aren't that many, and even less in the wild. I would say catching a virus has a chance of next to nothing, so at this stage anti-virus won't matter.
The few viruses in that list that have links appear to be outdated (i.e., aren't real threats).

Bliss, for example: [quote=Wikipedia entry]Although it was probably intended to prove that Linux can be infected, it does not propagate very effectively because of the structure of Linux's user privilege system.[/quote] or OSF.8759 > The virus attempts to infect all the files in the current directory recursively and if run from a root account, will try to infect all files in the /bin directory. In any case, no more than 201 files are infected in one run. Moreover the virus avoids infecting the files under /dev, /proc and all the files with a suffix ps such as in maps. The backdoor attempts to listen on UDP port 3049 and provides many internal commands to execute files on the target system. Upon execution, the virus tries to modify the firewall rules so that they do not interfere with the backdoor's operation. It also attempts to evade debugging by spawning a debugger itself. If the virus fails to spawn its own debugger, it assumes that the system already has a running debugger and will terminate its execution immediately. Staog > Staog was the first computer virus written for the Linux operating system. It was discovered in the fall of 1996, and the vulnerabilities that it exploited were shored up soon after. It has not been detected in the wild since its initial outbreak.

---


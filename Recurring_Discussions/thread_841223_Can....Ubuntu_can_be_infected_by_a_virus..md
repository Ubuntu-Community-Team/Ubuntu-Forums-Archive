---
title: "Can....Ubuntu can be infected by a virus."
date: 2008-06-26
forum: Recurring Discussions
---

### Post by vinod_jaiswal18 on 2008-06-26
Hello Guys,

pl. help me regarding..virus issue..
i am an absolute beginner in linux.
i hav started linux from a week or 2. 

i have Dual boot in my machine.

1.Vista
2.Ubuntu

My question is...
Is it is important to install an anti virus in Ubuntu?

If not, then....Do tell me tat Can Windows virus's entering through ubuntu browsing, can Corrupt my windows partition.?

Pl. answer asap.
Regards
ViNoD

---

### Post by pmlxuser on 2008-06-26
if you install an antivirus in ubuntu it catches windows viruses. But it is really not that important to install an antivirus in Ubuntu.
when you say
"Windows virus's entering through ubuntu browsing"
You mean while  
1.using  ubuntu or 
2.you mean if you access the files from the Ubuntu partition while in windows.

if you access files from ubuntu partition while in windows there might be a risk i think of activating  a dormant viral file . thats why it is very important to have an up-to-date antivirus in Windows.

On the other hand a virus will not attack you windows partition through Ubuntu browsing if the case is the first on.

---

### Post by ibutho on 2008-06-26
Hi.

Linux cannot be infected by Windows viruses unless you are running a Windows emulator e.g. something like WINE. Unless you are sharing files between Windows and Linux or running a mail server, then generally you do not need antivirus. If you are sharing files with Windows or Windows users, then its not a bad idea to run antivirus on Linux (not to protect the Linux system, but the Windows system or users). 

You can find out more info about Linux and viruses by reading this [article]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/").

---

### Post by flytripper on 2008-06-26
not likely but anything is possible....
all virus writers should burn in a fire..

---

### Post by Herman on 2008-06-26
If you can avoid using Windows on the internet and for email and use Ubuntu for those things you'll notice an immediate and remarkable reduction in the number of items that all kinds of scans of your Windows system will come up with.

Ubuntu isn't affected by viruses or malware unless you install the malware yourself. 
There is not very much malware available for Ubuntu, but if you choose to install software from outside of the official Ubuntu repositories it's theoretically possible to install a program (or write one yourself) that will do something bad or something other than intended, however, malware can't just install itself with a 'drive-by download' like it can in Windows. 

Viruses can't cross partition boundaries by themselves, but they can hitch a ride on files that you might download in Ubuntu and then pass into your Windows partition. You can make a separate FAT32 or NTFS partition for staging such files, (if you need to pass files between systems), and scan then with your antivirus before you move them the rest of the way into Windows.

You can get a few anitvirus programs that will run in Ubuntu, and they're very good, but they're not for protecting Ubuntu, they're for scanning Windows or files that you might want to transfer into Windows.

Regards, Herman :)

---

### Post by hyper_ch on 2008-06-26
basically

(1) ubuntu is save from viruses

(2) you can download a virus in a word document or so - and it has no effect on ubuntu... however if you open that file with windows, you might get infected...

So, if you have an antivirus on windows, you don't really need one on ubuntu.

---

### Post by |{urse on 2008-06-26
virus writers are pretarded. We learned all the basics needed to write viruses in my 1st quarter Introduction to programming class (covered a little C) sad. But there are a few "viruses" (more like petty annoyances) out there for linux. The chances of you ever seeing them is incredibly rare. Both avast and AVG linux scan for those. So the question really is, How paranoid are you?

---

### Post by Chayak on 2008-06-26
The more accurate statement is that you are fairly safe browsing in linux.  The only way for you to infect your windows install would be to execute something you downloaded in linux in windows.

Is linux more secure? Yes

Is linux perfectly secure? No, not every person who finds a vulrability reports it or fixes it.  They might just put it to use themselves and not tell.

Is any file I scan for malware safe to run in windows? No, there are quite a few malware samples I've seen that don't show up on any AV scans.  There are also ways to hide known malware from AV by custom compiling or using custom PE packing.

---

### Post by vinod_jaiswal18 on 2008-06-26
Thanks to everyone...!!

So i think.........i should install an antivirus.....for My ubuntu...!!

But question comes how and From where...!!

i am really Confused...i tried to install avast for Ubuntu.....It got Installed too....It was an .deb pakeage installation...!!

But when i was searching for the execution file for the Avast scanning..i didn't got any thing...!!

help me guys...!

---

### Post by hyper_ch on 2008-06-27
I still think you don't need AV on linux ;)

---

### Post by Herman on 2008-06-27
I agree with hyper_ch and the other posters, you don't need any anitvirus for Ubuntu.

However, you can install it and it's very good for finding Windows viruses in broken down Windows systems.
I have used the excellent how-tos here:

[HOWTO: Install AVG free anti-virus]("http://ubuntuforums.org/showthread.php?t=136064&highlight=avg") by Artificial Intelligence

[[64-bit] Install AVG free and pro anti-virus for Ubuntu 64-bit]("http://ubuntuforums.org/showthread.php?t=622967&highlight=avg") by Artificial Intelligence

I have used AVG in Ubuntu to find and identify viruses in Windows and I have also used Ubuntu to capture and hold virus files in quaratine for examination. They're harmless in Ubuntu, but they will wreck Windows.

The best thing to do is give up Windows and completely switch to Ubuntu, but if you have friends who still use Windows, you can still use AVG in Ubuntu to help them.
It doesn't kill the viruses, but it does find them and idenitfy them, then you have to decide what to do next.

The majority of people I know who have had viruses in Windows are very willing to switch to Ubuntu as soon as they can.

Regards, Herman :)

---

### Post by vinod_jaiswal18 on 2008-06-29
hyper_ch & Herman.....
thanks...for the reply.....!!

Herman.....but... i can't totally switch to Linux....because....i am an MCSE(Microsoft Certified Network Engg.) & an Information Technology Student...and most of the softwares on which i work r based on windows platform........!!

> 
But........if i neglect all these things.......i am fed up of using windows vista or XP......!!

Today morning Only......my vista just got crashed and..............at this time...ubuntu was their to help me ..!!!


ubuntu rocks....!!!

thanks..man...!!

---

### Post by Frak on 2008-06-29
Q. Are there Viruses for Linux
**A. Yes**

Q. Should I be worried about them
**A. Of course**

Q. Should I be worried about them infecting my system
**A. No, all of the known virii in the wild were jailed down some years ago**

Q. Should I use an Anti-Virus
**A. Should I buy Volcano insurance if I live in Oklahoma?**

---

### Post by 3rdalbum on 2008-06-29
Q. Are there viruses for Linux?
A. Not unless you live inside the lab of an anti-virus manufacturer

Q. Should I be worried about threats against Linux?
A. Yes, but not paranoidly so; just take passive security precautions (be careful of what you install, run a firewall, etc) rather than outsourcing your security to an extra piece of software.

Windows viruses don't run on Linux. Linux is a securely-designed operating system which works properly. **You do not need an anti-virus program for Linux.**

---

### Post by hyper_ch on 2008-06-29
how would a firewall protect against virus infections?

---

### Post by LaRoza on 2008-06-29
> **hyper_ch said:**
> how would a firewall protect against virus infections?

It give you the peace of mind that whatever happens, you did yourself :-)

---

### Post by wirewalker on 2008-08-17
> **vinod_jaiswal18 said:**
> Thanks to everyone...!!

So i think.........i should install an antivirus.....for My ubuntu...!!

But question comes how and From where...!!

i am really Confused...i tried to install avast for Ubuntu.....It got Installed too....It was an .deb pakeage installation...!!

But when i was searching for the execution file for the Avast scanning..i didn't got any thing...!!

help me guys...!These commands will install avast!'s icons&links into the Applications > Accessories > avast! Antivirus menu.
paste this in a terminal:

cd /usr/lib/avast4workstation/share/avast/desktop && sudo ./install-desktop-entries.sh install

---

### Post by grikdog on 2008-08-17
Criminentlies, the hubris!  Rephrasing, can Ubuntu be affected by a *linux virus*, and if not, why not?

My wife just got a panicky trojan horse denial-of-service attack that demanded she CLICK HERE IMMEDIATELY to "check your Windows XP operating system" for viruses.  Ok, we laughed about that -- this is Ubuntu, after all.

But aside from the thickest pile of hubris I've ever seen sloshing about at the bottom of a forum, I haven't yet detected much informed commentary from anyone in a position to know that viruses on Ubuntu are not only unthinkable, but haven't actually been thought of yet, and why not, I may ask?  Because Linus Torvalds is from the Planet Ethereal Desmesne and Canonical is His Messenger?

Get real.  At least discuss the topic like ... ah ... adults.

---

### Post by Giant Speck on 2008-08-17
Viruses [SIZE="1"][COLOR="Gray"](not virii, because that isn't a word)[/COLOR][/SIZE] aren't what you need to worry about on Linux.
Hell, you don't even need to worry about viruses on Windows as long as you practice safe internet browsing and e-mail opening practices.

What you do have to worry about is what people tell you to type into the terminal.  Using the command line can be very dangerous and very damaging to your computer if you don't know what you are doing.

---

### Post by doas777 on 2008-08-17
the way I understand it you are protected against most malware types (viruses and worms) because of the internal boundaries within the process model. Rootkits (and trojans as others have mentioned )are still a theorectical problem though, so i install and use chkrootkit every once in a while. I don;t know if it's as good as RKR for windows, but it gives me a little peice of mind.

to install:
```
sudo apt-get install chkrootkit
```

to run:
```
sudo chkrootkit
```


I also tend to recoment the the harden-environment package, and bastille.
you should look these up when you have the time.


```
sudo apt-get install harden-environment bastille
```

have fun and good luck,
Franklin

---

### Post by Twitch6000 on 2008-08-17
Here is a well thought out paragraph of a fellow forum member on this topic.

It should clear things up for you :).

> **lukjad007 said:**
> First of all, read this:
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

These are the two main questions you seem to have:

Are there and Anti-Viruses for Linux?
Are there any viruses for Linux?

For the first one, Yes.

For the second one, yes... and no.

As my esteemed colleague, Twitch6000, said, there are SOME viruses to be found. ***However***, they are hard to get. The difference between Linux Viruses and Windows Viruses is that Windows is always running as the root user. So, anything that happens to part of the computer, happens to all of the computer. Also, with Ubuntu most of the programs you  will ever install come from authentic repositories that are checked, double checked, and triple checked to be uninfected. If you choose in install programs from repositories other than those supported by Ubuntu, you do so at your own risk. You need to check the references of the repository you are using. If some guy you see at a cracker site tells you to activate the 1337h4xr repository, be suspicious.

The same is true about installing programs. If you install GIMP 2.50 from the GIMP's Official Website ([www.gimp.org](www.gimp.org)), you are giving them a measure of trust since they are a proven entity. However, if you go to [www.SuperCoolThingy.com](www.SuperCoolThingy.com) (I invented the site name) and start installing a bunch of programs, you may have a problem. The point of using Linux is not to be blissfully ignorant, but to be informed and cautious but not constantly in danger. Unlike in Windows, you cannot just accidentally click on a link and get infected. 

Now, if you are worried about loosing data, you need to be wary of any commands given to you. This ***_[COLOR="Red"]DANGEROUS COMMAND[/COLOR]_*** below will destroy your computer if run as root:
```
rm -rf /
```
The point is that you have to be careful, but you have a better foundation upon which to defend yourself. If ever you are suspicious of a program, don't install it until you check it out. If someone you don't trust tells you a command that you don't understand, ask someone what it does. Google is your friend. Look up what chmod is. Look up what rm -rf / does. If you don't like what you see, wait. Read [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73) for more on dangerous commands. 

Basically, it is possible to get a virus, if you are not careful. It is also easy to destroy the usability of your computer if you do a dangerous command. 

Below is a Youtube Video I found about what happens when you run rm -rf / as root. The point is that since Windows is always root, any program can destroy the system. In Linux, especially Ubuntu, the damage is limited.

[http://www.youtube.com/watch?v=wWOjmvWPRvQ](http://www.youtube.com/watch?v=wWOjmvWPRvQ)


Again I have to ask the mods to make this a sticky or something >.>.As lukjad007 made the point very clear :).

So all in all it is mainly this,
Can you get a virus on Linux?
Yes
How likely is it,how likely is it for me to win the lotto?

---

### Post by doas777 on 2008-08-17
I wish the forum quote mechanism could show the infinite recursion within your post Twitch. ;)

cheers

---

### Post by SunnyRabbiera on 2008-08-17
The way that linux and ubuntu is set up makes a virus near impossible to infect it.
Not like it cant be done, no OS is 100% safe but linux does make it harder as does unix.

---

### Post by Twitch6000 on 2008-08-17
> **doas777 said:**
> I wish the forum quote mechanism could show the infinite recursion within your post Twitch. ;)

cheers

Well if its the only way to make a point clear I guess I have to do it :).

---

### Post by MelissaEpiphany on 2008-08-19
Linux magazine have recently released an issue on security, June '08. The chances of infection are remote but more probable than they have been in the past, (cyber-criminals are becoming more sneaky.) Like others have said, Malware is the only real threat, (I've had someone try this on me while using an unnamed download program,) but if you don't give permission then they can't get in, so don't give your password out to anything that pops up unless you know exactly what it's for and you initiated it. 

I have CHKRootkit installed, it's easy to use to scan your system for root kit viruses: [http://www.chkrootkit.org/](http://www.chkrootkit.org/)

If you did ever get a rootkit though, you would really need to reinstall your entire infected system.


OSSEC is also worth looking at. It automatically performs rootkit checks, monitors logfiles and does intrusion detection. [http://www.ossec.net/](http://www.ossec.net/)

I know there are more things you can do to keep your PC safe like single-packet port knocking? But I'm still only a baby in Linux. 

Hope this helps somewhat.

Mel

---

### Post by hyper_ch on 2008-08-19
chkrootkit and rkhunter are both in the repos.

---

### Post by billgoldberg on 2008-08-20
> **vinod_jaiswal18 said:**
> Thanks to everyone...!!

So i think.........i should install an antivirus.....for My ubuntu...!!

But question comes how and From where...!!

i am really Confused...i tried to install avast for Ubuntu.....It got Installed too....It was an .deb pakeage installation...!!

But when i was searching for the execution file for the Avast scanning..i didn't got any thing...!!

help me guys...!

No you don't.

You have to install an AV on windows.

Why would you cripple your Ubuntu system when you scan your files anyway on windows with a AV?

---

### Post by cardinals_fan on 2008-08-20
> **billgoldberg said:**
> No you don't.

You have to install an AV on windows.

Why would you cripple your Ubuntu system when you scan your files anyway on windows with a AV?
No, you don't.

You don't have to install an AV on Windows.

Why would you cripple ANY [non-server] system with an AV?

---

### Post by aysiu on 2008-08-20
> **cardinals_fan said:**
> No, you don't.

You don't have to install an AV on Windows.

Why would you cripple ANY [non-server] system with an AV?
Amen.

Just have XP users install and use SuRun and be done with it.

---

### Post by fiddledd on 2008-08-21
> **aysiu said:**
> Amen.

Just have XP users install and use SuRun and be done with it.

Off topic, I assume you installed it at school then? I'm still using it, no problems to report yet.:)

---

### Post by aysiu on 2008-08-21
> **fiddledd said:**
> Off topic, I assume you installed it at school then? I'm still using it, no problems to report yet.:)
Not yet. We'll be testing it a bit more before fully rolling it out.

---


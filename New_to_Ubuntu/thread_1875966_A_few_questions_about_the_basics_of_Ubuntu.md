---
title: "A few questions about the basics of Ubuntu"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by deviouschick on 2011-11-05
I recently learned about Ubuntu and decided to give it a try.  I'm using Ubuntu and Windows XP on the same computer...It's a netbook and the ram is maxed out already at 1.5gb, so when Ubuntu seemed a little sluggish, I found a command to type in to download the Xubuntu desktop environment as well.

I'm still trying to figure out the basics.  I was wondering if I need to do some kind of maintenance to it similar to defragmenting Windows or if there were any temporary files I needed to clean out from time to time?
I've heard that I should use ClamAV for virus protection and then I've also heard I don't have to worry about virus protection...I'd rather be safe than sorry. So, do I need anti virus and if so, can I find a decent program on the software center? I don't know much about the command terminal, so I'm looking for something that is simple to install.

Also, sometimes my netbook's touch pad completely stops working for no apparent reason. At first I thought my laptop has frozen, but when I plugged a mouse into my usb port, it worked just fine...Then later my touch pad would start working again...?  Anyone know of a glitch that causes this? I've already went into settings for it and un-checked the box that says to disable it while typing...

And if anyone would like to give me a few pointers, like basic programs or plugins I'll need, that would be great because I've never used Linux before and I'm a little lost trying to figure out how to install things.  I ended up installing Chromium from the Ubuntu Software Center because I couldn't get Chrome to install...

ps - I've heard that there's a netbook edition for Ubuntu also.  Is that something that would be worth looking into?  I like the layout of Ubuntu a lot better than Xubuntu...

---

### Post by Lars Noodén on 2011-11-05
As far as the anti-virus goes you might find it informative to read the [security "stickies"](http://ubuntuforums.org/forumdisplay.php?f=338).  The short answer is that it's not really needed. 

As far as where to get programs from, if you can't get it from the Software Center, then it's probably not ready for public consumption.

As far as which programs to get, what do you want to use your computer for?  The activities you have planned will determine which applications can be recommended.

---

### Post by mike555 on 2011-11-05
adding Xubuntu desktop on top of Ubuntu is not so good as just installing Xubuntu , I use Xubuntu on my netbook as well as my desktop, it needed a few tweaks , but fast and not unity or gnome 3......

---

### Post by bryncoles on 2011-11-05
Hello Deviouschick, and welcome to the Ubuntu family!

If you're running native Linux file systems (ext3 or 3xt4 instead of NTFS or FAT32) then you [don't need to defrag your computer](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting).  That's one of the nice things!

As I understand antivirus stuff, that's usually recommended tso you don't pass on virsuses to Windows users.  Try clam-gtk though (I think that's what clam anti-virus non-command line version is called).

---

### Post by deviouschick on 2011-11-05
> **Lars Noodén said:**
> As far as the anti-virus goes you might find it informative to read the [security "stickies"](http://ubuntuforums.org/forumdisplay.php?f=338).  The short answer is that it's not really needed.
 
I've looked into a couple threads in Security Discussions forum, but everyone seems to have differing opinions on security. Some people say you need a firewall and that the Linux firewall is disabled by default...But I'm not even sure how to view firewall settings and if there is a command I need to type into command terminal, then I'm even more lost as to how to go about it.
It's not that I haven't tried to figure out the answer about security myself; it's just that every time I find an answer, the person's explanation is described with all these complex terms that I've never heard of.  I'm looking for a guide with things explained in laymen's terms. 

> As far as where to get programs from, if you can't get it from the Software Center, then it's probably not ready for public consumption.

As far as which programs to get, what do you want to use your computer for?  The activities you have planned will determine which applications can be recommended.

I'm okay with using Chromium as long as it's just as secure as Chrome. That was my main concern.
I'll mainly be using it for Facebook and other social networking sites. But I'll also use it to buy things off Amazon, eBay, etc and to check on my bank account, so that's why I'm concerned about the security.
Also, I've used Acer eRecovery on Windows on my computer because it had a virus of some sort that was using my email to spam everyone in my address book (It could see what I was typing because every time I changed my password, it could log right back into my email.), and I'm about 80% sure it's gone, but I'm still a little concerned that if it's still there, it could infect Ubuntu or still see the passwords and credit card numbers I type in while using it...

---

### Post by deviouschick on 2011-11-05
> **mike555 said:**
> adding Xubuntu desktop on top of Ubuntu is not so good as just installing Xubuntu , I use Xubuntu on my netbook as well as my desktop, it needed a few tweaks , but fast and not unity or gnome 3......

It seems to be running regular Ubuntu decently now that I've finished updating it. I am planning on installing Xubuntu or even Lubuntu onto a really old desktop I have though, so thanks for the tip. :)

---

### Post by mike555 on 2011-11-05
Chromium is probably more secure then chrome , because chromium is open source and doesn't spy on your browsing habits......

---

### Post by Lars Noodén on 2011-11-05
> **deviouschick said:**
> I've looked into a couple threads in Security Discussions forum, but everyone seems to have differing opinions on security. 

Yes.  That's the case.  If you really want a firewall, it's good to know that it is called iptables and you can work with it directly via the shell.  If you want a graphical interface then you can look at [Gufw](https://help.ubuntu.com/community/Gufw).

---

### Post by deviouschick on 2011-11-05
> **bryncoles said:**
> Hello Deviouschick, and welcome to the Ubuntu family!

If you're running native Linux file systems (ext3 or 3xt4 instead of NTFS or FAT32) then you [don't need to defrag your computer](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting).  That's one of the nice things!

As I understand antivirus stuff, that's usually recommended tso you don't pass on virsuses to Windows users.  Try clam-gtk though (I think that's what clam anti-virus non-command line version is called).
How do I know what file system I'm running? lol  I just downloaded Ubuntu from the site and then I used the command "sudo apt-get install xubuntu-desktop" to get the option for Xubuntu. 
It would be awesome if I didn't have to do any kind of maintenance though.  That seemed to be something I often neglected to do on Windows, ha.
I'll look into Clam-GTK.

---

### Post by lykwydchykyn on 2011-11-05
> **deviouschick said:**
> I've looked into a couple threads in Security Discussions forum, but everyone seems to have differing opinions on security. Some people say you need a firewall and that the Linux firewall is disabled by default...But I'm not even sure how to view firewall settings and if there is a command I need to type into command terminal, then I'm even more lost as to how to go about it.
It's not that I haven't tried to figure out the answer about security myself; it's just that every time I find an answer, the person's explanation is described with all these complex terms that I've never heard of.  I'm looking for a guide with things explained in laymen's terms. 


You can install the package "gufw" (I think it's called "Firewall configuration" in software center).  It's a graphical interface for the firewall.

I don't know of a simple guide, but here's a good analogy:

- Think of an office building with phones in every office.  There's a main line to call, then you dial an extension to reach a person.

- If you don't plug a phone into an extension, it can't be called because nobody's listening at it.

- On your computer, the "main line" is your computer's IP address.  The "extensions" are called ports, and they're numbered from 1 to 65,535.

- A firewall basically blocks access by port number.  But ports only need to be blocked if you have something "plugged in" to them -- i.e., a service running that's listening on that port.  By default, Ubuntu has no services listening (no phones plugged in).

- Thus, a firewall is only needed if you install services that listen on the network, and you want them to not be accessible to the outside.

- If you connect behind a router, nobody outside your own network can call the "main line" to begin with, so a firewall on your computer is redundant.

Hope that makes sense.

> 
I'm okay with using Chromium as long as it's just as secure as Chrome. That was my main concern.
I'll mainly be using it for Facebook and other social networking sites. But I'll also use it to buy things off Amazon, eBay, etc and to check on my bank account, so that's why I'm concerned about the security.
Also, I've used Acer eRecovery on Windows on my computer because it had a virus of some sort that was using my email to spam everyone in my address book (It could see what I was typing because every time I changed my password, it could log right back into my email.), and I'm about 80% sure it's gone, but I'm still a little concerned that if it's still there, it could infect Ubuntu or still see the passwords and credit card numbers I type in while using it...

Chromium is just Chrome without google's branding (name & icons) and a handful of proprietary extensions (like built-in pdf viewing).  It's as secure as any other browser out there, perhaps more secure than some.

Viruses are just programs.  Like any other program, they do nothing until they're run in a compatible environment.  The virus is no more able to "infect" your Ubuntu partition than Word or IE are likely to jump over to your Linux partition and start running of their own accord.

---

### Post by deviouschick on 2011-11-05
> **Lars Noodén said:**
> Yes.  That's the case.  If you really want a firewall, it's good to know that it is called iptables and you can work with it directly via the shell.  If you want a graphical interface then you can look at [Gufw](https://help.ubuntu.com/community/Gufw).

I've run across the term "iptables", but I have no idea what program to use to view them or what they are. I'm afraid if I go exploring stuff I'm going to get into the wrong file and mess something up. Basically, what you just said to me made no sense at all. lol That's what I meant by people's answers using words I didn't understand. XD
I'm only going to be using Chromium and maybe a word processor and a couple games, nothing that I would think that would need any kind of special permissions, unless you count anti virus...Should I even bother trying to figure out how to use a firewall?

---

### Post by lykwydchykyn on 2011-11-05
> **deviouschick said:**
> How do I know what file system I'm running? lol  I just downloaded Ubuntu from the site and then I used the command "sudo apt-get install xubuntu-desktop" to get the option for Xubuntu. 
It would be awesome if I didn't have to do any kind of maintenance though.  That seemed to be something I often neglected to do on Windows, ha.
I'll look into Clam-GTK.

Ext4 is the default; if you didn't change it, then that's what you have.  You can verify that by running the "mount" command, which will list all your mounted filesystems and what type they are.

IMO don't mess with clamav.  It mostly gives false positives, and will have you removing perfectly harmless and possible necessary files.

If you're worried about malware, install rkhunter and chkrootkit; these are utilities to find rootkits, something that people actually get sometimes on Linux systems (as opposed to viruses).

---

### Post by deviouschick on 2011-11-05
> **lykwydchykyn said:**
> You can install the package "gufw" (I think it's called "Firewall configuration" in software center).  It's a graphical interface for the firewall.

I don't know of a simple guide, but here's a good analogy:

- Think of an office building with phones in every office.  There's a main line to call, then you dial an extension to reach a person.

- If you don't plug a phone into an extension, it can't be called because nobody's listening at it.

- On your computer, the "main line" is your computer's IP address.  The "extensions" are called ports, and they're numbered from 1 to 65,535.

- A firewall basically blocks access by port number.  But ports only need to be blocked if you have something "plugged in" to them -- i.e., a service running that's listening on that port.  By default, Ubuntu has no services listening (no phones plugged in).

- Thus, a firewall is only needed if you install services that listen on the network, and you want them to not be accessible to the outside.

- If you connect behind a router, nobody outside your own network can call the "main line" to begin with, so a firewall on your computer is redundant.

Hope that makes sense.



Chromium is just Chrome without google's branding (name & icons) and a handful of proprietary extensions (like built-in pdf viewing).  It's as secure as any other browser out there, perhaps more secure than some.

Thanks. That makes more sense, and that seems to be breaking down the message that I've gotten from most other people's answers. However, there was one user who seemed to be arguing that everyone needs a firewall...I couldn't really understand all of his reasoning on it since I'm not very familiar with how Linux works...Maybe you can make sense of what he's trying to say. [http://ubuntuforums.org/showthread.php?t=1863680&highlight=anti+virus&page=2](http://ubuntuforums.org/showthread.php?t=1863680&highlight=anti+virus&page=2)  
I believe it's reply #15.

---

### Post by deviouschick on 2011-11-05
> **lykwydchykyn said:**
> Ext4 is the default; if you didn't change it, then that's what you have.  You can verify that by running the "mount" command, which will list all your mounted filesystems and what type they are.

IMO don't mess with clamav.  It mostly gives false positives, and will have you removing perfectly harmless and possible necessary files.

If you're worried about malware, install rkhunter and chkrootkit; these are utilities to find rootkits, something that people actually get sometimes on Linux systems (as opposed to viruses).

I was considering ClamAV just to protect other Windows users that I send files to occasionally through email, pictures and other documents... What are rootkits and how would I go about installing rkhunter and chkrootkit? Are they pretty simple to use and understand?

---

### Post by lykwydchykyn on 2011-11-05
> **deviouschick said:**
> I've run across the term "iptables", but I have no idea what program to use to view them or what they are. I'm afraid if I go exploring stuff I'm going to get into the wrong file and mess something up. Basically, what you just said to me made no sense at all. lol That's what I meant by people's answers using words I didn't understand. XD
I'm only going to be using Chromium and maybe a word processor and a couple games, nothing that I would think that would need any kind of special permissions, unless you count anti virus...Should I even bother trying to figure out how to use a firewall?

iptables is a command for low-level firewall manipulation.  It's quite possibly the least user-friendly method of configuring the firewall in existence.  You don't need it.

IMO, you really don't need to put much time into security configuration at this point.  Your chances of picking up malware or getting hacked on a default install of Ubuntu are on par with your chances of getting hit by falling satellite debris.  Invest your time in learning how to use the system.

---

### Post by lykwydchykyn on 2011-11-05
> **deviouschick said:**
> I was considering ClamAV just to protect other Windows users that I send files to occasionally through email, pictures and other documents... What are rootkits and how would I go about installing rkhunter and chkrootkit? Are they pretty simple to use and understand?

A rootkit is basically a set of modified system files that can be used to compromise your system.  Typical attack against a linux system would be to bombard some network service like SSH or Apache to find a hole (like a weak password on a well-known account name, or some unpatched security flaw) that would allow remote access.  Then the attacker would drop in a rootkit to (for example) replace the ssh server with a version that has a backdoor in it.

You can install clamav, but be aware that it's highly prone to false positives.  

both rkhunter and chkrootkit are console commands; like most things, they can be installed through software center or with apt-get.  Honestly, though, you probably don't need to worry about them either.  Unless you're running network services on a publicly-accessible IP address (i.e., not behind a router), you're not likely to end up with a rootkit.

---

### Post by deviouschick on 2011-11-05
> **lykwydchykyn said:**
> A rootkit is basically a set of modified system files that can be used to compromise your system.  Typical attack against a linux system would be to bombard some network service like SSH or Apache to find a hole (like a weak password on a well-known account name, or some unpatched security flaw) that would allow remote access.  Then the attacker would drop in a rootkit to (for example) replace the ssh server with a version that has a backdoor in it.

You can install clamav, but be aware that it's highly prone to false positives.  

both rkhunter and chkrootkit are console commands; like most things, they can be installed through software center or with apt-get.  Honestly, though, you probably don't need to worry about them either.  Unless you're running network services on a publicly-accessible IP address (i.e., not behind a router), you're not likely to end up with a rootkit.

So, what if I were to use public wifi? Would that put my system at risk?

---

### Post by dFlyer on 2011-11-05
My advice is to slow down and take it easy by going slow and working on one problem at a time. Remember Linux is not windows. As far as security goes, linux/Ubuntu is very secure. I've been using linux since the mid 90's and have never had a virus. I don't use a virus scanner, my wife also using linux does use one and she has never had a virus. RootKits are out there but I can say I nor my wife has ever had one. If your running a low resource computer why waste your resources with them. As far as determine what process are running open a terminal and enter:

ps -aux

this will list there names and current status. you can also run this from a terminal:

top

this will do the same as above but give you a continuing update of there status and list the amount of memory being used. Again just go slow and have fun.

---

### Post by lykwydchykyn on 2011-11-06
> **deviouschick said:**
> So, what if I were to use public wifi? Would that put my system at risk?

Technically yes.  Realistically, no.  I can't imagine many people connect to a public wifi and start looking for Linux systems to attack.

In any case, a firewall doesn't do much for you if you aren't listening on any ports to begin with.

---

### Post by Dangertux on 2011-11-06
Couple of things in this thread I've seen thus far. One you mentioned you read the stickies in the Security section of the forum. I highly suggest sticking to those, that information is for the most part accurate and not opinion based. Whereas some of the information in this thread is based on opinion or general use cases.

This is the part where someone sends me a private message telling me I'm spreading FUD (Fear Uncertainty and Doubt. Truthfully I'm being realistic.

From my point of view, choosing not to use a firewall is a very poor choice. Again check the stickies it's explained there. 

As far as using public access wifi goes, one person gave a very limited perspective on that. While attacking a linux based system on public wifi may not necessarily be within the interest of the average 16 year old "hacker kid". Stealing you social networking credentials, email credentials , and personal banking information with a silly browser addon like Firesheep or Wireshark if he's feeling particularly clever, is definitely within the scope of said hacker kid. Force SSL (HTTPS) everywhere on public access wifi. Or better yet don't use it.

Also... If you spend any amount of time on the internet , use a browser addon like NoScript, it will save you a lot of trouble. 

Anti-malware solutions on Linux (at least the free ones) are a joke, so it doesn't matter if you need one or not. They are ineffective to say the least.

I realize I am the dissenting opinion, and frankly feel free to light my inbox up with hate mail. I am however being realistic. Stick to the stickies, they are stuck for a reason.

Hope this helps.

P.S: Nothing is inherently secure.

---

### Post by lykwydchykyn on 2011-11-06
> **Dangertux said:**
> Couple of things in this thread I've seen thus far. One you mentioned you read the stickies in the Security section of the forum. I highly suggest sticking to those, that information is for the most part accurate and not opinion based. Whereas some of the information in this thread is based on opinion or general use cases.

This is the part where someone sends me a private message telling me I'm spreading FUD (Fear Uncertainty and Doubt. Truthfully I'm being realistic.

From my point of view, choosing not to use a firewall is a very poor choice. Again check the stickies it's explained there. 

As far as using public access wifi goes, one person gave a very limited perspective on that. While attacking a linux based system on public wifi may not necessarily be within the interest of the average 16 year old "hacker kid". Stealing you social networking credentials, email credentials , and personal banking information with a silly browser addon like Firesheep or Wireshark if he's feeling particularly clever, is definitely within the scope of said hacker kid. Force SSL (HTTPS) everywhere on public access wifi. Or better yet don't use it.

Also... If you spend any amount of time on the internet , use a browser addon like NoScript, it will save you a lot of trouble. 

Anti-malware solutions on Linux (at least the free ones) are a joke, so it doesn't matter if you need one or not. They are ineffective to say the least.

I realize I am the dissenting opinion, and frankly feel free to light my inbox up with hate mail. I am however being realistic. Stick to the stickies, they are stuck for a reason.

Hope this helps.

P.S: Nothing is inherently secure.

You have some good advice; the question about public wifi had to do with firewalls, which are of no use in securing against something like firesheep.

Which brings up the major misunderstand I think most people get about Linux and security:

There are things we have to secure against, but antivirus and firewall do not address them.  And people have had it drilled into their minds for years that "securing" a computer means installing antivirus and a firewall.

---


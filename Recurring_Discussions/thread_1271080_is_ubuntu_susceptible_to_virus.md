---
title: "is ubuntu susceptible to virus?"
date: 2009-09-20
forum: Recurring Discussions
---

### Post by fitgene on 2009-09-20
i have been using ubuntu 9.04 for 5 months now. recently i found a folder which i created before. i tried to delete it and got the message directory not empty can't delete. i checke for hidden files in it and found the file .fuse000013700000001d. i removed it by shift del option. when i reopen the folder but that file again appears. its 40 mb size. i tried in terminal with rm command and shred but in vain. finally i have to reboot to vista and deleted the file from there. now its clear. could this be a virus?????? after all is linux virus prone like windows???????

---

### Post by erilidon on 2009-09-20
Linux could have a virus written for it however, as several people will argue, Linux does not have the "market share" that Windows does. They says that this means that virus are less likely to be written.

Also there is the fact that you use the system not as root but as a user and are therefore not the "owner" of the files. This makes it harder for a virus to infect the system.

For someone to say that a virus can not attack Linux is just naive.

However I believe that your file in question was just a temp. Next time try "gksu nautilus" to delete the file.

---

### Post by NoaHall on 2009-09-20
Linux does not have mainstream viruses which can currently affect it. Why not? Because the source is open-source, so there are hundreds if not thousands of people can see the source code, and then see the errors which might let a problem happen, and then submit a fix for it.

FUSE is a application. See here -> [http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)

---

### Post by camper365 on 2009-09-20
When you try to remove a folder using rm, you have to use rm -r to remove the folder. The only time rmdir works is when the directory is empty (with the exception of the . and .. directories). If you are in any folder other than your home directory, then you have to use sudo to remove a file (but be careful with this, using sudo you can delete incredibly important files).

---

### Post by sunchiqua on 2009-09-20
The fact that you wasn't able ( or didn't knew, how to do that ) to delete a file, doesn't make it a virus.

---

### Post by mapes12 on 2009-09-20
Hi

I've been using Ubu for sometime now as my main OS and haven't had a single problem with viruses or system security. Online banking and internet purchases are secure and likewise all my LAN connections with my other Ubu boxes have never been hacked.

To do anything system wide on a Ubu box requires Root permission. Ubu by default does not have a root password set. The user has to assume root permission via sudo, hence nobody else can execute malicious code on your system. Quite simple really.

---

### Post by Whiffle on 2009-09-20
.fuse000013700000001d  looks like something created by FUSE ( [http://fuse.sourceforge.net/](http://fuse.sourceforge.net/) ), although I don't know what would be in that directory.

---

### Post by callumacrae on 2009-09-20
If you're feeling paranoid install AVG Free for Linux and do a scan.

[http://free.avg.com/download](http://free.avg.com/download)

I'm not sure what the point in that application is though, as I've never heard of a Linux user getting a virus.

~Callum

---

### Post by sunchiqua on 2009-09-20
> **mapes12 said:**
> Hi

I've been using Ubu for sometime now as my main OS and haven't had a single problem with viruses or system security. Online banking and internet purchases are secure and likewise all my LAN connections with my other Ubu boxes have never been hacked.

To do anything system wide on a Ubu box requires Root permission. Ubu by default does not have a root password set. The user has to assume root permission via sudo, hence nobody else can execute malicious code on your system. Quite simple really.

BTW= not nice to have as a sig :(

Heh, well .. It seems that it catches more attention than a link to a website, where you could win 1k$ :D

---

### Post by NoaHall on 2009-09-20
> **Whiffle said:**
> .fuse000013700000001d  looks like something created by FUSE ( [http://fuse.sourceforge.net/](http://fuse.sourceforge.net/) ), although I don't know what would be in that directory.

I already said that.

---

### Post by t0p on 2009-09-20
> **mapes12 said:**
> 
I've been using Ubu for sometime now as my main OS and haven't had a single problem with viruses or system security. Online banking and internet purchases are secure and likewise all my LAN connections with my other Ubu boxes have never been hacked.


I daresay this is a typical experience for a Linux user.  None of my computers have ever been compromised either.  But I'd just like to add: running Linux does *not* make your computer somehow immune to being attacked.  You need to use good security procedures administrating your machine, including keeping up to date with your security updates.  A well-administrated machine is a pain for any computer criminal to compromise.  But a badly-administrated box can be just as vulnerable as a computer running another well-known OS.

---

### Post by Whiffle on 2009-09-20
> **NoaHall said:**
> I already said that.

Is there some rule against repeating things, especially in the case when I don't think it was clear enough originally?

---

### Post by fitgene on 2009-09-21
thanx for the comments

---

### Post by humphreybc on 2009-09-21
> 
Linux could have a virus written for it however, as several people will argue, Linux does not have the "market share" that Windows does. They says that this means that virus are less likely to be written.

This is not a valid argument. Linux has a huge market share in servers, and servers are much more of a target than desktops as they can affect a lot more people and disrupt things a lot more. The fact that linux doesn't get many viruses is NOT due to its low market share, it's purely because linux has been designed to very secure.

---

### Post by schauerlich on 2009-09-21
Viruses aren't really as much of a problem nowadays; malware authors have moved on to more interesting things like keyloggers and botnets (along with the usual trojans and spyware). Linux is not immune to trojans, as they largely rely on social engineering. Linux botnets are known in the wild[[1]](http://lwn.net/Articles/222153/)[[2]](http://www.theregister.co.uk/2009/09/12/linux_zombies_push_malware/).

---

### Post by rookcifer on 2009-09-21
> **EDavidBurg said:**
> Viruses aren't really as much of a problem nowadays; malware authors have moved on to more interesting things like keyloggers and botnets (along with the usual trojans and spyware). Linux is not immune to trojans, as they largely rely on social engineering. Linux botnets are known in the wild[[1]](http://lwn.net/Articles/222153/)[[2]](http://www.theregister.co.uk/2009/09/12/linux_zombies_push_malware/).

Those "botnets" you refer to *were not* compromised by viruses or trojans.  Rather, they were specifically targeted and cracked via weak SSH passwords.

---

### Post by schauerlich on 2009-09-21
> **rookcifer said:**
> Those "botnets" you refer to *were not* compromised by viruses or trojans.  Rather, they were specifically targeted and cracked via weak SSH passwords.

They're still botnets, and they're still on linux machines. To the victim of the botnet, there's not really a difference.

---

### Post by gn2 on 2009-09-21
> is ubuntu susceptible to virus?

Absolutely not.

---

### Post by schauerlich on 2009-09-21
> **gn2 said:**
> Absolutely not.

[citation needed]



EVERY computer, running EVERY OS, which is hooked up to the internet, is susceptible to malware. It's simply a fact of life.

---

### Post by gn2 on 2009-09-21
> **EDavidBurg said:**
> [citation needed]

EVERY computer, running EVERY OS, which is hooked up to the internet, is susceptible to malware. It's simply a fact of life.

"Malware" isn't "virus".

As citation, how about the fact that there are no active viruses in the wild for Linux?

Remember we're talking "virus" not "malware".

---

### Post by Perfect Storm on 2009-09-21
There are differences on "malware" in general and virus. A virus can (usually) reproduce by itself and infect other files, some can move to other computers of their own.

I can't hardly see that in Linux without tricking the user to execute the virus, but then we're talking about social engineering.

---

### Post by schauerlich on 2009-09-21
> **gn2 said:**
> As citation, how about the fact that there are no active viruses in the wild for Linux?

Just because there are no widespread, in-the-wild viruses for a given OS does not mean that an operating system is immune to them, or not susceptible to them. The whole point of a virus is that it works in ways that the designers/security team in charge of the targeted OS hadn't thought of yet. If they had, the security hole would more than likely have been patched already.

For example, many people are quick to point out that Apple inflates its claims of security with Mac OS X. Although they don't explicitly state that OS X is immune from viruses (or maybe they do, I haven't seen it though), they certainly imply it when they say that Macs don't have the troubles of "tons of viruses" that "PC's" do. However, there are no widespread, in-the-wild viruses for Mac OS X, and only one trojan that I've heard of, that was limited to a couple porn sites. However, Mac OS X is not immune from viruses. Neither is Linux.

---

### Post by wojox on 2009-09-21
> **gn2 said:**
> "Malware" isn't "virus".

As citation, how about the fact that there are no active viruses in the wild for Linux?

Remember we're talking "virus" not "malware".

Is malware not short for malicious software? So how is a virus not considered malicious software?

---

### Post by erilidon on 2009-09-21
This discussion has broken down to a matter of semantics.

The simple fact is no OS is invincible.

---

### Post by gn2 on 2009-09-21
> **wojox said:**
> Is malware not short for malicious software? **So how is a virus not considered malicious software**?

Viruses are considered malicious software, but there are many types of malicious software.
The varying types do not all do the same thing or do it in the same way.

---

### Post by Perfect Storm on 2009-09-21
> **gn2 said:**
> Viruses are considered malicious software, but there are many types of malicious software.
The varying types do not all do the same thing or do it in the same way.

+1

Malicious software is the general overall term. Then you can break it down in sub categories.

---

### Post by gn2 on 2009-09-21
> **erilidon said:**
> The simple fact is no OS is invincible.


And the biggest reason for this is that fallable humans use them.
The weakest link in the chain is often the one in the chair.

---

### Post by erilidon on 2009-09-21
> **gn2 said:**
> And the biggest reason for this is that fallable humans use them.
The weakest link in the chain is often the one in the chair.


Amen.

---

### Post by erilidon on 2009-09-21
> **humphreybc said:**
> This is not a valid argument. Linux has a huge market share in servers, and servers are much more of a target than desktops as they can affect a lot more people and disrupt things a lot more. The fact that linux doesn't get many viruses is NOT due to its low market share, it's purely because linux has been designed to very secure.


[IMG]http://www.geek.com/wp-content/uploads/2009/06/net_applications_os_market_share_2009_05_may.jpg[/IMG]

Source: [http://www.geek.com/articles/news/windows-and-linux-lose-market-share-os-x-iphone-and-android-move-up-2009062/](http://www.geek.com/articles/news/windows-and-linux-lose-market-share-os-x-iphone-and-android-move-up-2009062/)


Now I will say that its doesn't directly apply, but the more something is used the more it can be abused.

---

### Post by misfitpierce on 2009-09-21
You said you went into Vista and got rid of it... maybe it was from Vista side as it did not seem to really affect Ubuntu besides not being able to be deleted because it was probably system protected file by vista somehow... I just doubt it very highly.

---

### Post by Exodist on 2009-09-22
Linux can get "linux" viruses. I have stated this many times before the only reason the linux community doesnt have virus and spyware issues at the moment unlike windows is our low usage rate. When GNU/Linux does start getting as popular as windows you will start seeing many of the same issues that windows users do currently.

The good part about linux tho is even if a USER gets a virus, it will only effect his account and not other users account. It also will not effect the system files. Thats saying also that the user is smart enough to not try to run everything as root.

Currently when you surf the web or download software you are still getting bombarded by spyware, maleware and even virus while running linux. The only good part is they are not written to run on the linux kernel.

But that day will come. Just prepare for it and get used to running AV programs now.

- Exo

---

### Post by gn2 on 2009-09-22
> **Exodist said:**
> I have stated this many times before the only reason the linux community doesnt have virus and spyware issues at the moment unlike windows is our low usage rate. 

Spouting rubbish many times doesn't stop rubbish from being rubbish.

---

### Post by Exodist on 2009-09-23
> **gn2 said:**
> Spouting rubbish many times doesn't stop rubbish from being rubbish.

Explain why you dont think a "linux" virus can infect "linux"?

You know doctors say denial is the first sign of trouble! :lolflag:


Ref: [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by Chronon on 2009-09-23
You make the claim, you furnish the proof.  I am comfortable remaining a skeptical agnostic about this.  If you wish to assert vulnerability to a particular virus then by all means point it out.

---

### Post by erilidon on 2009-09-23
What about Bliss?? It has happened before and it can happen again

[http://en.wikipedia.org/wiki/Bliss_%28virus%29](http://en.wikipedia.org/wiki/Bliss_%28virus%29)

---

### Post by Perfect Storm on 2009-09-23
> **erilidon said:**
> What about Bliss?? It has happened before and it can happen again

[http://en.wikipedia.org/wiki/Bliss_%28virus%29](http://en.wikipedia.org/wiki/Bliss_%28virus%29)

Well you have to execute the virus yourselves and give it permission to run as superuser before it's dangerous.

In the light that most software is installed through a package manager it's unlikely such virsu is a threat. Then we're back to social engineering issue.

---

### Post by Chronon on 2009-09-23
> **erilidon said:**
> What about Bliss?? It has happened before and it can happen again

[http://en.wikipedia.org/wiki/Bliss_%28virus%29](http://en.wikipedia.org/wiki/Bliss_%28virus%29)

Bliss can only do something with the cooperation of a user.  Some people consider it more of a trojan than a virus.

I looked at a selection of the viruses listed on that Wikipedia article and none of them seem to have a way to infect properly installed software (i.e. software located in a directory in which the user does not have write permission).  They mostly seem to rely on being executed too.

This is a reason that the Ubuntu repository system is good, because you have a set of trusted software to install, rather than going out on the internet and downloading random binaries, as some Windows users are in the habit of doing.

---

### Post by gn2 on 2009-09-23
> **Exodist said:**
> You know doctors say denial is the first sign of trouble! :lolflag:

Too true, it's full of crocodiles!

BOOM BOOM!

---

### Post by erilidon on 2009-09-23
> **Chronon said:**
> Bliss can only do something with the cooperation of a user.  Some people consider it more of a trojan than a virus.

> **Artificial Intelligence said:**
> Well you have to execute the virus yourselves and give it permission to run as superuser before it's dangerous.

It was not really dangerous, yes. But there it was. And Stoag was worse even though it didn't pose a problem for long.

---

### Post by lisati on 2009-09-23
Other than the nuisance value (mainly wasting bandwidth and disk space) the only trouble I've had directly involving viruses have had a ["pebcak error"]("http://it.wikipedia.org/wiki/PEBKAC") component. 
As this thread illustrates, we could wax lyrical about the topic....


Edit Realised the [original link]("http://www.ninetyandnine.com/Archives/20000807/devotion.htm") religious spin, we don't want any fights.

---


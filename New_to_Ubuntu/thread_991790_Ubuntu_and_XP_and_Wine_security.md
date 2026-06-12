---
title: "Ubuntu and XP and Wine security"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Crow550 on 2008-11-24
Is an anti virus and software firewall and spyware and such needed in Ubuntu?

I have XP setup with those on another partition, but is there any risks when running Ubuntu? I know Ubuntu closes all open ports so a firewall isn't needed? Right? and I haven't heard of anyone getting or spreading viruses or other nasties through Ubuntu. Can a virus live in Ubuntu and then attack an NTFS partition or Wine programs / games?



I installed Ubuntu 8.10 on my friends laptop, whom would always get XP infected with spyware and viruses somehow. He also connects to whatever hotspot is available.

Any additional security measure I should add? Like a VPN. 

He prefers tasks as simple as possible and is a total noob. You know Keep It Simple Stupid.

---

### Post by lakersforce on 2008-11-24
Anti Virus could be a good idea if you are sending emails to Windows users (so that you don't accidental send them malware). Firewall is always a good idea!

---

### Post by GSF1200S on 2008-11-24
> **Crow550 said:**
> Is an anti virus and software firewall and spyware and such needed in Ubuntu?

I have XP setup with those on another partition, but is there any risks when running Ubuntu? I know Ubuntu closes all open ports so a firewall isn't needed? Right? and I haven't heard of anyone getting or spreading viruses or other nasties through Ubuntu. Can a virus live in Ubuntu and then attack an NTFS partition or Wine programs / games?



I installed Ubuntu 8.10 on my friends laptop, whom would always get XP infected with spyware and viruses somehow. He also connects to whatever hotspot is available.

Any additional security measure I should add? Like a VPN. 

He prefers tasks as simple as possible and is a total noob. You know Keep It Simple Stupid.

Alot depends on your current setup. Yes, you can spread a virus to XP from Ubuntu, utilizing ntfs-3g. Thats to say, if you download a virus on Ubuntu, it will not hurt Ubuntu, but if its later moved to your XP partition and XP executes it, than it will be infected.

Ubuntu uses iptables, which is a firewall built right into the kernel. This is WHY the ports are normally closed. You can use GUI clients like bulldog and/or firestarter to configure iptables, and these can be found in the repos for free of course :). Also, if you use a router, many times they will offer firewalls themselves, and generally speaking a hardware firewall such as a router is more secure than a software one. You could install an antivirus client (there are some in the repos) to screen files before placing them on the XP partition, just to protect windows. Ubuntu itself will be fine. 

Yes, wine can be infected with certain viruses, but you would generally need to execute the viruses WITH wine, something that is not going to happen if you just download it. Also, even if this happens, since wine doesnt run as root, the ramifications will be limited to wine itself, and will not affect Ubuntu security wise.

For you, I would recommend an antivirus client to scan directories that you are worried about, and call it a day. You dont need to throw money at linux to keep it working, so try not to worry.. :)

---

### Post by Michael.Godawski on 2008-11-24
Here are some essays dealing with the issue of linux vs. windows viruses.

[LIST]
[*][http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
[*][http://ubuntuforums.org/showthread.php?t=925296](http://ubuntuforums.org/showthread.php?t=925296)
[*][http://ubuntuforums.org/showthread.php?t=143119](http://ubuntuforums.org/showthread.php?t=143119)
[/LIST]
> Being based off Unix Linux is built to be secure on a network from the ground up. This means that it is a lot easier to secure your vital files, and to avoid viruses being able to spread or damage your computer.

Also when you start to use Linux you become more tech-savvy auto-magically, so to speak. You become aware of the dangers and of the protective systems, and you stop doing dumb things. :)

---

### Post by hyper_ch on 2008-11-24
> **Crow550 said:**
> Is an anti virus and software firewall and spyware and such needed in Ubuntu?
Generally they are not needed... but depending on what you want to do it is good to have such...
e.g. if you are behind a hardware router (built into your dsl/cable modem for example) then there's no need for a seperate firewall... however if it's your notebook and you use it also at university and work and publich wifis/lan... then you might consider setting up a few things in iptables....

> **Crow550 said:**
> I know Ubuntu closes all open ports so a firewall isn't needed?
Acutally ubuntu doesn't close ports... it's just that no applications are running that will have open ports... but when you install a daemon (like ssh-server) then it will "activate" port 22 because it will listen on it.

> **lakersforce said:**
> Anti Virus could be a good idea if you are sending emails to Windows users (so that you don't accidental send them malware).
I disagree... it's much more likely those windows users will get infected by someone else... if they don't take care of themselves they will eventually get infected and chances are, that it's you, are very slim.

> **lakersforce said:**
> Firewall is always a good idea!
Not really...

---

### Post by billgoldberg on 2008-11-24
> **Crow550 said:**
> Is an anti virus and software firewall and spyware and such needed in Ubuntu?

I have XP setup with those on another partition, but is there any risks when running Ubuntu? I know Ubuntu closes all open ports so a firewall isn't needed? Right? and I haven't heard of anyone getting or spreading viruses or other nasties through Ubuntu. Can a virus live in Ubuntu and then attack an NTFS partition or Wine programs / games?



I installed Ubuntu 8.10 on my friends laptop, whom would always get XP infected with spyware and viruses somehow. He also connects to whatever hotspot is available.

Any additional security measure I should add? Like a VPN. 

He prefers tasks as simple as possible and is a total noob. You know Keep It Simple Stupid.

You can have a thousand viruses on your Ubuntu install.

None of them will do anything, they will just sit there like any file. 

Not doing anything.

Let's say you downloaded something from limewire. It could contain a virus. In Ubuntu the file can work as expected. If you copy that file to Windows, it will also work but the virus that came with it will wreak havoc.

By itself no virus will jump from the Ubuntu partition to the Windows partition.

It might be possible for Wine programs to get infected. Either way, it will not affect Ubuntu, but it might infect your wine drive.

So no, if a virus resides in Ubuntu it will not do anything. It will just be a file.

--

For you friend, well make sure he has a decent anti-virus client with real time protection. The same for anti-spyware client and a decent firewall.

Also make sure that when one of those programs says that some file is not safe to open or something that he doesn't open it.

The reason I say this is because when I was at my sisters house, she was browsing a website and avg popped up with a warning. I didn't even have time to say something, she had already allowed the action to take place. I asked her if she did that before, she said yes, all the time ...

---

### Post by Crow550 on 2008-11-24
What about his hotspotting or war driving. He has a bad habit if there is a hotspot avalible he is gonna use it. I've told him to only connect to trusted hot spots. But he's stubborn. Like I said a total Noob. Do I just tell him make sure when entering sensitive places like e-mail that you connect to https:// and or see a padlock on the bottom of the browser or a secure login button on the page and personal sites like bank and paypal are a no no on public hotspots and everything you type could be recorded by someone on a non https site.

Or what? Is there something he should use like a vpn or something? Or don't worry about it.

---

### Post by Crow550 on 2008-11-25
Well?

---

### Post by Paqman on 2008-11-25
> **Crow550 said:**
> Can a virus live in Ubuntu and then attack an NTFS partition or Wine programs / games?


Yes, but your antivirus protection in Windows would protect you from anything download in Ubuntu then executed in Windows, just the same as anything downloaded in Windows.

As for Wine, it's still running in Linux, so even if the code executes it can't really do anything because the system files it wants to use aren't available. At worst it could gunk up your .wine directory within your /home folder, which is hardly a big deal. The Wine devs are well on top of making sure that they aren't opening Linux up to Windows malware.

---

### Post by Crow550 on 2008-11-25
I was referring to what I posted last. "About his hotspotting or war driving"

---

### Post by Paqman on 2008-11-25
> **Crow550 said:**
> I was referring to what I posted last. "About his hotspotting or war driving"

I wouldn't worry about being cracked, it's pretty unlikely. A strong user password and the default security settings should protect him.

However, logging on to a non-public network is illegal in many places. So he's being a very naughty boy.

---

### Post by Crow550 on 2008-11-25
Yup but lots of people think just because they have wifi, if they scan and connect it's a hotspot. lol. Plus the amount of people who buy a wifi router and don't secure it. And some setup hotspots to collect suckers data and some are setup to infect anyone that connects. I will tell him again. Like I said he is stubborn. I think Ubuntu will make his PC last longer. He always seems to get a virus or spyware. Like sheesh do ya listen to anything I tell ya? I suspect it's from going to whatever pr0n sites Google comes up with and using Internet Explorer lol. I'm like use firefox. I also set him up with Gmail because his Yahoo account became a spam box.

I don't know. I secured XP as well. Using a limited account and SRP and putting a firewall and anti-virus. For those few Windows games when he needs to use XP.

---


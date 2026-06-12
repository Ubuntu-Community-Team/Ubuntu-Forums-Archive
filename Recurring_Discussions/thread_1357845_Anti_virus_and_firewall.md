---
title: "Anti virus and firewall"
date: 2009-12-17
forum: Recurring Discussions
---

### Post by sarsar on 2009-12-17
Hey, im running ubuntu 9.10 desktop my acer aspire one netbook (as the UNR 9.10 and UNR9.04 links were broken when i tried to boot from memory stick). I know linux does not get attacked as much by viruses as the windows os but i would like to upload an anti-virus and firewall just in case. Which one is the best to use? I had fire-starter but since been told that its not the best one to use. Can someone please help me find the best **[COLOR=Black]free[/COLOR]**  antivirus and firewall. 

I will warn you, i am an absolute beginner and if any uploading via the terminal is needed i will have to have it in step by step format. However i am willing to have a go after been empowered by 2 success stories with the terminal in ubuntu. 

Also sorry if this is already a thread.

Many Thanks

---

### Post by oldos2er on 2009-12-17
You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by wojox on 2009-12-17
And here: [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by admiralspark on 2009-12-17
For ease of use, I've found Firestarter to be the best firewall app out there. It's a push-to-start/push-to-stop kind of deal, clean screen and minimizes to a small button, sucking up little if any system resources. 

As for antivirus, well, I'll first point out the required: "Linux (and all Unix systems) are designed in such a way that it is very difficult to infect a system without actually intending to, and even then damage will be severely limited." --bigtomrodney
However, I'm sure you've heard that a million times, so I'll actually be helpful! Go to Applications-->Ubuntu Software Center, then search for ClamAV. You will see something called Virus Scanner, that's what you want. Installing that will allow you to run scans/update/remove viruses etc. with a GUI, nice and easy. Only problem I have with it is the fact that I can't schedule it to run, say, at 2 in the morning every night; however, I'm sure there's ways around that. 
Trust me though, unless you're afraid that something you downloaded to Ubuntu will have a virus that could infect a windows friend (say, anything over a torrent network) you will enjoy this. I'll be writing up a bit on how to use it on my blog, which hasn't been revised yet (check my sig in case it appears).

Peace


EDIT: couple more good links:
[http://www.psychocats.net/ubuntu/security#firewallantivirus](http://www.psychocats.net/ubuntu/security#firewallantivirus)
[http://ubuntuforums.org/showthread.php?t=425530](http://ubuntuforums.org/showthread.php?t=425530)

---

### Post by 3rdalbum on 2009-12-17
Don't bother with an antivirus program. There are no viruses for Linux in the wild. Enjoy your freedom.

Also about the firewall, Ubuntu does not listen to incoming ports by default, so you don't need a firewall running on your computer. Windows, however, does listen to incoming ports which is why you need a firewall on Windows.

Only use a firewall (I reccommend gufw from the repositories) if you install some server software that you don't want anyone but yourself to access.

---

### Post by staf0048 on 2009-12-17
> **3rdalbum said:**
> Don't bother with an antivirus program. There are no viruses for Linux in the wild. Enjoy your freedom.


Not true.  
[http://en.wikipedia.org/wiki/Linux_malware#Threats](http://en.wikipedia.org/wiki/Linux_malware#Threats)

Although I do agree that you probably do not have to worry about your Linux machine, your computer can still act as a carrier for viruses to your friends window's machines.  It's a good practice for all us Linux users to scrub our machines so at least we're not helping the virus spread - even if we don't get infected ourselves.

---

### Post by running_rabbit07 on 2009-12-17
You already have a firewall. Go to a terminal and enter ```
sudo ufw enable
``` It will tell you that the firewall is automatically started at boot up.

---

### Post by running_rabbit07 on 2009-12-17
```
sudo apt-get install clamav
``` Will get you anti virus. ```
sudo apt-get install clamtk
``` Will get you a GUI program to run the antivirus the easy way. For the GUI, you will have to go to the ClamTK site to get the latest version every other month.

---

### Post by Georgia boy on 2009-12-17
I also remember a thread about that's in the community cafe about where someone downloaded a deb from what is usually thought of as a trusted site. So, things can and do happen. But personally I have only AdBlock, NoScript and using a hard wire router. I'm only using a desktop. But, you will find throughout the forum that there are so many views on this subject. To each their own.

Tom

---

### Post by running_rabbit07 on 2009-12-17
To run ClamAV in terminal, use the command ```
sudo clamscan
``` To find the different commands that can be used with clamscan run this command.```
man clamscan
```

---

### Post by running_rabbit07 on 2009-12-17
> **Georgia boy said:**
> I also remember a thread about that's in the community cafe about where someone downloaded a deb from what is usually thought of as a trusted site. So, things can and do happen. But personally I have only AdBlock, NoScript and using a hard wire router. I'm only using a desktop. But, you will find throughout the forum that there are so many views on this subject. To each their own.

Tom

The only problem with the type of problem the guy with the .deb had is that there is no way to detect it. That is why we have to be vigilant on where we download from.

---

### Post by admiralspark on 2009-12-17
As an update, I finished the article I wrote for ubuntu user's who are protecting Windows computers by not spreading viruses. Here's the link to my blog: [http://admiralspark.blogspot.com/](http://admiralspark.blogspot.com/)
As the other's said, there's no reason to have either unless you're protecting other computers or taking unnecessary risks over the internet. Smart computing is the #1 anti-virus/-malware/-rootkit in the world, and it's free!

---

### Post by Georgia boy on 2009-12-20
> **running_rabbit07 said:**
> The only problem with the type of problem the guy with the .deb had is that there is no way to detect it. That is why we have to be vigilant on where we download from.


I totally agree with that. I think that is what also kept me out of trouble in Windows. The only thing I ever had was false hits I would get when I had McAfee and AVG. I used to get false hits and would leave them until I did a Google and researched to be sure. That was one of the things I hated about Anti-Virus alerts. Granted I was lucky in that I had never gotten anything but I still hated getting the false alerts and going to the sites to see that quite a few others had the same thing. I remember a former co-worker who would set his computer back to factory conditions about every three to five months just to make sure that there wasn't anything on it. Sounds like too much trouble doing that to me. I only did that once or twice in all the years I've owned a computer and it was due to something else not a virus or trojan/maleware. On the Windows side I do have the AVG, Zone Alarm,Spyware Blaster, plus the Windows defender installed. But, I haven't been back there to do anything since May or so. Last time I was on Windows it took me about two and a half hours to get everything updated. I'd hate to think about going back to the Windows side of the house now. Afraid how long I would spend getting everything updated. I only went there the last time to help out my cousin with her Open Office. Spent all that time just to find out that she had Vista and I'm running XP. Got all the information she needed and sent to her by email. Told her that if I get back to Georgia she can thank me by having a case of iced beer waiting for me. Told her that I wasn't going back to the Windows side for anything now.
I don't put Windows down, I've used it since the 3.1 days. It's just I want to learn and use something different. Believe me when I say that this is a learning experience all the time. Always something going on to learn here. Maybe someday I'll be able to contribute something to help others. Hope so, but I'm still learning.

Tom

---

### Post by crimesaucer on 2009-12-22
I'm using iptables with a stateful firewall script that is supposed to protect my computer against common attacks by "DROP"ing those packets, and also "hiding" the computer from certain ping requests.

(I check things out with the "sudo iptables -nvL" command and it looks like the only thing I see that ever gets dropped is some reserved private networks)

On top of that I use both the Adblock-plus and Ghostery Add-ons with Firefox.

---

### Post by sarsar on 2010-10-19
Thankyou all very much for your help. SO far so good with the virus thing. Going to set up the clam antivirus as i am now dual booting with windows. 

Again Thankyou

---

### Post by sarsar on 2010-10-19
Thankyou so much for such a simple solution. Sorry it is a very late thankyou, i was enjoying my freedom but now i dual boot so the anti-virus is helpful. Thankyou for making it so simple and effortless

---

### Post by Quadunit404 on 2010-10-20
I don't really like ClamAV or ClamTK that much - that thing eats resources, has poor detection rates and takes too long to scan something (I remember it taking at least three minutes to scan a folder with three files in it - each file was a few kilobytes, too.) I replaced it with BitDefender for Unices recently. You can request a free license key on their site - which gives you a license key for free that lasts an entire year. You can't do that for office environments, though.

It's always a good thing to have an additional layer of security, especially since the threat of Linux viruses is very real - just not a MAJOR threat right now.

---


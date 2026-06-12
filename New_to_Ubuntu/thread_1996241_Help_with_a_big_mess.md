---
title: "Help with a big mess"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by hawaiiman on 2012-06-04
I don't have much Linux iq (maybe negative number). I just started teaching English at a rural hs in N.E. Thailand. They have nearly 30 stations, the most of which are down for various reasons. At a normal work day maybe 10 machines running. Connected with LAN cable through several 10/100 switches to an HP Proliant ml350 gateway to a fiber line.
Internet keeps going down, and seems slow considering the fiber. I have a screen shot of the server monitor when it's down. Right now I just reboot it and 90% of the time a single reboot gets it up for hours to days.
Server is very dirty inside, so I'll clean it this week (it's hot here and they keep turning the air off to save money).
I am wondering if I couldn't install Ubuntu server as an alternative boot, and get a stable situation going that way.
I don't know if I can get the root password for the current o/s and I also don't know what that distro is.
It has 2 drives and when the internet fails, the lights on one turn from green to red.
Mysql (whatever that is) can't be accessed because it's part of a subsription from something called Freebee that I'm sure hasn't been paid. Anyway there is an error message about mysql.
The workers, admin and students at the school are very nice, and I want to help them. Any assistance truly appreciated--Jack

---

### Post by traditionalist on 2012-06-04
What is the current operating system?  Do you have any experience with that or hardware generally?

Doing something like you propose, basically from scratch, is a very big job for a beginner. It's not impossible, but it wont be easy either. 

In any case, a lot of information and a good plan is a basic necessity for such an undertaking.  You will also need the support of the "powers that be". If you try to do something like this on your own responsibility and something goes wrong you could be in trouble.

Some basic information for you;

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugbasicnet.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugbasicnet.html)

[http://www.basicconfig.com/linuxnetwork](http://www.basicconfig.com/linuxnetwork)

---

### Post by hawaiiman on 2012-06-04
Thanks for the response. As yet I don't know which Linux distro is running. I have a fair amount of hardware experience having started a small wisp, done some repairs, built some boxes, etc.
 Powers that be...hmmm, that's a tough one. This involves not only the usual politics of hierarchy that occur most places, but the intricacies of Thai culture. My wife (a Thai and office manager elsewhere) advised me just to do it.
One of the more senior teachers is the assigned admin, but he has business interests outside the school and has allowed the system to fall into near total disrepair. In this culture, confrontation is usually avoided. Whether I have "permission" or not I will pay the consequences (which because of my high status as a foreigner teacher may be limited) if it stops working altogether.
 In 2 weeks I have advanced to having a key to the server room, and being relied upon by actual users (students and office staff) to "please fix internet!".
I'm hoping getting the temp down with a good cleaning (yes I know about static) will help, and convincing them to leave the air turned on with the therm. set fairly high (maybe 27c) will help. Without air the ambient gets over 34c almost every day, and that room probably pushes 37c. The dirty carpet will get cleaned also. The modem was getting too hot also, so I moved it into the exhaust stream from the server, and that's actually helped a little.
Sorry the screen shot from my cell isn't better. This is what I see when it's stopped.

---

### Post by traditionalist on 2012-06-04
Well, in your position I would start small. Grab a box somewhere else and set that up as a server. Don't touch the present setup at all. You can then add machines to that and only go live or take any risks at all when you know that everything is working. High ambient temperatures can be a real killer, and this is worse with "high-end" boxes than standard workhorses.  Maybe you can set up some sort of cooling system in a small area for your setup?  If so many machines are out of commission, then you can simply begin repairing a few and installing your stuff on them.  Once you have  a couple set up and running well it 's easy to clone them later. You can set up a whole network quite quickly once you have the core running.

For a plan and more info have a look here;

[http://www.linuxquestions.org/questions/linux-networking-3/setting-up-a-linux-school-network-long-204996/](http://www.linuxquestions.org/questions/linux-networking-3/setting-up-a-linux-school-network-long-204996/)

[http://www.theregister.co.uk/Design/page/linux_case_study_orwell_high_school.html](http://www.theregister.co.uk/Design/page/linux_case_study_orwell_high_school.html)

[https://schoolforge.net/](https://schoolforge.net/)

[http://www.reallylinux.com/docs/ltsp-oped.shtml](http://www.reallylinux.com/docs/ltsp-oped.shtml)

You also need to be educating a few "admins"  ( Aka recruiting helpers who will also learn something).  You are a teacher so approach it as if you were teaching the subject and run a course in it.

---

### Post by hawaiiman on 2012-06-04
Great suggestions, all. Another problem here is that often hacked copies of windoze are are used which can be loaded with little ..problems. I've been a repair man, mostly factory type, and a mechanic most of my life, and find that often problems are due to a combination of causes. Right now I'm studying Linux so I can query the system and get more information (always a good thing).
Another idea I've toyed with is to get a gigabit security router, and throw it in, in place of the server. I could have many of the same security fixes in place. It would cost me $100 for a good used unit. Of course at this point everything comes out of my pocket.
I can tell the users, I'm going to shut down for an hour or so any time. They are so happy to see anyone actually trying.....
I haven't had a chance to go over the links you sent, but be assured that will get done today. 5 pm here.
Can I set up the server to "dual boot"?(would I need the root password to do that?) If I could, I could get Ubuntu Server going and get it configured a little at a time, switch back to the other if I have a problem.
It actually occurred to me that I could install Ubuntu on one of the client machines, get it working with the various uses of the office staff and teachers, and let them try it. If I could make that fly it would clean up possibles issues from hacked windoze, and school wouldn't be out a cent.

---

### Post by prshah on 2012-06-04
> **hawaiiman said:**
> As yet I don't know which Linux distro is running. 

That's freeBSD. It's not linux (though similar).

I would suggest you work on a different machine; prepare it as a "slot-in" replacement.

The scope is too wide to discuss here though; you need to get started and tackle things one at a time.

---

### Post by hawaiiman on 2012-06-04
PRShah, thank you! Ok so it's running freebsd. Can you see anything in my blurry screen shot that might give a clue as to why it's going down? 
As far as slotting in, are you saying that some form of dual booting would be not advisable for me? We have $0 budget, other than what I get for a salary, so the machine available would be one of the wounded or dead ones here. I guess that would work as a test bed, then if I hit on something useful, I could do a clean install on the HP with the same setup (?).

---

### Post by traditionalist on 2012-06-04
> **hawaiiman said:**
> PRShah, thank you! Ok so it's running freebsd. Can you see anything in my blurry screen shot that might give a clue as to why it's going down? 
As far as slotting in, are you saying that some form of dual booting would be not advisable for me? We have $0 budget, other than what I get for a salary, so the machine available would be one of the wounded or dead ones here. I guess that would work as a test bed, then if I hit on something useful, I could do a clean install on the HP with the same setup (?).

You would be better setting up a separate machine as a server and then switching over when you have it set up. Then you could set the existing machine up properly.

I am not a linux freak myself, ( although very quickly becoming one! :)  ) indeed I have only been using it as a desktop for four weeks, but I spent a very long time planning and setting up various networks, mainly GAN's and WAN's, using various systems, and the basic principles are the same.

The main trick here is to get everything set up so that you can switch over. You don't want to mess about with a running system at all.  When you can take it safely off line is the time to worry about that.

---

### Post by mcduck on 2012-06-04
based on what I can see on the screenshot, the system crashed due to a physical hard drive failure.

That could be beacuse of the high temperatures, but being sensitive mechanical devices the drives could break for any of the multiple other possible reasosn, or simply because of old age/bad luck.

If you have a bootable Ubuntu CD or USB drive at hand, you could try booting the system with it and using the Disk Utility to check the drive's SMART status. But in the end I'd say the general rule with physical drive failures is that the drive simply needs to be replaced, so you'll probably have to do that anyway.

---

### Post by hawaiiman on 2012-06-04
traditionalist, Thank you. Yes, I believe that do to the efficiency of Linux, a fairly modest machine could work well as a temporary server. As we have multiple machines out of service, I can rob some ram and get a second ethernet card for the output. I've already downloaded Ubuntu Server, and am scouting security add ons. It sounds like fun.

---

### Post by hawaiiman on 2012-06-04
mcduck, great information! Yes when it boots or is running ok,both drives are green lighted, but the second drive goes to red when internet fails. It's running Apache, so I'm guessing if i pick up a caddy for that machine and a drive I can just throw it on, and Apache will get it into the mix with no input from me. Then I can pull the suspect drive. (??)-thanks--Jack

---

### Post by prshah on 2012-06-04
> **hawaiiman said:**
> 
As far as slotting in, are you saying that some form of dual booting would be not advisable for me? We have $0 budget, other than what I get for a salary, so the machine available would be one of the wounded or dead ones here. I guess that would work as a test bed, then if I hit on something useful, I could do a clean install on the HP with the same setup (?).

Yes, I strictly advise against dual booting. It is preferable if you can re-use some of the hardware that you say is available, to make one working machine, upon which you can proceed to experiment.

The specs needn't be steller; 1GB of RAM if you can manage it, 512MB at a pinch; Any processor PIV and above (GHz/MHz does not matter).

As you are suggesting, you can use it as a test bed, and ramp it up if it seems promising. 

You really don't need to worry about budget; as far as I can see, your main worry will be about time.

One further suggestion: I would advise starting with Lubuntu / Xubuntu, rather than Ubuntu Server. Ubuntu Server has no GUI, and may increase your learning curve. Though most of your work will be done in command line (CLI), it is still reassuring / useful to have the GUI from time to time.

Once you have a suitable machine set up and running Xubuntu / Lubuntu, you can start throwing tasks at it one at a time, taking input from the forums when you are stuck, or don't know how to start off.

Once your familiarity has increased, you can then decide if Ubuntu Server better suits your needs or not.

---

### Post by hawaiiman on 2012-06-04
PRShah, Yes I see that ubuntu doesn't fully recommend a full gui for Server. As to experimenting with the others, are you saying I should use one of them as a base to install server features? I have run Ubuntu before, and had good luck. I'm not clear on why I shouldn't try Server, as it will be on a clean machine. 
I plan on using remote administration. I'll be looking at ssh, ebox, ispconfig....maybe a light gui like openbox ?
I can already see that to implement decent security, I will have to do a lot of commandline work anyway, so maybe the gui isn't a big deal. It will help when I access using ssh from my win7-64 laptop at home. I want to monitor network activity down to level 2 from home, as I only teach 3 days a week in the afternoons.-J

---

### Post by buzzingrobot on 2012-06-04
I'll just offer some non-technical advice:  If you fix it, you own it. People will find you when it breaks.

Mysql is a database program.  Is there a need for a database at the school?  Perhaps staff used one before this one broke.  In any case, you do not need it if all you need the server to do is provide internet connectivity.

Ditto Apache.  It's a web server. You don't need it unless you need to run a web site on the server.  For security reasons, you're better off not running it if you don't need it.

One reason to run Apache would be if someone set up a caching web server, i.e., one that caches web content locally .  When users at the school browsed the web, content would be served from the school's server (and refreshed at certain intervals). That's useful if you have a flaky net connection, and/or want to block student access to some sites.

For future reference, "uname -a"  will show you info about your kernel, etc.

---

### Post by hawaiiman on 2012-06-04
[buzzingrobot]("http://ubuntuforums.org/member.php?u=1488460"), thanks. Well, at this point I know zip about the history of this network or uses. There are 2 teacher rooms/offices each with 4 stations, a library with 4-5 stations that are student accessed, a computer science room with 12 stations which is also the home of the server (..may be a bad idea :-)  most of these machines are dead for various reasons and student access has been cancelled (loving the green carpet, not). I also see some cable tied to a tree going to the other building, as yet unexplored. There is a media room with projectors etc. which may have had video conferencing set as a goal. The director'soffice has a machine but lan is dead there, and admin office has one station. Main actual use is from the two teacher offices and the library. I know there has been an attempt to restrict student access, bandwidth limiting is in place, and for some reason, printer/file sharing is blocked. no router, just the server and switches around here and there.
There was a subscription service to Freebee (?) I looked them up, and they have a monthly fee, which probably hasn't been paid. I think they were hosting Mysql, for example. Freebee comes up with a password request when you access the browser. 
I don't believe the school has a wbsite, not sure about in house email. Central storage for records and shared files would certainly be a good idea if it isn't being done.

---

### Post by hawaiiman on 2012-10-20
Update: picked up a couple rebuilt drives, installed one and that fixed the old server. In the mean time our ISP and service level have changed 2-3 times. It finally settled on a fiber suplied adsl connection that won't work with the free bsd server. I embarked on building a fresh server based on Ubuntu server. Knowing next to nothing about Linux at the start, it's been a steep and bumpy ride. After uncounted attempts, finally got one going based on very minimal (packages at install) 10.04 64bit LTS server (highly recommended). Samba file server works, eth0 gets dhcp from enterprise modem router with QOS, eth1 has static ip and dnsmasq deals dhcp to LAN. Windows clients on LAN forwarded to internet with iptables command in /etc/rc.local. Simple and sweet. UFW makes problems and was uneeded, so dumped it, dhcp3, & NM. Never would have made it without this forum.

---

### Post by grahammechanical on 2012-10-20
You might find this link helpful

[https://wiki.ubuntu.com/ThaiTeam]("https://wiki.ubuntu.com/ThaiTeam")

and this one

[http://loco.ubuntu.com/teams/ubuntu-th]("http://loco.ubuntu.com/teams/ubuntu-th")

Regards.

---

### Post by larrys4227 on 2012-10-20
I've enjoyed reading through this thread .... :popcorn:

Glad you made some headway, but I'd like to ask if you ever found out HOW they were using network before all this?  Is the original machine nothing more than a gateway to the outside world for the teachers and students?, or were there intricate things going on like web, ftp, mail, etc??

I really cant help that much, but I have enjoyed the thread and you good natured-ness to take on such a task.

Good for you my friend!! :)

---

### Post by hawaiiman on 2012-10-20
Thanks for the heads up about Ubuntu Thai team.
So far I have learned that there was  a hosted web site, which by the time I got there was useless due to server problems. It was being used as a gateway with some firewall features. It was also dealing dhcp to the windows clients and controlling access with passwords. If there is good acceptance of the Ubuntu machine and new features, I will talk to them about formatting the old machine and making a Ubuntu server on it with samba file server, web hosting, email. The new machine is built from a normal desktop with a single hdd. The old machine is a real server with raid 5, hot swap, etc. If important files are being kept on the server, I would be more comfortable about having the increased reliability/security of a real server in the long run. I just don't see learning unix to do it.

---


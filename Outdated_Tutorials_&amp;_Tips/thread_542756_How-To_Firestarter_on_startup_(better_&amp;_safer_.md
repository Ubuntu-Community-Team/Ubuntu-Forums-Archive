---
title: "How-To: Firestarter on startup (better &amp; safer way)"
date: 2007-09-04
forum: Outdated Tutorials &amp; Tips
---

### Post by nvteighen on 2007-09-04
This how-to will let you start Firestarter automatically without having to enter a password for it, but also **not editing /etc/sudoers** and, thus, giving access to anyone to change it.

Actually, this how-to was originally developed by **kukibird1** [in this thread]("http://ubuntuforums.org/showthread.php?t=508392"); I put it here so it is more visible; also, I wrote it in a way I hope it will be more newbie-friendly than the original post. Thank, please, that user and not me.

**_0. Understand what Firestarter is_**
Firestarter is **not** the firewall, just a nice tool to configure **iptables**, the actual firewall. 

Iptables resets itself after reboot, so Firestarter is meant to start at boot and recreate iptables' *rules*. This is made before even GNOME/KDE/Xfce is started, so you won't see anything... 

You **don't need to open** Firestarter to be protected... So, any solution that makes Firestarter open (not only start) will prompt you for the "sudo" password and, because that's nasty, you're told to edit /etc/sudoers... Not good.

**_1. Is it really Firestarter your problem?_**
How do you know if Firestarter is your problem? Please, do this test:
1. Reboot your machine.

2. After having logged in as normally, go to a Terminal (Applications --> Accessories --> Terminal) and type:

```

sudo iptables -nL

```

3. If you get the following, Firestarter **must be fixed**:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

If you don't get that and you know your firewall is not working, then either Firestarter is not the issue or it's not the "usual" Firestarter issue.

**_2. Fix it!**_
(To do this succesfully **don't open Firestarter**)
1. Enter Terminal (see above)

2. Type:
```

gksudo gedit /etc/firestarter/firestarter.sh

```
3. Locate the following "paragraph":
```

if [ "$MASK" = "" -a "$1" != "stop" ]; then
        echo "External network device $IF is not ready. Aborting.."
        exit 2
fi

```
It's near the beginning; be careful, check twice before going to step 4!

4. Make that paragraph look exactly like this (put a # before each line):
```

#if [ "$MASK" = "" -a "$1" != "stop" ]; then
        #echo "External network device $IF is not ready. Aborting.."
        #exit 2
#fi

```

5. Reboot. (If you know how to do it and want to skip the rest of the steps, deactivate the boot spash and monitor the boot process; it should say "Firestarter firewall starting up...[OK]". If so, you don't need to follow the rest)

6. Enter a Terminal and type "sudo iptables -nL" again. It should be different to what you saw at the beginning.

7. Open Firestarter, go again to Terminal and type "sudo iptables -nL" again. It should be the same as in step 6.

8. Review Firestarter configuration to see if it's correct (there's no particular reason to do this, just to be sure you're protected).

Now, you (and all users) are protected from boot, without messing around with sudo's configuration! You'll have to enter the password to access Firestarter, but as you usually do with other administrative apps.

[COLOR="Red"]NOTE:[/COLOR] **If you run Firestarter's Wizard after this method, you'll have to repeat Section 2!** If you want to change Firestarter's configuration, better do it using Edit -- > Preferences.

**_Reasonale_**
It seems (to me) that Firestarter thinks the network is not configured, so, without network, no firewall is needed and shuts down with an error. Putting those # is equivalent to delete the code that analizes that error, so this fix forces Firestart to start ignoring that "error" (?).

---

### Post by chrome307 on 2007-09-05
Thank You for compiling this and making it easy to follow ::)

---

### Post by nvteighen on 2007-09-05
Thanks! Any suggestion is welcomed, of course.

---

### Post by jefferystone on 2007-09-05
nvteighen,

Thank you for the information.  Thankfully someone confirms what I've been saying.

I had an alternate solution - this would run firestarter after the networking was started.

[http://ubuntuforums.org/showthread.php?t=449319]("http://ubuntuforums.org/showthread.php?t=449319")

> 
Here is the solution that worked for me:

I added sudo /usr/sbin/firestarter -s & to /etc/rc.local

---

### Post by nvteighen on 2007-09-06
> **jefferystone said:**
> nvteighen,

Thank you for the information.  Thankfully someone confirms what I've been saying.

I had an alternate solution - this would run firestarter after the networking was started.

[http://ubuntuforums.org/showthread.php?t=449319]("http://ubuntuforums.org/showthread.php?t=449319")
But doesn't that starts the GUI? 

As I said before, you don't need to run the GUI... and according to some it may be also a bit dangerous to run something the whole time with root privileges.

---

### Post by wnelson on 2007-09-06
It is in rc5.d as S20firestarter I had problems with it not starting so I just changed it to S21firestarter this gives it enough time to start after the network come up.

Walt

---

### Post by citizenphil on 2007-09-15
Just to reiterate what I said on the other thread, ([http://ubuntuforums.org/showthread.php?t=449319&page=3](http://ubuntuforums.org/showthread.php?t=449319&page=3)) it seems to me that this should be a default setting for the Firestarter package and perhaps should be fixed.  Do I misunderstand?

---

### Post by BLTicklemonster on 2007-09-15
Huh. I have firestarter installed, set it up and all, and have rebooted several times since, and only have this in /etc/firestarter:

non-routables.

No shell script.

I did something wrong somewhere, didn't I?

EDIT*

lmao oops, I ran setup again, and clicked save this time. rebooted and checked, and I have all kinds of cool stuff when I do step 2.

---

### Post by nvteighen on 2007-09-17
> **BLTicklemonster said:**
> Huh. I have firestarter installed, set it up and all, and have rebooted several times since, and only have this in /etc/firestarter:

non-routables.

No shell script.

I did something wrong somewhere, didn't I?

EDIT*

lmao oops, I ran setup again, and clicked save this time. rebooted and checked, and I have all kinds of cool stuff when I do step 2.

A question: do you use any restricted driver for your network devices (ethernet/wireless/modem)? Maybe that's why some people like me (using restricted Intel driver) must run these steps and some like you don't.

---

### Post by clever on 2007-09-19
I have had this problem on three different computers and this solution fixed it.  They were all using different network hardware but I was using the stock Feisty drivers with all of them (i.e. I never installed any special network drivers on my own).

The symptoms were as you described.  I would configure some rules with Firestarter and they would be applied and working.  Upon reboot, I would find that the ports I had blocked were open again.  Iptables was running with no rules, and "sudo /etc/init.d/firestarter status" showed that Firestarter wasn't running.

To be clear, I was never trying to get the Firestarter GUI to start when I booted; I only wanted my rules that I had configured to be applied into Iptables.  The fix listed above finally got it to work.

Thanks to kukibird1 and nvteighen!

---

### Post by euler_fan on 2007-09-20
Thanks for putting this together.

I didn't realize this was an issue . . . makes me wonder if I shouldn't just learn fwbuilder . . .

---

### Post by wnelson on 2007-09-20
I found something that is of importance. Because of the init.d system since /etc/rc5.d/S20firestarter starts before /etc/rcS.d/S20network are initializing the network and starting firestarter. So I just made a S48firestarter in /etc/rcS.d/S48firestarter and everything work fine now.

Walt

---

### Post by nvteighen on 2007-09-21
> **wnelson said:**
> I found something that is of importance. Because of the init.d system since /etc/rc5.d/S20firestarter starts before /etc/rcS.d/S20network are initializing the network and starting firestarter. So I just made a S48firestarter in /etc/rcS.d/S48firestarter and everything work fine now.

Walt

That's a more elegant solution, I think, just that bypassing the error diagnose.

---

### Post by ST.x on 2007-09-27
Okay this works, but the command in my sesions im using is: sudo firestarter

Is this the right one? As i've seen ones like:
sudo firestarter --start
sudo firestarter --start-hidden
sudo firestarter --start-hidden &

---

### Post by nvteighen on 2007-09-27
> **ST.x said:**
> Okay this works, but the command in my sesions im using is: sudo firestarter

Is this the right one? As i've seen ones like:
sudo firestarter --start
sudo firestarter --start-hidden
sudo firestarter --start-hidden &

If you have used this method, then you can safely remove firestarter from sessions. Let me clarify: Sessions determines what to start at your GNOME session; this method fixes Firestarter's start at PC boot up.

---

### Post by zhanglini on 2007-09-29
I ran sudo iptables -nL, and got the following:
```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  205.152.37.23        0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  205.152.37.23        0.0.0.0/0           
ACCEPT     tcp  --  205.152.132.23       0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  205.152.132.23       0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
DROP       0    --  0.0.0.0/0            255.255.255.255     
DROP       0    --  0.0.0.0/0            192.168.1.255       
DROP       0    --  224.0.0.0/8          0.0.0.0/0           
DROP       0    --  0.0.0.0/0            224.0.0.0/8         
DROP       0    --  255.255.255.255      0.0.0.0/0           
DROP       0    --  0.0.0.0/0            0.0.0.0             
DROP       0    --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        0    -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    0    --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.101        205.152.37.23       tcp dpt:53 
ACCEPT     udp  --  192.168.1.101        205.152.37.23       udp dpt:53 
ACCEPT     tcp  --  192.168.1.101        205.152.132.23      tcp dpt:53 
ACCEPT     udp  --  192.168.1.101        205.152.132.23      udp dpt:53 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
DROP       0    --  224.0.0.0/8          0.0.0.0/0           
DROP       0    --  0.0.0.0/0            224.0.0.0/8         
DROP       0    --  255.255.255.255      0.0.0.0/0           
DROP       0    --  0.0.0.0/0            0.0.0.0             
DROP       0    --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   0    --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
LSI        0    --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     0    --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0   

```

what does this all mean?  is it bad?

---

### Post by Revvion on 2007-09-30
oke, it used nvteighen' s method and all worked fine until i added a rule to allow a port i use for torrents to be open, now for some reason i have to start the gui every time or else i wont have any internet at all. Also i needed to put the ports for standard things like http in the firewall since then or it blocks it for some reason. Can somebody please help

---

### Post by nvteighen on 2007-09-30
> **zhanglini said:**
> I ran sudo iptables -nL, and got the following:
```

[*cut for convenience*]

```
what does this all mean?  is it bad?
No, it means that you're firewall is configured. Those are iptables' rules, which are applied to your connections. We use firestarter to easily set up those rules each time you start your computer, but some more advanced people do it directly with iptables according to their needs.

> **Revvion said:**
> oke, it used nvteighen' s method and all worked fine until i added a rule to allow a port i use for torrents to be open, now for some reason i have to start the gui every time or else i wont have any internet at all. Also i needed to put the ports for standard things like http in the firewall since then or it blocks it for some reason. Can somebody please help

Hmm... If you have to open http, it may be because you have set Outgoing as "restrictive". Open the GUI, select "Rules", see Outgoing configuration and select "Permissive" (any outgoing allowed); then you should be able to remove rules for http. The Torrent-port related problem is strange... How did you set that up? Does removing that rule solve the problem? (so we know that's the real problem!)

---

### Post by Goombie on 2007-11-04
Thanks for this nice howto! It worked for my Firestarter problem. :) I have one question, though. when I run  *sudo iptables -nL*, I get that long list of rules returned. Then, when I open the Firestarter GUI and run sudo  *iptables -nL* again, I get nothing returned. Is this a bad thing?

---

### Post by nvteighen on 2007-11-05
> **Goombie said:**
> Thanks for this nice howto! It worked for my Firestarter problem. :) I have one question, though. when I run  *sudo iptables -nL*, I get that long list of rules returned. Then, when I open the Firestarter GUI and run sudo  *iptables -nL* again, I get nothing returned. Is this a bad thing?
Are you sure Firestarter is correctly configured? Open the GUI, go to Edit menu --> Preferences to check them or, if you prefer to redo the Wizard, Firewall menu --> Wizard... (but if you do this you'll probably have to do all steps again).

---

### Post by jdackle on 2007-11-07
Wild guess here:

On firestarter's "Preferences", "Firewall" menu, I have all of the below checked:
* **Start/restart firewall on program startup** - *i.e. when firestarter is called, e.g. from the command-line, even w/o the -start option, the firewall will be (re)started (the iptables firewall that is...). This seems to be working for everyone here, so everyone should have this turned on, I suppose...*
* **Start/restart firewall on dial-out** - *this means: when the network is started/restarted! ;-), firestarter will (re)implement the iptables rules. My doubt is wether this will happen regardless of whether the network was up or not when the bootup firestarter script was executed, i.e. whether firestarter needs to be running for this to run or if it is built into the iptables rules directly - Anyone iptables-wise care to elucidate on this possibility?*
* **Start/restart firewall on DHCP lease renewal** - *this is needed if your IP address is not static but is rather changed by you ISP every now and then, even when the connection is up. Should be of no major importance here, unless you happen to notice sometimes your iptables are correctly setup on boot-up and others not.*

I never had any troubles with firestarter not implementing iptables rules at bootup and I don't even use a restricted module for my modem, not available! I.e., I use a few shell scripts to actually load the firmware (directly downloaded from the Net) and setup a few things so I can have Internet...

Does that make any sense? (I haven't tried playing around with this myself)


BTW, IMHO, it is best to switch the number before firestarter in the the init.d script from 20 to higher, as mentioned above.
Would be nice to have this in the first post, at least as alternative, I guess.

---

### Post by nvteighen on 2007-11-08
Well, that's why it works for you, because you manually set up boot scripts.

The problem is that in Gutsy firestarter is placed now in a very high number, but if you reboot **without splash screen**, you'll notice that a non-fixed Firestarter will "[fail]" at loading. After this fix, "[OK]" is reported.

---

### Post by MegaJim on 2007-11-23
Just want to add my thanks for this... I had no idea that firestarter was failing to load on some of my boxes - I think this is due to ndiswrapper being somewhat broken in this kernel (so no matter how high a number you give it will always fail) - this fix is perfect, thanks.

---

### Post by ST.x on 2007-11-24
hmm, before I installed firestarter i ran sudo iptables -nL and I got:
```
 Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Then I installed firestarter(setup using config wizard) then rebooted and tried that command again and I get proper output with the iptables data. And the same result even when I start firestarter and run command again. So I guess I don't need the fix, I thought it was an issue in gutsy as well..

---

### Post by crjackson on 2007-12-01
Can someone tell just exactly what the "Lock Firewall" / "Unlock Firewall" does?

What is the purpose of either?

Thanks...

---

### Post by crjackson on 2007-12-01
Duhhh.... Never mind.  I found my answer...  Thanks

---

### Post by crjackson on 2007-12-01
I just tested my system on Shields Up! after configuring Firestarter.  I guess this means it's working properly...

---

### Post by nvteighen on 2007-12-01
> **crjackson said:**
> I just tested my system on Shields Up! after configuring Firestarter.  I guess this means it's working properly...
It's fine!

---

### Post by jis on 2008-04-27
Is ufw in Hardy supposed to replace firestarter?

---

### Post by nvteighen on 2008-04-27
> **jis said:**
> Is ufw in Hardy supposed to replace firestarter?
Good question. It sounds there is some research to be done!

---

### Post by crjackson on 2008-04-27
> **jis said:**
> Is ufw in Hardy supposed to replace firestarter?

Kind of.  It's not directly targeted at Firestarter though.  It's just a tool to make setting up the firewall (iptables) easier without having to add Firestarter or other configuration packages.

---

### Post by jis on 2008-04-27
New users would need a guide for configuring firewall, I guess.

---

### Post by crjackson on 2008-04-27
Turn on the firewall
```
sudo ufw enable
```

Turn off the firewall.
```
sudo ufw disable
```

Allow all connections by default.
```
sudo ufw default allow
```

Drop all connections by default.
```
sudo ufw default deny
```

Current status and rules.
```
sudo ufw status
```

Allow traffic on port <port>.
```
sudo ufw allow <port>
```

Block port number <port>
```
sudo ufw deny <port>
```

Block IP address.
```
sudo ufw deny from <ip>
```

---

### Post by Takmadeus on 2008-08-25
Thanks! your guide helped me fix the problem ;)

---

### Post by gb5757870 on 2008-12-20
> **jefferystone said:**
> nvteighen,

Thank you for the information.  Thankfully someone confirms what I've been saying.

I had an alternate solution - this would run firestarter after the networking was started.

[http://ubuntuforums.org/showthread.php?t=449319]("http://ubuntuforums.org/showthread.php?t=449319")

The solution in the quote worked for me too

---

### Post by Bambi_72 on 2009-01-12
Thanks for this, nor reassured that my iptable rules are being run.
You learn something new every day, if you're a linux newb, you learn SEVERAL new things every day!

---

### Post by blueshiftoverwatch on 2009-01-19
I followed the instructions that Nvteighen posted in the original thread 4 pages back. And when I start up my computer in text mode it says that it's starting up Firestarter.

But when I go into terminal and run **ps -e** to list all of the processes running I don't see anything resembling a firewall in the list. No Firestarter or iptables.

Am I doing something wrong?

---

### Post by scottuss on 2009-02-23
Yes it's a super old post, but thanks for this. Fixed my Firestarter problem on Arch Linux! :p

---

### Post by pro003 on 2009-07-14
> **nvteighen said:**
> But doesn't that starts the GUI? 

As I said before, you don't need to run the GUI... and according to some it may be also a bit dangerous to run something the whole time with root privileges.

You can call me crazy but I've been struggling with firestarter for months and the main problem is that 'he' applies given rules only when the gui mode is started. Otherwise it blocks everything.
I can tell that with 100/100 confidence.
One more thing. I don't think that every person or noob call it what you want - just wanted to see how firestarter is nice to look at its 'play button' icon *(maybe though someone does enjoys that ;p) but surely there are those who have problems with previously given rules that are not executed if THE GUI MODE of the FIRESTARTER IS NOT RUNNING!
 
Now, here's the BIG ONE. 

The makers or developers of Firestarter should change this behaviour, and let the main program run its GUI mode at startup (at least as an option available in preferences), but on the other hand when someone edits rules or try to delete the rules or make any changes while in GUI mode should AFTER THAT BE ASKED FOR ROOT PASSWD. 

And then everybody's happy as little penguins!  

And please stop this "You don't need to run firestarter's gui at startup!" 

P.S. While typing this I'm still trying to resolve this 'issue' with firestarter.

---

### Post by (((RADAR))) on 2009-10-03
> **pro003 said:**
> You can call me crazy but I've been struggling with firestarter for months and the main problem is that 'he' applies given rules only when the gui mode is started. Otherwise it blocks everything.
I can tell that with 100/100 confidence.
One more thing. I don't think that every person or noob call it what you want - just wanted to see how firestarter is nice to look at its 'play button' icon *(maybe though someone does enjoys that ;p) but surely there are those who have problems with previously given rules that are not executed if THE GUI MODE of the FIRESTARTER IS NOT RUNNING!
 
Now, here's the BIG ONE. 

The makers or developers of Firestarter should change this behaviour, and let the main program run its GUI mode at startup (at least as an option available in preferences), but on the other hand when someone edits rules or try to delete the rules or make any changes while in GUI mode should AFTER THAT BE ASKED FOR ROOT PASSWD. 

And then everybody's happy as little penguins!  

And please stop this "You don't need to run firestarter's gui at startup!" 

P.S. While typing this I'm still trying to resolve this 'issue' with firestarter.

Try this: > You can autostart Firestarter without having to enter a password (but it does involve a security compromise) using the following:

How to make Firestarter start automatically at startup
* System -> Preferences -> Sessions -> Startup Programs -> Add

sudo firestarter --start-hidden

* Press "OK"

How to have Firestarter start without the root password

Note: THIS IS NOT SECURE !!

In Terminal:
sudo visudo

• At the very bottom of the file add this line, USERNAME = your username:

  USERNAME ALL= NOPASSWD: /usr/sbin/firestarter

• Save and close the file
• Restart your computer
[Source]("http://ubuntuforums.org/showpost.php?p=3038499&postcount=15")

---

### Post by JohnnyJonJon on 2009-12-05
A much better way is to just add
```
sudo firestarter --start-hidden
```to /etc/rc.local before the "exit 0" line

Thats all.  Running this persistent with root privileges is only a security risk if the interface has a security issue that the cracker knows about... and knows your running firestarter.  From the outside it would only look like iptables with a rule set.

I don't like UFW... it has a monster rule set designed to "just work" with most networks and is bloated, inefficient and makes you detectable so not acceptable for a computer directly plugged into the Internet.  Maybe if your behind a hardware firewall and only concerned about your roomies and you want some connectivity but thats about it.

---

### Post by isaacd on 2010-07-23
I ran this howto on my laptop while and it was very useful. Thanks.

_**My main question is this:**_ I ran this while the laptop was hooked up to a clearwire modem (eth0). This laptop will also be hooking up to various WiFi networks. Do I need to go through the howto again for that?

Also, a general report:
I did the howto and everything worked fine. After running sudo iptables -nL I did indeed find that the firewall was not working as it should be. After running the how to, I did get a list of rules like I should by running sudo iptables -nL. The only weird thing was: after that, my internet connection from Firefox was stopped by the firewall. I opened firestarter and did some fiddling and I think that the way I fixed it was by going to Edit >> Preferences >> Interface >> Policy, and checking the "Apply Policy Changes Immediately" box. Interesting...

Regards,
Isaac.

---

### Post by kva on 2010-08-10
I see firestarter firewall [OK] from boot.log

/******************* boot.log **************/

fsck from util-linux-ng 2.17.2

/dev/sda1: clean, 160327/30154752 files, 2618351/120593152 blocks

 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox


[74G[ OK ]

 * Setting sensors limits       [80G 
[74G[ OK ]

 * Starting the Firestarter firewall...       [80G 
[74G[ OK ]

 [33m*[39;49m Speech-dispatcher configured for user sessions

 * Starting Common Unix Printing System: cupsd       [80G 

/******************************************/

Thanks, it works..

---


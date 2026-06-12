---
title: "Moblock (peerguardian linux alternative)"
date: 2006-06-08
forum: Outdated Tutorials &amp; Tips
---

### Post by pelle.k on 2006-06-08
> MoBlock and Peerguardian are both applications that enable you to block internet traffic based on large lists of ip address ranges in order to protect your privacy
[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)


**[COLOR="Red"]This HOWTO is moved to:[/COLOR]**
**[INDENT][https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) - i do not maintain it. feel free to edit as you like.[/INDENT]**

**[COLOR="Red"]Support thread maintained by JRE, the moblock maintainer.[/COLOR]**
**[INDENT][http://ubuntuforums.org/showthread.php?p=5016102](http://ubuntuforums.org/showthread.php?p=5016102)[/INDENT]**

---

### Post by pinoyskull on 2006-06-15
very nice guide, this will replace my old peerguardian installation :)

---

### Post by pinoyskull on 2006-06-15
i got an issue with moblock, the moblock.log says

---
error during nfq_create_queue()
Ranges loaded: 0
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'
**error during nfq_create_queue()**
Ranges loaded: 0
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'
---
i've highlighted the error

---

### Post by jamesford on 2006-06-15
can you tell me if this works with firestarter? last time i tried moblock and peerguardian it kept disabling my firewall

---

### Post by bionnaki on 2006-06-15
is this more stable than peerguardian?

---

### Post by bionnaki on 2006-06-15
how do you stop/restart moblock? how do you make exceptions for port 80?

---

### Post by pelle.k on 2006-06-15
**pinoyskull:** Are you using breezy? If so, you should install moblock-ipq instead...
If you are running a kernel > 2.6.15, could you run 'lsmod | grep NFQUEUE'.
Run 'sudo ls /etc/moblock'. I want to see if all files are there.

**jamesford:** I really don't know if it works alongside firestarter. It would be really nice if you (or somebody else) would try this as i have no need for a software firewall (i'm behind a hardware firewall ATM). Let me know, and i'll update my howto.

**bionnaki:** MoBlock is actively developed, PG for linux is not. I would say moblock is very easy to handle, and it has a nice and clean structure. You be the judge. I chose MoBlock because almost nothing is happening to PG linux ATM.
MoBlock has a whitelist at the top of /etc/moblock/MoBlock-nfq.sh. There you can add port 80 (80 which is http is already accepted for outgoing connectiond and their counterpart replys > in.)
About restarting moblock; it's in the howto, but anyway... 'sudo /etc/init.d/moblock-nfq restart'

**To all of you:**
I've been thinking of writing a GUI for MoBlock using python/ruby, which would handle starting/stopping, updating blocklist, live status and letting people cancel certain ips/ports from the blocklist.
It would be a tray app of course.

---

### Post by jamesford on 2006-06-15
well it doesent mess with firestarter but maybe thats cos moblock isnt blocking anything :( it doesent work.
there are no error messages in the log, appears to be running. but not blocking :(

---

### Post by smartalecks on 2006-06-15
thanks for the howto m8.
looking forward to the GUI, if you make it.

is there any equivalent to PG's "pgtext" and Monitor PG?

---

### Post by pelle.k on 2006-06-15
jamesford; could you 'tail -f /var/log/moblock.log' and connect to [http://relay.slayradio.org:8000/](http://relay.slayradio.org:8000/) using beep-media-player or whatever? I get blocked if I do. A couple of times at least, then i get connected from a different ip.
Also, if i'm not mistaken you can do sudo '/etc/init.d/moblock-nfq status'

---

### Post by jamesford on 2006-06-15
ur right, it does block it! and it also now block the other sites ive been trying (riaa.com etc)

ah now i get it, i just rebooted and hadnt started firestarter yet, and now ive started firestarter moblock blocks nothing again. so it seems that moblock eliminates firesterter and the toher way around (whichever app was last started overrules the other)

---

### Post by smartalecks on 2006-06-15
> **pelle.k]jamesford said:**
> http://relay.slayradio.org:8000/[/url] using beep-media-player or whatever? I get blocked if I do. A couple of times at least, then i get connected from a different ip.
Also, if i'm not mistaken you can do sudo '/etc/init.d/moblock-nfq status'

hoped but no :(

'sudo /etc/init.d/moblock-nfq' reports as only:

moblock-nfq start
moblock-nfq stop
moblock-nfq restart
moblock-nfq force-reload

---

### Post by jamesford on 2006-06-15
what does it mean when the log says skipping useless range ?
Skipping useless range: [www.68737075.com](www.68737075.com)
Skipping useless range: [www.neededware.com](www.neededware.com)
Skipping useless range: roings.com[Hijack-Spy]
Skipping useless range: [www.aaathemes.com](www.aaathemes.com)[Spy]
Skipping useless range: mymaydayinc.com[CWS]
for example

these wont be blocked ? and if so why not if they are in the bluetack blocklist?

---

### Post by gpogo on 2006-06-15
I'm having a similar issue.  Nothing is being blocked.
I am running Dapper Drake

```

ottoaim@jesse:~$ tail -f /var/log/moblock.log
Duplicated range ( ED2K Corru )
Duplicated range ( WinMx Fake )
Duplicated range ( ED2K Corrupt Data Senders )
Duplicated range ( ED2K Corru )
Duplicated range ( ED2K Virus )
Ranges loaded: 166915
Merged ranges: 187
Skipped useless ranges: 6407
NFQUEUE: binding to queue '0'
error during nfq_create_queue()
```

```
ottoaim@jesse:~$ lsmod | grep NFQUEUE
ipt_NFQUEUE             1920  0
ip_tables              23744  3 iptable_filter,ipt_NFQUEUE,ipt_state

```

```
ottoaim@jesse:~$ uname -a
Linux jesse 2.6.15-23-686 #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006 i686 GNU/Linux
```

if anyone has any idea I'd love to get this working

---

### Post by pelle.k on 2006-06-15
jamesford; useless ranges are usually duplicate ranges.
As for moblock and firestarter not working very well together, im no iptables guru, so i would let someone who knows iptables better than me point out what to do. The startup script is (with iptable rules), is as you probably know by now, in /etc/moblock/MoBlock-nfq.sh

gpogo; can't help you there. Theres something wrong with loading the correct modules i suspect. do 'dmesg | grep nfq' and 'dmesg | grep NFQ' (case sensetive...)

---

### Post by dom02 on 2006-06-15
great thanx a lot!  I've been looking for a linux alternative to peerguardian.

---

### Post by pinoyskull on 2006-06-16
[quote=pelle.k]
pinoyskull: Are you using breezy? If so, you should install moblock-ipq instead...
If you are running a kernel > 2.6.15, could you run 'lsmod | grep NFQUEUE'.
Run 'sudo ls /etc/moblock'. I want to see if all files are there.
[/quote]

1. Im running Dapper 

2. 
root@destiny:~# lsmod | grep NFQUEUE
ipt_NFQUEUE             1920  3 
ip_tables              23744  3 iptable_filter,ipt_NFQUEUE,ipt_stat
root@destiny:~# 


3. ls /etc/moblock
guarding.p2p  guarding.p2p.backup  MoBlock-nfq.sh


i did a reboot and found out that moblock is now working, i dont know what happened :)

---

### Post by smoove on 2006-06-16
> gpg --keyserver subkeys.pgp.net --recv DEDA0559
gpg --export --armor DEDA0559 | sudo apt-key add -

Hi do I just copy and paste that into sources.list? If so, Im getting erros in terminal:
 "Type ‘gpg’ is not known on line 34 in source list /etc/apt/sources.list"

---

### Post by pinoyskull on 2006-06-16
[QUOTE=smoove]Hi do I just copy and paste that into sources.list? If so, Im getting erros in terminal:
 "Type ‘gpg’ is not known on line 34 in source list /etc/apt/sources.list"[/QUOTE]

you have to enter that in the console like so

```
sudo gpg --keyserver subkeys.pgp.net --recv DEDA0559
sudo gpg --export --armor DEDA0559 | sudo apt-key add -
```
- the first command will pause for a bit, wait till it returns to the console then enter the 2nd one

---

### Post by pelle.k on 2006-06-16
smoove; No. gpg is a command line utility. So you should run it in a terminal, not put it in sources.list. I'll make it more obvious in the howto. thanks.

gpogo; I suggest you reboot your computer and check again, as pinoyskull did :)

pinoyskull; great to hear it resolved itself...

jamesford; You know what. Today, in the name of all that is good, i'll install firestarter and take a look at what iptable rules it spits out. Maybe i can solve this moblock/firestarter issue (if it's still a problem that is...)

---

### Post by pinoyskull on 2006-06-16
can moblock do a whitelisting?

---

### Post by smoove on 2006-06-16
Thanks, did that, but I cant find it to start it?
Got this error on 2nd part:

> 
gpg: WARNING: unsafe ownership on configuration file `/home/smoove/.gnupg/gpg.co nf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error


---

### Post by spockrock on 2006-06-16
ok its working how do allow connections on a port that amsn uses so I can use msn??  a connection over port 80 keeps giving me a wrong username password error, which is not right.... but I know the deb allows port 80 connections.

---

### Post by jamesford on 2006-06-16
i need the settings for permitting msn (gaim) too

EDIT:
found solution for gaim: tools > accounts >msn >modify > show more options > mark 'use http method'

---

### Post by spockrock on 2006-06-16
ok got it

first
```

sudo gedit /etc/moblock/MoBlock-nfq.sh
```

then find, 
WHITE_TCP_OUT="http https"

and amsn uses port 1863 so I changed it to this

WHITE_TCP_OUT="http https 1863"

then I simply did 

```

 sudo /etc/init.d/moblock-nfq restart

```

and I am now connected, able to send and receive messages. btw if anyone sees a problem with this plx feel free to point it out.

ok upon further investigation I found if I allow IN on 1863 I can get the full functionality such as nudges.  Also this method works only if the allow over http doenst work.  kept giving me a wrong username password error.

---

### Post by pelle.k on 2006-06-16
smoove; You are supposed to run gpg with sudo :)
[edit]Actually, gpg is supposed to be run without (not with) sudo... sorry about this post.[/edit]

---

### Post by pommattski on 2006-06-17
... looks good...

With regard to restarting moblock after updating the blocklist...  Is there any reason why the line, "sudo /etc/init.d/moblock-nfq restart" cannot be added to the end of the moblock-update script?

---

### Post by pelle.k on 2006-06-17
pommattski; You're absolutely correct. I did not add this because i want people to decide if rebootinbg the computer would be a better choice, as i dont know if restarting moblock leaves one unprotected for a second or two... But i'll add it (commented) to the update script so people can uncoment it on their own...

---

### Post by pommattski on 2006-06-17
Thanks Pelle.

On another point:
I'm using Kubuntu, and I found that I had to enter these lines WITHOUT sudo for them to work:
```

sudo gpg --keyserver subkeys.pgp.net --recv DEDA0559 
sudo gpg --export --armor DEDA0559 | sudo apt-key add -
```
(Still used sudo for "apt-key add -" though.)
WITH sudo I got errors about "unsafe ownership..." - the same as described by smoove.  (I also tried "kdesu" instead of sudo - no luck either)

... Otherwise, all is now working - and blocking - fine.

---

### Post by jamesford on 2006-06-17
ive kinda adjusted to the firestarter conflict now and starting to feel comfortable this way, running moblock

the tail thing is great, i didnt know about it until you pointed it out. is there a good way to get the tail output on desktop instaed of in a terminal ? ive tried 2 gdeslets and the tail command in conky, but they all use 100 % cpu and are unusable.

anyone know a better way?

---

### Post by pelle.k on 2006-06-17
OK fellas...
I know i've been kinda slow recently. Gonna do that GUI as soon as i get some time in front of my 'puter.
Yeah, that tail thingy is kindof neat. Since i discovered linux i've learned lots of nifty command line stuff like that. Highly recommend you get accustomized with the terminal.
Once my gui is done you will have access to live status of moblock. But right now i'm drinking some beverages (going out to meet some chicks, i suggest you do the same :) ), so that firestarter issue (and the GUI) will have to wait until sunday/monday i guess...
Have a nice 24 hours ;)

---

### Post by jamesford on 2006-06-17
looking forward to the gui, hope its trayable. and if not theres always alltray of course but always nicer with native tray support imo

---

### Post by Mechanical on 2006-06-17
If you make a gui to this program I will love you!  I was just testing it out and like it but of course would like it to be easier to manage.  Thanks for any time you put into it.

---

### Post by eXCeSS on 2006-06-19
Allowing port 80 you just add it into the "http https" thing to make "http htpps 80"?

Also, please make the gui!

---

### Post by jamesford on 2006-06-19
http=80

---

### Post by pelle.k on 2006-06-19
Just to clarify, as jamesfors said. http is the same as port 80. You can use regular names such as ftp http https instead of port numbers, if you want to.

Also i'm working on the GUI. Nothing fancy, but it will get you by.

---

### Post by jamesford on 2006-06-19
ive been playing with moblock for a while now, and using pelle's "quick'n'dirty blocklist update script", but theres also an update script inside /etc/cron.daily (well not anymore cos i deleted it) - why 2 update scripts ?

if you make a gui will we be able to pick what blocklists we want there? if so could there be a problem if i pick different blocklists than those listed in the script (which name escapes me) that is placed inside /etc/cron.daily ?

another thing, the gui, will there be a regular user part of the gui (just for viewing whats happening) and a root bit for making changes that require root privileges?
personally i think  entering a password in a popup window for making changes , and running the rest of the gui without root privileges is better than adding the gui app to the sudoers file, or having to enter passowrd at bootup if gui is set to run automaticly, but thats me.

sorry for dumb questions, im just wondering how you are planning to do it as im really looking forward to this :)

---

### Post by eXCeSS on 2006-06-20
[QUOTE=pelle.k]Just to clarify, as jamesfors said. http is the same as port 80. You can use regular names such as ftp http https instead of port numbers, if you want to.

Also i'm working on the GUI. Nothing fancy, but it will get you by.[/QUOTE]

Sweet, what's the ETA?

---

### Post by pelle.k on 2006-06-20
> but theres also an update script inside /etc/cron.daily
yikes! i didn't know about that! seriously :O There is really zero reference to that one in the documentation...
Oh well. I'll take a look at it. We cant have two of them can we ;)

About the GUI... normal user privileges should be enough for starting it up and monitoring logs etc. You will be able to choose blocklists to download and use.

The ETA for a draft is hopefully within 24 hours...

---

### Post by jamesford on 2006-06-22
*waiting* 
;)
:P

---

### Post by pelle.k on 2006-06-22
Sorry folks! I have the GUI running, i just need to get the update function working 100%
I'm one of those "i can't decide what DE to use" guys, so i've been rediscovering  plain ubuntu and xubuntu for a few days. That's why i haven't finished it yet but i'm working on it right now acctually.
Also, i have never really used ruby nor GTK before so this is kind of new to me. :)

---

### Post by smartalecks on 2006-06-22
Sounds good pelle :). Can't wait!

---

### Post by jamesford on 2006-06-22
take your time pelle :)

(ps u wont beat germany)

---

### Post by pinoyskull on 2006-06-22
way to go pelle, take your time :)

---

### Post by eXCeSS on 2006-06-25
Any updates? I'm anxious!

---

### Post by pelle.k on 2006-06-25
Well i'm getting there. I think i will have a beta for ya during monday. It will be without the advanced features, because those take time to program.
I also have an idea to implement fireHOL into the gui, to make it a blocker/firewall combo gui (as firestarter isn't very nice to moblock). I don't know yet. We'll see about that.

---

### Post by eXCeSS on 2006-06-25
Awesome!
Thanks a ton!

---

### Post by smoove on 2006-06-26
[QUOTE=pelle.k]smoove; You are supposed to run gpg with sudo :)
My wrong... i'll update the howto...[/QUOTE]


Sorry to sound like a complete n00blet, but what does that mean?

Should I just starting from the very beginning again?

---

### Post by smartalecks on 2006-06-26
you have to run it as the root user, so you would use sudo.

```
sudo gpg --keyserver subkeys.pgp.net --recv DEDA0559
sudo gpg --export --armor DEDA0559 | sudo apt-key add -
```

---

### Post by jamesford on 2006-06-26
sounds awesome pelle!

---

### Post by pelle.k on 2006-06-26
Hi.
I have edited that post about gpg. It's actually supposed to be run >without< sudo... :P
Yes i suck!
I'll be back shortly with a draft (ugly, quick'n'dirty code, no nicely formatted classes for now) of the GUI. It does work however. Just give me like 3-4 hours.

---

### Post by smartalecks on 2006-06-26
Take your time :D

---

### Post by pelle.k on 2006-06-26
This is the only sane way for me to let you have the GUI right now. I have stripped it of almost everything.
It is trayable, and it shows what is blocked. nothing more nothing less. But from what i understand, thats whats most important :)

[edit]File moved to howto (first post...)[/edit]

---

### Post by haani on 2006-06-27
[QUOTE=pelle.k]This is the only sane way for me to let you have the GUI right now. I have stripped it of almost everything, because in it's current state it's full of bugs. (or should i say, my ruby/gtk programming sucks).
It is trayable, and it shows what is blocked. nothing more nothing less. But from what i understand, thats whats most important :)

Seriously, yo mama could have done this but anyway. For now...
I've added a file as an attachment.
download it, extract it, and run the install.sh file (sudo ./install.sh). it should install the ruby script and the icon. you get no menu item, but i guess you are going to add this in you session startup anyway. run with moblock-simplegui or add it as a launcher, the icon is in /usr/share/pixmaps/moblock-gui.png. (dont laugh, i just cut'n'pasted it in 1 min...)

You'll need to "sudo apt-get install ruby libgtk2-ruby libgtk-trayicon-ruby" before you can run it.[/QUOTE]

thanks works gr8 but no too well under Xgl when i minimize it to tray and than maximize it, the program goes all wired with colours

---

### Post by pinoyskull on 2006-06-27
nice simple gui, are you gonna improve on it in the future? thanks again pelle

---

### Post by jamesford on 2006-06-27
well done, its a good foundation and something to build on i guess :)

my only little complaint about the gui in its current state is that there should be a way to have it start minimized (trayed)

---

### Post by smartalecks on 2006-06-27
very cool pelle, same ques as everyone else I suppose: are you going to keep on with it? 

It works great, I'm fine with it the way it is except that it says "Blocked out IP:s", instead of "IPs:"

I like it tho, shows that moblock is working. :) 

props to you

@haani:

I have xgl too, no problems minimizing.

---

### Post by sakis on 2006-06-27
Thank you very very very very much :D :D :D

---

### Post by manutremo on 2006-06-28
Not very original, but... thanks for the program. It works great!

---

### Post by ashrack on 2006-06-28
Just migrated from Win2k3 server to UBUNTU LINUX. 
In Win2k3 I was using PEERGUARDIAN but here MOBLOCK is in effect. 

My main concerne is since I'll be running this server 24/7 is with the problem of my FIRESTARTER firewall. I need it because it takes care of my INTERNET CONNECTION SHARING needs and its a very good Firewall.

Can Moblock coexist with FIrestarter firewall??

---

### Post by jamesford on 2006-06-28
ashrack, in my experience moblock and firestarter cancel eachother out. however if you run firesterter, set up all your rules and thetn reboot, with firestarter not set to run at startup (or possibly its enough just to exit firestarter and restart moblock) your firestarter rules will stick whil u will have a working moblock (until u start the firestarter gui again)

not tried with connection sharing though...so dont know if that will work

---

### Post by ashrack on 2006-06-28
Well if the only problem is when U start Firestarter GUI than thats not such a big problem. Had a similar problem in Win2k3 with PEERGUARDIAN and OUTPOST FW. Since OUTPUST had to be lunched first and PG second, else PG would work

---

### Post by jamesford on 2006-06-28
hmm i used outpost and peerguardian in xp too, i never had a problem, not that i can remember anyway, its been a while

---

### Post by pelle.k on 2006-06-28
Hey guys.
Yeah the GUI in it's present state isn't very "much", but as i said i'm working on the full version.
What you have right now is just "quick'n'dirty show me the log in a trayable window".

Moblock and fireHOL works fine together if you know what to add in the fireHOL configuration file. But fireHOL is a "iptable rules creator script", NO GUI, and thats why i figured i'd make a simple gui for that purpose as well.

---

### Post by jamesford on 2006-06-28
awesome pelle, cant wait for it! i really only use firestasrter to open torrernt ports etc, can firehol do the same?

---

### Post by ashrack on 2006-06-28
[QUOTE=jamesford]hmm i used outpost and peerguardian in xp too, i never had a problem, not that i can remember anyway, its been a while[/QUOTE]
then your a lucky man, its a well known bug between them

---

### Post by jamesford on 2006-06-28
outpost is/was one heck of a good firewall though, wasnt it? i kinda miss having that control in linux

---

### Post by ashrack on 2006-06-28
[QUOTE=jamesford]outpost is/was one heck of a good firewall though, wasnt it? i kinda miss having that control in linux[/QUOTE]
One of the best!!!

---

### Post by clessing on 2006-06-30
[QUOTE=jamesford]can you tell me if this works with firestarter? last time i tried moblock and peerguardian it kept disabling my firewall[/QUOTE]

Hi, I'm the gui who is maintaining [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/). ;-)

Please have a look at the scripts in /etc/firestarter. There are two interesting files "user-pre" and "user-post" to customize firestarter. 

You should be able to get moblock and firestarter working together if you disable the iptables stuff in /etc/moblock/MoBlock-....sh and add those rules to the firestarter scripts.

Make sure that the moblock rules grab the traffic before firestarter does :-)

---

### Post by sprucio on 2006-06-30
Sorry. Wrong post.

---

### Post by Mechanical on 2006-06-30
I have a question about updating.  First of all, I was using the list pelle.k had made and included up until now in the manual.  Now we have discovered another way to update the lists, yet in 'sudo nano /etc/cron.daily/moblock-nfq' there doesn't seem to be a mention for a p2p file.  There is the ad blocking and bad porn stuff, but I am usually used to seeing a p2p file which I figured was the most important part of blocking out the baddies.  Just wondering, and hope to see more of the gui soon, thanks.

---

### Post by clessing on 2006-07-01
[QUOTE=Mechanical]  There is the ad blocking and bad porn stuff, but I am usually used to seeing a p2p file which I figured was the most important part of blocking out the baddies.  Just wondering, and hope to see more of the gui soon, thanks.[/QUOTE]
Please see [http://www.bluetack.co.uk/forums/index.php?autocom=faq&CODE=02&qid=18](http://www.bluetack.co.uk/forums/index.php?autocom=faq&CODE=02&qid=18) and
[http://www.bluetack.co.uk/config/](http://www.bluetack.co.uk/config/)
and especially [http://www.bluetack.co.uk/modules.php?name=FAQ&myfaq=yes&id_cat=6&categories=Blacklists+FAQ](http://www.bluetack.co.uk/modules.php?name=FAQ&myfaq=yes&id_cat=6&categories=Blacklists+FAQ)

Especially level1 and level2 are anti p2p.

If you think that there is a list that should be included per default in the moblock package or if any of you has improvements for scripts in this package, feel free to contact me.

I know that I have to spend time and work on them but at the moment time is a problem... :-)

---

### Post by clessing on 2006-07-01
[QUOTE=gpogo]I'm having a similar issue.  Nothing is being blocked.
I am running Dapper Drake

```

ottoaim@jesse:~$ tail -f /var/log/moblock.log
NFQUEUE: binding to queue '0'
error during nfq_create_queue()
```

```
ottoaim@jesse:~$ lsmod | grep NFQUEUE
ipt_NFQUEUE             1920  0
ip_tables              23744  3 iptable_filter,ipt_NFQUEUE,ipt_state

```

if anyone has any idea I'd love to get this working[/QUOTE]

The script in /etc/init.d is not perfect. In some cases you may end up with two instances of moblock, the second one will be unable to bind to the queue.

You may try to killall moblock-nfq and to /etc/init.d/moblock-nfq start.

Maybe this solves your problem.

---

### Post by clessing on 2006-07-01
[QUOTE=pelle.k]pommattski; You're absolutely correct. I did not add this because i want people to decide if rebootinbg the computer would be a better choice, as i dont know if restarting moblock leaves one unprotected for a second or two... But i'll add it (commented) to the update script so people can uncoment it on their own...[/QUOTE]
"/etc/init.d/moblock-nfq reload" does this without leaving you unprotected.
This is the same as killall -HUP moblock-nfq. It reloads the blocklist without quitting moblock.
The command mentioned above is also used by the daily update script.

---

### Post by haani on 2006-07-01
[QUOTE=clessing]Hi, I'm the gui who is maintaining [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/). ;-)

Please have a look at the scripts in /etc/firestarter. There are two interesting files "user-pre" and "user-post" to customize firestarter. 

You should be able to get moblock and firestarter working together if you disable the iptables stuff in /etc/moblock/MoBlock-....sh and add those rules to the firestarter scripts.

Make sure that the moblock rules grab the traffic before firestarter does :-)[/QUOTE]

someone please tell me how to configure firestarter so that it can work with moblock in detail thanks

---

### Post by neev on 2006-07-01
Hello!! Sorry if it is a very basic question, but how do i get moblock installed?? Im newbie with linux so most of the things i do is basically read and try to follow steps but i cannot get it with moblock. Ive followed the steps in the 1st page of the topic but i get an error. When i do sudo apt-get update it says it cannot find  [http://moblock-deb.sourceforge.net/debian/dists/unstable/Release](http://moblock-deb.sourceforge.net/debian/dists/unstable/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?).

What am i doing wrong?? Any help is much appreciated,

sorry about my english!! and thanks a lot!!

---

### Post by clessing on 2006-07-01
[QUOTE=haani]someone please tell me how to configure firestarter so that it can work with moblock in detail thanks[/QUOTE]
I don't use it and I don't intend to use it.... but looking at the scripts in /etc/firestarter I can say, that firestarter deletes all existing firewall rules when  setting up its own rules.
So you have to open /etc/moblock/MoBlock-nfq.sh with your favourite text editor:

Find the line
/usr/bin/moblock $@

Everything before this line goes into /etc/firestarter/user-pre

Leave /etc/moblock/Moblock-nfq.sh unmodified.

Doing so should cause firestarter to insert the iptables rules that moblock uses under normal circumstances before its own rules.

---

### Post by clessing on 2006-07-01
[QUOTE=neev][http://moblock-deb.sourceforge.net/debian/dists/unstable/Release](http://moblock-deb.sourceforge.net/debian/dists/unstable/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?).
![/QUOTE]

I haven't compiled a version for amd64. Please google a bit to find out whether you can install debian packages for 32bit processors - I really don't know.

---

### Post by pelle.k on 2006-07-02
Thanks clessing! :)
Now try this out people, so i can add it to the howto... :D

---

### Post by haani on 2006-07-02
[QUOTE=clessing]I don't use it and I don't intend to use it.... but looking at the scripts in /etc/firestarter I can say, that firestarter deletes all existing firewall rules when  setting up its own rules.
So you have to open /etc/moblock/MoBlock-nfq.sh with your favourite text editor:

Find the line
/usr/bin/moblock $@

Everything before this line goes into /etc/firestarter/user-pre

Leave /etc/moblock/Moblock-nfq.sh unmodified.

Doing so should cause firestarter to insert the iptables rules that moblock uses under normal circumstances before its own rules.[/QUOTE]

doesnt work firestarter says that it can't connect/start!! when i remove the text from /etc/firestarter/user-per than it works!! so i am thinkin that there is no way of workin moblock and firestarter together??

---

### Post by clessing on 2006-07-03
[QUOTE=haani]doesnt work firestarter says that it can't connect/start!! when i remove the text from /etc/firestarter/user-per than it works!! so i am thinkin that there is no way of workin moblock and firestarter together??[/QUOTE]

ok, you have to leave out the
```

if [ -f $PIDF  ]; then
        PID=`cat $PIDF`
        if [ `ps -p $PID|wc -l` -gt 1 ]; then
                echo "$0: $PIDF exists and processs seems to be running. Exiting."
                exit 1;
        fi;
fi;

```
I thought that's obvious.

I did what I never wanted: spending time on firestarter ;-) Leaving out the lines above just works fine. The firestarter firewall is being build up and moblock starts blocking things. I tested it.

Here's the file user-pre for copy & paste:
```

#!/bin/sh
#
# MoBlock.sh - MoBlock start script
# ---------------------------------

ACTIVATE_CHAINS=1
WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT="http https 1863"
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""


PIDF=/var/run/moblock.pid

FNAME=`basename $0 .sh`
MODE=`echo $FNAME|awk -F-  '{print $2}'`

if [ -f /usr/bin/moblock-ipq ]; then
	modprobe ip_queue
	TARGET="QUEUE"
elif [ -f /usr/bin/moblock-nfq ]; then
	modprobe ipt_NFQUEUE
	TARGET="NFQUEUE"
fi;

modprobe ipt_state

# Filter all traffic, edit for your needs

iptables -N MOBLOCK_IN
iptables -N MOBLOCK_OUT
iptables -N MOBLOCK_FW

if [ $ACTIVATE_CHAINS -eq 1 ]; then
	iptables -I INPUT -p all -m state --state NEW -j MOBLOCK_IN
	iptables -I OUTPUT -p all -m state --state NEW -j MOBLOCK_OUT
	iptables -I FORWARD -p all -m state --state NEW -j MOBLOCK_FW	
fi;


iptables -I MOBLOCK_IN -p all -j $TARGET
#iptables -I MOBLOCK_IN -m state --state ESTABLISHED,RELATED -j ACCEPT 

iptables -I MOBLOCK_OUT -p all -j $TARGET
#iptables -I MOBLOCK_OUT -m state --state ESTABLISHED,RELATED -j ACCEPT 

iptables -I MOBLOCK_FW -p all -j $TARGET
#iptables -I MOBLOCK_FW -m state --state ESTABLISHED,RELATED -j ACCEPT 

for PORT in $WHITE_TCP_OUT; do
	iptables -I MOBLOCK_OUT -p tcp --dport $PORT -j ACCEPT
done
for PORT in $WHITE_UDP_OUT; do
	iptables -I MOBLOCK_OUT -p udp --dport $PORT -j ACCEPT
done

for PORT in $WHITE_TCP_IN; do
	iptables -I MOBLOCK_IN -p tcp --dport $PORT -j ACCEPT
done
for PORT in $WHITE_UDP_IN; do
	iptables -I MOBLOCK_IN -p udp --dport $PORT -j ACCEPT
done

for PORT in $WHITE_TCP_FORWARD; do
	iptables -I MOBLOCK_FW -p tcp --dport $PORT -j ACCEPT
done
for PORT in $WHITE_UDP_FORWARD; do
	iptables -I MOBLOCK_FW -p udp --dport $PORT -j ACCEPT
done


# Loopback traffic fix

iptables -I INPUT -p all -i lo -j ACCEPT
iptables -I OUTPUT -p all -o lo -j ACCEPT


```

There is just one problem left: AFAIK, if traffic is put into moblock's queue and moblock (or any other program that uses the same interface) decides that the package is accepted, it is accepted. Period. (Same as -j ACCEPT when using iptables, no possibility to use something similar to -j RETURN which enables the package to traverse the remaining rules of the firewall to be checked there, too)

So using what I posted above means putting moblock in front of firestarter, effectively leaving firestarter's rules unused because moblock is filtering everything.
You can only use firestarter to watch open connections :-)


You can fix part of this problem by putting all stuff into the file user-post, leaving user-pre empty and by replacing 
```

if [ $ACTIVATE_CHAINS -eq 1 ]; then
	iptables -I INPUT -p all -m state --state NEW -j MOBLOCK_IN
	iptables -I OUTPUT -p all -m state --state NEW -j MOBLOCK_OUT
	iptables -I FORWARD -p all -m state --state NEW -j MOBLOCK_FW	
fi;

```
by
```

if [ $ACTIVATE_CHAINS -eq 1 ]; then
	iptables -A INPUT -p all -m state --state NEW -j MOBLOCK_IN
	iptables -A OUTPUT -p all -m state --state NEW -j MOBLOCK_OUT
	iptables -A FORWARD -p all -m state --state NEW -j MOBLOCK_FW	
fi;
```

But this only replaces the problem by another: now firestarter is in charge and if firestarter decides that a packages is to be accepted, it may do so without consulting moblock.


This is one of the reasons for which on sourceforge.net I categorized moblock as software for "advanced end users": you should know how to use iptables before you use moblock. You can do without as per default the package blocks things. But if you want to integrate it in another firewall you need to know, what is going on.

I you are brave and grok the iptables documentation you can insert the moblock chains into firestarter's rules at exactly the places that make sense in your individual case.

It may make sense to use 
```

if [ $ACTIVATE_CHAINS -eq 1 ]; then

	iptables -A INBOUND -p all -m state --state NEW -j MOBLOCK_IN

	#where in output?
	OLINE=$((`iptables -L OUTBOUND|wc -l` - 2 ))
	iptables -R OUTBOUND $OLINE -p all -m state --state NEW -j MOBLOCK_OUT

	iptables -A FORWARD -p all -m state --state NEW -j MOBLOCK_FW	
fi;

```
in the file user-post.
But I cannot guarantee that it does what you want.

The moral of this story is: You are not secure if you don't know what your firewall does. Even if you do, you may be not secure, but it's better than the first case.

---

### Post by jamesford on 2006-07-03
are u still planning on a moblock/firehol combo thingy?

---

### Post by smoove on 2006-07-03
[QUOTE=smartalecks]you have to run it as the root user, so you would use sudo.

```
sudo gpg --keyserver subkeys.pgp.net --recv DEDA0559
sudo gpg --export --armor DEDA0559 | sudo apt-key add -
```[/QUOTE]

Still struggling with this lol:

gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

---

### Post by bigdon06 on 2006-07-04
I've got a predicament. I would like to be running moblock and still be able to run all of my web based programs and games. It is inevitable that every time I update the list it puts ranges back in that I don't want. Is there a way to set up exemptions, kind of in the way of peer guardians permallow.p2b? It certainly gets old digging through the blocklist all of the time and removing the same stuff.:confused:

---

### Post by clessing on 2006-07-04
[QUOTE=bigdon06]I would like to be running moblock and still be able to run all of my web based programs and games. [/QUOTE]

Moblock itself has no whitelisting functionality.

But if it's all about surfing I suggest that you

put WHITE_TCP_OUT="http https" into your moblock start script in /etc/moblock. But that's there by default so you shouldn't have a problem surfing.
Another possibility to whitelist ips is to put something like

iptables -I OUTPUT -d a.b.c.d -j ACCEPT
or
iptables -I OUTPUT -d a.b.c.0/24 -j ACCEPT

into your firewall (first example is a single ip, second example is a net with netmask)

---

### Post by pelle.k on 2006-07-09
Hi. I just wanted to say i have no time to spare to make a complete moblock GUI, because i am currently working all day long, 6 days a week. Sorry about that. Hopefully someone else have the time to code a decent GUI before i have time to do so...

About whitelisting certain ips... You would only have to write a simple bash/python script to remove those ips/ranges, and execute it after a succesfull update of the blocklist.

---

### Post by mikji on 2006-07-09
Hi folks,

I don't really post here that much (long time lurker), but I see you're looking for a moblock gui! Well, I've been working on one in gnome-python for the past few days, and it's about half done. I ran across this thread and thought I'd let you guys know about it so you don't duplicate work.

It'll have a dbus daemon, a notification applet and a preferences item. The first is mostly done, the second is trivial and I haven't gotten started on the last part.

I'll start a new thread when my sourceforge project is approved and I release something (a few days to a week).

Here are some screenshots; the first one is of the preference panel, and the second one is what you get when you click the notification icon.

---

### Post by clessing on 2006-07-10
> **mikji said:**
> Hi folks,

I don't really post here that much (long time lurker), but I see you're looking for a moblock gui! Well, I've been working on one in gnome-python for the past few days, and it's about half done. I ran across this thread and thought I'd let you guys know about it so you don't duplicate work.

Looks great. Please drop me a line when you're releasing it. I'd love to provide debian packages along with the moblock-deb stuff if you don't mind. :-)

---

### Post by jamesford on 2006-07-10
bah so it doesent work on 64 bit? i was planning to install 64 bit ubuntu tonight :/

is there and chance there will be a 64 bit version at some stage in the not too distant future ? or are there any alternative programs that does the same and works on 64 bit?

---

### Post by clessing on 2006-07-11
> **jamesford said:**
> 

is there and chance there will be a 64 bit version at some stage in the not too distant future ? or are there any alternative programs that does the same and works on 64 bit?

You should be able to compile moblock and build the package on 64bit. (have a look at "apt-get source", "apt-get build-dep" and "dpkg-buildpackage").

At the moment I can't afford the time to work on the package let alone setting up a cross-compiling environment to build 64bit packages.

However, chances are, that I will do this in September/October.

---

### Post by Sammy1 on 2006-07-11
> **mikji said:**
> Hi folks,

I don't really post here that much (long time lurker), but I see you're looking for a moblock gui! Well, I've been working on one in gnome-python for the past few days, and it's about half done.

Sweet man, that will be invaulable.

---

### Post by olnir on 2006-07-12
> **pelle.k said:**
> **pinoyskull:** Are you using breezy? If so, you should install moblock-ipq instead...
If you are running a kernel > 2.6.15, could you run 'lsmod | grep NFQUEUE'.
Run 'sudo ls /etc/moblock'. I want to see if all files are there.

**jamesford:** I really don't know if it works alongside firestarter. It would be really nice if you (or somebody else) would try this as i have no need for a software firewall (i'm behind a hardware firewall ATM). Let me know, and i'll update my howto.

**bionnaki:** MoBlock is actively developed, PG for linux is not. I would say moblock is very easy to handle, and it has a nice and clean structure. You be the judge. I chose MoBlock because almost nothing is happening to PG linux ATM.
MoBlock has a whitelist at the top of /etc/moblock/MoBlock-nfq.sh. There you can add port 80 (80 which is http is already accepted for outgoing connectiond and their counterpart replys > in.)
About restarting moblock; it's in the howto, but anyway... 'sudo /etc/init.d/moblock-nfq restart'

**To all of you:**
I've been thinking of writing a GUI for MoBlock using python/ruby, which would handle starting/stopping, updating blocklist, live status and letting people cancel certain ips/ports from the blocklist.
It would be a tray app of course.

Moblock works alongside firestarter.
Moblock has to be started after firestarter for some reason.
I have to manually restart moblock after I have started Firestarter.
After that, it seems to work just fine.

---

### Post by clessing on 2006-07-12
> **olnir said:**
> Moblock works alongside firestarter.
Moblock has to be started after firestarter for some reason.
I have to manually restart moblock after I have started Firestarter.
After that, it seems to work just fine.
Yes, but if you don't find a way to insert moblock at the right place into the firewall (see my previous posts) firestarter is useless except for watching connections.

---

### Post by jamesford on 2006-07-13
clessing im having severe problems making an amd64 package, ive never done this before. i dont even know what to do, so i tried as follows and got the following error:
sudo apt-get source moblock-nfq
Reading package lists... Done
Building dependency tree... Done
E: Could not open file /var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_unstable_main_source_Sources - open (2 No such file or directory)

a bit more help would be appreciated :)

---

### Post by mikji on 2006-07-13
My project is started at sf.net/projects/gnome-blocklist. The only thing interesting on there ATM is the svn repo, which you can check as I develop this thing.

Feel free to send me patches and suggestions, but as of this post it's not in a working state yet. Right now there is a dbus daemon which takes commands from a simple client. That's it.

---

### Post by clessing on 2006-07-14
> **jamesford said:**
> clessing im having severe problems making an amd64 package, ive never done this before. i dont even know what to do, so i tried as follows and got the following error:


You need ```

deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main

```
in /etc/apt/sources.list
Then do a "apt-get update".
After that you need to verify that you have all the tools to build the package:
"apt-get build-dep moblock-ipq" or
"apt-get build-dep moblock-nfq" depending on the package you want to build.

If that succeeds you can descend into the source directory:
These commands should get you towards the goal:

mkdir moblock
cd moblock
apt-get source moblock
cd moblock-0.8
dpkg-buildpackage -rfakeroot

If everything went right, you should have a .deb file.

However, you may need to do the same for the packages libnetfilter-queue and libnfnetlink before. These library packages produce two .deb files. You should install the library-package as well as the library-dev packages. (e.g. libnetfilter-queue and libnetfilter-queue-dev)

---

### Post by jamesford on 2006-07-14
clessing, i sucessfully installed the libnetfilter-queue and libnfnetlink thingies

however with moblock itself:

Failed to fetch [http://moblock-deb.sourceforge.net/debian/dists/unstable/main/source/net/moblock_0.8.orig.tar.gz](http://moblock-deb.sourceforge.net/debian/dists/unstable/main/source/net/moblock_0.8.orig.tar.gz)  404 Not Found
E: Failed to fetch some archives.

is some package missing in the repository, or am i doing something wrong?

---

### Post by clessing on 2006-07-14
> **jamesford said:**
> 
[http://moblock-deb.sourceforge.net/debian/dists/unstable/main/source/net/moblock_0.8.orig.tar.gz](http://moblock-deb.sourceforge.net/debian/dists/unstable/main/source/net/moblock_0.8.orig.tar.gz)  404 Not Found
E: Failed to fetch some archives.



Yes, that's really my fault (or that of debarchiver). It was really missing there and it's uploaded now.
Sorry for the inconvenience.

---

### Post by jamesford on 2006-07-14
ah thanks.
however now i ran into another problem, or maybe its just me, sorry i find this confusing especially since its been a few hours since i managed to set up the files mentioned above

anyway i get this error:

make[1]: Entering directory `/home/XXX/moblock/moblock-0.8'
gcc -DLIBIPQ -Wall -O2 -march=i586  -fomit-frame-pointer -ffast-math -D_GNU_SOURCE   -I/usr/include/libipq -c -o  MoBlock-ipq.o MoBlock.c
MoBlock.c:1: error: CPU you selected does not support x86-64 instruction set
MoBlock.c:1: error: CPU you selected does not support x86-64 instruction set
make[1]: *** [MoBlock-ipq.o] Error 1
make[1]: Leaving directory `/home/XXX/moblock/moblock-0.8'
make: *** [build-stamp] Error 2

btw is this the ipq or nfq version ? or both? how do i choose?

---

### Post by clessing on 2006-07-15
> **jamesford said:**
> 
MoBlock.c:1: error: CPU you selected does not support x86-64 instruction set

btw is this the ipq or nfq version ? or both? how do i choose?
It's the package's fault. I thought that I already had removed the optimization for i586.

A new package is being uploaded at the moment. You should refetch the source and compile molbock-ipq / moblock-nfq again. Should work now.

Building the moblock-source from my repository results in both packages. (You will have two .deb files afterwards.)

Thanks for finding a bug! ;-)

---

### Post by jamesford on 2006-07-15
wahey it works :D
thanks for your help clessing
it wasnt really difficult either as long as the correct files are in the repository ;)

---

### Post by Phil196949 on 2006-07-15
I have been using Ubuntu for only a few week. When I try to apt-get moblock it gives me these errors...
 moblock-nfq: Depends: lsb-base (>= 3.0-3) but 3.0-1ubuntu8 is to be installed

Where can I find these packages? thanks

---

### Post by jamesford on 2006-07-15
Phil196949
did u install dapper (ubuntu 6.06)?

as far as i can see 3.0-1ubuntu8 is only abailable in breezy, which is the old ubuntu version

dapper uses 3.1-5ubuntu2

---

### Post by Phil196949 on 2006-07-15
Hey thanks! I got it going. I was wondering why I was getting so many errors
when compiling packages. Now I am enlightened! :D

---

### Post by Nonninz on 2006-07-15
Hi. Many thanks for the guide. :D 

A question: is there some way to make a fixed "Whitelist", as with Peerguardian on Windows?

---

### Post by clessing on 2006-07-16
> **Nonninz said:**
> Hi. Many thanks for the guide. :D 

A question: is there some way to make a fixed "Whitelist", as with Peerguardian on Windows?
[http://ubuntuforums.org/showthread.php?p=1213534#post1213534](http://ubuntuforums.org/showthread.php?p=1213534#post1213534)

That's what the search function is for.

---

### Post by c0ugar on 2006-07-18
Hello all,

> **pelle.k said:**
> Moblock and fireHOL works fine together if you know what to add in the fireHOL configuration file. But fireHOL is a "iptable rules creator script", NO GUI, and thats why i figured i'd make a simple gui for that purpose as well.

Has anyone set up firehol to work with moblock? Does anyone know what needs to be added to firehol configuration? When I used PeerGuardian, I had to change all ACCEPTS in firehol's configuration file to PEERGUARDIAN and I had to create a PEERGUARDIAN chain. IE:

```

# PeerGuardian Configuration (Must be in place for PeerGuardian to receive packets)
iptables --new PEERGUARDIAN 
iptables -A PEERGUARDIAN -j QUEUE

server "dhcp dns ssh samba ntp ping" PEERGUARDIAN

```

Now I'm wondering if I need to do the same in order to get firehol and MoBlock to coexist nicely.

Further information on running PeerGuardian and FireHOL together can be found here. [http://forums.phoenixlabs.org/t11437-solution-for-firehol-amp-peerguardian.html](http://forums.phoenixlabs.org/t11437-solution-for-firehol-amp-peerguardian.html)

Thanks in advance,

---

### Post by jms830 on 2006-07-18
does anyone know if moblock works with guarddog firewall? or if there are any hitches to get them to work together? i don't know how to test if they are working together. Also, how do I even test moblock? I'm running 'tail -f /var/log/moblock.log' but nothings happening.

---

### Post by clessing on 2006-07-19
> **jms830 said:**
> Also, how do I even test moblock? I'm running 'tail -f /var/log/moblock.log' but nothings happening.

You should be able to do so by pinging a blocked host. E.g. a microsoft web server, etc. 
Example output:
```

Blocked OUT: Nederlands Forensisch Instituut,hits: 1,DST: 195.169.99.137
Blocked OUT: Nederlands Forensisch Instituut,hits: 2,DST: 195.169.99.137
Blocked OUT: Nederlands Forensisch Instituut,hits: 3,DST: 195.169.99.137
Blocked OUT: Case Western Reserve University fakes,hits: 1,DST: 129.22.247.172

```

A statement that is valid for all those firewall tools and scripts out there, no exceptions:
You have to adapt _each_ firewall tool/script by hand in order to get it working properly with moblock or peerguardnf.
Just starting both will not result in a setup that makes sense.
You have to understand how to use [iptables]("http://www.netfilter.org/") to do this.
Or you have to find someone who does. I will restructure the moblock package scripts towards September/October which may include the integration of popular firewall tools. Unfortunately, I'm way to busy to do this earlier.

---

### Post by clessing on 2006-07-19
> **c0ugar said:**
> 
```

# PeerGuardian Configuration (Must be in place for PeerGuardian to receive packets)
iptables --new PEERGUARDIAN 
iptables -A PEERGUARDIAN -j QUEUE

server "dhcp dns ssh samba ntp ping" PEERGUARDIAN

```

Now I'm wondering if I need to do the same in order to get firehol and MoBlock to coexist nicely.
If this worked with peerguardnf, it should work with moblock-ipq. If you're using moblock-nfq, use 
```
iptables -A PEERGUARDIAN -j NFQUEUE
```
In both cases, have a look at  /etc/moblock/MoBlock-nfq.sh, though.
If firehol is being startet after moblock, it should not be a problem as long as firehol deletes all iptables stuff on startup.

---

### Post by laytoncy on 2006-07-20
> **clessing said:**
> Moblock itself has no whitelisting functionality.

But if it's all about surfing I suggest that you

put WHITE_TCP_OUT="http https" into your moblock start script in /etc/moblock. But that's there by default so you shouldn't have a problem surfing.
Another possibility to whitelist ips is to put something like

iptables -I OUTPUT -d a.b.c.d -j ACCEPT
or
iptables -I OUTPUT -d a.b.c.0/24 -j ACCEPT

into your firewall (first example is a single ip, second example is a net with netmask)

I've been following this thread and have MoBlock running along with Azureus and it works like a champ.  I'm having trouble whitelisting an IP.  I tried the above example "iptables -I OUTPUT -d a.b.c.d -j ACCEPT" and put that in my MoBlock-nfq.sh.  Now I know it says insert in a firewall but will it work in the startup script because I'm not running a software firewall?  If you can put it in the script is there a particular place that it should be inserted?

---

### Post by clessing on 2006-07-20
> **laytoncy said:**
> If you can put it in the script is there a particular place that it should be inserted?

I'd suggest, that you edit /etc/moblock/MoBlock-nfq.sh and put

```
iptables -I MOBLOCK_OUT -d a.b.c.0/24 -j ACCEPT
```
just before 
```

/usr/bin/moblock $@
```

That should work.

/etc/moblock/MoBlock-nfq.sh is used by the startup scripts in /etc/init.d to start moblock.

To all: I've put a note on the moblock-deb homepage at sourceforge that I'll be away until the 18th of August. "Away" will much likely include also the access to the internet. So I will not respond to posts and emails during the next weeks.

---

### Post by laytoncy on 2006-07-20
Thank you!  That did it. :mrgreen:

---

### Post by glycerin on 2006-07-22
> **clessing said:**
> I will restructure the moblock package scripts towards September/October which may include the integration of popular firewall tools. Unfortunately, I'm way to busy to do this earlier.

I am using Ubuntu 6.06 and Firestarter 1.03. Before I can begin downloading torrents with Azureus I must have the protection of the PeerGuardian lists.

Is the ONLY way to have this happen is to wait for "clessing" to update MoBlock so that it works alongside Firestarter? It would be unfortunate to have to wait a few months since I just bought a server for this and want to try it out ASAP.

Maybe there's something I can do temporarily in the meantime? Can I add the PeerGuardian lists directly to Firestarter?

---

### Post by c0ugar on 2006-07-25
> **clessing said:**
> If this worked with peerguardnf, it should work with moblock-ipq. If you're using moblock-nfq, use 
```
iptables -A PEERGUARDIAN -j NFQUEUE
```
In both cases, have a look at  /etc/moblock/MoBlock-nfq.sh, though.
If firehol is being startet after moblock, it should not be a problem as long as firehol deletes all iptables stuff on startup.

Okay. I did this, and all network traffic was disabled. Local SSH sessions were disconnected, etc. Not sure exactly how to get MoBlock to work with fireHOL but I'm with another guy, it will suck if we need to wait a month or 2 for this to be worked out. I wouldn't mind getting on IRC and working with others to solve this problem. Altho my time is limited because I work nights, I'd be willing to take a crack at it.

I understand clessing will be away but why wait for him?

---

### Post by foxy123 on 2006-07-25
what should I whitelist to unblock a local network?

---

### Post by boast on 2006-07-27
How do you use the GUI? When I click on the accesories>moblock simplegui   nothing happens.

---

### Post by Daniel15 on 2006-07-29
Hi guys, just a quick question:
If I have my own iptables rules (created using Webmin), will this overwrite them? How can I make both MoBlock, and my own iptables rules run at the same time?

---

### Post by c0ugar on 2006-07-29
> **Daniel15 said:**
> Hi guys, just a quick question:
If I have my own iptables rules (created using Webmin), will this overwrite them? How can I make both MoBlock, and my own iptables rules run at the same time?

Bro you gotta read this thread before posting. It's been stated that there is no defined answer to your question, and other questions that are alike.

If MoBlock is launched after your firewall manager, such as web admin, MoBlock super-cedes anything else. Clessing when he gets back from his personal time off will hopefully define these answers for us.

In the mean time, all you can do is wait or attempt your own work around - Which involves editing MoBlock and WebAdmin. Same with FireHol and FireStarter, etc.

---

### Post by foxy123 on 2006-07-29
It looks like Moblocks blocks my local network traffic. Is there any way to allow traffic from the computers which are in my local network?

---

### Post by ba5e on 2006-07-29
when I click on the 'moblock simplegui' in accessories I get nothing! installed all relevant dependencies too. Any ideas?

---

### Post by ba5e on 2006-07-29
> **ba5e said:**
> when I click on the 'moblock simplegui' in accessories I get nothing! installed all relevant dependencies too. Any ideas?
UPDATE: I get the followign running moblock-simplegui from the terminal

willmc@willbuntu:~$ moblock-simplegui
/usr/bin/moblock-simplegui:66:in `initialize': Failed to open file '/usr/share/pixmaps/moblock-gui.png': Permission denied (GLib::FileError)
        from /usr/bin/moblock-simplegui:66

---

### Post by c0ugar on 2006-07-29
> **foxy123 said:**
> It looks like Moblocks blocks my local network traffic. Is there any way to allow traffic from the computers which are in my local network?

MoBlock like PeerGuardian, runs by default on all interfaces. I do not believe this can be configured to only run on the 'internet' interface. I believe it is developed that way in order to prevent computers on a LAN from contacting malicious sites, etc. It would defeat the purpose other wise.

---

### Post by foxy123 on 2006-07-30
> **c0ugar said:**
> MoBlock like PeerGuardian, runs by default on all interfaces. I do not believe this can be configured to only run on the 'internet' interface. I believe it is developed that way in order to prevent computers on a LAN from contacting malicious sites, etc. It would defeat the purpose other wise.

so is there any solutiion to that? Any way to whitelist certain ips maybe?

---

### Post by HBK on 2006-07-30
> **ba5e said:**
> UPDATE: I get the followign running moblock-simplegui from the terminal

willmc@willbuntu:~$ moblock-simplegui
/usr/bin/moblock-simplegui:66:in `initialize': Failed to open file '/usr/share/pixmaps/moblock-gui.png': Permission denied (GLib::FileError)
        from /usr/bin/moblock-simplegui:66

You have to sudo it, otherwise it won't work :).

Strangely, the GUI doesn't really help me... I can't find the options to update lists etc., isn't that coded yet or do we have a bug :P?

Regards,
HBK

---

### Post by pelle.k on 2006-07-30
I was to code a complete GUI in ruby. Unfortunately i haven't got any time to spare so i just made a "tail" in a "trayable" GTK window. Nothing more, nothing less.
You can essentially have the same result if you use alltray on a terminal with "tail -f" on moblock.log.

If you want features then wait for mikji to complete "GNOME Blocklist". This is what he wrote earlier in this thread... > Hi folks,

I don't really post here that much (long time lurker), but I see you're looking for a moblock gui! Well, I've been working on one in gnome-python for the past few days, and it's about half done. I ran across this thread and thought I'd let you guys know about it so you don't duplicate work.

It'll have a dbus daemon, a notification applet and a preferences item. The first is mostly done, the second is trivial and I haven't gotten started on the last part.

I'll start a new thread when my sourceforge project is approved and I release something (a few days to a week).

Here are some screenshots; the first one is of the preference panel, and the second one is what you get when you click the notification icon.

Moblock shouldn't block LAN ip:s. If it does, it will show up in the log.

---

### Post by ba5e on 2006-07-30
This sounds great! thanks for the help, and well done pelle.k for the howto!

---

### Post by foxy123 on 2006-07-31
> **pelle.k said:**
> Moblock shouldn't block LAN ip:s. If it does, it will show up in the log.

I wonder what is that:
```
Blocked IN: matica.hr,hits: 1,SRC: 192.168.1.3
```

192.168.1.3 is a local IP address for my other PC.

---

### Post by harryhoudini66 on 2006-08-02
I decided to uninstall Moblock. When I shut down I see the process is running and being terminated. I am sure it is because it starts with Daemon. How do I remove it?

---

### Post by harryhoudini66 on 2006-08-02
Bump

---

### Post by pelle.k on 2006-08-03
Remove the file "K20moblock-nfq" from all runlevels (/etc/rc0.d/ etc...), "moblock-nfq" in /etc/cron.daily and finally "sudo rm -r /etc/moblock".

---

### Post by Daniel15 on 2006-08-04
OK, I appear to have got MoBlock working in conjunction with my firewall/IP masquerading script. I just needed to edit the MoBlock-nfq.sh file slightly. At first, it wasn't working, but then I discovered that where you put the firewall script determines whether MoBlock will work or not. What I found was that if I put a call to my firewall script right at the top of that file (on top of **# Filter all traffic, edit for your needs**), the firewall works, and MoBlock works as well :)

As an advantage, I no longer need to run PeerGuardian on my computers, as all the blocking is done on the Linux server :D

---

### Post by Razer(x) on 2006-08-05
:D ...hi..i am italian,so my english is not so good...but i thank you,i tried a lot to use moblock but nothing..thank you...now it blocks a lot,but i have a problem...when i do "tail -f /var/log/moblock.log" happen this 
Duplicated range ( WinMx Fake )
Skipping useless range: BitTorrent Corrupt Data Senders
Duplicated range ( BitTorrent )
Duplicated range ( BitTorrent )
Duplicated range ( ED2K Virus )
Ranges loaded: 148141
what should i do??and i don't understand if moblock starts automatically when i boot my pc

---

### Post by pelle.k on 2006-08-05
I understand you perfectly good :)
Yes, moblock starts up automaticly when you start up your computer.

Skipping and merging ranges is done when loading the blocklist in to moblock, because of duplicate or bad adresses in the blocklists downloaded. Nothing to worry about...
"Ranges loaded: 148141" Means that moblock is up and running. That's a good thing. After this line, all blocked ip:s will show up.

Try this in another terminal window ```
ping -c 1 212.73.29.83

```
If i'm right, you will see this address blocked out in the log.

---

### Post by pelle.k on 2006-08-05
> I wonder what is that:
Code:

Blocked IN: matica.hr,hits: 1,SRC: 192.168.1.3


192.168.1.3 is a local IP address for my other PC.

**foxy123**: Have you got bogon.txt blocklist included in the updater? This blocklist supposedly contains LAN ip:s. Don't ask me why...

---

### Post by Razer(x) on 2006-08-06
:rolleyes: ;) ...i know that this is'nt a real problem..yes moblock has blocked this ip..thank you!!!

---

### Post by foxy123 on 2006-08-06
> **pelle.k said:**
> **foxy123**: Have you got bogon.txt blocklist included in the updater? This blocklist supposedly contains LAN ip:s. Don't ask me why...

cheers a lot, I can access my laptop from another one now!

---

### Post by AndyAWS on 2006-08-12
...never mind, found my answer

---

### Post by pcfreak on 2006-08-24
Hi, I also have this thing with my moblock, it's skipping frames, but it's 4721 ranges! seem to be like a lot of frames to skip, I got the range from bluetack.co.uk

Are you sure, what is the reason for them beeing skipped? Invalid IP addresses/ranges.

If someone here know more about the reason for ranges beeing skipped, then I would like to know. I would like some more details.

MoBlock says:

Skipping useless range:

Why would someone include invalid/bad etc ranges...

What I am a little afraid of, is that the ranges are important, and that they will not get blocked when they should.

---

### Post by djcuuna on 2006-08-25
hello there i set up moblock but not sure if it is blocking so i tryed the tail -f /var/log/moblock.log to see if it is working this what i get and it stays like this. Short guarding.p2p line BitTorrent Corrupt Data Senders:222.3.95.112, skipping it...
Short guarding.p2p line BitTorrent Corrupt Data Senders:81.236.159.212, skipping it...
Short guarding.p2p line BitTorrent Corrupt Data Senders:82.93.220.230, skipping it...
Short guarding.p2p line BitTorrent Corrupt Data Senders:82.136.28.66, skipping it...
Short guarding.p2p line BitTorrent Corrupt Data Senders:70.48.177.235, skipping it...
Short guarding.p2p line ED2K File Flood: 62.57.143.116-62.57.143.116, skipping it...
Ranges loaded: 152356
Merged ranges: 170
Skipped useless ranges: 5741
NFQUEUE: binding to queue '0'
so is this ok or is something wrong thank you for any help in advance cheers

---

### Post by pelle.k on 2006-08-26
Looks ok to me.

---

### Post by Ole32 on 2006-08-28
I read Clessing's post ([http://www.ubuntuforums.org/showpost.php?p=1209006&postcount=81](http://www.ubuntuforums.org/showpost.php?p=1209006&postcount=81)) about MoBlock and Firestarter.
I am beginner, so I would like to ask - all the problems are only with Firestarter? If I would use e.g. Guarddog, MoBlock will work correctly?

---

### Post by pelle.k on 2006-08-30
well, the problem is really this (it's not really that complicated to understand);
Both fireHOL and firestarter make rules in something called iptables, which is essentially a command line firewall. To simplify things, let's just say that you can tell iptables which traffic goes to "accept" or "drop".
Moblock doesn't filter traffic which goes to "accept", instead it requires sending traffic to a third action (or que really...) specific to moblock called NFQUEUE.

Somehow filtering all traffic that goes to "accept" would solve all problems with most firewalls, because no rules have to be changed in iptables.
_But_, because moblock requires all traffic you want to filter to go through "moblock" action, and this is not possible (as far as i know) in many firewalls, except fireHOL.

Morpheus (the author of moblock) has done a great job with moblock, but i would welcome a "diffrent approach" to do this kind of filtering.

---

### Post by Hype_ on 2006-09-04
Erm, quite an issue here: I installed MoBlock following your guide without problem.
 Then i wanted to remove it because i had to kill it to connect to services like msn, play Enemy Territory...i uninstalled moblock*.deb and deleted the rcon.daily moblock file.

 But now, i cant cant connect to internet at all (im usin my fathers pc :/)
The thing is: at start-up , network configuration shows no error, but i cant acces anything.

 When i try to ping my ISP (free.fr) i get unknown host error.
My DNS settings point to the good ip adress (this is given by my ISP, right?)

Help needed!

---

### Post by hype on 2006-09-04
Ok, i managed to fix it.
I just did the following:
 -removed mobblock (via synaptik)
 -sudo rm -Rf /var/spool/moblock/
 -sudo rm -Rf /etc/moblock/
 -restart

---

### Post by termite on 2006-09-04
has anyone managed to get moblock to work with initng?  I've been trying and getting initng to segfault a lot, which scares me.

I can get it to start (most of the time), but not to stop.  Advice (or better: a moblock.i script that works) welcome.

---

### Post by pelle.k on 2006-09-05
Is "initng" really worth the hassle when "upstart" is coming? After all edgy eft is only like two months away...

@ Hype: glad it worked out for you. I read your pm just a few seconds ago...

---

### Post by termite on 2006-09-05
I haven't been keeping up with edgy development, but will read up on upstart.  I've been running initng for a couple of months now and rather enjoy it.  I was hoping to get moblock running with it, though I suppose I can just start manually.

---

### Post by Anokyn_PT on 2006-09-06
hi!! i'm a pure debian user !! i instaled the moblock but if i put the bçacklist Microsoft i can't use aMSN , so how do i make a whitelist??

---

### Post by pelle.k on 2006-09-07
Currently, there is no good way of doing this. You can whitelist protocols/ports (in /etc/moblock/moblock-nfq at the top of the file), but not ip:s. If you wan't to do that, there is some commented code in the /etc/cron.d/moblock-nfq which let you remove certain ranges (based on ip range name), but it's very un precise. I guess the best thing is to remove the range in question manually from guarding.p2p

---

### Post by flamarro on 2006-09-07
hi there,
need some help here in one thing, i've installed moblock and firehol,( i consider myself a newbie here ), but the thing works good, but every morning when cron is activated, and the block lists are updated, i get no internet. I have to stop moblock-nfq, stop firehol, then start moblock-nfq, then start firehol. Only then i can get back to internet. In cron.daily i have moblock-nfq reload.....

PS: sorry for my english

---

### Post by swkiller on 2006-09-09
I've tried installing moblock but when I try

 sudo apt-get install moblock-nfq

it goes to install and then tries to connect to [www.bluetack.co.uk](www.bluetack.co.uk) and always gets a connection time out.

is the site no longer there?

---

### Post by ratai on 2006-09-10
i confirm that it's impossible to connect and update lists
ratai

---

### Post by clessing on 2006-09-10
> **ratai said:**
> i confirm that it's impossible to connect and update lists
ratai

[http://forums.phoenixlabs.org/showthread.php?t=12394&page=4&highlight=bluetack](http://forums.phoenixlabs.org/showthread.php?t=12394&page=4&highlight=bluetack)

I did not notice, because I had other things in mind. A new version of moblock is being uploaded at the moment that will compensate this by using a backup host.

[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

---

### Post by laytoncy on 2006-09-11
Ubuntu just told me there's an update available for download for moblock-nfq.  Is this the update in your previous post?  By updating this it should just go on working as it has for me thus far?

---

### Post by clessing on 2006-09-11
> **laytoncy said:**
> Ubuntu just told me there's an update available for download for moblock-nfq.  Is this the update in your previous post?  By updating this it should just go on working as it has for me thus far?

Yes, I just changed the URL where it downloads updates for the blocking lists from.
(This is in /etc/cron.daily/moblock-...)
Everything else is unchanged.

---

### Post by Razer(x) on 2006-09-12
hi...my moblock..doesn't block..what should i do?

---

### Post by pelle.k on 2006-09-12
Sorry razer(x) but that is like saying your house is broken (when you door doesn't work) ;) 
You have to explain to us what isn't working. Doesn't it start up? Does it give you any error messages somewhere. Doesn't it block ip:s any longer? Is it not updating blocklists (Because if you skim like the recent four posts you will see a fix is already uploaded)

---

### Post by Razer(x) on 2006-09-12
ehm....my problem is..that...it update..and i think it starts...but....it does'nt blocks..

---

### Post by ratai on 2006-09-12
it is very difficult for me to understand the difference between iptables, firestarter, and firehole... and today i was try firehol for the first time and after ur tutorial i was blocked (no connection):confused: , not with firehol but when i take lines about moblock in firehol.conf. 
Really in tutorial of firehol it is difficult what is essential and what is not necessary.
and i finish to reinstall all my ubuntu...:frown: 

is it possible for simple users to have some exemples of config with a pc with a router nat with firehol and moblock inside the firehol.conf ?
and a sugggestion to help us, poor users, maybe a**_ script_** who **tail, update, stop and start** who is on link on desktop could be easier :biggrin: 
tkx for ur help

---

### Post by mikji on 2006-09-13
hey guys, 

sorry for the lack of updates. long story short, i had a bit of a car accident, and college has been tough. with any luck, i'll have some updates to gnome blocklist this weekend, but don't hold your breath.

everyone is welcome to check out whats in subversion right now and play around with it, although i can't remember what works and what doesn't. patches welcome!

---

### Post by spockrock on 2006-09-13
sorry may seem like a n00b question it seems like my friends ip addy is being blocked by moblock when I try to access his ftp is there anyway I can unblock his specific ip?

---

### Post by pelle.k on 2006-09-13
> is it possible for simple users to have some exemples of config with a pc with a router nat with firehol and moblock inside the firehol.conf ?
Yes. I actually use NAT and moblock in my own firehol.conf, and i will squeeze that into the HOWTO as soon as possible.

> sorry may seem like a n00b question it seems like my friends ip addy is being blocked by moblock when I try to access his ftp is there anyway I can unblock his specific ip?
It's no noob question.
There's no elegant way yet, but do 'grep -i -v 217.56.68 /etc/moblock/guarding.p2p > /etc/moblock/temp.p2p'
then 'sudo mv /etc/moblock/temp.p2p /etc/moblock/guarding.p2p'
This would remove all ip:s starting 217.56.68 from the blocklist.

There's something like it commented out (comments are lines starting with a hash #) in /etc/cron.d/moblock-nfq. Use it to your advantage. /etc/cron.d/moblock-nfq is the "updater" script and it does run every day.

---

### Post by pelle.k on 2006-09-13
razer(x) could you paste the output of 'tail /var/log/moblock.log' to us?

---

### Post by flamarro on 2006-09-13
> **flamarro said:**
> hi there,
need some help here in one thing, i've installed moblock and firehol,( i consider myself a newbie here ), but the thing works good, but every morning when cron is activated, and the block lists are updated, i get no internet. I have to stop moblock-nfq, stop firehol, then start moblock-nfq, then start firehol. Only then i can get back to internet. In cron.daily i have moblock-nfq reload.....

PS: sorry for my english

I'm sorry to insist, but, does this happens to anyone else?

by the way, i have updated, have now the new site for updates, but i can only update if i change to txt the source blocks, if not, theres allways error 404 file not found, and had to put # in all the 3 lines that involve gunzip so that the script can run. Treat me good, don't shoot me, i'm just a newbie too....:D

---

### Post by Razer(x) on 2006-09-13
Skipping useless range: eAcceleration
Skipping useless range: [www.spybot-Spy-removal.com](www.spybot-Spy-removal.com)[Spy]
Skipping useless range: amigeek.com/gocybersearch.com[CWS]
Skipping useless range: n69.com/bc777.com
Skipping useless range: DigitalRooster.com
Skipping useless range: Parcproductions.com
Skipping useless range: Fastsearch[Spy]
Ranges loaded: 135805
Merged ranges: 135
Skipped useless ranges: 4525

it loads ips..but it doesn't blocks

---

### Post by spockrock on 2006-09-13
> **pelle.k said:**
> Yes. I actually use NAT and moblock in my own firehol.conf, and i will squeeze that into the HOWTO as soon as possible.


It's no noob question.
There's no elegant way yet, but do 'grep -i -v 217.56.68 /etc/moblock/guarding.p2p > /etc/moblock/temp.p2p'
then 'sudo mv /etc/moblock/temp.p2p /etc/moblock/guarding.p2p'
This would remove all ip:s starting 217.56.68 from the blocklist.

There's something like it commented out (comments are lines starting with a hash #) in /etc/cron.d/moblock-nfq. Use it to your advantage. /etc/cron.d/moblock-nfq is the "updater" script and it does run every day.


yeah worked perfectly but the update script is in /etc/cron.daily/moblock-nfq.  But I edited that to exclude my friends specific ip. thanks for the help.

---

### Post by pelle.k on 2006-09-13
razer(x):
OK...
Post the output of 'sudo iptables -L'
That will show if traffic is going through moblock.

spockrock:
way to go. :) glad to be of service...

flamarro:
When it doesn't work, save the output of 'tail /var/log/moblock.log' and of 'sudo iptables -L' to a textfile, so that you can post it here when you've reloaded everything.

---

### Post by smartalecks on 2006-09-16
Moblock was working, but I just did a clean install of ubuntu and now when I try to use Moblock the log shows this error:

```

NFQUEUE: binding to queue '0'
error during nfq_create_queue()
```

any ideas? I've tried resetting and reloading, no luck.

---

### Post by clessing on 2006-09-16
> **smartalecks said:**
> Moblock was working, but I just did a clean install of ubuntu and now when I try to use Moblock the log shows this error:

```

NFQUEUE: binding to queue '0'
error during nfq_create_queue()
```

any ideas? I've tried resetting and reloading, no luck.

Try a "killall moblock" before you use the script again to start it.
It happens sometimes and i hope to fix it with the next release when I reorganize the whole package.

---

### Post by flamarro on 2006-09-18
> **pelle.k said:**
> razer(x):
OK...
Post the output of 'sudo iptables -L'
That will show if traffic is going through moblock.

spockrock:
way to go. :) glad to be of service...

flamarro:
When it doesn't work, save the output of 'tail /var/log/moblock.log' and of 'sudo iptables -L' to a textfile, so that you can post it here when you've reloaded everything.

ok, i'll do it as soon as i can. Meanwhile, i've discover that this thing happens only when use reload. doing reload blocks internet.... stop and then start of both moblock and firehol do the job as i said. imediatly after this if i do reload, bum, blocks again....

---

### Post by pelle.k on 2006-09-18
Try "sudo /etc/firehol restart" only. It should rewrite iptables if moblock did something to it. If it works, then just add it to the end of /etc/cron.d/moblock-nfq.

---

### Post by Razer(x) on 2006-09-21
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

ps...i have compiled my kernel and it is 2.6.17

---

### Post by pelle.k on 2006-09-21
There you have it :) I've been there too. do 'make xconfig' if the correct modules is checked, then 'sudo make modules' and finally 'sudo make modules_install'
Not 100% sure this is correct, but give it a try.

From moblock 0.8 README
> Requirements.

1) iptables and kernel support for connection and state tracking (
   ip_conntrack,ipt_state) and ip_queue or ipt_NFQUEUE kernel modules/built-in.

   At least kernel 2.6.14 is required to use the NFQUEUE interface (the
   default interface from MoBlock version 0.6) and userspace library:

   libnfnetlink 0.0.14
   libnetfilter_queue 0.0.11

   These are the kernel modules i have with MoBlock running
   on 2.6.9-ac6:

   with kernel 2.6.15 using new NFQUEUE interface:

	nfnetlink_queue         9280  1
	nfnetlink               4824  2 nfnetlink_queue
	ipt_NFQUEUE             1408  2
	ipt_state               1472  0
	ip_conntrack           40044  1 ipt_state
	iptable_filter          2176  1
	ip_tables              17600  3 ipt_NFQUEUE,ipt_state,iptable_filter

---

### Post by ginzberg on 2006-09-21
I too am experiencing the problem where the log file throws no errors, yet it appears no ips are actually being filtered.  I have ensured that all the above required modules are loaded, however, it should be noted that they did not autoload once moblock was started.  In previous versions, I believe that it did.  I recently reinstalled due to a failed harddrive, so I am unable to check myself.  Does anyone have the previous ubuntu install deb's (i notice the latest was updated september 16th, 2006).  I would be interested in seeing if the older version fixes the problem.

> uname -a
Linux grebznig 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

---

### Post by pelle.k on 2006-09-21
Have you acctually tried to ping an ip in the guarding.p2p list?
Do 'sudo tail /etc/moblock/guarding.p2p'
Pick one ip adress from a range, and do 'ping -c 1 xxx.xxx.xxx.xxx'
Then 'tail /var/log/moblock.log'

---

### Post by ginzberg on 2006-09-21
A thousand apologies!  Just tried doing that and sure enough, got a hit.  I suppose that the default rules were either more stringent by default before, or I have just been a good boy lately.

Thank you for setting me straight.

---

### Post by pelle.k on 2006-09-22
:) No need to apologise.

---

### Post by Daniel15 on 2006-09-22
Sorry, I haven't kept up-to-date with this thread, and haven't had time to read through it...

Is there a way to use my IPTABLES script along with MoBlock? I previously thought that I found a way, but it didn't work well :(

---

### Post by pelle.k on 2006-09-22
Feel free to add whatever you want to iptables, AFTER moblock has activated. Just make sure those new rules are compatible with the rules moblock put in.

---

### Post by moore.bryan on 2006-09-22
[I]why not just use peerguardnf? 
[http://doc.gwos.org/index.php/Peer_Guardian](http://doc.gwos.org/index.php/Peer_Guardian)
[/I]

---

### Post by thechilde on 2006-09-22
mine is not blcoking anything as far as i can tell. my log never changes. here is iptables

sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
MOBLOCK_IN  all  --  anywhere             anywhere            state NEW 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
MOBLOCK_FW  all  --  anywhere             anywhere            state NEW 

Chain MOBLOCK_FW (1 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_IN (1 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_OUT (1 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
MOBLOCK_OUT  all  --  anywhere             anywhere            state NEW

---

### Post by pelle.k on 2006-09-22
I'll repeat what i wrote six posts ago:
> Have you acctually tried to ping an ip in the guarding.p2p list?
Do 'sudo tail /etc/moblock/guarding.p2p'
Pick one ip adress from a range, and do 'ping -c 1 xxx.xxx.xxx.xxx'
Then 'tail /var/log/moblock.log'

---

### Post by thechilde on 2006-09-25
I did, the log does not change. And the pinging has only failed once the others I was pinging fine.

---

### Post by thechilde on 2006-09-25
:~$ sudo tail /etc/moblock/guarding.p2p
Password:
222.187.120.016 - 222.187.120.023 , 000 , XuZhou Pol
222.191.240.060 - 222.191.240.063 , 000 , wuxi sony 
222.196.048.000 - 222.196.063.255 , 000 , Sichuan Co
222.198.246.000 - 222.198.246.255 , 000 , GuiZhou Po
222.218.156.005 - 222.218.156.005 , 000 , [DShield t
222.227.073.056 - 222.227.073.063 , 000 , COMING PIC
222.227.164.073 - 222.227.164.073 , 000 , DDoS/ap2p
222.228.161.106 - 222.228.161.106 , 000 , DDoS/ap2p
222.229.088.000 - 222.229.095.255 , 000 , Bogon
223.000.000.000 - 255.255.255.255 , 000 , Bogon, IAN
:~$ ping -c 1 222.191.240.062
PING 222.191.240.062 (222.191.240.50) 56(84) bytes of data.

--- 222.191.240.062 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

:~$ tail /var/log/moblock.log
Reopening logfile.
:~$ 


So it didn't ping, but it didn't log it either.

---

### Post by pelle.k on 2006-09-25
I'm afraid i can't help you with that :(, it would seem you really have a problem.

Compare the output of 'lsmod' to this;
```
nfnetlink_queue 9280 1
nfnetlink 4824 2 nfnetlink_queue
ipt_NFQUEUE 1408 2
ipt_state 1472 0
ip_conntrack 40044 1 ipt_state
iptable_filter 2176 1
ip_tables 17600 3 ipt_NFQUEUE,ipt_state,iptable_filter
```

'pidof moblock' should tell you if it's running. I would suggest you reinstall it.

---

### Post by Daniel15 on 2006-09-26
I see something weird in your ping output, thechilde:
```

PING 222.191.240.062 (222.191.240.50) 56(84) bytes of data.

```
222.191.240.062 is 222.191.240.50??

Try pinging Microsoft.com, and see if you have the same result.

What I usually do to test this is have two terminal windows open. In one, I type ```
tail -f /var/log/moblock.log
``` (which will leave the tail program open, and write the log messages as they appear). In the other window, I ping microsoft.com:```
ping microsoft.com
```. Then, I check the first window for any output.

---

### Post by flamarro on 2006-09-28
> **pelle.k said:**
> Try "sudo /etc/firehol restart" only. It should rewrite iptables if moblock did something to it. If it works, then just add it to the end of /etc/cron.d/moblock-nfq.
Sorry not to answer so soon, but in  this days that have passed when reloading theres was no problem at all, till today :confused: did restart as you said and there it goes again. But why the hell this happens only sometimes? I was thinking it was for the new version of moblock but...... well, never mind, restart we'll do :rolleyes: it works, thats all we want, yes? :mrgreen:

---

### Post by shookone on 2006-09-28
I just installed moblock and was experiencing problems running it with ubuntu-firewall script.

I tried loading iptables as recommended for firehol and it had no effects. Upon disabling my firewall, i was able to see the log file fill up with lines like:

```
Short guarding.p2p line 222.168.089.192 - 222.168.089.207 , 000 , CHANGCHUN-, skipping it...
Short guarding.p2p line 222.168.091.008 - 222.168.091.011 , 000 , CHANGCHUN-, skipping it...
Short guarding.p2p line 222.172.032.100 - 222.172.032.100 , 000 , [DShield t, skipping it...
Short guarding.p2p line 222.182.110.000 - 222.182.110.255 , 000 , [DShield b, skipping it...
Short guarding.p2p line 222.184.240.040 - 222.184.240.043 , 000 , police tra, skipping it...

```

Which results in:

```
Ranges loaded: 4445
Merged ranges: 9
Skipped useless ranges: 223
NFQUEUE: binding to queue '0'
error during nfq_create_queue()

```

ubuntu-firewall script:

```
############################################################################
#  ubuntu-firewall-cfg    Configuration settings for the Ubuntu-firewall.  #
#  This config file should be placed within your /etc/default directory.   #
#  Version: 0.5                                                            #
############################################################################

###
#  Network Interfaces
###

#  Set the external interface.  This is the interface that will
#  face the Internet.  It's the one you want Ubuntu-firewall to
#  protect.  Typically it will be eth0 or eth1.  However, you
#  may choose to have Ubuntu-firewall automatically select the
#  * first * active interface it finds.  In this case, you would
#  use the key word, "auto" as in, EXTIF="auto".  This is usually
#  a good choice for users who have only one active network
#  interface on their machine.
#
EXTIF="eth0"
#EXTIF="auto"

#  Set the internal interface if you have one and want to be
#  able to pass local traffic over it.  If not, then don't
#  specify an interface inside the quotes.  Just leave it blank
#  as in INTIF="".  This can NOT be set to, "auto!"
INTIF="eth1"



##
#  Miscellaneous options set with, "yes" or, "no"
##

#  Disable the firewall (useful for temporarily disallowing Ubuntu-firewall
#  to start, without having to remove it from your startup configuration).
#  This setting affects Ubuntu-firewall's ability to start on boot-up but
#  has no affect on the current firewall state.  In other words, if
#  Ubuntu-firewall has run before setting this to disabled, the firewall
#  will still be active until you either reboot, or issue the following
#  at the command line: 'sudo /etc/init.d/ubunti-firewall.sh stop'
DISABLED="no"

#  Firewall logging (useful for debug, curiousity, etc.  Logs to syslog)
LOG_PACKETS="no"

#  Verbose mode (feedback during script execution - useful for debug, etc.)
VERBOSE="no"

#  Respond to ICMP (echo-request) pings
ALLOW_PINGS="no"



###
#  Complex Server options set with, "yes" or, "no"
###

#  FTP server - Firewall requirements for an FTP Server are a little more
#  involved.  Thus, I've coded support for it directly into the Ubuntu-firewall
#  script.  It can be enabled/disabled here.
ALLOW_FTP="yes"

#  Micro$oft Networking - Firewall requirements for Micro$oft Networking are
#  a little more involved.  Thus, I've coded support for it directly into the
#  Ubuntu-firewall script.  It can be enabled/disabled here.
ALLOW_MSNETWORKING="no"



###
#  Other services
###

#  List the TCP ports you want un-blocked by the firewall.
#  The ports need to be inside the quotes with a space between each one.
#  (ex: OPEN_TCP_PORTS="22 80 110")
#  This would un-block TCP ports 22 (ssh), 80 (http), and 110 (POP-3).
OPEN_TCP_PORTS="37222 24808 49160 49161 49162 49163 49164 49200 49300 21 22 80 85 110 25 5900 8181 8080 10000 30000"

#  List the UDP ports you want un-blocked by the firewall.
#  The ports need to be inside the quotes with a space between each one.
#  (ex: OPEN_UDP_PORTS="53")
#  This would un-block UDP port 53 (DNS Server services).
OPEN_UDP_PORTS="4905 15801 34522 34525 37500"



###
#  Advanced Options
###

#  Network Address Translation/Routing
#
#  This enables NAT Routing capabilities.  To use this feature, you must
#  specify the interface for NAT_IF, for which you want NAT services applied.
#  This MAY be the same as your internal interface (INTIF) as specified above.
#  ex:  NAT_IF="eth1"  (this will allow you to connect another PC to this PC's
#  eth1 interface for Internet Access on that PC)  To disable NAT, don't
#  specify an interface inside the quotes.  Just leave it blank as in NAT_IF="".
#
#  Bear in mind that the PC connected to this one will need to be set up on
#  the same network segment that this one's NAT_IF is on.  You will also need
#  to use the IP address assigned to the NAT_IF device, as that PC's default
#  gateway to the Internet.
NAT_IF="eth1"

#  Forwarding of Ports
#
#  This allows you to forward ports to an internal host.  To use this feature,
#  simply specify an internal host to which you want to forward incoming
#  connections using the FORWARD_HOST directive.  Leaving it blank as in,
#  FORWARD_HOST="" will disable port forwarding.  Once you've specified a
#  host to which you want ports forwarded, you need to specify the ports.
#  This is done using the following two directives: FORWARD_TCP_PORTS
#  FORWARD_UDP_PORTS.  You may list multiple ports by separating them with
#  spaces.  For instance, if you wanted to forward incoming to TCP ports 22,
#  80, and 110, to an internal host with an IP address of 192.168.1.10, you
#  would use the following configuration:
#  FORWARD_HOST="192.168.1.10"
#  FORWARD_TCP_PORTS="22 80 110"
#  FORWARD_UDP_PORTS=""
FORWARD_HOST="192.168.100.100"
FORWARD_TCP_PORTS="6346"
FORWARD_UDP_PORTS=""

#  Custom Rules
#
#  This allows the user to define non-standard or custom rules to be added
#  to the firewall policy.  It is STRONGLY RECOMMENDED that you only make
#  use of this if you understand iptables hirarchy and firewall design in
#  general!  Carelessly inserting rules into Ubuntu-firewall can easily
#  render it ineffective.  You have been warned!  Now, with all that out
#  of the way, here's how to do it.  First, you need to create a file that
#  contains the appropriate iptables commands, making certain that you have
#  the syntax correct.  When making your custom rules, you should probably
#  test each of them, one-at-a-time at the command prompt to verify that they
#  work as expected.  You may define as many custom rules as you like but
#  remember, usually the simpler the firewall ruleset, the more robust it
#  tends to be.  Take special care to make sure that any rules you define,
#  don't sabotage other rules listed below it.  Once you have your file
#  populated with your custom rules, save it and set the CUSTOM_RULES directive
#  to point to your file. Ex: CUSTOM_RULES="/etc/default/custom_firewall_rules"
#  If you don't have any reason to use custom rules, then simply leave
#  CUSTOM_RULES blank as in, CUSTOM_RULES="".
CUSTOM_RULES="/etc/default/ubuntu-firewall-custom"

```

Custom Rules:
```

## Custome Rules for ubuntu-firewall-cfg
iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE

```

I am unable to block sites like microsoft. 

Here is additional information:

```


>lsmod | grep NFQUEUE
ipt_NFQUEUE             1920  0
ip_tables              23744  7 iptable_mangle,ipt_NFQUEUE,ipt_REJECT,ipt_limit,ipt_state,iptable_nat,iptable_filter

-------------

>ls /etc/moblock/
guarding.p2p  guarding.p2p.backup  MoBlock-nfq.sh

-------------
>uname -a
Linux linux-core-pc 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux


```

/etc/cron.daily/moblock-nfq:

```
BLOCKLISTS="nipfilter.dat ads-trackers-and-bad-pr0n"
```

>iptables -L :
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain MOBLOCK (0 references)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Please help. I just got one of those notifications your don't want to receive from your ISP. I've had moblock running for some time thinking its been blocking.  I'll be happy to provide any information needed.

---

### Post by pelle.k on 2006-09-28
very good report! :)
You shouldn't expect moblock to run with any other firewall script than firehol, as you probably know by now, so uninstall ubuntu-firewall, or see to it that it will run no more.
iptables -L shows me no traffic is using iptables firewall. If you have installed firehol, something is wrong. did you activate it (eg "START_FIREHOL=YES" in /etc/default/firehol)?
can you paste your /etc/firehol/firehol.conf here so i can take a look at it?

---

### Post by shookone on 2006-09-28
**pelle.k**: Well i removed my firewall completely. Moblock should work correct? I ran some commands to confirm its operational state:

I removed ubuntu-firewall script from /etc/rc* directories (ex. rm /etc/rc1.d/*ubuntu-firewall.sh) and all its configuration files(ex sudo rm /etc/default/ubuntu-firewall-*)

>tail command...:
```

>tail -f /var/log/moblock.log

Skipping useless range: adelinatech.com
Skipping useless range: CWS
Skipping useless range: ns1/ns2.playercodec.net
Skipping useless range: www.buhartes.info|BT|Hijackers
Skipping useless range: adv549|CWS|BT|Hijackers
Skipping useless range: Pluginaccess.com/Dialeraccess.com[CWS]
Ranges loaded: 4445
Merged ranges: 9
Skipped useless ranges: 223
NFQUEUE: binding to queue '0'


```

```

###@linux-core-pc:/etc/default$ ping microsoft.com
PING microsoft.com (207.46.250.119) 56(84) bytes of data.

--- microsoft.com ping statistics ---
26 packets transmitted, 0 received, 100% packet loss, time 25069ms

###@linux-core-pc:/etc/default$ ping www.microsoft.com
PING lb1.www.ms.akadns.net (207.46.199.30) 56(84) bytes of data.

--- lb1.www.ms.akadns.net ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5000ms

###@linux-core-pc:/etc/default$ ping adelinatech.com
PING adelinatech.com (68.178.232.100) 56(84) bytes of data.

--- adelinatech.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2001ms

###@linux-core-pc:/etc/default$


```

I have no firewall rules active and im not blocking sites... via firefox i can connect to microsoft's main site. 

Does moblock require firehol?

---

### Post by pelle.k on 2006-09-28
no, not at all. running moblock without a firewall such as firehol is actually less painful, as moblock creates rules in iptables automaticly. this is the reason it doesn't work with other firewalls, because after  moblock has setup some rules in iptables, the "firewall" put it's own rules also in iptables, and it becomes a mess.
Iptables can (unforuately) only have one application at a time create rules for it. _If_ you customize firehol a bit, then you can have them both running, that's the reason i have that bit in my howto, but it's not at all necessary.

---

### Post by shookone on 2006-09-28
After flushing all iptables and deleting chains to make sure moblock has full control of iptables without the use of a firewall i ran the following commands. 

```

iptables -X MOBLOCK (MOBLOCK_FW MOBLOCK_IN MOBLOCK_OUT)

iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


Then loaded moblock from init.d:
```

/etc/init.d/moblock-nfq restart
 * Restarting moblock moblock                       [Ok]
```

Then check iptables' current listing show:

```
# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
MOBLOCK_IN  all  --  anywhere             anywhere            state NEW

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
MOBLOCK_FW  all  --  anywhere             anywhere            state NEW

Chain MOBLOCK_FW (1 references)
target     prot opt source               destination
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_IN (1 references)
target     prot opt source               destination
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_OUT (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
MOBLOCK_OUT  all  --  anywhere             anywhere            state NEW

```

Now quickly see my /etc/cron.daily/moblock-nfq::

```
cat /etc/cron.daily/moblock-nfq |grep BLOCKLIST
# use from BLOCKLISTS.
#BLOCKLISTS="ads-trackers-and-bad-pr0n level1 level2  Microsoft  spyware "
BLOCKLISTS="nipfilter.dat ads-trackers-and-bad-pr0n"
#BLOCKLISTTXT="templist dshield"
BLOCKLISTTXT="dshield"

```

Now when i try to hit microsoft.com website. i get access to it.. (nipfilter.dat contains all level spyware and microsoft db's)

However, when i try an ip from the list:

```
>tail /etc/moblock/guarding.p2p

www.tendomain.com|Hijack|BT:218.38.13.220-218.38.13.220
CYBERSURFING:218.236.112.0-218.236.112.127
y3y.net/555y.com:219.129.216.39-219.129.216.39
xpire.info-Hijacker[spy]:221.139.50.11-221.139.50.11
Dabber.B|BT:221.236.167.192-221.236.167.192
MS Word Exploit|BT:222.92.208.225-222.92.208.225
hongnanjing.com:222.189.228.5-222.189.228.5
80ke.com:222.189.238.77-222.189.238.77
zinanjing.com:222.223.183.30-222.223.183.30
W32/Downloader/http.down.love.witlog.net:222.237.76.91-222.237.76.91

```

```
And pinging 80ke.com, my moblock log returns:
Blocked IN: [DShield block] FAST COLOCATION SERVICES,hits: 1,SRC: 204.16.208.90
Blocked IN: [DShield block] FAST COLOCATION SERVICES,hits: 2,SRC: 204.16.208.90
Blocked OUT: 80ke.com,hits: 1,DST: 222.189.238.77
Blocked OUT: 80ke.com,hits: 2,DST: 222.189.238.77
Blocked OUT: 80ke.com,hits: 3,DST: 222.189.238.77
Blocked OUT: 80ke.com,hits: 4,DST: 222.189.238.77
Blocked OUT: 80ke.com,hits: 5,DST: 222.189.238.77
Blocked IN: [DShield block] FAST COLOCATION SERVICES,hits: 3,SRC: 204.16.208.167
Blocked IN: [DShield block] FAST COLOCATION SERVICES,hits: 4,SRC: 204.16.208.167
Blocked OUT: MS Hotmail,hits: 1,DST: 64.4.32.7
Blocked OUT: MS Hotmail,hits: 2,DST: 64.4.32.7
Blocked IN: [DShield block] FAST COLOCATION SERVICES,hits: 5,SRC: 204.16.208.239
Blocked IN: [DShield block] FAST COLOCATION SERVICES,hits: 6,SRC: 204.16.208.183
Blocked IN: [DShield block] FAST COLOCATION SERVICES,hits: 7,SRC: 204.16.208.114
Blocked IN: [DShield block] FAST COLOCATION SERVICES,hits: 8,SRC: 204.16.208.114
Blocked IN: [DShield block] FAST COLOCATION SERVICES,hits: 9,SRC: 204.16.208.20
```


So the darn thing is working... Now to reinstall using Firehol. I hope im able to NAT easily from there.. I'm pretty savvy with shit but iptables troubles me.

Thanks for the support. Would be nice to have ubuntu-firewall work with this. Its a great script.

---

### Post by pelle.k on 2006-09-28
No sweat.
I'm no fan of iptables either. It's built for handwritten custom configurations.
I would rather have software using it directly, not through scripts, so that it could have slots for more than one application, and also not let one application change rules to a busy slot, but use it's own slot. Also this would make applications aware of each other through iptables, and one could tell iptables wich application would have the first slot.
Then the firewall could filter traffic in slot one, and moblock have it's own rules in slot two wich the filtered traffic would come to after slot 1.
Maybe i make no sense at all. ](*,)

Then again, it would be nice if moblock didn't use iptables at all to filter traffic (let firewalls and such have iptables for them self) but filter all traffic that goes in or out of the kernel by default.

---

### Post by shookone on 2006-09-28
Another gripe im having is that i noticed that i can access [http://www.microsoft.com](http://www.microsoft.com) [http://mpaa.org](http://mpaa.org) and sites of that nature.

Why do i connect to the microsoft site if i have all the lists blocking for me. Specially Microsoft.

Are there any bench marking tools/sites that can test my moblock

---

### Post by pelle.k on 2006-09-28
You know http traffic is whitelisted by default right?

---

### Post by shookone on 2006-09-28
meaning no matter what im blocking if its coming on via TCP 80 its entering coming in?

Makes no sense.. dont you think?

---

### Post by shookone on 2006-09-28
Id hate to be out of the scope of the project, but since i had to resort to another firewall... What type of rules can i put here. Is there any documented examples i can build off of. 

How would i put blocks to certain ports.. or NAT for my other interfaces can receive internet? *DHCP is already configured*

In any event, as requested:

/etc/default/firehol : 

```
$ cat /etc/default/firehol START_FIREHOL=YES

#If you want to have firehol wait for an iface to be up add it here
WAIT_FOR_IFACE="eth0"
```


/etc/firehol/firehol.conf:
```

#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5

########################
### moblock

iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE

##
########################



# Your internet interface

interface eth0 internet

        server ssh accept


        # This will send http traffic directly
        # to accept instead of moblock
        # thus whitelisting it...
        client http accept

        client all MOBLOCK

# Your local network
interface eth1 home


        # You can access whatever on your lan
        client all accept

        # If you want your lan user to access your http server
        server http accept

router internet2home inface eth0 outface eth1

router home2internet inface eth1 outface eth0
        route all accept


```

edit:

I made changes to my conf file. I want to give the world access to my ssh server for remote administrating.. hopefully this works since im on my way to work in a few.

---

### Post by pelle.k on 2006-09-29
why is whitelisting port 80 stupid? all ports are open by default, moblock just filters them. if you want to contact microsoft on port 80, i has to be whitelisted.

as for nat, add this entry before the interfaces;
```
 # fill in ip as needed, ethx = internet device
 dnat to 192.168.0.x:ssh inface ethx proto tcp dport 12345
```

do this with your router; (just an example)
```
 router lan2internet inface eth1 outface eth0
 masquerade reverse #now you can "imagine" it as a client, and not use route command...
 client all accept

 router internet2lan inface eth1 outface eth0
 route ssh accept dst 192.168.0.x
```

---

### Post by shookone on 2006-09-30
Pelle:

I misunderstood i guess. I thought that no matter what moblock is blocking if its port 80 it will come in. I have updated my firehol after much reading of the documentations. Would you mind a quick guidance since I cannot find a firehol.conf thread anywhere.

This is my current firehol.conf:

```

cat /etc/firehol/firehol.conf
#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5

########################
### moblock

iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE

##
########################


# The network of eth1
home_ips=192.168.100.2/24

# Your local network
interface eth1 home src "${home_ips}"

        policy reject
        server "dhcp samba" accept
        client "samba" accept

        # You can access whatever on your lan
        client all accept

        # If you want your lan user to access your http server
        server http accept

# Your internet interface

interface eth0 internet src not "${home_ips} ${UNROUTABLE_IPS}"

        protection strong 10/sec 10
        server "ssh ftp" accept


        # This will send http traffic directly
        # to accept instead of moblock
        # thus whitelisting it...
        client all MOBLOCK

router home2internet inface eth1 outface eth0
        masquerade
        route all accept


```

I'm searching for a front end that will allow me to better understand how this works.

Basically i have my ubuntu box with is directly connected to cable modem via eth0 and i have a xbox running both games and linux via eth1.

There are some ports i need to go from eth1 to the net. I'm not sure how to specify. I'm currently reading more into it but i managed to get the internet on my xbox/linux box.

Again much appreciation for the support. I'm still able to access microsoft.com via the web.. so how do i know if im blocking that stuff.

---

### Post by shookone on 2006-09-30
Wow what resting of the mind does.

I totally understand this now. 

What happens if i use this coding:

```
# Your internet interface

interface eth0 internet src not "${home_ips} ${UNROUTABLE_IPS}"

	protection strong 10/sec 10
	server "ssh ftp" accept
	**server all MOBLOCK**
	
        # This will send http traffic directly
        # to accept instead of moblock
        # thus whitelisting it...
	client "http https" accept
        client all MOBLOCK
	
router home2internet inface eth1 outface eth0
	masquerade
	route all accept
```

Will i be protected from anyone accessing my machine thats on the block list. or is this done automatically?

---

### Post by shookone on 2006-09-30
everything is working fine now... oh yeah except when firehol is loading at start up it shows an [ok] ... but then i do iptables -L and dont get back anything.


when i manually restart it.. then iptables -L show tons of info..

im about to reformat this partition and start fresh.. i know there is a way around it..

i used to use ubuntu-firewall and removed it from rc#.d directories.. i don't  know if i did it correctly.. thanks for any feed back.

---

### Post by pelle.k on 2006-09-30
if i'm not mistaken, you should use "server" instead of route after using reverse masquerading on a interface.

If only firehol, and moblock is installed, you should have a populated iptables after bootup. something is messing with the procedure. if you restart firehol, doesn't it complain about the route command?

---

### Post by Scum on a Dead Pelican on 2006-09-30
Hello,

I'm wondering if anyone else is having a problem that I'm having. 
Before the last update when I would 'tail -f /var/log/moblock.log'  it would show about 180,000 ranges blocked. Now when I do it, it only shows 2672 ranges blocked.
Also, I can leave amule going for hours downloading and nothing will show up on the log as being blocked, when I usually have a couple of blocks a minute.

I don't have any firewalls running.

Any ideas what's going on or any suggestions on how to fix it?

Thanks in advance and thank you for all the work you've put into this program.

---

### Post by pelle.k on 2006-09-30
Hi, clessing is going to reorganize things a bit in moblock-deb, but until then, there seems to be some problems with the new nipfilter.dat in /etc/cron.daily/moblock-nfq, comment the new BLOCKLISTS line, and uncomment the old one, and restart your computer and all will be well.

Those lines look like this (when modified as above)
```
BLOCKLISTS="ads-trackers-and-bad-pr0n level1 level2  Microsoft  spyware "
#BLOCKLISTS="nipfilter.dat ads-trackers-and-bad-pr0n"
```

Now i _don't_ now what is causing this, it might only be temporary, so I will not suggest this as a permanent solution. but for the time being...

---

### Post by shookone on 2006-09-30
> **pelle.k said:**
> if i'm not mistaken, you should use "server" instead of route after using reverse masquerading on a interface.

If only firehol, and moblock is installed, you should have a populated iptables after bootup. something is messing with the procedure. if you restart firehol, doesn't it complain about the route command?

Hey pelle.k:


I am able to use the net on my lan. I have problems with some applications like my xbmc(xbox) connecting to a client on my machine. Other then that it works... Although i'm still feeling compelled to fresh install. 

I restart my firewall an i get no error. I have a new configuration in my conf file.

```

version 5

#specify ports here
## type: client or server
## label: label port
## type/port: tcp or udp and port (Ex. tcp/80 or udp/300000
#format: type_label_ports="type/port"

server_xlink_ports="udp/37500"
client_xlink_ports="default"

# moblock settings
iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE

# The network of eth1
home_ips=192.168.100.2/24


# Your internet interface

interface eth0 internet src not "${home_ips} ${UNROUTABLE_IPS}"

        protection strong 10/sec 10
        server "ssh ftp xlink" accept
        # This will send http traffic directly to accept instead of moblock thus whitelisting it...
        client "http https" accept
        client all MOBLOCK

# Local network

interface eth1 home src "${home_ips}"
        policy accept
        client all accept

#Routing information

router home2internet inface eth1 outface eth0
        client all accept
        route all accept
        masquerade


```

If you see why a client connected to eth1 is having problems accessing the  web via port 37500. Please by all means, let me know.

I ran a script named firehol-wizard or something of that nature that made a check through my script and placed some TODO fields in showed a configuration that i used to have. my firehol.conf is located in /etc/firehol/. Perhaps it's pulling another conf file... im not sure what is going on.

Before using this firewall i never had experienced problems with my xbox and client/server connectivity. It's sad that I can't find another forum to discuss this issue in since there is moblock being an issue.

---

### Post by pelle.k on 2006-09-30
```
version 5

#specify ports here
## type: client or server
## label: label port
## type/port: tcp or udp and port (Ex. tcp/80 or udp/300000
#format: type_label_ports="type/port"

server_xlink_ports="udp/37500"
client_xlink_ports="default"

dnat to 192.168.100.2:37500 inface eth0 proto udp dport 37500

# moblock settings
iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE

# The network of eth1
home_ips=192.168.100.2/24


# Your internet interface

interface eth0 internet src not "${home_ips} ${UNROUTABLE_IPS}"

        protection strong 10/sec 10
        server "ssh ftp" accept # you dont need xlink here
        # This will send http traffic directly to accept instead of moblock thus whitelisting it...
        client "http https" accept
        client all MOBLOCK

# Local network

interface eth1 home src "${home_ips}" #this is only in your lan...
        policy accept
        client all accept
        #server all accept # you can safely remove this comment

#Routing information

router home2internet inface eth0 outface eth1
        masquerade reverse
        client all accept
        server xlink accept # xlink only here (this is the server)
```

Do you understand now?
I'm kindof tired, but i think this should be right...

---

### Post by shookone on 2006-09-30
Always good at that supporting end. Highly appreciated. Did you write moblock?

Anyways i tried your method for firehol.conf and i dont see any issues. Matter of fact i know see then when my client tries to connect to eth1(lan), moblock.log returns:

```
Blocked OUT: ServerBeach,hits: 3,DST: 66.135.32.175
Blocked OUT: ServerBeach Emule servers|P2P Fakes,hits: 3,DST: 64.34.165.84

```

I need this to work from a machine attached to eth1. I will continue my research. Thanks for everything... Any feed back from anyone is greatly appreciated.

---

### Post by Scum on a Dead Pelican on 2006-10-01
Thanks pelle.k,

That worked great!

---

### Post by 0815user on 2006-10-04
Well, hi.

I'm using moblock for 2.6.18 and the old filter files in cron.daily.

--------
Ranges loaded: 159469
Merged ranges: 176
Skipped useless ranges: 5890
NFQUEUE: binding to queue '0'
error during nfq_create_queue()
--------

Besides that error I noticed that moglock.log was bigger than 230MB today. That was because of all that "Skipping..."-messages. Maybe you should tweak the scripts to make sure that doesn't happen after a few weeks of usage.

---

### Post by pelle.k on 2006-10-04
I assume you have compiled your own kernel? Then you need to include some modules in xconfig. I wrote about it a couple posts back in the thread. Never done it myself though (running a custom kernel with moblock that is), so report back on what modules you included in xconfig. (I assume netfilter and ipt_state/iptables...)

I am not the author of moblock, nor am i maintaining the .debs... i'm just a friendly soul helping out, to the extent i can.
The .deb maintainer is however browsing this thread every now and then, so he'll probably notice your suggestion.

---

### Post by shookone on 2006-10-05
Sup guys. I have currently screwed my machine and have a new project at hand. 

So I will pause my issues with moblock and firehol... Pelle.k thanx for all the help.

Now i gotta recover lost files off a EXT3 partition that has been over written. Damn journalling is making this hard. But i will continue investigating this... If i come across anything i will post a thread on how i did it. Basically looking to recover pictures.. if i can recover my movies then ill post how to.

---

### Post by 0815user on 2006-10-05
> **pelle.k said:**
> I am not the author of moblock, nor am i maintaining the .debs.

Ahh. Thanks anyways. Yes, my kernel is my own creation. But those modules are all included.

Maybe it's because of new 2.6.18. Who knows.

---

### Post by devnulljp on 2006-10-09
I found sudo /etc/init.d/moblock-nfq restart seemed to start it running and blocking.

> **jamesford said:**
> well it doesent mess with firestarter but maybe thats cos moblock isnt blocking anything :( it doesent work.
there are no error messages in the log, appears to be running. but not blocking :(

---

### Post by Giggity on 2006-10-10
I'm afraid I don't know what this means, and searching for "sigterm" yields no results:
```
rob@rob-desktop:~$ tail -f /var/log/moblock.log
Ranges loaded: 0
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'
Got SIGTERM! Dumping stats and exiting.
Ranges loaded: 0
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'
Got SIGTERM! Dumping stats and exiting.

```

---

### Post by Zone17 on 2006-10-15
I am not running a firewall and I can not seem to get moblock to block anything my log file only returns this 


zone@zone-laptop:~$ tail /var/log/moblock.log
Short guarding.p2p line 222.198.246.000 - 222.198.246.255 , 000 , GuiZhou Po, skipping it...
Short guarding.p2p line 222.227.073.056 - 222.227.073.063 , 000 , COMING PIC, skipping it...
Short guarding.p2p line 222.227.164.073 - 222.227.164.073 , 000 , DDoS/ap2p, skipping it...
Short guarding.p2p line 222.228.161.106 - 222.228.161.106 , 000 , DDoS/ap2p, skipping it...
Short guarding.p2p line 222.229.088.000 - 222.229.095.255 , 000 , Bogon, skipping it...
Short guarding.p2p line 223.000.000.000 - 255.255.255.255 , 000 , Bogon, IAN, skipping it...
Ranges loaded: 2022
Merged ranges: 0
Skipped useless ranges: 65
NFQUEUE: binding to queue '0'

I tried to ping a blocked IP, but no luck, everthing is skipped.

---

### Post by wolf202 on 2006-10-16
Great Guide, Submitted to [wikitut.org]("http://www.wikitut.org")

[http://www.wikitut.org/index.php?title=How_to_Install_and_Use_Moblock](http://www.wikitut.org/index.php?title=How_to_Install_and_Use_Moblock)

-wolf

---

### Post by pelle.k on 2006-10-16
Giggity: Something is wrong with your setup. Try reinstalling.
Zone17: show me iptables rules (sudo iptables -L)
wolf202: Thanks

---

### Post by Zone17 on 2006-10-16
zone@zone-laptop:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
MOBLOCK_IN  all  --  anywhere             anywhere            state NEW

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
MOBLOCK_FW  all  --  anywhere             anywhere            state NEW

Chain MOBLOCK_FW (1 references)
target     prot opt source               destination
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_IN (1 references)
target     prot opt source               destination
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_OUT (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
MOBLOCK_OUT  all  --  anywhere             anywhere            state NEW

---

### Post by Zone17 on 2006-10-16
here are the results of my ping

zone@zone-laptop:~$ tail -f /var/log/moblock.log
Skipping useless range: adelinatech.com
Skipping useless range: CWS
Skipping useless range: ns1/ns2.playercodec.net
Skipping useless range: www.buhartes.info|BT|Hijackers
Skipping useless range: adv549|CWS|BT|Hijackers
Skipping useless range: Pluginaccess.com/Dialeraccess.com[CWS]
Skipping useless range: Parcproductions.com
Skipping useless range: Fastsearch[Spy]
Ranges loaded: 160907
Reopening logfile.

zone@zone-laptop:~$ ping microsoft.com
PING microsoft.com (207.46.250.119) 56(84) bytes of data.

--- microsoft.com ping statistics ---
121 packets transmitted, 0 received, 100% packet loss, time 120158ms

zone@zone-laptop:~$ ping microsoft.com
PING microsoft.com (207.46.250.119) 56(84) bytes of data.

--- microsoft.com ping statistics ---
33 packets transmitted, 0 received, 100% packet loss, time 32026ms

---

### Post by pelle.k on 2006-10-16
> 100% packet loss
I would say it's working perfectly! And you don't see these blocks in the log?

---

### Post by Zone17 on 2006-10-16
the logs just show skipping it, no blocks.

hort guarding.p2p line 071.142.027.224 - 071.142.027.239 , 000 , NORTHROP G, skipping it...
Short guarding.p2p line 071.142.028.056 - 071.142.028.063 , 000 , ACS STATE, skipping it...
Short guarding.p2p line 071.142.028.128 - 071.142.028.135 , 000 , MOTION PIC, skipping it...
Short guarding.p2p line 071.142.028.160 - 071.142.028.167 , 000 , LUCAS STUD, skipping it...
Short guarding.p2p line 071.142.042.024 - 071.142.042.031 , 000 , SACRAMENTO, skipping it...
Short guarding.p2p line 071.142.043.048 - 071.142.043.055 , 000 , LEGAL PHOT, skipping it...
Short guarding.p2p line 071.142.162.024 - 071.142.162.031 , 000 , CCSF POLIC, skipping it...
Short guarding.p2p line 071.142.179.032 - 071.142.179.039 , 000 , CLEAR CHAN, skipping it...
Short guarding.p2p line 071.143.100.192 - 071.143.100.199 , 000 , THE CASTIN, skipping it...
Short guarding.p2p line 071.143.106.240 - 071.143.106.247 , 000 , MORRISON &, skipping it...
Short guarding.p2p line 071.143.121.184 - 071.143.121.191 , 000 , NORTHROP G, skipping it...
Short guarding.p2p line 071.143.121.200 - 071.143.121.207 , 000 , NORTHROP G, skipping it..

---

### Post by Zone17 on 2006-10-16
I am very new to this though, but I do know in PG logs in winblows it shows blocks.

---

### Post by pelle.k on 2006-10-16
If you tail the log file, the most recent lines should show blocked ip:s, _if_ you recently tried to ping an ip from the blocklist. Those other lines is just feedback from loading ranges and other stuff.
'tail' just gives you the most recent lines. 'tail -f' (-f means 'follow') as in interactive tail, where stuff happens in real-time (you can exit it by pressing ctrl+c). Do you understand the difference?

---

### Post by Zone17 on 2006-10-16
I used 2 diffrent windows and did the tail in one and the ping in the other, the first time it did not show the blocks I exit and retyped and it started working! Thanks for all the help. 

I just don't get why when I am on Bit Torrent in windows with PG it shows tons of blocks and the only blocks in my log file from Moblock are those pings.

zone@zone-laptop:~$ tail -f /var/log/moblock.log
Skipping useless range: adelinatech.com
Skipping useless range: CWS
Skipping useless range: ns1/ns2.playercodec.net
Skipping useless range: www.buhartes.info|BT|Hijackers
Skipping useless range: adv549|CWS|BT|Hijackers
Skipping useless range: Pluginaccess.com/Dialeraccess.com[CWS]
Skipping useless range: Parcproductions.com
Skipping useless range: Fastsearch[Spy]
Ranges loaded: 160907
Reopening logfile.




zone@zone-laptop:~$ tail -f /var/log/moblock.log
Skipping useless range: adelinatech.com
Skipping useless range: CWS
Skipping useless range: ns1/ns2.playercodec.net
Skipping useless range: www.buhartes.info|BT|Hijackers
Skipping useless range: adv549|CWS|BT|Hijackers
Skipping useless range: Pluginaccess.com/Dialeraccess.com[CWS]
Skipping useless range: Parcproductions.com
Skipping useless range: Fastsearch[Spy]
Ranges loaded: 160907
Reopening logfile.
Blocked OUT: Microsoft,hits: 1,DST: 207.46.130.108
Blocked OUT: Microsoft,hits: 2,DST: 207.46.130.108
Blocked OUT: Microsoft,hits: 3,DST: 207.46.130.108
Blocked OUT: Microsoft,hits: 4,DST: 207.46.130.108
Blocked OUT: Microsoft,hits: 5,DST: 207.46.130.108
Blocked OUT: Microsoft,hits: 6,DST: 207.46.130.108
Blocked OUT: Microsoft,hits: 7,DST: 207.46.130.108
Blocked OUT: Microsoft,hits: 8,DST: 207.46.130.108
Blocked OUT: Microsoft,hits: 9,DST: 207.46.130.108
Blocked OUT: Microsoft,hits: 10,DST: 207.46.130.108
Blocked OUT: EDS Sweden AB,hits: 1,DST: 212.73.29.83
Blocked OUT: EDS Sweden AB,hits: 2,DST: 212.73.29.83
Blocked OUT: EDS Sweden AB,hits: 3,DST: 212.73.29.83

---

### Post by pelle.k on 2006-10-16
Well, to be perfectly honest - that's one of the many mysteries of the universe :)
I guess the pg2 list you get in windows is bigger, or... something.

> Blocked OUT: EDS Sweden AB,hits: 3,DST: 212.73.29.83
Hey, are you a fellow slay radio fan? :D

---

### Post by Ole32 on 2006-10-17
Is it possible to use blocklist files from PeerGuardian 2, eg. [http://peerguardian.sourceforge.net/lists/p2p.php](http://peerguardian.sourceforge.net/lists/p2p.php) ?

---

### Post by Bogaurd on 2006-10-17
Has anyone had this working with arno's iptables firewall script? It works fine for me, apart from one thing:

- If I run the script, it cancels all my firewall rules.
- If I re-run the firewall, it cancels the moblock rules!

Does anybody know what I need to do to get these 2 living peacefully together? :)

Thanks!

---

### Post by Ole32 on 2006-10-18
> **Ole32 said:**
> Is it possible to use blocklist files from PeerGuardian 2, eg. [http://peerguardian.sourceforge.net/lists/p2p.php](http://peerguardian.sourceforge.net/lists/p2p.php) ?

I (at [http://moblock.berlios.de/README-0.8](http://moblock.berlios.de/README-0.8)) found, that MoBlock should be able to use blocklist from PeerGuardian2 . 
Could you pls help me, how to setup MoBlock to use [www.bluetack.co.uk](www.bluetack.co.uk) (I already have in /etc/cron.daily/moblock-nfq: BLOCKLISTS="nipfilter.dat ads-trackers-and-bad-pr0n" ) and [http://peerguardian.sourceforge.net/lists/p2p.php](http://peerguardian.sourceforge.net/lists/p2p.php) lists together?

---

### Post by pelle.k on 2006-10-19
Bogaurd: Not at the moment, no. If you want to run a firewall, then use firehol.

Ole32: This last link you provided, [http://peerguardian.sourceforge.net/lists/p2p.php](http://peerguardian.sourceforge.net/lists/p2p.php) is level1 blocklist, and should be included in nipfilter.dat
How many ranges are loaded when you run moblock?

---

### Post by Ole32 on 2006-10-20
> **pelle.k said:**
> Ole32: This last link you provided, [http://peerguardian.sourceforge.net/lists/p2p.php](http://peerguardian.sourceforge.net/lists/p2p.php) is level1 blocklist, and should be included in nipfilter.dat
How many ranges are loaded when you run moblock?

I would like to use [http://peerguardian.sourceforge.net/lists/gov.php](http://peerguardian.sourceforge.net/lists/gov.php) and [http://peerguardian.sourceforge.net/lists/p2p.php](http://peerguardian.sourceforge.net/lists/p2p.php) from PeerGuardian together with blocklists from Bluetack.co.uk

Now I have this in MoBlock (/etc/cron.daily): BLOCKLISTS="nipfilter.dat ads-trackers-and-bad-pr0n" 

In Windows with PeerGuardian, when I use eg. eMule, I see many blocked attemps per minute.
But in Linux with MoBlock and settings I mentioned above, there are almost no blocked connections  in /var/log/moblock.log (although I am connected to the same server as in Windows!).
So I think, that blocklist used from Bluetack aren't so good as the PeerGuardian's...

---

### Post by termite on 2006-10-22
Today's update in edgy seems to break moblock: there's an unsatisfied dependence on libnetfilter-queue (requires >=0.0.12, has 0.0.11-1.1)

Any suggestions?

---

### Post by omajosi on 2006-10-22
There seems to be a version difference between debian and ubuntu,this seems to create all the problems
I intended a new install,this is what I got:

moblock-nfq:
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
 Depends: libnetfilter-queue1 (>=0.0.12) but it is not installable
 Depends: libnfnetlink1 (>=0.0.16) but it is not installable
 Depends: libnetfilter-queue1  but it is not installable

using Mepis,which is ubuntu dapper drake based
I hope this will help

---

### Post by lp7413 on 2006-10-22
I had the same problem in Edgy with the new moblock update.  Seems that the naming convention has changed on those two dependencies it needs.  Ubuntu is using: libnetfilter-queue and libnfnetlink0   On the debian side of things, the packages are now called libnetfilter-queue1 and libnfnetlink1.   I am guessing that its because moblock is designed for debian, I havent seen any changelogs for moblock-nfq yet either.  If ubuntu will upgrade those two packages here before edgy is final, it will work, otherwise your still going to get something like:

The following packages have unmet dependencies:
  moblock-nfq: Depends: libnetfilter-queue1 (>= 0.0.12) but it is not installable
               Depends: libnfnetlink1 (>= 0.0.16) but it is not installable
               Depends: libnetfilter-queue1 but it is not installable
E: Broken packages

I will look more into the moblock-nfq deb package and see if I can change the deps back to the same names they were previously and see what the outcome will be.  I will let you know what happens.

---

### Post by lp7413 on 2006-10-22
I took a look at all the moblock sources, in order to build a new moblock package I also need some lib/dev packages that arent available in the edgy repos.  It would be nice if the guy working on the moblock package would make some edgy ports of the libnfnetlink1 and libnetfilterqueue1 packages.  Once that happened the package would upgrade just fine without breaking.  I suggest just keeping moblock 0.8-12 until edgy releases the debian compatible versions of the above files, or wait for the moblock repos to backport them for us.  BTW according to the moblock 0.8-13 changelog, the only thing that changed was the dependency names, no extra features or anything like that have been implemented afaik.

---

### Post by Michaeldaley on 2006-10-22
I'm having the same problem with Dapper.  I just reinstalled my OS and when I went to install moblock I couldn't.

---

### Post by lp7413 on 2006-10-22
> **Michaeldaley said:**
> I'm having the same problem with Dapper.  I just reinstalled my OS and when I went to install moblock I couldn't.

You need to install the moblock 0.8-12 debian package instead of the 0.8-13 and wait until there is a patch for ubuntu to work with >0.8-12.  

I have noticed also that 0.8-12 deb package has been completely removed from the repo, if you want the 0.8-12 package and its required deps, please join #linuxsociety on irc.freenode.net and I (ttyfscker) will send you the deb packages through dcc.  I would attach them here but debs are not allowed to be posted.. It will be much easier to do on IRC.

---

### Post by termite on 2006-10-22
> debs are not allowed to be posted
Compress them as a .tar.gz, then post.  That's what most people here do.

---

### Post by lp7413 on 2006-10-22
> **termite said:**
> Compress them as a .tar.gz, then post.  That's what most people here do.

I saved the file as a tar archive, it contains libnfnetlink0_0.0.14-1.1_i386.deb
moblock-nfq_0.8-12_i386.deb
libnetfilter-queue_0.0.11-1.1_i386.deb

Just untar this archive.  Be aware that the relative path is still in the tar archive and it is bound to /var/cache/apt/archive

After you have the files extracted from the tarball use dpkg -i *.deb (but be sure you put just those 3 files in a directory by their self.  do not run that command from /var/cache/apt/archive directory!!  be sure you have the 3 files in their own directory..

---

### Post by omajosi on 2006-10-23
Thanks a lot for the files,it will help all of us till somebody comes out with a patch or whatever.

---

### Post by NiksaVel on 2006-10-23
ahem...  I was just doing a new install of fluxbuntu and ran into the same problem with dependancies... 

I installed from the above deb files (thanks!), BUT I don't see moblock actually blocking anything... 

it just skips loads of ranges, than says:

> Ranges loaded: 2022
Reopening logfile.


and hangs at that...  nothing new happens, it doesn't report any blocks...  I tries pinging [www.microsoft.com](www.microsoft.com) and it was 100% packet loss...  however no entries into the moblock.log file


I had firestarter installed when I installed moblock, than noticed that it was a no-no... so I removed firestarter....  is that the cause of moblock not working?

thanks!

---

### Post by omajosi on 2006-10-23
Has anybody ever tried linblock in Ubuntu??,it can be found here:[http://dessent.net/linblock/](http://dessent.net/linblock/)
It's supposed to do the same as moblock and peerguardian

---

### Post by NiksaVel on 2006-10-23
I take back my previous post - after a few hours of trailing the log file I got a few blocks...

anyways... is the 2020 an adequate number of ranges loaded?

---

### Post by skipo on 2006-10-24
> **Ole32 said:**
> I would like to use [http://peerguardian.sourceforge.net/lists/gov.php](http://peerguardian.sourceforge.net/lists/gov.php) and [http://peerguardian.sourceforge.net/lists/p2p.php](http://peerguardian.sourceforge.net/lists/p2p.php) from PeerGuardian together with blocklists from Bluetack.co.uk


I was thinking the same thing. Would that be possible?

---

### Post by pelle.k on 2006-10-24
I wrote this a while ago...
> Ole32: This last link you provided, [http://peerguardian.sourceforge.net/lists/p2p.php](http://peerguardian.sourceforge.net/lists/p2p.php) is level1 blocklist, and should be included in nipfilter.dat
How many ranges are loaded when you run moblock?
Apparently, the nipfilter.dat no longer does what it is supposed to, and that is include level1 level2 and other stuff..
Edit /etc/cron.d/moblock-nfq and use the old line with blocklists which is commented out just above the "new" one (i think)

As of now, moblock is a mess. Wait for a new version to come out, or use an old version (and make the necessary changes to load all blocklists).

---

### Post by NiksaVel on 2006-10-24
I don't have that file...

> niksavel@leddl-fluxbuntu:/$ sudo nano /etc/cron.d/moblock-nfq
Password:
niksavel@leddl-fluxbuntu:/$ cd /etc/cron.d
niksavel@leddl-fluxbuntu:/etc/cron.d$ ls
anacron
niksavel@leddl-fluxbuntu:/etc/cron.d$ 

---

### Post by lp7413 on 2006-10-25
> **NiksaVel said:**
> I don't have that file...

it should be in /etc/cron.daily/moblock-nfq

---

### Post by NiksaVel on 2006-10-25
true...  thanks!

---

### Post by termite on 2006-10-25
For those of you using KDE, here is a superkaramba theme that will monitor your moblock log file.

Suggestions welcome.

---

### Post by shookone on 2006-10-27
Sup guys.

Well im back from my minor setback. I wanna thank for the help you guys gave me before in getting moblock up and running with firehol. But i am having problems setting my firehol to work with my other devices.

My comp has two NICs. eth0 and eth1. 
I have a xbox connected to eth1. 

With the help of this thread i was able to create this file:

```
version 5

#specify ports here
## type: client or server
## label: label port
## type/port: tcp or udp and port (Ex. tcp/80 or udp/300000
#format: type_label_ports="type/port"

server_xlink_ports="udp/37500"
server_xlinkx_ports="udp/34522"
server_1024_ports="udp/1024"
client_xlink_ports="default"

dnat to 192.168.100.2:37500 inface eth0 proto udp dport 37500

# moblock settings
iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE

# The network of eth1
home_ips=192.168.100.2/24


# Your internet interface

interface eth0 internet src not "${home_ips} ${UNROUTABLE_IPS}"

        protection strong 10/sec 10
        server "ssh ftp" accept # you dont need xlink here
        # This will send http traffic directly to accept instead of moblock thus whitelisting it...
        client "http https" accept
        client all MOBLOCK

# Local network

interface eth1 home src "${home_ips}" #this is only in your lan...
        policy accept
        client all accept
        server all accept # you can safely remove this comment

#Routing information

router home2internet inface eth0 outface eth1
        masquerade reverse
        client all accept
        server xlink accept # xlink only here (this is the server)
```

The daemon communicates with the following:

LAN:
UIBind = :34522     #  UDP Communicates with UI

WAN:
OrbPort = 34525     #  UDP/TCP Daemon probes this port to talk to orbitals (udp/tcp)
OrbDeepPort = 34523 #  UDP Daemon probes this port to talk to deep res servers
EngineBind = :37500 #  UDP <- Needs port forwarding if NAT.


The daemon on my computer communicates to the xbox(lan) via port 34522 and communicates with orbital servers(WAN) via port 35700.

What I see happening is that the initial communication gets completed, but when going into arena's there are no more oribital responces. The request make it to my linux box, according to traffic logs. But none are returned to my xbox. 

Either im losing orbital connectivity or firehol is blocking. Never the less I am able to connect properly without firehol.

At first i thought it was the protection. But then i removed the protection and was able to communicate much better but after several tests im unable to see responces from orbital and im unable to see people when i actually intiate a game.


My current configuration is moblock plugged into FireHOL. FireHOL configuration is above. I can post my kaid.conf if needed. But basically the port settings are posted above.

---

### Post by shookone on 2006-10-27
I experience the same when running a client locally on the machine running firehol and kaid daemon. Same exact thing. I can post network traffic logs if needed.

---

### Post by pelle.k on 2006-10-27
Sorry shookone! I forgot about your PM. I was too tired to answer you when i first saw it...
These config files always hurt my brain :)
Why have you got```
server_xlinkx_ports="udp/34522"
server_1024_ports="udp/1024"
``` if you are not using them in the interfaces?

If your deamon (on computer) is using xlink port against internet, shouldnt xlink be a server in "internet" interface?

You're not making any sense i'm afraid. You need to clarify like this:

xbox:
which port need to be accessed from the internet? (I assume some of them only use lan = already open...)

computer:
which ports does the daemon need to be accessed from the internet (not from lan, because lan is already fully open...)

---

### Post by Naegling23 on 2006-10-27
So Im running edgy i386, and when I tried to install moblock-nfq but It was giving me a break install.  moblock-ipq installed fine, however.  This seemed odd to me since moblock-ipq seems to be for older systems.  Is this normal, or am I doing something wrong?  

Also, is moblock-ipq as up to date, and secure as moblock-nfq?

---

### Post by shookone on 2006-10-28
> **pelle.k said:**
> Sorry shookone! I forgot about your PM. I was too tired to answer you when i first saw it...
These config files always hurt my brain :)
Why have you got```
server_xlinkx_ports="udp/34522"
server_1024_ports="udp/1024"
``` if you are not using them in the interfaces?

If your deamon (on computer) is using xlink port against internet, shouldnt xlink be a server in "internet" interface?

You're not making any sense i'm afraid. You need to clarify like this:

xbox:
which port need to be accessed from the internet? (I assume some of them only use lan = already open...)

computer:
which ports does the daemon need to be accessed from the internet (not from lan, because lan is already fully open...)


Sorry about that pelle.k was probably drinking and such that evening :).

Xbox:
The xbox has no direct port to access from the internet. Only needs to communicate to my pc via port 34522. xbox does use the internet for my web browsing apps.

Computer:
ports needed by the internet:

kaid = 35700, 34525, and 34523


----

The above mentioned ports i have them defined just in case i needed to use them. Is that a bad idea?

I'm basically having a problems staying connected to the orbital servers. It connects but after so much data is received it just times out. It works fine with firehol down.

There is alot of traffic coming into my lan. Ping responces ... people enter and leaving arena... so protection can't allow to drop packets.

---

### Post by sakis on 2006-10-28
> **termite said:**
> Today's update in edgy seems to break moblock: there's an unsatisfied dependence on libnetfilter-queue (requires >=0.0.12, has 0.0.11-1.1)

Any suggestions?
Do we have a solution? ](*,)

---

### Post by pelle.k on 2006-10-29
> The xbox has no direct port to access from the internet. Only needs to communicate to my pc via port 34522
Why have you nat:ed port 37500 to your xbox (from the internet) then? If what you say is true, This is what it should look like;
```
version 5

#specify ports here
## type: client or server
## label: label port
## type/port: tcp or udp and port (Ex. tcp/80 or udp/300000
#format: type_label_ports="type/port"

server_kaid1_ports="udp/37500"
client_kaid1_ports="default"

server_kaid2_ports="udp/34525"
client_kaid2_ports="default"

server_kaid3_ports="udp/34523"
client_kaid3_ports="default"

iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE


# The network of eth1
home_ips=192.168.100.2/24


# Your internet interface
interface eth0 internet src not "${home_ips} ${UNROUTABLE_IPS}"
        protection strong 10/sec 10
        server "ssh ftp kaid1 kaid2 kaid3" accept
        # This will send http traffic directly to accept instead of moblock thus whitelisting it...
        client "http https" accept
        client all MOBLOCK

# Local network
interface eth1 home src "${home_ips}" #this is only in your lan...
        policy accept
        client all accept
        server all accept

#Routing information
router home2internet inface eth0 outface eth1
        masquerade reverse
        client all accept
```

---

### Post by shookone on 2006-10-29
pelle.k.

you helped me put that setup together. I now understand that this is not port forwarding as if i had a route/modem connecting to my machine. This computer is my firewal and it is also running daemons. I was trying to port forward eth0 (WAN) to eth1 (LAN)

eth0 = external ip
eth1 = local net (192.168.100.2)
xbox = 192.168.100.10

I just tried your setup and it connects but my problem still continues. It appears that im receiving information then it stops. 

I am supposed to receive lots of information, ping request and who ever enters and leaves the arena. I think that its dropping packets. What would happen if i remove protection? is it a big difference.

> **pelle.k said:**
> Why have you nat:ed port 37500 to your xbox (from the internet) then? If what you say is true, This is what it should look like;
```
version 5

#specify ports here
## type: client or server
## label: label port
## type/port: tcp or udp and port (Ex. tcp/80 or udp/300000
#format: type_label_ports="type/port"

server_kaid1_ports="udp/37500"
client_kaid1_ports="default"

server_kaid2_ports="udp/34525"
client_kaid2_ports="default"

server_kaid3_ports="udp/34523"
client_kaid3_ports="default"

iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE


# The network of eth1
home_ips=192.168.100.2/24


# Your internet interface
interface eth0 internet src not "${home_ips} ${UNROUTABLE_IPS}"
        protection strong 10/sec 10
        server "ssh ftp kaid1 kaid2 kaid3" accept
        # This will send http traffic directly to accept instead of moblock thus whitelisting it...
        client "http https" accept
        client all MOBLOCK

# Local network
interface eth1 home src "${home_ips}" #this is only in your lan...
        policy accept
        client all accept
        server all accept

#Routing information
router home2internet inface eth0 outface eth1
        masquerade reverse
        client all accept
```

---

### Post by cd-r80 on 2006-10-29
Using Xubuntu 6.06. I cannot install. Where correct repos? I got only:
apt-get install moblock-nfq
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  moblock-nfq: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
               Depends: libnetfilter-queue1 (>= 0.0.12) but it is not installable
               Depends: libnfnetlink1 (>= 0.0.16) but it is not installable
               Depends: libnetfilter-queue1 but it is not installable
E: Broken packages

---

### Post by pelle.k on 2006-10-29
> **shookone said:**
> 
I was trying to port forward eth0 (WAN) to eth1 (LAN)

eth0 = external ip
eth1 = local net (192.168.100.2)
xbox = 192.168.100.10
OMG, can't belive i didn't see that before. You cant NAT a port to a sub-network so that it is valid for any machine on 192.168.100.2-99. You have to choose a target. like you xbox for example. not 192.168.100.2 but rather 192.168.100.10 if you wanted the port forwarded there. But this is still not important as you say your xbox is expecting no connections from the internet...

Shouldn't these ports be included```

server_kaid4_ports="udp/37501"
client_kaid4_ports="default"

server_kaid5_ports="udp/34522"
client_kaid5_ports="default"
```

As you might have figured by now out, this is not an moblock issue though...

---

### Post by shookone on 2006-10-29
You are correct. This isn't moblock issue. But using moblock led me to firehol ... which is stopping something i could do without a firewall.

Unless there is another option to use a moblock inconjunction with another firewall by all means please let me know. But i was using ubuntu-firewall prior to using moblock. So if i'm not in the right place to discuss my issue let me know.. I have opened up a thread but no replies.. just views.

I'll look into those other ports... something is not making sense here.

shook-

---

### Post by spockrock on 2006-10-30
> **cd-r80 said:**
> Using Xubuntu 6.06. I cannot install. Where correct repos? I got only:
apt-get install moblock-nfq
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  moblock-nfq: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
               Depends: libnetfilter-queue1 (>= 0.0.12) but it is not installable
               Depends: libnfnetlink1 (>= 0.0.16) but it is not installable
               Depends: libnetfilter-queue1 but it is not installable
E: Broken packages

I have the same problem, preventing me from upgrading.

---

### Post by shookone on 2006-10-30
[COLOR="Red"][CENTER]xlink issue SOLVED[/CENTER][/COLOR]

My problems with kaid was not really related to firehol and moblock what so ever. 

I was thinking about my ip setup and realized the port i chose to use was on the cable modems network. So that subnet was messing me up. I switched to a different subnet and now xbox sees all games on xlink. Sorry for the headaches and thanks for the 101 with firehol. 

i have a Webstar cable modem that uses the subnet 192.168.100.0 (ISP SETUP?) and my network was in the 100's for some reason. Bad luck?. 

So i went to traditional 192.168.1.0 network and im all up and running.

---

### Post by pelle.k on 2006-10-30
way to go! :)
It's always like that. You try to solve this _evil_ problem, and it always turn out you were doing it the wrong way :P

Spookrock, and all other having problems installing moblock, [http://www.ubuntuforums.org/showpost.php?p=1650147&postcount=239](http://www.ubuntuforums.org/showpost.php?p=1650147&postcount=239)
This is not a very nice solution, but hey... it'll get you by for now.

---

### Post by spockrock on 2006-10-31
well luckily for me I was able to install it on edgy beta, however it wont let me upgrade but thanks for the debs.

---

### Post by shookone on 2006-10-31
> **pelle.k said:**
> way to go! :)
It's always like that. You try to solve this _evil_ problem, and it always turn out you were doing it the wrong way :P

Spookrock, and all other having problems installing moblock, [http://www.ubuntuforums.org/showpost.php?p=1650147&postcount=239](http://www.ubuntuforums.org/showpost.php?p=1650147&postcount=239)
This is not a very nice solution, but hey... it'll get you by for now.

I think i may have spoke too soon. I get drops still, i tried it with firehol off and got excited. But i am going to try logging features to see what exactly is happening. Any tips for logging. Applications to help me view log files and such? log settings.?

---

### Post by Ole32 on 2006-10-31
> **pelle.k said:**
> I wrote this a while ago...

Apparently, the nipfilter.dat no longer does what it is supposed to, and that is include level1 level2 and other stuff..
Edit /etc/cron.d/moblock-nfq and use the old line with blocklists which is commented out just above the "new" one (i think)

As of now, moblock is a mess. Wait for a new version to come out, or use an old version (and make the necessary changes to load all blocklists).

OK, I'll try 
BLOCKLISTS="ads-trackers-and-bad-pr0n level1 level2  Microsoft  spyware bogon hijacked temp"

---

### Post by pelle.k on 2006-10-31
> **Ole32 said:**
> OK, I'll try 
BLOCKLISTS="ads-trackers-and-bad-pr0n level1 level2  Microsoft  spyware bogon hijacked temp"
level1 and level2 should be enough in most cases. bogon contains LAN ips (don't ask me why) so i wouldn't use it.

---

### Post by pelle.k on 2006-10-31
> **shookone said:**
> I think i may have spoke too soon. I get drops still, i tried it with firehol off and got excited. But i am going to try logging features to see what exactly is happening. Any tips for logging. Applications to help me view log files and such? log settings.?

Use ulog in firehol. There are instructions about it if you search these forums.

---

### Post by Michaeldaley on 2006-11-03
Wouldn't it be easier to add the Debian repository which has what the dependency is looking for, install it the old way and then delete that repository?  Just a thought, I'm somewhat new to linux and still learning.

I added these:
deb [ftp://sunsite.cnlab-switch.ch/mirror/debian/](ftp://sunsite.cnlab-switch.ch/mirror/debian/) unstable main contrib non-free
deb-src [ftp://sunsite.cnlab-switch.ch/mirror/debian/](ftp://sunsite.cnlab-switch.ch/mirror/debian/) unstable main contrib non-free

and then installed moblock, I ignored the auto update icon, and then I took them out of my list.

Is this kosher, or is it going to mess everything up?


BTW...How many ranges are supposed to load?  I get 2023, is that the full amount or am I missing lists?

---

### Post by pelle.k on 2006-11-04
> Wouldn't it be easier to add the Debian repository which has what the dependency is looking for, install it the old way and then delete that repository? Just a thought, I'm somewhat new to linux and still learning. Then i would say you're learning fast. Good initiative. This is one way to get around it, even though ubuntu has it's own version of libc, probably for some reason. This way, you can't blame ubuntu if your computer becomes unstable in any way, but i guess that can be said of just about any software ;)

```
moblock-nfq: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
```

---

### Post by Michaeldaley on 2006-11-04
The default blocklist is definitely messed up.  I changed mine to the following:
BLOCKLISTS="ads-trackers-and-bad-pr0n level1 level2  Microsoft  spyware "

and now I get 163,405 ranges instead of 2023.

How come it doesn't block the default ranges it used to?

---

### Post by sakis on 2006-11-06
> **Michaeldaley said:**
> Wouldn't it be easier to add the Debian repository which has what the dependency is looking for, install it the old way and then delete that repository?  Just a thought, I'm somewhat new to linux and still learning.

I added these:
deb [ftp://sunsite.cnlab-switch.ch/mirror/debian/](ftp://sunsite.cnlab-switch.ch/mirror/debian/) unstable main contrib non-free
deb-src [ftp://sunsite.cnlab-switch.ch/mirror/debian/](ftp://sunsite.cnlab-switch.ch/mirror/debian/) unstable main contrib non-free

and then installed moblock, I ignored the auto update icon, and then I took them out of my list.
Nice, never thought about that... thank you :-D 

> **pelle.k said:**
> Then i would say you're learning fast. Good initiative. This is one way to get around it, even though ubuntu has it's own version of libc, probably for some reason. This way, you can't blame ubuntu if your computer becomes unstable in any way, but i guess that can be said of just about any software ;)

```
moblock-nfq: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
```
I installed that way the latest version in Edgy and everything works just fine! :mrgreen: 

Can you add that in your first message, if someone wants to add the latest version in Edgy? ;)

---

### Post by shookone on 2006-11-11
Those deb files are only if you are installing fresh in to edgy right.. i have dapper and i installed it.

---

### Post by forger on 2006-11-11
the debian source way is the fastest and the most risky one, but it does work :P

---

### Post by Michaeldaley on 2006-11-11
I don't think it's risky, I've been stable for the past week and Moblock is running great.  Just make sure that if you try this method, you must remove the deb sources before running Ubuntu's update feature (because just about every file in these sources is a higher version than Ubuntu uses).  This should work for dapper too.

Change your blocklist too, I don't think moblock's default works anymore.  It should read:
BLOCKLISTS="ads-trackers-and-bad-pr0n level1 level2 Microsoft spyware "

---

### Post by lp7413 on 2006-11-11
> **forger said:**
> the debian source way is the fastest and the most risky one, but it does work :P

Honestly, I would never add an official debian repo to your ubuntu sources.list.. If it installs libc6 you might get away fine for now, but when you try to upgrade ubuntu while your using external packages, then you might get a big list of errors.  It might work now, but break later on, I would not suggest using the debian sources.list period.  Its asking for trouble, the files i posted a few weeks ago work fine, and get the job done, there is absolutely no need in upgrading to the latest and greatest release of moblock-nfq, the only change was a dep that fixed debian installs, and broke ubuntu installs..  I hope those of you who might have installed the debian sources dont end up with problems later on down the road.  I'm just posting my two sense worth, its just not good practice, and a lot of people don't need to get in the habit of doing things like that.  sorry for the long paste, just concerned :)

---

### Post by foxy123 on 2006-11-12
I agree that installing moblock from Debian repo is not a good idea. lib6c is one of the libraries after all. Saying that I have to admit that I lived with Debian's libraries on Hoary without any major issues.

I tried to build moblock from source but failed in doing it. To build it you need two development libraries: libnetfilter-queue and libnfnetlink, which are not in Ubuntu. So I put the source repo in my sources.list:
```
deb-src ftp://sunsite.cnlab-switch.ch/mirror/debian/ unstable main contrib non-free
```

and did the following:
```
sudo apt-get build-dep libnfnetlink
apt-get source libnfnetlink
cd libnfnetlink-0.0.16
dpkg-buildpackage -rfakeroot
```

But it the end it was not built:
```
touch install-stamp
dh_testdir -i
dh_testdir: I have no package to build
make: *** [binary-indep] Error 1

```
Any idea why it that?

---

### Post by moopoo on 2006-11-12
Hi, 

I used pelle.k's temporary solution to install moblock on edgy. But I have the bad feeling, that the block-lists don't update daily. I was browsing through my log-files (auth.log etc) and only found those updates I did manually (sudo /etc/cron.daily/moblock-nfq). My manual updates always download new lists.

So, there are a few questions:

a) How can I find out, if the updates work?

b) If they don't work, what did I possibly do wrong and what can be done?

If you need more data, please let me know.

Thanks in advance,

yours,
moopoo

---

### Post by NiksaVel on 2006-11-13
I have the one installed from debs, but it seems to be killing my internet connection - at least it seems to be connected - 

I have a terminal open all the time with the tail command so I can track what it's blocking in real time...  


starting the computer everythng works as normal, HOWEVER from time to time I get to the office (i.e. every two to three days) and the computer is not connected to the internet I can't get any pings or anything, and the terminal with the tail command shows that moblock has just been updated ----  is it moblock or maybe cron and is it even at all connected I just don't know, but I could really use some help on the subject.

Through ifconfig I see that the network adapter is still correctly configured with the static IP and I even tried ifconfig down and up again, but nothing changes - I need to REBOOT (not just restart X) to get net again....   

PLEASE HELP!!!](*,)

---

### Post by Michaeldaley on 2006-11-13
> **lp7413 said:**
> Honestly, I would never add an official debian repo to your ubuntu sources.list.. If it installs libc6 you might get away fine for now, but when you try to upgrade ubuntu while your using external packages, then you might get a big list of errors.  

Nobody every suggested leaving that deb in the source list, in fact the importance of removing it after installation was stated several times.

---

### Post by Mechanical on 2006-11-13
> **Michaeldaley said:**
> Nobody every suggested leaving that deb in the source list, in fact the importance of removing it after installation was stated several times.

I am a bit confused on this now.  I did just as was suggested by adding the debian source list temporarily to get moblock installed and then removing it immediately after moblock was on my system.  I did no upgrades with these source lists.  Is this still potentially dangerous to my ubuntu installation?

---

### Post by foxy123 on 2006-11-13
> **Mechanical said:**
> I am a bit confused on this now.  I did just as was suggested by adding the debian source list temporarily to get moblock installed and then removing it immediately after moblock was on my system.  I did no upgrades with these source lists.  Is this still potentially dangerous to my ubuntu installation?

In addition to moblock it will upgrade some of your system libraries, which potentially may cause certain problems in future.

---

### Post by NiksaVel on 2006-11-14
> I have the one installed from debs, but it seems to be killing my internet connection - at least it seems to be connected -

I have a terminal open all the time with the tail command so I can track what it's blocking in real time...


starting the computer everythng works as normal, HOWEVER from time to time I get to the office (i.e. every two to three days) and the computer is not connected to the internet I can't get any pings or anything, and the terminal with the tail command shows that moblock has just been updated ---- is it moblock or maybe cron and is it even at all connected I just don't know, but I could really use some help on the subject.

Through ifconfig I see that the network adapter is still correctly configured with the static IP and I even tried ifconfig down and up again, but nothing changes - I need to REBOOT (not just restart X) to get net again....

PLEASE HELP!!!


here's a bit more info...   sometimes when cron starts updating firefox, I can see in my terminal with the tail command on moblock log that it starts running loads of lines with skipped range and duplicate range etc...


in the end it finishes with several lines:
Ranges loaded
Merged ranges
Skipped useless range
NFQUEE: Binding to queue '0'


this is all good and nice and works...   however, I loose all internet connection due to moblock on some occasions when it's updating, I tried updating it manually several times in a row and what I came up is that when it KILLS my internet connection, the updating process ends at Ranges loaded line...  it never gets to merged ranges, skipped and nfquee...

now...  what can I do about it exept turn of the auto updating via cron?


thanks!


Addon:   The only way to get back my network is to killall moblock and restart it...  or reboot

---

### Post by Scream72 on 2006-11-14
Hello. :)

I have amule and lopster connection problem with moblock.

Amule servers "low id" when moblock works, if i stop moblock and reconnecting, the id value is high....same thing with lopster, traffic is low and upload is drop for all ip...


Router rules is ok (atlantis web share), firewall and virtual server(dmz able on ip adress of ethernet card).

Iptables rules :
> 
 sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
MOBLOCK_IN  all  --  anywhere             anywhere            state NEW

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
MOBLOCK_FW  all  --  anywhere             anywhere            state NEW

Chain MOBLOCK_FW (1 references)
target     prot opt source               destination
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_IN (1 references)
target     prot opt source               destination
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_OUT (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
MOBLOCK_OUT  all  --  anywhere             anywhere            state NEW

 

Moblock is installed and configured by this tutorial(with default blocklist on line 34).
(Thanks pelle.K ;) )

> 

Ranges loaded: 191101
Merged ranges: 243
Skipped useless ranges: 7065
NFQUEUE: binding to queue '0'



Other users have this problem?

Thanks :) (and excuse my english).

---

### Post by pelle.k on 2006-11-14
I am sorry for not helping you all out in the thread since some time back, especially with recent events in mind. I have been working too much lately. Also i was kindof dissappointed with the latest ubuntu release (edgy) so i've been running arch most of the time.

We should really put our own repository up, with moblock build specific to ubuntu. Or at least build it for ubuntu and post the debs here, since the version on moblock-deb is turning away from ubuntu.
If, and i say _if_, i have the time i will build it myself as soon as possible.

[edit]If you wan't to remove the updater, then 'sudo chmod -x /etc/cron.daily/moblock-nfq'
This will make it "not" executable. the opposite of +x that is...
I belive that is the most common reason for many of the latest moblock issues
To manually run this update script 'sudo sh /etc/cron.daily/moblock-nfq' then reboot the computer (or stop/start the deamon) to have it load the ranges in a clean fasion[/edit]

---

### Post by pelle.k on 2006-11-14
> Amule servers "low id" when moblock works, if i stop moblock and reconnecting, the id value is high
OK, then you have a connection, but uploads are being dropped? I can't really say for sure what is the problem. It shouldn't be happening. Either way you can filter ip:s in amule with a nipfilter.dat list. get it at bluetack.co.uk
That's it... for now.

---

### Post by Michaeldaley on 2006-11-16
> **foxy123 said:**
> In addition to moblock it will upgrade some of your system libraries, which potentially may cause certain problems in future.

If you remove the debs or even put a "#" in front of them and then sudo apt-get update, there is no chance of upgrading the system libraries, except for the one file which moblock depends on.  The way you phrase that it makes it sound as if numerous files are being changed, when it really only downloads the one file.  I agree with Pelle though, we really need to start our own repository, but even if we did it would essentially do the same thing I did, unless someone goes into moblock and alters its dependencies.  As of now we can't get around using a different file than that which is found in the Ubuntu repository.

---

### Post by foxy123 on 2006-11-16
> **Michaeldaley said:**
> If you remove the debs or even put a "#" in front of them and then sudo apt-get update, there is no chance of upgrading the system libraries, except for the one file which moblock depends on.  The way you phrase that it makes it sound as if numerous files are being changed, when it really only downloads the one file.  I agree with Pelle though, we really need to start our own repository, but even if we did it would essentially do the same thing I did, unless someone goes into moblock and alters its dependencies.  As of now we can't get around using a different file than that which is found in the Ubuntu repository.

because of dependency. moblock depends on some libraries like libc6 and will update it to Debian version if you use Debian repo to install moblock. t is not a big deal, but people should be aware about it.

---

### Post by roadboy on 2006-11-17
hi all

i've problems with moblock. i'm using it for home network with firehol. i've some important rules in firehol config. i've ports 25 and 53 open but i only want home network to access them. the problem is when i activate moblock, the blocking rules don't work. when i nmap, i can see all of the open ports and i can connect them. but when moblock isn't working, my rules do what they have to do. i can't see the open ports which i don't want and also i can't connect them.

i'm running edgy and here is my firehol.conf

```
version 5

iptables --new moblock
iptables -A moblock -j NFQUEUE

server_e2dk_ports="tcp/3604 udp/3608"
client_e2dk_ports="default"

server_kad_ports="tcp/8466 udp/8466"
client_kad_ports="default"

server_mlnet_ports="tcp/4080"
client_mlnet_ports="default"

interface ppp0 internet
    policy drop
    protection strong

    server ident reject with tcp-reset
    server "ftp ssh http" accept with limit 5/s 50 overflow drop
    server "e2dk kad mlnet" moblock

    client all accept

interface eth0 home
    policy accept

    server all accept
    client all accept
```

---

### Post by OrganicPanda on 2006-11-17
Hey cool guide, just wondering after installing from the 3 debs will my software be automatically protected, for instance I use ktorrent, will the IP's on my blocklist be blocked from use in ktorrent and other BT/P2P programs?

---

### Post by pelle.k on 2006-11-18
Roadboy: It's very important that moblock starts first, then firehol. This happens at bootup, so no worries about that. If you want to restart moblock you _have_ to restart firehol after that as well. That _might_ be the problem. I dont know. I suggest you do what i wrote some posts above to also remove the automatic updater,as it might restart moblock without restarting firehol afterwards.> If you wan't to remove the updater, then 'sudo chmod -x /etc/cron.daily/moblock-nfq'
This will make it "not" executable. the opposite of +x that is...
I belive that is the most common reason for many of the latest moblock issues
OrganicPanda: Yes, you >should< be completely protected... As long as you don't install an iptables firewall that will mess up the rules that make moblock inspect your traffic.

---

### Post by moopoo on 2006-11-18
> Hi,

I used pelle.k's temporary solution to install moblock on edgy. But I have the bad feeling, that the block-lists don't update daily. I was browsing through my log-files (auth.log etc) and only found those updates I did manually (sudo /etc/cron.daily/moblock-nfq). My manual updates always download new lists.

So, there are a few questions:

a) How can I find out, if the updates work?

b) If they don't work, what did I possibly do wrong and what can be done?

If you need more data, please let me know.

Thanks in advance,

yours,
moopoo

BUMP
(Moopoo hopes this way of bumping doesn't bother anyone.)

---

### Post by pelle.k on 2006-11-18
if you can execute the script manually, and it does work; there's nothing wrong with the cron job.

---

### Post by jamesford on 2006-11-18
ive given up on the /etc/cron.daily/moblock-nfq instead i have my own script which is basically a copy of the moblock-nfq that i run daily via crontab. it sends me an email telling me the update was successful etc. it probably does the same with the cron.daily one but im not convinced so im using the crontab way to make sure and ive deleted the cron.daily one.
to read the email that u get after each update u need to install the package called mailx (choose local only and the default domain or host or what its called when it asks u to configure) and then type 'mail' in terminal - it may not work until you receive the first system mail

---

### Post by moopoo on 2006-11-19
thanks to both of you. maybe i will have a look at the mail-solution later.

---

### Post by clandestiny on 2006-11-19
> **NiksaVel said:**
> I have the one installed from debs, but it seems to be killing my internet connection - at least it seems to be connected - 

I have a terminal open all the time with the tail command so I can track what it's blocking in real time...  


starting the computer everythng works as normal, HOWEVER from time to time I get to the office (i.e. every two to three days) and the computer is not connected to the internet I can't get any pings or anything, and the terminal with the tail command shows that moblock has just been updated ----  is it moblock or maybe cron and is it even at all connected I just don't know, but I could really use some help on the subject.

Through ifconfig I see that the network adapter is still correctly configured with the static IP and I even tried ifconfig down and up again, but nothing changes - I need to REBOOT (not just restart X) to get net again....   

PLEASE HELP!!!](*,)

I have been having a similar problem.  After some time of having moblock running, the host machine loses the ability to originate or accept any connections.

I've traced it down to iptables.  (I noticed during a reboot to reestablish connectivity that something in the shutdown mentioned that there were gobs of queued packets [or something like that] disposed of from iptables.)  In talking to the office *nix guru, we devised a plan to diagnose this, and flushing iptables (sudo iptables -F) instantly resurrected my connection.

For the record, I'm using Ubuntu Dapper (now KDE-ified) and I dpkg installed moblock from the tar.gz posted here.

Now, I'm not at all sure WHY iptables is getting 'clogged,' but it apparently is.  It *could* have been due to the fact that I was using the original guarding.p2p list that relies on nipfilter.dat, and moblock seems to very dislike this list, reporting many skipped bad ranges, short lines, and duplicate ranges, ultimately installing only about 2k ranges.  I've had much more success using the commented-out line in /etc/cron.daily/moblock-nfq, which gives me somewhere over 160k ranges.

So, it appears that, for the time being -- unless I discover that using the other blocklist list magically stops iptables from getting clogged -- it seems I need to periodically flush iptables and force moblock to run only when I want to P2P.  (Any better suggestion from you *nix or *buntu geniuses would be appreciated.)

Finally, I recall seeing a few pages back someone asking about using blocklists from peerguardian.sourceforge.net/lists.  I note that they are very similar to the ones gotten from the above "other" list inside moblock's update script (and I happened to compare the lists obtained by p2p.php and gov.php and found them identical, so if you end up trying to use them, you should need only one or the other).  I was able to download a handful of them (p2p, ads, spy), extract them, cat them together, and place them in /etc/moblock/guarding.p2p, and moblock happily ate it and gave me over 100k blocked ranges -- but I note it was a number smaller than what I get with moblock's own downloaded alternate blocklist, so I'll be using that instead.

I'd really like to be able to run moblock and keep it running, but if it's gonna end up logjamming my stack, it's at best going to be a targeted-use helper.  I'll be happy to let it jam up my iptables and apply any diagnostics any of you gurus might suggest to diagnose how/why this is happening and prevent it.  I'm learning tons (formerly Win32 weenie), and want to know more.

Sorry this ran so long, but there was much to say.  ;-)

---

### Post by wilberfan on 2006-11-20
As a long-time user of PeerGuardian on Windoze XP, I'd love to give MoBlock a try--but I'm way n00b.

On behalf of all the other shy n00bs out there, is there a chance I could get some more specific instructions on how to get this installed and running?   I mean--I'm a little lost at the very first step:

> I saved the file as a tar archive, it contains libnfnetlink0_0.0.14-1.1_i386.deb
moblock-nfq_0.8-12_i386.deb
libnetfilter-queue_0.0.11-1.1_i386.deb

Just untar this archive. Be aware that the relative path is still in the tar archive and it is bound to /var/cache/apt/archive

After you have the files extracted from the tarball use dpkg -i *.deb (but be sure you put just those 3 files in a directory by their self. do not run that command from /var/cache/apt/archive directory!! be sure you have the 3 files in their own directory..

"Just untar this archive."  untar it *where?*  That seems important...!  Will it automatically go into /var/cache/apt/archive?

Yeah, hopeless n00b...

---

### Post by roadboy on 2006-11-21
> **pelle.k said:**
> Roadboy: It's very important that moblock starts first, then firehol. This happens at bootup, so no worries about that. If you want to restart moblock you _have_ to restart firehol after that as well. That _might_ be the problem. I dont know. I suggest you do what i wrote some posts above to also remove the automatic updater,as it might restart moblock without restarting firehol afterwards.
OrganicPanda: Yes, you >should< be completely protected... As long as you don't install an iptables firewall that will mess up the rules that make moblock inspect your traffic.
first of all thanks for your reply pelle.k. i've studied a little on moblock after your reply and solve the problem. i changed the runlevel defaults for moblock from 2,3,4,5 to 0,6,S and removed the last line (/etc/init.d/`basename $0` reload) from /etc/cron.daily/moblock-nfq and there's no problem :) thanks again.

---

### Post by NiksaVel on 2006-11-21
> I've traced it down to iptables. (I noticed during a reboot to reestablish connectivity that something in the shutdown mentioned that there were gobs of queued packets [or something like that] disposed of from iptables.) In talking to the office *nix guru, we devised a plan to diagnose this, and flushing iptables (sudo iptables -F) instantly resurrected my connection.


this did NOT work for me...  I had to do sudo /etc/init.d/moblock-nfq restart to get my connection back...

I stress again that there seems to be some problem with the reloading part of moblock after update...  it never shows the part:
> Merged ranges: 216
Skipped useless ranges: 6197
NFQUEUE: binding to queue '0'

it just gets to:
> 
Ranges loaded: 173688


and hangs with my network dead till I restart it and it gets till the NFQUEUE part...

---

### Post by pelle.k on 2006-11-21
OK, so i've had enough of this, and plan to build a moblock package myself. :)
Please don't rush me. When i have something that works well, i'll post it here. I'll be back as soon as possible (0 -> 48 hours i suppose).

---

### Post by Scream72 on 2006-11-21
> **Scream72 said:**
> Hello. :)

I have amule and lopster connection problem with moblock.

Amule servers "low id" when moblock works, if i stop moblock and reconnecting, the id value is high....same thing with lopster, traffic is low and upload is drop for all ip...


Router rules is ok (atlantis web share), firewall and virtual server(dmz able on ip adress of ethernet card).

Iptables rules :

 

Moblock is installed and configured by this tutorial(with default blocklist on line 34).
(Thanks pelle.K ;) )




Other users have this problem?

Thanks :) (and excuse my english).



I have changed my router atlantis webshare 242w, with a modem ethernet, and the problem is terminated....moblock working perfectly now (i have added other blocklist beyond default lists on line 34).

Other user have a configuration problem with atlantis webshare? :evil:

---

### Post by pelle.k on 2006-11-23
Hi all. The problem with moblock, is that it's relying on som new libraries in the debian repos. To get around that, i chose to build libnfnetlink and libnetfilter-queue for ubuntu. It works for me, but i can't be sure until some of you tried it out.

If you have added any debian repo (as someone suggested) you need to uninstall moblock 'sudo aptitude remove moblock-nfq' (aptitude to remove dependancies too. or does apt-get do that nowdays?) so that you have a clean ubuntu base to start with.

If you installed ubuntu through the debs provided as a temporary solution, you will have to uninstall them manually with 'dpkg -r packagename.deb'
[B]
I've attached two debs to this post. Install them, then install moblock as you would have done before through the moblock repo.[/B]

Lemme now how it works so that i can update the HOWTO. Oh, and you still need to use the commented BLOCKLISTS= line in /etc/cron.daily/moblock-nfq to get a full blocklist.

---

### Post by wilberfan on 2006-11-23
OK. I downloaded both of the packages from the previous post.  Saved 'em to my desktop, right-clicked and installed via the gDebi Package installer.

Used Synaptic to install moblock...

How do I know if it's installed properly?  How do I know if it's running?!  (I'm under the impression it will start up on it's own??)

---

### Post by pelle.k on 2006-11-23
I belive i did instruct you how to 'tail' the log file in the HOWTO.
Also you could run 'pidof moblock' to see if it's running.

---

### Post by wilberfan on 2006-11-23
> **pelle.k said:**
> 
Also you could run 'pidof moblock' to see if it's running.

Ah.  I get a process number of "4512"--but I don't see it listed in the System Monitor--so that confuses me a little...

---

### Post by clandestiny on 2006-11-24
First of all, I'd like to thank you for the time and effort you're putting into this.  It's surely appreciated.

> **pelle.k said:**
> Hi all. The problem with moblock, is that it's relying on som new libraries in the debian repos. To get around that, i chose to build libnfnetlink and libnetfilter-queue for ubuntu. It works for me, but i can't be sure until some of you tried it out.

If you have added any debian repo (as someone suggested) you need to uninstall moblock 'sudo aptitude remove moblock-nfq' (aptitude to remove dependancies too. or does apt-get do that nowdays?) so that you have a clean ubuntu base to start with.

I'm totally game for trying this out.  Having said that, I should mention that I'm using Ubuntu Dapper, and I've heard enough stories about Edgy to give me pause to go beyond this level right now.

I fully uninstalled moblock and the libn* components from the .debs that had been posted here and installed your new libn* .debs.  Attempts to install moblock from the repository still complain at me about the apparent shortcomings of my libc, as I'm not using debian per se.

Given this situation, would you recommend that I install the moblock .deb from the long-prior posting, or that I get the debian libc to satisfy the dependency?  (I'm much less comfortable shoving a debian update into Ubuntu, since I'm not quite savvy enough to fix this solid OS if I manage to break it with something unorthodox.)

For the time being, since I seem to need to 'break a rule' to satisfy the libc dependency, I'll go back to that moblock .deb and see how this works with that.  But I'm more than happy to be your 'guinea pig' on any other reasonable strategy you can make me understand how to recover from, if all goes south.

Regards!

---

### Post by pelle.k on 2006-11-24
Have you tried to install it with --force ? The diffrence between the debian libc and the ubuntu one shouldn't be very large... I'd say you'd be better of compromising moblock than the whole system, so give --force a try.
If that doesn't do it, i could probably build the latest moblock release for dapper. That wouldn't be the ideal solution though...

---

### Post by foxy123 on 2006-11-25
> **pelle.k said:**
> Hi all. The problem with moblock, is that it's relying on som new libraries in the debian repos. To get around that, i chose to build libnfnetlink and libnetfilter-queue for ubuntu. It works for me, but i can't be sure until some of you tried it out.

If you have added any debian repo (as someone suggested) you need to uninstall moblock 'sudo aptitude remove moblock-nfq' (aptitude to remove dependancies too. or does apt-get do that nowdays?) so that you have a clean ubuntu base to start with.

If you installed ubuntu through the debs provided as a temporary solution, you will have to uninstall them manually with 'dpkg -r packagename.deb'
[B]
I've attached two debs to this post. Install them, then install moblock as you would have done before through the moblock repo.[/B]

Lemme now how it works so that i can update the HOWTO. Oh, and you still need to use the commented BLOCKLISTS= line in /etc/cron.daily/moblock-nfq to get a full blocklist.

How did you manage to build those packages. I have a strange error every time I try it. BTW, they are both in Feisty but I have the same error trying to backport them:

```
touch install-stamp
dh_testdir -i
dh_testdir: I have no package to build
make: *** [binary-indep] Error 1
```

Apparently after "I have no package to build" dh_testdir should continue with another try but it fails. I found this on the Internet, it looks like a log for building a Debian 64 bit version:
```
touch install-stamp
dh_testdir -i
dh_testdir: I have no package to build
dh_testroot -i
dh_installdocs -i -A README
dh_installdocs: I have no package to build
dh_installchangelogs -i debian/no-upstream-changelog
dh_installchangelogs: I have no package to build
dh_install -i --sourcedir=debian/tmp
dh_install: I have no package to build
dh_link -i
dh_link: I have no package to build
dh_strip -i
dh_strip: I have no package to build
dh_compress -i
dh_compress: I have no package to build
dh_fixperms -i
dh_fixperms: I have no package to build
dh_installdeb -i
dh_installdeb: I have no package to build
dh_shlibdeps -i
dh_shlibdeps: I have no package to build
dh_gencontrol -i
dh_gencontrol: I have no package to build
dh_md5sums -i
dh_md5sums: I have no package to build
dh_builddeb -i
dh_builddeb: I have no package to build
dh_testdir -a
dh_testroot -a
dh_installdocs -plibnfnetlink-dev
dh_installdocs -plibnfnetlink1
ln -sf libnfnetlink1 debian/libnfnetlink1-dbg/usr/share/doc/libnfnetlink1-dbg
dh_installchangelogs -plibnfnetlink1
dh_installchangelogs -plibnfnetlink-dev
dh_install -a --sourcedir=debian/tmp
dh_link -a
dh_strip -a --dbg-package=libnfnetlink1-dbg
```

Maybe Dapper deb building tools cannot handle it for some reason?

---

### Post by pelle.k on 2006-11-25
So those two debs I made doesn't work under dapper?
Also i have a confession to make. As these two debs wasn't going in some repository, i figured checkinstall would do [-X , so I can't really help you to build them the proper way.
Also, the problem with dapper and moblock is _not_ netfilter, but dependancies in moblock package (eg libc-2.3.6-6 while dapper has 2.3.6-0ubuntu20)

---

### Post by foxy123 on 2006-11-25
> **pelle.k said:**
> So those two debs I made doesn't work under dapper?
Also i have a confession to make. As these two debs wasn't going in some repository, i figured checkinstall would do [-X , so I can't really help you to build them the proper way.
Also, the problem with dapper and moblock is _not_ netfilter, but dependancies in moblock package (eg libc-2.3.6-6 while dapper has 2.3.6-0ubuntu20)

no, these packages work fine. The problem as you mentioned is with libc6. I wanted to build moblock from Debian source, but it requires dev packeage of libnfnetlink and I guess libnetfilter. That is why I was asking.

I would not like to use --force to walk around the libc6 dependency really.

---

### Post by pelle.k on 2006-11-25
Oh, now i get it. :) It's a dirty compromise. You get a "ubuntu" package, but on the other hand, you will not get the updates for free (if you used a custom build that is...)
apt-get source moblock-nfq and see to it you've got all build-dependencies installed. (install netfilter sources with ./configure prefix=/usr & make & make install, just comment out libnfnetfilter-dev and libnetfilter_queue-dev in the control file later on...)

---

### Post by pelle.k on 2006-11-25
That was a "dirty" suggestion, i know. :twisted: 
However, i've built both libs the proper way now. I'm going to post them with -dev packages when i've had some sleep, and tested them out.

foxy123: I went straight for the vanilla source from netfilter.org. not the feisty source packages.

---

### Post by clandestiny on 2006-11-26
> **pelle.k said:**
> Have you tried to install it with --force ? The diffrence between the debian libc and the ubuntu one shouldn't be very large... I'd say you'd be better of compromising moblock than the whole system, so give --force a try.
If that doesn't do it, i could probably build the latest moblock release for dapper. That wouldn't be the ideal solution though...

No, I hadn't tried --force, but thanks, I'll keep that in mind for later, in case the progress I've made lately falls apart.  For the time being, I've backtracked to the Old Packages posted by lp7413 in post 239 and made some adjustments, and things appear more stable now.

I did finally have a realization as to the cause of my most major problem, and I'll post it here in case anyone else is in a similar boat and did the same not-thinking I did.  ;-)

My Ubuntu Dapper box is running bind9 with my own tables for internal addresses and bumping up to the root servers for anything unknown -- I've traditionally found ISP's DNS's to be slow or unreliable, and I've been very happy with DNS performance since I cut my ISP out of the loop.

What I didn't realize is that many, if not most or all, of the DNS root servers and various other target domain's servers are included in the blocklists that I get from "ads-trackers-and-bad-pr0n level1 level2  Microsoft  spyware".  With this full list loaded and moblock running, I lost the ability to resolve an uncached domain name from the root servers (which I seemed to find were blocked by entries labeled "VeriSign Global Registry Services").

Subsequent to this discovery, I grepped out from the building of guarding.p2p in /etc/cron.daily/moblock-nfq any of those or any having a dotted word with NS and an optional digit, and things became much better.

Still, something I read before kept echoing in my head, and today I seem to have stumbled over a better solution.  /etc/moblock/MoBlock-nfq.sh sets a number of WHITE* variables that control passthrough rules.  By adding "domain" to WHITE_TCP_OUT and WHITE_UDP_OUT, I was able to keep the VeriSign blocks (in case there could possibly be some nefarious P2P traffic from there...) without compromising my ability to resolve names.

So, for now, everything seems mostly stable.  If it all goes south, I may try to force up the latest .debs.

Hope the above can help someone.

---

### Post by clandestiny on 2006-11-26
Something else I've discovered that I think is worth mentioning here.

FTR, I'm using moblock 0.8-12 with libnfnetlink0 and libnetfilter-queue from the Old Packages I mentioned earlier, so I don't know if what I'm about to report has been fixed in 0.8-13....

At the top of /var/log/moblock.log, as I've mentioned before, I get *many* "Skipping useless range" reports when moblock loads.  I started tracing them back to the guarding.p2p, and it turns out that almost every one of them is a single-address range (e.g., 194.237.107.11-194.237.107.11).  I'm hoping I'm wrong, but this seems to be telling me that any such single address range is NOT being blocked.

If I'm right, I find this very disturbing...

---

### Post by foxy123 on 2006-11-26
with great help from pelle.k I managed to build moblock Dapper packages. They work on my laptop, but I am not sure if they will do on any other PC :)

Anyway I am attaching the package here. Give it a try and let me know.

---

### Post by adds2one on 2006-11-27
Will this package be safe to use on Edgy?

---

### Post by pelle.k on 2006-11-27
No. You should install the two debs attached in this post [http://www.ubuntuforums.org/showpost.php?p=1797134&postcount=302](http://www.ubuntuforums.org/showpost.php?p=1797134&postcount=302) for use in edgy, then install moblock from repo, as in my howto.
If someone could report back to me or foxy123 in this thread, and tell us if everything works as expected, I would gladly update my HOWTO.

---

### Post by clandestiny on 2006-11-27
> **pelle.k said:**
> If someone could report back to me or foxy123 in this thread, and tell us if everything works as expected, I would gladly update my HOWTO.

I had no trouble uninstalling the Old Packages and installing the lib's and moblock-nfq from foxy123's packages.  It appears to work substantially similarly to the Old Packages, so I'm superficially confident that this build is good.  :-D

I am still quite a bit concerned over moblock's apparent rejection of single-address ranges in guarding.p2p (which I referred to in a prior post), which now appear to number over 6000....

---

### Post by pelle.k on 2006-11-27
OK. great.
Single address ranges you say? Do you use the "old" commented BLOCKLISTS= or the new one (in /etc/cron.daily/moblock-nfq) with nipfilter.dat?

---

### Post by clandestiny on 2006-11-28
> **pelle.k said:**
> OK. great.
Single address ranges you say? Do you use the "old" commented BLOCKLISTS= or the new one (in /etc/cron.daily/moblock-nfq) with nipfilter.dat?

Sorry, my bad.  I'm using the old commented BLOCKLISTS.

But I only noticed a large coincidence between my "Skipping" lines in the log and single-address ranges in guarding.p2p.  What I didn't notice is that (so far) every single-address range I've found in the Skipping lines is included within a larger range somewhere above it, so it seems these lines are redundant and properly skipped.

It did initially give me the impression that something (perhaps important) was being ignored, but that no longer seems to be the case.  I may just whip up a little PHP program to chew on the Skips and verify that they're *all* covered elsewhere, but I have yet to find one (on further examination, jumping through the Skip list) that isn't.

Thanks to all in the forum for helping me get this running and understand what's going on.  It's amazing how much I've learned about iptables and other things just in getting this one important program running.

---

### Post by pelle.k on 2006-11-28
That's a relief. :)
Yeah, you can learn quite a lot when you have to. I remember back when i was a newbie and had to compile a usb stick network driver, and setp it up with wep in /etc/network/interfaces. Man i hadn't the slightest idea of even what a deamon was, but at some point you realize /etc/init.d/network restart is really more convenient than rebooting the computer really. :D

---

### Post by lykeion on 2006-11-28
I'm running Edgy and managed to apt-get install moblock v0.8-13 with the new debs (found [here]("http://www.ubuntuforums.org/showpost.php?p=1797134&postcount=302")), and it seems to be working okay. Tried to ping microsoft.com and another ip from the blocklist, and when I check moblock.log they're blocked.

> **clandestiny said:**
> 
It's amazing how much I've learned about iptables and other things just in getting this one important program running.

Amen to that...and many thanks to pelle.k for this great thread.

---

### Post by pelle.k on 2006-11-28
OK ladies and gentlemen. I've updated the howto with the latest. If you've added debian repos or installed debs other than from foxy123 or me - uninstall them...

---

### Post by adds2one on 2006-11-28
hey pelle, thanks for all your work. works great!!

---

### Post by david.rahrer on 2006-11-30
Man, I started out 15 minutes ago googling for a peerguardian for Ubuntu and I'm up and running thanks to your guide.  Thanks a bunch pelle!

---

### Post by Mechanical on 2006-12-01
This thread has been a constant visit for me here on the forums and I believe this project is quite important as well.  Thanks again for the update and keep up the great work!  I have installed the newer version by following the latest edgy update to the original post and I updated the block lists.. but I noticed the bluetack stuff not being able to download.  Anyone else have this problem?  Maybe I need to update my blocklist line?  I will try it again in a while.

---

### Post by fqb on 2006-12-05
Hi,
**TIPS : copy the last version of moblock-nfq (/etc/cron.daily/) into an older installation :**
[SIZE="1"](I use this tips for my (ubuntu dapper drake) amd64 version of moblock )[/SIZE]

Extract the last package archive of Moblock into your curent directory :
```
dpkg-deb -x moblock-nfq_0.8-13_i386.deb .
```
replace the old file with the new one :
```
sudo cp ./etc/cron.daily/moblock-nfq /etc/cron.daily/moblock-nfq
```


I hope this can help someone :)

Sorry for my english, I'm french

---

### Post by marx2k on 2006-12-12
One thing I would like to see in reference to the MoBlock log is to tell me what PORT the IP address was blocked on.  

Example:

Blocked OUT: VIVENDI TELECOM HUNGARY,hits: 1,DST: 213.163.51.151

I want it to be

Blocked OUT: VIVENDI TELECOM HUNGARY,hits: 1,DST: 213.163.51.151:PORT

---

### Post by skipo on 2006-12-12
> **marx2k said:**
> One thing I would like to see in reference to the MoBlock log is to tell me what PORT the IP address was blocked on.  


And timestamp would also be nice.

---

### Post by UberIcarus on 2006-12-12
Okay....how do I add sourceforge to the exceptions list? someone added it to the default block list

---

### Post by marx2k on 2006-12-12
Also, removing "Blocked" from the beginning of the log would be nice.

Configuring the logfile output through a config file would be a very nice addition to this program simce all I want is 
[Short Time Stamp]:[IN/OUT]:[DNS Name]-[IP}:[PORT]

---

### Post by pelle.k on 2006-12-13
Hey guys.
The features you ask, require changes in the source code. I'm neither a skilled C coder, nor very comfortable with branching moblock. So, until someone does, you'll have to wait, or do this yourself.

> Okay....how do I add sourceforge to the exceptions list? someone added it to the default block list
This is really the reason i put a FAQ in my howto...
good luck.

---

### Post by marx2k on 2006-12-13
On a seperate subject regarding MoBlock, I'd like to know from the people using it, what's the domain giving you the most hits?

I have Time Warner Telecom with **700** hits.
IP Range 206.80.17.*

---

### Post by beefcurry on 2006-12-15
forgive me for this may sound like a very n00b question. What will happen if moblock and firestarter are used togeather? The statement of "Firestarter (most iptables firewalls) does not work with moblock ATM" is kind of ambiguous. Does it mean it will not function with firestarter, or does it mean it can not integrated with firestarter?

---edit
Ah okay, I read through all 34 pages and found me answer. But didn't Clessing construct a method to use moblock with firestarter ( [http://ubuntuforums.org/showpost.php?p=1209006&postcount=81](http://ubuntuforums.org/showpost.php?p=1209006&postcount=81) ) ? does it work?

---

### Post by pelle.k on 2006-12-15
Not really. I'm quoting from his post.

Solution 1;> So using what I posted above means putting moblock in front of firestarter, effectively leaving firestarter's rules unused because moblock is filtering everything.
You can only use firestarter to watch open connections
Solution 2;> But this only replaces the problem by another: now firestarter is in charge and if firestarter decides that a packages is to be accepted, it may do so without consulting moblock.

This essentially means, you have no control over what is happening.

To sum it up;> This is one of the reasons for which on sourceforge.net I categorized moblock as software for "advanced end users": you should know how to use iptables before you use moblock. You can do without as per default the package blocks things. But if you want to integrate it in another firewall you need to know, what is going on.

I'm afraid this _is_ the current situation. I'm investigating new possibilities, though...

---

### Post by rageear on 2006-12-15
Great work by pelle!

Thanks a million!

---

### Post by skipo on 2006-12-17
I haven't been able to update my blocklists today, I can't get any connections to bluetack. Actually I can't even get their webpage to open with firefox.

Is it just me or is their service down?

---

### Post by simple on 2006-12-17
> **skipo said:**
> I haven't been able to update my blocklists today, I can't get any connections to bluetack. Actually I can't even get their webpage to open with firefox.

Is it just me or is their service down?

It's down for me also. I installed moblock for the first time tonight, thanks Pelle for the nice very simple guide and deb packages of the dependencies that were missing. Only problem is bluetack being down and can't seem to find an alternative server for a temp use.

---

### Post by skipo on 2006-12-17
Bluetack is under a DDoS attack.

From the Bluetack forum:
> 
Hi everyone. Well the forum is back , thanks to our most awesome , hardworking admins who have brought us back to life again.

The site's situation is that we are currently under a DDoS attack.

We will naturally continue to fight it , and we are putting together a report from all the logs on the IP's/users involved for the authorities. There will also be a nice new server-flooder blocklist available for download out of this attack.

We also took this time out over the past week to do a few upgrades and maintennance on the server itself , so there may be some errors around the site. If you find you have some problems on the forum , please let us know in the Site Related Issues & Suggestions forum section.


If the list updates are not working for you , please don't hammer the server unneccesarily , just try again later. Things will be back to normal in no time.

We also hope to have a new alternate server set up in the next week or so for hosting the lists , more information on that when it's up and running.

---
EDIT

Or then again maybe not. I looked at the date and it was Sep 10 2006. :-D

---

### Post by edwardecl on 2006-12-17
Does anyone know how you can view the moblock log on a windows computer on a network, and have it display the updated information like that theme in SuperKaramba does (doesn't have to be as fancy).

---

### Post by pelle.k on 2006-12-17
The easiest way would be to download and run putty in windows, start an ssh session to the computer with moblock installed, and 'tail -f' the logfile. Anything other than that, will probably be somewhat difficult. Moblock just isn't written to handle these situations out of the box.

---

### Post by golem3 on 2006-12-20
Phenomenal guide. Thanks a lot, pelle.k.

---

### Post by abelikoff on 2006-12-25
In case anyone is interested, I've modified _/etc/cron.daily/moblock-nfq_ . The modifications mostly deal with removing unnecessary verbosity (I don't want to see daily 3-page wget traces unless there was some problem) and adding some error handling. The modified script is attached and should be a drop-in replacement for stock file. Feel free to report any issues and/or to incorporate it in future package versions.

-- Sasha

---

### Post by skipo on 2006-12-26
There are no blocklists in txt file format in Bluetacks servers. All the lists are gzips or zips. So the dshield blocklist wont download.

And a different issue, I tried to download  level3 blocklist from bluetack. All I got was html-document:

> Welcome to test-a-contrib.com

Test
Evaluation
Accounting Test
Assessment Test
Employee Screening
Myers Briggs Type Indicator
360 Review
Employee Drug Testing
Myers Briggs Test
IQ Test Score
Employee Personality Test

Staffing Services | Employee Benefit Services | Background Checks | Physical Therapy | Hospitals | Cheap Airfare
Why am I seeing this web site? 

Does anyone have any info on that?
---
EDIT:
Apparently bluetack had some server issues, they fixed it and it's working again.

---

### Post by beanmonkey on 2006-12-26
Shouldn't the restart line be

sudo /etc/init.d/moblock-nfq restart

?

---

### Post by shookone on 2006-12-29
New version of moblock on ubuntu 6.10

Any reason why not to upgrade?

---

### Post by wilberfan on 2006-12-30
> **shookone said:**
> New version of moblock on ubuntu 6.10

Any reason why not to upgrade?

I may have found one:   I updated this morning and now I can't connect to my POP server to get my e-mail!!   :(    (I confirmed this by killing moblock-nfq.  Everything connected fine when it was "off"...)

Help!!   How do I fix this?   (There are 2 Charter.net accounts (same POP, obviously) and one yahoo.biz account being blocked.)

---

### Post by wilberfan on 2006-12-30
> **beanmonkey said:**
> Shouldn't the restart line be

sudo /etc/init.d/moblock-nfq restart

?

It should if you want it to actually restart!   ;)    (I learned that the hard way this morning!)

---

### Post by wilberfan on 2006-12-30
> **wilberfan said:**
> I may have found one:   I updated this morning and now I can't connect to my POP server to get my e-mail!!   :(    (I confirmed this by killing moblock-nfq.  Everything connected fine when it was "off"...)

Help!!   How do I fix this?   (There are 2 Charter.net accounts (same POP, obviously) and one yahoo.biz account being blocked.)

I have a feeling I need to put something in the grep command in /etc/cron.daily/moblock-nfq (below), but nothing I've tried has worked so far (do I use quotes?  do I put the pop.charter.net IP in there??   I'm confused!!)

	> # uncomment below to unblock Yahoo! Mail and whatever
	# else needs unblocking here. Do this also in the
	# restart section.
	grep -v -i "yahoo\!" merged.p2b.p2p | [COLOR="Blue"]grep -v -i "charter"[/COLOR] | grep -v "Trendstep Ltd" > merged.p2b.p2p.tmp
	mv merged.p2b.p2p.tmp merged.p2b.p2p
	mv $PG_LIST $PG_LIST.backup
	mv merged.p2b.p2p $PG_LIST
	/etc/init.d/`basename $0` reload
exit 0


None of these have worked:  grep -v -i "charter"        grep -v -i "209.225.8.224"        grep -v -i 209.225.8.224     grep -v -i "charter/!"    ....    (Plus, I don't know where the "restart section" is!)   HELP!

---

### Post by abelikoff on 2006-12-30
> **beanmonkey said:**
> Shouldn't the restart line be

sudo /etc/init.d/moblock-nfq restart

?

Considering that */etc/cron.daily/* scripts are run as root, it shouldn't. Or am I missing something?

---

### Post by wilberfan on 2006-12-30
> **abelikoff said:**
> Considering that */etc/cron.daily/* scripts are run as root, it shouldn't. Or am I missing something?

He was pointing out (I think) that in the first post in this thread:

> sudo /etc/init.d/moblock restart

"-nfq" was missing...   (ie,  sudo /etc/cron.daily/moblock restart vs  sudo /etc/cron.daily/moblock[COLOR="Red"]-nfq[/COLOR] restart)  ?

---

### Post by wilberfan on 2006-12-30
[A very polite *bump*  :???:  ]

> **wilberfan said:**
> I updated this morning and now I can't connect to my POP server to get my e-mail!!   :(    (I confirmed this by killing moblock-nfq.  Everything connected fine when it was "off"...)

Help!!   How do I fix this?   (There are 2 Charter.net accounts (same POP, obviously) and one yahoo.biz account being blocked.)

Can anyone help this n00b get the correct coding to whitelist my POP e-mail server?  I've tried various combinations of "charter.net" and 209.225.8.224 etc...but it's not working...  I'm doing something wrong...  Here's the latest incarnation:

	```
 # uncomment below to unblock Yahoo! Mail and whatever
	# else needs unblocking here. Do this also in the
	# restart section.
	grep -v -i "yahoo\!" merged.p2b.p2p | grep -v -i "charter\!" > merged.p2b.p2p.tmp
	mv merged.p2b.p2p.tmp merged.p2b.p2p
	mv $PG_LIST $PG_LIST.backup
	mv merged.p2b.p2p $PG_LIST
	/etc/init.d/`basename $0` reload
exit 0  
```

I don't know what the "restart section" is refering to, either...  :confused:

---

### Post by skipo on 2006-12-31
Before you try to connect to your email-server, open terminal and enter command 
```
tail -f /var/log/moblock.log
```
This will tell you what you need to whitelist. Then, if you need to whitelist for example yahoo and charter.net, the needed edits to the /etc/cron.daily/moblock-nfq would be something like this:
```
# uncomment below to unblock Yahoo! Mail and whatever
# else needs unblocking here. Do this also in the
# restart section.
grep -v -i "yahoo" merged.p2b.p2p | grep -v -i "charter.net" > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p
mv $PG_LIST $PG_LIST.backup
mv merged.p2b.p2p $PG_LIST
/etc/init.d/`basename $0` reload
```

The mention to the restart section is there only to confuse us all, I haven't found it either but I've managed to get yahoo working with this.

---

### Post by netyire on 2006-12-31
:D Just when to post a big thank you for your your efforts. A great guide, and leaves me without a doubt that Moblock can and does work.

Of course, for field testing, just start limewire... ;)

---

### Post by wilberfan on 2006-12-31
> **skipo said:**
> Before you try to connect to your email-server, open terminal and enter command 
```
tail -f /var/log/moblock.log
```
This will tell you what you need to whitelist. Then, if you need to whitelist for example yahoo and charter.net, the needed edits to the /etc/cron.daily/moblock-nfq would be something like this:
```
# uncomment below to unblock Yahoo! Mail and whatever
# else needs unblocking here. Do this also in the
# restart section.
grep -v -i "yahoo" merged.p2b.p2p | grep -v -i "charter.net" > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p
mv $PG_LIST $PG_LIST.backup
mv merged.p2b.p2p $PG_LIST
/etc/init.d/`basename $0` reload
```

The mention to the restart section is there only to confuse us all, I haven't found it either but I've managed to get yahoo working with this.

I still can't reach my POP server...    I've done a WHOIS for pop.charter.net and this is the ip that comes up:  209.225.8.224 (or at least that's what it was yesterday).   When I display the moblock.log, here's what I see:
> 
Blocked OUT: Exodus IDC - DC/DC2,Exodus IP Address Administrator,hits: 16,DST: 209.225.8.224
Blocked OUT: Exodus IDC - DC/DC2,Exodus IP Address Administrator,hits: 17,DST: 209.225.8.224
Blocked OUT: Exodus IDC - DC/DC2,Exodus IP Address Administrator,hits: 18,DST: 209.225.8.224

The ip's match exactly, so that would seem to be my problem, yes?  (I don't know why it doesn't say some variation of 'charter'!)

But when I change the moblock-nfq as you suggest, it's still blocked:

```
grep -v -i "yahoo\!" merged.p2b.p2p | grep -v -i "Exodus" > merged.p2b.p2p.tmp
	mv merged.p2b.p2p.tmp merged.p2b.p2p
	mv $PG_LIST $PG_LIST.backup
	mv merged.p2b.p2p $PG_LIST
	/etc/init.d/`basename $0` reload
```

What am I doing wrong?   Do I need the IP in there??  And how *do* you enter an IP range?

[Edit]  Just to add to the mystery:  I'm running 32-bit Edgy on two boxes, a Pentium IV Dell and an AMD Athlon 64x2.  I have Moblock 0.8-14 loaded on BOTH machines, and it's only the AMD that's blocking my POP server...!   I can retreive mail no-prob on the Dell.   :-k

[2nd Edit]   Now it's happening on the Dell box...   Obviously the block-list (whatever it's called) got updated there,too?)

---

### Post by skipo on 2006-12-31
> **wilberfan said:**
> 
But when I change the moblock-nfq as you suggest, it's still blocked:

```
grep -v -i "yahoo\!" merged.p2b.p2p | grep -v -i "Exodus" > merged.p2b.p2p.tmp
	mv merged.p2b.p2p.tmp merged.p2b.p2p
	mv $PG_LIST $PG_LIST.backup
	mv merged.p2b.p2p $PG_LIST
	/etc/init.d/`basename $0` reload
```

What am I doing wrong?   Do I need the IP in there??  And how *do* you enter an IP range?

[Edit]  Just to add to the mystery:  I'm running 32-bit Edgy on two boxes, a Pentium IV Dell and an AMD Athlon 64x2.  I have Moblock 0.8-14 loaded on BOTH machines, and it's only the AMD that's blocking my POP server...!   I can retreive mail no-prob on the Dell.   :-k

Well, now this gets out of my league. To my knowledge, that should have worked. And I am under impression that IP addresses or ranges can't be entered to whitelists, one can only use this name method thingy. Correct me if I am wrong.

---

### Post by wilberfan on 2006-12-31
Is there a way to prevent moblock from loading at startup (until I can figure out this whitelist problem!)?

---

### Post by abelikoff on 2007-01-06
> **wilberfan said:**
> Is there a way to prevent moblock from loading at startup (until I can figure out this whitelist problem!)?

I am no Debian expert, so please double-check. According to the update-rc.d manpage something like the commands below should work:

```

    update-rc.d -f moblock-nfq remove
    update-rc.d moblock-nfq stop 20 2 3 4 5 .

```

Another hardcore way is to move _/etc/init.d/moblock-nfq_ script somewhere else.

---

### Post by wilberfan on 2007-01-06
> **abelikoff said:**
> I am no Debian expert, so please double-check. According to the update-rc.d manpage something like the commands below should work:

```

    update-rc.d -f moblock-nfq remove
    update-rc.d moblock-nfq stop 20 2 3 4 5 .

```



Clever fellow!  This seems to have worked.     I'd sure prefer the whitelist option--but this will save me some aggrivation for awhile...   Thanks!

---

### Post by Richard Kut on 2007-01-06
Hey pelle.k !

I just followed your instructions and they worked great. Thank you very much!

However, I found that the Privoxy proxy server that I am running was giving me some trouble when running the daily cron script. I had to add the following two lines to the top of the script to get the daily updates to work properly:

unset http_proxy
unset HTTP_PROXY

I do not know if anyone else has come across a similar problem. If you are running Privoxy (or some other proxy like squid?) then try the above and maybe it will help you too.

Thanks again pelle.k for the useful info.

Cheers!

---

### Post by wilberfan on 2007-01-07
Gawd, I really need some help whitelisting my e-mail POP server!!

Here's what's showing after doing a

```
wilberfan@AMD64:~$ tail /var/log/moblock.log
Blocked OUT: Exodus IDC - DC/DC2,Exodus IP Address Administrator,hits: 52,DST: 209.225.8.224
Blocked OUT: Exodus IDC - DC/DC2,Exodus IP Address Administrator,hits: 53,DST: 209.225.8.224
Blocked OUT: Exodus IDC - DC/DC2,Exodus IP Address Administrator,hits: 54,DST: 209.225.8.224
Blocked OUT: Exodus IDC - DC/DC2,Exodus IP Address Administrator,hits: 55,DST: 209.225.8.224
```

And here's my attempt at a grep command inside of /etc/cron.daily/moblock-nfq

```
	# if any blockfiles were updated:
	for i in $BLOCKLISTS ; do
	gunzip -c $i.$SUFFIX > $i.$SUFFIX2
	done
	cat *.txt > merged.p2b.p2p
	for i in $BLOCKLISTS ; do
	rm $i.$SUFFIX2
	done
	# uncomment below to unblock Yahoo! Mail and whatever
	# else needs unblocking here. Do this also in the
	# restart section.
        # grep -v -i "yahoo\!" merged.p2b.p2p | grep -v -i "Exodus" > merged.p2b.p2p.tmp
	# mv merged.p2b.p2p.tmp merged.p2b.p2p
[COLOR="Red"]        grep -v -i "Exodus IDC - DC/DC2,Exodus IP Address Administrator" merged.p2b.p2p > merged.p2b.p2p.tmp[/COLOR]
        mv merged.p2b.p2p.tmp merged.p2b.p2p
	mv $PG_LIST $PG_LIST.backup
	mv merged.p2b.p2p $PG_LIST
	/etc/init.d/`basename $0` reload
exit 0
```

It DOES need quotes around the string, right?    Maybe the coding is correct, but something ELSE is wrong??  All I know is that I can't get e-mail until I 'kill' moblock!  :(

---

### Post by pelle.k on 2007-01-08
```
grep -v -i "Exodus" merged.p2b.p2p > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p

```
Try that instead. the / might be your problem since this is regexp.

---

### Post by wilberfan on 2007-01-08
> **pelle.k said:**
> ```
grep -v -i "Exodus" merged.p2b.p2p > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p

```
Try that instead. the / might be your problem since this is regexp.

Nope.  Still not working...    Here's the latest cat
> 
Blocked OUT: Exodus IDC - DC/DC2,Exodus IP Address Administrator,hits: 17,DST: 209.225.8.224
Blocked OUT: Exodus IDC - DC/DC2,Exodus IP Address Administrator,hits: 18,DST: 209.225.8.224
Blocked OUT: Exodus IDC - DC/DC2,Exodus IP Address Administrator,hits: 19,DST: 209.225.8.224

(I've verified that's my POP server.  If you enter that IP into a web-browser, you get the Charter Mail login screen...)

And here's my /etc/cron.daily/moblock-nfq
```
	# if any blockfiles were updated:
	for i in $BLOCKLISTS ; do
	gunzip -c $i.$SUFFIX > $i.$SUFFIX2
	done
	cat *.txt > merged.p2b.p2p
	for i in $BLOCKLISTS ; do
	rm $i.$SUFFIX2
	done
	# uncomment below to unblock Yahoo! Mail and whatever
	# else needs unblocking here. Do this also in the
	# restart section.
        # grep -v -i "yahoo\!" merged.p2b.p2p | grep -v -i "Exodus" > merged.p2b.p2p.tmp
	# mv merged.p2b.p2p.tmp merged.p2b.p2p
        grep -v -i "Exodus" merged.p2b.p2p > merged.p2b.p2p.tmp
        mv merged.p2b.p2p.tmp merged.p2b.p2p
	mv $PG_LIST $PG_LIST.backup
	mv merged.p2b.p2p $PG_LIST
	/etc/init.d/`basename $0` reload
exit 0
```

I tried rebooting and even manually updated the blocklist...   Something else is wrong somewhere...   

Is it possible to whitelist that specific IP?

---

### Post by pelle.k on 2007-01-09
This is impossible! The syntax is correct. grep you merged.p2b.p2b for "Exodus" It _shouldn't_ be there after an update.
```
# if any blockfiles were updated
```
So, did any of the blocklists get updated at the time you tried it out? e.g. are you sure this block of code got executed, when you ran the script?

If not, you might as well do it yourself, by running the two lines of code i gave you, in the directory where the blocklists reside.

---

### Post by skipo on 2007-01-09
> **pelle.k said:**
> 
If not, you might as well do it yourself, by running the two lines of code i gave you, in the directory where the blocklists reside.

But first you'd have to gunzip the archives and merge them into one file.

---

### Post by wilberfan on 2007-01-11
Well, it's STILL not working...  I haven't tried the manual method yet (I wanna get it working properly!)

I  just tried a manual update of the blocklist and got this:

> wilberfan@DELL-Ubuntu:~$ sudo sh /etc/cron.daily/moblock-nfq
moblock: checking for new block lists...
--19:16:43--  [http://www.bluetack.co.uk/](http://www.bluetack.co.uk/)
           => `-'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... [COLOR="Red"]failed: Connection refused.
no connection to [www.bluetack.co.uk](www.bluetack.co.uk), updating later.[/COLOR]

I don't know if that's a temporary problem or not?   If, for some reason, I haven't been able to connect to bluetack for awhile -- ie, if my blocklist hasn't updated for awhile -- could THAT be causing my problem??

---

### Post by Mechanical on 2007-01-12
> **wilberfan said:**
> Well, it's STILL not working...  I haven't tried the manual method yet (I wanna get it working properly!)

I  just tried a manual update of the blocklist and got this:



I don't know if that's a temporary problem or not?   If, for some reason, I haven't been able to connect to bluetack for awhile -- ie, if my blocklist hasn't updated for awhile -- could THAT be causing my problem??

Bluetack is currently down but I am sure its just a temporary thing.  I updated my list just yesterday.

---

### Post by tee2 on 2007-01-12
From digg: [http://digg.com/security/PeerGuardian_2_MPAA_Fake_Torrents_Tracker](http://digg.com/security/PeerGuardian_2_MPAA_Fake_Torrents_Tracker)

[quote=digg]([http://torrentfreak.com/mpaa-caught-uploading-fake-](http://torrentfreak.com/mpaa-caught-uploading-fake-) torrents/) Add this to your PG2 list. It blocks the IP ranges for the fake torrents listed in the recent Digg article. Just trying to save you some time. Special thanks to whiterabbit.[/quote]

These are the ranges
```
MPAA Tracker:66.172.60.1-66.172.60.255
MPAA Tracker:66.177.58.1-66.177.58.255
MPAA Tracker:66.180.205.1-66.180.205.255
MPAA Tracker:209.204.61.1-209.204.61.255
MPAA Tracker:216.151.155.1-216.151.155.255
```

I did this:
```
tee@tee-laptop:~$ cat /etc/moblock/guarding.p2p | grep mpaa
Razorback 2.0 and 2.1 closed by mpaa:195.245.244.243-195.245.244.244
Versatel Internet customer Stichting Kompaan 5041 JM:82.175.83.120-82.175.83.127

```
So I'm assuming I need to manually add the ranges since they aren't there, how do I do that? I skimmed through the thread but couldn't find anywhere that said how to.

---

### Post by pelle.k on 2007-01-12
@wilberfan
> if my blocklist hasn't updated for awhile -- could THAT be causing my problem??Yes! That's what i've been trying to tell you :)


@tee2
> So I'm assuming I need to manually add the ranges since they aren't there, how do I do that? Well, a quick'n'dirty way is to save those five lines in a text file, and then
```
cat textfile >> merged.p2b.p2p
```
Just before ```
mv merged.p2b.p2p $PG_LIST
``` at the end of /etc/cron.daily/moblock-nfq

---

### Post by ninjad on 2007-01-12
i cant install the second libnetfilter for some reason i dont get any error messages besides "Failed to install package..." any idea whats wrong?

other than that everything seems fine and thanks for the howto.

---

### Post by wilberfan on 2007-01-13
> @wilberfan
Quote:
if my blocklist hasn't updated for awhile -- could THAT be causing my problem??

> **pelle.k said:**
> @wilberfan
Yes! That's what i've been trying to tell you :)

And you would be correct!!  :rolleyes:    

This morning I was FINALLY able to connect to bluetack.     And *now* I'm able to connect to my POP server!   8) 

I'm not sure where to check--or even if it's possible--but is there a log that could have something posted that says "Unable to update blocklist", or something?

Now that I've removed everything that allowed moblock to autostart on my other box--is there an easy way to have moblock autoload on startup again?   (My noobie inclination is to just try and reinstall it...)

Thanks for your help!  :p

---

### Post by pelle.k on 2007-01-13
@ninjad
> i cant install the second libnetfilter for some reason i dont get any error messages besides "Failed to install package..." any idea whats wrong?
You haven't told us what version of the packages, and what version of ubuntu you are using... Also, you could probably spot what is wrong if you just open the packages with gdebi, before installing them.

@wilberfan

man update-rc.d
update-rc.d moblock-nfq defaults

---

### Post by pelle.k on 2007-01-17
Hey guys. I don't use ubuntu as much as I used to anymore. This means I can't stay up to date on what is happening with moblock-deb / ubuntu. That means i would like for someone to "rip off" my howto, in a new thread, and maintain it. You should preferably know how to make deb packages and have a good understanding of how moblock works. Send me a message, and we'll set something up...

---

### Post by wilberfan on 2007-01-18
I accidently ran the following command to turn OFF daily automatic updates...  How do I turn it back on??

```
sudo chmod -x /etc/cron.daily/moblock-nfq
```

I tried +x (!) but I don't think that's working...

---

### Post by pelle.k on 2007-01-18
> I tried +x (!) but I don't think that's working...
Well, then you are mistaken. Because +x is the correct syntax.

---

### Post by wilberfan on 2007-01-18
> **pelle.k said:**
> Well, then you are mistaken. Because +x is the correct syntax.

{Sigh...}   Sometimes the learning curve is a yucky place to be..!   But thanks for verifying that for me...

---

### Post by foxy123 on 2007-01-21
dev packages for Dapper

---

### Post by hagabaka on 2007-01-21
I know this is probably not the place for moblock tech support, but maybe you'd be willing to help with my problem.

I use moblock and related packages from the first post in this thread on Ubuntu Edgy, and I also use mldonkey and leave it running most of the time. Sometimes I suddenly become unable to connect to my DNS server, as I can't open or ping any website with their URL, but I can with their IP addresses, and my IM or IRC connections are still active. If I stop moblock, I'll immediately become able to access again, and it would continue to work for many hours. My DNS server and its subnet is not contained in /etc/moblock/guarding.p2p or /var/spool/moblock/*. I checked /var/log/moblock.log and syslog, and nothing related show up.

Do you know what the problem could be?

I recently found out that mldonkey can also use the guarding.p2p file. Do you think it's better to use that or moblock?

Thanks

Yaohan Chen

---

### Post by pelle.k on 2007-01-22
> Sometimes I suddenly become unable to connect to my DNS server
Are you behind a router/firewall? In that case, it's a common problem (which by the way has nothing to do with moblock...) as emule puts to much stress (connections) on the cheap hardware used in common routers/firewalls.

> I recently found out that mldonkey can also use the guarding.p2p file. Do you think it's better to use that or moblock?
If you think it's good enough to only block connections from within emule, and have no need for the log file moblock spits out, then yes. You'll have to compile your own blocklist file though. just download level1 blocklist from [www.bluetack.co.uk](www.bluetack.co.uk) and untar/unzip it (if you download level2 blocklist, then just merge it with level1.)

---

### Post by justin on 2007-01-22
Moblock seems to block Gmail (pop.gmail.com, and possibly smtp.gmail.com)

How can I stop it from blocking Gmail?

---

### Post by hagabaka on 2007-01-23
> **pelle.k said:**
> Are you behind a router/firewall? In that case, it's a common problem (which by the way has nothing to do with moblock...) as emule puts to much stress (connections) on the cheap hardware used in common routers/firewalls.

I'm on a university network and there might be a router/firewall/packet shaper involved, but I don't think it goes between me and the DNS server on the same subnet. Also, as soon as I stop the moblock daemon, the connection immediately "goes through", so it does seem related to moblock...or maybe iptables?

---

### Post by pelle.k on 2007-01-23
@hagabaka;
I'm sure there are a few bugs, not ironed out from moblock. I can't be really sure what the problem is, because it depends very much on your setup as well.
Use the ip-filter in emule, which is for the specific task of blocking connections in emule instead.

@justin
You'll have to watch the logfile, and filter those ranges out, during an update of the blocklists. It's described in my howto.

---

### Post by marx2k on 2007-01-24
Does this seem right to you? 

Short guarding.p2p line p2p Corrupt Data Senders:85.3.3.194-85.3.3.194The file format you requested is no longer supported., skipping it...
Short guarding.p2p line Please use the available .zip or .gz downloads instead., skipping it...
Short guarding.p2p line For more information please visit:, skipping it...
Short guarding.p2p line [www.bluetack.co.uk](www.bluetack.co.uk), skipping it...
Ranges loaded: 185137
Merged ranges: 225
Skipped useless ranges: 7017
NFQUEUE: binding to queue '0'


Those 'Short Guarding' lines it skipped, specifically and the amount of Skipped useless ranges seems quite high, no?

As a side note, I've been using MoBlock for months and my ISP got a letter from Pramount Studios about me :sad: 

I will have to figure out how to torrent via proxy

---

### Post by skipo on 2007-01-24
> **marx2k said:**
> Does this seem right to you? 

Short guarding.p2p line p2p Corrupt Data Senders:85.3.3.194-85.3.3.194The file format you requested is no longer supported., skipping it...
Short guarding.p2p line Please use the available .zip or .gz downloads instead., skipping it...
Short guarding.p2p line For more information please visit:, skipping it...
Short guarding.p2p line [www.bluetack.co.uk](www.bluetack.co.uk), skipping it...
Ranges loaded: 185137
Merged ranges: 225
Skipped useless ranges: 7017


You are trying to download a txt-file from bluetack, they are no longer supporting them. You'll have to edit the /etc/cron.daily/moblock-nfq to download proper blocklists.

Comment the lines
```
BLOCKLISTTXT="dshield"
```
and
```

for i in $BLOCKLISTTXT ; do
TIMESTAMP=0
if [ -e $i.$SUFFIX2 ] ; then
TIMESTAMP=`stat --format=%y $i.$SUFFIX2`
echo "File $i.$SUFFIX2 last updated $TIMESTAMP"
TIMESTAMP=`stat --format=%Y $i.$SUFFIX2`
fi
wget -N $URL/$i.$SUFFIX2
if [ `stat --format=%Y $i.$SUFFIX2` -gt $TIMESTAMP ] ; then
UPDATED=$i
fi
done
```
and remove all txt-files (if any) from /var/spool/moblock/

If you want to use the dshield blocklist, try adding it to the 
```
BLOCKLISTS="your blocklists"
```
in /etc/cron.daily/moblock-nfq. It might work. Or not.

---

### Post by Ole32 on 2007-01-25
Is it needed to comment the code? Isn't enought to use  only BLOCKLISTTXT="" at etc/crontab.daily/moblock-nfq?

---

### Post by skipo on 2007-01-26
> **Ole32 said:**
> Is it needed to comment the code? Isn't enought to use  only BLOCKLISTTXT="" at etc/crontab.daily/moblock-nfq?

I would (and did) use the # to make the code comment lines.

---

### Post by jre on 2007-01-26
@marx2k: Did you always have moblock blocking about 180000 ranges? Or did you have the problem described in the HOWTO/this thread that you had only about 2000 ranges blocked for a longer time?
To answer your question: Those many skipped ranges are normal, they are duplicates in the blocklists. But you really have to get rid of the txt-lists.

@Ole32: Your solution will have exactly the same results as commenting out the whole stuff. By the way, these are the lines from cron.daily in the current moblock.deb from moblock-deb.sourceforge.net:
```
BLOCKLISTS="ads-trackers-and-bad-pr0n bogon dshield hijacked level1 level2 Microsoft spider spyware templist"
BLOCKLISTTXT=""
```

greets
jre

EDIT: bluetack.co.uk (the providers of the blocklists) have some problems with their server at the moment. I recommend not to make updates at the moment and wait until they can maintain and provide their blocklists in a normal way again.
Just make (as root or with sudo) a
```
chmod -x /etc/cron.daily/moblock-nfq
```  to stop the daily list updates and
```
chmod +x /etc/cron.daily/moblock-nfq
```  to start it again
For more information have a look at the bluetack homepage or [http://forums.phoenixlabs.org/showthread.php?p=97067#post97067](http://forums.phoenixlabs.org/showthread.php?p=97067#post97067)

---

### Post by pelle.k on 2007-01-26
I acctually suggest leaving the cron job OFF. You can download your blocklist yourself, either through manually running the cron job, or downloading level1 (and maybe level2) with your browser and manually replacing the blocklist.
This way, you will oversee it. There will be no "surprises" like that error message that got into the blocklist insetad of an actual file with ip ranges.

How? Just download level1 from [http://www.bluetack.co.uk/forums/index.php?act=dscriptca&CODE=viewcat&cat_id=4](http://www.bluetack.co.uk/forums/index.php?act=dscriptca&CODE=viewcat&cat_id=4) and untar/unzip it and "mv level1 /etc/moblock/guarding.p2p"
If you need to merge level1 and level2 (for gods sake, untar/unzip both first) just "cat level1 level2 > merged.p2p" and then move merged.p2p to /etc/moblock/guarding.p2p and restart moblock. comprende?

Level1 and level2 blocklist, _will_ be enough in most cases.

---

### Post by zivagolee on 2007-01-26
Hi Guys,

For some reason, the firehol instructions listed in the first post doesn't seem to work for me.  Not sure why but the moblock install that I have has 3 chains and not one MOBLOCK chain.  You can see the MoBlock-nfq.sh script to see that is creating 3 chains so I'm not sure which version of moblock that pelle.k has (I believe mine was from the repos).

These are the changes I made to make it work.  Hopefully it helps someone out..

open /etc/firehol/firehol.conf and add 
```

iptables --new MOBLOCK_IN
iptables --new MOBLOCK_OUT
iptables --new MOBLOCK_FW
iptables -A MOBLOCK_IN -j NFQUEUE
iptables -A MOBLOCK_OUT -j NFQUEUE
iptables -A MOBLOCK_FW -j NFQUEUE


``` under "version 5"
Change all instances you wish to be inspected by moblock to MOBLOCK_IN, MOBLOCK_OUT, or MOBLOCK_FW instead of accept...

This is an example of how it might look;
```
#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5

# Moblock chain
iptables --new MOBLOCK_IN
iptables --new MOBLOCK_OUT
iptables --new MOBLOCK_FW
iptables -A MOBLOCK_IN -j NFQUEUE
iptables -A MOBLOCK_OUT -j NFQUEUE
iptables -A MOBLOCK_FW -j NFQUEUE

# Bittorrent. tcp ports 6881 to 6999
server_torrent_ports="tcp/6881:6999"
client_torrent_ports="any"

# Example udp ports
server_exampleport_ports="udp/15001:15011"
client_exampleport_ports="any"

# "any" means any interface, you can substitute it
# for eth0 or whatever.

interface any world

        # Let torrent and exampleport through, and
        # filter them in moblock.
        server "torrent" MOBLOCK_IN
        server "exampleport" MOBLOCK_IN

        # This will send http traffic directly
        # to accept instead of moblock
        # thus whitelisting it...
        client http accept

        # Filter all outgoing connections, and their replies.
        client all MOBLOCK_OUT

```


[COLOR="Red"]**This section is NOT required. You can safely skip this part...**[/COLOR]

Instead of one "interface" section you can have two interface sections (if you're connected to more than one network...)
```

# Your internet interface
interface eth0 myinternet

        server "torrent" MOBLOCK_IN
        server "exampleport" MOBLOCK_IN

        # This will send http traffic directly
        # to accept instead of moblock
        # thus whitelisting it...
        client http accept

        client all MOBLOCK_OUT

# Your local network
interface eth1 mylan

        # You can access whatever on your lan        
        client all accept
        
        # If you want your lan user to access your http server
        server http accept

```

In the /etc/moblock/MoBlock-nfq.sh file, you need to change:

```

ACTIVATE_CHAINS=1

```

to

```

ACTIVATE_CHAINS=0

```

so it will use the current iptable chains that was setup by firehol.

Just as an FYI, if you need to do any firewall changes to firehol, do these steps:

Modify firehol.conf
Stop moblock - /etc/init.d/moblock stop
Restart firehol - /etc/init.d/firehol restart
Start moblock - /etc/init.d/moblock start

As noted by pelle.k, do a 'moblock reload' after updating the guardian.p2p file.

---

### Post by jre on 2007-01-28
> **pelle.k said:**
> Level1 and level2 blocklist, _will_ be enough in most cases.
I totally agree that users shouldn´t just use the cron.daily job without checking if things really work. But otherwise I think level1 and level2 aren´t enough. See [Bluetacks blocklist FAQ]("http://www.bluetack.co.uk/modules.php?name=FAQ&myfaq=yes&id_cat=6&categories=Blacklists+FAQ") for which lists are available and why bluetack recommends to use them (they even recommend "edu").
By now the problems at bluetack seem to be over. The cron.daily job is working flawless (and even while bluetack had server problems it never resulted in wrong blocklists (=too few ranges blocked) on  the users computers.
So either use the manual method as described by pelle a few posts above (with the lists of your choice) or the cron.daily job (as long as you use it with a line like ```
BLOCKLISTS="ads-trackers-and-bad-pr0n bogon dshield hijacked level1 level2 Microsoft spider spyware templist"
``` without a "nipfilter.dat" or some other list in the wrong format.
If anyone sees a problem feel free to report it at phoenixlabs.org in the PeerGuardian Linux forum.
jre

EDIT: bluetack doesn´t really "recommend" to use any lists but recommends to use the lists that fit a user´s needs (you see the difference ;-) )

---

### Post by bodhi.zazen on 2007-02-02
Nice How-to

This thread has been added to the UDSF wiki.

[Moblock](http://doc.gwos.org/index.php/Moblock)

---

### Post by queen_yoshi on 2007-02-04
G'Day,

I keep getting this error when trying to install on Edgy following everything as written both here and on the wiki:

```
nirvash@gekkostate:~$ sudo apt-get install modblock-nfq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package modblock-nfq
```

In case anyone else has had the same problem I found a workaround:

Just download the deb for the Dapper install.
Install via terminal, you will get an error about dependancys, so dont worry. 
After you have done that type:
```
sudo apt-get install -f
```
You will then be asked if you would like to update the package you have just previously tried to install, say yes.
Then everything will update nicely and connect to the internet to update the blocklists, and modprobe will be running. To verify you can do the checks mentioned at the start of this How-To.


(Apologies if this has already been posted but I kept getting the same error, even on a fresh install of Edgy and this is all that worked:mrgreen:)

---

### Post by zivagolee on 2007-02-04
> **queen_yoshi said:**
> G'Day,

I keep getting this error when trying to install on Edgy following everything as written both here and on the wiki:

```
nirvash@gekkostate:~$ sudo apt-get install modblock-nfq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package modblock-nfq
```

(Apologies if this has already been posted but I kept getting the same error, even on a fresh install of Edgy and this is all that worked:mrgreen:)

You can also add in the /etc/apt/sources.list:

#moblock
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main

then do sudo apt-get install moblock-nfq

---

### Post by jre on 2007-02-04
> **queen_yoshi said:**
> 
```
nirvash@gekkostate:~$ sudo apt-get install modblock-nfq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package modblock-nfq
```
The PeerGuardian alternative is called "moblock" (not modblock).
"modprobe" is for (un)loading kernel modules, which is also needed to get moblock running.

greets
jre

---

### Post by dawg on 2007-02-04
nice how to...but i've got a question.  how do i disable moblock?  reason i ask is because its blocking game servers.

---

### Post by pelle.k on 2007-02-05
@dawg:
I've updated the howto faq. Look there.

---

### Post by dawg on 2007-02-05
> **pelle.k said:**
> @dawg:
I've updated the howto faq. Look there.

Uhm, I can't find it.  I hope you're not referring to the "startup" portion of the how to.  I wan't to be able to turn it on and off as I please, kinda like peerguardian, would it even be possible?  if not, using your "startup" method, would i be able to log out and then log back in, or would i have to restart the system?  thanks a lot.

---

### Post by wilberfan on 2007-02-05
> **dawg said:**
>   I wan't to be able to turn it on and off as I please, kinda like peerguardian, would it even be possible?

Thank you SO much for asking this, and Pelle.k--thanks for posting the answer to the FAQ's.   I've been wondering about this, too, for awhile!

:)

---

### Post by pelle.k on 2007-02-06
update-rc.d is a utility to manage the links to init scripts in certain runlevels. An example of a runlevel is "startup" and "shutdown". So, yes, it only applies to that situation.
To start and stop moblock (temporarily), you do what you would have done with every other daemon in the system; (since daemons live in /etc/init.d/)
```
sudo /etc/init.d/moblock-nfq start
```
```
sudo /etc/init.d/moblock-nfq stop
```

---

### Post by dawg on 2007-02-06
thanks pelle.k, im still new to the entire linux scene.  Im trying to make the transition from windows to linux, and let me tell you, its confusing at times.  so thanks for your help.

---

### Post by rafiks on 2007-02-07
All of a sudden ,since this morning my google talk is already being blocked.. How do i modify the blocklist?

---

### Post by rafiks on 2007-02-07
Solved it ..I just whitelisted port 5222 ..thanks anyway!

---

### Post by Pugwash on 2007-02-09
Many thanks for the guide, very useful. :)

---

### Post by shookone on 2007-02-23
Is using FAIL2BAN with this setup possible without overriding iptables

FAIL2BAN: bans failed attempts on a service (FTP SSH ETC.)
FIREHOL: iptables firewall
MOBLOCK: blocks ip address from a list of ip addresses (like peerguardian)

Will there be any conflicts if i run fail2ban with my current firehol/moblock settings?

Do fail2ban defaults over ride firehol settings.. All my inbound traffic goes to moblock, ip blocking program.

I believe that the fwstart section of fail2ban will cause some problems. Anyone with any ideas let me know please.

firehol.conf:

```
version 5

#iface
lan_iface="eth1"
net_iface="eth0"

# ip zone variables
lan_ips_zone="192.168.1.0/24"

#Custom Service
server_kaid_ports="tcp/8080 tcp/37500 udp/37500 tcp/34525 udp/34525 tcp/34523 udp/34523 tcp/37501 udp/37501 tcp/34522 udp/34522 tcp/30000 udp/30000"
client_kaid_ports="default"
server_lw_ports="tcp/18548"
client_lw_ports="default"
server_dc_ports="tcp/3117 udp/2290"
client_dc_ports="default"
server_mule_ports="tcp/4662 udp/4672"
client_mule_ports="default"

# service sets
# NOTE: the internal LAN is unprotected against other internal machines by the
#       firewall, as all services are allowed to pass through
lan_services="all"
net_services="mule vnc ftp ssh kaid dc lw"
http_services="http https" #ignores moblock

# moblock settings
iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE

# IP White Listing 
# (Examples)
# iptables -I OUTPUT -d a.b.c.d -j ACCEPT   | Single IP
# iptables -I OUTPUT -d a.b.c.0/24 -j ACCEPT| Net with Netmask
# iptables -I INPUT -s a.b.c.d -j ACCEPT
# iptables -I INPUT -s a.c.c.0/24 -j ACCEPT

iptables -I OUTPUT -d 66.135.32.175 -j ACCEPT
iptables -I OUTPUT -d 64.34.165.84 -j ACCEPT
iptables -I INPUT -s 66.135.32.175 -j ACCEPT
iptables -I INPUT -s 64.34.165.84 -j ACCEPT
iptables -I OUTPUT -d 72.21.211.32 -j ACCEPT
iptables -I INPUT -s 72.21.211.32 -j ACCEPT
iptables -I OUTPUT -d 66.230.129.242 -j ACCEPT
iptables -I INPUT -s 66.230.129.242 -j ACCEPT
iptables -I OUTPUT -d 65.207.183.49 -j ACCEPT
iptables -I INPUT -s 65.207.183.49 -j ACCEPT
iptables -I INPUT -d 218.55.89.101 -j DROP
iptables -I INPUT -s 218.55.89.101 -j DROP
iptables -I INPUT -d 65.207.183.49 -j DROP
iptables -I INPUT -s 65.207.183.49 -j DROP

## interfaces
interface "${lan_iface}" lan src "${lan_ips_zone}"
        server "${lan_services}" accept
        server "ident" reject with tcp-reset

        client all accept

interface "${net_iface}" net src not "${lan_ips_zone} ${UNROUTABLE_IPS}"
        protection strong 10/sec 10


        server "${net_services}" accept
        server "ident" reject with tcp-reset
        client "${http_services}" accept
        #client all accept
        client all moblock


# routers

# route lan <-> net
router lan2net inface "${lan_iface}" outface "${net_iface}"
        masquerade
        route all accept
router net2lan inface "${net_iface}" outface "${lan_iface}"
        route all accept

FIREHOL_LOG_MODE="ULOG"

```

fail2ban.conf:
```

# Fail2Ban configuration file
#
# $Revision: 1.9 $
#
# 2005.06.21  modified for readability  Iain Lea  iain@bricbrac.de

[DEFAULT]
# Option:  background
# Notes.:  start fail2ban as a daemon. Output is redirect to logfile.
# Values:  [true | false]  Default:  false
#
background = true

# Option:  verbose
# Notes.:  verbosity of the output.
#           0 - regular level
#           1 - INFO level
#           2 - DEBUG level (but commands get executed as opposed to
#                debug option)
# Values:  NUM  Default:  0
#
verbose = 1

# Option:  debug
# Notes.:  enable debug mode. No real commands gets executed but only
#          reported, more verbose output, bypass root user test.
# Values:  [true | false]  Default:  false
#
debug = false

# Option:  logtargets
# Notes.:  log targets. Space separated list of logging targets.
# Values:  STDERR SYSLOG file  Default:  /var/log/fail2ban.log
#
logtargets = /var/log/fail2ban.log

# Option:  syslog-target
# Notes.:  where to find syslog facility if logtarget SYSLOG.
# Values:  SOCKET HOST HOST:PORT  Default: /dev/log
#
syslog-target = /dev/log

# Option:  syslog-facility
# Notes.:  which syslog facility to use if logtarget SYSLOG.
# Values:  NUM  Default: 1
#
syslog-facility = 1

# Option:  pidlock
# Notes.:  path of the PID lock file (must be able to write to file).
# Values:  FILE  Default:  /var/run/fail2ban.pid
#
pidlock = /var/run/fail2ban.pid

# Option:  maxfailures
# Notes.:  number of failures before IP gets banned.
# Values:  NUM  Default:  5
#
maxfailures = 5

# Option:  bantime
# Notes.:  number of seconds an IP will be banned. If set to a negative
#          value, IP will never be unbanned (permanent banning).
# Values:  NUM  Default:  600
#
bantime = 600

# Option:  findtime
# Notes.:  lifetime in seconds of a "failed" log entry.
# Values:  NUM  Default:  600
#
findtime = 600

# Option:  ignoreip
# Notes.:  space separated list of IP's to be ignored by fail2ban.
#          You can use CIDR mask in order to specify a range.
#          Example:  ignoreip = 192.168.0.1/24 123.45.235.65
# Values:  IP  Default:  
#
ignoreip = 

# Option:  cmdstart
# Notes.:  command executed once at the start of Fail2Ban
# Values:  CMD  Default:
#
cmdstart = 

# Option:  cmdend
# Notes.:  command executed once at the end of Fail2Ban.
# Values:  CMD  Default:
#
cmdend = 

# Option:  polltime
# Notes.:  number of seconds fail2ban sleeps between iterations.
# Values:  NUM  Default:  1
#
polltime = 1

# Option:  reinittime
# Notes.:  minimal number of seconds between the re-initialization of
#          firewalls due to external changes in their rules (see fwcheck)
# Values:  NUM  Default:  100
#
reinittime = 10

# Option:  maxreinits
# Notes.:  maximal number of re-initialization of firewalls due to external
#          changes. -1 stays for infinite, so only reinittime is of importance
# Values:  NUM  Default:  -1
#
maxreinits = 1000

# NOTE: Interpolations
#
# fwstart, as well as fwend, fwcheck, fwban, fwunban, use interpolations
# so %(__name__)s  will be substituted by a name of each section
# (unless the option is overriden in a section).
# If you are going to use interpolations in your setup, please make
# sure that you specified options port and protocol (which also has
# an option in DEFAULT).
#

# Option:  protocol
# Notes.:  internally used by config reader for interpolations.
# Values:  [ tcp | udp | icmp | all ] Default: tcp
#
protocol = tcp

# Option:  fwchain
# Notes.:  chain from which to jump into fail2ban chains
# Values:  TEXT  Default: INPUT
#
fwchain = INPUT

# Option:  fwstart
# Notes.:  command executed once at the start of Fail2Ban.
# Values:  CMD  Default:
#
fwstart = iptables -N fail2ban-%(__name__)s
          iptables -A fail2ban-%(__name__)s -j RETURN
          iptables -I %(fwchain)s -p %(protocol)s --dport %(port)s -j fail2ban-%(__name__)s

# Option:  fwend
# Notes.:  command executed once at the end of Fail2Ban
# Values:  CMD  Default:
#
fwend = iptables -D %(fwchain)s -p %(protocol)s --dport %(port)s -j fail2ban-%(__name__)s
        iptables -F fail2ban-%(__name__)s
        iptables -X fail2ban-%(__name__)s

# Option:  fwcheck
# Notes.:  command executed once before each fwban command
# Values:  CMD  Default:
#
fwcheck = iptables -L %(fwchain)s | grep -q fail2ban-%(__name__)s

# Option:  fwban
# Notes.:  command executed when banning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    <ip>  IP address
#          <failures>  number of failures
#          <failtime>  unix timestamp of the last failure
#          <bantime>  unix timestamp of the ban time
# Values:  CMD
# Default: iptables -I INPUT 1 -s <ip> -j DROP
#
fwban = iptables -I fail2ban-%(__name__)s 1 -s <ip> -j DROP

# Option:  fwunban
# Notes.:  command executed when unbanning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    <ip>  IP address
#          <bantime>  unix timestamp of the ban time
#          <unbantime>  unix timestamp of the unban time
# Values:  CMD
# Default: iptables -D INPUT -s <ip> -j DROP
#
fwunban = iptables -D fail2ban-%(__name__)s -s <ip> -j DROP

[MAIL]
# Option:  enabled
# Notes.:  enable mail notification when banning an IP address.
# Values:  [true | false]  Default:  false
#
enabled = false

# Option:  host
# Notes.:  host running the mail server.
# Values:  STR  Default:  localhost
#
host = localhost

# Option:  port
# Notes.:  port of the mail server.
# Values:  INT  Default:  25
#
port = 25

# Option:  user
# Notes.:  the username for smtp-server if authentification is required.
#          if user is empty, no authentification is done.
# Values:  STR  Default:  
#
user = 

# Option:  password
# Notes.:  the smtp-user's password if authentification is required.
# Values:  STR  Default:  
#
password = 

# Option:  from
# Notes.:  e-mail address of the sender.
# Values:  MAIL  Default:  fail2ban
#
from = fail2ban@localhost

# Option:  to
# Notes.:  e-mail addresses of the receiver. Addresses are space
#          separated.
# Values:  MAIL  Default:  root
#
to = root@localhost

# Option:  localtime
# Notes.:  report local time (including timezone) or GMT
# Values:  [true | false]  Default:  false
#
localtime = true

# Option:  subject
# Notes.:  subject of the e-mail.
# Tags:    <section> active section (eg ssh, apache, etc)
#          <ip>  IP address
#          <failures>  number of failures
#          <failtime>  unix timestamp of the last failure
# Values:  TEXT  Default:  [Fail2Ban] <section>: Banned <ip>
#
subject = [Fail2Ban] <section>: Banned <ip>

# Option:  message
# Notes.:  message of the e-mail.
# Tags:    <section> active section (eg ssh, apache, etc)
#          <ip>  IP address
#          <failures>  number of failures
#          <failtime>  unix timestamp of the last failure
#          <br>  new line
# Values:  TEXT  Default:
#
message = Hi,<br>
          The IP <ip> has just been banned by Fail2Ban after
          <failures> attempts against <section>.<br>
          Regards,<br>
          Fail2Ban

# You can define a new section for each log file to check for
# password failure. Each section has to define the following
# options: logfile, fwban, fwunban, timeregex, timepattern,
# failregex.


[SASL]
# Option:  enabled
# Notes.:  enable monitoring for this section.
# Values:  [true | false]  Default:  true
#
enabled = false

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = smtp

# Option:  logfile
# Notes.:  logfile to monitor.
# Values:  FILE  Default:  /var/log/auth.log
#
logfile = /var/log/mail.log

# Option:  timeregex
# Notes.:  regex to match timestamp
# Values:  [Mar  7 17:53:28]
# Default: \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
#
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}

# Option:  timepattern
# Notes.:  format used in "timeregex" fields definition. Note that '%' must be
#          escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule)
# Values:  TEXT  Default:  %%b %%d %%H:%%M:%%S
#
timepattern = %%b %%d %%H:%%M:%%S

# Option:  failregex
# Notes.:  regex to match the password failures messages in the logfile.
# Values:  TEXT  Default:
#
failregex = : warning: [-._\w]+\[(?P<host>[.\d]+)\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed$


[Apache]
# Option:  enabled
# Notes.:  enable monitoring for this section.
# Values:  [true | false]  Default:  false
#
enabled = false

# Option:  logfile
# Notes.:  logfile to monitor.
# Values:  FILE  Default:  /var/log/apache/error.log
# Other.: /var/log/apache2/error.log
#
logfile = /var/log/apache/error.log

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = http

# Option:  timeregex
# Notes.:  regex to match timestamp in Apache logfile. For TAI64N format,
#          use timeregex = @[0-9a-f]{24}
# Values:  [Wed Jan 05 15:08:01 2005]
# Default: \S{3} \S{3} \d{2} \d{2}:\d{2}:\d{2} \d{4}
#
timeregex = \S{3} \S{3} \d{2} \d{2}:\d{2}:\d{2} \d{4}

# Option:  timepattern
# Notes.:  format used in "timeregex" fields definition. Note that '%' must be
#          escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule).
#          For TAI64N format, use timepattern = tai64n
# Values:  TEXT  Default:  %%a %%b %%d %%H:%%M:%%S %%Y
#
timepattern = %%a %%b %%d %%H:%%M:%%S %%Y

# Option:  failregex
# Notes.:  regex to match the password failure messages in the logfile.
# Values:  TEXT  Default:  [[]client (?P<host>\S*)[]] user .*(?:: authentication failure|not found)
#
failregex = [[]client (?P<host>\S*)[]] user .*(?:: authentication failure|not found)

[ApacheAttacks]
# Option:  enabled
# Notes.:  enable monitoring for this section.
# Values:  [true | false]  Default:  false
#
enabled = false

# Option:  logfile
# Notes.:  logfile to monitor.
# Values:  FILE  Default:  /var/log/apache/access.log
#
logfile = /var/log/apache/access.log

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = http

# Option:  maxfailures
# Notes.:  number of failures before IP gets banned.
# Values:  NUM  Default:  5
#
maxfailures = 2

# Option:  timeregex
# Notes.:  regex to match timestamp in Apache access logfile.
# Values:  [19/Feb/2006:08:38:18]
# Default: \d{2}/\S{3}/\d{4}:\d{2}:\d{2}:\d{2}
#
timeregex = \d{2}/\S{3}/\d{4}:\d{2}:\d{2}:\d{2}

# Option:  timepattern
# Notes.:  format used in "timeregex" fields definition. Note that '%' must be
#          escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule)
# Values:  TEXT  Default: %%d/%%b/%%Y:%%H:%%M:%%S
#
timepattern = %%d/%%b/%%Y:%%H:%%M:%%S

# Option:  failregex
# Notes.:  regex to match the password failure messages in the logfile.
# Values:  TEXT  Default:  [[]client (?P<host>\S*)[]] user .*(?:: authentication failure|not found)
#
failregex = ^(?P<host>\S*) -.*"GET .*(?:awstats\.pl\?configdir=|index2\.php\?_REQUEST\[option\].*)\|echo.*

[VSFTPD]
# Option: enabled
# Notes.: enable monitoring for this section.
# Values: [true | false] Default: false
#
enabled = false

# Option: logfile
# Notes.: logfile to monitor.
# Values: FILE Default: /var/log/secure
#
logfile = /var/log/vsftpd.log

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = ftp

# Option: timeregex
# Notes.: regex to match timestamp in VSFTPD logfile.
# Values: [Mar 7 17:53:28]
# Default: \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
#
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}

# Option: timepattern
# Notes.: format used in "timeregex" fields definition. Note that '%' must be
# escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule)
# Values: TEXT Default: %%b %%d %%H:%%M:%%S
#
timepattern = %%b %%d %%H:%%M:%%S

# Option: failregex
# Notes.: regex to match the password failures messages in the logfile.
# Values: TEXT Default: Authentication failure|Failed password|Invalid user
#
failregex = \[.+\] FAIL LOGIN: Client "(?P<host>\S+)"$


[PROFTPD]
# Option: enabled
# Notes.: enable monitoring for this section.
# Values: [true | false] Default: false
#
enabled = true

# Option: logfile
# Notes.: logfile to monitor.
# Values: FILE Default: /var/log/proftpd/proftpd.log
# Other.: /var/log/auth.log
#
logfile = /var/log/proftpd/proftpd.log

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default: ftp
#
port = ftp

# Option: timeregex
# Notes.: regex to match timestamp in VSFTPD logfile.
# Values: [Mar 7 17:53:28]
# Default: \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
#
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}

# Option: timepattern
# Notes.: format used in "timeregex" fields definition. Note that '%' must be
# escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule)
# Values: TEXT Default: %%b %%d %%H:%%M:%%S
#
timepattern = %%b %%d %%H:%%M:%%S

# Option: failregex
# Notes.: regex to match the password failures messages in the logfile.
# Values: TEXT Default:
#
failregex = USER \S+: no such user found from \S* ?\[(?P<host>\S+)\] to \S+\s*$


[SSH]
# Option:  enabled
# Notes.:  enable monitoring for this section.
# Values:  [true | false]  Default:  true
#
enabled = true

# Option:  logfile
# Notes.:  logfile to monitor.
# Values:  FILE  Default:  /var/log/auth.log
#
logfile = /var/log/auth.log

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = ssh

# Option:  timeregex
# Notes.:  regex to match timestamp in SSH logfile. For TAI64N format,
#          use timeregex = @[0-9a-f]{24}
# Values:  [Mar  7 17:53:28]
# Default: \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
#
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}

# Option:  timepattern
# Notes.:  format used in "timeregex" fields definition. Note that '%' must be
#          escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule).
#          For TAI64N format, use timepattern = tai64n
# Values:  TEXT  Default:  %%b %%d %%H:%%M:%%S
#
timepattern = %%b %%d %%H:%%M:%%S

# Option:  failregex
# Notes.:  regex to match the password failures messages in the logfile.
# Values:  TEXT  Default:  (?:Authentication failure|Failed (?:keyboard-interactive/pam|password)) for(?: illegal user)? .* from (?:::f{4,6}:)?(?P<host>\S*)
#
failregex = : (?:(?:Authentication failure|Failed [-/\w+]+) for(?: [iI](?:llegal|nvalid) user)?|[Ii](?:llegal|nvalid) user|ROOT LOGIN REFUSED) .*(?: from|FROM) (?:::f{4,6}:)?(?P<host>\S*)

```

---

### Post by zivagolee on 2007-02-23
I've used fail2ban successfully with moblock.  However, if you reload firehol, it will wipe out the moblock *and* fail2ban entries.

If you need to reload firehol, do these steps:

stop fail2ban
stop moblock
stop or restart firehol
start moblock
start fail2ban

Your entries seem pretty standard and it should work fine with fail2ban.  If you don't want to deal with fail2ban, you can always use denyhosts which uses tcpwrappers instead of iptables to do the same thing.

---

### Post by shookone on 2007-02-23
> **zivagolee said:**
> I've used fail2ban successfully with moblock.  However, if you reload firehol, it will wipe out the moblock *and* fail2ban entries.

If you need to reload firehol, do these steps:

stop fail2ban
stop moblock
stop or restart firehol
start moblock
start fail2ban

Your entries seem pretty standard and it should work fine with fail2ban.  If you don't want to deal with fail2ban, you can always use denyhosts which uses tcpwrappers instead of iptables to do the same thing.

Thanks ... i will make a note of that. However i'm having a problem that is not related to fail2ban.. i made changes in my firehol.conf. Please see conf. below.

firehol.conf:
```
version 5

#iface
lan_iface="eth1"
net_iface="eth0"

# ip zone variables
lan_ips_zone="192.168.1.0/24"

#Custom Service
server_kaid_ports="tcp/8080 tcp/37500 udp/37500 tcp/34525 udp/34525 tcp/34523 udp/34523 tcp/37501 udp/37501 tcp/34522 udp/34522 tcp/30000 udp/30000"
client_kaid_ports="default"
server_lw_ports="tcp/18548"
client_lw_ports="default"
server_dc_ports="tcp/3117 udp/2290"
client_dc_ports="default"
server_mule_ports="tcp/4662 udp/4672"
client_mule_ports="default"

# service sets
# NOTE: the internal LAN is unprotected against other internal machines by the
#       firewall, as all services are allowed to pass through
lan_services="all"
net_services="mule vnc ftp ssh kaid dc lw"
http_services="http https" #ignores moblock

# moblock settings
iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE

# IP White Listing 
# (Examples)
# iptables -I OUTPUT -d a.b.c.d -j ACCEPT   | Single IP
# iptables -I OUTPUT -d a.b.c.0/24 -j ACCEPT| Net with Netmask
# iptables -I INPUT -s a.b.c.d -j ACCEPT
# iptables -I INPUT -s a.c.c.0/24 -j ACCEPT

iptables -I OUTPUT -d 66.135.32.175 -j ACCEPT
iptables -I OUTPUT -d 64.34.165.84 -j ACCEPT
iptables -I INPUT -s 66.135.32.175 -j ACCEPT
iptables -I INPUT -s 64.34.165.84 -j ACCEPT
iptables -I OUTPUT -d 72.21.211.32 -j ACCEPT
iptables -I INPUT -s 72.21.211.32 -j ACCEPT
iptables -I OUTPUT -d 66.230.129.242 -j ACCEPT
iptables -I INPUT -s 66.230.129.242 -j ACCEPT
iptables -I OUTPUT -d 65.207.183.49 -j ACCEPT
iptables -I INPUT -s 65.207.183.49 -j ACCEPT
iptables -I INPUT -d 218.55.89.101 -j DROP
iptables -I INPUT -s 218.55.89.101 -j DROP
iptables -I INPUT -d 65.207.183.49 -j DROP
iptables -I INPUT -s 65.207.183.49 -j DROP

## interfaces
interface "${lan_iface}" lan src "${lan_ips_zone}"
        server "${lan_services}" accept
        server "ident" reject with tcp-reset

        client all accept

interface "${net_iface}" net src not "${lan_ips_zone} ${UNROUTABLE_IPS}"
        protection strong 10/sec 10


        server "${net_services}" accept
        server "ident" reject with tcp-reset
        client "${http_services}" accept
        #client all accept
        client all moblock


# routers

# route lan <-> net
router lan2net inface "${lan_iface}" outface "${net_iface}"
        masquerade
        route all accept
router net2lan inface "${net_iface}" outface "${lan_iface}"
        route all accept

FIREHOL_LOG_MODE="ULOG"
```


[HTML]ERROR   : # 1.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 68 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_net_all_c11 -m state --state NEW\,ESTABLISHED -j moblock 
OUTPUT  : 

iptables v1.3.5: Couldn't load target `moblock':/lib/iptables/libipt_moblock.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.[/HTML]

line 68 = #client all accept
```
## interfaces
interface "${lan_iface}" lan src "${lan_ips_zone}"
        server "${lan_services}" accept
        server "ident" reject with tcp-reset

        client all accept

interface "${net_iface}" net src not "${lan_ips_zone} ${UNROUTABLE_IPS}"
        protection strong 10/sec 10


        server "${net_services}" accept
        server "ident" reject with tcp-reset
        client "${http_services}" accept
        #client all accept
        client all moblock

```

i uncommented "client all moblock" and commented "client all accept"

---

### Post by zivagolee on 2007-02-23
Here's mine.. If you look at my post #389, I had to modify the original post since the version of moblock that I have created 3 iptables chains.  fail2ban seemed to work right out of the box...

```

version 5

# Moblock chain
iptables --new MOBLOCK_IN
iptables --new MOBLOCK_OUT
iptables --new MOBLOCK_FW
iptables -A MOBLOCK_IN -j NFQUEUE
iptables -A MOBLOCK_OUT -j NFQUEUE
iptables -A MOBLOCK_FW -j NFQUEUE

interface eth0 internet

        protection strong 10/sec 10

        # Let torrent and exampleport through, and
        # filter them in moblock.
        server "ssh ftp ident msn" MOBLOCK_IN

        # This will send http traffic directly
        # to accept instead of moblock
        # thus whitelisting it...
        client http accept
        client https accept

        # Filter all outgoing connections, and their replies.
        client all MOBLOCK_OUT

```

This config worked for me...

---

### Post by shookone on 2007-02-24
It seems that the problem was like 69 which was "client all moblock" which should be "client all MOBLOCK"

I didn't think it would be case sensitive.. But it fixed the problem i was having.

> **zivagolee said:**
> Here's mine.. If you look at my post #389, I had to modify the original post since the version of moblock that I have created 3 iptables chains.  fail2ban seemed to work right out of the box...

```

version 5

# Moblock chain
iptables --new MOBLOCK_IN
iptables --new MOBLOCK_OUT
iptables --new MOBLOCK_FW
iptables -A MOBLOCK_IN -j NFQUEUE
iptables -A MOBLOCK_OUT -j NFQUEUE
iptables -A MOBLOCK_FW -j NFQUEUE

interface eth0 internet

        protection strong 10/sec 10

        # Let torrent and exampleport through, and
        # filter them in moblock.
        server "ssh ftp ident msn" MOBLOCK_IN

        # This will send http traffic directly
        # to accept instead of moblock
        # thus whitelisting it...
        client http accept
        client https accept

        # Filter all outgoing connections, and their replies.
        client all MOBLOCK_OUT

```

This config worked for me...

---

### Post by shookone on 2007-02-24
How do i get it to load in that order at start up or is there no need to?

> **zivagolee said:**
> I've used fail2ban successfully with moblock.  However, if you reload firehol, it will wipe out the moblock *and* fail2ban entries.

If you need to reload firehol, do these steps:

stop fail2ban
stop moblock
stop or restart firehol
start moblock
start fail2ban

Your entries seem pretty standard and it should work fine with fail2ban.  If you don't want to deal with fail2ban, you can always use denyhosts which uses tcpwrappers instead of iptables to do the same thing.

---

### Post by thebluffer on 2007-03-01
Hello when I launch this command : cat /etc/moblock/guarding.p2p
File is empty, how can I force the update ?

---

### Post by thebluffer on 2007-03-01
Ok I download manually the list and It works...
bluetack is always down or it's a problem with my config ?

---

### Post by zivagolee on 2007-03-01
> **shookone said:**
> How do i get it to load in that order at start up or is there no need to?

Check /etc/rc#.d

If you are using X, then you are most likely using runlevel 5.

So, check /etc/rc5.d/

On mine, they are all in order on bootup.. You will see the S## numbers.. that's how they startup.

---

### Post by zivagolee on 2007-03-01
> **thebluffer said:**
> Ok I download manually the list and It works...
bluetack is always down or it's a problem with my config ?

I think they've been up and down for the past cpl of weeks.  Check their frontpage.

---

### Post by baroumas on 2007-03-02
Great guide
I even got Moblock working with Shorewall firewall perfectly, and i didn't have any iptables knowledges before i read this guide
Thanks alot!

---

### Post by qpwoeiruty on 2007-03-02
/etc/firehol/firehol.conf is empty. Is there anywhere else the config file could be?

---

### Post by zivagolee on 2007-03-02
> **qpwoeiruty said:**
> /etc/firehol/firehol.conf is empty. Is there anywhere else the config file could be?

New install?  It needs to be populated..

---

### Post by qpwoeiruty on 2007-03-02
> **zivagolee said:**
> New install?  It needs to be populated..

I installed it with dansguardian a couple weeks ago.

How would I "populate" it?

---

### Post by zivagolee on 2007-03-02
> **qpwoeiruty said:**
> I installed it with dansguardian a couple weeks ago.

How would I "populate" it?

You can use a text editor.  I would start with a tutorial:

[http://firehol.sourceforge.net/](http://firehol.sourceforge.net/)

or

you can read post #1 and try editing it with his notes...

---

### Post by qpwoeiruty on 2007-03-02
> **zivagolee said:**
> You can use a text editor.  I would start with a tutorial:

[http://firehol.sourceforge.net/](http://firehol.sourceforge.net/)

or

you can read post #1 and try editing it with his notes...

Thanks, I read through that tutorial earlier. I guess I was hoping that firehol could create a well commented framework file from the detected interfaces that I could edit. Lots of typing ahead of me, it seems...

---

### Post by zivagolee on 2007-03-02
> **qpwoeiruty said:**
> Thanks, I read through that tutorial earlier. I guess I was hoping that firehol could create a well commented framework file from the detected interfaces that I could edit. Lots of typing ahead of me, it seems...

Yea, firehol is pretty hands-on when it comes to firewall rules.  But, thats what makes it very configurable...

---

### Post by pelle.k on 2007-03-03
firehol.conf cant even be read as a regular user, so you _have_ to be su or sudo to edit it. You can't even "tab complete" this file in bash as regular user. It should be filled with a very basic config when installed for the very first time...

---

### Post by bravemosquito on 2007-03-08
Hi, I'm a newbie in moblock's things and I've question about it: Is FireHOL necessary for proper function of peerstopping ?

---

### Post by pelle.k on 2007-03-09
no.

---

### Post by Benjamin.Britton on 2007-03-11
I've just followed your guide, I have moblock installed, however, I can not get it to add the bluetack listings.
Output from "tail -f /var/log/moblock.log"

```
Got SIGTERM! Dumping stats and exiting.
Ranges loaded: 0
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'
Got SIGTERM! Dumping stats and exiting.
Ranges loaded: 0
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'

```

Output from "/etc/cron.daily/moblock-nfq"
```
 moblock: checking for new block lists...
--15:33:06--  http://www.bluetack.co.uk/
           => `-'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.bluetack.co.uk/forums/index.php [following]
--15:33:06--  http://www.bluetack.co.uk/forums/index.php
           => `-'
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [    <=>                              ] 99,930       115.57K/s             

15:33:08 (115.31 KB/s) - `-' saved [99930]

------------ 2007-03-11 15:33:08 GMT Begin PeerGuardian 
File ads-trackers-and-bad-pr0n.gz last updated 2007-03-09 10:22:52.000000000 +0000
--15:33:08--  http://www.bluetack.co.uk/config/ads-trackers-and-bad-pr0n.gz
           => `ads-trackers-and-bad-pr0n.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.bluetack.info/temp/ads-trackers-and-bad-pr0n.gz [following]
--15:33:08--  http://www.bluetack.info/temp/ads-trackers-and-bad-pr0n.gz
           => `ads-trackers-and-bad-pr0n.gz'
Resolving www.bluetack.info... 82.165.132.155
Connecting to www.bluetack.info|82.165.132.155|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30,394 (30K) [text/plain]
Server file no newer than local file `ads-trackers-and-bad-pr0n.gz' -- not retrieving.

File bogon.gz last updated 2007-03-09 10:22:57.000000000 +0000
--15:33:08--  http://www.bluetack.co.uk/config/bogon.gz
           => `bogon.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.bluetack.info/temp/bogon.gz [following]
--15:33:09--  http://www.bluetack.info/temp/bogon.gz
           => `bogon.gz'
Resolving www.bluetack.info... 82.165.132.155
Connecting to www.bluetack.info|82.165.132.155|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31,617 (31K) [text/plain]
Server file no newer than local file `bogon.gz' -- not retrieving.

File dshield.gz last updated 2007-03-09 10:11:03.000000000 +0000
--15:33:09--  http://www.bluetack.co.uk/config/dshield.gz
           => `dshield.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.bluetack.nl/bluetack/dshield.gz [following]
--15:33:09--  http://www.bluetack.nl/bluetack/dshield.gz
           => `dshield.gz'
Resolving www.bluetack.nl... 193.227.121.180
Connecting to www.bluetack.nl|193.227.121.180|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,020 (2.0K) [application/x-gzip]
Server file no newer than local file `dshield.gz' -- not retrieving.

File hijacked.gz last updated 2007-03-09 10:11:13.000000000 +0000
--15:33:09--  http://www.bluetack.co.uk/config/hijacked.gz
           => `hijacked.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.bluetack.nl/bluetack/hijacked.gz [following]
--15:33:09--  http://www.bluetack.nl/bluetack/hijacked.gz
           => `hijacked.gz'
Resolving www.bluetack.nl... 193.227.121.180
Connecting to www.bluetack.nl|193.227.121.180|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 712 [application/x-gzip]
Server file no newer than local file `hijacked.gz' -- not retrieving.

--15:33:10--  http://www.bluetack.co.uk/config/level1.gz
           => `level1.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.btack.info/level1.gz [following]
--15:33:10--  http://www.btack.info/level1.gz
           => `level1.gz'
Resolving www.btack.info... 82.165.138.54
Connecting to www.btack.info|82.165.138.54|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
15:33:10 ERROR 403: Forbidden.

stat: cannot stat `level1.gz': No such file or directory
[: 67: 0: unexpected operator
File level2.gz last updated 2007-03-09 10:11:47.000000000 +0000
--15:33:10--  http://www.bluetack.co.uk/config/level2.gz
           => `level2.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://bluetack.info/level2.gz [following]
--15:33:11--  http://bluetack.info/level2.gz
           => `level2.gz'
Resolving bluetack.info... 82.165.132.155
Connecting to bluetack.info|82.165.132.155|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://min.midco.net/jinx/bluetack/level2.gz [following]
--15:33:11--  http://min.midco.net/jinx/bluetack/level2.gz
           => `level2.gz'
Resolving min.midco.net... 24.220.0.103
Connecting to min.midco.net|24.220.0.103|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 588,154 (574K) [text/plain]
Server file no newer than local file `level2.gz' -- not retrieving.

File Microsoft.gz last updated 2007-03-09 10:10:54.000000000 +0000
--15:33:11--  http://www.bluetack.co.uk/config/Microsoft.gz
           => `Microsoft.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.bluetack.nl/bluetack/Microsoft.gz [following]
--15:33:11--  http://www.bluetack.nl/bluetack/Microsoft.gz
           => `Microsoft.gz'
Resolving www.bluetack.nl... 193.227.121.180
Connecting to www.bluetack.nl|193.227.121.180|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11,899 (12K) [application/x-gzip]
Server file no newer than local file `Microsoft.gz' -- not retrieving.

File spider.gz last updated 2007-03-09 10:11:49.000000000 +0000
--15:33:11--  http://www.bluetack.co.uk/config/spider.gz
           => `spider.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.bluetack.nl/bluetack/spider.gz [following]
--15:33:12--  http://www.bluetack.nl/bluetack/spider.gz
           => `spider.gz'
Resolving www.bluetack.nl... 193.227.121.180
Connecting to www.bluetack.nl|193.227.121.180|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,805 (2.7K) [application/x-gzip]
Server file no newer than local file `spider.gz' -- not retrieving.

File spyware.gz last updated 2007-03-09 10:25:35.000000000 +0000
--15:33:12--  http://www.bluetack.co.uk/config/spyware.gz
           => `spyware.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.bluetack.info/temp/spyware.gz [following]
--15:33:12--  http://www.bluetack.info/temp/spyware.gz
           => `spyware.gz'
Resolving www.bluetack.info... 82.165.132.155
Connecting to www.bluetack.info|82.165.132.155|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29,198 (29K) [text/plain]
Server file no newer than local file `spyware.gz' -- not retrieving.

File templist.gz last updated 2007-03-09 10:25:39.000000000 +0000
--15:33:12--  http://www.bluetack.co.uk/config/templist.gz
           => `templist.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.bluetack.info/temp/templist.gz [following]
--15:33:13--  http://www.bluetack.info/temp/templist.gz
           => `templist.gz'
Resolving www.bluetack.info... 82.165.132.155
Connecting to www.bluetack.info|82.165.132.155|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6,616 (6.5K) [text/plain]
Server file no newer than local file `templist.gz' -- not retrieving.

gunzip: level1.gz: No such file or directory

```

It seems to find the files on the bluetak server ok, and it even says that they shouldn't be updated because the local ones are new enough. However, there is nothing in the '/etc/moblock/guarding.p2p' file :<

Thanks,
Ben

---

### Post by pelle.k on 2007-03-11
I refer to this post [http://ubuntuforums.org/showpost.php?p=2066415&postcount=388](http://ubuntuforums.org/showpost.php?p=2066415&postcount=388) . I suppose i'll have to update my FAQ, since it seems the automatic updater is causing more bad than good for the most part...

---

### Post by mario_pl on 2007-03-11
Because one file (level1.gz) hasn't been downloaded properly, /etc/cron.daily/moblock-nfq script was finished without "mv merged.p2b.p2p $PG_LIST" command.

My solution is to create dummy level1.gz file and put it into /var/spool/moblock/ directory.
Then execute:
sudo sh /etc/cron.daily/moblock-nfq

Regards, Mario

---

### Post by konsole on 2007-03-12
> **pelle.k said:**
> I refer to this post [http://ubuntuforums.org/showpost.php?p=2066415&postcount=388](http://ubuntuforums.org/showpost.php?p=2066415&postcount=388) . I suppose i'll have to update my FAQ, since it seems the automatic updater is causing more bad than good for the most part...

FWIW I run it as a **weekly** cron job and have **never** had a problem. (daily is way overkill anyway IMO)

---

### Post by zivagolee on 2007-03-12
Same here.. I'm running it daily and have no issues..

---

### Post by Benjamin.Britton on 2007-03-12
Wahey, I did the dummy file trick 
```
 touch /var/spool/moblock/level1.gz
sh /etc/cron.daily/moblock-nfq

```
Then since that worked, I went and downloaded level1, and then used: 
```

cat ~/downloads/level1.txt > /etc/moblock/guarding.p2p
/etc/init.d/moblock-nfq restart 
```

That seems to work, how do I fix the cron.daily job (preferably move it to a weekly run too?)

Cheers!
Ben

---

### Post by konsole on 2007-03-15
> **Benjamin.Britton said:**
> Wahey, I did the dummy file trick 
```
 touch /var/spool/moblock/level1.gz
sh /etc/cron.daily/moblock-nfq

```
Then since that worked, I went and downloaded level1, and then used: 
```

cat ~/downloads/level1.txt > /etc/moblock/guarding.p2p
/etc/init.d/moblock-nfq restart 
```

That seems to work, how do I fix the cron.daily job (preferably move it to a weekly run too?)

Cheers!
Ben

This is what I did (on dapper server)

```
 sudo cp -p /etc/cron.daily/moblock-nfq /etc/cron.weekly
 sudo chmod -x /etc/cron.daily/moblock-nfq
```

HTH.

---

### Post by Michaeldaley on 2007-03-18
Did the guys at moblock update the blocklist settings?  I'm blocking close to 200,000 by default and all the nipfilter stuff in the cron file is gone.

---

### Post by jre on 2007-03-19
> **Michaeldaley said:**
> Did the guys at moblock update the blocklist settings?  I'm blocking close to 200,000 by default and all the nipfilter stuff in the cron file is gone.

So you have this line:
```
BLOCKLISTS="ads-trackers-and-bad-pr0n bogon dshield hijacked level1 level2 Microsoft spider spyware templist"
```
Indeed this results in nearly 200.000 blocked ranges, which AFAIK is absolutely correct (Note that these are ranges not IPs.)

moblock-deb.sourceforge.net had it´s last update in december. There the problematic nipfilter-stuff was removed. (The Howto on page one doesn´t really reflect this yet. Note: this problem was known here for months. When I read about it I could write a patch in no time for the maintainer of moblock-deb.sourceforge.net who then updated the packages. So please, if you notice serious problems then tell them to upstream.)
Since then neither at moblock-deb.sourceforge.net nor at moblock.berlios.de any changes were done.
But the provider of the blocklists, bluetack.co.uk has some bandwidth problems which may result in problems with downloading the level1-list. But don´t worry, if you succeeded to download the level1-list once you will always have this list´s protection (just not totally up-to-date).

Of course you can still follow pelle´s recommendation and turn off the daily updating.

jre

---

### Post by raffytaffy on 2007-03-29
not sure if its working right.

here is some output.

raf@Equinox:~$ tail /var/log/moblock.log
Skipping useless range: p2p fake files
Skipping useless range: p2p fake files
Skipping useless range: Possible Hack Hijack
Short guarding.p2p line p2p Corrupt Data Senders:80.143.142.68 -80.143.142.68, skipping it...
Skipping useless range: p2p fake file spammer
Short guarding.p2p line p2p Corrupt Data Senders:88.73.227.5 -88.73.227.5, skipping it...
Ranges loaded: 197656
Merged ranges: 217
Skipped useless ranges: 6588
error during nfq_unbind_pf()

raf@Equinox:~$ pidof moblock
raf@Equinox:~$

---

### Post by jre on 2007-03-29
> **raffytaffy said:**
> Ranges loaded: 197656
Merged ranges: 217
Skipped useless ranges: 6588

so the IP-ranges were loaded correctly.

> **raffytaffy said:**
> error during nfq_unbind_pf()

raf@Equinox:~$ pidof moblock
raf@Equinox:~$

Hmm, here you have a serious problem.  I think moblock crashed because there were problems with iptables/netfilter!?
What distro are you using? Which kernel-version and which moblock-version?

---

### Post by raffytaffy on 2007-03-29
> **jre said:**
> so the IP-ranges were loaded correctly.



Hmm, here you have a serious problem.  I think moblock crashed because there were problems with iptables/netfilter!?
What distro are you using? Which kernel-version and which moblock-version?

ubuntu edgy -6.10 
kernel 2.6.20.4 - enabled netfilter support with 

NETFILTER_XT_TARGET_NFQUEUE
-given nfqueue

my firewall worksproper with firestart.
tried to shut down firestart as some posts mentioned above. and reloaded / restart moblock. same problem

---

### Post by jre on 2007-03-29
> **raffytaffy said:**
> ubuntu edgy -6.10 
Did you install the netfilter libs that pelle´s got in his first post of this thread? I really hope this is the solution because I can´t see any other problems.

> **raffytaffy said:**
> my firewall worksproper with firestart.
tried to shut down firestart as some posts mentioned above. and reloaded / restart moblock. same problem
So indeed this seems not to be the problem right now. Just for future reference: You really have to be careful when using firewalls and moblock together. Just ´reload´ing moblock won´t help you, because you need the correct iptables-rules inserted. And those will only be inserted on ´(re-)start´, not on ´reload´. Check your ´iptables -L´ output to make sure that traffic with destiny moblock is directed to a rule QUEUE.

greets
jre

---

### Post by raffytaffy on 2007-03-29
i followed the directions tfrom the first post yes...including those 2 netfilter debs.
i really dont know why its not working. coud TOR and Privoxy somehow interfeere with it?

---

### Post by voodew on 2007-03-30
I'm getting some weird results. I just re-installed Ubuntu today, and tried installed Moblock. I had success with my previous installation of Ubuntu, but not this time. Basically, every command I type in says nothing is being blocked and Modblock isn't running. I pinged [www.riaa.com](www.riaa.com) and I have full loss and it's being reported that the IP was filtered. Even when I manually start or stop Moblock, I get this result.
Synaptic is telling me that version 0.8-14 is installed. Was something changed, or am I running a firewall that I'm not aware of?

---

### Post by jre on 2007-03-31
> **raffytaffy said:**
> i followed the directions tfrom the first post yes...including those 2 netfilter debs.
i really dont know why its not working. coud TOR and Privoxy somehow interfeere with it?
Hmm, as long as they don´t insert their own iptables rules I don´t see any reason. But still then, the error message says something about the kernel module, not the iptables.

You are compiling your own kernel? Have a look at [this thread at the phoenixlabs forums.]("http://forums.phoenixlabs.org/t13098-ipt-missing-from-26191.html")

> **voodew said:**
> I'm getting some weird results. I just re-installed Ubuntu today, and tried installed Moblock. I had success with my previous installation of Ubuntu, but not this time. Basically, every command I type in says nothing is being blocked and Modblock isn't running. I pinged [www.riaa.com](www.riaa.com) and I have full loss and it's being reported that the IP was filtered. Even when I manually start or stop Moblock, I get this result.
Synaptic is telling me that version 0.8-14 is installed. Was something changed, or am I running a firewall that I'm not aware of?
When and where does it say something is being blocked/filtered? You have to be more precise about that; just now I don´t understand your problem. Is it blocking too much or nothing???
moblock only "communicates" with you in "/var/log/moblock.log". So if you find your blocked IPs there then it was moblock.

Check (or post it here) your output of ´iptables -L´ to know if there´s any other firewall on your system or moblock is badly configured.

The difference between 0.8-13 and 0.8-14 is only that -13 had a bug in the cron.daily-script which resulted in most IPs not being filtered (I think 2000 ranges instead of nearly 200.000). So maybe moblock is just working as it should now.

jre

---

### Post by raffytaffy on 2007-03-31
a quick update..i installedmoblock-ipq instead...and get this

raf@Equinox:~$ pidof moblock
8439
picked an ip from list and did

raf@Equinox:~$ ping -c1 217.154.41.144
PING 217.154.41.144 (217.154.41.144) 56(84) bytes of data.

--- 217.154.41.144 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms


raf@Equinox:~$ tail /var/log/moblock.log
Skipping useless range: p2p fake files
Skipping useless range: p2p fake files
Skipping useless range: Possible Hack Hijack
Short guarding.p2p line p2p Corrupt Data Senders:80.143.142.68 -80.143.142.68, skipping it...
Skipping useless range: p2p fake file spammer
Short guarding.p2p line p2p Corrupt Data Senders:88.73.227.5 -88.73.227.5, skipping it...
Ranges loaded: 193629
Merged ranges: 197
Skipped useless ranges: 6780
Blocked OUT: ADSL: Roadshow Promotions,hits: 1,DST: 217.154.41.144


by george i think hes got it!

some more funzies

raf@Equinox:~$ tail /var/log/moblock.log
Blocked OUT: Gilat Satcom,hits: 21,DST: 62.56.243.233
Blocked OUT: Gilat Satcom,hits: 22,DST: 62.56.243.233
Blocked OUT: Gilat Satcom,hits: 23,DST: 62.56.243.233
Blocked OUT: Gilat Satcom,hits: 24,DST: 62.56.243.233
Blocked IN: p2p Corrupt Data Senders,hits: 1,SRC: 82.139.15.231
Blocked OUT: Microsoft Corp,hits: 29,DST: 65.54.239.20
Blocked OUT: Microsoft Corp,hits: 30,DST: 65.54.239.20
Blocked OUT: Microsoft Corp,hits: 31,DST: 65.54.239.20
Blocked OUT: Microsoft Corp,hits: 32,DST: 65.54.239.20
Blocked OUT: Microsoft Corp,hits: 33,DST: 65.54.239.20

---

### Post by voodew on 2007-04-02
> **jre said:**
> Hmm, as long as they don´t insert their own iptables rules I don´t see any reason. But still then, the error message says something about the kernel module, not the iptables.

You are compiling your own kernel? Have a look at [this thread at the phoenixlabs forums.]("http://forums.phoenixlabs.org/t13098-ipt-missing-from-26191.html")


When and where does it say something is being blocked/filtered? You have to be more precise about that; just now I don´t understand your problem. Is it blocking too much or nothing???
moblock only "communicates" with you in "/var/log/moblock.log". So if you find your blocked IPs there then it was moblock.

Check (or post it here) your output of ´iptables -L´ to know if there´s any other firewall on your system or moblock is badly configured.

The difference between 0.8-13 and 0.8-14 is only that -13 had a bug in the cron.daily-script which resulted in most IPs not being filtered (I think 2000 ranges instead of nearly 200.000). So maybe moblock is just working as it should now.

jre

When I go to terminal and type:
~$ **ping [www.riaa.com](www.riaa.com)**
PING [www.riaa.com](www.riaa.com) (63.147.176.10) 56(84) bytes of data.
From 72.166.68.134 icmp_seq=2 Packet filtered
From 72.166.68.134 icmp_seq=5 Packet filtered

--- [www.riaa.com](www.riaa.com) ping statistics ---
6 packets transmitted, 0 received, +2 errors, 100% packet loss, time 5009ms

If I type:
**ping [www.yahoo.com](www.yahoo.com)**
PING [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net) (209.131.36.158) 56(84) bytes of data.
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=1 ttl=52 time=33.6 ms
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=2 ttl=51 time=32.8 ms
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=3 ttl=50 time=34.1 ms
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=4 ttl=51 time=34.2 ms

--- [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 32.850/33.745/34.296/0.601 ms 

**iptables -L**
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
MOBLOCK_IN  all  --  anywhere             anywhere            state NEW 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
MOBLOCK_FW  all  --  anywhere             anywhere            state NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
MOBLOCK_OUT  all  --  anywhere             anywhere            state NEW 

Chain MOBLOCK_FW (1 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_IN (1 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_OUT (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
NFQUEUE    all  --  anywhere    


You did bring up a good point about the Kernel, I'm not compiling it myself and I'm not sure what source I received the update from. I'll try a backup Kernel and see if my situation improves.

---

### Post by voodew on 2007-04-02
> **voodew said:**
> When I go to terminal and type:
~$ **ping [www.riaa.com](www.riaa.com)**
PING [www.riaa.com](www.riaa.com) (63.147.176.10) 56(84) bytes of data.
From 72.166.68.134 icmp_seq=2 Packet filtered
From 72.166.68.134 icmp_seq=5 Packet filtered

--- [www.riaa.com](www.riaa.com) ping statistics ---
6 packets transmitted, 0 received, +2 errors, 100% packet loss, time 5009ms

If I type:
**ping [www.yahoo.com](www.yahoo.com)**
PING [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net) (209.131.36.158) 56(84) bytes of data.
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=1 ttl=52 time=33.6 ms
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=2 ttl=51 time=32.8 ms
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=3 ttl=50 time=34.1 ms
64 bytes from f1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.158): icmp_seq=4 ttl=51 time=34.2 ms

--- [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 32.850/33.745/34.296/0.601 ms 

**iptables -L**
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
MOBLOCK_IN  all  --  anywhere             anywhere            state NEW 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
MOBLOCK_FW  all  --  anywhere             anywhere            state NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
MOBLOCK_OUT  all  --  anywhere             anywhere            state NEW 

Chain MOBLOCK_FW (1 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_IN (1 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_OUT (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
NFQUEUE    all  --  anywhere    


You did bring up a good point about the Kernel, I'm not compiling it myself and I'm not sure what source I received the update from. I'll try a backup Kernel and see if my situation improves.

I tried one of my backup kernels, and still no dice. Though, I got it to work.
I was having the same output as Giggity on page 22:
I had the same problem Giggity had on page 22,

rob@rob-desktop:~$ tail -f /var/log/moblock.log
Ranges loaded: 0
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'
Got SIGTERM! Dumping stats and exiting.
Ranges loaded: 0
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'
Got SIGTERM! Dumping stats and exiting.

This thread is getting pretty long. Anyway, out of sheer desperation, I typed apt-get install libnet* (*I think*) and everything is working now. I'm thinking that a dependency is missing.

---

### Post by jre on 2007-04-02
shouldn´t go to eat while posting ;-)

---

### Post by voodew on 2007-04-02
I looked up which package I had to install and it was knetfilter. I thought it was libnet*, but I looked at my installation history: 

find /var/lib/dpkg/info/ -name '*.list' -printf '%c\t%f\n'

and found that I only installed knetfilter last night. Is knetfilter supposed to be part of the dependency list, or did I just get lucky?

---

### Post by jre on 2007-04-03
> **voodew said:**
> Is knetfilter supposed to be part of the dependency list, or did I just get lucky?
Just lucky. I don´t have it installed. Unless I have a equivalent under gnome (and I´ve never heard about wrong dependenys of the moblock-packages)  then you must have done anything else so that it is working now.

---

### Post by ratai on 2007-04-03
hi,
what firewall will we use for moblock if firehol is broken in Feisty 
founf in [[COLOR="Red"]Nabble[/COLOR]]("http://www.nabble.com/Upgrade-to-Feisty-breaks-FireHOL-or-possibly-iptables-t3413680.html")
listed as bug #98981.
> even with its original scripts with no modifications.  The problem is
> that it seems FireHOL is imported directly from Debian rather than being
> maintained.

ratai

---

### Post by voodew on 2007-04-04
> **jre said:**
> Just lucky. I don´t have it installed. Unless I have a equivalent under gnome (and I´ve never heard about wrong dependenys of the moblock-packages)  then you must have done anything else so that it is working now.

I started with a fresh install of Ubuntu and updated a few packages unrelated to networking. Could you check /var/log/dpkg.log.1 and make sure that it's not installed. If it's not, I'm willing to reformat and reinstall Ubuntu just to make sure that knetfilter was indeed my problem. Just seems weird that it's not required and everything started working once I installed that package. Googling the terms knetfilter and moblock suggests that the projects are related. Hmmm, I suppose this will be a learning a experience for me.

---

### Post by jre on 2007-04-04
> **voodew said:**
> I started with a fresh install of Ubuntu and updated a few packages unrelated to networking. Could you check /var/log/dpkg.log.1 and make sure that it's not installed. If it's not, I'm willing to reformat and reinstall Ubuntu just to make sure that knetfilter was indeed my problem. Just seems weird that it's not required and everything started working once I installed that package. Googling the terms knetfilter and moblock suggests that the projects are related. Hmmm, I suppose this will be a learning a experience for me.
It´s definitely not installed here.
But again, I´m still not sure if I understood what your problems are. Is it, that
you can´t ping riaa.com but it´s working with other hosts [so far this would be as we want moblock to work]
but this is happening independently if moblock is running or not [have you made sure that neither the process moblock is running (ps aux|grep moblock) nor the iptables rules are inserted (iptables -L) and vice versa?]
and those blocks never appear in the logfile [tail -f /var/log/moblock; open two terminals: one for ping (or better traceroute) one for "tail -f", make sure that you really use the "-f"]?

´knetfilter´ indeed has to do something with networking, but I never have used it. Those "ping ... icmp_seq=2 Packet filtered" are not the normal behavior of moblock (if even related, I´ve never seen that; it could even be your provider or sth. else blocking the icmp (therefor check it with traceroute)).

---

### Post by voodew on 2007-04-05
> **jre said:**
> It´s definitely not installed here.
But again, I´m still not sure if I understood what your problems are. Is it, that
you can´t ping riaa.com but it´s working with other hosts [so far this would be as we want moblock to work]
but this is happening independently if moblock is running or not [have you made sure that neither the process moblock is running (ps aux|grep moblock) nor the iptables rules are inserted (iptables -L) and vice versa?]
and those blocks never appear in the logfile [tail -f /var/log/moblock; open two terminals: one for ping (or better traceroute) one for "tail -f", make sure that you really use the "-f"]?

´knetfilter´ indeed has to do something with networking, but I never have used it. Those "ping ... icmp_seq=2 Packet filtered" are not the normal behavior of moblock (if even related, I´ve never seen that; it could even be your provider or sth. else blocking the icmp (therefor check it with traceroute)).

My problem was no output. When I typed:

cat /etc/moblock/guarding.p2p | grep ads
nothing outputted.

When I typed:
tail /var/log/moblock.log

I received the same output as previously posted. Basically, nothing was being filtered.

When I typed:
pidof moblock
I, again, received no output.

Today, I just tried the command
apt-get remove knetfilter

and everything is outputting as advertised. I'm getting a blocklist and a pidof. I restarted and everything is still working.

My theory is that a kernel module wasn't active and the knetfilter activated NFQUEUE or some other required module. You're right, knetfilter isn't required. Perhaps I should be more careful as to where I'm receiving my Kernel updates from. I changed my sources.list based on a recommendation from a random website. That's probably where my initial problem stems from.

---

### Post by jre on 2007-04-05
@everybody using the cron.daily script:
[ATM bluetack´s level1.gz list is distributed via the Coblitz system.]("http://www.bluetack.co.uk/forums/index.php?showtopic=16352&view=findpost&p=80423") (At least here) the IPs of the Coblitz server is in the level2 list. Therefore automatic updates for the level1.gz don´t work here. (This is the same problem as with the Coral system being blocked on the edu-list).
Don´t worry, the other lists update just fine and moblock continues to use the old level1-list (as long as it has been downloaded and saved to /var/spool/moblock/ in the past).
Everybody feel free to donate money to bluetack.co.uk so that they can afford to distribute their level1 list with their own server again ;-)

@voodew:
> **voodew said:**
> cat /etc/moblock/guarding.p2p | grep ads
At least this one has nothing to do with kernel modules. Make sure that you really have a file /etc/moblock/guarding.p2p with a size of about 10MB (the level1 list already has 8.5 MB.) Otherwise moblock might be working but not really blocking anything.
> **voodew said:**
> tail /var/log/moblock.log
Use "tail **-f** /var/log/moblock.log" instead so that you can follow changes in the log file in real time.

---

### Post by raffytaffy on 2007-04-07
hey guys, raf again. small problem . moblobk seems to be blocking evolution mail  . hehe

Blocked OUT: Google Inc,hits: 1,DST: 72.14.247.109
Blocked OUT: Google Inc,hits: 2,DST: 72.14.247.109
Blocked OUT: Google Inc,hits: 3,DST: 72.14.247.109
 what can be done about this?

---

### Post by voodew on 2007-04-08
> **raffytaffy said:**
> hey guys, raf again. small problem . moblobk seems to be blocking evolution mail  . hehe

Blocked OUT: Google Inc,hits: 1,DST: 72.14.247.109
Blocked OUT: Google Inc,hits: 2,DST: 72.14.247.109
Blocked OUT: Google Inc,hits: 3,DST: 72.14.247.109
 what can be done about this?

Follow the directions posted in the first post. I think gedit /etc/cron.daily/moblock-nfq and changing line 114 (or somewhere around there) to this:

       grep -v -i "Google Inc" merged.p2b.p2p > merged.p2b.p2p.tmp
and uncomment the next line.
You may have to update the file,
type this:
sudo sh /etc/cron.daily/moblock-nfq

Hope everything works out for you.

---

### Post by bravemosquito on 2007-04-08
> **voodew said:**
> You may have to update the file,
type this:
sudo sh /etc/cron.daily/moblock-nfq

```
root@xxx:~# sh /etc/cron.daily/moblock-nfq
sh: **Can't open** /etc/cron.daily/moblock-nfq
```

:-k

---

### Post by voodew on 2007-04-09
> **bravemosquito said:**
> ```
root@xxx:~# sh /etc/cron.daily/moblock-nfq
sh: **Can't open** /etc/cron.daily/moblock-nfq
```

:-k

That's just weird. Here's my moblock-nfq file in case yours is corrupt.
```

#!/bin/sh
# Update new blocklists and start/stop/restart PeerGuardian
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA
# testdescription
#
echo "moblock: checking for new block lists..."
TESTHOST=www.bluetack.co.uk

wget --timeout=5 --dns-timeout=5 -O -  $TESTHOST  >/dev/null
if [ $? -ne 0 ]; then
       	echo no connection to $TESTHOST, updating later.;
       	exit 0;
fi

#CONFIGURATION
# Make sure PG_SPOOL points to the directory where
# you want to put your downloaded blocklists.
PG_SPOOL=/var/spool/moblock
# Remove the lists you don't want to download and
# use from BLOCKLISTS.
BLOCKLISTS="ads-trackers-and-bad-pr0n bogon dshield hijacked level1 level2 Microsoft spider spyware templist"
BLOCKLISTTXT=""
#PG_CONF=/etc/PG.conf
#PG_LOG=/var/log/PG.log
PG_LIST=/etc/moblock/guarding.p2p
#The URL where the blocklists reside
URL=http://www.bluetack.co.uk/config
#The format of the lists to download
SUFFIX=gz
#The format after unpacking
SUFFIX2=txt

endscript () {
date +"------------ "%F" "%X" "%Z" End PeerGuardian Script"
exit $1
}
date +"------------ "%F" "%X" "%Z" Begin PeerGuardian $1"


	cd "$PG_SPOOL"
	# check if blockfiles were updated:
	UPDATED=""
	for i in $BLOCKLISTS ; do
		TIMESTAMP=0
		if [ -e $i.$SUFFIX ] ; then
		TIMESTAMP=`stat --format=%y $i.$SUFFIX`
		echo "File $i.$SUFFIX last updated $TIMESTAMP"
		TIMESTAMP=`stat --format=%Y $i.$SUFFIX`
		fi
		wget -N $URL/$i.$SUFFIX
		if [ `stat --format=%Y $i.$SUFFIX` -gt $TIMESTAMP ] ; then
		UPDATED=$i
		fi
	done
	for i in $BLOCKLISTTXT ; do
		TIMESTAMP=0
		if [ -e $i.$SUFFIX2 ] ; then
		TIMESTAMP=`stat --format=%y $i.$SUFFIX2`
		echo "File $i.$SUFFIX2 last updated $TIMESTAMP"
		TIMESTAMP=`stat --format=%Y $i.$SUFFIX2`
		fi
		wget -N $URL/$i.$SUFFIX2
		if [ `stat --format=%Y $i.$SUFFIX2` -gt $TIMESTAMP ] ; then
		UPDATED=$i
		fi
	done
	
	
	# if none of the blockfiles were updated:
	#if [ -z $UPDATED ] ; then
	#echo "No blocklists needed updating."
	#endscript 0
	#fi

set -e	
	# if any blockfiles were updated:
	for i in $BLOCKLISTS ; do
	gunzip -c $i.$SUFFIX > $i.$SUFFIX2
	done
	cat *.txt > merged.p2b.p2p
	for i in $BLOCKLISTS ; do
	rm $i.$SUFFIX2
	done
	# uncomment below to unblock Yahoo! Mail and whatever
	# else needs unblocking here. Do this also in the
	# restart section.
	grep -v -i "Google Inc" merged.p2b.p2p > merged.p2b.p2p.tmp
	mv merged.p2b.p2p.tmp merged.p2b.p2p
	mv $PG_LIST $PG_LIST.backup
	mv merged.p2b.p2p $PG_LIST
	/etc/init.d/`basename $0` reload
exit 0

```

Maybe if you pasted that into the moblock-nfq file, you can update once again.

---

### Post by raffytaffy on 2007-04-09
> **voodew said:**
> That's just weird. Here's my moblock-nfq file in case yours is corrupt.
```

#!/bin/sh
# Update new blocklists and start/stop/restart PeerGuardian
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA
# testdescription
#
echo "moblock: checking for new block lists..."
TESTHOST=www.bluetack.co.uk

wget --timeout=5 --dns-timeout=5 -O -  $TESTHOST  >/dev/null
if [ $? -ne 0 ]; then
       	echo no connection to $TESTHOST, updating later.;
       	exit 0;
fi

#CONFIGURATION
# Make sure PG_SPOOL points to the directory where
# you want to put your downloaded blocklists.
PG_SPOOL=/var/spool/moblock
# Remove the lists you don't want to download and
# use from BLOCKLISTS.
BLOCKLISTS="ads-trackers-and-bad-pr0n bogon dshield hijacked level1 level2 Microsoft spider spyware templist"
BLOCKLISTTXT=""
#PG_CONF=/etc/PG.conf
#PG_LOG=/var/log/PG.log
PG_LIST=/etc/moblock/guarding.p2p
#The URL where the blocklists reside
URL=http://www.bluetack.co.uk/config
#The format of the lists to download
SUFFIX=gz
#The format after unpacking
SUFFIX2=txt

endscript () {
date +"------------ "%F" "%X" "%Z" End PeerGuardian Script"
exit $1
}
date +"------------ "%F" "%X" "%Z" Begin PeerGuardian $1"


	cd "$PG_SPOOL"
	# check if blockfiles were updated:
	UPDATED=""
	for i in $BLOCKLISTS ; do
		TIMESTAMP=0
		if [ -e $i.$SUFFIX ] ; then
		TIMESTAMP=`stat --format=%y $i.$SUFFIX`
		echo "File $i.$SUFFIX last updated $TIMESTAMP"
		TIMESTAMP=`stat --format=%Y $i.$SUFFIX`
		fi
		wget -N $URL/$i.$SUFFIX
		if [ `stat --format=%Y $i.$SUFFIX` -gt $TIMESTAMP ] ; then
		UPDATED=$i
		fi
	done
	for i in $BLOCKLISTTXT ; do
		TIMESTAMP=0
		if [ -e $i.$SUFFIX2 ] ; then
		TIMESTAMP=`stat --format=%y $i.$SUFFIX2`
		echo "File $i.$SUFFIX2 last updated $TIMESTAMP"
		TIMESTAMP=`stat --format=%Y $i.$SUFFIX2`
		fi
		wget -N $URL/$i.$SUFFIX2
		if [ `stat --format=%Y $i.$SUFFIX2` -gt $TIMESTAMP ] ; then
		UPDATED=$i
		fi
	done
	
	
	# if none of the blockfiles were updated:
	#if [ -z $UPDATED ] ; then
	#echo "No blocklists needed updating."
	#endscript 0
	#fi

set -e	
	# if any blockfiles were updated:
	for i in $BLOCKLISTS ; do
	gunzip -c $i.$SUFFIX > $i.$SUFFIX2
	done
	cat *.txt > merged.p2b.p2p
	for i in $BLOCKLISTS ; do
	rm $i.$SUFFIX2
	done
	# uncomment below to unblock Yahoo! Mail and whatever
	# else needs unblocking here. Do this also in the
	# restart section.
	grep -v -i "Google Inc" merged.p2b.p2p > merged.p2b.p2p.tmp
	mv merged.p2b.p2p.tmp merged.p2b.p2p
	mv $PG_LIST $PG_LIST.backup
	mv merged.p2b.p2p $PG_LIST
	/etc/init.d/`basename $0` reload
exit 0

```

Maybe if you pasted that into the moblock-nfq file, you can update once again.

maybe hes using moblock-ipq like me hmm

---

### Post by bravemosquito on 2007-04-09
No, but I found that this file is missing :shock: I never deleted this file

---

### Post by voodew on 2007-04-10
> **bravemosquito said:**
> No, but I found that this file is missing :shock: I never deleted this file

Did you get it working?

---

### Post by bravemosquito on 2007-04-10
> **voodew said:**
> Did you get it working?

Yes. I think so... Just removed moblock and installed it again. During these actions I feel some MS Windows-like presence behind me :mrgreen:

---

### Post by chinaski on 2007-04-15
solution was just two post ago, request deleted sorry

---

### Post by chinaski on 2007-04-15
no way, gmail in evolution is not working for me

> **justin said:**
> Moblock seems to block Gmail (pop.gmail.com, and possibly smtp.gmail.com)

How can I stop it from blocking Gmail?

> **pelle.k said:**
> 
<snip>
@justin
You'll have to watch the logfile, and filter those ranges out, during an update of the blocklists. It's described in my howto.
I think I am really dumb because I cannot make gmail work

what I did is to open /etc/cron.daily/moblock-nfq and add

```
  grep -v -i "mail.google.com" merged.p2b.p2p | grep -v -i "mail.google.com" | grep -v "mail.google.com" > merged.p2b.p2p.tmp
        mv merged.p2b.p2p.tmp merged.p2b.p2p
```but this is not working... what is the right way?

I also followed [this suggestion]("http://ubuntuforums.org/showpost.php?p=2419607&postcount=452") but it's not working either

is there a simple and clear sintax that someone can explain to a dumb like me? :D

---

### Post by chinaski on 2007-04-15
ok, Moblock blocks also messenger protocol

I have read all thread and tried to follow all suggestions I found in order to whitelist mail and messenger but it seems I am really stupid or this is too difficult for me

if anyone has a clear solution on how to make gmail and messenger protocol work with Moblock on is welcome :D

---

### Post by jre on 2007-04-16
@chinaski: The grep command filters specific lines from your blocklist on rebuilding, so

- you have to make sure that you write something which corresponds to the line in /etc/moblock/guarding.p2p which blocks your site (try it with just "google" not "mail.google.com"). Try ´man grep´ to understand what you are doing.

- you have to make sure that the blocklist is really rebuilt, only editing the cron.daily file will not work. So either wait a day or remove one little blocklist (not level1!!) from /var/spool/moblock/ and do a ´/etc/cron.daily/moblock-nfq´ as root afterwards.

Another solution is to add the ports of the protocols you want to whitelist to /etc/moblock/MoBlock-nfq.sh and do a ´/etc/init.d/moblock-nfq restart´ as root afterwards.

---

### Post by chinaski on 2007-04-16
> **jre said:**
> 
<snip>
Another solution is to add the ports of the protocols you want to whitelist to /etc/moblock/MoBlock-nfq.sh and do a ´/etc/init.d/moblock-nfq restart´ as root afterwards.
once again i must thank you jre ;)

I'll try this option tonight :)

cheers

---

### Post by voodew on 2007-04-18
> **chinaski said:**
> no way, gmail in evolution is not working for me




I think I am really dumb because I cannot make gmail work

what I did is to open /etc/cron.daily/moblock-nfq and add

```
  grep -v -i "mail.google.com" merged.p2b.p2p | grep -v -i "mail.google.com" | grep -v "mail.google.com" > merged.p2b.p2p.tmp
        mv merged.p2b.p2p.tmp merged.p2b.p2p
```but this is not working... what is the right way?

I also followed [this suggestion]("http://ubuntuforums.org/showpost.php?p=2419607&postcount=452") but it's not working either

is there a simple and clear sintax that someone can explain to a dumb like me? :D

I use GMAIL and it works for me, though my syntax is different. Take a look at post #455, that's my Moblock-NFQ file if you want to make sure everything is the same. The syntax I used was:

```

grep -v -i "Google Inc" merged.p2b.p2p > merged.p2b.p2p.tmp
	mv merged.p2b.p2p.tmp merged.p2b.p2p
```

---

### Post by chinaski on 2007-04-18
hello,

I've tried that syntax too, but it's not working

I'm waiting tomorrow for Feisty stable to make a fresh install of Ubuntu so I am not making any change now, but I'll be back on this subject soon

thank you ;)

---

### Post by voodew on 2007-04-18
> **chinaski said:**
> hello,

I've tried that syntax too, but it's not working

I'm waiting tomorrow for Feisty stable to make a fresh install of Ubuntu so I am not making any change now, but I'll be back on this subject soon

thank you ;)

Did you run

```
sudo sh /etc/cron.daily/moblock-nfq
```

after editing the file? I suppose it doesn't matter since Moblock is supposed to automatically update after a restart. Someone suggest whitelisting the ports. If you want to try that method, you need to whitelist the SSL port (995) and the STARTTLS port (465 or 587). I'm not sure if the protocol name is required or if you're able to just put the numbers in.

In any case, I think you're going to run into the same problem with Feisty since Google Inc is blacklisted.

---

### Post by Leebo on 2007-04-19
Lo all,

I've created a very crude frontend to Moblock using Gambas...was wondering if any would like to try it out.

Leebo

---

### Post by jre on 2007-04-19
@voodew/chinaski: You´re right that it is necessary to do a `sudo sh /etc/cron.daily/moblock-nfq`, but don´t forget to first stop moblock (otherwise I think there would be two instances of moblock running. If in doubt, simply reboot, lol)

@Leebo: What are the features?

---

### Post by voodew on 2007-04-19
> **jre said:**
> @voodew/chinaski: You´re right that it is necessary to do a `sudo sh /etc/cron.daily/moblock-nfq`, but don´t forget to first stop moblock (otherwise I think there would be two instances of moblock running. If in doubt, simply reboot, lol)

@Leebo: What are the features?

I don't think stopping moblock is required because I never did that... though, stopping and applying the command certainly won't hurt anything. Especially after a reboot:)

---

### Post by jre on 2007-04-19
@voodew: you´re right, I was a bit sleepy when i wrote that
It´s only necessary to first stop and then start moblock again when you change the port-whitelisting in /etc/moblock/MoBlock-nfq.sh. (There the script checks if moblock is already running and simply quits if moblock is already running --> no ports whitelisted)

---

### Post by Leebo on 2007-04-19
Frontend

It's  a GUI that allows the user to start/stop/restart Moblock as well as update the blocklists (not updating level1 currently due to bluetack issues), displays the update info (when the last time all of the blocklists where updated), and displays the last 10 lines in the log for blocklists (still looking at improving this to actively displaying incoming block traffic) instead of having to click a button.

Been a while since a tried out my coding legs, was just seeing what i remembered :)

I just like having a launcher i can control everything from without console (i'm pretty lazy).

Eventually would like to minimize to systray instead of taskbar, and like i said improve the blocklist display as well.This is my first venture with Gambas so just seeing how it goes.

I'll post a screenshot when i can.

Leebo

---

### Post by jre on 2007-04-19
@Leebo: Your frontend; sounds really good (of course I´m sure I would have tons of feature requests once I tried it ;-) ). But starting/stopping and updating and seeing if the update worked are really the main features.

So, I´d suggest you post your code at the Linux forum at phoenixlabs.org (home of the original windows PeerGuardian, but the developer of moblock regularly steps by since there´s the plan to make moblock the official PeerGuardian Linux). I´m pretty sure "some" people would be interested in your work. (Personally I prefer init + console, but I know that I´m not mainstream).

Greets!
jre

---

### Post by sloter on 2007-04-20
Hello,

> @Leebo I've created a very crude frontend to Moblock using Gambas...was wondering if any would like to try it out.

Sounds great, I would like to see that.

sloter

---

### Post by voodew on 2007-04-21
I just installed Fiesty and have Moblock up and running. The instructions for installation are the same as Edgy's from the OP, however, you don't need to install the netfilter libs because Fiesty aptitude installs them correctly during Moblock installation... YAY!!!

---

### Post by Mechanical on 2007-04-21
> **voodew said:**
> I just installed Fiesty and have Moblock up and running. The instructions for installation are the same as Edgy's from the OP, however, you don't need to install the netfilter libs because Fiesty aptitude installs them correctly during Moblock installation... YAY!!!

Same here!  I was very happy to find it working perfectly.

---

### Post by sloter on 2007-04-21
Me too, I installed moblocknfq (0.8-14) with apt on the new dist-upgrade Feisty and everythink worked fined, the dependencies instlled by themselves! Very great!
sloter

---

### Post by jamesford on 2007-04-22
im having bad problems on a fresh feisty install, im using the amd64 version. ihad made debs for edgy that worked jsut fine but on feisty its a different story with broken dependencies and stuff

i wish someone more competent than me could make 64 bit debs

---

### Post by chinaski on 2007-04-22
many thanks to** jre** and **voodew** for their support to solve my problem

Moblock was blocking gmail mail accounts and Gaim MSN protocol

if you (read: anyone) have same issues just read previous posts (pages 46-47) and you'll solve it

thanks also to **jamesford** for the [solution for Gaim]("http://ubuntuforums.org/showthread.php?p=1146357&highlight=gaim#post1146357")

cheers! ;)

---

### Post by dalziel_86 on 2007-04-22
I suspect Moblock is causing me problems with youtube, but I can't be sure. Is there a way I can check the blocklist to see what's on it?

Also, my Ubuntu machine acts as a wireless access point for my laptop, bridging from a wireless card to ethernet. I'd prefer moblock didn't filter stuff going to and from the wireless, since I don't run P2P on the laptop, and it has its own firewall, etc. Is there a way to set Moblock not to affect bridged traffic?

---

### Post by jre on 2007-04-23
@dalziel_82: The blocklist is in /etc/moblock/guarding.p2p. But you can follow the logfile live with `tail -f /var/log/moblock.log`, then you can see if something is blocked while you´re on youtube.

I´m not sure about the laptop thing. But removing all "FORWARD" stuff (this relates to iptables FORWARD chain for packets being routed through the box) from /etc/moblock/MoBlock-nfq.sh might do it. (First stop moblock, then edit the file, then start it again. Check your results with `iptables -L`)

jre

---

### Post by sinpalabras on 2007-04-24
hi i upgrade to feisty and moblock is not working anymore : i'm on amd64 feisty. It worked fine on edgy,  but now i  run all the comands and nothing happens ( good or bad):

juan@ubuntubox:~$ pidof moblock
juan@ubuntubox:~$ 

juan@ubuntubox:~$ tail /var/log/moblock.log
Skipping useless range: ns1/ns2.playercodec.net
Skipping useless range: www.buhartes.info|BT|Hijackers
Skipping useless range: adv549|CWS|BT|Hijackers
Skipping useless range: Pluginaccess.com/Dialeraccess.com[CWS]
Skipping useless range: Parcproductions.com
Skipping useless range: Fastsearch[Spy]
Skipping useless range: 80ke.com
Ranges loaded: 196346
Merged ranges: 199
Skipped useless ranges: 6358
juan@ubuntubox:~$ 

juan@ubuntubox:~$ sudo /etc/init.d/moblock-nfq restart
Password:
 * Restarting moblock moblock                                            [ OK ] 
juan@ubuntubox:~$ pidof modblock
juan@ubuntubox:~$ 

i'm missing somethig, if you need more info, just tell me what to do, and i'll post it.
thanks

---

### Post by voodew on 2007-04-24
That's weird, I tried pidof moblock and got no output and checked to see if everything is working fine, and it is. I tried pidof a couple minutes later, and I got 5503.
Type
```
ps axu
```
And see if you can locate a moblock process ID that way.

> **sinpalabras said:**
> hi i upgrade to feisty and moblock is not working anymore : i'm on amd64 feisty. It worked fine on edgy,  but now i  run all the comands and nothing happens ( good or bad):

juan@ubuntubox:~$ pidof moblock
juan@ubuntubox:~$ 

juan@ubuntubox:~$ tail /var/log/moblock.log
Skipping useless range: ns1/ns2.playercodec.net
Skipping useless range: www.buhartes.info|BT|Hijackers
Skipping useless range: adv549|CWS|BT|Hijackers
Skipping useless range: Pluginaccess.com/Dialeraccess.com[CWS]
Skipping useless range: Parcproductions.com
Skipping useless range: Fastsearch[Spy]
Skipping useless range: 80ke.com
Ranges loaded: 196346
Merged ranges: 199
Skipped useless ranges: 6358
juan@ubuntubox:~$ 

juan@ubuntubox:~$ sudo /etc/init.d/moblock-nfq restart
Password:
 * Restarting moblock moblock                                            [ OK ] 
juan@ubuntubox:~$ pidof modblock
juan@ubuntubox:~$ 

i'm missing somethig, if you need more info, just tell me what to do, and i'll post it.
thanks

---

### Post by sinpalabras on 2007-04-24
juan@ubuntubox:~$ ps axu
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.2   5064  1960 ?        Ss   18:53   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    18:53   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   18:53   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    18:53   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   18:53   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   18:53   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   18:53   0:00 [kthread]
root        29  0.0  0.0      0     0 ?        S<   18:53   0:00 [kblockd/0]
root        30  0.0  0.0      0     0 ?        S<   18:53   0:00 [kacpid]
root        31  0.0  0.0      0     0 ?        S<   18:53   0:00 [kacpi_notify]
root       128  0.0  0.0      0     0 ?        S<   18:53   0:00 [kseriod]
root       158  0.0  0.0      0     0 ?        S    18:53   0:00 [pdflush]
root       159  0.0  0.0      0     0 ?        S    18:53   0:00 [pdflush]
root       160  0.0  0.0      0     0 ?        S<   18:53   0:00 [kswapd0]
root       161  0.0  0.0      0     0 ?        S<   18:53   0:00 [aio/0]
root      1998  0.0  0.0      0     0 ?        S<   18:53   0:00 [ata/0]
root      1999  0.0  0.0      0     0 ?        S<   18:53   0:00 [ata_aux]
root      2002  0.0  0.0      0     0 ?        S<   18:53   0:00 [scsi_eh_0]
root      2003  0.0  0.0      0     0 ?        S<   18:53   0:00 [scsi_eh_1]
root      2005  0.0  0.0      0     0 ?        S<   18:53   0:00 [ksuspend_usbd]
root      2006  0.0  0.0      0     0 ?        S<   18:53   0:00 [khubd]
root      2250  0.0  0.0      0     0 ?        S<   18:53   0:00 [kjournald]
root      2454  0.0  0.2  19900  1756 ?        S<s  18:53   0:00 /sbin/udevd --d
root      3405  0.0  0.0      0     0 ?        S<   18:53   0:00 [kpsmoused]
root      3478  0.0  0.0      0     0 ?        S<   18:53   0:00 [kgameportd]
root      3527  0.0  0.0      0     0 ?        S<   18:53   0:00 [scsi_eh_2]
root      3528  0.0  0.0      0     0 ?        S<   18:53   0:00 [usb-storage]
root      3892  0.0  0.0      0     0 ?        S<   18:53   0:00 [kjournald]
root      4207  0.0  0.0   3780   560 tty4     Ss+  18:53   0:00 /sbin/getty 384
root      4208  0.0  0.0   3780   564 tty5     Ss+  18:53   0:00 /sbin/getty 384
root      4211  0.0  0.0   3784   564 tty2     Ss+  18:53   0:00 /sbin/getty 384
root      4213  0.0  0.0   3784   564 tty3     Ss+  18:53   0:00 /sbin/getty 384
root      4214  0.0  0.0   3780   560 tty1     Ss+  18:53   0:00 /sbin/getty 384
root      4215  0.0  0.0   3784   564 tty6     Ss+  18:53   0:00 /sbin/getty 384
root      4453  0.0  0.1  12852  1488 ?        Ss   18:53   0:00 /usr/sbin/acpid
root      4555  0.0  0.0   5888   672 ?        Ss   18:53   0:00 /sbin/syslogd
root      4611  0.0  0.0   8036   572 ?        Ss   18:53   0:00 /bin/dd bs 1 if
klog      4613  0.0  0.2   5100  1832 ?        Ss   18:53   0:00 /sbin/klogd -P
103       4634  0.0  0.1  23508  1124 ?        Ss   18:53   0:00 /usr/bin/dbus-d
106       4650  0.4  1.2  36340  9296 ?        Ss   18:53   0:02 /usr/sbin/hald
root      4651  0.0  0.1  15380  1112 ?        S    18:53   0:00 hald-runner
106       4657  0.0  0.1  16548   952 ?        S    18:53   0:00 hald-addon-acpi
106       4665  0.0  0.1  16552   960 ?        S    18:54   0:00 hald-addon-keyb
106       4674  0.0  0.1  16548   956 ?        S    18:54   0:00 hald-addon-keyb
106       4677  0.0  0.1  16548   952 ?        S    18:54   0:00 hald-addon-keyb
106       4686  0.0  0.1  16548  1008 ?        S    18:54   0:00 hald-addon-stor
106       4694  0.0  0.1  16544   972 ?        S    18:54   0:00 hald-addon-stor
root      4708  0.0  0.0   6164   724 ?        Ss   18:54   0:00 /usr/sbin/dhcdb
root      4723  0.0  0.2  37524  1980 ?        Ss   18:54   0:00 /usr/sbin/Netwo
avahi     4741  0.0  0.1  27400  1408 ?        Ss   18:54   0:00 avahi-daemon: r
avahi     4742  0.0  0.0  27400   492 ?        Ss   18:54   0:00 avahi-daemon: c
root      4755  0.0  0.1  21684  1212 ?        Ss   18:54   0:00 /usr/sbin/Netwo
root      4768  0.0  0.1  15368   864 ?        Ss   18:54   0:00 /usr/bin/system
root      4769  0.0  0.1  23376  1296 ?        S    18:54   0:00 dbus-daemon --s
root      4801  0.0  0.2  94540  1632 ?        Ss   18:54   0:00 /usr/sbin/gdm
root      4804  0.0  0.3 107200  2628 ?        S    18:54   0:00 /usr/sbin/gdm
root      4807  1.0  4.7  99256 36448 tty7     SLs+ 18:54   0:05 /usr/X11R6/bin/
cupsys    4851  0.0  0.2  52536  2144 ?        Ss   18:54   0:00 /usr/sbin/cupsd
root      4875  0.0  0.1  41204   948 ?        Ss   18:54   0:00 /usr/sbin/hpiod
hplip     4878  0.0  0.9  91208  7352 ?        S    18:54   0:00 python /usr/sbi
root      4916  0.0  0.0  12756   520 ?        S    18:54   0:00 ptal-mlcd mlc:u
root      4919  0.0  0.0  16460   544 ?        S    18:54   0:00 ptal-printd mlc
root      4928  0.0  0.0  16464   564 ?        S    18:54   0:00 ptal-photod mlc
109       5013  0.1  1.4  27468 11068 ?        S    18:54   0:00 /usr/sbin/tor
daemon    5071  0.0  0.0  16332   436 ?        Ss   18:54   0:00 /usr/sbin/atd
root      5099  0.0  0.1  20836   956 ?        Ss   18:54   0:00 /usr/sbin/cron
juan      5217  0.0  1.9 197960 14824 ?        Ssl  18:54   0:00 x-session-manag
juan      5255  0.0  0.0  31264   616 ?        Ss   18:54   0:00 /usr/bin/ssh-ag
juan      5258  0.0  0.0  13092   672 ?        S    18:54   0:00 /usr/bin/dbus-l
juan      5259  0.0  0.1  23508  1016 ?        Ss   18:54   0:00 /usr/bin/dbus-d
juan      5261  0.0  0.7  39188  5816 ?        S    18:54   0:00 /usr/lib/libgco
juan      5264  0.0  0.1  17260  1028 ?        S    18:54   0:00 /usr/bin/gnome-
juan      5266  0.0  1.6 206416 12564 ?        Sl   18:54   0:00 /usr/lib/contro
juan      5274  0.0  0.0   3860   536 ?        Ss   18:54   0:00 /bin/sh -c /usr
juan      5275  0.0  0.4  23952  3244 ?        S    18:54   0:00 /usr/bin/esd -t
juan      5279  0.1  1.3 109632 10580 ?        S    18:54   0:00 /usr/bin/metaci
juan      5282  0.1  3.1 289352 24004 ?        S    18:54   0:00 gnome-panel --s
juan      5285  0.1  3.6 342140 27700 ?        S    18:54   0:00 nautilus --no-d
juan      5291  0.0  0.5  85440  3948 ?        S    18:54   0:00 /usr/lib/gnome-
juan      5293  0.0  0.4  79732  3680 ?        Ssl  18:54   0:00 /usr/lib/bonobo
juan      5294  0.0  0.7 167752  5508 ?        Ss   18:54   0:00 gnome-volume-ma
juan      5314  0.0  1.9 223792 15384 ?        S    18:54   0:00 update-notifier
juan      5322  0.0  1.5 281412 12096 ?        Sl   18:54   0:00 /usr/lib/evolut
juan      5326  2.4  6.2 324228 47888 ?        Sl   18:54   0:12 amule
juan      5329  0.0  0.1  14888   944 ?        S    18:54   0:00 /usr/lib/nautil
juan      5330  0.0  1.6 206760 12728 ?        S    18:54   0:00 nm-applet --sm-
juan      5331  0.0  1.2 225340  9960 ?        Sl   18:54   0:00 gnome-cups-icon
juan      5333  0.0  0.9 210660  7292 ?        Ss   18:54   0:00 gnome-power-man
juan      5342  0.0  1.5 270604 11676 ?        Sl   18:54   0:00 /usr/lib/evolut
juan      5355  0.2  4.2 262016 32744 ?        Sl   18:54   0:01 mono /usr/lib/t
juan      5376  0.0  1.0 227572  7832 ?        Sl   18:54   0:00 /usr/lib/evolut
juan      5426  0.0  2.1 226692 16440 ?        S    18:54   0:00 /usr/lib/gnome-
juan      5434  0.0  0.3 141772  2712 ?        Ss   18:54   0:00 gnome-screensav
juan      5592  0.0  0.2  10664  1680 ?        S    19:01   0:00 /bin/bash /usr/
juan      5593  0.0  0.2  10704  1800 ?        S    19:01   0:00 bash ./swiftfox
juan      5596  0.0  0.0   3864   580 ?        S    19:01   0:00 /bin/sh ./run-m
juan      5600 11.2  6.8 163148 52340 ?        Sl   19:01   0:12 ./swiftfox-bin
juan      5613  0.0  0.0      0     0 ?        Z    19:01   0:00 [net] <defunct>
juan      5661  5.2  2.7 245852 21032 ?        Sl   19:03   0:00 gnome-terminal
juan      5665  0.0  0.1  16932   796 ?        S    19:03   0:00 gnome-pty-helpe
juan      5666  3.0  0.4  20640  3660 pts/0    Ss   19:03   0:00 bash
juan      5685  0.0  0.1  14956  1060 pts/0    R+   19:03   0:00 ps axu

no is not here, i dont know what to do.

---

### Post by voodew on 2007-04-25
> **sinpalabras said:**
> juan@ubuntubox:~$ ps axu
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.2   5064  1960 ?        Ss   18:53   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    18:53   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   18:53   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    18:53   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   18:53   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   18:53   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   18:53   0:00 [kthread]
root        29  0.0  0.0      0     0 ?        S<   18:53   0:00 [kblockd/0]
root        30  0.0  0.0      0     0 ?        S<   18:53   0:00 [kacpid]
root        31  0.0  0.0      0     0 ?        S<   18:53   0:00 [kacpi_notify]
root       128  0.0  0.0      0     0 ?        S<   18:53   0:00 [kseriod]
root       158  0.0  0.0      0     0 ?        S    18:53   0:00 [pdflush]
root       159  0.0  0.0      0     0 ?        S    18:53   0:00 [pdflush]
root       160  0.0  0.0      0     0 ?        S<   18:53   0:00 [kswapd0]
root       161  0.0  0.0      0     0 ?        S<   18:53   0:00 [aio/0]
root      1998  0.0  0.0      0     0 ?        S<   18:53   0:00 [ata/0]
root      1999  0.0  0.0      0     0 ?        S<   18:53   0:00 [ata_aux]
root      2002  0.0  0.0      0     0 ?        S<   18:53   0:00 [scsi_eh_0]
root      2003  0.0  0.0      0     0 ?        S<   18:53   0:00 [scsi_eh_1]
root      2005  0.0  0.0      0     0 ?        S<   18:53   0:00 [ksuspend_usbd]
root      2006  0.0  0.0      0     0 ?        S<   18:53   0:00 [khubd]
root      2250  0.0  0.0      0     0 ?        S<   18:53   0:00 [kjournald]
root      2454  0.0  0.2  19900  1756 ?        S<s  18:53   0:00 /sbin/udevd --d
root      3405  0.0  0.0      0     0 ?        S<   18:53   0:00 [kpsmoused]
root      3478  0.0  0.0      0     0 ?        S<   18:53   0:00 [kgameportd]
root      3527  0.0  0.0      0     0 ?        S<   18:53   0:00 [scsi_eh_2]
root      3528  0.0  0.0      0     0 ?        S<   18:53   0:00 [usb-storage]
root      3892  0.0  0.0      0     0 ?        S<   18:53   0:00 [kjournald]
root      4207  0.0  0.0   3780   560 tty4     Ss+  18:53   0:00 /sbin/getty 384
root      4208  0.0  0.0   3780   564 tty5     Ss+  18:53   0:00 /sbin/getty 384
root      4211  0.0  0.0   3784   564 tty2     Ss+  18:53   0:00 /sbin/getty 384
root      4213  0.0  0.0   3784   564 tty3     Ss+  18:53   0:00 /sbin/getty 384
root      4214  0.0  0.0   3780   560 tty1     Ss+  18:53   0:00 /sbin/getty 384
root      4215  0.0  0.0   3784   564 tty6     Ss+  18:53   0:00 /sbin/getty 384
root      4453  0.0  0.1  12852  1488 ?        Ss   18:53   0:00 /usr/sbin/acpid
root      4555  0.0  0.0   5888   672 ?        Ss   18:53   0:00 /sbin/syslogd
root      4611  0.0  0.0   8036   572 ?        Ss   18:53   0:00 /bin/dd bs 1 if
klog      4613  0.0  0.2   5100  1832 ?        Ss   18:53   0:00 /sbin/klogd -P
103       4634  0.0  0.1  23508  1124 ?        Ss   18:53   0:00 /usr/bin/dbus-d
106       4650  0.4  1.2  36340  9296 ?        Ss   18:53   0:02 /usr/sbin/hald
root      4651  0.0  0.1  15380  1112 ?        S    18:53   0:00 hald-runner
106       4657  0.0  0.1  16548   952 ?        S    18:53   0:00 hald-addon-acpi
106       4665  0.0  0.1  16552   960 ?        S    18:54   0:00 hald-addon-keyb
106       4674  0.0  0.1  16548   956 ?        S    18:54   0:00 hald-addon-keyb
106       4677  0.0  0.1  16548   952 ?        S    18:54   0:00 hald-addon-keyb
106       4686  0.0  0.1  16548  1008 ?        S    18:54   0:00 hald-addon-stor
106       4694  0.0  0.1  16544   972 ?        S    18:54   0:00 hald-addon-stor
root      4708  0.0  0.0   6164   724 ?        Ss   18:54   0:00 /usr/sbin/dhcdb
root      4723  0.0  0.2  37524  1980 ?        Ss   18:54   0:00 /usr/sbin/Netwo
avahi     4741  0.0  0.1  27400  1408 ?        Ss   18:54   0:00 avahi-daemon: r
avahi     4742  0.0  0.0  27400   492 ?        Ss   18:54   0:00 avahi-daemon: c
root      4755  0.0  0.1  21684  1212 ?        Ss   18:54   0:00 /usr/sbin/Netwo
root      4768  0.0  0.1  15368   864 ?        Ss   18:54   0:00 /usr/bin/system
root      4769  0.0  0.1  23376  1296 ?        S    18:54   0:00 dbus-daemon --s
root      4801  0.0  0.2  94540  1632 ?        Ss   18:54   0:00 /usr/sbin/gdm
root      4804  0.0  0.3 107200  2628 ?        S    18:54   0:00 /usr/sbin/gdm
root      4807  1.0  4.7  99256 36448 tty7     SLs+ 18:54   0:05 /usr/X11R6/bin/
cupsys    4851  0.0  0.2  52536  2144 ?        Ss   18:54   0:00 /usr/sbin/cupsd
root      4875  0.0  0.1  41204   948 ?        Ss   18:54   0:00 /usr/sbin/hpiod
hplip     4878  0.0  0.9  91208  7352 ?        S    18:54   0:00 python /usr/sbi
root      4916  0.0  0.0  12756   520 ?        S    18:54   0:00 ptal-mlcd mlc:u
root      4919  0.0  0.0  16460   544 ?        S    18:54   0:00 ptal-printd mlc
root      4928  0.0  0.0  16464   564 ?        S    18:54   0:00 ptal-photod mlc
109       5013  0.1  1.4  27468 11068 ?        S    18:54   0:00 /usr/sbin/tor
daemon    5071  0.0  0.0  16332   436 ?        Ss   18:54   0:00 /usr/sbin/atd
root      5099  0.0  0.1  20836   956 ?        Ss   18:54   0:00 /usr/sbin/cron
juan      5217  0.0  1.9 197960 14824 ?        Ssl  18:54   0:00 x-session-manag
juan      5255  0.0  0.0  31264   616 ?        Ss   18:54   0:00 /usr/bin/ssh-ag
juan      5258  0.0  0.0  13092   672 ?        S    18:54   0:00 /usr/bin/dbus-l
juan      5259  0.0  0.1  23508  1016 ?        Ss   18:54   0:00 /usr/bin/dbus-d
juan      5261  0.0  0.7  39188  5816 ?        S    18:54   0:00 /usr/lib/libgco
juan      5264  0.0  0.1  17260  1028 ?        S    18:54   0:00 /usr/bin/gnome-
juan      5266  0.0  1.6 206416 12564 ?        Sl   18:54   0:00 /usr/lib/contro
juan      5274  0.0  0.0   3860   536 ?        Ss   18:54   0:00 /bin/sh -c /usr
juan      5275  0.0  0.4  23952  3244 ?        S    18:54   0:00 /usr/bin/esd -t
juan      5279  0.1  1.3 109632 10580 ?        S    18:54   0:00 /usr/bin/metaci
juan      5282  0.1  3.1 289352 24004 ?        S    18:54   0:00 gnome-panel --s
juan      5285  0.1  3.6 342140 27700 ?        S    18:54   0:00 nautilus --no-d
juan      5291  0.0  0.5  85440  3948 ?        S    18:54   0:00 /usr/lib/gnome-
juan      5293  0.0  0.4  79732  3680 ?        Ssl  18:54   0:00 /usr/lib/bonobo
juan      5294  0.0  0.7 167752  5508 ?        Ss   18:54   0:00 gnome-volume-ma
juan      5314  0.0  1.9 223792 15384 ?        S    18:54   0:00 update-notifier
juan      5322  0.0  1.5 281412 12096 ?        Sl   18:54   0:00 /usr/lib/evolut
juan      5326  2.4  6.2 324228 47888 ?        Sl   18:54   0:12 amule
juan      5329  0.0  0.1  14888   944 ?        S    18:54   0:00 /usr/lib/nautil
juan      5330  0.0  1.6 206760 12728 ?        S    18:54   0:00 nm-applet --sm-
juan      5331  0.0  1.2 225340  9960 ?        Sl   18:54   0:00 gnome-cups-icon
juan      5333  0.0  0.9 210660  7292 ?        Ss   18:54   0:00 gnome-power-man
juan      5342  0.0  1.5 270604 11676 ?        Sl   18:54   0:00 /usr/lib/evolut
juan      5355  0.2  4.2 262016 32744 ?        Sl   18:54   0:01 mono /usr/lib/t
juan      5376  0.0  1.0 227572  7832 ?        Sl   18:54   0:00 /usr/lib/evolut
juan      5426  0.0  2.1 226692 16440 ?        S    18:54   0:00 /usr/lib/gnome-
juan      5434  0.0  0.3 141772  2712 ?        Ss   18:54   0:00 gnome-screensav
juan      5592  0.0  0.2  10664  1680 ?        S    19:01   0:00 /bin/bash /usr/
juan      5593  0.0  0.2  10704  1800 ?        S    19:01   0:00 bash ./swiftfox
juan      5596  0.0  0.0   3864   580 ?        S    19:01   0:00 /bin/sh ./run-m
juan      5600 11.2  6.8 163148 52340 ?        Sl   19:01   0:12 ./swiftfox-bin
juan      5613  0.0  0.0      0     0 ?        Z    19:01   0:00 [net] <defunct>
juan      5661  5.2  2.7 245852 21032 ?        Sl   19:03   0:00 gnome-terminal
juan      5665  0.0  0.1  16932   796 ?        S    19:03   0:00 gnome-pty-helpe
juan      5666  3.0  0.4  20640  3660 pts/0    Ss   19:03   0:00 bash
juan      5685  0.0  0.1  14956  1060 pts/0    R+   19:03   0:00 ps axu

no is not here, i dont know what to do.

Well, I'm stumped. It looks like moblock is running from your tail output, but there's no pidof or apparent process ID. If you haven't modified anything, try pinging [www.riaa.com](www.riaa.com) and running the tail -f command in a separate terminal. If you're getting confirmed blocks, then moblock must be running correctly and there is a problem with pidof. If that's not the case, I hope someone can offer a solution.

---

### Post by kthu on 2007-04-25
If you had it installed from the amd64 debs someone made a while back, it will crash.  A new version needs to be built against the netfilter libraries that come with feisty. Building a new version can be done like this:

sudo echo "deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main" >>  /etc/apt/sources
sudo apt-get install build-essential
sudo apt-get update
mkdir foo
cd foo
apt-get source moblock-nfq
sudo apt-get build-dep moblock-nfq
cd moblock-0.8
debuild
cd ..
sudo dpkg -i moblock-nfq_0.8-14_amd64.deb

---

### Post by sinpalabras on 2007-04-25
thanks voodew for your interest and help.
 
 kthu i'll try to make what you say and post back

---

### Post by sinpalabras on 2007-04-25
i'm doing something wrong

juan@ubuntubox:~/foo/moblock-0.8$ sudo debuild
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp patch-stamp install-stamp install-stamp-moblock-ipq install-stamp-moblock-nfq 
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/home/juan/foo/moblock-0.8'
rm -f *.o *~ *# moblock-nfq moblock-ipq
make[1]: Leaving directory `/home/juan/foo/moblock-0.8'
dh_clean 
dpatch deapply-all
reverting patch MoBlock-ipq.sh from ./ ... ok.
reverting patch MoBlock-nfq.sh from ./ ... ok.
reverting patch makefile from ./ ... ok.
rm -rf patch-stamp debian/patched
 dpkg-source -b moblock-0.8
dpkg-source: building moblock using existing moblock_0.8.orig.tar.gz
dpkg-source: building moblock in moblock_0.8-14.diff.gz
dpkg-source: warning: file debian/docs has no final newline (either original or modified version)
dpkg-source: warning: executable mode 0755 of `debian/patches/MoBlock-nfq.sh.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of `debian/patches/makefile.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of `debian/patches/MoBlock-ipq.sh.dpatch' will not be represented in diff
dpkg-source: warning: ignoring deletion of file Changelog~
dpkg-source: building moblock in moblock_0.8-14.dsc
 debian/rules build
dpatch apply-all
applying patch makefile to ./ ... ok.
applying patch MoBlock-nfq.sh to ./ ... ok.
applying patch MoBlock-ipq.sh to ./ ... ok.
echo patched >patch-stamp
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: Entering directory `/home/juan/foo/moblock-0.8'
gcc -DLIBIPQ -Wall -O2  -fomit-frame-pointer -ffast-math -D_GNU_SOURCE   -I/usr/include/libipq -c -o  MoBlock-ipq.o MoBlock.c
gcc -Wall -O2  -fomit-frame-pointer -ffast-math -D_GNU_SOURCE   -I/usr/include/libipq   -c -o rbt.o rbt.c
gcc -o moblock-ipq MoBlock-ipq.o rbt.o -lipq
strip moblock-ipq
gcc -DNFQUEUE -Wall -O2  -fomit-frame-pointer -ffast-math -D_GNU_SOURCE   -I/usr/include/libipq -c -o  MoBlock-nfq.o MoBlock.c
gcc -o moblock-nfq MoBlock-nfq.o rbt.o -lnetfilter_queue
strip moblock-nfq
make[1]: Leaving directory `/home/juan/foo/moblock-0.8'
#docbook-to-man debian/moblock.sgml > moblock.1
touch build-stamp
 debian/rules binary
installing moblock-ipq
dh_testdir
dh_testroot
dh_installdirs
# Add here commands to install the package into debian/moblock.
/usr/bin/make install-moblock-ipq DESTDIR=/home/juan/foo/moblock-0.8/debian/moblock-ipq 
make[1]: Entering directory `/home/juan/foo/moblock-0.8'
install -m 755 moblock-ipq /home/juan/foo/moblock-0.8/debian/moblock-ipq/usr/bin
ln -s moblock-ipq /home/juan/foo/moblock-0.8/debian/moblock-ipq/usr/bin/moblock
make[1]: Leaving directory `/home/juan/foo/moblock-0.8'
touch install-stamp-moblock-ipq
installing moblock-nfq
dh_testdir
dh_testroot
dh_installdirs
# Add here commands to install the package into debian/moblock.
/usr/bin/make install-moblock-nfq DESTDIR=/home/juan/foo/moblock-0.8/debian/moblock-nfq 
make[1]: Entering directory `/home/juan/foo/moblock-0.8'
install -m 755 moblock-nfq /home/juan/foo/moblock-0.8/debian/moblock-nfq/usr/bin
ln -s moblock-nfq /home/juan/foo/moblock-0.8/debian/moblock-nfq/usr/bin/moblock
make[1]: Leaving directory `/home/juan/foo/moblock-0.8'
touch install-stamp-moblock-nfq
dh_testdir
dh_testroot
touch install-stamp
dh_testdir
dh_testroot
dh_installchangelogs Changelog
dh_installdocs --mainpackage=moblock-ipq -pmoblock-ipq
dh_installexamples
dh_install
dh_installlogrotate
dh_installinit
dh_installcron
dh_installman
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb -pmoblock-ipq
dh_shlibdeps
dh_gencontrol
dh_md5sums
dh_builddeb
dpkg-deb: building package `moblock-ipq' in `../moblock-ipq_0.8-14_amd64.deb'.
dh_testdir
dh_testroot
dh_installchangelogs Changelog
dh_installdocs --mainpackage=moblock-nfq -pmoblock-nfq
dh_installexamples
dh_install
dh_installlogrotate
dh_installinit
dh_installcron
dh_installman
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb -pmoblock-nfq
dh_shlibdeps
dh_gencontrol
dh_md5sums
dh_builddeb
dpkg-deb: building package `moblock-nfq' in `../moblock-nfq_0.8-14_amd64.deb'.
 dpkg-genchanges
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage (debuild emulation): binary and diff upload (original source NOT included)
Now signing changes and any dsc files...
 signfile moblock_0.8-14.dsc clessing <clessing@users.sourceforge.net>
gpg: WARNING: unsafe ownership on configuration file `/home/juan/.gnupg/gpg.conf'
gpg: WARNING: unsafe ownership on configuration file `/home/juan/.gnupg/gpg.conf'
gpg: skipped "clessing <clessing@users.sourceforge.net>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1155:
running debsign failed

sudo echo "deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main" >> /etc/apt/sources 

Did not work for me , so i add to my sources list : deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main . Update and work fine until debuild

---

### Post by Kaobear on 2007-04-25
Well laid out.  Exactly what was supposed to happen, did.

---

### Post by sinpalabras on 2007-04-25
could you be more specific Kaobear

---

### Post by sinpalabras on 2007-04-25
Should i generate a gpg key and try again?

---

### Post by sinpalabras on 2007-04-25
well i think is working. i just keeped going and it worked, just like kthu said. I was over complicated.
 I post here iff something happends. thaks you a lot!!!!!!!!!

---

### Post by kthu on 2007-04-25
The signing part is not important. The resulting file is not intended for distribution anyway :) The file should still be built and ready to install. Check the contents of the parent directory of the one you ran debuild in.

---

### Post by voodew on 2007-04-26
Wow, I didn't realize that there were many differences between a 32 bit and a 64 bit installation. I plan on upgrading soon, any more suggestions/differences?

---

### Post by shookone on 2007-04-26
Anyone find a way to resolve Feisty issue with Firehol/iptables??

All i have figured out is that "bash 3.2" is the culprit.

No idea how to fall back to 'bash 3.2 PL 17' 

shook-

---

### Post by shookone on 2007-04-26
I have managed to get rid of the error messages in feisty by doing the following:

```

sudo cat /lib/firehol/firehol |grep %q -n
2366:   printf "%q " "$@" >>${FIREHOL_OUTPUT}
4705:   printf >&2 "COMMAND: "; printf >&2 "%q " "${work_realcmd[@]}"; echo >&2
4726:   printf >&2 "COMMAND: "; printf >&2 "%q " "${work_realcmd[@]}"; echo >&2
4780:   printf >&2 "%q " "$@"
4977:           printf "%q " "${work_realcmd[@]}"
```


Using nano as my editor I edited the "/lib/firehol/firehol". (make a backup)

looking at lines 2366, 4705, 4726, 4780, & 4977. I replaced the %q with a %b.

No confirmation if this will resolve my issue, but the error messages are gone.. Now I have to test the integrity of the firewall.

---

### Post by shookone on 2007-04-26
> **shookone said:**
> I have managed to get rid of the error messages in feisty by doing the following:

```

sudo cat /lib/firehol/firehol |grep %q -n
2366:   printf "%q " "$@" >>${FIREHOL_OUTPUT}
4705:   printf >&2 "COMMAND: "; printf >&2 "%q " "${work_realcmd[@]}"; echo >&2
4726:   printf >&2 "COMMAND: "; printf >&2 "%q " "${work_realcmd[@]}"; echo >&2
4780:   printf >&2 "%q " "$@"
4977:           printf "%q " "${work_realcmd[@]}"
```


Using nano as my editor I edited the "/lib/firehol/firehol". (make a backup)

looking at lines 2366, 4705, 4726, 4780, & 4977. I replaced the %q with a %b.

No confirmation if this will resolve my issue, but the error messages are gone.. Now I have to test the integrity of the firewall.

Looks like the problems are gone.

Firehol is back to normal... atleast blocking services like ftp and ssh work....

---

### Post by Effect on 2007-04-26
How can you monitor what the program is doing, to make sure its doing it's job?

Having a gui with Peer Guardian in Windows makes this easy but not so I'm finding with Moblock. Thanks.

---

### Post by shookone on 2007-04-27
> **Effect said:**
> How can you monitor what the program is doing, to make sure its doing it's job?

Having a gui with Peer Guardian in Windows makes this easy but not so I'm finding with Moblock. Thanks.

I normally open a screen with tail -f /var/log/moblock

When i need to see whats up i just screen -r... or you can just leave a terminal open on a seperate desktop.

---

### Post by jingo811 on 2007-04-27
I don't understand how to install the two  *i386.deb files for my Dapper 6.06 which says Dapper 6.04 on the tutorial by the way :confused: 
Need help what do I do next?

.....ah now I see it had to be installed in a certain order and all that other sudo gedit stuff.  This is bad for us who's bad at using our Windows brains :-)

This happened during install is this something important or unimportant?
```
mike@sanka:~$ **gpg --export --armor DEDA0559 | sudo apt-key add -**
OK
mike@sanka:~$ **sudo apt-get update**
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:2 http://www.getautomatix.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:5 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Get:6 http://archive.canonical.com dapper-commercial Release [4886B]

....
....
....
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Err http://archive.ubuntu.com dapper/universe Packages
[COLOR="Red"]  404 Not Found [IP: 91.189.89.6 80]
Get:9 http://moblock-deb.sourceforge.net unstable Release [6720B]
Get:10 http://moblock-deb.sourceforge.net unstable/main Packages [889B]
Get:11 http://moblock-deb.sourceforge.net unstable/main Sources [602B]
Err http://packages.freecontrib.org dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection tim ed out
Fetched 13.3kB in 2m0s (111B/s)
Failed to fetch http://packages.freecontrib.org/plf/dists/dapper/Release.gpg  Co uld not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed o ut
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/x/xmms-midi/dists /dapper/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.89.6 80]
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used  instead.[/COLOR]
mike@sanka:~$
```

Also!
```

mike@sanka:~$ **sudo apt-get install moblock-nfq**
Reading package lists... Done
Building dependency tree... Done
[COLOR="Red"]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  moblock-nfq: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed
               Depends: libnfnetlink1 (>= 0.0.16) but it is not installable
E: Broken packages[/COLOR]
mike@sanka:~$

```

---

### Post by goodtimetribe on 2007-04-29
I'm surprised no one's asked, but I double checked with a search of this thread for wine and windows, but no results, so here's my question : Does it properly manage apps running in wine?

---

### Post by pelle.k on 2007-04-29
Yes.

---

### Post by clakar on 2007-05-01
Hi pelle.k
I have just installed MoBlock on my feisty. Just wanted to say that it works really well on my Toshiba laptop, nice and smooth. I have checked if it works, as following:

guille@maschine:~$ tail /var/log/moblock.log
Blocked OUT: British Broadcasting Corporation,hits: 3,DST: 132.185.8.88
Blocked IN: Beijing Television Station China,hits: 1,SRC: 202.108.108.251
Blocked OUT: United Nations Development Programme,hits: 4,DST: 140.191.12.88
Blocked OUT: Bogon,hits: 8,DST: 42.34.13.88
Blocked OUT: DoD Network Information Center,hits: 4,DST: 215.248.37.83
Blocked OUT: Bogon,hits: 32,DST: 103.134.124.84
Blocked OUT: Bogon,hits: 4,DST: 196.55.5.88
Blocked OUT: British Broadcasting Corporation,hits: 4,DST: 132.185.8.88
Blocked OUT: p2p abusers,hits: 2,DST: 202.98.116.66
Blocked IN: SONY Corporation,hits: 1,SRC: 202.94.128.92

So, that means it works & blocks quite well.
I am just looking forward fot that marvellous python GUI I read at the beginning of the thread. :) 
Please let us know! God bless an application as MoBlock!

---

### Post by techstop on 2007-05-05
Hi. I am getting an authentication error when trying to install;

```
WARNING: The following packages cannot be authenticated!
  moblock-nfq
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated
```

I have run the commands in the first post for importing the key. Any pointers?

---

### Post by worntreads on 2007-05-05
hey there,  i'm new to linux, and while i'm starting to get the hang of how things work around here, it's slow going in most regards.  i've been trying to get moblock up and running for several days now, i've spent hours reading throught the last 51 pages of post trying the various methods described herein to no avail.   i'm using edgy on a 32bit amd.  moblock is installed , i get a pid, it starts and stops, but i don't think anything is being blocked.  here's why:

a random address from guarding.p2p

```
fred@basement:~$ ping -c1 203.108.241.176
PING 203.108.241.176 (203.108.241.176) 56(84) bytes of data.

--- 203.108.241.176 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

fred@basement:~$ 

```

which results in the log 

```
fred@basement:~$ tail /var/log/moblock.log 
Ranges loaded: 179221
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'
error during nfq_create_queue()
Ranges loaded: 179221
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'
error during nfq_create_queue()
fred@basement:~$ 

```

and while i've manually downloaded the guarding.p2p file, i can't seem to ever connect to bluetack.co.uk for the other lists.  

my concern is that the log file never shows anything being blocked.    along with the 'error during nfq_create_queue' bit.  any help is always appreciated, thanks.

---

### Post by jre on 2007-05-06
@techstop: don´t worry, verification of moblock-deb.sourceforge.net is broken here, too. Don´t know what´s wrong, but you still get the correct packages.

@worntread:Your blocklist should be ok with 179221 loaded ranges. I don´t know why you can´t connect to bluetack.co.uk; normally if there are problems then only with the level1.gz list (which is the biggest list)

moblock is not working because of the "error during nfq_create_queue()". Perhaps your problem is that moblock was started several times, so just try `/etc/init.d/moblock-nfq stop` as root a few times and then start moblock again (or reboot).

If this doesn´t help then:
Did you install the netfilter-debs from the first post!?
You could still try moblock-ipq instead of moblock-nfq

---

### Post by worntreads on 2007-05-06
i've started from scratch on this one.  i uninstalled moblock and the libs, then reinstalled using the debs in the first post (just to make sure i was on the right versions).  

...and everything worked out fine.   i'm still not sure what the problem was,  but i'll assume user error and be happy. :)  actually, i think i was using the wrongs debs to start and just snowballed from there.  

thanks for the help.

---

### Post by shame on 2007-05-16
I have just installed the 64-bit version of moblock and followed the guide in the first post and it appears to be running ok (logs show it is blocking things at least).
I have one question though.

I have a really crap router and the firewall settings in it are very ropey and because I have to reset it to factory settings once a day to get proper access, I don't bother with the firewall rules at all, meaning everything is blocked.
So that being the case, is something like moblock still useful?

---

### Post by chronniff on 2007-05-18
?yo does anyone know how to  open  up specific ports so that they aren't blocked at all? I can't figure it out and I'm sure it is something simple, but it is driving me nuts haha

---

### Post by konsole on 2007-05-19
> **chronniff said:**
> ?yo does anyone know how to  open  up specific ports so that they aren't blocked at all? I can't figure it out and I'm sure it is something simple, but it is driving me nuts haha

sure is... search this thread for "whitelist" (hint: /etc/moblock/MoBlock-nfq.sh)

---

### Post by jre on 2007-05-19
@shame: a "normal" firewall and moblock have different purposes. **If** you want to block the IPs in moblock´s blocklist then moblock is usefull for you (this is all moblock is for, nothing more, nothing less). Go to [www.bluetack.co.uk](www.bluetack.co.uk) to see of what kind these IPs are.
On the other side your routers firewall will give you protection against unwanted connections/attacks not related to specific IPs.

---

### Post by MachineBucket on 2007-05-22
Has there been any progress in a GUI for MoBlock?

---

### Post by pelle.k on 2007-05-22
Nope. You'll be better of just creating a "launcher" and tick "run in terminal". The "command should be;
```
tail -f /var/log/moblock.log
```

If you're a bit adventurous, you could try something like this;
```
[ -n "$(pidof moblock)" ] && tail -f /var/log/moblock.log || echo "moblock is not running..."
```

This last code block is not fool proof, since i'm _not_ running ubuntu ATM. So i don't know if this still applies. (You should note however, that moblock takes some time to register it's "pid" so don't hammer this right away after booting up...)

Now, if you do this in kde (create a launcher, that is), you can have it placed in the system tray if you want. yay! ;)

---

### Post by klhrevolutionist on 2007-05-22
Hello, I followed your feisty instructions. Everything seems to be going fine & I was wondering how to make moblock startup when I startup my ubuntu install. Thanks.

tip: I also use a good hosts file, [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

---

### Post by paul_banks on 2007-05-24
Hey all,

I used the following instructions to get moblock working on my Feisty 64bit install:

sudo dpkg -i libnfnetlink0_0.0.14-1.1_amd64.deb
sudo dpkg -i libnfnetlink-dev_0.0.14-1.1_amd64.deb
sudo dpkg -i libnetfilter-queue_0.0.11-1.1_amd64.deb
sudo dpkg -i libnetfilter-queue-dev_0.0.11-1.1_amd64.deb
sudo dpkg -i moblock-nfq_0.8-10_amd64.deb

moblock works, as far as I can tell, but I've got a broken package now. Synaptic manager tells me that libnetfilter-queue-dev is broken, but when I try to reinstall it, it tells me I have to install libnetfilter-queue1 as well. Fine by me, but I get the following error:

E: /var/cache/apt/archives/libnetfilter-queue1_0.0.12-1_amd64.deb: trying to overwrite `/usr/lib/libnetfilter_queue_libipq.so.1.0.0', which is also in package libnetfilter-queue

I'm **very** new to Ubuntu, so I'm afraid to proceed on my own here...

---

### Post by aryah on 2007-05-24
> **jre said:**
> @shame: a "normal" firewall and moblock have different purposes. **If** you want to block the IPs in moblock´s blocklist then moblock is usefull for you (this is all moblock is for, nothing more, nothing less). Go to [www.bluetack.co.uk](www.bluetack.co.uk) to see of what kind these IPs are.
On the other side your routers firewall will give you protection against unwanted connections/attacks not related to specific IPs.

but    iptables -A INPUT -s $i -j DROP blacklists a host $i completely; apparently, a firewall is rather good in blacklisting, and has many other options as well.

isnt this basicly what moblock does; sets the behavior of the firewall? I thought it was simply a script to use the well researched blacklists maintained for peerguardian with netfilter firewall, and to update them automatically?

when it comes to classifying packages coming to your host and dealing with them accordingly , firewalls do this 'for living', and are very sophisticated in this, with a lot of possibilities.

---

### Post by jre on 2007-05-27
@aryah: Yes, what moblock does is basicly the same as inserting iptables rules for DROPing every range in the blacklists. It just does the dropping via the iptables rule QUEUE since this is faster for such a long list of IP ranges.
And yes, other firewalls in Linux also use the rich functionality of iptables (but in most cases not only based on the IP as moblock does).

---

### Post by phishinphree on 2007-05-30
I didn't see this issue addressed before but I could have missed it scanning the posts.

I have a problem with moblock-nfq when using apache and ssh.  when its installed, web requests made to the server moblock is running on take ~7 seconds to reply instead of being near instant on my local network. The lag also occurs after putting my username in when I ssh to the machine.  It takes ~7 seconds for the password prompt to pop back up.  I'm a 4th year cs student and ip tables are one of those things I've heard of but never worked with so I'm at a bit of a loss in figuring out where to start. 

I don't have any firewall or really anything other than a basic kubuntu LAMP setup.  Fresh install a week or two ago. 

First thing I did was try and add http to the whitelist but there was no effect:
```

#!/bin/sh
#
# MoBlock.sh - MoBlock start script
# ---------------------------------

ACTIVATE_CHAINS=1
WHITE_TCP_IN="http"
WHITE_UDP_IN="http"
WHITE_TCP_OUT="http"
WHITE_UDP_OUT="http"
WHITE_TCP_FORWARD="http https"
WHITE_UDP_FORWARD="http https"

```


And here's iptables -L:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     0    --  anywhere             anywhere
MOBLOCK_IN  0    --  anywhere             anywhere            state NEW

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
MOBLOCK_FW  0    --  anywhere             anywhere            state NEW

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     0    --  anywhere             anywhere
MOBLOCK_OUT  0    --  anywhere             anywhere            state NEW

Chain MOBLOCK_FW (1 references)
target     prot opt source               destination
ACCEPT     udp  --  anywhere             anywhere            udp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_IN (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_OUT (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0


```

I would be very grateful of any help and I'm curious if anyone else uses torrentflux when moblock.  I just rebuilt a server and things were working with a 8 or 9 month old version and older version of kubuntu before the harddrive expired.:(

Thanks 
-Phish

---

### Post by Occidere on 2007-05-31
Hello everybody,

I am running Moblock on a xubuntu (Edgy Eft) system and it's running okay so far. But I can't connect to jabber servers while Moblock is running.

```

Blocked OUT: Chaos Computer Club,hits: 1,DST: 217.10.10.194
Blocked OUT: Chaos Computer Club,hits: 2,DST: 217.10.10.194
Blocked OUT: Chaos Computer Club,hits: 3,DST: 217.10.10.194
Blocked OUT: Chaos Computer Club,hits: 4,DST: 217.10.10.194

```

This ip address is for jabber.ccc.de and I tried to unblock the ip address in /etc/cron.daily/moblock-nfq but it did not work. Does somebody here know how to unblock that specific ip address?

Thanks.

---

### Post by Occidere on 2007-05-31
That was a quick one, I just needed to unblock the jabber ports in /etc/moblock/MoBlock-nfq.sh.

---

### Post by iBART on 2007-06-01
wrong post

---

### Post by brk3 on 2007-06-01
Hey guys, I know theres being various posts about GUIs for moblock but none of them really seemed to appear, so Ive made a basic one for gnome using mono.
See what you think, the only thing in it that doesnt work at the moment is showing how many Ips are being blocked, I couldnt figure out how to do this, if anyone knows can they please let me know!

Ive included a readme on how to run it, anyway see what you think!

---

### Post by jamesford on 2007-06-02
the gui looks good (or at least a promising start)
i dont like that it has to be run as root though. wouldnt it be better to run as regular user and then prompt for password when the user clicks a button that performs a taks that requires root privileges?

also u forgot to tell alltray to use the M logo u made

---

### Post by brk3 on 2007-06-02
Thanks for the input! Have added your suggestions, found out how to display the number of ips being blocked and added a couple of other fixes.
Give it a go!

---

### Post by yano on 2007-06-03
from everything i have looked at there is one thing I still don't see I can do with MoBlock

How can I have multiple blocklists instead of just guarding.p2p?

---

### Post by ratai on 2007-06-03
Really good job.
But :
- often we must restart firehol for stopping really moblock : one proposition : because Firehol is working with Moblock maybe ur gui could give access to the firewall too with root access to modify anything
- often we would update or whitelist : maybe link access could exist on panel...

---

### Post by brk3 on 2007-06-03
> **yano said:**
> from everything i have looked at there is one thing I still don't see I can do with MoBlock

How can I have multiple blocklists instead of just guarding.p2p?

I think you just pass them in as parameters when starting moblock. I reckon I could implement a block list manager do you know where to find other blocklists?

---

### Post by jamesford on 2007-06-03
the new version of the gui is looking very good. thanks for implementing my suggestions

dont know how advanced u intend to make this gui but if ur planning to carry on improving it i would suggest a native non-alltray tray icon, maybe with some functionality liek showing different icons when enable and disabled etc

great job

edit:ive noticed mono an MoBlockGUI.exe stays in memory some times when u close it by rclicking the tray icon

---

### Post by brk3 on 2007-06-03
good idea, will look into it, alltray just seemed the quickest solution but im sure its not hard to program it.
ive stuck it on gnomefiles might be easier to keep track of it than forum posts: [http://www.gnomefiles.org/app.php/MoBlockGUI](http://www.gnomefiles.org/app.php/MoBlockGUI)

edit: noticed that too, shall be fixed!

---

### Post by jamesford on 2007-06-03
ive also noticed another thing, i dont know if its jut me who doesent know how to do things but ive made myself a launcher for the gui and it wont launch unless i edit startMoBlockGUI.sh and add a line at the top saying cd /path/to/moblockgui-dir

oh and u should hold a icon/logo design contest!

---

### Post by edwardecl on 2007-06-03
That GUI is very cool, although it involved a bit more than just installing mono and alltray. All I want now is a program that can run on clients to view the same information, as the computer running moblock just acts as a server...

But still it's a nice addition. The enable/disable button just seems to crash it but other than that it's good.

---

### Post by brk3 on 2007-06-03
hmm the enable/disable button should work fine, does it work for you jamesford?
Do you have gksudo installed? As it calls that to get the root password to enable/disable moblock.
Anywho, have got native tray support added, and it also takes care of the process not being killed on quitting. Should have the next version uploaded to the gnomefiles page by tomorrow evening!

---

### Post by golem3 on 2007-06-05
Again, great guide, thanks for updating it for Feisty.

---

### Post by rautamiekka on 2007-06-13
How to add custom filters ? Please update the first post with how-to that

---

### Post by pelle.k on 2007-06-13
I'm not sure i understand what you mean by "custom filters"? If you could elaborate on that i might update the howto...

---

### Post by rautamiekka on 2007-06-14
In PG you can make lists on your own, that's what I mean with custom filter, so how to make them in Moblock or how to add more blocked IPs on your own ?

---

### Post by sloter on 2007-06-14
Hello rautamiekka,


I think you can handle that by adding your own range of ip in /etc/moblock/guarding.p2p according to the .p2p format. I do not know any moblock script configuration file which does that yet.
You can also create your own list in a .p2p format and modify the shell variable BLOCKLISTS defined in /etc/cron.daily/moblock-nfq. I do not really like that.

I know you can edit /etc/moblock/MoBlock-nfq.sh and put your own tcp, udp whitelist.

But the most important to remember is that MoBlock is not a firewall.

Would you please give me an example when you use your own IP to be blocked by MoBlock?

Thx,

---

### Post by empthollow on 2007-06-24
i tried the moblockgui and it's pretty cool but there were some things I wanted to be able to do other than start and stop it.  so i wrote a graphical bash script that uses zenity (which is defaultly installed in ubuntu). i don't have anywhere to host the file so i'll post the text here. make sure you add execute permissions on the file, then doubble click and run. the only thing i haven't been able to do is dock the application. everytime i dock it with alltray, alltray quits with the application.

This is what Mobutil2 can do:

restart moblock
stop moblock
set moblock to autostart at boot
remove from autostart at boot
show end of log file
display process ID of moblock
show list of addresses affected
update the blocklist
disable daily update of blocklist
enable daily update of blocklist

Mobutil2 script
```
#!/bin/bash

pid()
{
if [ $(gksu pidof moblock) != "0" ]; then
	zenity --info --text "Moblock's PID is "$(gksudo pidof moblock) --width 400
else
	zenity --info --text "Moblock is not running" --width 400
	
fi
}

until [ "$selection" = "0" ] ; do
selection=$(zenity --height=385 --width=400 --list  --text "Please choose an option" --radiolist  --column "Choose" --column "Action" FALSE Restart FALSE Stop FALSE "Set to autostart" FALSE "Remove from startup" FALSE "Show end of log file" FALSE "Show Process ID" FALSE "Show blocked addresses" FALSE "Update block list" FALSE "Set to update block list daily" FALSE "Remove Daily Block list update" FALSE "Exit"); echo $selection
	case "$selection" in
		"Show Process ID"		) pid ;; 
		"Restart"			) gksu /etc/init.d/moblock-nfq restart | zenity --progress --pulsate --text Restarting ;;
		"Stop"				) gksu /etc/init.d/moblock-nfq stop | (zenity --progress --pulsate --text Stopping) ;;
		"Set to autostart"		) gksu update-rc.d moblock-nfq defaults | zenity --info --text "Moblock will start at boot" --width 500 ;;
		"Remove from startup"		) gksu "update-rc.d -f moblock-nfq remove" | zenity --info --text "Moblock will NOT start at boot" --width 500 ;;
		"Show end of log file"  	) tail /var/log/moblock.log | zenity --text-info --height 300 --width 530 ;;
		"Show blocked addresses"	) cat /etc/moblock/guarding.p2p | grep ads | zenity --text-info --height 300 --width 530 ;;
		"Update block list"		) gksu sh /etc/cron.daily/moblock-nfq | (zenity --progress --pulsate --text Updating) ;;
  		"Set to update block list daily"	) gksu chmod -x /etc/cron.daily/moblock-nfq | zenity --info --text "Block list will be updated daily" --width 500 ;;
	 	"Remove Daily Block list update"	) gksu chmod +x /etc/cron.daily/moblock-nfq | zenity --info --text "Block list will be NOT updated daily" --width 500 ;;
 		"Exit" 				) exit ;;
	esac
done
exit
```

---

### Post by sloter on 2007-06-24
Hi  empthollow,

Your script is pretty cool and light. Thx for posting

sloter

---

### Post by empthollow on 2007-06-24
glad you like it, let me know if you can find a way to dock it.

---

### Post by empthollow on 2007-06-26
i updated the script to display in the first window if moblock is running or not, here is the new code:

```
#!/bin/bash

pid()
{
if [ $(pidof moblock) != "0" ]; then
	zenity --info --text "Moblock's PID is "$(pidof moblock) --width 400
else
	zenity --info --text "Moblock is not running" --width 400
	
fi
}

until [ "$selection" = "0" ] ; do

if [ $(pidof moblock) != "0" ]; then
	text=""
else
	text="not "
	
fi

selection=$(zenity --height=385 --width=400 --list  --text "Moblock is "$text"running" --radiolist  --column "Choose" --column "Action" FALSE Restart FALSE Stop FALSE "Set to autostart" FALSE "Remove from startup" FALSE "Show end of log file" FALSE "Show Process ID" FALSE "Show blocked addresses" FALSE "Update block list" FALSE "Set to update block list daily" FALSE "Remove Daily Block list update" FALSE "Exit"); echo $selection
	case "$selection" in
		"Show Process ID"		) pid ;; 
		"Restart"			) gksu /etc/init.d/moblock-nfq restart | zenity --progress --pulsate --text Restarting ;;
		"Stop"				) gksu /etc/init.d/moblock-nfq stop | (zenity --progress --pulsate --text Stopping) ;;
		"Set to autostart"		) gksu update-rc.d moblock-nfq defaults | zenity --info --text "Moblock will start at boot" --width 500 ;;
		"Remove from startup"		) gksu "update-rc.d -f moblock-nfq remove" | zenity --info --text "Moblock will NOT start at boot" --width 500 ;;
		"Show end of log file"  	) tail /var/log/moblock.log | zenity --text-info --height 300 --width 530 ;;
		"Show blocked addresses"	) cat /etc/moblock/guarding.p2p | grep ads | zenity --text-info --height 300 --width 530 ;;
		"Update block list"		) gksu sh /etc/cron.daily/moblock-nfq | (zenity --progress --pulsate --text Updating) ;;
  		"Set to update block list daily"	) gksu chmod -x /etc/cron.daily/moblock-nfq | zenity --info --text "Block list will be updated daily" --width 500 ;;
	 	"Remove Daily Block list update"	) gksu chmod +x /etc/cron.daily/moblock-nfq | zenity --info --text "Block list will be NOT updated daily" --width 500 ;;
 		"Exit" 				) exit ;;
	esac
done
exit
```

---

### Post by moore.bryan on 2007-07-07
[I]nice script empthollow, but i keep getting the following error:
```
No column titles specified for List dialog.
./moblockgui.sh: line 27: --radiolist: command not found
./moblockgui.sh: line 29: FALSE: command not found

```
ideas?[/I]

---

### Post by pelle.k on 2007-07-07
the lines must have been truncated somehow when you cut/pasted them into a new file.

---

### Post by iBART on 2007-07-07
cool script. thanks :)

---

### Post by MiGke on 2007-07-07
Hi everybody, 

i've been using moblock for some time and i think it's a great application. I had to reinstall my ubuntu box and now i can't install moblock. It seems that the moblock repository's are not working (moblock is not present in the repository). Apt is giving me the 404 error. 

If anybody knows where else I can find the file I'd much appreciate any info, thanks.

---

### Post by VileTimes on 2007-07-08
> **MiGke said:**
> Hi everybody, 

i've been using moblock for some time and i think it's a great application. I had to reinstall my ubuntu box and now i can't install moblock. It seems that the moblock repository's are not working (moblock is not present in the repository). Apt is giving me the 404 error. 

I having the same problem. :(

---

### Post by zivagolee on 2007-07-09
Check out Trevino's repo:

[http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/](http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/)

---

### Post by VileTimes on 2007-07-09
> **zivagolee said:**
> Check out Trevino's repo:

[http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/](http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/)


Thanks for the help. :)

---

### Post by moore.bryan on 2007-07-09
> **pelle.k said:**
> the lines must have been truncated somehow when you cut/pasted them into a new file.
*i guess that was it... stupid nano.  ;-)*

---

### Post by pelle.k on 2007-07-09
> stupid nano
nano -w

:D

---

### Post by jre on 2007-07-10
> **empthollow said:**
> i updated the script to display in the first window if moblock is running or not, here is the new code:[...]

```
"Show blocked addresses"	) cat /etc/moblock/guarding.p2p | grep ads | zenity --text-info --height 300 --width 530 ;;
```This way you won´t see all blocked addresses, so remove "| grep ads"


```
"Set to update block list daily"	) gksu chmod -x /etc/cron.daily/moblock-nfq | zenity --info --text "Block list will be updated daily" --width 500 ;;
"Remove Daily Block list update"	) gksu chmod +x /etc/cron.daily/moblock-nfq | zenity --info --text "Block list will be NOT updated daily" --width 500 ;;
```Should be the other way I think.


From a first glance the rest seems nice and ok.
jre

EDIT: "Stop moblock" has funny results on your script, so that you have to kill it manually. I didn´t test the other options.

---

### Post by Occidere on 2007-07-12
I am running Feisty xubuntu now and installed Moblock, but it is not running correct.

Here is what the shell says:

```

 sudo /etc/init.d/moblock-nfq restart
 * Restarting moblock moblock                                            [ OK ] 

```

This is looking good.

```
cat /etc/moblock/guarding.p2p | grep ads
```

A big load of ip addresses, seems to be okay.

```

ping -c1 218.214.123.52
PING 218.214.123.52 (218.214.123.52) 56(84) bytes of data.

--- 218.214.123.52 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms
```

Looks good, too.

```
tail /var/log/moblock.log
```

Nothing happens, the file is empty.

```
pidof moblock
```

There is no process id for moblock.

```

 sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```

Moblock did not set up any rules for iptables.

Any ideas?

---

### Post by sloter on 2007-07-12
Occidere,

Did you try ```
kill -SIGHUP `cat /var/run/moblock.pid`
```
This  lets moblock perform a re-initialization. Dumps and resets stats then reloads blocklist file.

sloter

---

### Post by CaptainWalrus on 2007-07-12
I have been unable to get MoBlock to Install on Kubuntu Fiesty. I get the following error:

```

frank@TropicalIsland:~$ sudo apt-get install moblock-nfq
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  moblock-nfq: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is to be installed
               Depends: libnetfilter-queue1 (>= 0.0.13) but 0.0.12-1 is to be installed
               Depends: libnfnetlink0 (>= 0.0.25) but it is not installable
E: Broken packages
```

---

### Post by empthollow on 2007-07-12
i was unable to find a way to upgrade to the new version as well and can't find those packages. :confused:

---

### Post by Griz054 on 2007-07-13
I've got the same issue as CaptainWalrus and I'm running Ubuntu Feisty. Any thoughts?

---

### Post by Zaphrod on 2007-07-14
I have installed Moblock as described and it appears to be working when I ping an address the first time
```

$ ping -c1 209.87.178.244
PING 209.87.178.244 (209.87.178.244) 56(84) bytes of data.

--- 209.87.178.244 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

```

but if I then ping the same address or another address again it doesn't block it

```

$ ping -c1 209.87.178.244
PING 209.87.178.244 (209.87.178.244) 56(84) bytes of data.
64 bytes from 209.87.178.244: icmp_seq=1 ttl=240 time=124 ms

--- 209.87.178.244 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 124.296/124.296/124.296/0.000 ms

```

If I restart moblock
```
$ sudo /etc/init.d/moblock-nfq restart
 * Restarting moblock moblock                                            [ OK ] 

```

It blocks again for 1 ping only.

---

### Post by Occidere on 2007-07-14
> **sloter said:**
> Occidere,

Did you try ```
kill -SIGHUP `cat /var/run/moblock.pid`
```
This  lets moblock perform a re-initialization. Dumps and resets stats then reloads blocklist file.

sloter

```
cat: /var/run/moblock.pid: No such file or directory
```

Does not work, too.

---

### Post by pelle.k on 2007-07-14
OK guys, the moblock deb was compiled/updated against "unstable". That means you have two options;
1. Find the old package in /var/apt/cache and downgrade + comment out moblock repo in sources.list
2. Force installation. (completely on your own risk though. can _not_ guarantee it'll work)

It might help if somebody who have the latest working deb could post it at one of those download link sites (You know what i mean), for people here, who can't get it otherwise.
_NOTE_ ; If this is a new installation: "dpkg" doesn't resolve dependencies for you, but gdebi (the graphical package installer in ubuntu) does. So remeber to install libnetfilter-queue and libnfnetlink with dpkg method.

The package that doesn't work is "moblock-nfq_0.8-15_i386.deb", that got uploaded to the repo june 13:th (two days ago), and thus you should be looking for moblock-nfq_0.8-14_i386.deb.

I myself can't compile a new version of moblock for you, since i am _not_ running ubuntu ATM. You're not missing out on anything though, since _no_ new stuff was added, but it was just compiled against _other_ libs introduced to debian "unstable" of which this repo is originally for.

---

### Post by uljanow on 2007-07-18
> **CaptainWalrus said:**
> I have been unable to get MoBlock to Install on Kubuntu Fiesty. I get the following error:

```
The following packages have unmet dependencies:
  moblock-nfq: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is to be installed
               Depends: libnetfilter-queue1 (>= 0.0.13) but 0.0.12-1 is to be installed
               Depends: libnfnetlink0 (>= 0.0.25) but it is not installable
E: Broken packages
```

The reason for those unmet dependencies is that the moblock package is for Debian. But you could build ubuntu packages out of the moblock source.

There is also an alternative to the peerguardian linux alternative, named [**iplist**]("http://iplist.sf.net"), which has prebuild Ubuntu Feisty packages.

---

### Post by jre on 2007-07-24
moblock-deb.sourceforge.net provides the old package again (depends on libc6 >= 2.3.6-6, libnetfilter-queue1 >=0.0.12, libnfnetlink1 >= 0.0.16, lsb-base >= 3.0-3, gzip, iptables, wget).

@Zaphrod+Occidere: No idea...

Greets
jre

---

### Post by Overquoted on 2007-07-27
I'm feeling both frustrated and stupid at this point. I *must* whitelist these two bits or I am unable to do anything on the internet (it basically blocks my entire connection):

```
Blocked OUT: Route Object for IBMGSATL,hits: 4,DST: 67.32.118.46
Blocked OUT: Route Object for IBMGSATL,hits: 3,DST: 65.83.241.181

```

I'm not sure what I'm supposed to whitelist (though, after looking through a big portion of the forum, I know how to edit it through root, where to edit and that I can't whitelist IPs, which is not good, since it's only those two IPs I need whitelisted).

I'm new to Ubuntu (and Linux) but I'm also *really* missing PeerGuardian2 atm. I'm sorry I can't figure it out on my own. >_<

---

### Post by pelle.k on 2007-07-27
I'm quoting... my own FAQ! :D

> **What about filtering out some stuff i wan't to connect to**?
If you want to whitelist ip ranges then do it in cleartext in /etc/cron.daily/moblock-nfq at line 114 (at the end of the file).
Remove the two # (hashes) which makes it (the lines of code) commented out. add names of ip ranges from the guarding.p2p file. like this;
```
grep -v -i "IBMGSATL" merged.p2b.p2p > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p
```

I did however adjust it a bit **just for you**. :)
I know this concept is frightening, but this is often how things are done in linux, since everything is more or less ready to be run on a "headless" server. I agree the configuration files could be improved for readability quite a bit, but i am not the maintainer of this package. Furthermore, i also think what is missing is a decent GUI to do these kind of things, but until then this will have to do. Happy blocking!

---

### Post by Overquoted on 2007-07-28
Oh, thank you so much! :) I just couldn't figure out what I was supposed to put there. >_< I read your guide about fifteen times, too. Apparently, I'm just dense. :)

And yeah, a GUI would be nice. :)

---

### Post by pepz on 2007-08-01
i would know if i can use moblock with deluge torrent client ([http://deluge-torrent.org](http://deluge-torrent.org)).
It seems that moblock doesn't block any ip's with this client. How can i make a test?
Deluge client has a blocklist importer plugin, but i would use moblock in order to filter ip's on ed2k and torrent net.
Thanks
Bye
pepz

---

### Post by pelle.k on 2007-08-01
> It seems that moblock doesn't block any ip's with this client. How can i make a test?
You got this all wrong. moblock is just a layer between the internet and your kernel (although this explanation is heavily simplified)

Internet -> moblock -> kernel -> $application

See? moblock serves the kernel, not specific applications. I've described in my FAQ, how to test the functionality of moblock...

---

### Post by pepz on 2007-08-01
ok, i've made same mistakes... by the way, i understood that moblock works perfectly only if i start it manually, after my connection to the net, and after i can see in moblock.log file this string
```
NFQUEUE: binding to queue '0'
```

How can i solve this matter in order to let moblock work at the boot?
bye
pepz

---

### Post by pelle.k on 2007-08-01
I dont understand your question. Are you saying that it does start **automatically** at boot, but that you have to do it a second time **manually** before moblock is functional?

---

### Post by pepz on 2007-08-02
yes; if i don't restart it manually, i can't see the string 
```
NFQUEUE: binding to queue '0'
``` and moblock doesn't work.
bye
pepz

---

### Post by pelle.k on 2007-08-02
That is probably because moblock has to load a gigantic blocklist _before_ it's ready to kick ***. I suggest you wait a bit before checking moblock.log out after a reboot. Just a theory...

---

### Post by pepz on 2007-08-02
i followed your suggestion, i waited for 10 min, but nothing happens. This is my moblock.log file

```
pepz@ubuntu:~$ tail -f /var/log/moblock.log 
Skipping useless range: (050412) The Thing, Lovgate 3389 6000
Skipping useless range: (050309) W32.Rahack 4899
Skipping useless range: (050428) W32.Spybot 1433 6000
Skipping useless range: (050412) W32.Rahack 4899
Skipping useless range: (050430) Lala, W32.Keco 1025
Skipping useless range: (050428) W32.Spybot 1433 6000
Skipping useless range: (050326) Unassigned 33437
Ranges loaded: 276189
Merged ranges: 316
Skipped useless ranges: 8372

``` 

How can i edit moblock-nfq in order to start it when i connect to the Net?
I've a dsl dial-up connection.
thanks a lot.
pepz

---

### Post by pepz on 2007-08-03
ok i solved the problem with a start script placed in /etc/ppp/ip-up.d/
How can i am sure that moblock autoupdates its lists?
thanks 
bye
pepz

---

### Post by pelle.k on 2007-08-03
that's wierd. I don't really understand why moblock had to be started up after ppp, but nevertheless, good job!
There's a cron script that does updates daily. it's in /etc/cron.daily (i belive). You can move it to cron.weekly or deactivate it (chmod -x). But it's already activated by default...

---

### Post by pepz on 2007-08-04
ok i know that there's a script in /cron.daily, but how can i verify that ubuntu starts this script daily? is there a log where can i see this?
bye
pepz

---

### Post by jamesford on 2007-08-04
i dont trust the /cron.daily script. found it better to move the script elsewhere and run it with crontab, that way i get system email confirming the updates as well

---

### Post by pepz on 2007-08-04
how have i to edit crontab in order to run that script?
only adding a line with the script's path?
thanks
bye
pepz

---

### Post by Roxlo on 2007-08-13
I get this error when trying to open/install the MoBlock deb
error: dependency is not satisfiable libnfnetlink0
Thanks for any help

---

### Post by sloter on 2007-08-13
Hello Roxlo,

Did you try the Edgy installation in the first page of this thread ?

Best,

---

### Post by bamend on 2007-08-13
I tried to install Moblock but I keep on getting this error:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libnetfilter-queue1 0.0.12-1 [6716B]
Fetched 6716B in 0s (15.6kB/s)       
(Reading database ... 155727 files and directories currently installed.)
Removing peerguardnf ...
(Reading database ... 155722 files and directories currently installed.)
Unpacking libnetfilter-queue1 (from .../libnetfilter-queue1_0.0.12-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libnetfilter-queue1_0.0.12-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libnetfilter_queue_libipq.so.1.0.0', which is also in package libnetfilter-queue
Selecting previously deselected package moblock-nfq.
Unpacking moblock-nfq (from .../moblock-nfq_0.8-15_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libnetfilter-queue1_0.0.12-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please help.

---

### Post by jingo811 on 2007-08-14
I tried installing MoBlock on my Dapper 6.06 once it was a living hell.  Until the system crashed on me indefinitely for some other related issue.  Then I reluctantly installed Feisty 7.04 which to my surprise made a bunch of installations very care free.

So I would recommend getting rid of your old Ubuntus and install Feisty after that installing Moblock is only 4 lines in terminal and your done!

---

### Post by jre on 2007-08-14
Hi,

I'm the new maintainer of moblock-deb.sourceforge.net. Since a long time I'm working on the init and update script (the version in the current moblock.deb is based on an early version).

I'm still working on a new release for the repository so that you can simply "aptitude install moblock-nfq" them. I will offer the packages in different flavors (for now etch, lenny and sid, but I'm planning to also compile them for some Ubuntu versions).

I've put a prerelease for direct download on the site. These are the moblock-nfq versions for (links are under the distribution names):

etch (Debian stable; should work on older ubuntu versions, but I don't know how old - probably not on Dapper and before.
[INDENT]dependencys:
libc6 (>= 2.3.6-6)
libnetfilter-queue1 (>= 0.0.12)
libnfnetlink1 (>= 0.0.16)[/INDENT]
lenny (Debian testing; should work on newer ubuntu versions)
sid (Debian unstable; should work on newer ubuntu versions)
[INDENT]dependencys of lenny and sid packages:
libc6 (>= 2.6-1)
libnetfilter-queue1 (>= 0.0.13)
libnfnetlink0 (>= 0.0.25)[/INDENT]

NOTE: These links will only work temporarily - I'll edit this post when something changes.

The packages are signed, so you can do a:
```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -
```

Then, download the package in the correct flavor and do a
```
dpkg -i <packagename>
```

Have a look at the files in /usr/share/doc/moblock-nfq/, especially NEWS.Debian. The scripts changed, everything is done via the new "moblock-control" now.

I'm very interested in test reports ;-)

Last but absolutely not least: A big THANK YOU to clessing who started the project moblock-deb. Unfortunately he hasn't enough time to continue his good work.

jre

EDIT 2007-09-04: Removed links because preview repository is online

---

### Post by sloter on 2007-08-14
Congrats jre and good luck!
Talk to you soon.
sloter

---

### Post by NiksaVel on 2007-08-16
Hey guys...  I've succesfully used moblock for almost a year now and am very happy with this prog...  I do have a little problem, and I don't think I've seen anyone mentioning it here so far:

my moblock seems to get restarted every morning around 0900 hours regardless of the +x or -x property on the /etc/cron.daily/moblock-nfq  I've even tried removing the file completely - made no difference.
As soon as this restart of the moblock process is done, I a load of those skipping duplicate ranges and such messages on screen and the last message in the log is 
ranges loaded xxy...

My internet connection dies completely as of this moment.


The only solution I have found is running manualy
sudo /etc/init.d/moblock-nfq restart


than the reloading ends with
ranges loaded xxy...
NFQUEUE: binding to queue '0'


everything works perfectly than...   


note that in the first "improper" reload I don't get the nfqueue msg...  I am unsure why this is happening, but am getting a bit tired having to manually restart moblock every morning when I get up...   it's annoying.  :confused:


thank you very much in advance if anyone can help me...

---

### Post by phonzie on 2007-08-19
As of now i keep getting the same error when trying to install moblock as root. I added the deb links to sources.list and then did everything else and then : I get the same error as bamend 

¨Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libnetfilter-queue1 0.0.12-1 [6716B]
Fetched 6716B in 0s (15.6kB/s)
(Reading database ... 155727 files and directories currently installed.)
Removing peerguardnf ...
(Reading database ... 155722 files and directories currently installed.)
Unpacking libnetfilter-queue1 (from .../libnetfilter-queue1_0.0.12-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libnetfilter-queue1_0.0.12-1_i386.deb (--unpack):
trying to overwrite `/usr/lib/libnetfilter_queue_libipq.so.1.0.0', which is also in package libnetfilter-queue
Selecting previously deselected package moblock-nfq.
Unpacking moblock-nfq (from .../moblock-nfq_0.8-15_i386.deb) ...
Errors were encountered while processing:
/var/cache/apt/archives/libnetfilter-queue1_0.0.12-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)¨

I think the server is down for moblock. I dont know if that is the problem cuz it get the deb files alright. But then there is a dependency issue. I´m using feisty 7.04

---

### Post by phonzie on 2007-08-19
As of now i keep getting the same error when trying to install moblock as root. I added the deb links to sources.list and then did everything else and then : I get the same error as bamend 

root@Den:~# sudo apt-get install moblock-nfq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
moblock-nfq is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libnetfilter-queue1: Depends: libnfnetlink1 (>= 0.0.16) but it is not going to be installed
  moblock-nfq: Depends: libnfnetlink1 (>= 0.0.16) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@Den:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libnfnetlink1
The following NEW packages will be installed:
  libnfnetlink1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/7582B of archives.
After unpacking 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 116963 files and directories currently installed.)
Unpacking libnfnetlink1 (from .../libnfnetlink1_0.0.16-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libnfnetlink1_0.0.16-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libnfnetlink.so.1.0.0', which is also in package libnfnetlink0
Errors were encountered while processing:
 /var/cache/apt/archives/libnfnetlink1_0.0.16-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

This is after i had done the install already and it gave me what bamend gave and then a dependency error. Is the ANOTHER program cuz i really need something like this supported for linux

I think the server is down for moblock. I dont know if that is the problem cuz it get the deb files alright. But then there is a dependency issue. I´m using feisty 7.04

---

### Post by sloter on 2007-08-19
Hello phonzie,

Did you install peerguardnf before moblock?
In your install log it seems that peerguardnf was installed.
May be try ```
sudo aptitude purge peerguardnf 
```. Be careful this will remove peerguardnf and ll its configuration files...

sloter

---

### Post by jre on 2007-08-19
@NiksaVel: Really strange. Did you ever install some moblock stuff manually? I guess there are some things left that cause your problems.
Search your disk for any moblock files ("find / -name "*moblock*") and check your /etc/crontab for moblock entries.

@phonzie and all those with dependency problems:
Try the packages I posted in [this post]("http://ubuntuforums.org/showpost.php?p=3187264&postcount=580").
These packages have different dependencys (I just added the dependency information in my original post).
For phonzie (on Feisty) I'd suggest the lenny or sid package.

---

### Post by phonzie on 2007-08-19
Actually @slotter I´ve never installed peerguarding this is a brand new installation of feisty fawn 7.04 so im still getting used to it.

I will try your packages in the other post and see if they work, can i just use synaptic to install the dependencies?

I tried to install those depencies like i tried before and i get this error :
E: /var/cache/apt/archives/libnfnetlink1_0.0.16-1_i386.deb: trying to overwrite `/usr/lib/libnfnetlink.so.1.0.0', which is also in package libnfnetlink0

OK i figured it out, i had to install more recent versions of the packages from the Debian packages website. Now it installed the Lenny version. How do i run it?

---

### Post by jre on 2007-08-19
> **phonzie said:**
> OK i figured it out, i had to install more recent versions of the packages from the Debian packages website. Now it installed the Lenny version. How do i run it?
It's running automatically (may be turned off in /etc/moblock/moblock.conf)) but you can control it manually with "moblock-control". Have a look at /usr/share/doc/moblock-nfq/NEWS.Debian.gz.

---

### Post by quixotic-cynic on 2007-08-22
When you have WHITE_TCP_OUT="http https" then if I understand correctly outbound connections on port 80 are possible.

If someone has a bittorrent client with their inbound port set to 80 then connections would therefore still occur - correct?

---

### Post by Dark Star on 2007-08-22
Awesome guide bro :) Keep up the good work ;)

---

### Post by berttt on 2007-08-23
thanks for the sweet How To! I think i got this baby running! no problems so far! :popcorn::popcorn::popcorn::KS:KS:KS

---

### Post by bluecreek on 2007-08-31
For people running hamachi -- by default, moblock will block all traffic from the 5.0.0.0-5.255.255.255 address range.  Do the following to remove the hamachi subnet from the downloaded blocklist:

open the cron file that downloads the new blocklist every day...
```
$ gksudo gedit /etc/cron.daily/moblock-nfq &
```

now add the following down near the bottom of the file, just before the line that reads "mv $PG_LIST $PG_LIST.backup"...
```
# whitelist the hamachi subnet
         grep -v -i "5.0.0.0-5.255.255.255" merged.p2b.p2p > merged.p2b.p2p.tmp
         mv merged.p2b.p2p.tmp merged.p2b.p2p
```

save & close gedit, then update the blocklist & restart moblock...
```
$ sudo /etc/cron.daily/moblock-nfq
$ sudo /etc/init.d/moblock-nfq restart
```

that's it, you're done!

if you want to double-check that the hamachi subnet has been removed from the blocklist...
```
$ grep -i "5.0.0.0-5.255.255.255" "/etc/moblock/guarding.p2p"
```

you should not see any matches for 5.0.0.0-5.255.255.255 in the grep output.

---

### Post by sloter on 2007-08-31
@ quixotic-cynic,

> If someone has a bittorrent client with their inbound port set to 80 then connections would therefore still occur - correct?

Unfortunately, this is correct.

sloter

---

### Post by NiksaVel on 2007-08-31
> @NiksaVel: Really strange. Did you ever install some moblock stuff manually? I guess there are some things left that cause your problems.
Search your disk for any moblock files ("find / -name "*moblock*") and check your /etc/crontab for moblock entries.

here...  hope this makes sense to you :confused:   and no ...  I don't think I've tried any kind of manual installation - strictly whats written in this thread...


```

niksavel@sidious:~$ sudo find / -name "*moblock*"
Password:
/var/run/moblock.pid
/var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_unstable_Release
/var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_unstable_main_binary-i386_Packages
/var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_unstable_main_source_Sources
/var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_unstable_Release.gpg
/var/lib/dpkg/info/moblock-nfq.prerm
/var/lib/dpkg/info/moblock-nfq.list
/var/lib/dpkg/info/moblock-nfq.conffiles
/var/lib/dpkg/info/moblock-nfq.md5sums
/var/lib/dpkg/info/moblock-nfq.postinst
/var/lib/dpkg/info/moblock-nfq.postrm
/var/log/moblock.log
/var/log/moblock.log.1
/var/log/moblock.log.2.gz
/var/log/moblock.log.3.gz
/var/log/moblock.log.4.gz
/var/log/moblock.log.5.gz
/var/spool/moblock
/etc/cron.daily/moblock-nfq
/etc/cron.daily/moblock-nfq~
/etc/init.d/moblock-nfq
/etc/logrotate.d/moblock-nfq
/etc/rc0.d/K20moblock-nfq
/etc/rc1.d/K20moblock-nfq
/etc/rc2.d/S20moblock-nfq
/etc/rc3.d/S20moblock-nfq
/etc/rc4.d/S20moblock-nfq
/etc/rc5.d/S20moblock-nfq
/etc/rc6.d/K20moblock-nfq
/etc/moblock
/home/niksavel/shared/tools/linux/moblock
/home/niksavel/moblock-nfq
/home/niksavel/moblockgui.sh
/usr/bin/moblock-nfq
/usr/bin/moblock
/usr/share/doc/moblock-nfq
/usr/share/man/man1/moblock.1.gz
niksavel@sidious:~$ 


```

---

### Post by antharr on 2007-08-31
> keith@ubuntulappy:~$ tail -f /var/log/moblock.log
Ranges loaded: 235566
Merged ranges: 219
Skipped useless ranges: 5392
NFQUEUE: binding to queue '0'
Blocked OUT: VeriSign Global Registry Services,hits: 1,DST: 199.7.55.74
Blocked OUT: VeriSign Global Registry Services,hits: 2,DST: 199.7.55.74
Blocked OUT: VeriSign Global Registry Services,hits: 3,DST: 199.7.55.74
Blocked OUT: VeriSign Global Registry Services,hits: 4,DST: 199.7.55.74
Blocked IN: Bogon,hits: 1,SRC: 61.253.107.50
Blocked IN: Bogon,hits: 2,SRC: 61.253.107.50


When I used PeerGuardian for XP my number of blocked IP's were somewhere in the millions. 

Now in Moblock I have 235566 ranges blocked. My question is does Moblock block the same IPs as PG. Am I more at risk when using Moblock?

---

### Post by jre on 2007-09-02
@Niksavel: Well, I can only see that you edited /etc/cron.daily/moblock-nfq. But if your problem still occurs when you make it not executable, then this can't cause your problem
Did you check your /etc/crontab for moblock entries?


> **quixotic-cynic said:**
> When you have WHITE_TCP_OUT="http https" then if I understand correctly outbound connections on port 80 are possible.

If someone has a bittorrent client with their inbound port set to 80 then connections would therefore still occur - correct?

With "WHITE_TCP_**OUT**="http https"" you will only loose your protection when **you** initiate the connection, but not when another machine wants to connect to you (neither on port 80 or on another port).
I don't think that "**in**bound port set to 80" means that your **outgoing** traffic is also going over port 80 - but I think this might depend on your bittorrent client.


> **antharr said:**
> When I used PeerGuardian for XP my number of blocked IP's were somewhere in the millions. 

Now in Moblock I have 235566 ranges blocked. My question is does Moblock block the same IPs as PG. Am I more at risk when using Moblock?
A range consists of many single IPs. In it's standard configuration the moblock deb blocks the same lists as PG Windows (without the edu list) and some additonal ones.

Greets
jre

---

### Post by quixotic-cynic on 2007-09-03
Thanks for the replies about whitelisting port 80...

> **jre said:**
> @Niksavel: 
With "WHITE_TCP_**OUT**="http https"" you will only loose your protection when **you** initiate the connection, but not when another machine wants to connect to you (neither on port 80 or on another port).
I don't think that "**in**bound port set to 80" means that your **outgoing** traffic is also going over port 80 - but I think this might depend on your bittorrent client.


What about when other users set their inbound port as 80? Sending a packet to them is no different from an outbound packet from your machine to an http server listening on port 80 - so you have a hole in your protection. (WHITE_TCP_OUT="http https" means allow connections to xxx.xxx.xxx.xxx:80 and xxx.xxx.xxx.xxx:443 - adversaries just have to set their p2p client to accept connections on one of these ports and you have no protection).

It is such an obvious hole (for potential adversaries at any rate) that I would think anyone 'interested' would set their incomming port to 80 and you effectively get  no more moblock protection using the default configuration.

This is simmilar to PG2's "allow http" which they reccomend you do not use for exactly the same reason. See [here]("http://wiki.phoenixlabs.org/wiki/PeerGuardian_2:FAQ#Should_I_keep_.22http_blocked.22_at_all_times.3F"), [here]("http://wiki.phoenixlabs.org/wiki/PeerGuardian_2:FAQ#Is_it_safe_to_turn_off_the_.22Block_HTTP.22_option.3F") and [here]("http://wiki.phoenixlabs.org/wiki/PeerGuardian_2:FAQ#PeerGuardian_is_blocking_my_favourite_site.21_How_do_I_unblock_it.3F")  in the PG2 FAQ. [This part]("http://wiki.phoenixlabs.org/wiki/PeerGuardian_2:Manual#Solution_1:_Allow_All_Webpages_.28Unblock_HTTP.29") in the manual also seems relevant.

---

### Post by pelle.k on 2007-09-03
> That is certainly true. However, what about when other users set inbound port as 80... sending a packet to them is no different from an outbound packet from your machine to an http server listening on port 80 - so you have a hole in your protection. (WHITE_TCP_OUT="http https" means allow connections to xxx.xxx.xxx.xxx:80 and xxx.xxx.xxx.xxx:443 - adversaries just have to set their p2p client to accept connections on one of these ports and you have no protection).

It is such an obvious hole that I would think anyone 'interested' would set their incomming port to 80 and you effectively get no more moblock protection using the default configuration.

I'm _not_ quite sure i understand how you mean, but in either case moblock is not a firewall. Of course you're gonna have a hole in your protection, just as any really functional wall acctually has a door (port)...
If you then set your p2p client to port 80 that is still for incoming connections, so in essence your examaple has no effect in reality.

Maybe you should read up on iptables, and in particular the different "states" a connection can have.

---

### Post by pt123 on 2007-09-03
Is it possible to have another list of IPs that you can manually add to so they want get overwritten when guarding.p2p file gets updated.

It is just I want to ban IP address that don't share.

---

### Post by quixotic-cynic on 2007-09-03
> **pt123 said:**
> Is it possible to have another list of IPs that you can manually add to so they want get overwritten when guarding.p2p file gets updated.

It is just I want to ban IP address that don't share.

[removed redundant section]

That said, the templist provided by bluetack allready attempts to block people reported for misdemenours so you could just find out how entries are added to the templist and report people you have a problem with to the appropriate place on the bluetack.co.uk website...

I am sorry that I cannot help more but I hope that some of that helps.

EDIT: BETTER IDEA

Use cat (type "man cat" in a terminal for the manual). See below for details.

Put two lines in /etc/cron.daily/moblock-nfq near line 100 - after the commented lines where it says "# uncomment below to unblock Yahoo! Mail and whatever" but *before* mv $PG_LIST $PG_LIST.backup.

You are doing a simmilar thing to unblocking but you are adding stuff - the lines need to be approximately as follows:

cat merged.p2b.p2p yourblockfile.txt > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p

This merges your block file with the one that has just been gererated from the download. It then overwrites the generated block file with the new one with your lies included.

YAY! (I had no idea I could work out stuff like that properly) ;)   Let people know if there is a problem with it - if I see I will try again - but it really should work I think.

Credit to pelle.k for his "What about filtering out some stuff i wan't to connect to?" that gave me the idea.

---

### Post by quixotic-cynic on 2007-09-03
> **pelle.k said:**
> I'm _not_ quite sure i understand how you mean, ...

Ok, that is not reassuring for me considering you wrote such a useful thread - I really did think I understood this somewhat... now I am worried my question may not even make sense??!?

> **pelle.k said:**
>  ...but in either case moblock is not a firewall. 

Understood.

> **pelle.k said:**
> Of course you're gonna have a hole in your protection, just as any really functional wall acctually has a door (port)...

I understand that you need ports open for any net-facing program to work. What concerns me it that by allowing connections from the local computer to port 80 or 443 on another computer then you actually have an issue with your moblock protection (not in a firewall sense). AFAIK you dont *need* a hole in you moblock protection, unlike with a firewall - you just have to put up with a few blocked sites (which is a bit of a pain).

> **pelle.k said:**
> If you then set your p2p client to port 80 that is still for incoming connections, so in essence your examaple has no effect in reality.

In one of my previous posts I wrote *when you have WHITE_TCP_OUT="http https" then if I understand correctly outbound connections on port 80 are possible.* I have not been talking about incomming connections at all. I am sorry if I am unable to write with a sufficient degree of clarity, I am doing my best.

> **pelle.k said:**
> Maybe you should read up on iptables, and in particular the different "states" a connection can have.

You are probably correct - it is a good suggestion. As far as I know, with TCP in general, you can have 'open connection' packets with RST header bits to open a connection and ACK header bits in all other TCP packets. Packets can be sent outbound or inbound. So, WHITE_TCP_OUT="80" would allow open connection packets out, and normal packets out and in on the same connection, but would not allow open connection requests from outside. My questions above are directed from this particular understanding so if it is wrong my question could be mis-directed, and if right then vice versa.

I will do some more iptables reading since I am used to routers, kerio and kaspersy...

--QC

---

### Post by pelle.k on 2007-09-03
Oh, don't worry if I don't get what you mean. After all, english isn't my first language... ;)
So, can i take a guess at what you mean is that;
You are worried that traffic from, say a BT download, could sneak through by answering another peer at port 80?

I guess that is unlikely, but not impossible. The rules moblock create are just a default set, and you are encouraged to adjust them to your liking. In fact, moblock states it is a utility for advanced users in the first place.

I guess you could adjust the rules inserted by moblock to whitelist_out port 80, but _not_ if "sport" is in a range used internally by your BT client (or whatever software we speak about...)
See? It's all in the rules inserted by moblock, primarily.

---

### Post by quixotic-cynic on 2007-09-03
Yes, that was what I was going on about  ^_^

It sound like it's possible to do more stuff than I thought with the config file so I will mess around with it a bit and see what I can do. 

Thanks for the useful reply.

--QC

---

### Post by pt123 on 2007-09-04
> **quixotic-cynic said:**
> [removed redundant section]

cat merged.p2b.p2p yourblockfile.txt > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p

Credit to pelle.k for his "What about filtering out some stuff i wan't to connect to?" that gave me the idea.

Thanks I will try this.

---

### Post by jre on 2007-09-04
> **pelle.k said:**
> I guess you could adjust the rules inserted by moblock to whitelist_out port 80, but _not_ if "sport" is in a range used internally by your BT client (or whatever software we speak about...)
See? It's all in the rules inserted by moblock, primarily.

sport? did you mean dport!?

Anyway, if anybody has an practical way of doing this, then please post it! Personally I don't know a way how to use iptables rules on an application basis. The cleanest solution would be to only whitelist TCP out on port 80 for e.g. the webbrowser.
But anyway, I will change the default to no whitelisting. Sorry for all the users who will come here and ask why they can't surf or who will even not use moblock at all.

greets
jre

---

### Post by sloter on 2007-09-04
Hello,

Yes it could be excellent. I am currently reading some interesting netfilter documentation that may help
[http://www.netfilter.org/documentation/index.html#documentation-howto]("http://www.netfilter.org/documentation/index.html#documentation-howto")

sloter

---

### Post by quixotic-cynic on 2007-09-04
Reply CCd from [here.]("http://forums.phoenixlabs.org/showthread.php?p=107502&posted=1#post107502")

Thanks for taking the point seriously jre. 

Changing the default may be excessive (perhaps?) since, as you say, some people may just give up etc. It is up to you as to what you choose to do about it.

An alternative could be to make people aware of the issue - and then they could choose whether it is an acceptable 'risk' or not.

If you do choose to change the default (or even if you dont) I will try to lurk around the PG and Ubuntu forum pages to help newbies. I am fairly new to linux (a few weeks) so am looking for somewhere I can contribute. Since I am quite paranoid this may be a good place to start... ;)
___
@sloter: thanks for the link, i'm sure it will be good reading.

---

### Post by jre on 2007-09-04
I put a preview repository at moblock-deb.sourceforge.net/preview/debian

So just get my gpg key (see [this post]("http://ubuntuforums.org/showpost.php?p=3187264&postcount=580")) and add the following lines to your /etc/apt/sources.list:
Debian etch (stable):
```
deb [http://moblock-deb.sourceforge.net/preview/debian](http://moblock-deb.sourceforge.net/preview/debian) etch main
deb-src [http://moblock-deb.sourceforge.net/preview/debian](http://moblock-deb.sourceforge.net/preview/debian) etch main
```

Debian lenny (testing):
```
deb [http://moblock-deb.sourceforge.net/preview/debian](http://moblock-deb.sourceforge.net/preview/debian) lenny main
deb-src [http://moblock-deb.sourceforge.net/preview/debian](http://moblock-deb.sourceforge.net/preview/debian) lenny main
```

Debian sid (unstable):
```
deb [http://moblock-deb.sourceforge.net/preview/debian](http://moblock-deb.sourceforge.net/preview/debian) sid main
deb-src [http://moblock-deb.sourceforge.net/preview/debian](http://moblock-deb.sourceforge.net/preview/debian) sid main
```

Then you can easily install "moblock-nfq" (or "moblock-ipq")

Most important changes to the old debian packages from moblock-deb.sf.net:
moblock-control (see thread at forums.phoenixlabs.org, this implies many changes)
sloter's new man page
sloter's test function
NO port whitelisting (have a look at /etc/moblock/moblock.conf for this)

major TODOs:
Ubuntu packages (at least feisty and gutsy)
documentation updates

With these things done the repository will move to the old position (without the "preview" in the URL).

Feedback (including on which distribution you are) is very welcome!
You can have a look at the actual files at [http://moblock-deb.svn.sourceforge.net/](http://moblock-deb.svn.sourceforge.net/). Patches are always appreciated ;-)

Greets
jre

---

### Post by pelle.k on 2007-09-04
> Anyway, if anybody has an practical way of doing this, then please post it! Personally I don't know a way how to use iptables rules on an application basis. The cleanest solution would be to only whitelist TCP out on port 80 for e.g. the webbrowser.
But anyway, I will change the default to no whitelisting. Sorry for all the users who will come here and ask why they can't surf or who will even not use moblock at all.
I hope you know how much we appreciate you work jre. My exmaple was just an idea, and i have not evaluated if this could be done at all _in reality_, because i have never felt the need to do this.
Either way, the point was only to show that moblock does the filtering; iptables does the traffic redirection :)

Let me point out that i am by no means an iptables guru.

Oh, and please do tell me when, and if, i need to update the howto to reflect any recent changes that will be more or less permanent from now on. :D

---

### Post by jre on 2007-09-04
> **pelle.k said:**
> Oh, and please do tell me when, and if, i need to update the howto to reflect any recent changes that will be more or less permanent from now on. :D
Most things that will be permanent are already in the preview repository.
With the updated documentation I think you can easily change the howto.
Also, with special ubuntu packages the howto whould get much shorter ;-)
If you want I can announce the change of the official repository let's say 2 days in advance here and at forums.phoenixlabs.org.

Greets!!
jre

---

### Post by pelle.k on 2007-09-04
> But anyway, I will change the default to no whitelisting. Sorry for all the users who will come here and ask why they can't surf or who will even not use moblock at all.
I dont want to be a pain in the ***, but i think the best thing would be to leave http and https whitelisted, since the arguments against it are rather small, and i also think quixotic-cynic only wanted to confirm his theory, and not argue against whitelisting really.
In the end, i'll notify people of what to do about it ( in the FAQ), whatever you decide to set as default behaviour.

> If you want I can announce the change of the official repository let's say 2 days in advance here and at forums.phoenixlabs.org.

Yeah, that would be great :)

---

### Post by Zeikcied on 2007-09-05
Any idea when the Ubuntu packages will be made available?

Also, will this new version still use the file in /etc/cron.d?  I ended up deleting that, with the hope that reinstalling Moblock would add a more updated one in it's place (I've found that if I edit a file, dpkg may not replace it when installing a new version).  But it didn't.  Though, I'm using the regular repositories listed on the first page of this thread, so I don't know what is actually there.

I do have a version of Moblock running (the one from the current repositories), but I don't know if it's updating the filters at all.

---

### Post by sloter on 2007-09-05
@Zeikcied,

One way you can do to check if the blocking lists are updated is to check the creation date of the lists in /var/spool/moblock.
```
ls -la /var/spool/moblock
```

Also, when you reinstall a package previously installed use some --force or I don't know exactly with apt-get or aptitude or whatever package installer you use. That should allow you to reinstall the configuration files such as the cron.d... I guess

Thank you,

---

### Post by quixotic-cynic on 2007-09-05
For people who are really worried about the whitelisting issue and are using moblock primarily for the level1 list - if you just use that list and turn off whitelisting then not many sites are blocked. For those that are, as a get-around, you can use [www.ecoproxy.com](www.ecoproxy.com) or any other web proxy... (obviously dont trust them for secure stuff).

---

### Post by jre on 2007-09-05
Whitelisting port 80 and 443 per default:
Pro:
- Most people will do this anyway
- Security risk not very big

Contra:
- Security risk does exist
- I've sometimes seen the question: "I still can surf to riaa.com! Why doesn't moblock work?"
- Upstream doesn't have per default whitelisting
- Users should at least be so experienced that they are ready to read the documentation.
- It's very easy to turn whitelisting on; I just commented out the line in moblock.conf.
- People running moblock not on their normal desktop machine don't want whitelisting

So, for now I think it's better to start with no whitelisting and just document this fact well. Most people will have no problem to change this behaviour - I hope so ;-)
If it causes to many troubles I can change it back on again.


Ubuntu packages:
when their ready ;-) Perhaps today, perhaps this week, in the worst case never - I'm on it.

/etc/cron.daily/moblock-nfq
does exist. If you don't want the daily updates you can now turn them off in moblock.conf - no need to do anything with this cron file.
In theory this file is not a conf-file so apt should just install a new version (I have to look into this, I'm not absolutely sure).
 If I understood you correctly, Zeikcied, then this didn't work for you. So try "aptitude reinstall moblock-nfq" or even "aptitude purge moblock-nfq" and then "aptitude install moblock-nfq".
EDIT: well I tested it and the only way to get it back was to purge and install. I **think** apt will only look for user changes in real conf files and will then prompt what to do. Since the cron file is no conf file apt "knows" falsely that this file was not changed and so doesn't reinstall it. I think this is the normal behaviour in Debian so I won't change that.
Does the cron file come back when you upgrade from 0.8-15 to 0.8-16 (from the preview repository)?

Greets
jre

---

### Post by Zeikcied on 2007-09-05
> **sloter said:**
> @Zeikcied,

One way you can do to check if the blocking lists are updated is to check the creation date of the lists in /var/spool/moblock.
```
ls -la /var/spool/moblock
```

Also, when you reinstall a package previously installed use some --force or I don't know exactly with apt-get or aptitude or whatever package installer you use. That should allow you to reinstall the configuration files such as the cron.d... I guess

Thank you,
I did that, and the dates were from back in December 2006.  So...it hasn't been updated since?

Anyway, I did apt-get remove --purge, and then installed it again, and updated it manually.  So, all the lists have been updated, and the cron.daily script is back.  Hopefully it works now.

Also, I haven't used the preview repository yet.  I'd rather wait until official Ubuntu packages are made.  I don't want any possible conflicts between Debian and Ubuntu packages, even if there may not be any.  Just to be safe.

---

### Post by pelle.k on 2007-09-05
> In theory this file is not a conf-file so apt should just install a new version 
Oh, and speaking of that. Waaay back when clessing was maintaining moblock, i asked him if he could source config files in to the scripts, so that you wouldn't have to mess with the actual scripts in order to change settings. This could be an idea for the final version.
This could also be useful for storing regex patterns (in a flat text file/s) for the update function. As it is now, people have to get down and dirty and watch out for syntax errors when doing these kind of manouvers...

just brainstorming here :)

---

### Post by jre on 2007-09-05
Yay, **Ubuntu Feisty** support added!
Just add these lines to your sources.list if you're running feisty:
```
deb http://moblock-deb.sourceforge.net/preview/debian feisty main
deb-src http://moblock-deb.sourceforge.net/preview/debian feisty main

``` and add my key (see some posts above).

Gutsy seems to be broken at the moment, I'll look at that later.

> **pelle.k said:**
> Oh, and speaking of that. Waaay back when clessing was maintaining moblock, i asked him if he could source config files in to the scripts, so that you wouldn't have to mess with the actual scripts in order to change settings. This could be an idea for the final version.
Well, already done ;-)
Settings are made in /etc/moblock/moblock.conf and /etc/moblock/blocklists.list.
These configuration files are sourced by /usr/bin/moblock-control.
moblock-control offers start, stop, restart, reload, status, test and update.
The cron and init files first check moblock.conf if they shall run and if yes they source moblock-control (with start (init) or update (cron)).

[QUOTE=Zeikcied]
Also, I haven't used the preview repository yet. I'd rather wait until official Ubuntu packages are made. I don't want any possible conflicts between Debian and Ubuntu packages, even if there may not be any. Just to be safe.[/QUOTE]
Oh, I always forget these dependency problems because I'm not running ubuntu :-) But you might try it now. Of course as always: absolutely no warranty, I can't even test the ubuntu packages. Test reports are always welcome.

jre

PS. Pelle, don't worry, I won't change the repository before I've updated the documentation.

---

### Post by Zeikcied on 2007-09-07
I just noticed that Moblock is blocking my email.

My ISP (AT&T Yahoo DSL) switched the POP/SMTP settings to non-standard ports.  And for whatever reason, the IP range used by the mail sub-domain names is blocked.

I tried adding one of the IPs to "TCP_WHITE_OUT" or whatever it is, in /etc/moblock/MoBlock-nfq.sh, and it doesn't seem to work.  I'm using the version for Ubuntu Feisty in the regular repository (not the preview repository), if that makes any difference.  The log says that the IPs are from Inktomi Corporation, which I've never heard of before.  I turned off MoBlock, and I could send and receive my email perfectly fine.

Is there a way to simply whitelist by domain name instead of IP address?  Or would I have to somehow find the full range that those domains use?  (A GUI would really help with configuration problems such as this.)

---

### Post by quixotic-cynic on 2007-09-07
> **Zeikcied said:**
> I just noticed that Moblock is blocking my email.

I tried adding one of the IPs to "TCP_WHITE_OUT" or whatever it is, in /etc/moblock/MoBlock-nfq.sh, and it doesn't seem to work.

This part from the first post is what you want:

> **What about filtering out some stuff i wan't to connect to?**

If you want to whitelist ip ranges then do it in cleartext in /etc/cron.daily/moblock-nfq at line 114 (at the end of the file).
Remove the two # which makes it commented out. add names of ip ranges from the guarding.p2p file. like this;
Code:

       grep -v -i "whatever" merged.p2b.p2p | grep -v -i "whatever2" | grep -v "whatever3" > merged.p2b.p2p.tmp
        mv merged.p2b.p2p.tmp merged.p2b.p2p

-v means invert-match (so you get everything _but_ the search phrase. this has to be there.
-i means ignore-case, that is; "WhateveR" and "whatever" is both a match.

So what you have to do is check /var/log/moblock.log for the name of the range causing the problem and then replace whatever with the name of the range causing the problem.

 **EG:**

To edit the file open a terminal and enter *sudo gedit /etc/cron.daily/moblock-nfq* where gedit is the name of your text editor (others include nano, mousepad etc). *sudo* gives the text editor proceeding it the rights required to edit a file in the root-owned /etc/ directory.

Add these two lines where instructed in the above:

grep -v -i "my_mail_service" merged.p2b.p2p > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p

...where my_mail_service is the name of the IP range that shows up in you log file.

What it does: 
1) keeps all the lines except the ones you list 
2) [> this bit] ouptuts the modified file to a temp file.
3) The temp file is then moved [mv] over the orginal file generated from the blocklist sources. 
4) After this the blocklist is written out to it's  location where it is actually used.

A GUI might save a bit of time but it is actually a lot more simple than it would first appear (the start of this thread by pelle.k is a lifesaver ;) )

---

### Post by Zeikcied on 2007-09-07
> **quixotic-cynic said:**
> This part from the first post is what you want:



So what you have to do is check /var/log/moblock.log for the name of the range causing the problem and then replace whatever with the name of the range causing the problem.

 **EG:**

To edit the file open a terminal and enter *sudo gedit /etc/cron.daily/moblock-nfq* where gedit is the name of your text editor (others include nano, mousepad etc). *sudo* gives the text editor proceeding it the rights required to edit a file in the root-owned /etc/ directory.

Add these two lines where instructed in the above:

grep -v -i "my_mail_service" merged.p2b.p2p > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p

...where my_mail_service is the name of the IP range that shows up in you log file.

What it does: 
1) keeps all the lines except the ones you list 
2) [> this bit] ouptuts the modified file to a temp file.
3) The temp file is then moved [mv] over the orginal file generated from the blocklist sources. 
4) After this the blocklist is written out to it's  location where it is actually used.

A GUI might save a bit of time but it is actually a lot more simple than it would first appear (the start of this thread by pelle.k is a lifesaver ;) )
I saw that in the first post (which I looked over before replying with my problem) and I really couldn't make sense of that part.  Thanks for making it a bit more clear for me.

I've only been using Linux, exclusively, since December of last year.  While that seems like a long time, I've not actually had a lot of practice with the more advanced (in my opinion) stuff, like grep and all that.  I took classes on Linux, I read a book on Red Hat 9 years ago, so I know various things like piping and pushing the results of a query to a file, but I've not had to really use any of that since I started using Kubuntu in December.

(Plus, years of Windows use has had me rely on GUI apps too much, I guess.  I've become a lot more comfortable with the command line, but I can get easily confused.)

Again, thanks :)

---

### Post by floogy on 2007-09-08
> **jre said:**
> Whitelisting port 80 and 443 per default:
Pro:
- Most people will do this anyway
- Security risk not very big

Contra:
- Security risk does exist
- I've sometimes seen the question: "I still can surf to riaa.com! Why doesn't moblock work?"
- Upstream doesn't have per default whitelisting
- Users should at least be so experienced that they are ready to read the documentation.
- It's very easy to turn whitelisting on; I just commented out the line in moblock.conf.
- People running moblock not on their normal desktop machine don't want whitelisting

So, for now I think it's better to start with no whitelisting and just document this fact well. Most people will have no problem to change this behaviour - I hope so ;-)
If it causes to many troubles I can change it back on again.


I'm using the unofficial amd64 packages for feisty.
Often I got Problems to resolve google.com. Therefor I added to my /etc/moblock/MoBlock-ipq.sh this:
```
WHITE_TCP_OUT="http https"
WHITE_UDP_OUT="53"
```

```
$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
MOBLOCK_IN  0    --  anywhere             anywhere            state NEW 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
MOBLOCK_FW  0    --  anywhere             anywhere            state NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
MOBLOCK_OUT  0    --  anywhere             anywhere            state NEW 

Chain MOBLOCK_FW (1 references)
target     prot opt source               destination         
QUEUE      0    --  anywhere             anywhere            

Chain MOBLOCK_IN (1 references)
target     prot opt source               destination         
QUEUE      0    --  anywhere             anywhere            

Chain MOBLOCK_OUT (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
QUEUE      0    --  anywhere             anywhere   

```

Now I can surf almost any where I want to.

What are the downsides? Is this compareable secure like using only this?
```
WHITE_TCP_OUT="http https"
WHITE_UDP_OUT=""
```

```
$ ping -c1 microsoft.com
PING microsoft.com (207.46.197.32) 56(84) bytes of data.

--- microsoft.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

```

Results in:
```

Blocked OUT: Microsoft Corp,hits: 3,DST: 207.46.197.32

```

What is the meaning of this output? (useless ranges)
```
Skipping useless range: Fastsearch[Spy]
Skipping useless range: 80ke.com
Ranges loaded: 230261
Merged ranges: 188
Skipped useless ranges: 5131
```
Is that ok?

---

### Post by quixotic-cynic on 2007-09-08
> **Zeikcied said:**
> Thanks for making it a bit more clear for me.

I am happy it helped. I always think about that give [a man a fish / teach a man to fish] thing -- you can just say 'type this stuff and it will work' but in the long run that is tacky since you end up with loads of perma-newbies (& then some elitist people moan about it when they are usually the ones who exacerbate the problem :) ).

---

### Post by quixotic-cynic on 2007-09-08
> **floogy said:**
>  What are the downsides? Is this compareable secure like using only this? 

What programs are you using moblock for? If it is a p2p app that can be configured to accept incomming connections on port 80 then someone could run their app on port 80 and your p2p client would connect to them since adding http whitelists port 80... that is the risk. You have to decide whether it is acceptable to you or not.

The ping and skipping useless ranges looks normal - it is to be expected. I'm not 100% sure what the useless ranges actually are, but it might have something to do with lines that have an invalid layout... (?)

You don't need to whitelist your DNS port (53) unless your specific DNS server IPs are being blocked by moblock. This is highly unlikely so don't bother whitelisitng port 53 unless you cant connect to *any* site (it will either work 100% or block all sites).

---

### Post by Zeikcied on 2007-09-08
> **quixotic-cynic said:**
> I am happy it helped. I always think about that give [a man a fish / teach a man to fish] thing -- you can just say 'type this stuff and it will work' but in the long run that is tacky since you end up with loads of perma-newbies (& then some elitist people moan about it when they are usually the ones who exacerbate the problem :) ).
That's always a good way to go about it.

My main point of confusion was this part:

> grep -v -i "whatever" merged.p2b.p2p | grep -v -i "whatever2" | grep -v "whatever3" > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p

I see the series of grep commands, all piped together, and I'm thinking I need to use them all.  I guess it's like that to demonstrate how to whitelist several ranges at once.  But it confused me.

I'm not entirely a newbie, but it is nice to have some help along the way.

---

### Post by uljanow on 2007-09-08
> **Zeikcied said:**
> I see the series of grep commands, all piped together, and I'm thinking I need to use them all.  I guess it's like that to demonstrate how to whitelist several ranges at once.  But it confused me.
Lazy people would use egrep for that purpose.
```
egrep -iv "whatever1|whatever2|whatever3" merged.p2b.p2p > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p
```

---

### Post by floogy on 2007-09-09
```
merged.p2b.p2p > merged.p2b.p2p.tmp
mv merged.p2b.p2p.tmp merged.p2b.p2p
```
Can one use "tee" to cleanup this part of the code? 
```
merged.p2b.p2p |tee merged.p2b.p2p
```
I'm not sure about that, though.
This would result in this oneliner:
```
egrep -iv "whatever1|whatever2|whatever3" merged.p2b.p2p|tee merged.p2b.p2p
```

---

### Post by jre on 2007-09-09
> **Zeikcied said:**
> I'm using the version for Ubuntu Feisty in the regular repository (not the preview repository), if that makes any difference.
Err, there's no version for Feisty in the official (not preview) repository.

Note that nothing is "official", it's just a private project started by clessing who is not the moblock author. But well, this might be hairsplitting.

**Suggestions for improvements**: I really appreciate those suggestions, but please note that I have changed the scripts very much - so please first have a look at the new "moblock-control" from the preview repository.
The IP remove part has the following part there:
```
[ -z "$IP_REMOVE" ] || {
# Delete lines from the blocklist:
IFS=";"
for XIP in $IP_REMOVE ; do
    grep -v -i $XIP merged.blocklist > merged.blocklist.tmp || { log_failure_msg " failed!"; exit 1; }
    mv merged.blocklist.tmp merged.blocklist || { log_failure_msg " failed!"; exit 1; }
done
IFS=$STDIFS
}
log_end_msg $?
```
I admit that this is no one-liner :-)
But all that users have to do is to change in /etc/moblock/moblock.conf (the configuration file for moblock-control) this line:
```
IP_REMOVE=""
```
There they can place a ";"-seperated list of the lines that they want to remove from their guarding.p2p.
Feel free to send me suggestions how to make this better/nicer/shorter/...

BTW: There's also another option in moblock-control to directly whitelist IPs with iptables. This is done very similar to the port whitelisting that is already present in the current old script.

The **"skipping useless range"** is because you sometimes find lines like the following which contain only one IP in their range:
```
(050418) Unassigned 33437:208.42.224.236-208.42.224.236
```. But if you look through your whole guarding.p2p then you will find this line which already contains this IP.
```
Data393 Inc:208.42.224.0-208.42.237.223
```. This is why the useless first range is skipped. Note, that I haven't read the code, but it just has to be so :-)

Oh, any **feedback** for the preview repository?

greets
jre

---

### Post by jre on 2007-09-09
I did work around the currently broken Ubuntu Gutsy base files. So here they are: moblock debs for **Ubuntu Gutsy**. Just add these lines to your /etc/apt/sources.list:
```
deb [http://moblock-deb.sourceforge.net/preview/debian](http://moblock-deb.sourceforge.net/preview/debian) gutsy main
deb-src [http://moblock-deb.sourceforge.net/preview/debian](http://moblock-deb.sourceforge.net/preview/debian) gutsy main
``` and add my GPG key (see above) if you haven't done so already.

Currently I'm not going to make Ubuntu Edgy, Dapper or {even earlier distro} packets because they miss the netfilter libraries. If someone needs them I might look into it.

Feedback is still very welcome :-) Please always tell me what distro your using.

jre

---

### Post by Zeikcied on 2007-09-11
> **jre said:**
> Err, there's no version for Feisty in the official (not preview) repository.

greets
jre
There isn't?

Then I guess I'm using the Edgy packages.  I didn't actually check Adept to see which repositories it's using for Moblock.  *checks*  Wow.  So I've been using the Debian packages.  That's interesting.  (You can tell I don't often look back on this stuff.)

Well...okay then.  Heh. :oops:

---

### Post by quixotic-cynic on 2007-09-14
Previously I have been using the etch package. I just tried to use the packages from [http://moblock-deb.sourceforge.net/preview/debian/dists/feisty/main/binary-i386/net/](http://moblock-deb.sourceforge.net/preview/debian/dists/feisty/main/binary-i386/net/) (on feisty... ;) ) and I am getting problems when using either of them.

The nfq version doesn't seem to be blocking anymore (I tried installing the later version because of a dependency problem that kept driving me nuts when using aptitude) and I get a dependency problem.

If someone can explain how the hell I copy text from urxvt I would paste the output here (selecting it doesn't seem to copy) [resolved].

Edit: Ok, I went back to the -13 version at the start of the thread. It appears that I need to install libnfnetlink1 but the package won't install - it complains about trying to overwrite /usr/lib/libnfnetlink.so.1.0.0 which is also in package libnfnetlink0. [Incidentally, it does actually work like this still, it is just a real pain every time I want to add or remove a package with aptitude]

---

### Post by pelle.k on 2007-09-14
mark text -> paste with third mousebutton (wheel).
this is standard "behaviour" in X.

---

### Post by quixotic-cynic on 2007-09-14
Thanks, I sort of knew that but was trying to cut with the x method then use the paste button in nedit -- I was unaware that would not work.

Edit: I re-broke it by upgrading to -17 and here is the output:

```
corcorigan@deidre:~/package/nfq$ sudo dpkg -i *.deb
Selecting previously deselected package moblock-nfq.
(Reading database ... 93433 files and directories currently installed.)
Unpacking moblock-nfq (from moblock-nfq_0.8-17+feisty_i386.deb) ...
dpkg: dependency problems prevent configuration of moblock-nfq:
 moblock-nfq depends on libnfnetlink1 (>= 0.0.16); however:
  Package libnfnetlink1 is not installed.
dpkg: error processing moblock-nfq (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 moblock-nfq
```

EDIT: Removed part to shorten post - see below for resolution - (when trying to install libnfnetlink1make sure libnfnetlink0 is not installed).

---

### Post by jre on 2007-09-14
quixotic-cynic
In feisty there is libnfnetlink1 (0.0.16-1) in the "universe" section. So there should be no dependency problems.
Why is libnfnetlink0 installed on your machine? Go to aptitude to libnfnetlink and press "r" to see which installed package depends on this.
If it's only moblock-nfq then just uninstall moblock-... and libnfnetlink and then install moblock-nfq (0.8-17). I'm surprised that this doen't work automatically, but i don't know what to do.

Tell me if this worked and if moblock is blocking again. If not, then we have a problem ... :-/

Thanks for telling me that. That's a point for the howto!

pelle.k: i'd like to change the repository on sunday although i'm still late with updating the documentation (0.8-18 with some minor improvements is soon to come). have a look at the man page, NEWS.Debian, moblock.conf and blocklists.list.
tell me if you need to know something, i'll wait for your and quixotic-cynic's ok before moving the repository. thanks!

---

### Post by quixotic-cynic on 2007-09-14
jre,

Thanks for replying. I just decided to try again. I removed the moblock package (& checked in aptitude) then installed moblock-nfq_0.8-17+feisty_i386.deb using dpkg. I then went into aptitude, pressed 'g' and got the dependencies. 

Nothing I haven't tried before but this time IT WORKED! May have been a different permutation - or previously some stuff may have been left from an old install?

I still got the error message when trying to install libnfnetlink1- this truned out to be because libnfnetlink0 was still installed and occupied the area that libnfnetlink1 wanted to install to. So, to sum up, if people have problems installing between 0.8-13 and 0.8-17 make sure you *remove libnfnetlink0 as well as moblock-nfq.* (Or you look stupid like me... heh).

Thanks for you help - useful to know exactly what I needed. To explain the 'manual' install - I don't like adding pgp keys that I am unable to verfify properly (I have nothing against your *actual* key...) - you know i'm paranoid. ;)

EDIT: *looks in /etc/...*  Nice script revamp!!! :D

EDIT2: Yes, it's definitely blocking. I find the ping test a little shakey since some of the ip ranges don't reply to pings no matter whether moblock is on or off. However, it passed the ping test as well as using [http://www.advfilms.co.uk/](http://www.advfilms.co.uk/) as a test... a useful indicator when combined with a log check (it's in one of the block ranges).

---

### Post by jre on 2007-09-14
I'm currently updating the new homepage: [http://moblock-deb.sourceforge.net/preview/](http://moblock-deb.sourceforge.net/preview/). As always, feedback, suggestions etc. is welcome. I'm not a native speaker.

> **quixotic-cynic said:**
> I find the ping test a little shakey since some of the ip ranges don't reply to pings no matter whether moblock is on or off. However, it passed the ping test as well as using [http://www.advfilms.co.uk/](http://www.advfilms.co.uk/) as a test... a useful indicator when combined with a log check (it's in one of the block ranges).
moblock-test pings the first IP in the blocklist and then checks via /var/log/moblock.log if the IP was blocked by moblock. So no need to worry if the test IP would have responded. But look at the current TODO in the svn, this needs to be improved (greets, sloter :-) ).

---

### Post by quixotic-cynic on 2007-09-15
> **jre said:**
> moblock-test pings the first IP in the blocklist and then checks via /var/log/moblock.log if the IP was blocked by moblock.

Ah, that's good - as you say, it doesn't really matter if the target would have replied or not...

---

### Post by mak123 on 2007-09-16
In my /etc/moblock/blocklists.list file, some of the URLs for blocklists have a "#" at the start of the line.

What does that mean?

Thanks!  (It's really bugging me.  Like, are those URLs not loaded or something?)

---

### Post by Rasitiln on 2007-09-16
Thanks for the tutorial.

---

### Post by jre on 2007-09-16
> **mak123 said:**
> In my /etc/moblock/blocklists.list file, some of the URLs for blocklists have a "#" at the start of the line.
Yes, these lines are commented out. So they are not used. They are just there as examples.

Another example are these two lines in /etc/moblock/moblock.conf:
```
WHITE_TCP_OUT=""
#WHITE_TCP_OUT="http https"
```
Here, only the first line is used (no port-whitelisting). When you remove the "#" in the second line and add it in the first line, then you will have whitelisted the http/www (80) and https (443) port for outgoing TCP connections.

Thanks. As always, I'll add this to the documentation.

jre

---

### Post by quixotic-cynic on 2007-09-16
> **mak123 said:**
> In my /etc/moblock/blocklists.list file, some of the URLs for blocklists have a "#" at the start of the line. What does that mean?

# Any line preceeded by a hash mark is a comment
# They are treated as human readable lines and not used in the script.
# Don't worry too much so long as level1 is uncommented (i.e. has no #-mark).

# Other useful lists are the templist, and level2 (imo). The iana ranges are good too since they shouldn't be in use (same with the bogon file).
# Spyware and trojan would be useful but only if you were on windows. On linux they are pretty pointless.
# The lists that are useful vary depending on your requirements.
# e.g. almost no-one needs the edu or microsoft ranges...

# You can find out what each does at [www.bluetack.co.uk](www.bluetack.co.uk)

---

### Post by retselseer on 2007-09-22
I am not able to get past the first step of adding ´deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main´ & ´deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main´ to /etc/apt/sources.list .  I tried to add those lines to sources.list via a terminal after invoking root privileges but all I keep on getting is the error code, ´bash: deb-src: command not found´ .  What am I doing wrong?  If I am doing something wrong, please tell me what exactly it is in complete layman&#347; terms, not computer geekesque language.  Thank you very much.  By the way, why can´t Ubuntu let you simply let you log in initially as root?  If I f#@* something up, that is my problem, not anyone else&#347; problem.  Part of being free is being free to mess up, isn´t it?  Help me!!!!!

---

### Post by quixotic-cynic on 2007-09-22
> **retselseer said:**
> I am not able to get past the first step of adding ´deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main´ & ´deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main´ to /etc/apt/sources.list.

Ah, np, you just tried to put them in the wrong place... :)

Type ```
sudo getit /etc/apt/sources.list
```, enter that, and then type your password.

When gedit loads up then you just have to add those two lines that you typed at the bottom. Put a little note on a line starting with # to remind you what it is (see previous post). Save the file and that is that step sorted.

```
sudo aptitude update
```
and ```
sudo aptitude install moblock-nfq
``` can then help. (The update is required for the system to recheck the sources.list and find the lines you added).

---

### Post by soulbreak on 2007-09-22
I've got block installed and running but the guarding.p2p file is empty.  Isn't moblock supposed to auto update that itself or do I have to manually update my p2p lists all the time.

---

### Post by quixotic-cynic on 2007-09-23
Mine never auto-updates. I do it manually each day. It *should* auto-update and appears to do so for most people.

However, your guarding.p2p should never be empty since the install does a manual update initially - which is a little strange.

Try the ```
sudo sh /etc/cron.daily/moblock-nfq
``` command and see if it is still blank - if it is then you have a more fundamental problem to worry about than auto update.

---

### Post by jre on 2007-09-25
**I finally did the switch! Just have a look at [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net).**

If you used the preview repository in your /etc/apt/sources.list then you simply have to remove the word "preview".

Have fun and thanks for all help. Last but not least to my precessor lestlest/clessing who founded moblock-deb.sourceforge.net.

jre

---

### Post by pelle.k on 2007-09-25
OK! Nicely done :)
I'll update the HOWTO accordingly. However, (i've pointed this fact out in the past) i am *not* running ubuntu nowadays, so if there are any errors you will have to correct me.

However, if "gutsy" delivers, i might reconsider running ubuntu again. ;)

---

### Post by jre on 2007-09-26
> **pelle.k said:**
> OK! Nicely done :)
I'll update the HOWTO accordingly. However, (i've pointed this fact out in the past) i am *not* running ubuntu nowadays, so if there are any errors you will have to correct me.
Thanks. And don't worry: there are some guys around here who use ubuntu and do excellent support. I think it's time to tell that i **really appreciate** this; you know who you are.
Note that I am using Debian lenny and so can't check those things, too. I just hang around here because here are the most users ;-)

I had a look at your guide (nice):

older ubuntu versions: I can't comment that directly, but the dependencies in the packages are:
```
all versions:
iptables
lsb-base >= 3.0-6

etch
libc6 >= 2.3.6-6
libnetfilter-queue1 >= 0.0.12
libnfnetlink1 >= 0.0.16

lenny/sid
libc6 >= 2.6.1-1
libnetfilter-queue1 >= 0.0.13
libnfnetlink0 >= 0.0.25

feisty
libc6 >= 2.5-0ubuntu1
libnetfilter-queue1 >= 0.0.12
libnfnetlink1 >= 0.0.16

gutsy
libc6 >= 2.6-1
libnetfilter-queue1 >= 0.0.13
libnfnetlink0 >= 0.0.25
```


How do i keep it installed, without having it run at startup?
... MOBLOCK_INIT="0"

I'm still not sure it's running!
moblock-control status
will check the PID and if the process reacts to signals (kill -0)
However it's up to the users to check if the iptables rules are set correctly (they are also shown on "status")

whitelisting ports/IPs with iptables via moblock.conf requires "restart"
removing ranges from the blocklist via moblock.conf requires "reload" ("restart" is also ok)

automatic blocklist update:
on (default): MOBLOCK_CRON="1"
off: MOBLOCK_CRON="0"

for firehol users I recommend ```
IPTABLES_SETTINGS="0"
```. Then (re)starting moblock after firehol doesn't mess around with iptables.

greets
jre

PS: 20 hours switched - and no user complains. I think it works ;-)

---

### Post by pelle.k on 2007-09-26
Good points. I'll include this.

> PS: 20 hours switched - and no user complains. I think it works
It would seem that way. :)

---

### Post by LordKelvan on 2007-09-27
I just upgraded from 0.8.15 to 0.8.21 and I noticed that I lost internet access: I couldn't visit any websites, pidgin died, torrents died, couldn't ping anything.  Is anyone else experiencing this problems?

---

### Post by nuskool on 2007-09-27
Just wanted to say thanks to the writer of the tutorial (and the developer(s) of the application itself). 

Set it up last night first time. Got a little impatient on install when it said it was updating the list and cancelled it because i thought it had crashed. Ran the moblock-control update to get it to download the lists again.

Thanks all.

---

### Post by quixotic-cynic on 2007-09-27
> **LordKelvan said:**
> I just upgraded from 0.8.15 to 0.8.21 and I noticed that I lost internet access: I couldn't visit any websites, pidgin died, torrents died, couldn't ping anything.  Is anyone else experiencing this problems?

If I run moblock off my openbox start menu with the command ```
rxvt -e sudo /etc/init.d/moblock-nfq start
``` it completely nerfs my internet connection.

Starting with  ```
sudo /etc/init.d/moblock-nfq start
``` run within a terminal usually does not give me problems.

Sometime it also messes up after updating moblock.

If you are experiencing this problem I would suggest:
1) manually stopping moblock
2) starting it
3) waiting a few seconds,
4) trying a program that should not be blocked/has not been previously

I am unsure of a 'permanent' fix - I start/stop and update moblock manually.

Please let me know how you get on... also - it may be worth comparing set-ups: I have a command line install running xorg/openbox on top.

---

### Post by pelle.k on 2007-09-27
> **LordKelvan said:**
> I just upgraded from 0.8.15 to 0.8.21 and I noticed that I lost internet access: I couldn't visit any websites, pidgin died, torrents died, couldn't ping anything.  Is anyone else experiencing this problems?

What ubuntu you run, what repo do you get moblock from, and what does "sudo moblock-control status" tell you?
See, it's all in how you supply the clues. Without those we can't help you.

---

### Post by Githlar on 2007-09-27
After following your updated tutorial on how to install MoBlock on Gutsy, I receive this message after running `sudo apt-get install moblock-nfq`

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  moblock-nfq: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
               Depends: libnetfilter-queue1 (>= 0.0.13) but 0.0.12-1 is to be installed
               Depends: libnfnetlink0 (>= 0.0.25) but it is not installable
E: Broken packages


---

### Post by jre on 2007-09-27
@LordKelvan:
try "tail -f /var/log/moblock.log" to see live if/which IPs are blocked.
Maybe your own and some/many IPs that you want to ping/connect via pidgin/... is in the blocklist. Major changes since 0.8-15:

- **no more whitelisting of port 80 and 443**: This only explains why you have problems with web surfing.
- **new blocklists** (additional to the old ones):
[www.bluetack.co.uk/config/hijacked.gz](www.bluetack.co.uk/config/hijacked.gz)
[www.bluetack.co.uk/config/iana-multicast.gz](www.bluetack.co.uk/config/iana-multicast.gz)
[www.bluetack.co.uk/config/rangetest.gz](www.bluetack.co.uk/config/rangetest.gz)
[www.bluetack.co.uk/config/trojan.gz](www.bluetack.co.uk/config/trojan.gz)
[www.bluetack.co.uk/config/iana-private.gz](www.bluetack.co.uk/config/iana-private.gz)
[www.bluetack.co.uk/config/iana-reserved.gz](www.bluetack.co.uk/config/iana-reserved.gz)
Perhaps **your own** and/or the IPs you wanted to connect to/ping/... is in one of these lists.

If your problems continue and you see that the IPs are blocked in the logfile, then you have to whitelist IPs / ports and/or remove some IP ranges from the blocklist (both via moblock.conf) and/or don't use some blocklists (edit blocklists.list).

If no IPs are blocked then try restarting manually. If your problems continue then I'm quite clueless :-/

@Githlar:
current Gutsy:
libc6 is 2.6.1-1ubuntu7
libnetfilter-queue1 (0.0.12-1) in **universe**
libnfnetlink0 (0.0.25-1) in **universe**

So I think: you need to add "universe" to your sources.list and update your whole gutsy installation (this solves the libc6 and the libnfnetlink0) problem.
But then there's still a problem with libnetfilter-queue1. I'll try to sort this out, now. But I can't promise anything.

Note to pelle: add to the Howto that "universe" has to be in the sources.list.

greets
jre

---

### Post by pelle.k on 2007-09-27
I just installed the newly released gutsy beta today, and moblock *does* install flawlessly. Me thinks someone hasn't dist-upgraded in a while ;)
Both libnfnetlink, and libnetfilter-queue is in universe, which is activated by default after installation.

btw, updating the blocklists upon installation never did succeed.
However, the blocklists were downloaded to /var/spool/moblock, but the guarding.p2p was empty.

```
Updating blocklists and reloading MoBlock if any blocklist was updated   ...done.
Empty blocklist!
Starting MoBlock   ...done.
```
A manual update took care of that though.
I  think it would be helpful with some kind of "progress indicator" of some sort, or better yet, what lists got updated. The update took a good 2-3 minutes with no indication on what was happening.

Other than that, great work! :)

---

### Post by quixotic-cynic on 2007-09-27
I think the problem LordKelvan may be getting is more serious than what he wants being inside one of the block ranges. I get the problem too sometimes so I know what he means - your *whole* net connection goes... (I will work on this a bit more over the next few days I think).

---

### Post by sefs on 2007-09-27
I need a confirmation before installing if anyone can

MoBlock works well with IPTables and does not cancel each other out?

The problem arises where you try to use Moblock with a front end for iptables such as FireStarter?  

And if i stop FireStarter from loading at startup (PS: the iptables firewall in ubuntu will still be running in FULL effect ... just not with the gui front end firestarter .. so all firewall rules will still be running) and use MoBlock that MoBlock will run perfectly with the iptables firewall.

Is all that correct?

Thanks.

---

### Post by pelle.k on 2007-09-27
Moblock does its own iptable rules (that is what iptables is, a set of rules). It *has* to redirect traffic in a certain way, for it to inspect and stop some of it.
That's why it doesn't work with other iptable constructions very well.
It could work with other iptables frontends (like firestarter), if support for redirecting traffic the way moblock does would be supported.
That way, moblock wouldn't have to create it's own (conflicting) rulesets, but leave that to firestarter (or whatever frontend).

So in effect; No, you can't run firestarter. Even if you don't run the GUI, the iptable rules (run by the daemon, not the GUI) will still apply, and thus conflict with moblock in some way.

I hear "ipblock" can work in harmony with another iptables firewall though (if i'm not mistaken). There's even a HOWTO right here in the ubuntuforums for it.

---

### Post by Neovos on 2007-09-27
To JRE regarding updated Moblock on Feisty.

Great job btw. I just installed it and the updated .conf file is laid out really well. Was really simple to configure. I ran moblock successfully and all updates and configurations worked well for me. I did also try the setup with firehol and got lots of non success. So it's confirmed that it doesn't work with firehol out of the box. Heres what I got after configuring moblock (as per older firehol setup instructions above), updating, starting moblock. and then immediately starting firehol.
```

user@computer:~$ sudo firehol stop
FireHOL: Clearing Firewall: OK

user@compuer:~$ sudo moblock-control restart
(Re-)Starting MoBlock   ...done.
user@computer:~$ sudo firehol start


--------------------------------------------------------------------------------
ERROR   : # 1.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 34 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_torrent_s1 -p tcp --dport 6881:6981 -m state '' --state NEW\,ESTABLISHED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 2.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 34 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_torrent_s1 -p tcp --sport 6881:6981 -m state '' --state ESTABLISHED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 3.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 40 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_http_c2 -p tcp --sport 32768:61000 --dport 80 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 4.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 40 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_http_c2 -p tcp --sport 80 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 5.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 41 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_https_c3 -p tcp --sport 32768:61000 --dport 443 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 6.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 41 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_https_c3 -p tcp --sport 443 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 7.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 44 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_all_c4 -m state '' --state NEW\,ESTABLISHED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 8.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 44 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_all_c4 -m state '' --state ESTABLISHED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 9.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 44 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_irc_c5 -p tcp --sport 32768:61000 --dport 6667 -m state '' --state NEW\,ESTABLISHED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 10.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 44 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_irc_c5 -p tcp --sport 6667 --dport 32768:61000 -m state '' --state ESTABLISHED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 11.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 44 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c6 -p tcp --sport 32768:61000 --dport ftp -m state '' --state NEW\,ESTABLISHED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 12.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 44 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c6 -p tcp --sport ftp --dport 32768:61000 -m state '' --state ESTABLISHED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 13.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 44 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c6 -p tcp --sport ftp-data --dport 32768:61000 -m state '' --state ESTABLISHED\,RELATED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 14.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 44 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c6 -p tcp --sport 32768:61000 --dport ftp-data -m state '' --state ESTABLISHED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 15.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 44 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c6 -p tcp --sport 32768:61000 --dport 1000:65535 -m state '' --state ESTABLISHED\,RELATED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 16.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 44 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c6 -p tcp --sport 1000:65535 --dport 32768:61000 -m state '' --state ESTABLISHED -j MOBLOCK 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 17.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 18.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 19.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A INPUT -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 20.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A OUTPUT -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'



--------------------------------------------------------------------------------
ERROR   : # 21.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A FORWARD -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 

Try `iptables -h' or 'iptables --help' for more information.
Bad argument `'

Stopped: Couldn't activate new firewall.

FireHOL: Restoring old firewall: OK

user@computer:~$ 

```

I think almost every single line that was added in firehol.conf referencing moblock led to an error. So heres out of the box errors. Don't know if they're useful to you at all. But my next thought is that why do you even need an additional firewall anyway? Your already blocking the ip lists, then can't you just manually enter blocks or allows as you need them in moblock?

---

### Post by Githlar on 2007-09-27
Actually, I've been running Feisty for a while and I just got some upgrades today. I have it set to get proposed updates and stuff, so I just assumed it would kick me up to Gusty beta. I guess this isn't the case?

---

### Post by Neovos on 2007-09-28
I've heard that all you have to do is change your synaptic links from feisty to gusty and it will update it all automatically. I heard in the same breath though that it can very easily break alot of your programs and settings so it might be prudent to wait until more stable releases.  But my friend who said his programs broke was upgrading to dapper forever ago. So that might have alot to do with it.

---

### Post by pelle.k on 2007-09-28
> I have it set to get proposed updates and stuff, so I just assumed it would kick me up to Gusty beta. I guess this isn't the case?
You people should really check these things out before you act. This is an OS, not a kitchen mixer ;)
No, feisty wont be updated to gutsy just by itself!

> change your synaptic links from feisty to gusty and it will update it all automatically
No. You should run "sudo update-manager -c -d" after changing repos...

---

### Post by quixotic-cynic on 2007-09-28
> **Neovos said:**
> But my next thought is that why do you even need an additional firewall anyway? Your already blocking the ip lists, then can't you just manually enter blocks or allows as you need them in moblock?

Yes you can, but MoBlock is not exactly a firewall per-se - most firewall rules tend to focus on which ports are allowed rather than to which IPs (though IPs are also relevant, esp with your DNS provider and so on) so it could be desirable to have a firewall too.

That said, a reasonable DSL modem/router will have a firewall that does a decent job of stopping bad stuff coming in, and bad stuff going out is only really a problem on Windows. Ubuntu has no open ports facing the net open by default and so, provided that you keep it updated, you should not really have a problem on Ubuntu.

---

### Post by Juleshu on 2007-09-28
I am getting this error when running sudo apt-get update

Get:5 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) feisty Release.gpg [189B]
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) feisty/main Translation-en_US
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) feisty Release
Fetched 5B in 5s (1B/s)
Failed to fetch [http://moblock-deb.sourceforge.net/debian/dists/feisty/Release](http://moblock-deb.sourceforge.net/debian/dists/feisty/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

any ideas?
Is it because I am running 64 bit Ubuntu?

---

### Post by jre on 2007-09-28
> **pelle.k said:**
> I just installed the newly released gutsy beta today, and moblock *does* install flawlessly. Me thinks someone hasn't dist-upgraded in a while ;)
Both libnfnetlink, and libnetfilter-queue is in universe, which is activated by default after installation.
Welcome back in the world of Debian packages :-)
Thx for reporting that. I checked [http://packages.ubuntu.com/gutsy/libs/libnfnetlink0](http://packages.ubuntu.com/gutsy/libs/libnfnetlink0) yesterday and found the wrong version. today it was correct - hmm, time for a weekend without computer.


> **pelle.k said:**
> btw, updating the blocklists upon installation never did succeed.
However, the blocklists were downloaded to /var/spool/moblock, but the guarding.p2p was empty.

```
Updating blocklists and reloading MoBlock if any blocklist was updated   ...done.
Empty blocklist!
Starting MoBlock   ...done.
```
A manual update took care of that though.
I  think it would be helpful with some kind of "progress indicator" of some sort, or better yet, what lists got updated. The update took a good 2-3 minutes with no indication on what was happening.
Added progress indicator to the TODO, but don't know yet how to do it.
Here the initial update worked, very strange, once again. Added as a possible bug.

@Neovos: Did you insert the MOBLOCK chain in the beginning of the firehol script?
```
# Moblock chain
iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE
```

> **Juleshu said:**
> Is it because I am running 64 bit Ubuntu?
Yes, the packages are only for i386, not for amd64. There's an really outdated 64 bit version on moblock-deb.sf.net. You could also build the package on your own - instructions are also on moblock-deb.
If someone provides me with 64bit packages (or an 64bit machine :-)) I'd be happy to offer this version, too. Just contact me.



Thx for all feedback and support of you!! I'll be back in a few days.

---

### Post by jamesford on 2007-09-28
id love it if 64 bit debs are available in time for gutsy :)
otherwise soemone has to tell me how to make them myself again cos i forgot how :P

---

### Post by Neovos on 2007-09-28
@jre
> 
@Neovos: Did you insert the MOBLOCK chain in the beginning of the firehol script?
```
# Moblock chain
iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE
```


Yes I did in fact. I actually went through the whole setup twice from scratch just for the sake of trying to see if I got the same errors. And same thing happened.

And also, weirdly enough, I after I started moblock, then started firestarter just to see exactly what it would do, my moblock would no longer start up at all. It just kept saying "...failed" when I hit the start command (sudo moblock-control start). It was weird. I restarted, opened and reclosed firewalls, uninstalled everything but moblock, still didn't start up. So I just put the firestarter/ipblocker combo back on there for now. I'll try again in a couple days cause as we all know, computers only work on certain lunar calender days when the  amount of sunlight is just right and when......

@quixotic-cynic
> 
Yes you can, but MoBlock is not exactly a firewall per-se - most firewall rules tend to focus on which ports are allowed rather than to which IPs (though IPs are also relevant, esp with your DNS provider and so on) so it could be desirable to have a firewall too.


Moblock is already editing the iptables, do you think it would be difficult from a development standpoint to add in there port management as well and make it a full fledged firewall? Get rid of this compatibility issue once and for all? Perhaps even merge it with the firehol project or something?

---

### Post by quixotic-cynic on 2007-09-28
> **Neovos said:**
> Moblock is already editing the iptables, do you think it would be difficult from a development standpoint to add in there port management as well and make it a full fledged firewall? Get rid of this compatibility issue once and for all? Perhaps even merge it with the firehol project or something?

I see no reason why not in theory (but it would be quite a bit of work for someone). Afaik moblock does not use one rule per range blocked - it is implemented in a pseudo-iptables manner with a few rules to implement blocking for the whole list - so to actually manage firewall rules too would require more than a few lines extra to code.

---

### Post by pelle.k on 2007-09-28
> Moblock is already editing the iptables, do you think it would be difficult from a development standpoint to add in there port management as well and make it a full fledged firewall? Get rid of this compatibility issue once and for all? Perhaps even merge it with the firehol project or something?
Sure thing. That is essentially the problem. Firestarter (as an example) doesn't offer to send packets to NFQUEUE instead ACCEPT (the last time i checked).

If it did, we could do what moblock does, with firestarter. And yes, moblock *could* in theory be a full featured firewall since it deals with iptables, but that is not it's primary task.

In fact, moblock just does filtering in userspace (kernel), the iptables rules (created from a bash script) is just what is needed to get traffic to go that route.

---

### Post by nuskool on 2007-09-28
I'm glad (in a way) that others experienced the same issue of the lists not updating on install.. i thought it was just me being impatient.

On a separate note I wonder if you guys could help a linux beginner out (it's slightly on topic!)...

EDIT: I think it's working and as it was off topic (slightly) i'll remove my question.

---

### Post by draggy on 2007-09-29
Thanks for this awesome tutorial. unfortunately I can't get moblock to start.

I have it installed on an ubuntu edgy server. (installed...uninstalled it...and reinstalled it to make sure) But I cannot get moblock to start/stop. When I give the command, it says "Starting MoBlock   ...fail!"

It's like half started, because when I reboot, some of the ports are blocked, samba won't start and ssh only works because I whitelisted the port. When I do a stop or start, it says it failed, but if I do a reload, it stops whatever part of moblock is loaded, and then everything works. 

this is what moblock-control.log says:
[quote=/var/log/moblock-control.log]
2007-09-29 12:36:59 AM CDT Begin: /usr/bin/moblock-control start
Inserting iptablesiptables: Chain already exists
iptables: Chain already exists
iptables: Chain already exists
   ...done.
Starting MoBlock/usr/bin/moblock: invalid option -- $
* Logging to &

MoBlock 0.8 by Morpheus
Syntax: MoBlock -dnp <blocklist> [-b] [-q 0-65535] <logfile>

        -d      blocklist is an ipfilter.dat file
        -n      blocklist is a peerguardian 2.x file (.p2b)
        -p      blocklist is a peerguardian file (.p2p)
        -q      0-65535 NFQUEUE number (as specified in --queue-num with iptables)
   ...fail!
2007-09-29 12:36:59 AM CDT End: /usr/bin/moblock-control start
[/quote]

ideas/suggestions?

---

### Post by nuskool on 2007-09-29
I'm far from an expert on this but from that log it makes you think that moblock is already running... probably best waiting for an expert opinion tho.

---

### Post by Neovos on 2007-09-29
I had a similar problem with the "....fail" error. And at first it just meant that I had a firewall running in the background that I had to close via the terminal. But eventually I got that every time as well.

---

### Post by quixotic-cynic on 2007-09-29
> **draggy said:**
> invalid option -- $

The part above almost makes it sound like it is trying to start like ```
sudo moblock-control start -$
``` (which I'm sure you know would not be right). The part below that is very much like what you get whenever you enter an invalid parameter on any terminal program you try to run... which could be significant, but not with what I know. I am wondering if the script being run is somehow trying to run part of moblock with an invalid parameter.

I would remove the autostart for moblock, remove any firewalls (I hope you have a hardware one...) and then restart. After that I would try to start moblock with ```
sudo moblock-control start
``` from within a terminal (as usual).

See if that produces the same problem. If it does then post a reply and I will try and think of something else.

PS: [ CODE ] tags are probably more useful than [ QUOTE ] tags in you prev. post (quotes disappear when writing a reply with a quote...)

Edit: updated

---

### Post by LordKelvan on 2007-09-29
> **pelle.k said:**
> What ubuntu you run, what repo do you get moblock from, and what does "sudo moblock-control status" tell you?
See, it's all in how you supply the clues. Without those we can't help you.

Good points, I will provide more information in my future requests for help (and no, I'm not being sarcastic).

> **jre said:**
> :
Major changes since 0.8-15:

- **no more whitelisting of port 80 and 443**: This only explains why you have problems with web surfing.
- **new blocklists** (additional to the old ones):
[www.bluetack.co.uk/config/hijacked.gz](www.bluetack.co.uk/config/hijacked.gz)
[www.bluetack.co.uk/config/iana-multicast.gz](www.bluetack.co.uk/config/iana-multicast.gz)
[www.bluetack.co.uk/config/rangetest.gz](www.bluetack.co.uk/config/rangetest.gz)
[www.bluetack.co.uk/config/trojan.gz](www.bluetack.co.uk/config/trojan.gz)
[www.bluetack.co.uk/config/iana-private.gz](www.bluetack.co.uk/config/iana-private.gz)
[www.bluetack.co.uk/config/iana-reserved.gz](www.bluetack.co.uk/config/iana-reserved.gz)
Perhaps **your own** and/or the IPs you wanted to connect to/ping/... is in one of these lists.


Dude, much thanks man!!  It was the fact that I wasn't whitelisting the http/https protocols (I read this from your updated instructions, I'm not sure if it is the same as not whitelisting ports 80 and 443).  So I just uncommented the line:

WHITE_TCP_OUT="http https"

from moblock.conf and everything works.  The thing with pidgin/torrents may have been due to some ISP problems I was coincidentally having :D

Cheers,
LK

---

### Post by quixotic-cynic on 2007-09-29
> **LordKelvan said:**
> So I just uncommented the line: WHITE_TCP_OUT="http https" from moblock.conf and everything works.

Of course, if your paranoia is rated medium-high you now have a big problem: [http://ubuntuforums.org/showpost.php?p=3232624&postcount=589](http://ubuntuforums.org/showpost.php?p=3232624&postcount=589) (+ about 10 posts for whole discussion)

---

### Post by LordKelvan on 2007-09-29
Actually I just discovered that the root of my problem goes a bit further.  It appears that the newest version of moblock uses moblock.conf for configuration settings, and not MoBlock_nfq.sh for configuration.  Thus my real problem would be that I didn't transfer the settings (I found this out when my IM began having problems).  Can someone confirm this?

quixotic-cynic:
I am not a networking expert, so am I to understand that someone could set their BT port to 80, and in essence I would unwittingly connect to them?  I guess I had always thought that moblock and other such applications merely prevent the RIAA/MPAA from scanning me (i.e. try to connect to me), but that it doesn't prevent me from connecting to them (for some reason I thought that that was safe).  In any case, it doesn't really seem like the thread offers any solutions, so I suppose I will just have to accept this risk.  I realize that I could not whitelist then add IP's on a case by case basis, but that seems like more trouble than I am willing to go through.  I personally like the suggestion of enabling/disabling traffic based on an application (i.e. disable whitelisting for my p2p program).  Is this something which is technically feasible, and can it be added to the next version of this really useful app ? :D

---

### Post by draggy on 2007-09-30
quixotic-cynic: I removed the autostart and tried to run it with the command you posted, but it says:

```
* MoBlock is configured not to start automatically at boot time.
 * To change this edit the MOBLOCK_INIT entry in /etc/moblock/moblock.conf.
```

so I set it to autostart again, and ran the command again:

```
Starting MoBlock   ...fail!
```

The fail came after a long pause. did a status, and it says that it was not running. This time, I am sure that moblock was not running when I started it, so I am once against stuck.

fyi: I'm not running any firewall on that linux machine.

---

### Post by quixotic-cynic on 2007-09-30
> **draggy said:**
> quixotic-cynic: I removed the autostart and tried to run it with the command you posted, but it says:

```
* MoBlock is configured not to start automatically at boot time.
 * To change this edit the MOBLOCK_INIT entry in /etc/moblock/moblock.conf.
```

Draggy, I have no idea why it should care about startup issues when running manually - I have never encountered this problem. I'm probably one of the least knowledgable 'support' people here though - so some of the other ppl may be able to help when they get the time.

Sorry I could not help more.

---

### Post by quixotic-cynic on 2007-09-30
> **LordKelvan said:**
> I am not a networking expert, so am I to understand that someone could set their BT port to 80, and in essence I would unwittingly connect to them?  I guess I had always thought that moblock and other such applications merely prevent the RIAA/MPAA from scanning me (i.e. try to connect to me), but that it doesn't prevent me from connecting to them (for some reason I thought that that was safe).

You understood completely fine - apart from the bit about it being safe ;) Because with bittorrent and other P2P apps users act both as a client and a server you could connect out to them and then either download or upload stuff (probably both) and thus connecting to an 'adversary' would be a bad idea. 

It can be a risk people are willing to take though - & it all depends on whether the adversary thinks of setting their port to 80 or is clueless... so you have to decide. :)

---

### Post by LordKelvan on 2007-09-30
Hmm, I get it now.  Like I said, I will wait for the per-application feature (i.e. disabling/enabling based on application).

---

### Post by draggy on 2007-09-30
just to add to the info I've given: I'm running ubuntu edgy and no firewall.

As nuskool said, it seems like it's running, even though it says that it fails to follow any of the commands. But when I test it, it says that the ip was not blocked. 

It wouldn't be so bad if when it's supposedly "running" it would work. but all of my torrent traffic grinds to a halt when it's "running" The only way I'm able to connect to it was because I whitelisted my ssh port.

I just tried uninstalling moblock and those 2 libs and reinstalling, and I still have that problem.

---

### Post by feld on 2007-09-30
i am running gutsy amd64. I put the deb-src in my sources.list and apt-get source moblock. i did a fakeroot dpkg-buildpackage like i should; it built the packages. I dpkg -i the -nfq version like i wanted to; life is good. I had all build deps, I have all install deps. It freezes at "updating the blocklist" portion of the "install". Killing that and trying to manually run an update also fails.

Any tips? Is the update server just overloaded or something?

---

### Post by ordou on 2007-09-30
> **draggy said:**
> just to add to the info I've given: I'm running ubuntu edgy and no firewall.

As nuskool said, it seems like it's running, even though it says that it fails to follow any of the commands. But when I test it, it says that the ip was not blocked. 

It wouldn't be so bad if when it's supposedly "running" it would work. but all of my torrent traffic grinds to a halt when it's "running" The only way I'm able to connect to it was because I whitelisted my ssh port.

I just tried uninstalling moblock and those 2 libs and reinstalling, and I still have that problem.

I'm having the same problems as you, and I'm also running edgy. Did you manually install the net-debs also?

In my logs I see
```
2007-09-30 11:42:12 PM CEST Begin: /usr/bin/moblock-nfq-control restart
Deleting iptables   ...fail!
Stopping MoBlock   ...fail!
Inserting iptablesiptables: Chain already exists
iptables: Chain already exists
iptables: Chain already exists
   ...done.
Starting MoBlock/usr/bin/moblock: invalid option -- $
* Logging to &

MoBlock 0.8 by Morpheus
Syntax: MoBlock -dnp <blocklist> [-b] [-q 0-65535] <logfile>

        -d      blocklist is an ipfilter.dat file
        -n      blocklist is a peerguardian 2.x file (.p2b)
        -p      blocklist is a peerguardian file (.p2p)
        -q      0-65535 NFQUEUE number (as specified in --queue-num with iptabl$
   ...fail!
2007-09-30 11:42:16 PM CEST End: /usr/bin/moblock-nfq-control restart

```

And now I'm unable to uninstall mobck! :(

```
sudo apt-get remove moblock-nfq
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  moblock-nfq
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  moblock-nfq
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 201kB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 55121 files and directories currently installed.)
Removing moblock-nfq ...
Stopping MoBlock   ...fail!
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: error processing moblock-nfq (--remove):
 subprocess pre-removal script returned error exit status 3
Starting MoBlock   ...fail!
invoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Also, moblock doesn't respond when trying to update the blocklist...

Help? :confused:

---

### Post by draggy on 2007-09-30
[quote=ordou]And now I'm unable to uninstall mobck! [/quote]

turn off the auto start in /etc/moblock/moblock.conf, restart, and uninstall. And yes, I manually installed the net-debs provided

[quote=feld]It freezes at "updating the blocklist" portion of the "install".[/quote]

just wait for it, it takes a long time (unless you're installing through an ssh session like I was, then it might kick you off the session)

---

### Post by feld on 2007-09-30
> **feld said:**
> i am running gutsy amd64. I put the deb-src in my sources.list and apt-get source moblock. i did a fakeroot dpkg-buildpackage like i should; it built the packages. I dpkg -i the -nfq version like i wanted to; life is good. I had all build deps, I have all install deps. It freezes at "updating the blocklist" portion of the "install". Killing that and trying to manually run an update also fails.

Any tips? Is the update server just overloaded or something?

ok i tried to install again and left to go go the grocery store. it was stuck at that updating list thing when i left.

when i came back it was finished and said that the guarding.p2p was empty so i ran a manual update and it worked. tested moblock and it worked.

i dont know what was holding it up before but it is working now.

someone should really get the amd64 binaries hosted there though.

---

### Post by pelle.k on 2007-09-30
> someone should really get the amd64 binaries hosted there though.
If jre had a 64bit computer, that could happen. But he doesn't.
Well, i'd be happy to post them in the HOWTO, if you attach the .deb in your next post. But for them to be in a repo, someone must really maintain them.

---

### Post by daradib on 2007-09-30
What if one used an Ubuntu PPA?

---

### Post by daradib on 2007-09-30
Here are the AMD64 Gutsy packages for MoBlock.

---

### Post by pelle.k on 2007-09-30
tank you, daradib! :)

---

### Post by lucis on 2007-09-30
Hmm, in Gutsy it doesn't seem to work. I'm using the deb repo from the moblock-deb site

Testing MoBlock: trying to ping 3.0.0.0 from /etc/moblock/guarding.p2p ...
 * MoBlock did not block the IP. Test failed.

---

### Post by draggy on 2007-10-01
well, I just gave up and upgraded to Feisty. Now moblock starts and stops with no problems. Everything seems to be working great! So if you have edgy...just upgrade :)



[quote=lucis]* MoBlock did not block the IP. Test failed.[/quote]

btw, if you whitelist http/https the test WILL fail. Those must not be whitelisted if you want the test to work.

---

### Post by jre on 2007-10-01
Hey, I also have a real live, so I can't spend as much time with answering and fixing bux etc as I'd like to ...

General: If you are experimenting or have some problems: If you want to reinstall then first **purge** (not remove) moblock.

> **draggy said:**
> btw, if you whitelist http/https the test WILL fail. Those must not be whitelisted if you want the test to work.
No, the test is based on ping and does not use these whitelisted ports. The test will work with these ports whitelisted.

following my comments to the last posts. If you miss something then please remind me.


draggy/ordou [edgy doesn't work; update to feisty helps]
I guess that you have problems (a bug) with the lsb init-functions in edgy (in packet "lsb-base"). Those are responsible for starting moblock. Solving the edgy problems doesn't have high priority. But I'm working on an all distribution version, not only Debian and Ubuntu ...


lucis (gutsy) [moblock-control test does not succeed]:
but moblock is running? please post the output of "moblock-control status"
Also, the test function might gice wrong results e.g. if moblock blocks many other things the same time. So do in another terminal an "tail -f /var/log/moblock.log" and see what's happening.


daradib:
thanks for the packages. I added the nfq version on the homepage. Also, feel free to do the PPA thing. Just heard of it and it sounds very interesting, but I haven't enough time to start this now (just made a bookmark on it). Also, personally I'm using Debian, not Ubuntu. Fell free to do it.


jamesford:
dude, just look at the moblock-deb homepage for instructions to make (amd64) packages ;-)
But daradib already did it.

feld:
[initial update took long time and resulted in empty blocklist; manual update works]
I'll look into this bug later and will add some status message on install. Thx

LordKelvan:
Yes, MoBlock_nfq.sh is NOT used in the debian packages. You have to do all configuration in moblock.conf.

Neovos [firehol problems]:
Can anybody confirm that moblock (new deb version 0.8-21) and firehol don't work together? I can't imagine why this should stop working.

quixotic-cynic:
so many thx for your work.
Just: "/etc/init.d/moblock COMMAND" is old. Always use "moblock-control COMMAND" instead.

pelle:
I think in Debian it's recommended to use aptitude instead of apt-get. But that's really unimportant;-) THX!


Greets to all
jre

---

### Post by draggy on 2007-10-01
[quote=jre]No, the test is based on ping and does not use these whitelisted ports.[/quote]

I tried it again, and it started failing (again). So I messed with it, reloaded it, checked the status, tested it, and it would always fail. 

Then I did a update, and a reloaded (this is what I had done before to get it to work) and ran two tests, and they both succeed. Why would I need to update, and reload it for the test to work?

---

### Post by pelle.k on 2007-10-01
Well, that was a mouthfull! :)
Man am i happy you guys are helping out. (not that i've been *that* active lately, but anyway...)

> Neovos [firehol problems]:
Can anybody confirm that moblock (new deb version 0.8-21) and firehol don't work together? I can't imagine why this should stop working.

Sure thing. :)
It's firehol that is broken, nothing else. There's nothing about it in launchpad so i guess i'll have to file a bug. (god i hate launchpad. maybe it's gotten better than the last time i used it?...)

---

### Post by quixotic-cynic on 2007-10-02
> **draggy said:**
> I tried it again, and it started failing (again). So I messed with it, reloaded it, checked the status, tested it, and it would always fail.

Not an answer to your main question, but when you reload (and it fails) does it still occur if you replace the reload with a separate start command and stop command?

I.e. changing ```
moblock-control restart 
``` to 
```
sudo moblock-control stop
sudo moblock-control start
```

I had an issue recently that was simmilar and I was wondering if your issue behaves in the same way as my one did... if I autoloaded moblock or started it from my openbox menu it would not work. Reloading didn't fix it but for some reason stopping/starting did... it was weird.

---

### Post by draggy on 2007-10-02
Now I can't seem to get it to test successfully at all anymore

```

sudo moblock-control test
Testing MoBlock: trying to ping 3.0.0.0 from /etc/moblock/guarding.p2p ...
 * MoBlock did not block the IP. Test failed.
sudo moblock-control stop
Stopping MoBlock   ...done.
sudo moblock-control start
Starting MoBlock   ...done.
sudo moblock-control test
Testing MoBlock: trying to ping 3.0.0.0 from /etc/moblock/guarding.p2p ...
 * MoBlock did not block the IP. Test failed.
sudo moblock-control update
Updating blocklists and reloading MoBlock if any blocklist was updated   ...done.
sudo moblock-control test
Testing MoBlock: trying to ping 3.0.0.0 from /etc/moblock/guarding.p2p ...
 * MoBlock did not block the IP. Test failed.
sudo moblock-control reload
Reloading MoBlock   ...done.
sudo moblock-control test
Testing MoBlock: trying to ping 3.0.0.0 from /etc/moblock/guarding.p2p ...
 * MoBlock did not block the IP. Test failed.
sudo moblock-control update
Updating blocklists and reloading MoBlock if any blocklist was updated   ...done.
sudo moblock-control reload
Reloading MoBlock   ...done.
sudo moblock-control test
Testing MoBlock: trying to ping 3.0.0.0 from /etc/moblock/guarding.p2p ...
 * MoBlock did not block the IP. Test failed.

```


This is what the log says most recently:
But most of the log file consists of skipping useless ranges, whatever that means.
```

tail /var/log/moblock.log
Skipping useless range: (050326) Unassigned 33437
Ranges loaded: 241839
Reopening logfile.
Blocked IN: tzulo, inc,hits: 1,SRC: 208.77.17.4
Blocked OUT: Bogon,hits: 1,DST: 76.10.160.164
Blocked IN: tzulo, inc,hits: 2,SRC: 208.77.17.4
Blocked OUT: GAMES-BEZEQINT,hits: 1,DST: 212.179.109.105
Blocked OUT: General Electric Company,hits: 1,DST: 3.0.0.0
Blocked OUT: GAMES-BEZEQINT,hits: 2,DST: 212.179.109.105
Blocked OUT: GAMES-BEZEQINT,hits: 3,DST: 212.179.109.105

```

It looks like it's blocking ips, so why doesn't the test work correctly?


here's my status
```

Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
RETURN     0    --  anywhere             anywhere
moblock_in  0    --  anywhere             anywhere            state NEW

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
moblock_fw  0    --  anywhere             anywhere            state NEW

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
RETURN     0    --  anywhere             anywhere
moblock_out  0    --  anywhere             anywhere            state NEW

Chain moblock_fw (1 references)
target     prot opt source               destination
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_in (1 references)
target     prot opt source               destination
RETURN     tcp  --  anywhere             anywhere            tcp dpt:8888
RETURN     tcp  --  anywhere             anywhere            tcp dpt:ssh
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_out (1 references)
target     prot opt source               destination
RETURN     tcp  --  anywhere             anywhere            tcp dpt:8888
RETURN     tcp  --  anywhere             anywhere            tcp dpt:ssh
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * moblock is running, pid is 9093.

```

---

### Post by dannyboy74 on 2007-10-02
I think I have the same test failure problem as above guy.
Doing "moblock-control test" outputs FAILURE in 9 out of 10 times.
And sometimes like 1 out of 10 times I get SUCCESS.  And it's the same test ip What's going on man, Is it on or off??

---

### Post by pelle.k on 2007-10-02
Listen people, as jre has told us before, the "test" isn't foolproof in it's design. Let me show you why;
> Blocked OUT: General Electric Company,hits: 1,DST: 3.0.0.0
Blocked OUT: GAMES-BEZEQINT,hits: 2,DST: 212.179.109.105
Blocked OUT: GAMES-BEZEQINT,hits: 3,DST: 212.179.109.105
See, ip "3.0.0.0" *was* blocked, but i guess ip "212.179.109.105" was hammering you so fast that the script (that checks the *last* line in the log file) didn't catch the result of a succesful block...

---

### Post by DaveTheAve on 2007-10-02
Fesity AMD64 Error: (I'd like to build it from source but i thought i'd try the gusty packs.)

> ~$ sudo dpkg -i moblock-nfq_0.8-21+gutsy_amd64.deb
Selecting previously deselected package moblock-nfq.
(Reading database ... 125379 files and directories currently installed.)
Unpacking moblock-nfq (from moblock-nfq_0.8-21+gutsy_amd64.deb) ...
dpkg: dependency problems prevent configuration of moblock-nfq:
 moblock-nfq depends on libc6 (>= 2.6-1); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 moblock-nfq depends on libnetfilter-queue1 (>= 0.0.13); however:
  Version of libnetfilter-queue1 on system is 0.0.12-1.
 moblock-nfq depends on libnfnetlink0 (>= 0.0.25); however:
  Package libnfnetlink0 is not installed.
dpkg: error processing moblock-nfq (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 moblock-nfq


---

### Post by pelle.k on 2007-10-02
> Fesity AMD64 Error: (I'd like to build it from source but i thought i'd try the gusty packs.)

Nothing strange about that...
The gutsy packages has it's dependencies pointing to packages *in* gutsy.

It seems 64bit is gaining popularity. I tell all feisty owners the same thing i told 64bit gutsy owners. compile a .deb and i will post it in the guide.

---

### Post by takayuki on 2007-10-02
Hi,

when i try to do this:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
```

i get this:

```
gpg: requesting key 9072870B from hkp server wwwkeys.eu.pgp.net
?: [fd 4]: read error: Connection reset by peer
gpgkeys: HTTP fetch error 7: couldn't connect: eof
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```


is this an error on my end?

thanks

---

### Post by SSB on 2007-10-02
sorry if this has been resolved already. friend is getting this error:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg: requesting key 9072870B from hkp server wwwkeys.eu.pgp.net
gpg: no valid OpenPGP data found.
gpg: read_block: read error: invalid packet
gpg: Total number processed: 0
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

thanks for any help.

---

### Post by pelle.k on 2007-10-02
i would say the server is temporarily down. try again later.

---

### Post by jre on 2007-10-03
@all:
I changed the test log message for less confusion.
Also I put some lines to the install script to tell the users to be patient and have a look at the moblock.log to follow the update process.


> **quixotic-cynic said:**
> If I run moblock off my openbox start menu with the command ```
rxvt -e sudo /etc/init.d/moblock-nfq start
``` it completely nerfs my internet connection.
Maybe there are environment problems when you use your openbox menu.
Do a "rxvt -e sudo printenv > printenv.rxvt" from the openbox start menu (like the way where moblock does not work) and a "sudo printenv > printenv.terminal" (like the way where moblock works). This will save the output of printenv in two files. Please send me a diff of those files.
Also, please give me the lines of moblock-control.log when starting does not work and the output of "iptables -L -v"

@pelle.k, feld and some others [empty blocklist after installation:]
Did you check if the blocklist was really empty? Perhaps it was just the wrong output of my installation script.

greets
jre

---

### Post by pelle.k on 2007-10-03
Hello jre. I did some investigating, and it turns out this is why the blocklists doesn't add to guarding.p2p at install time - after an update, it reloads;
```
do_reload() {
        pidofproc $DAEMON > /dev/null 2>&1
        DAEMON_STATUS=$?
        if [ $DAEMON_STATUS -eq "0" ] ; then    # If daemon was already running return value is 0
                build_blocklist
                echo -n  "Reloading $DESC"
                kill -HUP `pidofproc -p $PIDFILE $DAEMON`
                RETVAL=$?
                log_end_msg $RETVAL
        elif [ $DAEMON_STATUS -eq "3" ] ; then
                log_success_msg "$DESC is not running."
                RETVAL=0
        else
                log_failure_msg "$DESC has some strange status."
                log_failure_msg "Try \"`basename $0` stop\". Otherwise kill all $NAME processes,"
                log_failure_msg "delete $PIDFILE and all iptables rules related to $DESC."
                RETVAL=$DAEMON_STATUS
        fi
}
```
And since the daemon isn't running **[ $DAEMON_STATUS -eq "3" ]**, it quits without building the blocklist.
To have it build a blocklist after an update, the daemon has to be running already...

Also, can i suggest you background the ping in test_daemon;
```
# Send one icmp echo request to the tested IP address
                ping -c1 $TEST_IP > /dev/null 2>&1 &

```
This removes the gap between the ping and the grep, and makes the test work if moblock is currently logging other blocked ip:s at the same time.

---

### Post by DaveTheAve on 2007-10-03
I'll be more than happy to generate a package if someone is willing to instruct me.

---

### Post by jre on 2007-10-04
Thx pelle! That's really great to hear such suggestions. Both things happily accepted. I will release 0.8-22 soon.

> **DaveTheAve said:**
> I'll be more than happy to generate a package if someone is willing to instruct me.

From moblock-deb.sourceforge.net:
```
mkdir foo
cd foo
apt-get build-dep moblock
apt-get source moblock
cd moblock-VERSION
dpkg-buildpackage -rfakeroot
```
Just ask if you need further help

jre

---

### Post by DaveTheAve on 2007-10-04
> 
(Added MoBlock for 32-bit feisty to /etc/apt/sources.list)
david@Devlon:~/moblock$ sudo apt-get update
...
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Fetched 2188B in 25s (86B/s)
Failed to fetch [http://moblock-deb.sourceforge.net/debian/dists/feisty/Release](http://moblock-deb.sourceforge.net/debian/dists/feisty/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

david@Devlon:~/moblock$ sudo apt-get build-dep moblock
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could not open file /var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_feisty_main_source_Sources - open (2 No such file or directory)


I'm running Kubuntu AMD64-bit Feisty 7.01... Like I said I used the 32-bit Feisty resposatory, from the first post in this thread.

---

### Post by jre on 2007-10-04
Ah, source retrieval fails, too :-/

Instead of "apt-get build-dep moblock" install these packages:
debhelper (>= 4.0.0), iptables-dev, dpatch, libnetfilter-queue-dev, libnfnetlink-dev

Instead of "apt-get source moblock" download these files:
[http://moblock-deb.sourceforge.net/debian/dists/feisty/main/source/net/moblock_0.8-21+feisty.diff.gz](http://moblock-deb.sourceforge.net/debian/dists/feisty/main/source/net/moblock_0.8-21+feisty.diff.gz)
[http://moblock-deb.sourceforge.net/debian/dists/feisty/main/source/net/moblock_0.8.orig.tar.gz](http://moblock-deb.sourceforge.net/debian/dists/feisty/main/source/net/moblock_0.8.orig.tar.gz)
(and eventually this one: [http://moblock-deb.sourceforge.net/debian/dists/feisty/main/source/net/moblock_0.8-21+feisty.dsc](http://moblock-deb.sourceforge.net/debian/dists/feisty/main/source/net/moblock_0.8-21+feisty.dsc))
then unpack both files and apply (dpatch !?) the orig with the diff.

Then continue with the instructions. Sorry this is just a quick shot, not tested.

Greets and thx
jre

---

### Post by DaveTheAve on 2007-10-04
> 
david@Devlon:~/moblock/moblock-0.8$ ls
00list                           moblock.conf            moblock-nfq.init
blocklists.list                  moblock-ipq-control     moblock-nfq.install
changelog                        moblock-ipq.cron.daily  moblock-nfq.logrotate
Changelog                        moblock-ipq.dirs        moblock-nfq.manpages
Changelog~                       moblock-ipq.init        moblock-nfq.postinst
compat                           moblock-ipq.install     MoBlock-nfq.sh
control                          moblock-ipq.logrotate   MoBlock-nfq.sh.dpatch
COPYING                          moblock-ipq.manpages    NEWS.Debian
copyright                        moblock-ipq.postinst    rbt.c
docs                             MoBlock-ipq.sh          README
Makefile                         MoBlock-ipq.sh.dpatch   README.blocklists
makefile.dpatch                  moblock.man             README.Debian
makefile-moblock-control.dpatch  moblock-nfq-control     rules
moblock_0.8-21+feisty.dsc        moblock-nfq.cron.daily  THANKS
MoBlock.c                        moblock-nfq.dirs        TODO.Debian

david@Devlon:~/moblock/moblock-0.8$ dpkg-buildpackage -rfakeroot
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is



Any ideas?

---

### Post by Mochtroid-X on 2007-10-05
Why does MoBlock on Gutsy prevent me from accessing isoHunt.com and Doomworld.com, and why is it blocking my gmail and weather applets? It never blocked any these on Feisty.

---

### Post by quixotic-cynic on 2007-10-05
> **Mochtroid-X said:**
> Why does MoBlock on Gutsy prevent me from accessing isoHunt.com and Doomworld.com, and why is it blocking my gmail and weather applets? It never blocked any these on Feisty.

Moblock used to have port 80 whitelisted by default. Due to potentially weakened protection against adversaries this is no longer the case. If you read the howto that pelle.k posted at the start of the thread you can change this to allow port 80 (or just find the right place in the config file) but be aware that your 'protection' will be weakened (see link a few posts back).

You can (alternatively) use fewer lists to reduce these problems (e.g. just use Level1 list) and the use of a web proxy such as ecoproxy.com can let you get round the problem for minor cases (don't use for secure sites etc).

---

### Post by Mochtroid-X on 2007-10-05
What kind of "adversaries" are we talking about here?

---

### Post by pelle.k on 2007-10-05
> What kind of "adversaries" are we talking about here?

Microscopic, one-in-a-thousand (million?) chance, that some malware (installed on *your* computer) (virtually non-existant in linux) could use a whitelisted port to receive communication from an outside source that is in the blocklist.
IMHO people should be more worried about the lack of a proper firewall, than this scenario i describe above. But sure, this could happen.

---

### Post by Mochtroid-X on 2007-10-05
Well I whitelisted port 80 but it still denies my gmail applet...

---

### Post by DaveTheAve on 2007-10-05
What port is your gmail applet using? You might need to whitelist that port also.

P.S. I'm still stuck with the error message with the compiling posted above.

---

### Post by Mochtroid-X on 2007-10-05
I can't find what port it uses, no docs or anything for it can be found.

---

### Post by pelle.k on 2007-10-05
> I can't find what port it uses, no docs or anything for it can be found.
Use the power of the command line! :D
Close down pretty much all programs that are using internet connectivity, and then run
```
netstat -a --program
```
You might figure it out that way...
*or*, you could figure out what the blocked "range" is in the moblock log file, and put that in moblock.conf so that moblock filter that "range" out when it rebuilds the blocklist for you. Just a couple of suggestions for ya...

---

### Post by minijoe on 2007-10-06
Follwed jre's instruction, I created deb package for feisty amd64.
Great job jre!! many thanks. =D>

Here's deb package for feisty amd64.

---

### Post by pelle.k on 2007-10-06
Excellent! Added to howto.

---

### Post by vikram on 2007-10-06
Hi Pelle,

I am using a simple text based firewall ```


#!/bin/sh

if [ -r /lib/lsb/init-functions ]; then
    . /lib/lsb/init-functions
fi

firewall_start()
{
    # Flush all rules
    iptables -F INPUT
    iptables -F OUTPUT
    iptables -F FORWARD

    # Default policies
    iptables -P INPUT   DROP
    iptables -P OUTPUT  ACCEPT
    iptables -P FORWARD DROP

    # Allow everything on the loopback network
    iptables -A INPUT -i lo -j ACCEPT

    # Allow ICMP from the intranet router
    iptables -A INPUT --protocol icmp --source 192.168.0.1 -j ACCEPT

    # Allow everything from the home server
    iptables -A INPUT --source 192.168.0.2 -j ACCEPT

    # Allow established sessions
    iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

    # Allow incoming SSH sessions
    iptables -A INPUT --protocol tcp --dport 22 --source 192.168.0.0/24 \
      -m state --state NEW -j ACCEPT

    # Allow incoming ftp sessions
    iptables -A INPUT --protocol tcp --dport 21 --source 192.168.0.0/24 \
      -m state --state NEW -j ACCEPT
    iptables -A INPUT --protocol udp --dport 21 --source 192.168.0.0/24 \
      -m state --state NEW -j ACCEPT
    iptables -A INPUT --protocol tcp --dport 22 --source 192.168.0.0/24 \
      -m state --state NEW -j ACCEPT
    iptables -A INPUT --protocol udp --dport 22 --source 192.168.0.0/24 \
      -m state --state NEW -j ACCEPT

    # Allow incoming bittorent sessions
    iptables -A INPUT --protocol tcp --dport 6881 -m state --state NEW -j ACCEPT
    iptables -A INPUT --protocol udp --dport 4444 -m state --state NEW -j ACCEPT

    # Allow incoming ICMP echo request and errors
    iptables -A INPUT --protocol icmp --icmp-type echo-request -j ACCEPT
    iptables -A INPUT --protocol icmp --icmp-type destination-unreachable \
      -j ACCEPT

    # Drop intranet broadcasts
    iptables -A INPUT --protocol udp --destination 192.168.0.255 -j DROP

    # Drop and log other packets
    iptables -A INPUT   -j LOG
    iptables -A FORWARD -j LOG
}

firewall_stop()
{
    # Flush all rules
    iptables -F INPUT
    iptables -F OUTPUT
    iptables -F FORWARD

    # Default policies
    iptables -P INPUT   ACCEPT
    iptables -P OUTPUT  ACCEPT
    iptables -P FORWARD ACCEPT
}

case "$1" in
    start)
        log_begin_msg "Starting firewall..."
        firewall_start
        log_end_msg 0
        ;;

    stop)
        log_begin_msg "Stopping firewall..."
        firewall_stop
        log_end_msg 0
        ;;

    restart)
        log_begin_msg "Restarting firewall..."
        firewall_stop
        firewall_start
        log_end_msg 0
        ;;

    *)
        echo "Usage: $0 {start|stop|restart}"
        exit 1
esac

```

So If I replace ACCEPT with NFQUEUE and run moblock first and then my firewall  - will this mean my firewall will  filter packets first bassed on port  and then moblock will filter what is sent to NFQUEUE based on ip ?



> **pelle.k said:**
> Sure thing. That is essentially the problem. Firestarter (as an example) doesn't offer to send packets to NFQUEUE instead ACCEPT (the last time i checked).

If it did, we could do what moblock does, with firestarter. And yes, moblock *could* in theory be a full featured firewall since it deals with iptables, but that is not it's primary task.

In fact, moblock just does filtering in userspace (kernel), the iptables rules (created from a bash script) is just what is needed to get traffic to go that route.

---

### Post by ManOnOneWheel on 2007-10-06
I installed Moblock succesfully in Fiesty about a week ago, the log file showed my schools IP blocked over and over and such and all was well and good.

Since then I have upgraded to Gutsy. I followed the same proccess to install Moblock but no IP's at all are showing up in var/log/moblock.log. I have made sure that my blocklists are updated and the correct lists are uncommented, but still noting. Any ideas?

---

### Post by quixotic-cynic on 2007-10-07
> **vikram said:**
> So If I replace ACCEPT with NFQUEUE and run moblock first and then my firewall  - will this mean my firewall will  filter packets first bassed on port  and then moblock will filter what is sent to NFQUEUE based on ip ?

AFAIK, the moblock rules should be below the port blocking rules if you want it to function like that. Manually editing the ipfilter rules should work fine - the problem with Firestarter etc is a deficiency in the program and not in ipfilter.

I can't comment on the actual file since I understand firewall theory but not iptables syntax yet (still, shame on me).

I think that replacing ACCEPT with NFQUEUE basically means that the firewall 'ok-s' the packets from it's perspective and passes them on to moblock (rather than just letting them through completely).

Hopefully pelle.k or jre can clarify for you.

---

### Post by quixotic-cynic on 2007-10-07
> **ManOnOneWheel said:**
>  I have made sure that my blocklists are updated and the correct lists are uncommented, but still noting. Any ideas?

Is your schools IP range actually in the current edu file? If not, you could find out the IP range using [www.whois.sc](www.whois.sc) or simmilar and add it in the manual range section (see faq @ start).

---

### Post by pelle.k on 2007-10-07
> So If I replace ACCEPT with NFQUEUE and run moblock first and then my firewall - will this mean my firewall will filter packets first bassed on port and then moblock will filter what is sent to NFQUEUE based on ip ?
I'm no iptables guru either, but it should work if you do just that.
Remeber to deactivate iptables in /etc/moblock.conf.

---

### Post by wilberfan on 2007-10-10
I'm reasonably inexperienced with MoBlock, and I've just run into a problem:   After installing MoBlock I see the following:

> 2007-10-10 09:07:15 AM PDT End: /usr/bin/moblock-control restart
* Logging to /var/log/moblock.log
* Ranges loaded: 242399
* Using .p2p file format
* Merged ranges: 274
* Skipped useless ranges: 7345
NFNETLINK answers: Invalid argument

I then can't connect to anything...

Can anyone explain what's happening here?   And perhaps how to remedy it?  :confused:

---

### Post by jre on 2007-10-10
I've put the amd64 packages also to moblock-deb.sf.net. Thx to the contributors - and always stay with the current version :-)
daradib, minijoe: How did you download the sources? Didn't you have the problems that DaveTheAve has?

> **DaveTheAve said:**
> P.S. I'm still stuck with the error message with the compiling posted above.

Finally an answer, although minijoe already made a packet for feisty. These are the instructions to build your own moblock packages (in this example for version 0.8-23. The source of the versions 0.8-23, 0.8-23+feisty and 0.8-23+gutsy is always the same.)

**Make a directory:**
```
mkdir foo
cd foo
```

**Get the build dependenies:**
```
apt-get build-dep moblock
```
or install the build dependencies manually instead: debhelper (>= 4.0.0), iptables-dev, dpatch, libnetfilter-queue-dev, libnfnetlink-dev

**Get the source:**
```
apt-get source moblock
```
or get the source manually instead:
```
wget http://moblock-deb.sourceforge.net/debian/dists/sid/main/source/net/moblock_0.8.orig.tar.gz
wget http://moblock-deb.sourceforge.net/debian/dists/sid/main/source/net/moblock_0.8-23.diff.gz
wget http://moblock-deb.sourceforge.net/debian/dists/sid/main/source/net/moblock_0.8-23.dsc
tar xvzf moblock_0.8.orig.tar.gz
zcat moblock_0.8-23.diff.gz | patch --strip=0
chmod +x debian/rules
```

or take the actual development version (normally there are no or not much differences to the released version) instead:
```
svn co https://moblock-deb.svn.sourceforge.net/svnroot/moblock-deb/moblock moblock-deb
```

**Compile and build the package:**
```
cd moblock-0.8
dpkg-buildpackage -rfakeroot
```

@wilberfan:
Huh, never seen this error messages ("NFNETLINK answers: Invalid argument"). And google has it only 4 times, including you.
Did it work before you did the "restart"?
 Which distro are you using (feisty!?), which kernel version? Are you on i386 or amd64? What's the version of your moblock .deb (0.8-23+feisty !?)? I guess you are using the -nfq version!?
Are all kernel modules loaded correctly ("lsmod")?
Did you change any configuration files or anything else (if yes, then "purge" moblock and then reinstall it)? Or post/send me your configuration file so that I can check it for errors.

greets
jre

---

### Post by wilberfan on 2007-10-10
> @wilberfan:
Huh, never seen this error messages ("NFNETLINK answers: Invalid argument"). And google has it only 4 times, including you.
Did it work before you did the "restart"?
 Which distro are you using (feisty!?), which kernel version? Are you on i386 or amd64? What's the version of your moblock .deb (0.8-23+feisty !?)? I guess you are using the -nfq version!?
Are all kernel modules loaded correctly ("lsmod")?
Did you change any configuration files or anything else (if yes, then "purge" moblock and then reinstall it)? Or post/send me your configuration file so that I can check it for errors.
jre

Well, I am  getting that error under Debian Sid (specifically, Sidux).   MoBlock DID work properly the first day I installed it--I remember having to wrestle with changing settings to let Thunderbird get access to my pop servers...  A couple of days later, (Beginning, perhaps, yesterday?)  I was getting that NFNETLINK message...

(I have done a dist-upgrade--which, for those unfamiliar with Sidux--is always the latest of everything from the Debian Sid repos--including the latest kernel, etc...  I have no idea if/how that would effect moblock!)

I currently have Gutsy 64-bit installed on one box--but I thought I'd try moblock out first under my (32-bit) Debian (Sidux).

Here's my moblock.config file:

```
# moblock-control configuration file

# This file is sourced by a bash script. Any line which starts with a # (hash) 
# is a comment and is ignored. If you set the same variable several times, 
# then only the last line will be used. You have to stop/restart/reload moblock
# if you change entries.

############################ General configuration ############################

# Specify the format of the blocklists that you use. You can´t mix different
# formats.
# d - eMule ipfilter.dat format
# n - peerguardian .p2b v2 binary format
# p - peerguardian .p2p text format
BLOCKLIST_FORMAT="p"

# Specify a NFQUEUE queue number (default 0)
# Works only with -nfq version
NFQUEUE_NUMBER="0"

# Turn on/off automatic start
# 0 - Don´t start MoBlock at system boot
# 1 - Start MoBlock at system boot
MOBLOCK_INIT="0"

# Turn on/off automatic blocklist update
# 0 - Don´t update the blocklists automatically
# 1 - Update the blocklists automatically
MOBLOCK_CRON="1"


################## Settings for the iptables firewall rules ###################

# MoBlock requires the iptables rule NFQUEUE (nfq version)
# or the deprecated QUEUE (ipq version).

# Do a "moblock-control stop" before you change these iptables settings.

# Define how traffic is sent to MoBlock
# 0 - Don't set any iptables rules.
#     You or another script/firewall has to do this!
# 1 - NFQUEUE is in the chains moblock_in, moblock_out and moblock_fw.
IPTABLES_SETTINGS="1"

# Define when traffic is sent to the chain that contains NFQUEUE
# This section works only for IPTABLES_SETTINGS="1"
# 0 - Do nothing. You or another script/firewall has to do this!
# 1 - Insert the rules at the head of the chains.
# 2 - Append the rules to the end of the chains.
IPTABLES_ACTIVATION="2"

# Define which traffic shall be sent to NFQUEUE (if it is sent there).
# 0 - All traffic
# 1 - Only NEW traffic
IPTABLES_STATE="1"

############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name.
# Seperate several entries with whitespace (" ")

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT=""
#WHITE_TCP_OUT="http https"
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""

################################ Whitelist IPs ################################

# Whitelist either a network name, a hostname (please note that specifying any
# name to be resolved with a remote query such as DNS is a really bad idea), a
# network IP address (with /mask), or a plain IP address.
# The mask can be either a network mask or a plain number, specifying the number
# of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent
# to 255.255.255.0.
# Seperate several entries with whitespace (" ")

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

IP_TCP_IN=""
IP_UDP_IN=""
IP_TCP_OUT=""
IP_UDP_OUT=""
IP_TCP_FORWARD=""
IP_UDP_FORWARD=""

###################### Remove lines from the blocklist ########################

# Remove lines from the blocklist
# Seperate lines with a semicolon. The example will delete lines that contain 
# either "Bogon", "General Electric Company" or "4.2.162.144-4.2.162.151"
#IP_REMOVE="Bogon;General Electric Company;4.2.162.144-4.2.162.151"

# Do a "moblock-control reload" when you have changed these settings.
IP_REMOVE=""

########################### Full LSB compatibility ############################

# The control script uses /lib/lsb/init-functions. In Debian this file also
# provides functions which are not defined by the LSB standard. Change this
# entry if the script complains of not knowing a function.
# 0 - Debian compatible system (default)
# 1 - LSB 3.1 but not Debian compatible system
LSB_MODE=0
```

---

### Post by quixotic-cynic on 2007-10-10
Whilst I don't specifically know how to solve the problem my best guess, based on intuition, is that somehow the netfilter package that moblock depends upon has been screwed up somehow in the update and is either broken or something else is causing it problems.

I would try purging that package and reinstalling it (rather than the moblock one) and, if that does not solve the problem, devoting your investigation in that direction.

Probably not a major insight, but that is the best thing I can think of atm.

---

### Post by fwojciec on 2007-10-10
@wilberfan : funny you should mention that... I just had the same error a moment ago.  seems to be caused by the new 2.6.23 kernel (check what your sidux install is using) - I reverted to 2.6.22.9 and everything is working, for now, but it is something that will need to be dealt with somehow in the future...

I did try updating all moblock deps to the latest versions, but that didn't help so I think it's the kernel itself.

---

### Post by wilberfan on 2007-10-10
Sorry, which *specific* package are  you suggesting I try removing and reinstalling?   I just did one of these

```
apt-get remove --purge libnetfilter-queue1
``` 

But it uninstalled moblock-nfq as well...

---

### Post by wilberfan on 2007-10-10
> **fwojciec said:**
> @wilberfan : funny you should mention that... I just had the same error a moment ago.  seems to be caused by the new 2.6.23 kernel (check what your sidux install is using) - I reverted to 2.6.22.9 and everything is working, for now, but it is something that will need to be dealt with somehow in the future...

I did try updating all moblock deps to the latest versions, but that didn't help so I think it's the kernel itself.

You know, I was wondering about that...cuz I upgraded to 2.6.23 on both machines yesterday/today...

Thanks for the hint...!

[EDIT]  I just installed MoBlock on my 64-bit Gutsy via the .deb, and it seems to be working OK.   Lends credence to our 'kernel theory'...?  (Gutsy is using 2.6.22-13 at the moment?)

---

### Post by fwojciec on 2007-10-10
I just filed a bug report on moblock website, we'll see how that goes...

---

### Post by abelstern on 2007-10-11
[SIZE=1]I looked through the changes in linux 2.6.23 and this seems to be due to the recent change in nf_queue.c: 
        if (pf >= NPROTO)
                return -EINVAL;
 was added to nf_register_queue_handler, and this seems to be where the moblock syscall fails.  I hope somebody fixes this.. in the mean time I've patched my kernel to revert the 2.6.23 change in nf_queue.c.

Actually I think the problem lies with libnetfilter_queue rather than with moblock, but their Bugzilla server is down so I can't file a bug.[/SIZE] 

> **abelstern said:**
> I made a stupid mistake; booted into 2.6.22 instead of the patched 2.6.23. Therefore, my post isn't valid: the problem must lie elsewhere. I'm currently compiling 2.6.23 with netfilter debugging to try to find the cause of all this.

---

### Post by fwojciec on 2007-10-11
> **abelstern said:**
> I looked through the changes in linux 2.6.23 and this seems to be due to the recent change in nf_queue.c: 
        if (pf >= NPROTO)
                return -EINVAL;
 was added to nf_register_queue_handler, and this seems to be where the moblock syscall fails. The moblock developers don't seem to be very active, but I hope somebody fixes this.. in the mean time I've patched my kernel to revert the 2.6.23 change in nf_queue.c.

So patching the kernel would just involve removing those two lines from nf_queue.c?  If so, that's not too bad - I compile my own kernels anyways...

Thanks for the info, btw, I've added that to the bugreport.

---

### Post by quixotic-cynic on 2007-10-11
> **wilberfan said:**
> Sorry, which *specific* package are  you suggesting I try removing and reinstalling?   I just did one of these

```
apt-get remove --purge libnetfilter-queue1
``` 

But it uninstalled moblock-nfq as well...

That was what I meant. Since moblock-nfq had it as a dependency I guess apt-get auto-removed moblock too (i'm used to using aptitude). It's not a problem though -  since moblock-nfq was not purged and thus you don't loose all your config changes when re-installing it.

---

### Post by abelstern on 2007-10-11
> **fwojciec said:**
> So patching the kernel would just involve removing those two lines from nf_queue.c?  If so, that's not too bad - I compile my own kernels anyways...

Thanks for the info, btw, I've added that to the bugreport.

I made a stupid mistake; booted into 2.6.22 instead of the patched 2.6.23. Therefore, my post isn't valid: the problem must lie elsewhere. I'm currently compiling 2.6.23 with netfilter debugging to try to find the cause of all this.

---

### Post by smartboyathome on 2007-10-11
I am new to Moblock as well, and it blocks Pidgin from connecting. How would I enable it to access?

---

### Post by quixotic-cynic on 2007-10-11
> **smartboyathome said:**
> I am new to Moblock as well, and it blocks Pidgin from connecting. How would I enable it to access?

Find out what is being blocked by looking in /var/log/moblock.log

Edit /etc/moblock/moblock.conf and add the IPs that you want to unblock to the exclude section...

---

### Post by tipsqueal on 2007-10-11
So I installed Moblock today and followed the instructions and it still blocks all of my HTTP traffic. With Moblock on I cannot access any webpages at all. 

YES I did delete the hash in the configuration file on line 68.
YES I did restart moblock (even my computer a few times)
YES I did re-install with no luck.
and YES after doing all of that it still blocks my http traffic. 

Can anyone please help?

Thanks, 
Tipsqueal.

[edit] It apparently blocks my all of my GAIM traffic (port 5190) and the traffic that the weather applet uses too.

---

### Post by fwojciec on 2007-10-11
> **abelstern said:**
> I made a stupid mistake; booted into 2.6.22 instead of the patched 2.6.23. Therefore, my post isn't valid: the problem must lie elsewhere. I'm currently compiling 2.6.23 with netfilter debugging to try to find the cause of all this.

The Moblock developer has provided a temporary fix for the 2.6.23 kernel - you'll find it in the bug report [here]("https://developer.berlios.de/bugs/?func=detailbug&bug_id=12156&group_id=2509").

---

### Post by pelle.k on 2007-10-11
> **tipsqueal said:**
> Can anyone please help?


```
sudo moblock-control status
```
paste the output here...

---

### Post by tipsqueal on 2007-10-11
it says:
> 
Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT 18768 packets, 19M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    2   100 ACCEPT     0    --  lo     any     anywhere             anywhere            
    0     0 ACCEPT     0    --  lo     any     anywhere             anywhere            
   44  2200 ACCEPT     0    --  lo     any     anywhere             anywhere            
    2   100 ACCEPT     0    --  lo     any     anywhere             anywhere            
    0     0 moblock_in  0    --  any    any     anywhere             anywhere            state NEW 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 moblock_fw  0    --  any    any     anywhere             anywhere            state NEW 

Chain OUTPUT (policy ACCEPT 18996 packets, 3108K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    2   100 ACCEPT     0    --  any    lo      anywhere             anywhere            
    0     0 ACCEPT     0    --  any    lo      anywhere             anywhere            
   44  2200 ACCEPT     0    --  any    lo      anywhere             anywhere            
    2   100 ACCEPT     0    --  any    lo      anywhere             anywhere            
    0     0 moblock_out  0    --  any    any     anywhere             anywhere            state NEW 

Chain moblock_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  any    any     anywhere             anywhere            NFQUEUE num 0

Chain moblock_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  any    any     anywhere             anywhere            NFQUEUE num 0

Chain moblock_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     tcp  --  any    any     anywhere             anywhere            tcp dpt:https 
    0     0 RETURN     tcp  --  any    any     anywhere             anywhere            tcp dpt:www 
    0     0 NFQUEUE    0    --  any    any     anywhere             anywhere            NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * moblock is running, pid is 10537.


Hope that helps...

---

### Post by pelle.k on 2007-10-12
> Chain INPUT (policy ACCEPT 18768 packets, 19M bytes)
pkts bytes target prot opt in out source destination
2 100 ACCEPT 0 -- lo any anywhere anywhere
0 0 ACCEPT 0 -- lo any anywhere anywhere
44 2200 ACCEPT 0 -- lo any anywhere anywhere
2 100 ACCEPT 0 -- lo any anywhere anywhere
0 0 moblock_in 0 -- any any anywhere anywhere state NEW
Your input output chains look a bit odd. Is this some iptables configuration i don't recognize, or is it simply broken somehow.
I only have one RETURN target before moblock_*, not 4 ACCEPT.
Can anyone on feisty confirm?

---

### Post by Scruffynerf on 2007-10-12
HI all,

I've just updated from an older version of Moblock (using the old 'unstable' repo to the current one on page 1, and I've noticed that the Gnome Panel Weather applet cannot update successfully.

If relevant, the weather update is pointing to the server for Adelaide, Australia.

Now, how can I go about finding what IP or Port that I need to whitelist, and how do I do it?

many thanks for any and all help.

cheers

Scruffy

Edit: Moblock Status Report:
```
 Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT 303K packets, 257M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    2   100 ACCEPT     0    --  lo     any     anywhere             anywhere            
   44  4107 ACCEPT     0    --  lo     any     anywhere             anywhere            
 2267  237K moblock_in  0    --  any    any     anywhere             anywhere            state NEW 
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 moblock_fw  0    --  any    any     anywhere             anywhere            state NEW 
Chain OUTPUT (policy ACCEPT 273K packets, 199M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    2   100 ACCEPT     0    --  any    lo      anywhere             anywhere            
   44  4107 ACCEPT     0    --  any    lo      anywhere             anywhere            
  985  120K moblock_out  0    --  any    any     anywhere             anywhere            state NEW 
Chain moblock_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  any    any     anywhere             anywhere            NFQUEUE num 0
Chain moblock_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 2267  237K NFQUEUE    0    --  any    any     anywhere             anywhere            NFQUEUE num 0
Chain moblock_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     tcp  --  any    any     anywhere             anywhere            tcp dpt:https 
    8   480 RETURN     tcp  --  any    any     anywhere             anywhere            tcp dpt:www 
  977  119K NFQUEUE    0    --  any    any     anywhere             anywhere            NFQUEUE num 0
Please check if the above printed iptables rules are correct!
 * moblock is running, pid is 8203.
 
```

Also I note that [www.google.com](www.google.com) is now blocked !

EDIT: SOLVED THE PROBLEM!

```
sudo gedit /etc/moblock/blocklists.list
```

Locate lines 22, 23 & 24 - they are the ones referring to IANA. Comment them out.

Then: 
```
 sudo moblock-control reload 
```

And after a short time, the weather update and websites such as Google will be back.

---

### Post by quixotic-cynic on 2007-10-12
> **pelle.k said:**
> Your input output chains look a bit odd. Is this some iptables configuration i don't recognize, or is it simply broken somehow.
I only have one RETURN target before moblock_*, not 4 ACCEPT.
Can anyone on feisty confirm?

Hi, pelle.k, here is my one:

```
Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     0    --  lo     any     anywhere             anywhere            
    0     0 moblock_in  0    --  any    any     anywhere             anywhere            state NEW 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 moblock_fw  0    --  any    any     anywhere             anywhere            state NEW 

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     0    --  any    lo      anywhere             anywhere            
    0     0 moblock_out  0    --  any    any     anywhere             anywhere            state NEW 

Chain moblock_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  any    any     anywhere             anywhere            NFQUEUE num 0

Chain moblock_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  any    any     anywhere             anywhere            NFQUEUE num 0

Chain moblock_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  any    any     anywhere             anywhere            NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * moblock is running, pid is 6360.
```

So the strange lines would appear to be:

```
2 100 ACCEPT 0 -- lo any anywhere anywhere
44 2200 ACCEPT 0 -- lo any anywhere anywhere
2 100 ACCEPT 0 -- lo any anywhere anywhere
```

---

### Post by belgofac117 on 2007-10-13
Hi,

Long time Windows user, just recently started with Linux and have a quintuple boot sys with XP, Vista, PcLinux 2007, Ubuntu 6.10 and Kubuntu 7.04. I have Moblock running in Ubuntu but Kubuntu is giving me some probs.

It seems to be blocking almost everythin but when I ping Microsoft nothing shows up in the logfile and get ¨packet filtered¨ bla bla in the ping terminal.

Here are a few tests I ran.

pidof moblock
6015




tail -f /var/log/moblock.log

Merged range 'Easynet UK', with range 'Easynet UK'
Ranges loaded: 238346
Merged ranges: 265
Skipped useless ranges: 6898
NFQUEUE: binding to queue '0'
Blocked OUT: New Dream Network, LLC,hits: 1,DST: 208.113.142.250
Blocked OUT: Max-Planck-Institut fur Plasmaphysik (IPP),hits: 1,DST: 130.183.3.145
Blocked OUT: New Dream Network, LLC,hits: 2,DST: 208.113.140.203
Blocked OUT: Opera Software,hits: 1,DST: 193.69.116.32
Blocked OUT: BBC,hits: 1,DST: 212.58.226.73
Blocked OUT: BBC,hits: 2,DST: 212.58.226.77
Blocked OUT: BBC,hits: 3,DST: 212.58.226.77
Blocked OUT: BBC,hits: 4,DST: 212.58.226.77
Blocked OUT: BBC,hits: 5,DST: 212.58.226.77
Blocked OUT: BBC,hits: 6,DST: 212.58.226.77
Blocked OUT: BBC,hits: 7,DST: 212.58.226.77



ping microsoft.com

PING microsoft.com (207.46.232.182) 56(84) bytes of data.
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=24 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=42 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=43 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=144 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=145 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=238 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=255 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=394 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=395 Packet filtered
From 207.46.35.134 icmp_seq=396 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=433 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=446 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=447 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=448 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=515 Packet filtered
From po14.tuk-65ns-mcs-1a.ntwk.msn.net (207.46.35.134) icmp_seq=516 Packet filtered


Edit:

When I visit the MS page, MS will get blocked however.

> Blocked OUT: NetIQ,hits: 1,DST: 63.88.212.184
Blocked OUT: Microsoft Corp,hits: 1,DST: 207.46.18.254
Blocked OUT: NetIQ,hits: 2,DST: 63.88.212.184
Blocked OUT: Microsoft Corp,hits: 2,DST: 207.46.18.254
Blocked OUT: NetIQ,hits: 3,DST: 63.88.212.184
Blocked OUT: Microsoft Corp,hits: 3,DST: 207.46.18.254
Blocked OUT: NetIQ,hits: 4,DST: 63.88.212.184
Blocked OUT: Microsoft Corp,hits: 4,DST: 207.46.18.254
                                                        


regards,

---

### Post by daradib on 2007-10-13
If you want to make your own moblock binary package from source and install it, you can use the following instructions. This worked for me on Ubuntu Gutsy 64-bit, but it should work on any system. Tell me how it goes.

```

mkdir moblock
cd moblock
sudo apt-get build-dep -y moblock
apt-get source moblock
cd moblock-*
dpkg-buildpackage -rfakeroot
cd ..
sudo dpkg -i moblock-nfq*.deb
sudo apt-get purge -y iptables-dev libnetfilter-queue-dev libnfnetlink-dev
sudo apt-get install -f

```

Some of these commands can be combined into one, but this lets you make changes like adding a patch if necessary and explains the process better.

These commands make the directory moblock and then changes the current working directory to it. It then installs moblock's development dependencies. The moblock source package is downloaded and changes the current working directory to it. The source and binary packages are built and the working directory moves one directory up. Then the moblock-nfq*.deb is installed and its dependencies are installed. Finally, the development dependencies (including configuration files) are removed.

---

### Post by belgofac117 on 2007-10-13
A new problem has arrived.  Moblock is suddenly blocking all http traffic via any search engine.  Google and Yahoo gets blocked.

I still want to keep HTTP blocked and only let searches via Google and Yahoo to get through.  How do I go about that?

I have already read all 75 pages yesterday to solve other problems.:popcorn:

What I mean: what and where do I put the IP ranges for Google?

---

### Post by belgofac117 on 2007-10-13
I have tried the following to solve the above problem:

Uncommented the Iana lines > no result

Still everything blocked.  Have to switch to xp to even log in here.:confused:   Why did it work in the first place?

---

### Post by gav616 on 2007-10-13
> **belgofac117 said:**
> A new problem has arrived.  Moblock is suddenly blocking all http traffic via any search engine.  Google and Yahoo gets blocked.

I still want to keep HTTP blocked and only let searches via Google and Yahoo to get through.  How do I go about that?

I have already read all 75 pages yesterday to solve other problems.:popcorn:

What I mean: what and where do I put the IP ranges for Google?

Hi,
In your '/etc/moblock/blocklists.list' have you uncommented the 'Spiders' list?
if soo, you need to re-comment it, like so;
```
# bluetack.co.uk/config/spider.gz
```
then, 'stop', 'update', 'restart' then 'reload' moblock, like so;
```
sudo moblock-control stop
sudo moblock-control update
sudo moblock-control restart
sudo moblock-control reload
```
hope that helps.

If your inexperienced with using blocklists just use the ones that you need i.e. level1, using too many can cause conflicts.

---

### Post by belgofac117 on 2007-10-14
Unfortunately the advice came a bit too late.:lolflag:

 After changing /etc/moblock/moblock.conf I performed a reload and Kubuntu completely froze.  The only way to get out was a hard reboot.  After this I cannot get into Kubuntu anymore.  The startscreen appears but at the end of the startup cycle, Kubu hangs and then goes to a alternate screen where it says:  "fsck dies with exit status 1" and "Mount: special device .dev/dsk/by-uuid/463a-19b5 does not exist" and from there on nothing happens.

I had a look into the files of Kubuntu via PcLinux and corrected the moblock file but this didn't help.  Is there another file that I could edit to fix this?

---

### Post by pelle.k on 2007-10-14
> I had a look into the files of Kubuntu via PcLinux and corrected the moblock file but this didn't help. Is there another file that I could edit to fix this?
The problem you have is not with moblock. You computer froze, probably while writing some stuff to the kubuntu root partition, and thus it's "broken". I can only recommend that you run "fsck.ext3 -fp /dev/<insert device here>" as root in pclinuxos.

---

### Post by jre on 2007-10-14
belgoflac, I don't think that your fsck/mount problem is related to moblock.

General: Have a look at /usr/share/doc/moblock-nfq/README.blocklists.gz to get an idea which lists are used. Then you will see that the spider list is more than Google and Yahoo. You can also look directly at the lists (/var/spool/moblock/...).

I don't know why not using the IANA lists should fix problems with Google/Yahoo/Weather Panel. Of course these lists also can cause problems, just others ;-)

So, if google and yahoo are your friends then my advice is to set in moblock.conf
```
IP_REMOVE="google;yahoo"
```.
Alternatively you can "tail -f /var/log/moblock.conf" while using google and yahoo and add the blocked IPs to IP_TCP_OUT="..."

---

### Post by tipsqueal on 2007-10-14
> **Scruffynerf said:**
> 

EDIT: SOLVED THE PROBLEM!

```
sudo gedit /etc/moblock/blocklists.list
```

Locate lines 22, 23 & 24 - they are the ones referring to IANA. Comment them out.

Then: 
```
 sudo moblock-control reload 
```

And after a short time, the weather update and websites such as Google will be back.


Thanks that helped a lot! Although it still blocks my Evolution email client from getting my Gmail mail. Anyone have any ideas?

Thanks,
Tipsqueal

---

### Post by pelle.k on 2007-10-14
I've updated the FAQ to help you solve your problem.

---

### Post by tipsqueal on 2007-10-14
I solved the Gmail problem by whitelisting two ports that Gmail required to be open. I don't remember what ports they were, but you can find it in the help section of Gmail that discusses setting up POP.

---

### Post by gav616 on 2007-10-16
Hi,

say i go to one of my favourite sites (not knowing its anti-p2p) and  realise its being block by moblock (beacuse using a list that blocks it and http;https is commented out), so i add a couple of the blocked  ips  to the white tcp out list.

although now i would be able to access the website what about the warez i'm downloading with bittorrent on port 5****?

won't there be the potential  that the site i've unblocked for browsing beng able to connect to me through the p2p client?

you see this is why i think 'system wide blocking in this case doesn't work.

for the system broadcasting/processes etc.. i.e...
IANA
LAN blocking
bogon
and spersific http blacklists i.e. AD servers...
moblock works great.

It would work best imo if you could just, say, bind moblock to certain programs i.e. p2p aps (BT, amule).
This working beacuse you woulded have to unblock anything, including http access to and from that spersific program. This is why emules updated IPfilter can contain vitually all the blocklist including spiders list (All google, yahoo) and if you used the same in moblock it would block nearly all websites!

What im basically asking is it more secure, less secure?, pros?, cons? in using ip blocking only on the spersific ports/programs that need it. i.e.
ADS lists only used on all http/https access
iana/bogon/lan lists used system wide
and level1/templist/spiders only in the the programs you need it. (without having to unblock anything.

correct me if im wrong :KS...

rant..

---

### Post by pelle.k on 2007-10-16
Listen, it doen't serve you to be this paranoid.
Like always, the only thing we can do is add "layers" of protection, and if that doesn't work, so be it. The only thing we can do is try.
I tell you, there's not a single computer on the net that is perfectly safe. If a hacker want's in, in theory ha can, it's just a matter of time and persistance (could be a minute or a hundred years, but still).

The fact is, that if you whitelist a specific ip _out, that means you will only allow new connections _out, not _in.
Of course you allow RELATED connections in, but those are only invited in by you initiating a connection *first*. Like with firefox, (you contact ip xxx.xxx.xxx.xxx, that ip replies).

Sure that could be a bad guy, but do you really think these blocklists are 100% correct? I would say you are probably contacting *far* more bad IP:s without knowing it because these lists are incomplete in some way, so worrying about a few whitelisted IP:s dont really serve you, IMHO.

---

### Post by gav616 on 2007-10-16
thank you for your reply, i see your point entirely.

p.s. keep up the good work, nice guide :)

p.p.s. 'The leading causes of death in the United States are: 1. Heart Disease 2. Chuck Norris 3. Cancer'

---

### Post by quixotic-cynic on 2007-10-16
> **pelle.k said:**
> Listen, it doesn't serve you to be this paranoid.

What?!?! Heresy!!!!  ;)

---

### Post by pelle.k on 2007-10-16
:)

---

### Post by jre on 2007-10-16
I just released moblock 0.8-26. It includes the "patch" from upstream for the kernel 2.6.23 problem. Since gutsy still fails to build here I recommend gutsy users to build the package manually.
Debian package changelog: [http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/moblock/moblock-0.8/moblock-0.8/debian/changelog?view=markup](http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/moblock/moblock-0.8/moblock-0.8/debian/changelog?view=markup)

greets
jre

---

### Post by daradib on 2007-10-16
I have created a page on the Ubuntu Community Documentation. If you don't mind, pelle.k, I'd like you to take a look at it (corrections, edits, comments). It can be used to maintain the howto up to date. Instructions for FireHOL users and apparently the new packages need to be added on to the page.

[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

---

### Post by daradib on 2007-10-16
I could not get the source package for moblock gutsy 0.8.26 (0.8.21 is the latest provided) so that I could compile it. I will try again tomorrow to see if the server has been updated. If not, should I use the Feisty source packages to compile a binary Gutsy 64-bit package?

---

### Post by pelle.k on 2007-10-17
Cool! I might even consider linking there, and use that as the "howto" instead. It seems it would be more trouble updating both guides, than to maintain just one of them...
Is that what you had in mind?

---

### Post by dodoalien on 2007-10-17
hi, im using 7.04
until yesterday the ***moblock-control test*** worked, today i downloaded the update, tried the test but it says:

```
 * MoBlock did not block the IP. Test failed.
 * Have a look at "/usr/bin/moblock-control status"
```
ok i read that there is a problem with the test, but there is a mode to test it? any ping or something?

i dont have any BLOCK in *tail -f /var/log/moblock.log*, just
```

...
[infinite Skipping useless range items]
...
Ranges loaded: 245274
Merged ranges: 320
Skipped useless ranges: 5586
moblock-control: trying to ping 4.18.162.102 from /etc/moblock/guarding.p2p ...
NFQUEUE: binding to queue '0'
Got SIGTERM! Dumping stats and exiting.

```

thx

---

### Post by jre on 2007-10-17
> **daradib said:**
> I could not get the source package for moblock gutsy 0.8.26 (0.8.21 is the latest provided) so that I could compile it. I will try again tomorrow to see if the server has been updated. If not, should I use the Feisty source packages to compile a binary Gutsy 64-bit package?

daradib, I can't compile Gutsy currently (I don't know why it doesn't work, remember I make the packages under a Debian system with "pbuilder"). And since I can't compile them the source doesn't get uploaded ...
But you can use any other (sid, etch, lenny, feisty) entry for your sources.list - the source is always the same.

@dodoalien: I think you just have to wait a bit longer until moblock has loaded it's whole configuration. And by the way: the "test" pings the first IP of the blockfile and then checks the logfile if this IP was blocked.

jre

---

### Post by dodoalien on 2007-10-17
> **jre said:**
> @dodoalien: I think you just have to wait a bit longer until moblock has loaded it's whole configuration. And by the way: the "test" pings the first IP of the blockfile and then checks the logfile if this IP was blocked.

i have waited (since i booted my pc 4 hours ago, is enought? ;)) and nothing changed.

```
sudo moblock-control test
Testing MoBlock: trying to ping 4.18.162.102 from /etc/moblock/guarding.p2p ...
 * MoBlock did not block the IP. Test failed.
 * Have a look at "/usr/bin/moblock-control status"

```

```
tail -f /var/log/moblock.log
Skipping useless range: (050327) W32.Spybot 1433
Skipping useless range: (050309) W32.Rahack 4899
Skipping useless range: (050428) W32.Spybot 1433 6000
Skipping useless range: (050412) W32.Rahack 4899
Skipping useless range: (050326) Unassigned 33437
Ranges loaded: 245274
Merged ranges: 320
Skipped useless ranges: 5586
moblock-control: trying to ping 4.18.162.102 from /etc/moblock/guarding.p2p ...

```

moblock can work with firestarter? can firestarter be the "problem"?

---

### Post by quixotic-cynic on 2007-10-17
> **dodoalien said:**
> moblock can work with firestarter? can firestarter be the "problem"?

moblock cannot work with firestarter - the problem is mentioned in the howto on thread page 1...

> * Firestarter (most iptables firewalls) does not work with moblock ATM

Pleeeeeeaassseee, read stuff, oki? ^_^

---

### Post by dodoalien on 2007-10-17
ops, but i got FS up yesterday and all was ok... mistery ;)

im going to remove it then :) thx



EDIT:
yep removed FS, rebooted, and now all is ok...

sorry mates :)

---

### Post by quixotic-cynic on 2007-10-17
pelle.k and jre - off topic, but why do you use debian (iirc) and not ubuntu - I'm just curious...

Edit: I ran dpkg-buildpackage under gutsy so are they gutsy packages or feisty ones? :confused:

Why isn't the source for 0.8-26 copied into the gutsy folder too?

---

### Post by c1rcu17 on 2007-10-17
I'm relatively new to ubuntu, and I'm trying to install moblock. I got everything installed, but It seems that moblock is having a hard time starting up. I'm on Ubuntu 7.10 fully updated. I'm getting the message 

>  sudo moblock-control test
Testing MoBlock: head: cannot open `/etc/moblock/guarding.p2p' for reading: No such file or directory
trying to ping  from /etc/moblock/guarding.p2p ...
tail: cannot open `/var/log/moblock.log' for reading: No such file or directory
 * MoBlock did not block the IP. Test failed.


I tried a manual update, restarting moblock to no avail.
When i tried an update, all i got is 

> sudo moblock-control update
Updating blocklists and reloading MoBlock if any blocklist was updated

any help would be appreciated

---

### Post by glotz on 2007-10-17
I suggest you instead of making a new thread make a wiki page. [https://wiki.ubuntu.com/MoBlock](https://wiki.ubuntu.com/MoBlock)

---

### Post by c1rcu17 on 2007-10-17
Correct me if I'm wrong, but Isn't the Ubuntu forum designed to help us newbies to use and understand Ubuntu? Well, I'm here with a legitimate question and I don't think making a wiki page just for a simple request for help will do much. I have already read the moblock documentations, searched the forums, and now, after exhausting all other means of getting answers, I am directly asking in a relevant forum thread. If you can't help me, please don't send me on some wild goose chase. Again, I greatly appreciate any help.

---

### Post by glotz on 2007-10-17
Dude, not talking to you but the original poster of this thread! :)

---

### Post by c1rcu17 on 2007-10-17
Ha Ha, oh... in that case, Yeah, make a Wik!!! ;)

---

### Post by daradib on 2007-10-17
pelle.k: yes, that is what I had in mind.

I have also attached an updated shell script (which installs dependencies and does not remove the generated debs) so they can be attached to this thread. The shell scripts should work on all recent Ubuntu releases (all architectures), but I have only tested it on Ubuntu Gutsy 64-bit.

I used the source package from feisty repository and created the following two debs. (I changed the top part of debian/changelog to the following (it was feisty before), so that the generated debs would be 0.8-26+gutsy not 0.8-26+feisty.
```

moblock (0.8-26+gutsy) gutsy; urgency=low

  * binary upload

 -- jre <jre-phoenix@users.sourceforge.net>  Tue, 16 Oct 2007 20:05:50 +0200
```

---

### Post by daradib on 2007-10-17
> **quixotic-cynic said:**
> 

Edit: I ran dpkg-buildpackage under gutsy so are they gutsy packages or feisty ones? :confused:

It appears to be Feisty because the the top part of debian/changelog has not been changed from Feisty to Gutsy. See my last post. I changed debian/changelog so that the packages would say Gutsy.

Why isn't the source for 0.8-26 copied into the gutsy folder too?[/QUOTE]

See [jre's last post]("http://ubuntuforums.org/showpost.php?p=3550341&postcount=770").

> **jre said:**
> 
I can't compile Gutsy currently (I don't know why it doesn't work, remember I make the packages under a Debian system with "pbuilder"). And since I can't compile them the source doesn't get uploaded ...
But you can use any other (sid, etch, lenny, feisty) entry for your sources.list - the source is always the same.


I guess you just have to change debian/changelog.

---

### Post by daradib on 2007-10-17
> **glotz said:**
> I suggest you instead of making a new thread make a wiki page. [https://wiki.ubuntu.com/MoBlock](https://wiki.ubuntu.com/MoBlock)

Actually, I created one. See it at [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

I would appreciate if people look over it to make sure there are not any mistakes and of course to improve/add.

---

### Post by glotz on 2007-10-17
Wow! Well done Sir, outstanding job!

---

### Post by pelle.k on 2007-10-17
> pelle.k and jre - off topic, but why do you use debian (iirc) and not ubuntu - I'm just curious... it shouldn't really matter if you run debian or ubuntu, just as long as you use pbuilder to compile in a chroot, of say, feisty or any other version of debian/ubuntu...
[edit] btw, i run gutsy :) [/edit]

---

### Post by wilberfan on 2007-10-17
As a follow-up to [my post]("http://ubuntuforums.org/showpost.php?p=3509046&postcount=728") from a week ago or so, I wanted to let everyone know that MoBlock seems to be working now on my Sidux install!  (Yay!)

I tend to keep Sidux up-to-date (that's the FUN of Sidux!), so I don't know if a different kernel made the difference, or....?   (At the moment, I'm running kernel 2.6.23.1-slh-smp-3?)

I always like to try and understand why something works (or doesn't)--any idea what would have changed in the last week or so that would make MoBlock run OK now?

---

### Post by quixotic-cynic on 2007-10-18
> **c1rcu17 said:**
> I got everything installed, but It seems that moblock is having a hard time starting up. I'm on Ubuntu 7.10 fully updated. I'm getting the message:

```
sudo moblock-control test
Testing MoBlock: head: cannot open `/etc/moblock/guarding.p2p' for reading: No such file or directory
trying to ping from /etc/moblock/guarding.p2p ...
tail: cannot open `/var/log/moblock.log' for reading: No such file or directory
* MoBlock did not block the IP. Test failed.
```

Check that the /etc/moblock/guarding.p2p and /var/log/moblock.log exist, using a file manager or a terminal /w the cd & ls commands. If they don't then either try a reinstall (and actually purge the config files too) or try creating the two files (just blank ones using a text editor via sudo - eg *sudo gedit* in a terminal) and then re-update.

```
sudo aptitude purge moblock-nfq; sudo aptitude install moblock-nfq
``` would do a reinstall.

The update message looks fine.

**For daradib:**
Thanks for the suggestions. I found what I think is the debian/changelog, and edited the appropriate section, however, the files created are still labelled as feisty ones. I also tried changing the word feisty anywhere in the folders to gutsy and tried again but that didn't work either - guess I must have missed a few. I saw the one-liner about jre not putting up gutsy source because it wouldn't compile (fair enough, it's not my choice to make), but if I had moblock_0.8-26+*gutsy*.diff.gz would it not make the whole process much easier?

---

### Post by jre on 2007-10-18
quixotic-cynic: daradib basically said everything: you just have to change the first line in moblock-0.8/debian/changelog and your package will have a new name.
The source diff is created automatically when I do the compiling (everything is done by pbuilder/pdebuilder, dupload and debarchiver). Have a look at the script that I use to make the packages, to get an idea why I won't create this manually: [http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/stuff/admin/moblock-deb-packager.sh?view=log](http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/stuff/admin/moblock-deb-packager.sh?view=log)

wilberfan: Which moblock version are you using? I applied the "patch" from the upstream author in 0.8-26.
As I understood it it was a bug in the kernel.
Was the kernel or any library moblock depends on updated since you experienced the problem first?
moblock 0.8-26 + no relevant updates --> patch fixed the problem
moblock < 0.8-26 --> some other update fixed your problem; you have to tell us what was updated.
Please answer so that I know if I can remove the patch again.

OFFTOPIC discussion: I run Debian because, hmm, my brothers told me 8 years ago that it is a nice distro. At that time there was no Ubuntu. But I really like the "testing" version of Debian which is always quite actual AND stable. I prefer this to making every six months a dist upgrade.

c1rcu17: What's in /var/log/moblock-control.log when you do a "update"? I can only see that the update failed and that because of this you don't have the /etc/moblock/guarding.p2p.

dodoalien: I'm glad that everything is working now, you made me think that I released a buggy package ;-)

daradib: I had a quick look at the wiki although I didn't read it in depth, very nice - like its sources ;-)
- the test function should not have any problems any more (except when you 're reloading moblock at the same time)
- I missed a hint to turn off the daily update (via moblock.conf)
- it's not that important, but I'm the new maintainer of moblock-deb.sf.net, clessing unfortunately hasn't enough time now.

---

### Post by quixotic-cynic on 2007-10-18
> **jre said:**
> quixotic-cynic: daradib basically said everything: you just have to change the first line in moblock-0.8/debian/changelog and your package will have a new name.

Ok, thanks. I can do it now I think.

> **jre said:**
> The source diff is created automatically when I do the compiling (everything is done by pbuilder/pdebuilder, dupload and debarchiver). Have a look at the script that I use to make the packages, to get an idea why I won't create this manually: [http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/stuff/admin/moblock-deb-packager.sh?view=log](http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/stuff/admin/moblock-deb-packager.sh?view=log)

I understood why you didn't want to make .debs by hand, but didn't realise that the source files/packages where so difficult to create/customise.

> **jre said:**
> OFFTOPIC discussion: I run Debian because, hmm, my brothers told me 8 years ago that it is a nice distro. At that time there was no Ubuntu. But I really like the "testing" version of Debian which is always quite actual AND stable. I prefer this to making every six months a dist upgrade.

Thanks. I could ask more Qs but since it is so O-T I will go and do some research myself now I think.

---

### Post by daradib on 2007-10-18
> **jre said:**
> daradib: I had a quick look at the wiki although I didn't read it in depth, very nice - like its sources ;-)
- the test function should not have any problems any more (except when you 're reloading moblock at the same time)
- I missed a hint to turn off the daily update (via moblock.conf)
- it's not that important, but I'm the new maintainer of moblock-deb.sf.net, clessing unfortunately hasn't enough time now.

Thanks. I had a problem with the test function before (when I was using 0.8-21 on Gutsy 64-bit), but I don't have that issue with the new 0.8-26 Gutsy 64-bit package. I will keep that the text "The test has been known to have problems in older versions of MoBlock. Look at the log to check if you are unsure. This can be done interactively (this command will show you the log in real-time)." just to be sure, especially since there is no new Ubuntu Feisty 64-bit package.

I fixed everything else.

I also made a link to this thread under Further Reading. Should I point the link to the Linux forum of phoenixlabs.org instead?

---

### Post by belgofac117 on 2007-10-18
Hi Guys.Girls,

Here´s the continuation of my Linux adventures of last week.:lolflag:

Recollection of the events:  Moblock blocked all google, Yahoo traffic and through too much fiddling I lost Kubuntu, one of my quintuple boots.

After more fiddling I also lost PcLinuxOS.:mad:

Had to take a break and today re-installed PcLinuxOs and then Linux MInt.  Installed Moblock, inserted Google and Yahoo in Ip_Remove and Bob´s your uncle.:popcorn:

Thanks to all for your help.

---

### Post by gav616 on 2007-10-19
Hi,

I don't use any LAN, WAN, or want to broadcast anything out side my one non modem to pc setup, soo beacuse of this i use the blocklists IANA, non-LAN ect..

everyone will probpley know if your using these, it tends to block an IANA hit every minute or in my case ever 2 seconds, this i don't mind btw, its doing its job.

question is, how to i stop the IANA activity happerning in the first place? 
has it got anything to do with my modem with dhpc trying to assisign more IP's were there is no network, or is it sometinhg to do with requesting broadcasting from DNS?

or am i completey off the mark, if soo, throw me a bone here!

:) ta

---

### Post by jre on 2007-10-19
> **daradib said:**
> I also made a link to this thread under Further Reading. Should I point the link to the Linux forum of phoenixlabs.org instead?
Well for Ubuntu this here is a good place. Currently there's much more posting here then at phoenixlabs.
For general improvement discussions phoenixlabs is the better place

belgofac117, glad that everything is running now. I'm sure you learned much ;-)

gav616, I don't understand what you use the network for. If you don't do it then jsut try "/etc/init.d/networking stop".

jre

---

### Post by antharr on 2007-10-19
> eith@ubuntudesktop:~$ tail -f /var/log/moblock-control.log
Updating blocklists ...
Updating ads-trackers-and-bad-pr0n.gz * .
Updating bogon.gz * .
Updating dshield.gz * .
Updating hijacked.gz * .
Updating iana-multicast.gz * .
Updating iana-private.gz * .
Updating iana-reserved.gz * .
Updating level1.gz * .
Updating level2.gz


This all I am getting. It doesn't get past the updating phrase. I have even restarted the PC and it still sticks here. Any suggestions???

---

### Post by belgofac117 on 2007-10-20
Moblock is running fine in Mint Cassandra but I am having trouble with Firehol.  Installed Firehol as per page 1 but refuses to start.

My question:

1. With Moblock installed, why is it still so important to have a Firewall installed?

2. Is it not possible to block everything, including all ports
 in Moblock?

3.  Why is Firestarter working with Moblock in Ubuntu 6.10 but cannot work in higher versions?

The only thing I want to do is browse a bit with Firefox on the web without my pc getting scanned by unwanted organisations.

---

### Post by Dr. Nick on 2007-10-20
just a little tip for anyone having problems. I have gutsy and the newest moblock

It always said I failed the test when running **sudo moblock-control test **At times it gave messages saying it loaded 0 ranges etc.. and it never blocked a thing. The solution it so remove the iptables package which removes mobock. After this reinstall moblock. When removing iptables I would suggest purging the config files by using the "completely remove" option in synaptic as opposed to just regular uninstall.

It still fails the test but watching the tail on the logfile and trying to browse known blocked sites I can tell its blocking it

---

### Post by quixotic-cynic on 2007-10-21
> **gav616 said:**
> question is, how to i stop the IANA activity happening in the first place? has it got anything to do with my modem with dhpc trying to assisign more IP's were there is no network, or is it something to do with requesting broadcasting from DNS? or am i completely off the mark, if so, throw me a bone here! 

I can probably help with this but some more details would be useful. The most useful information is what IP or IP block range is being hit. Also useful would be exactly what your modem is (DSL Modem/Router?). Does your router have NAT translation and/or a firewall?

If others are connected to the router (probably not, from your description) you can get hits from broadcasts, or netbios, etc. With a router by itself and no other PCs connected then you can be getting hits from outside. Some people do not configure their NAT router properly (or disable the NAT function) and broadcast their own computer's local IP across the internet (esp. with bittorrent/p2p) and thus this shows up as blocks on your log if you run one of the applications.

If that is what is causing it, it is nothing to worry about (for you anyway, not so sure about the people you are blocking).

There can be other causes too (some people IP spoof in the IANA ranges, or use an IP outside of conventional ranges, etc)

---

### Post by quixotic-cynic on 2007-10-21
> **belgofac117 said:**
> With Moblock installed, why is it still so important to have a Firewall installed?

Type *netstat -l* in a terminal and look in the "Active Internet connections" section. localhost:???? entries only pay attention to packets from somewhere else on your pc (iirc) and thus are not a risk. Entries such as *:8342 indicate a server running on your pc. If the server is up to date and no vulnerabilities exist on it then anyone connecting to that server cannot do any damage, if not, then your pc is has a security vulnerability that can be exploited *unless you have a firewall that does not permit packets on that port*.

So, run netstat -l ... and if you *don't* have any *:port entries then you don't have anything to worry about (remember running or installing software may change this). If you do, then you may want a firewall to block the ports. If you have a NAT router to access the internet then you don't have to worry (except where you have forwarded ports or disabled the NAT function) since it acts as a firewall for inbound connections. 

To sum up, Moblock filters based on IP but to be secure from the above (real) risks then you need to filter by destination port on incoming connections too.

> **belgofac117 said:**
> Is it not possible to block everything, including all ports in Moblock?

Not afaik.

> **belgofac117 said:**
> Why is Firestarter working with Moblock in Ubuntu 6.10 but cannot work in higher versions?

I was unaware that it could - but then, I'm not sure I used both together in 6.10. If you want a firewall you can set moblock and then edit the iptables file to put in the port blocks. Takes a little more effort than firestarter but on the other hand you learn how firestarter actually works then. I guess you have to decide whether it is worth the effort of learning something new. 

> **belgofac117 said:**
> The only thing I want to do is browse a bit with Firefox on the web without my pc getting scanned by unwanted organisations.

Organisations can't "scan you" as such - they need you to initiate a connection to their web server to learn anything about you (Firefox doesn't act as a server - i.e. doesn't open a *:80 server on your pc or anything). You could use moblock to avoid connecting to sites that you don't want to connect to but there are better ways of protecting your 'privacy' online...

Privoxy with +hide-accept-language{block}, +hide-forwarded-for-headers, +hide-from-header{block}, +hide-if-modified-since{-1}, +hide-referrer{conditional-block}, +hide-user-agent{whatever you want here}, +crunch-incoming-cookies and +crunch-outgoing-cookies would be a good start. (You add exceptions for trusted sites by editing user.action through [http://config.privoxy.org/show-status](http://config.privoxy.org/show-status)).

You can also achieve most of this with a decent firefox config.

I wish everyone hid their user agent and then web site designers would have no idea which browser to design for and would have to make their page *shock/horror* standards compliant, instead of the infuriating "We are sorry but this website has been designed to function on Microsoft Internet Explorer please download the latest version from...". It's better than it used to be with FFx near 15% but it is still there for lesser-known browsers. Do they really have a right to tell us what browser we should be using?

*looks up* oopsie... >.<   *rant ends*

Anyway, I hope that helps a bit.  :)

---

### Post by c1rcu17 on 2007-10-21
So I'm having a problem with moblock. I have it installed with no other firewall software. I would like to run firestarter with it (wikki addition?) but I can mess with that later. I have moblock running with the lists updated. When i test moblock, it always fails. here is my moblock config file.

> # moblock-control configuration file

# This file is sourced by a bash script. Any line which starts with a # (hash) 
# is a comment and is ignored. If you set the same variable several times, 
# then only the last line will be used. You have to stop/restart/reload moblock
# if you change entries.

############################ General configuration ############################

# Specify the format of the blocklists that you use. You can´t mix different
# formats.
# d - eMule ipfilter.dat format
# n - peerguardian .p2b v2 binary format
# p - peerguardian .p2p text format
BLOCKLIST_FORMAT="p"

# Specify a NFQUEUE queue number (default 0)
# Works only with -nfq version
NFQUEUE_NUMBER="0"

# Turn on/off automatic start
# 0 - Don´t start MoBlock at system boot
# 1 - Start MoBlock at system boot
MOBLOCK_INIT="1"

# Turn on/off automatic blocklist update
# 0 - Don´t update the blocklists automatically
# 1 - Update the blocklists automatically
MOBLOCK_CRON="1"


################## Settings for the iptables firewall rules ###################

# MoBlock requires the iptables rule NFQUEUE (nfq version)
# or the deprecated QUEUE (ipq version).

# Do a "moblock-control stop" before you change these iptables settings.

# Define how traffic is sent to MoBlock
# 0 - Don't set any iptables rules.
#     You or another script/firewall has to do this!
# 1 - NFQUEUE is in the chains moblock_in, moblock_out and moblock_fw.
IPTABLES_SETTINGS="1"

# Define when traffic is sent to the chain that contains NFQUEUE
# This section works only for IPTABLES_SETTINGS="1"
# 0 - Do nothing. You or another script/firewall has to do this!
# 1 - Insert the rules at the head of the chains.
# 2 - Append the rules to the end of the chains.
IPTABLES_ACTIVATION="2"

# Define which traffic shall be sent to NFQUEUE (if it is sent there).
# 0 - All traffic
# 1 - Only NEW traffic
IPTABLES_STATE="1"

############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name.
# Seperate several entries with whitespace (" ")

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT=""
WHITE_TCP_OUT="http https"
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""

################################ Whitelist IPs ################################

# Whitelist either a network name, a hostname (please note that specifying any
# name to be resolved with a remote query such as DNS is a really bad idea), a
# network IP address (with /mask), or a plain IP address.
# The mask can be either a network mask or a plain number, specifying the number
# of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent
# to 255.255.255.0.
# Seperate several entries with whitespace (" ")

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

IP_TCP_IN=""
IP_UDP_IN=""
IP_TCP_OUT=""
IP_UDP_OUT=""
IP_TCP_FORWARD=""
IP_UDP_FORWARD=""

###################### Remove lines from the blocklist ########################

# Remove lines from the blocklist
# Seperate lines with a semicolon. The example will delete lines that contain 
# either "Bogon", "General Electric Company" or "4.2.162.144-4.2.162.151"
#IP_REMOVE="Bogon;General Electric Company;4.2.162.144-4.2.162.151"

# Do a "moblock-control reload" when you have changed these settings.
IP_REMOVE=""

########################### Full LSB compatibility ############################

# The control script uses /lib/lsb/init-functions. In Debian this file also
# provides functions which are not defined by the LSB standard. Change this
# entry if the script complains of not knowing a function.
# 0 - Debian compatible system (default)
# 1 - LSB 3.1 but not Debian compatible system
LSB_MODE=0

I need to know if i need to change something. I'm still new to Ubuntu, and I don't know anything about the iptables stuff. Like I said, moblock test keeps failing, and I don't know what to do. Thanks for your help!

---

### Post by pelle.k on 2007-10-21
> I would like to run firestarter with it
Can't be done. Sorry.
btw, please post logs, config files etc within "code" tags, because "quote" doesn't have a scrollbar, and that makes some very long posts, depending on the size of the output.

Restart moblock, "test" it, and post "tail /var/log/moblock.log" for us.

---

### Post by c1rcu17 on 2007-10-21
Ok, I restarted moblock, still failed the test. When I did the "tail /var/log/moblock.log" I got, ```
Skipping useless range: adv549|CWS|BT|Hijackers
Skipping useless range: Pluginaccess.com/Dialeraccess.com[CWS]
Skipping useless range: (050501) HTTP Probe 1593
Skipping useless range: (050501) HTTP Probe 1672
Skipping useless range: (050501) HTTP Probe 1596
Skipping useless range: (050501) HTTP Probe 1669
Skipping useless range: (050501) HTTP Probe 1668
Ranges loaded: 2988
Merged ranges: 1
Skipped useless ranges: 134

```

---

### Post by Darganot on 2007-10-21
I posted this in another thread, but I may get a better reply here.  Sorry if this has been asked here already, but this is a huge thread....

So I have moblock installed and running on my install of Xubuntu Gusty.  While browsing with firefox, most (if not all) site take a very long time to load and some don't load at all.  When I disable moblock (moblock-control stop) pages immediately load normally.  My output file looks odd:

> 
~$ tail /var/log/moblock.log
Blocked OUT: AltaVista Company,hits: 2,DST: 209.73.188.78
Blocked OUT: AltaVista Company,hits: 3,DST: 209.73.188.78
Blocked OUT: AltaVista Company,hits: 4,DST: 209.73.188.78
Blocked OUT: AltaVista Company,hits: 5,DST: 209.73.188.78
Blocked OUT: Google Inc,hits: 1,DST: 64.233.165.147
Blocked OUT: Google Inc,hits: 2,DST: 64.233.165.147
Blocked OUT: Google Inc,hits: 3,DST: 64.233.165.147
Blocked OUT: Google Inc,hits: 4,DST: 64.233.165.147
Blocked OUT: Google Inc,hits: 5,DST: 64.233.165.147



I can post more outputs if needed.  Is there a fix for this?

---

### Post by spiker611 on 2007-10-21
Hello ladies and gentlemen!

I'm using moblock on my ubuntu router / server.  I installed moblock in order to protect myself while doing certain activities...

I also host a plethera of services that need to be accessable from the outside world, many of these taking up port ranges of like 2000-2050.  I need to tell moblock to allow (whitelist) all of these ports, and entering them in one by one is quite time consuming (about 10 ranges of 20-30 ports), but I guess it can be done.  Is there a way to specify port ranges for the whitelist?

Also, is there a way to whitelist all forwarded traffic through moblock?  I don't need moblock for the LAN since any sensitive data is port forwarded to the server, and it would make configuration of moblock a lot easier.

Thanks!

---

### Post by Darganot on 2007-10-22
Problem solved, I had missed the part in the initial post about editing the moblock.conf file...

So can someone recommend an easy to use firewall that will work with moblock?  I had been using firestarter since I switched to linux because of how nice it was, but now I'm not sure what will work and what won't.

---

### Post by pelle.k on 2007-10-22
> I also host a plethera of services that need to be accessable from the outside world, many of these taking up port ranges of like 2000-2050. I need to tell moblock to allow (whitelist) all of these ports, and entering them in one by one is quite time consuming (about 10 ranges of 20-30 ports), but I guess it can be done. Is there a way to specify port ranges for the whitelist?
I find it easier to use firehol to do this kind of magic with moblock. moblock-control was never meant to do anything else than basic iptables stuff to redirect traffic to NFQUEUE really.

---

### Post by quixotic-cynic on 2007-10-22
> **Darganot said:**
> So can someone recommend an easy to use firewall that will work with moblock?  I had been using firestarter since I switched to linux because of how nice it was, but now I'm not sure what will work and what won't.

You need a firewall that can send packets that pass the firewall rule to the mechanism that moblock uses to filter the packets. Firestarter is essentially a front end to the iptables firewall - unfortunately it ignores the modification of the iptables file by moblock and just overwrites it so that any ok-d packets go straight to your system.

If you cant find a front-end that does not bulldoze all of your current iptables set up when it runs, you would have to use iptables directly.

About 10 pages ago there was someone trying to do this and the comments there may help.

---

### Post by pwerner2 on 2007-10-22
I'm using Gutsy (7.10), and I have followed your directions (pertinent to this version) to the letter. I had attempted to use MoBlock with feisty previously, but it didn't work for me. When I type "moblock" into command line, I receive a message along the lines of 
" Moblock 0.8 by Morpheus
Syntax: MoBlock -dnp <blocklist> [-b] [-q 0-65535] <logfile>"

This is followed by various command line options which I will not bother typing out right now. 

I was simply wondering if I have (based on this limited information) appeared to have installed MoBlock correctly. Thanks for the help!

---

### Post by pwerner2 on 2007-10-22
Ok, I typed "moblock-control reload", followed by "moblock-control test". This seems to have worked. Sorry about the unnecessary posts.

---

### Post by pwerner2 on 2007-10-22
Sorry. Last one, I promise.

I've noticed that my email client no longer functions, and I can no longer connect to search engines such as google or yahoo. Does anyone know how to fix this? Thanks for the help.

---

### Post by pwerner2 on 2007-10-22
Found my answer on page 76 of the very same thread. I'm sorry. Maybe I'll learn to be intelligent next time I have a problem arise. Carry on.

---

### Post by jre on 2007-10-22
> **spiker611 said:**
> I also host a plethera of services that need to be accessable from the outside world, many of these taking up port ranges of like 2000-2050.  I need to tell moblock to allow (whitelist) all of these ports, and entering them in one by one is quite time consuming (about 10 ranges of 20-30 ports), but I guess it can be done.  Is there a way to specify port ranges for the whitelist?
Port ranges are specified in the format "port:port" (just added to the documentation, thx). [EDIT:I still hate the automatic smiley conversion. The above means "port : port" - but without the spaces.]
So for example:
```
WHITE_TCP_IN="2000:2050 3000:3050"
```

> **spiker611 said:**
> Also, is there a way to whitelist all forwarded traffic through moblock?
You'd have to edit /usr/bin/moblock-control and remove the lines regarding FORWARD (that is those that contain "$NAME\_fw ").

> **antharr said:**
> This all I am getting. It doesn't get past the updating phrase. I have even restarted the PC and it still sticks here. Any suggestions???
I don't know why you can't download the level2.
Is your harddisk on path /var/spool/moblock/ full?
What happens if you comment (#) the line with level2 in /etc/moblock/blocklists.list?

> **c1rcu17 said:**
> Ok, I restarted moblock, still failed the test. When I did the "tail /var/log/moblock.log" I got, 
There should be a line ```
NFQUEUE: binding to queue '0'
```.
No idea why this doesn't happen.
Is your whole system up to date?
Can you post (as CODE) your "moblock-control status" and "tail /var/log/moblock-control.log"?

---

### Post by akShane on 2007-10-23
I'm having problems similar to c1rcu17.  Moblock-control test always fails (uses 3.0.0.0 as the test ip).  I'm running Ubuntu Gutsy, all updates applied.  Moblock worked fine for me in Feisty.  I went as far as to uninstall Firestarter and uninstall/reinstall both iptables and moblock-nfq.  I'm no iptables expert but at a glance everything looks correct.


/var/log/moblock-control.log (just last update):
```

2007-10-22 11:25:07 PM AKDT Begin: /usr/bin/moblock-control update
Updating blocklists ...
Updating level1.gz * .
Updating level2.gz * . No update available.
Updating ads-trackers-and-bad-pr0n.gz * . No update available.
Updating bogon.gz * . No update available.
Updating dshield.gz * . No update available.
Updating hijacked.gz * . No update available.
Updating iana-multicast.gz * . No update available.
Updating iana-private.gz * . No update available.
Updating iana-reserved.gz * . No update available.
Updating Microsoft.gz * . No update available.
Updating rangetest.gz * . No update available.
Updating spider.gz * . No update available.
Updating spyware.gz * . No update available.
Updating templist.gz * . No update available.
Updating trojan.gz * . No update available.
 * Blocklists updated.
Building blocklist   ...done.
Installing blocklist to /etc/moblock/guarding.p2p   ...done.
Reloading MoBlockWarning! Empty blocklist, nothing to clear!
   ...done.
2007-10-22 11:26:49 PM AKDT End: /usr/bin/moblock-control update
2007-10-22 11:32:56 PM AKDT Begin: /usr/bin/moblock-control reload
Building blocklist   ...done.
Installing blocklist to /etc/moblock/guarding.p2p   ...done.
Reloading MoBlockWarning! Empty blocklist, nothing to clear!
   ...done.
2007-10-22 11:32:58 PM AKDT End: /usr/bin/moblock-control reload
2007-10-22 11:33:02 PM AKDT Begin: /usr/bin/moblock-control restart
Deleting iptables   ...done.
Stopping MoBlock* Ranges loaded: 246121
* Ranges loaded: 246518
* Ranges loaded: 246518
   ...done.
Inserting iptables   ...done.
Starting MoBlock   ...done.
2007-10-22 11:33:10 PM AKDT End: /usr/bin/moblock-control restart
* Logging to /var/log/moblock.log
* Ranges loaded: 246518
* Using .p2p file format
* Merged ranges: 304
* Skipped useless ranges: 6563

```

head /var/log/moblock.log (cleared, and then moblock-control reload)
```

NFQUEUE: binding to queue '0'

Got SIGHUP! Dumping and resetting stats, reloading blocklist

```

Then there's lots of Skipping useless ranges and duplicate range lines...I'm assuming that's normal.

tail /var/log/moblock.log (after moblock-control test):
```

Skipping useless range: (050409) W32.Gaobot 1434
Skipping useless range: (050429) W32.Spybot 1433
Skipping useless range: (050510) VRML  4200
Skipping useless range: (050507) W32.Spybot 1433 6000
Skipping useless range: (050327) W32.Spybot 1433
Skipping useless range: (050309) W32.Rahack 4899
Skipping useless range: (050428) W32.Spybot 1433 6000
Skipping useless range: (050412) W32.Rahack 4899
Skipping useless range: (050326) Unassigned 33437
Ranges loaded: 246518

```

Iptables:
```

Current iptables rules (this may take awhile):

Chain INPUT (policy DROP)
target     prot opt source               destination
RETURN     0    --  anywhere             anywhere
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  192.168.0.1          anywhere
ACCEPT     0    --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       0    --  anywhere             255.255.255.255
DROP       0    --  anywhere             192.168.0.127
DROP       0    --  224.0.0.0/8          anywhere
DROP       0    --  anywhere             224.0.0.0/8
DROP       0    --  255.255.255.255      anywhere
DROP       0    --  anywhere             0.0.0.0
DROP       0    --  anywhere             anywhere            state INVALID
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    0    --  anywhere             anywhere
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input'
moblock_in  0    --  anywhere             anywhere            state NEW

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward'
moblock_fw  0    --  anywhere             anywhere            state NEW

Chain OUTPUT (policy DROP)
target     prot opt source               destination
RETURN     0    --  anywhere             anywhere
ACCEPT     tcp  --  hungary              192.168.0.1         tcp dpt:domain
ACCEPT     udp  --  hungary              192.168.0.1         udp dpt:domain
ACCEPT     0    --  anywhere             anywhere
DROP       0    --  224.0.0.0/8          anywhere
DROP       0    --  anywhere             224.0.0.0/8
DROP       0    --  255.255.255.255      anywhere
DROP       0    --  anywhere             0.0.0.0
DROP       0    --  anywhere             anywhere            state INVALID
OUTBOUND   0    --  anywhere             anywhere
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output'
moblock_out  0    --  anywhere             anywhere            state NEW

Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     0    --  192.168.0.27         anywhere
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:53886
ACCEPT     udp  --  anywhere             anywhere            udp dpt:53886
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:53885
ACCEPT     udp  --  anywhere             anywhere            udp dpt:53885
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5900
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5900
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5901
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5901
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp
ACCEPT     udp  --  anywhere             anywhere            udp dpt:fsp
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6964
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6964
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:49152:60000
ACCEPT     udp  --  anywhere             anywhere            udp dpts:49152:60000
LSI        0    --  anywhere             anywhere

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  0    --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       0    --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     0    --  anywhere             anywhere

Chain moblock_fw (1 references)
target     prot opt source               destination
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_in (1 references)
target     prot opt source               destination
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_out (1 references)
target     prot opt source               destination
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * moblock is running, pid is 7725.

```

I've looked around this thread for a few hours and tried all the solutions that seemed applicable, but I apologize if I missed something.  Let me know if you need anything else, and thanks.

*Edit:*
I should add that I can't ping 3.0.0.0 anyway, but I can ping some of the other IPs listed in the blocklist.  Does moblock-control test just tested to makes sure the *outgoing* ping was blocked?

---

### Post by Darganot on 2007-10-23
> **quixotic-cynic said:**
> You need a firewall that can send packets that pass the firewall rule to the mechanism that moblock uses to filter the packets. Firestarter is essentially a front end to the iptables firewall - unfortunately it ignores the modification of the iptables file by moblock and just overwrites it so that any ok-d packets go straight to your system.

If you cant find a front-end that does not bulldoze all of your current iptables set up when it runs, you would have to use iptables directly.

About 10 pages ago there was someone trying to do this and the comments there may help.

How about this firewall script:

```

#!/bin/sh
#
# A simple firewall initialization script
#
WHITELIST=/etc/whitelist.txt
BLACKLIST=/etc/blacklist.txt
IFACE=eth+
ALLOWED="22"

#
# Drop all existing firewall rules
#
# iptables -F

#
# First, run through $WHITELIST, accepting all traffic from the hosts and networks contained therein.
for x in `grep -v ^# $WHITELIST | awk '{print $1}'`; do
echo "Permitting $x..." 
iptables -A INPUT -t filter -s $x -j ACCEPT
done

#
# Now run through $BLACKLIST, dropping all traffic from the hosts and networks contained therein.
#
for x in `grep -v ^# $BLACKLIST | awk ' {print $1}'`; do 
echo "Blocking $x..."
iptables -A INPUT -i $IFACE -t filter -s $x -j DROP
done

#
# Next, the permitted ports: What will we accept from hosts not appearing on the blacklist?
#
for port in $ALLOWED; do 
echo "Accepting port $port..."
iptables -A INPUT -i $IFACE -t filter -p tcp --dport $port -j ACCEPT
done

#
# Finally, unless it's mentioned above, and it's an inbound startup request, just drop it. 
#
# iptables -A INPUT -i $IFACE -t filter -p tcp --syn -j DROP

# Drop all ping requests
iptables -A INPUT -i $IFACE -p icmp --icmp-type ping -j DROP
```

That goes in /etc/init.d/firewall

Will that work with moblock?

---

### Post by akShane on 2007-10-24
Ok, some progress here.  If your moblock-control test is failing, it might be due to an incompatibility in your iptables settings.

If you're behind a router with a firewall and have that protection, try reseting iptables (allowing all connections).

You can try save your iptables with:
```

iptables-save > iptables.backup

```

and then reset iptables:
```

iptables -R
iptables -t nat -F
iptables -t mangle -F
iptables -X

```

Then try restarting moblock:
```

moblock-control restart

```

and see if "NFQUEUE: binding to queue '0'" shows up in moblock.log
```

tail /var/log/moblock.log

```

If it doesn't work, you can restore your old iptables settings from your backup like so:
```

iptables-restore < iptables.backup

```

This worked for me.  Once you clear out your iptables settings, you can set up your new configuration and save your final settings to a backup file...

Some helpful sites:
[Thread tutorial]("http://forums.pcper.com/showthread.php?t=432469")
[IPTablesRocks.org]("http://www.iptablesrocks.org")

---

### Post by jamesford on 2007-10-24
im wondering, if i wanted to go back to using the 0.8.10 is there any reason why i shouldnt do that? will it not work in gutsy for example?

the reason im asking is that 0.8.10 always worked perfectly 
while 0.8-26 amd64 by daradib does not. what happened this morning was that for some reason moblock hadnt been able to download level1, if this happened with htte old version moblock would just use the old level1 already on harddisk, but this didnt, it completely ignored level1 and i was left for hours with a blocklist containing some 60 000 entries instead of the normal 224 000 or so

so can i go back to useing the old version, of so how do i uninstall the previous version properly without fcking up iptables or whatever?

or is there something i can do to fix the current version

thanks

---

### Post by jre on 2007-10-25
jamesford, I'm working on fixing this. Until then you can just "purge" the current version and install the old one or (recommended) just put a "notimestamp" before the entries in your blocklists.list.

Gutsy users with problems, please try a newer version (for example "test" was fixed in 0.8-25). Since I can't build the packages for gutsy currently you have to build your own packages. Just use this in your /etc/apt/sources.list:
```
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) sid main
``` and compile your own package as described on [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/).
Current user-built packages for gutsy and/or amd64 are always welcome and will be published.
Sorry that I can't answer you correctly at the moment ...

greets
jre

---

### Post by jamesford on 2007-10-25
are the problems solved if i build my own packages? or do they only exist in the readymade debs?

---

### Post by Darganot on 2007-10-25
Alright, I have moblock working fine but I still have no firewall and this troubles me a bit (tho I do have a router with a hardware firewall so I'm not hanging in the breeze).  I'm going to uninstall moblock and start using the blocklist feature in Deluge (it looks like it was just added as a plugin).  Ktorrent users can also use a blocklist updater.

---

### Post by daradib on 2007-10-25
> **Darganot said:**
> Alright, I have moblock working fine but I still have no firewall and this troubles me a bit (tho I do have a router with a hardware firewall so I'm not hanging in the breeze).  I'm going to uninstall moblock and start using the blocklist feature in Deluge (it looks like it was just added as a plugin).  Ktorrent users can also use a blocklist updater.

BTW, I would consider a software firewall on my computer redundant when I have a firewall in my router, but that's just my opinion.

---

### Post by jre on 2007-10-26
> **jamesford said:**
> are the problems solved if i build my own packages? or do they only exist in the readymade debs?

Problem with test was fixed in 0.8-25.

One problem with gutsy and the current kernel was fixed in 0.8-26. 

I can't comment just now on possible other problems with gutsy, you have to try ...

It would be very appreciated if someone made new packages for amd64 (every distribution) and i386 (gutsy).

greets
jre

---

### Post by jamesford on 2007-10-26
ill make amd64 debs for gutsy when i get the time to do so, probably this weekend

---

### Post by quixotic-cynic on 2007-10-26
> **Darganot said:**
> I'm going to uninstall moblock and start using the blocklist feature in Deluge (it looks like it was just added as a plugin).  Ktorrent users can also use a blocklist updater.

Darganot, I looked over your firewall code above. It doesn't look quite right to me - i'm not sure that ACCEPT was the right thing to use. That said, editing iptables by hand is beyond me at present so I am afraid I can't really help much.

The Ktorrent and Deluge blocklists both worked rubbish for me, and are much less customisable  (I tried KTorrent and use Deluge). Overall I found moblock to be the best solution. Good luck, however; if you can get one or the other to work fast enough then that would be good.

---

### Post by pelle.k on 2007-10-26
> It would be very appreciated if someone made new packages for amd64 (every distribution) and i386 (gutsy).

Well, here's updated gutsy i386 packages (built from feisty source).

---

### Post by jre on 2007-10-26
> **quixotic-cynic said:**
> Darganot, I looked over your firewall code above. It doesn't look quite right to me - i'm not sure that ACCEPT was the right thing to use.
Darganot, quixotic-cynic is right.
[EDIT: Removed wrong advice, see my next post.]
Note that i did no complete check of your script.

> **akShane said:**
> I should add that I can't ping 3.0.0.0 anyway, but I can ping some of the other IPs listed in the blocklist.
That should be fixed with [Edit: EDIT: Removed wrong advice, see my next post.]

 I just changed the "test" to tell you if the ping was unsuccessful (good) but the test IP is not in moblock.log (bad) that you might have filtered it with your firewall.

> **akShane said:**
> Does moblock-control test just tested to makes sure the *outgoing* ping was blocked?
Yes.

All in all, as I see it now there are no problems with moblock and gutsy. These are "only" problems of integrating moblock with an custom firewall.

The version to fix the update problem and with improved "test" will be released *soon* (TM).

greets
jre

---

### Post by daradib on 2007-10-26
> **jamesford said:**
> ill make amd64 debs for gutsy when i get the time to do so, probably this weekend

Actually, you can already get the amd64 gutsy deb. It is [here]("http://moblock-deb.sourceforge.net/moblock-nfq_0.8-26+gutsy_amd64.deb").

But 0.8-26 deb packages for other Ubuntu 64-bit releases would be nice. Maybe I'll try to set up pbuilder.

---

### Post by daradib on 2007-10-26
Updated the [MoBlock Ubuntu Community Documentation]("https://help.ubuntu.com/community/MoBlock") to include link to Ubuntu 7.10 32-bit package.

---

### Post by pelle.k on 2007-10-27
> Maybe I'll try to set up pbuilder.
pbuilder is really nice! this is some further reading if you're interested;
[http://ubuntuforums.org/showthread.php?t=206382](http://ubuntuforums.org/showthread.php?t=206382)

I usually add the source repos and "apt-get source <packagename>" or use dget on the actual location of the .dsc from a repository to down load the source.
If i need to make an adjustment (like with the feisty -> gutsy package) i "dpkg-source - x <package>.dsc", and edit the changelog in the "debian" directory of the source.
If i made some adjustment (and therefore adjusted the changelog), i just "dpkg-source -b <new_package_folder>" and i get a new .dsc complete with diff.
Finally, i just "sudo pbuilder build <package>.dsc".

---

### Post by jre on 2007-10-27
> **jre said:**
> Darganot, quixotic-cynic is right, use RETURN instead of ACCEPT if you want this traffic to be checked by moblock. Then, if you start moblock **after** your script, everything should work. Note that i did no complete check of your script.
Daradib/AKShane: D'oh (once again), not RETURN but send traffic to moblock_in (from INPUT) or moblock_out/_fw instead of ACCEPT if you want it to be checked by MoBlock.
Also, start MoBlock BEFORE your script with option 
```
IPTABLES_ACTIVATION="0"
```

jre

---

### Post by jamesford on 2007-10-27
i compliled these just now on gutsy64 following the instructions here [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

i made this little thing for myself, i dont know if anyone can use it but what it does is it loads a terminal in the systray when the computer starts with 2 tabs, tab1 shows the output of the log (i.e. what is being blocked) the other tab shows the moblock-control log, which dispalys info about recent updates, how many ranges loaded etc. i find it a bit useful

you need to install alltray for this to work and also edit the icon path to point to an icon of your choice

```
alltray -i /path/to/prefered/icon.png "gnome-terminal --tab --active --title=molog --command='tail -f /var/log/moblock.log' --tab --title=moblock-control --command='tail -f --lines=99 /var/log/moblock-control.log'" &
```

add this to your startup

---

### Post by oni5115 on 2007-10-27
I'm stuck with the new version.  I figured out how to make firefox work by whitelisting http(s), but how to do I whitelist say a company name, like you used to with the old version?  (e.g. I want to be able to connect to any I.P. belonging to say... Blizzard Entertainment... so I can connect to WoW even if Moblock is on.).

I tried to modify /etc/moblock/moblock.conf and adding Blizzard Entertainment to the 'Remove lines from the blocklist' section.  That didn't seem to work at all.  Is there any other way to simply white list the company name?

Edit:
I've managed to get firefox working without whitelisting http(s) now by commenting out the spiders list.  yay.

I still can't seem to get World of Warcraft working without turning off moblock.  It's like the IP_REMOVE= does absolutely nothing.  even rebooted, and ran the moblock-control reload as well.  Still nothing, have to turn it off while running WoW.  I'm using the most up to date Gutsy, and Moblock.

---

### Post by jamesford on 2007-10-28
quick question:
is it safe to remove moblock-nfq from /etc/cron.daily and place it elsewhere so that it can be run via crontab at a more convenient time, or  does it have to be in /etc/cron.daily for moblock to function properly?

---

### Post by jre on 2007-10-29
@oni: A
```
diff /etc/moblock/guarding.p2p /etc/moblock/guarding.p2p.backup
```
will show you if your blocklist was modified by the IP remove entry (First remove all your entries, then make a "reload", then insert your entries, make a "reload" again and then the diff).

Please tell us the version number and not "the most up to date Gutsy". As you can see on the previous pages I have problems with creating Gutsy packages and so they have to be built manualyy/downloaded from other users.

> **jamesford said:**
> quick question:
is it safe to remove moblock-nfq from /etc/cron.daily and place it elsewhere so that it can be run via crontab at a more convenient time, or  does it have to be in /etc/cron.daily for moblock to function properly?
Yes.

---

### Post by jre on 2007-10-29
@oni: A
```
diff /etc/moblock/guarding.p2p /etc/moblock/guarding.p2p.backup
```
will show you if your blocklist was modified by the IP remove entry (First remove all your entries, then make a "reload", then insert your entries, make a "reload" again and then the diff).

Please tell us the version number and not "the most up to date Gutsy". As you can see on the previous pages I have problems with creating Gutsy packages and so they have to be built manualyy/downloaded from other users.

> **jamesford said:**
> quick question:
is it safe to remove moblock-nfq from /etc/cron.daily and place it elsewhere so that it can be run via crontab at a more convenient time, or  does it have to be in /etc/cron.daily for moblock to function properly?
It's safe to remove.

---

### Post by jingo811 on 2007-10-30
I just upgraded the old Moblock to the newest version on Feisty.  It makes Internet very slow, I can't even connect to the most common domain when it is running.
[www.google.com](www.google.com) 
[www.yahoo.com](www.yahoo.com).

Do others experience this also?

---

### Post by jamesford on 2007-10-30
jingo811: no i dont and i dont think most people do..cant help u with why u have this problem though. im sure some of the other guys will when they see your message

---

### Post by jingo811 on 2007-10-30
I did these commands in order to start from scratch.

```
$sudo apt-get remove moblock-nfq
$sudo apt-get autoremove
```

Then I tested to see if there where some traces left.  And it seems like it's clean.

```
$sudo moblock-control test
sudo: moblock-control: command not found
```

Then I install like usual.
```
$gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
$gpg --export --armor 9072870B | sudo apt-key add -
```

Did the repository thing.  Then installed the program.
```
$sudo apt-get install moblock-nfq
```

Then tested it.
```
$moblock-control test 
Testing MoBlock: trying to ping 4.18.162.102 from /etc/moblock/guarding.p2p ...
 * MoBlock blocked the IP. Test succeeded.
```

Tried to surf to [www.google.com](www.google.com) in Firefox it's totally blocked :( 


PS.
Does anybody else use Compiz Fusion with a working MoBlock on their Feisty?

---

### Post by feistybird on 2007-10-31
[COLOR="Silver"]It works perfectly in 7.04, but after I've upgraded to Gusty, it starting to block all my google.com traffics!!  
:(
---

PS. The download link of "moblock-nfq_0.8-26+gutsy_i386.deb" is actually pointing to "moblock-nfq_0.8-26+gutsy_amd64.deb"[/COLOR]


^^^^^^^^^^^^^^^^^^^^^^

**Thanks! Problems solved (yes, just whitelist it)**

[Page 76 #753]("http://ubuntuforums.org/showpost.php?p=3528634&postcount=753") and [#756]("http://ubuntuforums.org/showpost.php?p=3530638&postcount=756") is very helpful!

---

### Post by pelle.k on 2007-10-31
Oh crap! Thanks for the heads up...

[edit]you need to whitelist. All blocklists are used by default, and that means block pretty much everything....[/edit]

---

### Post by Rick123 on 2007-10-31
yeha when i installed moblock on gutsy i could not longer enter a webpage... i mean no one.. it was like everything got on in slow motion, When i tried to access demonoid i just saw the demonoid marker were you write http address... but was loading forever... so i uninstall it... and tried with Ipblock same problem there.

---

### Post by jingo811 on 2007-10-31
> **pelle.k said:**
> Oh crap! Thanks for the heads up...

[edit]you need to whitelist. All blocklists are used by default, and that means block pretty much everything....[/edit]

It worked now I can reach google and ubuntuforums with MoBlock turned on.
But is this the same as not having MoBlock running?
In what way is opening up port 80 and 443 to all traffic bad for me the user?

---

### Post by sloter on 2007-10-31
Hello,

Yes after a fresh install of moblock all the ports are blocked by default.
So just refer to the first post of this thread and look at the section "Some applications can't connect to the internet any more!".


Opening tpc out ports for http and or https is not so dangerous.
And p2p applications uses others ports which remains blocked by moblock.


Thank you,
sloter

---

### Post by daradib on 2007-11-01
I think the issue is that there is the potential for another p2p peer/client to connect to you on an unblocked port, like port 80 and therefore bypass MoBlock.

---

### Post by jamesford on 2007-11-01
is there any way to get the system mail moblock sends when updating to include whats been updated, how big files, how many total blocked ranges etc ? i miss that from previous versions. alternatively, how do i get it to send no email at all, since currently the info it sends is useless and annoying ?

---

### Post by debi@n on 2007-11-02
When I try to install Moblock as described i get an error:```
apt-get install moblock-nfq
[...]
Richte moblock-nfq ein (0.8-26+etch) ...
Starting MoBlockinvoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: Fehler beim Bearbeiten von moblock-nfq (--configure):
 Unterprozess post-installation script gab den Fehlerwert 170 zurück
```

I have no idea what causes this error. Any Ideas?

---

### Post by feistybird on 2007-11-03
> **sloter said:**
> Hello,

Yes after a fresh install of moblock all the ports are blocked by default.
So just refer to the first post of this thread and look at the section "Some applications can't connect to the internet any more!".


Opening tpc out ports for http and or https is not so dangerous.
And p2p applications uses others ports which remains blocked by moblock.


Thank you,
sloter

I've double checked my "/etc/moblock/MoBlock-nfq.sh"

and made sure that http, https, 1863 (for msn messenger) are all in my white list as follows:


```
WHITE_TCP_IN="http https 1863"
WHITE_TCP_OUT="http https 1863"
```

But the newer version of moblock installed in my 7.10 Gusty seems to ignore these settings? it used to work properly in my previous 7.04 Feisty.

=== Problem Solved ===

I think I've double checked almost everything except carefully reading the very first post of this thread :

The actual "TCP Port's White List" settings should be located in **/etc/moblock/moblock.conf** and NOT "/etc/moblock/MoBlock-nfq.sh" like it used to work in the earlier versions.

---

### Post by franz1789 on 2007-11-04
I don't know, maybe that's my fault, but moblock on gutsy make me feel noob. I'm just keeping on trying to make it work, and it keeps to fail. When I update, the /etc/moblock/guarding.p2p remain empty, so the tests fail, and it seems not to be under my comand, well, everything I do, it seems useless.
I don't know why I can't update the list, /etc/moblock/blocklist.list is full of adress, but the update keeps on fail, because that ******** file remain empty. Any idea? iplist was rubbish, I don't want to change software...
Please, help.

---

### Post by pelle.k on 2007-11-04
You did notice that the latest version 0.8-26 never got onto the repositories, right? You have to manually install it (the deb is in the HOWTO).

Try 1;
However, i just did a fresh install of 0.8-26, and according to the moblock-control log, "updating" level1 never completed, so i had to kill the update script (ctrl-c).

Try2;
After that, i ran an update manually, and it succeeded, without problems. The strange thing is, the log said level1 didn't have to be updated, and sure enough it was complete from the first run, even though that time it "froze" there...

Try3;
It got stuck on "updating" level1 this time as well. I tried changing level1 to notimestamp in blocklists.list, but that only made it freeze on "downloading" level1 instead of "updating" it...

**@ jre**
It would seem a timeout would be preferable in the function that download individual blocklists. I also think a flat text file log report on what *was* updated vs. what lists were kept as they were and when this happened would be in order... 

**@ everyone**
You can, however download the blocklist(s) you miss manually from the URLs in /var/moblock/blocklists.list, and then move them to /var/spool/moblock as a temporary measure. Then just use
```
moblock-control reload
``` to generate a new guarding.p2p
Still, even if you download the lists manually, moblock uses the uncommented URLs in blocklists.list to also single out what files should be used (like level1 etc) when building the guarding.p2p.

---

### Post by quixotic-cynic on 2007-11-04
> **jingo811 said:**
> It worked now I can reach google and ubuntuforums with MoBlock turned on.
But is this the same as not having MoBlock running?
In what way is opening up port 80 and 443 to all traffic bad for me the user?

Find my first post to this thread (probably using search) and then read the next few pages. Hopefully that can give you your answer.

---

### Post by smartboyathome on 2007-11-04
> **feistybird said:**
> 
=== Problem Solved ===

I think I've double checked almost everything except carefully reading the very first post of this thread :

The actual "TCP Port's White List" settings should be located in **/etc/moblock/moblock.conf** and NOT "/etc/moblock/MoBlock-nfq.sh" like it used to work in the earlier versions.

Thanks, you solved my problem with MSN that kept me from using Moblock!

---

### Post by nidya on 2007-11-05
First off, thanks for this! MoBlock is superawesome, nice job. But I've got an issue.

> **feistybird said:**
> and made sure that http, https, 1863 (for msn messenger) are all in my white list as follows:


```
WHITE_TCP_IN="http https 1863"
WHITE_TCP_OUT="http https 1863"
```
I was sure that this would solve my problem, but it did not. I can't connect to MSN anymore, I'm using Pidgin for that. Do I have to enable something else? I'm sorry but I can't read 85 pages right now...I hope somebody can help me, thanks!

If I stop MoBlock, I can connect to MSN via Pidgin and if I turn on MoBlock it's still connected, but that's not a long term solution...


&#8364;dit: AHA! It worked now, after I  deleted the WHITE_TCP_OUT="http https 1863" and the other one I added. I just added the port 1863 to the one I had to uncomment (removing the "#") to use Firefox. So it looks like this:

```
############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name.
# Seperate several entries with whitespace (" ")

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT=""
WHITE_TCP_OUT="http https 1863"
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""
```

---

### Post by kurotsuno on 2007-11-06
Just installed moblock tested and it failed

Also uncommented the http from moblock.conf

I followed all the steps to get this installed properly on Gutsy I'm not sure if its at all working properly. 

I'm running Gutsy as it is I haven't downloaded/installed firestarter or any firewall for that matter. 

Also I know from using peerguardian you could choose from several locations to get the blocklists. Is this possible with moblock and if so were do I get a list of the locations I can get the blocklists from. Also were do I go change the location is it moblock.conf ?

:) Thanks in advance

---

### Post by dn* on 2007-11-08
This appears to be working great. Am I right in thinking that MSN Messenger ports only need to be opened because Microsoft stuff is banned? I mean, I don't need to open ports for IRC and wotnot, do I?

---

### Post by Odin25 on 2007-11-09
I just installed moblock on an ubuntu-server 7.10 via a ssh terminal
using "dpkg" saying couldn't complete the installation so I started "aptitude" to find out a dependency was not matched ( something like in..quue0) which I decided to install
the installation went on ...moblock update ... moblock start

 and now I am kicked out of the system :-( leaving aptitude hanging (hopefully no damage)
Why is that? I'm entering via lan.

BTW: the howtos and the package you did helped me to install it at all! thanks for your effort!

**just found out:**
 to add the lan ips in the white list 
 so now i can maintain the server via the lan :-)

---

### Post by Odin25 on 2007-11-10
hi to you all

is there a possibility to open a range of ports without keying every single port in the list? also to open the whole lan ips at once?

is there a possibility to use different lists for different ports?

thanx in advance

---

### Post by 449 on 2007-11-12
Hi if anyone could help me that be great!

I installed moblock on Xbuntu Gutsy Gibbon using your guide. However I can't get the test to work, it always says it failed. How do I fix this? Also how do I load my ipfilter.dat files into moblock? Thanks for your time!

---

### Post by Odin25 on 2007-11-13
> **449 said:**
> 

... However I can't get the test to work, it always says it failed. How do I fix this? Also how do I load my ipfilter.dat files into moblock? ...

1st: what do you mean by failed? exactly

2nd: read first and then edit /etc/moblock/blocklists.list

---

### Post by jre on 2007-11-13
First off, I were offline the last 2 weeks. Additionally I had problems with creating the repository. That's working now (never use symlinks in /etc !), even gutsy is back :-)
So at the time of writing I'm releasing 0.8-29.  The major change is that *complete* downloaded lists are copied to /var/spool/moblock/used.

> **debi@n said:**
> When I try to install Moblock as described i get an error:```
apt-get install moblock-nfq
[...]
Richte moblock-nfq ein (0.8-26+etch) ...
Starting MoBlockinvoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: Fehler beim Bearbeiten von moblock-nfq (--configure):
 Unterprozess post-installation script gab den Fehlerwert 170 zurück
```

I have no idea what causes this error. Any Ideas?
170 is "missing external binary/function". Have a look at /var/log/moblock-control.log, there should be something more verbose.

> **pelle.k said:**
> It would seem a timeout would be preferable in the function that download individual blocklists.
It is: wget -T 120 (timeout 120 secs).
You really have funny update problems - if they continue with 0.8-29 please tell me.

> **jamesford said:**
> is there any way to get the system mail moblock sends when updating to include whats been updated, how big files, how many total blocked ranges etc ? i miss that from previous versions. alternatively, how do i get it to send no email at all, since currently the info it sends is useless and annoying ?
> **pelle.k said:**
> I also think a flat text file log report on what *was* updated vs. what lists were kept as they were and when this happened would be in order... 
pelle and jamesford: Even before reading this I added a warning when any update did not work (just a warning, not an error since I have the "used" dir for complete lists now).
If you want more then send me a patch ;-) To be honest I have no idea how to change this without a major restructuring of moblock-control. The text that is mailed is sent to standard output while *all the rest* is sent to the log file. Of course I might remove the logfile (I added this when wget's output was much more verbose) so that everything is mailed.
Some of the info is in /var/log/moblock-control.log. The informational point of the mail is the final "."! If it's there everything should have gone well, if not the update aborted.
I just added to my TODO:
- find a better way for the output (different verbosity levels, what is sent to the logfile, what to standard output)

> **Odin25 said:**
> is there a possibility to open a range of ports without keying every single port in the list? also to open the whole lan ips at once?
Port ranges are specified in the format "port:port" [EDIT: "p o r t : p o r t" - I hate the smiley theme] in moblock.conf
For ip ranges you can use network masks: e.g. use "192.168.178.0/255.255.255.0" for 192.168.178.0-192.168.178.255

> **Odin25 said:**
> is there a possibility to use different lists for different ports?
you might run several moblock instances. But you have to do this on your own - it's not possible by simply using the deb's.

> **449 said:**
> Also how do I load my ipfilter.dat files into moblock? Thanks for your time!
ipfilter.dat has another format then the predefined lists. So ATM you can't use both at the same time!
If you want to use only ipfilter.dat then edit /etc/moblock/blocklists.list (the URL of your list) and /etc/moblock/moblock.conf (the format of your list)

jre

EDIT: Someone to post new amd64 packages?

---

### Post by Odin25 on 2007-11-13
hi jre

that is quite an update :-)

I like the keeping of the lists (in /var/spool/moblock/used)

the description of ips and ports really helped, thx.

as Im new to the moblock "thing" I will need to wrap my mind around it a little longer to figure out how it works exactlly before I can use two instances of moblock.

for now: have a nice day

PS. I deeply appreciate the efford U're all putting in this project and I really enjoy reading this threat!
(too cheesy?)

---

### Post by daradib on 2007-11-13
I will post packages for Ubuntu Gutsy 64-bit as soon as possible, but unfortunately my hard drive is failing me (I'm using a Windows computer to post this). Once I get set up again I will post new packages for Gutsy 64-bit. Someone else, however, may be able to post it sooner.

jre: BTW, what do you mean by "The moblock package for dapper drake is not updated since i put it here" (on the first post). Doesn't dapper drake use the etch repos which have 0.8-29, or is this referring to something else?

Also on the first post, "Dapper drake (6.04)" should be 6.06.

It's just some minor things I noticed while updating [MoBlock in the Community Documentation]("https://help.ubuntu.com/community/MoBlock").

---

### Post by pelle.k on 2007-11-14
> jre: BTW, what do you mean by "The moblock package for dapper drake is not updated since i put it here" (on the first post). Doesn't dapper drake use the etch repos which have 0.8-29, or is this referring to something else?
Oh, you mean me i suppose ;)
That's an error on my part, from when i had those packages compiled before the repos shift and the updates from jre. I'll remove that comment...

---

### Post by Folk Theory on 2007-11-14
quick question: so if i have firestarter installed, moblock won't run [properly]?

---

### Post by jre on 2007-11-14
> **pelle.k said:**
> Oh, you mean me i suppose ;)
That's an error on my part, from when i had those packages compiled before the repos shift and the updates from jre. I'll remove that comment...
I think so, too ;-)
Further I *think* Dapper is broken the same way as Edgy (bug in lsb init function). But of course we can wait until someone confirms this.

Thanks for all feedback - that makes this work fun.

greets
jre

---

### Post by daradib on 2007-11-14
> **Folk Theory said:**
> quick question: so if i have firestarter installed, moblock won't run [properly]?

Referring to a previous post:

> **quixotic-cynic said:**
> You need a firewall that can send packets that pass the firewall rule to the mechanism that moblock uses to filter the packets. Firestarter is essentially a front end to the iptables firewall - unfortunately it ignores the modification of the iptables file by moblock and just overwrites it so that any ok-d packets go straight to your system.

If you cant find a front-end that does not bulldoze all of your current iptables set up when it runs, you would have to use iptables directly.

About 10 pages ago there was someone trying to do this and the comments there may help.

---

### Post by daradib on 2007-11-14
The bottom line is Firestarter doesn't work in conjunction with MoBlock, as far as I know, at least in Ubuntu 7.04 and above.

> Caution: MoBlock doesn't behave well with most other firewalls (iptables rules). There's only a known solution for moblock in combination with firehol. You may also try [iplist]("http://iplist.sourceforge.net/") by [uljanow]("http://forums.phoenixlabs.org/member.php?u=8022").
Source: [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

---

### Post by Odin25 on 2007-11-15
To fidle with the code a little to find out how it works and how to get timestamps and portnumbers logged:

I have tried to compile the moblock code but the compiler is asking for

libnetfilter_queue/libnetfilter_queue.h

do I need other headerfiles also?

and because I'm new to ubuntu (2weeks of ubuntu server) and the debian packaging I wonder where to find the headerfiles for moblock to compile and is there a rule in ubuntu where to put them?

I already had a look at the code and found some places where to put some code but any advice of you would be highly appreciated!

Thank you in advance

---

### Post by pelle.k on 2007-11-15
I suppose you use the makefile to compile, right?
All build dependencies should be installed with "apt-get build-dep moblock-nfq", and found if you use the supplied makefile i guess.

---

### Post by daradib on 2007-11-15
Here are the 0.8-29 amd64 packages for Gutsy. I used a live CD to do this since my hard drive has failed me.

EDIT: I have tested the nfq package on the Live CD and it does appear to work

---

### Post by jamesford on 2007-11-15
ah then i wont have to upload those i just made myself :)

---

### Post by daradib on 2007-11-15
Well, if you don't mind, could you test the packages I generated? They do appear to work on the live CD, but it would be better if someone tested it on a (updated) Ubuntu Gutsy 64-bit [hard drive] installation.

---

### Post by pelle.k on 2007-11-15
I was thinking i might phase out the HOWTO by removing key parts of it (the parts already covered by the one on the wiki [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)). Just so you guys now...
I will of course keep "news" items, and links to the wiki article etc.

---

### Post by Odin25 on 2007-11-16
> **pelle.k said:**
> I suppose you use the makefile to compile, right?
All build dependencies should be installed with "apt-get build-dep moblock-nfq", and found if you use the supplied makefile i guess.

Yes I use the Makefile and your answer really helped, I got the libs and the sources and it compiled nicely.

(Sorry I should have read [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/), but I was and still am a little bit lost in the dir-tree and the not knowing how are things done in ubuntu/debian which is to me like a jungle)

To test one of my own betas I have to rename "moblock"  to "moblock-nfq" & copy it to /usr/bin, right?

EDIT (5h later): I just did it (compile, rename & copy) and it works fine.

thank you

---

### Post by Odin25 on 2007-11-16
I just added a little bit of code into moblock.c to have the time logged too.

default format would be:
12:59:59 Blocked OUT ....

but one can also choose between:
2007-01-21 12:59:59 Blocked OUT ...
20070121 125959 Blocked OUT ...
125959 Blocked OUT ...

(format must still be chosen before compiling)

I used the latest source I got by "apt-get source moblock" so it should be new.And it works fine.

If someone is interested I could post the source code. or the compiled version as moblock-nfq (arch would be i586)

Have a nice day!

---

### Post by Odin25 on 2007-11-16
I tried to put a peerguardianlist "http://peerguardian.sourceforge.net/lists/p2p.php" into blocklist.list (that of course worked :) ) but after "moblock-control update" it crashed.

Any idea?

---

### Post by pelle.k on 2007-11-16
I guess a patch would be preferable. Make one with "diff".

---

### Post by jre on 2007-11-16
> **Odin25 said:**
> I just added a little bit of code into moblock.c to have the time logged too.

I always appreciate such work!
But our upstream author has done this already, too. In the current CVS repository you'll find (quoting from an email from september):
- timestamping
- log to syslog
- support for RETURNing packets and an example start script (MoBlock-nfq-reject.sh) that rejects instead of dropping.
Further he already has a patch for libdbus support for communication with a GUI that is under development.

So, for everyone who's working with the code of the daemon itself I recommend to have a look at the CVS repository at [http://moblock.berlios.de/](http://moblock.berlios.de/) first.
The packages that I release are based on the last official version (0.8) [EDIT: gna, fifth time I hate the smiley theme; it's "( 0 . 8 )."] instead.

People working on the code of moblock-control should have a look at the development repository from moblock-deb.sf.net (Although this is in most times in sync with the Debian packages).

> **Odin25 said:**
> I tried to put a peerguardianlist "http://peerguardian.sourceforge.net/lists/p2p.php" into blocklist.list (that of course worked :) ) but after "moblock-control update" it crashed.

The name of the blocklist has to be the same as the basename of the URL in blocklists.list. So php redirects are not possible.
I just documented that and made a check for it in the source. Sorry, that's necessary because I need to know the name of the blocklist so that I can copy complete lists to "used". I'll code something savvier when I've time.

[http://peerguardian.sourceforge.net/lists/p2p.php](http://peerguardian.sourceforge.net/lists/p2p.php) is just a mirror of [www.bluetack.co.uk/config/level1.gz](www.bluetack.co.uk/config/level1.gz)

Greets and good coding
jre

---

### Post by Odin25 on 2007-11-16
> **jre said:**
> I always appreciate such work!
Thanks

> **jre said:**
> .. In the current CVS repository you'll find (quoting from an email from september):...I recommend to have a look at the CVS repository at [http://moblock.berlios.de/](http://moblock.berlios.de/) first.
Thank you, yes I went there before to have a look, just by the html pages and couldn't find something for logging. And the comment in the forum was from july. So I thought...

But anyway, I just did it so I have a time logging now and it is just an offer, for those desperate to have the time logged for the time being.
It wasn't/isn't intended to disturb the mainline. Just a quick fix.

[QUOTE=pelle k.]
I guess a patch would be preferable. Make one with "diff".[/QUOTE]
Maybe Im going to install cvs so I can make a diff. 

> The name of the blocklist has to be the same as the basename of the URL in blocklists.list. So php redirects are not possible.... that's necessary because I need to know the name of the blocklist 
I thought so.

> 
Greets and good coding

U 2 :)

---

### Post by pelle.k on 2007-11-16
> Further he already has a patch for libdbus support for communication with a GUI that is under development.
Wow! That is some *great* news! I've always missed this kind of functionality, since it's not really "proper" to use logfiles and whatnot to interpret what is happening when you design a gui "client" to interact with the system.

---

### Post by Odin25 on 2007-11-16
hi pelle,jre et all!

Do you have any idea of cvs? 
I just installed it, loaded the moblock sources had a look in the cvs-docs and I'm stunned.
I have the moblock.c I changed earlier in a different dir what should I do now?

Geetings

---

### Post by elec999 on 2007-11-17
I am trying to test it
and get
Testing MoBlock: head: cannot open `/etc/moblock/guarding.p2p' for reading: No such file or directory
trying to ping  from /etc/moblock/guarding.p2p ...
 * Some error occured with ping, no test result.

I rebooted my system and now works like a charm. Amazing howto.
Thanks

---

### Post by cox377 on 2007-11-20
> **Odin25 said:**
> I just installed moblock on an ubuntu-server 7.10 via a ssh terminal
using "dpkg" saying couldn't complete the installation so I started "aptitude" to find out a dependency was not matched ( something like in..quue0) which I decided to install
the installation went on ...moblock update ... moblock start

 and now I am kicked out of the system :-( leaving aptitude hanging (hopefully no damage)
Why is that? I'm entering via lan.

BTW: the howtos and the package you did helped me to install it at all! thanks for your effort!

**just found out:**
 to add the lan ips in the white list 
 so now i can maintain the server via the lan :-)

Did you manage to get this sorted? I tried it in a test enviroment first and this happened

Am very glad I didnt do it on server first because there is on SSH haha

---

### Post by Odin25 on 2007-11-20
> **cox377 said:**
> Did you manage to get this sorted? I tried it in a test enviroment first and this happened

Am very glad I didnt do it on server first because there is on SSH haha

The server is on a lan so no real deep annoying problem, but I had to mount a monitor and a keyboard to fix the conf file where I changed the white-list to let  my lan addresses pass (192.168.0.0/255.255.255.0):
moblock.conf:
```
...
ip_tcp_in="192.168.0.0/255.255.255.0"
ip_udp_in="192.168.0.0/255.255.255.0"
ip_tcp_out="192.168.0.0/255.255.255.0"
ip_udp_out="192.168.0.0/255.255.255.0"
...
```
so now it works nicely.

But I think there should be a warning anyway or the local addresses should be in the white list (10.0.0.0, 192.168.x.x and there is another one I just cant remember)

BTW: thats just for the lan but if the server is external the according ports should be opened if one is not callig in from a fixed ip.

---

### Post by jre on 2007-11-21
> **Odin25 said:**
> hi pelle,jre et all!

Do you have any idea of cvs? 
I just installed it, loaded the moblock sources had a look in the cvs-docs and I'm stunned.
I have the moblock.c I changed earlier in a different dir what should I do now?
For you CVS is just a method to download the actual version of upstream's current code. (Indeed since the cvs server doesn't respond to me after asking for the password I just browsed the CVS repository and downloaded each file manually.)
You can edit these files and copy them to the directory that you got when you made the "apt-get source moblock". In the next release ALL files that I added for the debian packaging will be in the folder "debian/" and in the main will folder will be exactly the same content as you see it when you make the CVS checkout from upstream's source (burrently it's a wild mix ofd upstream's code and my code).


Odin25. I added a big warning in the package description, but I don't want to whitelist any IPs. But I'm still open for discussions about which blocklists should be on per default.

greets
jre

---

### Post by Odin25 on 2007-11-21
> **jre said:**
> For you CVS is just a method to download the actual version of upstream's current code. (Indeed since the cvs server doesn't respond to me after asking for the password I just browsed the CVS repository and downloaded each file manually.)

I had the same problem (I think it's just because I don't yet understand how to use cvs) but after entering the 2nd line mentioned on the berlios side
```
1st: cvs -d:pserver:anonymous@cvs.moblock.berlios.de:/cvsroot/moblock login
2nd: cvs -z3 -d:pserver:anonymous@cvs.moblock.berlios.de:/cvsroot/moblock co modulename
```
my cvs checked out the sources (I found the first line in a file in the repository. I think it's just for my cvs to know where to get the files)

> **jre said:**
> You can edit these files and copy them to the directory that you got when you made the "apt-get source moblock".
Okay, if I have done that how do I get a diff-file (what "cvs...."-instruction do I have to enter)?

> **jre said:**
>  In the next release ALL files that I added for the debian packaging will be in the folder "debian/" and in the main will folder will be exactly the same content as you see it when you make the CVS checkout from upstream's source (burrently it's a wild mix ofd upstream's code and my code).

That is interesting news, even though I think it's maybe a lot of work for you. Highly appreciated 


> **jre said:**
> Odin25,I added a big warning in the package description, but I don't want to whitelist any IPs. But I'm still open for discussions about which blocklists should be on per default.

For most of the cases and users the Installation routine is totally sufficient  and best of all: low maintenance! which is a great achievement! 

The thing which hit me of guard was: while installing the ssh connection was blocked so I had no chance to change the moblock.conf file at any time, therefor my suggestion with the IP-ranges mentioned (which are restricted to local LANs as I recall).
I found a comment in the peerguardian linux forum by morpheus =?= upstreamer who also doesn't understand why these ranges are in a blocklist. 
But anyway it wouldn't help if the server is not in a lan. 
I think the warning is a good way to go for now.

Thank you for doing such a great job!

Have a nice day!
odin25

---

### Post by Garret88 on 2007-11-24
Why i receive this error(and moblock doens't starts)?

> root@server:/home/garret# **moblock-control update**
Updating blocklists and reloading MoBlock
root@server:/home/garret# **moblock-control status**
Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT 885 packets, 782K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 852 packets, 82812 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Please check if the above printed iptables rules are correct!

 * moblock is not running.
root@server:/home/garret# 

---

### Post by jre on 2007-11-24
> **Garret88 said:**
> Why i receive this error(and moblock doens't starts)?
Have a look at /var/log/moblock-control (or post it). Did this happen only once or does a reboot fix it?
jre

---

### Post by Garret88 on 2007-11-24
> **jre said:**
> Have a look at /var/log/moblock-control (or post it). Did this happen only once or does a reboot fix it?
jre

Here there is the log -> [http://rafb.net/p/iexqJ147.html](http://rafb.net/p/iexqJ147.html)

(it always happens)

---

### Post by pelle.k on 2007-11-24
Bluetack has some problems with the level1. So moblock can't build a blocklist because level1 fails to download,
Can it be because of this?;
> Dear members and guests,

Regretfully we need to let you all know that in one weeks time the site may be closing indefinitely. Our web hosting bill is currently 3 months behind and without this server in operation there will also be no more blocklist updates possible.

We ask you to make a choice and decide on our future. If you want to help keep us alive then we need your support and donations.

There are literally millions of people downloading our files, however only a very small proportion of people find the time to invest anything in return to ensure that our free services can continue.

Everything we do here is offered free of charge, we make absolutely no money whatsoever. We do however spend quite a lot of time to keep everything running as best as we can for your benefit.

In the event that we cannot afford to continue offering our services for free, then we may need to consider introducing a small subscription/fee based service for downloading the blocklist updates and possibly looking towards using ads throughout the site.

We also need more server mirrors to cope with the excessive bandwidth/traffic associated with hosting the lists.

So now you can either choose to do nothing and let BISS die or help support us so that we can continue to support you. If you find any value in our free programs and services here then please consider donating.

The choice is now yours.

Our donation page is here :
[http://www.bluetack.co.uk/donate/index.html](http://www.bluetack.co.uk/donate/index.html)

---

### Post by Garret88 on 2007-11-24
So no one can't use moblock? Or all you use other lists?

---

### Post by Odin25 on 2007-11-24
> **Garret88 said:**
> So no one can't use moblock? Or all you use other lists?

we use them! at least the version we have.

the problem in your case seems to be that your moblock couldn't build the guardian.p2p file and therefore doesn't start.

try update again

---

### Post by Garret88 on 2007-11-24
> **Odin25 said:**
> we use them! at least the version we have.

the problem in your case seems to be that your moblock couldn't build the guardian.p2p file and therefore doesn't start.

try update again

WoW now it seems to work, or not????

> garret@server:~$ **sudo moblock-control update**
[sudo] password for garret:
Updating blocklists and reloading MoBlock   ...done.
garret@server:~$ **sudo moblock-control status**
Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT 13449 packets, 15M bytes)
 pkts bytes target     prot opt in     out     source               destination         
   75  6084 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
   77 11626 moblock_in  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 moblock_fw  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain OUTPUT (policy ACCEPT 11806 packets, 1337K bytes)
 pkts bytes target     prot opt in     out     source               destination         
   75  6084 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0           
  933 70227 moblock_out  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain moblock_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   77 11626 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    7   420 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
  585 35100 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
  341 34707 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * **moblock is running**, pid is 5305.
garret@server:~$ 


---

### Post by Odin25 on 2007-11-25
> **Garret88 said:**
> WoW now it seems to work, or not????

try:
```
sudo moblock-control test
```

also try:

```
tail -f /usr/log/moblock.log
```
this will show you the progress while generating the guardian.p2p and later shows you which connections are blocked (if you do the test you will also see the blocking)

and

```
tail -f /usr/log/moblock-control.log
```

---

### Post by Garret88 on 2007-11-25
Results: 

> garret@server:~$ **sudo moblock-control test**
[sudo] password for garret:
Testing MoBlock: trying to ping 4.18.162.102 from /etc/moblock/guarding.p2p ...
 * MoBlock blocked the IP. Test succeeded.
garret@server:~$ **tail -f /usr/log/moblock.log**
tail: impossibile aprire `/usr/log/moblock.log' per la lettura: Nessun file o directory
tail: nessun file rimasto
garret@server:~$ **tail -f /usr/log/moblock-control.log**
tail: impossibile aprire `/usr/log/moblock-control.log' per la lettura: Nessun file o directory
tail: nessun file rimasto
garret@server:~$ 


---

### Post by Odin25 on 2007-11-25
> garret@server:~$ tail -f /usr/log/moblock.log

sorry it should have been var not usr:

tail -f /var/log/moblock.log
tail -f /var/log/moblock-control.log

but the
> Testing MoBlock: trying to ping 4.18.162.102 from /etc/moblock/guarding.p2p ...
* MoBlock blocked the IP. Test succeeded.
shows that it was successful anyway :-)

congrats

EDIT: PS: I don't know how familiar you are with linux (so just in case): you don't need "tail" you can also have a look with an editor into the log-files; tail is used to continuously show the last lines of the log

---

### Post by Garret88 on 2007-11-26
in **/var/log/moblock.log**:
> Reopening logfile.
Blocked OUT: Cky Murray Electric,hits: 1,DST: 65.114.125.144
Blocked OUT: Istituto Elettrotecnico Nazionale Galileo Ferraris,hits: 1,DST: 193.204.114.105
Blocked OUT: ETH/UNIZH Camp Net,hits: 1,DST: 129.132.73.207

in **/var/log/moblock-control.log**:
> 2007-11-26 06:18:54 CET Begin: /usr/bin/moblock-control update
Updating blocklists ...
Updating ads-trackers-and-bad-pr0n.gz * .
Updating bogon.gz * .
Updating dshield.gz * .
Updating hijacked.gz * .
Updating iana-multicast.gz * . No update available.
Updating iana-private.gz * . No update available.
Updating iana-reserved.gz * . No update available.
Updating level1.gz * .
Updating level2.gz * .
Updating Microsoft.gz * .
Updating rangetest.gz * .
Updating spider.gz * .
Updating spyware.gz * .
Updating templist.gz * .
Updating trojan.gz * . No update available.
 * Blocklists updated.
Building blocklist   ...done.
Installing blocklist to /etc/moblock/guarding.p2p   ...done.
Reloading MoBlock   ...done.
2007-11-26 06:20:15 CET End: /usr/bin/moblock-control update

works not?

---

### Post by misfitpierce on 2007-11-26
Try going to moblock website and getting newest version for gutsy...

then in terminal you just type sudo moblock-control update and it should work

---

### Post by Garret88 on 2007-11-26
> **misfitpierce said:**
> Try going to moblock website and getting newest version for gutsy...

then in terminal you just type sudo moblock-control update and it should work

But i have the repo of moblock-deb.... so i have the last version.

---

### Post by Odin25 on 2007-11-26
> **Garret88 said:**
> in **/var/log/moblock.log**:


in **/var/log/moblock-control.log**:


works not?

everything looks great, everything that should be blocked is blocked; and you know how to check for it
you can relax now :-)

Have a nice day

---

### Post by pelle.k on 2007-11-26
good catch! thanks odin. :)

---

### Post by Garret88 on 2007-11-26
But with moblock-deb is the same thing of peerguardian on windows or for example moblock has more lists(or less...)?

---

### Post by jre on 2007-11-27
> **Garret88 said:**
> But with moblock-deb is the same thing of peerguardian on windows or for example moblock has more lists(or less...)?
The lsits are the same + some more. Have a look at /etc/moblock/blocklists.list to see which lists are used.

The functionality is the same, per default no ports are whitelisted (like with peerguardian blocking everything, also http).

---

### Post by yahooadam on 2007-11-27
```
adam@Server1:~/.scripts$ cat /etc/moblock/moblock.conf | grep "IP_REMOVE"
#IP_REMOVE="Bogon;General Electric Company;4.2.162.144-4.2.162.151"
IP_REMOVE="72.55.129.46"
adam@Server1:~/.scripts$ ping yi.org
PING yi.org (72.55.129.46) 56(84) bytes of data.

--- yi.org ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4001ms
```
What am i doing wrong?

---

### Post by jre on 2007-11-27
> **yahooadam said:**
> ```
adam@Server1:~/.scripts$ cat /etc/moblock/moblock.conf | grep "IP_REMOVE"
#IP_REMOVE="Bogon;General Electric Company;4.2.162.144-4.2.162.151"
IP_REMOVE="72.55.129.46"
adam@Server1:~/.scripts$ ping yi.org
PING yi.org (72.55.129.46) 56(84) bytes of data.

--- yi.org ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4001ms
```
What am i doing wrong?

The IP_REMOVE works with "grep" ["try "man grep" to learn more], so it has to match exactly (in parts) lines of your blocklist. But the IP you inserted is not noted down in the blocklist explicitly, only as part of a bigger range.

Alternatively you can directly whitelist IPs, e.g.
IP_TCP_OUT="72.55.129.46"
(also check the IN/FORWARD and the UDP entries, depending on your needs).
If you need help for this I need to know why you want to whitelist the IP

---

### Post by yahooadam on 2007-11-27
yi.org is a dynDNS provider, i have no idea why they are even blocked

it uses ez-ipupdate with the gnudip2 protocol to update your list of IP's

```
# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

IP_TCP_IN="72.55.129.46"
IP_UDP_IN="72.55.129.46"
IP_TCP_OUT="72.55.129.46"
IP_UDP_OUT="72.55.129.46"
IP_TCP_FORWARD="72.55.129.46"
IP_UDP_FORWARD="72.55.129.46"

```
Ive tried that, and i still cant get a ping response (and yes, i did restart moblock)

I just want that IP to be whitelisted, is that possible?

Thanks for any help :)

---

### Post by mredig on 2007-11-28
I am getting the problem where I run the command 

```
moblock-control test
```


and then I get:

```
Testing MoBlock: head: cannot open `/etc/moblock/guarding.p2p' for reading: No such file or directory
trying to ping  from /etc/moblock/guarding.p2p ...
 * Some error occured with ping, no test result.
```

I tried uninstalling moblock and reinstalling using this method:

```
aptitude purge moblock-nfq; aptitude install moblock-nfq
```


There were some errors, but it tried again a few times and ended without errors at the finish. I tried starting moblock and updating and reloading it and it seems to work fine. I get the impression that the guarding.p2p file is just a test ip that it blocks to see if its being blocked, so if no solutions seem to work, would someone mind sharing the contents of that file?

---

### Post by yahooadam on 2007-11-28
guarding.p2p is the blocklist, without it, moblock will be quite useless

try moblock-control update

---

### Post by chronniff on 2007-11-28
I've been using moblock for a log time now, and I just got a new laptop so I wanted to put moblock on it, but it won't fully install.....it looks like it cant download any of the lists right after the installation during the update....does anyone know if the bluetack site is down or something....this is the logfile output when I try to install


```
2007-11-28 12:27:23 PM EST Begin: /usr/bin/moblock-control update
Updating blocklists ...
Updating ads-trackers-and-bad-pr0n.gzstat: cannot stat `ads-trackers-and-bad-pr0n.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating bogon.gzstat: cannot stat `bogon.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating dshield.gzstat: cannot stat `dshield.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating hijacked.gzstat: cannot stat `hijacked.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating iana-multicast.gzstat: cannot stat `iana-multicast.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating iana-private.gzstat: cannot stat `iana-private.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating iana-reserved.gzstat: cannot stat `iana-reserved.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating level1.gzstat: cannot stat `level1.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating level2.gzstat: cannot stat `level2.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating Microsoft.gzstat: cannot stat `Microsoft.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating rangetest.gzstat: cannot stat `rangetest.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating spider.gzstat: cannot stat `spider.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating spyware.gzstat: cannot stat `spyware.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating templist.gzstat: cannot stat `templist.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
Updating trojan.gzstat: cannot stat `trojan.gz': No such file or directory
/usr/bin/moblock-control: line 412: [: -gt: unary operator expected
 * . No update available.
 * Blocklists updated.
Building blocklist * Error 6: www.bluetack.co.uk/config/ads-trackers-and-bad-pr0n.gz not available. Check your /etc/moblock/blocklists.list and try a "moblock-control update" first. Aborting!

```

---

### Post by pelle.k on 2007-11-28
It *is* indeed down. I'm afraid it might (i'm not really sure) be bëcause of this (i've posted this before, people);

> Dear members and guests,

Regretfully we need to let you all know that in one weeks time the site may be closing indefinitely. Our web hosting bill is currently 3 months behind and without this server in operation there will also be no more blocklist updates possible.

We ask you to make a choice and decide on our future. If you want to help keep us alive then we need your support and donations.

There are literally millions of people downloading our files, however only a very small proportion of people find the time to invest anything in return to ensure that our free services can continue.

Everything we do here is offered free of charge, we make absolutely no money whatsoever. We do however spend quite a lot of time to keep everything running as best as we can for your benefit.

In the event that we cannot afford to continue offering our services for free, then we may need to consider introducing a small subscription/fee based service for downloading the blocklist updates and possibly looking towards using ads throughout the site.

We also need more server mirrors to cope with the excessive bandwidth/traffic associated with hosting the lists.

So now you can either choose to do nothing and let BISS die or help support us so that we can continue to support you. If you find any value in our free programs and services here then please consider donating.

The choice is now yours.

Our donation page is here :
[http://www.bluetack.co.uk/donate/index.html](http://www.bluetack.co.uk/donate/index.html)

---

### Post by jre on 2007-11-28
> **yahooadam said:**
> yi.org is a dynDNS provider, i have no idea why they are even blocked

it uses ez-ipupdate with the gnudip2 protocol to update your list of IP's

```
# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

IP_TCP_IN="72.55.129.46"
IP_UDP_IN="72.55.129.46"
IP_TCP_OUT="72.55.129.46"
IP_UDP_OUT="72.55.129.46"
IP_TCP_FORWARD="72.55.129.46"
IP_UDP_FORWARD="72.55.129.46"

```
Ive tried that, and i still cant get a ping response (and yes, i did restart moblock)

I just want that IP to be whitelisted, is that possible?
ok, first I think IP_TCP_OUT="72.55.129.46" should be enough, but it won't hurt you to use more entries.

Now, I can't imagine that you can't ping this IP. Please post your iptables rules (just do a "moblock-control status"). There should be the entries for this IP.
If not, please check the last "start" section in  /var/log/moblock-control.log for iptables errors.
Also check /var/log/moblock.log to see if the IP is really blocked by moblock.
If it's not blocked by moblock you can try "traceroute 72.55.129.46" to see where the ping gets stopped.

Alternatively, (I just had a look at guarding.p2p) you can use this entry:
```
IP_REMOVE="Groupe iWeb Technologies inc:72.55.128.0-72.55.191.255"
```

greets
jre

---

### Post by pelle.k on 2007-11-28
Ok, so i double checked at phoenix labs forums, and bluetack is apparently safe **for now** (last minute donations), and they are working on getting the site up again.
Still, you really should consider donating some money. Maybe that would also not only save bluetack, but also give more reliable blocklist transfers and updates in the future (they need new servers).

---

### Post by chronniff on 2007-11-28
sorry, I didnt see that you had posted that already......yeah I was actually about to donate a little bit of cash, its the least we can do considering priceless service that they provide us....with out them the feds would have surely been knocking on my door ages ago.

---

### Post by DrObviousSo on 2007-11-29
Hm, I've got moblock installed (gutsy 64), but it is not passing it's test:

```
sudo moblock-control test
Testing MoBlock: trying to ping 4.18.162.102 from /etc/moblock/guarding.p2p ...
 * MoBlock did not block the IP, however 4.18.162.102 did not answer.
 * 
 * Maybe 4.18.162.102 is down/doesn't answer to pings
 * or your firewall filtered the ping.
 * 
 * Have a look at "/usr/bin/moblock-control status" and do some manual testing.
```

Here is the output of the status command
```
 sudo moblock-control status
Current iptables rules (this may take awhile):

Chain INPUT (policy DROP 6 packets, 3194 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       10.0.0.2             0.0.0.0/0           tcp flags:!0x17/0x02 
  497  138K ACCEPT     udp  --  *      *       10.0.0.2             0.0.0.0/0           
    0     0 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
  195 20347 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 DROP       0    --  eth0   *       0.0.0.0/0            255.255.255.255     
   12  2970 DROP       0    --  *      *       0.0.0.0/0            10.0.0.255          
    0     0 DROP       0    --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       0    --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       0    --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0             
   25  1052 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        0    -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
77608   60M INBOUND    0    --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 
    0     0 moblock_in  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
    0     0 moblock_in  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 
    0     0 moblock_fw  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
    0     0 moblock_fw  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain OUTPUT (policy DROP 3 packets, 3010 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       10.0.0.4             10.0.0.2            tcp dpt:53 
  498 31973 ACCEPT     udp  --  *      *       10.0.0.4             10.0.0.2            udp dpt:53 
    0     0 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       0    --  *      *       224.0.0.0/8          0.0.0.0/0           
    9   382 DROP       0    --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       0    --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0             
  102 12711 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
85359   27M OUTBOUND   0    --  *      eth0    0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 
    0     0 moblock_out  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
    0     0 moblock_out  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
76468   60M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 1097  308K ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
   43  7470 LSI        0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
   43  7470 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
   43  7470 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
   43  7470 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   18  2405 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
79081   27M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
   61  7543 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 6199  502K ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain moblock_fw (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_in (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_out (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * moblock is running, pid is 28733.

```
I don't really know thing 1 about iptables, so I don't really know what I'm looking at or what I should be manually testing.  I'd appreciate some advice.  Thanks.

---

### Post by raffytaffy on 2007-12-01
Help! my google inc is begin blocked, here are my moblock.conf and moblock-nfq sh files. what do i need to change?
moblock.conf
```
# moblock-control configuration file

# This file is sourced by a bash script. Any line which starts with a # (hash) 
# is a comment and is ignored. If you set the same variable several times, 
# then only the last line will be used. You have to stop/restart/reload moblock
# if you change entries.

############################ General configuration ############################

# Specify the format of the blocklists that you use. You can´t mix different
# formats.
# d - eMule ipfilter.dat format
# n - peerguardian .p2b v2 binary format
# p - peerguardian .p2p text format
BLOCKLIST_FORMAT="p"

# Specify a NFQUEUE queue number (default 0)
# Works only with -nfq version
NFQUEUE_NUMBER="0"

# Turn on/off automatic start
# 0 - Don´t start MoBlock at system boot
# 1 - Start MoBlock at system boot
MOBLOCK_INIT="1"

# Turn on/off automatic blocklist update
# 0 - Don´t update the blocklists automatically
# 1 - Update the blocklists automatically
MOBLOCK_CRON="1"


################## Settings for the iptables firewall rules ###################

# MoBlock requires the iptables rule NFQUEUE (nfq version)
# or the deprecated QUEUE (ipq version).

# Do a "moblock-control stop" before you change these iptables settings.

# Define how traffic is sent to MoBlock
# 0 - Don't set any iptables rules.
#     You or another script/firewall has to do this!
# 1 - NFQUEUE is in the chains moblock_in, moblock_out and moblock_fw.
IPTABLES_SETTINGS="1"

# Define when traffic is sent to the chain that contains NFQUEUE
# This section works only for IPTABLES_SETTINGS="1"
# 0 - Do nothing. You or another script/firewall has to do this!
# 1 - Insert the rules at the head of the chains.
# 2 - Append the rules to the end of the chains.
IPTABLES_ACTIVATION="2"

# Define which traffic shall be sent to NFQUEUE (if it is sent there).
# 0 - All traffic
# 1 - Only NEW traffic
IPTABLES_STATE="1"

############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name.
# Seperate several entries with whitespace (" ")
# Port ranges are specified in the format "port:port"

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN="yahoo Google Inc"
WHITE_UDP_IN="yahoo Google Inc"
WHITE_TCP_OUT="yahoo Google Inc"
WHITE_TCP_OUT="http https 5050 1863 60481 pop3 smtp"
WHITE_UDP_OUT="yahoo Google Inc"
WHITE_TCP_FORWARD="yahoo Googl Inc"
WHITE_UDP_FORWARD="yahoo Google Inc"

################################ Whitelist IPs ################################

# Whitelist either a network name, a hostname (please note that specifying any
# name to be resolved with a remote query such as DNS is a really bad idea), a
# network IP address (with /mask), or a plain IP address.
# The mask can be either a network mask or a plain number, specifying the number
# of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent
# to 255.255.255.0.
# Seperate several entries with whitespace (" ")

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

IP_TCP_IN="Google Inc"
IP_UDP_IN="Google Inc"
IP_TCP_OUT="Google Inc"
IP_UDP_OUT="Google Inc"
IP_TCP_FORWARD="Google Inc"
IP_UDP_FORWARD="Google Inc"

###################### Remove lines from the blocklist ########################

# Remove lines from the blocklist
# Seperate lines with a semicolon. The example will delete lines that contain 
# either "Bogon", "General Electric Company" or "4.2.162.144-4.2.162.151"
IP_REMOVE="Google Inc"

# Do a "moblock-control reload" when you have changed these settings.
IP_REMOVE="Yahoo"

########################### Full LSB compatibility ############################

# The control script uses /lib/lsb/init-functions. In Debian this file also
# provides functions which are not defined by the LSB standard. Change this
# entry if the script complains of not knowing a function.
# 0 - Debian compatible system (default)
# 1 - LSB 3.1 but not Debian compatible system
LSB_MODE=0
```
moblock-nfq sh

```
#!/bin/sh
#
# MoBlock.sh - MoBlock start script
# ---------------------------------

ACTIVATE_CHAINS=1
WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT="http https 1863 5050 pop3 smtp"
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""
IP_REMOVE="yahoo\! Google Inc"


PIDF=/var/run/moblock.pid

FNAME=`basename $0 .sh`
MODE=`echo $FNAME|awk -F-  '{print $2}'`

if [ -f $PIDF  ]; then
	PID=`cat $PIDF`
	if [ `ps -p $PID|wc -l` -gt 1 ]; then
		echo "$0: $PIDF exists and processs seems to be running. Exiting."
		exit 1;
	fi;
fi;

if [ -f /usr/bin/moblock-ipq ]; then
	modprobe ip_queue
	TARGET="QUEUE"
elif [ -f /usr/bin/moblock-nfq ]; then
	modprobe ipt_NFQUEUE
	TARGET="NFQUEUE"
fi;

modprobe ipt_state

# Filter all traffic, edit for your needs

iptables -N MOBLOCK_IN
iptables -N MOBLOCK_OUT
iptables -N MOBLOCK_FW

if [ $ACTIVATE_CHAINS -eq 1 ]; then
	iptables -I INPUT -p all -m state --state NEW -j MOBLOCK_IN
	iptables -I OUTPUT -p all -m state --state NEW -j MOBLOCK_OUT
	iptables -I FORWARD -p all -m state --state NEW -j MOBLOCK_FW	
fi;


iptables -I MOBLOCK_IN -p all -j $TARGET
#iptables -I MOBLOCK_IN -m state --state ESTABLISHED,RELATED -j ACCEPT 

iptables -I MOBLOCK_OUT -p all -j $TARGET
#iptables -I MOBLOCK_OUT -m state --state ESTABLISHED,RELATED -j ACCEPT 

iptables -I MOBLOCK_FW -p all -j $TARGET
#iptables -I MOBLOCK_FW -m state --state ESTABLISHED,RELATED -j ACCEPT 

for PORT in $WHITE_TCP_OUT; do
	iptables -I MOBLOCK_OUT -p tcp --dport $PORT -j ACCEPT
done
for PORT in $WHITE_UDP_OUT; do
	iptables -I MOBLOCK_OUT -p udp --dport $PORT -j ACCEPT
done

for PORT in $WHITE_TCP_IN; do
	iptables -I MOBLOCK_IN -p tcp --dport $PORT -j ACCEPT
done
for PORT in $WHITE_UDP_IN; do
	iptables -I MOBLOCK_IN -p udp --dport $PORT -j ACCEPT
done

for PORT in $WHITE_TCP_FORWARD; do
	iptables -I MOBLOCK_FW -p tcp --dport $PORT -j ACCEPT
done
for PORT in $WHITE_UDP_FORWARD; do
	iptables -I MOBLOCK_FW -p udp --dport $PORT -j ACCEPT
done


# Loopback traffic fix

iptables -I INPUT -p all -i lo -j ACCEPT
iptables -I OUTPUT -p all -o lo -j ACCEPT

# Here you can change block list and log files
/usr/bin/moblock $@

# On exit delete the rules we added

if [ $ACTIVATE_CHAINS -eq 1 ]; then
	iptables -D INPUT -p all -m state --state NEW -j MOBLOCK_IN
	iptables -D OUTPUT -p all -m state --state NEW -j MOBLOCK_OUT
	iptables -D FORWARD -p all -m state --state NEW -j MOBLOCK_FW
fi;

iptables -D INPUT -p all -i lo -j ACCEPT
iptables -D OUTPUT -p all -o lo -j ACCEPT

iptables -F MOBLOCK_IN
iptables -X MOBLOCK_IN
iptables -F MOBLOCK_OUT
iptables -X MOBLOCK_OUT
iptables -F MOBLOCK_FW
iptables -X MOBLOCK_FW

if [ -f $PIDF ]; then	
	rm $PIDF;
fi
```

---

### Post by jre on 2007-12-02
> **DrObviousSo said:**
> Hm, I've got moblock installed (gutsy 64), but it is not passing it's test:
Your iptables settings are too complex, so I won't have a look at them.

General answer: moblock works this way:
All IPs listed in /etc/moblock/guarding.p2p will be dropped if the iptables rules are configured to send packets to moblock (moblock checks packets with the target NFQUEUE).
All dropped packets are listed in /var/log/moblock.log.

Since the "test" is really basic you have to test moblock manually. Open a terminal and do a "tail -f /var/log/moblock.log" - here you will see live which packets are dropped.
Now ping in another terminal any IP from the blocklist (the "test" checks the very first IP).
If they appear in the logfile - good
If they answer - bad
If they don't appear in the logfile but also don't answer - make a traceroute and check out when the packet is lost:
- first hop: good, some of your iptables rules did block the IP
- any later hop: bad, the packet left your machine and just got lost somewhere else

> **raffytaffy said:**
> Help! my google inc is begin blocked, here are my moblock.conf and moblock-nfq sh files. what do i need to change?
Only moblock.conf, MoBlock-nfq.sh is not used.
To not block Yahoo and Goofle set in moblock.conf
```
IP_REMOVE="yahoo;google"
```
and do a "moblock-control reload". Don't set the same variable several times (as you did in your moblock.conf), since then only the last entry will be used.

This is only one solution, you also might do it other ways. Please have a look at the HOWTO before you ask further questions.

greets
jre

---

### Post by pelle.k on 2007-12-02
Another thing, please folks - **use [CODE] tags**, because that's what they're for. quotes have no scrollbars, and thus take up unnecessary space in the thread.

---

### Post by raffytaffy on 2007-12-03
Tried what JRE said, still google is blocked. Applied temp fix, I added ports 995 and 465 to the whitelist and i can send and receive mail with evolution now, however i dont see this as a permanent fix. I still cant unblock google using the "IP_REMOVE=google" script :(
Current rules

WHITE_TCP_OUT="http https 5050 1863 60481 5222 465 995"

---

### Post by pelle.k on 2007-12-03
Thanks for your edit raffytaffy. now, did you remove the second IP_REMOVE variable like jre said?
```
###################### Remove lines from the blocklist ########################

# Remove lines from the blocklist
# Seperate lines with a semicolon. The example will delete lines that contain 
# either "Bogon", "General Electric Company" or "4.2.162.144-4.2.162.151"
IP_REMOVE="Google Inc"

# Do a "moblock-control reload" when you have changed these settings.
IP_REMOVE="Yahoo" **## remove this line!!!!!**
```

Also, "Google Inc" is neither a domain name nor an ip adress, so remove those entries you made...
```
################################ Whitelist IPs ################################

# Whitelist either a network name, a hostname (please note that specifying any
# name to be resolved with a remote query such as DNS is a really bad idea), a
# network IP address (with /mask), or a plain IP address.
# The mask can be either a network mask or a plain number, specifying the number
# of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent
# to 255.255.255.0.
# Seperate several entries with whitespace (" ")

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

IP_TCP_IN="**Google Inc**"
IP_UDP_IN="**Google Inc**"
IP_TCP_OUT="**Google Inc**"
IP_UDP_OUT="**Google Inc**"
IP_TCP_FORWARD="**Google Inc**"
IP_UDP_FORWARD="**Google Inc**"
```

Again, "Google Inc" and "yahoo" are also *not* valid TCP/UDP ports in any way, so remove those as well...

```
############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name.
# Seperate several entries with whitespace (" ")
# Port ranges are specified in the format "port:port"

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN="yahoo Google Inc"
WHITE_UDP_IN="yahoo Google Inc"
WHITE_TCP_OUT="yahoo Google Inc"
WHITE_TCP_OUT="http https 5050 1863 60481 pop3 smtp"
WHITE_UDP_OUT="yahoo Google Inc"
WHITE_TCP_FORWARD="yahoo Googl Inc"
WHITE_UDP_FORWARD="yahoo Google Inc"
```

I suggest you read up a bit on some of those terms i just mentioned, because moblock isn't, and never was meant for the general public, but rather for advanced users or at least people who at least know to some degree what they are doing.

I suggest you follow my advice in the FAQ and track down *what* you need to unblock in real-time. Then, either whitelist a port number (nothing wrong with that) or a "search term" in ip remove depending on what you found out when tracking moblock.log.

Good luck.

---

### Post by antharr on 2007-12-03
I updated my system last night and the update listed Moblock as an update. I figured nothing could go wrong by just updating. Man was I wrong. My Moblock install is hosed. Could someone give me some advice here. I will include some stuff here to see if any of you guys can figure it out. I have tried to uninstall and I still ge t the error 6 code. 


Here are the commands I have tried to run:

> keith@ubuntudesktop:~$ sudo moblock-control test
/usr/bin/moblock-control: line 92: [: too many arguments
 * Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
keith@ubuntudesktop:~$ sudo gedit /etc/moblock/moblock.conf

keith@ubuntudesktop:~$ sudo moblock-control restart
/usr/bin/moblock-control: line 92: [: too many arguments
 * Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
keith@ubuntudesktop:~$ tail -f /var/log/moblock.log
Skipping useless range: (050309) W32.Rahack 4899
Skipping useless range: (050428) W32.Spybot 1433 6000
Skipping useless range: (050412) W32.Rahack 4899
Skipping useless range: (050326) Unassigned 33437
Ranges loaded: 257286
Reopening logfile.
Blocked IN: IMC ONLINE,hits: 1,SRC: 66.155.119.35
Blocked IN: DSL.net, Inc,hits: 1,SRC: 65.86.215.78
Blocked IN: DSL.net, Inc,hits: 2,SRC: 65.86.215.78
Got SIGTERM! Dumping stats and exiting.




Here is my /etc/moblock/moblock.conf file:

> # moblock-control configuration file

# This file is sourced by a bash script. Any line which starts with a # (hash) 
# is a comment and is ignored. If you set the same variable several times, 
# then only the last line will be used. You have to stop/restart/reload moblock
# if you change entries.

############################ General configuration ############################

# Specify the format of the blocklists that you use. You can´t mix different
# formats.
# d - eMule ipfilter.dat format
# n - peerguardian .p2b v2 binary format
# p - peerguardian .p2p text format
BLOCKLIST_FORMAT="p"

# Specify a NFQUEUE queue number (default 0)
# Works only with -nfq version
NFQUEUE_NUMBER="0"

# Turn on/off automatic start
# 0 - Don´t start MoBlock at system boot
# 1 - Start MoBlock at system boot
MOBLOCK_INIT="1"

# Turn on/off automatic blocklist update
# 0 - Don´t update the blocklists automatically
# 1 - Update the blocklists automatically
MOBLOCK_CRON="1"


################## Settings for the iptables firewall rules ###################

# MoBlock requires the iptables rule NFQUEUE (nfq version)
# or the deprecated QUEUE (ipq version).

# Do a "moblock-control stop" before you change these iptables settings.

# Define how traffic is sent to MoBlock
# 0 - Don't set any iptables rules.
#     You or another script/firewall has to do this!
# 1 - NFQUEUE is in the chains moblock_in, moblock_out and moblock_fw.
IPTABLES_SETTINGS="1"

# Define when traffic is sent to the chain that contains NFQUEUE
# This section works only for IPTABLES_SETTINGS="1"
# 0 - Do nothing. You or another script/firewall has to do this!
# 1 - Insert the rules at the head of the chains.
# 2 - Append the rules to the end of the chains.
IPTABLES_ACTIVATION="2"

# Define which traffic shall be sent to NFQUEUE (if it is sent there).
# 0 - All traffic
# 1 - Only NEW traffic
IPTABLES_STATE="1"

############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name.
# Seperate several entries with whitespace (" ")

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT=""
WHITE_TCP_OUT="http https"
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""

################################ Whitelist IPs ################################

# Whitelist either a network name, a hostname (please note that specifying any
# name to be resolved with a remote query such as DNS is a really bad idea), a
# network IP address (with /mask), or a plain IP address.
# The mask can be either a network mask or a plain number, specifying the number
# of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent
# to 255.255.255.0.
# Seperate several entries with whitespace (" ")

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

IP_TCP_IN=""
IP_UDP_IN=""
IP_TCP_OUT=""
IP_UDP_OUT=""
IP_TCP_FORWARD=""
IP_UDP_FORWARD=""

###################### Remove lines from the blocklist ########################

# Remove lines from the blocklist
# Seperate lines with a semicolon. The example will delete lines that contain 
# either "Bogon", "General Electric Company" or "4.2.162.144-4.2.162.151"
#IP_REMOVE="Bogon;General Electric Company;4.2.162.144-4.2.162.151"

# Do a "moblock-control reload" when you have changed these settings.
IP_REMOVE=""

########################### Full LSB compatibility ############################

# The control script uses /lib/lsb/init-functions. In Debian this file also
# provides functions which are not defined by the LSB standard. Change this
# entry if the script complains of not knowing a function.
# 0 - Debian compatible system (default)
# 1 - LSB 3.1 but not Debian compatible system
LSB_MODE=0

Thanks.

---

### Post by jre on 2007-12-03
There's a bug in MoBlock: When you use multiple lists and ranges have to be merged then IPs which are higher than the first merged range aren't blocked. See here: [https://sourceforge.net/tracker/index.php?func=detail&aid=1818886&group_id=162910&atid=825649](https://sourceforge.net/tracker/index.php?func=detail&aid=1818886&group_id=162910&atid=825649) 
 
Workaround: use a clean list. 
Warning: if you use a list in ipfilter.dat format then you have to change the option how MoBlock loads this. 
 
I'll prepare new packages when I find some time (not now). 
 

On a better side I released MoBlock 0.8-32 yesterday. Changelog: [http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/moblock/moblock-0.8/moblock-0.8/debian/changelog?view=markup](http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/moblock/moblock-0.8/moblock-0.8/debian/changelog?view=markup) 
Including: 
- New option to insert custom iptables rules 
- more output to STDOUT (sent by mail from cron), but also configurable turn off STDOUT 

> **raffytaffy said:**
> Tried what JRE said, still google is blocked.
Did you "moblock-control reload"?
Which are the IPs that are blocked? (/var/log/moblock.log)

---

### Post by jre on 2007-12-03
> **antharr said:**
> I updated my system last night and the update listed Moblock as an update. I figured nothing could go wrong by just updating. Man was I wrong. My Moblock install is hosed. Could someone give me some advice here. I will include some stuff here to see if any of you guys can figure it out. I have tried to uninstall and I still ge t the error 6 code. 
Well, I guess you kept your old moblock.conf.
Just place a
```
VERBOSITY="1"
```
somewhere in moblock.conf. Or **purge** and reinstall moblock.

Thanks pelle for your last post, I totally agree.

---

### Post by Maczimus on 2007-12-03
Wondering if anyone can help I just reinstalled Gutsy and added the repository and key per the instructions on the Moblock Deb website. I am having an error installing Moblock though...


E: moblock-nfq: subprocess post-installation script returned error exit status 6


can anyone tell me what to do to fix this? I have to remove it completely to install any other packages...

Thanks ahead of time.

---

### Post by antharr on 2007-12-03
> **jre said:**
> Well, I guess you kept your old moblock.conf.
Just place a
```
VERBOSITY="1"
```
somewhere in moblock.conf. Or **purge** and reinstall moblock.

Thanks pelle for your last post, I totally agree.

Thanks man. That was exactly the problem. You are a lifesaver.

---

### Post by n0ctem on 2007-12-04
I'm trying to remove moblock so that I can reinstall, but I keep getting this error:

```
Removing moblock-nfq ...
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: error processing moblock-nfq (--purge):
 subprocess pre-removal script returned error exit status 6
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Trying to stop moblock doesn't work either.

Any help would be much appreciated. Thanks.

---

### Post by raffytaffy on 2007-12-04
I seemed to have solved my problems. As someone before mentioned there was an update which indeed broke my moblock. So I removed it with all config files, and reinstalled. Configured the lists from scratch and it works well now. Here is the moblock.config I use now.
```
# moblock.conf - configuration file for moblock-control

# This file is sourced by a bash script. Any line which starts with a # (hash) 
# is a comment and is ignored. If you set the same variable several times,
# then only the last line will be used. You have to stop/restart/reload moblock
# if you change entries.

############################ General configuration ############################

# Specify the format of the blocklists that you use. You can´t mix different
# formats.
# d - eMule ipfilter.dat format
# n - peerguardian .p2b v2 binary format
# p - peerguardian .p2p text format
BLOCKLIST_FORMAT="p"

# Specify a NFQUEUE queue number (default 0)
# Works only with -nfq version
NFQUEUE_NUMBER="0"

# Turn on/off automatic start
# 0 - Don´t start MoBlock at system boot
# 1 - Start MoBlock at system boot
MOBLOCK_INIT="1"

# Turn on/off automatic blocklist update
# 0 - Don´t update the blocklists automatically
# 1 - Update the blocklists automatically
MOBLOCK_CRON="1"

# Set the verbosity of moblock-control
# 0 - No normal output to STDOUT, only to logfile
# 1 - Output to STDOUT and to logfile
VERBOSITY="1"

################## Settings for the iptables firewall rules ###################

# MoBlock requires the iptables rule NFQUEUE (nfq version)
# or the deprecated QUEUE (ipq version).

# Do a "moblock-control stop" before you change these iptables settings.

# Define how traffic is sent to MoBlock
# 0 - Don't set any iptables rules.
#     You or another script/firewall has to do this!
# 1 - NFQUEUE is in the chains moblock_in, moblock_out and moblock_fw.
# 2 - Set custom iptables rules (defined in
#     /etc/moblock/iptables-custom-insert.sh and iptables-custom-remove.sh)
IPTABLES_SETTINGS="1"

# Define when traffic is sent to the chain that contains NFQUEUE
# This section works only for IPTABLES_SETTINGS="1"
# 0 - Do nothing. You or another script/firewall has to do this!
# 1 - Insert the rules at the head of the chains.
# 2 - Append the rules to the end of the chains.
IPTABLES_ACTIVATION="2"

############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name
# (using iptables with the target RETURN)
# Seperate several entries with whitespace (" ")
# Port ranges are specified in the format "port:port"

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT=""
# This is an example to whitelist outgoing web traffic (port 80 is the service
# http, 443 is https) and the port range 1000-1024:
WHITE_TCP_OUT="80 443 5050 1863 5222 465 995"
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""

################################ Whitelist IPs ################################

# Whitelist either a network name, a hostname (please note that specifying any
# name to be resolved with a remote query such as DNS is a really bad idea), a
# network IP address (with /mask), or a plain IP address.
# (using iptables with the target RETURN)
# The mask can be either a network mask or a plain number, specifying the number
# of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent
# to 255.255.255.0.
# Seperate several entries with whitespace (" ")

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

IP_TCP_IN=""
IP_UDP_IN=""
IP_TCP_OUT=""
# This is an example to whitelist the range 192.168.178.1-192.168.178.255:
# IP_TCP_OUT="192.168.178.0/24"
IP_UDP_OUT=""
IP_TCP_FORWARD=""
IP_UDP_FORWARD=""

###################### Remove lines from the blocklist ########################

# Remove lines from the blocklist (using "grep -v -i")
# Warning for beginners: If you want to whitelist a special IP then check the
# above section. In most cases you won't succeed if you insert an IP here.
# Seperate values with a semicolon ";".

# Do a "moblock-control reload" when you have changed these settings.

IP_REMOVE=""
# This is an example to remove all lines from the blocklist which contain one
# of the words "google", "yahoo", "altavista", "debian" or "sourceforge":
# IP_REMOVE="google;yahoo;altavista;debian;sourceforge"	

########################### Full LSB compatibility ############################

# The control script uses /lib/lsb/init-functions. In Debian this file also
# provides functions which are not defined by the LSB standard. Change this
# entry if the script complains of not knowing a function.
# 0 - Debian compatible system (default)
# 1 - LSB 3.1 but not Debian compatible system
LSB_MODE=0

```

---

### Post by freedom on 2007-12-04
you dont need to reinstall everything
this morning I do update and moblock was broken but...
just by adding

VERBOSITY="1"

which was not in my moblock.conf 
and after
```
sudo moblock-control restart 
```
problem is solved 
;)

---

### Post by jre on 2007-12-04
> **Maczimus said:**
> E: moblock-nfq: subprocess post-installation script returned error exit status 6
6 is configuration error. In most cases this means that a blocklist (configured in /etc/moblock/blocklists.list) could not be downloaded. Therefore moblock won't start.
Just remove the missing blocklists from the conffile for a while or try updating the lists again.

---

### Post by wilberfan on 2007-12-04
Thanks for these posts...I was very sad last night when my beloved Moblock wouldn't install on my new mythbuntu partition!   :(

(Boy, you don't miss the water, till the well runs dry, do ya!)

All seems well this morning!  :guitar:

---

### Post by mellowd on 2007-12-04
> **jre said:**
> Well, I guess you kept your old moblock.conf.
Just place a
```
VERBOSITY="1"
```
somewhere in moblock.conf. Or **purge** and reinstall moblock.

Thanks pelle for your last post, I totally agree.

Works perfectly, thanks!

btw, I've never done a purge, how is that done?

---

### Post by pelle.k on 2007-12-04
```
sudo apt-get purge moblock-nfq; sudo apt-get install moblock-nfq
```
This is recommended, since the VERBOSITY variable may not be the only thing changed in the last update. save your changes from moblock.conf and merge them when you've purged the installation.

---

### Post by mellowd on 2007-12-04
> **pelle.k said:**
> ```
sudo apt-get purge moblock-nfq; sudo apt-get install moblock-nfq
```
This is recommended, since the VERBOSITY variable may not be the only thing changed in the last update. save your changes from moblock.conf and merge them when you've purged the installation.

Fantastic. I was having trouble trying to remove moblock, it simply wouldn't do it. 

Thanks again!

---

### Post by Maczimus on 2007-12-04
> **jre said:**
> 6 is configuration error. In most cases this means that a blocklist (configured in /etc/moblock/blocklists.list) could not be downloaded. Therefore moblock won't start.
Just remove the missing blocklists from the conffile for a while or try updating the lists again.

Thanks. I got moblock working but it scared me when it would give me the error whenever i would reinstall it (after removing it) but I have tailed the log and it is blocking sites.

Thanks again.

---

### Post by SpookyET on 2007-12-07
Is there any way to allow HTTP traffic like PeerGuardian?

---

### Post by wilberfan on 2007-12-07
> **SpookyET said:**
> Is there any way to allow HTTP traffic like PeerGuardian?


Look in this section of the moblock.conf?:

> ############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name
# (using iptables with the target RETURN)
# Seperate several entries with whitespace (" ")
# Port ranges are specified in the format "port:port"

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT=""
# This is an example to whitelist outgoing web traffic (port 80 is the service
# http, 443 is https) and the port range 1000-1024:
[COLOR="Red"]WHITE_TCP_OUT="80 443 5050 1863 5222 465 995"[/COLOR]
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""

---

### Post by SpookyET on 2007-12-08
> **wilberfan said:**
> Look in this section of the moblock.conf?:

I did that, and it's still blocking. Maybe it's blocking another port that firefox needs before it contacts port 80.

I'm using pipfilter.dat.gz (Paranoid IP filter).

---

### Post by pelle.k on 2007-12-08
> # Do a "moblock-control restart" when you have changed these settings.
And no, http traffic generally uses port 80.

---

### Post by naminem on 2007-12-08
when i start moblock, i can't access the internet.

i have allowed for http and https.

but when i allow certain ports in UDP, it works. (the ports being used changes when i restart comp)

can anyone tell me what's up? i'm using swiftfox btw.

---

### Post by jre on 2007-12-09
In the next version (0.8-33) I have removed the distinction between UDP and TCP protocol. So whitelisting (ports or IPs) will work for all protocols then - I think that solves many problems some users had.
After the experience of the last update this is also an warning to **replace your old conf files on the next update with the maintainer conf file** because the name of the whitelisting changes, there will only be:
```
WHITE_IP_IN
WHITE_IP_OUT
WHITE_IP_FORWARD
WHITE_PORT_IN
WHITE_PORT_OUT
WHITE_PORT_FORWARD
```
The old variables
```
WHITE_TCP_...
WHITE_UDP_...
IP_TCP_...
IP_UDP_...
``` aren't used any more.

Further I've changed the default blocklist to [www.bluetack.co.uk/config/nipfilter.dat.gz](www.bluetack.co.uk/config/nipfilter.dat.gz) because of bug 1818886 ([https://sourceforge.net/tracker/index.php?func=detail&aid=1818886&group_id=162910&atid=825649](https://sourceforge.net/tracker/index.php?func=detail&aid=1818886&group_id=162910&atid=825649)).
So the configured blocklist format changed to ipfilter.dat (-d) instead of peerguardian .p2p text (-p) format (changed in moblock.conf AND blocklists.list)!

greets
jre

---

### Post by jamesford on 2007-12-10
whats the status on fixing bug 1818886 ? i presume the aim is to get it fixed. im kinda unhappy with the nipfilter solution cos its not updated very regularly, and of course u cant choose the blocklists that suits u
(yes im aware i can use moblock the 'old' way still - just enquiring about the status and what the plans are)

---

### Post by jre on 2007-12-11
> **jamesford said:**
> whats the status on fixing bug 1818886 ? i presume the aim is to get it fixed. im kinda unhappy with the nipfilter solution cos its not updated very regularly, and of course u cant choose the blocklists that suits u
(yes im aware i can use moblock the 'old' way still - just enquiring about the status and what the plans are)

well, I have no more info than what is written in the bug report. So the upstream author recommends to use a clean blocklist for now and he'd like to fix the bug. But there are no changes in the CVS yet.
Personally I'm not able to do that, I'm only a script kiddie ;-)

greets
jre

---

### Post by SpookyET on 2007-12-11
Moblock is blocking my router. 

I've tried
IP_TCP_IN="192.168.10.1"
IP_UDP_IN="192.168.10.1"
IP_TCP_OUT="192.168.10.1"
IP_UDP_OUT="192.168.10.1"

And did a moblock-control restart, but it still does not work
I tried 192.168.10.1/24 as well.

**I want to enable 192.168.10.1 (router), and 192.168.10.101-192.168.10.255 (computers).**

If I ping my router, I get
**Blocked OUT: Bogon,,hits: 1,DST: 192.168.10.1**

By the way, what are WHITE/IP_TCP/UDP_FORWARD="" ?

---

### Post by pelle.k on 2007-12-11
Eh, i suggest you read this post by jre. (4 posts up)
[http://ubuntuforums.org/showpost.php?p=3920594&postcount=935](http://ubuntuforums.org/showpost.php?p=3920594&postcount=935)

Also, if you are using those variables, you didn't replace those files in the latest update with the "maintainers version", and that is another reason to purge moblock, and reinstall it.

---

### Post by SpookyET on 2007-12-11
> **pelle.k said:**
> Eh, i suggest you read this post by jre. (4 posts up)
[http://ubuntuforums.org/showpost.php?p=3920594&postcount=935](http://ubuntuforums.org/showpost.php?p=3920594&postcount=935)

Also, if you are using those variables, you didn't replace those files in the latest update with the "maintainers version", and that is another reason to purge moblock, and reinstall it.

That does not answer my question.

---

### Post by gav616 on 2007-12-11
its blocking you i.e localhost 127.0.0.1 out.. 

:) doing its job then

---

### Post by SpookyET on 2007-12-11
> **gav616 said:**
> its blocking you i.e localhost 127.0.0.1 out.. 

:) doing its job then

I need it to not block my router and other computers on my local network. They are in the bogon list.

---

### Post by SpookyET on 2007-12-11
My problem is that local network my router is in the BOGON list and my NETWORK is in the EMC List.

Whitelisting IP addresses DOES NOT WORK.

I've tried
"192.168.10.0-192.168.10.255"
"192.168.10.0/24-192.168.10.255/24"
"192.168.10.0:192.168.10.255"
"192.168.10.0/24:192.168.10.255/24"
"192.168.10.1"
"192.168.10.101"

I've tried that for all
IP_TCP_IN, IP_UDP_IN, IP_TCP_OUT, IP_UDP_OUT, IP_TCP_FORWARD, IP_UDP_FORWARD.

It does not work

IPTABLES_SETTINGS=1 as well

It blocks gnome services. it blocks a lot of things it should not. I cannot use it.

---

### Post by pelle.k on 2007-12-11
I hate to be a smartass, but i just told you these variables wont work;
> IP_TCP_IN, IP_UDP_IN, IP_TCP_OUT, IP_UDP_OUT, IP_TCP_FORWARD, IP_UDP_FORWARD

If you "purge" moblock, and then install it, you will get a new "moblock.conf" (among other things), with the variables that do work. :)

Also, this isn't the first timew the bogon blocklists have local ip:s in it, and i usually comment it in "blocklists.list".

---

### Post by SpookyET on 2007-12-11
> **pelle.k said:**
> I hate to be a smartass, but i just told you these variables wont work;


If you "purge" moblock, and then install it, you will get a new "moblock.conf" (among other things), with the variables that do work. :)

Also, this isn't the first timew the bogon blocklists have local ip:s in it, and i usually comment it in "blocklists.list".

0.8-33 is not in the repository yet.

---

### Post by pelle.k on 2007-12-11
Oh :oops:
My bad. What i'd like to now is what output you get from moblock-control status. That'll show us if iptables got it right.

---

### Post by SpookyET on 2007-12-11
> **pelle.k said:**
> Oh :oops:
My bad. What i'd like to now is what output you get from moblock-control status. That'll show us if iptables got it right.

I've attached the blocklist and conf file.
I can confirm that the LAN is in the blocklist in Bogon and EMC.
I can confirm that the IP address whitelists are ignored.

---

### Post by jre on 2007-12-14
Now i really released 0.8-33 (see [http://ubuntuforums.org/showpost.php?p=3920594&postcount=935](http://ubuntuforums.org/showpost.php?p=3920594&postcount=935) or just the changelog. BTW you can see this also online (before updating), just have a look at the news section on moblock-deb.sf.net). For all people with whitelisting problems: I think this solves them.
For everybody: Renew all your conf files on update

Further I've added Ubuntu hardy heron support.

jre

---

### Post by SpookyET on 2007-12-14
> **jre said:**
> Now i really released 0.8-33 (see [http://ubuntuforums.org/showpost.php?p=3920594&postcount=935](http://ubuntuforums.org/showpost.php?p=3920594&postcount=935) or just the changelog. BTW you can see this also online (before updating), just have a look at the news section on moblock-deb.sf.net). For all people with whitelisting problems: I think this solves them.
For everybody: Renew all your conf files on update

Further I've added Ubuntu hardy heron support.

jre

I was not confused about the differences between TCP and UDP. It was just not working.

**IP whitelisting is [now] working.** Before, even though I saw the IP listed with the status command, it was being blocked.  **PORT WHITELISTING IS NOT WORKING.**
As you can see in the moblock-status.txt, they are not being added. Maybe moblock on your dev machine assumes some things.

I've attached the files.

Feature Request:
Show port in log. In the case bellow, mail-notify is accessing GMAIL, and I don't know what port to enable.
Blocked OUT: Google,hits: 1,DST: 66.249.83.19

It would be nice if it was application aware, like a firewall. But, I don't think iptables supports that. I'm not sure how firewalls based on iptables work.

---

### Post by sloter on 2007-12-14
Hello Jre,


Thanks for this new update.
Just after the update from rev32 to rev33 I had the error exit 6 from the post-install script.

The root cause was that moblock-control was not able to find the new ipfilter.dat.gz list.

Thus I had to run a sudo moblock-control update and then start moblock.

Does the .deb post-install script run a moblock-control update before starting moblock daemon ?


I like the description output when moblock-control test. It rocks!


Thank you,
sloter

---

### Post by sloter on 2007-12-14
Hello SpookyET,


I guess "http" or "https" port designations are no more working with WHITE_PORT_OUT :(
But "80" "443" or whatever port number you wish works fine with me :)

I put the following line in the /etc/moblock/moblock.conf
```
WHITE_PORT_OUT="80 443"
```
Then I
```
moblock-control restart
```
I have access to all the web site I want from my web browser :)


Have fun!
sloter

---

### Post by SpookyET on 2007-12-14
> **sloter said:**
> Hello SpookyET,


I guess "http" or "https" port designations are no more working with WHITE_PORT_OUT :(
But "80" "443" or whatever port number you wish works fine with me :)

I put the following line in the /etc/moblock/moblock.conf
```
WHITE_PORT_OUT="80 443"
```
Then I
```
moblock-control restart
```
I have access to all the web site I want from my web browser :)


Have fun!
sloter

If you look at my atachments, you'll see that I have more ports and if  you look at the status atachment, you'll see that they are not being added to the iptables.

```
WHITE_PORT_OUT="80 443 587 993 1863 5050 5190 1000:1024"
```

---

### Post by jre on 2007-12-14
> **SpookyET said:**
> I was not confused about the differences between TCP and UDP. It was just not working.
**IP whitelisting is [now] working.** Before, even though I saw the IP listed with the status command, it was being blocked.
I had similar problems ;-)
and I 'guess there are just more protocols than UDP and TCP, therefore the change did not only remove this distinction but also added other protocols. But well, I'm no pro here. Perhaps there's a bug in my script or in iptables?

> **SpookyET said:**
> **PORT WHITELISTING IS NOT WORKING.**
As you can see in the moblock-status.txt, they are not being added.
Yes.
BTW: Do several 'moblock-control stop' until you have a empty iptables list, because you have duplicate entries in INPUT, OUTPUT, FORWARD

OK, hidden between much text the core of my message; I'm just finding the error although there are still some strange things. With your moblock.conf moblock-control.log gives:
```
iptables v1.3.8: Unknown arg `--dport'
```
Some minutes later; argh, I'm just releasing 0.8-34, reverting the port whitelisting changes: From `man iptables`
```
multiport: Up to 15 ports can be specified. A port range (port:port) counts as two ports. **It can only be used in conjunction with -p tcp or -p udp**.
``` Honestly, I waited extra days before releasing to be sure to not make an error, I was absolutely sure that I had tested this :-/ Errare humanum est.

> **SpookyET said:**
> Feature Request:
Show port in log. In the case bellow, mail-notify is accessing GMAIL, and I don't know what port to enable.
Blocked OUT: Google,hits: 1,DST: 66.249.83.19
This has to be done upstream (moblock.berlios.de). But AFAIK you're not the first to request this feature.

> **SpookyET said:**
> It would be nice if it was application aware, like a firewall. But, I don't think iptables supports that. I'm not sure how firewalls based on iptables work.
Again, upstream. But I doubt, too, that this is possible with iptables.

Spooky, you asked some time ago what FORWARD is for: when you're machine running MoBlock is acting as a router, it is forwarding traffic e.g. from your workstation to another host. If you've installed MoBlock on your workstation (common case) then you don't need FORWARD.

> **sloter said:**
> Just after the update from rev32 to rev33 I had the error exit 6 from the post-install script.
The error 6 will result for all people who have problems downloading the ipfilter.dat the first time. Sorry, I can't do anything about that.
Thanks for your warm words.

---

### Post by SpookyET on 2007-12-14
> **jre said:**
> I had similar problems ;-)
and I 'guess there are just more protocols than UDP and TCP, therefore the change did not only remove this distinction but also added other protocols. But well, I'm no pro here. Perhaps there's a bug in my script or in iptables?


Yes, I tested your moblock.conf here and had a look at /var/log/moblock-control.log tells us).
BTW: Do several 'moblock-control stop' until you have a empty iptables list, because you have duplicate entries in INPUT, OUTPUT, FORWARD

OK, hidden between much text the core of my message; I'm just finding the error although there are still some strange things. With your moblock.conf moblock-control.log gives:
```
iptables v1.3.8: Unknown arg `--dport'
```
Some minutes later; argh, I'm just releasing 0.8-34, reverting the port whitelisting changes: From `man iptables`
```
multiport: Up to 15 ports can be specified. A port range (port:port) counts as two ports. **It can only be used in conjunction with -p tcp or -p udp**.
``` Honestly, I waited extra days before releasing to be sure to not make an error, I was absolutely sure that I had tested this :-/ Errare humanum est.


This has to be done upstream (moblock.berlios.de). But AFAIK you're not the first to request this feature.


Again, upstream. But I doubt, too, that this is possible with iptables.

Spooky, you asked some time ago what FORWARD is for: when you're machine running MoBlock is acting as a router, it is forwarding traffic e.g. from your workstation to another host. If you've installed MoBlock on your workstation (common case) then you don't need FORWARD.


The error 6 will result for all people who have problems downloading the ipfilter.dat the first time. Sorry, I can't do anything about that.
Thanks for your warm words.

I'll wait for it. Hopefully, you did not revert the IP whitelisting changes.

---

### Post by jre on 2007-12-14
> **SpookyET said:**
> I'll wait for it. Hopefully, you did not revert the IP whitelisting changes.

argh (localtime 3 AM), cut&paste error which fixed PORT and broke IP. Just making 0.8-35, lol (with new working IP and old working port whitelisting)

---

### Post by SpookyET on 2007-12-14
> **jre said:**
> argh (localtime 3 AM), cut&paste error which fixed PORT and broke IP. Just making 0.8-35, lol (with new working IP and old working port whitelisting)

It's more secure to have the ports separated by protocol.
It's not confusing for those that understand the difference, but it is confusing when it isn't working.

You can even go further and allowing full control over the protocol using whatever syntax makes sense.

For example, open 80 for tcp, 93 for FOO, 100 for BAR, etc.
WHITELIST_PORT_OUT = 80,TCP 93,FOO  100,BAR

---

### Post by jre on 2007-12-14
> **SpookyET said:**
> You can even go further and allowing full control over the protocol using whatever syntax makes sense.

For example, open 80 for tcp, 93 for FOO, 100 for BAR, etc.
WHITELIST_PORT_OUT = 80,TCP 93,FOO  100,BAR
I think that such a new syntax is too complex and error-prone. You still have the possibility to set your custom iptables in /etc/moblock/iptables-custom-insert.sh and ... remove. IMHO people who want to use more from iptables should do this directly with iptables.

And now, good night, the release is done. I hope all went well, please give me some feedback.

---

### Post by sloter on 2007-12-14
SpookyET,

You are right!
Do not know why I had access to some web sites with my previous conf file [/etc/moblock/moblock.conf]("http://ubuntuforums.org/showpost.php?p=3954059&postcount=951")
but the port whitelisting is not working for me in rev33. :(

Hopefully Jre identified some fixes :)


sloter

---

### Post by SpookyET on 2007-12-14
> **sloter said:**
> SpookyET,

You are right!
Do not know why I had access to some web sites with my previous conf file [/etc/moblock/moblock.conf]("http://ubuntuforums.org/showpost.php?p=3954059&postcount=951")
but the port whitelisting is not working for me in rev33. :(

Hopefully Jre identified some fixes :)


sloter

```

apt-get update
apt-get upgrade

```

0.8-35 works for me. both IP and port whitelisting. I have only tested OUT, not IN.

---

### Post by quad341 on 2007-12-15
I didn't notice anyone post the AMD64 deb's for 0.8-35 so here's mine. They've been working fine for me.

---

### Post by hlx on 2007-12-15
Hi All,
I have a problem with the new update of moblock:

1) when i updated moblock i got this information:

```
Starting MoBlockinvoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: error processing moblock-nfq (--configure):
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

2) when i ran sudo moblock-control test i got this thing
```

Testing MoBlock: 
 * Error 6: /etc/moblock/ipfilter.dat not installed, without a blocklist MoBlock doesn't work!
```

I am running Ubuntu Gutsy, tried removing and reinstalling, purging and still no luck.
Could you help me with this? Any ideas?

---

### Post by moopoo on 2007-12-15
This didn't help me, but Krusader3z:

Update: removing works.. But not updating. The package is detected as broken, as reported before.

[http://ubuntuforums.org/showpost.php?p=3955791&postcount=2](http://ubuntuforums.org/showpost.php?p=3955791&postcount=2)

> **Krusader3z said:**
> I used the command line to install MoBlock, then when I wanted to uninstall it, I had no luck.

So what i did is go into Synaptic Package Manager (System- Administration)
and I ran a search for "moblock"

It found two results, one was marked as already installed, so i marked it to "remove completely" and it was gone.

yours,
moopoo

---

### Post by hlx on 2007-12-15
Thanks, but thats not the issue here:
I updated moblock through automatic updates via synaptic
THEN i those issues started.
I did remove completely through synaptic, I did apt-get purge through command line, I had reinstalled moblock and it didn't helped

Any ideas why?

---

### Post by moopoo on 2007-12-15
Same here.

---

### Post by hlx on 2007-12-15
ok, i think i have a temporary solution:

1) first we need to get guarding.p2p file (file containing ip ranges to be blocked)
i got mine from here:** [http://www2.openmedia.info:8080/p23.html](http://www2.openmedia.info:8080/p23.html)**
download** guarding_full.p2p.zip** and unzip it

2) next copy this file to moblock directory:
```
sudo cp ~/Desktop/guarding_full.p2p /etc/moblock/guarding.p2p
```

3) next we need to edit moblock.conf to set moblock to use right blocklist format. to do this type
```
sudo gedit /etc/moblock/moblock.conf 
```

find a line with** BLOCKLIST_FORMAT**
and change it to
```
BLOCKLIST_FORMAT="p"
```

save and exit

4) start moblock:
```
sudo moblock-control start
```
and check if everything is ok by typing (Update: thanks tenjin1 for pointing out my typo) :
```
sudo moblock-control test
```

sometimes moblock need a bit time to load so when in doubt you can check the status by typing
```
sudo moblock-control status
```

**UPDATE:** (thanks to jre for pointing this out)
you also have to update** blocklists.list** used for updating the ip ranges. if had changed  BLOCKLIST_FORMAT to "p" then  i'd suggest to change the default line from:
```
www.bluetack.co.uk/config/nipfilter.dat.gz
```
to:
```
#www.bluetack.co.uk/config/nipfilter.dat.gz
http://www.bluetack.co.uk/config/level1.gz
```




hope this will help someone. it worked for me.
have fun,
hlx

---

### Post by chinaski on 2007-12-15
today I turned moblock on (after last recent update) and got an error in moblock-control.log

I wanted to reinstall moblock but I made a mess throuhg Synaptic and now I got moblock-ipq (that I tried to install during the mess) that won't remove

I cancelled moblock folder in /etc and now I am stuck to this error anything I try to do, wether it's removing or installing moblock > Setting up moblock-ipq (0.8-35+gutsy) ...
 * Error 6: /etc/moblock/moblock.conf not installed.
dpkg: error processing moblock-ipq (--configure):
 subprocess post-installation script returned error exit status 170
Errors were encountered while processing:
 moblock-ipq
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by tenjin1 on 2007-12-15
Thanks hlx!
This route seems to be working since I was getting the "Error 6: /etc/moblock/ipfilter.dat not installed, without a blocklist MoBlock doesn't work!"

Also just noting....

> **hlx said:**
> 
and check if everything is ok by typing:
```
sudo moblock-config test
```


This is supposed to be ...

```
sudo moblock-control test
```

---

### Post by jre on 2007-12-15
About the error 6: Because of an bug I had to change the default blocklist. I chose one from bluetack (the provider of the old lists) which is in another format. So after the update nobody has a valid blocklist and so everybody has to download a new one. This link sometimes fails (buy bluetack.co.uk an server farm and it will always work). Those unlucky ones where the download fails get the error 6.
(Hey, would anybody prefer an moblock which seems to be completely installed but which lacks a blocklist? - No!)

Solution: Try again to get the blocklist with "moblock-control update".

Of course you can also reconfigure moblock to use another blocklist like hlx advised. **Warning, please change this, hlx: **You also have to change /etc/moblock/blocklists.list for your list/URL. Otherwise the ipfilter.dat blocklist will be downloaded tomorrow and be written over your guarding.p2p. Since you've changed the format this would be, err, not good. Alternatively you can switch off the daily blocklist update moblock.conf


Thanks, quad341, for the amd64 packages

---

### Post by hlx on 2007-12-15
hi jre,
i've updated my post as you said.
thanks for help mate,
cheers
hlx

---

### Post by moopoo on 2007-12-15
**moblock-control update** did the trick, thanks. but now there's a **new problem:**

whitelisting doesn't seem to work anymore. i tried 

```
WHITE_TCP_OUT="http https"
``` and ```
WHITE_TCP_OUT="80 443 1000:1024"
```

in the /etc/moblock/moblock.conf and restarted and/or reloaded moblock several times. after some minutes google and other websites become inaccessible. stopping moblock solves the surfing-problem.

i also experienced that gnome needs more time to load after a restart but that could be another matter.

---

### Post by ivanpantaleon on 2007-12-15
> **moopoo said:**
> **moblock-control update** did the trick, thanks. but now there's a **new problem:**

whitelisting doesn't seem to work anymore. i tried 

```
WHITE_TCP_OUT="http https"
``` and ```
WHITE_TCP_OUT="80 443 1000:1024"
```

in the /etc/moblock/moblock.conf and restarted and/or reloaded moblock several times. after some minutes google and other websites become inaccessible. stopping moblock solves the surfing-problem.

i also experienced that gnome needs more time to load after a restart but that could be another matter.

Im also getting the same errors as moopoo.  I tried uninstall/reinstall and reconfiguring, reloading, stopping numerous times.  This happened when i upgraded from .8-32 to .8-35.  About an hour ago, I noticed that the version number is now .8-36.  Whitelisting still does not work and I can not surf the net.  Am I missing something?  I am using Fiesty 7.04 on a HP DV6000z (yea, don't remind me of the horribleness of the dreaded DV series =P  ).

PS.  I just installed Linux a few days ago and I love it.  This is also my first time posting in the forums, I hope in contributing more in the future =).

---

### Post by daevaofshadow on 2007-12-15
Originally I was having the same issues with whitelisting http/https as everyone else, but I tried what hlx did and it seems to work okay. The only thing I did in addition to that was to whitelist google and yahoo in the ip remove section, so I don't know if that affected anything or not. I hope this issue gets resolved soon!

---

### Post by the_unexpected on 2007-12-15
The error message I keep getting when trying to test/start/stop/restart/uninstall/reinstall moblock (or, for that matter, install any system updates) is:

/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.

I'm not really sure what to look for here...some help would be appreciated. :)

Edit:: I'm running Gutsy for whatever differences that may make.

Second edit:: After looking at the packages installed and the packages that Ubuntu is trying to update, it appears that I have the feisty version of moblock installed. Definitely possible, since I upgraded from feisty to gutsy instead of re-installing. I *would* uninstall and then reinstall the latest version, however, I'm unable to uninstall (through command line, synaptic, etc.)

---

### Post by moopoo on 2007-12-16
hlx's way works. thank you.

UPDATE: No, everything is still blocked.

---

### Post by hlx on 2007-12-16
hi there,
as I don't have any problems with blocking http requests I thought I'll share a bit of moblock.conf settings. (It seems it is very basic, but maybe someone will find it helpfull)

open moblock.conf:
```
sudo gedit /etc/moblock/moblock.conf 
```

find **WHITE_TCP_OUT** and change it to:
```
WHITE_TCP_OUT="http https"
```

notice that in the comments above there is a line that says that it works only for **IPTABLES_SETTINGS="1"** so be sure you have it set the right way (it is in the same file)

additionally find: **IP_REMOVE ** and change it to:
```
IP_REMOVE="google;gmail;gtalk;Google"
```

after that do in terminal:
```
sudo moblock-control reload
```
and: 
```
moblock-control restart
```

and now the fun part:
open moblock log in terminal:
```
tail -f /var/log/moblock.log
```
and in your browser try to open google.com. if then log file will start to show blocked google entries then it might be something serious.on the other hand if no entries for google are showing up that  means  moblock isn't blocking google requests.

hope this will help someone.
cheers,
hlx

---

### Post by chinaski on 2007-12-16
I am sorry to insist, how could I wipe every thing out and make a fresh install?

I have cancelled moblock in /etc and in /usr/bin.. I always get error 6

...help...

> **chinaski said:**
> today I turned moblock on (after last recent update) and got an error in moblock-control.log

I wanted to reinstall moblock but I made a mess throuhg Synaptic and now I got moblock-ipq (that I tried to install during the mess) that won't remove

I cancelled moblock folder in /etc and now I am stuck to this error anything I try to do, wether it's removing or installing moblock

---

### Post by mellowd on 2007-12-16
> **hlx said:**
> 
**UPDATE:** (thanks to jre for pointing this out)
you also have to update blocklists.list used for updating the ip ranges. if had changed  BLOCKLIST_FORMAT to "p" then  i'd suggest to change the default line from:
```
www.bluetack.co.uk/config/nipfilter.dat.gz
```
to:
```
#www.bluetack.co.uk/config/nipfilter.dat.gz
http://www.bluetack.co.uk/config/level1.gz
```


hope this will help someone. it worked for me.
have fun,
hlx

I don't find this anywhere in my moblock.conf file, am I missing something? This is what I see:
```

############################ General configuration ############################

# Specify the format of the blocklists that you use. You canÂ´t mix different
# formats.
# d - eMule ipfilter.dat format
# n - peerguardian .p2b v2 binary format
# p - peerguardian .p2p text format
BLOCKLIST_FORMAT="p"

# Specify a NFQUEUE queue number (default 0)
# Works only with -nfq version
NFQUEUE_NUMBER="0"

# Turn on/off automatic start
# 0 - DonÂ´t start MoBlock at system boot
# 1 - Start MoBlock at system boot
MOBLOCK_INIT="1"

# Turn on/off automatic blocklist update
# 0 - DonÂ´t update the blocklists automatically
# 1 - Update the blocklists automatically
MOBLOCK_CRON="1"


VERBOSITY="1"
```

And then the rest.

(I just updated moblock, it was working fine before)

---

### Post by jingo811 on 2007-12-16
**1.**
If an upgrade has messed up your Moblock is there some command to revert back to the previous version before making the upgrade?

**2.**
What is the proper way to un-install Moblock and start installing from scratch again?
Is this enough or do you need to do some purge stuff also which I don't fully understand how to implement in my commands?
```
root@sama:~# apt-get remove moblock
```

.....

Sorry found this on the first page, so I will follow it and shutup now.
> sudo apt-get purge moblock-nfq; sudo apt-get install moblock-nfq
Well I can't shutup :-) because it didn't work.
```
root@sama:~# **apt-get purge moblock-nfq**
E: Invalid operation purge
root@sama:~# 

```

**3.**
What's the difference between "apt-get remove" and "apt-get purge" anyways which should I use in order to do things correctly?

**4.**
Waah the condom has fallen off I'm unprotected.
> root@sama:~# **uname -r**
2.6.20-16-generic
root@sama:~# **apt-get install moblock-nfq**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  p7zip p7zip-full
The following NEW packages will be installed:
  moblock-nfq
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/43.3kB of archives.
After unpacking 225kB of additional disk space will be used.
Selecting previously deselected package moblock-nfq.
(Reading database ... 172259 files and directories currently installed.)
Unpacking moblock-nfq (from .../moblock-nfq_0.8-36+feisty_i386.deb) ...
Setting up moblock-nfq (0.8-36+feisty) ...
[COLOR="Red"]Reloading MoBlockdpkg: error processing moblock-nfq (--configure):
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
root@sama:~# 

---

### Post by pelle.k on 2007-12-16
Uhm!? Maybe purge isn't a "command" but an "option" in apt-get before gutsy?
```
sudo apt-get --purge remove
```

---

### Post by mellowd on 2007-12-16
I've done a purge and now it works perfectly. This is what I did:

```
sudo aptitude purge moblock-nfq

sudo aptitude install moblock-nfq

moblock-control update
```


Now I get this:

```
root@simba:/new_downloads# moblock-control test
Testing MoBlock:

CAUTION: This is just a simple test to check if MoBlock blocks outgoing
connections. For this one IP from your blocklist will be pinged. This test does
not check if you have sane iptables rules or if your complete blocklist is in
the correct format. Therefore success doesn't imply that everything is working
as you expect it and failure doesn't imply that MoBlock is not working.

Also have a look at "/usr/bin/moblock-control status"

Trying to ping 4.2.145.239 from /etc/moblock/ipfilter.dat ...
 * MoBlock blocked the IP. Test succeeded.
root@simba:/new_downloads#
```

Perfecto :)

---

### Post by jingo811 on 2007-12-16
I still get this error when I follow the purge and aptitude install method mellowd used.
> [COLOR="Red"]Setting up moblock-nfq (0.8-36+feisty) ...
Reloading MoBlockdpkg: error processing moblock-nfq (--configure):
subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
I think there is some Feisty problems on the developer side of this story :confused:

---

### Post by chinaski on 2007-12-16
I am stuck too... how the heck can I totally remove everything and reinstall from scratch??

---

### Post by fj4 on 2007-12-16
I'm having a different issue. Ever since upgrading to 0.8-36+gutsy I get this nasty error:
```
frank@ForGreatJustice:~$ *** stack smashing detected ***: /usr/bin/moblock terminated
```
Sigh. Then:
```
frank@ForGreatJustice:~$ sudo moblock-control status
Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT 11613 packets, 16M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 moblock_in  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 moblock_fw  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain OUTPUT (policy ACCEPT 7642 packets, 561K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 moblock_out  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain moblock_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:1000:1024 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * moblock is dead and /var/run/ pid file exists, pid is .
 * Try "moblock-control stop". Otherwise kill all moblock processes,
 * delete /var/run/moblock.pid and all iptables rules related to MoBlock.

```
/var/run/moblock.pid doesn't exist. Tried complete removal/reinstallation, same results.

The missing pid in this line scare me:
```
* moblock is dead and /var/run/ pid file exists, pid is .
```
Any ideas? :( Thanks in advance.

---

### Post by jre on 2007-12-16
OK, I've just released 0.8-39: I've put sane configuration defaults in the script (they will be overwritten by moblock.conf, so there shouldn't be any more problems with VERBOSITY.
And I've overworked the postinst file, so there shouldn't be any more problems on installation/update (error 6). I were (partly) wrong with my first assumptions of the real origin of the problem, sorry for any inconvenience.

General: If you experience problems, have a look at the logfiles /var/log/moblock.log and moblock-control.log.
If you need assistance here tell your moblock version and try to post relevant parts from the logfiles.

> **ivanpantaleon said:**
> Whitelisting still does not work and I can not surf the net.
If the problems with whitelisting continue with 0.8-39 then please post your moblock.conf, "moblock-control status" and moblock-control.log.
There are no differences between feisty and other packages except how they were compiled.

To **downgrade**: Look for the old deb in /var/cache/apt/archives/
and install it "dpkg -i /path/to/moblock....deb"

> **moopoo said:**
> ```
WHITE_TCP_OUT="http https"
``` and ```
WHITE_TCP_OUT="80 443 1000:1024"
```
I've seen this so often: why do you open ports 1000-1024? This is only an example, there's no need to do that. Except if you want to access something on these ports.

And finally, the IP_REMOVE is case insensitive, so no need for "google;Google".


EDIT: fj4, which distro are you using? I've never seen this problem before.

---

### Post by fj4 on 2007-12-16
I was running Feisty, now upgraded with a verified Gutsy CD.
edit: I tried mellowd's fix, using apt-get purge moblock-nfq, and it worked, but as soon as I change the blocklists.list to add the bluetack lists, the problem returns. I changed it back to the same blocklists I was using with the previous release. I will try the 0.8-39.

---

### Post by chump1039 on 2007-12-16
it looks like the bluetack lists are down right now going by their forums. seems they took the lists down in the hopes of getting some attention and funding for the site.


edit: actually they're up. i was having problems connecting to the nipfilter.dat.gz and they mentioned taking them down on the forums. i tried from work today and could load the file fine. not sure why but i could not get moblock to update and download that file. i went into the conf and white listed 80 and 8080, as well as "nyud.net" and reran the update and everything seemed to work fine

---

### Post by quad341 on 2007-12-16
Updated AMD64 packages attached. Enjoy

---

### Post by the_unexpected on 2007-12-16
I tried the aptitude purge and then installing, got the following:

```
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package moblock-nfq.
(Reading database ... 212246 files and directories currently installed.)
Preparing to replace moblock-nfq 0.8-32+feisty (using .../moblock-nfq_0.8-36+feisty_i386.deb) ...
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 6
dpkg - trying script from the new package instead ...
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/moblock-nfq_0.8-36+feisty_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 6
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 /var/cache/apt/archives/moblock-nfq_0.8-36+feisty_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing moblock-nfq (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 moblock-nfq
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done    
```

Still not sure why it's pulling from Feisty...

Edit:: D'OH! Checked the sources.list file, and it was still set to pull from the moblock feisty repositories (since I'd upgraded through Ubuntu as opposed to a fresh install). Ran apt-get update and tried the purge/install again, still gave me the same error message. See below:

```
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://moblock-deb.sourceforge.net gutsy/main moblock-nfq 0.8-39+gutsy [43.6kB]
Fetched 43.6kB in 1s (36.5kB/s)     
Selecting previously deselected package moblock-nfq.
(Reading database ... 212246 files and directories currently installed.)
Preparing to replace moblock-nfq 0.8-32+feisty (using .../moblock-nfq_0.8-39+gutsy_i386.deb) ...
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 6
dpkg - trying script from the new package instead ...
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/moblock-nfq_0.8-39+gutsy_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 6
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 /var/cache/apt/archives/moblock-nfq_0.8-39+gutsy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing moblock-nfq (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 moblock-nfq
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done  
```

It gave the following message during both purges:

```
dpkg: error processing moblock-nfq (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

---

### Post by Zeikcied on 2007-12-16
I'm having trouble.

MoBlock is running, but it doesn't seem to be doing anything.  I do a test, and it doesn't block the ping (though the ping doesn't respond at all, anyway).  I did tests with other pings I found in the IP Filter file, and they didn't respond.  Yet the log didn't show any blocks.

The Test thing mentioned to wait until the log shows this:

NFQUEUE: binding to queue '0'

But I wait several minutes, and that doesn't show up in the log.  It only seems to show up in the log when I do "sudo moblock-control update" and even then it shows right before the update happens.

When I do "tail /var/log/moblock.log" I get this output.

```
Duplicated range ( Bogo )
Ranges loaded: 231231
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'

Got SIGHUP! Dumping and resetting stats, reloading blocklist

Duplicated range ( Bogo )
Ranges loaded: 231231
```

Then nothing more is added to the log until I go and do something.

I've tried it with the nipfilter.dat.gz and the pipfilter.dat.gz, with the same result both times.  I did apt-get purge moblock-nfq and then reinstalled it, and it still does this.

I can't tell if it's doing anything because the Test isn't working and the log isn't showing any activity beyond my various uses of moblock-control.  Also, I have no clue how to read the moblock-control status output, but I figure I could toss that in with the hopes that someone can tell me if it's actually doing anything.

```
Current iptables rules (this may take awhile):

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     tcp  --  *      *       192.168.0.1          0.0.0.0/0           tcp flags:!0x17/0x02
12305 2949K ACCEPT     udp  --  *      *       192.168.0.1          0.0.0.0/0
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5
   16  5328 DROP       0    --  eth0   *       0.0.0.0/0            255.255.255.255
  160 15360 DROP       0    --  *      *       0.0.0.0/0            192.168.0.255
    0     0 DROP       0    --  *      *       224.0.0.0/8          0.0.0.0/0
    0     0 DROP       0    --  *      *       0.0.0.0/0            224.0.0.0/8
    0     0 DROP       0    --  *      *       255.255.255.255      0.0.0.0/0
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0
   41  1808 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID
    0     0 LSI        0    -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5
 421K  503M INBOUND    0    --  eth0   *       0.0.0.0/0            0.0.0.0/0
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input'
    0     0 moblock_in  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW
    0     0 moblock_in  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW
    0     0 moblock_in  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward'
    0     0 moblock_fw  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW
    0     0 moblock_fw  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW
    0     0 moblock_fw  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     tcp  --  *      *       192.168.0.100        192.168.0.1         tcp dpt:53
12316  774K ACCEPT     udp  --  *      *       192.168.0.100        192.168.0.1         udp dpt:53
    0     0 DROP       0    --  *      *       224.0.0.0/8          0.0.0.0/0
    0     0 DROP       0    --  *      *       0.0.0.0/0            224.0.0.0/8
    0     0 DROP       0    --  *      *       255.255.255.255      0.0.0.0/0
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0
  154  6160 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID
 341K   35M OUTBOUND   0    --  *      eth0    0.0.0.0/0            0.0.0.0/0
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output'
    0     0 moblock_out  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW
    0     0 moblock_out  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW
    0     0 moblock_out  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination
 421K  503M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
    2   151 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
    0     0 LSI        0    --  *      *       0.0.0.0/0            0.0.0.0/0

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound '
    0     0 REJECT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination
   10   840 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0
 329K   34M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
11672  515K ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0

Chain moblock_fw (3 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_in (3 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_out (3 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * moblock is running, pid is 26690.
```

---

### Post by fj4 on 2007-12-16
> **chump1039 said:**
> it looks like the bluetack lists are down right now going by their forums. seems they took the lists down in the hopes of getting some attention and funding for the site.

Milady's XP laptop has the Bluetack lists updated in PeerGuardian, so that's not it. Even so, not downloading a list won't cause complete MoBlock crashes.

---

### Post by jingo811 on 2007-12-17
**jre wrote:**
> OK, I've just released 0.8-39: 
Yay that solved everything.

```
$ apt-get --purge remove moblock-nfq     ; remove alone keeps your configs, option purge will permanently delete every last file associated with moblock-nfq
$ apt-get install moblock-nfq
$ moblock-control update
$ moblock-control test
```

Yeah so some big shot on google search recommended using aptitude over apt-get since it handled dependencies and deborphans better but I had to go through hell on an offtopic situations when using aptitude so I'm sticking with apt-get. :)

---

### Post by PhilJ on 2007-12-17
just downloaded the latest update. There are  no blocklists in the /etc/moblock/blocklists.list except for one and all existing blocklists have gone after the update.
In order to reload you will have to add them to blocklists.list and update moblock. some of them  have no update. 

not a complaint just info
thanks for the program

Phil

the list is in /usr/share/doc/moblock-nfq   folder

---

### Post by freedom on 2007-12-17
Yes... one.. :)
Since default list type in moblock.conf is changed to eMule version, only one list is there
[www.bluetack.co.uk/config/nipfilter.dat.gz](www.bluetack.co.uk/config/nipfilter.dat.gz)
and as sayed in /usr/shared/doc/moblock-nfq/README.blocklists
it includes almost everything we used before

Lists from bluetack.co.uk in eMule &#8217;ipfilter.dat&#8217; format:
[http://www.bluetack.co.uk/config/nipfilter.dat.gz](http://www.bluetack.co.uk/config/nipfilter.dat.gz)
This blocklist is the (normal) IP Filter.dat for loading into Emule.
The nipfilter.dat file includes the following ranges pre-merged into it:
1. Level1
2. Bogon list
3. Hijacked IP blocks
4. IANA Multicast
5. IANA Private
6. IANA Reserved
7. level2 corp
8. Microsoft
9. NonLan list
10. templist
;)

---

### Post by PhilJ on 2007-12-17
but for some reason nothing was being blocked until I altered blocklists.list adding all the lists. After this moblock updated the lists then started blocking. I'm no expert so I dont know why this happened . Moblock-control.log showed  ranges loaded 0
merged ranges 0 
skipped ranges 0 

 until I altered the file and restarted moblock now it shows 
ranges loaded 328575
merged ranges 614
skipped 9125

Philj

---

### Post by jre on 2007-12-17
> **PhilJ said:**
> but for some reason nothing was being blocked until I altered blocklists.list adding all the lists. After this moblock updated the lists then started blocking. I'm no expert so I dont know why this happened . Moblock-control.log showed  ranges loaded 0
merged ranges 0 
skipped ranges 0 

 until I altered the file and restarted moblock now it shows 
ranges loaded 328575
merged ranges 614
skipped 9125
I guess you kept your old moblock.conf with wrong settings. For the ipfilter.dat you need ```
BLOCKLIST_FORMAT="d"
``` in /etc/moblock/moblock.conf.



Zeikcied (all users not using special iptables rules/firewalls can stop reading here), you have to be careful with your iptables settings (and since you have some advanced settings you should learn what they mean.
I guess you're using an firewall together with MoBlock. Except with "firehol" there exists no known solution for firewalls in combination with MoBlock 0.8.

All traffic that is ACCEPTed in your rules before it is sent to MoBlock won't be checked by MoBlock but will simply be accepted. The same goes for DROP rules: packets matching these will be dropped and not be checked by MoBlock. Last but not least, your general rule DROP is undermined by MoBlock, who ACCEPTs packets which aren't blocked.

Now to MoBlock: You have three times the same rule, I don't know how this happened, but this shouldn't be. Do "moblock-control stop" untill there isn't  any moblock rule in your iptables settings. Then "moblock-control start" once.
Since Moblock is the last rule in your chains it's generally well configured, but keep in mind what I wrote in the last paragraph.

Finally, follow the logfile live with ```
tail **-f** /var/log/moblock.log
```.

The "status" shows that no (0 in the first two columns) packet ever reached MoBlock. So you have to tweak your iptables rules so that traffic is sent to MoBlock:

Since you're already having a general DROP only the traffic that is allowed by you will be possible. So you have to insert on the ports where you want to allow traffic the iptables target NFQUEUE (queue number 0).
The easiest way is to do this with the "custom iptables settings" (see /etc/moblock/moblock.conf). You can insert your iptables rules for insertion and deletion in /etc/moblock/iptables-custom-insert.sh and iptables-custom-remove.sh.
Just remember that every packet that passes through NFQUEUE to MoBlock (0.8) will either be ACCEPTed or DROPped.
If your new to iptables rules you will have to learn something ;-)

You can also use firehol, see the HOWTO for instructions. Other firewalls are not compatible with MoBlock 0.8

Greets
jre

---

### Post by gav616 on 2007-12-17
IBM Co i.e iana is being blocked every second(which is good i guess, coz i have no LAN set up or NAT), wish i could stop this from happening in the first place though...

like make ubuntu disable lan access altogether? ha?

---

### Post by moopoo on 2007-12-17
**Victory!** As mentioned before, I couldn't surf the web anymore after the latest update.

I had a look into the log file (/var/log/moblock.log) and realized that moblock now **blocks my router**.

```
Consig,hits: 10,SRC: 192.168.178.1
```

So I edited the config and uncommented the example to whitelist IPs:

```
sudo gedit /etc/moblock/moblock.conf

```

```
################################ Whitelist IPs ################################
...
# This is an example to whitelist the range 192.168.178.1-192.168.178.255:
WHITE_IP_OUT="192.168.178.0/24"
```

---

### Post by Zeikcied on 2007-12-17
> **jre said:**
> I guess you're using an firewall together with MoBlock. Except with "firehol" there exists no known solution for firewalls in combination with MoBlock 0.8.
I thought that maybe I could use an extra layer of protection, so I downloaded Firestarter to configure a firewall.  I never thought it'd interfere with MoBlock.  I just assumed there would be two separate instances of iptables or something.  (I've been using Kubuntu for a year now, and most of the "non-visible" stuff I still don't understand.)

> If your new to iptables rules you will have to learn something ;-)
This iptables stuff is confusing enough already.

> You can also use firehol, see the HOWTO for instructions. Other firewalls are not compatible with MoBlock 0.8

Greets
jre
I guess that will have to do.  Thanks for the advice, and I'm glad it's not too difficult of a solution.  I'm hoping removing Firestarter will help things.

---

### Post by spockrock on 2007-12-17
> **moopoo said:**
> **Victory!** As mentioned before, I couldn't surf the web anymore after the latest update.

I had a look into the log file (/var/log/moblock.log) and realized that moblock now **blocks my router**.

```
Consig,hits: 10,SRC: 192.168.178.1
```

So I edited the config and uncommented the example to whitelist IPs:

```
sudo gedit /etc/moblock/moblock.conf

```

```
################################ Whitelist IPs ################################
...
# This is an example to whitelist the range 192.168.178.1-192.168.178.255:
WHITE_IP_OUT="192.168.178.0/24"
```

Thank you I had, the same problem now to figure out why amsn causes my system to lock up when moblock is running....

---

### Post by ivanpantaleon on 2007-12-18
I'm still having troubles surfing the net with Moblock on.  Here are the the logs and conf.  I am using Fiesty .8-39 of moblock.

"Moblock.log""
Duplicated range ( Bogo )
Ranges loaded: 210844
Merged ranges: 0
Skipped useless ranges: 0

"Moblock.conf"
# moblock.conf - configuration file for moblock-control

# This file is sourced by a bash script. Any line which starts with a # (hash) 
# is a comment and is ignored. If you set the same variable several times,
# then only the last line will be used. You have to stop/restart/reload moblock
# if you change entries.

############################ General configuration ############################

# Specify the format of the blocklists that you use. You can´t mix different
# formats.
# d - eMule ipfilter.dat format
# n - peerguardian .p2b v2 binary format
# p - peerguardian .p2p text format
BLOCKLIST_FORMAT="d"

# Specify a NFQUEUE queue number (default 0)
# Works only with -nfq version
NFQUEUE_NUMBER="0"

# Turn on/off automatic start
# 0 - Don´t start MoBlock at system boot
# 1 - Start MoBlock at system boot
MOBLOCK_INIT="1"

# Turn on/off automatic blocklist update
# 0 - Don´t update the blocklists automatically
# 1 - Update the blocklists automatically
MOBLOCK_CRON="1"

# Set the verbosity of moblock-control
# 0 - No normal output to STDOUT, only to logfile
# 1 - Output to STDOUT and to logfile
VERBOSITY="1"

################## Settings for the iptables firewall rules ###################

# MoBlock requires the iptables rule NFQUEUE (nfq version)
# or the deprecated QUEUE (ipq version).

# Do a "moblock-control stop" before you change these iptables settings.

# Define how traffic is sent to MoBlock
# 0 - Don't set any iptables rules.
#     You or another script/firewall has to do this!
# 1 - NFQUEUE is in the chains moblock_in, moblock_out and moblock_fw.
# 2 - Set custom iptables rules (defined in
#     /etc/moblock/iptables-custom-insert.sh and iptables-custom-remove.sh)
IPTABLES_SETTINGS="1"

# Define when traffic is sent to the chain that contains NFQUEUE
# This section works only for IPTABLES_SETTINGS="1"
# 0 - Do nothing. You or another script/firewall has to do this!
# 1 - Insert the rules at the head of the chains.
# 2 - Append the rules to the end of the chains.
IPTABLES_ACTIVATION="2"

############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name
# (using iptables with the target RETURN)
# Seperate several entries with whitespace (" ")
# Port ranges are specified in the format "port:port"
# Up to 15 ports can be specified. A port range (port:port) counts as two
# ports.

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT=""
WHITE_UDP_OUT=""
# This is an example to whitelist outgoing web traffic (port 80 is the service
# http, 443 is https) and the port range 1000-1024:
WHITE_TCP_OUT="80 443 1000:1024"
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""

################################ Whitelist IPs ################################

# Whitelist either a network name, a hostname (please note that specifying any
# name to be resolved with a remote query such as DNS is a really bad idea), a
# network IP address (with /mask), or a plain IP address.
# (using iptables with the target RETURN)
# The mask can be either a network mask or a plain number, specifying the number
# of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent
# to 255.255.255.0.
# Seperate several entries with whitespace (" ")

# This replaces the old (up to 0.8-32) IP_TCP_ and IP_UDP_ entries.

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_IP_IN=""
WHITE_IP_OUT=""
# This is an example to whitelist the range 192.168.178.1-192.168.178.255:
WHITE_IP_OUT="192.168.178.0/24"
WHITE_IP_FORWARD=""

###################### Remove lines from the blocklist ########################

# Remove lines from the blocklist (using "grep -v -i")
# Warning for beginners: If you want to whitelist a special IP then check the
# above section. In most cases you won't succeed if you insert an IP here.
# Seperate values with a semicolon ";".

# Do a "moblock-control reload" when you have changed these settings.

IP_REMOVE=""
# This is an example to remove all lines from the blocklist which contain one
# of the words "google", "yahoo", "altavista", "debian" or "sourceforge":
# IP_REMOVE="google;yahoo;altavista;debian;sourceforge"

########################### Full LSB compatibility ############################

# The control script uses /lib/lsb/init-functions. In Debian this file also
# provides functions which are not defined by the LSB standard. Change this
# entry if the script complains of not knowing a function.
# 0 - Debian compatible system (default)
# 1 - LSB 3.1 but not Debian compatible system
LSB_MODE=0"

"Moblock-control.log"
2007-12-17 20:57:14 PST Begin: /usr/bin/moblock-control update
Updating blocklists ...
Updating nipfilter.dat.gz * . No update available.
 * Blocklists updated.
Building blocklist   ...done.
Installing blocklist to /etc/moblock/ipfilter.dat   ...done.
 * MoBlock is not running.
2007-12-17 20:57:23 PST End: /usr/bin/moblock-control update
2007-12-17 08:57:29 PM PST Begin: /usr/bin/moblock-control restart
Deleting iptables   ...fail!
Stopping MoBlock   ...done.
Inserting iptables   ...done.
Starting MoBlock   ...done.
2007-12-17 08:57:33 PM PST End: /usr/bin/moblock-control restart
* Logging to /var/log/moblock.log
* Ranges loaded: 210844
* Using .dat file format
* Merged ranges: 0
* Skipped useless ranges: 0

---

### Post by spockrock on 2007-12-18
```
WHITE_TCP_OUT=""
```

should be;

```
WHITE_TCP_OUT="80 443"
```

but it does not seem to work, port whitelisting seems to be broken.  I wish moblock in the log displayed the port that an IP was blocked on.....

---

### Post by deviant420 on 2007-12-18
I'm a big time linux newb --- however I thought I'd share my experience with moblock on gutsy.   The instant I installed the ipq package, i was blocked from grabbing the npq package --


it seems that the lists used over at bluetack use blanket-blocking.

or perhaps there are moles submitting ip ranges at bluetack to make the use of such blockers more troublesome than they should be

Anyone have a list that isn't so massive - perhaps anti-p2p folks are lurking on every possible server out there

viva la resistance!

Ron Paul for president!

---

### Post by jre on 2007-12-18
> **ivanpantaleon said:**
> I'm still having troubles surfing the net with Moblock on.  Here are the the logs and conf.  I am using Fiesty .8-39 of moblock.
First off, please post your settings and logs only in CODE tags, that makes reading your posts much easier!
moblock.conf and moblock-control.log look fine so far. Did everything work before the updates of last weekend?


I'm really confused about the reports that whitelisting does not work. I've already received reports saying that everything works.
So for people with problems: Please post "moblock-control status" and verify in /var/log/moblock.log that the IPs were really blocked by MoBlock. Finally always tell your moblock version.

@deviant420, can't be that you are blocked from installing moblock-nfq. Try again.
Have a look at /usr/share/doc/moblock-nfq/README.blocklists.gz to learn more about available blocklists. The level1 list is the most popular one. If You change blocklists remember to configure the right blocklist format, too.

---

### Post by moopoo on 2007-12-18
I don't want to sound narcistic bui this could really **solve** the "**whitelisting doesn't work**" problem.

If you're behind a router and that one is blocked by moblock (or the blocklists) then whitelisting http is futile:

> **moopoo said:**
> **Victory!** As mentioned before, I couldn't surf the web anymore after the latest update.

I had a look into the log file (/var/log/moblock.log) and realized that moblock now **blocks my router**.

```
Consig,hits: 10,SRC: 192.168.178.1
```

So I edited the config and uncommented the example to whitelist IPs:

```
sudo gedit /etc/moblock/moblock.conf

```

```
################################ Whitelist IPs ################################
...
# This is an example to whitelist the range 192.168.178.1-192.168.178.255:
WHITE_IP_OUT="192.168.178.0/24"
```

---

### Post by kacheng on 2007-12-19
If you are still having problems with connecting to the internet, try the following in this order:


1. Whitelist your subnet (i.e. ignore blocklist for internal networking)

What is your IP address and corresponding subnet?  Check using **ifconfig**.  If your IP address is 192.168.1.118, then you want to whitelist everything on 192.168.1.0/24 in 
/etc/moblock/moblock.conf

**WHITE_IP_OUT="192.168.1.0/24"**

Don't forget **sudo moblock-control restart**


2. If you still encounter issues, you may whitelist all http and https services (i.e. ignore blocklist for http and https)

**WHITE_TCP_OUT="http https"**

I found that WHITE_TCP_OUT="80 443 1000:1024" did not work for me.

Don't forget **sudo moblock-control restart**



Good luck. Let us know if this helps you (or hit the 'thanks' icon on the bottom right). Thx.

---

### Post by theotherbastard on 2007-12-19
> **jingo811 said:**
> **jre wrote:**

Yay that solved everything.

```
$ apt-get --purge remove moblock-nfq     ; remove alone keeps your configs, option purge will permanently delete every last file associated with moblock-nfq
$ apt-get install moblock-nfq
$ moblock-control update
$ moblock-control test
```

I had an issue with the upgrade, and fortunately running the above steps was able to resolve it.

However, (assuming some developers for moblock are reading this) since I run moblock on a headless system running this reinstall becomes a pain because it blocks communication with my local network.  (Since I have to effectively blow away my configuration file)  This forces me to haul out a monitor to plug into my system so I can log on locally and fix this issue.

A bit frustrating that this happens what seems to be every time an upgrade comes out.:confused:

---

### Post by fj4 on 2007-12-20
I'm unsure what was so broken about 0.8-36, but 0.8-39 fixed all my problems! :)
Thanks!

---

### Post by jre on 2007-12-20
> **theotherbastard said:**
> I had an issue with the upgrade, and fortunately running the above steps was able to resolve it.

However, (assuming some developers for moblock are reading this) since I run moblock on a headless system running this reinstall becomes a pain because it blocks communication with my local network.  (Since I have to effectively blow away my configuration file)  This forces me to haul out a monitor to plug into my system so I can log on locally and fix this issue.

A bit frustrating that this happens what seems to be every time an upgrade comes out.:confused:

I'm the developer of the debian packages/moblock-control. So all changes (good and bad) in 0.8-xy are from me.
First, I try to change the conf files as seldom as possible. But if there is an improvement to be done or even an bug to be fixed (as in 0.8-33 - 0.8-39) then I think it's better to change it.

Second, if you install via SSH you already have a connection. Since MoBlock only blocks NEW connections this connection won't be blocked. So if you update and edit the moblock.conf during the same session everything should go well. (This is theory, I'm on an Desktop with Monitor)


> **fj4 said:**
> I'm unsure what was so broken about 0.8-36, but 0.8-39 fixed all my problems! :)
Thanks!
/usr/share/doc/moblock-nfq/changelog.Debian.gz tells the story ;-)

greets
jre

---

### Post by Nisun on 2007-12-21
I don't know if this has been covered before but I did search the forums and skim over some of the recent posts..... :(

I had a few problems getting firestarter to play nice with moblock.... so a little iptables work and.... i think its working now. Its my first post (yes im so n00b) and please be gentle :)

well i ran a
```
iptables -L INPUT
```
and saw that moblock was way at the bottom of the table. that didnt seem right so a few little commands to move things

```
# remove moblock_in jump from INPUT table
iptables -D INPUT -p all -m state --state NEW -j moblock_in

# add moblock_in jump from INPUT table
iptables -I INPUT -p all -m state --state NEW -j moblock_in

# remove moblock_in jump from OUTPUT table
iptables -D OUTPUT -p all -m state --state NEW -j moblock_out

# add moblock_in jump from OUTPUT table
iptables -I OUTPUT -p all -m state --state NEW -j moblock_out

# remove moblock_in jump from FORWARD table
iptables -D FORWARD -p all -m state --state NEW -j moblock_fw

# add moblock_in jump from FORWARD table
iptables -I FORWARD -p all -m state --state NEW -j moblock_fw
```

of course i have no idea if this has been covered... or if this really leaves firestarter fully functional at the same time. i did check to make sure that moblock was loggin hits by doing "tail -f /var/log/moblock.log"

Well its nap time. I hope this helps someone

---

### Post by jre on 2007-12-21
> **Nisun said:**
> I had a few problems getting firestarter to play nice with moblock.... so a little iptables work and.... i think its working now. Its my first post (yes im so n00b) and please be gentle :)

Please don´t be offended, but, lol, you did absolutely the wrong thing ;-)
What you did is good to get MoBlock working but you completely ruined firestarter. There´s no known way to use both of these programs (there´s only a solution for firehol and MoBlock known)
Let me explain: MoBlock 0.8 either ACCEPTs or DROPs packets. This means as soon as any traffic is sent to MoBlock it will leave iptables - it will not be checked by any following rule - and since you put MoBlock on the first place ... ;-)
This problem will be solved in MoBlock 0.9
greets
jre

---

### Post by the_unexpected on 2007-12-21
I'm still unable to start or update moblock...I still get the following message:

E: /var/cache/apt/archives/moblock-nfq_0.8-39+gutsy_i386.deb: subprocess new pre-removal script returned error exit status 6

Help, please!

---

### Post by jre on 2007-12-22
> **the_unexpected said:**
> E: /var/cache/apt/archives/moblock-nfq_0.8-39+gutsy_i386.deb: subprocess new pre-removal script returned error exit status 6
Please post (if possible) the complete output of the moblock installation and your /var/log/moblock-control.log, please.
I guess you have the problem I first thought about in the previous cases: sometimes MoBlock simply fails to download the blocklists the first time which results in the exit code 6.
An "moblock-control update" should help then. Further I hope that you installed the new conf files when you were asked.

greets
jre

---

### Post by ivanpantaleon on 2007-12-22
OK, I just fixed my problem.  

What I did was purge Moblock-nfq from the computer, did the white listed the IP ports for internet, THEN finally fixed  the white list IP's.  It was blocking my router.  To whitelist your router, go back to your moblock.conf file look for the WHITE_IP_OUT and copy your router IP address to allow communications with your router.  Don't forget to do a moblock-control restart and reload.

Thx for the help guys, couldn't have done it without the forums =).

---

### Post by the_unexpected on 2007-12-22
This is what I got when I tried to do the purge/reinstall suggested earlier:

```
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package moblock-nfq.
(Reading database ... 212246 files and directories currently installed.)
Preparing to replace moblock-nfq 0.8-32+feisty (using .../moblock-nfq_0.8-36+feisty_i386.deb) ...
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 6
dpkg - trying script from the new package instead ...
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/moblock-nfq_0.8-36+feisty_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 6
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 /var/cache/apt/archives/moblock-nfq_0.8-36+feisty_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing moblock-nfq (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 moblock-nfq
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done    
```

After reading that, I checked the sources.list file, and it was still set to pull from the moblock feisty repositories (since I'd upgraded through Ubuntu as opposed to a fresh install). Changed the sources.list file, ran apt-get update and tried the purge/install again, still gave me the same error message. See below:

```
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://moblock-deb.sourceforge.net gutsy/main moblock-nfq 0.8-39+gutsy [43.6kB]
Fetched 43.6kB in 1s (36.5kB/s)     
Selecting previously deselected package moblock-nfq.
(Reading database ... 212246 files and directories currently installed.)
Preparing to replace moblock-nfq 0.8-32+feisty (using .../moblock-nfq_0.8-39+gutsy_i386.deb) ...
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 6
dpkg - trying script from the new package instead ...
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/moblock-nfq_0.8-39+gutsy_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 6
/usr/bin/moblock-control: line 92: [: too many arguments
* Error 6: Check your VERBOSITY settings in /etc/moblock/moblock.conf.
invoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 /var/cache/apt/archives/moblock-nfq_0.8-39+gutsy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing moblock-nfq (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 moblock-nfq
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done  
```

It gave the following message during both purges:

```
dpkg: error processing moblock-nfq (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

To be honest, I don't remember which option I chose when prompted regarding the conf files, since this has been ongoing for several weeks now. Any help that you could offer would be greatly appreciated. :)

---

### Post by Darles on 2007-12-23
Hi,

I'm having siilar problems as above. If i try and purge i get:

```
dpkg: error processing moblock-nfq (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

If i try to reinstall i get:

```
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 6
dpkg - trying script from the new package instead ...
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/moblock-nfq_0.8-39+feisty_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 6
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 /var/cache/apt/archives/moblock-nfq_0.8-39+feisty_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm unable to remove or reinstall through synaptic either. The problem also stops me from installing any other software. Everytime i try it seems that synaptic is trying to upgrade moblock which it has problems doing.

Any help would obviosuly be appreciated.

---

### Post by durrell on 2007-12-23
I just did a fresh Gutsy install and for some reason moblock is blocking everything. I have gotten http and https unblocked as it says in the how-to, but for some reason anything outside of that is being blocked. I can't get updates or use Synaptic at all while moblock is running.

How can I fix this? I never had this issue in Feisty and I never had it in Gutsy when I first started running it. It just seems to be an issue with this install.

Any help is greatly appreciated. I don't like running my box with no IP blocker. :D

---

### Post by jingo811 on 2007-12-24
OFFTOPIC:

I think that the owners of the Moblock project should talk to some forum admins and get a corner of their own such as one in the 3rd party sub-forums.

Then you should create something like 2 sub-sub-forums.  One for dealing with problems that arises from upgrades.  And another one for learning how to use the complicated functions inside the program.
It seems like the same kind of questions comes back again and again.  The mixing of these 2 issues makes it difficult to read through 100 threads when searching for answers that have already been answered before.

That's my 2 cents.

---

### Post by empthollow on 2007-12-24
> **durrell said:**
> I just did a fresh Gutsy install and for some reason moblock is blocking everything. I have gotten http and https unblocked as it says in the how-to, but for some reason anything outside of that is being blocked. I can't get updates or use Synaptic at all while moblock is running.

How can I fix this? I never had this issue in Feisty and I never had it in Gutsy when I first started running it. It just seems to be an issue with this install.

Any help is greatly appreciated. I don't like running my box with no IP blocker. :D

I have the same problem, i just installed gutsy - fresh install and moblock is blocking everything.  Incidentially i have another gutsy install on my laptop and moblock is working just fine, so... i copied /etc/moblock onto my fresh install of gutsy.  But to no avail, it still is blocking everything - (except google searches, can't click on results though).  To make matters even more confusing both machines tell me moblock is version 0.8.  

OK, fixed my problem.  Didnt' whitelist my router, only the http ports.  i whitelisted my router in the next section and all is well :)

---

### Post by atf487 on 2007-12-25
> **empthollow said:**
> I have the same problem, i just installed gutsy - fresh install and moblock is blocking everything.  Incidentially i have another gutsy install on my laptop and moblock is working just fine, so... i copied /etc/moblock onto my fresh install of gutsy.  But to no avail, it still is blocking everything - (except google searches, can't click on results though).  To make matters even more confusing both machines tell me moblock is version 0.8.  

OK, fixed my problem.  Didnt' whitelist my router, only the http ports.  i whitelisted my router in the next section and all is well :)

I had a similar situation, but whitelisting the router fixed it. Now I can finally have moblock running, woo!

---

### Post by jre on 2007-12-26
@the_unexpected and darles: Your moblock.conf is broken (old version) or non existent. So manually install a new one from the current package:
```
mkdir /home/{YOURLOGIN}/moblock_0.8-39
dpkg -X /var/cache/apt/archives/moblock-nfq_0.8-39+gutsy_i386.deb /home/{YOURLOGIN}/moblock_0.8-39
sudo cp /home/{YOURLOGIN}/moblock_0.8-39/etc/moblock/moblock.conf /etc/moblock/moblock.conf
```

Darles, replace gutsy with feisty in the second line of the above code. Of course you both have to insert your real {YOURLOGIN}.

> **durrell said:**
> I just did a fresh Gutsy install and for some reason moblock is blocking everything. I have gotten http and https unblocked as it says in the how-to, but for some reason anything outside of that is being blocked. I can't get updates or use Synaptic at all while moblock is running.
So whitelisting http and https works? Then you can simply whitelist other protocols or IPs. Check the log (tail -f /var/log/moblock.log) to see what is blocked.
If you have more severe problems: Please post "moblock-control status", I guess you have installed additional firewall software (this will cause problems). Further you need to be more concrete what is not working (which IPs are blocked (see logfile)? On which ports (which application wanted to contact them? or use "whireshark" to analyze the traffic).


> **jingo811 said:**
> I think that the owners of the Moblock project should talk to some forum admins and get a corner of their own such as one in the 3rd party sub-forums.
Maybe a good idea but I guess people would still post here. So next to development I prefer to improve the HOWTO so that it is easier to point people there.

---

### Post by empthollow on 2007-12-26
I just wanted to clarify how i whitelisted my LAN because i did it incorectly at first. Here is the way i got it to work.
```
WHITE_IP_OUT="192.168.1.0/24"
```
the "0" at the end of the ip being the key to my success.  I acts as an all inclusive range for my LAN.

I then for the http ports did
```
WHITE_TCP_OUT="http https"
```

This gave me my web browsing capabilities but it leaves me insecure on ports 80 (http) & 443 (https) so when i use a p2p client such as azureus i tell it to ignore peers with those port numbers.  moblock will take care of the rest.

:guitar:

---

### Post by Scorper on 2007-12-27
How am I supposed to "properly" whitelist the stuff needed to let pidgin connect to MSN? 

I know I can either whitelist the port or the IP(range) but cant I do a combination? Whitelisting the port seems kinda dumb because that would leave the port open for all IPs. And I dont necessarily want to whitelist all the microsoft IP-ranges and all ports either.

And I'm having some problems whitelisting IP-ranges, since I dont understand what the mask thing is...

So what exactly should I put to WHITE_IP_OUT= if I want to allow connections to the ip ranges 207.46.*.* and 64.4.*.*? MSN uses those IPs atleast and maybe some more... I cant find a complete list anywhere. I tried putting WHITE_IP_OUT="207.46.0.0/24" etc. but it still seems to block them. WHITE_IP_OUT="207.46.29.0/24" and such seem to work by allowing the range 207.46.29.* but how can I allow a larger range?

---

### Post by jre on 2007-12-27
> **Scorper said:**
> I know I can either whitelist the port or the IP(range) but cant I do a combination?
You have to use the custom iptables rules to do that. There's no short way for this, sorry.

> **Scorper said:**
> And I'm having some problems whitelisting IP-ranges, since I dont understand what the mask thing is...
From `man iptables`:
"The mask can be either a network  mask or  a plain number, specifying the number of 1&#8217;s at the left side of the network mask.  Thus, a mask of 24 is equivalent to 255.255.255.0."
16 is equivalent to 255.255.0.0 and
8  is equivalent to 255.0.0.0
This mask is [err, I can't really explain it] subtracted from the IP.
So you want:
```
WHITE_IP_OUT="207.46.0.0/16"
```

---

### Post by mikerduffy on 2007-12-28
I just got web browsing to work by replacing the /24 I had with a /16.

---

### Post by jre on 2007-12-28
I've started to package MoBlock 0.9 (Release Candidate 1). So here it is moblock (0.9~rc1-1), use it only if you really want to test it. I've renamed the nfq package and skipped the ipq version. 
This version now allows to MARK packets instead of DROPping or ACCEPTing them. 
I've also added a /etc/moblock/moblock.default configuration file to make future updates easier. 
Warning: This version also logs accepted packages, so your logfile will grow faster than usual. 
 
Please have a look at the Debian package changelog ([http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/moblock/moblock-0.8/moblock-0.8/debian/changelog?view=markup](http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/moblock/moblock-0.8/moblock-0.8/debian/changelog?view=markup)) to get a complete list of the changes. 

jre

---

### Post by empthollow on 2007-12-28
forgive me for asking a simple question but, .. could you explain what it means to mark vs drop or accept?

---

### Post by jre on 2007-12-28
> **empthollow said:**
> forgive me for asking a simple question but, .. could you explain what it means to mark vs drop or accept?
It's the possibility to make many errors ;-)
With moblock 0.8 matched packets (ip in blocklist) were either ACCEPTED or DROPped. So as soon as they were checked by MoBlock they were no more checked by further iptables rules. This means you could not use MoBlock together with other firewalls (except firehol).
Now, you have the option to let MoBlock simply MARK the packets. They will then continue their voyage through later iptables rules, where you can put rules which only apply to the marked packets next to other firewall rules.
The combination of MoBlock with other firewalls is therefore possible now, but we first need some testers ;-)
Further (already done in the packet) OUTPUT matched packets can be rejected instead of being DROPped. So if YOU want to access an IP that is blocked by MoBlock your applications get notified immediately instead of having to wait until they timeout (I really like that.)

Have fun with testing. But remember not to use this blindly.
jre

---

### Post by empthollow on 2007-12-28
from this i gather that the packets marked by moblock are ok unless otherwise determined by further firewall rules.  is that correct?  i don't use a sofware firewall so this has never been an issue for me (i use my router) except when i go on a trip.  I then use firestarter which i think is just a front end to iptables.  i'd be happy to do some testing but i'll need a little instruction on how to see if it's working.  i would use moblock and firestarter. my router would of course still have a firewall and i need that running for all of my other computers.  Let me know if i can be of any help to you. i would need to know what command to run to know if the proper ip's are being blocked though.

---

### Post by AlexEagar on 2007-12-30
> **fj4 said:**
> I'm having a different issue. Ever since upgrading to 0.8-36+gutsy I get this nasty error:
```
frank@ForGreatJustice:~$ *** stack smashing detected ***: /usr/bin/moblock terminated
```

Any ideas? :( Thanks in advance.

I had this same error. The problem for me was that I changed my .dat.gz list to plain .gz lists without changing BLOCKLIST_FORMAT="d" to BLOCKLIST_FORMAT="p" in /etc/moblock/moblock.conf :). Try changing that value and let us know if it resolves your problem. Also remember that you can't use both .dat.gz and .gz at the same time.

Alex Eagar

---

### Post by jre on 2007-12-31
> **empthollow said:**
> from this i gather that the packets marked by moblock are ok unless otherwise determined by further firewall rules.  is that correct?
Yes
> **empthollow said:**
>  i don't use a sofware firewall so this has never been an issue for me (i use my router) except when i go on a trip.  I then use firestarter which i think is just a front end to iptables.For me a software firewall and a frontend for iptables is the same.
> **empthollow said:**
> i'd be happy to do some testing but i'll need a little instruction on how to see if it's working.  i would use moblock and firestarter. my router would of course still have a firewall and i need that running for all of my other computers.  Let me know if i can be of any help to you. i would need to know what command to run to know if the proper ip's are being blocked though.

Ok, install moblock 0.9~rc1-4 (just releasing while I type this).

First, make sure that moblock is started AFTER firestarter (/etc/rc2.d/SNNname: the NN of moblock has to be higher than that of firestarter [does Ubuntu still work this way!?])

Then check and post your iptables rules ("moblock-control status").

Do a "moblock-control test" and "tail -f /var/log/moblock.log". Note the "Marked block" entries in the logfile. Now make a "traceroute" for such an IP:  the packet must not pass the first hop (otherwise it has left your machine).

So, this way you can make sure that the "Marked block" IP from the test really didn't leave your machine. But I can't tell you if this was MoBlock's achievement or firestarter's.
Anyway, I'd take this as "moblock is working" if the rest of the iptables rules make sense.

Now you have to check firestarter: Since you have a LAN with other machines, you can go to another machine and try to access your moblock machine with some ways you would want not to be able (access it on blocked ports).

Try it with two ways: First add a line to "/etc/moblock/ipfilter.dat" like ```
192.168.178.0 - 192.168.178.255 , 000 , Lan,
``` with the IP range of your LAN (With I get ifconfig "inet addr:192.168.178.124", therefore this example entry). Do a "moblock-control reload" and test.

Then whitelist your LAN:
```
WHITE_IP_IN="192.168.178.0/24"
``` Do a "moblock-control restart" and make the same tests again.

In both cases you should not be able to access your MoBlock machine. First time because of MoBlock and firestarter, second time only because of firestarter. A real port scanning would of course be a better test.

greets
jre

---

### Post by NiksaVel on 2008-01-01
Hi, I'm running kubuntu gutsy and I have a problem with autostarting moblock....

even though it's set to 1 (autostart on boot) in the config file, it doesn't start and I have to do it manually....   it works just fine after that...


thanks for the help

---

### Post by jre on 2008-01-01
Which package and version are you using?

Please post ```
ls -l `sudo find /etc/ -name "*moblock*"`

```

Please verify that you have the ```
MOBLOCK_INIT="1"
``` entry only once in your moblock.conf (and moblock.default).


Note: I propose to use "moblock-nfq" currently. The "moblock" package contains newer code but is still in a testing stage.

---

### Post by NiksaVel on 2008-01-02
Well...  I just intalled the whole system like 3 days ago (and moblock along with it as per the instructions int he ubuntu howto) so I guess it's the latest version.


```
niksavel@sidious:~$ ls -l `sudo find /etc/ -name "*moblock*"`
[sudo] password for niksavel:
-rwxr-xr-x 1 root root 1777 2007-12-16 23:46 /etc/cron.daily/moblock-nfq
-rwxr-xr-x 1 root root 2661 2007-12-16 23:45 /etc/init.d/moblock-nfq
-rw-r--r-- 1 root root  366 2007-12-16 23:46 /etc/logrotate.d/moblock-nfq
-rw-r--r-- 1 root root 4787 2007-12-30 14:37 /etc/moblock/moblock.conf
-rw-r--r-- 1 root root 4773 2007-12-30 14:33 /etc/moblock/moblock.conf~
lrwxrwxrwx 1 root root   21 2007-12-30 19:42 /etc/rc0.d/K20moblock-nfq -> ../init.d/moblock-nfq
lrwxrwxrwx 1 root root   21 2007-12-30 19:42 /etc/rc1.d/K20moblock-nfq -> ../init.d/moblock-nfq
lrwxrwxrwx 1 root root   21 2007-12-30 19:42 /etc/rc2.d/S20moblock-nfq -> ../init.d/moblock-nfq
lrwxrwxrwx 1 root root   21 2007-12-30 19:42 /etc/rc3.d/S20moblock-nfq -> ../init.d/moblock-nfq
lrwxrwxrwx 1 root root   21 2007-12-30 19:42 /etc/rc4.d/S20moblock-nfq -> ../init.d/moblock-nfq
lrwxrwxrwx 1 root root   21 2007-12-30 19:42 /etc/rc5.d/S20moblock-nfq -> ../init.d/moblock-nfq
lrwxrwxrwx 1 root root   21 2007-12-30 19:42 /etc/rc6.d/K20moblock-nfq -> ../init.d/moblock-nfq

/etc/moblock:
total 20299
-rw-r--r-- 1 root root      868 2007-12-16 23:45 blocklists.list
-rw-r--r-- 1 root root 10364174 2008-01-01 02:55 ipfilter.dat
-rw-r--r-- 1 root root 10364174 2007-12-31 07:38 ipfilter.dat.backup
-rwxr-xr-x 1 root root      565 2007-12-16 23:45 iptables-custom-insert.sh
-rwxr-xr-x 1 root root      564 2007-12-16 23:45 iptables-custom-remove.sh
-rw-r--r-- 1 root root     4787 2007-12-30 14:37 moblock.conf
-rw-r--r-- 1 root root     4773 2007-12-30 14:33 moblock.conf~
-rwxr-xr-x 1 root root     2647 2007-12-16 23:46 MoBlock-nfq.sh
niksavel@sidious:~$         
```


this is my moblock.conf:
```

# moblock.conf - configuration file for moblock-control

# This file is sourced by a bash script. Any line which starts with a # (hash) 
# is a comment and is ignored. If you set the same variable several times,
# then only the last line will be used. You have to stop/restart/reload moblock
# if you change entries.

############################ General configuration ############################

# Specify the format of the blocklists that you use. You can´t mix different
# formats.
# d - eMule ipfilter.dat format
# n - peerguardian .p2b v2 binary format
# p - peerguardian .p2p text format
BLOCKLIST_FORMAT="d"

# Specify a NFQUEUE queue number (default 0)
# Works only with -nfq version
NFQUEUE_NUMBER="0"

# Turn on/off automatic start
# 0 - Don´t start MoBlock at system boot
# 1 - Start MoBlock at system boot
MOBLOCK_INIT="1"

# Turn on/off automatic blocklist update
# 0 - Don´t update the blocklists automatically
# 1 - Update the blocklists automatically
MOBLOCK_CRON="1"

# Set the verbosity of moblock-control
# 0 - No normal output to STDOUT, only to logfile
# 1 - Output to STDOUT and to logfile
VERBOSITY="1"

################## Settings for the iptables firewall rules ###################

# MoBlock requires the iptables rule NFQUEUE (nfq version)
# or the deprecated QUEUE (ipq version).

# Do a "moblock-control stop" before you change these iptables settings.

# Define how traffic is sent to MoBlock
# 0 - Don't set any iptables rules.
#     You or another script/firewall has to do this!
# 1 - NFQUEUE is in the chains moblock_in, moblock_out and moblock_fw.
# 2 - Set custom iptables rules (defined in
#     /etc/moblock/iptables-custom-insert.sh and iptables-custom-remove.sh)
IPTABLES_SETTINGS="1"

# Define when traffic is sent to the chain that contains NFQUEUE
# This section works only for IPTABLES_SETTINGS="1"
# 0 - Do nothing. You or another script/firewall has to do this!
# 1 - Insert the rules at the head of the chains.
# 2 - Append the rules to the end of the chains.
IPTABLES_ACTIVATION="2"

############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name
# (using iptables with the target RETURN)
# Seperate several entries with whitespace (" ")
# Port ranges are specified in the format "port:port"
# Up to 15 ports can be specified. A port range (port:port) counts as two
# ports.

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT="80 443"
WHITE_UDP_OUT=""
# This is an example to whitelist outgoing web traffic (port 80 is the service
# http, 443 is https) and the port range 1000-1024:
# WHITE_TCP_OUT="80 443 1000:1024"
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""

################################ Whitelist IPs ################################

# Whitelist either a network name, a hostname (please note that specifying any
# name to be resolved with a remote query such as DNS is a really bad idea), a
# network IP address (with /mask), or a plain IP address.
# (using iptables with the target RETURN)
# The mask can be either a network mask or a plain number, specifying the number
# of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent
# to 255.255.255.0.
# Seperate several entries with whitespace (" ")

# This replaces the old (up to 0.8-32) IP_TCP_ and IP_UDP_ entries.

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_IP_IN="192.168.2.0/24"
WHITE_IP_OUT="192.168.2.0/24"
# This is an example to whitelist the range 192.168.178.1-192.168.178.255:
# WHITE_IP_OUT="192.168.178.0/24"
WHITE_IP_FORWARD=""

###################### Remove lines from the blocklist ########################

# Remove lines from the blocklist (using "grep -v -i")
# Warning for beginners: If you want to whitelist a special IP then check the
# above section. In most cases you won't succeed if you insert an IP here.
# Seperate values with a semicolon ";".

# Do a "moblock-control reload" when you have changed these settings.

IP_REMOVE=""
# This is an example to remove all lines from the blocklist which contain one
# of the words "google", "yahoo", "altavista", "debian" or "sourceforge":
# IP_REMOVE="google;yahoo;altavista;debian;sourceforge"

########################### Full LSB compatibility ############################

# The control script uses /lib/lsb/init-functions. In Debian this file also
# provides functions which are not defined by the LSB standard. Change this
# entry if the script complains of not knowing a function.
# 0 - Debian compatible system (default)
# 1 - LSB 3.1 but not Debian compatible system
LSB_MODE=0

```

I don't think I have a moblock.default...

---

### Post by jre on 2008-01-02
Hmm, everything ok so far. Please post "/var/log/moblock-control.log", perhaps that's enlightening.
Sorry, but I have no idea what is wrong.

> **NiksaVel said:**
> Well...  I just intalled the whole system like 3 days ago (and moblock along with it as per the instructions int he ubuntu howto) so I guess it's the latest version.
dpkg --list moblock-nfq
But it should be ok.

> **NiksaVel said:**
> I don't think I have a moblock.default...
Yes, I just added it for moblock (0.9~rc1).

jre

---

### Post by NiksaVel on 2008-01-02
nothing interesting here I'm afraid :)

```

2008-01-02 07:36:07 AM CET Begin: /usr/bin/moblock-control update
Updating blocklists ...
Updating nipfilter.dat.gz * . No update available.
 * Blocklists updated.
Building blocklist   ...done.
Installing blocklist to /etc/moblock/ipfilter.dat   ...done.
Reloading MoBlock   ...done.
2008-01-02 07:36:22 AM CET End: /usr/bin/moblock-control update


```


```

iksavel@sidious:~$ dpkg --list moblock-nfq
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  moblock-nfq    0.8-39+gutsy   An IP blocker for linux
niksavel@sidious:~$

```

---

### Post by rye_ on 2008-01-02
Hi all,

I apologise if this has already been addressed in previous posts (I'd be surprised if it hasn't, but I can't find it).

Could someone explain the meaning on Blocked Out as opposed to Blocked In in terms of the results of tail - f /var/moblock/moblock.log.
And why perhaps whereas I've noticed other peoples log shows Blocked In but mine never does.

[ATTACH]55049[/ATTACH]

Thanks in advance

---

### Post by yahooadam on 2008-01-02
Blocked out means it blocked something on your computer communicating with the world
Blocked In means it stopped some other computer communicating with you

At least, that is my understanding ..
Yahooadam

---

### Post by dn* on 2008-01-02
I dunno if anyone has posted on this thread about this before, but the website that serves the blocklists to MoBlock (bluetack.co.uk) are having some problems funding their servers.

Some of you may be interested in sending them a donation to help them out: [http://www.bluetack.co.uk](http://www.bluetack.co.uk)

---

### Post by rye_ on 2008-01-03
Am I correct then that the reason I get no Blocked In results is that IP tables prevents any computer from connecting to me already.

As things stand with me getting no Blocked In results, am I safe using bittorrent.

Thanks,

Ryan

---

### Post by yahooadam on 2008-01-03
> **rye_ said:**
> Am I correct then that the reason I get no Blocked In results is that IP tables prevents any computer from connecting to me already.

As things stand with me getting no Blocked In results, am I safe using bittorrent.
did you try
```
sudo moblock-control test
```

---

### Post by rye_ on 2008-01-03
Yes, I tried the test and was informed that moblock was functioning accordingly.
However, I think that this only tests any outgoing transmissions that I make to a blocked address, not whether or not such a blocked address can connect to me.

Thanks anyway yahooadam, I appreciate your input.

Ryan

---

### Post by catfishy on 2008-01-04
Hey friends!  I'm having trouble doing anything with moblock.  It worked so well before I tried to update it and now I can't update/remove/re-install or anything.  I can't even install anything because moblock is seriously broken (in a bad state).  I've searched and tried to find a solution but to no avail.  I believe I've tried to force it to remove but nothing works.  Does anyone have any suggestions.  I've tried changing the repository between both feisty and gutsy.  I'm still using Feisty.  My installed version is .8-32 and it's trying to install 39.  Thank you so much for your help!

When I try:
```
sudo apt-get purge moblock-nfq; sudo apt-get install moblock-nfq
```

I am asked to install some of those four files attached.  But when I try to install them 3 of the 4 of them say that I already have newer versions.  The third one: "libnfnetlink0_0.0.16_i386.deb"  says that I have broken dependencies!  AHHHH!

Is there a way to force a removal and re-install later the newer version?  Does the gutsy one work with feisty?

When I try to install it at cmd line I get:
Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.

I found some help at:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3999751](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3999751)
AND THAT DID IT!
My .conf file was messed up or non-existant.  I used a backup and now it's working.  Thanks for listening.

---

### Post by Hawkeye05 on 2008-01-04
ive been trying to get it to work on my torrent server but it always blocks ssh and torrentflux, is there a way i can allow just http and ssh traffic but leave the old settings on the other ports, all i want to block is my torrent traffic thats it.

---

### Post by jre on 2008-01-04
> **NiksaVel said:**
> nothing interesting here I'm afraid :)
Yep, indeed boring ;-) 
Have a look at older moblock-control.log files (they are rotated daily) and check if there's an entry for the failed starting.

Is the package "sysvinit" installed on your machine?


> **rye_ said:**
> However, I think that this only tests any outgoing transmissions that I make to a blocked address, not whether or not such a blocked address can connect to me.
Correct (in fact it only checks "ping", nothing more!). I think there are no blocked IN because nobody wanted to connect to you. This might change when you start any p2p application.
To test it you'd have to  try to connect from another machine to your machine after adding that other machines IP (in the correct syntax) to your blocklist.
Just to be sure: I hope you don't use any additional firewalls/iptbles rules, this would most probably cause troubles (except if you configured firehol correctly and/or are already using moblock 0.9rc1).

hawkeye, I answered in your [other thread]("http://ubuntuforums.org/showthread.php?p=4071458"), please don't double post.

---

### Post by gav616 on 2008-01-05
wow gui is out!! :)

---

### Post by belgofac117 on 2008-01-05
I have just installed moblock 0.9~rc1-4 together with Firestarter on UBuntu 7.10  

Here's the outcome of moblock-control status:


 

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    5   400 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
  350 28670 moblock_in  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
    0     0 ACCEPT     tcp  --  *      *       192.168.0.1          0.0.0.0/0           tcp flags:!0x17/0x02 
   83 20540 ACCEPT     udp  --  *      *       192.168.0.1          0.0.0.0/0           
    0     0 LSI        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
    0     0 LSI        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       0    --  eth0   *       0.0.0.0/0            255.255.255.255     
  890 69746 DROP       0    --  *      *       0.0.0.0/0            192.168.0.255       
    0     0 DROP       0    --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       0    --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       0    --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        0    -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
 1637 1325K INBOUND    0    --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
    0     0 moblock_fw  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
    0     0 LSI        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
    0     0 LSI        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 3 packets, 234 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    5   400 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0           
    1    84 REJECT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa reject-with icmp-port-unreachable 
  280 21303 moblock_out  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
    0     0 ACCEPT     tcp  --  *      *       192.168.0.3          192.168.0.1         tcp dpt:53 
   99  6039 ACCEPT     udp  --  *      *       192.168.0.3          192.168.0.1         udp dpt:53 
    0     0 DROP       0    --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       0    --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       0    --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
 2555  242K OUTBOUND   0    --  *      eth0    0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 1394 1303K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     0    --  *      *       4.79.142.202         0.0.0.0/0           
    0     0 ACCEPT     0    --  *      *       72.14.207.99         0.0.0.0/0           
    0     0 ACCEPT     0    --  *      *       64.233.187.99        0.0.0.0/0           
    0     0 ACCEPT     0    --  *      *       64.233.167.99        0.0.0.0/0           
  243 21870 LSI        0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (6 references)
 pkts bytes target     prot opt in     out     source               destination         
  243 21870 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
  243 21870 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
  243 21870 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (8 references)
 pkts bytes target     prot opt in     out     source               destination         
   16   704 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
   16   704 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
   16   704 REJECT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
 1193  140K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    6   264 LSO        0    --  *      *       0.0.0.0/0            207.46.19.190       
    0     0 LSO        0    --  *      *       0.0.0.0/0            207.46.19.254       
    0     0 LSO        0    --  *      *       0.0.0.0/0            207.46.193.254      
    2    88 LSO        0    --  *      *       0.0.0.0/0            207.46.192.254      
    0     0 LSO        0    --  *      *       0.0.0.0/0            207.68.178.61       
    0     0 LSO        0    --  *      *       0.0.0.0/0            76.74.24.143        
    0     0 LSO        0    --  *      *       0.0.0.0/0            17.149.160.10       
    8   352 LSO        0    --  *      *       0.0.0.0/0            17.251.200.32       
 1346  101K ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain moblock_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     0    --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0x14 
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     0    --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0x14 
  350 28670 RETURN     0    --  *      *       192.168.0.0/24       0.0.0.0/0           
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     0    --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0x14 
  264 20559 RETURN     0    --  *      *       0.0.0.0/0            192.168.0.0/24      
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
   15   660 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    1    84 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * moblock is running, pid is 13540.

-----------------------------------------------------------------------------------------------------------------------------

I do not have a clue how to read this status output but I have done the following:

Started firestarter and added microsoft and Apple to the Firestarter blocking rules.

Tried to browse to MS and Apple but both were blocked by FS.

Started Mb and did a moblock-control test with the IP being blocked by Mb

Picked another IP out of the Ipfilter.dat list and Pinged this IP with the ping tool from networking tools. This IP was not blocked!

How do I know that everything is working fine when 1 IP is blocked and not the other?

---

### Post by belgofac117 on 2008-01-05
To continue from my post above:

I have been following the moblock "story" for quite a while now and I know what pages  too look at to find info.  However, for a beginner this is becoming mission impossible.  Going through 105 pages of info?  

More questions I cannot find an answer for:

I also installed Mobloquer and under blocklists I can only find "nipfilter".
Is this correct?

What command can I use to ping an ip from terminal?


Note!! Testing Firestarter and Moblock is a real challenge since Fs is suffering from a well documented bug in Ubuntu 7.10.  It just exites randomly, especially after opening up the GUI.

---

### Post by jre on 2008-01-06
> **belgofac117 said:**
> Picked another IP out of the Ipfilter.dat list and Pinged this IP with the ping tool from networking tools. This IP was not blocked!
Very short answer: on the first glance your iptable rules look good.
What's in moblock.log when you ping that IP?

---

### Post by jimtb on 2008-01-07
> **belgofac117 said:**
> 
I also installed Mobloquer and under blocklists I can only find "nipfilter".
Is this correct?

Hi, I'm the developer of mobloquer. This is probably correct. Right now only nipfilter.dat is used, due to a bug in moblock.

More information:
[http://forums.phoenixlabs.org/showthread.php?t=15790](http://forums.phoenixlabs.org/showthread.php?t=15790)
[http://www.bluetack.co.uk/forums/index.php?act=dscript&CODE=showdetails&f_id=24](http://www.bluetack.co.uk/forums/index.php?act=dscript&CODE=showdetails&f_id=24)

PS. You can post suggestions and bug reports for mobloquer here too.
PPS. Mobloquer does not work with moblock 0.9 yet.

---

### Post by Jeff_From_VA on 2008-01-07
I just learned a painful lesson, don't install this on a remote server via SSH!!!!  

Now I have to squeeze my fat *** into the closet I have my server in to fix it - LOL

---

### Post by belgofac117 on 2008-01-07
JRE;  Nothing showed up in the log after pinging this IP.
I will continue experimenting with it.

JIMTB:  Mobloquer seems to be working partly with Mb 0.9.  I can start stop, reload and update Mb with it.  

Keep up the good work !

---

### Post by gav616 on 2008-01-08
will there even be an option to not log a certain ip but still block it?

reason is its blocking a dhcp server every 2-5 seconds and my log on conky is very hard to read.

---

### Post by jre on 2008-01-08
@belgoflac,
the command is simply "ping". "traceroute" is a bit more informative because you see **when** a packet is lost.
There's no need to read the complete thread, most info in here is outdated given the age of this thead.
Just to make sure you  use the correct command: use "tail **-f** /var/log/moblock.log" to follow the logfile life.
Having said all this, I have to say that it seems as if there is a bug. (It's already known that merging several blocklists has the result that not all IPs from merged ranges are really blocked. But as I understood it you are simply using bluetack's "nipfilter.dat" (see /etc/moblock/blocklists.list)). Therefore, please give me an example IP from the blocklist which isn't blocked. Please also make a backup of the blocklist - so that I can test it with your blocklist if I can't verify this with my current blocklist.

> **gav616 said:**
> will there even be an option to not log a certain ip but still block it?

reason is its blocking a dhcp server every 2-5 seconds and my log on conky is very hard to read.
No, there's no such option.

---

### Post by belgofac117 on 2008-01-08
Still testing!  I have tried to add the level 1 blocklist form bluetack but I get an error saying the blocklist is not available?

jre: I have changed a few settings in the conf file and this resulted that all IP addresses in the nipfilter list now get blocked (good news).:):

---

### Post by durrell on 2008-01-08
I still can't seem to get it working. It blocks updates and everything.

Edit: I fixed it. I had to whitelist my IP out by using "192.168.1.0/24". That fixed it all. :)

Edit2: Ok now I have a new problem. I need to figure out how to not block traffic from/to my home network. I share a printer and files with other computers. Thanks.

Edit3: Fixed that, too. White_IP_In="192.168.1.0/24"

---

### Post by jre on 2008-01-09
> **belgofac117 said:**
> Still testing!  I have tried to add the level 1 blocklist form bluetack but I get an error saying the blocklist is not available?
```
wget bluetack.co.uk/config/level1.gz
```
works here. Make sure that the update server is not blocked by moblock.
Remember that the level1 is in another format than the ipfilter.dat!
Further remember not to merge multiple blocklists because of the described bug.

Glad to here everything is working now.

---

### Post by 449 on 2008-01-09
Where can I download this? The one at SourceForge is no longer...

---

### Post by jre on 2008-01-10
> **449 said:**
> Where can I download this? The one at SourceForge is no longer...
moblock-deb.sourceforge.net still exists. If you already installed MoBlock then make sure that sourceforge isn't blocked.

---

### Post by belgofac117 on 2008-01-10
jre: The problem is that nipfilter.dat is in .dat format and the bluetack list isn't.

Since you cannot mix lists of different formats I get an error.

Should I just get rid of the nipfilter.dat and use all the bluetack lists or should I just use the nipfilter list?  I only use Moblock because I do not like the idea of anyone sneaking into my pc to see whats on my drives.

---

### Post by jre on 2008-01-11
> **belgofac117 said:**
> jre: The problem is that nipfilter.dat is in .dat format and the bluetack list isn't.

Since you cannot mix lists of different formats I get an error.

Should I just get rid of the nipfilter.dat and use all the bluetack lists or should I just use the nipfilter list?  I only use Moblock because I do not like the idea of anyone sneaking into my pc to see whats on my drives.

Currently you should use only one blocklist because of [this bug]("https://sourceforge.net/tracker/index.php?func=detail&aid=1818886&group_id=162910&atid=825649") (Merging blocklists results in incomplete IP ranges)
Therefore I currently recommend the nipfilter.dat

---

### Post by belgofac117 on 2008-01-20
Hi all,

I hit a little snag.  Youtube is getting blocked by Moblock.  I have added YouTube to the IP_REMOVE but that doesn.t do it.
I then tried to add the Youtube range to WHITE_IP_IN and OUT but I must be doing something wrong.

The manual is saying: Seperate several entries with whitespace (" ").  I have tried many combo's but cannot unblock the Youtube range.  I already got 1 IP (Router) in the WHITE_IP_IN and OUT and want to add the range of 64.15.112.0 - 64.15.127.255.  

How would that entry look like together with my router IP? =  192.168.0.0/24

---

### Post by jackietreehorn on 2008-01-21
Hey,
I just installed moblock, but one question I have (being new to linux in general) is how do I know that the program is working? I know that you have to type:
sudo moblock- control start

in the terminal to the program working, and I did that as well as 
sudo moblock -control status

I guess what I'm asking is how do you know when the program has blocked something? What about editing blocklists as well as updating blocklists? Thanks in advance for the help, I am knew to all this and am just trying to work it all out.

---

### Post by wilberfan on 2008-01-21
> **jackietreehorn said:**
> Hey,
I just installed moblock, but one question I have (being new to linux in general) is how do I know that the program is working? I know that you have to type:
sudo moblock- control start

in the terminal to the program working, and I did that as well as 
sudo moblock -control status

I guess what I'm asking is how do you know when the program has blocked something? What about editing blocklists as well as updating blocklists? Thanks in advance for the help, I am knew to all this and am just trying to work it all out.

I like to have a terminal open and enter:
```
tail -f /var/log/moblock.log
```

It will then display anything it's blocked.   

I believe you can also run a ```
sudo moblock-control test
``` ?

---

### Post by jackietreehorn on 2008-01-21
> **wilberfan said:**
> I like to have a terminal open and enter:
```
tail -f /var/log/moblock.log
```

It will then display anything it's blocked.   

I believe you can also run a ```
sudo moblock-control test
``` ?

when I typed the second code I got ```
pid file /var/run/moblock.pid exists. Not startingmatt@matt-laptop:~$ 
```


Also, to run moblock, do I need to keep the terminal open?

---

### Post by wilberfan on 2008-01-21
I don't believe you need to keep the terminal open to run moblock...   And that other error?  I would probably search this thread--that may have been addressed already?

---

### Post by jackietreehorn on 2008-01-21
I'll try and look through this thread for that error, but everything else seems to work fine. Thanks for the help. :)

---

### Post by jre on 2008-01-22
> **belgofac117 said:**
> The manual is saying: Seperate several entries with whitespace (" ").  I have tried many combo's but cannot unblock the Youtube range.  I already got 1 IP (Router) in the WHITE_IP_IN and OUT and want to add the range of 64.15.112.0 - 64.15.127.255.  

How would that entry look like together with my router IP? =  192.168.0.0/24
I can't tell you the correct subnet for the range you requested (where from did you get that anyway?), but for the range 64.15.112.0-64.15.112.255 it would be:
```
WHITE_IP_OUT="192.168.0.0/24 64.15.112.0/24"
```


> **jackietreehorn said:**
> when I typed the second code I got ```
pid file /var/run/moblock.pid exists. Not startingmatt@matt-laptop:~$ 
```


Also, to run moblock, do I need to keep the terminal open?

Was it really "moblock-control test"?! This can't be, did you edit the files or did you write "moblock-control start".
If it was really "test" then reinstall:
```
aptitude purge moblock
aptitude install moblock
``` and tell us the results again.
For the rest wilberfan already said everything.

---

### Post by jackietreehorn on 2008-01-22
> Was it really "moblock-control test"?! This can't be, did you edit the files or did you write "moblock-control start".
If it was really "test" then reinstall:
```
aptitude purge moblock
aptitude install moblock
``` and tell us the results again.
For the rest wilberfan already said everything.

I tried the test and got this 

```
Trying to ping 4.2.153.63 from /etc/moblock/ipfilter.dat ...
 * MoBlock did not block the IP.
 * 
 * If you just started/reloaded MoBlock wait until it loaded completely.
 * This will be when /var/log/moblock.log shows the following line:
 * NFQUEUE: binding to queue '0'
 * 
 * 4.2.153.63 did not answer.
 * 
 * Maybe 4.2.153.63 is down/doesn't answer to pings
 * or your firewall filtered the ping.
```

Not sure what that means exactly, but it doesn't seem good.

---

### Post by jre on 2008-01-23
At least you get something that makes sense now  ;-) But it's not good.
What does "moblock-control status" say?

---

### Post by jackietreehorn on 2008-01-23
> **jre said:**
> At least you get something that makes sense now  ;-) But it's not good.
What does "moblock-control status" say?

Okay, this is starting to get more frustrating than it should be. jre, I did what you suggested in a previous post, removing and reinstalling moblock. I only did that however, because this morning moblock was not functioning properly, while the day before it was working very well. I think the change is mostly due to the fact that I was adding different IP's to the whitelist, and trying to configure moblock to get the most out of it. 

After reinstalling it, I did "sudo moblock control status" and got his loverly bit of info:

```
 Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT 93939 packets, 55M bytes)
 pkts bytes target     prot opt in     out     source               destination         
   16  2985 moblock_in  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
    0     0 moblock_fw  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 

Chain OUTPUT (policy ACCEPT 60519 packets, 5506K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa reject-with icmp-port-unreachable 
    0     0 moblock_out  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 

Chain moblock_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
   16  2985 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     0    --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Please check if the above printed iptables rules are correct!

 * moblock is dead and /var/run/ pid file exists, pid is .
 * Try "moblock-control stop". Otherwise kill all moblock processes,
 * delete /var/run/moblock.pid and all iptables rules related to MoBlock.
```

---

### Post by jre on 2008-01-23
Indeed, that's not looking good.
I had this problems only when I started/stopped/reinstalled MoBlock very often while testing a new release. So I hope everything is working normally again when you reboot.

Otherwise please tell me
- your distribution (feisty/gutsy/hardy? i386/amd64/... ?)
- the version of the package "moblock" and "lsb-base"
- once again the moblock.log and moblock-control.log
Do you have "mobloquer" installed?

I noticed something strange in your output: the script thinks that the pid (/var/run/moblock.pid) exists but can't find its contents. Please check if this file exists and what's written in it.
I have to check if there's a bug in the lsb init-functions or what went wrong.

---

### Post by jackietreehorn on 2008-01-23
> **jre said:**
> Indeed, that's not looking good.
I had this problems only when I started/stopped/reinstalled MoBlock very often while testing a new release. So I hope everything is working normally again when you reboot.

Otherwise please tell me
- your distribution (feisty/gutsy/hardy? i386/amd64/... ?)
- the version of the package "moblock" and "lsb-base"
- once again the moblock.log and moblock-control.log
Do you have "mobloquer" installed?

I noticed something strange in your output: the script thinks that the pid (/var/run/moblock.pid) exists but can't find its contents. Please check if this file exists and what's written in it.
I have to check if there's a bug in the lsb init-functions or what went wrong.

I have gutsy, and I got moblock from the package manager, so it should be the most up to date, no?  I do not, as far as I know, have mobloquer installed. Also, I could not find the file /var/run/moblock.pid,

What is lsb-base and how do I know if it's there?

I think that maybe the best thing to do might be a reinstall, and start with a clean slate. I know I can make it work as it did all of yesterday and the day before. I started having problems when I tried to add to the list of blocklists on /etc/moblock/blocklists.list, and perhaps in my editing of that file and the config file I did something that affected moblock.

---

### Post by jre on 2008-01-24
lsb-base is also a package. It provides some functions moblock depends on.
You can get the versions with
```
dpkg -l moblock
dpkg -l lsb-base
```.

If you reinstall do the "purge" command as i wrote above. Otherwise you'll keep your config files and so probably the errors.

Because of a bug (unrelated to your current problems) I propose not to use multiple blocklists currently, see here: ([https://sourceforge.net/tracker/?atid=825649&group_id=162910](https://sourceforge.net/tracker/?atid=825649&group_id=162910)
and /usr/share/doc/moblock/BUGS.

greets
jre

---

### Post by jackietreehorn on 2008-01-24
> **jre said:**
> lsb-base is also a package. It provides some functions moblock depends on.
You can get the versions with
```
dpkg -l moblock
dpkg -l lsb-base
```.

If you reinstall do the "purge" command as i wrote above. Otherwise you'll keep your config files and so probably the errors.

Because of a bug (unrelated to your current problems) I propose not to use multiple blocklists currently, see here: ([https://sourceforge.net/tracker/?atid=825649&group_id=162910](https://sourceforge.net/tracker/?atid=825649&group_id=162910)
and /usr/share/doc/moblock/BUGS.

greets
jre
You're gonna love this. MoBlock is working again. How? I honestly have no clue. The test showed that moblock is working fine. I'll take a look at lsb-base, and not use multiple blocklists, although I would in the future like to use them and optimize the whole experience. Thanks for the help, I'll be sure to keep you up to date if everything works out, or gets screwed up again.

---

### Post by kosak on 2008-01-27
Check this out an GUI for moblock! at last~~~~!!!:guitar:

[http://mobloquer.foutrelis.com/](http://mobloquer.foutrelis.com/)

---

### Post by jre on 2008-01-28
> **kosak said:**
> Check this out an GUI for moblock! at last~~~~!!!:guitar:

[http://mobloquer.foutrelis.com/](http://mobloquer.foutrelis.com/)

Yes, and it's already packaged in the same repository like moblock ;-)

---

### Post by empthollow on 2008-01-29
i was running some tests on moblock today.  in order to get web access i have to whitelist my lan.  some sites load but to load them properly i needed to whitelist http & https.  the thing that confuses me is that when whitelisting http & https w/o my lan i could not load any web sites.  why is it necessary that i whitelist my lan if my lan is not in my blocklist?

---

### Post by jackietreehorn on 2008-01-29
ran a test and this came up 

```
Trying to ping 4.2.145.239 from /etc/moblock/ipfilter.dat ...
 * MoBlock did not block the IP.
 * 
 * If you just started/reloaded MoBlock wait until it loaded completely.
 * This will be when /var/log/moblock.log shows the following line:
 * NFQUEUE: binding to queue '0'
 * 
 * 4.2.145.239 did not answer.
 * 
 * Maybe 4.2.145.239 is down/doesn't answer to pings
 * or your firewall filtered the ping.
```

Not sure what to do in order to fix it...

---

### Post by empthollow on 2008-01-29
try this and then run the test again.
```
sudo moblock-control restart
```

---

### Post by RossumsChild on 2008-02-04
Hi.

I'm new.  Here goes.

I used peerguardian on Windows, and recently made the switch to 7.10 when I put together a new 64 bit machine, which I'd been planning for ages.   I was excited to see there was a PG alternative available on Linux, and I attempted to install it.

At first I tried to install from the repositories and couldn't find it.  Eventually I figured out that the repositories don't have a prebuilt version of moblock available for 64 bit processors (huh?).  I tried to install from the .deb package provided on the website and had no luck--it didn't appear to be running when I executed top, but it broke half the internet and I had to delete it manually, there was no way to uninstall it because it claimed it wasn't installed, but when I gutted the directories it was using my internet access fixed itself.  Whatever.  I've had dodgier things happen under Windows.

So I gave it up and figured I'd run without it (I'm not doing much file transfer right now).  However, today I decided to try again.  I tried to compile from source just now, based on the guide here:
[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

I added the source gutsy repository and followed the steps in the script under "compile from source"
when I got to 
/etc/moblock# sudo apt-get build-dep -y moblock

I get this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up moblock-nfq (0.8-39+gutsy) ...
Can't load configuration from /etc/moblock/moblock.conf, exiting.
dpkg: error processing moblock-nfq (--configure):
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies

What am I doing wrong?

---

### Post by jre on 2008-02-05
You're having the same problem as this guy: [http://ubuntuforums.org/showthread.php?t=674929&highlight=moblock.conf+error](http://ubuntuforums.org/showthread.php?t=674929&highlight=moblock.conf+error)
Follow my advice there to reinstall the manually deleted files.
Then do a "aptitude purge moblock-nfq" (or "aptitude purge moblock" if you installed version 0.9RC1)

Then try again.

BTW: Yesterday I added a amd64 version of moblock 0.8 to the moblock-deb repository. But I've no feedback of my tester yet. So without any guarantee: you might try your first step again (after cleanly uninstalling your old moblock mess ;-)

---

### Post by jamesford on 2008-02-05
wonderful news about the 64 bit repo! 
will u be keeping it as up to date as the 32 bit one or is it a bit more now and then ?

---

### Post by jre on 2008-02-06
Cross-compiling seems to work!
> **jamesford said:**
> wonderful news about the 64 bit repo! 
will u be keeping it as up to date as the 32 bit one or is it a bit more now and then ?
I don't promise anything but I want to handle both the same way. Of course, if there are amd64 specific problems it might take longer or in the worst case I can't do anything. For example I can't build packages for hardy, yet.
I'll add moblock 0.9rc1 and mobloquer this evening/tomorrow. **So the testing phase is officially open now! Please tell me if it's working with you (positives and negatives).**

---

### Post by jre on 2008-02-06
> **jre said:**
> **So the testing phase is officially open now! Please tell me if it's working with you (positives and negatives).**
Done, now I'm waiting for your (all amd64 guys) feedback.

---

### Post by reseto on 2008-02-07
I just installed the 0.9rc1 and mobloquer from repository on my 64bit gutsy, copied the whitelists, updated and started
it worked for 2 seconds.. but then it just stopped
when I hit restart, mobloquer says everything is ok, up and running but after 2~3 seconds stops again every time
it looks like its blocking the IPs in the background tho (I have no idea how that works) what did I do wrong? :)

---

### Post by jre on 2008-02-07
What stops? MoBlock the daemon or mobloquer the GUI? What exactly happens?

You can check the daemon status directly with "moblock-control status" in a terminal. With "tail -f /varlog/moblock.log" you can see live if anything is blocked (that's the same as in the mobloquer log window).

If you have problems with mobloquer you might start it from a terminal so that you eventually get error messages.

---

### Post by Shadowmeph on 2008-02-07
I installed Moblock but now it just starts then stops also ( I think it is running in the back ground) I cannot access the internet so I open up moblock GUI and is says it isn't running but if I push on the stop button I am able to access the internet again

---

### Post by jamesford on 2008-02-07
is that famous bug still there or can either the rc or the other one merge multiple blocklists properly now ? if not, is it being worked on ?

---

### Post by moopoo on 2008-02-08
hi,

**i'd like to whitelist every port but port xyz. in other words**, i'd just like to block (blacklist) one or two ports and leave the others unfiltered. is there an elegant way to do that?

**situation:** i just want moblock to filter traffic of a certain app (port)

**problems:**

- sometimes http is filtered, whitelisting like mentioned before[ doesn't always do the trick]("http://ubuntuforums.org/showthread.php?p=3975393&highlight=moopoo#post3975393").

- i couldn't get samba shares to work with moblock

- games/apps use ip's that are blocked by moblock. worst case: the game/app locks up. getting the info, which ports are used and whitelisting 1-10 of them every time i install something like that can be a pain in the a**.

- there are ip filters plugins for some apps, but they are often not so good as moblock (ressources, stability)

**less elegant solutions:**

- whitelist selective ports - can be very strenuous

- turn off moblock every time i need to access samba

- turn off moblock i'd like to run a certain game/app

- whitelist every single port there is, except port 12345 ```
WHITE_TCP_IN/OUT="0000:12344 12346:99999"
``` <- not a good idea, is it?

**desired solution:**

- possibility to activate "blacklist-mode". whitelisting of ports is not nessecairy anymore

- instead, only desired ports are beeing blacklisted (filtered by moblock)

```
BLACK_WHATEVER_IN/OUT="12345 66666 11111"
```

----

what do you think?

yours,
moopoo

---

### Post by jre on 2008-02-08
> **Shadowmeph said:**
> I installed Moblock but now it just starts then stops also ( I think it is running in the back ground) I cannot access the internet so I open up moblock GUI and is says it isn't running but if I push on the stop button I am able to access the internet again

Please check /var/log/moblock-control.log,  /var/log/moblock.log and "moblock-control status" when you have the problems.
Which system are you running (ubuntu version, amd64 or i386)?
Which versions have you installed? ("dpkg -l mobloquer", ...)

> **jamesford said:**
> is that famous bug still there or can either the rc or the other one merge multiple blocklists properly now ? if not, is it being worked on ?
The developer was looking into it in january, but I think he hasn't found a solution, yet.

> **moopoo said:**
> **i'd like to whitelist every port but port xyz. in other words**, i'd just like to block (blacklist) one or two ports and leave the others unfiltered. is there an elegant way to do that?
You can do this with custom iptables rules. There's an option for that. Have a look at /etc/moblock/moblock.conf. Basically you only have to send traffic from that port on INPUT and/or OUTPUT to the iptables target NFQUEUE. Have a look at "man iptables" and /usr/bin/moblock-control to get an idea how to do that.
I think I don't like the idea of making this an direct option (see the discussions why per default EVERY traffic is filtered).

---

### Post by moopoo on 2008-02-10
thank you. i'll give a try, when i find the time.

---

### Post by kraymore on 2008-02-10
does anyone know if its possible to use a different url for moblock-nfq to fetch its blacklists from ?  i just installed moblock-nfq and i get a error 171 no connection to bluetrack.co.uk 

i'm also having issues allowing me to *try* connecting to websites.  all websites are blocked including google and ubuntuforums.org by default.  i do want some level of "Moblock-functionality" to my web browsing, however i cannot access any websites whatsoever no matter how trivial they are.  

also oddly irc does work so there is some level of functionality when its enabled.  

under "WHITELIST IPS" in moblock.conf i added my router to try and achieve some level of functionality.  i am not sure if it helped or not.  please advise.  moblock.conf:  

WHITE_IP_IN="192.168.1.1 "

i realize that these questions are most likely redundant.  i tried reading this thread but it was so big that there was no way i could make it to page 110.  google didn't help either.  

would really love to get this working.  also, i dont want to have to edit anything if possible like moblock.conf entries for forwarded ports on my static ip address.  eg adding a line for every port/port range. 

thank you very much.

---

### Post by coasted on 2008-02-13
Is it possible for Moblock to act like PeerGuardian for windows did?

PG didn't attempt to block specific ports (that I know of I guess) and only blocked bad IPs from a list.

**nevermind** Got it I guess .  :P

---

### Post by Dawa on 2008-02-17
hello moblockers-

I was directed to this thread from this one:

[http://ubuntuforums.org/showthread.php?t=699280](http://ubuntuforums.org/showthread.php?t=699280)

anyway, long story short, the new moblock RC is causing all kinds of calamity.  I'll help any way I can, however I fear my skills are limited to posting logs and scratching my head.  (still learning!)  :)

---

### Post by dynafish on 2008-02-17
Same problem here I hope they get it resolved soon. I cannot even remove moblock via synaptic. I am thinking once I get it uninstalled I may quit using it all together. Moblock has been a huge pain to me. Seems like deluge with blocklist plugin is the way to go.

---

### Post by jre on 2008-02-17
About the bug in 0.9~rc2-1 (I'm the developer): Sorry for any inconvenience.
I'm just releasing a fixed version.
You can also fix it maually:
Change the first line of /usr/bin/moblock-control to:
```
#!/bin/bash
```

This error only occured in Gutsy, where /bin/sh is not directing to bash. So it did not happen here (Debian lenny)
dynafish, I can't promise that this won't happen again. But since much of the development is done there's a big chance that this will not happen again. I'm thinking about making a seperate infrastructure for beta testers, but I doubt that I find the time for this. So, sorry, if you decide against moblock. The problems were all produced by me, not by the upstream author.

---

### Post by Shadowmeph on 2008-02-17
excellent that works perfectly now i have to go back to the Pheonix labs site and try to find my post lol

---

### Post by jre on 2008-02-17
The fixed version is out (0.9~rc2-2)

BTW, the** range merge bug is also fixed** now! So this version uses multiple blocklists from bluetack.co.uk in peerguardian .p2p text format again. This means be careful with updating: accept all my changes to the conf files blocklists.list AND moblock.conf

---

### Post by Dawa on 2008-02-17
thanks for the quick update, jre!

something I noticed-

when running "moblock-control test" I'm getting an error.  here's the whole result:

Testing MoBlock: 

CAUTION: This is just a simple test to check if MoBlock blocks outgoing
connections. For this, one IP from your blocklist will be pinged. This test does
not check if you have sane iptables rules or if your complete blocklist is in
the correct format. Therefore success doesn't imply that everything is working
as you expect it.

You are marking blocked packets. This means you have to make sure that the
marked packets are also blocked later. If you are using the default
configuration and no other firewalls this will be the case.

Also have a look at "moblock-control status" and test manually with traceroute.

Trying to ping 12.21.127..6 from /etc/moblock/guarding.p2p ...
 * MoBlock did not block the IP.
 * 
 * If you just started/reloaded MoBlock wait until it loaded completely.
 * This will be when /var/log/moblock.log shows the following line:
 * NFQUEUE: binding to queue '0'
 * 
 * Some error occured with ping, no test result.

Could the problem be that extra point in the IP address?  there's two dots before the six:  "Trying to ping **12.21.127..6**"

---

### Post by jamesford on 2008-02-18
i decided to install 0.9-rc2-2 (amd64) and it was all a rather big mess and i was left without any connection, i guess eiter i did something wrong or its because its a beta. i got completely lost in the end. didnt really document what i did and id rather not try again until a final version is out and went back to my trusted old version. but nevermind that

 in any case i have a question regarding the conf file, it confused me especially these parts:
```
# Configure what happens to matched packets (IP in list)
# 0 - DROP them (like in MoBlock 0.8)
# 1 - MARK and RETURN them (default)
REJECT="1"

# Set the corresponding MARK
REJECT_MARK="10"

# Configure what happens to the marked packets
# This section works only for IPTABLES_ACTIVATION="1"
# Valid values are all iptables targets. There's no check for sane values.
# INPUT packets are always drop'ped
REJECT_OUT="REJECT"
REJECT_FW="DROP"
```

i dont really understand how this works, can u shed some light on it? does moblock not reject the packages anymore but instead mark them and pass them on to iptables which then will block the connection? if so will it silently reject the package or send a message ?

would be very happy if u could explain this and give some examples perhaps

---

### Post by Garret88 on 2008-02-18
> **Dawa said:**
> 
Trying to ping 12.21.127..6 from /etc/moblock/guarding.p2p ...
 * MoBlock did not block the IP.
 * 
 * If you just started/reloaded MoBlock wait until it loaded completely.
 * This will be when /var/log/moblock.log shows the following line:
 * NFQUEUE: binding to queue '0'
 * 
 * Some error occured with ping, no test result.

Could the problem be that extra point in the IP address?  there's two dots before the six:  "Trying to ping **12.21.127..6**"

**I have the same problem**. I didn't understand if moblock doens't work [SIZE=3]completely or it works but the error is only fot that ip. 

Please someone could explain it?[/SIZE]

---

### Post by jre on 2008-02-18
> **Garret88 said:**
> ```
Trying to ping 12.21.127..6 from /etc/moblock/guarding.p2p ...
* MoBlock did not block the IP.
*
* If you just started/reloaded MoBlock wait until it loaded completely.
* This will be when /var/log/moblock.log shows the following line:
* NFQUEUE: binding to queue '0'
*
* Some error occured with ping, no test result.

Could the problem be that extra point in the IP address? there's two dots before the six: "Trying to ping 12.21.127..6"
```

Yes, the ".." causes the problem. Generally nothing to worry, I think. AFAIK moblock loads only correct ranges.
Which blocklists are you using? I can't find that ".." here, also the test works fine here. I only have as 9th line:
```
Comment spammer:12.21.127.106-12.21.127.106
```
Could you please post the **10th line** of /etc/moblock/guarding.p2p. I need to know if it's a problem of the blocklist or if my test function causes the ".."
Which Ubuntu version are you using?


> **jamesford said:**
> i decided to install 0.9-rc2-2 (amd64) and it was all a rather big mess and i was left without any connection, i guess eiter i did something wrong or its because its a beta. i got completely lost in the end. didnt really document what i did and id rather not try again until a final version is out and went back to my trusted old version. but nevermind that
Hmm, I can only suggest to "purge" and install again.
If the problems persist I assume it's something with amd64.
There are no known problems (except those where something strange happens and nobody knows why :-/ ) with this version. I think MoBlock 0.9 will also be released quite soon officially. So if there stays something wrong we have to investigate it. For a start I'm interested in the output of "moblock-control status" and the logfiles.

> **jamesford said:**
> 
 in any case i have a question regarding the conf file, it confused me especially these parts:
```
# Configure what happens to matched packets (IP in list)
# 0 - DROP them (like in MoBlock 0.8)
# 1 - MARK and RETURN them (default)
REJECT="1"

# Set the corresponding MARK
REJECT_MARK="10"

# Configure what happens to the marked packets
# This section works only for IPTABLES_ACTIVATION="1"
# Valid values are all iptables targets. There's no check for sane values.
# INPUT packets are always drop'ped
REJECT_OUT="REJECT"
REJECT_FW="DROP"
```

i dont really understand how this works, can u shed some light on it? does moblock not reject the packages anymore but instead mark them and pass them on to iptables which then will block the connection? if so will it silently reject the package or send a message ?
In MoBlock 0.8 all packets which  were sent to Moblock (via the iptables NFQUEUE target) were checked and then either accepted (without returning to the iptables chains) or dropped (of course also without returning).

With MoBlock 0.9 and my default configuration (note that I broke the configuration to have the same behaviour as in 0.8, but will soon fix that) the packets will be marked (this marking will be logged in /var/log/moblock.log). As an exception, incoming packets which match the blocklist will be dropped directly like in MoBlock 0.8.
The marked packets then repeat (return to the head of) the iptables chains (INPUT/OUTPUT/FORWARD):
"Marked accept" packets will not be sent to the moblock chains again - so other iptables rules/the iptables policy decide what happens to them.
Outgoing "Marked blocked" packets will be REJECTed by an seperate iptables rule.
Forwarded "Marked blocked" packets will be DROPped by an seperate iptables rules.

So yes, everything correct what you said. And it's only logged that the packets were marked, but not when they are really dropped (except matching incoming packets, which are always dropped directly and so are logged, see above).

It's quite easy to see that the REJECTED packets are really blocked, because the sending program gets an "Destination Port Unreachable" and so stops directly the connection attempts.

---

### Post by jamesford on 2008-02-18
thanks for the explanation, i might give it another try soon.

does the moblock >mark >iptables >reject work whatever iptables config u got? or do u have to do something with iptables ?

---

### Post by Dawa on 2008-02-18
I am using Ubuntu 7.10 gutsy gibbon; and I'm using the default "green checked" blocklists that show up in mobloquer after install.  Here's the full list:

microsoft, ads-trackers-and-bad-pr0n, bogon, dshield, hijacked, iana-multicast, iana-private, iana-reserved, level 1, level 2, rangetest, spider, spyware, templist, and trojan.

here's the 10th line of my guarding.p2p:

```
Comment spammer:12.21.127.106-12.21.127.106
```

just so you know, jre: in mobloquer's log display it is showing blocked connections (incoming and outgoing), so moblock is apparently working just fine.  it seems like the test function is all that's having a hiccup.

hope this helps!  :)

---

### Post by Garret88 on 2008-02-18
> **Dawa said:**
> 
```
Comment spammer:12.21.127.106-12.21.127.106
```

I have the same line!!! :(

Then if i try to "ping google.com" through the terminal the test fails, but if i stop moblock and then re-try the test is ok....

so moblock blocks also google?

---

### Post by jamesford on 2008-02-18
i just tried again, several times actually. it just isnt working. firstly moblock wont run, i get no error msg when starting it but its not listed in any process list
secondly wile moblock is installed i have no network connection, i have to uninstall it then network works again

the only error message ive been able to see is when simply typing 'moblock' in a terminal i get:
error while loading shared libraries: libnetfilter_queue.so.1: cannot open shared object file: No such file or directory

tried uninstalling and reinstalling that file as well but to no avail.

 i get no error messages during the install procedure...

this is for moblock_0.9~rc2-2+gutsy+amd64_amd64.deb

---

### Post by dynafish on 2008-02-19
> **jre said:**
> About the bug in 0.9~rc2-1 (I'm the developer): Sorry for any inconvenience.
I'm just releasing a fixed version.
You can also fix it maually:
Change the first line of /usr/bin/moblock-control to:
```
#!/bin/bash
```

This error only occured in Gutsy, where /bin/sh is not directing to bash. So it did not happen here (Debian lenny)
dynafish, I can't promise that this won't happen again. 

Don't sweat it JRE and thanks for the quick reply and for developing moblock. I was just frustrated that day and maybe a bit over caffeinated. Will try the fix later today and likely keep using it if it works.

---

### Post by dynafish on 2008-02-19
I too have had the same problems after reinstalling. Test fails and moblock blocks all http traffic. I just reinstalled mobloquer and checked the boxes off for http,https,pop,smtp,and imap so all functions should have returned as far as networking. I still wonder if moblock is actually working.

moblock status:


Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1386  486K moblock_in  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
   11   880 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     0    --  eth1   *       98.213.124.140       255.255.255.255     
    8   320 logaborted  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED tcp flags:0x04/0x04 
 6098 7452K ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
16102 5632K nicfilt    0    --  *      *       0.0.0.0/0            0.0.0.0/0           
16102 5632K srcfilt    0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
    0     0 moblock_fw  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
    0     0 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
    0     0 srcfilt    0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP 1 packets, 146 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa reject-with icmp-port-unreachable 
   18   974 moblock_out  0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
   11   880 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0           
 4986  325K ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
  298 16595 s1         0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain f0to1 (3 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:6970:7170 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpts:6881:6889 state NEW 
16093 5630K logdrop    0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain f1to0 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:6346 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:587 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:6969 state NEW 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:109 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:1723 state NEW 
    0     0 ACCEPT     47   --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:110 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:995 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:21 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:119 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:143 state NEW 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:143 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpts:6660:6669 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 state NEW 
   26  1650 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
  206 10712 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:80 state NEW 
    4   208 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8080 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8008 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8000 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8888 state NEW 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:587 
    1    76 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:123 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:123 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:1755 state NEW 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:1755 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:554 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:7070 state NEW 
   11   572 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:443 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpts:6881:6889 state NEW 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spts:1024:5999 dpt:37 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:37 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:993 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:25 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:111 state NEW 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:111 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:1024:65535 state NEW 
    9  1737 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:2049 state NEW 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:2049 
   41  1640 logdrop    0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain logaborted (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    8   320 logaborted2  0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED ' 

Chain logaborted2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    8   320 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `ABORTED ' 
    8   320 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 

Chain logdrop (4 references)
 pkts bytes target     prot opt in     out     source               destination         
 9146 3205K logdrop2   0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
  263 92782 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED ' 
 6997 2429K DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain logdrop2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 9146 3205K LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `DROPPED ' 
 9146 3205K DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain logreject (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 logreject2  0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED ' 
    0     0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset 
    0     0 REJECT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain logreject2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `REJECTED ' 
    0     0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset 
    0     0 REJECT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain moblock_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:143 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:21 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:110 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
 1386  486K NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain moblock_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     0    --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:143 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:21 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:110 
   15   780 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    3   194 NFQUEUE    0    --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain nicfilt (1 references)
 pkts bytes target     prot opt in     out     source               destination         
16102 5632K RETURN     0    --  eth1   *       0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     0    --  eth1   *       0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 logdrop    0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain s0 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    9  1092 f0to1      0    --  *      *       0.0.0.0/0            98.213.124.140      
16084 5629K f0to1      0    --  *      *       0.0.0.0/0            255.255.255.255     
    0     0 f0to1      0    --  *      *       0.0.0.0/0            127.0.0.1           
    9  1737 logdrop    0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain s1 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  298 16595 f1to0      0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain srcfilt (2 references)
 pkts bytes target     prot opt in     out     source               destination         
16102 5632K s0         0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Please check if the above printed iptables rules are correct!

 * moblock is running, pid is 9162.

---

### Post by Dawa on 2008-02-19
just wanted to post that besides the "test", my moblock is working fine.  here's what I did, maybe it has something to do with it:

edited moblock-control as per jre's instructions

completely removed moblock and mobloquer

updated my package list and installed moblock RC2-2

then I went into the config file, and changed the WHITE_TCP_OUT values from the text "http https"  to the numbers "80 443"   (i also added some other ports for IM networks so pidgin could connect)

after that, moblock seems to work as it always has, besides the "moblock-control test" function being broken.

---

### Post by jre on 2008-02-19
> **jamesford said:**
> thanks for the explanation, i might give it another try soon.

does the moblock >mark >iptables >reject work whatever iptables config u got? or do u have to do something with iptables ?
With Marking on MoBlock is working fine with other iptables rules/firewalls if the **first lines** in the chains INPUT/FORWARD/OUTPUT are like these.

```
Chain INPUT (policy ACCEPT 64214 packets, 85M bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1734  118K moblock_in  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
[Every following line is ok]

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
    0     0 moblock_fw  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
[Every following line is ok]

Chain OUTPUT (policy ACCEPT 42390 packets, 3454K bytes)
 pkts bytes target     prot opt in     out     source               destination         
   34  2040 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa reject-with icmp-port-unreachable 
 1221 86849 moblock_out  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
[Every following line is ok]

```
This will be the case when moblock is started **after** other iptables changes/firewalls. Of course the MOBLOCK... chains have to exist, too.

Now, what is needed is the running "moblock" process and a valid blocklist.

@jamesford:
Sorry, I've no answer (yet) for the
error while loading shared libraries: libnetfilter_queue.so.1: cannot open shared object file: No such file or directory
problem on amd64. It might be a problem with my cross-compiling - you might test building your own packages,


@garret: yes, per default moblock blocks also google.

---

### Post by jamesford on 2008-02-20
jre
i compiled my own packages and now it works :) no more errors when typing 'moblock'
ive attached it in case u wanna compare it with ur own packages.

i dont know why theres a i386 in the name, it was autogenerated but i left it there. its a amd64 package

while ive got u here, what are the iana ranges ? are they needed ?

edit: i noteced the ranges loaded are identical to with 8.29...i thought there would be a few more with the bug supposedly fixed?

---

### Post by p0k3r808 on 2008-02-21
> **bionnaki said:**
> how do you stop/restart moblock? how do you make exceptions for port 80?

To start and stop and restart moblock enter these commands


sudo moblock-control start
sudo moblock-control stop 
sudo moblock-control restart


respectively

---

### Post by jre on 2008-02-21
> **jamesford said:**
> while ive got u here, what are the iana ranges ? are they needed ?
Have a look at /usr/share/doc/moblock/README.blocklists.gz.
Basically they contain ranges which should not be assigned to publicly available computers - so you should not have contact with them. Most problems occurs with LAN ranges (LAN = not publicly available, so your router/LAN is in the IANA lists)

> **jamesford said:**
> edit: i noteced the ranges loaded are identical to with 8.29...i thought there would be a few more with the bug supposedly fixed?
The number of ranges should be the same (as long as the lists are exactly the same). But the number of IPs contained in these ranges should be bigger.

I'll have to rework the amd64 setup - next week ... For then use your own packages, sorry!

---

### Post by jamesford on 2008-02-21
ah ic, thanks

btw, any chance u could add an rss feed for the moblock-deb news?

---

### Post by jackietreehorn on 2008-02-21
Currently having this problem and not sure how to fix it:

```
CAUTION: This is just a simple test to check if MoBlock blocks outgoing
connections. For this, one IP from your blocklist will be pinged. This test doesnot check if you have sane iptables rules or if your complete blocklist is in
the correct format. Therefore success doesn't imply that everything is working
as you expect it.

You are marking blocked packets. This means you have to make sure that the
marked packets are also blocked later. If you are using the default
configuration and no other firewalls this will be the case.

Also have a look at "moblock-control status" and test manually with traceroute.

Trying to ping 12.21.127..6 from /etc/moblock/guarding.p2p ...
* MoBlock did not block the IP.
*
* If you just started/reloaded MoBlock wait until it loaded completely.
* This will be when /var/log/moblock.log shows the following line:
* NFQUEUE: binding to queue '0'
*
* Some error occured with ping, no test result.
```

---

### Post by jre on 2008-02-25
jamesford, there is one (i think) on the *project* page. Note that the NEWS on the project site and on the web sites are the same.

jackiethreehorn, this was discussed just some posts ago. Don't woryr, MoBlock is working. It's just a bug (!?) in the test function.

---

### Post by jre on 2008-02-28
I removed the amd64 packages from the repository moblock-deb.sourceforge.net because they seem not to work. Now I'm trying to setup qemubuilder. No ETA, sorry. Just compile your own packages for the time being.

---

### Post by rye_ on 2008-03-02
EDIT:WOOHOO! I got a blocked incoming, I guess all's well

Thanks for  mobloquer, this is really wonderful.

I notice I'm not getting any incoming blocks, is this normal?

Thanks,

Ryan

---

### Post by luvinit on 2008-03-02
Hi,
Can someone help me interpret these results? I run a test and get the following output

Trying to ping 4.2.145.239 from /etc/moblock/ipfilter.dat ...
 * MoBlock did not block the IP.
 * 
 * If you just started/reloaded MoBlock wait until it loaded completely.
 * This will be when /var/log/moblock.log shows the following line:
 * NFQUEUE: binding to queue '0'
 * 
 * 4.2.145.239 did not answer.
 * 
 * Maybe 4.2.145.239 is down/doesn't answer to pings
 * or your firewall filtered the ping.

Unfortunately the test is very vague and doesn't tell you if it is conclusive.
I am using gutsy. Until today I was using an old version from gutsy unstable repository which seemed to work fine. I am running Ipkungfu firewall if that makes any difference, but the results I get are identical with or without it. Also, it doesn't load at boot, even though the config says it should. Appreciate any help.

---

### Post by luvinit on 2008-03-02
I decided to go with Ipblock, which seems to just work. It gets much less coverage than moblock for some reason. This might be useful to some of you having problems.

---

### Post by jre on 2008-03-02
> **luvinit said:**
> Hi,
Can someone help me interpret these results? I run a test and get the following output

Trying to ping 4.2.145.239 from /etc/moblock/ipfilter.dat ...
 * MoBlock did not block the IP.
 * 
 * If you just started/reloaded MoBlock wait until it loaded completely.
 * This will be when /var/log/moblock.log shows the following line:
 * NFQUEUE: binding to queue '0'
 * 
 * 4.2.145.239 did not answer.
 * 
 * Maybe 4.2.145.239 is down/doesn't answer to pings
 * or your firewall filtered the ping.

Unfortunately the test is very vague and doesn't tell you if it is conclusive.
I am using gutsy. Until today I was using an old version from gutsy unstable repository which seemed to work fine. I am running Ipkungfu firewall if that makes any difference, but the results I get are identical with or without it. Also, it doesn't load at boot, even though the config says it should. Appreciate any help.

I assume you run moblock 0.9~rc2-2 (check "dpkg --list moblock")

The test is based on a "ping" and then checks if this IP appears in the logfile.
Nothing more!
 Your result indicates that this IP did not appear in the logfile but also didn't answer to the ping.
Check your iptables rules (e.g. with "moblock-control status"). Your INPUT/OUTPUT chains should **begin** with something like this:
```
Chain INPUT (policy ACCEPT 14503 packets, 14M bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1589  107K moblock_in  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 

Chain OUTPUT (policy ACCEPT 13039 packets, 1137K bytes)
 pkts bytes target     prot opt in     out     source               destination         
   61  3924 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa reject-with icmp-port-unreachable 
 1110 79279 moblock_out  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
```

A "ping 4.2.145.239" must not succeed. If it is MoBlock (and not some other firewall rule) that blocks the IP you will get a ```
PING 4.2.145.239 (4.2.145.239) 56(84) bytes of data.
From 192.168.178.124 icmp_seq=1 Destination Port Unreachable
```

A "traceroute 4.2.145.239" must show that the packet is blocked at the **first** hop:
```
traceroute to 4.2.145.239 (4.2.145.239), 30 hops max, 40 byte packets
 1  dream.local (192.168.178.124)  0.255 ms  0.066 ms  0.056 ms
```(no more output following!)

---

### Post by luvinit on 2008-03-02
Thanks a lot for your response. It makes much more sense now. Yes, that was the version, but for some reason it just doesn't block the IP. I will have another play some other time, but in the short term I will use Ipblock as it is giving me exactly the result you describe when pinging. :)

---

### Post by DamonChyld on 2008-03-05
Hi all,

Quick question about blocking http/https. I understand that some clients (such as bittorrent) use http/https for exchanges and that if http/https is unblocked in these cases that it nullifies the moblock protection (as I will then be seeding blindly). 

I use the Deluge client and am wondering if I am safe to unblock outgoing http/https. I know that I can just add an ip through the logs (I have the mobloquer gui) when a site I want is blocked but this becomes a pain as most big sites have multiple ip's. I think that I have allowed about 15 from amazon so far and keep getting new ones!

Thanks in advance!

---

### Post by jre on 2008-03-05
"Nullifies" is a bit too much, but yes, if another peer listens e.g. on port 80 (http) than whitelisting port 80 out will allow connections to this peer even if he's in the blocklist.

But you can whitelist complete ranges in /etc/default/moblock
This is an example to whitelist the range 192.168.178.1-192.168.178.255 next to other IPS:
WHITE_IP_OUT="some IPs that you've already whitelisted 192.168.178.0/24"

---

### Post by DamonChyld on 2008-03-05
Thanks for getting back to me jre. 

Is there a way to allow all IP's from a specific site? Amazon's ip's seem to be pretty broad, I am not sure if they could be included in a range and then defining that range for each site would be a pain.

---

### Post by jre on 2008-03-06
You can use "IP_REMOVE" (for info have a look at /etc/moblock/moblock.conf. Then insert it to /etc/default/moblock) which allows to "grep" the blocklist for search terms and remove the corresponding lines.

E.g. IP_REMOVE="amazon"
Have a look at /var/log/moblock-control.log (after every reload/update) to see which lines were removed from the blocklist.

IP_REMOVE is case-insensitive.

---

### Post by empthollow on 2008-03-07
i use azureus and have an option
```
Ignore peers with these data ports
```
i set it to ignore 80 & 443, does ingoring those peers then protect me from unwanted listeners?

---

### Post by snowx1000 on 2008-03-07
I am running the latest Moblock and while the log says its blocking IPs, nmap is still able to reach these hosts. Any suggestions?

---

### Post by dbqp on 2008-03-08
Just curious, is this still an actively supported program? Modblock that is...and are the instructions updated or do I need to go through all 113 pages?

Thanks!

---

### Post by jimtb on 2008-03-08
MoBlock is still under active development.
As far as I know that the instructions on the first post are updated regularly by pelle.k.

:-)

---

### Post by pelle.k on 2008-03-10
They are indeed, even though the actual *howto* has been moved to the community wiki, so that everyone can contribute :)
I may not be very active in this thread any more, but i try to edit the first post when it is needed.

---

### Post by jre on 2008-03-10
> **empthollow said:**
> i use azureus and have an option
```
Ignore peers with these data ports
```
i set it to ignore 80 & 443, does ingoring those peers then protect me from unwanted listeners?
I think so, yes.

> **dbqp said:**
> Just curious, is this still an actively supported program? Modblock that is...and are the instructions updated or do I need to go through all 113 pages?
Do NOT read all these pages. The last 10 might contain usefull information. Older things might be outdated and completely wrong with the current versions.

But still, the wiki (link on the first page) should also be updated more frequently, everybody feel free!

> **snowx1000 said:**
> I am running the latest Moblock and while the log says its blocking IPs, nmap is still able to reach these hosts. Any suggestions?

What's your "latest" version? There's a 0.8 series and a 0.9 series! Please, always tell the version you get with "dpkg --list PACKAGENAME"
What are your iptables rules (e.g. with "moblock-control status").

Anyway what I get is:
```
$moblock-control test
[...]
Trying to ping 12.25.215.191 from /etc/moblock/guarding.p2p ...
MoBlock marked the IP to be blocked and the IP did not answer. Test succeeded.
```
good

```
$ traceroute  12.25.215.191
traceroute to 12.25.215.191 (12.25.215.191), 30 hops max, 40 byte packets
 1  dream.local (192.168.178.124)  0.740 ms  3.090 ms  3.156 ms

```
good, packet stopped at first hop

```
$ ping -c1  12.25.215.191
PING 12.25.215.191 (12.25.215.191) 56(84) bytes of data.
From 192.168.178.124 icmp_seq=1 Destination Port Unreachable

--- 12.25.215.191 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

```
good, packet was immediately rejected (feature of moblock.0.9)

```
$nmap 12.25.215.191
Starting Nmap 4.53 ( http://insecure.org ) at 2008-03-10 18:52 CET
All 1714 scanned ports on 12.25.215.191 are closed

Nmap done: 1 IP address (1 host up) scanned in 2.898 seconds


```
Is this what you get, too? Indeed this seems to indicate that nmap can connect to this IP. But:
- I'm not savvy enough to really interpret this result, but the "1 host up" even comes when i nmap 1.0.0.0
- Perhaps nmap is such a lowlevel tool that it circumvents iptables - while MoBlock depends on iptables rules. I object to this being a security flaw since AFAIK all Linux firewalls depend on iptables and AFAIK there is no way to get IN a system  circumventing iptables.

Greets
jre

---

### Post by peepingtom on 2008-03-14
I think it would be a bad idea to whitelist all HTTP(S) traffic, but I would like my web browsers to be able to access the web without being filtered by Moblock. Does anyone have a recommendation of how to do this using FireHOL?
I'm investigating the PID and CMD commands but don't really know the proper syntax.
Thanks for any help you can give!

---

### Post by jre on 2008-03-20
oh no, broken packages again if you kept your config files on update to moblock 0.9~rc2-4.
If you have problems sdd this to /etc/init.d/moblock after the line
```
CONTROL_CONF="/etc/moblock/moblock.conf"
```

```
# Set sane configuration defaults. They will be overwritten by
# the values in CONTROL_CONF and CONTROL_DEFAULT
PATH="/sbin:/bin:/usr/sbin:/usr/bin"
DESC="MoBlock"
NAME="moblock"
LSB="/lib/lsb/init-functions"
MOBLOCK_INIT="1"
VERBOSITY="1"
CONTROL_DEFAULT="/etc/default/$NAME"
CONTROL_SCRIPT="/usr/bin/moblock-control"
```

Or reinstall and take all new (package maintainer's) config files.
```
sudo aptitude reinstall moblock
```

Hope (and think so) that helps.
Please give me feedback. I'll release a new version then tomorrow.

Greets
jre

EDIT: Done. Now the "Error 6, can't uninstall MoBlock" problems are also solved. This occured when people had deleted their moblock.conf. Now all necessary variables always have a sane fallback.

---

### Post by jre on 2008-03-21
> **peepingtom said:**
> I think it would be a bad idea to whitelist all HTTP(S) traffic, but I would like my web browsers to be able to access the web without being filtered by Moblock. Does anyone have a recommendation of how to do this using FireHOL?
I'm investigating the PID and CMD commands but don't really know the proper syntax.
Thanks for any help you can give!

@peepingtom: I don't think that's possible. AFAIK there's no possibility to filter depending on the software with iptables - you can only choose by port. Have a look at "man iptables" or the netfilter homepage if you want to learn more.
But what you can do is to whitelist http(s) (port 80 and 443) and at the same time tell your other applications not to use/listen on these ports. Of course this is only possible if your other applications have this feature.

---

### Post by peepingtom on 2008-03-23
Unfortunately the filesharing programs in question don't allow blacklisting of certain ports (if anyone knows a script  for this i'd appreciate the effort!). I would run this a a different user but there programs aren't daemons and I don't know how to run a GUI program as a different user and be able to use the interface in my X session.
Firehol seems to have functionality to make rules for specific programs,  I'm asking for help on the FireHol support forum and progress can be followed here [http://sourceforge.net/forum/forum.php?thread_id=1970089&forum_id=196547]("http://sourceforge.net/forum/forum.php?thread_id=1970089&forum_id=196547")

With the following lines in my firehol.conf (in the appropriate order):  
 
```
#Freeweb 
server_freeweb_ports="tcp/80 
client_freeweb_ports="any" 
 
interface any world 
client "freeweb" accept command firefox
``` 
 
I get: 
 
```
ERROR : # 1. 
WHAT : A runtime command failed to execute (returned error 1). 
SOURCE : line INIT of /etc/firehol/firehol.conf 
COMMAND : /sbin/iptables -t filter -A out_world_freeweb_c3 -p tcp --dport 80 -m owner --cmd-owner firefox -m state --state NEW\,ESTABLISHED -j ACCEPT  
OUTPUT : iptables: Invalid argument 
```
^^An example, i've tried with other cmd names such as nautilus.

I fear that the "--cmd-owner" command is broken/deprecated somewhere, whether at a kernel level, in iptables/netfilter or even FireHol.

according to man iptables:
"--cmd-owner name
              Matches if the packet was created by a process  with  the  given
              command name.  (Please note: This option requires kernel support
              that might not be available in official Linux kernel sources  or
              Debian&#8217;s packaged Linux kernel sources.  And if support for this
              option is available for the specific Linux  kernel  source  ver&#8208;
              sion,  that  support  might  not be enabled in the current Linux
              kernel binary.)
NOTE: pid, sid and command matching are broken on SMP"

I use a single, old Pentium 4, I hope this SMP warning doesn't apply to me! The warning about Debian is ominous, and I don't know how practical it is to use ubuntu with a custom kernel. 

[QUOTE=skipo's post below this one] have you tried this?[/QUOTE] Thank, i edited to address this.
Sorry for hijacking this thread, this seems pertinent to Moblock users| I'll post again when i've investigated this further, I struggle with grep and sed  but I read every new post in this thread.

---

### Post by skipo on 2008-03-23
> **peepingtom said:**
> 

With the following lines in my firehol.conf (in the appropriate order):  
 
```
#Freeweb 
server_freeweb_ports="tcp/80 
client_freeweb_ports="any" 
 
interface any world 
client "freeweb" accept command firefox
``` 
 

Firefox-bin is the running process of firefox, so have you tried this?

```
#Freeweb 
server_freeweb_ports="tcp/80 
client_freeweb_ports="any" 
 
interface any world 
client "freeweb" accept command firefox-bin
```

---

### Post by peepingtom on 2008-03-24
please delete this ;)

---

### Post by jamesford on 2008-03-24
im wondering if u can implenent some extra feature to make sure level1 is downloaded, it seems to fail 2 out of 3 times these days. ive noticed that if i delete the level1.gz from /var/spool/moblock and from /var/spool/moblock/used and rerun the update procedure it usually works, but usually not if i dont delete those files

maybe if level1 fails the updater could delete those files (maybe keep an emergency backup in a third dir just in case) and retry downloading those files that failed or something. and if that still doesent work then use the emergency backup?

also, on the same topic, if my level1 fails, what do i do if i only want to download level1.gz? i mean i could create a small bash script that wgets the file and puts it in /var/spool/moblock/ but what would the command be then to make moblock extract/merge the new level1 with all the existing blocklists already downloaded and restart moblock with the ip ranges in my newly downloaded level1 included?
maybe a command like "sudo moblock-control update level1" could work if this command did exactly the same as "sudo moblock-control update" except getting just level1 and ignoring the rest ?

---

### Post by jre on 2008-03-24
@peepingtom: I didn't know this iptables option "cmd-owner" that firehol. Here, with Debian lenny (testing) the man page reads:
```
       --cmd-owner name
              Matches  if  the  packet was created by a process with the given
              command name.  (this option is present only if iptables was com&#8208;
              piled under a kernel supporting this feature)

       NOTE: pid, sid and command matching are broken on SMP
```
I can't tell you yet if it does work here.

> **jamesford said:**
> im wondering if u can implenent some extra feature to make sure level1 is downloaded, it seems to fail 2 out of 3 times these days. ive noticed that if i delete the level1.gz from /var/spool/moblock and from /var/spool/moblock/used and rerun the update procedure it usually works, but usually not if i dont delete those files
If it really works if the level1 is not present then I assume it has something to do with the timestamping. So try to add a "notimestamp" in blocklists.list before the "level1" line.


> **jamesford said:**
> maybe if level1 fails the updater could delete those files (maybe keep an emergency backup in a third dir just in case) and retry downloading those files that failed or something. and if that still doesent work then use the emergency backup?
The "emergency backup" is already in the "used" directory so I just implemented what you suggested (version moblock 0.9~rc2-9)

> **jamesford said:**
> also, on the same topic, if my level1 fails, what do i do if i only want to download level1.gz? i mean i could create a small bash script that wgets the file and puts it in /var/spool/moblock/ but what would the command be then to make moblock extract/merge the new level1 with all the existing blocklists already downloaded and restart moblock with the ip ranges in my newly downloaded level1 included?
maybe a command like "sudo moblock-control update level1" could work if this command did exactly the same as "sudo moblock-control update" except getting just level1 and ignoring the rest ?
Save it to /var/spool/moblock/used, then issue "moblock-control reload". "rebuild" rebuilds  the blocklist and reloads moblock if it is running.
Note that it is essential that the blocklist is contained in /etc/moblock/blocklists.list (as it is the case with the "level1.gz"). The lists in that file get extracted and cat'ted together to the master blocklist /etc/moblock/guarding.p2p. Just copying any blocklist to "used" will not work.

---

### Post by feistybird on 2008-03-31
How to disable logging of moblock?

My log file is getting to big!

Thanks!

---

### Post by chunchengch on 2008-04-02
I create a deb file of MoBlock GUI, you can find it in my thread [http://ubuntuforums.org/showthread.php?t=742538](http://ubuntuforums.org/showthread.php?t=742538)

---

### Post by jre on 2008-04-02
> **feistybird said:**
> How to disable logging of moblock?

My log file is getting to big!
Set in /etc/default/moblock:
DAEMON_LOG=""
I have never really used that but it should work.
"moblock-control test" will not work anymore with this setting.

But is the logfile really a problem for you? Currently the logfiles are rotated daily. This means that every day a new logfile is started, and the old one gets archived for a while. So you have:
moblock.log
moblock.log.1 (the log from yesterday)
moblock.log.2.gz (the log from 2 days ago, already gzip'ed)
...
moblockl.log.11.gz
After 12 days the logfiles are deleted.

---

### Post by gims77 on 2008-04-03
I'm a bit of an Ubuntu newbie so please bear with me.

I've installed the 64 bt version of moblock 8.39 and it's blocking things fine. The only problem is it's blocking things that aren't actually in my blocklist(s).

This is my moblock.conf file:
```
# Specify the format of the blocklists that you use. You can´t mix different
# formats.
# d - eMule ipfilter.dat format
# n - peerguardian .p2b v2 binary format
# p - peerguardian .p2p text format
BLOCKLIST_FORMAT="d"

# Specify a NFQUEUE queue number (default 0)
# Works only with -nfq version
NFQUEUE_NUMBER="0"

# Turn on/off automatic start
# 0 - Don´t start MoBlock at system boot
# 1 - Start MoBlock at system boot
MOBLOCK_INIT="0"

# Turn on/off automatic blocklist update
# 0 - Don´t update the blocklists automatically
# 1 - Update the blocklists automatically
MOBLOCK_CRON="0"

# Set the verbosity of moblock-control
# 0 - No normal output to STDOUT, only to logfile
# 1 - Output to STDOUT and to logfile
VERBOSITY="1"

################## Settings for the iptables firewall rules ###################

# MoBlock requires the iptables rule NFQUEUE (nfq version)
# or the deprecated QUEUE (ipq version).

# Do a "moblock-control stop" before you change these iptables settings.

# Define how traffic is sent to MoBlock
# 0 - Don't set any iptables rules.
#     You or another script/firewall has to do this!
# 1 - NFQUEUE is in the chains moblock_in, moblock_out and moblock_fw.
# 2 - Set custom iptables rules (defined in
#     /etc/moblock/iptables-custom-insert.sh and iptables-custom-remove.sh)
IPTABLES_SETTINGS="1"

# Define when traffic is sent to the chain that contains NFQUEUE
# This section works only for IPTABLES_SETTINGS="1"
# 0 - Do nothing. You or another script/firewall has to do this!
# 1 - Insert the rules at the head of the chains.
# 2 - Append the rules to the end of the chains.
IPTABLES_ACTIVATION="2"

############################### Whitelist ports ###############################

# Whitelist ports by port number or with the associated service name
# (using iptables with the target RETURN)
# Seperate several entries with whitespace (" ")
# Port ranges are specified in the format "port:port"
# Up to 15 ports can be specified. A port range (port:port) counts as two
# ports.

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT=""
WHITE_UDP_OUT=""
# This is an example to whitelist outgoing web traffic (port 80 is the service
# http, 443 is https) and the port range 1000-1024:
# WHITE_TCP_OUT="80 443 1000:1024"
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""

################################ Whitelist IPs ################################

# Whitelist either a network name, a hostname (please note that specifying any
# name to be resolved with a remote query such as DNS is a really bad idea), a
# network IP address (with /mask), or a plain IP address.
# (using iptables with the target RETURN)
# The mask can be either a network mask or a plain number, specifying the number
# of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent
# to 255.255.255.0.
# Seperate several entries with whitespace (" ")

# This replaces the old (up to 0.8-32) IP_TCP_ and IP_UDP_ entries.

# This section works only for IPTABLES_SETTINGS="1"
# Do a "moblock-control restart" when you have changed these settings.

WHITE_IP_IN="192.168.1.0/24"
WHITE_IP_OUT="192.168.1.0/242"
# This is an example to whitelist the range 192.168.178.1-192.168.178.255:
# WHITE_IP_OUT="192.168.178.0/24"
WHITE_IP_FORWARD=""

###################### Remove lines from the blocklist ########################

# Remove lines from the blocklist (using "grep -v -i")
# Warning for beginners: If you want to whitelist a special IP then check the
# above section. In most cases you won't succeed if you insert an IP here.
# Seperate values with a semicolon ";".

# Do a "moblock-control reload" when you have changed these settings.

IP_REMOVE=""
# This is an example to remove all lines from the blocklist which contain one
# of the words "google", "yahoo", "altavista", "debian" or "sourceforge":
# IP_REMOVE="google;yahoo;altavista;debian;sourceforge"

########################### Full LSB compatibility ############################

# The control script uses /lib/lsb/init-functions. In Debian this file also
# provides functions which are not defined by the LSB standard. Change this
# entry if the script complains of not knowing a function.
# 0 - Debian compatible system (default)
# 1 - LSB 3.1 but not Debian compatible system
LSB_MODE=0
```

and this is my blocklists.list file:
```
# blocklists.list - lists the blocklists used by moblock-control

# Place one URL per line for every blocklist. Any line which starts with a #
# (hash) is a comment and is ignored. You have to do a "moblock-control update"
# after editing this file.

# All lists have to be in the same blocklist-format. This format has to be
# specified in moblock.conf.
# The name of the blocklist has to be the same as the basename of the URL, i.e.
# php redirects are not possible.

# If the remote server doesn´t support timestamping start the line with
# "notimestamp". Don´t abuse this. This is only necessary if the remote
# server doesn´t provide timestamping (Error 400).

# For local blocklists start the line with "locallist".
locallist /etc/moblock/list.txt
```

where /etc/moblock/list.txt is
```
ip:9.9.9.9-9.9.9.9
```

As you can see, I'm only bocking a single dummy ip address (for testing purposes). Unfortunately, when I try to access google I get the following errors in my log file:

```
Ranges loaded: 1
Merged ranges: 0
Skipped useless ranges: 0
NFQUEUE: binding to queue '0'
Blocked OUT: @,hits: 1,DST: 66.102.9.147
Blocked OUT: @,hits: 2,DST: 66.102.9.147
Blocked OUT: @,hits: 3,DST: 66.102.9.147
Got SIGTERM! Dumping stats and exiting.
```

Could anyone please help to explain why '66.102.9.147' is getting blocked when the only ip address in my blocklist is '9.9.9.9'? (By the way, I've done all the requisite reloads and restarts. My ipfilter.dat file also only contain this single range).

I don't have any firewall installed atm and since I'm new to linux I have no idea what the following output means:
```
~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
moblock_in  0    --  anywhere             anywhere            state NEW 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
moblock_fw  0    --  anywhere             anywhere            state NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
moblock_out  0    --  anywhere             anywhere            state NEW 

Chain moblock_fw (1 references)
target     prot opt source               destination         
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_in (1 references)
target     prot opt source               destination         
RETURN     0    --  192.168.1.0/24       anywhere            
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_out (1 references)
target     prot opt source               destination         
RETURN     0    --  anywhere             192.168.1.0/24      
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

```

If any of that helps, I'd really appreciate someone telling me what's going wrong because I'm at my wit's end right now.

Thanks.

---

### Post by jre on 2008-04-04
```
ip:9.9.9.9-9.9.9.9
``` is in the peerguardian .p2p text format. Therefore set
BLOCKLIST_FORMAT="p" in moblock.conf.

Just out of interest: where from did you get the amd64 package?

---

### Post by partiallynothing on 2008-04-06
I'm installed MoBlock from source as per the instructions on its home page ([http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)). Everything went fine (as far as I could tell), but when trying to update itself on first start, it said it could not download trojan.gz.

The moblock-control log showed the following:

```
2008-04-06 01:35:02 PM EDT Begin: moblock-control update
Updating blocklists ...
Updating ads-trackers-and-bad-pr0n.gz * . No update available.
Updating bogon.gz * . No update available.
Updating dshield.gz * . No update available.
Updating hijacked.gz * . No update available.
Updating iana-multicast.gz * . No update available.
Updating iana-private.gz * . No update available.
Updating iana-reserved.gz * . No update available.
Updating level1.gz * . No update available.
Updating level2.gz * . No update available.
Updating Microsoft.gz * . No update available.
Updating rangetest.gz * . No update available.
Updating spider.gz * . No update available.
Updating spyware.gz * . No update available.
Updating templist.gz * . No update available.
Updating trojan.gz * Error 6: www.bluetack.co.uk/config/trojan.gz not available. Aborting!
```

Any ideas. Can I get this file elsewhere?

---

### Post by skipo on 2008-04-07
> **partiallynothing said:**
> Everything went fine (as far as I could tell), but when trying to update itself on first start, it said it could not download trojan.gz.


Bluetack does not maintain that blocklist any more and have removed it from their server.

---

### Post by LPGDEV on 2008-04-07
I tried to get the lists from [http://iblocklist.com/lists.php](http://iblocklist.com/lists.php), but moblock can't parse the lists. How would I go about including these lists?

---

### Post by jre on 2008-04-07
For now remove the trojan.gz entry from /etc/moblock/blocklists.list.

A new version which fixes that is soon coming.

---

### Post by Dawa on 2008-04-07
I tried to install the new moblock, but it fails with a size mismatch in the update manager.

---

### Post by jre on 2008-04-08
> **Dawa said:**
> I tried to install the new moblock, but it fails with a size mismatch in the update manager.
Was it 0.9~rc2-8 or 0.9~rc2-10?
I had the problem myself with the -8 and therefore made a new upload.
So if you still have problems with -10 please tell me.

---

### Post by jamesford on 2008-04-08
0.9~rc2-10
ive found a little problem
i added some ips to the local blocklist (locallist /etc/moblock/custom-blocklist.p2p) and changed the name of each entry to 'MOTEST999' so that it would be easy to recognize them in the log
what i get is a over 100 entries of
Skipping useless range: MOTEST999
i guess it could be duplicates..

several were also removed by my 'Remove lines from the blocklist' in moblock.conf

why are these skipped and why dont these manually added ips override the remove feature ?

imho either such a local list should be excepted from any removal rule or there should be a locallist_override_rules list of some sort so that im guaranteed that all entries in my local list are blocked

---

### Post by jre on 2008-04-09
> **jamesford said:**
> 0.9~rc2-10
ive found a little problem
i added some ips to the local blocklist (locallist /etc/moblock/custom-blocklist.p2p) and changed the name of each entry to 'MOTEST999' so that it would be easy to recognize them in the log
what i get is a over 100 entries of
Skipping useless range: MOTEST999
i guess it could be duplicates..

several were also removed by my 'Remove lines from the blocklist' in moblock.conf

why are these skipped and why dont these manually added ips override the remove feature ?

imho either such a local list should be excepted from any removal rule or there should be a locallist_override_rules list of some sort so that im guaranteed that all entries in my local list are blocked
This is how in the packages the lsits are loaded:

1. First all lists from blocklists.list are downloaded, extracted and cat'ted together (including the locallists),

2. then the IP_REMOVE is done.

3. the resulting list is /etc/moblock/guarding.p2p (if you have peerguardian text format blocklists). This list is loaded by the MoBlock daemon which does the range merging and skipping.

ad 2.:
Do you really have entries there which also match your locallists? Can't you just choose some names in your locallist which are not matched by the IP_REMOVE?

ad 3.:
AFAIK skipping is done when a range with one single IP should be loaded which is already covered by a previous range.
I think that, if some of your ranges are skipped, then these ranges were already present in your downloaded blocklists.
Please test this:
- Try to ping IPs from the "Skipping useless range: MOTEST999" range.
- Then remove your locallist and reload MoBlock. Then try to ping these IPs again.
In both cases you should not be able to ping these IPs. Everything is working as I'd expect it and I see no need to fix anything.
If you can ping the IPs then you've found a bug in MoBlock - which I doubt to be so.

---

### Post by pelle.k on 2008-04-09
Hey jre. Long time no see.
I was thinking; i am finding myself further and further away from this thread, and i think that is sort of bad since this is where people go to fetch the newest reports etc. on what going on with moblock.
What about you creating a new thread, where you have the "first post", and i can link to that one from this thread, until this thread is transitioned away? Just an idea...

---

### Post by jre on 2008-04-09
Oh, I'd like you to stay ;-)
Of course we might change locations. Is there a possibility to CLOSE threads here?
Thanks anyway for all your work.

Greetings!
jre

---

### Post by pelle.k on 2008-04-09
When you have the time, create a new thread/howto and let us know about it in this thread, and i'll update the first post accordingly, and contact a forum admin and have this thread locked.
I will of course help out when i can. I wouldn't want to miss out on the fun! :)

---

### Post by peepingtom on 2008-04-11
oo

---

### Post by lucien on 2008-04-18
Hi,

I've added the MSN port to WHITE_TCP_OUT:
```
WHITE_TCP_OUT="80 443 1863"
```
But I still can't connect:
```
Fri Apr 18 08:34:39| Marked block OUT: Microsoft Corp,hits: 2,DST: 65.54.239.20
Fri Apr 18 08:35:37| Marked block OUT: Microsoft Corp,hits: 3,DST: 65.54.239.20
Fri Apr 18 08:37:31| Marked block OUT: Microsoft Corp,hits: 4,DST: 65.54.239.20
Fri Apr 18 08:41:20| Marked block OUT: Microsoft Corp,hits: 5,DST: 65.54.239.20
```
Any ideas? I'm using Hardy Heiron and Moblock 0.9~rc2-10+hardy+i386.

Greetings,
Pascal

---

### Post by pelle.k on 2008-04-18
Eh, are you sure you only need to whitelist *outgoing* connections?
Use
```
netstat --tcp --udp
```
to spy on your connections

You never said you have reloaded moblock, nor what configuration file you modified.
Be verbose about these things !

---

### Post by jimtb on 2008-04-19
@lucien: You can also find the option to use the http method to connect in the IM client you're using. This way the only port you will have to have whitelisted is port 80.

:-)

---

### Post by pt123 on 2008-04-24
On Hardy I have the moblock rep. in my apt sourcelist. 

There is a moblock package that shows ups in the packages to be updated. 

When I try to update it I get this error:
```
E: /var/cache/apt/archives/moblock_0.9~rc2-10+hardy+i386_i386.deb: subprocess new pre-removal script returned error exit status 3

```

When I try to update the package through synaptic I get this error (same one but with a longer debug output):
```

(Reading database ... 129517 files and directories currently installed.)
Preparing to replace moblock 0.9~rc2-7+hardy+i386 (using .../moblock_0.9~rc2-10+hardy+i386_i386.deb) ...
 * Stopping MoBlock moblock
   ...fail!
invoke-rc.d: initscript moblock, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 3
dpkg - trying script from the new package instead ...
 * Stopping MoBlock moblock
   ...fail!
invoke-rc.d: initscript moblock, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/moblock_0.9~rc2-10+hardy+i386_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 3
 * MoBlock is configured not to start automatically at boot time.
 * To change this edit the MOBLOCK_INIT entry in /etc/moblock/moblock.conf.
 * Also check /etc/default/moblock.
Errors were encountered while processing:
 /var/cache/apt/archives/moblock_0.9~rc2-10+hardy+i386_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:



```

Is there a way to fix this problem. 

Note I also have Mobloquer installed.

---

### Post by empthollow on 2008-04-24
When i am running moblock i cannot view and files on my ftp server.
I have port 21 white listed in and out.  I can log into the server which is more than i could do before port 21 was white listed.  When i try to connect with gftp i recieve this error.

Cannot create a data connection: Connection refused

This was previously not a problem, i am using hardy.  Does anyone have any ideas on how i can use ftp without completely stopping moblock? 
Thanks in advance.

EDIT:
i took a look at my blocklist and it turns out godaddy's ip is in the list.  godaddy is listed multiple times, once as godaddy inc (this is where my ip range is) and a few others as godaddy anti p2p.  is it safe for me to remove godaddy inc from my blocklist or am i better off stopping moblock while i do my webmin-istration.  Thanks for your input.

---

### Post by draggy on 2008-04-25
I have a server setup to be a router, using iptables rules for the firewall and NAT forwarding. Since moblock adds rules to iptables, what would be the best way to integrate my rules and moblock's rules? It didn't seem to be working for the NAT machines when I first tried it. 

More troubleshooting on my part is still needed, but I'd like to know opinions on the best way of merging the rules.

---

### Post by jamesford on 2008-04-25
im having a lot of troubles installing moblock in hardy (amd64) -0.9~rc2-10 compiled myself

during install i get messages like
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 * Some iptables rules could not be deleted. The most common reason for this is
 * that they did not exist. If MoBlock was not running this is the correct
 * behaviour. But if MoBlock was running there is some problem. Make sure that
 * MoBlock inserts its iptables rules correctly and that other software, e.g.
 * firewall applications, don't delete them. Make sure that MoBlock is started
 * after other firewall applications.

but it eventually finishes but it only seems to block outbound connections
ive tried both with ufw enabled and disabled

any help on this ?

---

### Post by Dawa on 2008-04-26
i tried updating moblock today and got this message:

Updating level1.gzrm: cannot remove `level1.gz': No such file or directory
 *  failed! Using old blocklist.

is this my problem, or is the update server just down?

EDIT:  I fixed this by copying the level1.gz from /var/spool/moblock/used  to /var/spool/moblock

---

### Post by jhezza on 2008-04-27
Hi
I am having problems installing moblock, when i do sudo aptitude install moblock i get the following error.
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following partially installed packages will be configured:
  moblock 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up moblock (0.9~rc2-10+hardy+i386) ...
 * Reloading MoBlock moblock                                                                                                                              failed. Trying an update instead, this may take several minutes.
You may do in another terminal a "tail -f /var/log/moblock-control.log"
to follow the update process. Pressing "control" + "c" stops this.
The lists are saved to /var/spool/moblock/.
 * Updating blocklists and reloading MoBlock moblock                                                                                                      failed.
No blocklist in /etc/moblock/guarding.p2p.
Try a "moblock-control update" to complete the installation.
dpkg: error processing moblock (--configure):
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 moblock
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up moblock (0.9~rc2-10+hardy+i386) ...
 * Reloading MoBlock moblock                                                                                                                              failed. Trying an update instead, this may take several minutes.
You may do in another terminal a "tail -f /var/log/moblock-control.log"
to follow the update process. Pressing "control" + "c" stops this.
The lists are saved to /var/spool/moblock/.
 * Updating blocklists and reloading MoBlock moblock                                                                                                      failed.
No blocklist in /etc/moblock/guarding.p2p.
Try a "moblock-control update" to complete the installation.
dpkg: error processing moblock (--configure):
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 moblock
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      

```

any help would be greatly appreciated. Thanks

---

### Post by mike.berggren on 2008-04-27
Hi. Really simple question but I couldn't find it in the FAQs...

How can I verify that updates are succeeding? 

-MB

---

### Post by mike.berggren on 2008-04-27
> **mike.berggren said:**
> Hi. Really simple question but I couldn't find it in the FAQs...

How can I verify that updates are succeeding? 

-MB

(*sigh) nevermind... it was right in front of me the whole time: /var/log/moblock-control.log ](*,)

---

### Post by quixotic-cynic on 2008-04-27
> **empthollow said:**
> I took a look at my blocklist and it turns out godaddy's ip is in the list.  godaddy is listed multiple times, once as godaddy inc (this is where my ip range is) and a few others as godaddy anti p2p.  is it safe for me to remove godaddy inc from my blocklist or am i better off stopping moblock while i do my webmin-istration.  Thanks for your input.

You are probably better off stopping moblock + p2p apps when using your ftp app - there is no guarantee which IPs godaddy will use for anti-p2p stuff.

If godaddy inc is in the level2 blocklist it is safer to remove than if it is in the level1 blocklist (which you should never remove items from).

The blocklists come from bluetack.co.uk so they may be able to provide additional help.

---

### Post by quixotic-cynic on 2008-04-27
> **jhezza said:**
> Hi
I am having problems installing moblock, when i do sudo aptitude install moblock i get [an] error.

I got this problem but fixed it with some minor experimentation. I cant remember how I fixed it... >.<

Some suggestions:

1) Run aptitude, look at the moblock package and check that the packages that moblock depends-on/suggests are installed.

2) Purge moblock (sudo aptitude purge moblock) and then reinstall it.

3) Try running "sudo moblock-control update".

4) Try experimenting with mobloquer.

---

### Post by quixotic-cynic on 2008-04-27
> **jamesford said:**
> im having a lot of troubles installing moblock in hardy (amd64) -0.9~rc2-10 compiled myself. any help on this ?

Presumably you compiled it yourself because you require unusual settings. If not then I would definitely try the .deb package.

The firewall will definitely cause problems with moblock since they will fight for control over iptables.

You could try temporarily removing ufw (purge/delete it if possible - I don't know if it is 'fully' disabled when disabled - it may still interfere with iptables), starting/stopping moblock a couple of times (to make sure it really has overwritten your iptables file), and then look at the iptables file to see if it looks right - i.e. if it is set to deal with the inbound connections properly.

---

### Post by quixotic-cynic on 2008-04-27
> **draggy said:**
> I have a server setup to be a router, using iptables rules for the firewall and NAT forwarding. Since moblock adds rules to iptables, what would be the best way to integrate my rules and moblock's rules?

Afaik, the best way to do it is by hand, i.e.: run moblock and copy the iptables file it creates to a temporary file somewhere. Then get your iptables file that you usually use and manually integrate the rules from the temp file into your usual iptables file.

---

### Post by quixotic-cynic on 2008-04-27
> **pt123 said:**
> When I try to update it I get this error:
```
E: /var/cache/apt/archives/moblock_0.9~rc2-10+hardy+i386_i386.deb: subprocess new pre-removal script returned error exit status 3

```

Is there a way to fix this problem.

Try:
sudo moblock-control stop
sudo aptitude update
sudo aptitude safe-upgrade (or sudo aptitude and find the package yourself)
sudo moblock-control start

---

### Post by jamesford on 2008-04-27
quixotic-cynic, i compliled myself due to there not being any amd64 deb available. or is there?

---

### Post by mike.berggren on 2008-04-27
Is there a webmin module available for moblock? If not, could someone point me to some basic documentation on creating webmin modules? 

Ideally, I'd like the module to offer the following functionality:

1) Stop/start services
2) Allow user to add/remove whitelisted ports/IPs
3) Choose which lists to enable.
4) Pull up recent log entries. 

Thanks, 

MB

---

### Post by quixotic-cynic on 2008-04-27
> **jamesford said:**
> quixotic-cynic, i compliled myself due to there not being any amd64 deb available

Makes sense; to my knowledge only i386 is built due to who has what pc available.

---

### Post by pt123 on 2008-04-27
> **quixotic-cynic said:**
> Try:
sudo moblock-control stop


 * Stopping MoBlock moblock                                              [fail] 

I got the above, I don't run moblock on start up ( and don't wish to). 

When I tried 
sudo /etc/init.d/moblock stop
I got 
 * Stopping MoBlock moblock                                              [fail] 

When I tried 
sudo /etc/init.d/moblock start
I got 
* MoBlock is configured not to start automatically at boot time.
 * To change this edit the MOBLOCK_INIT entry in /etc/moblock/moblock.conf.
 * Also check /etc/default/moblock.

Not sure if this meant it succeeded in starting.
It didn't because Mobloquer is reporting it couldn't start.

Interestingly I was able to start it through Mobloquer.

I will try uninstalling moblock and then reinstalling it.

When I tried to remove it I got this message:
```

Removing moblock ...
 * Stopping MoBlock moblock                                              [fail] 
invoke-rc.d: initscript moblock, action "stop" failed.
dpkg: error processing moblock (--remove):
 subprocess pre-removal script returned error exit status 3
 * MoBlock is configured not to start automatically at boot time.
 * To change this edit the MOBLOCK_INIT entry in /etc/moblock/moblock.conf.
 * Also check /etc/default/moblock.
Errors were encountered while processing:
 moblock
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Maybe I should booting into recovery mode and sudo apt-get remove moblock

---

### Post by quixotic-cynic on 2008-04-28
> **pt123 said:**
> * Stopping MoBlock moblock                                              [fail] 

I got the above, I don't run moblock on start up ( and don't wish to).

Ok, that was not clear to me. I thought the reason it might not be working is that it was unsuccessfully stopping moblock... but, if it's not running in the first place then I guess it's something else.

---

### Post by jre on 2008-04-28
@pt123: your problem was fixed in moblock (0.9~rc2-4). Probably you kept your old /etc/init.d/moblock.
Anyway, set MOBLOCK_INIT="1", then updating will work. Make sure to install all new config files when you are asked by apt/synaptic/whatever. I recommend to make all configuration changes in /etc/default/moblock. After the update you can safely go back to MOBLOCK_INIT="0".

@emphtollow: I suggest to whitelist the specific IP of your FTP server with the WHITE_IP_OUT="" option. Have a look at /var/log/moblock.log to see which IP is blocked. You can also do this with a simple click in mobloquer.

@lucien:
Using the WHITE_IP_OUT="" option might also help you. So I fixed jabber here.

> **mike.berggren said:**
> Is there a webmin module available for moblock?
No, I don't think so.

@jhezza: if you did not already quixotic-cynic's advice: do a "sudo moblock-control update" that should fix the package installation. Installation failed because somehow the blocklists could not be downloaded/installed. Have a look at /var/log/moblock-control.log to learn more about what went wrong.

@draggy: Sorry, no idea. All I can say is that with the MARKing feature (since moblock 0.9~rc2) it is easy to integrate MoBlock with firewalls. Simply start MoBlock after all other iptables insertions. but I don't know if there are specific things when using nat

> **jamesford said:**
> im having a lot of troubles installing moblock in hardy (amd64) -0.9~rc2-10 compiled myself

during install i get messages like
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
 * Some iptables rules could not be deleted. The most common reason for this is
 * that they did not exist. If MoBlock was not running this is the correct
 * behaviour. But if MoBlock was running there is some problem. Make sure that
 * MoBlock inserts its iptables rules correctly and that other software, e.g.
 * firewall applications, don't delete them. Make sure that MoBlock is started
 * after other firewall applications.
Well, this is not a problem. This e.g. always comes if you stop an already stopped Moblock. Post your iptables rules and I might see if INCOMING traffic is checked. Note that other firewalls (I don't know ufw) might purge your moblock iptables rules, so make sure to (re-)start moblock after starting/stopping them.

> **jamesford said:**
> quixotic-cynic, i compliled myself due to there not being any amd64 deb available. or is there?
Finally good news for you: I've got a new amd64 laptop ;-) So just wait some time ;-)

---

### Post by mike.berggren on 2008-04-28
I want a deeper understanding of how Moblock works... is there any documentation (ERDs, flowcharts, etc) that show how the process works? 

Btw, is moblock multi-threaded? I would assume so but thought I'd check anyway...

-MB

---

### Post by pt123 on 2008-04-29
> **jre said:**
> @pt123: your problem was fixed in moblock (0.9~rc2-4). Probably you kept your old /etc/init.d/moblock.
Anyway, set MOBLOCK_INIT="1", then updating will work. Make sure to install all new config files when you are asked by apt/synaptic/whatever. I recommend to make all configuration changes in /etc/default/moblock. After the update you can safely go back to MOBLOCK_INIT="0".

The files have it  set to 1 in the /etc/init.d/moblock file and in /etc/moblock/moblock.conf. I have not touched either of them. 

Which one takes priority. :confused:

---

### Post by jre on 2008-04-29
> **mike.berggren said:**
> I want a deeper understanding of how Moblock works... is there any documentation (ERDs, flowcharts, etc) that show how the process works?
Documentation is in /usr/share/doc/moblock/
Also have a look at the homepages moblock.berlios.de and moblock-deb.sf.net.
There are no graphics etc., yet. But I might do one once to explain the iptables rules.
Ask when you have questions.

> **mike.berggren said:**
> Btw, is moblock multi-threaded? I would assume so but thought I'd check anyway...

No idea, I'm not a programmer. Mobloquer 0.5 is.


> **pt123 said:**
> The files have it  set to 1 in the /etc/init.d/moblock file and in /etc/moblock/moblock.conf. I have not touched either of them. 

Which one takes priority. :confused:

They are loaded in the following order, so the last overwrites previous ones:
/etc/init.d/moblock
/etc/moblock/moblock.conf
/etc/default/moblock

---

### Post by apamatos on 2008-05-02
Hello

I tried to install MoBlock 0.9 (Latest version of the Ubuntu Gutsy repository). From what I read in this thread it should work with Firestarter.

I have a LAN and the computers access the internet through the gateway that is running MoBlock. I White-listed the ports and the ip range of the LAN as suggested in these posts and configuration documentation. Masquerading and DHCP is activated by Firestarter running in the same gateway cmputer.

Now, when I activte Firestarter first (MoBlock off) the LAN computers are able to browse the internet. As soon as I activate MoBlock all internet access stops for the LAN computers, but not for the gateway that still can see the internet.

Help please. How can I restore internet access to the LAN computers with MoBlock on ????!!!! This should not be the nightmare it looks like, since this setup should be fairly common.

Cheers

AP

---

### Post by dnoiz on 2008-05-03
Hello,

I'm trying to build moblock myself on Hardy 64-bit and I get the following error message, I hope someone can help me out,

```

bboxone@bboxone:~$ mkdir moblock
bboxone@bboxone:~$ cd moblock/
bboxone@bboxone:~/moblock$ sudo apt-get build-dep moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bboxone@bboxone:~/moblock$ sudo apt-get source moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'moblock' packaging is maintained in the 'Svn' version control system at:
https://moblock-deb.svn.sourceforge.net/svnroot/moblock-deb/moblock/
Need to get 63.1kB of source archives.
Get:1 http://moblock-deb.sourceforge.net hardy/main moblock 0.9~rc2-10+hardy+i386 (dsc) [889B]
Get:2 http://moblock-deb.sourceforge.net hardy/main moblock 0.9~rc2-10+hardy+i386 (tar) [21.8kB]
Get:3 http://moblock-deb.sourceforge.net hardy/main moblock 0.9~rc2-10+hardy+i386 (diff) [40.4kB]
Fetched 63.1kB in 2s (27.8kB/s)                                
dpkg-source: extracting moblock in moblock-0.9~rc2
dpkg-source: unpacking moblock_0.9~rc2.orig.tar.gz
dpkg-source: applying ./moblock_0.9~rc2-10+hardy+i386.diff.gz
bboxone@bboxone:~/moblock$ cd moblock-0.9~rc2/
bboxone@bboxone:~/moblock/moblock-0.9~rc2$ sudo dpkg-buildpackage -rfakeroot
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package moblock
dpkg-buildpackage: source version 0.9~rc2-10+hardy+i386
dpkg-buildpackage: source changed by jre <jre-phoenix@users.sourceforge.net>
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
Can't exec "fakeroot": No such file or directory at /usr/bin/dpkg-buildpackage line 477.
dpkg-buildpackage: failure: fakeroot debian/rules clean failed with unknown exit code -1
bboxone@bboxone:~/moblock/moblock-0.9~rc2$ 

```

R.

---

### Post by mike.berggren on 2008-05-03
Some more questions: 

- What's the size threshold for logs (moblock.log moblock-control.log) to roll over? Is that definable? If so, where can I modify this?

Could I get clarification on how blocklist data is handled? Its my understanding that after the various blocklists are downloaded, moblock sifts through the data for duplicates and then stores the ranges... where? In a flat file? In memory?

Thanks, 

MB

---

### Post by pt123 on 2008-05-03
> **jre said:**
> 
They are loaded in the following order, so the last overwrites previous ones:
/etc/init.d/moblock
/etc/moblock/moblock.conf
/etc/default/moblock

Thanks that solved the issue. What's the deal with 3 conf files?

---

### Post by mike.berggren on 2008-05-04
> **pt123 said:**
> Thanks that solved the issue. What's the deal with 3 conf files?

I second this. :) 

Why are there three configuration files and which one should we be modifying?

-MB

---

### Post by stinger30au on 2008-05-04
i give up trying to instal moblock, i use this one instead

[https://sourceforge.net/project/showfiles.php?group_id=198679](https://sourceforge.net/project/showfiles.php?group_id=198679)

im using 8.04 so i just d/l the deb file and let it install restarted pc, it did the updates and im off and running.piece of cake

---

### Post by jre on 2008-05-06
> **dnoiz said:**
> Hello,

I'm trying to build moblock myself on Hardy 64-bit and I get the following error message, I hope someone can help me out,

```
 fakeroot debian/rules clean
Can't exec "fakeroot": No such file or directory at /usr/bin/dpkg-buildpackage line 477.
dpkg-buildpackage: failure: fakeroot debian/rules clean failed with unknown exit code -1
bboxone@bboxone:~/moblock/moblock-0.9~rc2$ 

```

R.
Install the package "fakeroot"



> **mike.berggren said:**
> - What's the size threshold for logs (moblock.log moblock-control.log) to roll over? Is that definable? If so, where can I modify this?
It's done by "logrotate". But not after size just in daily interrvals. Configuration is done in /etc/logrotate.d/. Have a look at the logrotate documentation to learn if it is possible to consider file size.

> **mike.berggren said:**
> Could I get clarification on how blocklist data is handled? Its my understanding that after the various blocklists are downloaded, moblock sifts through the data for duplicates and then stores the ranges... where? In a flat file? In memory?
The lists are downloaded to /var/spool/moblock/.
If the download succeeded they are copied to /var/spool/moblock/used
Then these lists are unpacked and *cat*'ted together to one list.
Optional: If you use the configuration "IP_REMOVE" now some lines are *grep*'ped out.
The resulting list is copied to /etc/moblock/guarding.p2p (in case you are using the peerguardian v2 text format blocklists (current default)).
Until now that was all done by the bash script moblock-control. Note that this master blocklist contains duplicates.
If you now start the moblock daemon this file gets loaded. During this loading ranges get merged and duplicates get sorted out. For more details you have to take a look on the source code or ask the upstream author Morpheus (moblock.berlios.de).
Short answer: file on harddisk does contain duplicates, ranges in memory are already merged.

> **pt123 said:**
> Thanks that solved the issue. What's the deal with 3 conf files?

/etc/init.d/moblock: This is more a script then a conf file. Normally users should not edit it. It's only a conf file from the technical side (Debian packaging). I added every conf variable there, too, because some users deleted their real conf files which resulted in broken packages.

[BTW: /usr/bin/moblock-control also includes all configuration variables (conf file no. 4). It gets executed by the init script. But users should just keep their hands off this file ;-) )

/etc/moblock/moblock.conf: This is the main configuration file which does list all possible configuration variables and comments which explain them. It does not include any source. So it's also a kind of **documentation** file

/etc/default/moblock: Here you can insert all your configuration. Yes, short answer: **Use this file!** I added this file because the big moblock.conf does change frequently. Now if you did edit moblock.conf and make a package update your packaging software (aptitude/synaptic/...) will ask you whether you want to keep your changes or install the new version. The best to do would be to take the new version (e.g. bringing in new features) and to integrate your own changes to this new file. Unfortunately this is time consuming.
Therefore many users just kept their old moblock.conf.
This is the second reason why I had to make default entries in every script (init.d and moblock-control, see above).
Further to make automatic package updates easier I added the /etc/default/moblock file which does allow to keep user changes seperate from the main configuration bulk. Since the /etc/default/moblock file never gets changed in the packages (it only contains a short explanation) you will never be asked if you want to keep your changes or install my new version.

Greets
jre - who is astonished why he did write so much. Everybody feel free to add this stuff to the wiki (see post #1 in this thread).

---

### Post by jre on 2008-05-06
> **apamatos said:**
> Now, when I activte Firestarter first (MoBlock off) the LAN computers are able to browse the internet. As soon as I activate MoBlock all internet access stops for the LAN computers, but not for the gateway that still can see the internet.

Help please. How can I restore internet access to the LAN computers with MoBlock on ????!!!! This should not be the nightmare it looks like, since this setup should be fairly common.

Cheers

AP

When you do the whitelisting also edit the _FORWARD entries (not only _IN and _OUT)

---

### Post by empthollow on 2008-05-10
> **quixotic-cynic said:**
> You are probably better off stopping moblock + p2p apps when using your ftp app - there is no guarantee which IPs godaddy will use for anti-p2p stuff.

If godaddy inc is in the level2 blocklist it is safer to remove than if it is in the level1 blocklist (which you should never remove items from).

The blocklists come from bluetack.co.uk so they may be able to provide additional help.

Thanks for the input, since i don't like removing ip's from blocklists i'll do just that and stop all p2p apps when utilizing ftp.

---

### Post by apamatos on 2008-05-11
> **jre said:**
> When you do the whitelisting also edit the _FORWARD entries (not only _IN and _OUT)
Thanks. It solved the problem

AP

---

### Post by apamatos on 2008-05-11
> **jre said:**
> When you do the whitelisting also edit the _FORWARD entries (not only _IN and _OUT)


Thanks. It solved the problem

AP

---

### Post by empthollow on 2008-05-14
i have recenly started using gmail's imap server.  moblock is blocking the signal to retrieve my message to view because moblock is blocking it.  according to this page [http://mail.google.com/support/bin/answer.py?answer=78799&topic=&useful=1&expand_useful=1&#helpful]("http://mail.google.com/support/bin/answer.py?answer=78799&topic=&useful=1&expand_useful=1&#helpful"), the ports that is uses are 993 465 587 ... i have whitelisted these in udp, tcp, in, out and _forward.  moblock is still blocking the ip. i don't want to remove the ip from being blocked, i would just like moblock to allow requests from and to these ports.  How do i do that??  One other thing, it's worth mentioning that evolution does not hang when i send and recieve.  I just cannot view my messages when i click on them.  Thanks

---

### Post by empthollow on 2008-05-15
I've solved my own problem.  the /etc/default/moblock file was overwriting the /etc/moblock/moblock.conf file thus making my changes invalid.  I believe this was caused by using the mobloquer gui tool.  I believe the file was created by that program.  Perhaps i'll just use the moblock-control utility, i've grown acustom to it anyway because there was no gui for so long.

---

### Post by jre on 2008-05-22
> **pelle.k said:**
> What about you creating a new thread, where you have the "first post", and i can link to that one from this thread, until this thread is transitioned away? Just an idea...
Finally done. You can find the new "General MoBlock thread" in the Networking & Wireless section, or just click here: [http://ubuntuforums.org/showthread.php?p=5016102](http://ubuntuforums.org/showthread.php?p=5016102)
I placed the thread there because it is not really an HOWTO any more as your thread originally was.

Thanks for all your work, feel free to step by any time.

Greetings!
jre

---

### Post by K.Mandla on 2008-05-22
Thread closed and moved to Outdated Tutorials and Tips at the request of the OPer. :)

---


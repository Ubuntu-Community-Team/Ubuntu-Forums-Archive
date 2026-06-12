---
title: "HOWTO: Surf and IM anonymously using tor and privoxy"
date: 2005-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by flygmaskin on 2005-01-11
This howto will show you how you can surf (or IM, or irc, or whatever) anonymously using the [tor](http://tor.eff.org) network. I'm using hoary, so I don't know if this will work on warty. Please give me some feedback on this.

**BEFORE YOU START**
Make sure you have enabled the universe repository.

**INSTALL TOR AND PRIVOXY**
```
$ sudo apt-get install tor privoxy
```

**CONFIGURE PRIVOXY**
Add the following line to */etc/privoxy/config*. You can put it at the top of the file if you want (Don't forget the last dot.)
> forward-socks4a / localhost:9050 .
then it's time to start tor and privoxy
```

$ sudo /etc/init.d/tor start
$ sudo /etc/init.d/privoxy start
```

To Torify an application that supports http (ie Firefox), just point it at Privoxy (that is, localhost:8118 ). To use SOCKS directly (for example, for instant messaging, Jabber, IRC, etc), point your application directly at Tor (localhost:9050). 

To see if everything is working, go to [this site.](http://peertech.org/privacy-knoppix/)

---

### Post by jdong on 2005-01-11
I strongly support the use of anonymizing functions to browse the internet. Excellent documentation!

Please tell me if it works in Warty -- if it doesn't I'll help you out with Warty backports/extras!

---

### Post by poptones on 2005-01-12
"No hay ningún sitio Web en esta dirección."

Is this coming from the app or from some weird server it keeps connecting to?

---

### Post by wallijonn on 2005-01-12
[QUOTE=poptones]"No hay ningún sitio Web en esta dirección."[/QUOTE]

I think that translated it means "There's no website [defined] in this direction".

Under Warty the file is in /etc/tor/tor-socks.conf.

[http://network-tools.com/analyze/](http://network-tools.com/analyze/)

---

### Post by negativ on 2005-01-15
Is there any way to speed this up?  I've got it working per the instructions in the post, but the result is that browsing is now sssslllloooowwww.  It makes me feel like I'm on dial-up.

Could there be something tweakable, or is this just the price you pay?

---

### Post by wallijonn on 2005-01-17
With TOR installed I basically see no difference in web surfing, ie, I detect no slow down. I'm on a 128k DSL.

---

### Post by kyle.quamme on 2005-01-19
I am having problems getting this set up, but I really want to use it. Could someone that has it working post some directions for Firefox, Gaim, and whatever else you would like to help me out a little? It would be greatly appreciated.

Thanks

---

### Post by Leaf on 2005-01-19
[QUOTE=kyle.quamme]I am having problems getting this set up, but I really want to use it. Could someone that has it working post some directions for Firefox, Gaim, and whatever else you would like to help me out a little? It would be greatly appreciated.

Thanks[/QUOTE]

Sure thing buddy.

To get firefox to work with it (keep in mind I'm using 1.0)
10 GOTO to edit>prefs
20 GOTO the general tab
30 GOTO Connection settings
40 set manual proxt connection
50 in the HTTP field type localhost 
60 in the port field type 8118
70 this assumes that you followed the OP's instructions.

this is what mine looks like [http://img114.exs.cx/my.php?loc=img114&image=screenshot4hc.png](http://img114.exs.cx/my.php?loc=img114&image=screenshot4hc.png)

Actually I had a question too, do we have to type sudo /init.d start tor/privoxy every time the computer boots up?  Originally I thought it didnt matter, but I modified one of my xsession.d startup scripts to run the commands at startup.

For GAIM however, I did not get it to work, with either one of the localhost ports and attempting every combination of socks4/5 http etc.  Kept on getting a connection error.  Anyone else have any luck?

Thanks again to the OP

---

### Post by Tichondrius on 2005-01-22
As is common in the world of Linux, just like the internet at large, many times the information you find is not complete and/or accurate, but still potentially very valuable. In this case, the instructions are generally correct, but the problem is that the tor package in Ubuntu's repositores is a little old (version 0.0.7) and doesn't work with some networks, like mine. Tor did not start for me, and its log file  (/var/log/tor/log) contained an error:

[err] You are running Tor version 0.0.7, which will not work with this network.

So you need to get the latest version 0.0.9.2 from [here](http://tor.eff.org/download.html). Follow the instructions to add the Tor repository to your sources.list file, do "sudo apt-get update" and download and install it using apt-get or synaptic. Then startup the tor daemon:

$ sudo /etc/init.d/tor start

to check that it's running and listenning on port 9050:

$ netstat -a | grep 9050

Now everything should work, assuming you set firefox proxy to localhost:8118 as shown in the previous post. And btw, you do not need to start tor and privoxy manually after a reboot, as they were added to the system startup scripts, when the packages were installed.

There is definetly a long wait for webpages to load, but you do get complete  anonimity as verfied by the link given in the first post. To stop using it, just change the proxy setting in firefox back to "direct connection to the internet" (no proxy) or whatever it was before. I don't think there is any impact on system performance if you are not using this anonymizing proxy.

---

### Post by Lovechild on 2005-01-26
it's kinda slow but it works.. gaim still doesn't like it though.

---

### Post by az on 2005-01-26
Has anyone use anon-proxy?  It is in Universe and it does the same thing.  I would wonder if anyone could tell me which one is truly more private?

JAP Homepage: [http://anon.inf.tu-dresden.de/index_en.html](http://anon.inf.tu-dresden.de/index_en.html)

---

### Post by Mendezster on 2005-03-30
[QUOTE=flygmaskin]This howto will show you how you can surf (or IM, or irc, or whatever) anonymously using the [tor](http://tor.eff.org) network. I'm using hoary, so I don't know if this will work on warty. Please give me some feedback on this.

...
...


To Torify an application that supports http (ie Firefox), just point it at Privoxy (that is, localhost:8118 ). To use SOCKS directly (for example, for instant messaging, Jabber, IRC, etc), point your application directly at Tor (localhost:9050). 

To see if everything is working, go to [this site.](http://peertech.org/privacy-knoppix/)[/QUOTE]

Hi guys,

Thanks for the tutorial.  This is a great tool, but I still have a couple of questions about this.  

1) I'm accessing things through squid.  Among the headers in Privoxy processed request, I get

Via: 1.1 site.name.net:3128 (squid/2.5.STABLE6)

Which of course negates the privacy affored by the ever-changing IP address.  How do I configure Privoxy to remove this header?

2) I can't get my IM to work through the proxy. Privoxy documentation says that it doesn't yet understand IM protocols.  Should I be connecting directly to tor's port?

Thanks in advance!

---

### Post by Mendezster on 2005-03-30
Bad form, following up on myself. Still, I'd like to publish the possible solutions in case other people are looking for them.

[QUOTE=Mendezster]
1) I'm accessing things through squid.  Among the headers in Privoxy processed request, I get

Via: 1.1 site.name.net:3128 (squid/2.5.STABLE6)
[/QUOTE]

This is actually a Squid setting called **visible hostname**.  Just change it to whatever  you want.



[QUOTE=Mendezster]
2) I can't get my IM to work through the proxy. Privoxy documentation says that it doesn't yet understand IM protocols.  Should I be connecting directly to tor's port?
[/QUOTE]

I had to work around this by creating an ssh tunnel from port 9050 on my machine, and using that port instead of Privoxy's for IM.

---

### Post by igster on 2005-04-06
[QUOTE=azz]Has anyone use anon-proxy?  It is in Universe and it does the same thing.  I would wonder if anyone could tell me which one is truly more private?

JAP Homepage: [http://anon.inf.tu-dresden.de/index_en.html](http://anon.inf.tu-dresden.de/index_en.html)[/QUOTE]

You may want to steer clear of this one.  I found this posted by one of the developers on their SourceForge forum:

[i]We are an interdisciplinary research 
group. And the lawyers amoung us find it quite interesting to do research 
about the amount of crimes carried out with JAP. And it's our goal to give 
the software the technical feature to track specific kind of crimes if and 
only if it is legally necessary. But I can promise you we do and plan no 
interception of all users. Interception will only be executed in justified 
individual cases ex post after warrant.[/i]

Apparently JAP has the ability to keep tabs on the users utilizing it which obviously undermines the entire point of using it in the first place.  Tor is sponsored by the [EFF](http://www.eff.org/) so I think it may be a bit more trustworthy (but who knows for sure right?).

---

### Post by ktulu1115 on 2005-04-08
Honestly, I don't think any of these 'localhost' proxy anonymizing services work.  Think about it - The idea of a proxy is to have a "middle" man between your PC and the end server you are communicating with (web, IM, etc).

If you run a local proxy server, the webservers or whatever you contact will have the IP of your proxy - which will be the same as your PC if it's run locally, completely defeating the purpose of using one.  The only way to do it correctly would be using a proxy *somewhere else* on the internet - that way any servers you hit will have the address of that proxy instead of yours.

There are a few sites that list pubilc proxy servers (dunno if these actually work anymore):

[www.lightspeed.de/irc4all/eproxy.htm](www.lightspeed.de/irc4all/eproxy.htm)
proxys4all.cgi.net/proxy.shtml
[www.ijs.co.nz/proxies.htm](www.ijs.co.nz/proxies.htm)

Also, **be forewarned** that not all public proxies mask your IP - some are transparent and foward your info to the websites.  If you're using a proxy in a first place there is a reason for it, so most likely you will want to avoid these.  There might be some sites/pages out there specifically designed for testing proxies to ensure they are not transparent (I googled for "proxy security check"), but I think just visiting a site that displays your IP will work just fine - ensure it displays the IP of your proxy and not your actual IP.

---

### Post by k.ODOMA on 2005-04-21
I set this up and it works fine with Firefox, but I almost immediately got a RSS message in Thunderbird from Slashdot telling me that my Headline Reader was banned. I guess they have problems with people behind proxies (like Tor) pulling too much/often.

---

### Post by aaarg on 2005-06-25
[QUOTE=ktulu1115]Honestly, I don't think any of these 'localhost' proxy anonymizing services work.  Think about it - The idea of a proxy is to have a "middle" man between your PC and the end server you are communicating with (web, IM, etc).

If you run a local proxy server, the webservers or whatever you contact will have the IP of your proxy - which will be the same as your PC if it's run locally, completely defeating the purpose of using one.  The only way to do it correctly would be using a proxy *somewhere else* on the internet - that way any servers you hit will have the address of that proxy instead of yours.[/QUOTE]



tor is not a 'localhost' proxy. the localhost is only used to point tor at privoxy. privoxy is used because most browsers leak your DNS requests when they use a SOCKS proxy directly.....read h__p://wiki.noreply.org/noreply/TheOnionRouter/TorFAQ#SOCKSAndDNS

[QUOTE=ktulu1115]The only way to do it correctly would be using a proxy *somewhere else* on the internet - that way any servers you hit will have the address of that proxy instead of yours.[/QUOTE]

that is exactly what tor does...read h__p://tor.eff.org/

---

### Post by rockmusic88 on 2005-06-26
aim works fine for me using socks 5, localhost and port 9050

---

### Post by aaarg on 2005-06-26
i have had mixed results with gaim on tor.......sometimes its fine and sometimes it will switch servers and i get connection errors.

---

### Post by word_virus on 2005-07-30
Hey, thanks for the guide!  Just followed your instructions and it worked perfectly.

A couple of notes for those of you running Hoary:

These instructions also work with Hoary.

The latest version of Tor in the hoary universe repositories is 0.0.9.2-1, so there is no need to add extra repositories to sources.list as suggested by another post in the thread.

The proper place in the config file for the line:
forward-socks4a / localhost 9050 .
is line 1008.  Remember, neatness counts! :)

If you need instructions about how to anonymize your applications after installing Tor, check out the Tor Wiki @:
[http://wiki.noreply.org/noreply/TheOnionRouter/TorifyHOWTO](http://wiki.noreply.org/noreply/TheOnionRouter/TorifyHOWTO)

I found it most helpful.

If you've put off trying Tor because you're worried about it bringing your surfing experience to a crawl, don't be.  I'm on a 1.5mbit DSL line and notice virtually no slow down.

Cheers, and thanks again!

---

### Post by Hikaru79 on 2005-08-03
I *highly* reccomend the Firefox extension "SwitchProxy" which basically allows you to turn Tor on and off with one click of the toolbar, which means you can turn it on for a site, and when you're done, turn it back off. 

As for the slowdown issue, I suppose it depends which proxy you get landed with. I'm on an American proxy at the moment, and the speed difference is VERY noticeable, but other times its not. Luck of the draw :)

---

### Post by srijith on 2005-08-17
I highly recommend that everyone immediately ditch the broken old obsolete Tor 0.0.9.2 version of Tor available via Ubuntu Universe. Using such an old version of Tor is worse that having Tor itself. I didn't say that. One of the core developers of Tor stated that.

You could either compile Tor from the source available at [http://tor.eff.org/download.html](http://tor.eff.org/download.html) or try and install the much updated debian package.

---

### Post by eamonn on 2005-09-01
I've installed Tor and set up Firefox to run with it, but when I installd switch proxy it says that I'm not running a proxy. Also, when I click on the link posted by flygmaskin to verify that Tor's working, nothing happens. Have I done something wrong setting it up or is this how it's supposed to run?

---

### Post by ubuntu27 on 2005-09-13
Hey guys! I love TOR. I've been using it on Windows and it works !!

Now... oh my! I am still a beginner at Linux. ANyway, the Tor in the repositories is old.

How can update it? I do not know how to compile yet :(

Please help me. 

The latest stable release is 0.1.0.14, and the latest development release is 0.1.1.6-alpha.

Thank you in advance

---

### Post by detour on 2005-09-13
If you are looking to install the lastest version of Tor I suggest you add the backports repositories to your apt sources. 

[http://ubuntuforums.org/showthread.php?t=52168](http://ubuntuforums.org/showthread.php?t=52168)

---

### Post by ubuntu27 on 2005-09-16
Thank you so much! 
Now  I have the updated version, yey!

---

### Post by ubuntu27 on 2005-09-16
[QUOTE=flygmaskin]This howto will show you how you can surf (or IM, or irc, or whatever) anonymously using the [tor](http://tor.eff.org) network. I'm using hoary, so I don't know if this will work on warty. Please give me some feedback on this.

**BEFORE YOU START**
Make sure you have enabled the universe repository.

**INSTALL TOR AND PRIVOXY**
```
$ sudo apt-get install tor privoxy
```

**CONFIGURE PRIVOXY**
Add the following line to */etc/privoxy/config*. You can put it at the top of the file if you want (Don't forget the last dot.)

[/QUOTE]

I have a problem. 

I cannot configure Privoxy. The config file in etc/privoxy/  is "Read-Only" 
How can I modify it? 

Thank you in advance.

---

### Post by Hikaru79 on 2005-09-24
[QUOTE=ubuntu27]I have a problem. 

I cannot configure Privoxy. The config file in etc/privoxy/  is "Read-Only" 
How can I modify it? 

Thank you in advance.[/QUOTE]
You shouldn't try to change its permissions settings. Simply edit it with 'sudo'. So, for example, ```
sudo gedit /etc/privoxy/config
```, then just enter your password. That's how you should deal with all read-only config files in Linux.

---

### Post by primeirocrime on 2005-10-01
I've got gaim to work by insisting in it to connect. Socket4. and socket5 .both complete the handshake. After a few atempts it gets easier.

---

### Post by davebgimp on 2005-10-18
I've used Tor and Privoxy for a while and really like it.

One thing I wanted to point out...

Going through the setup tutorial on the Tor website has you disable logging of the sites you visit. One thing it does not do is disable the logging of errors, as in sites that you can't reach, etc. If you use Tor and Privoxy you might want to get a secure deletion tool like [Wipe]("http://wipe.sourceforge.net/") and perhaps run a cron or manually destroy this log, located in /var/logs/errorfile.

---

### Post by GeorgePeppard on 2005-11-16
Although I can get Privoxy and Tor to work together no problem, I can get neither torify nor tsocks to work. Anything run using these scripts seems to connect directly to the internet without routing through Tor. Anyone else having this problem.

This is on Ubuntu 5.10

George

---

### Post by poptones on 2005-11-16
If you are using tor and your security concerns are sufficient you worry about self incrimination by data like that in /var/log leaking, you need to be using encryption rather than just trying to sweep over your tracks.

Privoxy is one of the first things I install. Don't hae much need for tor as it makes surfing on dialup way too slow.

---

### Post by gorillaman on 2005-11-17
According to the manual, addresses are scrubbed from the tor error log if the SafeLogging option is set to 1, which it is by default. I checked my TOR log at /var/log/tor/log, and indeed the addresses are scrubbed.

---

### Post by gorillaman on 2005-11-17
[QUOTE=GeorgePeppard]Although I can get Privoxy and Tor to work together no problem, I can get neither torify nor tsocks to work. [/QUOTE]

I have the same problem. I can get socat to work OK. Maybe you can use this. Tried everything to get torify working but no joy. Apparently it works by catching calls to various networking functions. Maybe there is something funny about the environment on Breezy that affects this. Dunno.

---

### Post by cdhotfire on 2005-11-25
Any ideas, on how to set tor to only get a certain range of ips?

really makes me mad that i have to go sudo /etc/init.d/tor restart to get new tor server.

:)

---

### Post by Reverend_Morgan on 2005-11-27
cdhotfire, when you run tor, you can specify the StrictExitNodes and ExitNodes options to specify a list of tor servers for the exit node. This is not ideal - the tor network should be left to choose the exit node itself unless you have specific requirments.

Perhaps better, if you run the latest testing release 0.1.1.9-alpha, you will find its performance is better than the stable release. You will probably have to compile and install this yourself.

---

### Post by jing10 on 2005-12-25
there is no need to install any program, you can use webbased phproxy like this.

[http://radiofarda.be]("http://http://radiofarda.be")

they are fast , free and need nothing to install on your pc. just go to that site and put the site adress in

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-25
Oh, the irony...

Belgium requires retention of user data for a period of a year (or more) and *anonymity* on telecommunications networks is expressly prohibited.

If you're going to use an "anonymous" proxy, make sure the proxy isn't in a nation with privacy laws even worse than your own.

---

### Post by Nimefurahi on 2005-12-27
&#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046;,

Talk about irony....

About two weeks ago I installed privoxy and tor as a curiosity. With both daemons running, I could in fact browse anonymously. Whoopee! But I have no real need to browse without my own identity, so I turned the option off in Firefox and just put it all behind me as a learning experience. I only wish I had then taken the time to remove tor and privoxy.

Three days ago I became alarmed to see quite a bit of unsolicited traffic through my box and immediately began to capture packets with Ethereal. It appears as if my box had suddenly become a proxy host itself through no purposeful manipulation or consent by me. Can you believe it! No, I did not have my browser running. There's no http or ftp server, no nfs, no ssh, no telnet, no inetd services running here... nothing out of the ordinary except for tor and privoxy.

I killed them. Then I studied the captured packets. Oy, do I feel violated! Someone out there in ether-land used me as a proxy in what appears to be through the courtesy of tor and/or privoxy. Yeah, talk about irony!

I've run clamscan through the entire file system and have found no published trojans. I believe I've survived my "learning experience" with no lasting damage. Tor? Privoxy? Yeah, they're powerful tools for an adventure I have no need of. You won't find them in my box. Not after last Saturday's "packets from Hell".

---

### Post by Cliff_Richard on 2005-12-28
Nimefurahi: sounds to me that you were running tor as an exit node. If you read how tor works, you will see what is happening. The default setting is not to act as a server - either you or your package creator must have set it to do this.

---

### Post by Nimefurahi on 2005-12-28
Thank you Cliff.

You made my day! Of all the events that have transpired in the course of this day, events at work and here at home, your response to my "advisory" post brings a warm smile to my heart. I am truly Nimefurahi, "He who is happy."

Is that by virtue of your advice in regard to Tor and its exit mode? No. Not exactly.

You made my day because I have the singular honor of welcoming you to the Ubuntu community. I see where your reply post to mine is your very first on this forum and I am honored to be the very first recipient of your posts. Thank you and welcome to Ubuntu and to our global "human" community. We are all one family here.

Now then, dear friend, as I look at my /etc/tor/torrc and /etc/tor/tor-tsocks.conf I don't see anything out of the ordinary. All appears to be as I originally opted for, the package defaults. There may be a problem more with Privoxy where I added "forward-socks4a / localhost:9050" to my /etc/privoxy/conf file. Other than that, I was running the package defaults.

Truth be told, I haven't a clue as to why I suddenly became vulnerable to exploitation by using Tor and Privoxy, but for me it really doesn't matter. I have no use of Tor and Privoxy. I just wanted to see what all the excitement was about browsing "anonymously" and it did seem to work according to its claims. What IS important to me is that I don't want to see anybody else made a target of exploitation as I was (however brief) by using Tor and/or Privoxy with default scripting and configuration. After 7 years in the Open Source Community, I'm afraid to admit that all don't necessarily play fair.

But back to the real substance of my reply to yours... I don't really care about anonymous browsing and such... I really don't care about Tor and Privoxy. What does matter to me is this... That I welcome you to Ubuntu! You fit well into our community! Thank you for your reply, your very first on this our forum.

- Nimefurahi

---

### Post by j-strap on 2005-12-28
Seems strange that your TOR node would be behaving like that. Have you checked that privoxy is not accepting external connections and that your firewall is working OK? Different builds of privoxy install the config in different places and it can be confusing as to which one is being used. Maybe you could remove/turn off privoxy and see if that stops the traffic. That would narrow down the source of the traffic. If it is TOR, you could stop it:

sudo /etc/init.d/tor stop

and then run manually like this

tor ClientOnly 1

to see if that is the problem.

---

### Post by Nimefurahi on 2005-12-28
Whoa!

After having welcomed Cliff to our community, I see where you, J-strap, are relatively new as well. Thank you for your reponse, and welcome aboard.

I was thinking that Tor and Privoxy were water under the bridge for me, that I have no real use for them, but the original and potential issue does remain. Maybe I should reinstall them as an exercise of... whatever... and see if I can repeat and then resolve the issue I experienced on Christmas Eve. It could be of value to others who really want or need to use Tor and/or Privoxy.

OK my friend. Maybe not just now, but I'll reinstall those utilities with careful consideration of your and Cliff's suggestions as an experiment.

Here's hoping I don't get hacked. (I've since "dropped" the IP that found its way through my firewall by way of Tor and/or Privoxy). I really don't need a proxy and I certainly don't want anyone to use me as such, but reenabling Tor and Privoxy could be a learning experience at my expense for others. I especially like the command "tor ClientOnly 1" as you suggested.

-Nimefurahi

---

### Post by j-strap on 2005-12-29
Nimefurahi: it would be nice to find out what the problem is. I think it is unlikely that either TOR or privoxy have been hacked - they both come from competent and benevolent development teams. More likely to be due to some kind of configuration issue. If you have time to investigate, would be nice to hear what you find.

---

### Post by Skytreker on 2005-12-31
Tor simply doesn't work for me.
I've red everything above very carefuly. Installed and uninstalled Tor and Privoxy several times and it keeps poping this messege when I try to use my browser:

[B]Connect failed

Your request for [http://www.space.com/](http://www.space.com/) could not be fulfilled, because the connection to [www.space.com](www.space.com) (127.0.0.1) could not be established.

This is often a temporary failure, so you might just try again. [/B]

This is NOT a temporary condition I'm asuring you.](*,)

---

### Post by j-strap on 2006-01-04
Skytrekker: is this error coming through as a 503 error from privoxy? If so, it means that either tor is not running or the privoxy config file does not have the correct forward command to route traffic to tor.

Have you used the ubuntu packaged versions of tor, privoxy, or have you compiled your own? Are you sure tor and privoxy are running?

Don't give up - tor and privoxy do work - it is probably an easily cured problem.

Things to check:

1. tor and privoxy daemons are both running
2. privoxy config file has correct forward command added
3. all protocols are directed to privoxy in the firefox config.

---

### Post by thought on 2006-01-05
I’m attempting to get tor to work but I’m getting an error when I try to run it.

Jan 05 00:38:16.707 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.
 Jan 05 00:38:16.722 [warn] /var/lib/tor is not owned by this UID (114). You must fix this to proceed.
 Jan 05 00:38:16.723 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
 Jan 05 00:38:16.724 [err] init_from_config(): Acting on config options left us in a broken state. Dying.
 

Anyone else get this or know how to solve it

Thanks

Thought

:???:

---

### Post by j-strap on 2006-01-05
'thought', it means that the /var/lib/tor directory has the wrong owner. Which version of tor have you installed - the ubuntu package? Did you have a different package of tor installed previously? It could be that an old tor package did not de-install properly and this directory got left behind with wrong owner/permissions.

If you fix this, tor should run OK.

There is a similar problem (with solution) in this thread:

[http://archives.seul.org/or/talk/Mar-2005/msg00161.html](http://archives.seul.org/or/talk/Mar-2005/msg00161.html)

---

### Post by Skytreker on 2006-01-07
[QUOTE=j-strap]
Don't give up - tor and privoxy do work - it is probably an easily cured problem.
[/QUOTE]

Yes they actualy do work now. Thanks **j-strap**. Tor v0.1.0.14  from the Hoary-Backport repositories did the trick. I guess that the 0.9... version was just too old to run properly. Silly me.:oops:

---

### Post by thought on 2006-01-13
i did everything that it said to do and even reinstalled tor and i get this again:

Setting up tor (0.1.0.15-1ubuntu1) ...
debian-tor uid check: ok
debian-tor homedir check: ok
 * Starting tor daemon (tor)... Jan 13 12:26:11.115 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.
Jan 13 12:26:11.162 [warn] /var/lib/tor is not owned by this UID (114). You must fix this to proceed.
Jan 13 12:26:11.163 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Jan 13 12:26:11.199 [err] init_from_config(): Acting on config options left us in a broken state. Dying.
                                                                         [fail]
invoke-rc.d: initscript tor, action "start" failed.

---

### Post by j-strap2 on 2006-01-14
'thought': try this command to set the permissions on that directory:

sudo chown debian-tor /var/lib/tor

Then try and start tor again. You can test it at the command line just by typing 'tor'.

---

### Post by Galoot on 2006-01-29
In light of the recent DOJ "request" of Google and other search engines, I've finally decided to give this a try. I've got to say, I'm impressed right out of my foil hat!

[www.whatismyip.com](www.whatismyip.com) shows that I'm currently surfing from somewhere in Brazil.
[www.GRC.com](www.GRC.com)'s "machine name" no longer identifies me as a Shaw Cable subscriber.
Graphically intensive sites are *almost* as fast to load, though there's a bit of lag.
As an added bonus, Privoxy is blocking more ads than my browser normally handles.

Excellent!

---

### Post by j-strap2 on 2006-01-29
Remember to turn java off for anonymous surfing.

---

### Post by beeldings on 2006-01-29
[QUOTE=negativ]Is there any way to speed this up?  I've got it working per the instructions in the post, but the result is that browsing is now sssslllloooowwww.  It makes me feel like I'm on dial-up.

Could there be something tweakable, or is this just the price you pay?[/QUOTE]

I found a way to slightly increase Tor's speed. In a terminal:

```

sudo nano /etc/tor/torrc

```

Look for this line:

```

AllowUnverifiedNodes middle,rendezvous

```

and replace it with:

```

#AllowUnverifiedNodes middle,rendezvous

```

This tweak helped speed up my overall Tor/Privoxy/Firefox performance, but YMMV.

---

### Post by Mustard on 2006-02-18
[QUOTE=Nimefurahi]Whoa!

After having welcomed Cliff to our community, I see where you, J-strap, are relatively new as well. Thank you for your reponse, and welcome aboard.

I was thinking that Tor and Privoxy were water under the bridge for me, that I have no real use for them, but the original and potential issue does remain. Maybe I should reinstall them as an exercise of... whatever... and see if I can repeat and then resolve the issue I experienced on Christmas Eve. It could be of value to others who really want or need to use Tor and/or Privoxy.

OK my friend. Maybe not just now, but I'll reinstall those utilities with careful consideration of your and Cliff's suggestions as an experiment.

Here's hoping I don't get hacked. (I've since "dropped" the IP that found its way through my firewall by way of Tor and/or Privoxy). I really don't need a proxy and I certainly don't want anyone to use me as such, but reenabling Tor and Privoxy could be a learning experience at my expense for others. I especially like the command "tor ClientOnly 1" as you suggested.

-Nimefurahi[/QUOTE]

Interesting to read of your experience. :)

I noticed something similar myself, but didn't spend much time to investigating what was happening.  All that mattered to me was that for some unknown reason, Tor was accessing the internet with quite significant traffic, when I wasnt browsing.  It didn't last long on my system after I noticed that.  I've been a privoxy user for many years though, so I still have privoxy installed.  I like the ad removal features of privoxy, and its handling of cookies, as well as other features.

---

### Post by mschievano on 2006-02-19
[QUOTE=j-strap2]'thought': try this command to set the permissions on that directory:

sudo chown debian-tor /var/lib/tor

Then try and start tor again. You can test it at the command line just by typing 'tor'.[/QUOTE]

I think the dapper release of ubuntu have some problem with tor and privoxy....

:-k 

i'm not able to make them run together...

I've start the to daemon (/etc/init.d ...) and then tor and privoxy (with /etc/privoxy/config as suffiss), but when I open the web page to config.privoxy.com, it write
```
Privoxy is not being used

The fact that you are reading this page shows that Privoxy was not used in the process of accessing it. Had the request been made through Privoxy, it would have been intercepted and you would be looking at Privoxy's web-based user interface now.
```

I'll do everything detailed up to my topic...:cry:

---

### Post by Frak on 2006-10-11
Good Howto, find it great,
P.S. off subject REALLY want to know
How (Lovechild) did you get burnt beans?

---

### Post by matthew on 2006-10-11
> **Frak said:**
> P.S. off subject REALLY want to know
How (Lovechild) did you get burnt beans?He can't answer you..."burnt beans" means the user got banned for violations of [forum guidelines]("http://www.ubuntuforums.org/index.php?page=policy").

---

### Post by loko on 2006-11-04
yes, nice howto, but:

can somebody now explain how to install the latest privoxy please.

i tried to install the new 3.0.5 beta and i stick at this point:

```
******************************************************************
 WARNING! WARNING! installing config files as root!
 It is strongly recommended to run privoxy as a non-root user,
 and to install the config files as that user and/or group!
 Please read INSTALL, and create a privoxy user and group!
*******************************************************************
make: *** [install] Fehler 1
```

i made a group and also user named privoxy, but then what?

---

### Post by jms830 on 2006-11-09
I found a similar version of this howto for edgy

[http://christer.homeip.net/index.php/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/](http://christer.homeip.net/index.php/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/)

Edit: step 2 of that tutorial should be 
**sudo gedit /etc/tor/torrc**
and step 4 should be
**sudo gedit /etc/privoxy/config**

---

### Post by squidward_tentacels on 2006-11-27
Ive been using Tor & Privoxy without difficulty on Dapper for some time now thanks to this great tutorial :). However recently I have encountered an item of great concern. Normally I view the active connections to tor using firestarter, and recently Ive begun seeing this on occasion;

[IMG]http://i59.photobucket.com/albums/g306/staceychandler/Screenshot.png[/IMG]

Curiosity arroused, I began to google "Gatechrasher Tor" the only information I could find on it stems from a french site, the translation is here; [http://translate.google.com/translate?hl=en&sl=fr&u=http://www.secuobs.com/plugs/10093.shtml&sa=X&oi=translate&resnum=9&ct=result&prev=/search%3Fq%3DGatecrasher%2Btor%26hl%3Den%26lr%3D%26sa%3DG](http://translate.google.com/translate?hl=en&sl=fr&u=http://www.secuobs.com/plugs/10093.shtml&sa=X&oi=translate&resnum=9&ct=result&prev=/search%3Fq%3DGatecrasher%2Btor%26hl%3Den%26lr%3D%26sa%3DG)

HERE IS A CUT AND PASTE OF THE SITE INFO: (ROUGH TRANSLATION)
____________________________________________________
ID
	
10093
Name
	
GateCrasher
Authors
	
This script is Copyright (C) 1999 Renaud Insanity
Category
	
Backdoors
Action
	
infos
Summary
	
Checks for the presence of GateCrasher
Description
	
GateCrasher is installed. This backdoor allows anyone to partially take the control of the remote system. Year attacker may uses it to steal your password gold prevent your from working properly. Solution: telnet to this host on port 6969, then type &#8220;gatecrasher&#8221;, without the quotes, and press Enter. Standard type &#8220;uninstall&#8221; and press Enter, it will Be uninstalled. Risk Factor: High
_________________________________________________________________
And the gist of it is this is a backdoor, allowing remote access and control of your system! Now based on the fact this is the only site I found pertaining to "Gatecrasher Tor" compounded with the ludicrous "removal" directions supplied, this sounds like a total scam to me. I would be willing to bet that following these sceptical "removal" directions,this server youve just telneted into would indeed attempt to install a Backdoor/ Rootkit on your system (probably would only work on windows,anyway?)

Any thoughts on this? Or maybe someone better versed in security would be willing to be willing to set-up a packet capture of the session between host and that sever in a sandboxed enviorment, and post the results?

Im almost certain it's a scam, but it would be nice to be sure....Maybe this thread should be moved to the security section, but this concerns all Tor users.

---

### Post by Nimefurahi on 2006-11-27
> **Mustard said:**
> Interesting to read of your experience. :)

I noticed something similar myself, but didn't spend much time to investigating what was happening.  All that mattered to me was that for some unknown reason, Tor was accessing the internet with quite significant traffic, when I wasnt browsing.  It didn't last long on my system after I noticed that.  I've been a privoxy user for many years though, so I still have privoxy installed.  I like the ad removal features of privoxy, and its handling of cookies, as well as other features.

My goodness dear brother! I just now (only 9 months later) have read your response to mine, and I see by your response that perhaps my mistrust of Tor was not necessarily unfounded. I quite simply don't trust it. Oh granted it is a powerful utility, much like a big hammer. It is able to best what it was intended to do. If exploitable and in the hands of the mischievous, it can do much damage. As for me, I don't want my fingers smashed.

In light of the most recent post about "Gatecrasher", Tor will not find its way onto my box.

Peace,
Nimefurahi

---

### Post by squidward_tentacels on 2006-11-27
Eh, After more research, it appears that firestarter flags any usage of port 6969 as Gatecrasher, despite the fact that many torrent programs use this port (Azureus, BitTorrent & others) I am running Azureus when this connect comes up......And from what Ive read Gatecrasher is predominantly a Windoze Trojan (Not to say that it couldn't be ported to Linux) Ive also researched Tor Vulnerabilities on BugTraq, and there is only a handful of published exploits, none of them mention Gatecrasher. I think Im going to monitor this for awhile and perhaps set up an ethereal capture of the port next time I notice a connection....But at this point Im really not too concerned.

---

### Post by WookieLuv0nMarz on 2006-12-31
Jesus i was sweating for about 3 hours there trying to find a good anti-spyware for ubuntu. i got the gatecrasher on port 6969 as well from torrents and i figured some one was trying my box.  well i hope it is just the torrents cause if spyware were to work thru wine or something i dont know if their is anything in the repos to snag spyware other than clamav.  Desktopsecurity wont work when i install from the repos either. i guess ill relax now and go to bed

---

### Post by EdThaSlayer on 2006-12-31
This guide seems to work for me on Ubuntu Edgy Eft. No problems at all. Very nice and simple way to get Tor up and running. Thanks.

---

### Post by shareMenaPeace on 2007-01-06
Installed it without problems, thanks.

Than i read on the official download ubuntu site this:
> Do not use the packages in ubuntu's universe. They are not maintained and most likely old and therefore miss out on stability and possibly security fixes.

For tor's stable version (for amd64,i386 and sparc):

  deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) <DISTRIBUTION> main
  deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) <DISTRIBUTION> main

where <DISTRIBUTION> should be replaced with either woody, sarge, etch, or sid, or - if you are using ubuntu - hoary, breezy, or dapper. 
[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian)

So i use edgy - to get the latest i need to put edgy in the source list?
And is it still not updated frequently?


Thanks

---

### Post by skep on 2007-01-06
> **shareMenaPeace said:**
> So i use edgy - to get the latest i need to put edgy in the source list?
And is it still not updated frequently?ThanksYes, but only the "deb" soure, not the "deb-src" (doesn't exist so far). Worked like a charm here some days ago..

---

### Post by shareMenaPeace on 2007-01-06
thx ```
Preparing to replace tor 0.1.1.23-1 (using .../tor_0.1.1.26-1~edgy.1_i386.deb) ...
Stopping tor daemon: tor.
Unpacking replacement tor ...
Setting up tor (0.1.1.26-1~edgy.1) ...
debian-tor uid check: ok
debian-tor homedir check: ok
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
Jan 06 15:05:31.733 [notice] Tor v0.1.1.26. This is experimental software. Do not rely on it for strong anonymity.
Jan 06 15:05:31.735 [notice] Initialized libevent version 1.1a using method epoll. Good.
Jan 06 15:05:31.735 [notice] connection_create_listener(): Opening Socks listener on 127.0.0.1:9050
done.

```

thx :P

---

### Post by Zelut on 2007-01-07
@JMS830 - thanks for pointing out my little mistake there.  I've updated the post accordingly.

---

### Post by frodon on 2007-01-09
Does tor and privoxy impact other internet apps like games, IRC, MSN, synaptic and so on. I'm interrested to use it for web browsing only but i'd like to keep other internet apps like they are now without changing anything in network configuration.

---

### Post by j-strap2 on 2007-01-09
The Ubuntu packages of Tor and Privoxy run as daemons on your system. Internet applications only proxy traffic through them if configured to do so - normal traffic is unaffected. That is, you can do just as you described.

Do not install the anon-proxy package, which is based on JAP (another anonymising proxy service). The Breezy version was badly packaged and mucked up networking for the whole system. I don't know whether this is fixed now, but Tor is superior anyway.

---

### Post by frodon on 2007-01-10
Thanks ;)

I updated this guide on the UDSF with details and screenshots for those interested :

[http://doc.gwos.org/index.php/Surf_anon](http://doc.gwos.org/index.php/Surf_anon)

---

### Post by gpierce on 2007-01-23
Thanks for the instructions. This is a wonderful tool for when I am feeling paranoid!

Greg

---

### Post by C-A on 2007-01-29
I recently installed tor and privoxy according to the [Surf Anon Document]("http://doc.gwos.org/index.php/Surf_anon"). Instead of using the torbutton I used the [Foxy Proxy Plug-In]("https://addons.mozilla.org/firefox/2464/"). I then ran the [Tor Detector]("http://lefkada.eecs.harvard.edu/cgi-bin/ipaddr.pl?tor=1") and the following was my result:

You are (probably) NOT using Tor.

"You connected to this site from **.**.**.***, hostname , which is NOT a valid Tor exit node. If you are attempting to use a Tor client, please refer to the Tor website and specifically the instructions for configuring your Tor client. If this is not the IP address from which you appear to connect when you disable your HTTP proxy, then it may be that the particular Tor node selected by your Tor client is multi-homed."

**.**.**.*** was the ip address which it id'd me as connecting from which is not my ip address.  

Should I assume that all is well (tor is working) and my tor client is multi-homed?

---

### Post by Surgeon General on 2007-02-08
how does one test if tor and privoxy is working right? i've clicked on a link that somehow have changed to [http://xx.xx.xx.xx](http://xx.xx.xx.xx) instead of [http://www.abc.def](http://www.abc.def) and it was blocked (?) by my isp. also installing the tor and privoxy package for edgy shows that one should not rely on it 100% for surfing anonymously. is there no maintenainer for tor and privoxy in ubuntu?

---

### Post by arijarot on 2007-06-02
a curious thing happened after I followed the instructions, my default google page changed from .com to [http://www.google.se/](http://www.google.se/) which is an unknown language to me... 
does anyone know what happened here or why this happened?

also, I did I "shields up!" test before and after. before, without tor and privoxy, i got all stealth... after I got all closed instead, which is worse as far as I understand... my ip and all that was different ... is it my machine it's scanning or? i don't get it, cause my firewall settings haven't changed...
----
edit: I don't know if this is just me or not, but this is what I got after doing an auditmypc ```
Type  	Port  	Services, Programs and Trojans that are commonly found to be running on this port.
tcp  	22222  	Trojans or Viruses known to use this port are: Donald Dick.   Donald Dick.   Prosiak.   Ruler.   RUX The TIc.K.    

The following ports have been reported open! I've attempted to give you information about what software or viruses might be listening on your open ports. If you are a typical home computer user and did not intentionally install a service, then you should not find any open ports.
``` 

I'd rather a "secure" system than an anon one, imo... UNless someone can explain this otherwise.
----
edit: is there another, more secure, way?

---

### Post by Nimefurahi on 2007-06-02
Your anonymity is being served by a Swedish IP address. When you visit Google with your Tor/Privoxy rendered IP address, you are thought to be Swedish and Google responds appropriately.

---

### Post by arijarot on 2007-06-02
ok, make sense, I'm swedish now;)

but what about all the security issues I found?

edit: see post [#76]("http://ubuntuforums.org/showpost.php?p=2770486&postcount=76") above...

---

### Post by kilou on 2007-06-07
2nd time I try Tor with FF but either it is way too slow or pages just simply don't load due to timeout :(

---

### Post by Pugwash on 2007-06-16
Just a question, is it safe to use the tor and privoxy packages in the ubuntu repository? Would they not be outdated?

---

### Post by frodon on 2007-06-16
> **Pugwash said:**
> Just a question, is it safe to use the tor and privoxy packages in the ubuntu repository? Would they not be outdated?Why do you think they would be ?
If you use the latest version of ubuntu (feisty) the tor version in the repositories is the 1.1.26 and actual version of tor is the 1.2.14., so yes there's a more recent version now but i don't think we can call the 1.1.26 version outdated.

changelog here :
[http://tor.eff.org/download.html.en](http://tor.eff.org/download.html.en)

Anyway you can add the tor repository if you want the latest version (there's a repository for dapper, edgy and feisty) :
[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian)

---

### Post by Pugwash on 2007-06-16
> **frodon said:**
> Why do you think they would be ?
If you use the latest version of ubuntu (feisty) the tor version in the repositories is the 1.1.26 and actual version of tor is the 1.2.14., so yes there's a more recent version now but i don't think we can call the 1.1.26 version outdated.

changelog here :
[http://tor.eff.org/download.html.en](http://tor.eff.org/download.html.en)

Anyway you add the tor repository if you want the latest version (there's a repository for dapper, edgy and feisty) :
[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian)

Sorry, that's me being paranoid again. Thanks for the links and the information. I've upgrade to latest version using the tor repos. 

Thanks

---

### Post by frodon on 2007-06-16
> **Pugwash said:**
> Sorry, that's me being paranoid again. Thanks for the links and the information. I've upgrade to latest version using the tor repos. 

ThanksI did as well, i think might be as paranoid as you :)

---

### Post by tech4web on 2007-08-08
hi , can anyone send to my email this software ! 
my country don't let me to go to this site!!!

[email]tech4web@gmail.com[/email]

i'm using ubuntu 7.04  .
------------[SOLVED]       AdrianP send it to my email .

---

### Post by apetresc on 2007-08-08
> **tech4web said:**
> hi , can anyone send to my email this software ! 
my country don't let me to go to this site!!!

[email]tech4web@gmail.com[/email]

i'm using ubuntu 7.04  .

Which, Tor? Just ```
sudo apt-get install tor
``` Unless your country blocks access to the Ubuntu repos, that will work.

---

### Post by tech4web on 2007-08-08
NO, Not Solved! 
$sudo apt-get install tor
or
$sudo apt-get install tor privoxy

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tor has no installation candidate


this is my error..
but i can't connect with my computer with high speed connection , so where i want to get it have windows!! installed  so i need it by email to download!
just send me please , i can't get it by repository..

[email]tech4web@gmail.com[/email]

---

### Post by apetresc on 2007-08-08
> **tech4web said:**
> 
but i can't connect with my computer with high speed connection , so where i want to get it have windows!! installed  so i need it by email to download!
just send me please , i can't get it by repository..

[email]tech4web@gmail.com[/email]
Okay, okay, I'll e-mail it to you. Do you want the Windows version, then?

---

### Post by tech4web on 2007-08-08
No,Never Windows.....!

Altough in my country there is no CopyWrite!! I don't have any m$ software on my computer..

ok,thanks for your help. i want it for ubuntu  feisty fawn 7.04.

---

### Post by apetresc on 2007-08-08
Okay, the package has been sent to your e-mail. Make sure you have tsocks installed, it is a needed prerequisite for this package.

To install it, put the packages in the /var/cache/apt/archives/ and run dpkg -i on both of them. First tsocks, then tor.

Though really your easiest recourse would have been to add the Universe repository and install it yourself through apt.

---

### Post by b3y0nd on 2007-12-06
Thought i'd dig up this old thread in hopes of someone else with Ubuntu Ultimate Edition 1.6 "Gnarley Gnome" who has successfully installed Tor and Privoxy. 

Anyne know how I could go about getting it up and running under by distro?



beyond

---

### Post by keyboardslave on 2008-01-18
Great job mate,

Simple and to the point, and it works

im using feisty fawn and it works fine, thanks for this. Maybe next time try to explain in more detail.

Kind regards,

---

### Post by Chest2Tank on 2008-01-20
Does anyone have any updated information on this?  I use TOR with XP, and I can't get it to work with gusty.

---

### Post by michaelzap on 2008-02-13
> **Chest2Tank said:**
> Does anyone have any updated information on this?  I use TOR with XP, and I can't get it to work with gusty.

Indeed it seems to be broken in Gutsy. Anyone have a proper fix for it? I've added the latest tor repos from [here]("http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian") but after reinstalling tor, stopping it, and starting it again it still doesn't work.

---

### Post by michaelzap on 2008-02-13
Actually, it seems as if I just needed to restart my system. Tor is working now! I think the key is just adding the extra repos from the link I posted last night.

---

### Post by Taris-Quickpaw on 2008-02-18
I'm using Ubuntu 7.10 and downloaded the tor and privoxy packages via the Synaptic Package Manager, and the Tor Button for firefox via the Firefox add-on page.  I've checked my firefox settings and such, it says it's pointing to 8118, but when i try to test it using [http://torcheck.xenobite.eu/](http://torcheck.xenobite.eu/)  to no avail.  Any idea what i could be doing wrong?

---

### Post by michaelzap on 2008-02-18
I had to use the packages from the link I pasted two posts above yours to get tor to work (not the version in the gutsy repos).

---

### Post by Taris-Quickpaw on 2008-02-18
i assume those are supposed to be commands you type into the terminal, but it tells me 'bash: deb: command not found'   I'm not good with the terminal or coding, so i'm stuck once again :(

---

### Post by michaelzap on 2008-02-18
Those aren't commands; they're software sources. So you need to add them to your Software Sources list (etc/apt/sources.list). The easiest way to do this is via the GUI in Applications > System > Software Sources (also accessible via the Synaptic Package Manager).

I would uninstall tor before you add these sources (use Synaptic or whatever you prefer). The add them and reinstall tor. You should now have the later version from the new source.

For whatever reason tor/privoxy didn't work for me until I restarted my machine. I could probably have just started both services from the command line and made them work, but I didn't know that then. Restarting is easy, and should do the trick.

---

### Post by Taris-Quickpaw on 2008-02-18
well, i tried that, add it to sources, removed old tor and privoxy, turned off all other sources, reloaded the updater, and told it to grab those again, rebooted.  Still doesnt work.

Just to be sure, what version of Tor and Privoxy should i have?  it's telling me that it has version 0.1.2.17-1 of TOR and 3.0.6-3 of Privoxy.  i ask because i checked and i think the latest version TOR is 0.1.2.19 ?

---

### Post by michaelzap on 2008-02-18
> **Taris-Quickpaw said:**
> well, i tried that, add it to sources, removed old tor and privoxy, turned off all other sources, reloaded the updater, and told it to grab those again, rebooted.  Still doesnt work.

Just to be sure, what version of Tor and Privoxy should i have?  it's telling me that it has version 0.1.2.17-1 of TOR and 3.0.6-3 of Privoxy.  i ask because i checked and i think the latest version TOR is 0.1.2.19 ?

The latest version of tor is 0.1.2.19-1, and that's what I'm using and it's working. So perhaps you didn't add those software sources properly or they were down. Did you refresh the application list after you added them? Did you see any errors when you did?

---

### Post by Taris-Quickpaw on 2008-02-18
yep, that was the problem, i put in a typo in the list, so now it works and i have the current version.  it gave me an error about no public key or signature or something, but i have the latest version.  Unfortunately, that doesnt seem to have done the trick.  I don't know where to take it from here.  The probably is probably me and my coding illiteracy, but thanks for the help! :)

---

### Post by michaelzap on 2008-02-18
> **Taris-Quickpaw said:**
> yep, that was the problem, i put in a typo in the list, so now it works and i have the current version.  it gave me an error about no public key or signature or something, but i have the latest version.  Unfortunately, that doesnt seem to have done the trick.  I don't know where to take it from here.  The probably is probably me and my coding illiteracy, but thanks for the help! :)

Have you restarted since you installed the latest version? I use the Tor button for Firefox, which starts/stops the service. Are you using it or something else to start up Tor?

---

### Post by Taris-Quickpaw on 2008-02-18
yea, i rebooted and i have the tor button installed.  unless a quick fix can be found ,i might have to put this off for a while, i need to focus my time on other endevors, like my art projects :P  Thanks though :)

---

### Post by michaelzap on 2008-02-18
> **Taris-Quickpaw said:**
> yea, i rebooted and i have the tor button installed.  unless a quick fix can be found ,i might have to put this off for a while, i need to focus my time on other endevors, like my art projects :P  Thanks though :)

Oh well. Maybe it will be updated soon and fix your problems. In the meantime, go make art.

---

### Post by waterspider on 2008-03-28
please how can i get to the /etc/privoxy/config file?

---

### Post by SINZAR on 2008-04-11
Hi guys, I'm trying to set up tor + privoxy on my ubuntu machine. I've done it on my windows machine no problems but it doesn't seem to be working on this one. Keep in mind, my windows machine is not running tor + privoxy at the same time.

I'm looking to set up a tor/privoxy server for my windows machines using ubuntu. I followed the instructions, set it up, says its running but I can't connect to it through windows. I tried changing localhost to the IP of the ubuntu machine but that didn't work.

Just to check, I tested it out with firefox on ubuntu to see if it was working, I put in the settings (having changed the config back to localhost and putting localhost in the proper firefox field) and went to whatismyip.com but it was showing my actual IP, not the one supplied from the tor network. I've configured my router for the ports and it shows that privoxy and tor are listening on ubuntu.

Any ideas?

---

### Post by zer010 on 2009-07-24
I am running Jaunty, and installed Tor and Privoxy. Everything seemed to work well enough, until I would go to the "test" sites.  They always said "You don't seem to be running Tor".  I had rechecked all my settings/confgs, and found nothing out of the ordinary(same as given instr).  Is there something I'm missing? I have since uninstalled them, but was wanting to try again... if I know everything will work right.  Any suggestions will be appreciated!:)

---


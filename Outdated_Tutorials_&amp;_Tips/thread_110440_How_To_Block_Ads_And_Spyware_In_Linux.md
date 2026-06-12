---
title: "How To Block Ads And Spyware In Linux"
date: 2005-12-30
forum: Outdated Tutorials &amp; Tips
---

### Post by anil_robo on 2005-12-30
Hi all! I'm seeing heated discussions on spyware for linux, and I think it's a well-suited time to post a useful tutorial here. By following these simple steps, you will be able to block most advertisement banners on webpages, virus-infected websites, spyware-infected websites, and other insecure websites.
 
Theory: In Linux, the file /etc/hosts contains information about how the system interprets website domain names. If you want to block a website, just make it point to 0.0.0.0 (e.g. [www.site-to-be-blocked.com]("http://www.site-to-be-blocked.com") will point to 0.0.0.0 => The site won't open at all!).
 
How to: First, you need a good hosts file to install. The one I use is [here.]("http://www.mvps.org/winhelp2002/hosts.txt")
Click on that link right now, and the file will open in a browser or a text editor. Select all the text in the file, and copy it.
 
Now open a terminal, and type ```
sudo gedit /etc/hosts
```. Your hosts file should open up. This file may already have some entries in it, which we're not going to change. Go to the end of the file, and "paste" the contents of the hosts file you had copied to the clipboard earlier.
Save the hosts file, and it should be active. Just to be more sure, you might want to logout and relog to Ubuntu.
 
Now when you start browsing, you'll not see any ads, rather they'll simply fail to load! Here's a screenshot when I try to access an advertisement site ([www.doubleclick.net):]("http://www.doubleclick.net%29:")
[ATTACH]4963[/ATTACH]
 
A lot of people have recommended using adblock extension for Firefox instead of this hosts-file blocking method. Adblock protects you against spyware/adware when you're surfing the internet through Firefox. But what about the other malicious things you can get through other programs? For example, in your email which you view through evolution? Since evolution accesses internet directly, I'd still go for blocking all the parasites through the hosts file.
 

This method does not work if you are using a proxy.

The host file structure changed with Ubuntu 8.10, so I doubt the same hosts file will work for Intrepid.

---

### Post by Ali_Baba on 2005-12-31
Sounds good,thanks for Howto. I have to try this :D

---

### Post by Norberg on 2005-12-31
Very nice How To

---

### Post by guice on 2005-12-31
You're using Firefox. Just install AdBlock. ;)
There's even a Filter Updater extension for AdBlock, too, that'll auto-update when the list changes.

---

### Post by evs on 2005-12-31
[QUOTE=guice]You're using Firefox. Just install AdBlock. ;)
There's even a Filter Updater extension for AdBlock, too, that'll auto-update when the list changes.[/QUOTE]

AdBlock is probably my favorite extension, along with the updater.  I've been using Konqueror a lot more lately, too, so I exported the blocked sites list from Firefox to a file, and imported that into Konqueror's built-in adblock feature.  It makes surfing the web so much more enjoyable.

---

### Post by limit223 on 2005-12-31
Related to this subject,
If anyone noticed in firefox when you do about:config in browser address, filter: dns -- network.dns*=.doubleclick.net, change the value to true! (stay out of their dns)

---

### Post by earobinson on 2005-12-31
this could be used as a nanny lock to no?

---

### Post by limit223 on 2005-12-31
well..it said that was implemented for speed but if you choose any other dns: mozilla.org , google would return no search.... True value works fine.

---

### Post by Orunitia on 2005-12-31
This just seemed to slow a lot of sites down for me. I took it back out of my host file and everything seemed to speed up again.

---

### Post by Gandalf on 2005-12-31
its normal to slow down sites that use one of the addresses u blocked, since your browser will keep trying a bit to connect to localhost untill it time out!!

---

### Post by peanut butter on 2005-12-31
i could also be because it has to look through the hosts file every time it loads a webpage.

---

### Post by earobinson on 2005-12-31
that would be a very short amount of time, it takes mirco seconds to read a file, want proof time cat <my file> its super fast

```
earobinson@null:~/Desktop/download$ time cat UbuntuCodeofConduct-1.0.txt
= Ubuntu Code of Conduct =

This Code of Conduct covers your behaviour as a member of the Ubuntu
Community, in any forum, mailing list, wiki, web site, IRC channel,
install-fest, public meeting or private correspondence. The Ubuntu
Community Council will arbitrate in any dispute over the conduct of a
member of the community.

      '''Be considerate.''' Your work will be used by other people,
      and you in turn will depend on the work of others. Any decision
      you take will affect users and colleagues, and we expect you to
      take those consequences into account when making decisions. For
      example, when we are in a feature freeze, please don't upload
      dramatically new versions of critical system software, as other
      people will be testing the frozen system and not be expecting
      big changes.

      '''Be respectful.''' The Ubuntu community and its members treat
      one another with respect. Everyone can make a valuable
      contribution to Ubuntu. We may not always agree, but
      disagreement it no excuse for poor behaviour and poor
      manners. We might all experience some frustration now and then,
      but we cannot allow that frustration to turn into a personal
      attack. It's important to remember that a community where people
      feel uncomfortable or threatened is not a productive one. We
      expect members of the Ubuntu community to be respectful when
      dealing with other contributors as well as with people outside
      the Ubuntu project, and with users of Ubuntu.

      '''Be collaborative.''' Ubuntu and Free Software are about
      collaboration and working together. Collaboration reduces
      redundancy of work done in the Free Software world, and improves
      the quality of the software produced. You should aim to
      collaborate with other Ubuntu maintainers, as well as with the
      upstream community that is interested in the work you do. Your
      work should be done transparently and patches from Ubuntu should
      be given back to the community when they are made, not just when
      the distribution releases. If you wish to work on new code for
      existing upstream projects, at least keep those projects
      informed of your ideas and progress. It may not be possible to
      get consensus from upstream or even from your colleagues about
      the correct implementation of an idea, so don't feel obliged to
      have that agreement before you begin, but at least keep the
      outside world informed of your work, and publish your work in a
      way that allows outsiders to test, discuss and contribute to
      your efforts.

      '''When you disagree,''' consult others. Disagreements, both
      political and technical, happen all the time and the Ubuntu
      community is no exception. The important goal is not to avoid
      disagreements or differing views but to resolve them
      constructively. You should turn to the community and to the
      community process to seek advice and to resolve
      disagreements. We have the Technical Board and the Community
      Council, both of which will help to decide the right course for
      Ubuntu. There are also several Project Teams and Team Leaders,
      who may be able to help you figure out which direction will be
      most acceptable. If you really want to go a different way, then
      we encourage you to make a derivative distribution or
      alternative set of packages available using the Ubuntu Package
      Management framework, so that the community can try out your
      changes and ideas for itself and contribute to the discussion.

      '''When you are unsure,''' ask for help. Nobody knows
      everything, and nobody is expected to be perfect in the Ubuntu
      community (except of course the SABDFL). Asking questions avoids
      many problems down the road, and so questions are
      encouraged. Those who are asked should be responsive and
      helpful. However, when asking a question, care must be taken to
      do so in an appropriate forum. Off-topic questions, such as
      requests for help on a development mailing list, detract from
      productive discussion.

      '''Step down considerately.''' Developers on every project come
      and go and Ubuntu is no different. When you leave or disengage
      from the project, in whole or in part, we ask that you do so in
      a way that minimises disruption to the project. This means you
      should tell people you are leaving and take the proper steps to
      ensure that others can pick up where you leave off.

real    0m0.077s
user    0m0.000s
sys     0m0.000s
```

note that also includes printing the text which takes longer

---

### Post by peanut butter on 2005-12-31
sorry i dident think of that but sometimes weird stuff can slow programs down

---

### Post by limit223 on 2005-12-31
I'm not an expert in network and if someone knows more could correct me..but following this how-to: copy and paste the whole host.txt would erase your own fixed ip's set by your network system card('s) (In my case I've got a shared fixed connection over 2 eth cards over pppoe which have 2 ip's set on /etc/hosts file). Otherwise my speed on sites seems unchanged with all blocked sites.

127.0.0.1 localhost.localdomain localhost ubuntu
my.first.static.ip ubuntu.localdomain ubuntu
my.second.static.ip ubuntu.localdomain
#start of lines added by WinHelp2002
# [Misc A - Z]
127.0.0.1  phpadsnew.abac.com
127.0.0.1  a.abnad.net
127.0.0.1  b.abnad.net
..........................................................................

---

### Post by Refrozen on 2005-12-31
Instead of using localhost (127.0.0.1) in your [hosts file](http://manlib.com/man/412), use 0.0.0.0, it should remove that loopback effect and alleviate the timeout-lag.

---

### Post by forbmj on 2006-01-01
Hey, thanks for your work. But I still can connect some of these sites, for example: [www.visitfind.net](www.visitfind.net)

Does it really work? 

forbmj


[QUOTE=anil_robo]Hi all! I'm seeing heated discussions on spyware for linux, and I think it's a well-suited time to post a useful tutorial here. 
By following these simple steps, you will be able to block most advertisement banners on webpages, virus-infected websites, spyware-infected websites, and other insecure websites.

Theory: In Linux, the file /etc/hosts contains information about how the system interprets website domain names. If you want to block a website, just make it point to your local address (e.g. [www.site-to-be-blocked.com]("http://www.site-to-be-blocked.com") will point to 127.0.0.1 => The site won't open at all!).

How to: First, you need a good hosts file to install. The one I use is [here.]("http://www.mvps.org/winhelp2002/hosts.txt")
Click on that link right now, and the file will open in a browser or a text editor. Select all the text in the file, and copy it.

Now open a terminal, and type ```
sudo gedit /etc/hosts
```. Your hosts file should open up. This file may already have some entries in it, which we're not going to change. Go to the end of the file, and "paste" the contents of the hosts file you had copied to the clipboard earlier.
Save the hosts file, close it, and reboot your computer.

Now when you start browsing, you'll not see any ads, rather they'll simply fail to load! Here's a screenshot when I try to access an advertisement site ([www.doubleclick.net):]("http://www.doubleclick.net%29:")
[ATTACH]4963[/ATTACH][/QUOTE]

---

### Post by anil_robo on 2006-01-01
[quote=forbmj]Hey, thanks for your work. But I still can connect some of these sites, for example: [www.visitfind.net]("http://www.visitfind.net")

Does it really work? 

forbmj[/quote] 
Proof: Click on the thumbnail: 
[ATTACH]5010[/ATTACH]

Did you follow the directions carefully?

---

### Post by forbmj on 2006-01-01
sorry, I made a mistake and used the proxy when viewing it.

Thanks a lot.

[QUOTE=anil_robo]Proof: Click on the thumbnail: 
[ATTACH]5010[/ATTACH]

Did you follow the directions carefully?[/QUOTE]

---

### Post by Mustard on 2006-01-01
[QUOTE=forbmj]sorry, I made a mistake and used the proxy when viewing it.

Thanks a lot.[/QUOTE]

I was doing the same thing.  I followed all the instructions and was not getting any results.  It was due to me having firefox set up to use my ISP proxy. :)

---

### Post by ibanez88 on 2006-01-01
Thanks for this!

---

### Post by mrsad on 2006-01-02
just leave your /etc/hosts file alone. it is a file owned by root and casual users should not need to fiddle around with it.
use firefox with adblock and the adblock-filter-updater for the ultimate browsing expirience ;)

if you must, you can also install a proxy server (squid, see a fast guide here - [http://mkeadle.org/index.php?p=14](http://mkeadle.org/index.php?p=14)) or (if you are bored to hell) use linux build-in firewall to block unwanted connections to hosts.

---

### Post by anil_robo on 2006-01-02
[quote=guice]You're using Firefox. Just install AdBlock. ;)
There's even a Filter Updater extension for AdBlock, too, that'll auto-update when the list changes.[/quote]
 
Adblock protects you against spyware/adware when you're surfing the internet through Firefox. But what about the other malicious things you can get through other programs? For example, in your email which you view through evolution? Since evolution accesses internet directly, I'd still go for blocking all the parasites through the hosts file.

---

### Post by anil_robo on 2006-01-02
In addition, I'd like to know how can I change the default error page in Firefox. I'd like to replace the big error message by a little one so that the page structure in firefox after ad-blocking looks acceptable. Thanks

---

### Post by anil_robo on 2006-01-02
[quote=Mustard]I was doing the same thing. I followed all the instructions and was not getting any results. It was due to me having firefox set up to use my ISP proxy. :)[/quote]
 
I appreciate that you found out the solution yourself and also shared it with us. Unfortunately I'm a not a technical superperson and I have never used proxies to access internet before. But I would really appreciate if you could tell me how to set up hosts blocking with proxies, if it's possible. I'd like to update the how-to with this as well. Thanks. :)

---

### Post by anil_robo on 2006-01-02
[quote=Refrozen]Instead of using localhost (127.0.0.1) in your [hosts file]("http://manlib.com/man/412"), use 0.0.0.0, it should remove that loopback effect and alleviate the timeout-lag.[/quote]
 
Thanks Refrozen! I'm in office right now, and when I get home, I'll test this trick on my Ubuntu laptop and if all goes well, I'll update the how-to accordingly. Thanks a lot! :)

---

### Post by Mustard on 2006-01-02
[QUOTE=anil_robo]I appreciate that you found out the solution yourself and also shared it with us. Unfortunately I'm a not a technical superperson and I have never used proxies to access internet before. But I would really appreciate if you could tell me how to set up hosts blocking with proxies, if it's possible. I'd like to update the how-to with this as well. Thanks. :)[/QUOTE]

I haven't had any success at all with getting it to work with my proxy.  I've gone through the settings and fiddled around a bit, but no luck yet.  I'm keen to see how it goes with the 0.0.0.0 settings rather than the 127.0.0.1 setting.  I just didn't want to be the first one to try it. :)

---

### Post by oimon on 2006-01-03
Spyware? Has anyone actually ever been infected by Spyware/Malware using linux? 

The lack of virus/malware is a major reason why many people make the switch from Windows to (K)Ubuntu and other flavours of Linux

---

### Post by linkunderscore on 2006-01-03
[QUOTE=oimon]Spyware? Has anyone actually ever been infected by Spyware/Malware using linux? 

The lack of virus/malware is a major reason why many people make the switch from Windows to (K)Ubuntu and other flavours of Linux[/QUOTE]

Im under the impression you can not get spyware or malware running *nix. I use to get a pop-up every now and then running Fx 1.0.7 but since I upgraded to 1.5 I haven't had even a single popup. 

Maybe someone more experienced and knowledgable could comment on this issue.

---

### Post by Ptero-4 on 2006-01-03
I'm going to put it in both of my *nices in my eMac.

---

### Post by bikeboy on 2006-01-04
[QUOTE=anil_robo]In addition, I'd like to know how can I change the default error page in Firefox. I'd like to replace the big error message by a little one so that the page structure in firefox after ad-blocking looks acceptable. Thanks[/QUOTE]
The only thing I can see about changing error messages in Firefox is the xul error page option. Not sure if that will do what you want but you can try disabling it through about:config.

---

### Post by tofudrifter on 2006-01-09
changing 127.0.0.1 to 0.0.0.0 in the hosts file does little to stop Opera from ](*,) freezing up trying to download the ads to the detriment of all other surfing in the browser, it won't even continue loading the page.  Firefox seems to work alright though.

---

### Post by leech on 2006-01-10
I've got to add my little comment here....

1) You can do this same trick on Windows, in fact it's a lot better on Windows because that's where you have to worry about the spyware/malware crap.  The file is in the same format and is located in c:\windows\system32\drivers\etc

2) This really isn't required in linux, a lot of times the pop-ups will still pop up (if there is one in the first place Firefox isusually really good at blocking most of those.

3) Adblock is better, because as someone else had said, hey want to change the screen that is shown because if you're reading some article that links to ads, you're going to have a weird text box there.  With Adblock it removes the whole box from the page, making it a lot easier to read the article

Leech

---

### Post by sl0play on 2006-01-17
Sorry to drag this thread back up, but [here]("http://www.mvps.org/winhelp2002/hosts.txt") is a good pre-compiled hosts file with thousands of sources blocked.  Just copy and paste.

---

### Post by FiggyG on 2006-01-20
I get my hosts file from [this site.]("http://www.everythingisnt.com/hosts.html") For those dual-booting, the Windows installer is quite handy ;)

Forgot this tid-bit, instead of just putting the linked hosts file in your /etc directory, you'll need to open your existing and copy the existing information into the new hosts file, or the other way around. If you just do a straight copy, you may end up with some issues like, sudo not working.

---

### Post by Mustard on 2006-01-20
[QUOTE=FiggyG]I get my hosts file from [this site.]("http://www.everythingisnt.com/hosts.html") For those dual-booting, the Windows installer is quite handy ;)

Forgot this tid-bit, instead of just putting the linked hosts file in your /etc directory, you'll need to open your existing and copy the existing information into the new hosts file, or the other way around. If you just do a straight copy, you may end up with some issues like, sudo not working.[/QUOTE]

I emailed 'Mike' about his instructions. :)

Hopefully he will edit that page to give the correct instructions for appending to the /etc/hosts file rather than 'saving this file to our /etc directory'.

---

### Post by Heliode on 2006-01-20
[QUOTE=anil_robo]

Save the hosts file, close it, and reboot your computer.
 
[/QUOTE]

You don't need to reboot. just do
```

/etc/init.d/networking restart

```

And it should work.

EDIT:

Also, since I have Apache installed on my localhost, it displays whatever page I have running there. On my laptop I just created a page that says "Blocked!". This should fix the problem of sites slowing down (since localhost will open instantly) but I'd agree that installing Apache for it is a bit overkill.

---

### Post by househead on 2006-01-20
[QUOTE=Heliode]You don't need to reboot. just do
```

/etc/init.d/networking restart

```

And it should work.
[/QUOTE]

You shouldn't even have to do that.

---

### Post by Heliode on 2006-01-20
[QUOTE=househead]You shouldn't even have to do that.[/QUOTE]

You might be right with that... I noticed on another machine that restarting FF was enough.

When will people learn that rebooting a machine to apply something is a Windows CrazyThing(tm) 
(See the howto)

---

### Post by Casey on 2006-01-20
In most cases hitting localhost (127.0.0.1 ) in the hosts file is going to slow you down as it waits for things to load until the timeout time is hit.  Using 0.0.0.0 as others have said should aleviate this (as it should immediately fail).

All of the hosts files people have posted are using 127.0.0.1 so this is probably why you're seeing a slow browsing experience.

Personally, mucking with the hosts file is more trouble than it's worth for me, but I think that those complaining of slow browsing could fix it by making this change.

---

### Post by FiggyG on 2006-01-20
[QUOTE=Casey]In most cases hitting localhost (127.0.0.1 ) in the hosts file is going to slow you down as it waits for things to load until the timeout time is hit.  Using 0.0.0.0 as others have said should aleviate this (as it should immediately fail).[/QUOTE]
Opening the downloaded hosts file and doing a Replace 127.0.0.1 with 0.0.0.0 was very easy in Kwrite. I'll let ya know if it's any faster :)

---

### Post by BLTicklemonster on 2006-01-30
[QUOTE=limit223]Related to this subject,
If anyone noticed in firefox when you do about:config in browser address, filter: dns -- network.dns*=.doubleclick.net, change the value to true! (stay out of their dns)[/QUOTE]
What? I see nothing like that. Be more specific for the token asshat please? :)

---

### Post by DigitalDuality on 2006-01-30
Great how-to :)  I'll try it out 

As of late i've been using Adblock, the updating Filter set, No Script and Site Advisor to block it out.

---

### Post by Orunitia on 2006-01-31
Changing it from 127.0.0.1 to 0.0.0.0 did nothing for me on Opera. Though I realized Konqueror can use adblock filters so I'm using that as my main browser now.

---

### Post by tomski on 2006-01-31
great idea & how-to for stopping unwanted sites/popups/popunders/ads but does this mean that we are wrong in thinking that the only way you can get:

virus
spyware
malware
adware
or any wares

 in *nix is to compile/install them yourself or if your evil: gain access, acquire root, then compile/install ??? has this been forgotten because this is why *nix was is powerful (also the fundamental difference between win & *nix)
sorry but i think this needs to be clarified before people get confused

more info :
[The Register]("http://www.theregister.co.uk/2004/10/12/spyware/")


or 
you could just get 2 pc's put ubuntu on one then put windows(straight off the disk, no extra software) on the other & start a stopwatch &    wait to see what gets attacked first but im sure you all know the answer!!!!

---

### Post by Ptero-4 on 2006-02-01
I added the hosts file a few weeks ago. I did some mods to it though, I added M$ and hotmail to the blocked sites (no M$ for me).

---

### Post by BoyOfDestiny on 2006-02-02
I recommend privoxy, I've been using it for years now. It's gpl and browser agnostic too... 

Makes it easy to block ads, and get rid of various web annoyances (spoof referer tag, etc etc). Anyway, it's in the ubuntu repos, you can visit the website to learn more.

[www.privoxy.org](www.privoxy.org)

---

### Post by limit223 on 2006-02-03
[QUOTE=BLTicklemonster]What? I see nothing like that. Be more specific for the token asshat please? :)[/QUOTE]


Is this picture specific enough for you?

---

### Post by louis_nichols on 2006-02-03
The default "page not found" in firefox is a html file somewhere in the installation directory or the user settings directory. i'm sorry, but I'm not running ff 1.5 right now, so I can't look for it. But it's there. Only thing is that, if you replace it with something that says "blocked" then I think it will get a little confusing towards sites that it  really can't find.

---

### Post by robotgeek on 2006-02-03
[http://pgl.yoyo.org/adservers/](http://pgl.yoyo.org/adservers/) is another great resource for hosts file based ad blocking.

---

### Post by nixclusive on 2006-02-03
I don't think it would be feasable to reduce the borwser timeout as it would block slower sites as well
How about opening an empty internal web server on 127.0.0.1:80? That should feed the browser with an empty (0 byte) page and thus the time-out wait would be eliminated! :D

That being the theory; the question here is...how do I do that? 

I just moved from Windows where I was a pro but c'mon man its been only 8 hrs. since I installed Ubuntu.

---

### Post by nixclusive on 2006-02-03
[QUOTE=Gandalf]its normal to slow down sites that use one of the addresses u blocked, since your browser will keep trying a bit to connect to localhost untill it time out!![/QUOTE]
I don't think it would be feasable to reduce the borwser timeout as it would block slower sites as well
How about opening an empty internal web server on 127.0.0.1:80? That should feed the browser with an empty (0 byte) page and thus the time-out wait would be eliminated! :D

That being the theory; the question here is...how do I do that? 

I just moved from Windows where I was a pro but c'mon man its been only 8 hrs. since I installed Ubuntu.

---

### Post by BLTicklemonster on 2006-02-03
[QUOTE=limit223]Is this picture specific enough for you?[/QUOTE]
You're too kind!

---

### Post by Heliode on 2006-02-03
[QUOTE=nixclusive]I don't think it would be feasable to reduce the borwser timeout as it would block slower sites as well
How about opening an empty internal web server on 127.0.0.1:80? That should feed the browser with an empty (0 byte) page and thus the time-out wait would be eliminated! :D

That being the theory; the question here is...how do I do that? 

I just moved from Windows where I was a pro but c'mon man its been only 8 hrs. since I installed Ubuntu.[/QUOTE]

sudo apt-get install apache2
sudo /etc/init.d/apache2 start
sudo gedit /var/www/index.html

Fill the file with:
```

<html>
Blocked!
</html>

```

Should do the trick...

---

### Post by BLTicklemonster on 2006-02-03
Wait a minute. Change what to true? :-k

---

### Post by BLTicklemonster on 2006-02-03
Just editing hosts, I see no ads on drudgreport, but here [http://news.mywebpal.com/index.cfm?pnpid=680](http://news.mywebpal.com/index.cfm?pnpid=680) I still see all the ads (I think they are ads? Maybe they aren't the same kind of thing)

---

### Post by nixclusive on 2006-02-04
[QUOTE=Heliode]sudo apt-get install apache2
sudo /etc/init.d/apache2 start
sudo gedit /var/www/index.html

Fill the file with:
```

<html>
Blocked!
</html>

```

Should do the trick...[/QUOTE]
It Worked!! Thanks...Browsing a breeze now.

---

### Post by cbudden on 2006-02-06
Hello.  I am running XAMPP.

I have set the localhost ip to 0.0.0.0, and I still get my website being displayed in the advert spaces.  Why am I getting my website on 0.0.0.0 !!  

thanks

---

### Post by anil_robo on 2006-03-11
[quote=cbudden]Hello.  I am running XAMPP.

I have set the localhost ip to 0.0.0.0, and I still get my website being displayed in the advert spaces.  Why am I getting my website on 0.0.0.0 !!  

thanks[/quote]

Are you using a proxy? That may be the reason.

---

### Post by BeeDee on 2006-03-13
[QUOTE=BoyOfDestiny]I recommend privoxy, I've been using it for years now. It's gpl and browser agnostic too... 

Makes it easy to block ads, and get rid of various web annoyances (spoof referer tag, etc etc). Anyway, it's in the ubuntu repos, you can visit the website to learn more.

[www.privoxy.org](www.privoxy.org)[/QUOTE]
Thanks for that tip **BoyOfDestiny**. Using the recommended *hosts* file worked but slowed or froze Opera as **tofudrifter** reported so I reverted to the original *hosts* file, installed **Privoxy** and Opera works like lightning again but without the junk.

---

### Post by RavenOfOdin on 2006-03-26
I don't know if this has been said before, but someone should put various Internet shock sites (ie: bakla.net) into this thing. :p

That being said, good find. I'll try it out and see what happens.

(EDIT: It doesn't seem to be working. [http://doubleclick.net](http://doubleclick.net) still showed up in Epiphany. And that was with a direct copy/paste of the hosts file.)

---

### Post by bodhi.zazen on 2006-07-09
Check out this site for a hosts file:

[http://hostsfile.mine.nu/downloads/](http://hostsfile.mine.nu/downloads/)

The site works well and gives several options for the format of the hosts file.

There is also a bash script to update the hosts file (here is the link to the bash script)

[http://hostsfile.mine.nu/downloads/updatehosts.sh.txt](http://hostsfile.mine.nu/downloads/updatehosts.sh.txt)

I have not read all the posts, so I apologize if this is a duplicate.

I have read the controversy RE: using the hosts in this way.

The advantage is that this method works for any browser (I just started with SeaMonkey, but use Dillo as well) where as the Firefox extensions both only work for Firefox and seem to slow Firefox more then the hosts file.

---

### Post by pravuil on 2006-07-10
Linblock would work but you have to make sure you get the list for spyware from a trusted source. For ads I just use adblock plus for firefox. They have some good sources to update from.

---

### Post by tturrisi on 2006-07-11
i'm surprised no one has mentioned cookies thoroughly in this thread.  I for one, am not concerned with spyware or web viruses wheh using linux, but I don't want all tracking cookies in use.  FF has good cookie handling and also alows one to block domains from setting a cookie.  However, this must be done one domain at a time, and is a pita to do manually.  My solution was to boot to windows where I have an extensive list of blocked domains that I accumulated over the years as well as the domains added by Spybot Search & Destroy and Spyware Blaster.  These are stored in a windows regkey (hkcu/software/microsoft/windows/current version/internet settings/zonemap/domains).  I exported the key values and edited the reg file into the file that FF uses to block cookie domains.  The file is stored as /home/user/.mozilla/firefox/xxxxxx.default/hostperm.1

Here's my hostperm.1.txt file.  Save it as "hostperm.1", baqckup & replace your existing one.

[hostperm.1]("http://members.cox.net/aturrisi/hostperm.1.txt")

---

### Post by bodhi.zazen on 2006-07-11
Thank you tturrisi.

I personally HATE COOKIES !!!!!!!!!

It is VERY IRRITATING that checking the "reject cookies" option in most (?all)browsers is ineffective, BOTH in WINDOWS and LINUX.

Suggestion: Try Dillo. Small, light weight browser. Rejects all cookies by default. I am not familiar enough with Dillo to know if it downloads cookies.

---

### Post by fakie_flip on 2006-12-06
> **Orunitia said:**
> This just seemed to slow a lot of sites down for me. I took it back out of my host file and everything seemed to speed up again.

That's why I would not do it. I found something that works better. Each site has to be checked for whats in the /etc/hosts. The more you have, the more is checked, the longer it takes.

---

### Post by esaym on 2006-12-06
I've always liked this one here: [http://everythingisnt.com/hosts.html](http://everythingisnt.com/hosts.html)

---

### Post by Flying caveman on 2007-01-06
This seemed to work fine for me until recently.  It seems that someone or something is changing my /etc/hosts file.  :-k 

So, I was asking about this in another forum, and someone suggested there might be something in a start up script that is changing it.  

I don't seem to even have a /etc/init.d file ??

Can someone help me find what is doing this?  I don't think it is supposed to change itself.

---

### Post by Crinos512 on 2007-07-17
> **bodhi.zazen said:**
> 
There is also a bash script to update the hosts file (here is the link to the bash script)

[http://hostsfile.mine.nu/downloads/updatehosts.sh.txt](http://hostsfile.mine.nu/downloads/updatehosts.sh.txt)


Interesting... On Win-DOH!s I have a 3 step process using a vb script and 2 .bats... provided in the hopes of improving both processes. I'll leave it up to better coders than I to script as they see fit. :)

**Step 1: **[COLOR="Blue"]_[ATTACH]38457[/ATTACH]_[/COLOR] Grabs the New host file from the internet, merges and sorts.
**Step 2:** [COLOR="#0000ff"]_[ATTACH]38458[/ATTACH]_[/COLOR] (Takes the Hosts file as an argument) Verifies the existance of the blocked sites, and creates a list of sites no longer active. ...some sites close down or rename themselves to avoid blocking.
**Step 3:** [COLOR="#0000ff"]_[ATTACH]38459[/ATTACH]_[/COLOR] (Takes the list from step 2 as an argument) Removes the invalid sites from the merges host file.

---

### Post by fakie_flip on 2007-07-17
It is best just to use the adblock firefox extension with the filter g set updater, but not the adblock plus firefox extension because it has memory leaks.

[https://addons.mozilla.org/en-US/firefox/addon/1136](https://addons.mozilla.org/en-US/firefox/addon/1136)

[https://addons.mozilla.org/en-US/firefox/addon/10](https://addons.mozilla.org/en-US/firefox/addon/10)

---

### Post by fakie_flip on 2007-07-17
> **bodhi.zazen said:**
> Thank you tturrisi.

I personally HATE COOKIES !!!!!!!!!

It is VERY IRRITATING that checking the "reject cookies" option in most (?all)browsers is ineffective, BOTH in WINDOWS and LINUX.

Suggestion: Try Dillo. Small, light weight browser. Rejects all cookies by default. I am not familiar enough with Dillo to know if it downloads cookies.

In Firefox, Tools>Options>Privacy tab>

Now you can configure how Firefox deals with cookies. I have all of my cookies deleted automagically every time I close Firefox.

---

### Post by bodhi.zazen on 2007-07-18
Thanks fakie_flip

1. The "advantage" of a hosts file is it covers not just fire fox, but any app that wants to access the wed like say opera, dillo, lynx ... The adblock firefox extension is good for firefox, but does not do much for other apps.

2. yea, I am familiar with those options for firefox and cookies. I like the safe history extension personally. Again, the problem is the does not block all cookies (and again it covers firefox only).

---

### Post by bodhi.zazen on 2007-07-18
> **Crinos512 said:**
> Interesting... On Win-DOH!s I have a 3 step process using a vb script and 2 .bats... provided in the hopes of improving both processes. I'll leave it up to better coders than I to script as they see fit. :)

**Step 1: **[COLOR="Blue"]_[ATTACH]38457[/ATTACH]_[/COLOR] Grabs the New host file from the internet, merges and sorts.
**Step 2:** [COLOR="#0000ff"]_[ATTACH]38458[/ATTACH]_[/COLOR] (Takes the Hosts file as an argument) Verifies the existance of the blocked sites, and creates a list of sites no longer active. ...some sites close down or rename themselves to avoid blocking.
**Step 3:** [COLOR="#0000ff"]_[ATTACH]38459[/ATTACH]_[/COLOR] (Takes the list from step 2 as an argument) Removes the invalid sites from the merges host file.

Very cool bat files.

---

### Post by matchstich on 2007-10-04
> **limit223 said:**
> Related to this subject,
If anyone noticed in firefox when you do about:config in browser address, filter: dns -- network.dns*=.doubleclick.net, change the value to true! (stay out of their dns)


i screwed this  up .

deleted doubleclick.

now it say----network.dns.ipv4OnlyDomains  , under status  it say 

user set,  under type it say string and under value it is blank.

will that be a problem?

thanks

---

### Post by twinszg on 2007-10-04
thanks m8 it works just fine

---

### Post by bodhi.zazen on 2007-10-04
> **matchstich said:**
> i screwed this  up .

deleted doubleclick.

now it say----network.dns.ipv4OnlyDomains  , under status  it say 

user set,  under type it say string and under value it is blank.

will that be a problem?

thanks

What did you do ?

---

### Post by matchstich on 2007-10-04
i was trying to toggle the thing to show true or whatever the first post about said to do.

but, i deleted it instead.

now it shows what i posted.

is that a bad thing ?

or should i have something  in there?

thanks

---

### Post by user1234 on 2007-11-18
> **evs said:**
> AdBlock is probably my favorite extension, along with the updater.

I see the package "mozilla-firefox-adblock" but I don't see a filer or updater package your talking about.  What's it called?

---

### Post by elec999 on 2007-11-18
What about the hosts.allow and hosts.deny.
Thanks

---

### Post by elec999 on 2007-11-18
> **bodhi.zazen said:**
> Very cool bat files.
How do you enable/use these three bats in linux.
Thanks

---

### Post by myharshdesigner on 2007-11-21
COOL TUTORIAL thanks :)

---

### Post by tturrisi on 2007-11-21
more re Firefox cookies:

In older versions of FF one had the option to block 3rd party cookies (cookies from a domain other than the domain in the address bar).  For example, one views the site [www.my-stuff-for-sale.com](www.my-stuff-for-sale.com) and that site has an advertisement from cheap-viagra.com along with a cookie from the cheap-viagra.com domain.

Newer version of FF removed the feature to be able to block such cookies.

However, you can still block such cookies via your user.js file.  Type about:confing in the FF address bar, search for this string:
network.cookie.cookieBehavior
and set the value to 1.

Possible values are: ( [http://kb.mozillazine.org/Network.cookie.cookieBehavior](http://kb.mozillazine.org/Network.cookie.cookieBehavior) )
0 All cookies are allowed. (Default)
1 Only cookies from the originating server are allowed.
2 No cookies are allowed.

---

### Post by darthwxe on 2008-05-17
:guitar: A couple of years later, I wish to thank you for your post of Dec 30, 2005. Being new to Linux, using your "How To" on installing Host Files in Linux I did it.  Now if I knew how to install Edexter(tinyserver HTTP, Port80) I would not have the FF msgs saying they could not load a blocked web site.
Instead I would a a red -- of about that length in place of FF msg.

Question: Does anyone know how to install Edexter on Unbuntu 8.0.6, if its possible?

---

### Post by y-lee on 2008-08-09
> **bodhi.zazen said:**
> Check out this site for a hosts file:

[http://hostsfile.mine.nu/downloads/](http://hostsfile.mine.nu/downloads/)

The site works well and gives several options for the format of the hosts file.

There is also a bash script to update the hosts file (here is the link to the bash script)

[http://hostsfile.mine.nu/downloads/updatehosts.sh.txt](http://hostsfile.mine.nu/downloads/updatehosts.sh.txt)


line 22852 of the hosts file I downloaded from hostsfile.mine blocks [pastebin.com]("http://pastebin.com/"). I noticed this yesterday because i couldn't connect to a pastebin link someone in IRC sent me, with any web browser and not even wget could connect to pastebin. I looked in my host file and found :

> 
127.0.0.1	passthison.com
127.0.0.1	passwordlovers.com
[COLOR="Red"]127.0.0.1	pastebin.com[/COLOR]
127.0.0.1	pastebin.spywire.net
127.0.0.1	pastubes.com
127.0.0.1	patches-cracks.de

Since pastebin.com is used on forums and IRC and what not to store code by many people in this community I felt it was worth mentioning. If you use this host file you *will be unable to connect* to pastebin unless you either delete the line above in red or comment it out (or of course ditch this host file and revert back to the ubuntu original.)

---

### Post by seamustry on 2008-08-22
how do i know if i have spyware? i'm using ubuntu...

---

### Post by matchstich on 2008-08-22
go to package manager install clam, i get clamtk with it. that is the gui.

also, rkhunter and chkrookit.

also, this is a good read

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by seamustry on 2008-08-23
> **matchstich said:**
> go to package manager install clam, i get clamtk with it. that is the gui.

also, rkhunter and chkrookit.

also, this is a good read

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

thanks!

how do i use rkhunter and chkrootkit?

---

### Post by matchstich on 2008-08-23
sudo rkhunter --update
sudo rkhunter --checkall

sudo chkrootkit

chkrootkit -d sniffer

What's chkrootkit?
chkrootkit is a tool to locally check for signs of a rootkit. It contains:

* chkrootkit: a shell script that checks system binaries for rootkit modification.

* ifpromisc.c: checks if the network interface is in promiscuous mode.

* chklastlog.c: checks for lastlog deletions.

* chkwtmp.c: checks for wtmp deletions.

* check_wtmpx.c: checks for wtmpx deletions. (Solaris only)

* chkproc.c: checks for signs of LKM trojans.

* chkdirs.c: checks for signs of LKM trojans.

* strings.c: quick and dirty strings replacement.

* chkutmp.c: checks for utmp deletions.

chkwtmp and chklastlog *try* to check for deleted entries in the wtmp
and lastlog files, but it is *not* guaranteed that any modification
will be detected. 


go to applications>terminal

---

### Post by valianayil on 2008-12-07
Dear anil_robo,

I was enjoying the host technique (in ubuntu6.10). Last week I upgraded to xubuntu 8.10, there is a host file. I copied the mentioned text. but nothing happend!
there are host.allow and host.deny files. How we go about this.

Please Help Please I need this blocking of ads...

---

### Post by anil_robo on 2008-12-07
> **valianayil said:**
> Dear anil_robo,

I was enjoying the host technique (in ubuntu6.10). Last week I upgraded to xubuntu 8.10, there is a host file. I copied the mentioned text. but nothing happend!
there are host.allow and host.deny files. How we go about this.

Please Help Please I need this blocking of ads...

If all you want is blocking of ads, consider installing "Adblock Plus" Firefox extension.

Regarding the hosts files: Put all IP addresses you want to block in the hosts.deny file. For example, if you want to deny all connections from IP 100.100.100.100 to your host, you'd add an entry like this: 
All: 100.100.100.100

Try it and let me know if it works.

---

### Post by treepolitik on 2008-12-13
All I know is that very frequently after I've been using Firefox for a while, the computer thinking light starts going almost solidly and never stops, even after half an hour.  Meanwhile, when I try to move the mouse, I have to wait for five seconds for it to go anywhere, and it won't respond to clicks.  So I just cut the power and reboot.](*,)

Would there be a way to prove that I have or do not have bots in my system? I am using Hardy Heron 8.04, with a 2.624-21-generic kernel, GNOME 2.22.3, and an Intel Pentium 4 CPU 2.40 GHz:biggrin:

I am going to change my system password to something with more than six characters and with several anti-letters.  I know I might sound repetitive, but each person is a different level, and many forget.

The two programs under "virus" offered by Add/Remove Programs read, 
in brief: 

Virus Scanner
graphical front-end for ClamAV 
ClamTk is a GUI front-end for ClamAV using perl-Gtk2.

StepBill
Get rid of those nasty Wingdows viruses 
This is a port of the MacBill, which is based on xbill, source to GNUstep.

Of course, I tried to install the first and found that my Synaptic Package Manager is dead: :shock:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
Does this mean that I haven't been getting security updates? I don't have the "Install security updates without confirmation" in the Software Sources turned on, but I told it to tell me when there's updates.

If I were to try to develop a program to defend my computer against bots starting with zero knowledge of computer security, is there a good place to start?  Perhaps a book, tutorial, or site?  When I had Windows, I used Spybot Search and Destroy.:confused:

I also heard compatibility rumors. :idea: Would it be possible to install a Mac program on a Linux, here an anti-virus software; they have Symantec for Mac OS X.3 or X.4-5

I'm definitely going to try out all the chk and rkhunter things previously mentioned.  Is there a security test available?  Package Manager reveals:

Nessus
Remote network security auditor, the client  
The Nessus Security Scanner is a security auditing tool. It makes possible to test security modules in an attempt to find vulnerable spots that should be fixed.:popcorn:

---

### Post by treepolitik on 2008-12-27
[QUOTE=treepolitik;6364632]All I know is that very frequently after I've been using Firefox for a while, the computer thinking light starts going almost solidly and never stops, even after half an hour.  Meanwhile, when I try to move the mouse, I have to wait for five seconds for it to go anywhere, and it won't respond to clicks.  So I just cut the power and reboot.](*,)

Everybody who has this problem of Firefox taking all or a good deal of your CPU--remember to ***clean your cache*** and your cookies!!  You are most likely **not under attack**, mostly likely **do not have spyware**.  Go to Preferences>Privacy (and I understand that many of you already have done this) and clear private data, uncheck the accept cookies box, and if you wish, always clear my private data when I close Firefox.

(Just for kicks and giggles, my Windows-using sister has to go into Safe Mode with msconfig to clean her Internet Explorer cache)

Another concern, which I cannot verify, is that if you have a **firewall**, it might interfere with the *internal settings* and make you *more vulnerable*.  

(When I had Windows, they told me not to run ZoneAlarm and Windows Firewall at the same time.  I'm simply making a possible analogy).

---

### Post by Thomas00 on 2008-12-29
"AVG is very famous anti virus software and made his own space in the market. I know one superb anti virus software [www.search-and-destroy.com](www.search-and-destroy.com) it is able to fight with any kind of virus.

Thank You."

---

### Post by invenit on 2009-01-02
Great thread! Me, I dual boot Ubuntu 8.10 and WinXP on both of my machines. I get superior overall ad blocking with Ad Muncher payware + HOSTS in Windows; but it took me awhile to get linux up to speed. I've been experimenting with the Proxomitron using wine and Bfilter along with a HOSTS file. (By the way, Proxomitron works well in Ubuntu -- just make sure that you use up-to-date filters (check out [http://www.buerschgens.de/Prox/](http://www.buerschgens.de/Prox/) --I know the site's in German but the download works good out of the box)). :D

Anyway, I chain Proxomitron or Bfilter to Firefox (with AdblockPlus), Epiphany, Dillo, Galeon & works well. OTOH, I use fanboy's ad blocking filters with Opera (no Prox) since Proxomitron's German filters interfere with some of the news video at Yahoo. YMMV.

By the way, I got to agree with the folks who invoke Firefox's AdBlockPlus. It may be all you need for ad blocking *if* Firefox is all you use.

---

### Post by Custom Cowboy on 2009-01-04
I am getting E-Mails (spam) aparently from myself. How can I use this host list to block them. A relative newbie writing.

---

### Post by gonkyouka on 2009-05-16
this is what i need and it works on my jaunty. thanks so much~

---

### Post by Fyrzen_ on 2009-05-20
In the first post the link [www.doubleclick.net](www.doubleclick.net) directs to the URL: "http://www.doubleclick.net)/", which has a ")" at the end and is thus an invalid address, which causes firefox to display the Page Load Error(See: your firefox address bar). You can still go to [www.doubleclick.net](www.doubleclick.net) after adding the lines to etc/hosts/. 

IMHO This howto is brilliant! *thumb of approval*

---

### Post by antony_css on 2009-06-16
> **Heliode said:**
> sudo apt-get install apache2
sudo /etc/init.d/apache2 start
sudo gedit /var/www/index.html

Fill the file with:
```

<html>
Blocked!
</html>

```

Should do the trick...


What about images? flash?
I am afraid the apache server will return 404 error.

BTW, the latest version of a windows app **Hostsman** also includes a mini-server which return a text "[blocked]" to every html file request, and return a transparent image to every image file (png, gif, jpg,...) request.

Is it possible to port this feature to the apache server in linux?

EDIT: Included another approach in linux using lighttpd:
[http://www.lousycoder.com/blog/index.php?/archives/85-Using-the-hosts-file-and-lighttpd-to-block-ads.html]("http://www.lousycoder.com/blog/index.php?/archives/85-Using-the-hosts-file-and-lighttpd-to-block-ads.html")

---

### Post by Irvine_himself on 2009-09-07
I read this long post with great interest and realised that this idea can profitably extended.

For those with either a dual boot or a separate access to a Windows machine, installing either "Spyware Blaster" and/or "SpyBot search & Destroy" offers not only Host file immunization, (with which you simply copy/edit the host file over,) but also offers immunization against tracking cookies and dangerous [inline?] images. (This last is a potentially catastrophic and sadly all to common, way of installing malware into windows)

The immunized Windows host file is found in 

C:\windows\..\etc\

The cookie and image immunization can be found by searching for and copying "permissions.sqlite" from 

C:\Documents and Settings\user\\Application Data\Mozilla\Firefox\Profiles\

which would then be pasted into the relevant directory of Ubuntu

PS 

There is a Firefox add-on, "Better Privacy", which deletes flash cookies.

---

### Post by matchstich on 2009-09-10
sorry, my chemo and drug infested mind missed a post .

thanks

---

### Post by Cyber_rader on 2010-10-29
thanks for the info, i kept getting ads that would play audio on there own, the hosts file fix works great and i had no issue in updating it now those ads are gone and the net speed is just a tad bit faster without all that crud downloading

---

### Post by karthick87 on 2010-10-29
It blocks the entire site..In some site the banner will appear with close button,after closing the button only we will be able to browse the site..How to block the banner alone.?

---

### Post by bodhi.zazen on 2010-10-29
> **getyourkarthick said:**
> It blocks the entire site..In some site the banner will appear with close button,after closing the button only we will be able to browse the site..How to block the banner alone.?

Try privoxy.

---

### Post by karthick87 on 2010-10-29
What is privoxy..?Is it a proxy..?

---

### Post by Omnomnom on 2010-10-29
It's great, no more "Get a free car and enter your social security number here" ads!

---

### Post by Irvine_himself on 2010-10-31
> How to block the banner alone.?Either "AdblockPlus" or "Privoxy" can block specific elements of a web-page: They are both avialble as Firefox add-ons, though you would be better getting privoxy from the Ubuntu repos.

There operation is not the same though they are equivalent and complementary. "AdBlockPlus" acts as a http filter much like using the host file, except it filters the address of individual elements rather than the entire address. Privoxy is a local host anonymizing proxy that among other things filters the same sort of things. Of the two, Privoxy is more powerful, but "AdBlockPlus" is probably easier to use. 

Privoxy works well with the "TOR" Onion network: an anonymous encrypted network that sits on top of the Internet. The entry and exit nodes are constantly changing and because of the multiple layers of encryption, it is for all practical purposes, completely anonymous when used in conjunction with Privoxy. [There are theoretical ways of feeling the shape of the Onion network, but this is of theoretical interest only.]

Designed by DARPA, the "TOR" networks intended users were political dissidents. Although this is still the case, criminals and people of dubious morality are now also using it. There is no Google, but you can explore the network and find sites that do not exist in the wider Internet, though be prepared to be shocked since there is no "censorship"

Other Firefox add-ons that are useful with respect to filtering junk and privacy are "RequestPolicy" to control referral requests, "BetterPrivacy" for flash cookies and "NoScript" for java script, there also any number of cookie editors and scripts to control the referrer headers.

To give an example of how vulnerable your on-line privacy is, I recently set-up a small Ubuntu/Xp network so that I can legally play with various networking tools. I was shocked when I discovered the amount of personal information I could pull off my Xp box just by probing for open ports. (I always consider my Xp box to be very heavy on security!)

I have not, as yet, tried some of the more exotic tools but I am studying hard and what I have learned so far is eye-opening.

PS:
Be warned that patience is required when learning to use some of these privacy tools: Basically you are blocking content and though this guards privacy and dramatically speeds up download speeds, it requires a certain judgment to decide on what to block. For example, I find "BetterPrivacy" to be indispensable, but the problem is that when just randomly browsing  referrals have to be allowed individually. This is not usually a problem, but some sites use seperate domains for each element. eg in order to see the images when you read a NYT article, you have to allow referals from NYT.com to NYT.images.com. Another example is  getting a blank page after clicking a link  because the page hs no content other than referrals to other domains, (a surprisingly common occurrence.)

---

### Post by bodhi.zazen on 2010-10-31
> **Irvine_himself said:**
> Be warned that patience is required when learning to use some of these privacy tools: Basically you are blocking content and though this guards privacy and dramatically speeds up download speeds, it requires a certain judgment to decide on what to block.

Nice post.

+1 to this last part, it takes a while to learn privoxy. Once it clicks it is quite easy.

Probably the biggest mistake is to change the default settings to block too much (when you look at the configuration it sounds good, but unless you understand what and why you are changing a setting you will almost certainly cause breakage).

White lists for trusted sites can help a bunch.

---

### Post by chrislongski on 2011-12-01
sudo gedit don't work AND Nano won't allow a paste into the hosts file...

---

### Post by Crinos512 on 2011-12-01
a little trick for pasting into a terminal is press 'Ctrl + Shift + V' instead of just 'Ctrl + V'... works with nano.

other than that what happens when you type '[COLOR="Indigo"]sudo gedit[/COLOR]' ?

---


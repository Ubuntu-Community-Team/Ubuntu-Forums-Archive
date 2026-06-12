---
title: "HOWTO: Block most ads in firefox"
date: 2005-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by jerome bettis on 2005-03-23
someone posted this on another forum, i think it's worth passing on.  doing this will get rid of those google ads, a lot of banner ads and possibly even more stuff (i've only been using it for 10 minutes).  the person who wrote it claims it stops 99% of ads.

1.  install the ChromEdit extension available here: [https://addons.update.mozilla.org/extensions/moreinfo.php?application=firefox&version=1.0&os=Windows&id=17](https://addons.update.mozilla.org/extensions/moreinfo.php?application=firefox&version=1.0&os=Windows&id=17)
2.  restart firefox
3.  open this link: [http://www.mozilla.org/support/firefox/adblock](http://www.mozilla.org/support/firefox/adblock) and copy all of the text you see there.
4.  go to tools > edit user files.  click the userContent.css tab up top.
5.  clear that text and paste in what you copied
6.  restart firefox and enjoy no advertisements

---

### Post by bored2k on 2005-03-23
Great .

Thanks a lot mr Bettis .

I use adblock regularly, i hope this makes it better.

edit --  It actually does make things even better :D .

Adblock + This trick : Jewel Mix .

Kudos for Mr. Bettis :D .

edit 2 -- Boy are websites **empty** without ads ! .

---

### Post by Michael on 2005-03-23
[QUOTE=bored2k]Great .

Thanks a lot mr Bettis .

I use adblock regularly, i hope this makes it better.

edit --  It actually does make things even better :D .

Adblock + This trick : Jewel Mix .

Kudos for Mr. Bettis :D .

edit 2 -- Boy are websites **empty** without ads ! .[/QUOTE]
 They sure are.. I'm actually thinking in disabling Adblock.. lol :)
The only really annoying ads are these types of popup flash ads that take over half of the browser window and then you need to search for the "close" button while cursing the creator of that ad. I don't mind ad banners, really. I can even click on them every now and then if it helps support the sites I am visiting.. think about it, ads are not just there to be annoying :)

---

### Post by telmo on 2005-03-23
WOW... this is SWEET! :P

---

### Post by beeldings on 2005-03-23
Great post, thanks for the tip! With this extension and my hosts file, my web browsing is virtually ad-free.

---

### Post by Glanz on 2005-03-23
[QUOTE=beeldings]Great post, thanks for the tip! With this extension and my hosts file, my web browsing is virtually ad-free.[/QUOTE]
 I just cp'd the userContent.css file with that "blockAds" config from firefox to Epiphany (/home/x/.gnome2/epiphany/mozilla/epiphany/chrome/userContent.css)  and it seems to be working very well!!! =D>

---

### Post by macewan on 2005-03-23
outstanding suggestion

---

### Post by josue on 2005-03-23
[QUOTE=macewan]outstanding suggestion[/QUOTE]
 Clever. Thanks, seems to work.

The internet looks empty :)

---

### Post by primeirocrime on 2005-03-23
grand! a lot more oxygen in the web-air. 
thanks for the generous tip. [-o<

---

### Post by Glanz on 2005-03-23
Finally! freedom!!! No more used car and pork belly peddlers! I am proud to go against every principle of "forced" enterprise and monopolofaschistic capitalism known to slimekind!

---

### Post by Technoviking on 2005-03-23
Great tip, works under Windows also. 

We need a sub-forum to store the best how-tos like this.

Mike =D>

---

### Post by justaguynpc on 2005-03-24
Thanks for the script, actually, it takes some getting used to ....................

---

### Post by trailwalker on 2005-03-26
I use the hosts file from [http://www.everythingisnt.com/hosts.html](http://www.everythingisnt.com/hosts.html) to block most ads.  It is copied to /etc/hosts and will block ads on any browser.

I use adblock to get anything the hosts file misses.

---

### Post by teumima on 2005-03-26
It's good. Damn adds. Why does it block out the YAHOO on the yahoo.com page? Bit too much.

---

### Post by istoyanov on 2005-03-27
A more efficient userContent.css file may be found at [http://www.gozer.org/mozilla/ad_blocking/css/userContent.css](http://www.gozer.org/mozilla/ad_blocking/css/userContent.css)

Have a clean browsing:)

---

### Post by Yamakazi on 2005-03-29
Hello,

I'm trying the hosts file way, but i can't get it to work.  I added the file  [http://www.everythingisnt.com/hosts.html](http://www.everythingisnt.com/hosts.html) to my hosts. 
But i when surfing to one of the entry's it still shows up. 
I use a proxy server.  Could that be the problem??  
Please help me :)

---

### Post by myfology on 2005-04-01
I like Privoxy!  Here's the description from the homepage.  BTW  you can get it from the Universe via synaptic or apt.  Also, configure your firefox (you don't have to config your entire network prefs for Ubuntu) to go to 127.0.0.1:8118 

 Privoxy is a web proxy with advanced filtering capabilities for protecting privacy, modifying web page content, managing cookies, controlling access, and removing ads, banners, pop-ups and other obnoxious Internet junk. Privoxy has a very flexible configuration and can be customized to suit individual needs and tastes. Privoxy has application for both stand-alone systems and multi-user networks.

Privoxy is based on Internet Junkbuster (tm).

The most recent release is 3.0.3 (stable)


Have Fun!  
Matthew

---

### Post by bored2k on 2005-04-01
After this patch I see no ads at all, only those hosted by the own website [few]. It so rocks, I barely use Adblock now.

---

### Post by bored2k on 2005-04-01
[QUOTE=Mike Basinger]Great tip, works under Windows also. 

We need a sub-forum to store the best how-tos like this.

Mike =D>[/QUOTE]
 We're thinking of ways to clear things up right now, NOT create more divisions ;) . For that we have stickies.

---

### Post by dejitarob on 2005-04-01
I use a more [up to date userContent.css filter](http://adblock.f2g.net/) in addition to [Adblock](http://adblock.mozdev.org/) to knock out even more ads. It's simply amazing, many sites appear completely more clean. To setup Adblock with the great custom [filterset.g](http://www.geocities.com/pierceive/adblock/):
1. [Install](http://adblock.mozdev.org/installation.html) the Adblock extension.
2. Open up the [filterset.g site](http://www.geocities.com/pierceive/adblock/).
3. Navigate to the very bottom and save the latest custom filter.
4. In Firefox goto 'Tools', 'Adblock', 'Preferences'. Select 'Adblock Options' and click 'Check Parent Links'.
5. Select 'Adblock Options' again and 'Import Filters'. Open the custom filterset.g and click 'Ok'.

To block google's Sponsored Links edit your userContent.css with ChromEdit to include this at the end: ```
table[align="right"][width="25%"][border="0"][bgColor="#ffffff"] {display: none ! important; }
```
Another neat trick with the userContent.css are [gmail skins](http://persistent.info/archives/2004/10/05/gmail-skinning), which need to go underneth the aforementioned entries to work correctly.

---

### Post by gw90se on 2005-04-01
Thanks, this trick is fantastic!!

---

### Post by sinbad782 on 2005-04-10
Even better - run this in combination with Privoxy (you can use the switchproxy Firefox extension to turn it off if any given web page doesn't load properly). This shouldn't give too much of a performance hit, but will absolutely blast those banner ads!

PJS

---

### Post by bassMonkey on 2005-06-28
I'm sorry to report it doesn't work for me... I remember it worked on my previous install but after I reinstalled ubuntu and upgraded to ff 1.04 backport and tried this it doesn't do anything. I just can't understand why. It was a bit of a hassle to upgrade firefox but I wouldn't expect that to be a problem... anyone else having problems? I cleared userContent.css and pasted the adblock thingy as I did previously but it simply doesn't do anything... help?

--edit--
Aah, now it works, I had to remove my old profile and add a new...

---

### Post by allforcarrie on 2005-06-28
WOW! i thought adblock was great!

---

### Post by trinaryouroboros on 2009-03-27
[FONT="Courier New"][COLOR="SeaGreen"]Don't know if anyone still hunts around for this stuff, but, the link in the beginning of this page regarding the data to plug into UserContent.css has expired (well jeez this thread was from 2005), as well as the actual addon itself.

**   I have, however, stumbled upon ChromEdit Plus here:**

[http://webdesigns.ms11.net/chromeditp.html]("http://webdesigns.ms11.net/chromeditp.html")

**   Also, the code you seek to plug into UserContent.css is here now:**

[http://www.floppymoose.com/userContent.css]("http://www.floppymoose.com/userContent.css")

[FONT="Franklin Gothic Medium"]**Sidenote: Has anyone else noticed the alarming number of disappearing sites that helped you block ads?  I remember Mike's Host File was a well-to-do place, suddenly it's literally disappeared off the face of the web!**[/FONT]

His site used to be:  [http://everythingisnt.com]("http://everythingisnt.com")

Google seems rather objective to providing even a cached page of it...have to wonder.

**Go cyberpunks, down with the Corps! [opens fire]**

8-)[/COLOR][/FONT]

---


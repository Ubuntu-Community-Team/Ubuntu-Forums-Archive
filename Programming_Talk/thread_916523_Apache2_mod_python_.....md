---
title: "Apache2 mod_python ...."
date: 2008-09-11
forum: Programming Talk
---

### Post by hockey97 on 2008-09-11
HI I installed the mod_python for apache2. 

I now want to get it working. I can't figure out how to get apache2 to run python scripts.

Also if I do get python scripts to work would I be able to use pygame to make online games??

just woundering.

---

### Post by ad_267 on 2008-09-11
This might help: [http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-ubuntu-fedora-centos-mandriva-opensuse](http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-ubuntu-fedora-centos-mandriva-opensuse)

No I don't think you can make games like that. You would need to use flash or something like that.

---

### Post by hockey97 on 2008-09-11
yes I did  google search and found that site before I even found more sites that just tell you to do the sudo get to download the mod and then installed it and it should work.

I installed using the package manger program this is how I installed the mod_python.

I followed that tutorial but I can't find /etc/httpd/conf.d/python.conf

I only can see /etc/  that is all I don't find /etc/httpd at all. I assume it's a folder and I looked where the H's supposed to be and I can't find it.

why can't I use pygame to make python games for the internet???

is it because pygame dosen't use the http protocal and uses the udp protocal.

I wish python does someday include a online game making lib. 

SO if I do get this mod_python then what can I do with it???

there was a website that said you can run python scripts so I assumed if the pygame you can use in a python script then why not make the game run on apache2?

It was just a thought.

---

### Post by pmasiar on 2008-09-11
> **hockey97 said:**
> yes I did  google search and found that site before I even found more sites that just tell you to do the sudo get to download the mod and then installed it and it should work.

why can't I use pygame to make python games for the internet???

...because you do not have clue about difference between a desktop app (like pygame is) and CGI app, which runs in browser?

> I wish python does someday include a online game making lib. 

I wish pigs could fly :-)

> SO if I do get this mod_python then what can I do with it???

web based app? Use Django, much simpler. And before that, make simple CGI app. See wiki in my sig

> there was a website that said you can run python scripts so I assumed if the pygame you can use in a python script then why not make the game run on apache2?

... and you assumed wrong. CGI is completely different animal: it is a program which generates text file (HTML) for browser to display. 

Attitude is not a valid replacement for competence.

You are really trying to run before learning to  crawl and walk. Patience, grasshopper: start with plain text games to run in terminal, like everybody else did.

---

### Post by LaRoza on 2008-09-11
> **hockey97 said:**
> HI I installed the mod_python for apache2. 

I now want to get it working. I can't figure out how to get apache2 to run python scripts.

Also if I do get python scripts to work would I be able to use pygame to make online games??

just woundering.

See: [http://ubuntuforums.org/showthread.php?t=915532](http://ubuntuforums.org/showthread.php?t=915532)

---

### Post by Kadrus on 2008-09-11
Pygame isn't for web applications as far as I know,I could be wrong,but it's Python + SDL.
You can write online text-based games with Python using CGI.
If you want something simple.([Samll CGI Web Server]("http://learnpython.pbwiki.com/WebApplication")) It's from pmasiar's wiki.
Check [Web Server Gateway Interface]("http://en.wikipedia.org/wiki/Web_Server_Gateway_Interface")
You can make online games with [haXe]("http://haxe.org")
Or you can use an action script compiler: [mtasc]("http://mtasc.org")
You seem to be rushing into things quickly,which will lead to failure(not trying to sound pessimistic)

---

### Post by skullmunky on 2008-09-14
Here is an example of an online game using mod_python and apache2:

[http://www.crudeoils.us/wafaa/html/domesticTension.html](http://www.crudeoils.us/wafaa/html/domesticTension.html)

the game's over now, but you can use the links at the bottom to read about it and watch some videos.

mod_python was the bridge between the website and the microcontroller that moved and fired the gun.

though I suppose that's probably not what you had in mind ... :p

---


---
title: "wondershaper frontend"
date: 2007-05-13
forum: Programming Talk
---

### Post by iamah on 2007-05-13
I made a little front end for Wondershaper... its useful sometimes when you want do quick changes on bandwidth limits... I decided to share it, probably won't help many people, but anyway... XD

Its python with glade interface, I don't remember quite well, its old code, but still works... 

The file is attached, and mirrored here:
[http://www.myjavaserver.com/~iamah/](http://www.myjavaserver.com/~iamah/)

bye:)

nice tip:
> **intel352 said:**
>  I've add this app to my user directory, then I dragged run.sh to the toolbar (systray), which prompted me to setup a launcher link. I chose an Icon, specified a name and description, and voila, it appears to be a normally installed application that I can easily access from my toolbar :-D

---

### Post by bgryderclock on 2007-06-08
> **iamah said:**
> I made a little front end for Wondershaper... its useful sometimes when you want do quick changes on bandwidth limits... I decided to share it, probably won't help many people, but anyway... XD

Its python with glade interface, I don't remember quite well, its old code, but still works... 

The file is attached, and mirrored here:
[http://www.myjavaserver.com/~iamah/](http://www.myjavaserver.com/~iamah/)

bye:)

I installed this app and it works greats. :) 

 I wish there was an application that would just set torrent traffic priority below all others types and dynamically change upload speed when web browsers slows.

cheers!

---

### Post by bgryderclock on 2007-06-08
> **iamah said:**
> I made a little front end for Wondershaper... its useful sometimes when you want do quick changes on bandwidth limits... I decided to share it, probably won't help many people, but anyway... XD

Its python with glade interface, I don't remember quite well, its old code, but still works... 

The file is attached, and mirrored here:
[http://www.myjavaserver.com/~iamah/](http://www.myjavaserver.com/~iamah/)

bye:)

I installed this app and it works greats. :) 

 I wish there was an application that would just set torrent traffic priority below all others types and dynamically change upload speed when web browsers slows.

cheers!

---

### Post by bunker on 2007-06-09
> **bgryderclock said:**
>  I wish there was an application that would just set torrent traffic priority below all others types and dynamically change upload speed when web browsers slows.cheers!

You can do this with a combination of iptables, layer7 filter, and ipp2p.  It's pretty much over my head and takes about 3 pages worth of iptables rules, but I connect through a router running openWRT with it all set up and I notice no difference in speed or ping when using bit torrent (unless your ISP limits it of course; my ISP used cripple my connection when using bit torrent until they were taken over recently.  Might have just been an error of course.).  [Here](http://www.bananadine.co.uk/stuff/iptables.html) are the rules I have set up.

---

### Post by intel352 on 2007-06-20
kudos to you sir. I've add this app to my user directory, then I dragged run.sh to the toolbar (systray), which prompted me to setup a launcher link. I chose an Icon, specified a name and description, and voila, it appears to be a normally installed application that I can easily access from my toolbar :-D

nice script ;-)

---

### Post by Mithrilhall on 2008-02-15
Old thread but check out [www.mastershaper.org](www.mastershaper.org)

---

### Post by Runaway1956 on 2010-09-13
Replying to a two year old thread, LOL

Anyway - the front end seems to work fine.  However, I've already installed Wondershaper through the package manager.  A little edit is required to use the installed Wondershaper, it seems. 


Replace each instance of "./wondershaper-1.1a/wshaper" with "/usr/sbin/wondershaper"

I'm doing so right now - 

Hmmm - I can open smoothnet from a terminal, but it won't "run" with a double click any longer.  No big deal - I can create a launcher for it.

Clicking the "status" button has the same effect as clicking the "remove" button - which is to clear wondershaper.

I'm getting an error in the console, which I need to research a little bit:

./smoothnet.py:90: DeprecationWarning: os.popen4 is deprecated.  Use the subprocess module.
  stdin, stdouterr = os.popen4(oscommand)

The answer to the error can be found here - [http://docs.python.org/library/subprocess.html#subprocess-replacements](http://docs.python.org/library/subprocess.html#subprocess-replacements) - but I'm afraid it's a little over my head.  I may play with it later - not tonight though!

---

### Post by Kriese on 2010-09-20
Thought i have the same issue with my frontend, but i works, sry ;)

---

### Post by ibuclaw on 2010-09-20
hmm... Old thread, no point keeping this chevy running.

Just FYI, as a rule of thumb, with legacy/old software your mileage may vary with regards to how well it runs.

On that bombshell



[IMG]http://www.hth-c.com/images/smilies/thread_closed.gif[/IMG]

---


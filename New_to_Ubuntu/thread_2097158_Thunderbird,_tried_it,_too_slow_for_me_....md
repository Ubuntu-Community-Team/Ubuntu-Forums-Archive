---
title: "Thunderbird, tried it, too slow for me ..."
date: 2012-12-22
forum: New to Ubuntu
---

### Post by cwmoser on 2012-12-22
I have been using Evolution for years and when Evolution
would not consistently display email in the preview menu
I decided I would install Thunderbird and move my
emails to Thunderbird.

Well, that turned out to be a mistake.  Thunderbird is
way slower on my 12.04 64-bit Ubuntu.  Fortunately
I maintained my Evolution configuration.

So, why is Thunderbird so slow???

Carl

---

### Post by Temporarily on 2012-12-22
Is not slow for me. I use Thunderbird and Thunderbird only.. for years now. 

And what you mean about.. slower ? Slower than Evolution ? Well , I don't know that, because I never used it (Evolution).

---

### Post by Yougo on 2012-12-22
it can get slow to start if you have a large or many accounts set up. also having many add-ons can slow things down at start up. depends on what particular add-on. 

i have a gmail account through IMAP, and it's a couple of GB big by now. Thunderbird about doubles the size because it keeps the labels, as well as "all messages" as folders. messaages that have gmail labels end up in each corresponding folder, and in the "all messages" folder.

i have lightning, an add-on foor google contact synching, an add-on for google tasks, for GPG keys and a couple more for theming, such as viewing messages in google-discussion mode, and thinner scrollbars.

considering the huge mass of messages, contacts, appointments and tasks to sync, and all the addons to load, i'm not complaining about a 20-30 second start-up time. it's my own fault :-)
my MS Outlook at work is connected to an exchange account, and loads slower still :P

why not just use gmail web interface? i like my stuff offline aswell, in case of no connection, or should i ever skip to another host, i have my data.

i did try Evolution, but it reminded me of my grandpa, and it ran from my desktop screaming when i introduced it to my gmail account.

if gmail (or someone else?) ever makes an offline client that does the exact same everything that gmail does online, and i don't mean some glorified web-app, but actual offline storage and syncing, gimme a call

---

### Post by Filip II on 2012-12-22
The startup can be slow when I use it on my PC, but overall I don't have any speed issues with it.

---

### Post by Frogs Hair on 2012-12-22
I haven't experienced slow performance with Thunderbird while using multiple desktop sessions. I run Enigmail and Lightning calendar for add-ons. Tbird doesn't integrate with the Gnome Shell which made to work with Evolution and no surprise because it is an extra session.

---

### Post by cwmoser on 2012-12-22
Thunderbird is slow when I select a different email in the message 
list - extremely slow.  Evolution does not have this problem.

I don't use the Calendar in Evolution so Thunderbird has all the features
I need but because it is so slow, I went back to Evolution.

I wonder if the problem is that I saved Evolution messages as an
mbox file and imported them into Thunderbird?

Carl

---

### Post by Yougo on 2012-12-22
Once imported, the emails are stored in thunderbird's mail format and files. there shouldn't be a problem there.

is your home folder on a different location, or did you specify a non-standard location for your thunderbird profile? or do you have a low spec computer?

how slow is slow. 2-3 seconds? 30 seconds?

---

### Post by hoosier82 on 2013-01-27
Just my thoughts, but I used Evolution for as long as I could, but several kernels back it just kept crashing. Searching revealed that this was known to happen with whatever kernel was current at the time and we would have to wait for Ubuntu's next version change for relief. I couldn't put up with that and went to Thunderbird and it worked fine. 

However, for the past several months, my Thunderbird had became sluggish and for the past several weeks, it has barely run at all. Running htop in the terminal showed it going over 100% of CPU a lot and it was sucking up over 15% of available RAM.  This morning it struck me: take a look at the swap file. I have 4 GB of DDR2 RAM and the swap was set for just over 5 GB of swap space. So, I made the swap partition 9 GB and this thing runs like a rocket ship! I don't know why it needs so much swap space, but it seems to have solved the problem. The less RAM you have, the more swap space you need. Let's say you have 2 GB of RAM, then I'd suggest you need 3x, or at least 6 GB of swap. If you have from 4-8 GB of RAM, try 2x, or 8-15 GB of swap space. Over 12, you can probably get by fine with 1.5x. That's just my rule of thumb. Experiment and see what works for you. Best of luck to you all!

---

### Post by Frogs Hair on 2013-01-27
Thunderbird has a cache and history like Firefox and history can be cleared.The only way I have found to clean the cache _so far_ is with a cleaner. Like a browser a large cache will slow the application down.

---

### Post by frank604 on 2013-01-27
I noticed it has a lot of cpu consumption when it is indexing.  At this point there are no word indicators that it is indexing, just a bar on the bottom right with a moving ball.

Besides those times, thunderbird has remained light and responsive.  I've been using thunderbird on weaker than current market pcs for 2 years and don't really think it is sluggish at all.

I have thunderbird open in the back on my asus eee 1005ha netbook with 2gig of ram.  No problemo, except when it indexes.

---

### Post by uRock on 2013-01-27
> **Frogs Hair said:**
> Thunderbird has a cache and history like Firefox and history can be cleared.The only way I have found to clean the cache _so far_ is with a cleaner. Like a browser a large cache will slow the application down.

Though I have never experienced slowness with Thunderbird, I still run Bleachbit weekly and let it clean out Thunderbird and other applications. This may help with the OP's issue.

---

### Post by Lemuriano on 2013-01-27
Seamonkey is fast!

---

### Post by gifford on 2013-01-27
I too am using Thunderbird without problems. Can be slow at times starting and consumes a lot of the cpu's when doing so.
I run lightning and several other add-ons including Google voice, which allows me to send sms messages from the app.

When Evolution started crashing several years ago, forced me to move to Thunderbird. Not perfect, but workable. 
There is also Claws mail available but do not have any experience with it.

---


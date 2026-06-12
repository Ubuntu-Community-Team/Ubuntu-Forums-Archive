---
title: "[SOLVED] Looking for a backup utility with disc-spanning and file-name indexing..."
date: 2008-06-29
forum: New to Ubuntu
---

### Post by diablo75 on 2008-06-29
Here's what I'd LOVE.  I want a utility that I can use to backup a folder with 30 gigs of information, and span it across several DVD's for me automatically.  While its doing that, it will also keep track of the names (perhaps even thumbnails) of the files that have been backed up locally for indexing purposes.

So, lets say you backed up 100 gigs of stuff over a long period of time, over several backup/burning sessions and you've deleted all the data you backed up from your hard drive to create free space.  You've got everything on disc....or rather... dozens of discs.  I wouldn't want to sit there inserting each disc one after another to find a file back.  What I would prefer to do is search a database that was compiled by the backup utility.  That way I can just do a file name search, then it would tell me, "That file is on disc 22." or something like that.

And, aside from backing up, I would also love it if I could go through a bunch of discs that I already have burned (prior to ever using the backup utility), scan them with the same utility, and it would index their contents into the rest of the database as well, giving me a number to write on the disc after the scan.

Is there anything out there that can do this at least partially?  I can burn discs without a backup utility to span the data for me if that's what it comes down to, but what I really need is something that I can use to scan hundreds of CD/DVD's and index all the files for me so I can search against all of those discs contents at once, instead of one disc at a time.

---

### Post by hyper_ch on 2008-06-29
is there a reason you want to backup onto dvds and not an external disk?

---

### Post by diablo75 on 2008-06-29
Because it's cheaper?

---

### Post by hyper_ch on 2008-06-29
short term maybe... longterm... not really... especially not if you want to backup often ;)

---

### Post by diablo75 on 2008-06-29
Could you...like.... go away?  Come back when you have an answer to a question and stop posting replies that don't help me or anybody else.  You did it here too:  [http://ubuntuforums.org/showthread.php?t=844214](http://ubuntuforums.org/showthread.php?t=844214)

---

### Post by hyper_ch on 2008-06-29
I could ;)

and my replies might not be an answer to what you expect but show a different approach - that you might have missed ;)

and besides that other thread, did you read my reply? ;)

---

### Post by zeronothing on 2008-06-29
I'm going to agree with hyper_ch that backing up to DVD is probably not a great approach. with external drives being so cheap, backing up to a external hard drive would be your best bet. to answer your question about the whole backing up to DVD's. I dont know of a way to specifically backup to DVD the way you would like. for the record diablo75 dont ask for help if you cant take replys that don't meet your standard. diablo75 no offense but your talking to Linux folks. We tend to jump the gun with are replys instead of thinking sometimes.

---

### Post by diablo75 on 2008-06-29
> **zeronothing said:**
>  diablo75 dont ask for help if you cant take replys that don't meet your standard. diablo75 no offense but your talking to Linux folks. We tend to jump the gun with are replys instead of thinking sometimes.

My standard?  I would hope everybody would at least expect the first reply to a question to be an answer or a good suggestion, and not an implied personal opinion that changes the subject and derails the thread.  Did I ask for a cost comparison between backup methods?  No!  Because if you really wanted to debate about archiving on burned media versus MAGNETIC media, burned media wins hands down (provided you store it in a cool, dry place).  I didn't want to waste my time expressing that to someone who felt like wasting their time telling me to back up data the way THEY backup data.

So again, I am looking for software.  Not a debate about method or personal preference.  Thanks!

---

### Post by diablo75 on 2008-06-29
I found better help elsewhere.  [This thread]("http://ubuntuforums.org/showthread.php?t=844263") is a great example of  what I was originally expecting to see here.  Until *somebody *decided to turn it into a arbitrary debate.

---

### Post by hyper_ch on 2008-06-29
> **diablo75 said:**
> Until *somebody *decided to turn it into a arbitrary debate.
you speak of yourself in the 3rd person?

---

### Post by robertchahine on 2008-06-29
we need a moderator in this thread :D

---

### Post by cleopete on 2011-03-15
Diablo might be a little peevish, but they're right: no one answered the actual question.  I got directed here 2 1/2 years later because I need a spanned disk back up as well.  I am backing up 10 GBs for a client, and I don't particularly want to buy them a stupid external drive.

Any idiot could see an  external would be easier, probably why they (and I) were/are looking for help with a more difficult route.  Why didn't you just suggest Carbonite, or not backing up at all?  Makes as much sense.

If you don't know, don't waste web space.

---

### Post by gypaete09 on 2011-08-24
> **robertchahine said:**
> we need a moderator in this thread :D

For those like me, who look for a *real* answer to a (quite common) problem, reading this thread is disappointing, to say the least.

I'll move on to more constructive threads :-|:-|:-|

---

### Post by psylencer on 2011-08-24
> **diablo75 said:**
> Because it's cheaper?

You say its cheaper???  Do you have a job?  If so lets say you get paid $20 an hour.  

Im in Aus - a pack of DVDs (say 25) cost me around $20-30.

Now you have 30GB of Data right? 30GB/4.7 = 6.3 (7) discs

Time taken to burn 7 discs?  Im guessing around 5 or 6 hours. Thats IF the process was reduced to "insert new disc..."  Trouble is that isn't the case no matter how good your process is.

So IF you do work and earn $20 an hour - this process has cost you 7hrs x $20 PLUS the cost of the discs ($140+).

So you've spent $140+ so far and what have you got?  
A bunch of discs that took forever to make, get scratched, take forever to load (even at 40x) and you COULD have purchased a new 500GB HDD which would have had your problem solved quickly ,reliably with no disc changing or scratching for around $50.

Sometimes it's best to do thing the right way despite the apparent "savings" you most probably won't receive by doing things the wrong way.

---

### Post by js4ndstrom on 2011-09-25
Here is how I do it:

# 1 divide myBigFolder into several dvd bite-sized folders using hardlink copies:
dirsplit -s 4300M -e2 myBigFolder -L -p myDvdBackup_

# 2 create isofile for burning:
genisoimage -J -R -o myDvdBackup_1.iso myDvdBackup_1/

# 3 burn isofile to dvd:
wodim -v myDvdBackup_1.iso

---

### Post by coffeecat on 2011-09-25
This is an old thread and the OP has not posted in it for more than three years. If anyone wants to discuss the subject of backups you are welcome to start a discussion thread in a non-support area such as the Community Cafe. If anyone need technical support on this issue, please start a fresh thread in a support area. And now...

Back to sleep.

Closed.

---


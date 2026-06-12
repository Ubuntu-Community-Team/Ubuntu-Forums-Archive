---
title: "Creating a maintenance script; I need everyone's help"
date: 2007-03-21
forum: Programming Talk
---

### Post by mozkaynak on 2007-03-21
Hello,
I would like to create a script (probably a bash script but may need to use some python)
that will maintain my ubuntu system.
I am a beginner bash and python programmer (I have lots of Visual basic and Pascal experince though).
This script will run periodically and perform some maintain jobs.
This is a project I take very serious and also a good learning opportunity for me.
So, my question is what are the periodical maintenance tasks that should be carried out by Ubuntu?
currently I have two tasks:

cleaning the cache > sudo apt-get clean
cleaning the recycle-bin > rm -rf ~/.Trash/*


what other things should be done to the system periodically?(if you know terminal command of that please let me know too)
Once I collect all ideas I will start coding it.

I will share the final code and all upgrades in this forum.


Thanks in advance for your help....

---

### Post by raja on 2007-03-21
Hello !
I have been interested in a similar script. I actually wrote up one for use at my work pc. I wrote it in Python since it was quicker to write that way, but probably bash would be the more 'native' way to do it. 
The way I have it now, it clears trash that is more than 10 days old, clears my downloads folder of items more than 10 days old and does an apt-get clean. So, my first suggestion is that you should try to allow a variable period to be set so that only trash older than that will be discarded. 
I am surely interested in this, think it will be useful. If you want any help in this, I am ready.

---

### Post by jrib on 2007-03-21
> **mozkaynak said:**
> Hello,
I would like to create a script (probably a bash script but may need to use some python)
that will maintain my ubuntu system.
I am a beginner bash and python programmer (I have lots of Visual basic and Pascal experince though).
This script will run periodically and perform some maintain jobs.
This is a project I take very serious and also a good learning opportunity for me.
So, my question is what are the periodical maintenance tasks that should be carried out by Ubuntu?
currently I have two tasks:

cleaning the cache 
cleaning the recycle-bin 


what other things should be done to the system periodically?(if you know terminal command of that please let me know too)
Once I collect all ideas I will start coding it.

I will share the final code and all upgrades in this forum.


Thanks in advance for your help....

For the trash thing, you'll want to be careful.  If you use that command and say run it every week, it may happen that you delete something, the next minute that command runs, and then you decide to go to your trash and retrieve it and it is gone!  An idea you might want to consider is to check when the file was deleted and delete only after 20 days.  Maybe there is something that does this already.

---

### Post by mozkaynak on 2007-03-21
some more ideas from #ubuntu-chicago IRC channel



> 
(08:36:02 PM) mozkaynak: I started this post in the forum
(08:36:10 PM) mozkaynak: but a few people responded
(08:36:27 PM) mozkaynak: I am just wondering whether you guys may wanna contribute
(08:36:50 PM) Red_Herring: umm.......
(08:36:54 PM) Red_Herring: you might wanna make it apt-get update
(08:36:56 PM) Red_Herring: and apt-get upgrade
(08:37:09 PM) Red_Herring: and clean up the cache for firefox and konqueror
(08:37:24 PM) mozkaynak: these are good
(08:37:34 PM) Red_Herring: ummmm.......
(08:37:35 PM) mozkaynak: keep thinking please
(08:37:46 PM) Red_Herring: everything else already takes care of itself
(08:37:50 PM) Red_Herring: if you REALLY wanna get picky
(08:38:03 PM) Red_Herring: you could rm the old log files in /var/log/
(08:38:32 PM) mozkaynak: ok
(08:38:41 PM) mozkaynak: thanks alot for your feedback
(08:38:49 PM) Red_Herring: no problem


---


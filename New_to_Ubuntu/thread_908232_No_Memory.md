---
title: "No Memory"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by browncoatrebel on 2008-09-02
Total noob here, so please be patient with me....

I have a dual boot system and was trying to install program updates in Ubuntu.  During that process, it told me I didn't have enough memory, so I tried to remove some programs I don't use through Add/Remove Programs.  When I tried to remove them, it gave me an error message telling me to remove the programs using Synaptic Package Manager.  However, when I tried to use Synaptic Package Manager, it gave me an error telling me there wasn't enough disk space to run.

Now I have only marginal system functionality in Ubuntu.  I can run Firefox but none of my add-ons work, nor do the back and forward browser buttons.  Thunderbird will open and check my mail, but I can't reply.  OpenOffice won't open at all; I just get error messages.

Help me out: I have *no* idea what to do.  If I get rid of excess files and programs on my Windoze OS, will that clear out enough space that I can then run Synaptic?  Or is there something else I should be doing?

Apologies, again, for the total noob-ness of the question.

---

### Post by snowpine on 2008-09-02
Hi Browncoat, this happened to me once before. Basically, you need to clear up some space on your Ubuntu partition before you can do anything useful. Empty your trash, delete some personal files you no longer need, clear your Firefox temporary files, etc. Until you clear a little bit of space, programs like Synaptic just won't work. :)

---

### Post by Sef on 2008-09-02
Applications > Accessories > Terminal

paste or type these two codes into the terminal (one at a time):

```
sudo apt-get clean
```

```
sudo apt-get autoremove
```

---

### Post by jemate18 on 2008-09-02
> **browncoatrebel said:**
> Total noob here, so please be patient with me....

I have a dual boot system and was trying to install program updates in Ubuntu.  During that process, it told me I didn't have enough memory, so I tried to remove some programs I don't use through Add/Remove Programs.  When I tried to remove them, it gave me an error message telling me to remove the programs using Synaptic Package Manager.  However, when I tried to use Synaptic Package Manager, it gave me an error telling me there wasn't enough disk space to run.

Now I have only marginal system functionality in Ubuntu.  I can run Firefox but none of my add-ons work, nor do the back and forward browser buttons.  Thunderbird will open and check my mail, but I can't reply.  OpenOffice won't open at all; I just get error messages.

Help me out: I have *no* idea what to do.  If I get rid of excess files and programs on my Windoze OS, will that clear out enough space that I can then run Synaptic?  Or is there something else I should be doing?

Apologies, again, for the total noob-ness of the question.

Would you type this in the terminal
```
top
```
to see which program is using a lot of memory

what is the output of these
```
free -m
```
this will show the memory utilization

---


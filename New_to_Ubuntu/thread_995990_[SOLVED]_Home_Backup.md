---
title: "[SOLVED] Home Backup"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by mesmith on 2008-11-28
What's a quick easy way (gui preferably) to backup my Home directory to DVD.  Something fool proof that will allow me to save things in case of HD failure, etc.

Mike

---

### Post by roger_1960 on 2008-11-28
Hi

In synaptic have a look at pybackpack which might well suit.

> **mesmith said:**
> What's a quick easy way (gui preferably) to backup my Home directory to DVD.  Something fool proof that will allow me to save things in case of HD failure, etc.

Mike

---

### Post by mesmith on 2008-11-28
Installed it.  It looked fine, but hangs at the point of writing the CDR.  Anything else?

Mike

---

### Post by edcouch on 2008-11-28
I installed grsync, and it works really well.

---

### Post by halitech on 2008-11-28
look at remastersys, its not in the repos (I don't think) but it gives an option to do a live cd of everything or just folders  you select.

---

### Post by kansasnoob on 2008-11-28
If you're creating a backup to CD/DVD I really like K3B.

This is how it works:

[ATTACH]94530[/ATTACH]

You see I've highlighted "new data project". then if you drag-n-drop "Home" from the menu at the left you'll see this:

[ATTACH]94529[/ATTACH]

The rest becomes self explanatory! Of course I want the hidden files!

---

### Post by richg on 2008-11-28
I first backup files to a external hard drive once a week or more. Turn off the HD. I then use k3b for backing up to a DVD. I use the verify data option also. I store the DVD off site.

Rich

---

### Post by mesmith on 2008-11-29
I installed k3b.  It looks like it will work just fine.  Haven't tried it yet because when I dragged the Home directory to the lower left panel it dropped in directory Mike, which is under Home.  That's okay I suppose, and I did tell it to include hidden files.  But then, it asked me about following "symbolic links" and I hadn't a clue how to answer.  Yes, no, now, always???  What exactly is this about, before I get carried away?

Mike

---

### Post by mesmith on 2008-11-30
Thanks for all your help.  All of you.  Looks like k3b will be my choice and should be just fine for what I want to accomplish.

Mike

---


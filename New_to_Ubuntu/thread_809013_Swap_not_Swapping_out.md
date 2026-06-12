---
title: "Swap not Swapping out"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by philipluna66 on 2008-05-27
With youre help I thought increasing my swap file from 385mb to 895mb would solve the problem of my swap file showing full on my widget. I have left my computer running all night running Ktorrent downloading 5 items. Yesterday my swap was 227mb full This morning it was 844mb full.My compute was very slow to operate Either my widget is telling lies or things are building up in my swap file. What is causing this and can I do anything to stop it apart from keep rebooting

---

### Post by Trail on 2008-05-27
Try opening a terminal and typing "free -m". This will show you the actual swap file usage. For example:

```

             total       used       free     shared    buffers     cached
Mem:          2025        960       1064          0         23        720
-/+ buffers/cache:        216       1809
Swap:          980          0        980

```

So currently I use 0MB of swap (and 216MB of RAM for applications by the way). I rarely, if ever, swap.

---

### Post by philipluna66 on 2008-05-27
Acording to yesterdays figures I had 385nb swap and 375mb ram. When I shut it down this morning I was using 844mb swap and 301mb ram It just semes to be building up the longer I use my computer. OK what is youre secret how can I stop it doing this. Please keep it simple I am new at this.

---

### Post by Trail on 2008-05-27
Hmm. I am pretty sure Ktorrent has an option controling how much RAM it will use. Try setting this lower.

Also, if you close ktorrent, does it stop using all that RAM? If it does, then it sounds healthy (your system just tries to use all the resources fully, which is good).

---

### Post by reeseslover531 on 2008-05-27
Also if you want you can adjust the swappiness of your 
computer.  This will adjust how much real ram and how much swap the machine uses.  Edit your /etc/sysctl.conf file and look for the vm.swapiness line.  It is probably currently  set to 60 the lower the number the more real ram it will use.  The total memory used shouldnt be any different though.  How much ram do you have???

---

### Post by philipluna66 on 2008-05-27
Ok this sounds complicated I would like you to spell it out for me please I have to put sudo first in the terminal window yes. I have 375mb ram No if I dont use Ktorrent my computer is Ok I think but I have never used it that long to see for anything else I am still experimenting with Ubuntu as dare I say it I have been a windows user for years and all this terminal busines scares me I am frightend of bugering it up
ALL I GET WHEN I ENTER /etc/sysctl.conf is permision denied

---


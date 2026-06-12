---
title: "Tip on hdparm"
date: 2007-01-09
forum: Outdated Tutorials &amp; Tips
---

### Post by jester45 on 2007-01-09
First think about the help im giving is that your doing this on your free will so if it breaks im not going to help you, sorry. Second is that these are done on a 32bit xubuntu edgy install the computer has 192mb of ram a 80gb WD drive (not sure on what kind the label is gone) a 400mhz 128kb L2 cache so your results my differ 

Now on how i did this, i booted up the computer like normal and opened a terminal and thats all i opened during all of the test and i didn't restart i reset the options after the 4 test on each option i also didn't use --direct on any of these. Also all the speeds are MB/s and all test are with internal drive read ahead unless noted

the best way to test the speed is with --direct but i didn't use that so what i used was 
hdparm -Tt /dev/hda

an example of the test would be 
Test # cache drive

what i found that worked the best for simple options was -d1 that enables DMA
Test1 132.94 12.45
Test2 150.89 17.38
Test3 138.89 15.88
Test4 139.46 15.88
Average 140.9 15.23

-c1 enables 32bit transfer 
Test1 158.54 3.72
Test2 149.34 3.94
Test3 154.90 4.35
Test4 147.42 4.32
Average 154.58 4.08

-c3 enables 32bit transfer with sync
Test1 144.54 3.83
Test2 163.40 3.49
Test3 137.47 3.67
Test4 127.71 3.43
Average 143.28 3.60

nothing special but internal drive read ahead
Test1 151.44 2.56
Test2 159.88 2.31
Test3 131.06 2.08
Test4 141.75 2.56
Average 146.03

-A0 nothing special including no internal driver read ahead *NOTE*The drive read is in KB/s
Test1 138.68MB/s 474.31KB/s
Test2 157.07MB/s 475.48KB/s 
i quit testing after 2 becuase they were to slow and pointless

-a24 software read ahead plus my drives internal
Test1 136.62 2.50
Test2 157.82 2.56
Test3 149.23 2.47
Test4 154.42 2.47
Average 155.21 2.50

-u1 unmasking of the I/O interruptions
Test1 151.07 2.52
Test2 137.37 2.15
Test3 141.88 2.34
Test4 148.52 2.51
Average 144.71 2.38

-m16 i used -i to find a good setting for my drive WD suggest about 16, 16 or 32 are good
Test1 131.30 2.45
Test2 144.61 2.69
Test3 153.94 2.40
Test4 148.55 2.63
Average 144.6 2.54

and last i combined all of them  -d1 -cc1 -a24 -u1 -m16 -A1
Test1 157.25 17.32
Test2 161.88 17.63
Test3 158.13 17.03
Test4 158.35 16.97
Average 158.90 17.74

i have yet to decide what is better i think i will be going with the combo and might remove a few options or mess with a higher -m setting

if anyone has something to add or me to change post a reply or email me at [email]Jester456@nerdschack.com[/email] you can get a hold of me there faster also you can try irc.freenode.net #xubuntu im in there often

---


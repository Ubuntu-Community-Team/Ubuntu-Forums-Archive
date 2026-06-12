---
title: "Newbie Intro"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by darkspryte on 2012-04-15
Good gawd...I'm so new to ubuntu I'm not even sure how to tell what version I have.  It's been ages since someone installed it.  And at the moment I don't have a clue as to how to set up an internet connection with a wireless adapter.  Until some kind soul comes along with the patience to walk me through it, I'm scouring the forums and google search on an ancient laptop w/XP.  ](*,) 

Anyhow, glad to be here...it is time, I guess.  Been putting this off for too long.

---

### Post by Ma7moud on 2012-04-15
I have the same problem. guys do you have an installation manual to helps the first time users.

---

### Post by Rodney9 on 2012-04-15
Welcome.

1. Help Guide to Ubuntu Oneiric version 11.10

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric](http://ubuntuguide.org/wiki/Ubuntu_Oneiric)

Linux is Not Windows

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Very good pictorial Install Guide

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

10 Things to after Installing Ubuntu

[http://www.omgubuntu.co.uk/2011/10/1...-ubuntu-11-10/](http://www.omgubuntu.co.uk/2011/10/1...-ubuntu-11-10/)

---

### Post by bkratz on 2012-04-15
> **darkspryte said:**
> Good gawd...I'm so new to ubuntu I'm not even sure how to tell what version I have.  It's been ages since someone installed it.  And at the moment I don't have a clue as to how to set up an internet connection with a wireless adapter.  Until some kind soul comes along with the patience to walk me through it, I'm scouring the forums and google search on an ancient laptop w/XP.  ](*,) 

Anyhow, glad to be here...it is time, I guess.  Been putting this off for too long.


A good place to start would be to post the outputs of the following terminal commands. ( use cntrl--alt--t to access the terminal).  Copy/paste the response to

```
cat /etc/lsb-release; uname -a 
lspci -nnk | grep -iA2 net

```


back here. It will give the version and networking info.

---

### Post by audiomick on 2012-04-15
> **darkspryte said:**
> Good gawd...I'm so new to ubuntu I'm not even sure how to tell what version I have. 

Look for a program called "system monitor". On version of Ubuntu before 11.04, it should be in the menu system> administration.
The first tab in that will tell you which version you have. It doesn't say whether it is a 32- or 64- bit version, but if your machine is that old, it is most likely 32-bit.

---

### Post by morhin on 2012-04-15
I'm running 10.04 (Lucid Lynx) and as a newbie I'm going to stick with this til 12.04, the latest release, gets settled. in.
Just so you know 10.04 is the date as well as the release number. In other words 10.04 came out in April of 2010. It is what the call a stable release. All the ones that followed are betas. The next stable release is out this month, April of 2012 so it is called 12.04.
Moving along.
I tried several linux releases and finally found ubuntu. But even then I struggled until......
Ubuntu for Non-Geeks by Rickford Gran with Phil Bull.
This book is amazing. 
The printer will be putting a new one out for 12.04 so I'll watch for it and you better believe I'll be adding that to my library. Best and easiest I have found for getting me going.
To be honest I'm not sure I'd have stuck except for this book

Have fun, have patience....

):P

---


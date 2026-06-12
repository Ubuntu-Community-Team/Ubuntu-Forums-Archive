---
title: "GPL -  Restrictions and uses?"
date: 2015-01-08
forum: Programming Talk
---

### Post by flaymond on 2015-01-08
Hello guys! I love Linux and really love to explore it much further. As well, Linux is under GNU projects..I'm curious with the GNU Public License (GPL). So here is my question - 

> 1. Does using GPL is free to anyone, any age, any countries?

                2. Does using it need an approvement?  - (Example...I just made a simple program and release it under GNU without asking anyone that related for fun)

                3. What type of projects that can be released under the GPL?

               4. (If you willingly to help) - What are the restrictions to use ? (If there is). 


 Thanks so much!

---

### Post by Lars Noodén on 2015-01-08
You can read the [GPL license itself](https://gnu.org/licenses/gpl.html) at the Gnu site.  You can also read a comparison of it to other FOSS licenses at [OSI](http://opensource.org/licenses)

In short,

1. yes

2. yes, but only by the copyright holder(s) for the project

3.  any

4. you must follow the license(s) of software you have, the GPL is no different

---

### Post by flaymond on 2015-01-09
Thanks for you help Lars!

---

### Post by Lars Noodén on 2015-01-10
Yes, whoever is the copyright holder for a project or code can decide the license. 

Linus moved the kernel to the GPL early on and considers it [the best thing he ever did](http://www.tlug.jp/docs/linus.html), even in recent interviews he has mentioned as much.  

A fine point is that some licenses cover only copyright and others cover patents and some cover both.  Of the GPL licenses, the GPL v 2 is pure copyright and the GPL v3 also include patents.  Patents govern usage, regardless of origin of the code, and copyright governs (re-)distribution.  Then there are also trademarks and trade secrets, but they are not mentioned so much as copyright and patents.  People, usually out of either ignorance or an agenda, might lump them together, but they are all quite separate.  

Searching around a little, I am finding a few recent negative articles about the GPL.  These seem to be attributable to [Black Duck](http://techrights.org/wiki/index.php/Black_Duck), with ties to MS, and using [questionable data](http://techrights.org/2014/12/30/black-duck-debunked/).   Same for Redmonk and outercurve.  They seem to have some limited success in saturating the channels of late.  

For what it's worth, [Github has an online tool to go through the decision tree you have when choosing a FOSS license](http://choosealicense.com/) for your project.  The reason they have it is to encourage people to choose a license, any license, because if you don't have one for your code, then in the Berne Convention countries your code is all rights reserved and not usable.

---


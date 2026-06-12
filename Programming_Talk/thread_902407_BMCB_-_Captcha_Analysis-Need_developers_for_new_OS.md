---
title: "BMCB - Captcha Analysis-Need developers for new OSS project"
date: 2008-08-27
forum: Programming Talk
---

### Post by sumdog on 2008-08-27
For the past several months I've been working on an engine written in Java for filtering, segmentation and analyzing CAPTCHA; in effect trying to measure the accuracy of several different CAPTCHA analysis techniques. The engine is pretty robuts and useful, however it contains just a few basic analyzers. 

I'm looking for developers who'd want to help me on this project. I know some of you may be concerned about the ethics of braking CAPTCHA and publicly releasing an open source engine for it, but I believe that by developing techniques and analyzing them, we can design better CAPTCHA, possibly even combing the research with human trials eventually to see which CAPTCHA types are easier for people to recognize yet harder for machines to analyze.  

In anycase, please check out the project [http://penguindreams.org/page/see/Bmcb](http://penguindreams.org/page/see/Bmcb). Any help/contributions would be greatly appreciated.

---

### Post by Wybiral on 2008-08-27
There's already been an algorithm that's proven to break captchas with the same efficiency of human beings. It's called the "make a human solve it" algorithm :)

No, seriously, there are websites (usually porn) that mirror captchas from emails signups and other captcha-blocked accounts and have the users solve the captchas thinking it's for their site, when it's really for a spam account.

Watch this: [http://www.youtube.com/watch?v=dtFroEJN1nI](http://www.youtube.com/watch?v=dtFroEJN1nI)

But I imagine you're more interested in the OCR/image recognition aspects than the general efficiency? I've seen more complicated captchas asking things like "how many cats are in this picture" and such (which I imagine will be VERY hard to break for a very long time)... But even those are subject to being mirrored on other sites.

---

### Post by sumdog on 2008-08-27
I actually address CATPCHA farming-by-proxy (getting others on a porn site to do your CAPTCAH for you, a.k.a. the virtual stripper) and using alternative CAPTCHAs in my thesis paper, which is what this project was for.

The engine itself just deals with the text based CAPTCHA, which is the most common type you see on the Internet. My thesis got rejected because there wasn't enough analysis on my results (I only had like a 3% success rate). Rather than revise it with more analysis on why it wasn't successful, I was hoping I could turn the project around. The engine is solid, but I'm just not sure how to approach the problem using machine learning and I don't have a good understanding of image filtering or shape recognition either.

---

### Post by hod139 on 2008-08-27
Wybrial, here is the page on [kittenAuth]("http://www.thepcspy.com/read/the_cutest_humantest_kittenauth")

---


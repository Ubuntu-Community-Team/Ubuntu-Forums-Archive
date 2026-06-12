---
title: "Hardy screen resolution: Have the monkey's on the keyboard stumbled on a bug?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Jonas thomas on 2008-05-11
I had been stuck in 840X600 screen resolution for about 2-3 weeks(I've lost track) until I indirectly stumbled on something that actually works.  I'm thinking that there are some critters in Hardy but am looking for a second opinion.
Here's what happened:

Machine#1
Graphics: Intel 82815
Monitor: CTX PL9
Gusty Live session CD has 1200+ resolution
Hardy 8.04 stuck on 840 X 600
**If I get good screen resolution on Gutsy and bad on Hardy, Wouldn't this be considered a bug? A rose by any other name???**

Ok... So after about a week or so of messing around with this. I thought perhaps it was an issue with my old hardware and I thought I would try some less old hardware a try.

I created a dual on my XP machine
Machine#2
Graphics:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
Monitor: CTX PL9 [I'm running on a KVM]
After Install: Exact same problem stuck at 840 X 600

So I basically tried everything until I stumbled on this:
I downloaded the manufactures driver:[http://ubuntuforums.org/archive/index.php/t-609006.html]("http://ubuntuforums.org/archive/index.php/t-609006.html")
These instructions didn't see to work for me but I think it gave me the opporutunity to enable the third party drivers under System=>Administration=>Hardware Drivers. I did that and it basically failed. But then something very cool happened: Somehow I got a manual configuration list to popped up and I manually selected the monitor and graphics card that I had on my box.  I tested it within the Gui.  It said it failed.  I saved it within the Gui, rebooted and now it's working fine as far as screen resolutions is concerned. (Until I understand what happened, I reluctant to try special effects). 
**_Questions_**:
I'm not sure if this manual configuration Gui comes out of the initial Hardy install or if it was something that I loaded when I was in my monkey mode of trying everything:
1)Is this manual configuration Gui Party of a initial Hardy install?

2) Is there a way of directly accessing this selection GUI, without having failed 3rd party drivers?

3) My suspicion is that the root of my problems is my CTX pl9 monitor. Does that seem plausible?

4) Since I get screen resolution using live session of Gusty and It fails under Hardy, this seems(to me anyway) to be a bug.  I've seen hundreds of posts of similar problems.  I still a relative newbie at Ubuntu-Linux... What is the proper protocol for reporting this bug?

Thanks,
JT

---

### Post by SIXAXIS on 2008-05-11
I think that's a bug that has to do specifically with your monitor and 8.04. These kinds of bugs happen to me too. Like, the special effects with the Live CD worked with 8.04, but not with 7.10. There were some things that worked with the Live CD that didn't work with the complete installation.

---


---
title: "Graphics - Weird graphical glitches with Xubuntu 14.04 including folder icons missing"
date: 2014-08-19
forum: New to Ubuntu
---

### Post by Dale_P on 2014-08-19
I&#8217;ve just installed the above version on my ailing Dell Dimension tower PC - great to be able to get it up and running again...


The only thing is that there seems to be a strange graphics issue - some of the icons in finder windows disappear on mouseover. Also, the system has a habit of randomly highlighting text in strange colours so that it is unreadable. Very odd.


As the problem is quite difficult to explain in words, I&#8217;m made a short screencast video on Youtube to share the problem as it appears to me: [http://youtu.be/VN0uQ_kjHcg](http://youtu.be/VN0uQ_kjHcg)


Any help greatly appreciated!

---

### Post by Rob Sayer on 2014-08-19
That's not actually a YouTube link, and I'm certainly not going to click on it.

---

### Post by Dale_P on 2014-08-19
Hi Rob,

The link I posted is a shortened version - here's the full link: [https://www.youtube.com/watch?v=VN0uQ_kjHcg](https://www.youtube.com/watch?v=VN0uQ_kjHcg)

Do you know what could be causing this?  I see there's not been much bite on this post, and unfortunately the folder structure of the system is rather unusable with this issue.

Thanks a lot for your time.

---

### Post by dave131 on 2014-08-19
I just watched you video and indeed that is strange.  What is your video adapter?  Try:

lspci | grep VGA

and post the output back here.

Is this an on-board GPU or is there an actual video card?

If on-board GPU, check the BIOS settings and post back what it says for video memory.

If may be a driver problem as well.

I *think* the above information should at least get everyone started.

---

### Post by Dale_P on 2014-08-19
Thanks Dave, I've run the command and here is the output:

> **dave131 said:**
> 

Try:
lspci | grep VGA
and post the output back here
.

01:00.0 VGA compatible controller: NVIDIA Corporation NV17 [GeForce4 MX 420] (rev a3)

> **dave131 said:**
> 
Is this an on-board GPU or is there an actual video card?


Not sure how to find this out?  I downloaded the sysinfo package, which says this (basically the same as the above command output)

[IMG]http://i.imgur.com/pc9baIt.png[/IMG]
[http://imgur.com/pc9baIt](http://imgur.com/pc9baIt)



> **dave131 said:**
> 
If may be a driver problem as well.

I suspect this may be the case too.  However, there are no items shown in the 'additional dirvers' menu.

> **dave131 said:**
> 
I *think* the above information should at least get everyone started.

Hope so! do let me know if there's anything else which would be hlepful...

---

### Post by monkeybrain20122 on 2014-08-19
See if this thread helps
[http://ubuntuforums.org/showthread.php?t=2228137](http://ubuntuforums.org/showthread.php?t=2228137)

---

### Post by dave131 on 2014-08-19
Basically, that thread lets you know that the card is not really supported in 14.04.  They got it to work in Linux Mint - but that may be too heavy for your system if you had to run xubuntu.  The other alternative mentioned there is linux lite.   If worse comes to worse, and if this is a seperate card, you could try a different video card.  However, if it's a laptop or if you are using on-board graphics (the hint would be if you are connected to a video output that is in with a bunch of ports on the back of your system, or if it's connected to something else).

---

### Post by Dale_P on 2014-12-23
Just a follow-up to this post.  The issue was indeed due to a an unsupported graphics card, which was fixed by swapping the card. Everything now works fine!  Thanks for all your help... :-)

---


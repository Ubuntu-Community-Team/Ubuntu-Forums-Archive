---
title: "General Hardware and LINUX OS question.  Am I going in the right direction?"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by rick19 on 2014-03-26
Hello all,

I'm a old world programmer from the mainframe days and a tinkerer / entrepreneur. I've built, modified and maintained PCs since they became available in the days for the Intel 8088. I also know my way around DOS, Windows, Networking and electronics. I have no practical LINUX experience but have bumped into it through some diagnostic tools I've used in the past.

I came up with an idea and I'm currently researching the technology platform(s) in which develop.

My idea is basically a remote accessed and controlled multimedia display. Display will be a standard PC type LCD on which I'd like to display slideshows and movies with stereo sound. (In the future I'd like the flexibility to hold SKYPE type communications in order to communicate with remote locations....for another conversation down the road)

I don't want to stream content to the remote display. Therefore, I'm leaning towards incorporating a networked SBC (Single Board Computer, Ala Raspberry Pi etc) into the display. I'd like to upload images (JPG, BMP, PNG etc) or video (MOV, MPEG4, AVI WMV) to the SBC.  From there the images will be displayed in a slideshow.....continuously. Other than that video clips may be utilized on a on-demand basis. In other words, the slideshow will be interrupted after some type of physical trigger is tripped and the video clip will commence. When done the slideshow will resume. That's pretty much the extent of the initial functionality required.

So, I've been researching SBCs with the following criteria:
[LIST]
[*]Well supported / robust community 
[*]Company with proven track record in the industry (Will be around for a while) 
[*]Ability to withstand 24/7 operation 
[*]Relatively inexpensive 
[*]Flexibility with software (OS?) and hardware (SD, HDMI, DVI etc) 
[*]Expandable via add-on modules (Camera add-on etc) 
[/LIST]

There's a lot to consider.

With this in mind, and with the SBCs I'm considering, the two OS platforms I'm looking at are android and LINUX.  At this point I really don't see Android as an appropriate suitor.
Here are some of the criteria I'm using for the OS.
[LIST]
[*]No licensing fees (or at least minimal) I believe this kills the PC104 / Windows platform. 
[*]Robust support and user community 
[*]SECURITY (Especially since content will be uploaded remotely) 
[*]Configuration ease 
[*]Small footprint and low overhead 
[/LIST]

If the first few prototypes go well the potential for implementing many of these units is possible.


Can anyone comment or offer advice on the info / idea I've outlined? Is LINUX a viable platform? Any tools, software, hardware, OS variations or other suggestions on where to start?

All feedback is greatly appreciated.

---

### Post by PartisanEntity on 2014-03-26
Hi there,

You did not mention specifically which flavour of Linux you are considering. Since you are posting here on the Ubuntu Forums, I assume Ubuntu is one of the flavours you might be considering.

If that is the case, then I just want to point out that Ubuntu does not support the ARMv6 architecture that the Raspberry Pi uses. So for the Raspberry Pi unfortunately Ubuntu will not be an option.

Other than that, I think for what you would like to do Linux is a very viable option, it is scalable, flexible and you can mix and match the components and packages that you want.

---

### Post by rick19 on 2014-03-26
Thank you for your feedback. My research did not go deep enough to determine compatibility between the Linux version and the ARM core. (Was v6 supported at one time?)

After a bit of reading I see a match between **Ubuntu** and one of my other picks, the **Panda** (ES) board ([Cortex-A9]("http://en.wikipedia.org/wiki/ARM_Cortex-A9_MPCore") (v7)). 

If you were to select a combo for a similar project would these two be on your short list? Any other products I should be considering?

Thanks again.

***Update:** After searching for a Panda ES I'm finding virtually none available. Not good. If I need a large quantity this will be an issue.*

---


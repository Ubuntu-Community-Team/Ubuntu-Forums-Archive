---
title: "crashing,freezing,turning gray, general pain"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by rootessa on 2011-10-04
Problems, problems and more problems!
This computer has run flawlessly for about  3 months. :P This problem seems to have begun with  things loaded from Update Manager or maybe that's just coincidence.idk. This is 1st turning gray, 2nd, freezing and then 3rd, crashing about every 10-30 minutes. The problem is not with Firefox or Opera as I've tried all day to work in Open Office offline and it continues to happen. Suggestions? Anyone? Please? Need more info? I'll do my best! Thanks in advance!

---

### Post by mastablasta on 2011-10-04
yes need more info. it could be: software error (you should be able to make an erro log), faulty ram (run memtest, might take a while), faulty graphics card, faulty motherboard (open the box and check capacitors if any are bulged or leaking)).

---

### Post by rootessa on 2011-10-04
I've been trying to troubleshoot this myself and did find my graphics driver(s) are way out of date. This computer is running a 1.5 version which needs to be update to a 7.10.3 version. Could this be the problem? Been knocked offline for 5 days due to weather. Just getting back on to try to solve this. Thanks for your info!

---

### Post by audiomick on 2011-10-04
I'd do a couple of "hardware" things first, to try and exclude that possibility. My reasoning is that something has changed. Your graphics drivers have been working up till now, so why should they suddenly not work?

Open the box and make sure it isn't full of dust and getting hot. Observe all the fans to see if they are working. Check that cables are properly seated.

Run memtest. You should let this run for a long time. Overnight is good. If your RAM is ok, you will get zero errors. If you get errors, take out the RAM one stick at a time and run it again to isolate where the problem is.

Your problem sounds a lot like problems I was having just recently with faulty RAM.

Memtest is in the menu of the live CD, if you were wondering where to find it. It is in the Grub menu too, if you see that on boot up. I generally run it from a live CD or USB, but only because that is easier for lazy me than to figure out how to make the computer show the Grub menu at boot. :D

---

### Post by ajsoulmate on 2011-10-04
> **audiomick said:**
> I'd do a couple of "hardware" things first, to try and exclude that possibility. My reasoning is that something has changed. Your graphics drivers have been working up till now, so why should they suddenly not work?

Open the box and make sure it isn't full of dust and getting hot. Observe all the fans to see if they are working. Check that cables are properly seated.

Run memtest. You should let this run for a long time. Overnight is good. If your RAM is ok, you will get zero errors. If you get errors, take out the RAM one stick at a time and run it again to isolate where the problem is.

Your problem sounds a lot like problems I was having just recently with faulty RAM.

Memtest is in the menu of the live CD, if you were wondering where to find it. It is in the Grub menu too, if you see that on boot up. I generally run it from a live CD or USB, but only because that is easier for lazy me than to figure out how to make the computer show the Grub menu at boot. :D

I second that.

---

### Post by Mark Phelps on 2011-10-04
Could be an incompatibility between the video drivers and a recent kernel upgrade.  

So, boot into GRUB and select an older kernel version -- one before the recent updates.  

If the problem goes away, that conflict is the trouble.

Freezing and crashing after the PC has been on for a while is most frequently the result of overheating.  Dust and dirt buildup in fans and heatsink fins is a common source of this problem.  Need to open the PC case and clean it.

---

### Post by rootessa on 2011-10-06
You are all wise, intelligent and interesting people! Again, I've been knocked offline for 2 days so I couldn't come look at your posts. Very strange thing has happened, completely by accident. I'm house sitting in a place that's completely not computer friendly. This is a laptop and I've had it propped up on a notebook that's much smaller than it is and the problem has completely stopped. Lightbulb moment! Air circulation! I never in a million years would have thought of it!(I always think worst case scenario first!) Yes, it's pretty dusty so I guess I know what my next job is! By George, I think you've done it!
I'm going to run a memory test just to see what it looks like. Insatiable curiosity!
Thanks again! :p

---

### Post by verymadpip on 2011-10-06
I have a friend (amazing in itself :)) who fairly recently bought a new laptop for his wife.  She has to have the front end of it propped up on coasters (the little table mats for mugs & cups) in order for the machine not to overheat.

Technology; here to make life easier ;)

---

### Post by audiomick on 2011-10-06
> **rootessa said:**
>  Lightbulb moment! Air circulation! I never in a million years would have thought of it! 
How often have I started looking for the "digital problem" only to find the cable isn't plugged in? :lolflag:
Open it up and give it a clean. Glad it was so simple.

> 
I'm going to run a memory test just to see what it looks like. Insatiable curiosity!
Thanks again! :p
Never a bad idea. Let it run for several hours, maybe overnight.

---

### Post by illyoung on 2011-10-06
I hope the problems had gone.
But, if you still have problems like that.
I'm thinking you should check your network status.

Previously, I've encountered a little bit same problem, and it turns out that some other not authorized people uses the ip allocated to my desktop.

BTW, where do you use your ubuntu system? in the office or at home?
If it's problem with network, the solution or the reason would be various.

---


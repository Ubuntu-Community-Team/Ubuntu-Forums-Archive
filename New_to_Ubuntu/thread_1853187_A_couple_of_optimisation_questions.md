---
title: "A couple of optimisation questions"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by blueghoti on 2011-10-01
Hi - 

A couple of quick questions I wonder if the community could help with please....

1/ I toggled a setting a while back so that I could get a listing of "hidden" files when I browse in directories...  so I see a lot of files starting with a . 
How do I turn this off (and shorten my list?)

2/ my system feels slower on bootup than in the past.  Where would I go (or what app could I run) to determine what the system is actually loading?

Thanks!
Chris

---

### Post by Rex Bouwense on 2011-10-01
1.  To hide the hidden files again just tick view and then untick Show hidden files.  Then all of the files that start with "." will miraculously disappear.
2.  To view the start-up applications, I believe that you have to go to Preferences and then Start-up Applications.
If you are still using 9.10, I think that it has reached end of life and is not receiving any more updates.  You might want to change to a newer version.

---

### Post by wildmanne39 on 2011-10-01
Hi, also Ctrl+h will hide the files again.
Thank you

---

### Post by josephmills on 2011-10-01
> **blueghoti said:**
> Hi - 

A couple of quick questions I wonder if the community could help with please....

1/ I toggled a setting a while back so that I could get a listing of "hidden" files when I browse in directories...  so I see a lot of files starting with a . 
How do I turn this off (and shorten my list?)

there are a couple ways in your sindow under edit I think is the opition to view hidden files 
if you are in there terminal and say are looking for somefile.txt 
you an use the command locate somefile.txt 
say there are 20 somefiles.txt all named somefile.txt 1somefile.txt 2somefile.txt 3somefile.txt 
id I was looking for three I would use the command locate somefile.txt | grep 3somefile.txt 
there are a bunch of ways of doing this 

> 
2/ my system feels slower on bootup than in the past.  Where would I go (or what app could I run) to determine what the system is actually loading?
I would say to look for a tutorial on "sysv-rc-conf" or "B.U.M"(boot up manager)

---

### Post by blueghoti on 2011-10-04
Hi all - 

This is very helpful!  Thanks so much for the support.

Little things make life easier :-)

Cheers,
Chris

---


---
title: "Thunderbird &amp; Lightning Broken After Ubuntu Update"
date: 2015-03-14
forum: New to Ubuntu
---

### Post by bonzo2 on 2015-03-14
I'm fairly sure that either or both Thunderbird & Lightning updated today when I was installing a printer and utilized the "upgrade" command.  I had previously declined to permit Thunderbird & Lightning to update but I did not know how to avoid it today.  When I log into Thunderbird (31.5.0), neither Lightning (3.3.5) not SoGo (31.0.1) works.

I'm posting here because I'm hoping Ubuntu users can instruct me how to roll back to the last version of Thunderbird and Lightning  I'm using Thunderbird and Lightning from the Ubuntu repository, not from Mozilla. (The version numbers are different there.)

 It seems that I have far less control over Thunderbird under Ubuntu 14.04 than in my previous OS, but it may just be my ignorance as to what my options are under Ubuntu.

Whatever it was that happened, Mozilla's Thunderbird page does not have any reports about.

Thanks

---

### Post by gifford on 2015-03-14
Not sure what you mean by "upgrade" command. Was this done using the terminal?

---

### Post by bonzo2 on 2015-03-14
Hi Gifford,

Thanks for taking time to reply.  I was trying to install a printer and added a ppa.  Then I went to the Synaptic Package Mgr and added some additional printer components.  Then I selected "apply" and "mark all upgrades."  I later went to the terminal and entered "sudo apt-get install && upgrade" for good measure...just to really mess things up! ;-)

Would my terminal command have updated everything on my system that needed updates?  Ubuntu has been asking to Ubdate Mozilla products for awhile: I've been getting Mozilla pop-ups for a while but decline them.

How would I know if Thunderbird and Lightning had just been updated.  I don't have their versions memorized.  

Thanks again

---

### Post by gifford on 2015-03-14
The command would have installed and upgraded the newest version of all the packages installed on your system.
The latest version of Thunderbird through the Ubuntu ppa is 31.5.0 which you listed in your first post.
I am at a loss for what occurred. My experience with Thunderbird and Lightning has been very positive and without 
issues.
Have you checked to see if you have any broken packages?

---

### Post by bonzo2 on 2015-03-14
Gifford:

I think you are on to something about "broken packages."  Synaptic struggled to achieve my updates, which necessitated a lot of re-dos on my part.  

Would the below approach be a sound approach to fix broken packages?  Does this approach require me to know the name of the broken package or will it identify broken packages for me?

How to fix broken packages?         (See this thread: [http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124))
    
1 - sudo apt-get update ...to update your package list.

2 - sudo apt-get autoclean ...to clean up any partial packages.

3 - sudo apt-get clean ... to clean up the apt cache.
     4 - sudo apt-get autoremove ...will clean up any unneeded dependencies.


 
If while doing this you can identify the broken package this code will very forcefully remove it.
     Code: sudo dpkg --remove -force --force-remove-reinstreq package name

---

### Post by gifford on 2015-03-14
The easiest way is to use Synaptic package manager. Open it and under sections you will find custom filters. Go to Broken and it will indicate the broken packages.
Edit at the top has a selection for fix broken packages.

---

### Post by bonzo2 on 2015-03-14
Gifford,
I like your style :-)  K.I.S.S. (Keep It Simple Stupid) is best for me at this juncture. Your easy suggestion fixed Thunderbird/Lightning and I'm back in business. :-)  Thanks for your time.
Bonzo2

---

### Post by gifford on 2015-03-14
Good! And you are welcome. Just mark this as solved.

---

### Post by bonzo2 on 2015-03-14
And now, I present the newby-est of newby questions: Is there an official mechanism for marking the thread "solved" or should I just edit the subject line with "[SOLVED]"?


Thanks,
Bonzo2

EDIT: Found the answer myself and marked a "solved." Bonzo2

---


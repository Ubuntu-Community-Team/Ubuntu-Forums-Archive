---
title: "upgrading?"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by Shadius on 2012-05-08
Upon reading this, I have a question. Keep in mind that I'm fairly new to Ubuntu & Linux. I've upgraded from 11.10 to 12.04 and I've experienced some issues, maybe bugs, not sure, but my question is if it's better to have done a fresh install rather than upgrade?

---

### Post by Perfect Storm on 2012-05-08
post moved. T&E is not a support forum.


Without knowing your issues, I say it's possible that your upgrade gone bad.

---

### Post by Shadius on 2012-05-08
> **Artificial Intelligence said:**
> post moved. T&E is not a support forum.


Without knowing your issues, I say it's possible that your upgrade gone bad.

Generally speaking, is it better to do a fresh install than upgrade?

---

### Post by sadaruwan12 on 2012-05-08
Please, Let us know about your issues so we can give you a clear answer.

---

### Post by Shadius on 2012-05-08
One issue that I've noticed is that I have to re-enable networking sometimes when I login for the internet to work. Otherwise, when I try to access the internet via Firefox or Chrome, it'll say there's no connection.

---

### Post by mastablasta on 2012-05-08
> **Shadius said:**
> Generally speaking, is it better to do a fresh install than upgrade?
 
 
if you have only default programmes installed then upgrade should work ok. even with some addded programmes from the repositories it should work ok. for your issue sit is best to try them running liveOS first to see if it all works and then upgrade.
 
however it can always go wrong as well. maybe some packets get lost during download and such. lately there is an option to upgrade using live media (CD, DVD, USB).
 
if you want to do fresh install then backup home (also hidden folders and files) and then simply install fresh and put the home back. you will of course need to add programmes you had before. i did this because upgrading from 10.10 to 12.04 would otherwise take too long.

---

### Post by Prescilla on 2012-05-08
> **Shadius said:**
> Generally speaking, is it better to do a fresh install than upgrade?
In my opinion, it is better to do a clean install.
I used to do upgrades but then some apps don't work anymore after the upgrade.
So I partitioned my drive to have a different / and /home partition.
Then I just install the new distro on / partition.

---

### Post by Shadius on 2012-05-08
> **mastablasta said:**
> if you have only default programmes installed then upgrade should work ok. even with some addded programmes from the repositories it should work ok. for your issue sit is best to try them running liveOS first to see if it all works and then upgrade.
 
however it can always go wrong as well. maybe some packets get lost during download and such. lately there is an option to upgrade using live media (CD, DVD, USB).
 
if you want to do fresh install then backup home (also hidden folders and files) and then simply install fresh and put the home back. you will of course need to add programmes you had before. i did this because upgrading from 10.10 to 12.04 would otherwise take too long.

I've been doing some research and came across some things mentioning that some packages might not be used, but are left behind when upgrading. How would I locate those unused packages that are now just taking up space and "clean" them out?

---

### Post by westie457 on 2012-05-08
> **Shadius said:**
> I've been doing some research and came across some things mentioning that some packages might not be used, but are left behind when upgrading. How would I locate those unused packages that are now just taking up space and "clean" them out?

These commands will let you know if you have orphaned apps on your system ```
sudo apt-get update

sudo apt-get upgrade
```

Then if you have things that are no longer required ```
sudo apt-get autoremove
``` should remove them for you.

---

### Post by Shadius on 2012-05-08
> **westie457 said:**
> These commands will let you know if you have orphaned apps on your system ```
sudo apt-get update

sudo apt-get upgrade
```

Then if you have things that are no longer required ```
sudo apt-get autoremove
``` should remove them for you.

I ran ```
sudo apt-get upgrade
``` and I noticed something on the last two lines of the output. Wondering if I should be concerned. 

Output:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I haven't ran the other codes yet.

---

### Post by westie457 on 2012-05-08
If you have any of these running - Synaptic Package Manager, Software Centre or Update Manager. Close them wait a few seconds then retry the commands.

---

### Post by Shadius on 2012-05-08
> **westie457 said:**
> If you have any of these running - Synaptic Package Manager, Software Centre or Update Manager. Close them wait a few seconds then retry the commands.

Okay, that worked. 23 packages needed to be updated and 0 to be removed. So I guess there weren't any unused packages left over from when I upgraded from 11.10 to 12.04. So now the question is, should these commands be ran everytime there's an upgrade/update?

---

### Post by westie457 on 2012-05-08
> **Shadius said:**
> Okay, that worked. 23 packages needed to be updated and 0 to be removed. So I guess there weren't any unused packages left over from when I upgraded from 11.10 to 12.04. So now the question is, should these commands be ran everytime there's an upgrade/update?

Update Manager usually takes care of the updates, that is why someone wrote the code for it. On my laptop the updates are checked once a day with settings for security updates to be accepted immediately and other updates accepted once a week with notification of the next release set to never. My choice as I only recently upgraded to 11.10 on this machine. OOps rambled on a bit there.

The update and upgrade commands are usually used by people who prefer the command line to graphical apps for their updates and when problem solving.

---

### Post by Shadius on 2012-05-09
> **westie457 said:**
> Update Manager usually takes care of the updates, that is why someone wrote the code for it. On my laptop the updates are checked once a day with settings for security updates to be accepted immediately and other updates accepted once a week with notification of the next release set to never. My choice as I only recently upgraded to 11.10 on this machine. OOps rambled on a bit there.

The update and upgrade commands are usually used by people who prefer the command line to graphical apps for their updates and when problem solving.

Since you said that the Update Manager takes care of the updates, I'm curious as to how come the Update Manager didn't prompt me to update these 23 packages that had updates for them? Maybe something in my update settings? That leads me to think that if I had never ran these codes in Terminal, I would've never known that 23 packages had updates to be installed.

---

### Post by westie457 on 2012-05-09
> Update Manager **usually** takes care of the updates, that is why someone wrote the code for it is what I said.

I then went on and gave you the settings that I use.

However my settings are not really important in this issue so I suggest you check and possibly reset the settings to how you want them.

Also it never hurts to run those commands whenever you want and especially if you notice that your system is not receiving or notifying you of any updates.

No I am not upset that a comment was misquoted and I hope you are not upset by this reply.

---

### Post by Shadius on 2012-05-09
> **westie457 said:**
> is what I said.

I then went on and gave you the settings that I use.

However my settings are not really important in this issue so I suggest you check and possibly reset the settings to how you want them.

Also it never hurts to run those commands whenever you want and especially if you notice that your system is not receiving or notifying you of any updates.

No I am not upset that a comment was misquoted and I hope you are not upset by this reply.

Sorry for the misquote. I will look into my settings for the Update Manager. Thanks for your help. :)

---

### Post by westie457 on 2012-05-09
No worries, enjoy your Ubuntu experiences.

If any problems always ask. You never know we might meet again on another issue one day.

---

### Post by Shadius on 2012-05-09
> **westie457 said:**
> No worries, enjoy your Ubuntu experiences.

If any problems always ask. You never know we might meet again on another issue one day.

Look forward to it. You were very helpful in helping me.

---


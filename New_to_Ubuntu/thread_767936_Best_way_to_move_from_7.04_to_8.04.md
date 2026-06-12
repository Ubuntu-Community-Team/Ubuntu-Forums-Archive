---
title: "Best way to move from 7.04 to 8.04"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by swarup on 2008-04-26
I worked so hard to get my Feisty working really well (wireless, sound, etc, etc) that when Gutsy came out I was scared to risk anything by doing the upgrade. So I just stuck with my Feisty, which is still working really well. But it sounds like there have been a lot of improvements in the last year, and I am considering upgrading to 8.04. Would the best way be to first do the upgrade to Gutsy using the upgrade manager, and then upgrade from there to Hardy again using the upgrade manager? 

I can remember in the days when gutsy first came out, some people were saying the best way to upgrade was via a clean install. There was a fair bit of controversy about which way was best and which was safest, and I ended up just staying with what I had -- Feisty. My main point is that I have worked hard to get my wireless dongle and other such things working well. If I upgrade will I put these things at risk of being disrupted in the process? Which is safest--doing the sequential upgrade or saving my home directory on an external drive and doing a clean install?

---

### Post by dangerpl on 2008-04-26
If you're unsure whether something will work in 8.04 just d/l the LiveCd and run it to test your hardware. And saving your data to an external drive is recommended for both. You never know how the upgrade is gonna go. It might go bad. But a clean install will give you a cleaner system. That's what I did. Took me about an hour to install and set it up just the way I like it. Best of luck!

---

### Post by Dev'olution on 2008-04-26
> **dangerpl said:**
> If you're unsure whether something will work in 8.04 just d/l the LiveCd and run it to test your hardware. And saving your data to an external drive is recommended for both. You never know how the upgrade is gonna go. It might go bad. But a clean install will give you a cleaner system. That's what I did. Took me about an hour to install and set it up just the way I like it. Best of luck!

I disagree. From memory the gutsy repo's are still there...

so just change any 'feisty' to 'gutsy' in your /etc/apt/sources.list then in terminal type apt-get update, then use synaptic to update you to the gutsy. from there do the same thing with hardy :)

---

### Post by vishzilla on 2008-04-26
If you have a separate /home partition its better to freshly install Hardy. You can save time as well some internet data download.

---

### Post by swarup on 2008-04-26
(This post is in reply to dangerpl)
However, if I d/l and boot to the Hard livecd, that will not show whether the driver I have set up in Feisty for my dongle, will work in Hardy or not. I am guessing that my Netgear wireless adapter is not going to work out of the box with Hardy just as it didn't with Feisty, although perhaps I am wrong. If I do the sequential upgrade 7.04->7.10->8.04, then whatever drivers I have set up in Feisty will remain active through the upgrades, won't they?

And if I do a clean install, then I'll have to reinstall the driver for the Netgear wireless adapter won't I?

You mention that doing a clean install--as opposed to an upgrade--will give me a "cleaner" system. What does "cleaner" mean, here? If you do an upgrade, do you end up with all sorts of clutter on the hard driver left over from the previous version?

---

### Post by vishzilla on 2008-04-26
Yes, on upgrades you are left with some useless packages. But that can be removed with Synaptic. If you prefer to keep the same config I recommend you to upgrade. Else if you don't mind having a fresh install with the default config, freshly install Hardy

---

### Post by swarup on 2008-04-26
> **WestAussieUbu said:**
> I disagree. From memory the gutsy repo's are still there...

so just change any 'feisty' to 'gutsy' in your /etc/apt/sources.list then in terminal type apt-get update, then use synaptic to update you to the gutsy. from there do the same thing with hardy :)

I opened the file /etc/apt/sources.list and looked through it. Do you mean that wherever the word 'feisty' appears in that file, I should change it to 'gutsy'?

And how do you use synaptic to update to gutsy? I opened synaptic and looked in it, but could not find a command for general OS upgrade. And when I type "Gutsy Gibbon" in the search window, it doesn't find anything.

Also, I tried opening the Adminitration -> Upgrade Manager, but nothing happens when I click on it. Don't know why.

---

### Post by swarup on 2008-04-26
> **vishzilla said:**
> Yes, on upgrades you are left with some useless packages. But that can be removed with Synaptic. If you prefer to keep the same config I recommend you to upgrade. Else if you don't mind having a fresh install with the default config, freshly install Hardy

1. If I do the upgrade option, then how will I later know which are the useless packages which I need to remove with Synaptic?

2. In regards to the config, I think it does not matter much if I go to a fresh install. The main thing would be setting up the driver for the wireless Netgear dongle. But by now, I've done it a few times and I guess I could do it again.

3. If I do a fresh install, then is there anything besides my home folder which I need to copy to an external drive? Would all my data be there, or could there be any important settings in other places that I need. I do have Hindi set up through SCIM for word processing. But I suppose that shouldn't be too hard to set up again.

I suppose the bottom line question is, what WORKS better? Will I be assured of a smoother functioning OS if I do a fresh install using livecd, in comparison to an upgrade? If so, then I'll definitely go with the fresh install.

---

### Post by nina_aoki on 2008-04-26
> Also, I tried opening the Adminitration -> Upgrade Manager, but nothing happens when I click on it. Don't know why.

The servers are all likely still in extensive psychotherapy sessions from all the traffic they've seen in the last two days -- or have outright committed suicide.

Use the torrent to DL Hardy rather than the update manager.

- nina

---

### Post by FrancesL on 2008-04-26
> **nina_aoki said:**
> The servers are all likely still in extensive psychotherapy sessions from all the traffic they've seen in the last two days -- or have outright committed suicide.

Use the torrent to DL Hardy rather than the update manager.

- nina
Forgive me for this .but just how do I use Torrent to d/l Hardy? I looked and see about 4 files..?

---

### Post by swarup on 2008-04-26
> **nina_aoki said:**
> The servers are all likely still in extensive psychotherapy sessions from all the traffic they've seen in the last two days -- or have outright committed suicide.

Use the torrent to DL Hardy rather than the update manager.

- nina

What I mean is, the update manager itself doesn't open. I've never actually used it before, so I don't know if it ever worked or not. But when I go in "Administration" and click on "update manager", nothing happens.

---

### Post by swarup on 2008-04-26
I think I'm going to go ahead and do a fresh install. Delete my Feisty and install Hardy. Before deleting Feisty, is there anything I need to backup onto an external drive besides the Home folder? 

All my evolution mail and the account settings etc, everything is there in the Home folder, right?

---

### Post by nicedude on 2008-04-26
I would suggest waiting till the madness slows down and by then everyone will have dealt with any issue you will have and you will get quick and good answers. Its not like its gonna make everything way better if you already are fully functional and after upgrade you don't till you fix stuff. Just my two cents.

---

### Post by swarup on 2008-04-26
> **nicedude said:**
> I would suggest waiting till the madness slows down and by then everyone will have dealt with any issue you will have and you will get quick and good answers. Its not like its gonna make everything way better if you already are fully functional and after upgrade you don't till you fix stuff. Just my two cents.

Yes, I see. If it's really like that, then I should certainly wait. But wouldn't it be mostly the people who are trying to upgrade who have the problems, and not those who do a fresh install? I thought those who do a fresh install wouldn't have problems. Because after all, the install livecd is going to remain the same for the next 6 months. That I'm fairly sure about.  -- So a fresh install should be smooth. Shouldn't it?

---


---
title: "Reinstall 10.04"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by Concert on 2012-05-04
My install of 10.04 is getting a little long in the tooth and a little shaky and I think I might need to reinstall. I have one small swap partition, one partition for the install, and one for home.

If I reinstall 10.04, do I leave the swap partition and the home partition alone, and just install into the same partition as Ubuntu is installed into now?

I think I do not need to reformat, but please advise if otherwise.

Will all the additions that I have made, e.g., Opera browser work straight away, or will I need to reinstall them.

Are there any directories that need to be saved elsewhere and copied back after the reinstall?

Is there anything else that needs to be saved elsewhere and copied back after the reinstall?

---

### Post by wildmanne39 on 2012-05-04
Hi, there should be no reason to reinstall 10.04 unless you are replacing the hard drive or something along that lines, what is the reason you think you need to reinstall?
Thanks

---

### Post by PivotalEpiphany on 2012-05-05
Be sure to check your **startup applications, **this was a big thing with Windows. Also, right-click your panel and add the ***system monitor***  and the ***force-quit*** icon. This has proven to be quite useful in my very ancient setup.

However, if you choose to reinstall the OS: When I do my back up (manually), I *sudo nautilus *and copy the personal contents of my home folder to my secondary hard drive.
Upon fresh install, *sudo nautilus...again, *change the permissions of the folders and copy-paste them into the corresponding folders. Worked like a charm.

---

### Post by CharlesA on 2012-05-05
> **wildmanne39 said:**
> Hi, there should be no reason to reinstall 10.04 unless you are replacing the hard drive or something along that lines, what is the reason you think you need to reinstall?
Thanks

+1. I just finished getting my web development box "moved" to 12.04 (Fresh install on a different VM) but I still have the Lucid install on a different VM so it's still around.

> **FetalVivisection said:**
> Be sure to check your **startup applications, **this was a big thing with Windows. Also, right-click your panel and add the ***system monitor***  and the ***force-quit*** icon. This has proven to be quite useful in my very ancient setup.

However, if you choose to reinstall the OS: When I do my back up (manually), I *sudo nautilus *and copy the personal contents of my home folder to my secondary hard drive.
Upon fresh install, *sudo nautilus...again, *change the permissions of the folders and copy-paste them into the corresponding folders. Worked like a charm.

gksudo nautilus ;)

---

### Post by PivotalEpiphany on 2012-05-05
Thanks!

> **CharlesA said:**
> +1. I just finished getting my web development box "moved" to 12.04 (Fresh install on a different VM) but I still have the Lucid install on a different VM so it's still around.



gksudo nautilus ;)

---

### Post by grahammechanical on 2012-05-05
10.04 is still supported on the desktop for another year. Have you downloaded the latest 10.04 ISO image or will you use an image that you have had for a couple of years. Use the latest ISO image.

From this link you will see that Lucid is now at 10.04.4

[http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")

When you eventually upgrade to 12.04 it may be better to upgrade from 10.04.4 than from the early ISO images of 10.04.

To answer your questions

Run the live CD and select the Do Something Else option and at the partitioner screen select the partition where you want to install 10.04 and click Change.

In the little panel select the file format, ext3 or ext4, give the partition a mount point of /

It is your choice whether to format. If you do not format you may have old configuration files that may conflict with the new ones.

Then, select the partition which is your /home partition and give it a mount point of /home. Do not format. I repeat, **DO NOT FORMAT** this partition or you will loose all your data and documents.

The installer should notice the swap partition and re-use it.

And that is it. You may need to re-install some applications but their user configuration files are in your /home folder on the /home partition. So, you should find that when you launch these applications again they pick up the same settings, etc., as before.

Regards.

---

### Post by Concert on 2012-05-05
Part of the motivation stems from long experience with Windows which seems to benefit enormously from periodic reinstalls, part from the fact that I have regretably deleted my workspace switcher and want to get it back.

I see that there is another thread where Odyssey1942 did the same thing and wants to reinstall his workspace switcher. I also googled for a reinstall solution but couldn't find one. I have been following the other thread, but no solution has been found so far. If there is a way to reinstall the Workspace Switcher, I will just do that first and continue on using the current installation.

I have the Monitor on my panel but not the force quit. Will definitely add that! Where do I find Startup Applications?

When you say "copy the personal contents of my home folder to my secondary hard drive" do you mean the entire contents or just some part and which?

Thanks

Edit: I posted at the same time as grahammechanical without seeing. Thanks and will utilize these very good instructions if no solution to the Workspace Switcher problem is suggested.

---

### Post by philinux on 2012-05-05
> **Concert said:**
> Part of the motivation stems from long experience with Windows which seems to benefit enormously from periodic reinstalls, part from the fact that I have regretably deleted my workspace switcher and want to get it back.

I see that there is another thread where Odyssey1942 did the same thing and wants to reinstall his workspace switcher. I also googled for a reinstall solution but couldn't find one. I have been following the other thread, but no solution has been found so far. If there is a way to reinstall the Workspace Switcher, I will just do that first and continue on using the current installation.

I have the Monitor on my panel but not the force quit. Will definitely add that! Where do I find Startup Applications?

When you say "copy the personal contents of my home folder to my secondary hard drive" do you mean the entire contents or just some part and which?

Thanks

Workspace switcher. Just right click on the top or bottom panel choose add to panel and scroll down the list. I forget what the switcher is called but I'm sure it will be obvious. And reinstalling would not cure this as it's part of the settings in home in the hidden .config folders.

If you would like to reset both panels to their default installed state then open a terminal and use this command.

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by Concert on 2012-05-05
Philinux, Thanks, but I only would want to reset to defaulted if this will reinstall the Workspace Switcher (which I had deleted). I had been having boot problems and two popup boxes mentioned that there was a problem with two different applets and asked me if I wanted to delete them. I did not think through how I was going to reinstall them, but assumed it would be no problem. 

It is a problem.

Will resetting to default re-install the Workspace Switcher?

---

### Post by philinux on 2012-05-05
> **Concert said:**
> Philinux, Thanks, but I only would want to reset to defaulted if this will reinstall the Workspace Switcher (which I had deleted). I had been having boot problems and two popup boxes mentioned that there was a problem with two different applets and asked me if I wanted to delete them. I did not think through how I was going to reinstall them, but assumed it would be no problem. 

It is a problem.

Will resetting to default re-install the Workspace Switcher?

Yes but you can just add it back easily as I described.

---

### Post by Concert on 2012-05-05
Failed to mention that I also tried to reinstall using the right click on the panel as suggested. There is a Workspace Switcher listed but when I add it to the panel and click on the new panel icon, nothing happens.

I assume that this is because I had deleted the two applets that should be started up when the panel icon is clicked on

This is why I also assume that I must reinstall the applets.

---

### Post by philinux on 2012-05-05
> **Concert said:**
> Failed to mention that I also tried to reinstall using the right click on the panel as suggested. There is a Workspace Switcher listed but when I add it to the panel and click on the new panel icon, nothing happens.

I assume that this is because I had deleted the two applets that should be started up when the panel icon is clicked on

This is why I also assume that I must reinstall the applets.

Sheesh it's been a while since I used classic of course.

```
sudo apt-get install --reinstall gnome-panel gnome-applets
```

Then add the ones that are missing. I think.

---

### Post by Concert on 2012-05-05
Maybe this should be another thread, but I have stayed with 10.04 because I love the Workspace Switcher and if I am correct, this was done away with in ll.04 or 11.10 and later. Is this the case?

If the workspace switcher is available in the later versions, it would make sense for me to update to a currently supported version, ideally an LTS, so this is another way to solve the problem, IF....

---

### Post by philinux on 2012-05-05
> **Concert said:**
> Maybe this should be another thread, but I have stayed with 10.04 because I love the Workspace Switcher and if I am correct, this was done away with in ll.04 or 11.10 and later. Is this the case?

If the workspace switcher is available in the later versions, it would make sense for me to update to a currently supported version, ideally an LTS, so this is another way to solve the problem, IF....

As you can see Workspace switcher is the bottom icon in Unity. Never been removed from the OS.

---

### Post by Concert on 2012-05-05
Now that I look at the screen you posted, I remember why I did not upgrade before. The Unity screen is way less efficient than my workhorse 10.04, extra clicks to get to things that I am accustomed to having on the upper panel, which I thought had gone away, but apparently not. 

Or was it the ability to place icons on the panel that went away?.

---

### Post by CharlesA on 2012-05-05
> **Concert said:**
> Now that I look at the screen you posted, I remember why I did not upgrade before. The Unity screen is way less efficient than my workhorse 10.04, extra clicks to get to things that I am accustomed to having on the upper panel, which I thought had gone away, but apparently not. 

Or was it the ability to place icons on the panel that went away?.
Gnome classic has the top panel and it is included in 12.04.

Gnome shell is another choice.

---

### Post by Concert on 2012-05-05
Can shortcuts/icons be placed onto the panel?

Thanks

Also Charles, I see that you are on the Ubuntu Forums staff. Can you shed any light on reinstalling the workspace switcher?

---

### Post by CharlesA on 2012-05-05
> **Concert said:**
> Can shortcuts/icons be placed onto the panel?

Thanks

Also Charles, I see that you are on the Ubuntu Forums staff. Can you shed any light on reinstalling the workspace switcher?

Should be able to, it works just like the Gnome 2 version did except it is running Gnome 3.

Did you try the command that philinux posted?

---

### Post by Concert on 2012-05-05
Not yet! Trying to get up the courage. Since I am a newbie, I seem to manage to cause as many problems as I cure. Is this likely to change some of my other existing apps? Or none?

---

### Post by wildmanne39 on 2012-05-05
Hi, just make sure you copy and paste the commands given for accuracy.
Thanks

---

### Post by CharlesA on 2012-05-05
> **Concert said:**
> Not yet! Trying to get up the courage. Since I am a newbie, I seem to manage to cause as many problems as I cure. Is this likely to change some of my other existing apps? Or none?
It will only reinstall the panel.

---

### Post by Concert on 2012-05-05
Worked like I was hoping that  it might. I made the mistake of installing the switcher on the top panel instead of the bottom, but once that was sorted, I'm back in business. Thanks to all.

As to 12.04, since 10.04 is no longer supported, would you suggest that the advantages of upgrading to 12.04 (or the successor LTS, if not 12.04?) would outweigh any inconveniences as I mentioned before? 

What would be the main improvement/s?

Thanks also for your comments on this.

---

### Post by CharlesA on 2012-05-05
10.04 is still supported for another year, so there's no rush to upgrade.

---

### Post by Concert on 2012-05-05
I got a pop-up on the 10.04 in my office saying that it is no longer supported. I had thought it was for 3 years and so was surprised.

Glad to have your reconfirmation. Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-05-05
> **Concert said:**
> I got a pop-up on the 10.04 in my office saying that it is no longer supported. I had thought it was for 3 years and so was surprised.

Glad to have your reconfirmation. Thanks.
LTS gets 4 years 10.04 is on its last year
server gets longer than desktop

---

### Post by CharlesA on 2012-05-05
> **Concert said:**
> I got a pop-up on the 10.04 in my office saying that it is no longer supported. I had thought it was for 3 years and so was surprised.

Glad to have your reconfirmation. Thanks.
Where did you get that message?

EoL for Lucid Desktop is April 2013.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Concert on 2012-05-05
On the monitor of the 10.04 computer in my office. Is this what you meant? Not sure I understood your question.

---

### Post by CharlesA on 2012-05-05
> **Concert said:**
> On the monitor of the 10.04 computer in my office. Is this what you meant? Not sure I understood your question.
Probably update manager then.

---


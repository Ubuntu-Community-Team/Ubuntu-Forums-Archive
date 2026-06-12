---
title: "upgrades wrecking ub"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by jonabark on 2012-09-27
I got a new small cheap acer aspire one netbook for my wife it came with windows with which we've had problems. She just needs it for internet, email and writing letters, storing music for ipod. I loaded ubuntu from online and it walked me through the set up and it was working fine though very slow the first time with any app and faster afterwards. Is that normal? I went to the update manager and checked for updates and it showed 109 or so which seemed like too many for a program i had just downloaded an hour before  but I tried to download and install them and it was disastrous.The little wheel started spinning and then after quite a while the system froze cursor stalled, then disappeared. I tried escape but it turned up something that looked like a different OS and stalled again. finally I used the power button to force it off. When I reopened ubuntu the internet connection was gone and so i went to the update manager again and got error messages. 
So I ended up with insoluble problems and uninstalled ub from windows and reinstalled it .  Then after all was working fine again I assumed that I had been impatiient and not finished something and tried again to update the program. It seemed like it was working till late in the game when I ended up with the same mess or worse.

What am I doing wrong?  Is there someplace where I can find which updates are really needed or a good idea for ubuntu. Shouldn't the update process be safer?

Also I am concerned in looking through the comments on the user forum and seeing a lot of code fixes that I don't understand and don't want to deal with. I like the look and feel and philosophy of ubuntu's open source OS but wonder if this is really for me.

---

### Post by critin on 2012-09-27
Well, the updates are from when the os was first released, so updates will be many.  That's normal.  After that, they are fewer.
No, it isn't normal to run exceptionally slow.  Is it an internet issue?  Do you have good internet?

A hard power off is always a bad idea with any os.  Depending on the stage of updating, interrupting it could cause errors.  If they were actually installing at the time, something will break.  If they were only still downloading, they will only need to begin downloading again.  Time consuming.

 > 
and uninstalled ub from windows and reinstalled it 

Is this a Wubi install or did you create a separate partition for ubuntu?

It shouldn't be acting this way.  Sorry.

---

### Post by jonabark on 2012-09-27
My internet connection is pretty good- about 1MB/s . Also I did not interrupt the download or power down the computer until it stalled, the cursor disappeared, and would not come back and it happened twice with me being very careful and patient the second time and doing no other fiddling as the download proceeded.. As far as the slowness, the first time I opened any app it is quite slow. It gets faster the second time and is quick the 3rd. That doesn't bother me and I like the ubuntu OS but this is a major problem..

Yes this is a Wubi install.  

Maybe the question should be how should a normal update proceed  in detail, step by step. I have never had problems with this on my mac. If a download fails it doesn't affect the computer and there is a progress bar that shows where it is in time. In this case there was a a progress bar space as it said it was installing but no actual colored moving bar in that space though the wheel thing was spinning. After it stalled and  I powered it off the update manager said there were now 79 updates to install instead of 109.  I don't want to go through this again and need some help with how to insure a successful download/installation of the updates.  Should I do it  at 25 MB of update downloads a time?, are there ones I should avoid or ignore?  Why is it disabling my wireless connection.

Thanks for your interest. I 'm not getting much help so far.

---

### Post by critin on 2012-09-27
>  Why is it disabling my wireless connection.Wireless.  There you are.
Use an ethernet cable while downloading/installing large items.   Wired internet won't disconnect on you, while wireless just isn't as dependable or powerful.
> 
 I have never had problems with this on my mac.Did you install the system on the Mac?

---

### Post by snowpine on 2012-09-27
Welcome to the forums! I recommend that you install all of the updates. These are security patches and bug fixes to *applications you already have installed*; not new features or removing old features.

If you'd like help with your wireless then I recommend using the following terminal command (Applications->Accessories->Terminal to start a terminal) to identify which wireless card you have:

```
lspci
```

You should see one or more lines that identifies your network hardware, for example here's mine:

```
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

Then you can start a new discussion thread with a descriptive topic like "Help with Intel 3945ABG wireless" and I'm sure you'll get the help you need.

As to why an application is slower the first time you use it, it gets cached in RAM after that point, so it's faster the 2nd time.

Generally speaking, Ubuntu will be faster on fast hardware, and slower on slower hardware like your netbook.

---

### Post by jonabark on 2012-09-27
OK so I hooked up with the ethernet wire and it connected to the internet fine and I deselected half the   updates to do the download install in 2 smaller actions. I  pressed install updates, authenticated pressed install updates again  spinning action spin stops and install updates button un-grays  so I sit a while -nothing happens -press install updates again. box comes up saying applying changes with an empty  horizontal progress bar space but no moving  bar and under the bar it says Waiting and to the right the wheel is spinning, which it has been doing for at least 12 minutes. I'm waiting and hoping for the best but this does not look promising to me. It is only 126 MB so I don't get what the problem is.

As far as what I have done with computers, i am definitely no expert, but I have successfully installed systems a couple times and I bought an old macbook for my daughter, took it apart, put in a larger hard drive, more ram and a new OS. It worked fine. I know virtually no code apart from some xhtml and try to avoid anything like that without direct supervision. I love the idea behind ubuntu and am not trying to one-up this project with references to the mac, (though I do love adobe programs) I'm.  just trying to understand so I can make it work for us. 

OK finally there is action, almost 30 minutes later- separate progress bar then the applying changes bar and  after a bit it seems to be done.  I think this is a rinky dink cpu and that is the deal. 

Thanks much. IAppreciate the input.

Using the ethernet cable seemed to make the difference, Everything went the same but with the wireless the wheel stopped spinning and the whole desktop froze. I am almost done now with the second batch of updates which started right away with the slow movement of the applying changes bar. It's all done. working fine and I think Priscilla is going to love it.

---

### Post by snowpine on 2012-09-27
Here is a terminal (Ctrl+Alt+T) trick if you want to download the updates in "chunks" and then apply them all at the same time. (Not a good idea to selectively update somethings but not other things, because one part might depend on a different part, better to update them all together.)

```
sudo apt-get update
sudo apt-get dist-upgrade -d
```

The -d flag means download only. Then when you have time to sit down, apply the updates, and troubleshoot any potential errors:

```
sudo apt-get dist-upgrade
```

This will apply the updates that you had downloaded previously.

---


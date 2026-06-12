---
title: "[SOLVED] Accidentally deleted root ext3"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by AirWreck on 2008-09-12
I installed Kubuntu a week ago and am in "break it to learn it" mode.  I accidentally deleted the ext3 /root partition on my hard drive today and it pooched my dual boot (grub, I guess).  I put my XP HDD clone in and am trying to learn from my mistakes.  I know there are XP programs out there but is there an open source program that I can use to recover ext3 data from the deleted partition?

Many thanks.

---

### Post by iaculallad on 2008-09-12
That would be [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by AirWreck on 2008-09-12
Great, I'll give it a shot.  Thanks!

---

### Post by AirWreck on 2008-09-13
Ok I loaded Testdisk and it shows as loaded in the Adept Manager but does not show up in Add/Remove Programs nor in any of the program categories in the K-Menu.  Looking online, it looks like it might not be a super GUI program so maybe I'm missing something.  After a week in Kubuntu, I was figuring stuff out pretty well but this one has got me.  FYI - I did also try the Run Command.  I hadn't used that yet so I tried a known entity and it will boot Konqueror but not Testdisk.  Stumped in Hawai'i... :confused:

Don't know if this is a contributing factor but I accidentally nuked my / partition today so just did a quick reinstall on this old cloned drive I'm abusing during my learning curve;)  I only put 2gb into a separate home partition as a test and I'm getting low disk errors but I think that's just because I'm surfing here =cache?  I'm going to reinstall with a better config tomorrow but wonder if that's all it is?

I'm callling it a night but thanks for any tips to try with my morning cup of joe tomorrow :)

---

### Post by AirWreck on 2008-09-13
Found a post on how to boot it from terminal, thanks!

---

### Post by ronnielsen1 on 2008-09-13
Did it work to get your files back?

---

### Post by AirWreck on 2008-09-13
It worked awesome thanks!  Every passing day, I become more and more of a Kubuntu/open source believer!

I did have to jump through some newbie hurdles, trying to figure out how to boot testdisk "as root".  After that it worked like a champ!  I know there are posts all over the place, but for any other nooB's out there who are struggling to recover their deleted /root ext3 partition...

Caveat - I have no clue what I'm doing.  I hadn't really lost anything of value but wanted to do it as a learning exercise.  I learn by breaking things so the following is only informational.  If you're trying to recover something near/dear, please ask someone else to confirm the below :)

With my system all pooched and not able to boot, I swapped in a clone hard drive I made last week of my XP system.  I did this using Acronis in XP right before I installed Kubuntu Hardy.  This turned out to be a great idea ;)

I reinstalled Kubuntu on the cloned drive.  Then I installed the testdisk package but couldn't find it in the menu tree.  I tried "run tesdisk" and "boot testdisk" in Terminal with no luck.  Finally I found a post that said I just had to enter "testdisk" in terminal.  I was feeling sheepishly proud but now it would load and then error out saying I had to "be root".

Still not entirely sure what that means because I thought that was basically linux speak for administrator and I thought my user profile was administrator.  I even went into User management and ticked off "root" in the box.  Anyway...

I found a post that said enter "sudo apt-get install gksu" to become a mighty root kinda guy.

I did that but still no love when I tried to boot testdisk.

I found another post on the testdisk website that said now that I had done this thing called sudo, I should enter something like "sudo ./testdisk_static"

That errored out too but seemed to be the right idea so I tried some permutations and finally got "sudo testdisk" to open the program successfully.

After that, the rest was relatively easy as their website has good tutorials you can wade through to figure out your particular ailment.  

In my case, I did the scan of the drive I had pooched (now mounted via a USB shell) and it showed my "deleted" ext3 partition as logical.   That seemed to indicate (to me at least) no problems but I just rolled the dice and changed the partition from "L" (logical) to "P" (primary).  I rebooted and ouila, all was good and I recovered the user profile.

Now that Humpty is back together, I'm going to try to break it again by...

1)  seeing if I can boot from the newly recovered USB removeable drive.  This would be handy for me because I travel a lot.

2)  try to replace my new profile in Home that doesn't have much installed with my old Home profile that has a lot installed.  Wish me luck!

Life is good.  Life in Kubuntu is even better :guitar:

---


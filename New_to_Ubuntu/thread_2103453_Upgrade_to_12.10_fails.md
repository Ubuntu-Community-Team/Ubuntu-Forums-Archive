---
title: "Upgrade to 12.10 fails"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by Acharn on 2013-01-10
I'm currently running Precise Pangolin 12.04 and someone suggested in another thread that upgrading might cure my periodic problem with program windows going grey and freezing for anywhere from a few seconds to a minute of so. When I tried to upgrade through the Update Manager I got an error message, "Could not calculate the upgrade. An unresolvable problem occurred while calculating the upgrade: E:Unable to correct problems, you have held broken packages..." OK, I thought it might be because of the game Marathon that I finally got installed a couple of days ago. It's from the getdeb.com repository, but the main repository is down and I finally stumbled across a mirror that had the package. I used Synaptic to try to completely remove all the packages but I must have missed some.

So I have several questions to choose my best option. Is there some way I can find the packages that are making the updater barf? I don't see any entries in syslog that seem informative, but maybe I just don't recognize them. I am not able to burn the 12.10 to a DVD -- my Lite-on DVD burner doesn't recognize DVD's under Ubuntu. It worked OK under Windoes XP, but if I put a DVD in it now it just spins. For some reason my Acer Aspire M-1610 wil not boot from a USB drive -- I spent days trying every possible configuration and don't understand why, but it just won't do it. But I have 12,04 on a CD, which my drive does read. In fact last year I was booting from it almost every day while my hard drive was down.

So I was thinking I might try a clan install of 12.04, overwriting what is in that partition. I have the /home directory in a separate partition, so I should be able to keep all my data. All my programs are open source and I really don't use many, so reinstalling them isn't a big problem. On the other hand I don't remember the installation process clearly. Is there a point where I can choose which partitions bet erased? I think there is, but would like some reassurance.

Obviously I would prefer to be able to just upgrade, if there's some way to track down the cause of this error.

---

### Post by grahammechanical on 2013-01-10
You could do a couple of things.

You could check the settings of Software Sources/Update Manager. Do you have any PPAs or repositories other than standard Ubuntu Repositories. If so, remove them. This could be the reason that the Upgrader program cannot calculate the upgrade. The links to PPAs sometimes get broken and cause difficulties to updating and upgrading.

Do you have a separate /home partition? If so, that will help protect your data. Although backing up data is always a good thing to do.

When you run the Install CD chose the Do Something Else option. Tell Ubuntu to install into the partition that the present Ubuntu is installed in by selecting that partition and editing the settings.

Give the partition a file type. Default for 12.04 is Ext4. Keep that the same. Give it a mount point of / But do not mark it for format. That is important. Then Ubuntu will install over the existing Ubuntu. It will not remove your data in the /home folder.

Of course, if you have a separate /home partition you can mark the / partition to be formatted. Then the installation will not have may be conflicting configuration files. Just remember to select the /home partition and give it a file type the same as it already has (again Ext4 is the default) and give it a mount point of /home.

Then when you reboot the new install it will access the /home partition and use the configuration files there.  A tip is to run the live session and use Gparted to see what paritions you have and how Ubuntu describes them. Make a copy on paper so that you know what you will see during the install process when you get to the partitioner part.

Regards.

---

### Post by oldfred on 2013-01-10
I think grahammechanical covered the upgrade, re-install.

But your issue on grey screen. I get that on my laptop with 1.5GB of RAM when it uses swap. Or I can tell when I have loaded too many apps at once or a large data file. My Desktop never has that issue and has 4GB of RAM. 

How much RAM and do you load lots of apps at once? Also can check memory & swap use.

free -m

All of RAM being used is often normal as Linux caches recent programs as you often reuse them. It frees unused if you start something new and only if all working apps are more than RAM, then has to use swap.

---

### Post by Acharn on 2013-01-19
OK, the command 'free -m' gives me:
```
             total       used       free     shared    buffers     cached
Mem:          1002        913         89          0          4         90
-/+ buffers/cache:        818        184
Swap:         4766        743       4023

```

I generally don't run many programs, but I might have the browser open and open up Rhythmbox to listen to music while I browse. I figured it was something to do with swap, but it's a bit annoying. I thought Linux was supposed to be better on limited hardware than Wondows. Well, it will be about another year and a half until I can afford to replace this one, but next time I'll know about the need for more memory and a better graphics card. ATI Radeon sux.

Thank you for your help, sorry I was so late getting back to you.

---

### Post by Acharn on 2013-01-19
Wow, this was exactly the help I needed. Thanks so much.

---


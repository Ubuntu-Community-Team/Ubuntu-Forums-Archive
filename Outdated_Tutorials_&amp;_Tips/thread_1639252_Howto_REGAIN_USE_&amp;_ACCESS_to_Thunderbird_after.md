---
title: "Howto REGAIN USE &amp; ACCESS to Thunderbird after an upgrade."
date: 2010-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by WinRiddance on 2010-12-06
In the past I've always been able to rebuild my system from scratch, followed by reinstalling my software, which was then followed by copying my old application folder contents (folders within home/user) over to the freshly installed or upgraded home/user folder. This has always worked like a charm for all of my applications, until recently with Thunderbird that is.

**[COLOR="DarkRed"]The scenario:[/COLOR]**  After rebuilding my system a few weeks ago, I could no longer access my old Thunderbird profiles, emails, account settings, etc. I had more than one backup copy, could even view and open the folders in Nautilus, but could not access any of that data via Thunderbird. Sure, Thunderbird could be opened and I could even install, working accounts from scratch, but no matter what I did, I was no longer able to access my previous information. My file permissions were fine, the application itself worked, and I was able to select the new path to my old store folder without any error messages from Thunderbird. But no matter how often I tried, to include making use of restarts and even a couple of cold starts (power off completely), Thunderbird simply refused to allow me access to my old data. Well, since I have important emails, some of which date back in excess of 10 years, I ended up spending several hours here, on the Mozilla Thunderbird forum, and other Mozilla related forums as well ... without finding the _absurdly simple solution_ that I'm writing below. So anyway, if the above scenario applies to you, then here's the solution:
(follow these steps in that same order)

**1.** After making sure that you still have a safe backup copy of your email store folder and .Thunderbird files, open up Thunderbird, _then go to Edit_ on the file menu and open up the _Preferences_. Move on to the _Advanced settings_ and locate the tab for Network & Disk Space. **Clear your cache!**

**2.** Next step, locate your existing email store/folder (the one containing all of your saved, previous emails & custom email folders that you want to use again). If you've tried this earlier and it didn't work ... it was probably because you didn't clear the cache **first**. Make sure that you click on OKAY, followed by opening up Thunderbird/Preferences again in order to double-check that your selections are still there. More than likely, everything is working fine again. I've never had to clear my cache in the past, that's why I never thought of it. Before I just found the correct path if it had changed, selected it, and that was that. I'd even done that a few times to switch between backed up older account settings and everything worked right away (in the past, that is).

**3.** If applicable, also locate the new or changed _path to your downloaded files_ and select that path again too. See the screenshots below for additional help. I can't believe that this was not posted in the help section or a Mozilla Thunderbird FAQ online ... least not when I wasted my time looking through the Mozilla forum recently.

**If steps 1 - 3 still didn't work for you**, i.e. you can definitely open and use Thunderbird, but without access to your old emails/accounts, then it's more than likely either an issue with missing file permissions, or an issue with inadvertently deleted files/folders which can no longer be located on your machine at all. If you've changed your user name during an upgrade or fresh installation of Ubuntu, that could be the problem too. Or if you've previously backed up your saved information as a sudo level administrator, then that could be the reason why your new user account no longer has access since user accounts do not have default sudo admin access after installing or updating Ubuntu. Last but not least, if your previous settings were part of a path to a partition that was written to your fstab, then you might want to check your fstab file as well. My Ubuntu 10.10 upgrade from within the software update manager wiped out everything in my previous fstab. I hope this thread is able to help someone!

.

---


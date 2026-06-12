---
title: "Firefox 7 Startup Causing Instant Reboot in Kubuntu 11.10"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by GregA on 2011-10-19
A few days ago, I updated from Narwhal to Ocelot via the distro update process versus a new install.

I've had a couple issues with Nepomuk and Akonadi that this forum has helped me to resolve.

Now the remaining issue is about 50% of the time, when launching Firefox 7, it causes an immediate restart of Kubuntu.   The screen goes black, and after about 1 or 2 seconds, a new login screen is displayed.   Once the various users log back in, Firefox 7 will start and run normally.  But not upon that very first session.

Any tips or thoughts?  Have others seen this.   I'm running a basic Lenovo desktop (H410) with Intel integrated graphics.

Thanks

---

### Post by lovinglinux on 2011-10-20
Sounds like a faulty memory or video driver issue.

However, what it is strange is that it happens on the first launch only, so it might be something related to the Firefox profile. Have tried a clean profile already?

---

### Post by GregA on 2011-10-22
Hi,

I've re-installed Firefox, and all users on this Lenovo system (newly updated from narwhal) are still having this issue.

It is strange that after the user logs back in, Firefox launches normally every time.

I don't know much about checking and updating any config or profile setups.  I'll do some more reading and check a couple other forums.   It's like something is not pre-loaded into Firefox's setup upon the first login.

Greg

---

### Post by mglennpooh on 2011-10-22
I have a somewhat similar problem except when I 1st login to Ubuntu then bring up Firefox I get an error message - "well, this is embarrassing..." which is similar to an error message I get from Internet Explorer when I reboot Windows after a hard shutdown . I suspect all three instances are related to an error in memory. 

Since I run solo on my Ubuntu off a Wubi which I uninstall & reinstall like potato chips, I would be very alarmed if you're running multiple users off a hard partition. Obviously, you may need to round up whomever many to get them to save their files before you reinstall at least once, if not more times, if needed to solve this problem. 

However, Firefox is normally downloaded & installed with GNOME compatibility in mind, vs KDE which has its own brand of addons & such. I would strongly recommend you correct that issue 1st if you don't know the brand yet. or then, or also, I would  try uninstalling Konqueror as a possible memory rival to the normally incompatible Firefox. I also discovered a new version of sun-java (1.6.29) which seems to have eradicated any remaining problems.

Mozilla also has sibling browsers in its stables - try these too if you have the time.

---

### Post by lovinglinux on 2011-10-22
> **GregA said:**
> Hi,

I've re-installed Firefox, and all users on this Lenovo system (newly updated from narwhal) are still having this issue.

It is strange that after the user logs back in, Firefox launches normally every time.

I don't know much about checking and updating any config or profile setups.  I'll do some more reading and check a couple other forums.   It's like something is not pre-loaded into Firefox's setup upon the first login.

Greg

Only new users have this problem?

---

### Post by GregA on 2011-10-22
The crash/restart issue occurs with established users.   This PC has 1 admin/sudoer, and 3 users.   Users are more prone to crashes than the admin, and all KDE user profiles are correct insofar as I can tell (re privileges and groups).  The crashes are linked to a "new login" for either admin or a user.  And after the re-login, Firefox starts normally and remains stable.

I'm interested in seeing what an update to the next version of Firefox will do . . . if that doesn't correct this annoying issue, I'll probably just use Chrome although Firefox has the interface I'm most comfortable with.

Also, in the meantime, I'll check out Synaptic for Firefox clones and see if those are functional.

note - - starting Firefox from the Konsole in safe-mode doesn't prevent the crashes.   Also, Firefox doesn't log any crashes - like it's not aware that X has restarted.

Greg

---

### Post by HalfEmptyHero on 2011-10-23
Did you try deleting the .mozilla folder? If not, back it up and then delete it and see if it still does it.

---

### Post by GregA on 2011-10-23
Hi,

Thanks for the suggestions so far.

I've deleted the hidden folder and contents of .mozilla.   That didn't effect the high probability of Firefox or X crashing and restarting when launching Firefox in a new session.   

At this point, I'm OK with using Chromium, and waiting for the next upgrade to Firefox.  I'll try that update and if that doesn't fix it, well, I'll stick with the more stable Chromium.

Thanks again,

Greg

---

### Post by GregA on 2011-10-24
Am still working to resolve this Firefox instability, and I think I've run across a work-around.

As stated earlier, Firefox will cause an X Server restart, when it is started upon the "first" KDE login.   After inputting the user password on the new login screen, Firefox will "always" start normally (no crashes of X).

I've found that if I log-off, restart, or shutdown the PC, and leave Firefox open - - it will automatically open upon the new login and "not crash x".   

So, that's an easy, although not elegant fix to this issue.   If anyone has any thoughts or insights, I'd appreciate hearing from you.

---

### Post by hashok on 2011-10-25
Hi **GregA**!

   I had absolutely the same problem on the same versions. I checked backtrace of X-server crash found in /var/log/kdm.log and noticed that functions from intel_drv.so were called close to the end of X-server life. As always, video drivers usually cause X-server problems, so I brutally forced X-server NOT to use intel_drv.so by doing:

    sudo mv /usr/lib/xorg/modules/drivers/intel_drv.so  /usr/lib/xorg/modules/drivers/intel_drv.so_


    And rebooted the machine. As a result, X-server switched to VESA driver and X-server crashes disappeared after firefox launches.  Yeap, it is a bit dirty solution, I just have no time now to find a nice way to force X-server to use VESA driver instead of intel.
   Before doing this workaround, make sure you also have intel driver in your backtrace, just open kdm.log and search for "Backtrace".  Have fun!

  BR, Andrey.

---

### Post by GregA on 2011-10-27
Thanks Hashok . . . 

I will check the logs, although I want to avoid that fix (using only Vesa on this higher end machine).

I've been using Chromium and/or Midori without these issues.  Perhaps the next upgrade to Firefox 7.1 will not have this bug.

---


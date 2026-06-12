---
title: "We Need A Firefox Fix"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by Garland Fox on 2011-11-05
My wife has a hp desktop running 64 bit 10.04 Lucid that dual boots along side Windows 7.

I have no idea on checking error logs or any of that.

I searched and tried fixes moving .mozilla and reinstalling firefox to no help there.

The problem: She boots into linux, shortcuts to yahoo mail; then exits when finished with mail.
Then most often clicks shortcut to Facebook website and a box pops up that says firefox is still running and not responding... and to close the instance of firefox before running it again. OR restart.
   Either restarting or using kilall firefox-bin clears it.
VLC add on suspected but was not installed.
Cant figure it out - started about a month ago.

Any ideas?

---

### Post by CharlesA on 2011-11-05
Do you have it set to clear history on exit?

---

### Post by as2000 on 2011-11-05
This has been discussed and I suggest you try to update Firefox to the current version. I have updated it simply by installing Ubuntu Tweak and then enabling the PPA for Firefox. It was pretty easy but you can read more about it [here]("http://ubuntuforums.org/showthread.php?t=1857944")

---

### Post by Garland Fox on 2011-11-05
Thanks for reply- we set that now will give it a try - it is intermittent problem so we wait and see

---

### Post by Garland Fox on 2011-11-05
By current version you mean 7 or whatever it is that comes with the new 11.10?

---

### Post by CharlesA on 2011-11-05
> **Garland Fox said:**
> By current version you mean 7 or whatever it is that comes with the new 11.10?
They probably mean 7. I'm not sure which version comes with 11.10.

---

### Post by vasa1 on 2011-11-05
> **as2000 said:**
> This has been discussed and I suggest you try to update Firefox to the current version. I have updated it simply by installing Ubuntu Tweak and then enabling the PPA for Firefox. It was pretty easy but you can read more about it [here]("http://ubuntuforums.org/showthread.php?t=1857944")

Just curious but why does one need to install Ubuntu Tweak in order to update Firefox?

If OP is running 11.10, Firefox 7 should be installed and updates will be automatic.

---

### Post by thenixedreport on 2011-11-05
If it's still causing you problems, then open up System Monitor, go to the Processes tab, select Firefox, then click End Process.  Wait a few moments.  If it's not off the list, right-click and choose Kill Process.  For some reason, Firefox doesn't unload itself completely from memory (at least that was the case in the past).

---

### Post by vasa1 on 2011-11-05
> **CharlesA said:**
> They probably mean 7. I'm not sure which version comes with 11.10.

Version 7.0

---

### Post by Garland Fox on 2011-11-05
Wife running 10.04 LTS which does not use the latest version of firefox. I guess it would be okay to install the new 7, I dont know.

---

### Post by CharlesA on 2011-11-05
> **vasa1 said:**
> Version 7.0

Ah, thanks.

> **Garland Fox said:**
> Wife running 10.04 LTS which does not use the latest version of firefox. I guess it would be okay to install the new 7, I dont know.

10.04 came with 3.2. You'd have to add the PPA to get that bumped up to the latest version.

See [here]("http://ubuntuforums.org/showthread.php?t=1712247") if you want to bump to the latest version. :)

---

### Post by Garland Fox on 2011-11-05
Ok may try that going to 7.0 if this clear history thing doesn't work

Thanks much

---

### Post by CharlesA on 2011-11-05
> **Garland Fox said:**
> Ok may try that going to 7.0 if this clear history thing doesn't work

Thanks much
Was "clear recent history on exit" set? I know I've run into the same error on my work machine when I close ff and then try to reopen it since it's still running the sanitize script.

---

### Post by Garland Fox on 2011-11-05
No it was not set to clear - I thought you meant to set it to clear history and try that-- BUT I see what you meant now

There I go Assuming again instead of listening

We try this awhile and probably upgade to 7.0 if it continues to act up. Thanks Much

---

### Post by CharlesA on 2011-11-05
> **Garland Fox said:**
> No it was not set to clear - I thought you meant to set it to clear history and try that-- BUT I see what you meant now

There I go Assuming again instead of listening

We try this awhile and probably upgade to 7.0 if it continues to act up. Thanks Much
Happens to everyone. :)

Good luck with the upgrade.

---

### Post by thenixedreport on 2011-11-05
Version 7 is supposed to fix some memory leak issues, so it would probably be a good idea to update.  I'm not running 10.04 (11.10 at the moment is what I run), so I wouldn't know if it was backported by now or not.

---

### Post by CharlesA on 2011-11-05
> **thenixedreport said:**
> Version 7 is supposed to fix some memory leak issues, so it would probably be a good idea to update.  I'm not running 10.04 (11.10 at the moment is what I run), so I wouldn't know if it was backported by now or not.

You'd have to add the PPA for 10.04.

---

### Post by dniMretsaM on 2011-11-05
> **Garland Fox said:**
> Then most often clicks shortcut to Facebook website and a box pops up that says firefox is still running and not responding... and to close the instance of firefox before running it again. OR restart.
   Either restarting or using kilall firefox-bin clears it.
VLC add on suspected but was not installed.
Cant figure it out - started about a month ago.

Deleting (or renaming) ~/.mozilla SHOULD fix the problem. The fact that it didn't seems odd. Try renaming it and then run this in terminal:
```
sudo apt-get purge firefox
sudo apt-get install firefox
```

Or you could run this, which will do the same as the above, and will update you to FF 7.0.1 (latest stable version):
```
sudo apt-get purge firefox
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by enkay009 on 2011-11-05
Well I'm not sure if you found a fix for this. But if it helps...

Firefox tends to create a lock file in your profile directory to prevent you from launching Firefox while it's still running.

Get rid of the lock and you should be good.

[http://kb.mozillazine.org/Profile_in_use#Remove_the_profile_lock_file](http://kb.mozillazine.org/Profile_in_use#Remove_the_profile_lock_file)

I don't know if you plan on jumping between different OSes or if you're simply looking to move your settings to a new OS, but if it's the first take a look at Firefox Sync. This allows you to sync your settings and bookmarks across many machines. For example having the same bookmarks at work and at home.

[http://www.mozilla.org/en-US/mobile/sync/](http://www.mozilla.org/en-US/mobile/sync/)

---

### Post by Garland Fox on 2011-11-05
OK thanks for the code - will probably use it here shortly

GF

---

### Post by Garland Fox on 2011-11-05
OK will check out the lock file.

Not jumping around OSes- That just the way the wife use her puter...

Thanks again

---

### Post by CharlesA on 2011-11-05
> **dniMretsaM said:**
> 
Or you could run this, which will do the same as the above, and will update you to FF 7.0.1 (latest stable version):
```
sudo apt-get purge firefox
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install firefox
```

Thanks for that. I just installed FF7 on my Lucid box. :)

---

### Post by lovinglinux on 2011-11-05
Just to add that sometimes the what causes the problem with Firefox not closing is the plugin-container. Disabling it might solve the problem, but then Firefox will crash entirely if flash crashes. To disable the plugin container, type *about:config* in the address bar, then *dom.ipc.plugins.enabled* in the filter and double-click the resulting preference to disable it.

For more information see [http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins](http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins)

BTW, Firefox 8 is just around the corner. I have been testing it today and it is really faster than 7 in regard to page loading time. you should be able to get it from the mozillateam ppa in a few days.

See [Firefox 7 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by as2000 on 2011-11-05
> **vasa1 said:**
> Just curious but why does one need to install Ubuntu Tweak in order to update Firefox?


Because it is easy and I am too lazy to run the command line! ;)

---

### Post by kaldor on 2011-11-05
<edit>
Oops, guess this information is entirely useless at this point. Good luck, though- it should be a simple solution.
</edit>

I used to have the OP's exact issue back on 9.10 and 10.04. I haven't seen that bug since around 4.0.

I may be overlooking previous posts, but upgrade to the latest stable version of Firefox. There are many improvements and you've got nothing to lost :)

Add [_the PPA_]("https://launchpad.net/~mozillateam/+archive/firefox-stable") as described on other posts.

Or, copy and paste these commands in order:

```
sudo apt-add-repository ppa:mozillateam/firefox-stable
```
```
sudo apt-get update
```
```
sudo apt-get install firefox
```

This will add the Stable repository, update the list, then install the latest Stable version of Firefox.

---


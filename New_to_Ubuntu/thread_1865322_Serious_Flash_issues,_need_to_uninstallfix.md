---
title: "Serious Flash issues, need to uninstall/fix"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by Psyael on 2011-10-20
Hey folks, I've got two issues with the Flash plug-in. I'm afraid I started off with a simple problem and then made it worse while trying to fix it.:(

Problem 1: Some Flash video sites cause the plug-in to crash. I'm not sure what this is, but I discovered that using a Guest Session or other account solved it. So the problem is specific to my Home directory, not universal.

Problem 2: Before finding that out, I did every manner of installing and uninstalling Flash known to man, and now I have Flash installed even when I've removed all the packages (I messed about a Firefox plugin and a Flash fixer app while installing and uninstalling it every which way). Now I've got even MORE problems, like trying to skip to a forward point in YouTube videos causes blackouts, on all accounts.

I need to delete Flash plugins beyond the provided packages. I have Firefox and Chrome, where are the files I should delete? And once I've solved that, anything I should try deleting in my home folder? Should I just make a new account and start over?

I was about to format/reinstall, but I figured given that my original problem was account-specific I should try and troubleshoot it if possible.

---

### Post by waynefoutz on 2011-10-20
Try installing Opera browser and use that on sites that are heavy on Flash. For some reason, Opera and Flash play nice with each other.

---

### Post by oldsoundguy on 2011-10-20
OR, install FlashGet into Firefox and let it clean things up and install the newest stable version.

---

### Post by garvinrick4 on 2011-10-20
> I need to delete Flash plugins beyond the provided packages. I have Firefox and Chrome, where are the files I should delete?
Close all running Firefox.
```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
``````
sudo rm -f /usr/lib/mozilla/plugins/*flash*
``````
sudo rm -f ~/.mozilla/plugins/*flash*
``````
sudo rm -f /usr/lib/firefox/plugins/*flash*
``````
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
```Now reinstall flash any of a number of ways available.
> And once I've solved that, anything I should try deleting in my home folder? No /home has nothing to do with flash.

---

### Post by Psyael on 2011-10-20
Is there some way I can get a crash report then? I'm still crashing the plug-in when watching streaming videos on certain sites (ex: giantbomb.com) but not when using another account, which is using the same plug-in and the same NVidia driver.

There's SOMETHING in my user's config that is causing the plugin to break.

---


---
title: "message when doing apt upgrade"
date: 2020-08-16
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-08-16
Hi all, I got a message today when doing apt upgrade, and I'm not sure what it means. I think it *might* be a configuration file that I have edited via the software updater GUI that it wants to replace, but I'm not sure...

[ATTACH=CONFIG]286712[/ATTACH]

I opted to keep the locally modified version as I'm sure if that was the wrong thing to do I'll get chance to correct it on the next upgrade, but can anyone tell me what it's all about?

---

### Post by CelticWarrior on 2020-08-16
I suspect that you've made changes to that file before, maybe pinning some package or something like that. The updater wouldn't have asked if the file was in the default state.

---

### Post by ajgreeny on 2020-08-16
The unattended-upgrades package is one that I always remove straight away from all my systems as I like to see what's happening all the time and update when I want to, not when the system decides to.

I accept that I am different from many other users in this, and other respects regarding system management, but that aside it is likely that any changes that you have made to the default timings or your choice of packages that auto-upgrade may have also made changes to that conf file that the message is asking about.

However, for possibly more detail that should help you have a read through [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates) which I think explains all this.
I don't think it will matter which one you choose as you can easily make your own choice again in the Updates tab of Software-sources.

---

### Post by ActionParsnip on 2020-08-16
I suggest you keep the current one. It's my default option.

---

### Post by Impavidus on 2020-08-16
I got that message a few days ago. I forgot about removing unattended upgrades after my fresh install back in July. It's probably not important. Just check the settings for your upgrades.

---

### Post by jcdenton1995 on 2020-08-19
> **ajgreeny said:**
> I don't think it will matter which one you choose as you can easily make your own choice again in the Updates tab of Software-sources.

I believe this is actually what I have done in the past and possibly the reason for the message, like you I have it set to check for updates daily, notify me of security updates immediately and notify me of all other updates weekly, so I think it's probably these settings that are saved in that config file.

Either way it seems nothing to worry about :)

---


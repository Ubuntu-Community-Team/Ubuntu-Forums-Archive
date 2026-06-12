---
title: "[SOLVED] KDE4 Install woes"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by tennesseebrewer on 2008-10-23
Well, I am pretty new to the switch from *gulp Windows to *ta-da Linux. So far, I absolutely love it! I can't help but try to get everyone on Ubuntu because it is so nice for the new user. I installed Ubuntu off of a disk from a magazine and then downloaded Kubuntu with the KDE4 environment. And then the trouble began...

I went to install a bunch of items from the synaptic Package Manager and they all downloaded just fine. However when they went to install, the progress bar showed that it was done, but the message in the terminal box showed it was still reading the database. Then I left it for around four hours and when I got back, still the same thing. It never installed anything and I could not close it. I had to do a hard restart and no programs were installed.

Has anyone else had this issue? should I try installing things in Gnome rather than KDE4?

---

### Post by aysiu on 2008-10-23
I've never heard of this issue, but that doesn't mean it's not a real problem. Maybe it's having trouble with the repository mirrors you're using (in which you can try other mirrors)?

There are several parts to the package management process:
1. Connect to the repositories to see what's available to install or not
2. Download the appropriate packages needed for installation
3. Unpack those packages
4. Set up those packages

Do you know at which part of the process it started hanging?

---

### Post by tennesseebrewer on 2008-10-27
Well, I can tell you that it is at the point when the install should be complete. The really interesting thing is, I can use synaptic package manager successfully in the Gnome environment, but when I do it in KDE4, it hangs up.

---


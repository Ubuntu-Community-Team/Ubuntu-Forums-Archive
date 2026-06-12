---
title: "Ubuntu Internal Error?"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by Daniel Tan on 2012-11-22
Hi, I have been getting many of this popup lately. How do I resolve this issue? Thank you in advance.

---

### Post by arpanaut on 2012-11-22
That is Apport, the error reporting system built into Ubuntu.
If you want to help with improving Ubuntu, hit continue and follow through with the reporting process.
You will need to create a Launchpad account to follow up on the bug report.
You will be given the chance to do that later on in the process.
After you make the report you won't bugged about the same error again. (or you can dismiss the prompt)

You can disable apport if you want, but I'll let you figure out how to do that as I feel that users should be involved in improving Ubuntu.

---

### Post by offgridguy on 2012-11-22
> **Daniel Tan said:**
> Hi, I have been getting many of this popup lately. How do I resolve this issue? Thank you in advance.

I had the same popup , but in my case i could not log in.  So i installed another ubuntu
version  over it, effectively wiping out the previous version.
      I really had nothing of importance to worry about losing, so i didn't worry about it.
Probably an extreme solution, but at least i have something that works again. :)

---

### Post by monkeybrain2012 on 2012-11-22
I see this a lot but they are all false alarms. This is apparently a bug in Apport. You should just disable it. Normally it is enabled by default only during alpha and beta testing stages and is disabled after release but somehow they forget to disable it(??)

[http://askubuntu.com/questions/156720/ubuntu-12-04-issues-internal-error-system-problem](http://askubuntu.com/questions/156720/ubuntu-12-04-issues-internal-error-system-problem)

---

### Post by arpanaut on 2012-11-22
> **monkeybrain2012 said:**
> I see this a lot but they are all false alarms. This is apparently a bug in Apport. You should just disable it. Normally it is enabled by default only during alpha and beta testing stages and is disabled after release but somehow they forget to disable it(??)

[http://askubuntu.com/questions/156720/ubuntu-12-04-issues-internal-error-system-problem](http://askubuntu.com/questions/156720/ubuntu-12-04-issues-internal-error-system-problem)

I think that there was a policy change for 12.10 and beyond to leave apport enabled to gather more error reports and data on the more prevalent issues with Ubuntu and a greater focus on solving those issues.
This video is a bit long but shows what is being implemented to help with the bug fixing process and focus.
[https://www.youtube.com/watch?v=PPQ7k0jRUE4#t=30m10s](https://www.youtube.com/watch?v=PPQ7k0jRUE4#t=30m10s)

Edit: It is a bit presumptuous to assume that all of these are false alarms or a bug in apport, I have had great success from reporting bugs through apport. during testing and otherwise, If it was a bug I'm sure it has been fixed or the efforts shown in that video would not be going forward.

---

### Post by monkeybrain2012 on 2012-11-22
> **arpanaut said:**
> 
Edit: It is a bit presumptuous to assume that all of these are false alarms or a bug in apport, I have had great success from reporting bugs through apport. during testing and otherwise, If it was a bug I'm sure it has been fixed or the efforts shown in that video would not be going forward.

Well it popped up very 10 minutes even when the PC was idle, it'd better be false alarms or I would think that 12.04 shouldn't have been released in the first place, let alone being a LTS. :) I have experienced no problem at all after turning it off.

---

### Post by SantaFe on 2012-11-23
I'm pretty sure they might be false alarms, as I just had one pop up for Apport just a little while ago. ;)  Pretty funny when your error reporting app says it has an error.:)

---


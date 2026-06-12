---
title: "Stop Thunderbird From Autostarting"
date: 2015-11-29
forum: New to Ubuntu
---

### Post by stephen91 on 2015-11-29
Hello,

I am new to Ubuntu 14.04.3 coming from the Windows environment.

I recently installed this Ubuntu and in playing around with the software I started the Thunderbird mail client to explore it and now Thunderbird always starts when I boot Ubuntu.

I don't intend to use Thunderbird at this point. Is there some way to prevent it from autostarting when Ubuntu boots?

I searched around but I didn't see any useful information on how to stop Thunderbird from starting.

Please help and thanks.

---

### Post by stephen91 on 2015-11-29
Hello,

I am new to Ubuntu 14.04.3 and linux in general (I'm a Windows user).

While reading through some comments I see people referring to the "Session Manager" in Ubuntu. I poked around in my Ubuntu 14.04.3 installation and I couldn't find this "Session Manager" (the closest function I could find was the "System Settings").

Does "Session Manager" exist in Ubuntu 14.04.3 and if so where please?

Let me thank you in advance for your help.

P.S.
The reason I am looking for this "Session Manager" is because I ran across it in some postings about how to stop the Thunderbird Mail Client from autostarting when Ubuntu boots. I launched Thunderbird once and now it always autostarts even though I quit the app. Some comments indicated that I should go into "Session Manager" and clear the log to help prevent the autostart of Thunderbird.

---

### Post by SlidingHorn on 2015-11-29
This would be better suited as a further post on your original request here: [http://ubuntuforums.org/showthread.php?t=2304739](http://ubuntuforums.org/showthread.php?t=2304739)

Try to keep issues to one thread, as it clutters the forum and makes it more difficult for others to help, as they'd have to keep up with two threads instead of just one.

---

### Post by coffeecat on 2015-11-29
Threads merged.

---

### Post by grahammechanical on 2015-11-29
Perhaps they mean Startup Applications? Search for it in the Dash.

[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html)

This still works on 15.10

[https://help.ubuntu.com/community/ShowHiddenStartupApplications](https://help.ubuntu.com/community/ShowHiddenStartupApplications)

Regards

---

### Post by stephen91 on 2015-11-29
> **coffeecat said:**
> Threads merged.


Many apologies for my mistake.

My intention was to ask two questions: 1- What is "Session Manager", 2- How to stop Thunderbird from autostarting.

I only added a Post Script about Thunderbird in the Session Manager thread as background to why I was asking about Session Manager.

I will be more careful next time, again many apologies.

---

### Post by stephen91 on 2015-11-29
> **grahammechanical said:**
> Perhaps they mean Startup Applications? Search for it in the Dash.

[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html)

This still works on 15.10

[https://help.ubuntu.com/community/ShowHiddenStartupApplications](https://help.ubuntu.com/community/ShowHiddenStartupApplications)

Regards


Thank you for the information. I checked into this and as far as I can tell Thunderbird isn't showing up in the Startup Applications list.

Does anyone have any other suggestions on what I can look for to prevent Thunderbird from autostarting?

Thanks.

---

### Post by Kpenguin on 2015-11-29
Are you using just plain Ubuntu, or another desktop environment such as XFCE or KDE? Xubuntu has an option to restore your last session on startup, so that could be the problem.

---

### Post by stephen91 on 2015-11-29
> **Kpenguin said:**
> Are you using just plain Ubuntu, or another desktop environment such as XFCE or KDE? Xubuntu has an option to restore your last session on startup, so that could be the problem.

I went to the Ubuntu website, downloaded the Ubuntu 14.04.3 LTS package, and installed that code. Is that what you refer to as "plain" Ubuntu?

Assuming that the OS is restoring my last session how can I clear that please?

Many thanks.

---

### Post by buzzingrobot on 2015-11-29
Out of curiosity, how did you initially launch Thunderbird?

If you don't intend to use Thunderbird, remove it and that should end the startup problem.

---

### Post by mc4man on 2015-11-29
What makes you think TB is autostarting?
(if it's that message indicator in top right panel that's not thunderbird, it's an indicator that show up once you've used an appropriate app that then can be started from it or make use of.

---

### Post by stephen91 on 2015-11-30
> **buzzingrobot said:**
> Out of curiosity, how did you initially launch Thunderbird?

If you don't intend to use Thunderbird, remove it and that should end the startup problem.

I went to Dash, searched on Thunderbird, and clicked on the icon. After that I saw the Thunderbird envelope icon in the upper right menu bar ever since.

Yes I could remove Thunderbird but I was hoping there is a way to stop it from autostarting.

Thanks.

---

### Post by pqwoerituytrueiwoq on 2015-11-30
check there startup applications
if t is xfce check if session restore is check on the logout screen
also delete the last session restore data to be sure that feature has been buggy in my exp (have not used it in a while though)
i have had issues with it double started apps that are in startup

---

### Post by buzzingrobot on 2015-11-30
> **stephen91 said:**
> I went to Dash, searched on Thunderbird, and clicked on the icon. After that I saw the Thunderbird envelope icon in the upper right menu bar ever since.

Yes I could remove Thunderbird but I was hoping there is a way to stop it from autostarting.

Thanks.

As McMan said, that icon in the panel is not Thunderbird.  That's a messaging indicator to tell you when, among other things, you have new mail.

If Thunderbird was autostarting, you'd see Thunderbird opening on the desktop.

---

### Post by stephen91 on 2015-11-30
> **mc4man said:**
> What makes you think TB is autostarting?
(if it's that message indicator in top right panel that's not thunderbird, it's an indicator that show up once you've used an appropriate app that then can be started from it or make use of.

Wow, lol, that is very enlightening.

Let me thank everyone for their help, I am closing the thread now.

---


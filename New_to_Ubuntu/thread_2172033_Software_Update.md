---
title: "Software Update"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by novice_penguin on 2013-09-02
Hi all, I have recently encountered a new problem, but I do not know why/how this was changed.  Before, when I ran the sudo apt-get update, if there was an update available, it would prompt the Update manager to update any software.  Now, if I run the same command and there is an update available, I am not prompted.  I have double-checked this several times by running sudo apt-get update, then when not prompted, I go to Software Up To Date, and I have software that needs to be updated.  Am I missing something here?  How could this have happened, and should I be worried?  Thanks!

---

### Post by plucky on 2013-09-03
> **novice_penguin said:**
> Hi all, I have recently encountered a new problem, but I do not know why/how this was changed.  Before, when I ran the sudo apt-get update, if there was an update available, it would prompt the Update manager to update any software.  Now, if I run the same command and there is an update available, I am not prompted.  I have double-checked this several times by running sudo apt-get update, then when not prompted, I go to Software Up To Date, and I have software that needs to be updated.  Am I missing something here?  How could this have happened, and should I be worried?  Thanks!

What version of Ubuntu are you running?

You will only get prompted daily by the **Update Manager** if there are **security** updates.This behaviour was changed a while back.

If there are only **Recommended** updates, you will only get prompted once a week. It does a countback to when the last updates were installed.

Of course it doesn't stop you installing the **Recommended** updates when you want.

Good Luck

---

### Post by newb85 on 2013-09-03
If you're in 12.04, go to Edit>Software Sources in Software Center, and go to the Updates tab.  If you're in 13.04, open Software & Updates and go to the Updates tab.  The option of when you're notified of available updates should be there.

---

### Post by grahammechanical on 2013-09-03
Stop running sudo apt-get update. Let the software Updater/Update Manager do its job. Either that or follow sudo apt-get update with
```
sudo apt-get upgrade
```

and do all the updating through the command line. Update Manager runs those two commands. The prompt is to allow you to authorise running apt-get update, which then allows you a review of what is to be downloaded and installed with your authorization.

It is just coincidence that Update Manager is flagging an update about the same time as you are running the apt-get command in a terminal. 

Regards.

---

### Post by novice_penguin on 2013-09-03
Ok thanks all!

---

### Post by isa.dsouza on 2014-01-04
Ubuntu hasn't updated for more than a week now: before this there were updates every single day. I didn't do anything to the system. There is no warning from Software Updater/Update Manager as there usually was. Is my system dead? Should I be freaking out? Any answers and/or clues will be appreciated.

---

### Post by plucky on 2014-01-04
> **isa.dsouza said:**
> Ubuntu hasn't updated for more than a week now: before this there were updates every single day. I didn't do anything to the system. There is no warning from Software Updater/Update Manager as there usually was. Is my system dead? Should I be freaking out? Any answers and/or clues will be appreciated.

Have you read the thread?

What happens if you run the Software Updater?

Does it say there are Updates to Install?

Any Errors reported?

If there are Updates, what type of Updates? 

Recommended or Security?

---

### Post by isa.dsouza on 2014-01-04
Have you read the thread? Yes.

What happens if you run the Software Updater? It runs.

Does it say there are Updates to Install? No.

Any Errors reported? System problem detected. Just a few minutes ago. This doesn't happen all the time though.

If there are Updates, what type of Updates? No.

Recommended or Security? No updates. It says the software is up to date.

---

### Post by Rooster2000 on 2014-01-26
I have had similar problem after I upgraded my Lubuntu from 13.04 to 13.10.

Few days ago I noticed that software updater hasn't showed up as often as it used to. When I ran it manually today, there was a lot of updates, both security and other, which installed without problems. Now software updater says that my system is up to date, but I cannot trust that it will notify me when there are updates available, although it is configured to check for updates daily and display security updates immediately.

---


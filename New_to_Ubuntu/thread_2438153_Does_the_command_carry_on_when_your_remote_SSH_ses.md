---
title: "Does the command carry on when your remote SSH session ends?"
date: 2020-03-06
forum: New to Ubuntu
---

### Post by cable_guy on 2020-03-06
Hi all,

I am thinking of uploading my treasured family photos which I store on Ubuntu to a Cloud Provider using Rsync or Rclone.

This will take over a week for the bandwidth I have. 

During this time it is likely that my computer I use to SSH into my Ubuntu will reboot.

Will the command continue to run, or stop when the computer does?

---

### Post by CelticWarrior on 2020-03-06
You may need a script to start the process and detach.

PS - Some feedback in your other threads would be great! And if meanwhile you found a solution please post it and then use the thread tools > Solved.

---

### Post by SeijiSensei on 2020-03-06
You can keep processes running after you log out by running them in the background like this:
```
/path/to/some/program &
```
However that won't survive a reboot.  For that you'd probably need a script that runs from [cron]("https://help.ubuntu.com/community/CronHowto"). I'd write a script that writes a "semaphore" file to some persistent directory like $HOME when it is launched.  Schedule the script to run automatically at boot and have it look for the file.  If it finds it, the script resumes the transfer.  When the transfer is complete have the script delete the file.

---

### Post by CelticWarrior on 2020-03-06
> **SeijiSensei said:**
> You can keep processes running after you log out by running them in the background like this:
```
/path/to/some/program &
```
However that won't survive a reboot.  For that you'd probably need a script that runs from [cron]("https://help.ubuntu.com/community/CronHowto"). I'd write a script that writes a "semaphore" file to some persistent directory like $HOME when it is launched.  Schedule the script to run automatically at boot and have it look for the file.  If it finds it, the script resumes the transfer.  When the transfer is complete have the script delete the file.

I think the OP isn't expecting a reboot in the Ubuntu machine, only at the machine accessing it remotely.

---

### Post by SeijiSensei on 2020-03-06
> **CelticWarrior said:**
> I think the OP isn't expecting a reboot in the Ubuntu machine, only at the machine accessing it remotely.
In that case I'd bet that rsync will wait when it can't see the remote and resume the transfer again once the remote comes back online.  

OP, why don't you try this as a test?  Begin an rsync transfer on the Ubuntu machine, then reboot the remote.  What happens?

Notice that you want to set up the transfer to come from the Ubuntu machine to the remote, not the reverse, if you want to protect against a remote reboot.

---

### Post by cable_guy on 2020-03-06
common sense is what I came for, it's been delivered in spades by @seijisensei! I just needed to test.

I was concerning myself with this one time big transfer, but I could just test first. facepalm.jpg!!!! I actually work in IT btw.....

It also made me think, what I REALLY need to test is the cron job which I'll be using forever more.

---


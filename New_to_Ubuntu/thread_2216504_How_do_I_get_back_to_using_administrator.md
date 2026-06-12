---
title: "How do I get back to using administrator ?"
date: 2014-04-12
forum: New to Ubuntu
---

### Post by hebdave on 2014-04-12
Hi I went into the user account settings today but could not find the advanced settings that tech radar talks about - [http://www.techradar.com/news/software/operating-systems/how-to-secure-your-linux-system-915651](http://www.techradar.com/news/software/operating-systems/how-to-secure-your-linux-system-915651) . So foolishly I set the administrator to a standard account to look for them. I then clicked the ubuntu updates and it asked for a superuser password. I did not realise this would mean my normal password which I had when I was administrator would not work. So I went back to change my user account back to administrator and it also asked for the superuser password. For some reason this is not my normal password. Google says its a root password that is needed which is different I believe. I looked at this for a possible solution -
[http://www.tuxradar.com/answers/343](http://www.tuxradar.com/answers/343) but am unsure if it will help me back to becoming an administrator again.

Its all a bit silly and frustrating but can you help me sort it #-o

Many thanks !!

---

### Post by Impavidus on 2014-04-12
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Root account is locked by default and best kept locked. This should help you getting back your sudo rights.

---

### Post by hebdave on 2014-04-12
Hi I am still a bit unsure of how to proceed. I do have ubuntu 12.04 LTS. However my username is still there and active if I click on user accounts in the settings. So since I have not screwed up any other parts of ubuntu and just clicked on 'standard account' I think I just need one command only to solve it. The command in recovery mode for a 12.04 Ubuntu being -
 
adduser username admin (with username of course being my username)

So from reading the website you sent me too I do the above only. However I ought to perhaps expand on what I did wrong. I merely just went into my user account and clicked unlock and then was able to change the account from Administrator then to 'Standard' after using my password. It was as simple as that and I could not then update without it asking for a 'Password for root'. The authentication box says I need authentication as a super user to perform this action. While I am sure this is normal I wanted to be certain we were on the same page as the ' adduser myusername admin ' command appears to ask me to ' add a user ' from what I perceive. My user is already ' available ' so I wonder if adding another is correct or the command means something slightly different. I have no problem going to recovery mode but worry if I do something wrong here is might not boot or something else.

Many thanks !

---

### Post by grahammechanical on 2014-04-12
I do not think that it is possible to change a user account from Administrator to Standard user without Unlocking the utility and that requires our user password as we are the administrator.

The problem is that you as a user are now not recognised as an administrator. That command does not do anything that will stop Ubuntu from loading. Go to Recovery mode and at the Recovery menu run Network. That will put the file system into read/write mode, which is necessary if we are to change system files. Then when back at the Recovery menu select Root. Run the command and type exit to get back to the Recovery menu. Then select Resume. You should be able to log in. Now you will need to see if you can work as administrator.

By the way, Resume brings us to a desktop without loading a proprietary video driver so you may notice a less than good visual experience. Reboot.

For future reference, please understand that in Ubuntu we are both administrator and standard user. When we need to be administrator our password will work to authenticate administrator tasks. Other than that we work as a standard user. This means that if we leave our machine and someone else tries to do damaging stuff to the OS they will be unable to as they will only be working as a standard user. Unless we have been negligent with our password security.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 

Regards.

---

### Post by hebdave on 2014-04-12
Hi after using networking it won't go past the black load up screen and so shows no root starting command. So I used the original instructions telling me to go via the 'drop to root shell prompt'. Then I typed in mount -o rw,remount /. This dropped me down one place to a new root command prompt (this is correct so far according to instructions) as far as I can tell. I then hoped it was a read and write or what ever it needs to be at that point. Unfortunately after typing adduser fredblogs admin it says 'username fredblogs not recognised' or similar. I did of course then just type exit and resume normal boot.
 
Is there something I need to have typed instead ?

Many thanks.

---

### Post by steeldriver on 2014-04-12
Are you sure it didn't complain about the *group* not being recognised? The group for 'Administrator' users is no longer called 'admin', it's called 'sudo' (since at least 12.04 - earlier I think)

You can check which of the two groups exists using getent

```
getent group {admin,sudo}
```

Then it would be

```
adduser fredblogs sudo
```

or equivalently (my preferred group management command)

```
gpasswd --add fredblogs sudo
```

---

### Post by hebdave on 2014-04-12
High thanks that seems to have fixed it. I notice when I typed adduser Fred admin I got a different error to when I typed in adduser fred admin (notice all lowercase fred). One said like I referred to above 'user not recognised' and the all lowercase 'group not being recognised'. Intresting for someone perhaps to no particularly if your a beginner in Ubuntu reading this thread. So I ended up mounting  , adduser fred admin (at this point is does not work in 12.04 ) and then adding the next two commands just above you gave me to try -this then works !

So thank you. I thought completing the thread may help an individual soon enough.

---

### Post by steeldriver on 2014-04-12
Yes as you spotted (almost) everything is case sensitive in Linux (and Unix in general) - commands, usernames, filenames etc.

Glad you got it fixed - if you could take the time to mark the thread [SOLVED] that would help others even more

---

### Post by hebdave on 2014-04-13
Are yes thanks for the reminder !

---


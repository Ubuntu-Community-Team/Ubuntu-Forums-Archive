---
title: "sudo is not playing nicely"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by infraction2 on 2014-03-30
Ok, I'm not a beginner but this seems like the place to be for this question.  'sudo' lately does not behave as expected.  I expect to enter 'sudo' and be prompted for a password.  Instead, I get usage information.  I am still on 12.04, and I suspect some update that I allowed to happen has trashed either sudo itself, or my permissions.

Any ideas anyone?

---

### Post by tfrue on 2014-03-30
Will you post an example of the command you are typing?

---

### Post by r.stiltskin on 2014-03-30
You don't type "sudo" by itself.  You type sudo followed by a command that you need to run as superuser, such as

```
# to use nano to edit your /etc/hosts file
sudo nano /etc/hosts
```
or
```
# to install chromium-browser
sudo apt-get install chromium-browser
```
and so on ...

---

### Post by buzzingrobot on 2014-03-30
What happens when you supply sudo's full path?  E.g., "/usr/bin/sudo nano ..."?

Don't see how this could happen with an update, but run "alias" in a terminal just to see if sudo has been aliased. If you see a line with "sudo" in it, copy and post it here.

What does the "usage information" say?

---

### Post by mcduck on 2014-03-30
> **r.stiltskin said:**
> You don't type "sudo" by itself.  You type sudo followed by a command that you need to run as superuser, such as

```
# to use nano to edit your /etc/hosts file
sudo nano /etc/hosts
```
or
```
# to install chromium-browser
sudo apt-get install chromium-browser
```
and so on ...

I agree this is the most likely reason. Most programs and commands will give you basic usage instructions if you try to run them without providing all required parameters in the command, in sudo's case either a command to execute with sudo or one of the optiosn that are used to launch a shell session ("sudo -i", for example). So trying to just run "sudo" *should* give you basic usage instructions.

---

### Post by infraction2 on 2014-03-30
Many thanks to all that replied....you input was certainly of great value.  But, and this is just an exploratory question, when did sudo stop behaving as I described the expected behavior I was ready for.  I really do not think I am off-base here.....and I will admit that I have not had the need to go to the command line in quite some time (obvious kudos to the Ubuntu community and all associated developers).  But I am dead certain that in the past I could just enter 'sudo' on the command line prompt and then be presented with a password request.  A trivial question of course, but computers are my profession......I simply do not get what went wrong here, and I'm really only curious in the history that will resolve my confusion.  Or maybe I'm just being anal!!

---

### Post by bab1 on 2014-03-30
> **infraction2 said:**
> Many thanks to all that replied....you input was certainly of great value.  But, and this is just an exploratory question, when did sudo stop behaving as I described the expected behavior I was ready for.  I really do not think I am off-base here.....and I will admit that I have not had the need to go to the command line in quite some time (obvious kudos to the Ubuntu community and all associated developers).  But I am dead certain that in the past I could just enter 'sudo' on the command line prompt and then be presented with a password request.  A trivial question of course, but computers are my profession......I simply do not get what went wrong here, and I'm really only curious in the history that will resolve my confusion.  Or maybe I'm just being anal!!

You can just use sudo if you use the correct switch.  Both *sudo -i* or *sudo -s *will work.  They give you a root shell with differing environments.

---

### Post by Dave_L on 2014-03-30
> **infraction2 said:**
> ...  But I am dead certain that in the past I could just enter 'sudo' on the command line prompt and then be presented with a password request....

You may be confusing "sudo" with "su". The latter works the way you describe.

Since the root login is disabled by default in Ubuntu, "sudo" is normally used in place of "su".
More details: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by r.stiltskin on 2014-03-30
Maybe, infraction2, you are thinking of another Linux distro.  In general, "su" isn't used by itself in Ubuntu unless you have chosen to define a root password, which, as Dave_L points out, is not the usual practice in Ubuntu.

Or maybe you're thinking of
```
sudo su
```which will request your password, and then give you a root shell which will persist until you run "exit".

---

### Post by deadflowr on 2014-03-30
> **Dave_L said:**
> You may be confusing "sudo" with "su". The latter works the way you describe.

Since the root login is disabled by default in Ubuntu, "sudo" is normally used in place of "su".
More details: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

+1

sudo wants you to do something. (hence the do at the end)
If you don't tell it what to do, then it will offer up some suggestions.
Which is what it has done.

su, on the other hand, will simply prompt for the root password and then switch you over to that(root).

---


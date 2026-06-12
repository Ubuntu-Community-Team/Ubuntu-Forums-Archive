---
title: "Correct password not recognised"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by oddsteph on 2012-04-05
My uncle has a problem where he can no longer log in to his account using his password. It is definitely the correct password. I even tried logging in using the recovery option and changing the password, but it still claims the password is wrong. He has also tried using the on screen keyboard at login in case his keyboard layout was somehow changed, and logging in using the command line, but these did not work either. Does anyone have any idea how to fix this?

Thanks

(He is using 11.10 dual booted with windows 7 and installed about a month ago. As far as I know he has made no changes to cause the problem.)

---

### Post by Paqman on 2012-04-05
Hmm, odd. I would have suspected a dodgy key on the keyboard if he hadn't used the on-screen one.

You can [reset the password]("http://www.psychocats.net/ubuntu/resetpassword").

---

### Post by winh8r on 2012-04-05
Make sure his username does not have any spaces in it. For instance if the user name is bob smith , ubuntu will alter this to bobs as it does not allow spaces in logins/passwords.

You could try going into recovery mode and dropping to a root shell and creating a new user account:

```
adduser oddsteph
```

and try logging in via that account to check that login is possible then get to the bottom of what is causing the problem from there.

---

### Post by oddsteph on 2012-04-05
Thanks for the suggestions, I had already tried resetting the password but the new password didn't work either, and the username is just one word so that's not the problem.

When I tried adding a new user I got the following message:

groupadd: cannot lock /etc/group; try again later.
adduser: 'usr/sbin/groupadd -g 1001 steph' returned error code 10. Exiting.

Any thoughts?

---

### Post by winh8r on 2012-04-05
Drop to the root shell again and enter this :

```
 rm /etc/group.lock
```

Then repeat the```
 adduser oddsteph
```process again and see if you can get in now.

---

### Post by oddsteph on 2012-04-05
Tried that, got a new error:

rm: cannot remove '/etc/group.lock': No such file or directory

So that didn't work either, any more ideas?

---

### Post by winh8r on 2012-04-05
In the root shell again


enter:

```
cat /var/log/auth.log
```

and look for any error messages flagged up in there.

---

### Post by oddsteph on 2012-04-05
Well that showed up quite a few errors, but we don't know what they mean. The most common one was:

requirement "user ingroup nopasswdlogin" not met by user "bill"

But now it seems to be working *fingers crossed*. I have no idea what happened, but thanks very much winh8r, your help is very much appreciated.

---

### Post by winh8r on 2012-04-05
Glad to hear it's working again, I am at a bit of a loss to know why it stopped working in the first place.

probably best to run

```
sudo apt-get update && sudo apt-get upgrade
```

Just to make sure everything is up to date in case it has missed an update and there is a buggy bit of code somewhere.

Good Luck.

---


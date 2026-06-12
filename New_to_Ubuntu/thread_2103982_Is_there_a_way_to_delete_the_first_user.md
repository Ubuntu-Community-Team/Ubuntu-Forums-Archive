---
title: "Is there a way to delete the first user?"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by SteamDonkey74 on 2013-01-11
I have installed Xubuntu 12.04 LTS on a Dell Dimension 2400. Everything works just fine. I am transferring that machine to a friend of mine, and I have created a user profile for her and made it an admin, hoping I could then delete my account so that it's just off that machine. I was unable to do so from the users and groups window.

I know this is probably a real n00b kind of question, which is why it's here. I have searched other threads and while the answer is probably in one of them the things I have tried haven't yielded the result I am seeking.

Thanks in advance,
Adam

---

### Post by SteamDonkey74 on 2013-01-11
Because I don't fully know what I am doing, I am hesitant to take a hack at it with sudo, but would this work?

sudo userdel -r [username]

---

### Post by audiomick on 2013-01-11
I'm not sure if you can delete the first user, although I think it is possible. You would need to use sudo to do that. It is an administrator task.

Having said that, if you are passing the machine on, why not do a fresh install for your friend? Then she would have an install that is guaranteed fresh.

---

### Post by steeldriver on 2013-01-11
AFAIK there's nothing special about the first user account - apart from its group memberships of course. As long as you've got a second sudo account to delete it from it should be fine. Or you could do it from the recovery console. 

You'd probably be better using [FONT=Courier New]deluser[/FONT] rather than userdel - it's a higher level interface and has options to remove the user's home dir, or to remove ALL files on the system that are owned by the user. You may still need to remove the user private group separately I think.

However I agree that re-imaging would be a more thorough solution.

---

### Post by rburkartjo on 2013-01-11
steam that command will work fine. i used it once to delete my daughters account. suggestion make sure the account you made for her has admin  priv etc. log in under that new account and run
sudo userdel -r [username] in terminal to delete your account.

---

### Post by Paqman on 2013-01-11
> **steeldriver said:**
> As long as you've got a second sudo account to delete it from it should be fine. Or you could do it from the recovery console. 

You'd probably be better using [FONT=Courier New]deluser[/FONT] rather than userdel - it's a higher level interface and has options to remove the user's home dir, or to remove ALL files on the system that are owned by the user. You may still need to remove the user private group separately I think.


^ This

By default the user's home folders are not deleted, but you can use --remove-home to delete those too.

---

### Post by jerome1232 on 2013-01-11
```
sudo deluser --remove-home *[COLOR="Red"]usernamehere[/COLOR]*
```

Whoops, apparently I've had this tab open for a while and forgot to refresh it before posting.

:D

---

### Post by SteamDonkey74 on 2013-01-12
I got this to work. I had considered doing a clean install but this basically was a clean install I hadn't hardly used. I just absent-mindedly created an account for myself before I really started thinking. 

Thank you all for your help!

Adam

---


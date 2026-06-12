---
title: "can't login to console"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by boregard on 2012-03-02
Hello,Isn't the passw to login to console the same that you reguarly use to login? When I try to login to the console it says incorrect pass w.I have checked caps lock and Iam positive the passw is correct. Any help/advice will be appreciated.Thanks

---

### Post by Gremlinzzz on 2012-03-03
They should be the same/ did you ever change the password?:popcorn:

---

### Post by boregard on 2012-03-03
No, other than when I reinstalled ubuntu. It works fine when I Iogin or enter it using regular terminal. Can't figure out why it doesn't work when at the console. Thanks for reply.

---

### Post by matt_symes on 2012-03-03
Hi

It's a silly question however are you sure you are typing your user name in correctly as well.

Kind regards

---

### Post by winh8r on 2012-03-03
Does your username have spaces in it?

---

### Post by _0R10N on 2012-03-03
@winh8r Spaces are not allowed on usernames
@boregard you should try changing your password to something like "123456" and give it a try, just to get sure that it's your system who is messing up with your logging.
BTW, if you open a terminal and enter something like ```
sudo bash
``` you'll be prompted to enter your password, does it work?

Regards!

---

### Post by boregard on 2012-03-03
Hi all, I don't know what was wrong, After awhile I gave up and shut the console down & rebooted and it is now working. I just reinstalled ubuntu 2 days ago and used a new passw & username maybe that had something to do with the problem, I don't know. Anyways Thanks to everyone who replied. Best Regards

---

### Post by winh8r on 2012-03-03
> **_0R10N said:**
> @winh8r Spaces are not allowed on usernames


Thank you, I am well aware of that.

I was trying to ascertain whether the OP had spaces in the username as Ubuntu will automatically shorten a username with spaces.

If you create a user with the name Bob Smith and try to login to the console as Bob Smith you will receive errors when entering the password.

However Ubuntu will have shortened Bob Smith to bobs and login works perfectly when entering username=bobs and normal password for user Bob Smith.

---


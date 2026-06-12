---
title: "Keyring did not get unlocked"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by steelpython on 2012-06-03
After I log in, I keep getting a message saying that the keyring did not get unlocked, and I need to enter my keyring password.

How do I fix this, I'm not using auto-login and the passwords are the same for both login and keyring.

---

### Post by rburkartjo on 2012-06-03
try this 

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

### Post by scottbomb on 2012-06-24
That's not a fix, it's a workaround which creates a gaping security hole. Does anyone have a fix? It's very annoying. Why isn't my keyring getting unlocked when I log in? I'm the only user on this machine and I use a password to log in. Once I'm in, I shouldn't be pestered for my password again (unless, of course, I'm trying to sudo something).

---

### Post by jagdefalke on 2012-07-10
Bump.

My netbook with 12.04 has recently started doing this out of the blue.  I have vague memories of having this same problem once on my desktop with 10.04 but can't remember how I fixed it.   (I need to start keeping record of this stuff... haha!)

---

### Post by glennric on 2012-07-10
This usually happens when you have your computer set to automatically login to your account.  Since you are not entering your password to login the keyring is not unlocked, and must be later unlocked.  I think there is a way around this using pam, but I can't rememeber how.  I did it on my wife's computer a long time ago, and now I can't remember how to do it for my computer.

If you are having this happen without using automatic login it is because your user password and your keyring password are different.  To fix this just change the keyring password to be the same as your user password using the method described on [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/).

---

### Post by DingusFett on 2012-07-11
A fix for this would be great as I have exactly the same problem, my computer is set to automatically login as I am the only one using this computer.

---

### Post by habana on 2012-07-22
I would also appreciate a fix for this. All was well until a couple of days ago when the dreaded keyring password entry box appeared (I also autologin). I did make some changes to Empathy around the same time and have since unchecked the "automatically connect on startup" box in Empathy - it made no difference. 

How can I find out which application(s) wants to unlock the keyring?

---


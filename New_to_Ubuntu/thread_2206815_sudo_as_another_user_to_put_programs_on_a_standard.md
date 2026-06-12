---
title: "sudo as another user to put programs on a standard account"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by amber4 on 2014-02-20
Hi all,
I know I keep posting, but I'm a n00b and have a lot of questions. :P I was wondering, is there a way to use a standard account and sudo through Terminal as the other user (the administrator account I have set up)? It would be useful, since I'd rather not have to install packages through the admin account and have them junking up my files, but I don't want the other users to be able to sudo in terminal, as they know even less about what they're doing than I do, and that's really saying something. :P

---

### Post by papibe on 2014-02-20
Hi amber4.

Take a look at this: [Give permission to other users to only to install applications]("http://askubuntu.com/questions/64889/give-permission-to-user-only-to-install-applications").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by deadflowr on 2014-02-20
You don't have to worry about installation files junking up any users folders.
They install within the system's folder structure and not the users folder structure.
They won't clutter up your stuff, in anyway.

But for fun, you can switch users in a terminal session by using su user.
(su by itself switches to the root account, but su with a username will switch to that users account)
su = swtich to root
su otheruser = switch to other user
It'll ask for the other user's password.
Just type exit to get back to the normal user(the user who started the terminal session)

---


---
title: "[SOLVED] installing without root"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-07-06
How do I install a package in another users account without root, without going into my account and giving them root permissions?
Ie I want to install a few packages for my wife but don`t want her to be able to interfere with the system (she just has to look at a machine or gadget and it breaks).
Thankyou

---

### Post by sdennie on 2008-07-06
I'm not quite sure what you mean.  If you login as yourself (with admin privileges), you can install whatever you want and it will be reflected across all user accounts.  If you need to install something from your wifes account and it's a hassle to login as your account, you can also do:

```

su *your_admin_user*

```

That will log you in as your admin user and you can do whatever you like form the command line.

---

### Post by ChameleonDave on 2008-07-06
> **vor said:**
> I'm not quite sure what you mean. ...

I believe he wants to create a user without sudo privileges.

Nothingspecial, after you have created an account for your wife, you can at any time tweak what privileges she has by running the program "users-admin".

It will allow you to change the privileges of the various users on your system.

---

### Post by sayakb on 2008-07-06
You can install anything from any user account by just providing the root's password. You can though add the apt-get application to the sudoers group that will not require password for installing packages. But that is **not recommended** to avoid system vulnerabilities.

---

### Post by nothingspecial on 2008-07-06
Let me try to explain better. If my wife is logged on and something happens and I need to fix it, can I do this from the terminal in her account, granting her account temporary root privaleges.
 See if she`s in the middle of something, logging back into my account will close what she`s doing, no?
I`m just trying to save myself some earache.

---

### Post by sdennie on 2008-07-06
> **nothingspecial said:**
> Let me try to explain better. If my wife is logged on and something happens and I need to fix it, can I do this from the terminal in her account, granting her account temporary root privaleges.
 See if she`s in the middle of something, logging back into my account will close what she`s doing, no?
I`m just trying to save myself some earache.

Yup, you can.  That's exactly what the "su" command will do.  It will allow you to login as your account and have full admin privs.  If your username is "foo", you can type:

```

su foo

```

It will ask you for your password and then you will have a terminal as your normal user.  You can sudo from there with no problems.  When you are done, just keep typing "exit" until the terminal closes.  ;)

---

### Post by sayakb on 2008-07-06
Alternatively, you can open up a terminal from your wife's account and type:
```
sudo bash
```
And you would have the # prompt. In that way, you stay in bash, as well as, you have root privileges.

---

### Post by sdennie on 2008-07-06
> **LinuxIsInnovation said:**
> Alternatively, you can open up a terminal from your wife's account and type:
```
sudo bash
```
And you would have the # prompt. In that way, you stay in bash, as well as, you have root privileges.

That will only work if the wife account has admin privileges.  Users not in the admin group can't run sudo.  ;)

---

### Post by ChameleonDave on 2008-07-06
> **LinuxIsInnovation said:**
> Alternatively, you can open up a terminal from your wife's account and type:
```
sudo bash
```
No, that is bad advice.   He doesn't want to give his wife's account sudo privileges, so that will not work!


> **nothingspecial said:**
> Let me try to explain better. If my wife is logged on and something happens and I need to fix it, can I do this from the terminal in her account, granting her account temporary root privaleges.
 See if she`s in the middle of something, logging back into my account will close what she`s doing, no?
I`m just trying to save myself some earache.

If you need to do admin stuff from inside your wife's account, open and terminal and type "su" followed by your account name.  Do not just put "su" by itself, because it will try to make you become root, and since root has no password on Ubuntu, it will fail.

Once you are logged into the terminal as yourself, you can then run any admin commands by prefixing them with "sudo" in the ordinary fashion.

There you go: the ability to run admin commands whilst your wife is logged into the graphical desktop, and you don't need to make her a sudoer.

Instead of opening a terminal program, you can also go to the tty terminal which is always lurking behind the scenes.  Hit Ctrl + Alt + F1 or F2 to switch to one.  Log in as yourself, then use "sudo" for admin stuff.  To get back to the graphical desktop, hit Ctrl + Alt + F7.

P.S: Vor above had the right idea.

P.P.S: Here's an example:

```

su *nothingspecial*   *# or whatever your username is*
sudo apt-get install *nameofsomecoolsoftware*

```

or

```

su *nothingspecial*   *# or whatever your username is*
gksudo synaptic     *# and then you go and install stuff in Synaptic*

```

---

### Post by sdennie on 2008-07-06
@ChameleonDave: I got your post via e-mail before you edited it.  ;)

---

### Post by ChameleonDave on 2008-07-06
> **vor said:**
> @ChameleonDave: I got your post via e-mail before you edited it.  ;)
You sneak!  Haha.  I should remember that some people read this by e-mail instead of on here.

I edited it immediately after re-reading the thread.  You have to reply quickly on here or someone else leaps in ahead of you!  Sometimes that means you rush things.

---

### Post by nothingspecial on 2008-07-06
I get it now thanks guys!

---


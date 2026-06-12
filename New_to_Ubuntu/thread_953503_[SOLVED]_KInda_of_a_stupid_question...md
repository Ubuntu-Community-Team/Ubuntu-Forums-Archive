---
title: "[SOLVED] KInda of a stupid question.."
date: 2008-10-20
forum: New to Ubuntu
---

### Post by hovtzi on 2008-10-20
Hey, I'm really new in this Linux stuff.

I know that in order to do several action I have to be logged as the ROOT user.
How do I do it?

While installing the Ubuntu I was never prompt to enter a ROOT user or password,. Only my name and password.

I would appreciate any help,:confused:

---

### Post by halitech on 2008-10-20
Ubuntu doesnt use Root the same way most distros do, it uses Sudo so if you need to do admin work, simply add sudo to the beginning of the command and type your password to get it done

ie```
sudo apt-get install pidgin
```

---

### Post by OldTimeTech on 2008-10-20
Root user is only used in the terminal, for when you load specific commands...ie:

marianne@RebelWoman:~$ sudo apt-get install (something)

IF you open terminal you will see that your name and what ever your computer is named with show up...looking similar to above.  Then after you type sudo and your command it will ask you for a password...that is the password you use to get on the machine.

If this answers your question, mark the question solved at the top under thread.

Thank you

---

### Post by Brain-free on 2008-10-20
The password and username you're entering merely give you the right to use your home folder and read the filesystem. However, if an action needs read/write access to your filesystem, you must give your root password. That password is usually the same password you log in with.

Also, if you need to execute programs as super user, the way to do it is to type in terminal : 

```
sudo <action>
```
and give your password when prompt. The reason for this is to always be aware when a command changes something in your filesystem. If you were super user by default, there would be an open door for viruses, as it happens with Windows.

---


---
title: "Ubuntu 18.0.4 Trying to RDP in as root fails after one second"
date: 2018-11-27
forum: New to Ubuntu
---

### Post by samersultan1 on 2018-11-27
I'm able to RDP into Ubuntu using a standard user account. However when I try to RDP (using Windows 10) with the system root account it closes after one second. 

How do I go about trouble shooting this further?

---

### Post by QIII on 2018-11-27
Hello!

I am going to say this very emphatically (but someone may come along to help):

DON'T DO THAT!  

You shouldn't need to log in as root at all, and you certainly should not do it remotely.  You place your machine, your data, your important files and your identity at exceptional risk by doing things like that.  Ubuntu comes with a disabled root user (by virtue of root not having a password) for a very good reason:  security.  Having an active root account, and using it to make remote connections, is a fantastically effective way to be sure you get pwned.

Carry on if you wish.  But down that road lie significant emotional events.

---

### Post by samersultan1 on 2018-11-27
Hi QIII, 

I do understand the risks involved. This is for a local "test" server that I am trying to deploy xampp /  nginx on for local testing only. 

When using RDP from a normal account, nautilus won't allow me to open a folder "as administrator" (the password prompt does not show up, and it hangs indefinitely). Having to make many changes in the "etc\nginix" folder this has become a pain because I have to do everything from VMware console as opposed to RDP (to avoid the bug of not being able to open any locked folders).


I figured I would RDP in as root for testing / learning purposes and then once I figure things out I will use it as non root.

---

### Post by QIII on 2018-11-27
It would be best to do it right from the start, even in your home.  You should not start by developing bad habits.

1.  A server should not have a GUI.  That opens a lot of services as attack surfaces.  A server should provide the barest minimum of services required for it's intended purpose.

2.  Use SSH and the command line.

3.  Don't allow root logins over SSH.

4.  Log in with an account in sudoers and elevate your privileges with sudo.

I don't want to sound pedantic, but nobody in the real world does things as you intend to go about them.  If you want to learn to run an internet facing server like a web server, learn it right from jump.  Then you don't have to unlearn/relearn.

I know you would like an answer to your technical question, but this is one of those few cases where a bad idea is just a bad idea -- and a solution might be a disservice to you.

---

### Post by CatKiller on 2018-11-27
> **samersultan1 said:**
> I figured I would RDP in as root for testing / learning purposes and then once I figure things out I will use it as non root.

You aren't going to learn anything useful by logging in remotely as root, other than (eventually) that it's a really bad idea to do that.

When you have your webserver set up it (hopefully) won't be running as root, and it also (hopefully) won't be running as the user you log in as for administration, either. It's also unlikely to be running any kind of graphical interface.

Familiarising yourself with security and user accounts, and learning to do things entirely through the terminal, however, *are* useful skills.

---


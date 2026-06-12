---
title: "[SOLVED] Setting different Desktop Environment"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by rlogan on 2008-08-23
Hi all

I am wondering if there is an application that allows different users on one pc to have a different desktop environment as default with changing session type on the login screen.

Any help or thoughts would be great

Cheers

Richard:confused:

---

### Post by Patb on 2008-08-24
Richard, I have a standard Gnome Ubuntu install but also installed Fluxbox window manager and set that as my default. Any new users I create are set up with a standard Gnome desktop.  But in the startup GDM login, I can change their default session to Fluxbox or, presumably, any other acceptable desktop environment I have installed.  So it is just a matter of having the alternative session manager installed. 

Hope this helps. Cheers, Pat.

---

### Post by tenzen on 2008-08-24
> **Patb said:**
> Richard, I have a standard Gnome Ubuntu install but also installed Fluxbox window manager and set that as my default. Any new users I create are set up with a standard Gnome desktop.  But in the startup GDM login, I can change their default session to Fluxbox or, presumably, any other acceptable desktop environment I have installed.  So it is just a matter of having the alternative session manager installed. 

Hope this helps. Cheers, Pat.

This is exactly it.   By default, the last environment used is the environment upon logon.

To install other desktop environments, you simply need to use the right command..

eg.  sudo apt-get install kubuntu-desktop

enjoy

---

### Post by rlogan on 2008-08-24
Hi all

Thanks for your thoughts ?

I have gnome installed and kde4.1 and can use the session manager/selection to select which desktop I want when I login. 

What I am trying to do is avoid selecting each desktop variety on each login and make each user have a different desktop by default. So that when a user logs in that has a preference for kde is just logs in that way. Likewise a user that likes Gnome gets gnome when they login on the same computer.

I had a look at Admin>Login Window and changed the default desktop there but it did not seem to change it.

Any other thoughts

Richard

---

### Post by eightmillion on 2008-08-24
Users desktop environments should automatically default to whatever they last used. You shouldn't have to change anything.

---

### Post by rlogan on 2008-08-24
Thats right they do default to the last enviro logged into. But I want to set say my login to KDE4.1 and then my wife wants hers on say Gnome without having to change it at each login. It just automatically logs into my login with kde and my wifes with Gnome.

Any thoughts

Cheers in advance

Richard

---

### Post by eightmillion on 2008-08-24
It will do that. It remembers the previous login of the user that is logging in, not the previously logged in user. For example: say you log in to kde 4.1 and log out. Your wife then logs in to gnome and logs out. You input your credentials into the log in screen and it will remember that you logged into kde 4.1 last and load that unless you select otherwise.

---

### Post by rlogan on 2008-08-24
Cheers I didn't release it worked like that.... will check it out !!!!

---

### Post by rlogan on 2008-08-24
Cheers it is as you say and working just right !!!!!

Thanks heaps

Richard

---


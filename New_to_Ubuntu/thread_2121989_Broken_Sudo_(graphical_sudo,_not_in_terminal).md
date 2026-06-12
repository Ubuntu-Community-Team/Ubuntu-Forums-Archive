---
title: "Broken Sudo (graphical sudo, not in terminal)"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by Snowingheart on 2013-03-03
Hello, 

I have an issue whenever I use any program that requires root authorization. For instance, trying to install software via Ubuntu Software Center yields a black "pop-up" prompting for root credentials; after I input them and hit enter, it lags a little and just displays the message: "Sorry, that did not work. Please try again." 

Of course my password is correct, otherwise I would not be asking here.

I've read somewhere that there's a gk-sudo and it is useful to circumvent this issue, whenever I know the name of the program I want to use, but I'd rather have the "usual" sudo working and be done with it.

And yeah, usual sudo (as in within terminal) works just fine. It's just the one in the graphical environment that's broken.

Running Ubuntu 12.10 (quantal) 64-bit
Kernel Linux 3.5.0-22 generic 
Gnome 3.6.0 (installed via gnome-shell with apt-get)

Any help is appreciated.

---

### Post by Sin@Sin-Sacrifice on 2013-03-03
gksudo should already be installed by default. Try hitting alt-F2 or opening a terminal and typing "gksudo your-command" of course replacing your-command with the command you are actually trying to run.

Edit: I put gtksudo rather than gksudo

---

### Post by Snowingheart on 2013-03-03
Hi, and thanks for the reply.

I had read about that, but the thing I'm looking for is fixing the existing sudo pop-up message. That is, I do not want to use gtksudo <command>, but instead want to fix the screen that pops up asking for my root password.

---

### Post by bab1 on 2013-03-03
> **Snowingheart said:**
> ... I do not want to use gtksudo <command>, but instead want to fix the screen that pops up asking for my root password.
Ubuntu by default ***never asks for a root password***.  Rather it, asks for *your* password to verify that you are a allowed to used sudo for root privileges.  This would be for sudo, gksudo and gksu.  Are you trying to use the wrong password?  Do you have a password for the root account?  Have you altered sudo or changed your password?

---

### Post by Snowingheart on 2013-03-03
Bad choice of words, my pardons.

What I meant is that the graphic environment sometimes has to ask for "Administrator authorization" or something like that to run things like installations, disk operations, mounting a specific drive and stuff like that.

That said, in the past it prompted for the "admin" password, which is my user's password, since it is in the admin group, and it let me do whatever the task it was.
Now, that does not work, even though the password is the correct one.

As for the part of enabling a root account, I did, in the past, but disabled it afterwards. I do not know if that might be the issue, since I don't know which of sudo, gksudo or gksu is asking for authorization. And I can't take a screenshot, since it "locks" the screen when asking for that.

---

### Post by presence1960 on 2013-03-03
For GUI applications you should issue the gksudo instead of the sudo. Read [this]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Snowingheart on 2013-03-03
I think that gksudo is used to run an application as root, right?

That's not what I want. I just want to enable some feature of an application that needs admin rights to work.

Here's the screen I'm talking about: [https://www.dropbox.com/sh/9ml26w8lrzp41fv/cgK2FL9Uue?m#f:Screenshot%20from%202013-03-03%2021%3A37%3A03.png](https://www.dropbox.com/sh/9ml26w8lrzp41fv/cgK2FL9Uue?m#f:Screenshot%20from%202013-03-03%2021%3A37%3A03.png)

And the error message: [https://www.dropbox.com/lightbox/home/Photos/screenshots?select=Screenshot%20from%202013-03-03%2021%3A43%3A35.png](https://www.dropbox.com/lightbox/home/Photos/screenshots?select=Screenshot%20from%202013-03-03%2021%3A43%3A35.png)

---

### Post by bab1 on 2013-03-03
> **Snowingheart said:**
> I think that gksudo is used to run an application as root, right?

That's not what I want. I just want to enable some feature of an application that needs admin rights to work.

Here's the screen I'm talking about: [https://www.dropbox.com/sh/9ml26w8lrzp41fv/cgK2FL9Uue?m#f:Screenshot%20from%202013-03-03%2021%3A37%3A03.png](https://www.dropbox.com/sh/9ml26w8lrzp41fv/cgK2FL9Uue?m#f:Screenshot%20from%202013-03-03%2021%3A37%3A03.png)

And the error message: [https://www.dropbox.com/lightbox/home/Photos/screenshots?select=Screenshot%20from%202013-03-03%2021%3A43%3A35.png](https://www.dropbox.com/lightbox/home/Photos/screenshots?select=Screenshot%20from%202013-03-03%2021%3A43%3A35.png)

Sudo, gksudo and gksu all use the same routines (e.g sudo)  This is what the "pop-up" is asking for: sudo authentication.  There is no *admin rights  * other than the sudoers group as such.  Did you create a user named *administrator*?

---

### Post by Snowingheart on 2013-03-03
Yeah.. I think I have figured it out. I did enable a root account; that is, the actual user "root" has an entry in passwd. I seem to recall I "disabled" that account just by running passwd and setting an empty password for that user. I'm not quite sure where I read that, but that's what I did. 

SO, I think the issue is that the "pop-up" is asking for the actual root user password, and not my-user sudo password...

Thus, I ran passwd again and set a dummy password, re-tested and it works. Thing is, I read that it's not a wise thing to have an actual root user enabled in Ubuntu (for some sort of safety reasons). That said, how could I go about deleting/disabling the existing root account and still being able to authenticate via the "pop-up" window?

---

### Post by arpanaut on 2013-03-04
You would need to lock the root account again not just remove the password.
Take a look at this link and re-lock the root account and the issue "should" correct itself.
[http://www.ubuntugeek.com/enable-and-disable-ubuntu-root-password.html](http://www.ubuntugeek.com/enable-and-disable-ubuntu-root-password.html)

This is a very old instruction, but I don't think anything has changed since.
HTH

---

### Post by bab1 on 2013-03-04
> **Snowingheart said:**
> Yeah.. I think I have figured it out. I did enable a root account; that is, the actual user "root" has an entry in passwd. I seem to recall I "disabled" that account just by running passwd and setting an empty password for that user. I'm not quite sure where I read that, but that's what I did. 
This is NOT the way to do disable the root account.  Read about how to do that [**_[COLOR="#0000CD"]here[/COLOR]_**]("http://askubuntu.com/questions/20450/disable-root-account-in-ubuntu"). > 

SO, I think the issue is that the "pop-up" is asking for the actual root user password, and not my-user sudo password.
The pop-up is always in response to the user that called the routine.  If the user was *john * then the pop-up is for that user.  If that user has sudo rights and types in their password the the routine (install) will run with root user permissions.  If you *_are the user [COLOR="#FF0000"]root[/COLOR]_*,  you don't need sudo so no pop-up would be called.  You can not make a user root.  That user is part of the system.
> 

Thus, I ran passwd again and set a dummy password, re-tested and it works. Thing is, I read that it's not a wise thing to have an actual root user enabled in Ubuntu (for some sort of safety reasons). To protect you from yourself.  ;-) > 

That said, how could I go about deleting/disabling the existing root account and still being able to authenticate via the "pop-up" window?
Do as I said above to disable root password.  Then make sure your account can use sudo.  If you can't use sudo see the info [**_[COLOR="#0000CD"]here[/COLOR]_**]("http://www.psychocats.net/ubuntu/fixsudo") for a solution.

---

### Post by Snowingheart on 2013-03-04
I did as @arpanaut[COLOR=#000000] said and disabled the root account with:

passwd -l root

Which, in turn, put me back in square one (the "pop-up" would not authorize me with my password).

Then, I did as @bab1 said, and:

> [/COLOR][COLOR=#000000]Then make sure your account can use sudo. If you can't use sudo see the info [/COLOR][**_[COLOR=#0000CD]here[/COLOR]_**]("http://www.psychocats.net/ubuntu/fixsudo")[COLOR=#000000] for a solution.[/COLOR][COLOR=#000000][/COLOR] 

Added my user to sudo group. This changed the "pop-up" from what it was to display my user icon and user name; then, after entering my password, things worked as they should. 

Thank you both for that. This issue is solved :D

---

### Post by Snowingheart on 2013-03-04
Ummm... How do I mark this as SOLVED ?

---

### Post by bab1 on 2013-03-04
Thread tools at the top right...

---

### Post by Snowingheart on 2013-03-04
That menu only shows 3 options: to get a printable version of the thread, email it or subscribe to it...

---

### Post by bab1 on 2013-03-04
The answer is; it's broken.  See [**_[COLOR="#0000CD"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2121377&p=12538923") for info.

---

### Post by Snowingheart on 2013-03-04
Thanks again bab1! :D

---


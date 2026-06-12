---
title: "GUI for user accounts properties: where?!"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cpbl on 2011-09-28
Firstly, what on earth is the command line name for the gui that edits user accounts?

Secondly, how can I modify all the details? It used to be that if I clicked on a user, I'd get the option for details: group memberships, etc, and even setting uid.

I cannot see how even to change groups, which is kind of important, because that's how you change someone's administration privileges and some peripherals privileges...

thanks!

---

### Post by RomeReactor on 2011-09-28
Hi. Is users-admin what you're looking for?
```
users-admin
```

---

### Post by haqking on 2011-09-28
[s]you mean what do you type at CLI to launch the GUI user accounts manager as oppose to clicking on it in your menu ?

```
users-admin
```

 and do you have admin privelege and unlocking with the use of sudo ?[/s]

Edit: just realised this is oneiric, my bad, my apologies

---

### Post by cariboo on 2011-09-28
If you are going to answer questions in this sub-forum, you should at least be using Oneiric, users-admin no longer works, unless gnome-system-tools is installed, which it isn't by default. 

To set user properties, click the power button in the top right corner, and select System Settings->User Accounts. BTW the user accounts applet, is really basic, it really only allows you to create another user account, as a normal user, or and administrative user.

---

### Post by cpbl on 2011-09-28
Hm. I can get users-admin by installing gnome-system-tools.
That is not installed by default in 11.10.
Yes, it looks like the one I wanted. Thanks. 
But:
I could not find this in the software centre with sensible search terms. (user, user admin, ...)
And I don't see any GUI path from the Desktop to the software centre in Gnome 3, either.

Are these things any more idiot proof than they seem to this idiot?

---

### Post by cariboo on 2011-09-28
The Software Center icon is in the Unity launcher by default, so if you removed it, the only way to open it is by clicking the BFB in the launcher to open the dash, then type **so** and click the icon.

---

### Post by cpbl on 2011-09-28
Okay, but this limitation was my original complaint.  What is one meant to do to administrate users, then? Is this functionality regression the plan for the RC?

---

### Post by cariboo on 2011-09-28
> **cpbl said:**
> Okay, but this limitation was my original complaint.  What is one meant to do to administrate users, then? Is this functionality regression the plan for the RC?

Gnome has been reducing configuration options for the last couple years, it's their feeling that they know what's best for us. :(

---

### Post by seeker5528 on 2011-09-30
> **cpbl said:**
> Okay, but this limitation was my original complaint.  What is one meant to do to administrate users, then? Is this functionality regression the plan for the RC?

Personally I always preferred kuser for this anyway, but if the users and groups are already created, I'm more likely to use ```
sudo -H vim /etc/group
``` to manage which users belong to what groups.

Later, Seeker

---


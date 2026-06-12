---
title: "[SOLVED] Consequences of &amp;quot;sudo su&amp;quot;?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by JillSwift on 2008-07-05
For the first time in my career with Linux I have a box where I'm concerned with more than my account and root.

I have a lil server that has a Samba shared directory for openly (no password) sharing office document templates &c. I made a no-particular-privileges account to act as the user account for this open share.

I wanted to add an automated download of some off-site information into this public share, and whipped up a simple shell script to handle it - it fetches the info into a new folder on the share. Problem is, I set up the cron job as my admin account, so the folders are being made by that account and the Samba user account can't read them.

Easy enough fix, but I need to log into the Samba user account to for its crontab. It has no password and I don't want it to have one even breifly.

So...

is it safe to "sudo su <account>"?

I'm hoping so as this would aslo let me more easily do a little automated file cleaning.

Better ways also appreciated >.>; Thanks for reading =^_^=

---

### Post by miwaypet on 2008-07-05
Yes. Sudo su is just super user access for that point of access. Remember to exit out before quitting. Why don't you create a simple root file manager. Open add to panel. Give it the nam: File Manager. Command: gksudo nautilus. Give it an icon (gnome foot is cool). Instant access to your file system as root including samba shares. Good lick.

---

### Post by aysiu on 2008-07-05
You really should use ```
sudo -i
``` instead. *sudo su* gives you root privileges but uses the user environment. *sudo -i* gives you root privileges and uses root's environment.

---

### Post by sayakb on 2008-07-05
You could also use:
```
sudo bash
```That way, you are superuser, and you're also within bash.
You may also try a Nautilus Script called [**Rootilus**]("http://www.gnome-look.org/content/show.php/Browse+Nautilus+as+root?content=69816"). That would allow you to start Nautilus as superuser from any folder via the GUI menu selections.

EDIT: The script is badly rated on the site, but does comes in handy a couple of times ;)

---

### Post by jw5801 on 2008-07-05
> **JillSwift said:**
> For the first time in my career with Linux I have a box where I'm concerned with more than my account and root.

I have a lil server that has a Samba shared directory for openly (no password) sharing office document templates &c. I made a no-particular-privileges account to act as the user account for this open share.

I wanted to add an automated download of some off-site information into this public share, and whipped up a simple shell script to handle it - it fetches the info into a new folder on the share. Problem is, I set up the cron job as my admin account, so the folders are being made by that account and the Samba user account can't read them.

Easy enough fix, but I need to log into the Samba user account to for its crontab. It has no password and I don't want it to have one even breifly.

So...

is it safe to "sudo su <account>"?

I'm hoping so as this would aslo let me more easily do a little automated file cleaning.

Better ways also appreciated >.>; Thanks for reading =^_^=

'sudo su' will log you in to root (in your users environment, as Aysiu describes). If you simply want to switch to the dummy samba account you've created, then you don't need the 'sudo' just 'su <account>'.

---

### Post by JillSwift on 2008-07-05
> **jw5801 said:**
> 'sudo su' will log you in to root (in your users environment, as Aysiu describes). If you simply want to switch to the dummy samba account you've created, then you don't need the 'sudo' just 'su <account>'.it asks me for a password, though. And as the account doesn't have one... no loggie innie. Am I doin' it wrong?

---

### Post by JillSwift on 2008-07-05
Thanks for all the info (I learned something! Yay!)!

But, I'm confused. What I need to do is get my Samba dummy user account to run a few scripts, since the scripts create new directories and files in the samba share, which the Samba dummy user can not read if my admin account makes them thus preventing the Samba users on the network from reading them.

So I want to avoid making any files owned by root or my admin account.

[SIZE=1][COLOR=Gray]Though it only just now occurs to me I could probably just chmod g+r the directories 'n' files  >.>[/COLOR][/SIZE];

---

### Post by jw5801 on 2008-07-05
> **JillSwift said:**
> Thanks for all the info (I learned something! Yay!)!

But, I'm confused. What I need to do is get my Samba dummy user account to run a few scripts, since the scripts create new directories and files in the samba share, which the Samba dummy user can not read if my admin account makes them thus preventing the Samba users on the network from reading them.

So I want to avoid making any files owned by root or my admin account.

[SIZE=1][COLOR=Gray]Though it only just now occurs to me I could probably just chmod g+r the directories 'n' files  >.>[/COLOR][/SIZE];

Yes, chmod is your friend :P

You don't really want to dummy user to be able to create executable scripts do you? You can create the script and have it owned by you or root and then chmod it to give the dummy user permission to run it.

---

### Post by jw5801 on 2008-07-05
> **JillSwift said:**
> it asks me for a password, though. And as the account doesn't have one... no loggie innie. Am I doin' it wrong?

If the user has no password then you shouldn't be asked for a password. But 'sudo su -l <account>' will log you in properly to their account through the all powerful root.

---

### Post by JillSwift on 2008-07-05
> **jw5801 said:**
> Yes, chmod is your friend :P

You don't really want to dummy user to be able to create executable scripts do you? You can create the script and have it owned by you or root and then chmod it to give the dummy user permission to run it.Yep, I think that's best. Plus I just now discovered you can 'sudo crontab -u <account> -e' so I don't need 'sudo su' or anything like that at all.

Oi. I am always posting before thinking. Thanks for the help folks! =^_^=

---

### Post by jw5801 on 2008-07-05
> **JillSwift said:**
> Yep, I think that's best. Plus I just now discovered you can 'sudo chrontab -u <account> -e' so I don't need 'sudo su' or anything like that at all.

Oi. I am always posting before thinking. Thanks for the help folks! =^_^=

Haha, no problems. And I see you are correct about 'su' asking for a password to switch to a non-passworded account. Very odd indeed. You could always switch to a tty and log in as the user. Or 'sudo su -l <account>' will get you into the account properly through the all powerful root. It's odd that it still asks for a password though. I wonder what password it expects?

---


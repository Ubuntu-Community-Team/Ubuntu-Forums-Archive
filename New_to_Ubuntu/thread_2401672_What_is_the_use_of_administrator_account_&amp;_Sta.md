---
title: "What is the use of administrator account &amp; Standar account?"
date: 2018-09-20
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2018-09-20
Hello all,

Recently I came to aware of using administrator account for usual purpose is not recommended.

So I made my other account as (administrator account) and made my main  account as (Standard Account) which is created at the time of Ubuntu  Install.

And the New administrator is completely new and I can't do anything with it.(Even accessing files and other applications too)

After changing the administrator account as standard, it only asks for password whenever I try to access the hard disk?

What are the key differences here?, how ubuntu will protect my files as administrator & Standard?

will that cause any harm? 

How can I move other account which is currently (Administrator account. I  created after) to main account? Is that possible to do so?

Mainly is that possible to access particular application and files from a standard user to admin user?

Hope you understand my query, sorry for my bad english.

---

### Post by deadflowr on 2018-09-20
An administrator account can make changes to the system. Including creating, editing, moving and removing files. As well as create and remove users. And installing or removing software.

A standard account cannot. All a standard user can do is create edit move and remove their own files in their own Home folder (and any other specific location granted by an administrator account, but by default only file in Home). They cannot remove users or install or remove software.

Protection level for your files is the same, regardless of the account setting.
> How can I move other account which is currently (Administrator account. I created after) to main account? Is that possible to do so?
I'm not sure I'm following, but you must have at least one administrator account.

---

### Post by The Cog on 2018-09-21
The first account you create (the username you gave to the installer) is automatically an "administrator" account - it is allowed to use the **sudo** command to perform restricted administration type actions such as adding other users, installing system software. The actual user name is not significant.

The reason for recommending that you normally use a non-administrator account for your day-to-day work is that in that case, even if something compromises your account (opening an infected document for instance) it cannot easily infect the entire system.

---

### Post by mastablasta on 2018-09-21
> **jegan2 said:**
> 
So I made my other account as (administrator account) and made my main  account as (Standard Account) which is created at the time of Ubuntu  Install.

And the New administrator is completely new and I can't do anything with it.(Even accessing files and other applications too)



so you want your user account you created first to become a normal user and the account you named administrator to become a super user that can sudo?

have a look at this: [https://help.ubuntu.com/lts/serverguide/user-management.html.en](https://help.ubuntu.com/lts/serverguide/user-management.html.en)

or here: [https://websiteforstudents.com/one-manage-groups-ubuntu/](https://websiteforstudents.com/one-manage-groups-ubuntu/)

or here for a GUI: [https://askubuntu.com/questions/66718/how-to-manage-users-and-groups](https://askubuntu.com/questions/66718/how-to-manage-users-and-groups)

also i strongly suggest you do not name your administrator account "administrator " or "admin" or "ubuntu" or "ubnt". name it "theboss", "billy" or "hans". security though obscurity :)

but automated bots do attempt to hack password using the usual account names. once they see they have the right username all they need is a password.

---

### Post by sporksrule on 2018-09-21
As mentioned above, your original account has Super User privileges (sudo), the new account does not. Each user has their own 'home' folder, therefore, you will not be able to access documents from your original admin account with your new account. If you want to follow the proposed advice of using a non-admin account as your default account, then you should sign into the admin account and copy the files your need to access from the home folder of your admin account to the home folder of your non-admin account using 'sudo cp [files] [destination]' or sudo 'sudo cp -R [directory] [destination]'. 

If a program was installed globally you should be able to access it as any user.

---

### Post by oldrocker99 on 2018-09-21
Incidentally, Windows has always made the user the administrator, which is exactly why, along with it being closed-source, it is the malware magnet that we know and hate.

You might advise your unenlightened friends who don't/won't use Linux to create a separate user account for everyday Windows usage, and keep a separate administrator account for installing software. 

That can at least help in stanching the flow of nasty bits to the system. 

Also: How in the name of all that is holy can people even **STAND** to use Windows 10](*,)? (Rhetorical question)

---

### Post by SeijiSensei on 2018-09-21
> **The Cog said:**
> The reason for recommending that you normally use a non-administrator account for your day-to-day work is that in that case, even if something compromises your account (opening an infected document for instance) it cannot easily infect the entire system.
I think the much more important reason to avoid running as root is so you can't bork your system.  Running a command to change permissions in the wrong place, accidentally deleting some libraries, etc., etc., can all turn a perfectly fine system into one needing a re-installation of Linux to fix.

I've never opened a document in Linux that threatened the integrity of my system.  Have you?

---

### Post by pauljw on 2018-09-22
> **SeijiSensei said:**
> I think the much more important reason to avoid running as root is so you can't bork your system.  Running a command to change permissions in the wrong place, accidentally deleting some libraries, etc., etc., can all turn a perfectly fine system into one needing a re-installation of Linux to fix.

I've never opened a document in Linux that threatened the integrity of my system.  Have you?

Excellent points!  And, no, I've never opened any file that threatened my linux system, but I sure have borked more than my share of installs misusing my powers as root.  Now that I've grown accustomed to the ways of linux, it's been years since I've had to reinstall. :)

---

### Post by The Cog on 2018-09-26
> **SeijiSensei said:**
> I think the much more important reason to avoid running as root is so you can't bork your system.  Running a command to change permissions in the wrong place, accidentally deleting some libraries, etc., etc., can all turn a perfectly fine system into one needing a re-installation of Linux to fix.

I agree, but that's not an answer people asking that question want to hear: "Are you calling me an idiot?" I think that to Windows users, preventing malicious intrusions is a much more acceptable answer.

---


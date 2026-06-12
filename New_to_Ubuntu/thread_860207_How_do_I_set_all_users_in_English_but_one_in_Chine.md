---
title: "How do I set all users in English but one in Chinese?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by sarc on 2008-07-15
I have Hardy Heron and can change the language options, but all users change together!  I want the default to be in English and one (unprivileged) user to be in Chinese-TW.  I cannot find a way to change the language setting at login (I tried the Sessions menu).  Ideally I would like to have the Chinese user with Chinese as default anyway.  Is there a HOWTO on this?  Could not find one searching the forum...

---

### Post by Inxsible on 2008-07-15
you might have to login as that user and install the locale specific language packs in that user's home directory. This would be a one time thing.

But I don't think that will change the language in GDM - you might just have to teach that user to enter their username and password in the blank box.

Let me see if I can find some tutorials on how to install language packs in the home directory.

---

### Post by Het Irv on 2008-07-15
Brainstorm:

If there was a way to change the language though the command line you could set that up in the Sessions menu.

I have no idea if that is possible though....

---

### Post by sarc on 2008-07-15
Thanks guys.
Yes I had to install the language packs from the root user as my Chinese user was unprivileged.
Then I switched user to the Chinese login and tried to select Chinese as the default language, but could no do it from there.  The system asked for a root password, which I entered, but was refused.  I tried all passwords from all users still no luck.  Then I tried to make the user Administrator privileged and was successful in loading the Chinese desktop.  But all combinations I tried would change the desktop for all other users as well.

---

### Post by Inxsible on 2008-07-15
> **sarc said:**
> Thanks guys.
Yes I had to install the language packs from the root user as my Chinese user was unprivileged.
Then I switched user to the Chinese login and tried to select Chinese as the default language, but could no do it from there.  The system asked for a root password, which I entered, but was refused.  I tried all passwords from all users still no luck.  Then I tried to make the user Administrator privileged and was successful in loading the Chinese desktop.  But all combinations I tried would change the desktop for all other users as well.If you installed the chinese pack under root it would be available to all users....

As I mentioned earlier...you have to install it under the "users' home directory"

I havent found any tutorials yet...still searching.....

---

### Post by Inxsible on 2008-07-15
Try one of the two links here. It says something about using locale_gen. The second link is the man page....By default it stores the generated locale under /usr/lib/locale.

But maybe you can change the locale_gen script and have it stored under the home directory for the user which will over-ride the default English. I am not sure if it will work though.



[http://ubuntuforums.org/showthread.php?t=214099&page=2](http://ubuntuforums.org/showthread.php?t=214099&page=2)

[http://www.digipedia.pl/man/locale.gen.5.html](http://www.digipedia.pl/man/locale.gen.5.html)

EDIT: You also need to look at the localedef command --  [http://www.digipedia.pl/man/localedef.1.html](http://www.digipedia.pl/man/localedef.1.html)

This allows for changing the location of the **I18NPATH**- which you can set for that user within the home directory.

Yet another thing that can be done is to use the setlocale  command - 
[http://www.digipedia.pl/man/setlocale.3.html](http://www.digipedia.pl/man/setlocale.3.html)
and have the bash_profile run a script which calls this setlocale command and sets everything to chinese when that particular user logs in.

Hope that helps !!

---

### Post by Het Irv on 2008-07-15
Because the user that you want to set as Chinese is restriced, they do not have root access.  You may have bump that user's permissions up a level.

---

### Post by Inxsible on 2008-07-15
> **Het Irv said:**
> Because the user that you want to set as Chinese is restriced, they do not have root access.  You may have bump that user's permissions up a level.Having a bash script that changes the locale (locale file stored in the user's home directory) might be a better way to go - depending on whether the OP is comfortable giving root privs to that user.

---

### Post by drs305 on 2008-07-15
Once you have installed the language packs as root, the user should be able to log-in with a specific language as follows:

Select "Options" in the lower left corner of the login screen (where the user enter's his/her username). Then select "Language". As long as the language is installed on the machine I believe the user will be logged on with the selected language as the default (for their session).

---

### Post by sarc on 2008-07-15
Thanks it works!  I did not know that the language selection at login was in the options menu... DUH

6 replies in 30 minutes that's pretty amazing!  Thanks!

---

### Post by Het Irv on 2008-07-15
> **drs305 said:**
> Once you have installed the language packs as root, the user should be able to log-in with a specific language as follows:

Select "Options" in the lower left corner of the login screen (where the user enter's his/her username). Then select "Language". As long as the language is installed on the machine I believe the user will be logged on with the selected language as the default (for their session).


Wow, I completely forgot about that.... show how much the bean count is worth...:lolflag:

---


---
title: "Getting into the terminal while on live dvd"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by Dieselrider 1 on 2012-12-06
Hi, First time posting and first time trying out ubuntu. I am on the live DVD right now and wondering if there is a way to get into the terminal without installing? Thank you.:popcorn:

---

### Post by monkeybrain2012 on 2012-12-06
> **Dieselrider 1 said:**
> Hi, First time posting and first time trying out ubuntu. I am on the live DVD right now and wondering if there is a way to get into the terminal without installing? Thank you.:popcorn:

Yeah, choose try Ubuntu and then you will get into the desktop where you can bring up the terminal either from the menu (dash) or type ctr+alt+t

---

### Post by audiomick on 2012-12-06
Yep. Are you on 12.10, or at least on a version with the Unity desktop? Open the dash and search for "terminal" in the search box. To open the dash, click on the top most icon in the panel on the left, or hit the button that Microsoft likes to call the Windows button.

---

### Post by Dieselrider 1 on 2012-12-06
Hey thank you very much. Now what would be the root password for Ubuntu while running on live DVD? Most distros make you sign in as a guest when first booting and you also see the root password then. I guess I never realized that Ubuntu just loaded up without that part (or I slept through it:confused:).

---

### Post by snowpine on 2012-12-06
> **Dieselrider 1 said:**
> Hey thank you very much. Now what would be the root password for Ubuntu while running on live DVD? Most distros make you sign in as a guest when first booting and you also see the root password then. I guess I never realized that Ubuntu just loaded up without that part (or I slept through it:confused:).

There is no "root password" in Ubuntu. Rather, use 'sudo' in front of the command as illustrated here: [http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by Dieselrider 1 on 2012-12-06
Thank you snowpine. I was just over reading about that and coming back here to say so when I saw your reply. Sorry.

---

### Post by Dieselrider 1 on 2012-12-06
okay, I am having a bit of trouble using the cd command. I am opening the terminal and then trying to navigate to a directory on another drive. If I scroll over the drive I see /media/ubuntu/maxtor (the name of the drive) but, if I type in cd/media/ubuntu/maxtor, I get a no such file or directory message. What am I doing wrong? 

I'll have to try this some more tomorrow. I'm beat. Thanks to you all though.):P

---

### Post by snowpine on 2012-12-06
You're missing a space character:

```
cd /media/ubuntu/maxtor
```

---


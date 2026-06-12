---
title: "[SOLVED] cant get restricted drivers"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by daberger on 2008-11-26
hi i tried enabling restricted drivers in a new installation of 8.10 and it didnt download. sudo apt-get install also doesnt find any packages to install even tho i know they exist. internet works fine for browsing the web so im not sure what the problem is here

---

### Post by NewJack on 2008-11-26
What are you trying to do?  Your question is a little vague.  Why do you need the restricted drivers?

When posting here in the forums, the more information you give, the better people can help.

---

### Post by Paqman on 2008-11-26
Ubuntu-restricted-extras is in the multiverse repo. Go to System > Admin > Software sources and make sure Multiverse is checked. Then reload the repos and you should be able to get it.

---

### Post by daberger on 2008-11-26
my bad i was in a rush

i need to enable the restricted drivers for NVidia 8600m gt so i can get compiz working

my package manager doesnt seem to be working even tho the internet works fine
so i flaw in the lsp (or the ubuntu equivalent?)

i need to get the restricted driver

---

### Post by NewJack on 2008-11-26
Go to where paqman told you go for your Sources and while you are there make sure that the option for "CD" is unchecked.  If that is still checked it could screw you up with getting updates.  

Happened to me with Edgy.  Didn't realize "CD" was checked off and I would never get any updates (until I figured it out).  No matter how good your internet connection is, you won't get squat.

---

### Post by daberger on 2008-11-26
there is no multiverese to select

---

### Post by Ryadt on 2008-11-26
> **daberger said:**
> there is no multiverese to select
Can you post the output of ```
cat /etc/apt/sources.list
```

---

### Post by GepettoBR on 2008-11-26
Open System>Administration>Software Sources

On the first tab, make sure that "Software restricted by copyright or legal issues (multiverse)" is selected, and "Cdrom with Ubuntu 8.10 'Intrepid Ibex'" is not.

Click Close. If a message pops up, agree to rescan the repositories.

If an update notification pops up, install the updates.

Then, try installing the Hardware Drivers again.

I have the same video board and it works great, so don't worry.

---

### Post by NewJack on 2008-11-26
> **GepettoBR said:**
> Open System>Administration>Software Sources

On the first tab, make sure that "Software restricted by copyright or legal issues (multiverse)" is selected, and "Cdrom with Ubuntu 8.10 'Intrepid Ibex'" is not.

Click Close. If a message pops up, agree to rescan the repositories.

If an update notification pops up, install the updates.

Then, try installing the Hardware Drivers again.

I have the same video board and it works great, so don't worry.

^^^What he said (Sorry, I am at work and don't have Ubuntu IFO me at the moment).

Good Luck!

---

### Post by daberger on 2008-11-26
aight i did that

---

### Post by NewJack on 2008-11-26
And....???

---

### Post by GepettoBR on 2008-11-26
> **daberger said:**
> aight i did that

If it worked, please mark this thread as "Solved" from the thread tools to help other people who might have the same problem find it :)

If it didn't, tell us what happened and we'll try to help you further.

---

### Post by daberger on 2008-11-26
desktop effects are a breeze however im having mouse/bluetooth problems so ill post another

---


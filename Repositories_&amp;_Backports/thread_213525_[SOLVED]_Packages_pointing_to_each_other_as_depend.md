---
title: "[SOLVED] Packages pointing to each other as dependencies"
date: 2006-07-11
forum: Repositories &amp; Backports
---

### Post by shinkaide on 2006-07-11
Good lord. I don't mind downloading dependencies from anywhere at all and installing them one by one, but this is driving me nuts.

[COLOR="Red"]**kdelibs-bin**[/COLOR] and **[COLOR="Red"]kdelibs4c2a[/COLOR]** point to each other as dependencies and refuse to be installed unless the other is.

Btw, I've just installed 6.06 and I've downloaded and installed most of the packages (And their dependencies) listed [here]("https://help.ubuntu.com/community/RestrictedFormats"). I just need help with the aforementioned packages.

Thanks.

[IMG]http://www.evergreensd.com/stuff/depscr.jpg[/IMG]

---

### Post by Paerez on 2006-07-11
try using aptitude:
```
# sudo aptitude install dkelibs4c2a kdelibs-bin
```

---

### Post by shinkaide on 2006-07-11
Hello, I've tried to do as you have suggested but I get the following error messages:

[I]E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
[/I]
Could this possibly be because at one time I enabled the traditional root account and then disabled it? (Just speculating).

---

### Post by shinkaide on 2006-07-11
Pardon that, I've worked around it. :)

---

### Post by Paerez on 2006-07-11
the lock is because you probably had synaptic open. But you probably figured that out.

---

### Post by shinkaide on 2006-07-12
Just wanted to add if there are some new users out there (like me!) who've experienced a similar problems, you should just use the aptitude command that Paerez suggested above on a terminal to get and install your package.

Saved me a lot of time, since aptitude also got the dependencies in one go. If you want to do it the graphical way, use the Synaptic Package Manager. 

I've already learned a ton of new stuff in just 2 days of running ubuntu. Cheers!

---

### Post by Paerez on 2006-07-12
yeah I like synaptic's interface for searching and reading about packages, but aptitude really knows how to handle dependencies well. It is also better at fixing broken packages, I think.

---

### Post by asimon on 2006-07-12
Just for your information: this circular-dependency problem was already fixed for Edgy, the kdelibs-bin package was completely merged into kdelibs4c2a and is no more.

---

### Post by Paerez on 2006-07-12
cool beans.

Hey where is the info for running edgy? I have tried to search for it all over the place. I was hoping to run it inside vmware just to test the waters, but all I found were random forums posts where people guessed the repo. names. Is there a more official page?

---

### Post by shinkaide on 2006-07-13
> **asimon said:**
> Just for your information: this circular-dependency problem was already fixed for Edgy, the kdelibs-bin package was completely merged into kdelibs4c2a and is no more.

Wow, that was fast. I guess I'll just have to wait for the next release...

---


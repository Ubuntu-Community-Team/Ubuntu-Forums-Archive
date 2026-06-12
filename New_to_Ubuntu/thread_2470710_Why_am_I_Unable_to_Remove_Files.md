---
title: "Why am I Unable to Remove Files?"
date: 2022-01-08
forum: New to Ubuntu
---

### Post by jesus-pieces on 2022-01-08
Ubuntu 20.0.4

I installed ClamAV and then uninstalled it, but there are some files left on the system, which are configuration files, that are owned by root. I have tried the <rm> with/without <sudo>, which resulted in this: cannot remove 'clamconf': No such file or directory. I can see them in /usr/bin. How do I remove these files?

---

### Post by deadflowr on 2022-01-08
Post all commands run and output from those commands.

---

### Post by tea for one on 2022-01-08
Also, indicate that you have navigated to the directory where the files reside.

---

### Post by KBar on 2022-01-08
It looks like you're talking about [this](https://packages.ubuntu.com/search?suite=focal-updates&arch=any&searchon=contents&keywords=clamconf) file, which is installed by the *clamav-daemon* package. Try issuing the following command to get rid of it:```
sudo apt purge clamav-daemon
```

---

### Post by jesus-pieces on 2022-01-08
so, I [cd] to /usr/bin, and [sudo] [rm] three files -- the power ... I have the power! Then, I had a problem with the last file, and it turned out that I had missplelled the file name. Uhm, this is New to Ubuntu, right? Thanks for your patience.

---

### Post by tea for one on 2022-01-08
Yes, you are correct - This is [COLOR="#FF8C00"]New to Ubuntu[/COLOR]
Many users have inexhaustible patience.

If your question has been answered satisfactorily, then it is helpful for other forum users/searchers to mark the thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by rsteinmetz70112 on 2022-01-08
Pretty much all of us have been there before. Usually earlier today.

---

### Post by TheFu on 2022-01-08
> **jesus-pieces said:**
> so, I [cd] to /usr/bin, and [sudo] [rm] three files -- the power ... I have the power! Then, I had a problem with the last file, and it turned out that I had missplelled the file name. Uhm, this is New to Ubuntu, right? Thanks for your patience.

To prevent misspellings, use tab-completion.  You'll never misspell a directory or program or file again - the system won't let you.  If you don't know what tab-completion is ... search and learn it.  If you type more than 2-3 characters, you are doing it the hard way.

---


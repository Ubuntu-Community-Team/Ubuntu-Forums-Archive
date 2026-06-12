---
title: "[SOLVED] What is this &amp;quot;Lists Directory&amp;quot; and why is it missing?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by mj0lnir on 2008-12-01
Running Ubunut 8.04 with an eeepc kernel. Everything has been running great and I am loving it. But in the past few weeks, sometimes an orange triangle pops up on my menu bar, asking me to update. The problem is, even if I try to update, I can't. It tells me to open the updater and then click on "check." If I do that, it tells me:

Cannot download all repository indexes

then goes on and lists some info about this possibly being due to a network connection problem. I've gone into the website that supports the eeepc kernel, and I've tried using other servers for the first-party updates, and it still doesn't solve the problem. Also, under the first error message, there's a box, and inside it it says:

Lists directory /var/lib/apt/lists/partial is missing

So, what on earth is this directory, how did it go missing, and how do I get it back? :)

---

### Post by oldos2er on 2008-12-01
You can recreate it:

 cd /var/lib/apt/lists

 sudo mkdir partial

---

### Post by handydan918 on 2008-12-01
> **oldos2er said:**
> You can recreate it:

 cd /var/lib/apt/lists

 sudo mkdir partial

Or, the single command approach ```
sudo mkdir /var/lib/apt/lists/partial
```

But maybe you aren't as lazy as I am...


:)

---

### Post by mj0lnir on 2008-12-02
So that's it? I just need to create the directory? That sounds too easy, but I'll try it when I get home. :)

---

### Post by oldos2er on 2008-12-02
I don't know if you'll have other errors, but creating the "partial" directory should cure "Lists directory /var/lib/apt/lists/partial is missing".

---

### Post by mj0lnir on 2008-12-02
Yep, that solved the missing directory problem. Then an error occurred:

> W: Failed to fetch [http://www.array.org/ubuntu/dists/hardy/Release.gpg](http://www.array.org/ubuntu/dists/hardy/Release.gpg) Could not resolve 'www.array.org'

W: Failed to fetch [http://www.array.org/ubuntu/dists/hardy/eeepc/i18n/Translation-en_US.bz2](http://www.array.org/ubuntu/dists/hardy/eeepc/i18n/Translation-en_US.bz2) Could not resolve 'www.array.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.

Then I tried 'sudo apt-get update' in the terminal and got the same error messages, followed by a helpful suggestion that I may want to run 'apt-get update' to correct these problems. At least I got a good laugh out of this. :lolflag:

---

### Post by oldos2er on 2008-12-02
You can go directly to [www.array.org](www.array.org) (using Firefox or any web browser), and download packages from there. Does eeepc come with a program called gdebi?

---

### Post by mj0lnir on 2008-12-02
Yeah, I'm beginning to think there's some issue with array.org or something. The orange warning triangle has gone away now though. Yes, I have gdebi installed.

---

### Post by oldos2er on 2008-12-02
Then if you run gdebi, and point it to any *deb files downloaded from [www.array.org](www.array.org), it should install them for you--unless it needs to download dependencies from the same site. Maybe the site's down for maintenance.

---

### Post by mj0lnir on 2008-12-02
> **oldos2er said:**
> Then if you run gdebi, and point it to any *deb files downloaded from [www.array.org](www.array.org), it should install them for you--unless it needs to download dependencies from the same site. Maybe the site's down for maintenance.

Ok, if the orange warning triangle rears its ugly head again, I'll try that. Thanks to everyone for the help!

---


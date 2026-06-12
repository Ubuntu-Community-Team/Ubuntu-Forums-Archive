---
title: "Can't connect to Repository"
date: 2012-05-29
forum: Programming Talk
---

### Post by ColinMcQueen on 2012-05-29
Hi, this is my first time signing up on any forums related to Linux or computer in general. 

I am running Ubuntu in Virtual Box and this VM has a repository I created. I have one package in it and I need another VM to get that package. I need the VM that gets the package to install it and then update it whenever.

Going to the /etc/apt/sources.list I added
deb [http://10.31.31.89/shift/](http://10.31.31.89/shift/) ./ and when I do a sudo apt-get update I receive these errors:

```
Err http://10.31.31.89 ./ InRelease
Err http://10.31.31.89 ./ Release.gpg
Unable to connect to 10.31.31.89:http:
```

The directory structure for the repository is
shift
  binary

I was able to get this working on the repository VM but the point is to get this working on the other VM.

---

### Post by Cheesehead on 2012-05-29
Is the repo VM reachable by other means like ssh?
Is the repo server listeninig for a network connection?
Are any firewalls configured to block access?

---

### Post by ColinMcQueen on 2012-05-29
> **Cheesehead said:**
> Is the repo VM reachable by other means like ssh?
Is the repo server listeninig for a network connection?
Are any firewalls configured to block access?

I figured it out it was because I did not have a web server to use http. Once I installed that, I don't have those errors any more.

---


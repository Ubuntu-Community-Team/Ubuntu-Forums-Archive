---
title: "After installing Mate desktop I am getting this error...."
date: 2017-02-23
forum: New to Ubuntu
---

### Post by Joe_Martin on 2017-02-23
The repository 'http://ppa.launchpad.net/ubuntu-mate-dev/xenial-mate/ubuntu yakkety Release' does not have a Release file.

Any advice on how to correct this issue?

Thanks.

---

### Post by howefield on 2017-02-23
> **Joe_Martin said:**
> Any advice on how to correct this issue?

Yes, delete the file pointing to that non existent repository.

From a GUI use the Software Sources application and remove the relevant repository from the "*Other Software*" tab. Close out and you'll be prompted to update your sources, accept it.

Or using the terminal..

```
sudo rm /etc/apt/sources.list.d/name_of_file
```

substitute name_of_file with the actual file name.

---

### Post by Joe_Martin on 2017-02-23
if I remove the repo for Mate, how will I receive updates?

---

### Post by howefield on 2017-02-23
You won't.

But given a yakkety repository for that source doesn't exist you can't have installed anything from it, so there is nothing to update :)

Might help to know which release you are on and why you installed the repository in the first place ?

```
cat /etc/*-release
```

---

### Post by Joe_Martin on 2017-02-23
I appreciate your help but I am fully aware of what release I am running.  My follow up question was, how do I receive Mate updates automatically?

---

### Post by howefield on 2017-02-23
> **Joe_Martin said:**
> I appreciate your help but I am fully aware of what release I am running.

Of course you do, that'll be why you added a yakkety repository. I wasn't asking for your benefit but rather for others.

> My follow up question was, how do I receive Mate updates automatically?

With the level of detail that you provide, I'm unable to continue.

Good luck in resolving, I'm out.

---


---
title: "Automating the installation script"
date: 2010-10-18
forum: Programming Talk
---

### Post by vksingh on 2010-10-18
Hi,

I have written a shell script to install some set of packages when I do a fresh installation of my ubuntu.

like..

apt-get install vim
apt-get install ssh
...
...

But the problem I am facing is that, after every start of installation of a package in the script, it wails for me to authenticate.

[I]Need to get 1,464kB of archives.
After this operation, 6,935kB of additional disk space will be used.
Do you want to continue [Y/n]? y
[/I]

I want some some so that all the packages are installed without asking for authentication if I start the script with *root* privileges.

Thanks,

Vivek

---

### Post by asp314 on 2010-10-19
> **vksingh said:**
> Hi,

I have written a shell script to install some set of packages when I do a fresh installation of my ubuntu.

like..

apt-get install vim
apt-get install ssh
...
...

But the problem I am facing is that, after every start of installation of a package in the script, it wails for me to authenticate.

[I]Need to get 1,464kB of archives.
After this operation, 6,935kB of additional disk space will be used.
Do you want to continue [Y/n]? y
[/I]

I want some some so that all the packages are installed without asking for authentication if I start the script with *root* privileges.

Thanks,

Vivek

It's been a while since I've used Ubuntu, but I believe you can string together all the packages in one command such as

```
apt-get install vim ssh etc
```

From the apt-get man page:

> 
-y
--yes
--assume-yes
    Automatic yes to prompts; assume "yes" as answer to all prompts and run non-interactively. If an undesirable situation, such as changing a held package or removing an essential package occurs then apt-get will abort. Configuration Item: APT::Get::Assume-Yes.


Thus you should be able to accomplish what you want by running

```
apt-get -y install vim ssh etc
```

Always remember, **man** is your friend.

---

### Post by juancarlospaco on 2010-10-19
--force-yes 
will force instead of abort.

---


---
title: "Software sources: some security concerns"
date: 2017-02-05
forum: New to Ubuntu
---

### Post by martemarziano on 2017-02-05
Hi,
I have got several sources in my sources.list with the following remark:

> ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

The same remark is being stated about software from multiverse and backports. So I was a bit alarmed by the statement that software from these sources will not get any "review or updates from the Ubuntu security team". Apart from Chrome and Opera, I have only installed software from Ubuntu software center or Appgrid. Should I be worried?

---

### Post by yancek on 2017-02-05
The Ubuntu developers don't have anything to do with the creation and maintenance of such software (Opera, Chrome) and have no control over it.  So the questions is, do you trust the people who develop/write whatever software you are downloading from outside sources.

---

### Post by martemarziano on 2017-02-05
I understand that. What I want to know is how secure are softwares from universe, multiverse and backports. If I am not mistaken, all these sources are chosen by default in the software updater. I don't even know what software might be pre-installed from these sources on my system.

It maybe that I haven't understood what sources like "universe", "multiverse" and"backports" actually refer to.
:confused:

I have found these two links:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

I guess I have to do some reading.

---

### Post by howefield on 2017-02-06
> **martemarziano said:**
> I don't even know what software might be pre-installed from these sources on my system.

Using the terminal and..

```
awk '$1 == "Package:" { if (a[$2]++ == 0) print $2; }' /var/lib/apt/lists/*restricted*Packages
```

will tell you what packages you have installed from a particular repository. Change "restricted" to main or whatever other repository you want to check.

I'm sure that the Software Centre will also show you installed packages from any particular repository but I can't check that not having the Software Centre installed.

---

### Post by martemarziano on 2017-02-08
> **howefield said:**
> 
I'm sure that the Software Centre will also show you installed packages from any particular repository

You are absolutely right. I was a bit alarmed by the statement that software from certain sources which are, by the way, listed in the Software Updater, 
[COLOR=#000000][I]> "WILL NOT receive any review or updates from the Ubuntu security team"
[/I][/COLOR]so I forgot about the obvious. Sorry about that. One can also find detailed descriptions of all the packages installed in Synaptic as well.

---


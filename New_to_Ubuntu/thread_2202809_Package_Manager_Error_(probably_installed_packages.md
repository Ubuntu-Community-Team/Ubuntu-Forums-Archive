---
title: "Package Manager Error (probably installed packages have unmet dependencies)"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by nikolides on 2014-01-31
Hi,

I can no longer use the Package Manager on Ubuntu 12:04 LTS and am receiving the following serious error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/kh.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

Any help on what to do would be gratefully received.

---

### Post by fantab on 2014-01-31
We have to repopulate the 'lists' sometimes:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
```

---

### Post by henryf61 on 2014-02-03
Hi,

I thought your reply might help my problem, which I believe started with a download of SKYPE, followed by unmet dependencies. Subsequently, I have been plagued with update manager errors. I tried typing your 3 lines of code into a terminal, After the 3rd line i got the following error message:

E:Malformed line 53 in source list /etc/apt/sources.list (dist parse)
E: the list of sources could not be read.

If it helps any, the following is the error message when I try to open the update manager:

Update manager

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 53 in source list /etc/apt/sources.list (dist parse)'


I have no idea how to report this bug or take any other action.

Any help will be greatly appreciated.

TIA,
Henryf61

---

### Post by Bashing-om on 2014-02-03
@ henryf61; Hi !

Your problem is of a different nature that that of the Original Poster's.
Please start your thread on this issue; and as your problem is related to your sources.list file, please post the output of:
```

cat -n /etc/apt/sources.list

```
Forum protocol -> one problem to each thread.

And we will address your issue.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by nikolides on 2014-02-05
Perfect. All fixed.

Many thanks Fantab.

---


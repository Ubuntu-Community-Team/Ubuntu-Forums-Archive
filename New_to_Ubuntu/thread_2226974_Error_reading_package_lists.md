---
title: "Error reading package lists"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by rmallett on 2014-05-29
Hello,

I am a casual user of Ubuntu, and I have run into an issue while trying to load Skype onto 14.04.

I now cannot even open Software Centre (it simply will not open). 

When I run sudo apt-get update, many things are fetched. Then I get the output: 

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

It says the same thing when I enter sudo apt-get upgrade.

I'm stumped as to how to fix this. Any help would be appreciated. 

Thank you

Rob

---

### Post by Bashing-om on 2014-05-29
rmallett; Hi !

Let's suppose from the error condition that the control file is corrupt. 
Remove it, generate a new one(s), sync up the data base and finally update all the installed packages that the package manager is tracking:
terminal commands:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```


Please to advise on results

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by rmallett on 2014-05-29
This worked. Thank you very much.

---

### Post by Bashing-om on 2014-05-30
rmallett, Great !

Pleased it worked out.
Please mark this thread solved; aides others seeking the solution,
helps keep the forum clean and 
precludes others miss-directing efforts to aid.

thread tools @ top of post

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---


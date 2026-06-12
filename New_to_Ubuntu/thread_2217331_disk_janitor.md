---
title: "disk janitor"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by newblank25 on 2014-04-16
in ubuntu 13.04 I believe i used unity tweak program for the disk janitor function to clean out old kernals & packages. I have that but the icon for disk janitor is there. Can someone help me to install that function to unity tweak tool. a big thx.

---

### Post by gifford on 2014-04-16
The program is Ubuntu Tweak. Unity tweak does not have that capability.

---

### Post by mörgæs on 2014-04-17
Just run **sudo apt-get autoremove** to get rid of old packages and kernels.

---

### Post by monkeybrain20122 on 2014-04-17
Use bleachbit, it is in the repo. Computer-jaintor or whatever it is called is kind of danagerous from what I have read.

---

### Post by mcduck on 2014-04-17
> **monkeybrain20122 said:**
> Use bleachbit, it is in the repo. Computer-jaintor or whatever it is called is kind of danagerous from what I have read.

Only in the exact same way Bleachbit is, as it offers the option to delete files the user might not actally want removed without explaining what the files are for.

Anyway, I agree with mörgæs here, *sudo apt-get autoremove* cleans old kernel versions in recent Ubuntu versions and never removes anything the user might still actually need. (and doesn't require installing any extra software)

---

### Post by monkeybrain20122 on 2014-04-17
> **mcduck said:**
> Only in the exact same way Bleachbit is, as it offers the option to delete files the user might not actally want removed without explaining what the files are for.

Anyway, I agree with mörgæs here, *sudo apt-get autoremove* cleans old kernel versions in recent Ubuntu versions and never removes anything the user might still actually need. (and doesn't require installing any extra software)

Well the user of course has to decide what to delete. The software cannot (and should not) make that kind of decisions for you.

Sudo apt-get clean only cleans the cache, apt-get autoremove only cleans autoremovables, and you need other commands to remove unnecessary localizations etc and none of these would clean your /home (Firefox and chrome caches etc)

Of course you can do everything in the command line as bleachbit doesn't do things by magic. But there is the convenience of doing everything with one click once you have set it up and you can preview what you will delete before running so it is pretty safe.

I frankly don't understand this attitude: Having the ability to remember long and semantically nonsensical strings and being a fast typist I can do something by remembering and typing a bunch of commands one by one, therefore, a convenient, streamlined gui that enables inexperienced users with not so good typing skills or memory to do the same thing in one go is to be frowned upon. :)

For most things that I do with guis I can do with the cli, but unless there are some marked advantages for the task at hand to type (like writing scripts to automate something) I very much prefer the gui way since it is intuitive and convenient.

---


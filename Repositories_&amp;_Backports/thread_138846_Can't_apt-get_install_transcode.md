---
title: "Can't apt-get install transcode"
date: 2006-03-02
forum: Repositories &amp; Backports
---

### Post by Alanius on 2006-03-02
I'm running hoary and this is what it the console tells me when I enter apt-get install transcode:
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  transcode: Depends: libgcc1 (>= 1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed
E: Broken packages
```
What's the problem?

Thanks in advance for helping a newbie.

---

### Post by Xian on 2006-03-02
The problem is that the package Transcode is not in the Hoary repos. It is in Breezy, but to install that build you need another file not available in Hoary, which is libgcc1-1:4.0.1-4. Basically, you are working outside of your Ubuntu versioned environment and this is creating dependency and candidate errors.

---

### Post by eriefisher on 2006-03-03
I'm having the same problem with Breezy 5.10 when trying to apt-get install DVD::RIP. The error say that Transcode is the dependency but can't be installed. I then try to apt-get install Transcode alone and I'm told there is lib dependency(I forget which one now) but is not installable. The lib shows up on the Debian site but have not pursued it further yet.


eriefisher

---

### Post by Xian on 2006-03-03
[QUOTE=eriefisher]IThe error say that Transcode is the dependency but can't be installed. [/QUOTE]

It could be looking for a different version than is in the repo. When you get a chance post some of the terminal output of that install session. I assume of course that you are not mixing repos, and that all the entries in your source list refer strictly to Breezy.

---

### Post by eriefisher on 2006-03-03
I'm away from the box right now but when I get a chance I'll post the info. My source.list should be ok but that was my next check. Thanks

eriefisher

---

### Post by akiro.yamamoto on 2006-03-03
Try adding the PLF repo as well.

---


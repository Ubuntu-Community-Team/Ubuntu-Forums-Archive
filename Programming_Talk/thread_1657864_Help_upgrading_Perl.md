---
title: "Help upgrading Perl"
date: 2011-01-01
forum: Programming Talk
---

### Post by dpitch40 on 2011-01-01
I am new to Perl but am trying to do some basic programming in it. For starters I want to upgrade to the latest version, as apparently Ubuntu 10.10 doesn't come with it. I absolutely cannot figure out how to do this. I download the latest source code and followed the readme instructions for installing it, but it didn't work; I still have version 5.10.1. I can't figure out how to remove my current version or install a new one. I can't believe it's so hard to upgrade perl. Am I missing something incredibly obvious?

---

### Post by dpitch40 on 2011-01-01
Okay, I appear to be able to get it to work by changing my path so the path to the new version comes first. But the old version is still there. Is this necessary?

---

### Post by Vox754 on 2011-01-01
> **dpitch40 said:**
> I am new to Perl but am trying to do some basic programming in it. For starters I want to upgrade to the latest version, as apparently Ubuntu 10.10 doesn't come with it. I absolutely cannot figure out how to do this. I download the latest source code and followed the readme instructions for installing it, but it didn't work; I still have version 5.10.1. I can't figure out how to remove my current version or install a new one. I can't believe it's so hard to upgrade perl. Am I missing something incredibly obvious?

Why would you want to upgrade Perl in the first place? You are a beginner, right? That doesn't make sense.

Perl is a very sensitive part of a Linux operating system, many things may depend on it, so downloading the source code, compiling it, and installing a new version is not trivial nor recommended.

You may install pre-compiled versions that are already pre-packaged, and ready to be used, such as those offered by ActiveState, which provide ActivePython, ActivePerl, ActiveTcl, etc. You can install those by essentially extracting the contents to any directory, setting the proper PATH variable, and using the appropriate executable.

However, you should not try to do this if you are a beginner, and more important, there is really no need, because the current version is more than enough, and more modules are already available in the current repositories.

Also, which version do you want to install? Perl 6? With Perl 5.10 is more than enough. Small version numbers, such as 5.10.1.1313, 5.10.2.123, etc. don't mean big changes to the language, usually just bug fixes.

---

### Post by Vox754 on 2011-01-01
> **dpitch40 said:**
> Okay, I appear to be able to get it to work by changing my path so the path to the new version comes first. But the old version is still there. Is this necessary?

It is a common misconception from people coming from Windows that they want the latest software.

This is not the way Ubuntu works. The entire system is set on using a particular version of Perl, so if you upgrade this component you may be disrupting packages that depend on the distribution-provided Perl.

There have been cases before of people upgrading Python from the current 2.6 version to the new 3.0 version. Of course, later they realize many things exhibit a strange behavior, and other things just don't work.

Upgrading for the sake of upgrading is not a valid reason. It is very possible to have several versions of a given programming language installed side-by-side on the same computer. There is no clash if the user knows what he is doing, and knows how to call each one for a particular purpose. Think about compatibility, a given programmer may want to have several major versions of Perl in order to test and maintain a given application that was developed some time ago.

---


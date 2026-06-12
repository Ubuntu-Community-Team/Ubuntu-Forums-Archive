---
title: "Trouble Compiling Abiword from Source"
date: 2010-01-07
forum: Packaging and Compiling Programs
---

### Post by beastrace91 on 2010-01-07
So I downloaded the Abiword source from [here](http://www.abisource.com/downloads/abiword/2.8.1/source/). But it fails to compile for me, when it dies it gives the following error message:

```
ut_go_file.cpp:1640: warning: 'char* check_program(const char*)' defined but not used
```

Also a screen shot of terminal with the full dump/output:

[IMG]http://i45.tinypic.com/2ahulfp.jpg[/IMG]

Suggestions on what is wrong? At first I thought it was an issue with the source code but I get the same failure/message with all three different Abiword sources I have tried to compile. Also I Googled around for the issue and found [this old thread](http://www.abisource.com/mailinglists/abiword-user/2009/Jul/0008.html) on the Abiword mailing list, but it did not really have a solution present in it...

Open To suggestions,
~Jeff

---

### Post by Queue29 on 2010-01-08
Does the output of  ./configure say everything is good to go? Obviously you are missing a library, libgsf-gio  would be a first guess according to that mailing list.

---


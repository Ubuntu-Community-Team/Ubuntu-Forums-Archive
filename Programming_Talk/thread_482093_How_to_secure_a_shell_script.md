---
title: "How to secure a shell script"
date: 2007-06-23
forum: Programming Talk
---

### Post by Cappy on 2007-06-23
I made a shell script here:[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
called getlibs that solves binary dependencies by calling ldd <filename> on the binary.
However, some people are using the script on shell scripts and loki installers (.run).

Basically, I need a way to get the dependencies that this shell script is erroring out on
I could do:
```
sh /supplied/path/to/file &> $variable_that_intercepts_error
```
but I'm afraid someone could use that to run their own custom code as root (as an exploit). Any idea on how to prevent this? Is there is someway to run that as the user and not as root, even if the script itself is run with root?

Also, if there is another way to figure out the dependencies other than capturing an error I would like to know.

Thank you!

---

### Post by Cappy on 2007-06-24
bump

---

### Post by McNils on 2007-06-24
I think that you could use **su** when running sh as root. The problem is that you need to find a user that exist on the system. nobody seems to be a good candidate...

---

### Post by Mr. C. on 2007-06-24
Force your script to exit with a warning when running with UID=0.

Use **file** to ensure that you run only on supported types:

```
$ file /bin/ls
/bin/ls: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped

$ file myscript
/home/mrc/bin/myscript: Bourne-Again shell script text executable
```

A few quick comments about your script:

[LIST]
[*]Place your URLs or at least URL bases at the top of your script, and use variable below.  Don't liter your script with various [http://.](http://.).. URIs.

[*]Do likewise for your paths (/tmp/getlibs, etc.)

[*]Use getopts to process your arguments, rather than the simple, and your very inaccurate usage of $#.

[*]Create a usage function, which can be called rather than duplicating the usage error messages.

[*]Present a list and ask for confirmation before blindly copying a bunch of libraries to /usr/lib32; this is potentially dangerous :   sudo cp -R /tmp/getlibs/extracted/usr/lib/* /usr/lib32/

[*]The code that attempts to remove /tmp/getlibs, and then sudo's to remove them in the case of failure is redundant: just use the sudo call the first time, and remove them.  Exit with an error if they aren't removed after that.

[*]Use a case statement for your test of $download instead of if / endif, or at least and if/else.

[*]sort has a -u option.  Dispose of the pipe to uniq.

[*]No need to create the temporary file: liblist.tmp .  Use a pipeline.

[*]You can replace if [ "$packagename" = "" ]; with  if [ -z "$packagename" ];
[/LIST]

MrC

---

### Post by Cappy on 2007-06-24
Thank you for the tips! As you can probably tell from reading my code I've been learning as I go. Thanks again.

---

### Post by Mr. C. on 2007-06-24
You're welcome.

Here's some more stuff you might like.  Check out the notes and homework:

[http://cis68b1.mikecappella.com](http://cis68b1.mikecappella.com)

MrC

---


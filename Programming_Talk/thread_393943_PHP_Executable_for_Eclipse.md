---
title: "PHP Executable for Eclipse"
date: 2007-03-26
forum: Programming Talk
---

### Post by MR Bacardi on 2007-03-26
Hello
I am trying to Debug my PHP code with Eclipse (and PDT plugin).
I have just installed Apache and PHP5, and Eclipse wants the PHP Executable set in my Preferences, but I can't seem to find the file.

I do not know what the file is called, nor where to look.
Any help would be great.

---

### Post by Mirrorball on 2007-03-26
Type in a terminal:
```
whereis php
```

---

### Post by MR Bacardi on 2007-03-26
That narrowed my search, but I have now had Eclipse search the output:
/usr/bin/php
/usr/X11R6/bin/php
/usr/bin/X11/php
/usr/share/php
For PHP executables, but none were found...

---

### Post by Karma_Police on 2007-03-26
try:
```
which php
```

from the man:
> which returns the pathnames of the files which would be executed in the
       current environment, had its arguments been  given  as  commands  in  a
       strictly  POSIX-conformant  shell.   It does this by searching the PATH
       for executable files matching the names of the arguments.

It should probably be in "/usr/bin/php" . At least mine is.

---

### Post by Oen386 on 2007-03-28
Weird. I am having the same issue, but for another reason.  A program wants to find where the PHP executable is. I can't seem to find it.

I have done the suggested above, but "which php" returns nothing. "which php5" also returns nothing.

Any ideas?

---

### Post by Oen386 on 2007-03-28
Nevermind, I had to do a full reinstall of all the PHP5 files, now it shows up. Not sure why it wouldn't show up the first time (since I had PHP running on my webserver), but it's all good now.

---

### Post by MR Bacardi on 2007-03-29
My solution isn't perfect, but I found out that Eclipse PDT does not by default provide me with the Debug mode I was trying to use. I had to download a PHP debugging executable from Zend (found the link at PDT's project page).
 Debugging does not work as I thought, but now I am able to get syntax check as I want etc.

---

### Post by ahildoer on 2007-04-29
FYI...the php executable is part of the PHP Command Line Interface. On my distribution, it is part of the php5-cli package. So, if you do not have this package, do the following:

```
sudo aptitude update
sudo aptitude install php5-cli
```

If you have installed the package, and binary is still no where to be found, a reinstall can be done like this:

```
sudo aptitude update
sudo aptitude reinstall php5-cli
```

If you still can not find the binary, maybe you need to start from scratch and do this:

```
sudo aptitude update
sudo aptitude purge php5-cli
sudo aptitude install php5-cli
```

I hope this helps anyone having the same problem mentioned above. Also, this solution works for the Komodo IDE.

-Anthony

---

### Post by snowtown86 on 2010-10-24
Seems nice after I install php5-cli

---


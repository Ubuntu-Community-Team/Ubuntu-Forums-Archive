---
title: "Error during installation of XML::Parser perl module (perl .MCPAN -e shell)"
date: 2005-08-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Hägran on 2005-08-06
[According to this thread](http://ubuntuforums.org/showthread.php?t=53769&highlight=error%3A+XML%3A%3AParser+perl+module+required+intltool): I have the same problem.

(I do not know what the policy is about "bumping" threads, so I simply post a new thread. Any moderator/administrator can easily remove this thread if I have done wrong by posting a new thread instead of bumping the old one).

My error message is:

```

cpan> XML::Parser
Can't locate object method "Parser" via package "XML" (perhaps you forgot to load "XML"?) at /usr/share/perl/5.8/CPAN.pm line 201, <FIN> line 1.

```

What shall I do? I know it's a very silly way to ask, but what to say? I have just installed Ubuntu.  :?

---

### Post by ctcecil on 2005-10-30
sudo apt-get install libxml-parser-perl

---

### Post by clarkth on 2006-04-30
Thanks, I was looking for this too as I install Alacarte.

---


---
title: "Problem with PEAR (PDO Install) on Ubuntu"
date: 2007-05-09
forum: Programming Talk
---

### Post by malibu on 2007-05-09
Has anyone run into this?  when I try to install PDO via 'pecl install pdo' I get the following:

Fatal error: Allowed memory size of 8388608 bytes exhausted (tried to allocate 114 bytes) in /usr/share/php/PEAR/Registry.php on line 1012
Allowed memory size of 8388608 bytes exhausted (tried to allocate 40 bytes)


PEAR is running out of memory for PHP, fine.  So I went to change my two php.ini files, restart apache2 (which shouldn't matter for this) and I still get the error.  I saw some advice to change a line within /usr/share/php/pearcmd.php but the memory_limit setting no longer exists within the script.  Then I did the following:

find / -name "*.php" -exec grep memory_limit {} /dev/null \; 

and I found nothing.  Same with grepping for '8M'.

So does anyone know what is causing this?  Apparently this only happens on Ubuntu (as per another post) but I cannot find a solution.  I even rebooted at one point after changing both php.ini files.  (apache2 and cli)  Well, the cli file was already at 16M.

---

### Post by Mirrorball on 2007-05-09
Not answering your question, but doesn't PHP >5.2 already have PDO?

---

### Post by malibu on 2007-05-09
So I've heard..  When I ran 'apt-get install php5' again on my server all I got was an updated php 5.1.

Is there a way for me to apt-get install PHP 5.2?  I had concluded that it was only in the leading edge version in Ubuntu, not the stable one.  It would be awesome if I could install the package for it.  That would probably solve my problems.

---

### Post by Mirrorball on 2007-05-10
Upgrade to Feisty? :D

---

### Post by malibu on 2007-05-10
Yeah, I was starting to think that would be easiest..

Currently I have 6.06 running on a VMWare box.. I was just going to install Fiesty on another one and move my stuff over.

Unless... Is there a way to 'upgrade' 6.06 to Feisty in place?

---

### Post by Mirrorball on 2007-05-10
Yes. I can't find the instructions, but I'm sure they exist.

---


---
title: "giving a php script more memory"
date: 2006-11-28
forum: Programming Talk
---

### Post by oldmanstan on 2006-11-28
ok, so i have this script that needs to have a really big string variable but every time it hits a certain amount of memory (i think it was 8 meg, it was a couple days ago that i ran it and it takes awhile so i dont wanna do it again, the number isn't really important i dont think) the script crashes.  this is being run from the CLI, not on a web server in case that matters.

basically, is there any way that i can allow php to give the script more memory? like say 32 meg or something?

thanks.

---

### Post by Joe_CoT on 2006-11-28
[http://us2.php.net/manual/en/ini.core.php#AEN262844](http://us2.php.net/manual/en/ini.core.php#AEN262844)
Change the directive in your php.ini

---

### Post by oldmanstan on 2006-11-28
woah! never knew that existed, how fun, thank you greatly!

---


---
title: "Password protecting zipped folder"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by keiths2 on 2014-05-21
Wanting to password protect a folder, I stumbled upon this:-
[http://www.upubuntu.com/2013/01/easily-password-protect-your.html](http://www.upubuntu.com/2013/01/easily-password-protect-your.html)
It seems ideal for what I want, and I managed to create, zip, and protect a test folder which I placed in my Documents folder, and I can open it, add to it, and delete part or whole of it.
Great!
Until I get to "More Advanced Options" paragraph near the end of the article.
Given that I've placed the protected folder in my own Documents folder, how do I navigate (cd)  to my own Documents Folder via the terminal where I need to type the given sudo command? I've tried every combination of /home and /documents and variations, but I keep getting told there's no such file or directory.
I'm obviously missing something very basic in the directory, folders, file structure
Please help

---

### Post by bapoumba on 2014-05-21
```
bapoumba@SonyBlue:~$ locate temp.png
/home/bapoumba/Desktop/temp.png
bapoumba@SonyBlue:~ cd ~/Desktop
bapoumba@SonyBlue:~/Desktop$ ls *.png
temp.png
```

For one, Linux is case sensitive, so your document folder should be ~/Documents, ~ stands for your home directory.
The idea is to locate your zip folder (I used the locate command with a temp.png file of mine), cd to that directory, ls the file to make sure it is there, then run your chattr command.

While you are in the terminal,
```
man locate
man ls
man chattr
```
and in particular the last one. Arrow down or up to navigate the man pages, "q" to exit.

---

### Post by keiths2 on 2014-05-21
[**[COLOR=#C61919][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=171805")bapoumba Wow! Many thanks, so much for the simple 'navigate to...' in the article :(
I got there eventually and all is well. If I wasn't so busy getting Ubuntu up and running in the first place, I'd have plenty of time to read the man files, but I'm feeling snowed under, there's so much of it.
Thank you

---

### Post by bapoumba on 2014-05-21
You are most welcome.

Could you please mark your thread as solved (under Thread Tools) thanks.
You can read the man pages in a web browser, I like [http://linux.die.net/man/](http://linux.die.net/man/) (I've never quite figured out their search engine, I just use the bottom alphabetical order when I know a command name). There are many other resources, including [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/). Best is to use your favorite search engine as I do :

> chattr manual page site:[http://linux.die.net](http://linux.die.net)
chattr manual page site:[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

That respectively gives :
[http://linux.die.net/man/1/chattr](http://linux.die.net/man/1/chattr)
[http://manpages.ubuntu.com/manpages/trusty/man1/chattr.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/chattr.1.html)

---


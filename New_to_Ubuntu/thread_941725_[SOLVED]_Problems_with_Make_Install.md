---
title: "[SOLVED] Problems with Make Install"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Vendettaseve on 2008-10-08
Hey everyone, Im attempting to install something with make install as is instructed to do on the programs site, however I get an error message every time -_-


vendettaseve@vendettaseve-Lair:~/rarcrack-0.2$ make
gcc -pthread rarcrack.c `xml2-config --libs --cflags` -O2 -o rarcrack
rarcrack.c: In function ‘crack_thread’:
rarcrack.c:206: warning: comparison between pointer and integer
vendettaseve@vendettaseve-Lair:~/rarcrack-0.2$ make install
install -s rarcrack /usr/bin
install: cannot create regular file `/usr/bin/rarcrack': Permission denied
make: *** [install] Error 1


Any advice/opinion?

Thanks

---

### Post by Titan8990 on 2008-10-08
Make install will not work properly until Make has worked.


You are in dangerous grounds here as your first post on this topic has been locked.


Edit: If anyone is curious about the OP's motive with rarcrack it can be found here: [http://ubuntuforums.org/showthread.php?t=941253](http://ubuntuforums.org/showthread.php?t=941253)

---

### Post by Vendettaseve on 2008-10-08
As was previously stated, the thread was locked due to lack of clarity in my original post. I am doing nothing illigal and thus have every right to use said software. 

Im trying to break a forgotten password on the RAR containing the files from my computer before I converted to Ubuntu.

I am not trying to start any fights with this and I have PMed the mod who locked my original thread and cleared things up.-_-

Anywho, Why is the make command not working? Any ideas?

---

### Post by Titan8990 on 2008-10-08
Well, I am not sure that it is failing but it is flagging a warning which could cause issues. Most of the time when programs fail the make process it due to a lack of libraries that are required to compile the program.


Let me give you a hint. Your user account can't create a file in /usr/bin but root can....

---

### Post by Vendettaseve on 2008-10-08
Iv been reading about Root on here, but I cant figure out how to get into it.. Im the only user on this comp and I know the password etc, but its not prompting me to input it like it does when I use sudo etc.

---

### Post by Titan8990 on 2008-10-08
Sudo runs a command as root using your user accounts password.



sudo make install

---

### Post by Vendettaseve on 2008-10-08
Wow, that was easy, thanks mate :D

---

### Post by Titan8990 on 2008-10-08
Anytime.

---


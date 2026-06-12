---
title: "CDPATH environmental variable???"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by emerson1979 on 2013-07-17
Hello Everyone
                      I'm reading a book on Ubuntu,"Ubuntu Unleashed". I just read a section on the "cd" command. In it I read the following piece, ....CDPATH environmental variable'. What does this mean, CDPATH and environmental variable.


Thanks

---

### Post by papibe on 2013-07-17
Hi emerson1979.

Environment variables are global variables that are available from every program in a particular session. A common used variable is USER. That holds the name of the current user. That way if you write a script or a program, you can know which user is running the program.

You can see what's in a variable by echoing its value. For instance:
```
echo $USER
```
To see all environment variables run this:
```
env
```
For more details on environment variables see this: [Ubuntu Help on Environment Variables]("https://help.ubuntu.com/community/EnvironmentVariables").

I wouldn't worry much about CDPATH. It enable kind of an advanced (and maybe confusing) feature. It is not used by Ubuntu, in other words, it is not set.

Does that help? Let us know how it goes.
Regards.

---

### Post by emerson1979 on 2013-07-17
Thanks a lot. Environmental variables are now understood

---


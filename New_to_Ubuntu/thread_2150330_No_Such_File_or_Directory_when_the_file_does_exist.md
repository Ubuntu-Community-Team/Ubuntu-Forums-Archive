---
title: "No Such File or Directory when the file does exist"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by Lieske on 2013-05-31
I'm trying to install cmake. [The cmake website]("http://www.cmake.org/cmake/help/install.html") suggests I follow these steps. 

```
   ./bootstrap
    make 
    make install 
```

I downloaded the .tar.gz file and uncompressed it. The contents are as follows:

[IMG]http://i.imgur.com/sdRlFCC.jpg[/IMG].

As you can see, I do have the bootstrap file. I do have the permissions to execute the file, according to:

```
ls -l bootstrap
```


What else could be going wrong?

---

### Post by CatKiller on 2013-05-31
The error message could be in relation to what the program's trying to do rather than your attempts to run it.

---

### Post by Cheesemill on 2013-05-31
You are probably missing the dependencies needed to compile cmake.

As I mentioned in your [other thread]("http://ubuntuforums.org/showthread.php?t=2150299") it's going to be almost impossible to install OpenCV without the proper permissions on the server.

What can be achieved in a couple of lines with the correct permissions is going to take you hours of compiling and downloading possibly hundreds of packages. Even if you could compile them all they would all be installed in non-standard locations as you don't have the permissions needed to install them in the default system locations.

You need to get your supervisor and server admin to sort this out between them, what you're being asked to do just isn't feasible at the moment.

---

### Post by kinglear333 on 2013-05-31
Edited:
It seems like the bootstrap file is in bash, whereas your error shows you're using zshell? That could definitely be a problem since those 2 shells are not the same.

Hope this helps.

---


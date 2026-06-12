---
title: "Control Banshee player with C"
date: 2011-06-21
forum: Programming Talk
---

### Post by kirill578 on 2011-06-21
I want to control bash player with my c program. I tried 

```
system("banshee --next");
```
 
, but the problem that my program have to be ran with sudo permissions (to get access to parallel port), so this reopen another windows of banshee which doesn't have any of my music (probably because it is Administrator). I tried to add 


```
system("su myusername");
```

before, but it stops the program somewhy :(

---

### Post by Petrolea on 2011-06-21
It stops the program because you would have to enter the password. You could echo the password and use a pipe to transfer it, but that isn't recommended because of security reasons. But you can try it if you don't see any risks. Google will find you tons of examples on how to do it.

---

### Post by kirill578 on 2011-06-21
I don't think it asks for password, it does execute the "su myusername" but it exit the program after it.
maybe I'm wrong, anyway I couldn't find any think about what you said

---

### Post by Petrolea on 2011-06-21
> **kirill578 said:**
> I don't think it asks for password, it does execute the "su myusername" but it exit the program after it.
maybe I'm wrong, anyway I couldn't find any think about what you said

Read this: [http://ubuntuforums.org/showthread.php?t=1355242](http://ubuntuforums.org/showthread.php?t=1355242)

The way I described isn't recommended, but this thread describes lots of other ways to run something as su.

---

### Post by kirill578 on 2011-06-21
It does the same thing - opens sudo banshee process
I think that "SU" itself cause program to exit. In addition, it doesn't ask for password if you have already entered the it (when ran the program)

I believe there should be some other solution to control banshee with C

---

### Post by maddog39 on 2011-06-22
Though probably a bit more complicated, if you use dbus you will get much better results and will avoid the permissions issue. If you really cant use dbus, then the next proper way to approach this would probably be to fork() and exec() on the banshee command and create a pipe to send the password to the child process (su/sudo) over stdin. The method I just described is quite complicated and not very straight forward if you've never done it before. 

One last dirty method which might work is to do something like:
```

system("yes yourpassword | su yourusername -c \"banshee --next\"");

```

[Edit]
On a side note, I wonder if there is a system call for switching users during execution, though afaik there isn't one.

---

### Post by kirill578 on 2011-06-22
I tried the dirty method, it **pause**s my program, opens a new process of Banshee player wait until I close the process and then continue execute my program. I don't really understand why should I enter any password. to stop music I can just open the terminal and execute the following command "banshee --stop". Furthermore my program is executed with sudo command (because i have to get permissions to control parallel port - hardware) ,therefor it should get all the permissions to all users ( The only one user I have ). So I don't understand why I should enter my password again.

Due to my lack of knowledge of fork() and exec() stuff, I don't know how to do this. I'll appreciate anyone who would be nice help me with this.

---

### Post by maddog39 on 2011-06-22
You need to switch users because when banshee launches it look in the home directory for your music library database and its settings for your user. If your running the program as root then the home directory is that of the root user and banshee comes up in a new window with a library thats completely empty. Maybe banshee has a command line option to specify a database path? I dont know off hand.

And your program hangs when you run the banshee command because system() is a blocking system call meaning that it stops all execution of your program until your call to system() returns (or is otherwise finished executing). Using fork and exec gives you more control in this situation.

Quite honestly, see if you can't figure out how to use dbus because this is the reason its there and finding a work around is not going to solve your problem in the long term. I wrote an article on how to use dbus with banshee using python and use that as a starting point then look at the native C dbus documentation and see if you can't rewrite my example in C. Google "banshee dbus python" and its the first result.

---


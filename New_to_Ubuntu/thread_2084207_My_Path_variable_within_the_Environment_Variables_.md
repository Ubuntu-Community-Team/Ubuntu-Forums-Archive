---
title: "My Path variable within the Environment Variables is deleted, how can I fix it?"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by sepids on 2012-11-14
I think that the I have deleted or set a wrong value to the Path variable within the Environment Variables in my Ubuntu server 12.10. I was able to log in from a text editor but don't know how to access the file to replace this value with the default "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
It doesn't know any of the command or directories that I type!:( 

Appreciate your help.

*I have many settings and programs on this server and don't want to lose them!

---

### Post by sisco311 on 2012-11-14
You have to use the full path to the commands you have to run. If memory serves, in Ubuntu, the default PATH is defined in /etc/environment. To open the file in nano you have to run, as root:
```
/bin/nano /etc/environment
```
or as an admin:
```
/usr/bin/sudo /bin/nano /etc/environment
```

Obviously, if you have overwritten the PATH variable in another file, then you will have to replace /etc/environment with the said file.

---

### Post by drmrgd on 2012-11-14
How did you change your $PATH?  If it was just a one time command like:

```
PATH="something I didn't want to put here"
```

Then that will be a one time thing, and you can fix it by logging out and back in (it'll reload the default from /etc/environment).  If you actually made a more permanent change somewhere, then you can rebuild it.  I think it's pretty standard as it's the same on my 10.04 server and my 12.04 desktop:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

```

---

### Post by sepids on 2012-11-14
Thank you both so much! it's fixed! but I'm facing another problem!:( whatever command that I get command not found?!!!

---

### Post by Impavidus on 2012-11-15
Then it's not fixed, because if your PATH is correct it should find every command. Could you check the result of```
/bin/echo $PATH
```The problem can also be in your .bashrc. Use```
/bin/cat /home/yourusername/.bashrc
``` and look for any code block containing PATH.

---

### Post by claudevandort on 2013-05-15
> **drmrgd said:**
> How did you change your $PATH?  If it was just a one time command like:

```
PATH="something I didn't want to put here"
```

Then that will be a one time thing, and you can fix it by logging out and back in (it'll reload the default from /etc/environment).  If you actually made a more permanent change somewhere, then you can rebuild it.  I think it's pretty standard as it's the same on my 10.04 server and my 12.04 desktop:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

```
You saved me! thank you!! :D

---


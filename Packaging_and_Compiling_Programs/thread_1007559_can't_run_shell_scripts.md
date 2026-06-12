---
title: "can't run shell scripts"
date: 2008-12-10
forum: Packaging and Compiling Programs
---

### Post by mohitgoyal on 2008-12-10
Welcome all...
I am a new user to bash shell. Can anyone tell me how to run self made shell scripts...? Earlier it was no problem. But I don&#8217;t know why it now not runs...Same is cases with my internet settings...Presently I am sending this thread using vista...I have ubuntu 7.04... Below is A SNAPSHOT of the commands that appear actually...


mohit@mohit-desktop:~/practice/self/shell$ cat > ss1 
#ss1 
date 

mohit@mohit-desktop:~/practice/self/shell$ cat ss1 
#ss1 
date 

mohit@mohit-desktop:~/practice/self/shell$ ls -l 
total 4 
-rw-r--r-- 1 mohit mohit 11 2008-12-04 19:24 ss1 

mohit@mohit-desktop:~/practice/self/shell$ umask 0022 

mohit@mohit-desktop:~/practice/self/shell$ chmod 744 ss1 

mohit@mohit-desktop:~/practice/self/shell$ ls -l 
total 4 
-rwxr--r-- 1 mohit mohit 11 2008-12-04 19:24 ss1 

mohit@mohit-desktop:~/practice/self/shell$ ss1 
bash: ss1: command not found 

mohit@mohit-desktop:~/practice/self/shell$ su 
Password:  

root@mohit-desktop:/home/mohit/practice/self/shell# ss1 
bash: ss1: command not found 

root@mohit-desktop:/home/mohit/practice/self/shell# ls -l 
total 4 -rwxr--r-- 1 mohit mohit 11 2008-12-04 19:24 ss1 

root@mohit-desktop:/home/mohit/practice/self/shell# ss1 
bash: ss1: command not found 

root@mohit-desktop:/home/mohit/practice/self/shell# chmod 777 ss1 

root@mohit-desktop:/home/mohit/practice/self/shell# ls -l 
total 4 
-rwxrwxrwx 1 mohit mohit 11 2008-12-04 19:24 ss1 

root@mohit-desktop:/home/mohit/practice/self/shell# ss1 
bash: ss1: command not found

---

### Post by caljohnsmith on 2008-12-10
Try adding the "shebang" at the beginning of your script, because you need to specify which shell should be used to run the script:
```
#!/bin/bash
date
```
Then after you have made it executable with "chmod" like you did before, run it with:
```
mohit@mohit-desktop:~/practice/self/shell$ [COLOR="Blue"]./ss1 [/COLOR]
```
How about giving that a shot and let me know how it goes.

---

### Post by mali2297 on 2008-12-10
You should also be able to run it directly with the command
```

mohit@mohit-desktop:~/practice/self/shell$ bash ss1 

```

---

### Post by mohitgoyal on 2009-02-04
thnx buddy... i will try it...

---

### Post by mohitgoyal on 2009-02-04
> **caljohnsmith said:**
> Try adding the "shebang" at the beginning of your script, because you need to specify which shell should be used to run the script:
```
#!/bin/bash
date
```
Then after you have made it executable with "chmod" like you did before, run it with:
```
mohit@mohit-desktop:~/practice/self/shell$ [COLOR="Blue"]./ss1 [/COLOR]
```
How about giving that a shot and let me know how it goes.

thnx caljohnsmith....nice to see your suggestion.. will try it

---


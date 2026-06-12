---
title: "How do I get perl/python programs to run?"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by linsol on 2013-05-20
I've been trying to get a perl and a python program to run. When I click on them, it opens in kate etc. How do I make them use perl/python? Using Ubuntu 13.04.

Thanks
Bill

---

### Post by sanderj on 2013-05-20
> **linsol said:**
> I've been trying to get a perl and a python program to run. When I click on them, it opens in kate etc. How do I make them use perl/python? Using Ubuntu 13.04.

Thanks
Bill

Start the file browser Nautilus, go to the directory containing the python file ".py". Then right click somewhere in that folder but NOT on a file, and click on "Open in terminal". That will open a (black) terminal. Type "python <filename>.py" and press enter.

---

### Post by anoldone on 2013-05-20
You need to change the file's permission to be executed:```
chmod +x /path/to/file
```
If that's not enough, the first line of your program needs a correct interpreter chosen. Example for python:```
#!/usr/bin/python

#rest of your code
```

---

### Post by sanderj on 2013-05-20
> **anoldone said:**
> You need to change the file's permission to be executed:```
chmod +x /path/to/file
```
If that's not enough, the first line of your program needs a correct interpreter chosen. Example for python:```
#!/usr/bin/python

#rest of your code
```

Are you sure?

```
sander@flappie:~$ ll testing.py
-rwxrwxr-x 1 sander sander 35 May 20 18:37 testing.py*
sander@flappie:~$ cat testing.py
#!/usr/bin/python

print "Hello!"

sander@flappie:~$ 
```

... but the default app in Nautilus is ... "Text Editor".
So it would also need changing the default handler to python ...

---

### Post by supremedalek on 2013-05-20
I think what is happening is that your file browser think you want to edit it. See if you can right-click on the file, select *Open with _O_ther application* and then select python/perl.

You can also create an icon/tab/something in your menu that when clicked will run the file for you.

Is this how you want to run those programs (double-clicking on them)?

---

### Post by linsol on 2013-05-21
Thanks, I had to do it from a terinal. Wouldn't do it in a file manager.

Bill

---


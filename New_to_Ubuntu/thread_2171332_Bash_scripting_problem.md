---
title: "Bash scripting problem"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by acc61287 on 2013-08-30
Hello guys, im creating a script that automatically install the installer

ex:
##################################
#!/bin/bash


installer=myinstaller.tar


cd /tmp
tar xpvf $installer
cd ./dist
./setup 
#do some task here
#list of lot command

##################################

After the setup the script in terminated (exit)
My question is how do i prevent the this? the command on the do some task here is not executing :(

Thanks in advance!
-Chris

---

### Post by bkline on 2013-08-30
That's not how bash is supposed to work.  If your master script is really that simple (no conditionals deciding what to do based on the exit code from setup), and you're really sure that "some task" is not being invoked (confirm this by having "some task" do some logging when it's first invoked), then you'll need to start digging into setup (assuming it's a script or compiled program to which you have the source).  Check available disk space.  Check to make sure setup hasn't changed permissions in some surprising way which would prevent "some task" from doing what you expect.

---

### Post by whitesmith on 2013-08-30
To help us help you, post all code between tags like ```
this
``` and then use something like postimage.org to give us a screenshot.

---

### Post by prodigy_ on 2013-08-30
> **acc61287 said:**
> #do some task here
...
After the setup the script in terminated (exit)
My question is how do i prevent the this? the command on the do some task here is not executing :(
Well, if a line is prepended with **#** like in your example here bash treats it as a comment and thus it never gets executed.

If it's not commented out, post the actual script (if possible).

---

### Post by SpEcIeS on 2013-08-30
You may find it useful to write your scripts with:
```
#!/bin/bash -e
```

Also, you may want to use the following to display any error codes:
```
echo $?
```

Here is a link to some error code descriptions:
[http://tldp.org/LDP/abs/html/exitcodes.html]("http://tldp.org/LDP/abs/html/exitcodes.html")

Have a look at this book:
[http://it-ebooks.info/book/1533/]("http://it-ebooks.info/book/1533/")

---


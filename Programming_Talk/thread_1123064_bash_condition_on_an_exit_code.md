---
title: "bash: condition on an exit code"
date: 2009-04-11
forum: Programming Talk
---

### Post by PGScooter on 2009-04-11
Hi,

I would just like to make sure my perl program completed without any problems from within my bash script. Is this the best way to do it or is there an easier way?

thanks

```

perl myprogram.pl anargument1
if [ "$?" = '0' ]; then
        echo "program completed without problems"
fi

```

---

### Post by odyniec on 2009-04-11
You could do:
```
perl myprogram.pl anargument1 && echo "program completed without problems"
```

---

### Post by slavik on 2009-04-11
OP, I would suggest using your way and add an else for when it exists with an error.

odyniec's versions depends on short circuiting of logical operations.

---

### Post by PGScooter on 2009-04-11
thank you both!

odyniec, that is an interesting trick to know

---

### Post by ghostdog74 on 2009-04-12
not sure why you don't do that from inside your Perl script.

---

### Post by ad_267 on 2009-04-12
> **ghostdog74 said:**
> not sure why you don't do that from inside your Perl script.

I assume he might want to do something a bit more complex, using more than just echo.

---

### Post by ghostdog74 on 2009-04-12
> **ad_267 said:**
> I assume he might want to do something a bit more complex, using more than just echo.
he could have done everything in Perl. :)

---

### Post by PGScooter on 2009-04-12
> **ghostdog74 said:**
> he could have done everything in Perl. :)

haha yeah this is true. But I am trying to learn a little bit of bash.. I am making a script that sees if a list of URLs have changed from the last time you ran the script. In bash, I think this is quicker- you have wget to download the url easily (and with good options) and you have diff to check if it is different from the previous versions (which I have archived somewhere).

The only reason I need Perl is for regular expressions. A lot of URLs change every second because they give the time or have some weird javascript or because of advertisements; thus, I use regexs to get rid of these parts before comparing the two file in Bash. I'm sure I could do this in Bash as well, but with Perl it's just so easy.

The script is actually working great so far. Perhaps it would have worked better if only in Perl though? :)

---

### Post by jcrout on 2009-04-22
The exit code you want to test is the exit code produced after the script ends. If the test is *inside* the script, this can't be done because the script hasn't terminated yet.  The test code, if run *inside* it, will return the result of the most-recently executed command that ran while its shell was open, instead of returning the result after the termination of the script.  

When a script is executed, it runs inside its own shell; a shell that was spawned, specifically so the script could be run inside it.  The script hasn't ended until the shell has been exited. So, putting the test inside the script will test the command most-recently executed *inside the shell*.

To see this, try the following:
```
#!/bin/sh
#
pwd
cd /var/log
pwd
exit $?
```The first pwd command will give as output,  the name of the directory you started in. Then the cd command will change it to /var/log, so that when the next 'pwd' command is executed, the directory named, will be /var/log. Then the exit is executed. The bash variable "$?" doesn't need to be explicit since this variable is used by default.   If you add "echo $_" just before the "exit" command, it will show 'pwd' is the command that was most-recently executed.  If you run "echo $_" at the command prompt after the script ends, the echoed value will be whatever name you assigned to this test script.

That is, of course, if you've also changed the file mode to allow it to be executed (e.g. ./mytest.script).  If you run it as "sh mytest.scipt", the "echo $_" statement will output "sh".

Hope this is useful to you. 

--J

---

### Post by PGScooter on 2009-04-22
jcrout,

that was very useful! thank you for the detailed explanation- that put a few things in perspective for me that I was overlooking.

thanks!

---


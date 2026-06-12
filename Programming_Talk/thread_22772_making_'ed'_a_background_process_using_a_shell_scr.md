---
title: "making 'ed' a background process using a shell script"
date: 2005-03-29
forum: Programming Talk
---

### Post by scm on 2005-03-29
I need to make the program 'ed' a background process using a shell script. I have been sucessful in making 'ed' a background process in shell mode doing the following:

ed &

However, when I using the following BASH script:

#/bin/bash

ed &

make the file +x and run it, it does not put ed into the background. Does anyone know why/how to make this work?

TIA

---

### Post by bnutting on 2005-03-29
What exactly are your trying to do?

---

### Post by scm on 2005-03-31
[QUOTE=bnutting]What exactly are your trying to do?[/QUOTE]

I am writting a program that requires 'ed' to be put in the backgroud with a shell script.

---

### Post by bnutting on 2005-04-01
[QUOTE=scm]I am writting a program that requires 'ed' to be put in the backgroud with a shell script.[/QUOTE]
I kind of gathered that from your first post ;-) I *was* looking for more detail but that's OK. Try adding nohup to your line that starts ed &.
Will this do what you want?

---

### Post by scm on 2005-04-02
[QUOTE=bnutting]I kind of gathered that from your first post ;-) I *was* looking for more detail but that's OK. Try adding nohup to your line that starts ed &.
Will this do what you want?[/QUOTE]

Thanks for getting back to me O:) The following did not work: nohup ed& when written in a shell script. The shell script I wrote looked like this:

#/bin/bash

nohup ed&

Let me go into more details about what I'm trying to do, maybe you could try them yourself to see the delema I am in.

What I am trying to do is make the program 'ed' start up and run as a background process after it is called from a shell script. If you were to create the following script and run it, you will see that it does not work:

#/bin/bash

ed&

If you use the command 'bg' you will see that 'ed' is not running in the backgroud.

Interesting enough, if you run the following from the command prompt (ed&) it _does_ run in the background.

Give it a shot and see.

So you're probably wondering why it is so important for me to be able to start 'ed' and have it run in the background from a shell script. The reason is that I am working on a program called EULUIE that is a command interface/editor that utillizes calls to given commands via shell scripts. In this case, I need 'ed' to be started and put in the background.

I have looked all over the Net for info as to why 'ed' will start in the background via a prompt but not a script and how to fix this. Any suggestions/help would be great as the the editor part of my program is at a stand still.

---

### Post by Roptaty on 2005-04-03
It seems like bash is closing down the stdin descriptor for your ed process. ed will then exit, since it can't read more data. 

Some of the solutions I can think of, are using pipes to send and read data from ed or just invoking ed when you need it.

---

### Post by dusu on 2005-04-03
Hi,

maybe that's totally stupid from me, but shouldn't your first line have a ! in it, like that :
```
#!/bin/bash
```
?

---

### Post by scm on 2005-04-03
[QUOTE=dusu]Hi,
maybe that's totally stupid from me, but shouldn't your first line have a ! in it, like that :
```
#!/bin/bash
```
?[/QUOTE]

I did that in my script, just left it out in the posting. Good eyes though.;-)

---

### Post by scm on 2005-04-03
[QUOTE=Roptaty]It seems like bash is closing down the stdin descriptor for your ed process. ed will then exit, since it can't read more data. 

Some of the solutions I can think of, are using pipes to send and read data from ed or just invoking ed when you need it.[/QUOTE]

Hmmm, interesting. I'll have to see about this.

---

### Post by bnutting on 2005-04-13
Roptaty sounds like he/she has a better solution. I am courious to here is calling it as you need works.

---

### Post by mynk on 2008-10-01
I faced an issue with using '&' to create a background process on an arm board. I realized it gives an error /dev/null not found. Creating the same fixed the problem for me.

Are you getting any such errors?

---


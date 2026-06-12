---
title: "starting Tomcat using Shell Scripts"
date: 2007-08-29
forum: Programming Talk
---

### Post by Dave85 on 2007-08-29
hi there,

I believe what i want to do is fairly straight forward, but i cant seem to be able to do it. Normally, to start tomcat, i would type in the following:

```


cd /home/path/tomcat/bin
./startup.sh

```

and that will run tomcat (although, in windows, you can click on that startup bat fie and it will start it, but in linux, this shell script wont run by clicking it, only by entering the text into the terminal)
Now in windows, i can create a bat file with the above code and it will un the command in cmd. 

How can i do that using a shell script?
I tried adding that code and creating a shell file, and then creating a launcher from the desktop (tried running as an application and an application in the terminal) but that doesnt work!

So does anyone know how i can make a script file that will run this tomcat from using a single click of a shellfile/launcher?

Many Thanks

---

### Post by Dave85 on 2007-08-30
Anybody? This is causing me a massive headache. I would greatly appreciate anybodies help.

---

### Post by nanotube on 2007-08-30
> **Dave85 said:**
> Anybody? This is causing me a massive headache. I would greatly appreciate anybodies help.

did you make that script executable?
```
chmod a+x scriptname
```

also, add the line
```
#!/bin/bash
```

if you don't want to do either of those, you could also invoke the script directly with a shell when starting it,  using command
```
bash scriptname
```

let us know if any of those are of any help. :)

---

### Post by Dave85 on 2007-08-31
Sorry for the delayed reply, but that didnt work either.
I added in that line so the shell script has the following:
```

#!/bin/bash
cd /home/path/tomcat/bin
./startup

```

and i made the file executable!

Creating a launch to run this (as an application or application in the terminal) doesnt work

Any ideas?

---

### Post by Another Monkey on 2008-03-27
Hi there,

Did you ever find out the answer to this?  It is doing my head in.

I know it must be simple, but it seems that it is so simple it's not documented anywhere!

I can launch Tomcat from a Terminal session or from Eclipse in order to debug, but sometimes I just want to double click on a launcher and get it going and I just can't figure out how to do it.

Any instructions are going to have to be explicit I'm afraid as I am still new at this.

---

### Post by Another Monkey on 2008-03-28
Done it.

I created 2 scripts "gnome_tomcat_start.sh" and "gnome_tomcat_shutdown.sh" in /bin and then pointed launchers at them.  Is this the correct way to do it, or is there a better way?  It seems that Gnome is unaware of any environment variables defined in "~/.bashrc" for some reason.

[FONT="Courier New"]#!/bin/bash
#Varibales to let Tomcat launch
export CATALINA_HOME=/opt/apache-tomcat-5.5.26
export JAVA_HOME=/opt/jdk1.5.0_15

bash -i /opt/apache-tomcat-5.5.26/bin/startup.sh[/FONT]

and
[FONT="Courier New"]#!/bin/bash
#Varibales to let Tomcat launch
export CATALINA_HOME=/opt/apache-tomcat-5.5.26
export JAVA_HOME=/opt/jdk1.5.0_15

bash -i /opt/apache-tomcat-5.5.26/bin/shutdown.sh[/FONT]

---

### Post by nanotube on 2008-03-28
well, from "man bash" and its "invocation" section, i see the following:
> When bash is started non-interactively, to run a shell script, for example, it looks for the variable BASH_ENV in the environment, expands its value if it appears there,  and  uses  the
       expanded value as the name of a file to read and execute.  Bash behaves as if the following command were executed:
              if [ -n "$BASH_ENV" ]; then . "$BASH_ENV"; fi
       but the value of the PATH variable is not used to search for the file name.

so, yea, shellscripts by default don't inherit the environment variables. but if you set an environment variable BASH_ENV to say, your .bashrc, then it will. but what you're doing looks reasonable, as well.

---

### Post by mssever on 2008-03-28
> **nanotube said:**
> if you set an environment variable BASH_ENV to say, your .bashrc, then it will.
I never knew about $BASH_ENV. Thanks.

---

### Post by Finch75 on 2008-03-31
I see this is (almost?) solved, but just wondering:

What's wrong with "/etc/init.d/tomcat55 start"?

That's always worked for me :-)
I guess this only works if you installed Tomcat from the repositories but you never said you hadn't so I just assume you have ;-)

---


---
title: "Eclipse + Console command"
date: 2008-07-29
forum: Programming Talk
---

### Post by LightRaven on 2008-07-29
Would anyone know how to run (inside Eclipse) the unix time command on the program you are executing using Eclipse?

Thanks.

---

### Post by Shin_Gouki2501 on 2008-07-29
System.currentTimeMillis ???
You need to go more into Details if you want an answer...

---

### Post by tinny on 2008-07-29
> **LightRaven said:**
> Would anyone know how to run (inside Eclipse) the unix time command on the program you are executing using Eclipse?

Thanks.

:confused:

Do you want to make the application your executing in eclipse run with a specific set of command line args?

I think this is what you are looking for...

"Run" > "Open Run Dialog" > create a new “Java Application” configuration (are you developing a standard J2SE app?)

You will then be presented with the "Run" dialog (see attached image)

You will want to pay particular attention to the “Arguments” tab of this dialog, this is where you can define various command line arguments (like you would enter if you where executing your application in a standard command line)

---

### Post by DrunkTankGunner on 2011-05-09
I think what he wants to use is this:
"time 
Determine the amount of time that it takes for a process to complete + other process accounting. Don't confuse it with the date command (see previous entry). E.g. I can find out how long it takes to display a directory content using: time ls. Or I can test the time function with time sleep 10 (time the commands the does nothing for 10 seconds)."
But instead of using it on the command line, he wants to use it when running a program in eclipse. I would like to know how to do this also.
Editing the variables in the run configurations doesn't help because the time command has to come before everything on the command line, it is not an argument.

---


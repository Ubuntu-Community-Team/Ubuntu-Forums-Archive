---
title: "Directory error"
date: 2019-01-18
forum: New to Ubuntu
---

### Post by alyce85 on 2019-01-18
I am new to my understanding of linux.

I am trying to install a bunch of libraries to set up the weather research and forecast model. 

Using csh (instead of the bash it runs off) all I need to do is link the pathway to export data using the following:
[COLOR=#000000][FONT=&quot]
setenv PATH $DIR/mpich/bin:$PATH[/FONT][/COLOR]

And the error I receive is:


DIR: Undefined variable.

Sounds easy, but how do I link this? There are 5 libraries to install so I'm stuck at the final part!

---

### Post by Holger_Gehrke on 2019-01-18
The character '$' in that command starts a substitution, "$DIR" should be replaced by the value of the variable DIR. There is no such variable in memory, so you get an error. You can either define that variable with the path to 'mpich/bin' as it's value or put that path directly in the command (example: 'setenv PATH /home/user/mpich/bin:$PATH').

Holger

PS: You're lucky you're using csh, bash would just substitute nothing for an undefined variable and go on with the execution ... A lot harder to find the reason for the errors resulting from that.

---


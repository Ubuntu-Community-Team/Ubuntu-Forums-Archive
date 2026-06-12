---
title: "execute terminal commands in QT4???"
date: 2007-06-29
forum: Programming Talk
---

### Post by @vijay@ on 2007-06-29
ok i recently installed QT4 ............and playing with it :p

i want the the application to execute [terminal commands] or [shell scripts (stored in a seperate file )]  when i press a button

im trying to make a simple gui to play a mp3 file which uses the  play command from  terminal to play the file:KS

how can i do this??? im knocking my head for quite a long time .........searched in google but no use:(:(
what should i play in the 
QObject::connect(.....................,SLOT(?????));

---

### Post by FilthyMonkey on 2007-06-29
Well, you could connect your button to a slot function which calls the system function with your argument.  See

[http://www.gnu.org/software/libc/manual/html_node/Running-a-Command.html#Running-a-Command](http://www.gnu.org/software/libc/manual/html_node/Running-a-Command.html#Running-a-Command)

If you want to do it more QT like, you would use a QProcess

[http://doc.trolltech.com/4.3/qprocess.html](http://doc.trolltech.com/4.3/qprocess.html)

---

### Post by @vijay@ on 2007-06-30
> **FilthyMonkey said:**
> Well, you could connect your button to a slot function which calls the system function with your argument.  See

[http://www.gnu.org/software/libc/manual/html_node/Running-a-Command.html#Running-a-Command](http://www.gnu.org/software/libc/manual/html_node/Running-a-Command.html#Running-a-Command)

If you want to do it more QT like, you would use a QProcess

[http://doc.trolltech.com/4.3/qprocess.html](http://doc.trolltech.com/4.3/qprocess.html)


thanx alot qProcess worked
just want to know which slot function calls the system function??? what must be the recever???

one more doubt 

how can i start a Qprocess when i clicked a button

i tried the below code  but didnt worked 
.......................................................................................................
QObject::connect(pushbutton,SIGNAL(clicked()), ????  ,SLOT(startProcess()));

void startProcess()
{
QProcess *myProcess = new QProcess;
myprocess->start("play /file/path");
}
...................................................................................................................

what should i place in place  of ????
i tried with QProcess but no use
 
THe error im getting is no such slot startProcess()

---


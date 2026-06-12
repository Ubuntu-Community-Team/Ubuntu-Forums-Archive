---
title: "Does learning linux commands essential for programming in c"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by mnbharadwaj on 2013-03-14
Hi I am a beginner in Linux,having 6 years of Programming Experience in C(With out RTOS,OS Concept)firmware developer, with the Windows OS.

I Have few Questions...

1. Does Learning Linux Commands(Shell Scripting and Other Linux related commands for Debian) is essential for Programming under Linux with C:confused::confused::confused:
2. If yes, How much do i need to learn(If u provide Links or Bulleted points whould be very helpful)
3. Do i need to learn Threading concept(But Again its the application based,I am planning to make 1 application on rasberry Pi(Linux Board,which will have USB,UART,GPIO etc everything inbuilt) as Robotic car,which will have Camera for lane detection,and will be driving the car with some dc motor,through UART i wll be controlling the car wirelessly with x-Bee Controller), does for this sort of application threading is essential:confused:

Your valuable comments are most welcome... :)
I am happy to become part of Linux Community :guitar:

---

### Post by kramer65 on 2013-03-14
Learning to navigate on the command line would be very helpful I guess. But this is quite easy. When you' ve learned the following commands you can already do a lot:

cd myfolder (change directory into myfolder/)
cd .. (change directory one folder up from the present one)
./somefile (execute somefile)
rm somefile (remove somefile)
cp somefile somedirectory/somefile (copy somefile to somedirectory/somefile)

And using threading is for small applications not really needed.

---

### Post by Abhinav Kumar on 2013-03-14
Hi
Shell scripting is generally used to automate tasks and interact with the shell. What do you mean when you say programming under Linux with C? Are you going to develop algorithms or write drivers or any other purpose? For developing algorithms you just need to know how to compile C code. For writing drivers you need to need to know a bit more of the shell commands (such as compiling and loading kernel object into kernel ). Have a look at
[http://www.codecoffee.com/tipsforlinux/articles/18.html](http://www.codecoffee.com/tipsforlinux/articles/18.html)

You should use gcc -Wall -lm firstProgram.c for compiling

For driving the car with DC motor, you can use microcontroller (which can be programmed using C). I am not sure whether threading is essential for x-Bee controller

Regards,
Abhinav

---

### Post by mnbharadwaj on 2013-03-14
Hi Kramer and Abhinav,

Thanx for quick reply....It clarified my doubt :P

---

### Post by Impavidus on 2013-03-14
Learning to use the command line isn't really necessary for C progamming, but it will come in handy. I've always run all programming tools from the command line. Threading is useful to take advantage of multiple processor cores, which isn't very useful if you're I/O limited, but it can also be good if you have I/O routines that may cause long waits and you don't want to interrupt more time critical parts of your program. You can have for example one thread in a fast loop to control your car based on lane detection and another thread waiting long times for user commands.

---

### Post by abrianb on 2013-03-14
You will get some great info from this... [http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

---

### Post by Vaspro on 2013-03-15
Hi,
   i to have the same problem can some one help me am not a programer but am a charcter designer so can some one help me regarding php commends and scripts

---

### Post by Impavidus on 2013-03-15
Php? Sounds like a completely different question to me. Better start your own thread. Anyway, what kind of characters? Typographical, mathematical, narrative, role playing game, ...?

---


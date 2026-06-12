---
title: "C++ executable problems."
date: 2008-04-14
forum: Programming Talk
---

### Post by atsukoarai86 on 2008-04-14
I am having an issue with a program I'm writing in Visual C++ 6.0. When I compile the program inside the compiler and execute it, the program runs properly, and the output file is created correctly, etc. However, when I close the compiler after selecting "Build executable" from the Build menu, and I open the Debug folder within the project folder and try to run the .exe file, it simply will not run. 

I don't know what on earth the problem could be. There are at LEAST two system("pause"); statements, one at the end of main, and one at the end of the write function, but when I run the executable outside the compiler, the command windows flashes for a fraction of a second on the screen, but the program isn't running.

Any suggestions? I don't have the code with me right now, otherwise I would post it. That's why I tried to describe the problem in as great detail as possible. If it will help, I will post the source code when I get home. 

Thanks programmers.

---

### Post by LaRoza on 2008-04-14
Get rid of the system("PAUSES") and run it from a terminal.

If there are errors, they will be visible.

---

### Post by mike_g on 2008-04-14
Try using getchar() instead of system("pause").

---

### Post by LaRoza on 2008-04-14
> **mike_g said:**
> Try using getchar() instead of system("pause").

system("PAUSE") isn't the problem, but it also isn't the solution.

---

### Post by atsukoarai86 on 2008-04-14
> **LaRoza said:**
> Get rid of the system("PAUSES") and run it from a terminal.

If there are errors, they will be visible.


I put the system pauses in there so it would stop executing. If I don't put the pauses in there, I wouldn't be able to read any of the cout statements because the execution wouldn't pause. 

and I don't know what "run it from a terminal" means. I run it in the command prompt on Windows XP.

---

### Post by atsukoarai86 on 2008-04-14
> **mike_g said:**
> Try using getchar() instead of system("pause").

hmmm... getchar()... yes, I think I remember my teacher saying something about that... but all of the other programs I've written work, and I haven't don't anything differently... It just galls me that I'm having this problem and there are no indications as to what's causing it...

---

### Post by Zugzwang on 2008-04-14
Ok, so you're telling us that your program isn't running and you're using the command prompt (terminal called by most users here). 

So you use CD to switch into the debug build directory and then type "program"<ENTER> or however your program is called. What happens then? Does your computer hang or does your program return immediately? Do you get an error message? "Isn't running" isn't very precise here.

---

### Post by LaRoza on 2008-04-14
> **atsukoarai86 said:**
> I put the system pauses in there so it would stop executing. If I don't put the pauses in there, I wouldn't be able to read any of the cout statements because the execution wouldn't pause. 

and I don't know what "run it from a terminal" means. I run it in the command prompt on Windows XP.

Ok, open a command prompt. (cmd.exe) 

Run the program from the command prompt. Does it work? Are there errors?

Don't double click on the executable.

If this program is throwing errors, no amount of system("PAUSE") or getchar()s are going to help. Error messages are meant to be seen.

---


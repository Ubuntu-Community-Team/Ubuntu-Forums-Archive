---
title: "opening a new terminal from the existing terminal and transfer  control to it"
date: 2010-11-14
forum: Programming Talk
---

### Post by skarthik on 2010-11-14
Hi all.... 
I have a c program with a parent and child created using fork() and both  do different actions. I want to display the printf statement outputs of  two processes in two different terminals. So i tried to open a new  terminal using gnome-terminal sing system call. It opens a new terminal  but the control is not transferred to new terminal
Meanwhile i tried the xterm commands  but am unable to get what i need
What i want to implement is as follows

int main()
{
   ....
   ....

   pid=fork();
   if(pid==0)//child
  {
     system("COMMAND");  /*COMMAND is command needed to open a new  window and display further printf outputs and get fiurther inputs needed  by child here after, with parent retaining its control in parent  terminal and that should do parent input and outputs in tat parent  terminal */
      .....
      .....   //some actions
      printf("...."); // This is child's one , so needed to display in new window
      getchar(); // wait for user to see displayed results
      system("COMMAND"); /* COMMAND is to close the child window or terminal after user seeing displayed results */
   }
   if(pid>0) //parent 
   {
      ....
      ....
      /* The printfs and scanfs here are to be done in parent terminal from where program is executed*/
   }
   return 0;
}

So I need help in this.
Thanx in advance

---

### Post by Arndt on 2010-11-14
> **skarthik said:**
> Hi all.... 
I have a c program with a parent and child created using fork() and both  do different actions. I want to display the printf statement outputs of  two processes in two different terminals. So i tried to open a new  terminal using gnome-terminal sing system call. It opens a new terminal  but the control is not transferred to new terminal
Meanwhile i tried the xterm commands  but am unable to get what i need
What i want to implement is as follows

int main()
{
   ....
   ....

   pid=fork();
   if(pid==0)//child
  {
     system("COMMAND");  /*COMMAND is command needed to open a new  window and display further printf outputs and get fiurther inputs needed  by child here after, with parent retaining its control in parent  terminal and that should do parent input and outputs in tat parent  terminal */
      .....
      .....   //some actions
      printf("...."); // This is child's one , so needed to display in new window
      getchar(); // wait for user to see displayed results
      system("COMMAND"); /* COMMAND is to close the child window or terminal after user seeing displayed results */
   }
   if(pid>0) //parent 
   {
      ....
      ....
      /* The printfs and scanfs here are to be done in parent terminal from where program is executed*/
   }
   return 0;
}

So I need help in this.
Thanx in advance

The terminal emulator opens a new pseudo-tty (you can see which one if you give the command 'tty' in it), and you can freely write to it, you just need to know which one it is. For reading, let the command you start be one which reads from its stdin and send the data to your original process. But calling 'system' will not work, since it waits for the command to end. At least unless you end the command with an '&'. You can also look at 'popen'.

These are just ideas I would pursue myself to solve the problems - I haven't done this myself.

I don't think there ought to be a difference between gnome-terminal and xterm, but I could be wrong.

---

### Post by itcotbtoemik on 2010-11-14
It seems that what you're trying to do is usually done via
attaching to the pseudo-terminal itself rather than opening
a pipe.  (xterm and gnome-terminal, by the way, differ on
what file-descriptors are/are not closed on starting the
terminal).  Someone was asking about the same thing in "expect"
last week, for which there's an xterm solution using the
"multixterm" script.

---


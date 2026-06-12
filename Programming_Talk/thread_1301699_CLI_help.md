---
title: "CLI help"
date: 2009-10-26
forum: Programming Talk
---

### Post by hifza on 2009-10-26
im completely new to linux. i hav the following task to complete. i managed to do this by adding aliases to the .bashrc file and by changng the PS format from there. but the teacher wants it all to be done in the form of a c code. plz help. i'm not looking for someone to solve the whole thing for me. 
isn't there a way i could add the same aliases into a new bash script and call it from within the c code and still have these functions implemented?

TASK:
When the process starts, a prompt of following format should appear on the Terminal/Konsole: 


[time] user@host: working_dir $ 


e.g., [12:34] ali@myPC: /home/ali $ 


Students are required to implement three possible operations. These include

When the user enters “list”, a listing of all the contents of the working directory should be displayed (similar to the 'ls' program in Linux)
When the user enters “create file_name content”, the process should
Create a file called file_name in the current directory
Write the string “content” into the newly created file

The process should terminate/end when the user enters "quit"

---

### Post by dwhitney67 on 2009-10-26
Use printf() for printing prompts, data, whatever to the terminal.

You then need to wait (ie fgets()) for user input for one of the valid commands.  For valid commands, you can "cheat" by using the system() command to execute the command, or you can use popen().  The latter returns a file descriptor with which you can use fgets() to read, line by line, the results.  For each line read, just printf() it to the terminal.

For invalid commands, just display some error message, and then poll again for the user's input.

---

### Post by benj1 on 2009-10-26
you cant use your .bashrc file, unless  you were to read and parse the file yourself.
look up getenv() for user variables ie current user

for the rest of the task, im not sure what level you need to complete it to but [http://www.gnu.org/software/libc/manual/html_node/index.html]("http://www.gnu.org/software/libc/manual/html_node/index.html") might be useful

---

### Post by cariboo on 2009-10-26
It is against forum policy to answer homework questions.

This thread is closed.

---


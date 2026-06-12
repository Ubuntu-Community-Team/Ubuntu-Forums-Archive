---
title: "[C++]Redirecting tty on stdout, stdin on tty?"
date: 2009-04-12
forum: Programming Talk
---

### Post by Uriziel on 2009-04-12
Problem bellow is mainly solved. My actual problem is described in next posts 
```
I'm trying to make program making stats and few other functions from game - Enemy Territory. There are few similar programs on Windows, I asked one guy for a code so I could make this for linux, well, I was impressed how easy it was, it was collecting informations from 'ET Console', which is separate window in Windows. Seriously, its few minutes of work. But on linux it doesn't create new window. If I run it in terminal its printing everything from 'ET Console' in terminal. It even prints nice comment:
[code]Started tty console (use +set ttycon 0 to disable)
```
(if I don't run it in terminal it says:
```
stdin is not a tty, tty console mode failed
```
I tried useing popen(), but well, it doesn't work with ET.
So, I suppose I have to redirect on my stdin on tty and tty on stdout, I suppose its only way, but I don't know how.
Thanks in advance.
btw. If you didn't notice I'm still beginner

#edit
To run et I'm useing script et-sdl-sound -> it echos some informations in terminal. When I was trying to use popen() it gave me only this echos, nothing from ET Console. Dunno why, I run ./etsdl > dump. It dumped only echos (without anything from ET Console which actually printed many things in terminal). So, I made et.x86 > dump, it gave nothing. Even if terminal was spammed by everything from ET Console, dump was empty.[/code]

---

### Post by dribeas on 2009-04-12
There are a couple of things you can do. If you launch the game programmatically, then you can create a couple of pipes (man pipe) before you fork to call the game. Then use the dup/dup2 () system functions to make standard input and output (fd=0,2) go through your pipe. Finally exec (man exec) the game. The game will read and write from the console, but that would be redirected through the pipes to your program (other process).

The other solution involves redirecting from bash. You can create a couple of named pipes (man mknod, I believe) that will appear as files in your system. Then your program just needs to read/write from the pipes.

```

$ mknod -p /tmp/console_input
$ mknod -p /tmp/console_output
$ game < /tmp/console_input > /tmp/console_output

#on another terminal if you want to use your stdout as input for the game, and viceversa:
$ your_program < /tmp/console_output > /tmp/console_input 

```

---

### Post by Zugzwang on 2009-04-13
BTW: Note that besides "stdout", there's also "stderr", so even if you redirect your output, a lot of stuff might still be printed to the console. You might need to redirect stderr as well. Try:
```

./program 2>&1 >/tmp/test

```
and see if all output is redirected.

---

### Post by Uriziel on 2009-07-02
Refresh after a while. I dropped this project after few tries but now I'm back to it.
I made /tmp/console_input and /tmp/conole_output, last time it didn't work because command was wrong :P
not mknod -p /tmp/console_input 
but mkond /tmp/console_input p
Thanks anyway, it helped me a lot.
So I run the game in terminal:
```
uriziel@uriziel-desktop:~$ ./etsdl < /tmp/console_input  > /tmp/console_output 2>&1 
```
Nothing happens.
In other terminal i run
```
cat /tmp/console_output
```
And in the 3rd teminal i run:
```
 cat > /tmp/console_input
```
Now game starts with output in 2nd terminal. But there is no input :<
Not 1st nor 2nd terminal writes input into game. I don't know how to slove it.
Also I have no idea how to read /tmp/console_output in my program. I supposed anything will work
```
int main() { while(1);}
```
```
./my_program < /tmp/console_output
```
Prints nothing

---

### Post by benj1 on 2009-07-02
first off

```
 cat > /tmp/console_input
```

wont work, you are sending nothing to the input file

cat just displays what is currently in the file you want to view

does 

```
game < /tmp/console_input
```
work ?

what input are you trying to send? why is it in tmp? or are you trying to capture stdout to process, to then use as stdin?

---

### Post by Uriziel on 2009-07-02
cat also redirects stdin into stdout (man cat)
so ```
cat > /tmp/console_input
```
will redirect eveything i write in terminal into /tmp/console_input
I'm sure it works because i tested it with:
```
cat /tmp/console_input
``` in one terminal and ```
cat > /tmp/console_input
``` in second.
I'm trying to send commands from other terminal (later from my program) into game and receive stderr from game into 3rd terminal (later into my program).

---

### Post by benj1 on 2009-07-02
> **Uriziel said:**
> cat also redirects stdin into stdout (man cat)
so ```
cat > /tmp/console_input
```
will redirect eveything i write in terminal into /tmp/console_input
I'm sure it works because i tested it with:
```
cat /tmp/console_input
``` in one terminal and ```
cat > /tmp/console_input
``` in second.

I'm trying to send commands from other terminal (later from my program) into game and receive stderr from game into 3rd terminal (later into my program).

re cat > /tmp/console_input yes it would work for sending something for a file, but i fail to see the point of it, it would just send it to the file, the same as using a text editor.
are you trying to record the input you send to the game? you could perhaps look at bash history.
is it fixed input or does it vary, not really knowing the game (quake enemy territory) or what program you are trying to make, i don't know.

2nd thought why don't you use the c++ system() command? 
system("GAME options you want to add > /tmp/console_output")

or read up on pipes heres a [start]("http://www.gnu.org/s/libc/manual/html_node/index.html")

---

### Post by Uriziel on 2009-07-02
I suppose you didn't read previous posts.
Its nod created by mknod.
I use it to redirect game (not mine) input/output into my own program because I don't know how to use pipe/fork/dup/dup2 method.
But before I'll implement this into mine program I have to test this out.
So I use cat to check if everything work fine, but it doesn't. I can redirect output, that works fine. Input is supposed to be redirected, but, yhmm... it doesn't work, i described it in previous post.
It should look like this:
```

mknod /tmp/console_input p && mknod /tmp/console_output p #creating nodes to redirect input/output 
./game < /tmp/console_input > /tmp/console_output 2>&1 # Redirecting games in/out+err to nodes
./myprogram < /tmp/console_output > /tmp/console_input # Redirecting my stdout/stdin to nodes

```
Atm ./mypogram is replaced with cat because i don't have myprogram yet.

Second problem is that i don't know what to do with redirected output/input in myprogram. I supposed 
```
./myprogram < /tmp/console_output > /tmp/console_input 
``` that this will work with any code, but I was wrong.

---

### Post by benj1 on 2009-07-02
i have read your posts, they just aren't very clear (to me at least)

if they are just command line options then just use
'GAME options > tmp/console_output' in your program simply wrap that in a system command, then you can open console_output to read the output.

if you need to send continuous data to your program (ie more data after you have started it) you will need to use a pipe, for c you will need to read up on it (i provided a link on my previous post).
for bash get a bash guide.

---

### Post by Uriziel on 2009-07-02
Ehh :P
tmp/console_input / console_output aren't normal files, they are nods
Using it i can get continuous data. Output is working w/o problems, its just my input that doesn't work. 
But nvm, I'll read about pipes.

---


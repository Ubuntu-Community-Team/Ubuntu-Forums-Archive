---
title: "Bash command to open a new terminal session and display results or actual actions."
date: 2008-04-19
forum: Programming Talk
---

### Post by Bruce M. on 2008-04-19
Xfce related for Xubuntu

Hi Folks,

How would I write in a "bash" command that would open a second terminal session (xfce4-terminal and/or xterm; if they are different) and display information in the second terminal not in the first.

**EDIT:**
My idea maybe wasn't clear enough in the original post:

I'm trying to write a bash script that will display results of commands in a second terminal so as not to mess up the the original terminal.

**EDIT: 2**
Can someone tell me which terminal is the "default" for Xubuntu
[LIST=1]
[*]xfce4-terminal; or
[*]xterm
[/LIST]
as both are installed by default on a clean install, but only xfce4-terminal shows up in the menus. Applications > Accessories > Terminal

From comments so far, up to post #15, people seem to be using *xterm* more.
**End EDIT 2**

For example

**ONE:**
 Type in a command - opens another terminal and displays all files in /media/sdb1/Documents/Book, keeping my original terminal clean except for the original command

**TWO:**
 Or if I want to copy a number of files: Chapter??.**~
From: /media/sdb1/Documents/Book
To: /media/sdb1/Documents/Book/old

  The command given would be in the 1st terminal, it would open a 2nd terminal and I'd see the "list of files being copied" as they were being copied.

**THREE:**
I have this bash file:
```
#!/bin/bash
find /media/sdb1/Documents/Book -mtime +14 -type f -delete
```

How can I rewrite that one to open a 2nd terminal and display the contents of what's there before and after the process, *before just for the practice*, I'm really interested in the "after" :)

Thanks Folks
Bruce

---

### Post by LaRoza on 2008-04-19
You want a traditional file manager.

Try mc (midnight commander)

It seems to have all you really want.

---

### Post by mdpalow on 2008-04-19
> **LaRoza said:**
> You want a traditional file manager.

Try mc (midnight commander)

It seems to have all you really want.

Don't understand what this has to do with the original question.

Using Ubuntu 7.10, one can open a terminal and put in a command followed by a ' -x '.

However, not sure what the command is for other terminals...

---

### Post by LaRoza on 2008-04-19
> **mdpalow said:**
> Don't understand what this has to do with the original question.


mc has two "windows" and a command line. One can have different directories open in each window, and use the command line separately.

---

### Post by Bruce M. on 2008-04-19
> **LaRoza said:**
> You want a traditional file manager.

Try mc (midnight commander)

It seems to have all you really want.

No, I want to do this with terminals. I already have a file manager., Thunar

---

### Post by LaRoza on 2008-04-19
> **Bruce M. said:**
> No, I want to do this with terminals. I already have a file manager., Thunar

mc runs in the terminal. [http://en.wikipedia.org/wiki/Midnight_Commander](http://en.wikipedia.org/wiki/Midnight_Commander)

(I use mc and thunar as my file managers)

---

### Post by ghostdog74 on 2008-04-19
eg 
```

xterm -hold  -e /bin/bash -l -c "ls"

```

---

### Post by mssever on 2008-04-19
You might also be interested in hotwire, available from getdeb.net.

---

### Post by jpkotta on 2008-04-19
```
xterm -e "ls ; sleep 2"
```
or maybe
```
xterm -e "ls | less"
```

---

### Post by Bruce M. on 2008-04-20
> **LaRoza said:**
> mc runs in the terminal. [http://en.wikipedia.org/wiki/Midnight_Commander](http://en.wikipedia.org/wiki/Midnight_Commander)

(I use mc and thunar as my file managers)

Hi LaRoza,

Not in line with what I was asking but I'm still going to check this out. Thanks for this.

My idea maybe wasn't clear enough in the original post:

I'm trying to write a bash script that will display results of commands in a second terminal so as not to mess up the the original terminal.

Now I have another dot on my ToDo list:

[LIST]
[*]Check out Midnight Commander.
[/LIST]

Have a nice day,
Bruce

---

### Post by ghostdog74 on 2008-04-20
> **Bruce M. said:**
> 

I'm trying to write a bash script that will display results of commands in a second terminal so as not to mess up the the original terminal.

have you tried those xterm methods?

---

### Post by Bruce M. on 2008-04-20
> **ghostdog74 said:**
> eg 
```

xterm -hold  -e /bin/bash -l -c "ls"

```

First: Is the double spacing between -hold and -e critical? From things I've read "spacing is critical.  cd .. is NOT cd..  :confused:

I checked out xterms "man page" and "xterm -help" page: (have them as a txt files here to help me in my quest.)

I found:

-hold
```
       -hold   Turn  on  the  hold  resource, i.e., xterm will not immediately
               destroy its window when the shell command completes.   It  will
               wait  until you use the window manager to destroy/kill the win&#8208;
               dow, or if you use the menu entries that send a  signal,  e.g.,
               HUP or KILL.
```
I take it that's what keeps the second terminal open forever until manually closed. Perfect!  Thanks.

-e
```
       -e program [ arguments ... ]
               This option specifies the program (and its command  line  argu&#8208;
               ments)  to be run in the xterm window.  It also sets the window
               title and icon name to be the basename  of  the  program  being
               executed  if  neither  -T nor -n are given on the command line.
               This must be the last option on the command line.
```
Hmmm ... "This must be the last option on the command line." but you use it in the middle?  I'm :confused: here

next comes */bin/bash* What does this do exactly?
So I went looking again:
```
               If you do want the effect of -ls and -e simultaneously, you may
               get away with something like
                      xterm -e /bin/bash -l -c "my command here"
```
Again it is using **-e** in the middle of stuff.  :confused: And there's that **-c**

-c **-->** I can't find this command, what I do find is:
```
       -C      This  option  indicates that this window should receive console
               output.  This is not supported on all systems.  To obtain  con&#8208;
               sole  output,  you must be the owner of the console device, and
               you must have read and write permission for  it.   If  you  are
               running  X under xdm on the console screen you may need to have
               the session startup and reset programs  explicitly  change  the
               ownership  of the console device in order to get this option to
               work.
```
That "seems" to be what -c should do looking at the script, but I thought all command were case sensitive. :confused: ahhhhhhh!

and of course "ls" this I knew.

So I try:```
xterm ls
```which of course "blinks" an xterm window with the info (I already knew this part and that's one of the reasons for the question.  :)

Now I try```
xterm -hold ls
```and it did everything that your command did.

Why do I need the other stuff?

Thanks a million for your input.
Have a nice day
Bruce

---

### Post by ghostdog74 on 2008-04-20
> **Bruce M. said:**
> 
Why do I need the other stuff?

Thanks a million for your input.
Have a nice day
Bruce
if it does the job for you, then fine. The one I posted is direct example from the man page. :)

---

### Post by Bruce M. on 2008-04-20
> **mdpalow said:**
> Don't understand what this has to do with the original question.

Using Ubuntu 7.10, one can open a terminal and put in a command followed by a ' -x '.

However, not sure what the command is for other terminals...

Oopps, missed this sorry...

Can't find that in the man or help pages for xterm.

However in Xfce4-terminal yes:```
  -x, --execute                       Execute the remainder of the command
                                      line inside the terminal
```is there. hmmmmm: --execute, can't find an "execute" command in xterm

:confused: this is going to be worse than I though.

**Different terminals = different commands**

For example```
xfce4-terminal ls
```gives me```
bruloo@bruloo:~$ xfce4-terminal ls
Unknown option "ls"
Usage: Terminal [OPTION...]

```with the help page. And ```
xfce4 -hold ls
```gives the same results.

Ghostdog74's command reaps the same thing with xfce4-terminal```
xfce4-terminal -hold  -e /bin/bash -l -c "ls"
```However opening an *xfce4-terminal* and putting in```
xterm -hold  -e /bin/bash -l -c "ls"
```works fine.

:confused: :confused:

---

### Post by Bruce M. on 2008-04-20
> **ghostdog74 said:**
> if it does the job for you, then fine. The one I posted is direct example from the man page. :)

Yes, I see that now, but missed it before.
Still it's confusing that I can do the same thing with a much simpler command:```
xterm -hold ls
```

Again, thanks for the input.  :)
Have a GREAT day
Bruce

---

### Post by Bruce M. on 2008-04-20
> **jpkotta said:**
> ```
xterm -e "ls ; sleep 2"
```
or maybe
```
xterm -e "ls | less"
```

WoW!  now those are good, especially the "ls | less" one.

OK, not with xfce4-terminal though.
```
xfce4-terminal -e "ls ; sleep 2"
xfce4-terminal -e "ls | less"
```
neither work.

I'm getting the impression that *xfce4-terminal* isn't as good as *xterm*.

GRACIAS! Thank you.
Have a great day
Bruce

---

### Post by jpkotta on 2008-04-20
> **Bruce M. said:**
> 
I'm getting the impression that *xfce4-terminal* isn't as good as *xterm*.


I've had that impression too.  xterm is just about guaranteed to be installed on anything with an X server.  Also, many terminals attempt to be more or less compatible with xterm.  Personally, I use rxvt-unicode.

You can get a short description of what xfce4-terminal's options are with ```
xfce4-terminal --help
```  xterm's -hold apparently is --hold in xfce4-terminal.  It doesn't work for me either.

Everything after the -e is interpreted as a command for the terminal.  However, things like ';' and '|' are command separators in the shell, so they will be interpreted by the shell you're using to launch the terminal, unless you quote them.  These things always get tricky, because you have to keep in mind what each program (shell, terminal, command that you're trying to run) is interpreting and how it modifies the command string as it gets passed to subsequent programs.

---

### Post by Bruce M. on 2008-04-20
> **jpkotta said:**
> I've had that impression too.  xterm is just about guaranteed to be installed on anything with an X server.  Also, many terminals attempt to be more or less compatible with xterm.  Personally, I use rxvt-unicode.

Really, I didn't know that.
So Ubuntu and Kubuntu have xterm as well as Xubuntu?

> **jpkotta said:**
> You can get a short description of what xfce4-terminal's options are with ```
xfce4-terminal --help
```  xterm's -hold apparently is --hold in xfce4-terminal.  It doesn't work for me either.

Yea, I have the man pages and help pages for both xterm and xfce4-terminal in a hard txt file  :)

Comes in handy when trying to figure things out.

> **jpkotta said:**
> Everything after the -e is interpreted as a command for the terminal.  However, things like ';' and '|' are command separators in the shell, so they will be interpreted by the shell you're using to launch the terminal, unless you quote them.  These things always get tricky, because you have to keep in mind what each program (shell, terminal, command that you're trying to run) is interpreting and how it modifies the command string as it gets passed to subsequent programs.

OK! CURVE BALL HERE!

I've learned here that terminal commands differ between programs.

Now you toss "shell" into the pot.
OK, officially lost again.

Shell?

{sigh}
Bruce

---

### Post by jpkotta on 2008-04-20
The shell, in a broad sense, is the user interface to the computer, the way the user interacts (indirectly) with the kernel (I think the terminology comes from plant seeds, where a kernel is surrounded by a protective shell).  Usually, when people talk about shells, they refer to text-based command interpreters like Bash.  

A terminal is basically a program to type text into and have text displayed.  It goes back to the days when everyone used the same large shared computer, and accessed it through simple devices called terminals.  Terminals were not much more than a CRT and a keyboard.  Further back, they were keyboards and printers, known as teletypes (TTY).  This is why there are a ton of tty device nodes in your /dev directory.  Strictly, xterm and similar programs are terminal emulators, because they emulate in software what was once a piece of hardware.

The shell is the program that takes in commands, launches programs, controls the flow of the commands' output, and so forth.  The terminal is the program that displays the output and sends input to the shell.  There is no need for the shell to be connected to a terminal (e.g. a script run by a cron daemon), likewise there is no reason why a terminal must get its input and send its output to a shell (e.g. the problem at hand).  

To further complicate things, there is also a console, but for most practical purposes this is equivalent to a terminal.

[http://en.wikipedia.org/wiki/Shell_(computing](http://en.wikipedia.org/wiki/Shell_(computing))
[http://en.wikipedia.org/wiki/Terminal_emulator](http://en.wikipedia.org/wiki/Terminal_emulator)
[http://en.wikipedia.org/wiki/Computer_terminal](http://en.wikipedia.org/wiki/Computer_terminal)

---

### Post by mssever on 2008-04-20
I don't know if I explained myself well enough earlier when I recommended that you check out hotwire. It's a combination shell/terminal that displays the output of many commands in a separate window automatically. Results of other commands are kept in a history mechanism. I've just played with it a little recently. It looks like an interesting idea, though I know bash and gnome-terminal well enough that I don't know if it's worth learning something different. But you might like it.


If you already decided it wasn't for you, my apologies for bringing it up again.

---

### Post by Bruce M. on 2008-04-21
> **mssever said:**
> You might also be interested in hotwire, available from getdeb.net.

Sorry for not responding to this post. I'm relatively new to Linux, Ubuntu is my first kick at the can, Most of my beans come from asking questions and helping people with "conky".

Step outside of conky and I'm still a green bean here. I have promised myself if it's not in the Ubuntu repositories I'm not going to play with it's until I get more accustomed to Linux. I saw the getdeb.net and said: "No, not yet, have no idea what he's talking about." But forgot to respond.

> **mssever said:**
> I don't know if I explained myself well enough earlier when I recommended that you check out hotwire. It's a combination shell/terminal that displays the output of many commands in a separate window automatically. Results of other commands are kept in a history mechanism. I've just played with it a little recently. It looks like an interesting idea, though I know bash and gnome-terminal well enough that I don't know if it's worth learning something different. But you might like it.

However, now that I see this I have yet another dot on my todo list.
I'll check out out ... later.  Thanks for the tip.

> **mssever said:**
> If you already decided it wasn't for you, my apologies for bringing it up again.

No, as seen above, just didn't know what it was.
Thanks
Bruce

---

### Post by skarthik on 2010-11-14
Hi all.... 
I am also in same type of requirement
I have a c program with a parent and child created using fork() and both do different actions. I want to display the printf statement outputs of two processes in two different terminals. So i tried to open a new terminal using gnome-terminal sing system call. It opens a new terminal but the control is not transferred to new terminal
Meanwhile i tried the xterm commands listed in this thread but am unable to get what i need
What i want to implement is as follows

int main()
{
   ....
   ....

   pid=fork();
   if(pid==0)//child
  {
     system("COMMAND");  /*COMMAND is command needed to open a new window and display further printf outputs and get fiurther inputs needed by child here after, with parent retaining its control in parent terminal and that should do parent input and outputs in tat parent terminal */
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


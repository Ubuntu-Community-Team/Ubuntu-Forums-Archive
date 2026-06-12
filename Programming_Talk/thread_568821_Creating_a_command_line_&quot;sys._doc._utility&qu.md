---
title: "Creating a command line &quot;sys. doc. utility&quot;. Want to discuss design and impl."
date: 2007-10-06
forum: Programming Talk
---

### Post by kentl on 2007-10-06
Hi,

I want to create a logging utility which I'll use to remember what I've done to my system. I want to be able to enable and disable logging as well as storing meta information in my log file. I have a vision of how the utility would work, and even some thoughts about the design and implementation. Still, I want to discuss this with you, my fellows, to get the best system possible as I am still quite new to Linux.

An example command line history from using my fictual logging system
```
> log on
> log comment Deleting all foobar files and creating some bar-files
> rm foobar*.txt
> vim bar1.txt
> vim bar2.txt
> vim bar3.txt
> log comment Change bar1.txt to simply say 'Hello logging'
> vim bar1.txt
> log comment A new revelation is making me change bar2.txt
> vim bar2.txt
> log comment The second line of bar3.txt is making me annoyed, it must go!
> vim bar3.txt
> log off

```

And this is how the log file would look
```
Deleting all foobar files and creating some bar-files
  action: removed 'foobar1.txt', 'foobar2.txt' and 'foobar3.txt'
  command: rm foobar*.txt
  action: Created a text file named 'bar1.txt' with the contents
    This is the only line in bar1.txt
  command: vim bar1.txt
  action: Created a text file named 'bar2.txt' with the contents
    In bar2.txt I felt it
    was a good decision to
    have three lines
  command: vim bar2.txt
  action: Created a text file named 'bar3.txt' with the contents
    Two lines
    are enough
  command: vim bar3.txt
Change bar1.txt to simply say 'Hello logging'
  action: Changed line 1 from 'This is the only line in bar1.txt' to 'Hello logging'
  command: vim bar1.txt
A new revelation is making me change bar2.txt
  action: Changed bar2.txt according to this diff
    2c2
    < was a good decision to
    ---
    > was bad decision to
    3a4
    > so now i have four
  command: vim bar2.txt
The second line of bar3.txt is making me annoyed, it must go!
  action: Removed line 2, 'are enough', from bar3.txt
  command: vim bar3.txt

```

As you can see there is much more information in the log file than given by the command line history. This is done by my utility, which will have a rough design such as:
[LIST=1]
[*]log on
[*]# From now on logging is enabled
[*]The user has typed a command, for example rm bar*.txt, I want to intercept this command BEFORE it is executed
[*]I locate the file argument of the given command. In this case bar*.txt.
[*]I expand this to be a list of all the files to be sent as an argument to the command in question (in our example it was rm), we can call it FILELIST. For example I might get {bar1.txt, bar2.txt, bar3.txt}
[*]For each item in FILELIST I check if the file exists already, in which case I store a temporary copy of it.
[*]Now I let the command execute, in our example it was rm bar*.txt which deletes {bar1.txt, bar2.txt, bar3.txt}
[*]I intercept again! First I store the exit status of the rm command.
[*]Then I check if the files in FILELIST have changed. In our example they have been removed. This is enough meta information to store an "intelligent" action description, which I do store. *******
[*]I remove the temporary copies of the files which was affected.
[*]I return the exit status of the given command, in our case it was rm
[*] log off
[*] # Now logging is disabled. This was a simple design example, I could have done more things than just executing one rm command. But then it would have been harder to understand too, right? :-)
[/LIST]
******* In the case of simple edits to the file. I write it out using a human readable format. If the edit is more complex then changing lines I store the result of diff.

I have some initial questions to get our discussion started:
[LIST=1]
[*]Is there already something like this?
[*]If your anser to [1] is to save Bash history I might have failed to communicate what this utility does. In which case I could explain more.
[*]Would you find something like this useful? Why or why not?
[*]Are there hooks or something I can use to let me intercept Bash before AND after a command has executed?
[*]Is there a context free grammar for how command arguments in Linux are laid out? So that I may create a parser which extracts the file arguments from "any" command.
[*]If there is no such standard. I might get away by identifing hard coded commands using regular expressions. And extract the file arguments that way. What do you think about that way?
[*]When I've found a commands file argument. How do I expand it to the list of files it matches. Like in the example above where bar*.txt matched three files.
[*]If there is no hooking way. Perhaps I should design my logging system to be used like: log <my log option> <command> <command options>. What do you think of that way? Should I go for this way even if there is a hooking way?
[/LIST]

Thanks for reading! Let's start the discussion! :)

---

### Post by slavik on 2007-10-06
I think that certain parts are going to be difficult. Like for example catching created files and such.

Also, it seems like your logging utility will have to process all the commands, iow, become like a shell.

---

### Post by kentl on 2007-10-06
I only want something to document my installations and configurations. I think it will be sufficient to log:
[LIST=1]
[*]touch -- for creating new empty files
[*]apt-get install, to note which packages I need to install
[*]apt-get remove, to note which packages I remove
[*]vim/emacs/nano etc, to keep track of text file changes
[*]cp, for when I need to copy files
[*]mv, for when I need to move files
[/LIST]
I could skip the hooks part and use it like:
```
> log comment This is my comment
> log apt-get install openssh
> log vim ~/ssh/bogusconfigfile.txt

```
In which case I could hard code the 6 different operations above. If I need to do something else not covered by the 6 operations I could use comments:
```

# Used xwindows configuration tool named foo to set bar to true

```
Do you see any problems with this system?

---

### Post by cwaldbieser on 2007-10-07
I kind of like your original example, but I agree that some of what you proposed seemed like you would need to recreate a shell to evaluate commands, globbing, etc.

What I found appealing was the fact that you could kind of document what you were doing as you did it.  When I write programs at work, I have a personal SVN repository set up so I can constantly commit changes so I can keep track of what I am doing.  I get interrupted so many times during the day, it is really useful when I can go back and scan the log and say-- "Oh, yeah, that's where I left off and what I was doing!"

I thought your idea of the ability to add comments to your history was neat.  I would also find a timestamp in the output useful so you could see when you issued each command.

I think trying to get the program to determine exactly what evey other program that runs is doing might be a bit difficult, even if it is for just a handful of programs.  I think you could probably have options to capture the command line, some fraction of the standard output / standard error, and the command return status, and combined with the annotations that would be sufficient.

It would be similar to the "script" program on steroids.

---

### Post by #Reistlehr- on 2007-10-07
Basically what you just said is everything that SVN (Subversion) does, only without the seperate revision numbers. 

Possibly check out SVN and see what you can use from that to create a log, minus the revision module.

One of my favorite functions is, SVN allows you do view the difference between two files with a function called syncronize, so something like this might sound like an idea you can embelish.

---

### Post by kentl on 2007-10-08
cwaldbieser:

If I match specific commands using regular expressions then I won't have to create a whole shell. As soon as I extract the file pattern I could use the glob() function to unfold it into the list of files affected.

Perhaps I should write this in C, C++ or maybe Python instead of Bash. The only thing which keeps me from being able to implement it right now is that I need hooks to interecept the command before and after execution by Bash. Perhaps it's possible too? (I'm pretty new to Linux.)

Reistlehr:

I'm not very good at SVN. I've only used it through TurtleSVN on Windows.

Still, wouldn't I need to have pretty much all of my file system under version control? Where would those .trunc etc directories reside?

I actually think that for my problem the solution I'm thinking about so far fits pretty well. Only log a few commands, turn logging on and off as you please, be able to insert comments, everything is stored in one plain text file.

---

### Post by cwaldbieser on 2007-10-08
> **kentl said:**
> cwaldbieser:

If I match specific commands using regular expressions then I won't have to create a whole shell. As soon as I extract the file pattern I could use the glob() function to unfold it into the list of files affected.
.
Maybe you could just create aliases or bash functions to wrap the existing commands.  Then you could embed before and after hooks in the functions.

---

### Post by kentl on 2007-10-09
I've been up that branch, using alias, that might be sufficient for what I want to do. Do you have any ideas on how I would make the alias affect both the normal user running the log script, and the root user in case i need to sudo some commands (which I will need).

Bash functions, new to me. :-) (But a lot of things are new to me.) They're just syntatic sugar so that I'm able to structure my code better, right? That is, there is no way I could create a function called "vim" and make it precede the actual vim command using some Bash stuff? (Without using alias that is)

---

### Post by SeanHodges on 2007-10-09
I'd suggest writing a little script that could run as a daemon (background process, launch it using something like "./logging.sh&" - you could even alias it to "log on"

The script should continuously read the tail of the "history" command, format the text that comes in, and write it to a log file.

One option, anyway.

---

### Post by kentl on 2007-10-09
Seems like an interesting solution. I'll look into it!

---

### Post by cwaldbieser on 2007-10-09
> **kentl said:**
> I've been up that branch, using alias, that might be sufficient for what I want to do. Do you have any ideas on how I would make the alias affect both the normal user running the log script, and the root user in case i need to sudo some commands (which I will need).

Bash functions, new to me. :-) (But a lot of things are new to me.) They're just syntatic sugar so that I'm able to structure my code better, right? That is, there is no way I could create a function called "vim" and make it precede the actual vim command using some Bash stuff? (Without using alias that is)

```

$ function cat { echo $# args; /bin/cat $@; }

```
You can actually use bash functions similar to aliases, but you can use parameters in them, too.  It would be similar to making your own version of cat that appeared earlier in the PATH and called the original cat.

---


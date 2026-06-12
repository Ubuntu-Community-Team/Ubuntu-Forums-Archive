---
title: "[SOLVED] echo $0 returns bash, not script name"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by deepspacesolitude on 2008-11-29
Hi,

I am using O'Reilly's learning the bash shell on an Ubuntu 8.04 machine, and am working through the example in chapter four, a script, or function, called alice.

function alice
{
 echo "alice: $@"
 echo "$0: $1 $2 $3 $4"
 echo "$# arguments"
}

I have tried changing this in many ways, putting it in .bash_profile, as a file called alice, with and without the function alice{} part,

and essentially, echo $0 gives me bash, instead of alice.

I found something i didn't understand in a forum about whether the function was sourced, or executed. this is the difference between
alice in wonderland 
or
./alice in wonderland

no?

thanks ahead of time for your help.

Joseph

---

### Post by jgoguen on 2008-11-30
If the function is sourced, and called from the shell, then $0 is (correctly) set to "bash".  There's four scenarios I can think of, with these results


[LIST]
[*]As a function in a script, called from a script (./test): $0 is the path to my script file (./test)
[*]A script contains the function code, but does not define a function (./test2): Same as above, $0 is the path to the script (./test2)
[*]The function is in a file sourced with ". /path/to/script" and called from the shell(. test3.sh; alice "One" "Two" "Three" "Four"): $0 is set to "bash" (or the name of your shell)
[*]The function is in a file or script sourced by and called from a second script (alice.sh is sourced by ./test4): $0 is the path to the second script (./test4)
[/LIST]
Not sure what the O'Reilly tutorial says, but this is how Bash handles it in at least version 3 (check your version with 'bash --version').

---

### Post by deepspacesolitude on 2008-11-30
thanks for answering my question. I still don't feel i understand this very well, but it seems that there may be a mistake in the book I have. the book is for bash 3.0, and bash --version = GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu) Copyright (C) 2007 Free Software Foundation, Inc.

to precisely define my confusion, if I create a file called example, that contains only the statement: echo "$0"

enter: chmod +x example

and enter:

  example  
  bash: example: command not found

  source example
  bash

  ./example
  ./example

these are the results I get. this contradicts the book in that the book implies that this simple shell script should respond to entering

example

with

example

There may be an issue here that I don't understand correctly, but in the end, why doesn't ./example get me example?

and in what situation (can you give me an example) echo "$0" return just the name of the script? ( or function?)

Thanks again,
Joseph

---

### Post by jgoguen on 2008-11-30
Entering "example" alone won't do it.  Explanation below.  The book should be telling you to run "./example".  That means "run the executable file named example in this directory".  If the book isn't telling you that, then it's an error with the book.  There's usually a way to report errors like that to the author, but I'm not sure where you'd find that information.  Probably near the beginning, before the actual content.

Now, the reason that you can't just type "example" is because it's not on your path.  To see you path, type "echo $PATH" at the prompt.  You'll see a list of directories separated by colons.  When you type a command without "./", the shell will look through each of those directories, in order, to try and find the file you specified.  If it finds the file on the path, then it runs it.  If not, you get the error you saw.  If you run it the way I said to above, you should see the script print "./example".  While you can add directories to your path, adding "." (a special directory name that always means "the directory I'm in right now") is a bad idea.  Security risks abound.

---

### Post by deepspacesolitude on 2008-11-30
thank you so much for helping here. I think I understand much more clearly now. In the preceeding chapter the author suggests I add to PATH in this way:

PATH=$PATH":/home/you/bin" (as opposed to PATH="/home/you/bin:"$PATH , for security reasons)

I had not yet done so. Having made the suggested change, (this computer is solely dedicated to my self education in linux) and having moved the script to home/me/bin, I am able to run it without the antecedent "./"

However, the result of echo "$0" in this case is: /home/myname/bin/example

and not just example.  this is much closer to making sense, and i think i understand why adding "." to path would make it work, and i *think* i get why this is a horrible idea, but i still fail to see how the author might expect 

example 
 to return
example 

unless it were in the root folder? maybe???

---

### Post by jgoguen on 2008-12-01
$0 isn't just "name of the program or script", it's actually "how I was called".  It's set by the shell when it executes anything.  For compiled programs, where the shell executes it, the shell actually sets $0 (and if you get into C programming, you'll learn how to set $0 for programs you execute from yours) but that's not how Bash runs shell scripts.  Bash finds "example" on your path and runs the full path it constructs.  So for shell scripts, with no way I know of to set $0, the value of "how I was called" ($0) turns into the full path to the script.

You may have seen that running certain programs (notably SSHd) requires running them with a full path rather than just the command.  This is how it knows whether it was run with a full path or not, cause the shell sets $0 to whatever you typed to run the program (compiled programs only remember).

Hope that's not too complicated.  Let me know if it is, I'll try and clear it up.

---

### Post by deepspacesolitude on 2008-12-01
it makes perfect sense now. I will be checking O'Reilly's errata on the book, and possibly contacting them. 

thanks!

---


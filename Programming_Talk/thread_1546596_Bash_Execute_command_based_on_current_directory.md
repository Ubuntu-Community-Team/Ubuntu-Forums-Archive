---
title: "Bash: Execute command based on current directory?"
date: 2010-08-05
forum: Programming Talk
---

### Post by DigitalDingo on 2010-08-05
Hi everyone!

I'm trying my hands on .bashrc, and I have run into a small problem.

I want to make an alias of a command if, and only if, the command is executed in a particular directory.

Is this possible?

---

### Post by DaithiF on 2010-08-05
Hi, not sure why you might want this, but something like:
```
alias onlyinhome='[[ "$PWD" == "/home/you" ]] && echo somecommand'

```

---

### Post by conundrumx on 2010-08-05
Maybe.

If you create a function in your bashrc:
```
function() {
if pwd = "/foo/bar" ; then
    alias cmd="othercmd"
else 
    alias cmd="otherothercmd"
fi
}
```

And alias that function to the command you want to check, it'll change the alias when executed.  To check every single time, you'd have to actually not use aliases, but instead pass the arguments the function was invoked with to the command, which the function would decide on based on pwd.

---

### Post by DigitalDingo on 2010-08-06
> **DaithiF said:**
> Hi, not sure why you might want this, but something like:
```
alias onlyinhome='[[ "$PWD" == "/home/you" ]] && echo somecommand'

```

Thanks! This works exactly like I wanted! The reason I want this is that I want to alias the command 'latex' so that in a specific directory it also executes a small home-made script to make some statistics about the document.

> **conundrumx said:**
> Maybe.

If you create a function in your bashrc:
```
function() {
if pwd = "/foo/bar" ; then
    alias cmd="othercmd"
else 
    alias cmd="otherothercmd"
fi
}
```

And alias that function to the command you want to check, it'll change the alias when executed.  To check every single time, you'd have to actually not use aliases, but instead pass the arguments the function was invoked with to the command, which the function would decide on based on pwd.
Thanks for your answer, but I can't seem get this to work. Should I be able to execute the following by writing 'test' in a terminal, or should I make an alias to it? Either way it doesn't seem to be working.
```
function test() {
	if [ pwd = "/foo/bar" ] ; then
		alias ls='echo "Lalalala!!"'
	else
		alias ls='ls'
	fi
}

```

---

### Post by conundrumx on 2010-08-06
You don't need "function test() {" just "function() {".  Here's an example from my .profile of a working function.

```
psgrep() {
	if [ ! -z $1 ] ; then
		echo "Grepping for processes matching $1..."
		ps aux | grep $1 | grep -v grep
	else
		echo "Nothing to grep for."
	fi
}
```

Now, when I type "psgrep" the function is invoked.

---

### Post by DaithiF on 2010-08-06
> **conundrumx said:**
> You don't need "function test() {" just "function() {".  Here's an example from my .profile of a working function.

```
psgrep() {
    if [ ! -z $1 ] ; then
        echo "Grepping for processes matching $1..."
        ps aux | grep $1 | grep -v grep
    else
        echo "Nothing to grep for."
    fi
}
```Now, when I type "psgrep" the function is invoked.

not really relevant to this thread, but you know there is a '**pgrep**' command that does exactly this?  :)

---

### Post by conundrumx on 2010-08-06
> **DaithiF said:**
> not really relevant to this thread, but you know there is a '**pgrep**' command that does exactly this?  :)

On Linux.  :)

[i]And FreeBSD...

Looks like pgrep has been around since 1998, no idea why it isn't included in OSX.  Maybe I should change my function name and throw the poor man's pgrep under OSX specific stuff.  :p[/i]

---


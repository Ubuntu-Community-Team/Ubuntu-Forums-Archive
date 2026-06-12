---
title: "Alias setting"
date: 2010-05-12
forum: Programming Talk
---

### Post by huangyingw on 2010-05-12
Hello all,
	As a lazy man, I have tried to update my /root/.bashrc file with this line:
	```

	alias	gcb='git clone --bare "." "$1" && git remote add origin "$1"'
	
```
	My expected result is like following shorter command:
	```

	gcb /media/smb/myproject/demo
	
```
	After this command the git clone and remote add could be done at the same time.
	While the actual output is like bellowing:
	```

	Reinitialized existing Git repository in /media/volgrp/myproject/git/demo//
	error: refs/heads/master does not point to a valid object!
	fatal: remote origin already exists.
	
```

---

### Post by MadCow108 on 2010-05-12
when evaluating aliases it expands variables when executing the bashrc when starting bash
so $1 will be whatever it is at that time and not what it is when you execute the alias

solution I know to that is to alias to a little wrapper script which takes the $1 and executes the command

---

### Post by diesch on 2010-05-12
Use a function instead of an alias:

gcb(){
 git clone --bare "." "$1" && git remote add origin "$1"
}

---

### Post by huangyingw on 2010-05-16
> **diesch said:**
> Use a function instead of an alias:

gcb(){
 git clone --bare "." "$1" && git remote add origin "$1"
}
Seems that your solution will still get the same error as mine.
"the $1 will point to somehow curious place":(

---

### Post by huangyingw on 2010-05-16
> **MadCow108 said:**
> when evaluating aliases it expands variables when executing the bashrc when starting bash
so $1 will be whatever it is at that time and not what it is when you execute the alias

solution I know to that is to alias to a little wrapper script which takes the $1 and executes the command
thanks. My understanding of your solution is that 
```

alias	gcb='/root/gcb.sh'

```
And this indeed works, and save me a lot of time.

---

### Post by slavik on 2010-05-16
use .bash_aliases instead of .bashrc?

---

### Post by gmargo on 2010-05-16
> **huangyingw said:**
> 
> 
                                                                      Originally Posted by **diesch**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9288282#post9288282")                 
                 [I]Use a function instead of an alias:

gcb(){
 git clone --bare "." "$1" && git remote add origin "$1"
}[/I]
Seems that your solution will still get the same error as mine.
"the $1 will point to somehow curious place":(

It "seems" that way?  You didn't bother to try it or read the documentation. The basic difference is:

Bash aliases **do not** accept arguments.
Bash functions **do** accept arguments.

---

### Post by huangyingw on 2010-05-21
> **gmargo said:**
> It "seems" that way?  You didn't bother to try it or read the documentation. The basic difference is:

Bash aliases **do not** accept arguments.
Bash functions **do** accept arguments.
Sorry, the last days I am busy with moving...
This time, my use of function works:)
Indeed I have a rough try last time, and fail, but, I could not repro it now:(.
I remember that, last time, when using function, the parameter passed to function, is not the one I input or expect. However, I could not repro it now.

---


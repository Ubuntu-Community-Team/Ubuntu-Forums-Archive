---
title: "Executing function before every cd"
date: 2009-11-05
forum: Programming Talk
---

### Post by silentrebel on 2009-11-05
I'm trying to find some sort of back function for working in a terminal.  For instance, if you are in directory 'a', and then cd to directory 'b' you can use this function (I chose 'cd,') to return to directory 'a'.  I looked and could neither find an environment variable that stored the location of the last directory, nor any built-in back function.  So, I decided to make one (let me know if you know of such an environment variable or function...)

I added 
```
. cdmod
```
to my .bashrc.

cdmod:
```
#!/bin/ksh
prevPath=

#this is the part where I get lost
<whenever directory is going to be changed> 
	prevPath=`pwd`
	prevPath=`true_path $prevPath`
	cd <new directory>
#in the clear again 

alias "cd,"="cd $prevPath"
```

So how would you go on about doing this?  

On a more humourous note, I tried using this overriding function:
```
function cd
{
	prevPath=`pwd`
	prevPath=`true_path $prevPath`
	cd $1
}
```

Quite logically, it recursed infinitely... I did not think, for some reason, that the 'cd' inside the new 'cd' function would call the new 'cd' and not the old one...
Any ideas or hints are greatly appreciated.
Note: I know how to do this with a name other than 'cd'.  My goal is to keep 'cd' as the name as it is so recognised.

---

### Post by MindSz on 2009-11-05
How about: ```
$cd -
```

I think that takes u back to the previous directory

---

### Post by silentrebel on 2009-11-05
That works splendidly!  Thanks MindSz... How delicious...  
Okay, well for programming's sake, does anyone know how to run a function whenever another is called?

---

### Post by dwhitney67 on 2009-11-05
> **silentrebel said:**
> That works splendidly!  Thanks MindSz... How delicious...  
Okay, well for programming's sake, does anyone know how to run a function whenever another is called?

There's also pushd and popd.

For calling a function within another function, that's easy.

```

#!/bin/bash

function One()
{
   ls
}

function Two()
{
   One
}

```
You can also place your function definitions within ~/.bashrc.

---

### Post by johnl on 2009-11-05
I usually add the following in my .bashrc:

```

cdls() {
    \cd "$*"
    RESULT=$?
    if [ "$RESULT" -eq 0 ]; then
        ls
    fi
}

alias cd='cdls'

```

Which will list the contents of a directory every time you (successfully) change directories.   You could use a similar method to do something whenever you 'cd'.

---

### Post by silentrebel on 2009-11-05
That is exactly what I was looking for, johnl ! Thank you very much...
What is it called when you do \cd?
What does it do, exactly?

---

### Post by johnl on 2009-11-05
\cd means use the bash builtin 'cd' command, not any alias or external command.  The reason for this is that if we don't use it, and the function cdls() is evaluated again after we alias 'cd' to be 'cdls' (for example, if you type 'source ~/.bashrc' to reload the .bashrc), it will evaluate to this:

```

cdls() {
  cd "$*" # this is going to call cdls() again.
  # rest of code 
}

```

which is going to recurse forever :)

---

### Post by silentrebel on 2009-11-05
Thanks great...  Thanks for the explanation.

---

### Post by eightmillion on 2009-11-05
I'm surprised that no one has pointed out that if you're aliasing shell builtins or writing functions for them, you can use the shell builtin, "builtin" to call the unaliased function.

silentrebel's example would be written like this to avoid an infinite recursion:
[PHP]function cd
{
	prevPath=`pwd`
	prevPath=`true_path $prevPath`
	builtin cd "$@"
}[/PHP]

The preceding backslash syntax works on the command line, but it doesn't work for functions.

---

### Post by silentrebel on 2009-11-06
Don't you just love it how it seems that everyone has already run into all the same problems as you and made beautiful, idiomatic and efficient solutions for them.
Thanks for the hint eightmillion... 
Does the builtin keyword work in all contexts then?  Would it be safer to adopt it rather than the backslash?

---

### Post by eightmillion on 2009-11-06
> **silentrebel said:**
> Don't you just love it how it seems that everyone has already run into all the same problems as you and made beautiful, idiomatic and efficient solutions for them.
Thanks for the hint eightmillion... 
Does the builtin keyword work in all contexts then?  Would it be safer to adopt it rather than the backslash?

No problem. I wouldn't say either one was inherently better than the other. They just have different uses. The backslash is great for entering a command on the command line and it even has limited use in aliases, but it doesn't work in functions, whereas "builtin" does. That's all you have to remember.

---


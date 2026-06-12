---
title: "User input in .bashrc file"
date: 2012-01-06
forum: Programming Talk
---

### Post by thedemon13666 on 2012-01-06
Hi

I currently have a bit of a problem with my .bashrc file.  I am trying to make an alias so when I am compiling C++ code with root I dont have to type out a massive line of text, here is what I normally type:

```
g++ "program name" `root-config --cflags llibs`
```


Now I have tried to make an alias such as:

```
alias gr='g++ `root-config --cflags --libs`'
```


The problem is when this is run, I have to place the program name AFTER all of the root-config stuff, and when that happens it fails to compile, so I need a way for bash to insert the program name inbetween g++ and `root-config....`

Thanks

---

### Post by ofnuts on 2012-01-06
> **thedemon13666 said:**
> Hi

I currently have a bit of a problem with my .bashrc file.  I am trying to make an alias so when I am compiling C++ code with root I dont have to type out a massive line of text, here is what I normally type:

```
g++ "program name" `root-config --cflags llibs`
```
Now I have tried to make an alias such as:

```
alias gr='g++ `root-config --cflags --libs`'
```
The problem is when this is run, I have to place the program name AFTER all of the root-config stuff, and when that happens it fails to compile, so I need a way for bash to insert the program name inbetween g++ and `root-config....`

ThanksWrite a script... aliases aren't meant to resolve all problems.

---

### Post by Grenage on 2012-01-06
I don't believe that aliases can have parameter substitution, but a basic script would do what you want.

---

### Post by thedemon13666 on 2012-01-06
Attempting to do that now, however I am quite new to bash scripting,

Is there away for a bash script to take user input at the point it is run? i.e

./test.sh input

---

### Post by Grenage on 2012-01-06
> **thedemon13666 said:**
> Attempting to do that now, however I am quite new to bash scripting,

Is there away for a bash script to take user input at the point it is run? i.e

./test.sh input

Absolutely; there are some in-built variables for exactly that:

$0 is the script name
$1 is the first argument passed
$2 is the second argument passed
et ceteca

So in your example, $0 would be *test.sh*, and $1 would be *input*.

---

### Post by thedemon13666 on 2012-01-06
Ok here is what I have so far:

```

#!/bin/bash
echo "g++ $1 `root-config --cflags --libs`"

```I make it executable using chmod however when I run it passing a argument with it, it does not seem to work, 

I read somewhere that you use backticks to show that you are making bash run a shell command, however I need to use backticks for `root-config --cflags --libs`, 

Is it this that is causing me problems?


EDIT

Sorted it, I got around using the backticks by using $, if anyone would like a look here is my final code which seems to work:

```
echo $(g++ $1 `root-config --cflags --libs`)
```

I can now execute this whilst passing it an argument and it compiles fine.

Cheers

---

### Post by epicoder on 2012-01-06
Instead of making an alias, you can write a function. This can be placed in your .bashrc.
```
gr() {
g++ $1 $(root-config --cflags --libs)
}
```

---

### Post by Grenage on 2012-01-06
> **thedemon13666 said:**
> Ok here is what I have so far:

```

#!/bin/bash
echo "g++ $1 `root-config --cflags --libs`"

```

I make it executable using chmod however when I run it passing a argument with it, it does not seem to work, 

I read somewhere that you use backticks to show that you are making bash run a shell command, however I need to use backticks for `root-config --cflags --libs`, 

Is it this that is causing me problems?

I hate backticks, lol.  does the problem occur if used like so:
```

#!/bin/bash
echo $(g++ $1 `root-config --cflags --libs`)

```

Edit:

Ah you got there anyhow, and also have an even better solution from sh228.

---

### Post by nothingspecial on 2012-01-06
> **sh228 said:**
> Instead of making an alias, you can write a function. This can be placed in your .bashrc.
```
gr() {
g++ $1 $(root-config --cflags --libs)
}
```

```
$(commands)
``` is the preferred syntax for command substitution rather than ```
`commands`
``` 

See [here]("http://wiki.bash-hackers.org/syntax/expansion/cmdsubst#a_closer_look_at_the_two_forms") for an explanation.

---

### Post by Stovey on 2012-01-06
> **sh228 said:**
> Instead of making an alias, you can write a function. This can be placed in your .bashrc.

Would you kindly explain:

1. In this case, why would a function be preferable to a script?
2. Why would the function be defined in .bashrc rather than .profile?

I am a newbie and am trying to learn bash.  Thanks.

---

### Post by cgroza on 2012-01-06
> **Stovey said:**
> Would you kindly explain:

1. In this case, why would a function be preferable to a script?
2. Why would the function be defined in .bashrc rather than .profile?

I am a newbie and am trying to learn bash.  Thanks.
If you write your function into bashrc, you will be able to call it from anywhere.
If you make it a script, you will have to either refer to its location in the filesystem when calling it, or add its location to the $PATH.

---

### Post by gnometorule on 2012-01-06
> **Stovey said:**
> Would you kindly explain:

1. In this case, why would a function be preferable to a script?
2. Why would the function be defined in .bashrc rather than .profile?

I am a newbie and am trying to learn bash.  Thanks.

1. The comparison was not between a function and a script. A bash function (like the one suggested) is usually a bash script. It was between an alias (where you have trouble with parameters), and a script (where you don't).

2. Either would work, but it's more common to put it into your .bashrc file. Just have a look at the two files in your home directory. The advantage of putting it there over making it an executable script was detailed in the prior reply: you can then refer to it from within your bash sessions without any path reference.

---


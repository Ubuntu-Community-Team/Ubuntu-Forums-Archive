---
title: "Simple BASH question - how do I capture a command as a variable?"
date: 2008-04-04
forum: Programming Talk
---

### Post by altonbr on 2008-04-04
Right now I have a script in PHP that runs shell_script. I did this because my BASH skills weren't to great at the time. I've decided to convert it to BASH, but I'm already stuck between programming languages.

In PHP I have this:
```
$data .= shell_exec('find '.$folder.' -iname *.'.$ext);
```

How do I capture the above in a variable in BASH?

I've tried this so far, but no luck:
```
$DATA=`find $FOLDER -iname *.$EXT`
``` 

Is there a term for this sort of thing? Possibly I could have googled it.

---

### Post by Whiffle on 2008-04-04
Try removing the $ from in front of DATA.

---

### Post by altonbr on 2008-04-04
> **Whiffle said:**
> Try removing the $ from in front of DATA.

Huh, must be tired. I apologize.

While we're here, how would I explode the newly formed $DATA into an array? I read that you can use 'cut -d', but I'm unsure of how to write "new line" as only one character and not "\n".

Example:
$DATA="hello
joe
know"

$DATA{1}="hello"
$DATA{2}="joe"
$DATA{3}="know"

---

### Post by ghostdog74 on 2008-04-04
> **altonbr said:**
> I've tried this so far, but no luck:
```
$DATA=`find $FOLDER -iname *.$EXT`
``` 



normally you wouldn't want to do it like this (in bash/shell). The reason is because find may give you many lines of output. Unless you really want to store all these lines in $DATA, i would recommend piping your find results to while loop ( or other tools ) so you can process your data as it comes. Also, in PHP, you might want to find a way such that your code is not dependent on external shell programs to do your stuff. eg readdir()  ??

---

### Post by altonbr on 2008-04-04
> **ghostdog74 said:**
> normally you wouldn't want to do it like this (in bash/shell). The reason is because find may give you many lines of output. Unless you really want to store all these lines in $DATA, i would recommend piping your find results to while loop ( or other tools ) so you can process your data as it comes. Also, in PHP, you might want to find a way such that your code is not dependent on external shell programs to do your stuff. eg readdir()  ??

That's true, why not just use the data already in the loop instead of looping, collecting the data, exloding the data and then looping again. Rather silly.

As for the PHP with shell commands, that's because I'm sort of weak with Bash and I learned programming from a Web Dev. perspective so it was what I'm most comfortable with... I'm not converting it to BASH however, due to the same questions you raised.

---

### Post by nanotube on 2008-04-04
generally, if you want to learn better bash scripting, for future reference, see the advanced bash scripting guide:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

:)

---

### Post by altonbr on 2008-04-04
> **nanotube said:**
> generally, if you want to learn better bash scripting, for future reference, see the advanced bash scripting guide:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

:)


Thanks, but I've been referenced to that about 6 times already. I'm aware of it and use it often. I come here when I get really stuck...

---

### Post by stroyan on 2008-04-05
If you did want to put the output of a command into an array then assign to a variable with the output of the command inside of parenthesis.
To have the array elements delimited by newlines instead of white space set IFS to control the field separator.
You should be careful about quoting special characters like * so that bash does not expand them into file names before passing parameters on to commands like find.
I prefer the $(cmd) form instead of the older `cmd` form.  It is easier to seen and can be nested.
```

IFS=$'\n' DATA=( $(find . -iname \*.$EXT) )

```

---

### Post by ghostdog74 on 2008-04-05
> **stroyan said:**
> 
```

IFS=$'\n' DATA=( $(find . -iname \*.$EXT) )

```
am not sure where you got $ infront of $"\n" and $EXT, but this works though
```

IFS='\n' 
DATA=( $(find . -iname "*.EXT" ) )

```
also minor note for OP, a need to reset IFS thereafter (if IFS is going to be used again later )

---

### Post by stroyan on 2008-04-06
Ghostdog- 
Look for $' in 'man bash' under 'QUOTING'.  It handles the \n conversion.
The '$EXT' was in altonbr's original question.
It uses the value of the EXT variable instead of a literal 'EXT' pattern.

The single line form that I used was an attempt to have the IFS setting only apply to the DATA= assignment.
The 'SIMPLE COMMAND EXPANSION' section in 'man bash' notes how that works.
It is very handy for setting an environment variable for just one command.
Unfortunately, it does not work that way for the assignment.
So IFS does need to be reset.  Thanks for catching that.

---


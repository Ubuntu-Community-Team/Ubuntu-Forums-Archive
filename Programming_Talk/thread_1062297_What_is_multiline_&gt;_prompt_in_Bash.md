---
title: "What is multiline &gt; prompt in Bash?"
date: 2009-02-06
forum: Programming Talk
---

### Post by Backharlow on 2009-02-06
I am comfortable in Bash but one thing still baffles me...
If I type just \ at a Bash prompt, the new line changes my prompt handle from the normal user@machine:~$ to just the greater than symbol >. This looks like:
```

user@machine:~$ \
>

```
Then hitting enter will keep this strange prompt going.
```

>
>
>

```
like that.
If I execute any other normal process it then goes away, reverting back to my normal prompt:
```

> ls
(normal output of ls)
user@machine:~$

```
Question, what is this phenomenon and what is for?

---

### Post by apmcd47 on 2009-02-06
If you check the man page for bash you will find that there are four environment variables PS1, PS2, PS3 and PS4.

PS1 is your normal prompt. PS2 is for multi-line commands, eg
```
$ for i in *
> do
> echo $i
> done
$
```
PS3 is used for prompts with the select command, and PS4 is used for execution traces.

In my .bashrc I tend to set PS1 and PS2 to the same thing except for the trailing $/>.

Andrew

---

### Post by kaibob on 2009-02-06
> **apmcd47 said:**
> If you check the man page for bash you will find that there are four environment variables PS1, PS2, PS3 and PS4. PS1 is your normal prompt. PS2 is for multi-line commands, eg... 

Thanks apmcd47. I've encountered the same prompt and never understood its purpose.

---

### Post by Reiger on 2009-02-06
It also enables you to echo multiline strings in the shell.
```

echo '
line1
line2
done3
'

```

---

### Post by snova on 2009-02-06
The point is that you can split a command across more than one line.

Oddly enough, I can't reproduce this. If I type \, press enter, and press enter again, I get back to my normal prompt.

---

### Post by ghostdog74 on 2009-02-06
> **Backharlow said:**
> I am comfortable in Bash but one thing still baffles me...
If I type just \ at a Bash prompt, the new line changes my prompt handle from the normal user@machine:~$ to just the greater than symbol >. This looks like:
```

user@machine:~$ \
>

```
Then hitting enter will keep this strange prompt going.
```

>
>
>

```
like that.
If I execute any other normal process it then goes away, reverting back to my normal prompt:
```

> ls
(normal output of ls)
user@machine:~$

```
Question, what is this phenomenon and what is for?

the "\" just escapes the newline for you. ie, you are going to another line. just like when you write your commands in an editor. do not worry about ">".

---


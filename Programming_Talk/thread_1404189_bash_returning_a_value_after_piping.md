---
title: "bash: returning a value after piping"
date: 2010-02-11
forum: Programming Talk
---

### Post by Paddy Landau on 2010-02-11
A bit of a newbie question...

If I have a list of commands, any variable settings that I make persist after the list is closed. Example:
```
z=[COLOR=DarkRed]'P'[/COLOR]
{
    z=[COLOR=DarkRed]'Q'[/COLOR]
}
echo ${z}    # Will display [COLOR=DarkRed]Q[/COLOR], which is what I want.
```But if I use a pipe, then the new setting is lost. Example:
```
z=[COLOR=DarkRed]'P'[/COLOR]
{
    z=[COLOR=DarkRed]'Q'[/COLOR]
} | cat
echo ${z}    # Will display [COLOR=DarkRed]P[/COLOR], but I want [COLOR=DarkRed]Q[/COLOR]
```I want to keep the new setting ([COLOR=DarkRed]Q[/COLOR]). How can I do that when using a pipe?

---

### Post by Paddy Landau on 2010-02-11
Actually, I realised after reading the manual (yet again) that there is a simpler way to describe this.

Using a list with a pipe as described in my previous post causes a subshell environment. In other words, it's equivalent to:
```
z=[COLOR=DarkRed]'P'[/COLOR]
(
    z=[COLOR=DarkRed]'Q'[/COLOR]
)
echo ${z}    # Will display [COLOR=DarkRed]P[/COLOR], not [COLOR=DarkRed]Q[/COLOR].
```Then, my question becomes: How do I pass a value back from the subshell to the parent shell? In other words, what I want is:
```
(
    *do something with *[COLOR=DarkRed]Q[/COLOR]
)
echo ${z}    # I want this to display [COLOR=DarkRed]Q[/COLOR].
```

---

### Post by avidday on 2010-02-11
Because everything to the right of the pipe is in a subshell, you can't directly. If the subshell returns the result you need to stdout, then you can do something like:

```
result = `command1 | command2`
```and the output of the subshell(s) will be saved in *result*. In the shell, that is about as much as can be done, I think.

---

### Post by Paddy Landau on 2010-02-11
[LEFT]Hmm, thanks.

The output, unfortunately, doesn't hold the result that I need. I guess that I'll have to use a temporary file, perhaps something like:
[/LEFT]
 ```
[COLOR=Navy]response[/COLOR]=[COLOR=DarkRed]"/tmp/${$}.tmp"[/COLOR]

(
    # Do things
    echo [COLOR=DarkRed]'Q'[/COLOR] >[COLOR=Navy]"${response}"[/COLOR]
)

z=$( cat [COLOR=Navy]"${response}"[/COLOR] )
rm [COLOR=Navy]"${response}"[/COLOR]
```Thanks for the reply.

---

### Post by diesch on 2010-02-11
Maybe you can use a function:

```

foo(){
 echo 'Q'
}

result="$(foo)"
echo Result: $result

```

---

### Post by Paddy Landau on 2010-02-11
> **diesch said:**
> Maybe you can use a function...
Thanks for the idea. The coding in question is more complex than that, and its output is distinct from the value that I need to return. It's more like this:
```
{
    *# Create some output*
    *# Create a value that I need returned*
} | *<program to handle output>*
*# Deal with returned value*
```

---


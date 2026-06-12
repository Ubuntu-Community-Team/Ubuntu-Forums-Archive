---
title: "How to expand a variable and keep the quotation marks?"
date: 2014-11-21
forum: Programming Talk
---

### Post by GrouchyGaijin on 2014-11-21
Hi Guys,

I need the output to be:
```
rainlendar2 --add "<user input> [FTASKS]" 
```

I can get the user input by:
```
read -p "Enter some text: " var1
```
I can almost get this to work with:
```

rainlendar2 --add "$var1 [FTASKS]"

```

except that gives me:
```
rainlendar2 --add user input [FTASKS] 
```
and I need
```
rainlendar2 --add **[COLOR=#ff0000]"[/COLOR]**user input [FTASKS]**[COLOR=#ff0000]"[/COLOR]** 
```
That is, I need quote marks before the user input and after ].
Could someone please give me some advice on the correct way to do this?

---

### Post by sisco311 on 2014-11-21
Check out: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

 I'd try something like:
```

read -r var1
var1="$var1 [FTASKS]"
rainlendar2 --add "$var1"

```

---

### Post by Vaphell on 2014-11-21
are the quotes supposed to be the part of the passed string? why would that be the case?

> ```
rainlendar2 --add "$var1 [FTASKS]"
```

that should work if preserving the string as 1 continuous chunk of text is what you are after.

> except that gives me:

```
rainlendar2 --add user input [FTASKS]
```

how exactly can you tell this is what happens, with each of these being considered a separate param?
double quoted string undergoes param expansion but no matter what it stays in 1 piece.

---

### Post by GrouchyGaijin on 2014-11-21
Hey Vaphell,

This is to send a todo to the caldav server.
rainlendar2 is the desktop calendar program that syncs with the server.
They have a gui to add tasks and events, but it is a bit cumbersome.
I can add a task by running this in the terminal:
```
 rainlendar2 --add "some task [Calendar_name]"
```

Basically what I am trying to do is make it a bit easier by being able to simply enter the task descriptiion and haveing that turned into the correct format.
So yeah that format is: ```
 rainlendar2 --add "some task [FTASKS]"
```

By the way, sisco311's suggestion resulted in the same as my own attempt.  I ended up with:
```
 rainlendar2 --add some task [FTASKS] 
``` According to what I see in the terminal if I add an echo command, the quotes are lost.

---

### Post by Vaphell on 2014-11-21
so you are adding echo in front of the command? Everything is peachy. The outermost quotes are for shell, like a parenthesis that makes sure than a continuous string is from here to there. The command itself never sees them. What matters in the end is what shell considers a param, not what you see in echo stripping the details.

```
[COLOR="#0000FF"]cmd[/COLOR] [COLOR="#008000"]aaa[/COLOR] [COLOR="#800080"]bbb[/COLOR] **"**[COLOR="#008080"]ccc ddd[/COLOR]**"**
 [COLOR="#0000FF"]$0[/COLOR]  [COLOR="#008000"]$1[/COLOR] [COLOR="#800080"] $2[/COLOR]   [COLOR="#008080"]$3[/COLOR]
```

to prove it, instead of *echo* try this instead **printf -- '%s\n' <your stuff>**

check this out
```
$ my_cmd() { echo "params i got:"; printf -- '%s\n' "$@"; }
$ echo my_cmd --add "some task [XXX]"
my_cmd --add some task [XXX]            <- wtf?!?
$ my_cmd --add "some task [XXX]"
params i got:
--add
some task [XXX]       <- false alarm, everything is peachy
```

---

### Post by GrouchyGaijin on 2014-11-22
Vapell,

I think I understand what you are saying, but the example you used is confusing (at least to me).
In any case I came up with a [Rube Goldberg]("https://en.wikipedia.org/wiki/Rube_Goldberg") solution:
```
 
echo rainlendar2 --add' "task' $var1' [FTASKS]"' >~/Documents/task.txt

```
and the an xclip command to grab the command from the task.txt and paste it in the terminal.

---

### Post by Vaphell on 2014-11-22
the problem is you haven't described your problem in detail so it's not entirely clear where to look. I thought it was about passing params to another program, but here i see it's about echoing some text into a file.

Long story short:
1. If you need to see quotes in some kind of loosely defined output, then the quotes have to be included in the content too. Shell always strips outermost quotes during parsing.
printf is a good way to do that kind of thing because format string gets rid of a lot of hassle with escaping.
```
$ var1='abc def [WUT]'
$ printf -v var2 '**something --add "[COLOR="#0000FF"]%s[/COLOR]"**' "[COLOR="#0000FF"]$var1[/COLOR]"
$ echo "$var2"
something --add "abc def [WUT]"
```



2. If you need to make sure params are passed without mangling you wrap them in a single pair of quotes which will act as a hint for shell.

Reading OP again i see 'i need the **output** to be' so i misunderstood and it's #1. In that case you need to include the quotes within the content too.
Out of curiosity, what do you need it for?

---

### Post by GrouchyGaijin on 2014-11-22
Thanks man,

Basically this is just so I can quickly submit todo items and events to a calendar on a remote server.
There is a gui to the desktop calendar program I am using, but it is cumbersome - the cli is quicker.  I'm lazy though and only wanted to have to type the message and not the rest of the command.

---


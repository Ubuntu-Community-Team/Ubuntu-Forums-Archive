---
title: "help with regexp"
date: 2007-09-17
forum: Programming Talk
---

### Post by nanotube on 2007-09-17
hey everyone
so, i need to match any lines that don't start with a '>', and that contain "attach" in them. my initial impulse is to do the following:
```
^[^>].*attach.*$
```

however, for now-obvious-to-me reasons, that fails to match lines that actually start with the word attach (and don't contain it anymore). e.g, the following line will fail to match:
```
attach some stuff
```

maybe it's just so late in the night that my brain isn't working well, because it seems it should be obvious, but i just can't think of a nice way to correct this. any hints/tips?

i'm hoping to wake up to some good suggestions. :)

thanks to everyone in advance!

edit: by the way, i'm doing this in javascript - so no fancy stuff that isn't implemented in javascript regex, please. :)

---

### Post by Cappy on 2007-09-17
How about ```
^[^>]*attach
```

---

### Post by nanotube on 2007-09-17
> **Cappy said:**
> How about ```
^[^>]*attach
```

but that wouldn't match
```
some stuff > attach me now
```
?

---

### Post by JinxAu on 2007-09-17
I am no expert myself, but if you go with what Cappy posted, but add in a wildcard ".", it seems to work...
```
grep '^[^>].*attach' file
```

From my understanding that says, "Don't match a ">" at the start of the sentence, followed by anything and the string "attach".

Using following test file:
> some stuff > attach me now
some stuff > me attach now
> some other stuff without an attachment
< stuff some > me now attach


Results  of:
> some stuff > attach me now
some stuff > me attach now
< stuff some > me now attach


Cya round
Jinx

---

### Post by nanotube on 2007-09-17
> **JinxAu said:**
> I am no expert myself, but if you go with what Cappy posted, but add in a wildcard ".", it seems to work...
```
grep '^[^>].*attach' file
```

From my understanding that says, "Don't match a ">" at the start of the sentence, followed by anything and the string "attach".

Using following test file:



Results  of:



Cya round
Jinx

hi jinx
this is exactly what i had originally! (see first post). and that fails to match ```
attach me now
```

---

### Post by JinxAu on 2007-09-17
Sorry, best to read before jumping in... I am new to regular expressions, but been going through it over the last couple of days. Trying to get it to "sink in".

How about:
```
 grep '^[^>]*.*attach' file
```

Which would be, "Don't match a ">" at the start of the sentence, if it's there, otherwise except null pattern (with *) followed by anything and the string "attach".

Cya round
Jinx

---

### Post by Cappy on 2007-09-17
No that doesn't work because it turns out like this:
```

**echo '> attachment' | grep '^[^>]*.*attach'**
> attachment

```

That's why I took it off. I'm not sure of anyway to do this except to match something like ```
'^[^>]*[[:space:]]*.*attach'
```
but that wouldn't match something like this:
```

>some attachment
```

Edit: That above doesn't even work at all

---

### Post by Sensenseppl on 2007-09-17
Edit: Sorry, totally overlooked that one!

---

### Post by nanotube on 2007-09-17
> **Sensenseppl said:**
> I haven't tested it like I should, and I guess its far from perfect, but this should bring you one step further:
```
'^[^>]*attach.*$'
```

It results in:
```
attach_some_stuff
jackson_does_attach
some_attachment
some_attach_stuff

```

And not resulting in:
```
>attach_some_stuff
>some_attach_stuff

```

read post #2 and #3 above - your suggestion was already suggested, and rejected on the grounds that it wouldn't match
```
blabla > attach me
```
:)

---

### Post by bigboy_pdb on 2007-09-17
**This response contains the regular expression that solves your problem** (even though it might appear from the first part that one does not exist). **It also states where you will have trouble when attempting to solve similar types of problems** so** please read it and ask any questions if you are confused**.

Often when you want to do something when a regular expression isn't matched, there is a good chance that you cannot use a single expression to perform that task. The reason why is because regular expressions can only match sequences of characters, they cannot NOT match a sequence of characters.

It is important that you don't mistake "not matching a specific set of characters in a specific position" for "not matching a sequence of characters". When stating that you don't want to match some set of characters, you are actually stating that you want to match every other character that wasn't mentioned. For example, when you state "[^a]", this actually means that you want to match b through z, 0 to 9, and many non-alphanumeric characters.

As an exercise, think about trying avoid matching a sequence of characters. For example, how can we NOT match "daddy"? The short response is without some incredibly specific information about the format of the data we cannot do this.

Regular expressions are always used to perform some operation. When you are using a regular expression, you are stating "if I match this pattern then I do something". So in other words we could say:
if I match expression E then I will do P
Or we could say:
if I match expression E then I will not do P

It is up to the program to allow you to do this. For example, I could tell sed to delete all lines that have daddy using: "sed '/daddy/d' ". I could tell sed to delete all lines that don't have daddy using: "sed '/daddy/!d' ". The follow code shows this:
```

# The "echo -e" commands are sending the following input to sed:
# daddy <newline> baby <newline> mommy <newline> daddy and mommy

# Deletes lines matching "daddy", meaning "baby <newline> mommy" is printed
echo -e " daddy \n baby \n mommy \n daddy and mommy " | sed '/daddy/d'

# Deletes lines that don't match "daddy", meaning "daddy <newline> daddy and mommy" is printed
echo -e " daddy \n baby \n mommy \n daddy and mommy " | sed '/daddy/!d'

```

What you are trying to say is:
If I do not match ">" at the beginning of the line then if I match "attach" then I will perform some operation (such as printing the line).
The problem with this is you are trying to mix two procedures using regular expressions into one. Sometimes under certain circumstances this can be done.

Due to your rigid conditions we can create an expression to do what you want to do:
^[^>].*attach | ^attach

**[EDIT]**There should be no spaces on either side of the "|" character, meaning the expression should be '^[^>].*attach|^attach'**[/EDIT]**

It works because the expression to the left of "|" (which stands for "or") handles the case where the first character is not the letter "a" from the word "attach" and the expression to the right of "|" handles the case where the first character is the letter "a" from the word "attach".

If you had been trying to match an unknown number of ">" characters at the front of the expression, you could not have done this.

---

### Post by nanotube on 2007-09-17
hey bigboy_pdb
thanks for your detailed reply
i suspected there may not be a way without a two-step regexp... i guess your response confirms that it wasn't just me having a brainfreeze, which is the good part. ;)

---

### Post by Cappy on 2007-09-17
> **bigboy_pdb said:**
> 
It is important that you don't mistake "not matching a specific set of characters in a specific position" for "not matching a sequence of characters". When stating that you don't want to match some set of characters, you are actually stating that you want to match every other character that wasn't mentioned. For example, when you state "[^a]", this actually means that you want to match b through z, 0 to 9, and many non-alphanumeric characters.

It works because the expression to the left of "|" (which stands for "or") handles the case where the first character is not the letter "a" from the word "attach" and the expression to the right of "|" handles the case where the first character is the letter "a" from the word "attach".


Very useful information! I didn't know it worked like that. That explains why it wouldn't work without the * behind the [^>]

---

### Post by bigboy_pdb on 2007-09-17
You're welcome. I'm glad to see that you guys appreciate my response (it took some time to make it concise and simpler than my first draft).

---

### Post by JinxAu on 2007-09-17
I know I jumped into this thread without fully knowing what I was talking about. So, I do apologies for that. It's been a good lesson in regular expressions. :)

Just out of interest, I was playing with filtering out strings such as "attachment" and "deattachment" (I know that's not a word, but just in case it showed up)... is it correct to use the \b option to do this? Eg. "\battach\b" ?

Cya round
Jinx

---

### Post by JinxAu on 2007-09-17
Also, I am confused as to how to get the "^[^>].*attach | ^attach" expression to work... as I can not get it to work via sed. Have I missed something here?

First, I made a sedscr file containing:
> /^[^>].*attach | ^attach/p

Second, I populate a test file with sentences:
> some stuff > attach me now
some stuff > now me attach
> some other stuff without an attachment
< stuff some > me now attach
attach me now
> attach me now
>attach me now



Then, I run:
```
sed -n -f sedscr file
```

There is no results printed... I am assuming it is something I am doing wrong... just trying to get my head around things.

Apologies once again to Nanotube for hijacking the thread. :P

Cya round
Jinx

---

### Post by bigboy_pdb on 2007-09-17
Sorry, I forgot to mention something. There should be no spaces on either side of "|" (technically the space on the right won't matter because "^" was specified at the beginning which means that you want to match everything following it if it's at the beginning of the string although doing this could form bad habits). I had typed the spaces to make it more readable.

I've never used \b before so I can't really say much about using it, but special characters like "\b" or "\<" are short forms for writing other expressions. For example, '\<hello' is the same thing as '^hello|[[:space:]]hello' meaning it matches the word "hello when it's at the beginning of a line or when it follows a space character. Space characters are tabs, newlines, vertical tabs, form feeds, carriage returns, and spaces. However, the newlines will not be matched if they are the characters that the lines are being split across (which is the default behaviour in sed). '[[:space:]]' is the same thing as '[ \t\n\v\f\r]'.

JinxAu, there is one more problem with your script. In sed you must place a "\" character before the "|" character. Unfortunately, in some older programs that use regular expressions the characters "|", "{", "}", "(", and ")" represented themselves and in order to give them their special meanings you had to place backslashes before them. For example, to use "|" to mean "or" you had to use "\|" and the character "|" represented the pipe character. This was later changed (and I'm guessing it's because those characters were probably more commonly used with backslashes) so that each of those characters represented their escaped versions (the versions preceded by backslashes) from the previous standard. In the newer programs, to get their literal meanings you needed to put a backslash before them. For example, "|" was later used to mean "or" and "\|" was later used to mean "|" (the pipe character). So basically the definitions were switched, which most likely causes many people problems. Thus, it is a good idea to check either the man page or the info page for whatever version of sed/grep/awk that you're using to be sure of what those characters mean according to the version of the program that you're using.

To make a long story short, for sed you need to use "\|" to represent "or" instead of "|". Thus, with all of the corrections, the expression in sed would be as follows:
```

/^[^>].*attach\|^attach/p

```

To use sed on your file use the following command:
```

sed -n '/^[^>].*attach\|^attach/p' *filename*

```

The output that I got was:
```

some stuff > attach me now
some stuff > now me attach
< stuff some > me now attach
attach me now

```

This is the correct output.

By the way, nanotube the expression that I gave you will match lines like "attachment" as well. Did you want this? If not then use the expression '^[^>].*attach\>|^attach\>'. The character "\>" will match the end of words. '*exp*\>' is the same as '*exp*[[:space:]]|*exp*$', which is true when the expression is followed by space characters or the end of the line.

---

### Post by JinxAu on 2007-09-17
Thanks for the follow up explanation bigboy_pdb. It makes a lot more sense now. 

Appreciate your patience.

Cya round
Jinx

---

### Post by bigboy_pdb on 2007-09-18
While I'm stating this other stuff I might as well state some other things that are useful.

When using regular expressions in the bash shell you should put them within single quotes to avoid problems special characters in the bash shell. If you need to use a bash shell variable within the expression then you can put it in a set of double quotes that are within a set of single quotes. An example of this would be:
```

exp='daddy\|mommy\|baby'
sed 's/\<'"$exp"'\>/family' *filename*

```
This replaces the words (and only the words) "daddy", "mommy", and "baby" with the word "family".

Another useful tip is that you can have newlines in strings by hitting enter after typing an opening quote. This is useful when you're using sed because it expects newlines between expressions. You can use semicolons, but I read (in the O'Reilly "sed & awk" book) that their use isn't documented. An example of this would be:
```

sed '/special/{
/delete/d
s/\(.*\)reverse\(.*\)/\2reverse\1/
}' *filename*

```
In this example, the expressions are only performed if the line contains the word "special". If this is the case and the line contains the word "delete" then the line is deleted. If the line contains the word "special", it doesn't contain the word "delete", and it contains the word "reverse" then the sequence of characters to the left of the word "reverse" are swapped with the sequence of characters to the right of the word "reverse".

The following input
```

reverse and delete do nothing without something else
this line is special and should be deleted instead of reversed
 I should not reverse anything special 

```
(there's a space after the word "special" on the last line)
produces the following output
```

reverse and delete do nothing without something else
 anything special reverse I should not 

```

This is a good example of how programs can use regular expressions as conditions for performing tasks with other regular expressions. We could have printed the lines containing "attach" that don't start with a ">" character by typing the following:
```

sed -n '/attach/{
/^>/d
p
}' *filename*

```

---


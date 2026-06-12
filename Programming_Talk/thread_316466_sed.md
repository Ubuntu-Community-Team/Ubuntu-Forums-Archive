---
title: "sed"
date: 2006-12-10
forum: Programming Talk
---

### Post by bajetownrep on 2006-12-10
i want to append a line after any line with a particular regular expression. The pattern is found in a file called datafile

The regular expression is central.

So I did this

sed '/central/a\
This is a test' datafile

But I get an error message stating that it cant find a label for jump to `his`.

:-? 

That was pretty cryptic. Any suggestions

---

### Post by duff on 2006-12-10
what about ```
sed -e 's:central$:&\nThis is a test:' datafile
```

---

### Post by bajetownrep on 2006-12-10
i will try that but could you shed any light on why sed was giving me that error.

I like unix well enough but some of the error messages are  extremely unhelpful. I am willing to learn but it seems that sometimes these tools go out of their way to be difficult

The append looked simple enough in all the tutorials i read on sed but I am obviously doing something wrong :(

---

### Post by po0f on 2006-12-10
bajetownrep,

"T" is a sed command, much like "s//" and "d".  And apparently, it sets a label.  :)

---

### Post by Arndt on 2006-12-11
> **bajetownrep said:**
> i will try that but could you shed any light on why sed was giving me that error.

I like unix well enough but some of the error messages are  extremely unhelpful. I am willing to learn but it seems that sometimes these tools go out of their way to be difficult

The append looked simple enough in all the tutorials i read on sed but I am obviously doing something wrong :(

That's a reasonable request, but when I try your command, it works fine. What shell are you using? I'm using bash. There could be a problem with how \ is interpreted.

I think the error message is not hopelessly cryptic. sed tells you it found something it didn't like near the text "his" and that's easy to identify in your input. So it's probably the 'T' that is being interpreted as a command instead of text. It's difficult for sed to deduce at what point earlier the actual error occurred, since sed had no problems up to that point.

Now that I try without the \ character, I get the same error message as you did. So it's either something with how multiple-line command lines are input in the shell you're using, or you just forgot the \ when you tried it out, I guess.

---

### Post by bajetownrep on 2006-12-11
Oh, my apologies, I was attempting this in tcsh as this is what a tuorial I was doing was using. This may very well work perfectly in bash.

I will scan the sed manpage. Thanks for the input guys. I dodnt want to give the impression that I am unwilling to learn, I guess I was just a bit fustrated last night that what seemed to be a simple command as opposed to regex matching and substitution was giving me a problem when I was able to get other sed commands done.

so once again thanks

---

### Post by po0f on 2006-12-11
bajetownrep,

Apparently I need to RTFM as well:
```
[FONT="Courier New"]T label
    If  no  s///  has  done a successful substitution since the last
    input line was read and since the last  t  or  T  command,  then
    branch to label; if label is omitted, branch to end of script.[/FONT]
```
Basically, it thought "his" was a label it should branch to.

---

### Post by bajetownrep on 2006-12-11
T label
    If  no  s///  has  done a successful substitution since the last
    input line was read and since the last  t  or  T  command,  then
    branch to label; if label is omitted, branch to end of script

hmmmm.What exactly is a label? What are they defining as the last input line?  

Suppose that this append line command is the first sed command I am performing on a file? What then?

And how then do I indicate to sed to not treat t or T as a command but just a simple character.

I am here reading the sed manpage and it uses the term label without clarifying what it means(or maybe I am just a simpleton).

---

### Post by Arndt on 2006-12-11
> **bajetownrep said:**
> T label
    If  no  s///  has  done a successful substitution since the last
    input line was read and since the last  t  or  T  command,  then
    branch to label; if label is omitted, branch to end of script

hmmmm.What exactly is a label? What are they defining as the last input line?  

Suppose that this append line command is the first sed command I am performing on a file? What then?

And how then do I indicate to sed to not treat t or T as a command but just a simple character.

I am here reading the sed manpage and it uses the term label without clarifying what it means(or maybe I am just a simpleton).

It's the first command listed:

>    Zero-address ‘‘commands’’
       : label
              Label for b and t commands.


'sed' reads lines from some input source, and sends them, one at a time, through the script you specify. The script often just looks like a number of substitutions and matches, but it can also change execution flow just as usual programming languages, by branching ("goto") to a label, either unconditionally or dependent on some condition.

---


---
title: "Sed is the coolest thing in the history of ever!"
date: 2009-12-26
forum: Programming Talk
---

### Post by nmccrina on 2009-12-26
Sorry, this thread is pretty pointless but I just had to shout that somewhere!

```
sed '4 s/I Saw Her Standing There/Love Me Do/g' convert > temp && mv -f temp convert
```

:guitar:
:lolflag:

---

### Post by sisco311 on 2009-12-26
:)
```
sed -i.backup "4 s_I Saw Her Standing There_Love Me Do_g" convert
```

---

### Post by ghostdog74 on 2009-12-26
don't be silly. you can do the same with awk, and awk can do a lot more than sed, so can many others.
```

awk 'NR==4{gsub(/I Saw Her Standing There/,"Love Me Do")}1' file

```
so why is sed the coolest thing?

---

### Post by nmccrina on 2009-12-26
> **sisco311 said:**
> 
```
sed -i.backup "4 s_I Saw Her Standing There_Love Me Do_g" convert
```

Cool! That would answer [this guy's]("http://www.unix.com/shell-programming-scripting/122889-sed-edit-place-i-issues.html") question too! :)

> **ghostdog74 said:**
> don't be silly. you can do the same with awk, and awk can do a lot more than sed, so can many others.
```

awk 'NR==4{gsub(/I Saw Her Standing There/,"Love Me Do")}1' file

```
so why is sed the coolest thing?

:shock: Oh no! There's MORE text processing utilities I have to learn how to use??? 

<sigh>Oh well, back to the man pages...  :)

---

### Post by monkeyking on 2009-12-26
I think most people are using a mix of awk,sed and tr.
Depending what they want to do.

---

### Post by slavik on 2009-12-26
1 word: Perl. :)

---

### Post by nmccrina on 2009-12-26
> **slavik said:**
> 1 word: Perl. :)

I have long gazed at it from afar, but was never brave enough to approach!

I chose Python. :lolflag:

---

### Post by kwyto on 2009-12-26
hi guys, i've messed around with python, but i have never done any bash scripting. i think python is very powerful, so i don't see the point of learning bash scripting. can anyone give an opinion? now, i'm not making a distinction between python or perl. i'm talking about bash, awk, sed, etc. thank you for your input

---

### Post by sisco311 on 2009-12-26
> **kwyto said:**
> hi guys, i've messed around with python, but i have never done any bash scripting. i think python is very powerful, so i don't see the point of learning bash scripting. can anyone give an opinion? now, i'm not making a distinction between python or perl. i'm talking about bash, awk, sed, etc. thank you for your input

Why do you think that python is more powerful than bash? 

IMO, you have to make an educated decision.

---

### Post by ghostdog74 on 2009-12-27
> **nmccrina said:**
> 
:shock: Oh no! There's MORE text processing utilities I have to learn how to use??? 

for text processing with the shell, only awk you need to learn. forget about sed. their functions overlap, and awk can do more, so learn the one with more features.

---

### Post by ghostdog74 on 2009-12-27
> **kwyto said:**
> hi guys, i've messed around with python, but i have never done any bash scripting. i think python is very powerful, so i don't see the point of learning bash scripting. 
its funny. why do you make judgement on something that you don't even know, at least in depth? if you don't know something, better don't say anything.

---

### Post by kwyto on 2009-12-27
well, the way i look at it, python can be used to develop web pages as well as databases. python is very versatile which makes it powerful. can you create web pages with bash? also writing and reading code for python seems easier than doing with bash. of course that varies with the person. still my question hasn't been answered, maybe it wasn't phrase correctly. maybe i should be asking which is more powerful between python and bash ? or are they that much different, such there is no comparison?

---

### Post by nvteighen on 2009-12-27
> **kwyto said:**
> hi guys, i've messed around with python, but i have never done any bash scripting. i think python is very powerful, so i don't see the point of learning bash scripting. can anyone give an opinion? now, i'm not making a distinction between python or perl. i'm talking about bash, awk, sed, etc. thank you for your input

> **sisco311 said:**
> Why do you think that python is more powerful than bash? 

IMO, you have to make an educated decision.

Why the hell people insist in comparing Python with Bash?

Python is a general programming language and thus, it **could** be used a shell scripting language, though the fact that you can doesn't mean you should. Python constructs make it possible, but it's a bit of a mess precisely because Python is a cross-platform language: Shell-scripting isn't meant to be cross-platform, but the opposite! Python being cross-platform makes it abstract system operations too much (the whole os.path stuff, for example) that are useful in cases in which you can't assume/don't care what system are running on top of.

Bash is a shell-scripting language for a specific shell widely used in UNIX(-like) environments. It is a useless language for creating a 3D game (though in theory you could) because it is designed to work in a shell: it relies on string processing in order to make up commands, it incorporates any system-wide executable as it were a native function, etc. because it is meant to automate the system. (IMO, shell scripting is the high-level counterpart of the system programming you do in C or C++).

So, this discussion is nonsense.

---

### Post by kwyto on 2009-12-27
thank you for the clarification.

---

### Post by DaithiF on 2009-12-27
as a general point, if someone says, learn A rather than B because A can do more, the better answer may be to learn both, at least the basics.  If you only ever work on your own 'stuff', then I guess you can specialise in whatever you like, but if/when you work 'in the real world', you'll come across all kinds of code written in all kinds of technologies and having a broad set of skills can be very valuable.  I'm not saying learn cobol or fortran but knowing some sed / awk / bash scripting / perl / python can all be very useful and what you learn in one will likely make you a better all-round technologist.

---

### Post by ghostdog74 on 2009-12-27
> **kwyto said:**
>  can you create web pages with bash? also writing and reading code for python seems easier than doing with bash. 

why not? what do you use to create web pages? I can create a web page just by using a text editor .

---

### Post by ghostdog74 on 2009-12-27
> **DaithiF said:**
> as a general point, if someone says, learn A rather than B because A can do more, the better answer may be to learn both, 

there's a subtle difference. For example in the context of sed and awk. awk can do more AND in the process of learning awk, you can also learning about regular expression which sed is based on. In that case, where this function overlap, learning awk IS BETTER than learning sed.

---

### Post by DaithiF on 2009-12-27
> **ghostdog74 said:**
> there's a subtle difference. For example in the context of sed and awk. awk can do more AND in the process of learning awk, you can also learning about regular expression which sed is based on. In that case, where this function overlap, learning awk IS BETTER than learning sed.

while reg-exes are common to both (and to any number of other programming languages) , sed and awk syntax is otherwise quite different.  I can think of a couple of reasons why sed might be a preferred tool for someone to learn over awk  ... (1) For vim users sed syntax comes very naturally as its basically an extension of the functionality available within the editor itself (2) you might find yourself the maintainer of a bunch of existing sed scripts -- so you need to know what they are doing.  So I would still suggest learning both.

---

### Post by ghostdog74 on 2009-12-27
> **DaithiF said:**
> while reg-exes are common to both (and to any number of other programming languages) , sed and awk syntax is otherwise quite different. 

yes they certainly are. sed uses regex a lot and too much use of it makes sed code unreadable and hard to decode. while you can use regex in awk, there is certainly no need to. 

> 
(2) you might find yourself the maintainer of a bunch of existing sed scripts -- so you need to know what they are doing.  So I would still suggest learning both.
Do you mean one that already learns about regex in awk cannot understand how to read sed commands, which are basically just regexes?  that's not true right? any statistics to back up your claim?

---

### Post by DaithiF on 2009-12-28
> **ghostdog74 said:**
> Do you mean one that already learns about regex in awk cannot understand how to read sed commands, which are basically just regexes?  that's not true right? any statistics to back up your claim?
Why do you say that sed commands are basically just regexes?  That is not correct.  There are sed commands for inserting, appending, substituting, deleting text which need not involve reg-exes at all.  There are also commands for manipulating the pattern and buffer spaces (G, g, H, h, x), and a command for branching, etc.  So sed is a langugage, consisting of commands, which are applied to a stream, and may optionally be applied to only certain parts of the stream, and (only) one way of specifying those parts is through regexes.

I get your point -- you prefer awk.  Thats fine.  I use both, and I happen to think sed is a useful tool.

---

### Post by ghostdog74 on 2009-12-28
> **DaithiF said:**
> Why do you say that sed commands are basically just regexes?  That is not correct.  There are sed commands for inserting, appending, substituting, deleting text which need not involve reg-exes at all.  There are also commands for manipulating the pattern and buffer spaces (G, g, H, h, x), and a command for branching, etc.  So sed is a langugage, consisting of commands, which are applied to a stream, and may optionally be applied to only certain parts of the stream, and (only) one way of specifying those parts is through regexes.

that's why, all these abbreviations, G,H,h,etc makes your code harder to decipher. Its like reading an english essay that is written with numbers..

---

### Post by piyush.neo on 2009-12-29
Nice to see a 'sed' thread..i have a doubt about sed....why this command doesn't work when i am trying to substitue '\n' with any other character...
**sed 's/\n/try/g' list.txt**
although...
**sed 's/\t/try/g' list.txt**
works....
what i think is sed manipulate the text line by line where '\n' delimiter....so it never take '/n'....
**please put the light on its working.....:confused:**

---

### Post by DaithiF on 2009-12-29
> **piyush.neo said:**
> Nice to see a 'sed' thread..i have a doubt about sed....why this command doesn't work when i am trying to substitue '\n' with any other character...
**sed 's/\n/try/g' list.txt**
although...
**sed 's/\t/try/g' list.txt**
works....
what i think is sed manipulate the text line by line where '\n' delimiter....so it never take '/n'....
**please put the light on its working.....:confused:**
correct, sed is a line by line editor -- it is designed to work on a line at a time, and it does not include the newline character when it reads in a line to work on.  In some cases you can get around this through the use of the N command which reads in the next line of output and appends it (separated by a newline), to the 'pattern space' (the buffer that sed commands work on).

For example, if you had this file:
```
one
two
three

```
and you wanted to replace the newline after 'one' with something else, (ie. thereby joining the first & second lines), you could do something like this:
```
sed '/one/{N;s/\n/ newline is now gone /}' somefile

```giving
```
one newline is now gone two
three
```

---

### Post by ghostdog74 on 2009-12-29
```

$ awk '/one/{o=$0;getline;$0=o" newline gone "$0}1' file
one newline gone two
three


```

---

### Post by piyush.neo on 2009-12-29
> **DaithiF said:**
> correct, sed is a line by line editor -- it is designed to work on a line at a time, and it does not include the newline character when it reads in a line to work on.  In some cases you can get around this through the use of the N command which reads in the next line of output and appends it (separated by a newline), to the 'pattern space' (the buffer that sed commands work on).

For example, if you had this file:
```
one
two
three

```and you wanted to replace the newline after 'one' with something else, (ie. thereby joining the first & second lines), you could do something like this:
```
sed '/one/{N;s/\n/ newline is now gone /}' somefile

```giving
```
one newline is now gone two
three
```

Thanks a lot....nice command **N** from where do u get these command like [B]N
:guitar:
[/B]

---

### Post by DaithiF on 2009-12-29
> **piyush.neo said:**
> Thanks a lot....nice command **N** from where do u get these command like [B]N
[/B]

sed manual page
```
man sed

```
or try one of the many online tutorials, eg:
[URL="http://www.grymoire.com/Unix/Sed.html#uh-47"]http://www.grymoire.com/Unix/Sed.html#uh-47
[/URL]

---


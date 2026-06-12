---
title: "Why to love/hate shell scripting"
date: 2008-09-04
forum: Programming Talk
---

### Post by mssever on 2008-09-04
We have threads on why to love/hate a number of different languages, but recent discussions reminded me that we don't have one on shell scripting. So, here it is. (/me puts the fire department on alert :))
[SIZE=2][B]
My Background[/B][/SIZE]
I've been using Linux for about ten years. When I started, satisfactory GUI environments were either unavailable or I didn't know about them, so I learned the shell quite well. Naturally, I began writing shell scripts. At first, they were merely sequential lists of commands. Then, as I began to learn more about programming, my scripts became more elaborate. Today, I think I'm reasonably competent when it comes to bash scripting (though I'm by no means an expert). I've learned some things along the way that I think are relevant to a number of discussions we have around here.

[SIZE=2]**Things I like about shell scripting**[/SIZE]
Bash is a great interactive language. For executing external commands, I love it. I read somewhere where Mark Shuttleworth would like to see Python syntax throughout the Linux stack--including the shell, but I have to disagree. The way bash handles whitespace makes commands easy to type quickly. There are no parentheses to worry about, and no modules to import (well, you *can* source files, but that's not normally done in interactive shells except for login scripts).

Shell scripting is also handy for quick one-off tasks. There have been a number of times when I wanted to do some sysadmin-type task, which was simple but repetitive. In many cases, the easiest thing is just to type the program on the command line.

Another thing I like about shell scripting is it makes a great wrapper for other programs. For example, suppose you need a .desktop file to launch its program with a varying set of arguments depending on some condition. That's a great job for bash.

Bash is also good when you primarily need to launch other programs; that's really its main purpose.

[SIZE=2]**Things I dislike about shell scripting**[/SIZE]
Bash's syntax oddities, while they can be vary handy on the command line, make programming more difficult. I've seen many noobs trip up over bash's aggressive whitespace handling when they fail to protect stuff using double or single quotes--stuff you wouldn't have to protect in most other languages.

Some of bash's data structures are seriously deficient for serious programming. For example, to create an empty array, then append an item to it: ```
# Bash:
declare -a some_array
some_array[${some_array[@]}]=1

# Ruby:
some_array = []
some_array.push 1
```This is only one example of bash's array weirdness. Pretty much any array operation involves jumping through hoops, and IMHO arrays are a basic data type, on par with numbers and strings.

Speaking of numbers, have you ever tried to manipulate numbers in bash? Again, you have to jump through hoops. You can use the [FONT=Courier New]let[/FONT] command to do math, or you can use double parentheses. If you want floating point numbers, you have to store them as strings, and use [FONT=Courier New]bc[/FONT] or something similar to do math with them. In other languages, such as Ruby, you don't need to worry about this kind of thing.

Another common task that's difficult in bash is text processing. Bash is able to tokenize strings and loop over them in several ways, and if you use the [FONT=Courier New][[[/FONT] command, you can test for regular expression matches. Beyond that, you have to resort to other tools. [FONT=Courier New]sed[/FONT] is one such tool, but it uses odd regexp syntax that's different from most every other language (meaning there's more to remember). You can, of course, use [FONT=Courier New]awk[/FONT]. But that involves learning an entirely separate language, just to be able to process text.

Shell scripting scales poorly. There are no namespaces, and as mentioned above, higher-level data structures are inadequate or nonexistent.

Shell scripting is also incredibly inconsistant. CptPicard put it well when he described it as "piping unstructured externally-semantic text between various complex tools with totally different usage." [[link]("http://ubuntuforums.org/showpost.php?p=5723280&postcount=27")]
[SIZE=2][B]
When I use a shell script[/B][/SIZE]
I used to write a lot of shell scripts. These days, I've learned better. :) When I have a short, trivial task, I write it in bash. When I write an init script, I write it in sh, since that's what the standard requires. If I need portability--well, if the sysadmin can't be bothered to provide a decent environment including at least one of Ruby or Python, then I can't be bothered to care whether my scripts run on that system. If I find myself fighting bash, or pulling out the [*Advanced Bash Scripting Guide*]("http://tldp.org/LDP/abs/html/") frequently, then I know I've got the wrong tool for the job.

Otherwise, I write in Ruby (or another language if appropriate). Even though my Ruby code is occasionally longer than its bash equivalent, it's a whole lot easier to understand, write, debug, and maintain. I don't have to mess with bash's odd syntax. I don't have to fool with bash's poor data structures. And it's hard to beat Ruby when it comes to text processing.

In summary, I think that shell scripting has its uses, but many people around here use it when another language would be much more appropriate. What are your reasons to love or hate shell scripting?

---

### Post by LaRoza on 2008-09-04
The shell is a very handy tool, but as a scripting language comparable to Python and Ruby and Perl, it has a few flaws. One is that is it is way too diverse. There is the bash, dash, and c shell, amoung many others with subtle differences. The standard unix tools can very slightly between distros and Unix like OS's (awk isn't just awk the world over).

It origins also are a limitation. It can be "cross platform" but in practice it is usually specific to a distro (or even a version of that distro).

It can be the first programming language a person learns when they get into Linux, and in that respect it isn't better or worse than others. It is very useful (if much less portable) and it can be used for the common tasks that Linux users typically want to do.

---

### Post by slavik on 2008-09-04
the interesting thing about shell scripts is that the basic datatype is a string, not a number type.

---

### Post by pmasiar on 2008-09-04
I think there is little misunderstanding - bash is one of scripting languages, but comparing bash with Perl/Python is comparing apples with oranges. Perl/Python are general programming languages, bash is specialized to manage processes and files. 

So there are different kinds of scripting: 
- shell scripting (bash and all the shell dialects) to manage OS tasks
- using dynamically typed general programming languages (also called "scripting languages"), like Perl and Python, to solve common programming problems. They overlap a little, but for any larger project I prefer real language: Python.

Still, bash is something every competent programmer should know - even if not using daily, to know basic tricks/features, piping, redirections, and where to learn more if needed.

bash, when used as supposed (ie: sparingly) can save your bacon - I know it saved mine :-) And you have no idea how brilliant idea shell is, and how hard was life before shell - in times of JCL/360: [http://en.wikipedia.org/wiki/Job_Control_Language](http://en.wikipedia.org/wiki/Job_Control_Language) Pain, pure pain, you are lucky you never encountered that! :-)

Of course once you go over 20-30 lines, or start fancy parsing, you are IMHO better off with Perl, or go all the way to Python.

I have no problem with people suggesting to learn bash - I know I need to learn it better. But I do have problem with suggesting bash/awk as first language. Yes, it is trivial to run in shell. But Python has also (Python) shell, no advantage there. And bash lacks convenient data structures, it is designed to handle processes and files (and does it with aplomb), but not to write simple text game or anything. And as I mentioned, it does not scale.

So as long as not suggested as first language, I recommend to learn bash. Scripting is fun - computer works for you much harder than when using strictly statically typed language.

So, here is to all who accuse me of telling that Python is the only language, ever: You are wrong. bash is good to know, and good tool for some task. But unless you are sysadmin, you don't do those tasks where bash is best daily, or even monthly.

Another trick what might be of use for bash ignoramuses like me, is to learn midnight commander: Create little bash snippets with shell scriplets, and call them from mc menu (and you can forget the syntax until you need to tweak it next time). Works like charm :-)

Thanks mssever for this rare opportunity to say good  words for bash without need to fight against accusation of promoting Python. I know I did, but just a little 8-)

---

### Post by ghostdog74 on 2008-09-04
> **mssever said:**
> 
[SIZE=2]**Things I dislike about shell scripting**[/SIZE]
Bash's syntax oddities, while they can be vary handy on the command line, make programming more difficult. I've seen many noobs trip up over bash's aggressive whitespace handling when they fail to protect stuff using double or single quotes--stuff you wouldn't have to protect in most other languages.
 
Can you give an example ?

> **mssever said:**
> 
Some of bash's data structures are seriously deficient for serious programming. For example, to create an empty array, then append an item to it: ```
# Bash:
declare -a some_array
some_array[${some_array[@]}]=1

this is much easier:
[code]
arr=( ${arr[@]} $val )

```

> **mssever said:**
> 
```

# Ruby:
some_array = []
some_array.push 1

```

I don't think this is a basis for comparison. Behind that ".push" is an piece of algorithm to append to arrays. A bash function 
can also be done and stored as library.
```

append() { # code to append to arrays}

```

> **mssever said:**
> 
Speaking of numbers, have you ever tried to manipulate numbers in bash? Again, you have to jump through hoops. You can use the [FONT=Courier New]let[/FONT] command to do math, or you can use double parentheses. If you want floating point numbers, you have to store them as strings, and use [FONT=Courier New]bc[/FONT] or something similar to do math with them. In other languages, such as Ruby, you don't need to worry about this kind of thing.

Again this is no basis for comparison. If you know how its done using the shell, its just as easy to code. 

> **mssever said:**
> 
Another common task that's difficult in bash is text processing. Bash is able to tokenize strings and loop over them in several ways, and if you use the [FONT=Courier New][[[/FONT] command, you can test for regular expression matches. Beyond that, you have to resort to other tools. [FONT=Courier New]sed[/FONT] is one such tool, but it uses odd regexp syntax that's different from most every other language (meaning there's more to remember). You can, of course, use [FONT=Courier New]awk[/FONT]. But that involves learning an entirely separate language, just to be able to process text.

Awk is a programming language. It can be used to do what bash can or cannot do(easily). As for the argument of learning a separate language, i don't see it as a basis for comparison. In python or ruby, you have to learn how to manipulate text as well, right?
To use re in Python, one have to import re. In Bash, one just use awk/sed. No BIG difference.

> 
Shell scripting scales poorly. There are no namespaces, 

yes, there is local namespace. 

> 
and as mentioned above, higher-level data structures are inadequate or nonexistent.

Do you mean hashes/dictionaries and things like that? They are complemented using awk.

> **mssever said:**
> 
Shell scripting is also incredibly inconsistant. CptPicard put it well when he described it as "piping unstructured externally-semantic text between various complex tools with totally different usage." [[link]("http://ubuntuforums.org/showpost.php?p=5723280&postcount=27")]
[SIZE=2][B]

Piping is another way of calling your functions/methods to do tasks. 
```

echo "$var" | tr '[a-z]' [A-Z]' #convert to uppper case

```
Python
```

"abc".upper()

```
In the above, upper() is just like tr ... no BIG difference. So i don't agree with what CptPicard said.

---

### Post by lucho64 on 2008-09-04
> **ghostdog74 said:**
> 
Can you give an example ?

if ["a"=="a"]; then echo yes; else echo no; fi

Ok, not quite the example you were asking for, but somebody with, say C background only, will trip over that one. And I actually like bash.

---

### Post by mssever on 2008-09-04
> **ghostdog74 said:**
> Can you give an example ?I just gave an example. Want another one? How about this? Suppose I need to add floating point numbers and assign the result to a variable. I need to launch a subprocess and employ special syntax to accomplish what should be a straightforward task: ```
# Note that these numbers are actually strings...
# Also, the fact that bash doesn't allow whitespace around
# the = during variable assignment trips many people up.
num1=1.2
num2=13.2
result=$(echo "$num1 + num2" | bc)
```And file descriptor manipulation must have been the inspiration for Perl. It certainly looks like line noise.

> this is much easier:
```

arr=( ${arr[@]} $val )

```But just as ugly and kludgy.


> I don't think this is a basis for comparison. Behind that ".push" is an piece of algorithm to append to arrays. A bash function 
can also be done and stored as library.
```

append() { # code to append to arrays}

```This brings up another problem with bash which makes your suggestion to write a bash function very difficult. Bash functions can only return unsigned integers < 256. So how will you return the new array? Basically, you have two options, neither of which is much cleaner than the original way.
[LIST=1
[*]Dedicate a global variable to holding return values. The function should assign to that value, then after it returns, you need to manually assign the return value to your variable you're working with.
[*]echo the return value, and use $() to capture it. 
[/LIST]Both of these are messy. However, in my Ruby example, Array#push has already been written, so I don't need to care how it's implemented. It's a black box.

> Awk is a programming language. It can be used to do what bash can or cannot do(easily). As for the argument of learning a separate language, i don't see it as a basis for comparison. In python or ruby, you have to learn how to manipulate text as well, right?But learning another language simply to work around the deficiencies of the first is silly. Why not sidestep the issue altogether? Furthermore, the comparison with Ruby and Python doesn't make sense. When you manipulate text in one of those languages, you're using standard features of the language, not a separate language.
> To use re in Python, one have to import re. In Bash, one just use awk/sed. No BIG difference.But there is. When you import re, you're still writing Python code. When you use sed or awk, you're in a completely different language, with different syntax and different semantics.

> Do you mean hashes/dictionaries and things like that? They are complemented using awk.But to use them, I need to stay in awk, right? How can I pass a hash around in bash? OK, I know it can be done if you're sufficiently determined, but why not use a language better suited for the task to begin with?

> Piping is another way of calling your functions/methods to do tasks.You missed the point. There are many subtle inconsistencies between the various Unix tools, giving you a convoluted situation like the PHP "API." Furthermore, you're stuck passing strings. Now, there are good reasons for passing strings, but there are also many situations where that isn't optimal.

Oh, I just remembered something else: Bash variables are global unless explicitly declared local. That's OK if you're trying to set environment variables. But for scripting, it's a Bad Thing.

---

### Post by ghostdog74 on 2008-09-04
> **pmasiar said:**
> I think there is little misunderstanding - bash is one of scripting languages, but comparing bash with Perl/Python is comparing apples with oranges. Perl/Python are general programming languages, bash is specialized to manage processes and files. 

yes you can:
1) almost apples with apples: if Python/Perl minus modules/libraries.
2) orange to orange : bash+awk+tools = Python+modules 


> **pmasiar said:**
> 
Of course once you go over 20-30 lines, or start fancy parsing, you are IMHO better off with Perl, or go all the way to Python.

What type of fancy parsing?

> **pmasiar said:**
> 
 But I do have problem with suggesting bash/awk as first language.

i don't. Like in my previous comments with you, no matter which language, as long as it provides basic programming concepts, its ok
to use it as first language.

> **pmasiar said:**
>  And bash lacks convenient data structures, it is designed to handle processes and files (and does it with aplomb), but not to write simple text game or anything. And as I mentioned, it does not scale.

if you want data structures like dictionaries, you can use awk. Simple text game? Of course you can.

---

### Post by mssever on 2008-09-05
> **ghostdog74 said:**
> Simple text game? Of course you can.Did you ever see the adventure shell? It was essentially a text-based adventure game written (I think) in bash, which pretended to be a shell. I was playing with it a number of years ago, made a mistake, and accidentally deleted everything in my homedir. I didn't have a backup.

---

### Post by slavik on 2008-09-05
OK, to dispell some myths ...

Perl was written to do text process (directly rival awk), it then became a general purpose programming suited language.

to do regular expressions in bash, you do not have to use awk/sed, bash has them (so does korn). ksh93 and bash are the two most used shells.

the thinking behind writing shell code is to link smaller tools to accomplish the task. perl/python are bigger tools.

Just because you can, doesn't mean you should. :) (I did not come up with that quote, I am sure that someone else did).

@pmasiar, since you mention JCL ... retire already!!! :)

---

### Post by ghostdog74 on 2008-09-05
> **mssever said:**
> I just gave an example. Want another one? How about this? Suppose I need to add floating point numbers and assign the result to a variable. I need to launch a subprocess and employ special syntax to accomplish what should be a straightforward task: ```
# Note that these numbers are actually strings...
# Also, the fact that bash doesn't allow whitespace around
# the = during variable assignment trips many people up.
num1=1.2
num2=13.2
result=$(echo "$num1 + num2" | bc)
```And file descriptor manipulation must have been the inspiration for Perl. It certainly looks like line noise.

I don't see what's wrong with not allowing whitespace around the "=". Just like other lang has their quirks and warts. One just have to master and get used to it. 
```

awk 'BEGIN { num1=1.2; num2=13.2; print num1+num2}'

```


> **mssever said:**
> 
But just as ugly and kludgy.

Only if you want to base your arguments on cosmetics.

> **mssever said:**
> 
This brings up another problem with bash which makes your suggestion to write a bash function very difficult. Bash functions can only return unsigned integers < 256. So how will you return the new array? Basically, you have two options, neither of which is much cleaner than the original way.
[LIST=1
[*]Dedicate a global variable to holding return values. The function should assign to that value, then after it returns, you need to manually assign the return value to your variable you're working with.
[*]echo the return value, and use $() to capture it. 
[/LIST]Both of these are messy. However, in my Ruby example, Array#push has already been written, so I don't need to care how it's implemented. It's a black box.

```

Return_Array ()
{
  local passed_array   # Local variable.
  passed_array=( `echo "$1"` )
  echo "${passed_array[@]}"
}
returned_array=( `Return_Array "123"` )
echo ${returned_array[@]}

```
blackbox? Once i write Return_Array and use it as a library, isn't it the same???

> **mssever said:**
> 
But learning another language simply to work around the deficiencies of the first is silly. 
No its not, why do you think its silly? C has deficiencies, and many other languages are written to cover those deficiencies. So you mean to tell me its silly to learn them? 

> **mssever said:**
> 
Why not sidestep the issue altogether? Furthermore, the comparison with Ruby and Python doesn't make sense. When you manipulate text in one of those languages, you're using standard features of the language, not a separate language.

why does it not make sense. Bash has its own string manipulation. If you think its not enough, there's awk. In fact, you can just use Awk. In terms of text processing, Awk can do as much as ruby/Python. Unconvinced?

> **mssever said:**
> 
But there is. When you import re, you're still writing Python code. When you use sed or awk, you're in a completely different language, with different syntax and different semantics.

No, you are at the same time, learning regular expression. 

> **mssever said:**
> 
But to use them, I need to stay in awk, right? How can I pass a hash around in bash? OK, I know it can be done if you're sufficiently determined, but why not use a language better suited for the task to begin with?

That's why there's Awk , right?

---

### Post by escapee on 2008-09-05
ghostdog74, you seem to be missing what mssever is saying about using awk for text manipulation with bash.  It can be done, yes, and likely as efficient as with other languages alone, but the point is you are still learning bash and awk instead of just learning bash.  With other languages, the text manipulation libraries are included with the syntax of that particular language, therefore there is only 1 language to learn.  And yes, I'm acknowledging bash has built in text manipulation, but it's obviously lacking the power of awk.

I'm no bash expert, but I've done some scripts in bash and learning awk just to work with text in bash is a pain for me, so I appreciate where mssever and the others are coming from.

---

### Post by ghostdog74 on 2008-09-05
> **escapee said:**
> ghostdog74, you seem to be missing what mssever is saying about using awk for text manipulation with bash. 

text manipulation can be done using awk alone. If you are struggling with bash, then you can learn just awk. Most of what bash can do, awk can too.

> 
 With other languages, the text manipulation libraries are included with the syntax of that particular language, therefore there is only 1 language to learn. 

Can you name me some ?

> 
 And yes, I'm acknowledging bash has built in text manipulation, but it's obviously lacking the power of awk.

It depends on the problem to solve. if you want, you can give examples what bash can't do with text.

> 
I'm no bash expert, but I've done some scripts in bash and learning awk just to work with text in bash is a pain for me, so I appreciate where mssever and the others are coming from.
you don't have to learn bash to work with text, if you want, just learn awk.

---

### Post by pmasiar on 2008-09-05
> **ghostdog74 said:**
> this is much easier:
```

arr=( ${arr[@]} $val )

```

That is excellent example for both "love" and "hate" part. For untrained eyes of a beginner, it looks like cartoon cursing. After spending significant efforts to train your eyes (and brain) to parse such patterns, you can see terse  expression.

So, beginner and expert may have diametrally opposite perceptions of the same script of code. Who is right? 

When expert dismisses beginner's opinion, she shows arrogance of an elitist. But is beginner just a lazy whiner? There **are** other more modern languages which make that basic snippet look simpler.

Maybe it is just just a case of misunderstanding: bash was targeted for different audience (sysadmin) at different times (when nobody dreamed about "unwashed masses" having access to such huge computing power on their desk, and nobody would consider wasting 20% of that power on syntax sugar).

---

### Post by slavik on 2008-09-05
you don't learn just bash, you learn bash, awk, sed, tr, bc, and all the other small tools. shell is mainly a way to tie all those tools together to get the job done.

---

### Post by mssever on 2008-09-05
> **ghostdog74 said:**
> text manipulation can be done using awk alone. If you are struggling with bash, then you can learn just awk. Most of what bash can do, awk can too.Perhaps you should start a "Why to love/hate awk" thread. Awk is a distinct language. It's only relation to shell scripting is a common hereitage and the fact that people often mix the two.

> Can you name me some ?Ruby, Python, PHP, Perl, etc.

> you don't have to learn bash to work with text, if you want, just learn awk.True, especially since a number of tasks are difficult in bash without using some external language. But that language could easily be Ruby or Perl, not awk. Or, it could be awk.

---

### Post by ghostdog74 on 2008-09-05
> **mssever said:**
> Perhaps you should start a "Why to love/hate awk" thread. 

Maybe someday. meanwhile, the last link in my sig tells it all.

> 
Ruby, Python, PHP, Perl, etc.

And (g)awk. 

> 
 But that language could easily be Ruby or Perl, not awk. Or, it could be awk.

don't understand -=> not awk, or it could be awk??

---

### Post by mssever on 2008-09-05
> **ghostdog74 said:**
> don't understand -=> not awk, or it could be awk??
I mean, that if you're going to use an external language to do text processing, awk is only one of several good choices.

---

### Post by CptPicard on 2008-09-05
Looks like the thread is off to a good start, a lot of what I would have said has already been said... but let's just grab this one

> **ghostdog74 said:**
> So i don't agree with what CptPicard said.

(I should have added .."using glue language with awkward syntax" :) )

Piping is actually an interesting functional-style transformation of data, which is an interesting paradigm in its own right certainly. I chose it as the main descriptor because it really is an interesting (and different) feature and way of using the shell -- the shell's claim to fame really is the idea of combining small tools to do the job.

But, the text really is "externally semantic"... you're always outputting and parsing some format that you just have to "know" to regex it right. I think the new fancy Microsoft shell had the correct idea IIRC -- data needs to have some type information to it. As it stands we're just using some kind of weak(?) typing via strings. Nasty.

And the fact that the tools are very diverse in usage shouldn't be a point of contention at all. There is so much more man pages to read and learn the particular oddities (often historical in nature) of whatever you're using compared to having apidocs for libraries in some one given language...

---

### Post by mssever on 2008-09-05
> **CptPicard said:**
> Piping is actually an interesting functional-style transformation of data, which is an interesting paradigm in its own right certainly. I chose it as the main descriptor because it really is an interesting (and different) feature and way of using the shellCome to think of it, I'm not sure it's so unique. Consider this case: You have to read multiline input from stdin, sort the lines, strip out all non-unique lines, and print the result to stdout. The way I'd approach this in Ruby is quite similar to the way I'd do it in bash:```
# Bash
text="$(while read line; do echo "$line"; done)"
echo "$(echo "$text" | sort | uniq)"

# Ruby
puts gets.chomp.split("\n").sort.uniq.join("\n")
```Although the Ruby way gives me more flexibility since Array#sort can take a block (Ruby parlance for a closure) containing arbitrary sorting rules. The version of sort used in the Bash example can handle all the common cases, but if you needed a special case, you'd have to use something else.

> And the fact that the tools are very diverse in usage shouldn't be a point of contention at all. There is so much more man pages to read and learn the particular oddities (often historical in nature) of whatever you're using compared to having apidocs for libraries in some one given language...And it's not just manpages. Some commands are documented in info pages, which are a poorly-executed attempt at enabling hyperlinks. Then, there are the builtins, which are documented via the help command. Thus, "man [" and "help [" document two distinct programs. Guess which one you get by default in a shell script?

---

### Post by ghostdog74 on 2008-09-05
> **mssever said:**
> Come to think of it, I'm not sure it's so unique. Consider this case: You have to read multiline input from stdin, sort the lines, strip out all non-unique lines, and print the result to stdout. The way I'd approach this in Ruby is quite similar to the way I'd do it in bash:```
# Bash
text="$(while read line; do echo "$line"; done)"
echo "$(echo "$text" | sort | uniq)"

[code]
cat | sort -u

```
Or am i missing something ?


> 
And it's not just manpages. Some commands are documented in info pages, which are a poorly-executed attempt at enabling hyperlinks. Then, there are the builtins, which are documented via the help command. Thus, "man [" and "help [" document two distinct programs. Guess which one you get by default in a shell script?
I had trouble with man pages when i first started. Don't like it at all. After a while of reading them, i got used to it. man pages are the first thing i go if i forgot a syntax. Whether its info or man page or help, one have to just get used to it. Its simple as that.

---

### Post by CptPicard on 2008-09-05
IMO the defense of "anything is perfectly fine as long as you just take the time to get used to it" is just way too generic and thus flawed ... :) I guess you get used to being *<reference to actions not suitable for family forum>* daily, but I would still not recommend getting to the habit...

---

### Post by ghostdog74 on 2008-09-05
> **CptPicard said:**
> 

(I should have added .."using glue language with awkward syntax" :) )

depending on the situation, there's usually no need to use much glue. If you may, please show an awkward syntax that you encounter.

> 
 the shell's claim to fame really is the idea of combining small tools to do the job.

and these "tools" are just like Ruby/Python/Perl functions and modules. 

> 
But, the text really is "externally semantic"... you're always outputting and parsing some format that you just have to "know" to regex it right. I think the new fancy Microsoft shell had the correct idea IIRC -- data needs to have some type information to it. As it stands we're just using some kind of weak(?) typing via strings. Nasty.

whether its weak typing or default type is string or whatever, the shell knows what to do when you tell it to. what is really nasty?? :)

> 
There is so much more man pages to read and learn the particular oddities (often historical in nature) of whatever you're using compared to having apidocs for libraries in some one given language...

maybe you want to elaborate more on the difference between reading api docs and man pages?

---

### Post by pmasiar on 2008-09-05
Very interesting association what gives shell that power: piping simple text through different tools

> CptPicard put it well when he described it as "piping unstructured externally-semantic text between various complex tools with totally different usage. 

Simple general programming language does not have that power right? Because for every change you need to tweak code deep inside loops? 

Yes and no. Traditional language, yes. But Python has generators, and I found fascinating presentation how to use them for **exactly** such kind of processing: [Generator Tricks for Systems Programmers](http://www.dabeaz.com/generators/) (see page 18-20 of PDF, slide I-35..I-39)

So you can build your filter app 'stacking' one process after another, but you have powerful tool (Python) to build the processing steps exactly as you need.

Of course this is not killer app for someone who spend 10 years to master all those "small sharp tools" with their own idiosyncratic and quirky switch parameters. But for someone just entering the field, learning just one tool beats that.

Again, I am not saying that shell should be ignored. I am saying that now there are much better tools to solve problems which used to require sysadmin with 10 years of experience.

---

### Post by ghostdog74 on 2008-09-05
> **pmasiar said:**
> 
Again, I am not saying that shell should be ignored. I am saying that now there are much better tools to solve problems which used to require sysadmin with 10 years of experience.
Can you give an example of such a problem ?

---

### Post by ghostdog74 on 2008-09-05
> **CptPicard said:**
> IMO the defense of "anything is perfectly fine as long as you just take the time to get used to it" is just way too generic and thus flawed ... :) I guess you get used to being *<reference to actions not suitable for family forum>* daily, but I would still not recommend getting to the habit...

why is it flawed? How much time did you , for example get used to Python's whitespace or other Python warts? It happens everywhere and everything you do. With practice and practice and more practice, one will know what to do.
i am also curious what that <reference to actions ...> mean. :)

---

### Post by CptPicard on 2008-09-05
> **ghostdog74 said:**
> Can you give an example of such a problem ?

You are aware aren't you that most stuff in a typical distro is not written using a combination of shell tools, for good reason? :)

> **ghostdog74 said:**
> why is it flawed?

It is, because I just simply won't agree to believing that anything can be overcome by just "getting used to it" or that before getting used to X and Y, it would not be possible that the other would be easier to "get used to" and that this is actually meaningful.

It seems to me like an argument against all kinds of progress and development of different languages, because obviously if it held, there would be no point.

> How much time did you , for example get used to Python's whitespace or other Python warts?

I still don't like it, but I can live with it. Otherwise Python is actually remarkably wart-free, and has very "sensible defaults", which is the whole point here.

---

### Post by ghostdog74 on 2008-09-05
> **CptPicard said:**
> You are aware aren't you that most stuff in a typical distro is not written using a combination of shell tools, for good reason? :)

most stuff like for example? Please enlighten me because I don't play with distro's much.

> 
It is, because I just simply won't agree to believing that anything can be overcome by just "getting used to it" or that before getting used to X and Y, 

we have to agree to disagree then.



> 
I still don't like it, but I can live with it. Otherwise Python is actually remarkably wart-free, and has very "sensible defaults", which is the whole point here.
there you go. The key words are "can live with it". :) 
Perl hackers can live with it, C/C++ lovers can live with it. Java developers can live with it. AFter a while, all hate becomes love.

---

### Post by CptPicard on 2008-09-05
> **ghostdog74 said:**
> most stuff like for example? Please enlighten me because I don't play with distro's much.

What exactly do you use then, all the time? Take a good, long look inside most source code packages.

> 
we have to agree to disagree then.

So you're saying that something like developing Python has indeed been pointless because obviously, Guido could have just got used to awk?

> AFter a while, all hate becomes love.

No, I couldn't live with brainfuck, INTERCAL, or by that matter, building the analysis toolkit I make my living with in terms of shell scripts. It would be huge pain no matter how much I tried to get used to it. The awk/sed/bash combination of the algorithms would be completely, utterly unreadable.

Mind you, I do use awk for collating data from the resultant huge text files full of numbers. It makes for a handy "command-line spreadsheet".

These kinds of "endless-denial-arguments" à la Lster are really a borderline case of whether they're worth grinding over and over again though...

---

### Post by mssever on 2008-09-06
> **ghostdog74 said:**
> maybe you want to elaborate more on the difference between reading api docs and man pages?
In Ruby or Python, there's a central source for documentation, which is well-indexed (especially Ruby's docs). (And there are command-line tools for when you don't need the full documentation site and just need some quick answers.) In the shell, you're fine if you already know the name of the command you want to learn about. Otherwise, you have to use tools like apropos and hope that you search on the right term.

---

### Post by Sinkingships7 on 2008-09-06
My small input to this conversation: shell scripting should be used in trivial/repetitive system admin tasks, but should not be confused by or used in place of a general-purpose language. If the task is anything more than trivial, it should be done in a general-purpose language, like Python.

---

### Post by ghostdog74 on 2008-09-06
> **CptPicard said:**
> 
So you're saying that something like developing Python has indeed been 
pointless because obviously, Guido could have just got used to awk?

then I might as well say that developing Java is pointless because James Gosling could have got used to Python?? That's obviously not what i meant.

> 
No, I couldn't live with brainfuck, INTERCAL, or by that matter, building the analysis toolkit I make my living with in terms of shell scripts.

then, that's your problem right? Since you are only a programmer and its just impossible for you live out of the box.

> 
 It would be huge pain no matter how much I tried to get used to it. The awk/sed/bash combination of the algorithms would be completely, utterly unreadable.

You have not got the message, that when written properly, giving relevant comments and using the right combination of tools, a piece of shell script (or other codes) can be as readable as hell.

> 
Mind you, I do use awk for collating data from the resultant huge text files full of numbers. It makes for a handy "command-line spreadsheet".

if you have read any of my previous posts, I said that awk is a Programming language and can do much more than just file processing. It just shows your lack of understanding of the tools you use and "getting used to it"

> 
These kinds of "endless-denial-arguments" à la Lster are really a borderline case of whether they're worth grinding over and over again though...
Lster is Lster, me is me. so now you are accusing me of giving you endless-denial-arguments ? I did show code that things can be done right? 

conclusion:
I am just showing the people here who "hates" the shell(tools) because of this and that, that there's really nothing to hate at all.

---

### Post by LaRoza on 2008-09-06
> **ghostdog74 said:**
> 
I am just showing the people here who "hates" the shell(tools) because of this and that, that there's really nothing to hate at all.

The words "love" and "hate" are extreme, but the purpose of these types of threads is more to point out strengths and weakness of their topics instead of having full out religious wars on them. No one (I hope) denies the usefulness of shell scripting and all respect those with skill (ghostdog74, everyone on this forum is in awe of your shell skills).

---

### Post by ghostdog74 on 2008-09-06
> **LaRoza said:**
> The words "love" and "hate" are extreme, but the purpose of these types of threads is more to point out strengths and weakness of their topics instead of having full out religious wars on them.

maybe we should change similar thread topics to "The strengths/weakness of blah language." I do acknowledge strengths, however i also believe weaknesses can be overcome.

---

### Post by ghostdog74 on 2008-09-06
> **Sinkingships7 said:**
> My small input to this conversation: shell scripting should be used in trivial/repetitive system admin tasks, but should not be confused by or used in place of a general-purpose language. If the task is anything more than trivial, it should be done in a general-purpose language, like Python.
this is not to disprove your believes or anything like that, i am just still curious what kind of things are "general purpose" that the shell+tools cannot provide? Care to enlighten me one more time?

---

### Post by Sinkingships7 on 2008-09-06
> **ghostdog74 said:**
> this is not to disprove your believes or anything like that, i am just still curious what kind of things are "general purpose" that the shell+tools cannot provide? Care to enlighten me one more time?

It's not to say that the shell (and compliments) cannot provide the functionality that one could achieve through a general-purpose language (Python, Ruby), but that after a certain point of task complexity is surpassed, it becomes inefficient and unmanageable to perform such a task in a shell scripting language, as opposed to the readability and to-the-point syntax of said "general-purpose" language.

---

### Post by LaRoza on 2008-09-06
> **ghostdog74 said:**
> maybe we should change similar thread topics to "The strengths/weakness of blah language." I do acknowledge strengths, however i also believe weaknesses can be overcome.

Overcoming a weakness is not the same as not having it ;) 

> **ghostdog74 said:**
> this is not to disprove your believes or anything like that, i am just still curious what kind of things are "general purpose" that the shell+tools cannot provide? Care to enlighten me one more time?

You always ask about general purpose and get lots of answers. My answer about "doing simple text handling to 3d games" didn't satisfy the criteria, so I don't know what will.

Unix tools and the shell are aimed more at system administration, which is a vital yet restricted goal. It can be used for other things, but it is not well suited for it.

Python and Ruby (for example) on the other hand can do the things the shell and Unix tools can do (at the simplest, Python or Ruby would be overkill) but can be used easily for a more diverse range.

If one wanted to get a listing of the contents of the directory, it would be trivial to do in the shell, and extremely simple to do in Python, but on this extreme, using the shell is the easiest way unless one wants cross platform solutions. However, if one wanted to make a more complex GUI'd app, it could be done in the shell with a bit of work, but would be much easier to do in Python or Ruby. And when you get to tasks which are more complicated or require more flexibility (complex GUI's, etc), Python and Ruby win out totally.

---

### Post by ghostdog74 on 2008-09-06
> **Sinkingships7 said:**
> It's not to say that the shell (and compliments) cannot provide the functionality that one could achieve through a general-purpose language (Python, Ruby), but that after a certain point of task complexity is surpassed, it becomes inefficient and unmanageable to perform such a task in a shell scripting language, as opposed to the readability and to-the-point syntax of said "general-purpose" language.

So let me iterate again your definition of "general purpose". Its that you can do a lot of things in just one language correct? Do you consider external modules that say, lets you program a game, ( such as pygame ) being part of "general purpose" ? Note: The key word is external module done by third party. Without it, do you think you can program games in just Python itself? Here's my definition: If I could find a games "api" that can be used in shell scripts for example, I am calling it a "general purpose language" as well. you can disagree with me but that's how I view things from a different angle.

---

### Post by mssever on 2008-09-06
> **ghostdog74 said:**
> You have not got the message, that when written properly, giving relevant comments and using the right combination of tools, a piece of shell script (or other codes) can be as readable as hell.First, some languages naturally lend themselves to clarity, so that even noobs who don't know how to write clear code will still turn out something manageable (though I once saw a Python script using single-space indents and no comments or blank lines anywhere, which proves the futility of fool-proofing your design).

Secondly, even in the hands of experts, some languages are more readable than others. I'd guess that even an expert would have a hard time writing readable code in Whitespace. Or consider Perl. Readable Perl does exist, but it's uncommon, and readable Perl is harder to understand at a glance than mediocre Python.

> **LaRoza said:**
> ghostdog74, everyone on this forum is in awe of your shell skills.
+1
[quote=ghostdog74]maybe we should change similar thread topics to "The strengths/weakness of blah language."[/quote]I'm game. Last I knew, regular users didn't have the right to rename threads, but if a mod wants to rename this thread according to the suggestion, I'm fine with it. Note: This is not a request; it's permission.

---

### Post by ghostdog74 on 2008-09-06
> **LaRoza said:**
> Overcoming a weakness is not the same as not having it ;) 

Nothing is perfect in this world. 
> 

You always ask about general purpose and get lots of answers. My answer about "doing simple text handling to 3d games" didn't satisfy the criteria, so I don't know what will.

see reply to sinkingship

---

### Post by mssever on 2008-09-06
> **LaRoza said:**
> However, if one wanted to make a more complex GUI'd app, it could be done in the shell with a bit of work, but would be much easier to do in Python or Ruby. And when you get to tasks which are more complicated or require more flexibility (complex GUI's, etc), Python and Ruby win out totally.
To elaborate: You can make basic GUIs using tools like zenity. But let's suppose I want to make a music player (for example) and I want to follow the Gnome HIG. That's far beyond zenity's ability, and AFAIK there's no sufficiently-capable tool to do this from the shell. But that's quite possible from a language which provides full Gnome and GTK bindings.

---

### Post by LaRoza on 2008-09-06
> **ghostdog74 said:**
> 
see reply to sinkingship

I understand but as pmasiar often says "In theory, there is no difference between practice and theory. In practice, there is" or something like that.

To illustrate this, try to make this with shell tools: [http://ubuntuforums.org/showthread.php?t=908423](http://ubuntuforums.org/showthread.php?t=908423)

Simple it is, but not for shell. I don't even think it is possible, but I'd be willing to be proved wrong (and look forward to it)

> **mssever said:**
> To elaborate: You can make basic GUIs using tools like zenity. But let's suppose I want to make a music player (for example) and I want to follow the Gnome HIG. That's far beyond zenity's ability, and AFAIK there's no sufficiently-capable tool to do this from the shell. But that's quite possible from a language which provides full Gnome and GTK bindings.
There are some other such things, but they all have more limits than using a toolkit to its fullest and I was also taking OpenGL and SDL into account as being a GUI. Even that shooter game in Python (a single file) is beyond what I think shell scripts can do.

---

### Post by ghostdog74 on 2008-09-06
> **mssever said:**
>  and AFAIK there's no sufficiently-capable tool to do this from the shell. But that's quite possible from a language which provides full Gnome and GTK bindings.
I am sure there [are](http://www.gtk-server.org/). I have not used [them](http://www.satisoft.com/satshell/), but definitely worth a look .

---

### Post by ghostdog74 on 2008-09-06
> **LaRoza said:**
> 

To illustrate this, try to make this with shell tools: [http://ubuntuforums.org/showthread.php?t=908423](http://ubuntuforums.org/showthread.php?t=908423)

Simple it is, but not for shell. I don't even think it is possible, but I'd be willing to be proved wrong (and look forward to it)


[Not impossible](http://www.gtk-server.org/apps.html). 


>  Even that shooter game in Python (a single file) is beyond what I think shell scripts can do.
As above.

---

### Post by LaRoza on 2008-09-06
> **ghostdog74 said:**
> [Not impossible](http://www.gtk-server.org/apps.html). 

As above.

The py version works in Windows also. How easily does that work in Windows?

(Part of criteria ;))

---

### Post by DavidBell on 2008-09-06
I don't do shell scripting at all, but use micro distro Puppy Linux a little bit. It doesn't have python so a lot of it's utilities use shell with Gtkdialog. It's very successfull, you wouldn't know they were done with bash, and it's a step up from  for eg easygui IMO. 

Only problem I have with it is that it seems to often throw up a sequence of semi-sophisticated messageboxes in place of all-in-one-place wizards, not sure if this is a limitation of gtkdialog or just the way they chose to code it. DB

---

### Post by ghostdog74 on 2008-09-06
> **LaRoza said:**
> The py version works in Windows also. How easily does that work in Windows?

(Part of criteria ;))

From the [FAQ](http://www.gtk-server.org/faq.html). See under COMPILATION.

---

### Post by jimi_hendrix on 2008-09-06
> **lucho64 said:**
> if ["a"=="a"]; then echo yes; else echo no; fi

Ok, not quite the example you were asking for, but somebody with, say C background only, will trip over that one. And I actually like bash.

i know nothing of bash other then what its used for and i can understand that with a C/C++/C# background...(it was one of the few things i can understand on this page :))

anyway from looking at some of these posts i think bash helps give the user a better way to interact with the OS (like the terminal is)...you dont see anyone writing scripts to run in cmd prompt in windows...it does look very unfriendly as a syntax though

---

### Post by pmasiar on 2008-09-06
> **ghostdog74 said:**
> Can you give an example of such a problem ?

I just did? How to analyze logs using generators instead of piping tools using shell, and explained why. Maybe you need to pay more attention before you reflexively disagree next time? ;-)

---

### Post by pmasiar on 2008-09-06
> **ghostdog74 said:**
> why is it flawed? How much time did you , for example get used to Python's whitespace 

I decided to go with Perl for my early project, because that was my medical-educated colleague used, and I irrationally rejected the idea if significant whitespace.

After having to maintain (even read!) her code ("I cannot put there 'use strict;' -- it breaks my code ) and endless discussion with another cowboy coder, whose style was unlike anything else I ever seen, I realized that significant whitespace and having common style **might** be good idea.

Then, it took me about 15 minutes to go from:
"ok, I'll just learn it" 
"it's not that bad" 
"not bad at all!"
"I LOVE it"
all the way to:
"why all other languages cannot be like that"

Try it, might work for you too :-)

---

### Post by ghostdog74 on 2008-09-06
> **pmasiar said:**
> I just did? How to analyze logs using generators instead of piping tools using shell, and explained why. Maybe you need to pay more attention before you reflexively disagree next time? ;-)
Some people know how to analyse logs without generators so i don't get why you say generators are better than shell tools to analyse logs.

---

### Post by ghostdog74 on 2008-09-06
> **pmasiar said:**
> 
"why all other languages cannot be like that"

because not everyone is pmasiar and thinks like pmasiar. I know i am one of that kind. :)


> 
Try it, might work for you too :-)

lol, I have many years of experience with Python. I started using it in 1997/8 when it was still in 1.5. If you have already not known, I love it till now. However,  I also don't hate my other programming tools. I just know when,how,why to use them under what circumstances.

---

### Post by pmasiar on 2008-09-06
> **ghostdog74 said:**
> lol, I have many years of experience with Python. I started using it in 1997/8 when it was still in 1.5. If you have already not known, I love it till now. However,  I also don't hate my other programming tools. I just know when,how,why to use them under what circumstances.

Good for you then.

I am not expert in shell tools of your class, and not likely will ever become: too many years wasted in Windows. But not all people are like you either :-) Many do not have time or need to dive for 10 years into shell tools to learn them all, including quirks. For those, non-shell solutions, like Python, are godsend.

Python was exactly **designed** for people who have better things to learn than master shell and C and XYZ. Python allows them to solve most of those problems with single tool, possibly learning a library or two as needed, but united by single language. 

IMHO, unless person is sysadmin, bare basics of shell is enough, and time is better invested in universal language and it's libraries than many small shell tools. And of course taking your local sysadmin expert to a lunch once in a while, so when you need him, he remembers you :-)

---

### Post by LaRoza on 2008-09-06
> **pmasiar said:**
> 
Python was exactly **designed** for people who have better things to learn than master shell and C and XYZ. Python allows them to solve most of those problems with single tool, possibly learning a library or two as needed, but united by single language. 

+1 Python is a language that will do well as the only known language, and the person will not be severely limited. Knowing Windows Batch, Bash or other's is handy, but limiting. Someone comfortable with Python can write programs easily for any OS in common use, take advantage of its many standard modules, easily use other libraries for various GUI toolkits and designers, math and science, and multimedia and browser engines and more.



> 
IMHO, unless person is sysadmin, bare basics of shell is enough, and time is better invested in universal language and it's libraries than many small shell tools. And of course taking your local sysadmin expert to a lunch once in a while, so when you need him, he remembers you :-)
The only systems I have to admin are my own computers. I know enough shell scripting to do what it would be easiest to do in, for everything else, there's C and Python.

---

### Post by ghostdog74 on 2008-09-06
> **pmasiar said:**
>  Many do not have time

a common excuse :) no doubt. Those who give such excuses do not know how to time manage.

> 
 or need to dive for 10 years into shell tools to learn them all, 

I can tell you, you don't need 10 years. awk makes learning wc/cut/sed/(e)grep/tr/cat/paste/comm/join/bc including most of bash and many others unnecessary. If only they knew...

---

### Post by slavik on 2008-09-06
there is a reason why shells go into /bin but perl/python/ruby interpreters go into /usr/bin ...

---

### Post by pmasiar on 2008-09-06
> **ghostdog74 said:**
> a common excuse :) no doubt. Those who give such excuses do not know how to time manage.

Would you tell it to bio-researcher working on cure for cancer? I work with those. You seems to be stuck in sysadmin world. There is world outside managing linux boxes, and people use computer to solve interesting real-world problems, not sure why you pretend ignoring that.

---

### Post by ghostdog74 on 2008-09-06
> **pmasiar said:**
> Would you tell it to bio-researcher working on cure for cancer? I work with those. 
Everybody needs to manage their time well for doing things. I am not sure where you are coming from.

> 
You seems to be stuck in sysadmin world.

I can say the same to you 

> 
 There is world outside managing linux boxes, and people use computer to solve interesting real-world problems, not sure why you pretend ignoring that.
You pretend that i don't know about these.

---

### Post by slavik on 2008-09-07
> **pmasiar said:**
> Would you tell it to bio-researcher working on cure for cancer? I work with those. You seems to be stuck in sysadmin world. There is world outside managing linux boxes, and people use computer to solve interesting real-world problems, not sure why you pretend ignoring that.
and for cases like yours, there is Haskell (sorry, too tempting).

---

### Post by pmasiar on 2008-09-07
> **ghostdog74 said:**
> Everybody needs to manage their time well for doing things. 

Exactly. And for many people, becoming expert in shell tools is not efficient use of their time, and solving those problems in substantially more advanced general language like Python (which they can use also to build website, parse text file, or glue numeric calculations with R) is better use of their time. And there is hardly anything you can do, calling them 'lazy' and lacking time management skills just shows your lack of understanding.

I never said that shell is useless. Certainly, experienced sysadmin can solve some problems very easy - as you proved you can, by helping posters.

But I strongly disagree with your thesis that if shell is good for sysadmin, everyone should master it. That's ridiculous waste of time for most people.

So when you put equal signs between lazy bums
who cannot manage time, and bioresearcher solving problem, I can tell you that you are full of it. You just lost the perspective.

It is just arrogance of old-school sysadmin, who has hard time to accept that usability of his once valuable skills are diminishing, and any kid can
parse/merge text files and shuffle them to cluster for processing - if it is done in Python.

And it's not like those syadmins will have less work to do: because we have more computers, in more complex clusters, it will be more work. But it will be more complex orchestration of more complex processing workflow (merge data, split them for cluster, then merge results), for which Python might be superior.

And you already know Python, you just want to sell buggy whip to car owners, because you have really good buggy whip. And you are upset because many people do not care.

OK I am not going to waste time in this discussion. I am sure you know your awk, shell etc, and I wish I know it as you do. But I don't plan to learn it anytime soon, because I am too busy learning biology/bioinformatics side of the problem - it would be better use of my time, together with Python, to solve real problems in Python, which I can do as easy as you with awk, and my scientists colleagues would be able to expanf on my Python solutions, but would be quite lost with awk.

Any reader has enough information to make own mind regarding whose situation and whose solution is closer to his own, and decide accordingly:

For some, shell/awk/other tools is appropriate, for many, Python+libraries is simpler better solution.

Have a nice day.

---

### Post by ghostdog74 on 2008-09-07
> **pmasiar said:**
>  
OK I am not going to waste time in this discussion.
good, me too. sorry, i did not read your crap. This is the only sentence that make sense.

---

### Post by LaRoza on 2008-09-07
Now that everyone has it out of their system... please try to be respectful towards each other from now on.

---

### Post by CptPicard on 2008-09-07
> **ghostdog74 said:**
> sorry, i did not read your crap.

Explains a lot -- it really *is* Lster all over again, just in a different shape and form. I miss the guy in the sense that getting him here on this thread to argue against you that you'd write everything in assembler if you just were as smart as he is enough would have been just perfect :)

Looked into the Firefox or X server codebase yet? I would be interested in hearing how shell tools would in particular help you model the applications in a reasonably readable and manageable way...

---

### Post by pmasiar on 2008-09-07
> **ghostdog74 said:**
> good, me too. sorry, i did not read your crap. This is the only sentence that make sense.

Now **your** arguments make sense too. You argued from position that reading what I wrote is not nercessary... :-(

I am sorry but I **did** read your arguments, and did tried to understand your point. Now I know that I wasted time writing my point, because you did not read it.

Oh well. maybe other people will read it, and will make more informed decision that you did.

---

### Post by ghostdog74 on 2008-09-07
while I very much like to continue "arguing", i find it that will be useless and a waste of time since my POV is very different from any of you. Whatever it is, I will still respond to queries about the shell+tools and how you should not hate it to the best of my knowledge. Nothing more.

---

### Post by nvteighen on 2008-09-08
> **ghostdog74 said:**
> while I very much like to continue "arguing", i find it that will be useless and a waste of time since my POV is very different from any of you. Whatever it is, I will still respond to queries about the shell+tools and how you should not hate it to the best of my knowledge. Nothing more.
I'm sure people will appreciate your help on shell tools' issues :)

---

### Post by TheUbGuy on 2008-09-08
> **Sinkingships7 said:**
> My small input to this conversation: shell scripting should be used in trivial/repetitive system admin tasks, but should not be confused by or used in place of a general-purpose language. If the task is anything more than trivial, it should be done in a general-purpose language, like Python.

I'd have to disagree with you on this. I've been in the computer/programming industry for over twenty years. Shell scripting is not relegated to just 'trivial' or sysadmin tasks. Many organizations use scripting (in particular, Kornshell) to handle their business needs. Kornshell (ksh93) is exceptionally robust, and it can handle some very difficult tasks. Sure, it is command-line and not a pretty GUI, but it can handle the most complex tasks surprisingly well.

Python is a good multi-purpose language; so is Perl. However, unless an organization is Perl/Python based, their use may not even be allowed, as code needs to be maintained, and if an organization only has 1 or 2 people in-house that could maintain code, they are not going to want production jobs written in a language that they can not maintain. But, with a UNIX-based organization, it's easy to find resources to maintain shell scripts.

Again, I have nothing against Python or Perl - I just don't think that saying shell scripting should be relegated to trivial or sysadmin tasks is a good position.

---

### Post by LaRoza on 2008-09-08
> **TheUbGuy said:**
> I'd have to disagree with you on this. I've been in the computer/programming industry for over twenty years. Shell scripting is not relegated to just 'trivial' or sysadmin tasks. Many organizations use scripting (in particular, Kornshell) to handle their business needs. Kornshell (ksh93) is exceptionally robust, and it can handle some very difficult tasks. Sure, it is command-line and not a pretty GUI, but it can handle the most complex tasks surprisingly well.

What type of tasks?

I looked up the Kornshell and saw it had features not found in other shells (specially, Bash) and its scripting language seems to be designed almost like a Perl like language. This sort of proves the point that for non trivial/sysadm tasks, the shell is less suitable in that the shell that you are saying is good for that is unique among shells in its features.

---

### Post by TheUbGuy on 2008-09-08
> **LaRoza said:**
> 
I looked up the Kornshell and saw it had features not found in other shells (specially, Bash) and its scripting language seems to be designed almost like a Perl like language. This sort of proves the point that for non trivial/sysadm tasks, the shell is less suitable in that the shell that you are saying is good for that is unique among shells in its features.

Huh??? :confused:

Kornshell is considered the *standard* shell for many operating systems, like AIX, etc. Though just about all flavors of UNIX(Solaris, AIX,HP-UX, etc) allow the use of other shells like bash, tcsh, etc. It is still a standard Shell. So, just because Kornshell has great features, that proves that shell is less suitable because Kornshell is a unique shell and therefore shouldn't be considered? Sorry, that is totally illogical. Since Kornshell use is very widespread, you just can't exclude it when discussing the suitability of UNIX shell scripting just because you feel it has more advanced features than other shells!

---

### Post by LaRoza on 2008-09-08
> **TheUbGuy said:**
> 
Kornshell is considered the *standard* shell for many operating systems, like AIX, etc. Though just about all flavors of UNIX(Solaris, AIX,HP-UX, etc) allow the use of other shells like bash, tcsh, etc. It is still a standard Shell. So, just because Kornshell has great features, that proves that shell is less suitable because Kornshell is a unique shell and therefore shouldn't be considered? Sorry, that is totally illogical. Since Kornshell use is very widespread, you just can't exclude it when discussing the suitability of UNIX shell scripting just because you feel it has more advanced features than other shells!

No one says the shell can't be used for more than what they claim it is best for, just that it gets less suitable as you diversify. The more suitable shells for such tasks have more inbuilt features. Many of them are cross platform. So one could say the pinnacle of that progression is a completely independant cross platform language, like Python or Ruby or Perl.

---

### Post by CptPicard on 2008-09-08
> **TheUbGuy said:**
> 
Kornshell is considered the *standard* shell for many operating systems, like AIX, etc.

Just like bash (or dash) is considered the *standard* shell on Linux, and others are the exception.

And just as Python installations are becoming so commonplace that you usually find it out of the box.

IMO the argument that "the shell" is found on all boxes and Python (which is usually found by default as *the same Python as anywhere else* or easily installed) is a liability an organisation won't find coders for is leaking here :)

> So, just because Kornshell has great features, that proves that shell is less suitable because Kornshell is a unique shell and therefore shouldn't be considered? Sorry, that is totally illogical. 

The logical argument would allow other languages to be equally considered, then. In particular languages like Python or Perl are way more consistent as "platforms", actually way more widespread on Linux than kornshell and are easier to find code monkeys for (hey, even I write pretty decent Python and suck at shell magic!)

---

### Post by LaRoza on 2008-09-08
> **CptPicard said:**
> 
The logical argument would allow other languages to be equally considered, then. In particular languages like Python or Perl are way more consistent as "platforms", actually way more widespread on Linux than kornshell and are easier to find code monkeys for (hey, even I write pretty decent Python and suck at shell magic!)
That was what I was trying to show, a progression from shells with few features, relying on other apps specific to its host to a full featured, cross platform language. The shells show a lot of diversity, with some of the more feature rich seeming to be straining to be more than a shell. Python and Ruby are general purpose programming languages, that allow shell like use. So things best suited for shell work can be a little extra work in Python, but the overlap is great and the other abilities of Python put it way beyond any shell.

---

### Post by CptPicard on 2008-09-08
> **LaRoza said:**
> That was what I was trying to show

Yeah, we were typing at the same time... +1

---

### Post by TheUbGuy on 2008-09-08
> **CptPicard said:**
> Just like bash (or dash) is considered the *standard* shell on Linux, and others are the exception.

And just as Python installations are becoming so commonplace that you usually find it out of the box.

IMO the argument that "the shell" is found on all boxes and Python (which is usually found by default as *the same Python as anywhere else* or easily installed) is a liability an organisation won't find coders for is leaking here :)



The logical argument would allow other languages to be equally considered, then. In particular languages like Python or Perl are way more consistent as "platforms", actually way more widespread on Linux than kornshell and are easier to find code monkeys for (hey, even I write pretty decent Python and suck at shell magic!)

Yes, bash is the defacto 'standard' on Linux - though like most flavors of UNIX, you can pretty much pick your shell, including Kornshell.

Whereas Perl is pretty much installed by default on larger systems, while you will see Python on most Linux systems, a lot of times it is not installed by default on AIX, Solaris, etc boxes. This may be the way the particular sys admin set the box up, of course, or it could be that it isn't used in the organization (i.e. not a 'standard') and therefore they don't install it.

You may have misunderstood me - I did not intend to imply that Python is a liability. However, many organizations look for UNIX skills, and if they do a lot of shell scripting, they hire people conversant in shell programming as well as generalized UNIX knowledge. You can do a lot with things like awk :-) ! Knowing Perl or Python may be nice, but if it isn't their focus, it will not be something they will want their staff coding in, because, again, it needs to be maintained, and they may not WANT to have to hire outside help for a process that was written by someone who has left the organization and they have no one on staff who is a Python/Perl/Tcl whatever programmer.

My point was simply this -people shouldn't dismiss shell script programming as being for trivial or sys admin-only tasks. That's simply not true. I have nothing against Perl or Python. In fact, I just recently picked up an O'reilly book on Python and am beginning to get into it - gotta love the whitespace :-). I will no doubt do a lot on my own Linux box.  I'm also now in an organization that uses a lot of Linux systems, instead of larger AIX/Solaris boxes. They seem to be more open with what can be used, versus the last organization I was at. Who knows, maybe I'll end up using Python at work too!

---

### Post by mssever on 2008-09-08
It's also worth noting that shell scripting isn't necessarily portable--even if you use the same shell throughout. The GNU folks have extended the standard UNIX tools in a number of ways, which means that a shell script might not work on non-GNU systems unless you develop it with the various POSIX compatibility options and environment variables. My webhost runs FreeBSD, and when I copied over my aliases, some of them failed because I used GNU-style long options (if the other Unices were smart, they'd copy GNU-style long options since they're such a good idea).

My basic approach is to ignore the commercial Unices (since I don't get paid to care about them). As for the *BSDs, they should be willing to copy good ideas from the GNU project. If they aren't, that's their loss. Why should I use primitive tools when I can have the GNU extensions?

---

### Post by LaRoza on 2008-09-08
> **TheUbGuy said:**
> 
My point was simply this -people shouldn't dismiss shell script programming as being for trivial or sys admin-only tasks. That's simply not true. I have nothing against Perl or Python. In fact, I just recently picked up an O'reilly book on Python and am beginning to get into it - gotta love the whitespace :-). I will no doubt do a lot on my own Linux box.  I'm also now in an organization that uses a lot of Linux systems, instead of larger AIX/Solaris boxes. They seem to be more open with what can be used, versus the last organization I was at. Who knows, maybe I'll end up using Python at work too!

Well, sysadmin isn't all that easy, so that is not dissing shell scripting. For "trivial" that is in reference to other capabilities, like GUI's and such, where shell scripts aren't the most flexible.

---

### Post by weresheep on 2008-09-08
I guess I'm in the minority because I love shell scripting. To me its one of the most important aspects and advantages of GNU/Linux (well Unix in general really).

The main argument against writing shell scripts put forward in this thread seems to be you have to learn the various tools (e.g. find/[ef]grep/sed/awk). What I don't get is how come people don't know these tools, at least a little, already?

Don't people use these tools all the time, just using their computer?

I'm sure Python is a nice language for a certain class of problems but when it comes to scripting, I can't see why I'd want to use a general purpose programming language instead of the specialised tools that I have at my finger tips.

-weresheep

---

### Post by pmasiar on 2008-09-08
> **weresheep said:**
> you have to learn the various tools (e.g. find/[ef]grep/sed/awk). What I don't get is how come people don't know these tools, at least a little, already?

Don't people use these tools all the time, just using their computer?

You will be surprised how many people can use computer without **any** knowledge of sed and awk. :-)

> I can't see why I'd want to use a general purpose programming language instead of the specialised tools that I have at my finger tips.

Maybe because I already have python at my fingertips? 8-)

I guess it depends what you consider your main job. If you are sysadmin and use all those tools daily, you are in different weight category than me -- app developer, and I do sysadmin tasks only when I have too, as little as I can get away with, and with least amount of learning: just enough to get back to programming.

So my main point is: don't feel like you have to invest a year of life to master all those shell tools (sed, awk etc) before being able to do anything in Linux. **For me** just the opposite seems to work good enough: start with applications, and learn as little as you need.

It's not like I would not love to be shell expert like ghostdog. But with my limited time, my learning priorities are elsewhere, and I think this approach might work for others, too. I might be wrong, I was wrong before :-)

---

### Post by mssever on 2008-09-08
> **weresheep said:**
> The main argument against writing shell scripts put forward in this thread seems to be you have to learn the various tools (e.g. find/[ef]grep/sed/awk). What I don't get is how come people don't know these tools, at least a little, already?I know the Unix tools (well, my knowledge of awk is minimal) and I've been using Linux for ten years, doing a fair amount of sysadmin stuff, mostly involving the shell in one way or another. I was fairly proficient at shell scripting--though not at ghostdog's level--and liked it OK. Then I learned Ruby and realized that a lot of the tasks I did regularly were just plain easier in Ruby than in Bash+tools. Previously, I'd been a bit of a blub (see my sig). I don't dislike the shell; it's a wonderful interactive language, and a lot better than the DOS shell. But I hope I can educate a few blubs (I'm not calling you a blub, since I don't know you well enough to know whether you're a blub or not).

---

### Post by weresheep on 2008-09-08
[quote=pmasiar]
You will be surprised how many people can use computer without **any** knowledge of sed and awk.
[/quote]

Absolutely, but I would have thought that the overlap of people who require scripting ability with those who know the Unix tool set (on a *nix system) would be quite large.

[quote=pmasiar]
Maybe because I already have python at my fingertips?

I guess it depends what you consider your main job. If you are sysadmin and use all those tools daily, you are in different weight category than me -- app developer, and I do sysadmin tasks only when I have too, as little as I can get away with, and with least amount of learning: just enough to get back to programming.
[/quote]

Perhaps we are two very different users. When I use my computer, its a shell that is at my finger tips. Its a shell I use for email, coding, VCS, playing music, browsing the web (when remote accessing the computer), IRC and file management. So when I want to automate e.g. downloading of files, my first instinct is to wrap around the commands I use interactively in a shell script. Same for ripping CDs, backing up data, managing my todo list and reminders etc.

Maybe I'm just weird :p

[quote=mssever]
Then I learned Ruby and realized that a lot of the tasks I did regularly were just plain easier in Ruby than in Bash+tools.
[/quote]

I fully support the idea behind using the best tool for the job, and if you find Ruby (or Python etc.) a superior / more productive tool I would agree it would be silly to use the shell. I guess I was just taken aback by the sheer amount of people arguing against shell scripting.

[quote=mssever]
But I hope I can educate a few blubs (I'm not calling you a blub, since I don't know you well enough to know whether you're a blub or not).
[/quote]

I haven't come across that term before and I've only had a quick scan at the links you provided but I think I get the concept. How do you tell someone who has actually no use for a new language / feature from someone who only thinks they have no use for it?

-weresheep

---

### Post by mssever on 2008-09-08
> **weresheep said:**
> How do you tell someone who has actually no use for a new language / feature from someone who only thinks they have no use for it?
That would be difficult to tell, unless the person had actually had sufficient experience in the language, etc. to be able to really know. As pointed out in the thread I linked to, being a blub isn't derogatory necessarily. We all go though that stage. But some people seem to be determined to remain a blub.

I that recognizing one's own deficiencies is the first step towards non-blubness.

---

### Post by CptPicard on 2008-09-08
> **TheUbGuy said:**
> 
However, many organizations look for UNIX skills, and if they do a lot of shell scripting, they hire people conversant in shell programming as well as generalized UNIX knowledge.

Well, then they have a very specific requirement for that, and I 100% understand their needs. :) I am a "general-purpose programmer" so therefore I argue "against" shell scripting from the position of someone who is writing a general app, and to hack it together in shell is a no go -- although certainly my own business runs on a server that has certain small scripts doing housekeeping and cron jobs on the server.

> 
My point was simply this -people shouldn't dismiss shell script programming as being for trivial or sys admin-only tasks.

I suppose calling it "trivial" is too strong fighting words... I suppose the central argument against shell scripting is that trivial things are not trivial enough in it, and nontrivial things are extremely nontrivial.

> **weresheep said:**
> I guess I'm in the minority because I love shell scripting. To me its one of the most important aspects and advantages of GNU/Linux (well Unix in general really).

Yes, it is, for its specialized purpose. However, if I got to redo the whole thing from scratch, I would "orthogonalize" the shell by making the "API" more consistenta and smaller and maybe adding some kind of metadata to streams... but then we would already be approaching a more general-purpose language instead of a collection of diverse tools hacked together in whichever way you can.

> 
The main argument against writing shell scripts put forward in this thread seems to be you have to learn the various tools (e.g. find/[ef]grep/sed/awk). What I don't get is how come people don't know these tools, at least a little, already?

It's not about not knowing them, it's about having a critical attitude towards them compared to alternatives :)

(Btw, awk and sed *are* nice for text file processing, but I formulate just a small part of all of my computation in terms of text file processing...)

> 
I'm sure Python is a nice language for a certain class of problems but when it comes to scripting, I can't see why I'd want to use a general purpose programming language instead of the specialised tools that I have at my finger tips.


The whole argument here is that Python is a nice general-purpose language for pretty much any problem, but shell tools are specialized tools you want to use for specialized problems.

---

### Post by ghostdog74 on 2008-09-09
> **weresheep said:**
> 
Maybe I'm just weird :p

you are just different.

---

### Post by LaRoza on 2008-09-09
> **ghostdog74 said:**
> you are just different.

Yes, another word for weird... :-)

---

### Post by weresheep on 2008-09-09
[QUOTE=mssever]That would be difficult to tell, unless the person had actually had sufficient experience in the language, etc. to be able to really know. As pointed out in the thread I linked to, being a blub isn't derogatory necessarily. We all go though that stage. But some people seem to be determined to remain a blub.

I that recognizing one's own deficiencies is the first step towards non-blubness.[/QUOTE]

But wouldn't that make just about everyone a blurb due to the fact that very few people can have gained enough experience in every languange to be able to knowingly decide which is the best for their task?

At some point you have to sit down and do some work rather than seeking out an even better tool for the job.

[QUOTE=CptPicard]
The whole argument here is that Python is a nice general-purpose language for pretty much any problem, but shell tools are specialized tools you want to use for specialized problems.
[/QUOTE]

I'm sure Python is a nice general purpose language. But shell scripting is about glueing together those specialised tools to get the job done. Why would you recreate the functionality of specialised tools in a general purpose programming language to accomplish something?

Or are you saying Python and its libraries are a superset of the Unix tools (or a large enough subset) and therefore you have all the functionality of the common tools via a consistent API?

-weresheep

---

### Post by CptPicard on 2008-09-09
> **weresheep said:**
> But wouldn't that make just about everyone a blurb due to the fact that very few people can have gained enough experience in every languange to be able to knowingly decide which is the best for their task?

Well, one has to understand that everyone is blub at something (or even at most things), but the lesson to be learned is that it is very valuable to understand the concept... that arguments of the kind "I really can't see the point of using X of Y because I've never used Y" should at least give pause to the person presenting them. They are, at the very least, *not* proof of the someone actually using Y being *wrong* (as has been suggested here occasionally) :)

> 
Why would you recreate the functionality of specialised tools in a general purpose programming language to accomplish something?

Why do I code my multithreaded parallelized crossplatform number-crunching analyzer application that needs to talk to a remote web server via http in Java instead of a combination of wget, sed, bash, awk and multiple processes that communicate via some sort of pipe or whatever? That would be an awfully fragile and completely non-understandable hodgepodge, no matter what ghostdog would say that I just need to learn to take the pain and manage my time better :)

I am doing this the way I do it (and the way any sane person would do it) exactly because a general purpose programming language is way more consistent, type-safe, allows for building of complex data structures and the expression of fairly difficult algorithms... I guess awk would come closest to what I need to do, but still, expressing my computation as a set of regexp-triggers on lines would be a stunt, not the rational thing to do.

> 
Or are you saying Python and its libraries are a superset of the Unix tools (or a large enough subset) and therefore you have all the functionality of the common tools via a consistent API?

Well... sort of. There is a difference between a set of specialized tools glued together any way you can and a good general-purpose language with assorted libraries. It's the consistent syntax and semantics of a hopefully fairly small set of language primitives that extends to anything and everything, plus the addition of a robust type system that models data the same way across libs and guarantees its consistency etc, that makes the difference.

Just out of curiosity, do you do any "actual" programming outside of the shell?

---

### Post by ghostdog74 on 2008-09-09
> **CptPicard said:**
> 
Why do I code my multithreaded parallelized crossplatform number-crunching analyzer application that needs to talk to a remote web server via http in Java 
what is that application called? just curious;)
BtW, i am not a "Shell/awk/tools is the GOD of programming language" kind of person, if you have read my posts carefully.

---

### Post by ghostdog74 on 2008-09-09
> **LaRoza said:**
> Yes, another word for weird... :-)
i am sure you know the difference. If not, there's a always a thing called the dictionary :)

---

### Post by Greyed on 2008-09-09
> **weresheep said:**
> I'm sure Python is a nice general purpose language. But shell scripting is about glueing together those specialised tools to get the job done. Why would you recreate the functionality of specialised tools in a general purpose programming language to accomplish something?

For me, globbing.  More specifically, not having to worry about shell's globbing messing up my variables because of misplaced, lacking or incorrect escape characters.  Anything over 2-3 lines in shell (unless it is a simple list of batched commands), includes anything more complex than a passed list of text or requires the use of a for loop should be done in $scripting_language_of_choice (mine happens to be Python after years of Perl hell).

Secondly development time.  I have spent more than 10 years in the Linux world with a few years more in unixland.  I am no stranger to shell.  But honestly I was more productive in one afternoon of Python than I ever have been in 10 years of shell.  Another 10 years of shell won't change that.

People talk about how it takes a tad more effort to do sysadmin work in Python.  Honestly I'd rather the sysadmin work chuck shell in favor of Python because I find Python demonstrably superior to shell on all counts.  Faster coding, more robust code, easier for humans to parse and follow and simple nothing lacking compared to shell.  I have never, once, **ever** thought while programming in Python "Wow, I wish I could use this shell tweak for this."  Contrast that to every time I have to even look at shell I start to see red for it not being in something better; even Perl (which I now loathe).

Those specialized tools and the overhead associated with them have offered little to no advantage to me.  I am aware of them.  I can use them.  I am thankful for them when I need some one-off, which, 2-3 pipe operation; especially when I am stuck on Windows.  They are, by no means, a productive or sane way to build even the tiniest of projects.

---

### Post by ghostdog74 on 2008-09-09
> **Greyed said:**
> Honestly I'd rather the sysadmin work chuck shell in favor of Python.


The shell is the default interface between the comp and user. A sysadmin should know shell at least. 
1) Not every distribution has Python
2) should know that most rc scripts are written in shell.
3) some things are better done with shell than Python.

Lastly, imagine a sysadmin who doesn't know shell at all.

---

### Post by Greyed on 2008-09-09
> **ghostdog74 said:**
> The shell is the default interface between the comp and user. A sysadmin should know shell at least. 

Maybe 20 years ago.  Today it is arguably the GUI which is the default interface between the comp and user.

> 1) Not every distribution has Python

Ah, the ol' vi argument.  I don't respond to it any better than why people should learn vi even though I know and love vim.  

> 2) should know that most rc scripts are written in shell.

This being the ol' historical argument.  Nevermind that there is a distribution of Linux which replaces them to good effect.

[http://www.pardus.org.tr/eng/projects/comar/SpeedingUpLinuxWithPardus.html](http://www.pardus.org.tr/eng/projects/comar/SpeedingUpLinuxWithPardus.html)

Just because shell is what they are written in is by no means an argument for them to be continued to written in shell.  If anything it is an argument against the pig-headed ludditeness of the process.

> 3) some things are better done with shell than Python.

I haven't found a single task where this is true.  Not one in 10+ years of unix-like experience both on a hobbiest and professional level.

> Lastly, imagine a sysadmin who doesn't know shell at all.

I'd call it refreshing.  Yes, it is needed for legacy purposes much in the same way that we still need people around fluent in COBOL and FORTRAN.  Doesn't mean that every bloke out of the gate needs to be fluent in either or that either is well suited for anything other than the legacy which maintains their existence.

---

### Post by ghostdog74 on 2008-09-09
> **Greyed said:**
> 
I haven't found a single task where this is true. 

how do you find files in and rename them in Python?
how do you do a process listing in Python?
how do you parse a csv file and get field items of a particular choice in Python?
I am sure you can do these easily in Python with function wrappers etc

---

### Post by weresheep on 2008-09-09
[QUOTE=CptPicard]
Why do I code my multithreaded parallelized crossplatform number-crunching analyzer application that needs to talk to a remote web server via http in Java instead of a combination of wget, sed, bash, awk and multiple processes that communicate via some sort of pipe or whatever?
[/QUOTE]

From the brief description, it sounds like Erlang may be a better fit to your problem than Java (threads suck!) :)

I'm not sure what "multithreaded parallelized" means.

To clarify, I am not promoting shell scripting as an alternative to a general purpose language for genuine programming (as opposed to scripting) tasks. But for the areas that the shell is good at I'd prefer to use the specialised tools that are available. Best tool for the job etc.

However, I do not think that the areas the shell is good at is limited to system administration tasks. But perhaps that is a side effect of my 'weird' usage of the computer.

[QUOTE=CptPicard]
Just out of curiosity, do you do any "actual" programming outside of the shell?
[/QUOTE]

If you mean do I do any programming rather than just writing shell scripts, then yes. I program in C and Erlang (whilst playing with Lisp, Lua, Haskell and even Python, when the mood takes me).

If you mean do I use a GUI interface (as opposed to shell) for programming then the answer is (a partial no). I do all my coding at home with VIM and compiler/linker etc. in the shell.

However, at work I use IntelliJ IDEA to program Java (in Windows Vista :( ).

-weresheep

---

### Post by CptPicard on 2008-09-09
> **weresheep said:**
> From the brief description, it sounds like Erlang may be a better fit to your problem than Java (threads suck!)


Well, Java is mostly dictated by the "easy crossplatformness" requirement. Plus, it is actually sufficiently fast in in the kind of "crunch a lot of floating-points" stuff this thing does.

Threads don't suck that much when state can be easily divided between threads, or when you can make use of queues... otherwise I'll have to agree with you. :)

Actually, the potential "other" language I've considered is Haskell... pure-functional programming parallelizes nicely.

> Best tool for the job etc.

Well, then we don't disagree... I believe that for shell scripting you should use shell scripting (although any comprehensive scripting language should always be considered as an alternative...)

Just today I counted the lines of occurrence of a regexp pattern in a file, and for stuff like that, yes, shell is good.

> 
If you mean do I do any programming rather than just writing shell scripts, then yes. I program in C and Erlang (whilst playing with Lisp, Lua, Haskell and even Python, when the mood takes me).

Ok, ok. That "why would you use anything else than the shell" was starting to sound a little extreme without your clarification ;)

---

### Post by LaRoza on 2008-09-09
> **ghostdog74 said:**
> i am sure you know the difference. If not, there's a always a thing called the dictionary :)



> **ghostdog74 said:**
> The shell is the default interface between the comp and user. A sysadmin should know shell at least. 
1) Not every distribution has Python
2) should know that most rc scripts are written in shell.
3) some things are better done with shell than Python.

Lastly, imagine a sysadmin who doesn't know shell at all.

1. Most distros have different shells and there are many shells. Master them all? Or one?

2. Most aren't all that complex either. 
3. That is true, no one is saying that it isn't. You listed later some things that are best done with the shell, and possible, but less convenient in Python. The same argument is used the other way. Somethings are possible in the shell, but more convenient in Python, and considering Python is Python (whereas the shell is a multitude of shells) and that most distros have it, non sysadmins would be better off learning in depth Python rather than in depth shell scripting.

---

### Post by LaRoza on 2008-09-09
> **ghostdog74 said:**
> how do you find files in and rename them in Python?
how do you do a process listing in Python?
how do you parse a csv file and get field items of a particular choice in Python?
I am sure you can do these easily in Python with function wrappers etc

Finding files and renaming them isn't hard in Python, I'm sure you know that. The shell is better suited for it though.

parsing a csv file is easy. 

```

for line in open('file.csv').split(","):
    #process the lines which are lists the comma separated values

```

---

### Post by mssever on 2008-09-09
> **ghostdog74 said:**
> 1) Not every distribution has Python
If it doesn't have Python, you can install it. If you can't install something as basic as Python, then the system isn't worth using.
> **LaRoza said:**
> parsing a csv file is easy. 

```

for line in open('file.csv').split(","):
    #process the lines which are lists the comma separated values

```
But not that easy, unless you use a csv module which I assume is available for Python. Consider this line from a CSV file:
```
foo,bar,42,"field, with ""comma"" and double quotes",another field
```Calling split(',') on this file will result in corrupt data.

---

### Post by LaRoza on 2008-09-09
> **mssever said:**
> If it doesn't have Python, you can install it. If you can't install something as basic as Python, then the system isn't worth using.

Also, there are many shells, and the Unix tools can be different between *nixes (like awk), wheras Python is Python.

> 
But not that easy, unless you use a csv module which I assume is available for Python. Consider this line from a CSV file:
```
foo,bar,42,"field, with ""comma"" and double quotes",another field
```Calling split(',') on this file will result in corrupt data.

Knew there would be one: [http://docs.python.org/lib/module-csv.html](http://docs.python.org/lib/module-csv.html)

---

### Post by ghostdog74 on 2008-09-09
> **LaRoza said:**
> 1. Most distros have different shells and there are many shells. Master them all? Or one?

1) master according to circumstances. eg popularity, usage in organization etc
2) Master them all, why not?? Like i said, not all people are programmers. sysadmins should learn to know all kinds of shells where possible. The same logic applies to programmers who only knows one language. That doesn't make him/her marketable.

---

### Post by ghostdog74 on 2008-09-09
> **LaRoza said:**
> 

parsing a csv file is easy. 

```

for line in open('file.csv').split(","):
    #process the lines which are lists the comma separated values

```

that's what i said earlier, its not difficult. 
```

 awk -F"," '/pattern/{print ++d , $1,$NF }' OFS="," file

```

---

### Post by LaRoza on 2008-09-09
> **ghostdog74 said:**
> 1) master according to circumstances. eg popularity, usage in organization etc

That would make sense, if one couldn't use a single language like Python.

> 
2) Master them all, why not??

Because it is redundant and most people have more important things to do than learn the ins and outs of subtly different shells when Python is Python.

---

### Post by ghostdog74 on 2008-09-09
> **mssever said:**
> If it doesn't have Python, you can install it. If you can't install something as basic as Python, then the system isn't worth using.
you have not been in a company that has policies like that.

---

### Post by ghostdog74 on 2008-09-09
> **LaRoza said:**
> 

Because it is redundant and most people have more important things to do than learn the ins and outs of subtly different shells when Python is Python.
If you know bash only, and the next company you work for uses zsh for most of its work. You will have more important things to do, learn zsh.

---

### Post by LaRoza on 2008-09-09
> **ghostdog74 said:**
> you have not been in a company that has policies like that.

The main argument "against" shell scripting is that it is best for small tasks and sysadmin. You seem to be reinforcing this ;)

---

### Post by ghostdog74 on 2008-09-09
> **LaRoza said:**
> Also, there are many shells, and the Unix tools can be different between *nixes (like awk), wheras Python is Python.

What is "python is Python"?? is it Python+modules? Or just Python shell with inbuilt functions? 
you said tools like awk is different between nixes, doesn't Python have different versions as well?

---

### Post by ghostdog74 on 2008-09-09
> **LaRoza said:**
> The main argument "against" shell scripting is that it is best for small tasks and sysadmin. You seem to be reinforcing this ;)
the main arguments comes from this quote from Greyed
> **Greyed said:**
> 
I haven't found a single task where this is true. 


Also, i have showed you how one can do GUI with the shell. reinforcing or not, up to you to decide.

---

### Post by LaRoza on 2008-09-09
> **ghostdog74 said:**
> What is "python is Python"?? is it Python+modules? Or just Python shell with inbuilt functions? 
you said tools like awk is different between nixes, doesn't Python have different versions as well?

Python as in the standard Python release. The version differences usually mean a "version x or greater", and isn't as big as a problem in my experience.

Also, Python code works on OS X, Solaris, BSD, Linux and Windows if it uses the standard features. What shell script will? When one is using Python, they can just have a simple require "requires Python version x or greater". With the shell, you not only have to have compatible shells, but all the unix tools have to be compatible as well.

---

### Post by LaRoza on 2008-09-09
> **ghostdog74 said:**
> 
Also, i have showed you how one can do GUI with the shell. reinforcing or not, up to you to decide.
Yes, that was interesting. Now, how many projects use it? How many individuals use it? How valuable is that knowledge?

---

### Post by ghostdog74 on 2008-09-09
> **LaRoza said:**
> 
Also, Python code works on OS X, Solaris, BSD, Linux and Windows if it uses the standard features. 

true, so does shell+tools if you use standard features.

---

### Post by mssever on 2008-09-09
> **ghostdog74 said:**
> you have not been in a company that has policies like that.
If they pay me enough, I'll do what they want. But that doesn't mean they're smart.

I was once installing a network of RedHat machines dedicated to a particular application, and part of the installation instructions involved changing the default shell to csh. Of course, there's no valid reason for an application to care about the default shell, and those of us who knew how to use a shell were Linux users and had much more experience with bash than csh. I tried to leave the default shell as bash (we used shared accounts, not individual accounts), but I was told to follow the instructions exactly. Since they were paying me, I complied while pointing out that it's impossible for the default shell to affect the application. I guess they shot themselves in the foot, because it was only a summer job for me, and the odds of their hiring someone who's expert at csh were slim. Of course, the first thing I always typed after logging in was "bash".

---

### Post by mssever on 2008-09-09
> **ghostdog74 said:**
> true, so does shell+tools if you use standard features.
So why did I have to partially rewrite my aliases file when I set up an account on my webhost's FreeBSD server? Oh yeah, it's because the FreeBSD folks can't be bothered to copy good ideas from the GNU folks. You could argue that for portability, I should stick to POSIX-compatible techniques. But why restrict myself to a primitive set of options?

---

### Post by ghostdog74 on 2008-09-09
> **mssever said:**
> But that doesn't mean they're smart.
that really doesn't matter, does it :)

> 
I was once installing a network of RedHat machines dedicated to a particular application, and part of the installation instructions involved changing the default shell to csh. Of course, there's no valid reason for an application to care about the default shell,

that would depend on whether the application is written with some specific features of csh.

> 
and the odds of their hiring someone who's expert at csh were slim. Of course, the first thing I always typed after logging in was "bash".
for someone with bash/shell experience, its not that difficult to grasp csh concepts.

---

### Post by mssever on 2008-09-09
> **ghostdog74 said:**
> that would depend on whether the application is written with some specific features of csh.Not really, because as long as csh is installed, the shebang will launch it regardless of the current shell. Unless the authors were stupid and omitted the shebang line.

---

### Post by slavik on 2008-09-10
just to note. back in the days of JCL, you had JCL (Job Control Language) and an interactive shell. The people realised that you can just merge the two and we got our bash, korn, and other interactive and programmable shells.

shells are not designed to be used towrite applications, they are designed to control jobs ... look at some of the scripts in /etc/init.d/ . A shell is one of those things that you can expect to be there, but just because there are different shells doesn't mean squat, because IronPython isn't 100% same as Jython which isn't 100% the same as CPython ... the simple example of that is threading and the collection type classes which have to be made thread safe (with mutex locks).

a shell script is something that is rarely migrated to another system, it doesn't have any particular strengths like PPR do. It is also supposed to be smaller than PPR since there is no external module system.

---

### Post by pmasiar on 2008-09-10
> **slavik said:**
> shells are not designed to be used towrite applications, they are designed to control jobs ... 

Exactly! shell orchestrates workflow between different little tools (using external semantics in plain text files, and CptPicard mentioned) - that's why it is called script: tell 'actors' where to come and what parameters to use to filter stdin to stdout. It is not real language.

> just to note. back in the days of JCL, you had JCL (Job Control Language) and an interactive shell. The people realised that you can just merge the two and we got our bash, korn, and other interactive and programmable shells.

That was easy. **way back** in days of IBM/360 JCL, you had JCL and console to start the batch - and that was all you had. Shell was brilliant idea back then.

---

### Post by pmasiar on 2008-09-10
> **ghostdog74 said:**
> What is "python is Python"?? is it Python+modules? Or just Python shell with inbuilt functions? 
you said tools like awk is different between nixes, doesn't Python have different versions as well?

Yes and no.

Python has policy of "batteries included": quite a lot of "core" modules is included in every version, and each release adds new modules (after they were stabilized outside of 'core'). This is result of python as language for scripting interaction between libraries: many details which are in say Perl or Ruby part of syntax, are delegated to libraries. It makes  syntax of language simpler (and easier to maintain and extend), and improvement of libraries is independent of language: Early versions of library can be radically improved and even changed if needed, in faster development cycle than language is released, and only interested parties are affected by the churn. When stable and mature, library is included in core.

So you can program against 'core' modules API, which is stable, or some advanced/custom libraries (which you need to handle separately).

---

### Post by ghostdog74 on 2008-09-10
> **pmasiar said:**
> Yes and no.

Python has policy of "batteries included": quite a lot of "core" modules is included in every version, 

so does the shell. It has "batteries included" as well. If you want to gzip a file in Python, you import gzip. If you want to tar a file, you import tarfile. In shell, the "batteries" will be tar and gzip/zip.

---

### Post by mssever on 2008-09-10
> **ghostdog74 said:**
> so does the shell. It has "batteries included" as well. If you want to gzip a file in Python, you import gzip. If you want to tar a file, you import tarfile. In shell, the "batteries" will be tar and gzip/zip.
Except that in the shell, the "batteries" aren't necessarily portable. For example, GNU tar is different from other versions of tar, and supports different options. And ps varies wildly. Even ls varies, as I discovered when trying to port a script to FreeBSD. So if you want your script to be portable, you have to read up on POSIX and hope all your tools correctly support POSIX. If you don't care about portability, then you potentially lose one of the reasons for writing shell scripts.

---

### Post by ghostdog74 on 2008-09-10
> **mssever said:**
> Except that in the shell, the "batteries" aren't necessarily portable. For example, GNU tar is different from other versions of tar, and supports different options. And ps varies wildly. Even ls varies, as I discovered when trying to port a script to FreeBSD. So if you want your script to be portable, you have to read up on POSIX and hope all your tools correctly support POSIX. If you don't care about portability, then you potentially lose one of the reasons for writing shell scripts.
true, however with [proper guidance](http://www.amazon.com/Portable-Shell-Programming-Collection-Professional/dp/0134514947) from [people who have done it](http://www.google.com.sg/search?hl=en&q=Portable+Shell+Programming&btnG=Google+Search&meta=), its not impossible to write [portable shell scripts](http://www.gnu.org/software/autoconf/manual/autoconf-2.57/html_chapter/autoconf_10.html). Looking at your POV, if you use new features from new version, you have to take care of backwards compatibility as well...

---

### Post by Greyed on 2008-09-12
Oh god, a program off.  How boring.

> **ghostdog74 said:**
> how do you find files in and rename them in Python?

Depends, find where?  In a known directory?  os.listdir() and a for loop if one is so inclined.  Somewhere under yonder, os.walk().

> how do you do a process listing in Python?

In what context?  Or rather, how would you do it without ps in shell given that ps isn't a part of any shell I know (except for sash)?

> how do you parse a csv file and get field items of a particular choice in Python?

```

import csv
spam = csv.reader(open('somefile.csv'))
for row in spam:
    print row[choice]

```

Lemme throw that back at you.  I'm curious how cut would deal with field delimiters inside a quoted field since it has no concept of the difference between a barren and a quoted field in csv.  In fact I ran into that one when I tried to do just a simple split on a CSV which is why I learned the csv module.  Which, for the record, simplified many of my scripts since it made the concept so native.  It's a lists of lists to iterate over and parse using normal Python semantics.

> I am sure you can do these easily in Python with function wrappers etc

Quite so.  I'm just amused that two of your suggestions which I presume are supposed to be where shell is superior, might very well turn out to show that shell is inferior.  The third one certainly does since I hope you're surely not comparing find -exec to os.walk() in terms of simplicity or the ability to customize as needed.

Answer honestly though with terms like "function wrappers" I'm highly suspecting that while you profess having programmed in Python I doubt it hasn't been more than basic dabbling.  Correct?

---

### Post by ghostdog74 on 2008-09-12
> **Greyed said:**
> 
```

import csv
spam = csv.reader(open('somefile.csv'))
for row in spam:
    print row[choice]

```

Lemme throw that back at you.  I'm curious how cut would deal with field delimiters inside a quoted field since it has no concept of the difference between a barren and a quoted field in csv.  In fact I ran into that one when I tried to do just a simple split on a CSV which is why I learned the csv module.  Which, for the record, simplified many of my scripts since it made the concept so native.  It's a lists of lists to iterate over and parse using normal Python semantics.


you are using a csv module that specifically does csv parsing. Its true that makes things easy. However, its also true that such csv "modules" exists for the shell/awk. No arguments here. 

> 
Answer honestly though with terms like "function wrappers" I'm highly suspecting that while you profess having programmed in Python I doubt it hasn't been more than basic dabbling.  Correct?
lol, whatever you say that makes you happy.

---

### Post by Greyed on 2008-09-12
> **ghostdog74 said:**
> you are using a csv module that specifically does csv parsing.

And has been a part of the Python core libraries since 2002.  That means for 6 years now people have not had to reinvent that particular wheel nor Google the answer.  It also means 6 years from now code that utilizes it probably will not break as spectacularly as shell script written to do the same.  ;)

> Its true that makes things easy. However, its also true that such csv "modules" exists for the shell/awk. No arguments here.

We're talking shell, not awk.  'sides, are they included with the shell standard?  :P

> lol, whatever you say that makes you happy.

Nothing about happy.  Also I notice you didn't answer any of the questions I posed.  I presume this means that I was correct and your little program-off was a bust?  I mean, c'mon, you didn't even answer the challenge about a process listing without ps even though it is trivial.

---

### Post by ghostdog74 on 2008-09-12
> **Greyed said:**
> And has been a part of the Python core libraries since 2002.  That means for 6 years now people have not had to reinvent that particular wheel nor Google the answer.  It also means 6 years from now code that utilizes it probably will not break as spectacularly as shell script written to do the same.  ;)

if you have read my posts, you would have noticed i consider awk + tools part of shell "libraries" equivalent to your python core libraries.


> 
We're talking shell, not awk.  'sides, are they included with the shell standard?  :P


we have different frequencies then.

> 
Nothing about happy.  Also I notice you didn't answer any of the questions I posed.  I presume this means that I was correct and your little program-off was a bust?  I mean, c'mon, you didn't even answer the challenge about a process listing without ps even though it is trivial.
no, its because i find it pointless to continue since we have different POVs.
If you really want to know, I consider ps -ef short and sweet for displaying process listing then using os.popen and getting it to read() out the results. I consider tail -1 bigfile short and sweet to display the last line of a big file, than using seek(),mmap() etc..

---

### Post by Greyed on 2008-09-12
> **ghostdog74 said:**
> if you have read my posts, you would have noticed i consider awk + tools part of shell "libraries" equivalent to your python core libraries.

I did.  I also agreed with other people who pointed out that awk is a separate scripting language and if one is going to learn an entirely different scripting language one could just as easily learn perl, ruby, python and be done with it.

> no, its because i find it pointless to continue since we have different POVs.

Translations: When you were talking about absolutes for everyone it is ok, but when someone else does and has the gumption to back it up then its "different points of view".  Cop-out.

Besides, I'd expect someone who is arguing that a competent should know shell would be able to get a list of processes on a Linux machine without ps; there is real utility in doing so.  As long as a sysadmin knows the system what language they use to manipulate that knowledge is secondary.  If they know a dozen languages and not the system then they're useless in a dozen languages.

> If you really want to know, I consider ps -ef short and sweet for displaying process listing then using os.popen and getting it to read() out the results.

I said without ps.  And why would I use popen?  I'd use os.listdir().

Of course I'd give you the shell example except, naturally, file globbing is getting in the way, even when I am trying to quote-escape it.  But I mentioned something about that in my first post.

So here's the Python version, short and sweet:
```

import os
for name in os.listdir(/proc):
    try:
        int(name[0])
        print name
    except:
        continue

```

And the result on my machine (chopped for berevity):
```
{grey@igbuntu:~} python bar
1                          
2                          
3                          
4                          
5                          
6                          
7                          
41                         
44                         
45                         
90

```

"Ah-HA!  But then for me to get ps -ef you'd have to do a bunch of things" I can hear you formulating.  Except we're talking about shell **scripting**.  I'm not postulating that Python is a better interactive shell.  It's not, never was designed to be.  But as for scripting, especially in the niche role of system administration scripting often mindlessly conceded to shell, how often are you going to pull a ps -ef and use that output in a script which isn't going to chop the numbers out?

The above is just approaching the problem from the other side, we're starting with the numbers.  What we do from there depends on exactly what you want.  And that's the point when it comes to scripting; it isn't obtaining the information it is what you do with it that is important.  Shell is stupidly hard to do anything with the information you get because of its horrifyingly primitive variable system coupled with the freakshow that is called globbing.  I love globbing; it's great for interactive work.  For non-interactive work it gets in the way so much it is abysmal.  Just the mere fact that it takes me 5 lines to get the same information you get in 1 doesn't bother me.  It doesn't even mean that shell is better than Python for scripting.  Because once we have that information I'll be able to do what I want with it far easier, faster and in a more legible fashion than you ever will in shell.

Besides, if I really wanted to resort to ps why would I mess with popen when I have Popen?  Or even better...  
```

os.system('/bin/ps -ef > /tmp/pslist
foo = open(/tmp/pslist)
for line in foo:
    #do your magic here

```

>  I consider tail -1 bigfile short and sweet to display the last line of a big file, than using seek(),mmap() etc..

```

foo = open(bigfile)
bar = foo.readlines()
bar[-1],

```

Of course if you're worried about memory...

```

foo = open(bigfile)
for line in foo:
    pass
print line,

```

{grey@igbuntu:~/t} tail -1 spam
20 The rain in spain stays mainly in the plain.
{grey@igbuntu:~/t} python memhog.py
20 The rain in spain stays mainly in the plain.
{grey@igbuntu:~/t} python memlite.py
20 The rain in spain stays mainly in the plain.

seek()?  mmap()?  This isn't C.

---

### Post by ghostdog74 on 2008-09-12
> **Greyed said:**
> I did.  I also agreed with other people who pointed out that awk is a separate scripting language and if one is going to learn an entirely different scripting language one could just as easily learn perl, ruby, python and be done with it.

you have your choices and believes, so have i. never have i once in these thread discourage people not to use such languages have i? I am an advocate of learning as many as possible and making use of them appropriately.

> 
Besides, I'd expect someone who is arguing that a competent should know shell would be able to get a list of processes on a Linux machine without ps; there is real utility in doing so.  As long as a sysadmin knows the system what language they use to manipulate that knowledge is secondary.  If they know a dozen languages and not the system then they're useless in a dozen languages.
i agree. whatever fits best to the sysadmin. this is "best" for me.
```

ls /proc |grep -E "[0-9]+"

```

> 
"Ah-HA!  But then for me to get ps -ef you'd have to do a bunch of things" I can hear you formulating.  Except we're talking about shell **scripting**.  I'm not postulating that Python is a better interactive shell.  It's not, never was designed to be.  But as for scripting, especially in the niche role of system administration scripting often mindlessly conceded to shell, how often are you going to pull a ps -ef and use that output in a script which isn't going to chop the numbers out?

The above is just approaching the problem from the other side, we're starting with the numbers.  What we do from there depends on exactly what you want.  And that's the point when it comes to scripting; it isn't obtaining the information it is what you do with it that is important.  Shell is stupidly hard to do anything with the information you get because of its horrifyingly primitive variable system coupled with the freakshow that is called globbing.  I love globbing; it's great for interactive work.  For non-interactive work it gets in the way so much it is abysmal.  Just the mere fact that it takes me 5 lines to get the same information you get in 1 doesn't bother me.  It doesn't even mean that shell is better than Python for scripting.  Because once we have that information I'll be able to do what I want with it far easier, faster and in a more legible fashion than you ever will in shell.


There you go...differences in POVs. Not everyone is alike and think alike. So let's just stop here.


> 
Besides, if I really wanted to resort to ps why would I mess with popen when I have Popen?  Or even better...  
```

os.system('/bin/ps -ef > /tmp/pslist
foo = open(/tmp/pslist)
for line in foo:
    #do your magic here

```

why would you want to create an intermediate file when you can just iterate the results



> 
Of course if you're worried about memory...

```

foo = open(bigfile)
for line in foo:
    pass
print line,

```

Have you tried this on a big file? try to compare it with tail -1 and see the difference.


> 
seek()?  mmap()?  This isn't C.
who says its just for C??? Read [here](http://docs.python.org/lib/bltin-file-objects.html) if you have not read. As for mmap, I should have said [this](http://docs.python.org/lib/module-mmap.html).

As i very much look forward to your next reply, I feel this is going nowhere. If you have shell doubts which you are not clear, i can assist you to the best of my knowledge ( I am not a know all ). However, if you want to continue "arguing" about difference in POVs, i have no time for that.

---

### Post by Greyed on 2008-09-12
> **ghostdog74 said:**
> you have your choices and believes, so have i. never have i once in these thread discourage people not to use such languages have i? I am an advocate of learning as many as possible and making use of them appropriately.

Yes, you have.  You did in the very next sentence.  "Making use of them appropriately" implies there are situations in which the superior scripting languages would be inappropriate for use.  Thus you are discouraging their use since there is no such situation.

> i agree. whatever fits best to the sysadmin. this is "best" for me.
```

ls /proc |grep -E "[0-9]+"

```


Only took you 4 messages and a plain example to get you to come up with that.

> There you go...differences in POVs. Not everyone is alike and think alike. So let's just stop here.

This is called relativism.  You might be interested to know that not everything is relative.

> why would you want to create an intermediate file when you can just iterate the results

I dunno.  I was just showing you an example of being able to do it without having to worry about popen.


[quoteHave you tried this on a big file? try to compare it with tail -1 and see the difference.[/quote]

Ok, snipping matching lines since they're immaterial...

root@olethros:/var/log# tail -1 messages
Sep 12 04:53:44 olethros kernel: Shorewall:net2fw:ACCEPT:IN=eth0 OUT= 

root@olethros:/var/log# time tail -1 messages
Sep 12 04:54:13 olethros kernel: Shorewall:net2fw:ACCEPT:IN=eth0 OUT= 
tail -1 messages  0.00s user 0.00s system 0% cpu 0.002 total

root@olethros:/var/log# time python memlite.py messages
Sep 12 04:54:13 olethros kernel: Shorewall:net2fw:ACCEPT:IN=eth0 OUT= 
python memlite.py messages  0.01s user 0.00s system 3% cpu 0.265 total

root@olethros:/var/log# ls -lh messages
-rw-r----- 1 root adm 1.2M 2008-09-12 04:55 messages

1.2Mb file large enough?  0.01s longer for Python which could be the load time of the interpreter.  Want larger?

root@olethros:/var/log# tail -1 foo
Sep 12 04:58:34 olethros kernel: Shorewall:net2fw:ACCEPT:IN=eth0 OUT= 

root@olethros:/var/log# time tail -1 foo
Sep 12 04:58:34 olethros kernel: Shorewall:net2fw:ACCEPT:IN=eth0 OUT= 
tail -1 foo  0.00s user 0.00s system 0% cpu 0.002 total

root@olethros:/var/log# time python memlite.py
Sep 12 04:58:34 olethros kernel: Shorewall:net2fw:ACCEPT:IN=eth0 OUT= 
python memlite.py  0.01s user 0.02s system 20% cpu 0.149 total

root@olethros:/var/log# ls -lh foo
-rw-r--r-- 1 root root 31M 2008-09-12 04:58 foo

31Mb, still 0.01s.  I think I'm safe from falling asleep while waiting for my script to finish.  :P

> who says its just for C??? Read [here](http://docs.python.org/lib/bltin-file-objects.html) if you have not read. As for mmap, I should have said [this](http://docs.python.org/lib/module-mmap.html).

Ok, so, you're talking about a C programming hacking in Python instead of a Python programmer.  Yes, I am aware those are there.  I still am asking, what is this, C?  You asked for the last line.  Neither seek or mmap know of the concept of lines, only bytes.

> If you have shell doubts which you are not clear, i can assist you to the best of my knowledge ( I am not a know all ). However, if you want to continue "arguing" about difference in POVs, i have no time for that.

I have no shell doubts.  I am very comfortable with both my knowledge of shell and my application of shell.  Great for 4-5 discrete operations which do not require much data passing or data storage.  Anything which requires scripting is best done in a real scripting language and not an ancient, passed over worthless attempt at one.  As you said, use the tools appropriately.  :P

---

### Post by ghostdog74 on 2008-09-12
> **Greyed said:**
>   Want larger?

sure, try that on a 100MB++ file with 1 million lines for a start.


> 
Ok, so, you're talking about a C programming hacking in Python instead of a Python programmer.  Yes, I am aware those are there.  I still am asking, what is this, C?  You asked for the last line.  Neither seek or mmap know of the concept of lines, only bytes.

The context is on how you implement 'tail' in Python. I am only showing 2 examples where you can seek() or use memory mapping. Your example of using for loop and pass definitely is not applicable to large files. why would you want to scan the whole large file, when you only want the last part. you have to use some kinda "seek" to go to the last part in Python, and in this respect, i would certainly just use tail -1.

---

### Post by Greyed on 2008-09-12
> **ghostdog74 said:**
> sure, try that on a 100MB++ file with 1 million lines for a start.
Sorry, 1million lines is more like 300Mb.

root@olethros:/var/log# time python memlite.py
Sep 12 05:31:12 olethros kernel: Shorewall:net2fw:ACCEPT:IN=eth0 OUT= python memlite.py  0.01s user 0.00s system 1% cpu 0.973 total
root@olethros:/var/log# ls -lh foo
-rw-r--r-- 1 root root 121M 2008-09-12 05:31 foo
root@olethros:/var/log# wc -l foo
494104 foo

This time I didn't even do the pre-timing cache run since I'm not going to compare against tail.  0.0s to pull the 494104th of a 121Mb file.

> The context is on how you implement 'tail' in Python. I am only showing 2 examples where you can seek() or use memory mapping. Your example of using for loop and pass definitely is not applicable to large files.

You're engaging in what is known as pre-optimization.  Google pre-optimization and Python to see how dim a view the Pythonistas take of pre-optimization.  I can keep generating larger files, "cat foo >> bar ; cp bar foo" is exponential after all.  But I've already hit a point of diminishing returns on the sizes of log files I've seen in the real world and I've yet to get over 0.01s on my **shared leased vm**.

> why would you want to scan the whole large file, when you only want the last part.

Because computer cycles are cheap; programmer cycles are expensive.  Why should I spend 10-15m to noodle through using seek/mmap when a simple for loop is getting the trick done.  At 0.01s up to just shy of 500,000 lines in a 121Mb file that 10-15m represents 1000 runs of that particular tool at a minimum.  Meanwhile having the full breadth and depth of Pythons language at my fingertips might save me hours of development time on the portion of the script that does anything meaningful on that piece of text over a comparable experience in shell.

> you have to use some kinda "seek" to go to the last part in Python, and in this respect, i would certainly just use tail -1.

I do?  Why?  If I know I'm regularly going to hit >300Mb files sure I might go noodling through seek/mmap but, hey, only once!  The fact that in 10 years of Python programming for SysAdmin work I've yet to work with seek/mmap tells you exactly how many times I've regularly touched files that large in that manner.  It's somewhere between 0 and none.  

Far more often I've had to deal with text files where I want to iterate over every file and use 3-4 different regexs to pull the information from that file in which case I have the choice of iterating over those large files 3-4 times vs. recompiling each of the regexes per line.  Seems to me like one pass through the files using 1 compile of each of the regexes might be the more efficient way to go.  Or, even better, not having to do several stat calls per file when one will do.  Or having to fork/exec 30 times per file to do the job I can do with one fork/exec.

I can tell you the day I realized that shell is no longer viable as a system administration tool.  It is when I had to rewrite a shell script into Perl.  The shell script did all the same functionality of the shell script.  Slurped in the same data.  Spit out the same output.  And did it with a runtime that was 5 hours shorter than the shell version because I cut out several stat calls and did not fork to one external application to do the work.

You want to worry about the difference between a for loop vs. seek so you can say that tail -1 is more elegant than Python because of, mayyyybe, 1s of real-time overhead on a 300Mb, 1 million line file?  5 hours in stat/fork/exec calls.

---

### Post by ghostdog74 on 2008-09-12
> **Greyed said:**
> Sorry, 1million lines is more like 300Mb.

depending on how many characters/bytes on each line terminated by newline.

```

# ls -l file
-rw-r--r-- 1 root root 305416718 Sep 12 15:17 file
# wc -l file
20361109 file
# time python test.py
this is the last line

real    0m7.278s
user    0m7.044s
sys     0m0.232s
# time tail -1 file
this is the last line

real    0m0.016s
user    0m0.004s
sys     0m0.000s
# more test.py
foo = open("file")
for line in foo:
    pass
print line,

```


At present, the most straight forward, short and sharp way to get the last line of big and small files that doesn't lose much on performance is tail -1 for me. So we can just rest at that.

---

### Post by Greyed on 2008-09-12
> **ghostdog74 said:**
> At present, the most straight forward, short and sharp way to get the last line of big and small files that doesn't lose much on performance is tail -1 for me. So we can just rest at that.

We can?  Really?  Or did you miss the many times I said this was about shell scripting and not interactive shell?

Or let me put it another way for you.

You can construct a few dozen or hundred edge cases where one off commands will be easier than writing the 3-4 lines of Python to do the same.  That is not scripting.

Which is precisely why you cut my real-world experience where stat/fork/exec calls cost a shell script 5 hours on its run time compared to a Perl equivolant.  Or my example where shell cannot cache regular expressions so you either have to reiterate over a file multiple times (once per regex) or recompile them each per line.

Does my quick (and legible) Python example stand against tail -1?  Nope.  But it's not meant to.  My example was for one case; to show that your assertion of having to learn and use either seek or mmap is not needed.  A point I still stand by because if one knows they're going to hit large files they can spend the time to learn it and still get gains over shell when they are **scripting**.

So you want to play in my world?  Cook up my example.  Cache a grep in shell, please.  Or in Python (interactive just for illustrative purposes):

```

>>> import re                                                         
>>> cached = re.compile('a cached regex')                             
>>> cached                                                            
<_sre.SRE_Pattern object at 0x81da2a0>                                
>>> cached.pattern                                                    
'a cached regex'                                                      
>>> cached.match(cached.pattern)                                      
<_sre.SRE_Match object at 0x8373330>                                  
>>> cached.match('foo')

```

Regex compiled once, used twice.

Or my recent favorite base module, datetime.

```

>>> import datetime
>>> foo = datetime.now()
>>> foo = datetime.datetime.now()
>>> foo
datetime.datetime(2008, 9, 12, 3, 46, 3, 260663)
>>> foo.year
2008
>>> foo.month
9
>>> foo.day
12
>>> bar = datetime.timedelta(hours=23, minutes=55)
>>> foo - bar
datetime.datetime(2008, 9, 11, 3, 51, 3, 260663)
>>> bar = datetime.timedelta(weeks=3)
>>> foo - bar
datetime.datetime(2008, 8, 22, 3, 46, 3, 260663)

```

What's the find command for files access 23h55m ago?  No using calc to determine the number of minutes now.  I mean I told it I wanted 23h55m.  I told it 3 weeks, not 21 days.  Or even better; want to know if any log files are are out of whack, pull the mtime of one, mtime of the next, subtract one from the other and you get a delta which can then me used as a baseline to compare all other comparative routines.

```

>>> import os                                                                   
>>> log1 = datetime.datetime.fromtimestamp(os.stat('/var/log/messages.2.gz').st_mtime)
>>> log2 = datetime.datetime.fromtimestamp(os.stat('/var/log/messages.3.gz').st_mtime)
>>> log1
datetime.datetime(2008, 8, 22, 17, 43, 28)
>>> log2
datetime.datetime(2008, 8, 15, 23, 11, 25)
>>> delta = log1 - log2
>>> delta
datetime.timedelta(6, 66723)
>>> delta.days
6
>>> delta.seconds
66723

```

I've got my delta, now what can I do with it?  Well, I did say I wanted to check the log files to see if they were rotating at about the same time.  Obviously it won't be the exact same time, so let's say give or take a 5 minute window on either side...

```

>>> minutes = datetime.timedelta(minutes=5)
>>> log3 = datetime.datetime.fromtimestamp(os.stat('/var/log/messages.1.gz').st_mtime)
>>> newdelta = log3 - log1
>>> if newdelta > delta + minutes or newdelta < delta - minutes:
...     print "busted", newdelta.seconds
busted 54585

```

Looks like that one wasn't cycled within +/5 min of the last period.  :(

Arithmatic on date/time stamps direct from the stat calls which means second resolution for now and microsecond resolution in the future.  All with natural feeling language and semantics.

I'm still working in the core language here with no external utilities.  These are things I have used as a sysadmin in scripting all far more than a contrived "tail -1" example.  It is these examples, and more, which is why I feel that shell script as a system administration language, is dead.  It is why several posts back I said that any time I have to deal with shell script for system administration work I see red because it is so difficult to do anything useful in it.  Is it possible?  Sure, in the "all languages are turing complete" sense.  It is worth doing?  Hell no.

---

### Post by ghostdog74 on 2008-09-12
> **Greyed said:**
>  Or did you miss the many times I said this was about shell scripting and not interactive shell?

shell scripting? ok, so i put the tail command inside a file and call it a shell script. is that fine with you? 


> 
So you want to play in my world?  Cook up my example.  Cache a grep in shell, please.  Or in Python (interactive just for illustrative purposes):

```

>>> import re                                                         
>>> cached = re.compile('a cached regex')                             
>>> cached                                                            
<_sre.SRE_Pattern object at 0x81da2a0>                                
>>> cached.pattern                                                    
'a cached regex'                                                      
>>> cached.match(cached.pattern)                                      
<_sre.SRE_Match object at 0x8373330>                                  
>>> cached.match('foo')

```

Regex compiled once, used twice.

I don't understand what you trying to prove here. If you want, give me a use case example. 


> 
Or my recent favorite base module, datetime.

```

>>> import datetime
>>> foo = datetime.now()
>>> foo = datetime.datetime.now()
>>> foo
datetime.datetime(2008, 9, 12, 3, 46, 3, 260663)
>>> foo.year
2008
>>> foo.month
9
>>> foo.day
12
>>> bar = datetime.timedelta(hours=23, minutes=55)
>>> foo - bar
datetime.datetime(2008, 9, 11, 3, 51, 3, 260663)
>>> bar = datetime.timedelta(weeks=3)
>>> foo - bar
datetime.datetime(2008, 8, 22, 3, 46, 3, 260663)

```


not really sure what you trying to show here too...
```

DATE=$(date +%Y-%m-%d-%H-%M-%s)
IFS="-"
set -- $DATE
echo "Year: $1"
echo "month: $2"
echo "Day: $3"
echo "23 hours 55min ago: $(date --date='-23 hour -55 min')"
echo "3 weeks ago: $( date --date='3 weeks ago' +'%Y-%M-%d %H:%m:%S')"
unset IFS

```

> 
What's the find command for files access 23h55m ago? No using calc to determine the number of minutes now.  I mean I told it I wanted 23h55m.  I told it 3 weeks, not 21 days. 

```

day=$((  $(( $(date  +%s) / 86400 )) - $(( $(date --date="-3 weeks" +%s) / 86400 )) )) 
find . -type f -mtime +$day -print

```

> 
 Or even better; want to know if any log files are are out of whack, pull the mtime of one, mtime of the next, subtract one from the other and you get a delta which can then me used as a baseline to compare all other comparative routines.

```

>>> import os                                                                   
>>> log1 = datetime.datetime.fromtimestamp(os.stat('/var/log/messages.2.gz').st_mtime)
>>> log2 = datetime.datetime.fromtimestamp(os.stat('/var/log/messages.3.gz').st_mtime)
>>> log1
datetime.datetime(2008, 8, 22, 17, 43, 28)
>>> log2
datetime.datetime(2008, 8, 15, 23, 11, 25)
>>> delta = log1 - log2
>>> delta
datetime.timedelta(6, 66723)
>>> delta.days
6
>>> delta.seconds
66723

```

I've got my delta, now what can I do with it?  Well, I did say I wanted to check the log files to see if they were rotating at about the same time.  Obviously it won't be the exact same time, so let's say give or take a 5 minute window on either side...

```

>>> minutes = datetime.timedelta(minutes=5)
>>> log3 = datetime.datetime.fromtimestamp(os.stat('/var/log/messages.1.gz').st_mtime)
>>> newdelta = log3 - log1
>>> if newdelta > delta + minutes or newdelta < delta - minutes:
...     print "busted", newdelta.seconds
busted 54585

```

Looks like that one wasn't cycled within +/5 min of the last period.  :(

Arithmatic on date/time stamps direct from the stat calls which means second resolution for now and microsecond resolution in the future.  All with natural feeling language and semantics.

wow, you don't have to show me what these modules can do...true it may make things easy for you, but i am sure also that it can be done at the shell. I am not a shell expert but to partially illustrate
```

log1=$(( `stat -c %Y /var/log/messages-1.gz`/86400 ))
log2=$(( `stat -c %Y /var/log/messages-2.gz`/86400 ))
echo $((  $log2 - $log1 )) #delta.days

```

> 
I'm still working in the core language here with no external utilities. 

oh no, yes you are, you imported datetime. That's external to me. 

> 
 These are things I have used as a sysadmin in scripting all far more than a contrived "tail -1" example.  It is these examples, and more, which is why I feel that shell script as a system administration language, is dead.  It is why several posts back I said that any time I have to deal with shell script for system administration work I see red because it is so difficult to do anything useful in it.  Is it possible?  Sure, in the "all languages are turing complete" sense.  It is worth doing?  Hell no.
like i said, to each his best. You are entitled to your opinions that you feel shell script is dead. However, i am also entitled to mine that it will not be. Shall we stop here? ;)

---

### Post by pmasiar on 2008-09-12
> **ghostdog74 said:**
> like i said, to each his best. You are entitled to your opinions that you feel shell script is dead. However, i am also entitled to mine that it will not be. Shall we stop here? ;)

Yes, you are entitled to your opinion. And I am happy that here in this thread we have sysadmin expert you show anyone interested (except you) why using modern scripting language with extensive library is in most cases preferable (with real-life examples) to solve practical problems  beyond single line interactive shell command, and why learning universal library is better investment of time that learning bunch of shell tools.

Summary: Learn shell, use it interactively, but when your script is beyond trivial, switch to Python (which you should know anyway)

---

### Post by slavik on 2008-09-12
> **pmasiar said:**
> Yes, you are entitled to your opinion. And I am happy that here in this thread we have sysadmin expert you show anyone interested (except you) why using modern scripting language with extensive library is in most cases preferable (with real-life examples) to solve practical problems  beyond single line interactive shell command, and why learning universal library is better investment of time that learning bunch of shell tools.

Summary: Learn shell, use it interactively, but when your script is beyond trivial, switch to Python (which you should know anyway)
That is wrong on so many levels (IMO) ... have a look at the scripts in /etc/init.d/ :)

---

### Post by LaRoza on 2008-09-12
> **slavik said:**
> That is wrong on so many levels (IMO) ... have a look at the scripts in /etc/init.d/ :)

Like the scripts in init.d are so common to program ;)

That is the perfect domain of scripting, so that isn't an argument against the views.

---

### Post by slavik on 2008-09-12
> **LaRoza said:**
> Like the scripts in init.d are so common to program ;)

That is the perfect domain of scripting, so that isn't an argument against the views.
hmm, then I am missing the point of contention.

---

### Post by mssever on 2008-09-12
> **slavik said:**
> have a look at the scripts in /etc/init.d/ :)
That mess? AFAIK, init scripts are required to run under sh. But they're a bit awkward, and would benefit from a different language, IMO.

---

### Post by Greyed on 2008-09-12
> **ghostdog74 said:**
> shell scripting? ok, so i put the tail command inside a file and call it a shell script. is that fine with you? 

Nope.  Like I said, it is what you do with the information that matters.


> I don't understand what you trying to prove here. If you want, give me a use case example.

Filtering through a file where the results of one regex will trigger one of several other regular expressions.  One could mash it all together in one exceptionally huge branching regex but I find that when my regexes get over, say, 50-60 characters long I prefer to split it out to maintain simplicity.

> 
not really sure what you trying to show here too...
```

DATE=$(date +%Y-%m-%d-%H-%M-%s)
IFS="-"
set -- $DATE
echo "Year: $1"
echo "month: $2"
echo "Day: $3"
echo "23 hours 55min ago: $(date --date='-23 hour -55 min')"
echo "3 weeks ago: $( date --date='3 weeks ago' +'%Y-%M-%d %H:%m:%S')"
unset IFS

```


    First off this is not arithmetic.  I was taking two separate objects which I could manipulate independently of one another and then use in conjunction with one another.  This you're getting a one off return which you would use, how, exactly?  Also note the lengths you have to go to get around globbing.  Hardly a comparable example.
 

> 
```

day=$((  $(( $(date  +%s) / 86400 )) - $(( $(date --date="-3 weeks" +%s) / 86400 )) )) 
find . -type f -mtime +$day -print

```


More wrangling to get around globbing.

> wow, you don't have to show me what these modules can do...

You're not the only person reading this.  This is a public thread on a public forum.

> true it may make things easy for you, but i am sure also that it can be done at the shell. I am not a shell expert but to partially illustrate
```

log1=$(( `stat -c %Y /var/log/messages-1.gz`/86400 ))
log2=$(( `stat -c %Y /var/log/messages-2.gz`/86400 ))
echo $((  $log2 - $log1 )) #delta.days

```


And yet this does not comparison based on the difference, again, hardly comparative.  Again, tons of trying to get around globbing.  You're just proving my point, thanks!

> 
oh no, yes you are, you imported datetime. That's external to me.


No, it's not.  It is a part of Python as of 2.3 released 6 years ago.  That means if you install Python datetime is installed, period.  That would be like arguing that since I used import os that os is not a part of Python even though it has been a part of Python since I started w/1.5.2 about 10 years ago.  Even better, it's like arguing that the stdio library is not a part of C even though every C distribution installs stdio by default.

> like i said, to each his best. You are entitled to your opinions that you feel shell script is dead. However, i am also entitled to mine that it will not be. Shall we stop here? ;)

Sure, you've not proven anything other than my point.  Can't cache regex, can't do time based arithmetic, constant battle with globbing and wrangling shell into doing the right thing.

> **slavik said:**
> That is wrong on so many levels (IMO) ... have a look at the scripts in /etc/init.d/ :)

...

> **LaRoza said:**
> Like the scripts in init.d are so common to program ;)

That is the perfect domain of scripting, so that isn't an argument against the views.

...

> **mssever said:**
> That mess? AFAIK, init scripts are required to run under sh. But they're a bit awkward, and would benefit from a different language, IMO.

Er, you two should have pointed Slavik to this post from this very topic:
[http://ubuntuforums.org/showpost.php?p=5755005&postcount=91](http://ubuntuforums.org/showpost.php?p=5755005&postcount=91)

Specifically the link to the Pardus project which has rewritten the SysV init (AKA, init.d) in Python.  Not a pipe-dream or plans.  It is functional and it boots, now.  Quite frankly Ubuntu's plan to reinvent that wheel should be dropped and they should incorporate Pardus' system.  They've already done the legwork and have the stats to show it is outperforming the current system.  Not to mention Ubuntu's plans are to implement it in C.  o.O

---

### Post by slavik on 2008-09-12
I've written a startup script in Perl ... granted with a shell wrapper (I think) but it was 100% perl code for the functionality I wanted.

---

### Post by Pro-reason on 2008-09-16
I know bash.  By that, I mean that I can use bash, sed, zcat, gawk, etc to do what I currently need to do.

Mostly, this involves: (1) someone on the forums asking what program to use to accomplish a certain task; (2) me looking through Synaptic and finding nothing that does the job; (3) me writing a bash script that does it.

Python may be in some a “more appropriate” tool for real programming, but that's not enough of a motivation to spend a large amount of time learning how to do in a different way what I can already do.

Please convince me to learn Python.

(I'd quite like an excuse to learn another language, but only if I can see it enabling me to do something vaguely useful after a few days.)

---

### Post by LaRoza on 2008-09-16
> **Pro-reason said:**
> 
Please convince me to learn Python.

(I'd quite like an excuse to learn another language, but only if I can see it enabling me to do something vaguely useful after a few days.)
Once you get to the end of the official Python tutorial and understand it, you get a new laptop, car, house and servants for your residents and a monthly check of whatever amoung you need.

The only way to find out, is to do it and see if I am lying.

Other than that, no one can convince you to do anything short of threats.

---

### Post by mssever on 2008-09-16
> **Pro-reason said:**
> Please convince me to learn Python.
You just have to try it. Before I learned Ruby, I was all gung-ho about bash scripting. After I learned Ruby, I realized what I'd been missing all along. Besides, a language like Python or Ruby is incredibly useful to know, anyway. You'll find all kinds of uses for it that you never imagined.

---

### Post by Pro-reason on 2008-09-16
> **LaRoza said:**
> 

Other than that, no one can convince you to do anything short of threats.

Nope, informative comments will do.

I read the first few pages of this thread and didn't see any actual reasons to use Python that applied to me.  No doubt there are some.

So, programmers, convince me to learn Python.

(If someone asked me to convince them to use Ubuntu, I could come up something.)

---

### Post by Pro-reason on 2008-09-16
> **mssever said:**
> You'll find all kinds of uses for it that you never imagined.
Like what?!

That's what I'm asking.

---

### Post by LaRoza on 2008-09-16
> **Pro-reason said:**
> Nope, informative comments will do.

Well, we need to know your goals first ;) Python isn't magic and it could be very well that you wouldn't benefit with your current work.

> 
I read the first few pages of this thread and didn't see any actual reasons to use Python that applied to me.  No doubt there are some.


What applies to you?

---

### Post by Greyed on 2008-09-16
> **Pro-reason said:**
> So, programmers, convince me to learn Python.

You missed La Raza's point.  It is not our job to convince you of anything.  Either you will want to or you won't want to of your own volition.  It is, in fact, a very antagonistic and rude way to put it if you are honestly seeking information.  "I know what I know and that's enough.  Go ahead, prove me wrong!" is essentially what you're saying.

I can tell you what convinced me but that obviously won't work for you.

It isn't shell scripting.

---

### Post by Pro-reason on 2008-09-16
> **Greyed said:**
> You missed La Raza's point.  It is not our job to convince you of anything.  Either you will want to or you won't want to of your own volition.  It is, in fact, a very antagonistic and rude way to put it if you are honestly seeking information.  "I know what I know and that's enough.  Go ahead, prove me wrong!" is essentially what you're saying.

I can tell you what convinced me but that obviously won't work for you.

It isn't shell scripting.

As I said before, if someone asked me to convince them to use Ubuntu, telling me that they were looking for an excuse to get into Linux, I could give them some reasons.  And I wouldn't need to get all snarky with them, or tell them it wasn't my “job”.

Remember that no one is making your reply to anything on this forum, so if you don't consider it your “job” to reply as requested, then just don't reply at all.

As you're just deliberately being unpleasant now, I'll remove this thread from my watchlist.

---

### Post by pp. on 2008-09-16
> **Pro-reason said:**
> So, programmers, convince me to learn Python.

I have not ever neeeded any reasons to learn something, because learning is - for me - an enjoyable experience.

However, there ought to be advantages to learning Python even for people who claim that what they have learned so far covers all of their future or conceivable needs:

[LIST]
[*]Learning a more modern language gives insights into both shortcomings and strengths of the tools you are currently using.
[*]Since Python is being used by very many highly trained and intelligent people, chances are that many solutions being discussed are based on Python concepts and structures and only really understandable if you know Python.
[*]Python is a more powerful language than the usual shell scripting languages and allows even more powerful and cheap solutions than those do.
[*]Many kinds of solutions can be easier understand by less experienced people when done in Python than when done in - say - Bash. If you want to do all the maintenance of your ad-hoc scripts by yourself, keep writing them in Bash. If you want your 'posteriority' to be able to understand, maintain or enhance your stuff, use a language they are likely to understand.
[/LIST]

---

### Post by mike_g on 2008-09-16
I dont really know much about Python or Shell scripting, but one thing I find for sure is that Python code is more intuitive to use/read. I guess that if you know shell scripting well then that wouldent be much of an incentive to learn Python tho.

---

### Post by pmasiar on 2008-09-16
> **Pro-reason said:**
> I know bash.  By that, I mean that I can use bash, sed, zcat, gawk, etc to do what I currently need to do.

(I'd quite like an excuse to learn another language, but only if I can see it enabling me to do something vaguely useful after a few days.)

Please convince me to learn Python.

So you already know you stalled on old and should learn something new. But you are looking at it wrong way: blub programmer way (no offense, read FAQ in my sig - "Beating the averages"). Because you don't know new possibilities opened by more powerful language, you do not feel the need for them: you know how to solve problems 'old way', and your thinking is limited to old way. Once you learn list comprehension, generators, or decorators, whole new ways to solve old problems simpler opens for you. Like a born blind, you do not miss the light and colors.

> Python may be in some a “more appropriate” tool for real programming, but that's not enough of a motivation to spend a large amount of time learning how to do in a different way what I can already do.

What "large amount of time" are you talking about? Python is not C++ or Java. If you are competent programmer, you will learn basic Python in single afternoon. After that, all you need to learn libraries, as needed. Within a week you will be as fast solving problems which are good fit for Python (text parsing etc) as you are in shell or C++ or whatever you use now.

---


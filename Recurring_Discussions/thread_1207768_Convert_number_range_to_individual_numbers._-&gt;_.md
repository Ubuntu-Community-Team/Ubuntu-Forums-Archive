---
title: "Convert number range to individual numbers. -&gt; Off topic."
date: 2009-07-08
forum: Recurring Discussions
---

### Post by bigboy_pdb on 2009-07-08
> **ghostdog74 said:**
> then why are you using grep? its not part of bash shell. awk is a better utility/tool than the bash shell to process text/file. Period.

Because it was late, I had to get up for work in the morning, and I didn't have time to write a script using shopt (since I haven't used it enough to know it backward forward). I was going to mention that shopt should be used where I'm using sed and grep (essentially anywhere where regular expressions are needed), but I saw stroyan's post when I went to preview mine.

I posted my script to show how the numbers can be taken in as arguments.

The awk script that you've written has to run through the bash shell anyway and it doesn't take advantage of pre-existing programs or features such as shell arguments and the seq program (not to mention that it wasn't placed in a file for reuse). There's no need to rewrite code for solutions that exist.

Granted that the op has a better understanding of bash than awk, using a bash script that uses shopt seems best in this situation.

In this case, the speed difference would be insignificant. However, if you really care about parsing speed, you would have mentioned Perl instead of awk.

---

### Post by ghostdog74 on 2009-07-08
> **bigboy_pdb said:**
> Because it was late, I had to get up for work in the morning, and I didn't have time to write a script using shopt (since I haven't used it enough to know it backward forward). I was going to mention that shopt should be used where I'm using sed and grep (essentially anywhere where regular expressions are needed), but I saw stroyan's post when I went to preview mine.

yeah right.

> 
The awk script that you've written has to run through the bash shell anyway 
so? you have to use the shell to run shell internals too.

> 
and it doesn't take advantage of pre-existing programs or features such as shell arguments and the seq program (not to mention that it wasn't placed in a file for reuse). 

shell arguments? awk take in arguments if one wants
```

awk 'BEGIN{
 for(i=1;i<ARGC;i++){
    print ARGV[i]
 }
}' "5-10" "1" "21-40"

```
seq ? its true seq is very common nowadays, but why are mentioning seq when your emphasis is on bash itself. 

```

There's no need to rewrite code for solutions that exist.

```
huh? what solution exist to do this?  are you not writing something from scratch in bash as well.? 

> 
Granted that the op has a better understanding of bash than awk, using a bash script that uses shopt seems best in this situation.

and? what is "best" or not, is not up to you. 

> 
In this case, the speed difference would be insignificant. However, if you really care about parsing speed, you would have mentioned Perl instead of awk.
you are so damn misinformed. who says Perl is definitely faster than awk when it come to parsing?

---

### Post by bapoumba on 2009-07-08
Off topic posts from [http://ubuntuforums.org/showthread.php?p=7582514](http://ubuntuforums.org/showthread.php?p=7582514)

---

### Post by geirha on 2009-07-08
Another one in bash, without using eval.
```

#!/bin/bash

numbers="1 2 4-6 8-10"
result=()

for i in $numbers; do
    for (( j=${i%-*}; j <= ${i#*-}; ++j )); do  
        result+=($j); 
    done 
done

echo "${result[@]}"

```

---

### Post by bigboy_pdb on 2009-07-08
> **ghostdog74 said:**
> yeah right.

A post of mine from a while ago about patterns and shopt in bash:
[http://ubuntuforums.org/showpost.php?p=7267425&postcount=10](http://ubuntuforums.org/showpost.php?p=7267425&postcount=10)

You shouldn't be so pompous. You'll be more critical if you're less emotional and prideful.

I'll respond to a few of your other comments.

When you read a response, you should read it as a whole. I mentioned seq because there's no point in writing code to do something that another program does for you. seq does what the OP needed and writing code to duplicate what it does is unnecessary. Also, the OP himself said that he didn't know awk very well and wrote his original code in bash.

In addtion, I never said that awk can't take in arguments. I said that your program didn't take them in. The script should be reusable and executable from the shell.

Furthermore, I was being facetious about Perl! The strings that are being parsed are small and the expressions that are parsing them aren't complicated. As I said, the difference would be negligible.

---

### Post by ghostdog74 on 2009-07-08
> **bigboy_pdb said:**
> A post of mine from a while ago about patterns and shopt in bash:
[http://ubuntuforums.org/showpost.php?p=7267425&postcount=10](http://ubuntuforums.org/showpost.php?p=7267425&postcount=10)

so? i am talking about this statement you made:
> I don't see why you need awk for that since it can be done using the bash shell, which after that you posted a bash version that uses grep and sed and seq. I asked you what's the difference in using awk since they are both not using bash shell internals. But all you could do give a sorry excuse?


> 
When you read a response, you should read it as a whole. I mentioned seq because there's no point in writing code to do something that another program does for you.

really? What if the system doesn't have seq and one cannot download stuff from internet. one would have to create code on his own. furthermore, I am "attacking" your point of "use bash, why use awk" , so by mentioning seq, aren't you contradicting yourself? bash already has a way to do "sequence", i am sure you know this syntax {0..9} ,, therefore, why use seq?

>  seq does what the OP needed 
no it does not. not entirely. notice your code, how you used sed to remove the dash etc? if seq source code can be changed to take in ranges, then its another story. That said, seq is still not needed because bash can do it.

>  Also, the OP himself said that he didn't know awk very well and wrote his original code in bash.
that doesn't mean he can't see another awk solution or can't use it in future. (As a side note, you can see how ugly the syntax for bash is)

> 
In addtion, I never said that awk can't take in arguments. I said that your program didn't take them in. The script should be reusable and executable from the shell.

that's not even worth talking about. its TRIVIAL to add in. Besides, its not even mention OP wants it as arguments.

> 
Furthermore, I was being facetious about Perl! The strings that are being parsed are small and the expressions that are parsing them aren't complicated. As I said, the difference would be negligible.
look at this quote you made:
[quote="bigboy_pdb"]
However, if you really care about parsing speed, you would have mentioned Perl instead of awk
[/quote]
you are talking about parsing speed, in response, i said its not true. But in the above, you detracted from your argument and say the parsing is not complicated because the strings are small and not complicated, then what makes you think awk can't do the job as well as Perl since its small and not complicated? I can also tell you why its not true, especially for big files. we use a big file, roughly 2 million plus lines. and equivalent Perl and awk commands to produce same output
```

# wc -l < file
21898103
# head -3 file
this is a line
this is a line
this is a line

# perl  -lane "print @F[-1];" file | more
line
line
line
line
line
line
line
line
# awk '{print $NF}' file  |more
line
line
line
line
line
line
line
# time perl  -lane "print @F[-1];" file >/dev/null

real    3m25.221s
user    3m21.537s
sys     0m1.252s
# time awk '{print $NF}' file  > /dev/null

real    0m34.513s
user    0m31.962s
sys     0m0.716s
# time perl  -lane "print @F[-1];" file >/dev/null

real    3m21.627s
user    3m13.536s
sys     0m1.668s
# time awk '{print $NF}' file  > /dev/null

real    0m32.081s
user    0m29.814s
sys     0m0.740s


```
Perl takes more than 2 minutes to just get the last column, whereas awk takes less than a minute. does that convince you that what you said about Perl is not entirely true?

---


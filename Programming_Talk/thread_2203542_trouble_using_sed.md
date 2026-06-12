---
title: "trouble using sed"
date: 2014-02-04
forum: Programming Talk
---

### Post by IAMTubby on 2014-02-04
Hello,
 I have tried to get the part of a string between two words/characters using sed -n but I'm not getting the desired output


I have a string as follows
```
[INFO_|02/01 06:51:15|Data.logInfo:1447] gprmc: [192.168.0.102] POST: http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33 [acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33]
```


I want to get only the parts between(and including)http to *33
So basically the output should be like
```
http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33
```


However, when I try with the following, it gives me a different output. And firstly works only if I remove all the spaces, something I'm not allowed to do. ```
echo "[INFO_|02/01 06:51:15|Data.logInfo:1447]gprmc:[192.168.0.102]POST:http://192.168.0.106:8080/gprmc/Dataacct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33[acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33]"|sed -n 's/.*POST\([^ ]*\)acct/\1/p'
```


Thanks

---

### Post by varunendra on 2014-02-04
This worked here -
```
sed -r 's_.*POST: (http://.*,.33) .*_\1_'
```

Test command -
```
echo "[INFO_|02/01 06:51:15|Data.logInfo:1447] gprmc: [192.168.0.102] POST: http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33 [acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33]" | sed -r 's_.*POST: (http://.*,.33) .*_\1_'
```

Result output -
```
http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33
```

If you don't use -r switch (extended regexp), you'll have to escape the braces like you did originally (that is, "\(" and "\)" )

The problem in your filter is that you have told sed to match EVERYTHING in-between the given expressions EXCEPT SPACES. It is generously doing so :)

---

### Post by IAMTubby on 2014-02-04
Thanks a lot varunendra :)
I tried it out and it works for me. Let me spend some more time on it and get back to you if I still have not got it.

---

### Post by varunendra on 2014-02-04
Sure, I'd love to explain to the extent where I get confused myself :P

But if you sort it out all by yourself, without risking an explanation from me, then please consider marking the thread as [SOLVED]. :)

---

### Post by Bachstelze on 2014-02-04
sed is overkill here, use cut (or maybe awk).

---

### Post by IAMTubby on 2014-02-04
> **varunendra said:**
> This worked here -
```
sed -r 's_.*POST: (http://.*,.33) .*_\1_'
```

varunendra,
I am reading some sed tutorials and have understood a few things, but let me put my queries here.
I'm aware that the 2nd and 3rd points are quite an ask, you can point me somewhere in case they sound crazy :)

1. sed -r 's_.[COLOR=#ff0000]*[/COLOR]POST: ([http://.*,.33](http://.*,.33)) .[COLOR=#ff0000]*[/COLOR]_\1_'
  [TABLE="width: 500"]
[TR]
[TD]-r[/TD]
[TD]Extended Regex to escape the braces(quoting you)[/TD]
[/TR]
[TR]
[TD]s[/TD]
[TD]The following regex is a substitution? (But what are we substituting ?)[/TD]
[/TR]
[TR]
[TD][COLOR=#ff0000]*[/COLOR][/TD]
[TD]Does it mean start with and end with ? But hmm, can do with some explanation here[/TD]
[/TR]
[TR]
[TD]_\1_[/TD]
[TD]I read somewhere, "[COLOR=#000000][FONT=verdana] Replace anything that matches the blue part with the saved capture[/FONT][/COLOR]"  but couldn't make sense of it[/TD]
[/TR]
[/TABLE]

2. Also, to the original method, is there a way to replace the hard coded word 33 with some other pattern; the reason being, the actual format would be something like
```
[INFO_|02/01 06:51:15|Data.logInfo:1447] gprmc: [192.168.0.102] POST: http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*[COLOR=#0000ff]**SOMEHEXADECIMAL**[/COLOR] [acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,***[COLOR=#0000ff]SOMEHEXADECIMAL[/COLOR]**]
```
Note : SOMEHEXADECIMAL can be anything say, 33, or it can be 3a or 4b etc..

3. May I ask one more question.
 To the output below, I want to : (please see characters in green in the string below)
 A.Replace the space between 'Data' and 'acct' with a question mark
 B.Add a '\' before the word '$GPRMC' because it keeps getting trimmed off because of the '$' ```
http://192.168.0.106:8080/gprmc/Data**[COLOR=#008000]?[/COLOR]**acct=test01&dev=test01&gprmc=[COLOR=#008000]**\**[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]$GPRMC[/FONT][/COLOR],012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33
```
Would cutting the strings at the desired location, followed by concatenating part1 + '?' + part2 be the correct approach ? Or is there a better way ?

Thanks.

---

### Post by IAMTubby on 2014-02-04
Okay Bachstelze, will keep that in mind.
I've just started spending some time on sed. I'll go over to cut/awk or do you think I should look at it right away ?

---

### Post by IAMTubby on 2014-02-04
> **Bachstelze said:**
> sed is overkill here, use cut (or maybe awk).
Okay Bachstelze, will keep that in mind.
I've just started spending some time on sed. I'll go over to cut/awk or do you think I should look at it right away ?

---

### Post by steeldriver on 2014-02-04
How about something like

```
awk 'BEGIN{OFS="?"} {sub("[$]","\\$",$7); print $6,$7}'
```

e.g.
```

$ s='[INFO_|02/01 06:51:15|Data.logInfo:1447] gprmc: [192.168.0.102] POST: http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33 [acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33]'


$ awk 'BEGIN{OFS="?"} {sub("[$]","\\$",$7); print $6,$7}' <<< "$s"
http://192.168.0.106:8080/gprmc/Data?acct=test01&dev=test01&gprmc=\$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33

```

---

### Post by IAMTubby on 2014-02-05
> **steeldriver said:**
> How about something like
```
awk 'BEGIN{OFS="?"} {sub("[$]","\\$",$7); print $6,$7}'
```

Thanks steeldriver, that worked, but how come this doesn't work
```
$ awk 'BEGIN{OFS="?"} {sub("[$]","\\$",$7); print $6,$7}' <<< "[INFO_|02/01 06:51:15|Data.logInfo:1447] gprmc: [192.168.0.102] POST: http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33 [acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33]"

```

The output being the following, notice the missing $GPRMC after the word gprmc.
```
http://192.168.0.106:8080/gprmc/Data?acct=test01&dev=test01&gprmc=,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33
```

Would it be possible to give me some explanation, so I can get started ?

---

### Post by steeldriver on 2014-02-05
... because in **double** quotes, the shell expands $GPMRC as an (empty) **variable** before passing the string to awk - if you are reading the string from a file that should not be an issue.

---

### Post by IAMTubby on 2014-02-05
> **steeldriver said:**
> ... because in **double** quotes, the shell expands $GPMRC as an (empty) **variable** before passing the string to awk - if you are reading the string from a file that should not be an issue.
Thanks steeldriver, I have written this in terms of a script and it's working like I want it to, thank you.

```

#!/bin/bash

GPRMC="\$GPRMC"
mystring="[INFO_|02/01 06:51:15|Data.logInfo:1447] gprmc: [192.168.0.102] POST: http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33 [acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33]"


awk 'BEGIN{OFS="?"} {sub("[$]","\\$",$7); print $6,$7}' <<< $mystring

```

But can you tell me
1. How do I store the output in a variable instead of printing it on screen? I need to reuse this variable elsewhere
2. I understand that BEGIN is like to initialize, OFS is like Field separator, but what are we doing in the line **awk 'BEGIN{OFS="?"} {sub("[$]","\\$",$7); print $6,$7}'** Are we splitting it at every '?'. Can you provide me an explanation of this, if possible ?

Thanks.

---

### Post by steeldriver on 2014-02-05
TBH the BEGIN{OFS="?"} is a bit of a hack - awk (by default) splits input lines into fields separated by whitespace, and its print function separates output fields by whitespace, so setting the *output *field separator (OFS) to ? is just a way to replace the space between the **http://192.168.0.106:8080/gprmc/Data** and **acct=** by a ? character

To store command output in a variable you can use $(*command*)

```

newvar=$(awk 'BEGIN{OFS="?"} {sub("[$]","\\$",$7); print $6,$7}' <<< $mystring)

```

---

### Post by varunendra on 2014-02-06
Seeing that you are being answered by seasoned experts now, I'm just answering what you specifically asked to me. You may already be aware of most of it, I'm just trying to make it more useful by including the details.

First off, I made a mistake in my previous post by using double quotes with echo instead of single quotes. The result - $GPRMC was getting expanded to its value (blank) instead of being passed as a string. I noticed that only after reading your post.

Now the answers -
> **IAMTubby said:**
> 
1. sed -r 's_.[COLOR=#ff0000]*[/COLOR]POST: ([http://.*,.33](http://.*,.33)) .[COLOR=#ff0000]*[/COLOR]_\1_'
  -r    Extended Regex to escape the braces(quoting you)
-r switch enables interpretation of Extended Regular Expressions, which also includes interpretation of braces () as a grouping element. Without it, they need to be escaped (by adding a backslash "\" before them) to prevent bash from processing them in its own way.

>   s    The following regex is a substitution? (**But what are we substituting ?**)
We were matching EVERYTHING in the line and grouping a specific part of it. We were then Substituting this Everything with Nothing, but were escaping the first group (\1) from being substituted this way. So you could say that we were substituting 'Everything' with that grouped part alone. The explanation of "\1" below should make this clearer.

>   [COLOR=#ff0000]*[/COLOR]    Does it mean start with and end with ? But hmm, can do with some explanation here
In sed (or Regular Expressions), ***** means "repeat any number of times". It matches repetitions of whatever it is immediately placed after. For example **8*** would match 8888888, **[0-9]*** would match any series of digits (like 403053252), **[a-z]*** would match any series of small letter alphabets (like adefsdse). Now a dot (**.**) in regular expressions means [s]"any printable character"[/s] "Any Character" - printable or not. So a "**.***" matches any series of [s]printable characters, and as soon as the first non-printable character is found (like a space), the matching stops[/s] Characters, or 'Everything' if it is not delimited by some Fixed Character or String before or after it (like "**.*A**" or "**A.***" or "**A.*B**" *(better explained in next post below, sorry for the 'Printable Chars' confusion)*.

>   _\1_    I read somewhere, "[COLOR=#000000][FONT=verdana] Replace anything that matches the blue part with the saved capture[/FONT][/COLOR]"  but couldn't make sense of it
When you match a pattern in sed, you can group parts of it with braces. The number (1 in above example) denotes the number of group in the matched pattern. Escaping it with a backslash (\) prevents it from being processed by sed *(I'm not sure on "How", probably 'Escaping' makes the shell 'Ignore' it when sending the data to sed for processing)*, thus retaining or 'Saving' it as it is. An example to make it clear -
```
echo "abcdefgh12345678" | sed -r 's:ab[COLOR="#B22222"](cd)[/COLOR]ef[COLOR="#0000CD"](gh)[/COLOR]12[COLOR="#008000"](34)[/COLOR]56[COLOR="#FF0000"](78)[/COLOR]:[COLOR="#FF0000"]\4[/COLOR]-[COLOR="#0000CD"]\2[/COLOR]:'
```
..would produce result "**[COLOR="#FF0000"]78[/COLOR]-[COLOR="#0000CD"]gh[/COLOR]**"

It may also be interesting to know that you can define groups within groups (braces within braces) this way. For example -
In a grouped pattern "ab**(**cd**[COLOR="#FF0000"]([/COLOR]****[COLOR="#0000CD"]([/COLOR]**ef**[COLOR="#0000CD"])[/COLOR]****[COLOR="#800080"]([/COLOR]**gh**[COLOR="#800080"])[/COLOR]**ij**[COLOR="#FF0000"])[/COLOR]**kl**)**mn",
\1=cdefghijkl
\2=[COLOR="#FF0000"]efghij[/COLOR]
\3=[COLOR="#0000CD"]ef[/COLOR]
\4=[COLOR="#800080"]gh[/COLOR]

We'll take advantage of this kind of grouping in answer to your final question (not that it would be more efficient than what others suggested, just for the kick of it ;)).

> 2. Also, to the original method, is there a way to replace the hard coded word 33 with some other pattern; the reason being, the actual format would be something like
```
[INFO_|02/01 06:51:15|Data.logInfo:1447] gprmc: [192.168.0.102] POST: http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*[COLOR=#0000ff]**SOMEHEXADECIMAL**[/COLOR] [acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,***[COLOR=#0000ff]SOMEHEXADECIMAL[/COLOR]**]
```
Note : SOMEHEXADECIMAL can be anything say, 33, or it can be 3a or 4b etc..
You can replace 33 with a regular expression like [[:alnum:]]* or to be more precise (strictly two digits/alphabets), [[:alnum:]][[:alnum:]]. This ([[:alnum:]]) is a POSIX compatible Regular Expression and if you wish to use a more generalized RegExp., you may use [a-f0-9][a-f0-9] which will not only be more compatible (in case a shell doesn't understand POSIX character class), but also will limit the alphabets range to 'a-f', which is what is possible in a hexadecimal number. If there is a chance of the alphabets being in Capital Letters, use [a-fA-F0-9][a-fA-F0-9] instead.

> 
 To the output below, I want to : (please see characters in green in the string below)
 A.Replace the space between 'Data' and 'acct' with a question mark
You can group the desired parts into two groups and then use '?' in the substitution like -
```
sed -r 's_.*POST: [COLOR="#800000"]**(http://.*/Data)**[/COLOR] [COLOR="#0000CD"]**(acct=.*,.[a-f0-9][a-f0-9])**[/COLOR] .*_[COLOR="#800000"]**\1**[/COLOR]?[COLOR="#0000CD"]**\2**[/COLOR]_'
```

>  B.Add a '\' before the word '$GPRMC' because it keeps getting trimmed off because of the '$' ```
http://192.168.0.106:8080/gprmc/Data**[COLOR=#008000]?[/COLOR]**acct=test01&dev=test01&gprmc=[COLOR=#008000]**\**[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]$GPRMC[/FONT][/COLOR],012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33
```
Now this is something where my understanding of shell processing fails to support my explanation capability. I know how to do that, but can't properly explain it.
We'd take the grouping technique farther and turn the filter into the following form -
```
sed -r 's_.*POST: ((http://.*/Data) (acct=.*)(\$GPRMC.*,.[a-f0-9][a-f0-9])) .*_\2?\3\\\4_'
```

So using this final filter, the test command (with 33 replaced with 3b)-
```
echo '[INFO_|02/01 06:51:15|Data.logInfo:1447] gprmc: [192.168.0.102] POST: http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*3b [acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*3b]' | sed -r 's_.*POST: ((http://.*/Data) (acct=.*)(\$GPRMC.*,.[a-f0-9][a-f0-9])) .*_\2?\3\\\4_'
```
Produces result -
```
http://192.168.0.106:8080/gprmc/Data?acct=test01&dev=test01&gprmc=\$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*3b
```

What I can't explain confidently is why we needed to escape the "$GPRMC" in the matching pattern this time. My guess is that the grouping braces are processed by the shell first, then passed to sed. So while processing the contents of the braces, the $GPRMC gets expanded to its value (a blank in our test case) unless we escape it with a single backslash (\$GPRMC).

Oh, and if you are NOT going to pass this result again to the shell, obviously you don't have to replace $GPRCM with \$GPRCM. I was just telling a 'HowTo', and don't think you really need it.

> Would cutting the strings at the desired location, followed by concatenating part1 + '?' + part2 be the correct approach ? Or is there a better way ?
Golden Advice by Bachstelze, and Golden question from you.
Not asked to me, but I think YES, if the nature of the patterns to be matched is fixed and you can properly match it, then the Shell's inbuilt functions are always faster. I might use something like -
```
cut -d " " -f 6-7 <<< 'your string here' | tr " " "?"
```
So the test command -
```
cut -d " " -f 6-7 <<< '[INFO_|02/01 06:51:15|Data.logInfo:1447] gprmc: [192.168.0.102] POST: http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*3b [acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*3b]' | tr " " "?"
```
..produces the output -
```
http://192.168.0.106:8080/gprmc/Data?acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*3b
```
..which is **same** as what we obtained from the complex sed filter, only **much-much simpler and reliable too**, _if the number and position of spaces is fixed in the pattern to be matched_. :D
(oh, but if you do need to add a "\" before $GPRMC, then you must use either sed or some complex script, in which case, sed is a much better choice).

Hope you enjoyed the explanation :P *<phew!!>*


Now I have a doubt/question for **Bachstelze** -

@**Bachstelze**
I don't have enough understanding of the difference, and have almost absolute lack of knowledge about awk, so just hoping to learn something from you or anyone willing to explain or share their opinion on this -
> **Bachstelze said:**
> sed is overkill here, use cut (or maybe awk).
"sed is overkill".... but not "awk" ?? :confused:

As far as I know, sed and awk are both external programs (awk being a full programming language). So I believe the shell (bash) would need to do more work for loading awk (being much richer than sed) than for loading sed. So where am I wrong in thinking that using sed would be faster? Or is it that awk would be faster AFTER being loaded once?

Can you explain this for me please? Just hoping to expand my knowledge regarding the basics..

**PS:**
I ran 'while' loops of 10,000 iterations with all 3 variants, and the result on my i3-2330M CPU was - cut+tr 52 sec, awk 58 sec, sed 1:04 min (even the simplest form as in my first post didn't help more than 4 sec.)

---

### Post by Vaphell on 2014-02-06
> PS:
I ran 'while' loops of 10,000 iterations with all 3 variants, and the result on my i3-2330M CPU was - cut+tr 52 sec, awk 58 sec, sed 1:04 min (even the simplest form as in my first post didn't help more than 4 sec.) 

Well, you mostly tested how good your system is at spawning instances of programs, either way native bash solution eats all of them for breakfast. This particular case is a simple trimming + replace space with ?, bash parameter expansion is plenty enough for that.

```
$ str='[INFO_|02/01 06:51:15|Data.logInfo:1447] gprmc: [192.168.0.102] POST: http://192.168.0.106:8080/gprmc/Data acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33 [acct=test01&dev=test01&gprmc=$GPRMC,012113,A,1257.604403,N,07742.223007,E,0000,000.0,010214,,*33]'
$ time for i in {1..1000}; do url=$( sed -r 's/.*(http[^ ]+) ([^ ]+).*/\1?\2/' <<< "$str" ); done

[COLOR="#FF0000"]real	0m3.161s[/COLOR]
user	0m0.076s
sys	0m0.440s
$ time for i in {1..1000}; do url=$( awk '{ print $6"?"$7 }' <<< "$str" ); done

[COLOR="#FF0000"]real	0m2.639s[/COLOR]
user	0m0.088s
sys	0m0.416s
$ time for i in {1..1000}; do url=${str#*POST: }; url=${url% [*}; url=${url/ /?}; done

[COLOR="#0000FF"]real	0m0.096s[/COLOR]
user	0m0.100s
sys	0m0.000s
```


Prefer native bash, only when you see it's not flexible enough in a given scenario look further at sed/awk/cut/tr and what not.

---

### Post by varunendra on 2014-02-06
Eh, and I was under impression that 'cut' and 'tr' are inbuilt functions of bash :/

Thanks for sharing the gem Vaphell, basically that's why I post in here.... to improvise. :P

---

### Post by IAMTubby on 2014-02-06
> **varunendra said:**
> I'm just trying to make it more useful by including the details.
varunendra, :)
I read through your post over and over again, and every time, things made more sense. Thank you so much for the wonderful explanation. (I also did a few experiments like replacing **sed -r 's_.*POST: (([http://.*/Data]("http://.%2A/Data")) (acct=.*)(\$GPRMC.*,.[a-f0-9][a-f0-9])) .*_\2?\3\\\4_'** with **sed -r 's_.*POST: ([http://.*/Data]("http://.%2A/Data")) (acct=.*)(\$GPRMC.*,.[a-f0-9][a-f0-9]) .*_\1?\2\\\3_'** (_Notice that 2,3,4 have been replaced by 1,2,3 by making appropriate changes in putting braces_) and saw the same result. This gives me some confidence that I am beginning to understand.

However, based on your final explanation, I have a few more questions.
**1.** I'm sorry, but I still haven't understood some of the .* in the solution(the others I have understood and goes with your explanation of ANY printable character). Please can you explain the ones in red, green and orange
```
sed -r 's_**[COLOR=#FF0000].*[/COLOR][COLOR=#FF0000]POST:[/COLOR]** (http://.*/Data) (acct=.*)(\$GPRMC**[COLOR=#008000].*,[/COLOR]**.[a-f0-9][a-f0-9]) [COLOR=#FFA500]**.***[/COLOR]_\1?\2\\\3_'
```
-Does the one in [COLOR=#FF0000]**red**[/COLOR] mean keep proceeding until you find the word POST ?
-The one in [COLOR=#008000]**green**[/COLOR] is confusing me, because, isn't ',' also a printable character, so doesn't .* cover that too ?
-The one in [COLOR=#FFA500]**orange**[/COLOR], sorry, couldn't make sense of it.
[B]
2. [/B]Sorry, I didn't understand the part about **s_** in **sed -r 's_.*POST: (([http://.*/Data]("http://.%2A/Data")) (acct=.*)(\$GPRMC.*,.[a-f0-9][a-f0-9])) .*_\2?\3\\\4_'** If it's difficult to explain, we can skip this for now and I shall read up on it again.
> We were matching EVERYTHING in the line and grouping a specific part of it. We were then Substituting this Everything with Nothing, but were escaping the first group (\1) from being substituted this way. So you could say that we were substituting 'Everything' with that grouped part alone.


**3.** And finally, I did not understand the two underscores in **_**\1?\2\\\3**_**. (Note : I have the understood the \1 and \2 and \3 very clearly; your explanation was brilliant)

Once again, thanks varunendra. I know much more about sed from just reading your reply, these questions are only to get some more foothold. You have solved my original problem already :)

---

### Post by varunendra on 2014-02-06
You're always welcome to ask more. But be aware that I am no expert of sed, regular expressions or anything so far discussed in the thread. I'm just a learner like you who likes sed, and as such, my explanations *May be Wrong*, as I already have been three times by now in this very thread. :)

Before proceeding further, I also need to make the third correction in my explanation before - the dot (.) means "Any Character", not just "Printable" ones. Going to correct that in my previous post too.... sorry for the silly mistake.

> **IAMTubby said:**
> Please can you explain the ones in red, green and orange
```
sed -r 's_**[COLOR=#FF0000].*[/COLOR][COLOR=#FF0000]POST:[/COLOR]** (http://.*/Data) (acct=.*)(\$GPRMC**[COLOR=#008000].*,[/COLOR]**.[a-f0-9][a-f0-9]) [COLOR=#FFA500]**.***[/COLOR]_\1?\2\\\3_'
```
-Does the one in [COLOR=#FF0000]**red**[/COLOR] mean keep proceeding until you find the word POST ?
-The one in [COLOR=#008000]**green**[/COLOR] is confusing me, because, isn't ',' also a printable character, so doesn't .* cover that too ?
-The one in [COLOR=#FFA500]**orange**[/COLOR], sorry, couldn't make sense of it.
**_[COLOR="#FF0000"]For the first point[/COLOR]_** - Yes, exactly.
The **[COLOR="#FF0000"].*POST[/COLOR]** means "_Any Character(s), Any number of times, INCLUDING the word "POST" In-the-Last_". So two things just for sake of clarity -

[INDENT]**1) [COLOR="#FF0000"].*[/COLOR]** together means "A series of any type of characters, including non-printing ones". In contrast, a "P*" would mean PPPP.... (no spaces or other characters in-between), a p* would mean ppppp....., a 9* would mean 999999..... etc. But a ".*" can cover _Anything and Everything_, for example -
**[COLOR="#0000CD"]*@nyr@nd0m_ch@Ract3r$ 1ncL.udIng$p@   ces.!==*[/COLOR]** .

**2)** If we also include some FIXED characters Before/After/In-between such pairs, then the match has to include those FIXED characters also, otherwise there would be no match found. So a line like ***"My tr1@l Lin3 wid rep3!ted chars"***,

[INDENT]expression "**.***" would match **the entire line**, but
expression "**.*L**" would match "**My tr1@l L**",
expression "**t.*3**" would match "**tr1@l Lin3 wid rep3**", *(note that the match didn't stop at the first "3". This is called "Greedy Algorithm" - where an expression covers as much as possible without breaking the rule)*
expression "**L.***" would match "**Lin3 wid rep3!ted chars**"
and expression "**L.*3**" would match "**Lin3 wid rep3**"[/INDENT][/INDENT]

**[COLOR="#006400"]For the second point -[/COLOR]**
Good question (not that others were bad :P). Yes the comma (,) would be covered by ".*", but we want to tell sed that this particular character (**One** character before our hexadecimal number) STRICTLY has to be a COMMA, not any other character.

**[COLOR="#FF8C00"]For the third point (...f0-9]) .*...)-[/COLOR]**
The part after the Hexadecimal number ([a-f0-9][a-f0-9]) tells that there HAS to be a SPACE, not anything else after the hexadecimal, then Anything and Everything after it, which implies "till the end of line".

I would like to add that I used a dot (.) Before the hexadecimal expression. It means there HAS to be STRICTLY ONE Character between the comma and the hex number. I couldn't use a literal "*" unless escaping it, because otherwise it would have expanded to its meaning - "Repetition of the comma (,) to any number of times". Using a dot was easier. ;)

> [B]
2. [/B]Sorry, I didn't understand the part about **s_** in **sed -r 's_.*POST: (([http://.*/Data]("http://.%2A/Data")) (acct=.*)(\$GPRMC.*,.[a-f0-9][a-f0-9])) .*_\2?\3\\\4_'** If it's difficult to explain, we can skip this for now and I shall read up on it again.
I don't yet understand which part is confusing you, so will try to explain whatever I think may be confusing for most new learners..

You already know the generic form of the s(ubstitute) command of sed - **"s/<stuff to be substituted>/<substitution>/"**
I assume you also know that the delimiter "/" can be replaced by many other characters as suitable to us, or be needed depending upon the nature of the string to be matched. For example, **#,_,|** etc can be used as delimiters as well. So the above command can also be written as **"s_<stuff to be substituted>_<substitution>_"**

So **the whole expression In-Between the first two underscores (_)** was the _pattern that was to be substituted_. Being started with "**.***", and ended with the same, it was obviously covering the whole line that was supplied, while 'Grouping' certain parts of it so we can call them later as substitutions.

**The part between the second and third underscores** was the _substitution_ itself. This was an arranged combination of those certain parts of the string that we had grouped earlier in the "Stuff to be substituted" part of the command.

So we were _Substituting the whole line_, with _Selected parts_ of it.

Feel free to ask again if I didn't or couldn't explain the part you were interested in, but please help me in understanding what exactly I need to explain.


> **3.** And finally, I did not understand the two underscores in **_**\1?\2\\\3**_**.
I hope I already explained that above. I used underscores instead on slashes (/) as delimiters. Just because I could? Yeah, partly :P, but partly to avoid confusion, because "/" were also present in the string we were going to match.

If you mean "Why two **Backslashes**" before \3, then those were to put a Literal "\" before whatever was going to be the value of "\3" in the output. The result for \3 in our example, it was "GPRMC", and in order to put a literal backslash before it in the output (so it becomes "\GPRMC"), we needed to use Two "\" in the expression. It is necessary for a literal "\" (the first "\" is always treated as an 'escape' character, thus retaining as it is whatever is immediately after it).

If we used \3 alone, we wouldn't have gotten the "\" before "GPRMC", and if we used "\\3" then the result would have been a literal "\3" instead of "\GPRMC".

More questions? :)

---

### Post by IAMTubby on 2014-02-07
> **varunendra said:**
> You're always welcome to ask more.....More questions?
varunendra, I cannot tell you how well I have understood, thanks to your explanation.

The explanation about the following, among others have made concepts very clear to me
1. expression "**.*L**" would match "**My tr1@l L**", for the first point(first question)
2. **s_<stuff to be substituted>_<substitution>_ **for the second question

Thank you for being extremely patient with me. Re-reading my questions,  I feel I have asked similar questions multiple times(like for example 1.What does s_ mean, and 2.What are the two underscores in _\1?\2\\\3_). But that's because I wasn't aware that they belong to the same concept. Thanks for taking time to answer each one separately

Marking the thread as solved [IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

---

### Post by varunendra on 2014-02-07
No problem. :)

To mark the thread as [SOLVED] so that it appears as such in the search results, please see this link : [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

*(while I go make corrections to my previous post that I forgot earlier :P)*

---


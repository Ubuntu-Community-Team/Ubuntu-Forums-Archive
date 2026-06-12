---
title: "[Bash] replace complete words in a text"
date: 2009-07-15
forum: Programming Talk
---

### Post by Thibaud74 on 2009-07-15
Hi,

I need to replace words in a text. I can do that with sed, but it doesn't exactly replace a word, but a chain. For example, with these script :
```
echo "the thermostat works" | sed -e "s/the/a/g"
```
I get : "a armostat works", not "a thermostat works" !

I have to replace about 200 words, so it'd be useful to know the good script...

Thanks for help,
Thibaud.

---

### Post by ghostdog74 on 2009-07-15
awk
```

# echo "the thermostat works" |awk '{for(i=1;i<=NF;i++)if($i=="the"){$i="a"}}1'
a thermostat works


```

---

### Post by Thibaud74 on 2009-07-15
Hi ghostdog74,

Is it possible using a variable in awk parameters ? By e.g., this doesn't get "for what" as we attend :

```
var="so" ; echo "so what" | awk '{for(i=1;i<=NF;i++)if($i=="$var"){$i="for"}}1'
```

Thanks you,
Thibaud.

---

### Post by ghostdog74 on 2009-07-15
> **Thibaud74 said:**
> Hi ghostdog74,

Is it possible using a variable in awk parameters ? By e.g., this doesn't get "for what" as we attend :

```
var="so" ; echo "so what" | awk '{for(i=1;i<=NF;i++)if($i=="$var"){$i="for"}}1'
```

Thanks you,
Thibaud.

```

awk -v var=$var '{.......{$i==var}....}'

```

---

### Post by sisco311 on 2009-07-15
or
```
awk '{.......{$i=="'"$var"'"}....}'
```

---

### Post by ghostdog74 on 2009-07-15
> **sisco311 said:**
> or
```
awk '{.......{$i=="'"$var"'"}....}'
```

although its all about preferences, i would still not recommend this way, as there are too many quotes to take care of. Imagine if there are more than 1 variables to be passed to awk.... still, neater to use -v

---

### Post by Thibaud74 on 2009-07-15
Great, thanks a lot ! :-)

---

### Post by geirha on 2009-07-15
Similar to ^ and $ which matches the start and end of a line, you have \< and \> which matches the start and end of a word, so with a slight change to your original sed:
```
$ echo "the thermostat works" | sed -e "s/\<the\>/a/g"
a thermostat works

```

---

### Post by Thibaud74 on 2009-08-07
Thanks a lot Geirha. In fact, the awk procedure doesn't work perfectly. By example with this script :
```
echo "I like ubuntu, specially the last ubuntu" | awk -v origin="ubuntu" -v target="mandriva" '{for(i=1;i<=NF;i++)if($i==origin){$i=target}}1'
I like ubuntu, specially the last mandriva
```

But with sed that works :
```
echo "I like ubuntu, specially the last ubuntu" | sed -e "s/\<ubuntu\>/mandriva/g"
I like mandriva, specially the last mandriva
```

---

### Post by ghostdog74 on 2009-08-07
> **Thibaud74 said:**
>  In fact, the awk procedure doesn't work perfectly. By example with this script :
```
echo "I like ubuntu, specially the last ubuntu" | awk -v origin="ubuntu" -v target="mandriva" '{for(i=1;i<=NF;i++)if($i==origin){$i=target}}1'
I like ubuntu, specially the last mandriva
```
[/CODE]
that's because i expect those words to find and replace have boundaries, ie one word by itself. you have a comma after the first "ubuntu", if that's the case
```

# echo "I like ubuntu, specially the last ubuntu" | awk -v origin="ubuntu" -v target="mandriva" '{ gsub(origin,target) }1'
I like mandriva, specially the last mandriva


```

---

### Post by spupy on 2009-08-07
> **geirha said:**
> Similar to ^ and $ which matches the start and end of a line, you have \< and \> which matches the start and end of a word, so with a slight change to your original sed:
```
$ echo "the thermostat works" | sed -e "s/\<the\>/a/g"
a thermostat works

```

I thought that "\b" matches word boundary?
[http://www.regular-expressions.info/wordboundaries.html](http://www.regular-expressions.info/wordboundaries.html)

---

### Post by geirha on 2009-08-07
> **spupy said:**
> I thought that "\b" matches word boundary?
[http://www.regular-expressions.info/wordboundaries.html](http://www.regular-expressions.info/wordboundaries.html)

Indeed, replacing them with \b will work too.

> 
The GNU extensions to POSIX regular expressions add support for the \b and \B word boundaries, as described above. GNU also uses it's own syntax for start-of-word and end-of-word boundaries. \< matches at the start of a word, like Tcl's \m. \> matches at the end of a word, like Tcl's \M.


---

### Post by Thibaud74 on 2009-08-14
How to do with composed words ? By exemple with this :
```
# echo "i'm dark-haired, not dark"   | sed -e "s/\<dark\>/brown/gI"
i'm brown-haired, not brown
```

So, I want just replace dark, not dark-haired !

---

### Post by geirha on 2009-08-14
sed considers a word as [A-Za-z0-9_]*, so the '-' is a non-word character in that sense, and so the transition to the '-' is treated as a word boundary. You'll need to handle those cases spcecially.
```

$ echo "i'm dark-haired, not dark" | sed "s/\<dark\>\([^-]\|$\)/brown\1/gI"
i'm dark-haired, not brown

# or with ERE, to lose some escapes
$ echo "i'm dark-haired, not dark" | sed -r "s/\<dark\>([^-]|$)/brown\1/gI"
i'm dark-haired, not brown

```

---

### Post by Thibaud74 on 2009-08-15
I'm not sur to understand details of the script.
By example, this don't work :
```
$ echo "My hair is blue-red or red-blue, not red" | sed "s/\<red\>\([^-]\|$\)/green\1/gI"
My hair is blue-green or red-blue, not green

```

Then I tried to copy caracters at the end of red :
```
$ echo "My hair is blue-red or red-blue,not red" | sed "s/\([^-]\|$\)\<red\>\([^-]\|$\)/green\1/gI"
My hair is blue-red or red-blue,notgreen
```

So, why the space is erased ? Do you think that I can have other problems with a strange text, with other characters than "-" or " " ?

---

### Post by geirha on 2009-08-15
Ah right, forgot to take the start of the word into account
```
 
$ echo "My hair is blue-red or red-blue, not red" | sed "s/\([^-]\|^\)\<red\>\([^-]\|$\)/\1green\2/gI"
My hair is blue-red or red-blue, not green

```

\( \) starts a group. Everything matched inside that group, can be put in the replacement with \number, with \1 being the first group, \2 the second etc.

[^-]\|$  this says, either a character that is not - ([^-]), or (\|), end of line ($).

With the one before the word, you want to match start of line (^) instead of end of line.

---

### Post by Thibaud74 on 2009-08-15
That doesn't work with a repetition :
```
$ echo "red red" | sed "s/\([^-]\|^\)\<red\>\([^-]\|$\)/\1blue\2/gI"
blue red
```
What a challenge ! ;-)

---

### Post by geirha on 2009-08-15
Bah. Because the first substitution matches the space after the first red, and so the second substitution won't get a match on the character before the second red. :(

I don't see any obvious way around that at the moment :/

---

### Post by unutbu on 2009-08-15
Does this work for you?

[PHP]
#!/usr/bin/env python
import sys
import re
from_str,to_str=sys.argv[1:3]
contents=sys.stdin.read()
pat_str=r'(?<!-)\b%s\b(?=[^-]|\Z)'%from_str
pat=re.compile(pat_str,re.UNICODE|re.IGNORECASE)
result=pat.sub(to_str,contents)
print(result)
[/PHP]

Save this as ~/bin/test.py

Make it executable:```

chmod +x ~/bin/test.py

```
Run it like this:
```

% echo "My hair is blue-red or red-blue, not red" | test.py red blue 
My hair is blue-red or red-blue, not blue

% echo "i'm dark-haired, not dark" | test.py dark brown
i'm dark-haired, not brown

% echo "red red" | test.py red blue
blue blue
```

---

### Post by ghostdog74 on 2009-08-15
```

#  echo "My hair is blue-red or red-blue, not red" | awk '{for(i=1;i<=NF;i++){if($i~/^red$/){$i="blue"}}}1'
My hair is blue-red or red-blue, not blue


```
NB: will not work if "red" is valid in strings like 
```

"My hair is blue-red or red-blue, not red,red blue" 

```
where both "red" separated by legit punctuation.

---

### Post by vamped on 2009-08-15
works from this:

```
echo "the thermostat works" | perl -pe 's/(^|[^-])\bthe\b(?=$|[^-])/$1a/ig'
```
a thermostat works

to this:
```
echo "Red, my hair is blue-red or red-blue, redo not red red" | \
      perl -pe 's/(^|[^-])\bred\b(?=$|[^-])/$1green/ig'
```

green, my hair is blue-red or red-blue, redo not green green

In english: find ('beginning of line' OR 'not a -', 'beginning of word' red 'end of word') then peak for (end of line OR 'not a -')

One of the challenges people were having was when the word was repeated, ie "red red". That's because the RE read "red" then another character 'no a -', then /g tells it to continue from the current position. It reads 'not a -' which is the 'r' in the next red, leaving only "ed" for it to match.

If you want variables, you can add those too.
```
echo "the thermostat works" | \
      perl -pe '$this="the"; $that="a"; s/(^|[^-])\b$this\b(?=$|[^-])/$1$that/ig'
```
a thermostat works

---

### Post by Thibaud74 on 2009-08-17
Here I answer to unutbu (python script) and vamped (per script).

The python script doesn't work with an UTF8 encode. I work on french texts, and this doesn't work for me :
```
$ echo "I speak français" | erg-replace.py "français" "" "french"
I speak
```

The perl script works with the expression above, but how can I integrate into bash encapsulated variables ? I'd try anything like that :
```
echo "I speak français" | origin=français ; target=french \
 perl -pe 's/(^|[^-])\b$origin\b(?=$|[^-])/$1$target/ig'
```

I ask me if it would be easy to rewrite my entire bash script to python or perl (about 850 lignes of bash and sed), but probably it would be for later.

---

### Post by unutbu on 2009-08-17
Thibaud74, you put too many quotation marks here:
```

echo "I speak français" | erg-replace.py "français" "" "french"

```
Try:
```

echo "I speak français" | erg-replace.py "français" "french"

```
The erg-replace.py script expects 2 arguments. More arguments than that are ignored. So in the first command above,  "français" was getting replaced by "" and "french" was being ignored.

---

### Post by Thibaud74 on 2009-08-17
Exact, well seen...
How is strange... Actually, probably it was just a copy error because I tried first with this other example :
```

echo "I like ça" | erg-replace.py "ça" "this"
I like ça
```

Why this doesn't work ?!

After tests, your script seems work with words like [a-z][çéè...][a-z],
 but not with [a-z][çéè...] or [çéè...][a-z] !

---

### Post by vamped on 2009-08-17
> **Thibaud74 said:**
> The perl script works with the expression above, but how can I integrate into bash encapsulated variables ?

I ask me if it would be easy to rewrite my entire bash script to python or perl (about 850 lignes of bash and sed), but probably it would be for later.

I doubt you should need to rewrite your entire script. It should be easy to compliment bash with whatever tools work best, ie: sed, perl ...

I don't know if this is the correct/best way to do this, but it worked for me:

```
export origin=français; export target=french;  echo "I speak français" | \
perl -pe 's/(^|[^-])\b$ENV{"origin"}\b(?=$|[^-])/$1$ENV{"target"}/ig'
I speak french
```

---

### Post by unutbu on 2009-08-17
Thibaud74, I modified the python script here:
[http://ubuntuforums.org/showpost.php?p=7791724&postcount=19](http://ubuntuforums.org/showpost.php?p=7791724&postcount=19)
so that it recognizes unicode word boundaries now.

I agree with vamped that you don't need to rewrite your entire script.
If you choose to use the python script, you can call it inside your bash script 
just like any other program:
[PHP]
#!/bin/bash
line='I like ça'
result=$(erg-replace.py "ça" "this" <<<"$line")
echo "$result"
[/PHP]

---

### Post by Thibaud74 on 2009-08-17
OK, I'm testing your scripts. Is it possible to replace words and ignore the case ?

---

### Post by unutbu on 2009-08-17
The script has been modified to ignore case.

Also, would you prefer to use the script with 3 parameters like this:

[PHP]#!/bin/bash
line='I like ça'
result=$(erg-replace.py "$line" "ça" "this")
echo "$result"  
[/PHP]
If so, that could be easily arranged...

---

### Post by Thibaud74 on 2009-08-17
I tried the python script, but I've this problem with french expressions :

```
$ echo "ça a l'air d'aller" | erg-replace.py "a" "a pas"
ça pas a pas l'air d'aller
```

It had to get : "ça a pas l'air d'aller", but "ça" is considered like two words, so the letter "a" is replace too.

It's not necessary using three parameters, because I use a text not a line. So I write :
```
cat new | erg-replace.py "$origin" "$target" > new2
cat new2 > new
```

Sensitive case seems OK.

---

### Post by Thibaud74 on 2009-08-17
With last perl scirpt, I have exactly the same problem !
```
$ export origin="a"; export target="a pas" ; \
   echo "ça a l'air d'aller" | \
   perl -pe 's/(^|[^-])\b$ENV{"origin"}\b(?=$|[^-])/$1$ENV{"target"}/ig'
ça pas a pas l'air d'aller
```

---

### Post by unutbu on 2009-08-17
Are you willing to install python3? 
LOL, the python script works properly with python3...

---

### Post by Thibaud74 on 2009-08-17
OK, I installed it and create a link, but I have this error :
```
$ python --version
Python 3.0.1+
$ export origin="a"; export target="a pas" ;    echo "ça a l'air d'aller"| erg-replace.py "$origin" "$target"
  File "/home/hulin/bin/erg-replace.py", line 10
    print result
               ^
SyntaxError: invalid syntax
```

---

### Post by unutbu on 2009-08-17
Fixed here: [http://ubuntuforums.org/showpost.php?p=7791724&postcount=19](http://ubuntuforums.org/showpost.php?p=7791724&postcount=19)

---

### Post by Thibaud74 on 2009-08-17
Mh, it looks like it works ! I will continue to test, but I think that's good now !

---

### Post by vamped on 2009-08-17
Good job unutbu!

Yes I think that making it the script a program is the way to go, to call it more easily from a bash script. For completeness I've included a perl script version that works the same as the python one.

```
#!/usr/bin/perl
#
use encoding "utf-8";

$from=shift;
$to=shift;

while (<>) {
  s/(^|[^-])\b$from\b(?=$|[^-])/$1$to/ig;
  print;
}
```

# from="a"; to="a pas"; echo "ça a l'air d'aller" | replace.ps "$from" "$to"
ça a pas l'air d'aller

---

### Post by Thibaud74 on 2009-08-18
That works perfectly now, for all the both scripts ! Thanks a lot, good job !

Great regards,
Thibaud.

---


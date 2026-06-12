---
title: "Add character string in filename after fifth character"
date: 2012-08-26
forum: Programming Talk
---

### Post by jamesisin on 2012-08-26
I have a nice little script I have written for replacing strings in filenames.

[http://jamesisin.com/a_high-tech_blech/index.php/2011/04/malleable-renaming-script/](http://jamesisin.com/a_high-tech_blech/index.php/2011/04/malleable-renaming-script/)

It works great any time I can use a regex to identify a string to be replaced.  Problem I'm facing now is that I have a bunch of files where the two (variable) bits I need to keep are sandwiched together with no intervening string (not even a single character).

So, I know that I have two numbers, a dot, and another two numbers (totaling five characters) at the beginning of each filename before I want my new string placed (such as 01.05Other Stuff Needed.flac).

I have seen sed used to do similar within text files, but I'm not really familiar with sed.

Suggestions and samples welcome.  Thanks.

---

### Post by papibe on 2012-08-26
Hi jamesisin.

Since you are using parameter substitution already, you may extract sub strings using **position** and **length**.

For instance:
```
$ var="01.05Other Stuff Needed.flac"

$ echo ${var:0:2}
01

$ echo ${var:3:2}
05

```
Hope it helps.
Regards.

---

### Post by jamesisin on 2012-08-26
I understand what your code does (I think).  It allows me to take the filename variable I'm already using and call-out whatever happens to exist in some position for a number of characters to the right.

So something built like this maybe?

do
five=${filename:0:5}
mv "$filename" "${filename/$five/$five – }"
echo $filename changed
done

I'm sure my syntax on this isn't perfect (probably need some quotes at least in that $five variable construction), but is this in the ballpark?

---

### Post by Vaphell on 2012-08-26
you can put the code of $five directly in destination part if you want. $var, ${var} and ${var<some option>} don't make bash a difference when you embed these.
```
mv "$filename" "${filename/${filename:0:5}/${filename:0:5} &#8211; }"
```

in some cases you can utilize #, ##, % and %% options of parameter expansion (trimming).
substringing with position and length is somewhat rigid (you need to know numbers in advance) while trimming can match patterns.
```
$ var="01.05Other Stuff Needed.flac"
$ echo ${var##*[0-9]}  # trim the longest <anything>[digit] from the left
Other Stuff Needed.flac
$ echo ${var/${var##*[0-9]}/ - ${var##*[0-9]}}
01.05 - Other Stuff Needed.flac
```

but seriously, learn sed and use rename command for such things. Bash expansions are fine, but they are not the silver bullet.
with rename you'd be able to do something like this:
```
rename 's/([COLOR="Green"][0-9.]+[/COLOR])([COLOR="Blue"].*[/COLOR])/[COLOR="Green"]$1[/COLOR] - [COLOR="Blue"]$2[/COLOR]/'
```
sed has the same syntax, but uses \ instead of $ to call selection groups.

---

### Post by ofnuts on 2012-08-26
> **jamesisin said:**
> I have a nice little script I have written for replacing strings in filenames.

[http://jamesisin.com/a_high-tech_blech/index.php/2011/04/malleable-renaming-script/](http://jamesisin.com/a_high-tech_blech/index.php/2011/04/malleable-renaming-script/)

It works great any time I can use a regex to identify a string to be replaced.  Problem I'm facing now is that I have a bunch of files where the two (variable) bits I need to keep are sandwiched together with no intervening string (not even a single character).

So, I know that I have two numbers, a dot, and another two numbers (totaling five characters) at the beginning of each filename before I want my new string placed (such as 01.05Other Stuff Needed.flac).

I have seen sed used to do similar within text files, but I'm not really familiar with sed.

Suggestions and samples welcome.  Thanks.
So, you should really look at the 'rename' command...

This said, it is easy to skip 5 characters in a regexp:

```
s/^(.{5})(.*)$/\1your_string\2/
```

So using the rename command (perl-ish syntax):

```
rename -n 's/^(.{5})(.*)$/$1your_string$2/' *.flac
```

"-n" is for testing what would happen, remove to make effective changes.

---

### Post by jamesisin on 2012-08-26
Excellent stuff.  Thanks a bunch.

I used the rename bit which ofnuts suggested because it was the fastest for me to deploy for this renaming, but each suggestion is worth exploring and I hope to make some improvements to my scripts based on all these suggestions.

Thanks to each of you.

Vaphell - Probably I'll use the single line condensation (or some variation thereof) in this particular script in the future.  Unless I switch to rename (which opens different questions).

One thing though, I've not had much use getting #'s and %'s to work as expected.  I feel like using them in conjunction with a wildcard (like *) doesn't tend to obey my definition of "shortest".  Any reading suggestions?

---

### Post by Vaphell on 2012-08-26
>  I feel like using them in conjunction with a wildcard (like *) doesn't tend to obey my definition of "shortest". Any reading suggestions?
any examples of that?
```
$ x=a.b.c.d.e.f.g
$ echo ${x#*.} / ${x##*.} / ${x%.*} / ${x%%.*} 
b.c.d.e.f.g / g / a.b.c.d.e.f / a
```

---

### Post by jamesisin on 2012-10-27
Yes.

```
for filename in *
   do
   mv "$filename" "${filename/#* - /}"
   echo $filename changed
done

exit
```

(This is essentially taken directly from my script linked above.)

I took a folder with three folders in it:

```
1980-81 - On To Victory - Go For The Throat
1994 - Hot 'N' Nasty - The Anthology
2000 - Natural Born Bugie - The Immediate Anthology

```

If the pound (#) were saying shortest string from the left, only the years and their following dashes would be gone.  Instead I get this:

```
Go For The Throat
The Anthology
The Immediate Anthology

```

Not shortest.

Using ##:

```
for filename in *
   do
   mv "$filename" "${filename/##* - /}"
   echo $filename changed
done

exit
```

Yields errors:

```
mv: cannot move `Go For The Throat' to a subdirectory of itself, `Go For The Throat/Go For The Throat'
Go For The Throat changed
mv: cannot move `The Anthology' to a subdirectory of itself, `The Anthology/The Anthology'
The Anthology changed
mv: cannot move `The Immediate Anthology' to a subdirectory of itself, `The Immediate Anthology/The Immediate Anthology'
The Immediate Anthology changed

```

(Nothing is actually changed in this example.  The output includes my overly simple echo statement.)

---

### Post by Vaphell on 2012-10-27
```
$ name="1980-81 - On To Victory - Go For The Throat"
$ echo [COLOR="Blue"]${name/**#*** - /}[/COLOR]
Go For The Throat
$ echo [COLOR="Blue"]${name/**#**#* - /}[/COLOR]
1980-81 - On To Victory - Go For The Throat
$ echo [COLOR="Green"]${name#* - }[/COLOR]
On To Victory - Go For The Throat
```

there is a difference between ${v/#a/} expansion and ${v#a}
[http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)

> [COLOR="Blue"]${parameter/pattern/string}[/COLOR]

    The pattern is expanded to produce a pattern just as in filename expansion. Parameter is expanded and the longest match of pattern against its value is replaced with string. If pattern begins with &#8216;/&#8217;, all matches of pattern are replaced with string. Normally only the first match is replaced. **If pattern begins with &#8216;#&#8217;, it must match at the beginning of the expanded value of parameter.** If pattern begins with &#8216;%&#8217;, it must match at the end of the expanded value of parameter. If string is null, matches of pattern are deleted and the / following pattern may be omitted. If parameter is &#8216;@&#8217; or &#8216;*&#8217;, the substitution operation is applied to each positional parameter in turn, and the expansion is the resultant list. If parameter is an array variable subscripted with &#8216;@&#8217; or &#8216;*&#8217;, the substitution operation is applied to each member of the array in turn, and the expansion is the resultant list.

> [COLOR="Green"]${parameter#word}[/COLOR]
${parameter##word}

    The word is expanded to produce a pattern just as in filename expansion (see Filename Expansion). If the pattern **matches the beginning** of the expanded value of parameter, then **the result of the expansion is the expanded value of parameter with the shortest matching pattern (the &#8216;#&#8217; case)** or the longest matching pattern (the &#8216;##&#8217; case)** deleted.** If parameter is &#8216;@&#8217; or &#8216;*&#8217;, the pattern removal operation is applied to each positional parameter in turn, and the expansion is the resultant list. If parameter is an array variable subscripted with &#8216;@&#8217; or &#8216;*&#8217;, the pattern removal operation is applied to each member of the array in turn, and the expansion is the resultant list.

first example says:  replace '* - ' with nothing, but must match at the beginning (/#). Matching is greedy so it eats as much as it can
second one says: replace '#* - ' in a similar manner, but this fails due to expected # as the first char
3rd one: remove shortest '* - ' on the left side

---

### Post by jamesisin on 2012-11-14
Do you mean to suggest then that # will only work when performing substitution to null?

If not, how would I transform ${name/#* - /dog.} into ${name#* - /dog.} and make it work?  (That is to say how do I transform the syntax for substitution from /a/b to /#*stuff/notnull ?)

---

### Post by Vaphell on 2012-11-14
no, i don't mean that

your code
```
for filename in *
   do
   mv "$filename" "${filename[COLOR="Blue"]/#[/COLOR][COLOR="Red"]#* - [/COLOR][COLOR="Blue"]/[/COLOR]}"
   echo $filename changed
done
```
your pattern started with # and your string would not, so nothing happened.
```
$ name1='[COLOR="DarkGreen"]abc - def.ghi[/COLOR]'; name2='[COLOR="Blue"][COLOR="Red"]#[/COLOR]abc - def.ghi[/COLOR]'
[COLOR="DarkGreen"]$ echo ${name1/#[COLOR="Red"]#[/COLOR]* - /dog.} / ${name1/#* - /dog.}
abc - def.ghi / dog.def.ghi[/COLOR]
[COLOR="Blue"]$ echo ${name2/#[COLOR="Red"]#[/COLOR]* - /dog.} / ${name2/#* - /dog.}
dog.def.ghi / dog.def.ghi[/COLOR]
```


Alternatively you can do this:
```
$ name='abc - def - ghi.jkl'
$ echo [COLOR="DarkGreen"]**dog.**${name##* - }[/COLOR] / [COLOR="Blue"]**dog.**${name#* - }[/COLOR]
[COLOR="DarkGreen"]**dog.**ghi.jkl[/COLOR] / [COLOR="Blue"]**dog.**def - ghi.jkl[/COLOR]
```
this approach is better because replace // doesn't deal with shortest/longest at all. there is only 1 effect to be achieved. Trimming and gluing with the 'replacement' gives you 2.

---


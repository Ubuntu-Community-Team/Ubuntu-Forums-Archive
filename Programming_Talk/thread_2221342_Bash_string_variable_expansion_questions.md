---
title: "Bash string variable expansion questions"
date: 2014-05-01
forum: Programming Talk
---

### Post by Ralph L on 2014-05-01
I am trying to use Nautilus Actions to create an alternate copy function that includes Access Control Lists.  I got Nautilus Actions working fine, but I am having problems with my bash script.  Here is a contrived example of the problem I am having.

```
ralph@Lat1:~$ a1=$'this\nis\na\nte st'                                           #Create string with newlines in it.
ralph@Lat1:~$ IFS=$'\n'                                                          #Set IFS to find newlines during expansion
ralph@Lat1:~$ a2={$a1}                                                         #Expand a1 and set string a2 to the results of the expansion of a1
ralph@Lat1:~$ echo -n {$a1} |xxd
0000000: 7b74 6869 7320 6973 2061 2074 6520 7374  {this is a te st   #View the results of expansion of a1.  Note that the newlines (0a) have
0000010: 7d                                       }                  #been changed to spaces (20).
ralph@Lat1:~$ echo -n "$a2" |xxd                                     #a2 was set to the expansion of a1.  However, when I view it, 
0000000: 7b74 6869 730a 6973 0a61 0a74 6520 7374  {this.is.a.te st  #it shows the contents of a1--not the expansion of a1.
0000010: 7d                                                         # Double quotes are used to prevent any additional expansion of a2.
```

The only way to get correct a1 expansion seems to be to include the a1 expansion directly in the "echo" statement.  One cannot put the a1 expansion into another variable as I tried to do with the statement a2={$a1}.  Apparently the $a1 expansion in this statement didn't work.  Can somebody explain this?

Also, note that the only character in IFS is \n (newline).  According to the manuals I have read, unquoted expansion ($a1) should replace whitespace characters with the first character of IFS, which is newline.  Instead the newline whitespace was replaced by spaces.  What am I missing?

Any help is appreciated.

Note:  Please excuse the "screwed up" comments in the code above.  They were added after it was run, and the web site squeezed out all the spaces that were used for formating.  If someone can tell me how to avoid having the spaces squeezed out, I will reformat it to make it more readable.

---

### Post by Vaphell on 2014-05-01
[noparse]```

```[/noparse] tags preserve formatting and use monospace font which makes code and outputs readable.

either way i am not seeing what exactly you want to achieve here, but my gut feeling tells me you are doing it wrong. Using word splitting for anything is almost universally a bad idea.
You would be better off explaining what you expect your nautilus actions script to do. Some code would be nice.

---

### Post by Ralph L on 2014-05-01
At this time I am  only trying to understand bash string variable expansion.  All I did in this example is show that I could not store the results of a $string expansion in a variable.  The resulting variable contains the original string, not the expanded string as I wanted.  Is this documented in the bash manual someplace?

What led me to this problem was expanding the results of the clipboard for my Nautilus Action bash routine (paste with ACL).  The contents of the clipboard (after selecting files to copy) is (I think) a single word list of folders/files (with their complete path) separated by newlines.  Some of the folders/files contain spaces in their names, which must be handled correctly or the spaces are compressed out.  I don't even understand what is a single word list vs a multi-word list, how expansion can seemingly change one to the other, and what are the delimiters for a list of folders/files that have spaces in their name.  So I am seeking a basic understanding of expansion of string variables.

---

### Post by Vaphell on 2014-05-01
it's more than just expansion. If you are trying to use IFS you are dealing with word splitting. Either way what transformation are you trying to achieve?
Give an example like this is input string: ...., i need output string like this: ....

---

### Post by Vaphell on 2014-05-02
no example yet, so let me explain a bit.
In my opinion you should never leave your variables unquoted and depend on a globally scoped IFS for anything. There are other, kosher ways to transform text in bash and i consider these IFS/word splitting solutions nothing more than dirty hacks.

if you intentionally do something like
```
x=$'string with some whitespace including \t and \n in it'
echo $x
```
with no "", you are doing it wrong. That's it. That's where literally a half of bugs plaguing shell scripts comes from. Always quote variables is a rule of thumb you should stick to.

and if you are doing something like y=$x - there is no word splitting at play in such assignments so the value is passed verbatim.

---

### Post by SeijiSensei on 2014-05-02
I thought I'd run Vaphell's suggestion with and without quotes to see how they differ:
```

x=$'string with some whitespace including \t and \n in it'
echo $x
string with some whitespace including and in it
echo "$x"
string with some whitespace including    and 
 in it

```
Could the problem be a syntactical error?  
```

ralph@Lat1:~$ a2={$a1}  #Expand a1 and set string a2 to the results of the expansion of a1

```
Shouldn't the $ be outside the braces, like this "${a1}"?

---

### Post by Vaphell on 2014-05-02
i assume that's what OP meant to do, but that's rather immaterial  if i understand OP's train of thought correctly (in his typo {} get appended to the ends of the value but the input variable expands verbatim which is not what he expected).
I think OP wanted to break the content apart using IFS/word splitting and assemble it back using redefined IFS but in assignments written as y=so${m}e${thing} word splitting doesn't take place so that approach is dead in the water.

Imo word splitting is a bug prone, legacy feature with too many obscure implicit effects, caveats and generally should be avoided. I'd even risk saying that bash would be better if implicit word splitting was disabled entirely. For every script that uses it "correctly", there are dozens upon dozens just waiting to blow up on a whitespace ridden input, eg real life file names. Bash has many features that remove the need for these legacy hacks.

---

### Post by Ralph L on 2014-05-02
Thank you guys for putting up with me and responding!!  I have been traveling and unable to attend to this.

SeijiSensei, you are indeed correct that I should have made the statement read as below.  It was a typo on my part and I carelessly didn't see that it expanded differently than I wanted.
```
ralph@Lat1:~$ a2=${a1}  #Expand a1 and set string a2 to the results of the expansion of a1
```
However, using a2=${a1} still didn't achieve the results that I expected--namely that a2 would contain the expanded (and word split) string of a1.

Vaphell,
> I think OP wanted to break the content apart using IFS/word splitting and assemble it back using redefined IFS but in assignments written as y=so${m}e${thing} word splitting doesn't take place so that approach is dead in the water.  

Now you are answering my question!!  According to the bash manual I have been reading, it seems to me that the word splitting would have occurred.  Can you point me to a place in a bash manual that says that it won't (and explains the rationale behind not having the word splitting take place in this kind of an assignment a2=${a1}?  
That is all I am asking:  Where is it discussed in the bash manual, and what is the rationale.  

Then in the next script I write I won't have to randomly test all alternatives I can think of, before I find a solution.  I will understand how bash works!!

PS. I don't really understand exactly what a is a word, or a word split.  Is a word just a string of characters with whitespace at either end?  Is a word split just dividing that string and putting a space where the division takes place.

---

### Post by SeijiSensei on 2014-05-02
[Quoting]("http://www.tldp.org/LDP/abs/html/quoting.html") matters.
```
$ a1=$'this\nis\na\nte st'

# no quotes expand special characters to whitespace
$ echo $a1
this is a te st

# double quotes expand special characters to their corresponding values
$ echo "$a1"
this
is
a
te st

# single quotes return the literal string $a1
$ echo '$a1'
$a1


```

Setting one variable equal to another returns the identical results.
```
$ a2=$a1
$ echo $a2
this is a te st

$ echo "$a2"
this
is
a
te st
```
Using $a1 or ${a1} makes no difference in these examples.  You only need to use ${var} when the variable's meaning is [ambiguous]("http://www.tldp.org/LDP/abs/html/parameter-substitution.html"), like in Vaphell's "y=so${m}e${thing}" example.

---

### Post by Vaphell on 2014-05-02
[http://mywiki.wooledge.org/WordSplitting](http://mywiki.wooledge.org/WordSplitting)

> [B]Notes
[/B]
    Word splitting is not performed on expansions inside Bash keywords such as [[ ... ]] and case.
    Word splitting is not performed on expansions in assignments. Thus, one does not need to quote anything in a command like these:

        foo=$bar

        bar=$(a command)

        logfile=$logdir/foo-$(date +%Y%m%d)

        PATH=/usr/local/bin:$PATH ./myscript 

    In either case, quoting anyway will not break anything. So if in doubt, quote!

    When using the read command, word splitting is performed on the input, but only when multiple variable names are given, or when read -a is used (to populate an array). Quoting is irrelevant here, though this behavior can be disabled by removing whitespace from IFS.

If i had to substitute a class of delimiters with some other delimiter i'd use a simple replacement and not bother with the roundabout way with word splitting


```
string=$'x\t\t\ty    z'
$ echo "${string//+([[:space:]])/$'\n'}"
x
y
z
$ echo "${string//+([[:space:]])/$'\n'}" | od -c
0000000   x  \n   y  \n   z  \n
0000006

```

---

### Post by Ralph L on 2014-05-03
Thanks again to you guys for the response.

You sent me to a very good reference with the this statement:  "Variable assignment skips word splitting (because there's no meaningful way to handle multiple words when there's only a single variable to put things into)."  That was the kind of reference for which I was looking.  It tells me that my concept of the results of word splitting was in error.  I thought the result was a Single string with a delimiter between different words, but this tells me that the result is multiple strings (I guess each string is a word) addressed separately.  Just how that is done will require more study on my part.

Now I am going to have to study the concepts of a word, multiple words, parameters, lists (For loops use lists, and I use For loops in my script to process file names), and arrays; and how elements of those structures are stored and addressed.  Bash has a lot to it, and I need to learn more just to understand the examples in the reference.  My Linux stuff is just a hobby that I work on, when I get a chance.

Again thank you for putting up with me.

---

### Post by Vaphell on 2014-05-03
like i said before, you should try to forget word splitting is a thing. Just quote your variables and use arrays for multiple params/words and you are golden. Mastery of the *read *command is advised though.

```
$ array=( $'this\t\t\tis' $'some\narray' )
$ printf -- '<%s>\n' "${array[@]}"
<this			is>
<some
array>

# create array from a 1-line string (array elems defined by spaces and tabs)
$ read -a array2 <<< "this is some string"
$ printf -- '<%s>\n' "${array2[@]}"
<this>
<is>
<some>
<string>

# IFS redefined only for this read, no global change of IFS
$ IFS=: read -a array3 <<< "this:is:some:other:string"
$ printf -- '<%s>\n' "${array3[@]}"
<this>
<is>
<some>
<other>
<string>

# using printf to join array elems with arbitrary string
$ glue=':::'
$ printf -v gstr -- "%s${glue}" "${array3[@]}"; gstr=${gstr%${glue}}; echo "$gstr" 
this:::is:::some:::other:::string

# removed delimiter, array elems defined by spaces, tabs + newline
$ read -d '' -a array4 <<< $'yet\tanother\nstring'
$ printf -- '<%s>\n' "${array4[@]}"
<yet>
<another>
<string>

# array elems on a per-line basis (\n)
$ readarray -t array5 <<< $'guess what\none more string' 
$ printf -- '<%s>\n' "${array5[@]}"
<guess what>
<one more string>
```

and if you want to test what commands get as params, use a function like this
```
test_params() { printf -- '<%s>\n' "$@"; }
```

```
$ str=$'abc\t\t\td\nef'
$ test_params "$str"
<abc			d
ef>
$ str='abc def'
$ test_params "$str"
<abc def>
$ test_params $str
<abc>
<def>
$ test_params "$str" "${array3[@]}"
<abc def>
<this>
<is>
<some>
<other>
<string>
```

---


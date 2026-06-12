---
title: "Bash script to count occurrence of a string in multiple files"
date: 2010-09-05
forum: Programming Talk
---

### Post by saphil on 2010-09-05
I know how to count the occurrence of a word in one file.
```
grep -cw word1 file.txt
```I tried running it to check the occurrence in multiple files like this
```
grep -cw word1 *.txt
```and that tells me neatly how many of the word are in each file.
I am trying to come up with how to get a quantity of the word in all files
would it be something like this???
```
grep -w word1 *.txt >> file | sort | uniq -c; cat file
```

---

### Post by saphil on 2010-09-05
```
wolf@telcontar:~/test/SET 1$ clear; grep -w word1 *.txt > gfile.dat | sort | uniq -c; 
      grep -w word2 *.txt >> gfile.dat | sort | uniq -c; cat gfile.dat
```
gives me a file with each line that contains each word carefully listed, but no 
```

word1:377
word2:122

```

---

### Post by saphil on 2010-09-05
```
wolf@telcontar:~/test/SET 1$ clear; grep -w word1 *.txt > gfile.dat | 
      sort | uniq -c; grep -w word2 *.txt >> gfile.dat | sort | uniq -c; 
      w1=`grep -wc word1 gfile.dat`; w2=`grep -wc word2 gfile.dat`; 
      echo "word1 appears $w1 times"; echo "word2 appears $w2 times"
      # this is one code line.  I broke it for ease of reading

```gets me 
```
word1 appears 601 times
word2 appears 178 times
```I can see how I can put the mess at the end of gfile.dat for a neat output, but it is such an ugly code line...

---

### Post by geirha on 2010-09-05
```
awk '{for (i=1;i<=NF;i++) if ($i=="word") n++} END{print n}' *.txt
```

---

### Post by ghostdog74 on 2010-09-05
grep -c  don't count words for you. It counts number of lines where the word is.

```

grep -o word1 file | wc -l
grep -o word2 file | wc -l

```

---

### Post by saphil on 2010-09-05
> **ghostdog74 said:**
> grep -c  don't count words for you. It counts number of lines where the word is.

```

grep -o word1 file | wc -l
grep -o word2 file | wc -l

```
I got lucky that there weren't occasions in these files where a word appears more than once per line.

---

### Post by Some Penguin on 2010-09-05
Does the sentence

"This sentence suggests that regular expressions can be useful, as there are many seemingly basic searches which you can't solve nearly as neatly with simple exact-match searches."

contain the word "press"?  How about "This" or "can"?

---

### Post by saphil on 2010-09-06
> **geirha said:**
> ```
awk '{for (i=1;i<=NF;i++) if ($i=="word") n++} END{print n}' *.txt
```

When I run this I get an empty line and the command prompt back.  Would I need to replace the NF in the for loop with an actual integer?

---

### Post by saphil on 2010-09-06
> **Some Penguin said:**
> Does the sentence

"This sentence suggests that regular expressions can be useful, as there are many seemingly basic searches which you can't solve nearly as neatly with simple exact-match searches."

contain the word "press"?  How about "This" or "can"?

I don't get where you are going with this.  Yes of course it does.

---

### Post by saphil on 2010-09-06
why not ```
grep word1 file | wc -w
```?
I can see they get the same result from a grep output.

---

### Post by geirha on 2010-09-06
> **saphil said:**
> When I run this I get an empty line and the command prompt back.  Would I need to replace the NF in the for loop with an actual integer?

That means there's no matches. You can make it print 0, by either setting n=0 in a BEGIN action, or by using it in arithmetic context by adding 0.

```
$ echo "foo-bar [COLOR="Blue"]bar[/COLOR] baz" | awk '{for (i=1;i<=NF;i++) if ($i=="bar") n++} END {print n+0}'
1
$ echo "foo [COLOR="blue"]bar bar[/COLOR] baz" | awk '{for (i=1;i<=NF;i++) if ($i=="bar") n++} END {print n+0}'
2

```

On each line, it checks each field (separated by whitespace by default). If a field exactly match "bar" (in the example above), n is incremented.

---

### Post by DemonBob on 2010-09-06
Assuming all the files you want to look through are in one directory. 


```
ls -a | xargs grep word1 | wc -w
```

---

### Post by saphil on 2010-09-06
> **DemonBob said:**
> Assuming all the files you want to look through are in one directory. 


```
ls -a | xargs grep word1 | wc -w
```

What does xargs do for us here?
```
wolf@telcontar:~/test/SET 1$ ls -a | xargs grep Halton | wc -w
grep: READ: No such file or directory
grep: THIS.pdf: No such file or directory
729
wolf@telcontar:~/test/SET 1$ 

```
What is it telling me here?  I am trying to find the search term in the text of a bunch of files.  Won't this just give me a search of the titles?

---

### Post by saphil on 2010-09-06
> **geirha said:**
> That means there's no matches. You can make it print 0, by either setting n=0 in a BEGIN action, or by using it in arithmetic context by adding 0.

```
$ echo "foo-bar [COLOR=Blue]bar[/COLOR] baz" | awk '{for (i=1;i<=NF;i++) if ($i=="bar") n++} END {print n+0}'
1
$ echo "foo [COLOR=blue]bar bar[/COLOR] baz" | awk '{for (i=1;i<=NF;i++) if ($i=="bar") n++} END {print n+0}'
2

```On each line, it checks each field (separated by whitespace by default). If a field exactly match "bar" (in the example above), n is incremented.

Ah, that might be why it failed.  The search terms are parts of larger strings URIs like this:
[http://pagead2.googlesyndication.com/pagead/show_ads.js]("http://ubuntuforums.org/view-source:http://pagead2.googlesyndication.com/pagead/show_ads.js") where I am looking for "show_ads.js"
or more often the string I am looking for is in the middle of an URI like "pagead2" in this example.
This is not a super example since I am working with affiliate links and I don't want to come off as trying to obliquely sell anything here.
I will try looking for a fruitful term that has a few instances across the files.  My own name should show up 168 times in this one file.  

```
wolf@telcontar:~/test/SET 1$ cat gfile.dat | awk '{for (i=1;i<=NF;i++) if ($i=="Halton") n++} END {print n+0}'
1
wolf@telcontar:~/test/SET 1$ 
```

Here is a piece of the data pattern:

```
0060file1.txt:Wolf Halton
0060file1.txt:Wolf Halton
0001file2.txt:Wolf Halton
0001file2.txt:Wolf Halton
```

Where did I mess it up?  ;)

---

### Post by DemonBob on 2010-09-06
> **saphil said:**
> What does xargs do for us here?
```
wolf@telcontar:~/test/SET 1$ ls -a | xargs grep Halton | wc -w
grep: READ: No such file or directory
grep: THIS.pdf: No such file or directory
729
wolf@telcontar:~/test/SET 1$ 

```
What is it telling me here?  I am trying to find the search term in the text of a bunch of files.  Won't this just give me a search of the titles?


No, xargs pass multiple arguments to a command. In this case each line from the output of ls -a is an argument in xargs. Lets say you have three files when running ls -a.


```
text1.txt
text2.txt
text3.txt
```

passing xargs to grep is equivalent to doing this.

```
grep word1 text1.txt
grep word1 text2.txt
grep word1 text3.txt
```

Bascially it's running a loop. 

try the command with out the wc -w. 

```
ls -a | xargs grep Halton
```

you should see it output every line with Halton in it.

---

### Post by ghostdog74 on 2010-09-06
> **saphil said:**
> why not ```
grep word1 file | wc -w
```?
I can see they get the same result from a grep output.


```

$ more file
word2
word1
word3
word1word1

$ grep word1 file | wc -w
2

$ grep -o word1 file | wc -l
3


```

---

### Post by ghostdog74 on 2010-09-06
> **DemonBob said:**
> Assuming all the files you want to look through are in one directory. 


```
ls -a | xargs grep word1 | wc -w
```

why ls and xargs?
```
 grep -h word1 * 
```

---

### Post by Some Penguin on 2010-09-06
> **saphil said:**
> I don't get where you are going with this.  Yes of course it does.

The definition of 'word' and contains.  A search index that attempts to index *words* should not answer 'yes' to the question of whether that sentence contains 'press', for instance.  If you're going to use grep, you should at least use regular expressions to cover word boundaries and case sensitivity (where appropriate, which isn't always!).  Otherwise, you fail.  *shrug*

---

### Post by saphil on 2010-09-06
> **ghostdog74 said:**
> ```

$ more file
word2
word1
word3
word1word1

$ grep word1 file | wc -w
2

$ grep -o word1 file | wc -l
3


```

That is interesting behaviour, almost seems backward.  Thanks.

---

### Post by saphil on 2010-09-06
> **DemonBob said:**
> No, xargs pass multiple arguments to a command. In this case each line from the output of ls -a is an argument in xargs. Lets say you have three files when running ls -a.


```
text1.txt
text2.txt
text3.txt
```passing xargs to grep is equivalent to doing this.

```
grep word1 text1.txt
grep word1 text2.txt
grep word1 text3.txt
```Bascially it's running a loop. 

try the command with out the wc -w. 

```
ls -a | xargs grep Halton
```you should see it output every line with Halton in it.

I tried it with the more complicated embedded string 'arrowstar7'

```

ls -a *.txt | xargs grep arrowstar7 | wc -w
601

```

...and it came out with a good and quick answer.  Interesting to know about xargs.  Straight ls -a got the file where I had saved the grep output before, and that exactly doubled the number.

---

### Post by saphil on 2010-09-06
> **Some Penguin said:**
> The definition of 'word' and contains.  A search index that attempts to index *words* should not answer 'yes' to the question of whether that sentence contains 'press', for instance.  If you're going to use grep, you should at least use regular expressions to cover word boundaries and case sensitivity (where appropriate, which isn't always!).  Otherwise, you fail.  *shrug*

Now I get it. So to make sure you had a specific word would that be 

```
wolf@telcontar:~/test/SET 1$ cat regex.dat
cat puppy
dog kitten
fox otter
whale wolf
wallaby cotton
falcon cranberry
ton berry
ten lab
ran ox

wolf@telcontar:~/test/SET 1$ grep -o 'ran' regex.dat 
ran #in cranberry
ran
wolf@telcontar:~/test/SET 1$ grep -o '\<ran' regex.dat 
ran
```

I played with the regular expressions a little before I put this in here.  The specifics of regexp are not entirely foreign, but I could be a whole lot better with them.

---

### Post by Some Penguin on 2010-09-07
Along those lines, yup.

It's actually a pretty hard problem, so if you're doing this for somebody else it pays to ask them precisely what they mean; if you're doing this for a particular purpose, think carefully.  For instance, if you want to do do this for documents where there's punctuation... well, it can be made arbitrarily hard.  At some point you pretty much have to triage.

```

"Oh, bother", said Pooh, as he hid Tigger's mangled corpse.
Llamas' poor manners can't be criticized harshly enough.
Jimmy 'The Weasel' Smith wished that he had a more intimidating nickname.

```

If you know that your source material won't have such punctuation, then at least a lot of judgment calls (e.g. handling contractions and possessives -- would you want "Llamas'" or "Llamas", for instance?  "Tigger's" or "Tigger"?) go away.

Ignoring those, most regex systems have some sort of word boundary mechanics, I'd think.  Perl, for instance, lets you match ala

```

if ($string =~ /\bgiant\b/i) {...}

```

which should case-insensitively (/i) look for 'giant' surrounded by word boundaries (the definition of which is in the perldoc).

---

### Post by saphil on 2010-09-07
I made this one for myself, and had the basic thing done in 30 minutes.  Then I started thinking about making it friendlier for my associates when they are updating marketing materials to have their names on the stuff.  Scope-creep took over, and the last thing I did was an elapsed-time counter to show how much faster this app is than hand-editing all these documents.  the program currently runs in 34 seconds and 30 of those seconds are tied up in **sleep** commands.  If I add an if structure to "accept or deny" their typings, then the thing will be so fast that it will take longer for the user to type the inputs than for the thing to run.  I will take the sleeps out.

So, since 2 days ago, this went from being a personal time-saver to being a prototype for a compiled app (either c++ a java)  I foresee the C++ route being more work since I will have to run binaries for Win and Mac  GUI because the target market for this useful little thing are generally allergic to command-line.  

The biggest issue regarding regular expressions is that I cannot tell what the user-specified word1 and word2 will be.  In my test, I know whay the answers are liable to be, and within a certain set of boundaries, what they might be (probably no special characters except _ -)

Have to have a much larger set of test cases before I could come up with the pattern to match.  Right now I am using this kind of language

```

  grep -w $2 *.txt > gfile.dat | sort | uniq -c
  grep -w "$4" *.txt >> gfile.dat | sort | uniq -c
  w1=`grep -o $2 gfile.dat | wc -l`
  w2=`grep -o "$4" gfile.dat | wc -l`

```

At least the grep will search for the variable contents that the user put in.  May find some extras, if the variables have been changed to very common words.
I really like back-ticks where they work.  They make the code cleaner to look at than
```
  w1=$((grep -o $2 gfile.dat | wc -l))  
```
which might work, too, but to me is harder to read.

---

### Post by geirha on 2010-09-07
> **saphil said:**
> Ah, that might be why it failed.  The search terms are parts of larger strings URIs like this:
[http://pagead2.googlesyndication.com/pagead/show_ads.js]("http://ubuntuforums.org/view-source:http://pagead2.googlesyndication.com/pagead/show_ads.js") where I am looking for "show_ads.js"
or more often the string I am looking for is in the middle of an URI like "pagead2" in this example.
This is not a super example since I am working with affiliate links and I don't want to come off as trying to obliquely sell anything here.

If you know in advance what all the delimiters will be, you can tell awk to split on those. In that example, / would be one, possibly also " and space. 

```
awk -F '[/"[:space:]]+' '{for (i=0...
```
Another approach could be to use anything but alphanumeric characters, _ and .
```
awk -F '[^[:alnum:]_.]+' '{for...
```

> **saphil said:**
> 
I will try looking for a fruitful term that has a few instances across the files.  My own name should show up 168 times in this one file.  

```
wolf@telcontar:~/test/SET 1$ cat gfile.dat | awk '{for (i=1;i<=NF;i++) if ($i=="Halton") n++} END {print n+0}'
1
wolf@telcontar:~/test/SET 1$ 
```

Here is a piece of the data pattern:

```
0060file1.txt:Wolf Halton
0060file1.txt:Wolf Halton
0001file2.txt:Wolf Halton
0001file2.txt:Wolf Halton
```

Where did I mess it up?  ;)

If I put those four lines in a file and pass it to that awk, I get 4... What version do you have? ```
awk -W version
```
Lastly, don't do cat|awk, just pass the filename(s) as arguments to awk.
```
awk '...script...' file1 file2 file3 ...
```

---

### Post by Ole Tange on 2010-09-07
> **DemonBob said:**
> 
```
ls -a | xargs grep Halton
```

This use of xargs can lead to nasty surprises because of the separator
problem [http://en.wikipedia.org/wiki/Xargs#The_separator_problem](http://en.wikipedia.org/wiki/Xargs#The_separator_problem)

GNU Parallel [http://www.gnu.org/software/parallel/](http://www.gnu.org/software/parallel/) does not have that
problem and thus may be a better choice.

Watch the intro video for GNU Parallel to learn more:
[http://www.youtube.com/watch?v=OpaiGYxkSuQ](http://www.youtube.com/watch?v=OpaiGYxkSuQ)

---

### Post by geirha on 2010-09-07
And ls shouldn't be used in scripts; it's meant to provide human-readable output, you cannot safely parse its output in a script.

Instead of
```

ls -a | xargs grep Halton

```
you should do
```

shopt -s dotglob
grep -F Halton *

```

---

### Post by @Rednet on 2011-01-07
This is very easy, just use the following command:
  sort file.txt | uniq -c | sort -r

---


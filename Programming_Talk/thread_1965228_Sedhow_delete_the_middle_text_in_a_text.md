---
title: "Sed:how delete the middle text in a text"
date: 2012-04-25
forum: Programming Talk
---

### Post by yellowpaper on 2012-04-25
Hi Everyone !! I have a question about sed that i can't figure out.
I have this text

[COLOR=SeaGreen]blahblhablah[/COLOR]PATTERN1[COLOR=Red]blhablha
blhablhablha[/COLOR]PATTERN2[COLOR=SeaGreen]blhablha[/COLOR]

OR

[COLOR=SeaGreen]blahblhablah[/COLOR]PATTERN1[COLOR=Red]blhablha
blahblahblahblahblah[/COLOR][COLOR=Red]lahblah[/COLOR][COLOR=Red]lah[/COLOR]
[COLOR=Red]blhablhablha[/COLOR]PATTERN2[COLOR=SeaGreen]blhablah[/COLOR]

and i want , using sed , this

[COLOR=SeaGreen]blahblhablah[/COLOR]
[COLOR=SeaGreen]blhablah

[COLOR=Black]Is it possible?

THANKS!
[/COLOR][/COLOR]

---

### Post by SeijiSensei on 2012-04-25
So you want to delete the PATTERN and all the following text?  Use this:

```
sed 's/PATTERN.*//g'
```

Sed uses "regular expressions" to determine matches.  The ".*" construct in a regular expression matches any string of characters.  The "." represents a single character; the "*" is a repetition operator which matches the pattern it follows zero or more times.

See "man grep" for more details.

---

### Post by yellowpaper on 2012-04-25
Thank SeijiSensei ("Arigato Sensei") but...

If i do
$ cat examp.c 
[COLOR=SeaGreen]Here is the text text.[/COLOR][COLOR=Red]| This text 
want to be delete without delete the line
of the pattern |[/COLOR][COLOR=SeaGreen]End of text.[/COLOR]

Where the pattern is a pipe, and after that i do
$ cat examp.c | sed 's/|.*//g'

the output is

[COLOR=SeaGreen]Here is the text text.[/COLOR]
[COLOR=Red]want to be delete without delete the line[/COLOR]
[COLOR=Red]of the pattern [/COLOR]

and the text should be 

[COLOR=SeaGreen]Here is the text text.
End of text.[/COLOR]

Im newbie in bash/script  :cry:

(I was trying i guess that i get it..sed 's/|*.*|//'  maybe ...)-->>Not work fine...

---

### Post by yellowpaper on 2012-04-25
OK after play with sed for hours and hours i found something that delete the middle part of the text (another comando of sed) but i dont understand (by now) what do the command only know that works.
But for finish this thread i have another cuestion.The comand s/|*.*|//'   works always that the pattern has one character... BUT if the patter is || ( s/||*.*||//')  doesnt work and i dont know why... (like Matrix Why why why you persist Mr Anderson ).Any suggestion ???

---

### Post by Vaphell on 2012-04-25
sed is not too cool with multiline stuff. It can be forced to do that but personally i don't bother as it requires haxxorish approach, playing with internal buffers and whatnot. If it's not straightforward line-by-line, i use something else - bash script or awk or some perl oneliner found on google.

```
$ echo "blahblhablahPATTERN1blhablha
blahblahblahblahblahlahblahlah
blhablhablhaPATTERN2blhablah" | perl -00 -pe 's/PATTERN1.*PATTERN2/\n/sg'

blahblhablah
blhablah
```

this does the same as sed with the difference -00 sets record separator to null char which means that the whole text becomes one giant line (sed's separator is \n which means that record=line)

if the file is huge, reading everything at once may not be desirable. Check discussion here:
[http://stackoverflow.com/questions/5862461/problem-with-perl-multiline-matching](http://stackoverflow.com/questions/5862461/problem-with-perl-multiline-matching)

---

### Post by emiller12345 on 2012-04-25
sed appears to not work well running over new lines.  If you can get away with swapping out the newline characters with some other character temporarily, then this might work. 
```
$ echo "Here is the text text.| This text
want to be delete without delete the line
of the pattern |End of text." | tr '\n' '`' | sed 's/|[^|]*|//g' | tr '`' '\n'
```

this produces
```
Here is the text text.End of text.
```

---


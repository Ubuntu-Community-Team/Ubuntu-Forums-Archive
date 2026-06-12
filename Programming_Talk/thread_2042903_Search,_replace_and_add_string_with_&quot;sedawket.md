---
title: "Search, replace and add string with &quot;sed/awk/etc&quot;"
date: 2012-08-15
forum: Programming Talk
---

### Post by bubulescu on 2012-08-15
Hello

First, I hope this is the right place to ask, second I'm not a guru in programming, quite the contrary...

There is a problem I'm facing. I'll simplify and try to make it clear:

- There are a ton of text files in recursive folders.
- All of them have lines of text -- imagine a large poem (EOL doesn't matter).
- Many of them have certain lines containing some strings -- let's say OLD1 and OLD2.

What needs to be done is to search all the files for the occurence of OLD1 and OLD2, replace them with NEW1 and NEW2 but(!), in addition, for every OLD1 replaced by a NEW1 there has to be added a new line below the second one containing the string BLA.

If it's confusing, here's a small example:

This is the old file:
----------------
...
aaa OLD1 sss
qqq www eee
zzz OLD2 xxx
...
-----------------
This is the new file, after replacing and adding:
------------------
...
aaa NEW1 sss
qqq www eee
BLA
zzz NEW2 xxx
...
-----------------
I hope I managed to explain. I know about this approach:
```

find x -name "*.asc" -exec sed -i 's/OLD/NEW/g' {} \;
```
but it doesn't add the line. I tried to look for more help with "man sed", but I only felt a slight headache... If there's anyone that can help, please do.


Thank you in advance for any try in this matter,
Vlad

---

### Post by papibe on 2012-08-15
Hi bubulescu.

Take a look at awk (instead of sed). You would have not only the ability to replace patterns, but you would have access to the line numbers that matches the pattern, thus making it easier to add a new line.

I hope that points you in the right direction.
Regards.

---

### Post by bubulescu on 2012-08-15
Hello, papibe

Thank you for the reply. I took some time to read the man page for 'awk' but, unfortunately, that seems to me like another language to learn. For my case, in particular, I only need to run this script once; in general, I realize others may benefit form it, as well, but to start learning a language for the sole purpose of making a script that needs to be run only once, seems a bit too much for me...

In the end, if this causes too much hassle, I'll eventually dedicate a few days of patience and correct everything by hand. Just for clarification, I'm talking about all my LTspice's schematics out of which a very good deal use custom libraries which, recently, have undergone some changes; I need to replace in all the schematics the changed symbols. This involves searching for, e.g. Math\\Sum and replace with Math\\Math2r with the added line of 'SYMMATTR SpiceModel +' (I just noticed one case where the line that needs to be added may be placed right below the changed one, not necessarily second). There may be other lines to search for and replace, accordingly, as well (most likely).

So, there you have it. All I need is the skeleton upon which I will build the replacing, adding and verifying for all the variables, and for this I imagined that the line I gave, with sed, could be changed into a two or three line command. That is all.

---

### Post by steeldriver on 2012-08-15
You probably *could* do it in sed - if you must

The tricky bit imo is the insertion - you could try putting something like this in a sed script file

```
/OLD1/{$!N;s/OLD1/NEW1/;a \
BLA
}
s/OLD2/NEW2/

```which finds pattern OLD1, appends the following line (provided it is not at EOF) to the pattern space, then does the OLD1/NEW1 substitution and appends BLA *after* the following line

(the second substitution is straightforward I think)

and then doing

```
sed -f *scriptfile* *yourfile*
```No guarantees though!

---

### Post by Vaphell on 2012-08-15
maybe something like this
```
$ echo "aaa OLD1 sss
qqq www eee
zzz OLD2 xxx" | sed -r 's/OLD1/NEW1/g; s/^(.*)OLD2(.*)$/BLA\n\1NEW2\2/'
aaa NEW1 sss
qqq www eee
BLA
zzz NEW2 xxx 
```

---

### Post by trent.josephsen on 2012-08-15
How long could it take to learn enough awk to automate this process? 3 days? 5? Surely no longer than that.

Today it may well seem like learning awk is significantly harder than editing the files manually. But what if the libraries change again? Or, which may be more likely, what if somebody else runs into the same problem and asks you to help them solve it?

I don't know awk; I learned Perl first and that became my go-to text processing language, but I couldn't tell you how many times it's saved me time making tedious changes of the type you describe.

tl;dr - Work smarter, not harder.

---

### Post by Vaphell on 2012-08-15
agreed, besides typical usage cases for awk are trivially easy to grasp, nobody says you need to learn everything to have a useful tool in your toolbox.

this case:
```
$ echo "aaa OLD1 sss
qqq www eee
zzz OLD2 xxx" | awk '/OLD1/{ gsub("OLD1","NEW1") }
                     /OLD2/{ gsub("OLD2","NEW2"); print "BLA" }
                           { print $0 }'
aaa NEW1 sss
qqq www eee
BLA
zzz NEW2 xxx
```
for each line awk checks if a given block meets the criteria, blocks of code are tried and executed in order
1. if line contains OLD1: substitute NEW1 (but don't print), if not - skip
2. if line contains OLD2: substitute NEW2 (but don't print) and print "BLA", if not - skip
3. print line ($0)

$0 is the record (line by default, but it can be changed with record separator)
$1+ are the fields (whitespace delimited, but it can be changed with field separator). You can freely use these symbols with print (eg. *print $0,$3,$4*), in conditions (eg. *$3=="xyz"{...}*), do math and other operations (eg. *{ $2=$2+3 }*), etc.
There are also NR (record number) and NF (number of fields in the record) which are also allowed (eg. *NR>10 && NF<5 { print (NR-10)":"$0 }*)

---

### Post by bubulescu on 2012-08-16
Thank you all for the replies. While for you this may seem simple, for me it's something new as I never used sed, awk or the likes. Still, it works! I chose steeldriver's approach for its seeming simplicity and, with some brute-force tinkering on a copy of one folder, I managed to get it working.

Here's a part of the script, as it is now:
```
/Math\\\\Sum/{$!N;s/Math\\\\Sum/Math\\\\Math2r/g;a \
SYMATTR SpiceModel +
}
s/Math\\\\Dif/Math\\\\Math2r/g

```

There are other similar lines. Here's the command line:
```
find <path> -type f -name '*.asc' -print0 | xargs -0 sed -i -f sedscript
```

It took me a while to understand how to get the "\\" in place and, the bugger, after I opened the first schematic I realized there was a different model named Sum5 from an older library, so now I had Math2r5; thus, the second script was born...

All in all it was a success, thank you for all the guidance.

Now I'm trying to figure out how to search for occurences of OLD3, determine if the second 'xor' the third line has either X1, X2 or X3 and then do a proper replace. But I think it will be done by hand since there aren't that many schematics who have this.


Thank you,
Vlad

---

### Post by steeldriver on 2012-08-16
Glad you got it working - yes escaping literal backslashes in sed is a pain - you may find that Vaphell's 'awk' solution handles those better (Vaphell's 'sed' solution is also nice because unlike the 'a' command it doesn't require splitting the command over multiple lines.)

I forgot to mention you can make the sed script directly executable like a shell script if you prefer i.e.

```
#!/bin/sed -i -f 
/OLD1/{$!N;s/OLD1/NEW1/;a \
BLA
}
s/OLD2/NEW2/
```so that your find becomes

```
find <path> -type f -name '*.asc' -print0 | xargs -0 /path/to/sedscript
```(or put it somewhere in your path - e.g. $HOME/bin). Or you could even put everything in a bash script with the 'find' if that makes it more maintainable, like

 ```
#!/bin/bash

while read -r -d $'\0' file; do
    /bin/sed -e '/OLD1/{$!N;s/OLD1/NEW1/;a \
BLA
    }' -e 's/OLD2/NEW2/' "$file"
done < <(find <path> -type f -name '*.asc' -print0)
```or

```
#!/bin/bash

while read -r -d $'\0' file; do
  awk '/OLD1/{ gsub("OLD1","NEW1") }
    /OLD2/{ gsub("OLD2","NEW2"); print "BLA" }
    { print $0 }' "$file"
done < <(find <path> -type f -name '*.asc' -print0)
```[I *think* that the xargs is unnecessary if you do that (the shell should buffer the arg list?) but the other posters  are better than me at that kind of thing, in fact I probably stole the 'read' loop from Vaphell in the first place]

Don't forget to make the script executable (chmod) if you go either of those  routes.

---

### Post by bubulescu on 2012-08-18
Good ideas are always welcome, thank you! 

> Don't forget to make the script executable (chmod) if you go either of those routes.

That's how I got them working ;)

---


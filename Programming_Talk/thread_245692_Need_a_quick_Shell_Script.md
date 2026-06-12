---
title: "Need a quick Shell Script"
date: 2006-08-28
forum: Programming Talk
---

### Post by %hMa@?b&lt;C on 2006-08-28
could somebody please please write me a schll script that removes every line in a .txt file that begins with "0000"
thanks,
Jeff

---

### Post by tribaal on 2006-08-28
May I suggest you take a look at [this guide]("http://www.tldp.org/LDP/abs/html/")?
You might as well learn bash scripting in the process :)

I would have written it myself for you, but I can't remember how it works out of my head and I'm at work... :(

- trib'

---

### Post by amo-ej1 on 2006-08-28
```

$ cat test.txt; echo "---";  cat test.txt  | sed '/^0000/d'
0000
k0000

---
k0000


```

---

### Post by JonahRowley on 2006-08-28
```
$ cat test.txt; echo "---";  cat test.txt  | grep -v ^0000
0000
k0000
---
k0000

```

Definately more than one way to do it :P

---

### Post by skymt on 2006-08-28
Geek quiz alert! A free virtual beer to the first person to post versions in each of these languages:

* Perl
* Python
* Ruby
* Vim script
* Pure shell (any shell, no external programs)
* (extra credit) Awk

Don't let the virtual beers get cold, post away!

---

### Post by JonahRowley on 2006-08-29
```

$ perl -e 'while(<>){print unless $_ =~ /^0000/}' test.txt
k0000
$ cat grep.py
import re,sys

pat = re.compile('^0000')
for line in sys.stdin:
  if not pat.search(line):  print line,
$ python grep.py <test.txt
k0000
$ ruby -e 'STDIN.each_line do|l| puts l unless l =~ /^0000/ end' <test.txt
k0000
$ ruby -e 'puts STDIN.read.split("\n").select{|l| not l =~ /^0000/}.join("\n")' <test.txt
k0000
$ (while read line; do if [ ${line:0:4} != "0000" ]; then echo $line; fi; done) <test.txt
k0000
$ cat grep.awk
!/^0000/ {
  print
}
$ awk -f grep.awk <test.txt
k0000

```

Sorry, I don't know Vim script :(  I did give two Ruby ones though.

---

### Post by ifokkema on 2006-08-29
> **skymt said:**
> Don't let the virtual beers get cold, post away!
Euhmm... you always like your beer **hot**, then?

---

### Post by skymt on 2006-08-29
> **ifokkema said:**
> Euhmm... you always like your beer **hot**, then?

They're British.

---

### Post by skymt on 2006-08-29
> **JonahRowley said:**
> <snip code>

Sorry, I don't know Vim script :(  I did give two Ruby ones though.

Okay, Jonah, that's six warm beers! Half a beer for the extra Ruby version, one and a half for awk.

There's one left for whoever comes up with a VimScript implementation! (By the way, I have one, so it's possible. Easy, in fact, for anyone who knows regular expressions.)

---

### Post by ifokkema on 2006-08-29
> **JonahRowley said:**
> ```

$ perl -e 'while(<>){print unless $_ =~ /^0000/}' test.txt
k0000
$ cat grep.py
import re,sys

pat = re.compile('^0000')
for line in sys.stdin:
  if not pat.search(line):  print line,
$ python grep.py <test.txt
k0000
$ ruby -e 'STDIN.each_line do|l| puts l unless l =~ /^0000/ end' <test.txt
k0000
$ ruby -e 'puts STDIN.read.split("\n").select{|l| not l =~ /^0000/}.join("\n")' <test.txt
k0000
$ (while read line; do if [ ${line:0:4} != "0000" ]; then echo $line; fi; done) <test.txt
k0000
$ cat grep.awk
!/^0000/ {
  print
}
$ awk -f grep.awk <test.txt
k0000

```

Sorry, I don't know Vim script :(  I did give two Ruby ones though.

Damn, you're good. You surely know your languages. I'm kinda stuck with PHP, and a liiiitle bit of C++.

---

### Post by Ragazzo on 2006-08-29
In Vim
:g/^0000/d

---

### Post by skymt on 2006-08-29
Bingo! The last beer goes to Ragazzo! Maybe I should have picked [INTERCAL](http://en.wikipedia.org/wiki/INTERCAL_programming_language) for the extra credit.

---

### Post by JonahRowley on 2006-08-30
Hmm..  I misunderstood.  I wasn't aware vim commands were the same as vim script :P  And I could have had the beer :(

---


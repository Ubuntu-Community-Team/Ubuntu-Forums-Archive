---
title: "need help with grep or similar"
date: 2006-09-01
forum: Programming Talk
---

### Post by pedrotuga on 2006-09-01
Hi,
I want to catch all the urls from an html source.

I went and red about grep and its regulat expression but i am facing to basic problems:

-grep is designed to work on a line by line basis, that screws it up becauase oftem there is huge pieces of html without an endl
-there might be, but so far i havent figured out how to include spaces on the wildcards.

any alternative or hints?
a little code snippet would be wellcome as well of course ;)

---

### Post by ciscosurfer on 2006-09-01
How 'bout this:

[COLOR=DarkRed] cat[/COLOR] *your_html_source_file* [COLOR=DarkRed]| grep http

[COLOR=Black]or [/COLOR]

cat [/COLOR]*your_html_source_file *[COLOR=DarkRed]| grep href[/COLOR]

---

### Post by ifokkema on 2006-09-01
That would do exactly what he described what he doesn't want :)

I'm not currently working on Linux (shame on me) but I know grep has the option to show only the text that has matched the pattern. Then you would need to use a full URL pattern, and you'll have your results.

HTH

Ivo

---

### Post by ciscosurfer on 2006-09-01
Check 'man grep' for info on regular expressions.  By default, grep matches by line.

You can also try (for visual clarity): [COLOR=DarkRed] cat [/COLOR]*your_html_source_file *[COLOR=DarkRed]|  grep --color=always href[/COLOR]

---

### Post by Stone123 on 2006-09-01
Maby this can help , just search for some regular expression. 
Perl:
[http://www.troubleshooters.com/codecorn/littperl/perlreg.htm](http://www.troubleshooters.com/codecorn/littperl/perlreg.htm)

Since i don't know Perl i would use Php and regular expression.
Create one input box  button , place the page on apache with php. Use eregi to get String from http + rest till " "

---

### Post by pedrotuga on 2006-09-01
I thought about doing a php script instead... but thats not what i am looking for... i want to be able to catch the links without leaving the console... this can also be practical and reused in other shell scripts.

i am confused.
Are the regular expressions the exact same in perl, php? what about the ones used in grep??? are they the same as the ones mentioned before?

u gave me a link to perl regular expressions... can i use those on grep?
what about php's?

---

### Post by ifokkema on 2006-09-01
PHP has a set of 'Perl compatible' regular expressions, for which the syntax is almost exactly the same as Perl's. The native PHP regular expressions are a bit easier to use, but to be honest I can't even remember how they are used since I stick to the much faster Perl compatible ones.

Grep has different 'levels' of pattern matching. I believe the -E options allows grep to process regular expressions like you can use in Perl/PHP as well. I think regular expression patterns are just so common that you can easily adopt them to different languages / executables.

This is what I would use in PHP:
```
/^(ht|f)tps?:\/\/([0-9a-z][-0-9a-z]*[0-9a-z]\.)+[a-z]{2,4}\/?[%&=#0-9a-z\/._+-]*\??.*$/i
```
to match a absolute URL. It can easily be adopted for usage with grep.

---

### Post by pedrotuga on 2006-09-01
-E enables regular expressions, the problem is that grep always returns a line and i want the match only...
any other program i can use besides grep that returns the regular expression matches?

if not i will use php... the problem is that i have PHP installed 
as an  apache module :( wich means i have to donload it an recompile it in order to be able to run php in scripts in the shell.

ifokkema, thanks a million for the regular expression.

---

### Post by Ragazzo on 2006-09-01
I wrote this script in Python. It finds all links defined with an A element.

```

#!/usr/bin/env python

import re
import sys

p1 = re.compile(r'<\s*a.*?>', re.DOTALL | re.I) #A-tag
p2 = re.compile(r'href="(.*?)"', re.DOTALL | re.I)

sys.argv.pop(0)

for filename in sys.argv:
	file = open(filename)
	text = file.read()
	file.close()
	for tag in p1.findall(text):
		print p2.search(tag).group(1)


```

---

### Post by ifokkema on 2006-09-02
> **pedrotuga said:**
> -E enables regular expressions, the problem is that grep always returns a line and i want the match only...
According to the manual:
```

 -o, --only-matching
        Show only the part of a matching line that matches PATTERN.
```

> **pedrotuga said:**
> if not i will use php... the problem is that i have PHP installed as an  apache module :( wich means i have to donload it an recompile it in order to be able to run php in scripts in the shell.
No, you don't :D
```
sudo apt-get install php4-cli
```
(or php5-cli, if you'd like)

Then, you can put
```
#!/usr/bin/php
```
on top of your script and you're off writing your PHP app :)

> **pedrotuga said:**
> ifokkema, thanks a million for the regular expression.
You're welcome. Ragazzo has a good point too, matching the <A href=""> tags. It saves you a enourmous regular expression, but it depends on your source file if it's usable. Also, using that technique will catch relative URLs, not sure if you need those, too.

---


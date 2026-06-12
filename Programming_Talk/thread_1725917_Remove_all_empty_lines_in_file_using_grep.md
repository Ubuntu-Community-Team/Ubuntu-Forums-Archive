---
title: "Remove all empty lines in file using grep?"
date: 2011-04-10
forum: Programming Talk
---

### Post by hakermania on 2011-04-10
I know that 
grep -v "\here_something" file 
like
```
grep -v "\@" file
```
will remove all lines starting with @
But I've tried \n instead of @ and (as I supposed) it doesn't work.
It is important for me the solution to be with grep and not with awk or sed, because I want to remember the solution and not to combine them to my mind and then forget all I knew :P

Thx in advance!

---

### Post by Vaphell on 2011-04-10
```
grep -Ev '^$' file
```
or when you need to get rid of whitespace-only lines too, upgrade regex to '^\s*$'

---

### Post by ghostdog74 on 2011-04-10
Use awk. It has the advantage of getting rid of empty lines for you AND if you need other processing on other lines, it will do that for you too. 

```

#remove empty lines
awk 'NF' file

```

for example, if you need to count how many lines that are not empty 
```

awk 'NF{c++}END{print c}' file

```

---

### Post by bashologist on 2011-04-10
Another example using perl. This one removes any line containing just white space. Redirect the output or use the i switch to overwrite file.

```
perl -n -e 'print unless /^\s*$/' file.txt
```

Sed also works great check out this page for lots of great examples.

[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

---

### Post by kurum! on 2011-04-10
Similarly with Ruby(1.9+)

remove lines also with just white space
```

ruby -ne 'print unless /^\s*$/' file

```

remove empty lines
```
ruby -ne 'print unless /^$/' file

```

---

### Post by bashologist on 2011-04-10
Thats interesting. Ruby looks just like perl lol.

How about this bash example....

```
while read line; do
	if [[ "$line" =~ ^$ ]]; then
		continue
	fi
	echo "$line"
done < file.txt
```

---

### Post by geirha on 2011-04-11
To edit files, use an editor...
```
ed -s file <<< $'g/^$/d\nw'
```

@bashologist, that bash loop will also omit lines containing only whitespace. And using a regex for that is a bit overkill imo. I'd do:
```

while IFS= read -r line; do 
    [[ $line ]] && printf '%s\n' "$line"
done < file

```

---

### Post by kurum! on 2011-04-11
> **bashologist said:**
> Thats interesting. Ruby looks just like perl lol.

Ruby borrows syntax from Perl and also from Python. Its got the best of both worlds.

---

### Post by bashologist on 2011-04-12
@geirha Looks complex. I don't wanna use the brain power nessicary to process this ifs read commands.

But I have maybe a better solution if white space isn't an issue.
```

while read input; do
if [ -n "$input" ]; then
echo "$input"
fi
done < testing.txt

```
I don't think you can beat that. :)

---

### Post by hakermania on 2011-04-12
Omg guys! Too effort so just a simple question!
Do not solve a problem that it's already solved?
Thx all for your effort anyway :) I love UF :)

---


---
title: "Replace a Line With Sed - that Has a *"
date: 2011-05-10
forum: Programming Talk
---

### Post by bsntech on 2011-05-10
OK - I've been trying to get this working for a couple of hours now.  I've confirmed that it is due to a wildcard in the variable.

General info:

I'm attempting to replace a specific line (say line 108) in the /etc/apache2/httpd.conf file.

So, I do a grep to find the line, run it through a series of other programs which then returns me the line number.

I'm searching for "website.domain.com":

LINEA=$(grep -n "website.domain.com" /etc/apache2/httpd.conf | cut -f1 -d: | head -1)

Above you can see that I'm searching for it and then assigning the line number to the LINEA variable.

Then, the REAL line I need is one line below that - so I increment LINEA by 1:

LINEA=$((LINEA + 1))

Now, I use sed to then read that line in:

CHANGE=$(sed -n "${LINEA}p" /etc/apache2/httpd.conf)

So now the contents of the line is loaded in the CHANGE variable.

Now, I want to append something to the line, so I do this:

NEWLINE="domain2.com *.domain2.com"
NEW="$CHANGE $NEWLINE"

So I am making a new variable - called NEWLINE - which will store the new information that I want to append to that line - and then I concatenate the contents of the line from the file with the newline - so then I have my full line that I need to write back to the file.

Alright - here is where the problem is.  It should be as simple as doing this:

sed -e "${LINEA}s/$CHANGE/$NEW/g" -i /etc/apache2/httpd-test.conf

So basically the command above says to replace the contents of line number LINEA that contains the data in the $CHANGE variable with the data in the $NEW variable.

However, the $CHANGE variable has a * (asterisk) and I cannot escape it with a "\".  So, nothing is done.  If I manually type in the contents of the $CHANGE variable and escape the * (asterisk), it works.  It is funny that the $NEW variable has at least two asterisks - sed has no problem with it.

So, because I clearly cannot escape the asterisk(s) in the $CHANGE variable, how can I get sed to ignore it and actually look at the line with the asterisk?

Thank you for any assistance.

---

### Post by Telengard C64 on 2011-05-10
<gripe>
I honestly can't understand why you don't just use **sed** (or maybe AWK) for the whole thing instead of mucking about with **grep** and **cut**. It can be scripted to do what you want.
</gripe>

I do think this form of [parameter expansion](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html#Shell-Parameter-Expansion) will help you with the ***** problem.

[quote=Bash Reference Manual - 3.5.3 Shell Parameter Expansion]${parameter/pattern/string}
    The pattern is expanded to produce a pattern just as in filename expansion. Parameter is expanded and the longest match of pattern against its value is replaced with string. If pattern begins with ‘/’, all matches of pattern are replaced with string. Normally only the first match is replaced. If pattern begins with ‘#’, it must match at the beginning of the expanded value of parameter. If pattern begins with ‘%’, it must match at the end of the expanded value of parameter. If string is null, matches of pattern are deleted and the / following pattern may be omitted. If parameter is ‘@’ or ‘*’, the substitution operation is applied to each positional parameter in turn, and the expansion is the resultant list. If parameter is an array variable subscripted with ‘@’ or ‘*’, the substitution operation is applied to each member of the array in turn, and the expansion is the resultant list.
[/quote]

```
~$ a='domain2.com *.domain2.com'
~$ echo ${a/\*/\*}
domain2.com *.domain2.com
~$ echo "${a/\*/\*}"
domain2.com \*.domain2.com

```

HTH

---

### Post by bsntech on 2011-05-10
> **Telengard C64 said:**
> <gripe>
I honestly can't understand why you don't just use **sed** (or maybe AWK) for the whole thing instead of mucking about with **grep** and **cut**. It can be scripted to do what you want.
</gripe>

I do think this form of [parameter expansion](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html#Shell-Parameter-Expansion) will help you with the ***** problem.



```
~$ a='domain2.com *.domain2.com'
~$ echo ${a/\*/\*}
domain2.com *.domain2.com
~$ echo "${a/\*/\*}"
domain2.com \*.domain2.com

```

HTH

Thank you for the help - but it still doesn't work.

Here is the quick and dirty of the script.  It is pretty simple.  The whole idea here is to simply add a new domain name to a VirtualHost.

```
#!/bin/sh
LINEA=$(grep -n "sub.bsntech.com" /etc/apache2/httpd.conf | cut -f1 -d: | head -1)
LINEA=$((LINEA + 1))
CHANGE=$(sed -n "${LINEA}p" /etc/apache2/httpd-test.conf)
echo $CHANGE
NEWLINE="bsntech.com *.bsntech.com"
NEW="$CHANGE $NEWLINE"
echo $NEW
sed "${LINEA}s%\${CHANGE/\*/\*}\*%\\${NEW}%" -i /etc/apache2/httpd-test.conf
```

When I do this:

```
echo ${CHANGE/\*/\*}
```

It echos the line correctly.  But, I can simply put in:

```
echo $CHANGE
```

And it echos to the terminal fine as well.

It is just somehow getting sed to escape the asterisk.

---

### Post by dwhitney67 on 2011-05-10
This worked ok for me:
```

#!/bin/bash

...

sed -e "${LINEA}s/${CHANGE}/${NEW}/" -i /etc/apache2/httpd.conf

```

---

### Post by bsntech on 2011-05-10
> **dwhitney67 said:**
> This worked ok for me:
```

#!/bin/bash

...

sed -e "${LINEA}s/${CHANGE}/${NEW}/" -i /etc/apache2/httpd.conf

```

Tried it - doesn't work.  It doesn't do anything with the line; almost like it isn't finding it.

If I substitute the whole line in for ${CHANGE} like this:

```
sed -e "${LINEA}s/ServerAlias domain.com \*.domain.com/${NEW}/" -i /etc/apache2/httpd.conf
```

It works.  Notice that I used a backslash to escape the * (asterisk).

In essence, if there was a way to potential re-write the $CHANGE variable to escape wildcards, that probably would do the trick - but I can't find anything on that.

---

### Post by bsntech on 2011-05-10
> **bsntech said:**
> Tried it - doesn't work.  It doesn't do anything with the line; almost like it isn't finding it.

If I substitute the whole line in for ${CHANGE} like this:

```
sed -e "${LINEA}s/ServerAlias domain.com \*.domain.com/${NEW}/" -i /etc/apache2/httpd.conf
```

It works.  Notice that I used a backslash to escape the * (asterisk).

In essence, if there was a way to potential re-write the $CHANGE variable to escape wildcards, that probably would do the trick - but I can't find anything on that.

Fixed it.  Finally found a solution after looking for at least three hours online.

Here is the code:

```
sed -e "${LINEA}s/$(echo $CHANGE | sed -e 's/\(\.\|\/\|\*\|\[\|\]\|\\\)/\\&/g')/${NEW}/" -i /etc/apache2/httpd-test.conf
```

Basically in the case above, I am issuing a statement to echo the $CHANGE variable and piping it back int sed to escape the * (amongst other) wildcards.  Sed then basically re-writes it and plugs it back into the original process for processing.

---

### Post by dwhitney67 on 2011-05-11
> **bsntech said:**
> Tried it - doesn't work.
I find this hard to believe, unless of course you left out some nugget of information that is critical to solving the problem.

First of all, can you please indicate what shell your script is using?  In other words, what is /bin/sh referencing?  It is probably either one of these two:  dash or bash.

As for a little advice, I would recommend that you attempt your scripting experiments on a simple basis, rather than use your production script and system configuration file.  That is what I did last night, using the information you provided, to verify the solution I offered.

Here's my configuration file (file.conf):
```

# SERVER: website.domain.com
SERVER: www.google.com

```

Here's my script:
```

#!/bin/bash

LINEA=`grep -n "website.domain.com" ./file.conf | cut -f1 -d: | head -1`
LINEA=$((LINEA + 1))

CHANGE=`sed -n "${LINEA}p" ./file.conf`

NEWLINE="domain2.com *.domain2.com"
NEW="$CHANGE $NEWLINE"

sed -e "${LINEA}s/${CHANGE}/${NEW}/" -i ./file.conf

```
Bear in mind, that everything above is based on your information; if something is missing from above, then the responsibility is solely yours.


P.S.  I just verify that whether using dash or bash would not have made a difference for the code above.

---


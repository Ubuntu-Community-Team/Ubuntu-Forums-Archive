---
title: "bash pitfalls renaming files  in scripts"
date: 2013-03-09
forum: Programming Talk
---

### Post by jamesbon on 2013-03-09
I am reading a guide here
[http://mywiki.wooledge.org/BashFAQ/030]("http://mywiki.wooledge.org/BashFAQ/030#preview")
on this link a few examples are given I am trying to understand them one example code says

```

# Bash
# Replace all spaces with underscores
for f in *\ *; do mv -- "$f" "${f// /_}"; done

```
what I have known till now was use of a backslash for special characters like space of ~ or # etc in case of search and replace 
examples or in shell scripts here in above example they have
used ```
${f// /_}  
```

forward slashes , I am not clear with this is this allowed? 
in another example on same page
they give an example to remove space and replace it with underscores 
```


find . -depth -name "* *" -exec bash -c 'dir=${1%/*} base=${1##*/}; 
mv "$1" "$dir/${base// /_}"' _ {} \;

```
in above example I am not clear with following
1) dir=${1%/*}
2) base=${1##*/}
3) and when it says mv "$1"what is meant by $1 in the above statement,
4)  finally  the find command is being closed with -exec <something> _ {} \;
now what is the use of an underscore _ ,curly braces and a backslash followed by a colon above?
in the third example they say
```

# tolower - convert file names to lower case
# POSIX
for file in "$@"do 
   [ -f "$file" ] || continue                # ignore non-existing names   
 newname=$(echo "$file" | tr '[:upper:]' '[:lower:]')     # lower case   
 [ "$file" = "$newname" ] && continue      # nothing to do   
 [ -f "$newname" ] && continue             # don't overwrite existing files  
  mv -- "$file" "$newname"done
```
I am not clear with following lines
5) ```
[ -f "$file" ] || continue                # ignore non-existing names
```
[FONT=Verdana][FONT=arial]I am not clear with  [ ] tests the condition if $file exists then what is the use of OR condition || here and the continue statement[/FONT]
[/FONT][FONT=Verdana][FONT=arial]6) ```
[ -f "$newname" ] && continue             # don't overwrite existing files 
```same doubt here as in point 5[/FONT]
[/FONT]

---

### Post by schragge on 2013-03-09
> **jamesbon said:**
> in case of search and replace 
examples or in shell scripts here in above example they have
used ```
${f// /_} 
``` forward slashes , I am not clear with this is this allowed?Yes, it is.
> **jamesbon said:**
> in above example I am not clear with following
1) dir=${1%/*}
2) base=${1##*/}
3) and when it says mv "$1"what is meant by $1 in the above statement,
4)  finally  the find command is being closed with -exec <something> _ {} \;
now what is the use of an underscore _ ,curly braces and a backslash followed by a colon above?
1) is roughly the same as ```
dir=`dirname $1`
``` It removes the suffix that starts at '/'.


2) is roughly equivalent to ```
base=`basename $1`
``` It removes the longest prefix that ends in '/'.


3) $1 is the first shell parameter to *bash -c* in -exec action of find. It's the file name that find supplies in the stead of '{}' placeholder.


4) _ is a placeholder for $0 which is simply discarded. Have your read my explanation in [post=12544839]this post[/post]?
> **jamesbon said:**
> 5) ```
[ -f "$file" ] || continue                # ignore non-existing names
``` The test command ([...]) fails if the tested condition is wrong, i.e. $file doesn't exist or is not a regular file. The right part of || gets executed only in this case. It's basically a more concise way to say
```
if [ -f "$file" ]; then true; else continue; fi
```

It's a fairly common stanza in shell programming:
```
test_something && action_if_the_test_succeed || action_if_the_test_failed
```

---

### Post by drmrgd on 2013-03-09
The first parts of your questions all revolve around bash parameter substitution.  The syntax you see is a way to use a pattern match in bash and make a substitution.  It's not quite as flexible and powerful as a real regular expression, but it can still be useful for simple matching and replacing, as shown in Greg's Wiki.  See this page for some more details on how to use various forms of parameter substitution to modify variables:

[http://mywiki.wooledge.org/BashFAQ/073?action=show&redirect=ParameterExpansion](http://mywiki.wooledge.org/BashFAQ/073?action=show&redirect=ParameterExpansion)[URL="http://wiki.bash-hackers.org/syntax/pe"]
http://wiki.bash-hackers.org/syntax/pe[/URL]

To the '$1' question, this has to do with the '-c' option in bash.  From the manpages:

>  -c string If the -c option is present, then commands are read from string.  If there are arguments after the  string,  they                 are assigned to the positional parameters, starting with $0. 

The OR and AND in the last commands are ways to handle errors and unmet conditions.  In the first example, the code is testing "$file" to see if it exists and is a 'file'.  This gives the test an option so that if the test fails due to non-existing files (as the comment says), the loop is to just continue on rather than stopping at the point.  The same case for the AND, except this time, in order to prevent overwriting something that exists in $file, the script will continue on if there is suitable content in $file rather than overwriting what's there.  If you think about these tests as if / else statements (to which they're related by not quite the same), the || and && are sort of the else statements.  In this case they may not explicitly be necessary for such a simple process.  But, if you start processing unusual cases, this is a handy way to make sure you always get the result you expected.

---

### Post by The Cog on 2013-03-09
There are other good replies here, but I would like to refer you to this excellent link: [http://tldp.org/](http://tldp.org/)

> ${f// /_} is a string substitution. I hadn't seen it before today, so I went looking for an explanation. This looks like a very good one (search the page for "string replacement"):
[http://tldp.org/LDP/abs/html/string-manipulation.html](http://tldp.org/LDP/abs/html/string-manipulation.html)

---


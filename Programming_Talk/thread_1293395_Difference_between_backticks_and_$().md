---
title: "Difference between backticks and $()"
date: 2009-10-17
forum: Programming Talk
---

### Post by silentrebel on 2009-10-17
I was writing a script some time ago and came across an occasion where
```
variable=`echo $hello | awk '{ gsub(/\\/, "/"); print }'`
``` was not working...  I desperately posted on the forums and it was suggested that I should use $():
```
variable=$(echo $hello | awk '{ gsub(/\\/, "/"); print }')
```
Fortunately, that worked; unfortunately, the helpful individual never answered my question as to why this syntax worked and the other didn't.  Thus I pose this question again to the great public: what is the difference between backticks and $() and in what contexts should each be used?

---

### Post by jpkotta on 2009-10-17
I've never run into a situation before now where there was a difference between backticks and $().  I prefer $() because I think it's easier to read.  OTOH, backticks are the standard.  Only Bash supports $() AFAIK.

The Bash manual doesn't say anything about backticks being treated differently than $(), except for maybe this vague statement:
> 
When using the $(command) form, all characters between the parentheses make up the command; none are treated specially.


I guess that could mean that $() "quotes the command more", in the sense that backticks treat the command sort of like a string with the associated string processing.

If I set hello to "C:\windows\fails\at\paths" and then run your code, I need to double escape the search pattern when using the backticks.

```

**$ hello="C:\\windows\\fails\\at\\paths";  echo $hello**
C:\windows\fails\at\paths
**$ var=`echo $hello | awk '{ gsub(/\\/, "/"); print }'`; echo $var**
awk: line 1: runaway string constant "); print } ...
bash: echo: write error: Broken pipe
**$ var=`echo $hello | awk '{ gsub(/\\\\/, "/"); print }'`; echo $var**
C:/windows/fails/at/paths
**$ var=$(echo $hello | awk '{ gsub(/\\/, "/"); print }'); echo $var**
C:/windows/fails/at/paths

```

I have no idea if this is the problem you were seeing because you didn't supply enough information.

---

### Post by ghostdog74 on 2009-10-17
if you have taken a look at the [advance bash guide (under 3.4.5)]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_04.html") (see my sig link for more), you can see there are some caveats with regard to backslashes. Furthermore, you are substituting backslash in awk. see [here]("http://www.gnu.org/manual/gawk/html_node/Gory-Details.html") regarding uses of gsub with backslash. After reading and understand all that...you can be sure that it will work when you do this:
```

# hello="dkfafd\wklfafd\kdfasdfa"
# goodbye=`echo "$hello" | awk '{ gsub(/\\\\/, "/"); print }'`
# echo $goodbye
dkfafd/wklfafd/kdfasdfa


```

---

### Post by silentrebel on 2009-10-17
Sorry if you thought that the provided background was insufficient, jpkotta.  In any case, your comment was very helpful!  Thanks for confirming and showing me the awesome documentation ghostdog74...
Case closed...

---


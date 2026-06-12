---
title: "sed one line to another"
date: 2016-03-14
forum: Programming Talk
---

### Post by maclenin on 2016-03-14
"Why might this be happening?"

I have (moved) appended one line...
```
["<p class = \"a\">one line</p>"];
```
...to another...
```
["<p class = \"b\">another</p>"];
```
...within a javascript file, hoping to yield:
```
["<p class = \"b\">another</p>"];
["<p class = \"a\">one line</p>"];
```
However, this is the result I see:
```
["<p class = \"b\">another</p>"];
["<p class = "a">one line</p>"];
```
Note the missing \ and \ in the appended one line.

I have run a sed statement similar to...
```
sed -e '/^.*another.*$/ a\'$'\n'"${one_line}" < source > target
```
...to execute the move.

I captured one line inside a variable using:
```
one_line=$(sed -n -e '/^.*one line.*$/p' < source)
```
Running...
```
echo "${one_line}"
```
...yields...
```
["<p class = \"a\">one line</p>"];
```
...with \ and \ included.

Hmm? [http://www.grymoire.com/Unix/Sed.html#uh-62](http://www.grymoire.com/Unix/Sed.html#uh-62)

Thanks for any guidance!

---

### Post by papibe on 2016-03-14
Hi maclenin.

I believe you are trying to use a string as a regular expression. I think it would work if you escape the 'escapers'

Try this:
```
ol_expr="${one_line//\\/\\\\}"

sed -e '/^.*another.*$/ a\'$'\n'"${ol_expr}" < source
```
Or this:
```
sed -e '/^.*another.*$/ a\'$'\n'"${one_line//\\/\\\\}" < source
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by maclenin on 2016-03-14
papibe!

Thank you!

\[SOLVED\] indeed!

Can you tell me why that particular sequence / critical mass / method of escaper escaping did the trick?

Thanks, again!

P.S. I think one leading / is missing from your "Or this:" solution!

---

### Post by steeldriver on 2016-03-14
If you don't *have* to stream the source file via stdin, another option might be to use the 'r' command 

```

sed -e '/another/ r /dev/stdin' <<< "$one_line" source

```

You could probably combine them e.g.

```

sed '/one line/!d' source | sed -e '/another/ r /dev/stdin' source

```

---

### Post by papibe on 2016-03-14
> **maclenin said:**
> I think one leading / is missing from your "Or this:" solution!
Fixed! Thanks :D

> **maclenin said:**
> Can you tell me why that particular sequence / critical mass / method of escaper escaping did the trick?
Backslash works as an escape character in a regular expression. This create the problem of how to reference the backslash itself. The solution is escape it too ;)
```
$ echo 'hello\ world' | sed -e 's/**[COLOR="#FF0000"]\[/COLOR]**//'
sed: -e expression #1, char 5: unterminated `s' command

$ echo 'hello\ world' | sed -e 's/[COLOR="#FF0000"]**\\**[/COLOR]//'
hello world

```
Does that help?
Regards.

---

### Post by maclenin on 2016-03-15
steeldriver!

Thanks for the r - I'll take a closer look....

papibe!

Thank you - your latest example is very clear: sed statement with free-roaming \ gumming up the works, with second \ introduced to escape the previously free-roaming \

In your "Or this:" example (for example), I am trying to wrap my head around the structure and logic of this specific herd of (forward and) backslashes - //\\/\\\\ - and how it all escapes its way into the ${one_line} string. Are there delimiters / in the herd of \ or simply backslashes escaping!?

I count 3 / and 6 \ in the herd. What do they each do?

Thanks, again, for any additional clarity!

---

### Post by papibe on 2016-03-15
This:
```
${one_line//\\/\\\\}"
```
is what some called string replacement, parameter expansion, or parameter substitution.

Here's a basic example:
```
$ var="yabadabadoo"

$ echo "$var"
yabadabadoo

$ echo "${var}"
yabadabadoo

$ echo "${var/a/A}"
y[COLOR="#FF0000"]**A**[/COLOR]badabadoo

$ echo "${var//a/A}"
y[COLOR="#FF0000"]**A**[/COLOR]b[COLOR="#FF0000"]**A**[/COLOR]d[COLOR="#FF0000"]**A**[/COLOR]b[COLOR="#FF0000"]**A**[/COLOR]doo

```

So, in words this:
```
${one_line//\\/\\\\}"
```
would be:
[LIST]
[*]Take the variable called one_line
[*]do a string replacement for all occurrences of the string '\', a backslash (which has to be refer as '//'), and
[*]replace it with '\\', two backslashes (refer as '\\\\' because of the same reason).
[/LIST]
Hope it helps.
Regards.

EDIT: here are some details on the matter: [Shell parameter expansion]("https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html"), [String Manipulation (go down to Substring Replacement)]("http://tldp.org/LDP/abs/html/string-manipulation.html"), and [Parameter Substitution]("http://tldp.org/LDP/abs/html/parameter-substitution.html").

---

### Post by maclenin on 2016-03-15
papibe!

It helps (again) - indeed! Thank you and for the additional detail! I think I'd been trying to see a regular expression or sed syntax in the delimiters \ & / escapes and had overlooked the (ba)shell!

Relatedly - one other sed question (if I may!)....

Is it possible to use a line number as substitution for / reference to the content of that line (other than, say, 3 in sed -n '3p')?

For example (a hypothetical)...

```
sed -e '1 a\'$'\n'=2 < source > target
```

...where:

1 is the number of the line in source to which we are appending
2 is the number of the line in source whose content or /pattern/ we are (moving &) appending

It is possible - via...
```
sed -n '/pattern/='
```
...to retrieve the line number of the pattern - let's say 2. However, can the line number 2 be used, in reverse, as reference to the /pattern/ - as shown in my example?

Thanks, again, on all fronts!

---

### Post by steeldriver on 2016-03-15
You mean something like

Given
```

$ cat source
Line 1
Line 2
Line 3
Line 4
Line 5
Line 6

```

then to move line **5** after line **2**
```

$ sed '**5**!d' source | sed -e '**5**d' -e '**2**r /dev/stdin' source
Line 1
Line 2
Line 5
Line 3
Line 4
Line 6

```

EDIT: if you only want to move lines DOWN, then you can do that much more simply e.g. copy line m to the hold space and delete it, then append the hold space to the pattern space at line n

```

$ sed '2{h;d};5G' source
Line 1
Line 3
Line 4
Line 5
Line 2
Line 6

```

---

### Post by maclenin on 2016-03-16
steeldriver!

Perfect! You folks have been very helpful!

Just to distil the mission a bit (with a tiny wrinkle)....

source: a file which can have a varying quantity of lines
```

$ cat source
line one
line two
line three
line four
line five
line six
line seven
line eight
line nine
line ten
$
```
task: if certain lines exist, move certain lines
```
$ s=$(sed -n '/seven/,${/eight/=;}' < source)
$ echo "${s}"
8
[B]$ t=$(sed -n '/\(three\|four\)/=' < source)
$ echo "${t}"
3
4[/B]
$ if [ -z "${s}" ] && [ -z "${t}" ]; then echo "no match!"; else sed ''"${t}"'{**h;**d;};'"${s}"'G' < source > target; fi
[B]sed: -e expression #1, char 2: unknown command: `
'[/B]
$

```
target: this is the expected result (given the source), however, I smell a **multi-line match (handling) error**, which I am not certain how to address....
```

$ cat target
line one
line two
line five
line six
line seven < --- this line existed
line eight < --- this line existed
line three < --- this line was moved
line four < --- this line was moved
line nine
line ten
$
```
Note: If I were to change the t variable to match line /three/ only - all works for a single-line match - line three is moved....

I have switched to line numbers as the match reference method to escape having to "escape the 'escapers'"....

Thanks, again, for the guidance!

---

### Post by maclenin on 2016-03-18
...to clarify:

**single-line** match and move...
```
$ s=$(sed -n '/seven/,${/eight/=;}' < source)
$ t=$(sed -n '**/three/**=' < source)
$ if [ -z "${s}" ] && [ -z "${t}" ]; then echo "no match!"; else sed ''"${t}"'{h;d;};'"${s}"'G' < source > target; fi
```
... (runs error-free and) yields:
```
$ cat target
line one
line two
line four
line five
line six
line seven < --- this line exists
line eight < --- this line exists
line three < --- this line exists and was moved
line nine
line ten
$
```
**multi-line** match and move...
```
$ s=$(sed -n '/seven/,${/eight/=;}' < source)
$ t=$(sed -n '**/\(three\|four\)/**=' < source)
$ if [ -z "${s}" ] && [ -z "${t}" ]; then echo "no match!"; else sed ''"${t}"'{h;d;};'"${s}"'G' < source > target; fi
```
... (however) yields:
```
sed: -e expression #1, char 2: **unknown command**: `
'
$
```
I am working to untangle the **multi-line** match and move **unknown command** issue.

Thanks for any help.

---

### Post by maclenin on 2016-03-18
Nearly there (but for a stray [COLOR="#B22222"]newline[/COLOR])...

...and in a (portable*) nutshell:

```

$ cat source
line one
line two
line three
line four
line five
line six
line seven
line eight
line nine
line ten
$ **se**=$(sed -n '/seven/,${/eight/=;}' < source)
$ **tf**=$(sed **-E** -n '/(three**|**four)/=' < source | **paste -s -d, -**)
$ printf '%s\n' "${**tf**}"
**3,4**
$ if [ ! -z "${**se**}" ] && [ ! -z "${**tf**}" ]; then sed "${**tf**}{**H**;d;};${**se**}G" < source > target; fi 
$ cat -A target
line one$
line two$
line five$
line six$
line **s**even$
line **e**ight$
[COLOR="#B22222"]$ [/COLOR]< --- (how) can this newline be suppressed? or is *sed '/^[[:space:]]*$/d'* after the fact the best way do away with this line?
line **t**hree$
line **f**our$
line nine$
line ten$
$
```

Notes:
1. **-E**(xtended) switch added to allow (mac) alternation (a**|**b). Swtich has the same -E(xtended) effect as -r in (my experience) with gnu sed 4.2.2 (xubuntu)....
2. Multi-line, newline-delimited (numeric) string (**tf**) needed to be converted to a comma-delimited string (using **paste**) in order for both line numbers to be (interpreted / read and) separately added (match #1) and appended (match #2) to the hold buffer.
3. h changed to **H** to permit match #2 to be appended to the hold buffer, with G appending the (multi-line, in my case) hold buffer to the pattern space (after **se**).

* cat -A target ~ **cat -e target** on a mac < --- the only non-portable bit, I believe....

This is my take...thanks for any thoughts (or [COLOR="#B22222"]newline suppression tactics[/COLOR]).

---


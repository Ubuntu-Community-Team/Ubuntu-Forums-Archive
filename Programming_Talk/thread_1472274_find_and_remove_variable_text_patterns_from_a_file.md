---
title: "find and remove variable text patterns from a file"
date: 2010-05-04
forum: Programming Talk
---

### Post by boondocks on 2010-05-04
This will replace predefined text patterns in a file with:

sed 's/oldText/newText/g' before.txt > after.txt

But how do you do that with text patterns that are not predefined.
For instance, if the file contains:

[INDENT]May 4 04:29:54 item=1847 qty=49 loc=N5 status=avail
May 4 04:26:43 item=493 qty=562 loc=S4 status=order
May 4 04:24:21 item=6210 qty=82 loc=E1 status=order
May 4 04:21:41 item=92 qty=127 loc=W2 status=avail
[/INDENT]
And I need to remove all the qty fields:

[INDENT]May 4 04:29:54 item=1847 loc=N5 status=avail
May 4 04:26:43 item=493 loc=S4 status=order
May 4 04:24:21 item=6210 loc=E1 status=order
May 4 04:21:41 item=92 loc=W2 status=avail
[/INDENT]
How do you do that?

---

### Post by mo.reina on 2010-05-04
```

old_text = whatever you want to change
new_text = the replacement
sed -e s/"$old_text"/"$new_text"/g $text > text.out
sed -e "s/$old_text/$new_text/g" $text > text.out
```

assign user input to the variables old_text and new_text

---

### Post by boondocks on 2010-05-04
My new_text would be blank.

But my old_text is unknown because it could be anything:
qty=49
qty=562
qty=82
qty=127
qty=21
qty=1934
qty=102
....... etc.

So how do you handle that?

---

### Post by mo.reina on 2010-05-04
use regular expressions to extract the exact line:
ex. qty=104
then assign it to a variable:
old_text = 'qty=104'

an example
```
echo May 4 04:29:54 item=1847 qty=49 loc=N5 status=avail | sed 's/^.*item=[0-9]*\(.*\)loc.*/\1/'

```
will return:
```
qty=49 
```
i've done most of the work already, it's up to you to figure the rest out.  google up regular expressions and its usage in sed.

---

### Post by LasloHollyfeld on 2010-05-04
> **boondocks said:**
> This will replace predefined text patterns in a file with:

sed 's/oldText/newText/g' before.txt > after.txt

But how do you do that with text patterns that are not predefined.
For instance, if the file contains:

[INDENT]May 4 04:29:54 item=1847 qty=49 loc=N5 status=avail
May 4 04:26:43 item=493 qty=562 loc=S4 status=order
May 4 04:24:21 item=6210 qty=82 loc=E1 status=order
May 4 04:21:41 item=92 qty=127 loc=W2 status=avail
[/INDENT]
And I need to remove all the qty fields:

[INDENT]May 4 04:29:54 item=1847 loc=N5 status=avail
May 4 04:26:43 item=493 loc=S4 status=order
May 4 04:24:21 item=6210 loc=E1 status=order
May 4 04:21:41 item=92 loc=W2 status=avail
[/INDENT]
How do you do that?

In this case, it appears that you want to remove what is always the 5th field, if you break each line into records and use spaces to separate the fields in the records. You could use "cut" to do this, one way would be:

```

cut -f1-4,6 -d' ' before.txt > after.txt

```

the -d' ' tells cut that you use spaces to separate your fields, and -f1-4,6 tells it that you want fields 1 through 4 and then 6 in your output.

You could come up with a sed command that does the same thing using regular expressions, but it'd be more complicated for the same simple effect. Here's an example:
```

sed -e's/\([^ ]* [^ ]* [^ ]* [^ ]*\) [^ ]* \([^ ]*\)/\1 \2/' before.txt >after.txt

```

This isn't a really good pattern, sorry, I'm in a hurry. ;) But it should show the basic idea. I enclose a suitable pattern in \( \) on the left side of the s// substitution command, then I can use the text that matched the pattern in the the replacement part (the right hand side) by referring to it with \1, or \2 (for the second such pattern), and so on.

Hope one of those helps.

---

### Post by Portmanteaufu on 2010-05-04
```

cat original_file.txt |  sed 's/qty=[0-9]\+ //' > new_file.txt

```

Ta-da!

That expression says "Look for the string 'qty=', one or more digits and a space, then replace them all with nothing."

---

### Post by LasloHollyfeld on 2010-05-04
> **Portmanteaufu said:**
> 
That expression says "Look for the string 'qty=', one or more digits and a space, then replace them all with nothing."

Wow, was I tired! Missed the simple approach for the complicated one.

---

### Post by boondocks on 2010-05-04
> **Portmanteaufu said:**
> ```

cat original_file.txt |  sed 's/qty=[0-9]\+ //' > new_file.txt

```

Ta-da!

That expression says "Look for the string 'qty=', one or more digits and a space, then replace them all with nothing."

Yes, this worked out exactly as expected.
Thank you.

---


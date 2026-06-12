---
title: "Transform input text with sed command"
date: 2016-05-04
forum: Programming Talk
---

### Post by CrewDK on 2016-05-04
I'm lost a little :( 
I got input text like 08002738cb55 (it's MAC address without ":" separators). 
Is there any way I can transform this into 08:00:27:38:cb:55 with sed command?

I found one command to transform 123456789 into 123,456,789 with sed 

```
**sed -e :a -e 's/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/;ta'**
```

but i do not understand all triggers and can't find any info about it, so i can't transform this command for myself :(

---

### Post by steeldriver on 2016-05-04
I *think* it's just a matter of

[LIST=1]
[*]changing the [0-9] digit range to POSIX character class [[:xdigit:]] 
[*]changing the multiplicity \{3\} to \{2\} 
[*]changing the separator from comma , to colon : 
[/LIST]

So
```

$ sed -e :a -e 's/\(.*[[:xdigit:]]\)\([[:xdigit:]]\{2\}\)/\1:\2/;ta' <<< "08002738cb55"
08:00:27:38:cb:55

```

---

### Post by CrewDK on 2016-05-05
Thank you. 
I understand that **```
\(.*[[:xdigit:]]\)\([[:xdigit:]]\{2\}\)
``` **is regexp. But what about rest? I mean: 

```
sed -e :a -e 's/......./\1:\2/;ta'
``` 

Can you tell me what is it? Or at least tell me where I can read about this myself?

---

### Post by Bucky Ball on 2016-05-05
*Thread moved to **Programming Talk**.*

Might improve your chances as this is not related to *Desktop Environments*.

---

### Post by The Cog on 2016-05-05
> **CrewDK said:**
> Thank you. 
I understand that **```
\(.*[[:xdigit:]]\)\([[:xdigit:]]\{2\}\)
``` **is regexp. But what about rest? I mean: 

```
sed -e :a -e 's/......./\1:\2/;ta'
``` 

Can you tell me what is it? Or at least tell me where I can read about this myself?

I think I may have it. 
Here's a reference that Google found for me: [https://www.gnu.org/software/sed/manual/sed.txt](https://www.gnu.org/software/sed/manual/sed.txt)
Working through the command, I think...

First there's an expression, label 'a'. This provides a label that the script can jump back to (in a loop):```
-e :a
```
Then there's an expression, and it gives a substitute command.
The fact that 's' is followed by '/' nominates '/' as the separator between parts of the substitute command. There are two parts:```
-e 's/..../..../'
```
The first part is a regular expression. 
Notice there are two groups (in brackets). 
Group 1 will find any string ending in a hex digit. Group 2 will find exactly two hex digits. 
Because group1 is greedy, then overall effect is that it finds the last series of 3 more digits, and will end up with the last two in group 2, and everything preceding that in group 1:
```
\(.*[[:xdigit:]]\)\([[:xdigit:]]\{2\}\)
```
The second part is a replacement pattern. It recalls whatever was found in group1, then has a colon, then recalls the contents of group 2.
```
\1:\2
```
The combination of the above regex  and substitution will put a colon before the last two digits of the last 3 digit sequence. e.g. "08002738cb55" becomes "08002738cb:55".
Following the substitution command is a command separator "**;**" then a command that tells it to go back to label **a** if it made a successful substitution. For a MAC address, it will have to "go back and do it again" a further four times after the first successful substitution. 
```
;ta
```
In summary, it says "Find the last string of 3 hex digits and insert a colon before the last two. If successful then repeat."
I learned a lot answering that question. Interesting stuff.

---

### Post by steeldriver on 2016-05-05
^^^ very good explanation imho

I always find myself going back to Peteris Krumins' [http://www.catonmat.net/blog/sed-one-liners-explained-part-one/](http://www.catonmat.net/blog/sed-one-liners-explained-part-one/) for reference when it comes to sed

FYI, the advantage (for the "thousands separator" case) is that by starting from the RHS of the string, it handles variable length prefixes i.e. 1,234 or 12,345 or 123,456 which you can't achieve by the naive approach of starting from the LHS and working forward.

In the "MAC address" case, we should be able to assume that the (hex) digits always come in pairs, so we CAN use the naive L->R approach, just placing the delimiter every 2 characters -  in its simplest form:

```

sed 's/../&:/g' <<< '08002738cb55'

```

The tricky part is preventing a trailing ':' after the last pair - I can't think of an elegant way to do that in sed. In perl, you could use *negative lookahead* to apply the replacement everywhere except for the end of the string:

```

$ perl -pe 's/..(?!$)/$&:/g' <<< '08002738cb55'
08:00:27:38:cb:55

```

or you could do a "split and join" rather than a "search and replace":

```

$ perl -lne 'print join ":", m/../g' <<< '08002738cb55'
08:00:27:38:cb:55

```

or even (avoiding regular expressions altogether) 
```

$ perl -lne 'print join ":", unpack "(A2)*"' <<< '08002738cb55'
08:00:27:38:cb:55

```

---

### Post by vasa1 on 2016-05-05
I found this:```
echo "08002738cb55" | fold -w2 | paste -sd':' -
08:00:27:38:cb:55
```from [http://unix.stackexchange.com/a/183505](http://unix.stackexchange.com/a/183505)

Again, not a clue of how it does what it does :(

BTW, [another answer there]("http://unix.stackexchange.com/a/5981") uses *sed* but has the trailing ":" that steeldriver mentioned.

---

### Post by The Cog on 2016-05-05
Good point. Without thinking too hard, this does it - just cut the trailing colon off again:
```
sed -e 's/../&:/g' -e 's/\(.*\):$/\1/' <<< "08002738cb55"
```

Nice link.

---

### Post by vasa1 on 2016-05-05
There's so much to learn from this thread!

---

### Post by CrewDK on 2016-05-06
Yeah. Thank you all for realy good answers and explanations!

---

### Post by CrewDK on 2016-05-06
> **vasa1 said:**
> I found this:```
echo "08002738cb55" | fold -w2 | paste -sd':' **-**
08:00:27:38:cb:55
```

BTW, can someone tells me what does last "-" in this command?

---

### Post by vasa1 on 2016-05-06
> **CrewDK said:**
> BTW, can someone tells me what does last "-" in this command?
*man fold* has this:```
      With no FILE, or when FILE is -, read standard input.
```

Edit: I forgot all about the pipe! But, as [matt symes points out]("http://ubuntuforums.org/showthread.php?t=2323318&p=13484566#post13484566"), *man paste* makes the same use of "-".

---

### Post by matt_symes on 2016-05-06
Hi

> **vasa1 said:**
> *man fold* has this:```
      With no FILE, or when FILE is -, read standard input.
```

I think it's the paste command that's reading from standard input, vasa, as it also has that option.

Kind regards

---

### Post by vasa1 on 2016-05-06
> **matt_symes said:**
> ...
I think it's the paste command that's reading from standard input, vasa, as it also has that option.
...
Oops! You're right as usual :)

I'll try and salvage my post.

---


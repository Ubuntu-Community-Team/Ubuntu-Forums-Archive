---
title: "having trouble understanding * in awk"
date: 2014-05-23
forum: Programming Talk
---

### Post by IAMTubby on 2014-05-23
Hello,
 I'm having some trouble understanding what * means in awk. I'm basically confused between these two possible explanations.


_b*l could mean either of these according to me_
Explanation1 : The string starts with b and ends with l. in between b and l you could put any number of characters
Explanation2 : It's b* which means, you could have 0 or more occurrances of b and then l


But when I try cat filename | awk '/b*l/' on a textfile, this is the output I get
```
IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ cat input | awk '/b*l/'
alk  - it doesn't start with b nor does it end with l, how's it printed ?
chalk - it doesn't start with b nor does it end with l, how's it printed ?
bill - this is okay as per Explanation1 but doesn't fit in with Explanation2
cill
biell
l   - this looks like it's closer to Explanation2 which is fine with having 0 occurances of b, but doesn't fit in with Explanation1

```


Please advise.
Thanks

---

### Post by steeldriver on 2014-05-23
AFAIK it means the record ***contains zero or more copies of b***, followed by l - so basically anything containing l

---

### Post by Vaphell on 2014-05-23
awk deals with regexes where * is a quantifier for the preceding thing, that doesn't match anything in itself.
Bash globs on the other hand treat * as a full blown sequence of any length

in other words explanation #2 applies to awk, sed, grep, ... but explanation #1 applies to globs matching files in bash.

---

### Post by IAMTubby on 2014-05-23
> **steeldriver said:**
> AFAIK it means the record ***contains zero or more copies of b ***, followed by l
Thanks steeldriver for the clarification.

> so basically anything containing l
This is where I'm having trouble. b*l ==> 0 or more copies of b followed by l. So that would mean l, bl, bbl, bbbl, bbbbl and so on.
But how can it be valid for "biell"(see my original post). This contain 1 copy of b, not followed by l.

In b*l, we never said that between b and l, you could put anything. For that, perhaps we would have to do b*[COLOR=#ff0000]**.***[/COLOR]l ?

Please advise.
Thanks.

---

### Post by IAMTubby on 2014-05-23
> **Vaphell said:**
> explanation #2 applies to awk, sed, grep, ... but explanation #1 applies to globs matching files in bash.
Thanks Vaphell

> awk deals with regexes where * is a quantifier for the preceding thing, that doesn't match anything in itself.
Okay, so I understand that b* could now mean either 0 occurances of b or more occurances of b
So b*l ==> 0 or more copies of b followed by l. So that would mean l, bl, bbl, bbbl, bbbbl and so on

But how can it be valid for "biell"(see my original post). This contain 1 copy of b, not followed by l.In b*l, we never said that between b and l, you could put anything. For that, perhaps we would have to do b*.*l ?Please advise.

Also, for chalk : you have 0 occurances of b **followed by cha** followed by l **but again followed by 'k'**. How can this be allowed?

Thanks.

---

### Post by steeldriver on 2014-05-23
The awk 'print' action prints the whole record in which the match occurs, rather than the matched expression itself. So any record (by default, record == line, but other record separators are possible) that contains zero or more **b**s followed by an **l** - which is equivalent to any line of input containing the letter **l**

---

### Post by Vaphell on 2014-05-23
if you want to match the whole row, you need to make it explicit, by putting start-of-line/end-of-line symbols there: /^b*l$/ otherwise any non-empty substring fitting the regex satisfies the condition, just like in grep.

---

### Post by IAMTubby on 2014-05-23
> **steeldriver said:**
> The awk 'print' action prints the whole record in which the match occurs, rather than the matched expression itself. So any record (by default, record == line, but other record separators are possible) that contains zero or more **b**s followed by an **l** - which is equivalent to any line of input containing the letter **l**
Thank you steeldriver for that. So basically even if a line is like zzzzzz bl, the entire line gets printed. Verified it.

> **Vaphell said:**
> if you want to match the whole row, you need to make it explicit, by putting start-of-line/end-of-line symbols there: /^b*l$/ otherwise any non-empty substring fitting the regex satisfies the condition, just like in grep.
Vaphell, thank you so much for **/^b*l$/**. That's pretty much I've been trying to get the whole time.
However, I have one last related question.
How do I get alter the awk command above to print only hello**bbl**hello and not hello**bcl**hello ? I want something like, it can contain **b**s but after b it should strictly contain **only l**. Plus it can be anywhere in the middle of the line.

---

### Post by Vaphell on 2014-05-24
/bl/ ?

---

### Post by IAMTubby on 2014-05-24
> **Vaphell said:**
> /bl/ ?
No I meant _0 or more_ occurences of b, followed by a definite l

---

### Post by steeldriver on 2014-05-24
> **IAMTubby said:**
> No I meant _0 or more_ occurences of b, followed by a definite l

*Zero* or more occurrences of ANYTHING followed by THING is just an occurrence of THING. If you mean *one* or more occurrences of b, followed by l, you can use /b**+**l/

```

$ echo -e 'only hellobblhello\nand not hellobclhello' | awk '/b+l/'
only hellobblhello

```

---

### Post by IAMTubby on 2014-05-24
> **steeldriver said:**
> *Zero* or more occurrences of ANYTHING followed by THING is just an occurrence of THING.
Thought about it, yes right.

> ```

$ echo -e 'only hellobblhello\nand not hellobclhello' | awk '/b+l/'
only hellobblhello

```
Yes works.

Thanks steeldriver

---

### Post by Vaphell on 2014-05-24
but of course /bl/ ok's the same lines /b+l/ does, which is why i didn't bother with +
/b+l/ is an equivalent of /b*bl/ which can be reduced to /bl/ without changing the results
(quoting steeldriver: Zero or more occurrences of ANYTHING followed by THING is just an occurrence of THING. -> occurence of 'bl')

```
$ echo $'hellobblhello\nand not hellobclhello' | awk '/bl/'
hellobblhello
```

0-or-more can't work here, because it will just collapse to nothing and will allow anything in front of l.

---


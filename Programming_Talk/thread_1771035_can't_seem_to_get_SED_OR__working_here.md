---
title: "can't seem to get SED OR \| working here"
date: 2011-05-30
forum: Programming Talk
---

### Post by thaitang on 2011-05-30
#I am having some trouble getting this sed oneliner working right:
```
s/\(  \|"\)\([A-Z]\{0,1\}[a-z]\{1,\}ance\|cable\|cy\|ence\|ery\|ious\|mental\|ment\|ness\|sion\|tional\|tion\|tive\)\(  \|,\|'\|"\|;\|:\|.\)/\1<b><font  color="ff0000">\2<\/font><\/b>\3/g
```I want all words ending in any of the first set of 13 OR conditions to match the expr and then have the entire word flanked by HTML bold and font tags as specified, but of course this is not quite occurring yet.

my logic follows that sed should: 
first) look for either a space or " char
second) then for the next char that follows check if it is a single uppercase letter or not, which is optional and ok
third) then at least 1 lowercase char must follow in the expr up to an indefinite (undefined) series of lowercase letters
fourth) the next char that follows, breaking the series of lowercase letters must match 1 of the 13 possibilities separated by the first series of \| OR conditionals
fifth) finally the expr must end with 1 of 7 chars that are again separated by the \| OR conditional; specifically the expr should not be an alphanumeric char (basically either a space or punctuation to mark the end of a word)

Unfortunately my logic is failing here somewhere, because not only are words like "environmental" not matching the expr (but should b/c it begins with a " followed by a series of lowercase letters [environ] followed by the mental in the first set of OR conditions and ending wit a " from the second set of OR condtions, but words like "cycle" are being highlighted, but not the entire word, just the cy part of that word is getting surrounded in the HTML bold and font tags; but this word should even qualify at all because the cy part of the word occurs with lowercase letters that follows (NOT in the second set of OR conditions as a means of avoiding words like this), but if it was a word I wanted to highlight I want the entire word encapsulated in the HTML tags and not just the cy, so I guess sed sees just the cy part of cycle as matching the expr.
I can make it work fine if I remove the first set of OR conditions: ance\|cable\|cy\|ence\|ery\|ious\|mental\|ment\|ness\|sion\|tional\|tion\|tive, and instead create a separate line in my sed file for them such as: 
```
s/\( \|"\)\([A-Za-z][a-z]*ance\)\( \|,\|'\|"\|;\|:\|.\)/\1<b><font color="ff0000">\2<\/font><\/b>\3/g
s/\( \|"\)\([A-Za-z][a-z]*cable\)\( \|,\|'\|"\|;\|:\|.\)/\1<b><font color="ff0000">\2<\/font><\/b>\3/g
```But I would really love to know why this oneliner does not work b/c I cannot see it.

---

### Post by Vaphell on 2011-05-30
do yourself a favor and use sed with -r when you go hardcore with regexes, so you can drop all these \

somewhat simplified but i think it works
code
```
sed -r 's/(\s|")([A-Za-z][a-z]*)(mental|ance|ery|cle)("|\s|,|;|:|.|)/\1<b><font>\2\3<\/font><\/b>\4/g'
```
sample
```
some "environmental" damage
"romance" dance ...
"Fiery"
vicious cycle

```

result
```
some "<b><font>environmental</font></b>" damage
"<b><font>romance</font></b>" <b><font>dance</font></b> ...
"<b><font>Fiery</font></b>"
vicious <b><font>cycle</font></b>
```

---

### Post by epicoder on 2011-05-30
Vaphell's solution looks fine to me, but you might want to drop the <font> tags, as they are deprecated. Use CSS instead.

```
sed -r 's/(\s|")([A-Za-z][a-z]*)(mental|ance|ery|cle)("|\s|,|;|:|.|)/\1<b><span class="red">\2\3<\/span><\/b>\4/g'
```[HTML]<style type="text/css">
.red {color:#FF0000;}
</style>
...[/HTML]

---

### Post by thaitang on 2011-05-31
> do yourself a favor and use sed with -r when you go hardcore with regexes, so you can drop all these \
great, thanks for the tip, much more readable at first glance.

Since first posting yesterday I have since added a few modifications to fine tune what I want to do. So I took what you offered up and modified it to:
```
s/(^|\s|\t|"|<i>)([A-Za-z][a-z]{1,})(ance|cable|cy|ence|ery|ic|ient|ious|ment|ness|sion|tion|tive)(al|ally|d|ed|ily|ly|s{0,1})(\s|,|'|"|;|:|.|<\/i>|$)/\1<b><font color="ff0000">\2\3\4<\/font><\/b>\5/g
```
But for some reason words like everyday, everyone, and now, (with comma) are getting thru and I cannot see why.
```
(al|ally|d|ed|ily|ly|s{0,1})
```
These conditionals are optional after the first OR the end of the word.
 conditionals, one of which is mandatory.

```
(\s|,|'|"|;|:|.|<\/i>|$)
```
It is also mandatory for the word to end with one of these conditionals.

So why, for example, would the word everyone get thru? I see that ERY in evERYone matches ERY in the first set of OR conditions, but the O in everyOne which follows does not match eith of the conditions that follow and thus the word should, I thought, be ignored once SED gets to O in everyOne. If anyone can shed the light I would really appreciate it. this oneliner is just about working as I want.

However, there is a couple of lesser anomalies:
The word appearances if it is on a line by itself without any spaces at the end does not include the s at the end in the font and bold tags (html). appearance is enclosed in bold and font tags but the trailing s is left outside of the tags. Any deas why that might be happening?

Actually another anomaly is occurring due to another oneliner in the same sed file so I will leave that alone for now.

thanks again
tt

---

### Post by Vaphell on 2011-05-31
hint: ```
(\s|,|'|"|;|:|[COLOR="Red"].[/COLOR]|<\/i>|$)
```

```
(\s|$|<\/i>|[.,:;'"])
``` would be more like it

also you could use symbols ? and + for 0-or-1 and 1-or-more instead of {0,1} and {1,} but that doesn't change anything except shortening things a bit.

---


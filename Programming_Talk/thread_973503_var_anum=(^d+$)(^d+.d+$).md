---
title: "var anum=/(^\d+$)|(^\d+\.\d+$)/"
date: 2008-11-06
forum: Programming Talk
---

### Post by zpzpzp on 2008-11-06
Hi

I have read about this javascript code:

function isNumber(x){
var anum=/(^\d+$)|(^\d+\.\d+$)/
if (anum.test(x)) return true else return false
}

It checks whether x is a number. however i do not know how var anum=/(^\d+$)|(^\d+\.\d+$)/ works. Could someone please explain?

Thanks a lot.

Paul

---

### Post by Emill on 2008-11-06
That is called a regular expression. You can also do:
function isNumber(x){
    if (/(^\d+$)|(^\d+\.\d+$)/.test(x)) return true else return false
}

---

### Post by supirman on 2008-11-06
As the above poster said, it's a regular expression.

That's an easy one to decipher.

/(^[COLOR="Red"]\d+[/COLOR]$)[COLOR="Lime"]|[/COLOR](^[COLOR="Red"]\d+\.\d+[/COLOR]$)/

The two in red are the two formats it's searching for.

To decipher it, you need to know some syntax rules (see [this link]("http://en.wikipedia.org/wiki/Regular_expression#Syntax")):

^ matches the beginning of the string
$ matches the end of the string
\d matches a digit
+ means match 1 or more of the preceeding
| means or

So, the first one will match any number of digits, ex:
3
64492923

The second piece matches 1 or more digits, a period, then one or more digits, ex:
23.53
24234234.22223


Hope that helps.

---


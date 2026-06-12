---
title: "[SOLVED] sed reserved characters?"
date: 2008-04-07
forum: Programming Talk
---

### Post by davidpbrown on 2008-04-07
I'm trying to grab URL's from a text file and have found a few suggestions.

One from ietf itself that looks promising is
```
 ^(([^:/?#]+):)?(//([^/?#]*))?([^?#]*)(\?([^#]*))?(#(.*))?
```

but I'm having no luck converting this in a way sed will use - I've tried alsorts.

Can anyone suggest the characters that must be escaped and whether I need to opt for some regex extension, or ssed etc to be able to do regex as complex as that?

Having not used sed before, I had hoped for something simple like just escaping the ()s might work..
```
sed -n -e 's@^\(\([^:/?#]+\):\)?\(//\([^/?#]*\)\)?\([^?#]*\)\(\?\([^#]*\)\)?\(#\(.*\)\)?@\5@p' text
```

---

### Post by ghostdog74 on 2008-04-07
how does your text file with URL's look like?

---

### Post by davidpbrown on 2008-04-08
For now, first step, it's just a list of URL's each on a newline. So ^ should match the start well enough.

Later I might use delimiters to grab from HTML source but having the regex avaliable to grab the different elements is what I'm looking for initially.

I think that \5 should be the domain host for instance..

---

### Post by stroyan on 2008-04-08
It seems that you need to backquote the + and ? quantifiers.
I don't know why that should be necessary.  But it sure helps.
```

$ sed -n -e 's@^\(\([^:/?#]\+\):\)\?\(//\([^/?#]*\)\)\?\([^?#]*\)\(\?\([^#]*\)\)\?\(#\(.*\)\)\?@\5 \6 \7@p' text 

```

---

### Post by davidpbrown on 2008-04-09
Great - Thank you, that works!

For the record then the above gives for a URL, for example
[http://www.ics.uci.edu/pub/ietf/uri/?search#Related](http://www.ics.uci.edu/pub/ietf/uri/?search#Related)
the results in the following subexpression matches:

$1 = http:
$2 = http
$3 = //www.ics.uci.edu
$4 = [www.ics.uci.edu](www.ics.uci.edu)
$5 = /pub/ietf/uri/
$6 = ?
$7 = search
$8 = #Related
$9 = Related

---


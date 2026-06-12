---
title: "bash capture output between two &quot;&quot;"
date: 2011-10-28
forum: Programming Talk
---

### Post by Drenriza on 2011-10-28
Hi all.

I have some output as follows
```
SYSTEM    	"2M Hotel"
```

How can i capture the text between the two "" so the only output i get is 2M Hotel ?

Thanks on advance.
Kind regards.

---

### Post by WasMeHere on 2011-10-28
I think it works if you pipe your output through
```
sed s/.*\ \"//|sed s/\"$//
```

Have fun
Olle

---

### Post by Lars Noodén on 2011-10-28
Another way is to pipe it through [awk](http://manpages.ubuntu.com/manpages/oneiric/en/man1/awk.1posix.html) while setting the Output Field Separator to a double quote (")

```

*yourscript* | awk -F '"' '{print $2}' 

```

-F sets the field separator, $2 is the second column

Obviously there are limitations to this method.

---

### Post by tors on 2011-10-28
Another sed:

```
#> echo 'SYSTEM    "2M Hotel"' | sed "s/.*\"\(.*\)\"/\1/g"
2M Hotel
#>
```

---

### Post by dargaud on 2011-10-28
Another sed, which avoid parentheses:
```
yourscript | sed -e 's/[^"]*"//' -e 's/".*//'
```

---

### Post by Drenriza on 2011-10-28
Thanks for all the suggestions guys. Wish i knew what all those characters in the sed commands ment. But it looks a bit exhausting :) to be honest.

---

### Post by ofnuts on 2011-10-28
> **Drenriza said:**
> Thanks for all the suggestions guys. Wish i knew what all those characters in the sed commands ment. But it looks a bit exhausting :) to be honest.These are "regular expressions" and any programmer worth his salt should know about them.

[http://xkcd.com/208/](http://xkcd.com/208/)

---

### Post by Lars Noodén on 2011-10-29
> **Drenriza said:**
> Thanks for all the suggestions guys. Wish i knew what all those characters in the sed commands ment. But it looks a bit exhausting :) to be honest.

They are not just for programmers, they're essential also to system administration.  

There are lots of sources of material on regular expressions.  For sed you can start here:

  [http://www.gnu.org/software/sed/manual/html_node/Regular-Expressions.html](http://www.gnu.org/software/sed/manual/html_node/Regular-Expressions.html)

[http://www.faqs.org/docs/abs/HTML/regexp.html](http://www.faqs.org/docs/abs/HTML/regexp.html)

---


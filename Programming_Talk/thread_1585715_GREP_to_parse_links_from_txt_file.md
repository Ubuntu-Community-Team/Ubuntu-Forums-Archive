---
title: "GREP to parse links from txt file"
date: 2010-09-30
forum: Programming Talk
---

### Post by JackSparrow11 on 2010-09-30
Hey everyone

I need to search a text file and print all "<a href>" links
i was looking for a grep or sed command to do so.  
Basically i wget -k any website into a file then i search that file for links
I want to get it down to just "http://..........".
I am running into problems where there will always be a few random links
that do not end at the " after the link.  If you guys could help i would appreciate it!


Output:
[http://website.com/randomext/](http://website.com/randomext/)
[http://difwebsite.com/random5t/](http://difwebsite.com/random5t/)
[http://website3.com/rand4t/](http://website3.com/rand4t/)
[http://website6.com/random3/](http://website6.com/random3/)
[http://website.com/rand9/](http://website.com/rand9/)
[http://website4.com/randoext/](http://website4.com/randoext/)

---

### Post by r-senior on 2010-10-01
Interesting coffee-time problem. ;)

I had a go with (my very rusty) awk and this was the best I came up with:

```

# linkPrint.awk
# Print links from <a href> HTML tags

/<[aA].*>/ {
    for (token = 1; token <= NR; token++) {
        if (index($token, "href=\"http") == 1) {
            split($token, components, "\"");
            print components[2];
        }
    }
}

```

To run it (and throw out duplicates):

```
$ awk -f linkPrint.awk index.html  | sort | uniq
```

I don't think that solves the problem because it still looks for links between double-quotes. You might be able to take it further but my coffee-break is finished:

[GNU Awk]("http://www.gnu.org/manual/gawk/gawk.html")

HTML is often unpredictable and I'm thinking that it might need a C/Java/Perl, etc. program to parse the input. (As good as it is, Awk is line-based, as is grep, so the above wouldn't always work if the <a ...> ... </a> was broken across lines for example).

Someone else will probably have a genius solution.

---

### Post by r-senior on 2010-10-01
Subject to the caveat about links split across lines, I think this does it ...

```

$ cat linkPrint.awk 
# linkPrint.awk
# Print links from <a href> HTML tags

/<[aA].*>/ {
    for (token = 1; token <= NR; token++) {
        if (match($token, "href=.*http") == 1) {
            split($token, components, "[=|>]");
            print gensub(/\"/, "", "g", components[2]);
        }
    }
}

$ cat test.html 
<html>
<body>
	<p><a href=http://localhost/test.html>Test</a></p>
	<p><a href="http://localhost/test.html">Test</a></p>
	<p><a href="http://localhost/test.html>Test</a></p>
	<p><a href=http://localhost/test.html">Test</a></p>
</body>

$ awk -f linkPrint.awk test.html 
http://localhost/test.html
http://localhost/test.html
http://localhost/test.html
http://localhost/test.html

```

---

### Post by ghostdog74 on 2010-10-01
```

# cat file
<html>
<body>
        <p><a href=http://localhost/test1.html>Test1</a></p>
        <p><a href="http://

localhost/test2.html">Test2</a></p>
        <p><a href="http://localhost/
test3.html>Test3</a></p>
        <p><a href=http://lo

calhost/test4.html">T

est4</a></p>
</body>


# awk -vRS="</a>" 'RT{ gsub(/.*href=/,"");gsub(/\n+|\042|>.*/,"");print }' file
http://localhost/test1.html
http://localhost/test2.html
http://localhost/test3.html
http://localhost/test4.html


```

---


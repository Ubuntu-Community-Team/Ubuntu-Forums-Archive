---
title: "[SOLVED] Remove lines from a file starting and ending at a particular line"
date: 2008-05-12
forum: Programming Talk
---

### Post by arizonagroovejet on 2008-05-12
Say I have a file that looks like:

```

user_pref("browser.cache.disk.capacity", 1000);
user_pref("browser.search.selectedEngine", "Google");
// begin stuff added by some script or other
pref("network.protocol-handler.app.mailto","/usr/local/bin/mailhandler");
pref("network.protocol-handler.expose.mailto",true);
// end stuff added by some script or other
user_pref("browser.startup.homepage", "http://somewheregood"

```


What's a neat way, preferably using shell scripting rather than perl or ruby or something, to remove those two lines starting with // and anything between them?
I could do it by reading the file a line at a time in a while loop and watching for the relevant 'begin' and 'end' lines but that doesn't seem very elegant. I looked at sed and keywords ( e.g. sed '/start/,/stop/ s/#.*//' ) but can't get that working, possibly because the keywords need to contain spaces and possibly because of the // characters (though I did try using : instead of / for the delimiter character).

---

### Post by WW on 2008-05-12
```

sed '/^\/\//,/^\/\// d' filename > newfilename

```
It worked on a simple example; test it yourself to be sure.  If it works the way you want it to, you can use this version to edit the file in place:
```

sed -i~ '/^\/\//,/^\/\// d' filename

```
That version changes the file in place, and makes a backup called filename~.

---

### Post by arizonagroovejet on 2008-05-12
> **WW said:**
> ```

sed '/^\/\//,/^\/\// d' filename > newfilename

```

That would match any line starting // which is no good if there are other comments in the file. Since I cannot guarantee there won't be other comments in the file I need to match the whole line. But your suggestion can be easily expanded to do that However that still doesn't solve my entire problem, and here's the bit where I kick myself for not explaining exactly what I'm trying to do.

What if the matches are contained in variables. E.g. where foo is the afore described file and boo is the file from which the changes were original obtained:

```

set -x
first=`head -1 boo`
second=`tail -1 boo`
echo "first $first"
echo "second $second."
sed "^$first::,:^$second:: d" foo
```

Using : rather than / in sed expression rather than to avoid "sed: -e expression #1, char 4: unknown command: `/'" error and because I can't figure out how to stop that no matter how much I try and escape the / characters in the variables before using them.

When run produces

```
++ head -1 boo
+ first='//begin bits added by some script or other'
++ tail -1 boo
+ second='//end bits added by some script or other'
+ echo //begin bits added by some script or other
first //begin bits added by some script or other
+ echo //end bits added by some script or other
second //end bits added by some script or other
+ sed ':^//begin bits added by some script or other::,:^//end bits added by some script or other:: d' foo
sed: can't find label for jump to `its'

```

Which stumps me completely.

---

### Post by WW on 2008-05-12
Oh, that's a bit different. :)
Here's a version that you can experiment with.  It uses bash parameter expansion to "escape" any backslashes in the delimiting comments.
```

set -x
first=`head -1 boo`
second=`tail -1 boo`
p=${first//\//\\\/}
q=${second//\//\\\/}
sed "/^$p/,/^$q/ d" foo

```
p and q are copies of first and second, respectively, with each occurrence of / replaced by \/.

---

### Post by ghostdog74 on 2008-05-13
if you know the specific begin and end pattern
```

awk '/^\/\/ begin/,/^\/\/ end/ {next}1' file

```
output
```

# ./test.sh
user_pref("browser.cache.disk.capacity", 1000);
user_pref("browser.search.selectedEngine", "Google");
user_pref("browser.startup.homepage", "http://somewheregood"


```

---

### Post by arizonagroovejet on 2008-05-13
> **WW said:**
> Oh, that's a bit different. :)
Here's a version that you can experiment with.  It uses bash parameter expansion to "escape" any backslashes in the delimiting comments.
```

set -x
first=`head -1 boo`
second=`tail -1 boo`
p=${first//\//\\\/}
q=${second//\//\\\/}
sed "/^$p/,/^$q/ d" foo

```
p and q are copies of first and second, respectively, with each occurrence of / replaced by \/.

That does exactly what I want thanks. I'll have to look in to that expression thing you're using to assign values to p and q. I was trying to do the same thing with sed and getting nowhere.

---

### Post by arizonagroovejet on 2008-05-13
> **ghostdog74 said:**
> if you know the specific begin and end pattern
```

awk '/^\/\/ begin/,/^\/\/ end/ {next}1' file

```


Not used awk for a while. Thanks for the suggestion.

---


---
title: "problem with shell var in sed command"
date: 2012-10-31
forum: Programming Talk
---

### Post by thaitang on 2012-10-31
Often need to download multiple pages from same site. Want to streamline the process with the following script, but getting an error with this line:
```
#sed -ri 's/^http_/'"$url"'/' lkpg
```
The idea is I save a page with all the links to the multiple pages I want. then I modify the saved page to extract the desired links, all of which works fine and so needs little attention. It seems the problem is inserting the var $1 that is entered at the time the script is run. I have used var in sed this way before and I am not sure why I cannot get this to work as desired.

command entered is: $./wgetSpark.sh "http://www.sparknotes.com/philosophy/meditations/"

I know the the shell handles the var fine because I can insert the it fine with:
```
sed -ri '1i\'"$url"'' lkpg
```

so the problem has to be a sed issue; but like I said the above sed command works too, so I do not know why the previous one does not.

here is the script in context:
```
#!/bin/bash

url=$1

let cntr=1
while [ "$cntr" -lt 31 ] ; do
	sed -ri '/$/N;s/\n/ /' lkpg
	((cntr++))
done
sed -ri 's/[ ]{2,}/ /g' lkpg
sed -ri 's/[ ]{0,}<br>[ ]{0,}/<br>/g' lkpg
sed -ri 's/[ ]{0,}<p/<p/g' lkpg
sed -ri 's/[ ]{0,}<\/p>[ ]{0,}/<\/p>/g' lkpg

perl -pi -e 's/^.*?<h3.*?Table of Contents.*?<\/h3>//' lkpg
perl -pi -e 's/How to Cite This SparkNote<\/a>.*$//' lkpg

echo "url: $url"
sed -ri 's/<a href="/\n'"$url"'/g' lkpg
#sed -ri '/^http:/!d' lkpg
#sed -ri 's/^http_/'"$url"'/' lkpg
sed -ri '/^http:/!d' lkpg
sed -ri 's/">/\t/' lkpg
sed -r 's/\t.*$//' lkpg>1.sh
sed -ri 's/^(http.*)$/wget \-nc \-\-random\-wait \-\-user\-agent="Mozilla\/5\.0 \(X11\; U\; Linux i686\; en\-US\; rv\:1\.9\.0\.3\) Gecko\/2008092416 Firefox\/3\.0\.3" \1/' 1.sh
sed -ri '1i\#!\/bin\/sh' 1.sh
chmod +x 1.sh
#./1.sh

```

any ideas/suggs would be appreciated

---

### Post by ju2wheels on 2012-10-31
Try the following:

```

#sed -ri "s|^http_|${url}|" lkpg

```

---

### Post by thaitang on 2012-11-01
> **ju2wheels said:**
> Try the following:

```

#sed -ri "s|^http_|${url}|" lkpg

```

gonna be honest, it didn't occur to me to alter the delimiter and when i read the suggestion i didn't think it could be the problem. but after giving it a whirl it worked! awesome! why though?

btw i entered the wrong line I was having issues with...
```
sed -ri 's/<a href="/\n'"$url"'/g' lkpg
```
that's the one, edited to:
```
sed -ri "s|<a href=.|\n$url|g" lkpg
```
the fix worked regardless.

still, why though? I messed with different quote patterns, trying perl instead but nothing seemed to work.

cheers, gonna save me a load of messing around

---

### Post by ju2wheels on 2012-11-01
The problem was a combination of incorrect quoting and not escaping characters in the URL variable before substituting it into the regex.

Consider this:

```

url="http://www.yahoo.com/"
sed -ri 's/<a href="/\n'"$url"'/g' lkpg

```

The first problem here is the crazy mix of quoting, normally single quoted strings arent used or dont allow interpolation (but it varies by language, in the case of bash it wont interpolate iirc).

So to reduce issues just turn it into a double quoted interpolated string and remember to properly escape characters that need to be escaped for the regex to work ([http://www.regular-expressions.info/reference.html](http://www.regular-expressions.info/reference.html) see the second row of the table).

The problem you have if you use / as the regex separator is that this character is also in the http url, so once you substitute it into the regex (without first escaping it) then the regex engine thinks you terminated your regex expression early and sees all this garabage after it. So in order to use / as the regex separator, you have to escape the string so it looks like this (I havent tried it but you may need to double escape the \ as well, which is why this way is more difficult):

```

url='http:\/\/www.yahoo.com\/'; 

```

---


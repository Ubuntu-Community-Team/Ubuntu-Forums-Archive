---
title: "Regular expression for capturing repeated patterns"
date: 2007-07-18
forum: Programming Talk
---

### Post by abhijeetmaharana on 2007-07-18
Does anyone have a regular expression for capturing package names from strings of the type
```

Not installed: please install libnss-dev: usr/lib/pkgconfig/mozilla-nss.pc mozilla-dev: usr/lib/pkgconfig/mozilla-nss.pc

```
The regex should capture "libnss-dev" and "mozilla-dev" from the above string.

Currently I am using
```

(\S*): usr\S* 

```
It gets me libnss-dev. But I am unable to repeat this pattern so that all such occurrences are captured. The information at [http://www.regular-expressions.info/captureall.html](http://www.regular-expressions.info/captureall.html) seems to be helpful but I am unable to apply it here.

(This question is from [http://ubuntuforums.org/showthread.php?p=3040432#post3040432](http://ubuntuforums.org/showthread.php?p=3040432#post3040432))

---

### Post by Mr. C. on 2007-07-18
Which RE program are you using ?

MrC

---

### Post by abhijeetmaharana on 2007-07-22
I am using Java (1.5 / 1.6). 
```

import java.util.regex.MatchResult;

...

String tempString = "Not installed: ......";  // full string from above
Scanner sc = new Scanner(tempString);

// Double \ to escape \ required in the regex
sc.findInLine("Not installed: please install (\\S*): usr\\S*");
MatchResult result = sc.match();

// See how many groups have been captured
System.out.println(result.groupCount());

// Print one of them
System.out.println(result.group(1));

```

I tried using kregexpeditor from the repository but I can't seem to get hold of the matched groups (if it supports them).

---

### Post by slavik on 2007-07-22
in perl you'd be looking for global. in java, try matching it repeatedly and see if you get what you want (while result.groupCount() > 0)

---

### Post by abhijeetmaharana on 2007-07-22
I am trying to do just that. The problem is, I am looking for a regex string which will give me more than one group. And each group will be a library name extracted from the big string.

> 
try matching it repeatedly and see if you get what you want (while result.groupCount() > 0)

Not sure what you mean. 

```

for(int i=0; i<=result.groupCount(); ++i)
	System.out.println(result.group(i));

```
yields
Not installed: please install libnss-dev: usr/lib/pkgconfig/mozilla-nss.pc
libnss-dev

What I want is another group which is mozilla-dev and so on if more are present.

---

### Post by slavik on 2007-07-22
here's what it would look like in perl:

/\s(.*?):/g

that g flag will repeat a match and give back a list :)

---


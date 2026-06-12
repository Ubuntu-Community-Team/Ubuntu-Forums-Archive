---
title: "Java Regular Expressions"
date: 2010-09-07
forum: Programming Talk
---

### Post by firefly2442 on 2010-09-07
I have the following code and I'm trying to identify matches in the line based on the regular expression.  The problem I am having is it correctly bypasses the lines starting with comments but incorrectly passes by the ones that should match.  Is there something I'm missing?  Thanks.

```

Input:

//These shouldn't match because they are commented
//#include "no.sqf"
//execvm "no.sqf";

//These should match
#include "yes.sqf"
execvm "yes.sqf";

```

```

//Cleanup string, makes it easier to do regex
line = line.trim();
line = line.toLowerCase();
line = line.replace(";", "");


if (line.matches("[^/]{2}" + //Don't start with comment
	".*?" + //Zero or more characters of any type
	"(\\#include|execvm)" + //String literal (match any one)
	"\\s*?" + //Zero or more whitespace characters (account for space)
	"(\"|\')" + //String literal for quotation (single or double quote)
	".*?" + //Zero or more characters for the path/filename
	"(.sqf|.sqs)" + //String literal (any one of these extensions)
	"(\"|\')" + //String literal for quotation (single or double quote)
	".*?")) //Zero or more characters of any type
{
//There's a match!
}

```

---

### Post by trent.josephsen on 2010-09-07
Look a little closer at the first section -- that [^/]{2} matches the first two characters of any line that doesn't start with //, and the regex goes on to try to match the rest of the line to the rest of the pattern.  Try matching a line like "xx#include[...]".

---

### Post by Reiger on 2010-09-07
You are trying to read every line that is not prefixed with “//” ?
Why not use:
```

// code 

String cleaned, line;
//code to obtain value for line...

cleaned = line.trim();
if(! cleaned.startsWith("//")) {
   // we have a match! process line here?
}

// code

```

---

### Post by firefly2442 on 2010-09-07
Yep, I guess I can just use that startsWith method.  I was just thinking it would be really handy to have everything inside the regular expression but this is probably the easiest solution.

edit: The only thing I can think of when this wouldn't work is if you had something like the following:

```

Input:

#include "yes.sqf"; //#include "no.sqf";

```

Since the comment is after the valid include, both would be read as matches by the regular expression.

---

### Post by Some Penguin on 2010-09-07
I'd be inclined to preprocess ala

```

int commentIndex = line.indexOf("//");
if (commentIndex != -1) {
  line = line.substring(0, commentIndex);
}

```

before hitting the regex.  Use a new String variable if you'd rather keep the original reference, but in that case be sure to set it to the original if commentIndex is indeed -1.

---

### Post by firefly2442 on 2010-09-07
Wow too funny, yeah I ended up doing just that.  Now I just have to figure out how to deal with block comments.:-k

```

/* */

```

---

### Post by Reiger on 2010-09-07
Well they fit the same logic quite nicely. All you have to add is some state to track a previously opened comment.

In pseudo code:
```

if parser marked as block comment:
  skip until block comment closes
  if remainder is not empty:
     reset parser
     recurse on remainder
else:
  read until comment
  process text before comment
  if remainder is not empty and comment is a block:
     mark parser as block comment

```

---


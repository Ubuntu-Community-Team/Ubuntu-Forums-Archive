---
title: "Spaces in directory name"
date: 2007-12-27
forum: Programming Talk
---

### Post by amorangi on 2007-12-27
I'm writing a nautilus script to get the bottom level of the current directory and create it on another branch. It works fine, except it puts %20 in instead of spaces. 
This is what I have:
```

cd $NAUTILUS_SCRIPT_CURRENT_URI
CDNAME=$(basename $NAUTILUS_SCRIPT_CURRENT_URI)
BASEDIRNAME="/somewhere/else/"
mkdir $BASEDIRNAME$CDNAME

```

If I'm in directory "/the/first/place with spaces" I then get "/somewhere/else/place%20with%20%20spaces" created as the result. I realise %20 is meant to be a space, but I don't think its right on this occasion. Is there a way around this?

---

### Post by LaRoza on 2007-12-27
Don't use spaces in file names.

%20 is the only way to represent white space, which would be ignored.

-EDIT, you can use \ to escape spaces in the shell post three reminded me.

---

### Post by lamalex on 2007-12-27
I know little of nautilus scripts, but can you replace the %20 with a \ as an escape character?

---

### Post by jken146 on 2007-12-27
You should put filenames with special characters in single quotes.  This escapes everything.  Double quotes will escape some characters but not others.

---

### Post by ghostdog74 on 2007-12-27
> **amorangi said:**
> 

If I'm in directory "/the/first/place with spaces" I then get "/somewhere/else/place%20with%20%20spaces" created as the result. I realise %20 is meant to be a space, but I don't think its right on this occasion. Is there a way around this?

```

mkdir "$BASEDIRNAME$CDNAME"

```

---

### Post by engla on 2007-12-28
Honestly, all previos posters seem to miss the point -- _$NAUTILUS_SCRIPT_CURRENT_URI_ is a URL, not a path, and thus it is URL-encoded, without space characters. We need to convert this to the usual path encoding to proceed with other (path-based) command line tools (like basename). And yes, of course things should allow spaces..

I can't think of any command line tool converting uris to paths off hand (perhaps there is some) but you can do it with python, here is an untested example:

```
import gnomevfs
import sys

"""
Usage: ./topath.py <URL>
"""

if __name__ == "__main__":
	url = sys.argv[1]
	print gnomevfs.get_local_path_from_uri(url)
```

---

### Post by ghostdog74 on 2007-12-28
if that's the case, a simple substitute might be worth a try
```

# echo $NAUTILUS_SCRIPT_CURRENT_URI | sed 's/%20/ /g'
/somewhere/else/place with  spaces

```

---

### Post by geirha on 2007-12-28
or use $PWD instead of $NAUTILUS_SCRIPT_CURRENT_URI

---

### Post by engla on 2007-12-28
> **ghostdog74 said:**
> if that's the case, a simple substitute might be worth a try
```

# echo $NAUTILUS_SCRIPT_CURRENT_URI | sed 's/%20/ /g'
/somewhere/else/place with  spaces

```

Paths are in unicode and URLs are in ASCII; there are lots of more characters than space that could be encoded. So this won't work generally for all possible file names, not even all of those representable in latin-1.

---


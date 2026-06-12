---
title: "How to force mktemp to be quiet (bash)?"
date: 2010-10-18
forum: Programming Talk
---

### Post by shaggy999 on 2010-10-18
I'm writing a bash script that involves making a temporary directory. When I make the directory I need to catch the output. The following method is simple enough:

```

TMPDIR=`mktemp -d`

```

The problem is that it still spits out the directory to stderr even if I add the -q option. For the purposes of my script it needs to be absolutely silent. The problem is I can't seem to figure out a way to redirect stderr in this fashion.

What I want to do is basically this:

```

TMPDIR=`mktemp -q -d &> /dev/null`

```

Obviously, that command doesn't work. I have tried the following:

[code]
TMPDIR=`mktemp -q -d` 2> /dev/null
TMPDIR=`mktemp -q -d 2\> /dev/null`
TMPDIR=$(mktemp -q -d 2\> /dev/null)
[code]

... and about a dozen other variations. Why can I not get this to work?

---

### Post by dwhitney67 on 2010-10-18
It would be helpful if you would explain what error you are getting when your script executes the mktemp command.

The following works on my system, without any complaint (ie errors):
```

#!/bin/bash

TMPDIR=`mktemp -d`

echo "My temp directory is: $TMPDIR"

```

---

### Post by AndyCee on 2010-10-18
This one seems to work for me -

If I force an error:
```
TMPDIR=`mktemp --tmpdir=/home/zaphod`
mktemp: failed to create file via template `/home/zaphod/tmp.XXXXXXXXXX': No such file or directory
```

It disappears with:
```
TMPDIR=`mktemp -d --tmpdir=/home/zaphod 2>/dev/null`
```

Does this help?

---

### Post by shaggy999 on 2010-10-18
> **AndyCee said:**
> This one seems to work for me -

If I force an error:
```
TMPDIR=`mktemp --tmpdir=/home/zaphod`
mktemp: failed to create file via template `/home/zaphod/tmp.XXXXXXXXXX': No such file or directory
```

It disappears with:
```
TMPDIR=`mktemp -d --tmpdir=/home/zaphod 2>/dev/null`
```

Does this help?

I don't know why it didn't work last night, but it works this morning. Thanks.

---


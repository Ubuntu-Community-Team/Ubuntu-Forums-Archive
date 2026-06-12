---
title: "Bash filenames with spaces"
date: 2011-08-19
forum: Programming Talk
---

### Post by kerryhall on 2011-08-19
I searched for similar issues but everything I could find was a different case than mine.

I want to assign a path with spaces to a variable in Bash like so

$FILENAME="/path/to/file\ with\ spaces"

but it doesn't seem to work. Any ideas? Thanks!!

---

### Post by sisco311 on 2011-08-19
I rarely have to say this, but you use too many quotes. :) 

```

FILENAME="/path/to/file with spaces"
FILENAME='/path/to/file with spaces'
FILENAME=/path/to/file\ with\ spaces

```

Check out:
```
man bash | less +/^QUOTING
```

EDIT: and [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

### Post by Smart Viking on 2011-08-19
You assign without the dollar:
```
FILENAME="/path/to/file\ with\ spaces"
echo $FILENAME
```

---

### Post by ofnuts on 2011-08-19
And don't forget to use "$FILENAME" about everywhere else...

---

### Post by Habitual on 2011-08-21
> **sisco311 said:**
> Check out:
```
man bash | less +/^QUOTING
```

is SEXY!

Thanks!

---


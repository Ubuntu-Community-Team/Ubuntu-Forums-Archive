---
title: "Bash regex matching &quot;.&quot; in a character range"
date: 2010-01-23
forum: Programming Talk
---

### Post by botfish on 2010-01-23
I am writing the following bash scrip to convert geographic coordinates in degrees minutes seconds to decimal degrees.

How do I include a period "." in a character range?

I am trying to match 86.12 with the pattern ([0-9.]*)

```

#!/bin/bash
# Convert geographic coordinates in degrees minutes seconds to decimal degrees

DMS="38 deg 56' 86.12\" N"
REGEX="^([0-9]{1,2}) deg ([0-9]{1,2})' ([0-9.]*)\" ([NSWE]){1}$"

echo "$DMS"
echo "$REGEX"

if [[ "$DMS" =~ $REGEX ]]; then

	DEGREES="${BASH_REMATCH[1]}"
	MINUTES="${BASH_REMATCH[2]}"
	SECONDS="${BASH_REMATCH[3]}"
	REF="${BASH_REMATCH[4]}"

	echo "$DEGREES"
	echo "$MINUTES"
	echo "$SECONDS"
	echo "$REF"

	# Mathamatical conversion takes place here

else
	echo "Error converting DMS to Decimal degrees" >&2
	exit 1
fi

exit

```

---

### Post by Reiger on 2010-01-23
To match a dot (.) literally you need to escape it within the regular expression using a backslash. But your regular expression has some issues; compare it with the pattern in this example to see what I mean:
```

regex="^[a-z]+(\.[a-z]+)?$"; 
echo $regex; 
if [[ "dot.all" =~ $regex ]]; 
then 
  echo "dot.all"; 
fi;

```

---

### Post by jpkotta on 2010-01-24
> **Reiger said:**
> To match a dot (.) literally you need to escape it within the regular expression using a backslash. But your regular expression has some issues; compare it with the pattern in this example to see what I mean:
```

regex="^[a-z]+(\.[a-z]+)?$"; 
echo $regex; 
if [[ "dot.all" =~ $regex ]]; 
then 
  echo "dot.all"; 
fi;

```

Inside a character set (i.e. inside square brackets []), dot is just a literal, and no longer means "any single character".  IOW, there is no need to escape dot inside brackets.  But as you point out, OP probably doesn't want it in that character set anyway.

---


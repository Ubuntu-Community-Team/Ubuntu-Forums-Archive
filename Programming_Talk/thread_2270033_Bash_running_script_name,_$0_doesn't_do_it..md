---
title: "Bash running script name, $0 doesn't do it."
date: 2015-03-19
forum: Programming Talk
---

### Post by 1clue on 2015-03-19
Hi,

I'm trying to get the running script name when the script is 'sourced'.

For example, in my .bashrc:

```

# Pull in mystuff profile
 [[ -s "/path/to/mystuff/profile" ]] && source "/path/to/mystuff/profile"

```

That profile has:

```

#!/bin/bash
# This is the first file in MYSTUFF.  It needs to be non-versioned so it can be modified to the system.

if [ -n "$MYSTUFF_LOG" ]; then
    echo "Entering $0"
fi


export MYSTUFF_LOG=1
#unset MYSTUFF_LOG


export MYSTUFF_HOME=/usr/local/mystuff
export MYSTUFF_LOCAL_ETC=/etc/mystuff


# Go set it all up.
[[ -s "$MYSTUFF_HOME/etc/profile" ]] && source "$MYSTUFF_HOME/etc/profile"


if [ -n "$MYSTUFF_LOG" ]; then
	    echo "Leaving $0"
fi



```

When I login, it prints "Entering bash" and "Leaving bash" rather than the fully qualified filename.

Does anyone know how to do this?

Thanks.

---

### Post by ofnuts on 2015-03-19
See the [BASH_SOURCE](https://www.gnu.org/software/bash/manual/html_node/Bash-Variables.html) variable.

---

### Post by 1clue on 2015-03-19
Excellent, that works perfectly!  Thanks!

---


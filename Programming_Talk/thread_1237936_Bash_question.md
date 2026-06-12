---
title: "Bash question"
date: 2009-08-11
forum: Programming Talk
---

### Post by oomar on 2009-08-11
Im just starting to learn how to program bash and recently just wrote a completely random script and cant seem to figure out why its coming up with errors. Ive changed it several times and probably screwed it up more but please take a look and see if you can spot my problems.

```

#!/bin/bash
$var = "thing"
while var == "thing"; do
	echo "test"
	read testvar
	if $testvar == "exit"; then
	exit 0
	fi
        echo "You wrote " + $testvar
done
sleep 10
```

just a random program.

---

### Post by enz1m3 on 2009-08-13
Your variable declaration is badly done, aswell as the loop syntax, if syntax, etc.

Check, this is tested and working.

```

#!/bin/bash
thevar="thing"
while [ $thevar == "thing" ]; do
        echo "test"
        read testvar
        if [ $testvar == "exit" ]; then
        exit 0
        fi
        echo "You wrote " + $testvar
done
sleep 10

```

---


---
title: "bash script issue"
date: 2010-07-12
forum: Programming Talk
---

### Post by chris200x9 on 2010-07-12
Hi right now I am trying to have a shell script ssh into a machine using the local ip from a router, if that fails it uses the external ip. How in my shell script can I test if ssh fails? I tried cat ssh user@localip > out.txt then I was going to check if there was an error message in out.txt via grep, but nothing was written to out.txt.

---

### Post by dwhitney67 on 2010-07-12
```

#!/bin/bash

ssh user@localip

if [ $? -ne 0 ]
then
        # failure w/ ssh
        ssh user@remoteip
else
        #whatever
fi

```

---

### Post by chris200x9 on 2010-07-12
thank you!

---

### Post by geirha on 2010-07-13
Checking $? for true or false is pointless though. Just check the exit code of the command directly.
```
if ssh user@localip ...; then
  # whatever
else
  ssh user@externalip ...
fi

# or with negation
if ! ssh user@localip ...; then
  ssh user@externalip ...
fi

```

You could also check if the ssh port is open first.
```

if nc -w1 -z localip 22; then
  ssh user@localip ...
elif nc -w1 -z externalip 22; then
  ssh user@externalip ...
else
  echo bailing out
fi

```

---


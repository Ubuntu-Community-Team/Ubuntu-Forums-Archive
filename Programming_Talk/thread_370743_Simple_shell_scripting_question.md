---
title: "Simple shell scripting question"
date: 2007-02-26
forum: Programming Talk
---

### Post by mahy on 2007-02-26
Hi y'all i wanna make Opera start without the tray icon by default. This is my perception:

mv /usr/bin/opera /usr/bin/opera-mod

and then create another file named /usr/bin/opera looking like this:

```
#! /bin/bash

/usr/bin/opera-mod -notrayicon
```

This simple solution has one drawback, however. If i start Opera like this: "opera www.google.com", the URL is discarded. How do i have to modify the script to pass all arguments PLUS the -notrayicon option? TIA for any help.

---

### Post by Tomosaur on 2007-02-26
Use this script instead:
```

#!/bin/bash

/usr/bin/opera-mod $@ -notrayicon

```

The $@ means "all arguments".

---

### Post by louis_nichols on 2007-02-26
My bash scripting is not very good, but it would be something like this:
```
#! /bin/bash

/usr/bin/opera-mod -notrayicon $*
```
Or, if you only want to open the first address, use: ```
#! /bin/bash

/usr/bin/opera-mod -notrayicon $1
```

So $1 is the first argument, $2 is the second and so on. $* stands for all arguments.

---

### Post by Tomosaur on 2007-02-26
Opera takes the URL before the arguments. If you do it the other way around it won't work properly.

---

### Post by kaamos on 2007-02-26
It would be easier to just modify /usr/bin/opera by changing the last line from
```

exec "${OPERA_BINARYDIR}opera" "$@"

```
to
```

exec "${OPERA_BINARYDIR}opera" "$@" -notrayicon

```

---

### Post by geakMonkey on 2007-02-26
This should be an easy one: why am  getting this error?

bash: alias: la: not found
bash: alias: ls -a: not found


I uncommented these lines in the .bashrc:

# some more ls aliases
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'

I only uncommented the standared installed .bashrc, what do I need to edit here?

Thanks

---

### Post by mahy on 2007-02-26
> **kaamos said:**
> It would be easier to just modify /usr/bin/opera by changing the last line from
```

exec "${OPERA_BINARYDIR}opera" "$@"

```
to
```

exec "${OPERA_BINARYDIR}opera" "$@" -notrayicon

```

wow, this is even better. it works. THX!

---

### Post by mahy on 2007-02-26
> **geakMonkey said:**
> This should be an easy one: why am  getting this error?

bash: alias: la: not found
bash: alias: ls -a: not found


I uncommented these lines in the .bashrc:

# some more ls aliases
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'

I only uncommented the standared installed .bashrc, what do I need to edit here?

Thanks

The error messages seem weird. It should look like

bash: la: command not found

However, try to start your own thread next time :)

---


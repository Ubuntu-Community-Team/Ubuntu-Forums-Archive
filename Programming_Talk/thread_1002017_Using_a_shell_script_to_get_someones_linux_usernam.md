---
title: "Using a shell script to get someones linux username?"
date: 2008-12-04
forum: Programming Talk
---

### Post by Johnsie on 2008-12-04
Hi, I'm trying to write a shell script that copies a file to:

>  ~/.wine/drive_c/windows/profiles/<USERNAME>/Application Data/test


I can use ~ to get to the users home dir no problem, but I need to find out their username so that I know which subfolder to place the file into.

Thanks if anyone can help

---

### Post by sisco311 on 2008-12-04
> ~/.wine/drive_c/windows/profiles/**$USER**/Application Data/test

you can use the $USER [environment variable]("https://help.ubuntu.com/community/EnvironmentVariables")

---

### Post by stroyan on 2008-12-04
You can use "$LOGNAME" or "$USER".  They are documented in "man login" and "man environ".

---

### Post by DieB on 2008-12-04
take the printout of whoami put it in a variable and use that instead of USERNAME, above mentioned ways would work better

---

### Post by Johnsie on 2008-12-04
thanks that great :-)

---

### Post by stefanadelbert on 2008-12-04
You could use

```

id -nu

```

Par example
```

#!/bin/bash

echo "Your home directory is: /home/$(id -nu)"

exit 0

```

Stef

---


---
title: "where is the file?"
date: 2012-08-30
forum: Programming Talk
---

### Post by vanangamudi on 2012-08-30
code is ompiling and executing with no problem. but i cannot find a file named "data.dat" in my home directory. where else could it be??
```

#include<stdio.h>

int main()
{

  FILE* fd = fopen("~/data.dat","w");

  fprintf(fd,"he he some text;;;;;;;;;;;;\n");
  fclose(fd);

  return 0;

}

```

---

### Post by greenpeace on 2012-08-30
Are you running it as yourself?

You can always try these terminal commands to locate the file:
```
sudo updatedb 
locate data.dat
```

that should give you the location of the file.

---

### Post by MG&amp;TL on 2012-08-30
> **vanangamudi said:**
> code is ompiling and executing with no problem. but i cannot find a file named "data.dat" in my home directory. where else could it be??
```

#include<stdio.h>

int main()
{

  FILE* fd = fopen("~/data.dat","w");

  fprintf(fd,"he he some text;;;;;;;;;;;;\n");
  fclose(fd);

  return 0;

}

```

"~/" is a shell shortcut. E.g. it only works in your shell. 

If you want to do that, you can either use "/home/someuser", or if you want the home directory for any user, use getenv("HOME") from <stdlib.h>

---

### Post by vanangamudi on 2012-08-30
> **MG&TL said:**
> "~/" is a shell shortcut. E.g. it only works in your shell. 

If you want to do that, you can either use "/home/someuser", or if you want the home directory for any user, use getenv("HOME") from <stdlib.h>

good lord... i forgot something....

---


---
title: "copyright file in debian folder"
date: 2011-11-24
forum: Packaging and Compiling Programs
---

### Post by San_SS! on 2011-11-24
I'm packaging a program that I've written which is licensed under GPLv3 and above. It contains the files of the python chardet library which is licensed under GPLv2 and above, so there's no conflict about it, right?

My question is: in the copyright file of the package, is it compulsory to include the copyright for the chardet authors? if it is, where in the file should that go?

---

### Post by Bachstelze on 2011-11-24
> **San_SS! said:**
> I'm packaging a program that I've written which is licensed under GPLv3 and above. It contains the files of the python chardet library which is licensed under GPLv2 and above, so there's no conflict about it, right?

Right, you are just releasing everything under the GPLv3 (and above).

> My question is: in the copyright file of the package, is it compulsory to include the copyright for the chardet authors? if it is, where in the file should that go?

Yes. You can put it in the 'Copyright' section. Make sure to also clearly state which files fall under which copyright (yours or chardet's).

---

### Post by San_SS! on 2011-11-29
Thanks for the answer.

I put it like this:
```

Copyright:

    All files except the ones located in chardet folder:
    Copyright (C) 2011 Santiago Alessandri and Matias Fontanini

    Files located in chardet folder:
    Copyright (C) 2006, 2007, 2008 Mark Pilgrim

```

is it ok?

---

### Post by Bachstelze on 2011-11-29
This is OK, you can also state that the chardet files are GPLv2 and above. Not sure if it is required, but better be safe than sorry.

---


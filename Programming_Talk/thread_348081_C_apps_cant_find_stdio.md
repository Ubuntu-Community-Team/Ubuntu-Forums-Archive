---
title: "C apps cant find stdio"
date: 2007-01-28
forum: Programming Talk
---

### Post by k_smolka on 2007-01-28
Hi all

I have a number of small c apps that print out simple data to the terminal.

I have written and run a simple hello world example but no data is appearing in the standard out put in the terminal. 

When I compile these apps no warning are given. However inside my IDE it is saying that it is unable to locate #include <stdio.h> or #include <stdlib.h>

I have build essential installed and all apps compile and link ok. Does anyone know why data is not appearing in the terminal or how to locate these files.

Regards 

Karl

---

### Post by Tomosaur on 2007-01-28
Strange. Have you tried using this instead:
```

#include "stdio.h"
#include "stdlib.h"

```

I have used an IDE in the past where it claimed it could not find includes when I used the < > characters, but worked when I used quotation marks. Very strange behaviour. The programs always actually worked though, but this could be worth a try. Which compiler does the IDE use?

---

### Post by highneko on 2007-01-28
Doesn't using quotes around includes like that check the current directory? And using the greater than and less than things around the includes checks the programs paths or something?

---

### Post by k_smolka on 2007-01-28
> **highneko said:**
> Doesn't using quotes around includes like that check the current directory? And using the greater than and less than things around the includes checks the programs paths or something?

Just tried using the quotation marks around the includes and this still shows up as missing. This is most probably a bug with netbeans c plugin.

After some playing around I discovered that when I used the auto generated make file by netbeans the output worked fine. After running everything from the command line it seems to be a problem with the IDE.

Thanks for the help

Karl

---

### Post by Tomosaur on 2007-01-28
> **highneko said:**
> Doesn't using quotes around includes like that check the current directory? And using the greater than and less than things around the includes checks the programs paths or something?

Yeah I think it does. You CAN use the direct path to the .h file:

```

#include </path/to/stdio.h>

```

But in the IDE I was using, the lt, gt method always gave me an error - even though the compiler finished successfully and the program would run. I really don't know what was happening with it, I assume it was just some bug in the syntax checking or something, rather than the actual compiler going nuts. The programs always worked, I'd just get an error if I use < or >.

---


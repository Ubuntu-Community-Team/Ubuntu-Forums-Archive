---
title: "Adding &lt;conio.h&gt;"
date: 2012-09-16
forum: Programming Talk
---

### Post by manudo on 2012-09-16
How I can add <conio.h> library to the gcc Ubuntu compiler?

That's it, thank you! :)

---

### Post by MG&amp;TL on 2012-09-16
Ubuntu doesn't have <conio.h>. It's a Microsoft-specific header. What are you using it for?

---

### Post by manudo on 2012-09-16
> **MG&TL said:**
> Ubuntu doesn't have <conio.h>. It's a Microsoft-specific header. What are you using it for?

Sometimes I need the ```
clrscr();
``` instruction. If stdio.h has a clear screen instruction, it will be better.

---

### Post by MG&amp;TL on 2012-09-16
> **manudo said:**
> Sometimes I need the ```
clrscr();
``` instruction. If stdio.h has a clear screen instruction, it will be better.

I'm not sure that it does, but here's a simple hack:

```

//for system()
#include <stdlib.h>

main() {
    //clear the screen
    system("clear");
}

```

---

### Post by manudo on 2012-09-16
Really thank you man, It work fine! :D

---


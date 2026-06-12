---
title: "Detect printer in a network using c program"
date: 2011-06-03
forum: Programming Talk
---

### Post by infant_coder on 2011-06-03
Hi,

How to detect available printers on a local network through c program ?

---

### Post by Zugzwang on 2011-06-03
You mean the ones that are properly configured with your computer already? Try to use the GTK printing API or see if you can access CUPS directly with some API. These keywords should get you started on your google search.

---

### Post by dwhitney67 on 2011-06-03
I found CUPS to be helpful for a project I currently support.

Here's a small program that can be used to detect the available printers on a system:
```

#include <cups/cups.h>
#include <stdio.h>

int main()
{
   cups_dest_t* dests = NULL;
   int numDests = cupsGetDests(&dests);
   cups_dest_t* dest = dests;

   for (int n = 0; n < numDests; ++n, ++dest)
   {
      if (dest && dest->instance == NULL)
      {
         printf("Found printer: %s\n", dest->name);
      }
   }

   cupsFreeDests(numDests, dests);

   return 0;
}

```

To build this code, use gcc and link it with the CUPS library:
```

gcc -std=c99 get_printers.c -lcups

```

---

### Post by infant_coder on 2011-06-07
hi,

Thank you so much for the reply. But what I am searching for is a program to identify **printer services available on the network**, not only on the system.

I found that with avahi-discover we can discover the services on local network. I went through the source and found that avahi-discover is integrated with GTK.

I am trying to write this module for an embedded device without using GTK. 


I wonder how **to eliminate GTK from avahi-discover**. Any help would be appreciated.

---

### Post by Petrolea on 2011-06-07
> **infant_coder said:**
> hi,

Thank you so much for the reply. But what I am searching for is a program to identify **printer services available on the network**, not only on the system.

I found that with avahi-discover we can discover the services on local network. I went through the source and found that avahi-discover is integrated with GTK.

I am trying to write this module for an embedded device without using GTK. 


I wonder how **to eliminate GTK from avahi-discover**. Any help would be appreciated.

This is the same thread: [http://ubuntuforums.org/showthread.php?p=10912122](http://ubuntuforums.org/showthread.php?p=10912122)

---


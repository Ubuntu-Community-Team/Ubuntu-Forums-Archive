---
title: "[SOLVED] [C] Including headers in header files"
date: 2008-12-01
forum: Programming Talk
---

### Post by nvteighen on 2008-12-01
Playing around with some C code I had, I got myself into a question. For example, if I have a header like this:

```

#ifndef GRAPH_H
#define GRAPH_H

#include <stdio.h> /* <- Good practice? */

#include "list.h" /* <- Good practice? */

typedef struct GRAPH_T graph_t;

graph_t *graph_new(FILE *, list_t *);
void graph_free(graph_t *);

size_t graph_get_size(graph_t *);
char graph_get_queue(graph_t *, size_t);
void graph_set_queue(graph_t *, size_t, char);

char graph_is_edge(graph_t *, size_t, size_t);

#endif

```

As you see this interface requires other interfaces, one declared at list.h (which doesn't matter at all for the purposes of this post) and stdio.h, so we can get the list_t and FILE data types.

My question is what's the best practice: to #include those headers or to make the user #include them in his module? The first is only possible assuming the headers are correctly guarded (which is this case: stdio.h and list.h are guarded), otherwise everything crashes; the second avoids the possibility of a double #include of a non-guarded header, but increases the possibility of error.

Thanks in advance!

---

### Post by Idefix82 on 2008-12-01
Usually you would include everything into your header file which is needed by it. to avoid conflicts is precisely what the #ifndef...#endif part is for. You have to rely on error free headers of course, meaning that you have to rely on them using the same construction as you did here.

---

### Post by dribeas on 2008-12-01
> **Idefix82 said:**
> Usually you would include everything into your header file which is needed by it. to avoid conflicts is precisely what the #ifndef...#endif part is for. You have to rely on error free headers of course, meaning that you have to rely on them using the same construction as you did here.

I agree. Also, in some situations I have run into headers that did not include all that was needed directly but depended on it being included indirectly through one of the used headers. The problem with that situation (which I have suffered while developing for windows mostly) is that if one of the header changes and stops including the required .h, then your users code will break for no aparent reason.

---

### Post by nvteighen on 2008-12-02
Thanks. So, in conclusion: I should include everything so that my header could work independently.

---

### Post by dwhitney67 on 2008-12-02
And it is also good practice to include local header files (e.g. list.h) before including system header files (e.g. stdio.h).

That way, if list.h is missing a dependency header file (for example stdio.h), then you would find out quite quickly when you attempt to compile your application.

---

### Post by nvteighen on 2008-12-02
Thank you all for answering this. Now I have a clearer picture.

---


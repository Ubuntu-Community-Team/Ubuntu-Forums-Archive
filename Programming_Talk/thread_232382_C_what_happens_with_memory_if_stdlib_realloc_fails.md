---
title: "C: what happens with memory if stdlib realloc fails..."
date: 2006-08-08
forum: Programming Talk
---

### Post by red_Marvin on 2006-08-08
Reference: [http://www.cplusplus.com/ref/cstdlib/realloc.html]("http://www.cplusplus.com/ref/cstdlib/realloc.html")

If realloc fails a null pointer will be returned, _but is the original memory chunk freed?_
In other words is it safe to do this?:
```
int* pointer;
pointer=alloc(sizeof(int)*10);
pointer=realloc(sizeof(int)*100);
free(pointer);
```
Or do I have to do this to be **sure** to avoid memory leaks?:
```
int* pointer;
int* ptmp;
pointer=alloc(sizeof(int)*10);
ptmp=realloc(sizeof(int)*100);
if (ptmp!=0) {
    pointer=ptmp;
}
else {
    free(pointer); //<------ free the original memory
    //Other error handling
}
```


EDIT:
see: [http://www.c-faq.com/malloc/realloc.html]("http://www.c-faq.com/malloc/realloc.html")

---


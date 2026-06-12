---
title: "Problem with 'fpost_t' data type"
date: 2010-07-15
forum: Programming Talk
---

### Post by yousafsajjad on 2010-07-15
I have this code working on C++ but it is creating a problem when 
porting to C. Does anyone know how to fix it
```

bool retBool=TRUE;
    fpos_t  fpos;
    unsigned long *filePos='\0';
    unsigned short inHead = 4;
    unsigned short inTail = 5;

    if (fgetpos(c->fHandle, &fpos))
    {
        *filePos = 0;
        retBool = FALSE;
    }
    else
    {
        fpos = fpos - (inHead - inTail);                    // adjust for remaining in buffer
        *filePos = (unsigned long)fpos;
    }
    return retBool;

```

---


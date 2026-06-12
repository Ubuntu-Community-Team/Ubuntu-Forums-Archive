---
title: "Java help start of type"
date: 2009-04-23
forum: Programming Talk
---

### Post by SpyroViper on 2009-04-23
Hey,

I'm getting an illegal start of type in my boolean.  I have gone over it and I cannot for the life of me find what is wrong.

 
       > boolean authorIdValid = false;
       for (int i = 0; i < authorId.length; i++)
         
       if (authorId [i] >=0 && <=9)
       {    
        authorIdValid = true;
       }
       else
       {
       return false;
       }
      
   }


Any help would be appreciated :D

---

### Post by simeon87 on 2009-04-23
```

if (authorId [i] >=0 && <=9)

```

The second part of this conjunction is incomplete: <= 9. If you want to compare if authorId[i] is at least 0 and at most 9, you have to write:

```

if (authorId [i] >=0 && authorId [i] <=9)

```

---

### Post by SpyroViper on 2009-04-23
Ahh of course..  

Thank you!!  Much appreciated.

---


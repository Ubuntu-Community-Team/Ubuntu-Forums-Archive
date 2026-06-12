---
title: "JAVA passing commands to terminal"
date: 2011-10-23
forum: Programming Talk
---

### Post by Ra'anan on 2011-10-23
Hi,
I'm using this simple code:
```

public static void main(String args[]) throws IOException
    {   
        
        String command= "/usr/bin/gnome-terminal"; 
        Runtime rt = Runtime.getRuntime();     
        Process pr = rt.exec(command);
    }

```
I'm relatively new to JAVA programming but does anyone know how I can pass commands to the opened terminal?

---

### Post by Zugzwang on 2011-10-24
> **Ra'anan said:**
> 
I'm relatively new to JAVA programming but does anyone know how I can pass commands to the opened terminal?

Look at the man page of "gnome-terminal" - you can use the parameter "-x".

---


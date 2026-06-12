---
title: "gcj"
date: 2008-03-07
forum: Programming Talk
---

### Post by S15_88 on 2008-03-07
hey i've got a bunch of java programs i made using JCreator in windows back in the day.  i've been doing alot of C with gcc now and was curious to run some old programs using gcj.  of course i had the problem with the windows character encoding and stuff so i re-typed a little program:
```

import java.awt.*;
import java.io.*;
import java.awt.event.*;
import javax.swing.*;
import java.util.*;

public class ascii 
{

    public static void main(String[] args)
    {
        
        int pic;
        
        for(pic=0; pic<255; pic++)
        {
            system.out.println("#" + pic + " " + (char)(pic));
        }
    }
}

```

i get an error: 
> 
ascii.java:16: error: system cannot be resolved
        system.out.println("#" + pic + " " + (char)(pic));
        ^^^^^^
1 problem (1 error)


just wondering what might be causing this?  haven't done java in a while, pretty sure i got all my header files right.

any ideas?

Thanks, ALain

---

### Post by CptPicard on 2008-03-07
Java is case sensitive. Try "System.." :)

---


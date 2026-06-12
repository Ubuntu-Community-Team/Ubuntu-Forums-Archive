---
title: "Expository Comments"
date: 2009-05-12
forum: Programming Talk
---

### Post by fiddler616 on 2009-05-12
I've noticed a trend in my programming class: any code the teacher produces (either as part of a presentation or as part of a file we have to add to) has stuff like this in it:

```

//import statements
import java.util.*;
import javax.swing.*;

//global variables
int foo, bar;
String spam, eggs;
Scanner scan = new Scanner(System.in);

public static void doStuff(int stuff)
{
    //Assignment
    foo = scan.nextInt();
    bar = whatever(foo);
    double x = 0;
    double y = 300;
...
}
...
```

Am I crazy for being really bothered by those comments? If the code came from a student, I'd brush it off as bad code, but the teacher seems quite competent. I could maybe understand doing it the first few weeks of class, but we're at the point where if we don't know what an import statement is, we're in big trouble. Is there anything to be gained by such superficial, expository comments? Or am I on the wrong foot?

Thanks.

---

### Post by lloyd_b on 2009-05-12
> **fiddler616 said:**
> I've noticed a trend in my programming class: any code the teacher produces (either as part of a presentation or as part of a file we have to add to) has stuff like this in it:

```

//import statements
import java.util.*;
import javax.swing.*;

//global variables
int foo, bar;
String spam, eggs;
Scanner scan = new Scanner(System.in);

public static void doStuff(int stuff)
{
    //Assignment
    foo = scan.nextInt();
    bar = whatever(foo);
    double x = 0;
    double y = 300;
...
}
...
```

Am I crazy for being really bothered by those comments? If the code came from a student, I'd brush it off as bad code, but the teacher seems quite competent. I could maybe understand doing it the first few weeks of class, but we're at the point where if we don't know what an import statement is, we're in big trouble. Is there anything to be gained by such superficial, expository comments? Or am I on the wrong foot?

Thanks.

Consider that these comments are not intended to explain anything, but rather serve as an outline, showing where different elements belong.

Once a programmer has developed some proficiency, s/he will automatically group things like this without thinking about it.  But during the learning process, the teacher may feel that this needs to be reinforced.

Lloyd B.

---

### Post by fiddler616 on 2009-05-12
> **lloyd_b said:**
> Consider that these comments are not intended to explain anything, but rather serve as an outline, showing where different elements belong.

Once a programmer has developed some proficiency, s/he will automatically group things like this without thinking about it.  But during the learning process, the teacher may feel that this needs to be reinforced.

Lloyd B.
Thanks!

So I should see an appreciate, but not emulate.

---


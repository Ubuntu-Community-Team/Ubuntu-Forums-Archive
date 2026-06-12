---
title: "Java Annotations"
date: 2009-04-01
forum: Programming Talk
---

### Post by jamescox84 on 2009-04-01
I'm experimenting with annotations, and reflection in Java.  This simple piece of code below, I would of thought would work.  What I'm I doing wrong.

```
@interface Tag {}

@Tag
public class Main {

    public static boolean isTagged(Object o) {
        return o.getClass().isAnnotationPresent(Tag.class);
    }
    
    public static void main(String[] args) {
        System.out.println(isTagged(new Main()));
    }

}
```

I've greated an annotation call Tag applied it to the class Main, then written a function to check if the Tag annotation is present (isTagged).  I'd expect to see true printed to STDOUT.  But I'm getting "false".  I'm sure this has to be somthing simple.

Any help greatfully recieved.  Thanks

---

### Post by jespdj on 2009-04-01
By default, annotations are thrown away by the compiler. You have to specify that your annotation should be retained in the class file by annotating your annotation with the @Retention annotation:
```

import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;

@Retention(RetentionPolicy.RUNTIME)
@interface Tag {}

```

---

### Post by jamescox84 on 2009-04-01
Thank you so much I knew it had to be somthing simple.  Thanks

---


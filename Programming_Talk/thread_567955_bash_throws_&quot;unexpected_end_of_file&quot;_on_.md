---
title: "bash throws &quot;unexpected end of file&quot; on a script with a function using cat &lt;&lt;"
date: 2007-10-05
forum: Programming Talk
---

### Post by jamadagni on 2007-10-05
Try the following script.
```

#! /bin/bash
function foo
{
        cat > myfoo <<END
        foof
        fogog
        END
}
foo

```
It throws following error:
> line 10: syntax error: unexpected end of file
What's wrong with using "cat <<" syntax? I am able to use it outside of functions with no problems. Inside functions, I am forced to use "echo 'string' >> filename" syntax. That's highly inconvenient when I want to write a lot of stuff to a file from a script.

Using bash 3.2-0ubuntu10 on Kubuntu Gutsy Beta.

---

### Post by ghostdog74 on 2007-10-05
```

cat << EOF > myfile
....

```

---

### Post by jamadagni on 2007-10-05
whassa difference? and how come it works outside a function but not inside?

---

### Post by jamadagni on 2007-10-05
I found that the problem was not with bash or the order of the params. The order you specified did not help. The problem was that I had not used - after << which would strip leading tabs in the following lines, according to man:bash. Without the - after <<, I should place END and the other lines also without indent in the beginning of the line. Thanks for your efforts anyway.

---


---
title: "Something wrong with GCC in Edgy?"
date: 2006-10-25
forum: Programming Talk
---

### Post by scourge on 2006-10-25
I just upgraded to Edgy and was pleased to see that GCC now produces considerably faster binaries. However, everything isn't working as expected.

In my project (a chess engine) I have a function like this:
```

double getPhase(int mat)
{
    ASSERT(mat >= 0);

    if (mat > max_mat)
        mat = max_mat;

    return (double)(max_mat - mat) / (double)max_mat;
}

```

If I compile the app with assertions (I use my own assert macro) the function works as expected. But if I comment out the ASSERT line or disable all assertions the result isn't always correct. Most of the time the return value is what I want, but if I run the program's benchmark where the function is executed millions of times I see some problems:

With ASSERT: 4992637 nodes (correct result)
Without ASSERT: 5009880 nodes (incorrect result)

GCC 3.3 compiles the function correctly with or without the ASSERT line, but I've had no such luck with GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5). So does anyone have any idea what could be causing the problem?

---


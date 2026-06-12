---
title: "Regular Expresions Don't Work!"
date: 2009-01-27
forum: Programming Talk
---

### Post by rich1939 on 2009-01-27
I'm validating a lot of data and have decided to use regular expressions. For a first test, I defined the following variable:

```

 GRegex *stPat;

```

And I compiled following pattern, as follows:

```

stPat = g_regex_new("A[LKZR]|C[AOT]|D[EC]|FL|GA|HI|I[DLNA]|K[SY]|LA|M[EDAINSOT]|N[EVHJMYCD]|O[HKR]|PA|RI|S[CD]|T[NX]|UT|V[TA]|W[AVIY]", 0, 0, NULL);

```

Then when I test a text field containing "CA" as the data, I used the following function...and it fails:

```

if (!g_regex_match(stPat, text, 0, NULL));
    return FALSE;

```

The g_regex_match function always returns FALSE. What's going on?

---

### Post by Reiger on 2009-01-27
I think the problem lies in how the expression is evaluated, I wouldn't be surprised if your pipe operator in fact operates on the following operands (coloured):
```

"A[COLOR="DarkRed"][LKZR]|C[/COLOR][AOT]|D[EC]|FL|GA|HI|I[DLNA]|K[SY]|LA|M[EDAINSOT]|N[EVHJMYCD]|O[HKR]|PA|RI|S[CD]|T[NX]|UT|V[TA]|W[AVIY]"
```

Which means your regex will fail on "CA" as it looks for something beginning with "A"

---

### Post by rich1939 on 2009-01-27
> **Reiger said:**
> I think the problem lies in how the expression is evaluated, I wouldn't be surprised if your pipe operator in fact operates on the following operands (coloured):
```

"A[COLOR="DarkRed"][LKZR]|C[/COLOR][AOT]|D[EC]|FL|GA|HI|I[DLNA]|K[SY]|LA|M[EDAINSOT]|N[EVHJMYCD]|O[HKR]|PA|RI|S[CD]|T[NX]|UT|V[TA]|W[AVIY]"
```

Which means your regex will fail on "CA" as it looks for something beginning with "A"

Thanks for your reply; however, the problem wasn't with the pattern, it was with the call to the match operation, which had a stray semicolon ';' at the end of the 'if' statement, which caused the following (failure) statement to be executed.

I stressed out all day yesterday over the failing pattern match and only saw the stray semicolon immediately after I posted my message "Regular Expressions Don't Work!".

My bad.

---

### Post by sujoy on 2009-01-28
that looks like C, if yes then what library are you using for the regex functions?

---


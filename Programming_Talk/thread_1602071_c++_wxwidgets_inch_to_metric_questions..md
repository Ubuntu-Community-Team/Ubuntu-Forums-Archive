---
title: "c++ wxwidgets inch to metric questions."
date: 2010-10-21
forum: Programming Talk
---

### Post by Jonas thomas on 2010-10-21
I'm having a brain cramp here.

I have a string that I want to convert from inch to metric.
The standard is to say something like 1.5 inch  but I also want to allow 
1,5"  

I get an compiler error on the """
Is there an easy way around that? or do I need to go char by char '"'
```
wxString dimensionString = wxString(value).MakeLower();
         wxSscanf(wxString(value),_T("%lf"),&length);
    // Need to convert inch to internally stored metric
    // todo
    // This could be improved to do conversions such as
    // 1 Inch or 1 5/8" or 5/16 inch
   
    if dimensionString.Contains(_T("inch")))||dimensionString.Contains(_T(""")))
        length*=25.4;
```

---

### Post by worksofcraft on 2010-10-21
put a \ before the " you want in your string
[php]

    if (
         dimensionString.Contains(_T("inch")) ||
         dimensionString.Contains(_T("\""))
    ) length *= 25.4;
[/php]

Soz had to update cuz you got your braces wrong as well.
I always split complicated boolean expressions up like I did above to help me spot that kind of problem so wuz not attuned to the way you done it there ;)

---

### Post by Jonas thomas on 2010-10-21
You'd think that /" would work... That's generating a bunch of really interesting errors.  If I go "asdf" instead of """ it's generating errors as well... Need to look at this in the morning after some zzz's thanks.. anyway.

> **worksofcraft said:**
> put a \ before the " you want in your string
[php]

    if dimensionString.Contains(_T("inch")))||dimensionString.Contains(_T("\"")))
[/php]

---

### Post by Jonas thomas on 2010-10-21
Then again... 
This will compiles
>     if ((dimensionString.Contains(_T("inch")))||(dimensionString.Contains(_T("asdf"))))
        length*=25.4;

Change to this 
 > if ((dimensionString.Contains(_T("inch")))||(dimensionString.Contains(_T("\""))))
        length*=25.4;


works... It helps to have the \ in the correct direction.... Duhhhh...

---


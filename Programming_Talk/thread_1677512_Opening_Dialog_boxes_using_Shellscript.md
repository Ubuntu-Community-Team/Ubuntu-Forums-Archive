---
title: "Opening Dialog boxes using Shellscript"
date: 2011-01-28
forum: Programming Talk
---

### Post by Datweakfreak on 2011-01-28
I was working with Zenity to open dialog boxes from Terminal, and I found this:

1. When I type something like **zenity --info --text='Hello World'**, it opens a dialog box displaying **Hello World**.

2. When I type something like

[B]g='Hello World'
zenity --info --text=$g[/B]

It just shows** Hello**. I tried this out with several other text, including numbers and special characters, and zenity always seems to ignore everything after the first white space. Another instance is:

[B]g='**** .... ;;;;'
zenity --info --text=$g[/B]

And the resulting dialog box shows just the **'****'** and ignores the** '.... ;;;;' **part.

Any ideas on how to sort this out would be swell. If there's some utility other than Zenity that I could use to avoid this problem, please do share pointers.

Cheers.

---

### Post by sisco311 on 2011-01-28
Use quotes:
```
g='Hello World'
zenity --info --text="$g"
```

See:
[http://mywiki.wooledge.org/WordSplitting](http://mywiki.wooledge.org/WordSplitting)
at
[http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

---

### Post by Datweakfreak on 2011-01-28
> **sisco311 said:**
> Use quotes:
```
g='Hello World'
zenity --info --text="$g"
```

Wow, thanks tons! :P

Oh, my....I feel dumb now ](*,)

---

### Post by sisco311 on 2011-01-28
> **Datweakfreak said:**
> Wow, thanks tons! :P

Oh, my....I feel dumb now ](*,)

You're welcome!

Don't worry, if you check out [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls) , you will see that this is one of the most common errors that Bash programmers make. ;)

---


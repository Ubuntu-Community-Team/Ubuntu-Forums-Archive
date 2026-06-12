---
title: "Spaces in Bash variables"
date: 2010-08-18
forum: Programming Talk
---

### Post by Nonno Bassotto on 2010-08-18
I'm  having a problem with bash variables with spaces.

I can read an image metadata using
```

exiv2 -P IX pr path_to_the_image

```

If the path has spaces, I can just do
```

exiv2 -P IX pr path\ to\ the\ image

```
and everything is fine.

If I try to do this with variables, the escaped spaces become normal spaces. So
```

path=path\ to\ the\ image
exiv2 -P IX pr $path

```
gives errors. How can I keep the escaped spaces?

---

### Post by Bachstelze on 2010-08-18
Use quotes:

```
path="path to the image"
```

---

### Post by MadCow108 on 2010-08-18
instead of escaping you can also quote the string.

but in later use you now have to quote the variable, as the escape has been "used up" for the assignment:
```

path=path\ to\ the\ image
# or path="path to the image"

#note the quote
exiv2 -P IX pr "$path" 

```

---

### Post by Nonno Bassotto on 2010-08-18
Nice try. But it doesn't really work. Both quotes and escaped spaces are removed from variables...

---

### Post by DaithiF on 2010-08-18
use quotes:
```
path="path to the image"
exiv2 -P IX pr "$path"

```

-- edit --
oops, a bit late i see, but quotes definately *are* the answer

---

### Post by Nonno Bassotto on 2010-08-18
> **MadCow108 said:**
> instead of escaping you can also quote the string.

but in later use you now have to quote the variable, as the escape has been "used up" for the assignment:
```

path=path\ to\ the\ image
# or path="path to the image"

#note the quote
exiv2 -P IX pr "$path" 

```

Thank you, this works! :D

---

### Post by geirha on 2010-08-18
«path=path\ to\ the\ image» and «path="path to the image"» do exactly the same thing. The problem is with the expansion of the variable, because word splitting happens **after** the variable is expanded. See
[http://mywiki.wooledge.org/Arguments](http://mywiki.wooledge.org/Arguments) for a thorough explanation.

---

### Post by Zorgoth on 2010-08-18
"$path" is the format, not making $path be "<data with spaces>"

Also, if you want really precise control, you can use an array:

array=("my file" myotherfile my list of lots of files)

<mycommand> "${array[@]}" will pass the arguments exactly as expected.

to set values in an array:

<array_name>[n]=<stuff>

n is an integer.  Note that arrays are indexed from 0, not 1, so for example in 

array=(1 2 3 4 5)

${array[1]} is 2 - if you want 1, that would be ${array[0]}

---

### Post by AlphaLexman on 2010-08-18
Let me first say my 'beans' are lower, but my 'bash' book I have says:
> The character following a \ is taken literally. Use within " " to escape ", $, and '. Often used to escape itself, spaces, or newlines.So, I would interpret this ->
```
path="path=\'path\ to\ new\ image\'"
```But, to be honest I'm just guessing!!

---

### Post by Nonno Bassotto on 2010-08-18
> **geirha said:**
> «path=path\ to\ the\ image» and «path="path to the image"» do exactly the same thing. The problem is with the expansion of the variable, because word splitting happens **after** the variable is expanded. See
[http://mywiki.wooledge.org/Arguments](http://mywiki.wooledge.org/Arguments) for a thorough explanation.

Thank you, now I finally understand the logic.

---

### Post by Zorgoth on 2010-08-18
> **AlphaLexman said:**
> Let me first say my 'beans' are lower, but my 'bash' book I have says:
So, I would interpret this ->
```
path="path=\'path\ to\ new\ image\'"
```But, to be honest I'm just guessing!!

This will not always work.  Backslash escapes and quoting are handled before parameter expansion, so often that will result in those backslashes and quotes being taken literally rather than used as escapes.  This is one of the primary reasons for arrays.

---


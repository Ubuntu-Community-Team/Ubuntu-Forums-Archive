---
title: "csh sctipts - foreach doesn't work on $path variable."
date: 2009-12-02
forum: Programming Talk
---

### Post by IceMan68 on 2009-12-02
I write the next lines, for example:
```

set dirs = `echo $path`
foreach dir ($dirs)
 echo $dir
end

```

and i get an error regarding the foreach but if i change the first line with just regular directories that I input manually it works :-\

I printed this:

```
echo $dirs
```
and it gives all of the path variables with spaces in between I just don't understand why the foreach can't go over all the dirs.

any suggestions?

Thanks a lot in advance!

---

### Post by Arndt on 2009-12-02
> **IceMan68 said:**
> I write the next lines, for example:
```

set dirs = `echo $path`
foreach dir ($dirs)
 echo $dir
end

```

and i get an error regarding the foreach but if i change the first line with just regular directories that I input manually it works :-\

I printed this:

```
echo $dirs
```
and it gives all of the path variables with spaces in between I just don't understand why the foreach can't go over all the dirs.

any suggestions?

Thanks a lot in advance!

What's the exact error message? It works for me.

---

### Post by IceMan68 on 2009-12-03
[FONT=monospace]My bad, I didn't copy it right. very sorry for that.

that's the exact copy:

[/FONT]```

set dirs = `echo $path`

foreach dir ($dirs)
   set filesInDir = `echo $dir/*`
   foreach file ($filesInDir)
      echo $file
   end
end

```it gives the error :
```
echo : No match.
```on the line:
```
set filesInDir = `echo $dir/*`
```when the directory "dir" is empty.

How can I overcome this error?

p.s.
If I write the "echo $dir/*" or "$dir/*" in the foreach lines like this:
```
foreach file ($dir/*)
```it shows an error and exit the script in case the directory is empty.
The way I did it it just writes the error and continues. I just don't want it to
write the error either. In case the directory is empty it should continue with the next directory.


Thanks a lot!!!

---

### Post by Arndt on 2009-12-03
> **IceMan68 said:**
> [FONT=monospace]My bad, I didn't copy it right. very sorry for that.

that's the exact copy:

[/FONT]```

set dirs = `echo $path`

foreach dir ($dirs)
   set filesInDir = `echo $dir/*`
   foreach file ($filesInDir)
      echo $file
   end
end

```it gives the error :
```
echo : No match.
```on the line:
```
set filesInDir = `echo $dir/*`
```when the directory "dir" is empty.

How can I overcome this error?

p.s.
If I write the "echo $dir/*" or "$dir/*" in the foreach lines like this:
```
foreach file ($dir/*)
```it shows an error and exit the script in case the directory is empty.
The way I did it it just writes the error and continues. I just don't want it to
write the error either. In case the directory is empty it should continue with the next directory.


Thanks a lot!!!

Generally sh (either plain sh, or bash) is recommended before csh. csh has many problems as a script language.

I suppose you can do a kludge here: add a fictitious entry to filesInDir ("//" for example - it can't occur as filename), and skip that entry inside the loop.

---

### Post by IceMan68 on 2009-12-03
> **Arndt said:**
> Generally sh (either plain sh, or bash) is recommended before csh. csh has many problems as a script language.

I suppose you can do a kludge here: add a fictitious entry to filesInDir ("//" for example - it can't occur as filename), and skip that entry inside the loop.

thanks mate! it does work but is there a more elegant way to so?

isn't there a method to check if a directory is empty?

---

### Post by Arndt on 2009-12-03
> **IceMan68 said:**
> thanks mate! it does work but is there a more elegant way to so?

isn't there a method to check if a directory is empty?

Checking whether the variable is empty before looping over it is less convoluted than what I suggested first.

---


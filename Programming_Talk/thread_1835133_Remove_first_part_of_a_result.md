---
title: "Remove first part of a result"
date: 2011-08-28
forum: Programming Talk
---

### Post by bcooperizcool on 2011-08-28
I have a file for the purpose of this question called "bob"

the contents of "bob" are as such (not exactly, they change each time) :
```
/Library/Waffle
      /Dev/Cookie/Llama/bin
      /Applications/Settings.app
      /System/Library/CoreServices/SpringBoard.app
```

and so on and so forth.

What I am trying to do is only get the last part of it, so it would end up like this, in a new file:
```
Waffle
      bin
      Settings.app
      SpringBoard.app
```


Any thoughts?  I tried variations of this:
```
cat bob | sed 's/\/*$//' >> hi
```

Thanks!  :D

---

### Post by Bachstelze on 2011-08-28
This works except tat you want to delete everything between the firs and last slashes, so

```
sed 's_/.*/__' foo.txt
```

---

### Post by papibe on 2011-08-28
If indentation is not important:
```
#!/bin/bash

while read -r line
do
        echo "$(basename "$line")"
done < bob

```
Or this, with correct indentation
```
$ sed 's/\/.*\/\([^/]*\)$/\1/' bob
```
Regards.

---

### Post by kurum! on 2011-08-29
```

$ ruby -ne 'print $_.gsub(/\/.*\//,""); ; ' file
Waffle
      bin
      Settings.app
      SpringBoard.app


```

---

### Post by Arndt on 2011-08-29
> **Bachstelze said:**
> This works except tat you want to delete everything between the firs and last slashes, so

```
sed 's_/.*/__' foo.txt
```

What should happen if there is only one slash?

---

### Post by bcooperizcool on 2011-08-29
> **Arndt said:**
> What should happen if there is only one slash?


In that case, I probably know what it is, but his answer solved it for me :)


So thanks to all of you!  :D

---


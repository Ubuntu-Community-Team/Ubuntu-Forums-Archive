---
title: "Very basic BASH problem"
date: 2009-05-29
forum: Programming Talk
---

### Post by ml_fan on 2009-05-29
I have looked all over the place and tried a lot of different things but I am unable to get this to work

#!/bin/bash

position="a"

if["$position"=="a"];then
      echo "great job"
fi


error message as follows:
./bash_sample.sh: line 5: syntax error near unexpected token `then'
./bash_sample.sh: line 5: `if[$position=="a"];then'

---

### Post by x22 on 2009-05-29
#!/bin/bash

position=a

if [ $position = a ];then
echo "great job"
fi


*note spaces:-)

---

### Post by ghostdog74 on 2009-05-29
use awk
```

awk 'BEGIN{
 position="a"
 if ( position == "a"){
  print "ok"
 }
}'

```
you don't have to worry about "=" being a valid equality sign when == is actually what you need.

---

### Post by k2t0f12d on 2009-05-30
> **ml_fan said:**
> I have looked all over the place and tried a lot of different things but I am unable to get this to work

#!/bin/bash

position="a"

if["$position"=="a"];then
      echo "great job"
fi


error message as follows:
./bash_sample.sh: line 5: syntax error near unexpected token `then'
./bash_sample.sh: line 5: `if[$position=="a"];then'

```
package="a"
test "$package" -eq "a" && printf "Great job!"
```

---

### Post by Habbit on 2009-05-30
> **k2t0f12d said:**
> ```
package="a"
test "$package" -eq "a" && printf "Great job!"
```
```
package="a"
test "x$package" -eq "xa" && printf "Great job!"
```
So that `test` won't die with "another argument expected" when $package is empty.

---

### Post by k2t0f12d on 2009-05-30
> **Habbit said:**
> ```
package="a"
test "x$package" -eq "xa" && printf "Great job!"
```
So that `test` won't die with "another argument expected" when $package is empty.

```
package="a"
test "$package" == "a" && printf "great job"
```

no, but I had the wrong operator there.  try that

---

### Post by ml_fan on 2009-05-30
> **x22 said:**
> #!/bin/bash

position=a

if [ $position = a ];then
echo "great job"
fi


*note spaces:-)

Thank you.

---


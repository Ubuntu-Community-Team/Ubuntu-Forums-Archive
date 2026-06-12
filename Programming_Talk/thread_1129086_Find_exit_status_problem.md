---
title: "Find exit status problem"
date: 2009-04-18
forum: Programming Talk
---

### Post by aliahsan81 on 2009-04-18
Hi All

Its strange or i am doing it wrong.When find run successful it return exit status 0.And same if it didn't run successfully it return zero.



```


find /var/www/html  -maxdepth 1 -type f -name *.dsadas
 echo $?
0



```

```

find /var/www/html  -maxdepth 1 -type f -name *.php
/var/www/html/index.php
 echo $?
0

```

---

### Post by Namtabmai on 2009-04-18
> EXIT STATUS
       find  exits  with status 0 if all files are processed successfully, greater than 0 if errors occur.   This is deliberately a very broad description, but if the return value is non-zero,
       you should not rely on the correctness of the results of find.


Sorry for the cut paste from the man page, but I think this covers it.
Basically, find will only return a non-0 result if find encounters any errors. If there where no errors, it will return 0 regardless of the number of matches found.

---

### Post by aliahsan81 on 2009-04-18
Yes thanks but its not good approach ,It should be more intelligent.Can we mark this as a bug??

---

### Post by Namtabmai on 2009-04-18
> **aliahsan81 said:**
> Yes thanks but its not good approach ,It should be more intelligent.Can we mark this as a bug??


You can try but it's unlikely to change. Program return codes are used to identify errors within the program. As strange as it might sound to start with find not finding anything isn't an error. Find managed to search all the files you specified without any problems, the fact it didn't find any results isn't an error in the program. Does this make sense?


A better solution to what I think you are trying to do is pipe find through wc to count the number of results found.

```

RES=`find /var/www/html  -maxdepth 1 -type f -name *.dsadas | wc -l`
if [ $RES -eq 0 ]; then
  echo "No results found"
else
  echo "Found $RES results"
fi

```

---

### Post by aliahsan81 on 2009-04-18
yes correct,Now i have to deal this way,No option to use an other command to do the job.;)
Thanks for your suggestion

---

### Post by Arndt on 2009-04-18
> **aliahsan81 said:**
> yes correct,Now i have to deal this way,No option to use an other command to do the job.;)
Thanks for your suggestion

Another way is to find a command which passes every input along, but returns the exit status if the input was empty, and I think

```
grep ''
```

is such a command. So you can do

```
find /var/www/html  -maxdepth 1 -type f -name *.dsadas | grep ''
```

Note that this is one of those cases that _really_ merit a comment in your script why you're doing it, because the next person reading it (you yourself in two months) may not get the point.

---


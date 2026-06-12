---
title: "shell script"
date: 2009-06-06
forum: Programming Talk
---

### Post by leblancmeneses on 2009-06-06
attached is screenshot of my problem.

The output of the failed test should look like this:
Example of a failed item:
test_fail_fail    Failed
Aborted
printf statements

or

test_fail_fail    Failed
printf statements
Aborted
 


Here is the meat to my shell script:

even with error redirect to store output in message variable; Aborted statement shows up before the printf.  I would like it captured also.
```

            message=`./${TEST} 2>&1`
            status=$?
            printf "%-40.35s  %-22s\n" $TEST `fn_test_status $status`

            if [ $status -ne 0 ] || [ $isverbose = 1 ]; then    
                echo "${message}"
                echo
            fi

```the c file that generates the assertion
```

#include <stdio.h>
#include <assert.h>

int main(int argc, char *argv[]) {
    printf("\tReached: testing fail test.. \n"); 
    assert(1);
    printf("\tReached: A.. \n"); 
    assert(1);
    printf("\tReached: B.. \n"); 
    assert(1 == 0);
    printf("\tReached: C.. \n"); 
    return 0;
}

```any other ideas would be appreciated.

thanks

lm

---

### Post by Habbit on 2009-06-06
It seems that stdout (to which printf writes) and stderr (to which assert writes) are not synchronised. Flushing stdout after each printf() might help - for example, using cout << "Reached A" << endl flushes the stream.

---

### Post by leblancmeneses on 2009-06-06
that cannot be the problem
example:

if i change:
```


            message=`./${TEST} 2>&1`
to
            message=`./${TEST} 2>__testerror.o`

```

my output becomes:

```

Aborted
test_fail_fail                            Failed                
    Reached: testing fail test.. 
    Reached: A.. 
    Reached: B.. 
test_fail_fail: test_fail_fail.c:10: main: Assertion `1 == 0' failed.

```


so it seems is the backtick's produce "Aborted"

because __testerror.o file contains only:
```

$ cat __testerror.o 
test_fail_fail: test_fail_fail.c:10: main: Assertion `1 == 0' failed.


```

so how do we suppress backticks "Aborted" message
or what replacement can i use for backticks?

---

### Post by leblancmeneses on 2009-06-06
I'm going go a different direction....

instead of trying to solve it by populating $message correctly i'm just going redirect to file:

./${TEST} >__teststdin_${TEST}.o 2>__teststderr_${TEST}.o

and cat them locally

                cat __teststdin_${TEST}.o
                cat __teststderr_${TEST}.o

which is working.

just wonder what the real problem was... o well

---

### Post by MadCow108 on 2009-06-06
flushing stdout, like habbit proposed, is necessary on my system to put the assertion text in the right spot:
with flush (fflush(stdout) in c, cout is c++):
```

a.out                                      134                  
	Reached: testing fail test.. 
	Reached: A.. 
	Reached: B.. 
a.out: test.c:13: main: Assertion `1 == 0' failed.

```

without flush:
```

a.out                                      134                  
a.out: test.c:10: main: Assertion `1 == 0' failed.
	Reached: testing fail test.. 
	Reached: A.. 
	Reached: B..

```

I can't reproduce the aborted statement.

---


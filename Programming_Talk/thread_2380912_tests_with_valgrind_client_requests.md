---
title: "tests with valgrind client requests"
date: 2017-12-23
forum: Programming Talk
---

### Post by chuchi on 2017-12-23
Hi everyone!


I just discovered the Valgrind client requests, and I would like to use them in my tests (gtest) to check my code for leaks or invalid memory read. This is an example code:


```



TEST(ValgrindTest, myTest)
{
    int previous_num_errors, num_errors;
    VALGRIND_DO_LEAK_CHECK;
    previous_num_errors = VALGRIND_COUNT_ERRORS;
    
    //some testing code
    
    num_errors = VALGRIND_COUNT_ERRORS;
    
    //check the number of errors at the begging of the test are equal to the number of errors at the end of the test
    ASSERT_EQ (previous_num_errors, num_errors);
}



```


The problem is that the Valgrind macros (VALGRIND_COUNT_ERRORS and VALGRIND_DO_LEAK_CHECK) only work if the program is run under Valgrind, and my tests are in a remote machine and I can't change the command to run the tests under Valgrind.


So my question : Is there a way to make these macros work without Valgrind? Something like :


```

./myTests

```


Thanks a lot!

---


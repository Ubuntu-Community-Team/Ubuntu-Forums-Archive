---
title: "Null Pointer Exception (C++)"
date: 2008-11-18
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-11-18
I am trying to compute percentiles in the following code, but I am getting a null-pointer exception from someplace.  It could be coming from elsewhere besides what is shown below, but I think it is coming from below (goes away when I modify the part below).  Is there something wrong with the code below?  Assume buffer is a STL vector which can have any size, 0 to 100.

[PHP]
	if(buffer.size() == 0 || (buffer.size()/4 - 1) < 0)
	{
		return false;
	}
	
	//25th-percentile
	nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/4 - 1, buffer.end());
	double twentyfifthperc=*(buffer.begin()+(buffer.size()+1)/4 - 1);
	
	//compute the median
	nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/2 - 1, buffer.end());
	median=*(buffer.begin()+(buffer.size()+1)/2 - 1);
	
	//75th-percentile
	nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/4*3 - 1, buffer.end());
	double seventyfifthperc=*(buffer.begin()+(buffer.size()+1)/4*3 - 1);
[/PHP]

---

### Post by Tony Flury on 2008-11-18
with a small code fragment it is very difficult to diagnose problems - so have you tried to used the debugger (gdb) to step through the code to see what the values are set to.

Alternatively you could liberally pepper your could with printfs to dump the values of the variables to stdout (or stderr) - you can even print the value of any pointers, even if the pointer itself somewhere invalid (like NULL).

You say it goes away when you modify the code that you have shown - what modification ?

bear in mind with things like bad pointers, the bug is rarely near the code that actually fails. The key to debugging is to find which pointer is going NULL (using gdb or printfs as above).

---

### Post by samjh on 2008-11-18
I've no idea what those function calls are supposed to do, so it's hard to guess what the problem might be.

A hint: put some output statements to show the progress of your code, so when it does throw an exception, you'll be able to see exactly where.

E.g:```
    if(buffer.size() == 0 || (buffer.size()/4 - 1) < 0)
    {
        return false;
    }
    
    //25th-percentile
    cout << "calculating 25th-percentile" << endl;
    cout << "nth_element" << endl;
    nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/4 - 1, buffer.end());
    cout << "twentyfifthperc = ?" << endl;
    double twentyfifthperc=*(buffer.begin()+(buffer.size()+1)/4 - 1);
    
    //compute the median
    cout << "calculating the median" << endl;
    cout << "nth_element" << endl;
    nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/2 - 1, buffer.end());
    cout << "median = ?" << endl;
    median=*(buffer.begin()+(buffer.size()+1)/2 - 1);
    
    //75th-percentile
    cout << "calculating 75th-percentile" << endl;
    cout << "nth_element" << endl;
    nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/4*3 - 1, buffer.end());
    cout << "seventyfifthperc = ?" << endl;
    double seventyfifthperc=*(buffer.begin()+(buffer.size()+1)/4*3 - 1);  
```

---

### Post by dwhitney67 on 2008-11-18
> **SNYP40A1 said:**
> I am trying to compute percentiles in the following code, but I am getting a null-pointer exception from someplace.  It could be coming from elsewhere besides what is shown below, but I think it is coming from below (goes away when I modify the part below).  Is there something wrong with the code below?  Assume buffer is a STL vector which can have any size, 0 to 100.
...

I do not think the error is occurring where you think it is; I ran the test below, and it did not cause any grief.  Whether the results are valid is anyone's guess.
[php]
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
  std::vector<double> buffer;

  for (int i = 0; i < 100; ++i)
  {
    buffer.push_back((i+1) * 13.8 / 2.45);
  }

  // 25th-percentile
  std::nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/4 - 1, buffer.end());
  double perc25th = *(buffer.begin()+(buffer.size()+1)/4 - 1);

  // median
  std::nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/2 - 1, buffer.end());
  double median = *(buffer.begin()+(buffer.size()+1)/2 - 1);

  // 75th-percentile
  std::nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/4*3 - 1, buffer.end());
  double perc75th = *(buffer.begin()+(buffer.size()+1)/4*3 - 1);

  std::cout << "perc25th = " << perc25th << std::endl;
  std::cout << "median   = " << median   << std::endl;
  std::cout << "perc75th = " << perc75th << std::endl;

  return 0;
}
[/php]

---

### Post by SNYP40A1 on 2008-11-18
Thanks everyone, I was expecting that somehow that code was blatantly and obviously wrong in some way that I did not see.  It's used in application where the inputs are generated randomly from silicon wafer testing.  So I guess I need to log the inputs to the entire program to a text file, wait for the program to crash, and then feed back in the input that made the program crash and figure out what is happening offline.  I tried the random input approach and I think something else is going on.  Again, I figured that since the only thing I changed were those 3 lines, the code that I posted must be blatantly wrong, but I don't see anything wrong with it.  I know that the first step in debugging is to reproduce the problem...

---

### Post by SNYP40A1 on 2008-11-18
> **dwhitney67 said:**
> I do not think the error is occurring where you think it is; I ran the test below, and it did not cause any grief.  Whether the results are valid is anyone's guess.
[php]
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
  std::vector<double> buffer;

  for (int i = 0; i < 100; ++i)
  {
    buffer.push_back((i+1) * 13.8 / 2.45);
  }

  // 25th-percentile
  std::nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/4 - 1, buffer.end());
  double perc25th = *(buffer.begin()+(buffer.size()+1)/4 - 1);

  // median
  std::nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/2 - 1, buffer.end());
  double median = *(buffer.begin()+(buffer.size()+1)/2 - 1);

  // 75th-percentile
  std::nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/4*3 - 1, buffer.end());
  double perc75th = *(buffer.begin()+(buffer.size()+1)/4*3 - 1);

  std::cout << "perc25th = " << perc25th << std::endl;
  std::cout << "median   = " << median   << std::endl;
  std::cout << "perc75th = " << perc75th << std::endl;

  return 0;
}
[/php]

Actually, the error is occuring above.  Took me all morning to figure this out though, had to reproduce the error, capture the input and then debug.  Anyhow, the problem lies in these lines:

  std::nth_element(buffer.begin(), buffer.begin() + (buffer.size()+1)/4 - 1, buffer.end());
  double perc25th = *(buffer.begin()+(buffer.size()+1)/4 - 1);

What if buffer has size of 2?  Then:

(buffer.size()+1)/4 - 1
(2+1)/4 - 1
3 / 4 -1
0 - 1
-1

So buffer.begin() + -1 = bad.

---

### Post by dwhitney67 on 2008-11-18
But you had the following test in the code in your OP.  Seems to me that you were already handling the situation where the data cannot be less than 4 items.  Maybe the '<' should be changed to '<='??
[php]
    if(buffer.size() == 0 || (buffer.size()/4 - 1) < 0)
    {
        return false;
    }
[/php]

---


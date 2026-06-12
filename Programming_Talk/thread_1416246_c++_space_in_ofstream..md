---
title: "c++ space in ofstream."
date: 2010-02-25
forum: Programming Talk
---

### Post by chris200x9 on 2010-02-25
Hi I want to output a 9 by 9 matrix with spaces between the numbers, I have the following code:

```
 void outputdata()
{
	ofstream outData;
	outData.open("out.txt");
	int counter = 0;
	int i =0;
	while (i < 9)
	{
		while (counter < 9)
		{
			
	 outData << matrix[i][counter];
// 	 outData << " "; 
	counter++;
}
outData << endl;
counter = 0;
i++;
}
outData.close();
}
``` 
it works fine except there is no spaces and when I uncoment the commented line it does not exit. Any help?

---

### Post by dwhitney67 on 2010-02-25
When examining the code you posted, I cannot see any reason why it would not work, even when the commented-out line is included.

One thing that confuses me is why you elected to use while-loops instead of for-loops?

Here are two alternative solutions you should be able to use:
```

// option 1
//
for (int i = 0; i < 9; ++i)
{
   std::copy(matrix[i], matrix[i] + 9, std::ostream_iterator<int>(outData, " "));
   outData << std::endl;
}


// option 2 (very comparable to your attempt)
//
for (int i = 0; i < 9; ++i)
{
   for (int j = 0; j < 9; ++j)
   {
      outData << matrix[i][j] << " ";
   }
   outData << std::endl;
}

```

P.S.  The std::copy() and std::ostream_iterator are documented here:
[http://www.cplusplus.com/reference/algorithm/copy/](http://www.cplusplus.com/reference/algorithm/copy/)
[http://www.cplusplus.com/reference/std/iterator/ostream_iterator/](http://www.cplusplus.com/reference/std/iterator/ostream_iterator/)

---

### Post by chris200x9 on 2010-02-25
niether of those work, I'm thinking it may be an error in another function (maybe?) I don't know why it didn't show up before though... anyway thank you, :popcorn:

---

### Post by dribeas on 2010-02-26
What is it that you are really trying to achieve? I would think that maybe you do not really want to just print spaces, but rather make sure that each column takes a fixed width. If that is the case, take a look at width and setw:

```

int array[] = { 1, 2, 3, 4 };
for ( int i = 0; i < 4; ++i )
{
   std::cout << std::setw(5) << array[i];
}
std::cout << std::endl;

```

That will pad each number to at least 5 characters in width.

---

### Post by Some Penguin on 2010-02-26
That sort of thing screams memory corruption.

[http://www-01.ibm.com/software/awdtools/purify/unix/](http://www-01.ibm.com/software/awdtools/purify/unix/)

(and similar tools) might be of interest.

---

### Post by dwhitney67 on 2010-02-26
> **chris200x9 said:**
> niether of those work, I'm thinking it may be an error in another function (maybe?) I don't know why it didn't show up before though... anyway thank you, :popcorn:

Actually, my examples do work.  Whether they meet your *requirements* may be a different story, or as SomePenguin mentioned, if you have a memory corruption issue, then all bets are off.

---


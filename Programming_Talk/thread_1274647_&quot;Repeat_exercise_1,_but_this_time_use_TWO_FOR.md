---
title: "&quot;Repeat exercise 1, but this time use TWO FOR LOOPS, one nested within the other.&quot;"
date: 2009-09-24
forum: Programming Talk
---

### Post by s3a on 2009-09-24
On my programming assignment, here is the code I used to answer question 1:

```
public class Q1
{
	public static void main (String [] args)
	{	
		
		for(int number = 1; number <= 100; number += 1)
		{
		System.out.printf("%2d ", number);
		if((number%10) == 0)
			System.out.println();
		}
		
		
	}
}
```

"Repeat exercise 1, but this time _use two for loops, one nested within the other_."

Can someone please give me an example of how to do this?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by samjh on 2009-09-24
I won't give you a plain answer, but take a look at the code in this thread for hints: [http://ubuntuforums.org/showthread.php?t=314728](http://ubuntuforums.org/showthread.php?t=314728)

---

### Post by Can+~ on 2009-09-24
Pseudo code:

```
loop from 1 to 10 as i:
    loop from i to 10*i as j:
        print j
        ...
```

Or...

```
loop from 1 to 10 as i:
    loop from 1 to 10 as j:
        print i*j
        ...
```

---

### Post by cariboo on 2009-09-24
We don't do homework help here. This thread is closed.

---


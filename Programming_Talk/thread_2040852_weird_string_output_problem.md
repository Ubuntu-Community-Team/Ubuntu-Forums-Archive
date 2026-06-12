---
title: "weird string output problem"
date: 2012-08-11
forum: Programming Talk
---

### Post by pellyhawk on 2012-08-11
I got very weird results with two similar code block.

```
		int communication;
		char communication_str[][12]=
	                 {
	               		    "[COLOR="Red"]GPRS Offline[/COLOR]",
				    "GPRS Idle",
	               		    "GPRS COMM",       			
	               	    	"---"
			};
			for (communication = 0; communication < 4; communication++)
			{
			    printf("communication = %d %s\n", communication, communication_str[communication]);
		  }
```
got:
```
communication = 0 [COLOR="Red"]GPRS OfflineGPRS Idle[/COLOR]
communication = 1 GPRS Idle
communication = 2 GPRS COMM
communication = 3 ---

```

If I modified the code block above:
```
		int communication;
		char communication_str[][12]=
	                 {
	               		    "[COLOR="Red"]GPRS Off[/COLOR]",
				    "GPRS Idle",
	               		    "GPRS COMM",       			
	               	    	"---"
			};
			for (communication = 0; communication < 4; communication++)
			{
			    printf("communication = %d %s\n", communication, communication_str[communication]);
		  }
```

got:```
communication = 0 [COLOR="Red"]GPRS Off[/COLOR]
communication = 1 GPRS Idle
communication = 2 GPRS COMM
communication = 3 ---

```

Why I got different result? Thanks.

---

### Post by lisati on 2012-08-11
You might need to bump up the space you allocate by at least one to 13, to allow for the null byte that C/C++ use to signal the end of strings. Another option would be to let the compiler work out the necessary size for you.

---

### Post by spjackson on 2012-08-11
I'll assume that this is C or C++. "GPRS Offline" is 13 characters long, including the terminating nul byte. Your array is only big enough to hold 12 characters, without the nul byte, so when you pass it to a function such as printf, the function continues reading until some other nul byte is found - wherever that might happen to be in memory.

---

### Post by durdenstationer on 2012-08-11
> **lisati said:**
> Another option would be to let the compiler work out the necessary size for you.

That only works if you are using single dimensional arrays.  Multi-dimensional arrays only let you leave out specifying the left-most size.  The compiler *can't* do what you say at least from the way the person wrote the code.  You'd get a compiler error.

If he did it something like 

```
char * array[] = { "one", "two", "three" };
```

then it would be fine.

---


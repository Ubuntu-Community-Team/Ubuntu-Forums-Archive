---
title: "smallest number allowed by my system"
date: 2012-10-04
forum: Programming Talk
---

### Post by IAMTubby on 2012-10-04
Hey,
I have a couple of questions

1)Is there any special variable assigned for the smallest and largest possible numbers allowed by my system ? like int.MinValue, int.MaxValue or something of that sort ?

2)Does it depend on my system alone or does it also depend on my version of gcc ?

Thanks

PS : I have a 64 bit system, running gcc (GCC) 4.1.2 20080704 (Red Hat 4.1.2-52)
What's the smallest and largest numbers that I can get ?

---

### Post by IAMTubby on 2012-10-04
Hey I did this :)
```

#include <stdio.h>
#include <math.h>

int main(void)
{
 //printf("\nLargest possible number = %u",(unsigned int)((pow(2,(double)((sizeof(unsigned int)) * 8)))));
 printf("\nLargest possible number = %d",(int)((pow(2,(double)((sizeof(unsigned int)) * 8)))));

 return 0;
}


```

---

### Post by cipherboy_loc on 2012-10-04
Define smallest for us? On the number line, a negative number would be the smallest, but you could be talking about number of decimal points of accuracy. 

In 32 bits:
Largest unsigned int is (2^32)-1==4294967295
Smallest unsigned int is 0
Largest signed int is (2^31)-1==2147483647
Smallest signed int is -1*(2^31)=-2147483648

64 bits, just change the math to 64/63 from 32 and 31 respectively. 


Thanks,
Cipherboy

---

### Post by IAMTubby on 2012-10-04
> **cipherboy_loc said:**
> Define smallest for us? On the number line, a negative number would be the smallest, but you could be talking about number of decimal points of accuracy. 

In 32 bits:
Largest unsigned int is (2^32)-1==4294967295
Smallest unsigned int is 0
Largest signed int is (2^31)-1==2147483647
Smallest signed int is -1*(2^31)=-2147483648

64 bits, just change the math to 64/63 from 32 and 31 respectively. 


Thanks,
Cipherboy
Thanks Cipherboy :)

---

### Post by Tony Flury on 2012-10-04
in C there are macros defined for these limits : 

[http://en.wikipedia.org/wiki/C_data_types#Interface_to_the_properties_of_the_basic_types](http://en.wikipedia.org/wiki/C_data_types#Interface_to_the_properties_of_the_basic_types)

---


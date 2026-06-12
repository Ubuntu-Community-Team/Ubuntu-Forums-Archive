---
title: "c++ binary writing of array issue"
date: 2010-06-02
forum: Programming Talk
---

### Post by kaspar_silas on 2010-06-02
Hi all,

Hopefully someone can shine some light on this. The following is a short code demo. It sets up three arrays. A large static one, a small dynamic one and a big dynamic one. When I try to write these out it always fails on the big array. Hence the output is:

250000
300000
-1

and the produced file varies in size around 560000 bytes.

So why is the big array failing mid write? I can even put a loop around the small array and run it so that it writes out the same data. Is there limit on the maximum array that be cast or wrote in one block? 

```
#include <fstream>
#include <iostream> 
using namespace std; 
 
 
int main(int argc,char* argv[] )
{
	//Binary write file
	ofstream OUT( "TESTY.bin" , ios::out | ios::binary);

	char sbuf[250000];
	for(int i=0;i<250000;i++)sbuf[i]=0;
	
	//Make small Dynamic Buffer
	short* sdbuf=new short[25000];	
	for(unsigned long i=0;i<25000;i++)sdbuf[i]=0;
	
	//Make Dynamic Buffer
	short* dbuf=new short[250000];	
	for(unsigned long i=0;i<250000;i++)dbuf[i]=0;
	
	//Make Static Buffer	

	
	//Binary writing
	OUT.write( sbuf, sizeof(sbuf) );
	cout<<OUT.tellp()<<endl;
	
	OUT.write( (char*) &sdbuf, 25000*sizeof(short) );
	cout<<OUT.tellp()<<endl;
		
	OUT.write( (char*) &dbuf, 250000*sizeof(short) )<<endl;
	cout<<OUT.tellp()<<endl;
	
	//Tidy up		
	OUT.close();
	if(sdbuf){delete[]sdbuf;sdbuf=0;}
	if(dbuf){ delete[]dbuf; dbuf=0;}
	return 0;
}
```

---

### Post by PmDematagoda on 2010-06-02
> 	OUT.write( (char*) &sdbuf, 25000*sizeof(short) );

		
	OUT.write( (char*) &dbuf, 250000*sizeof(short) )<<endl;

The addresses being provided to write () to obtain the data from is incorrect because what you are passing it is the address of the _pointer_ to the arrays and not the arrays themselves. So since you are obviously going over the boundary in that respect since a pointer is much smaller than 50000 bytes your program is segfaulting. To fix the problem just get rid of the &s. :)

---

### Post by Zugzwang on 2010-06-02
Let's have a look at the following lines:

```

	//Binary writing
	OUT.write( sbuf, sizeof(sbuf) );

```

Here, you write 4 bytes on 32-bit machines and 8 bytes on 64-bit machines to disk, as "sbuf" is a pointer, which has size 4 or 8. 

```

	OUT.write( (char*) &sdbuf, 25000*sizeof(short) );

```

Here, you write 25000*sizeof(short) bytes to disk, starting with the position in memory that holds the pointer to sdbuf. Unless you want the address of a pointer (which does not make sense in this case), omit the "&".

```

        OUT.write( (char*) &dbuf, 250000*sizeof(short) )<<endl;

```

Same here. I hope that I'm not wrong here in any respect and also hope that this helps you!

---

### Post by PmDematagoda on 2010-06-02
> **Zugzwang said:**
> ```

	//Binary writing
	OUT.write( sbuf, sizeof(sbuf) );

```

Here, you write 4 bytes on 32-bit machines and 8 bytes on 64-bit machines to disk, as "sbuf" is a pointer, which has size 4 or 8. 

But because sbuf is actually referring to a static array and not a dynamic array, I think the actual output of the sizeof () is 250000 isn't it?

---

### Post by MadCow108 on 2010-06-02
> **Zugzwang said:**
> Let's have a look at the following lines:

```

	//Binary writing
	OUT.write( sbuf, sizeof(sbuf) );

```

Here, you write 4 bytes on 32-bit machines and 8 bytes on 64-bit machines to disk, as "sbuf" is a pointer, which has size 4 or 8. 


this is the only one which is correct as sbuf is an array and no pointer.
sizeof works on array's (but beware of the implicit conversion to pointers).

---

### Post by Zugzwang on 2010-06-02
> **MadCow108 said:**
> this is the only one which is correct as sbuf is an array and no pointer.
sizeof works on array's (but beware of the implicit conversion to pointers).

Oh, ok, my fault: I mixed "sbuf" with "sdbuf". #-o

---

### Post by kaspar_silas on 2010-06-02
Thanks to all,

You solved the problem and educated me in an amazingly fast time.

---


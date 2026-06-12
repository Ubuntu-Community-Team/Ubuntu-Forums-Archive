---
title: "[c++] Problem with file i/o and a really big number in a file"
date: 2010-04-04
forum: Programming Talk
---

### Post by fasoulas on 2010-04-04
i try to improve my skills on file i\o in c++ so i found a project to do from here 

[http://projecteuler.net/index.php?section=problems&id=8](http://projecteuler.net/index.php?section=problems&id=8)

but the result i get is not correct.

The code as it is below calculates the product 205 times instead of 200 that is the normal times it must to calculate.

i used some information from here [http://www.cplusplus.com/reference/clibrary/cstdlib/atoi/](http://www.cplusplus.com/reference/clibrary/cstdlib/atoi/) about the atoi function.

i have used the atoi function but i don't know if i used it in a correct way as it is the first time i use it.

The code below compiles and runs without problem,but it doesn't do what i want

```
/*
  Program Descripion : Find the greatest product of five consecutive digits in the 1000-digit number.
  WEBSITE : http://projecteuler.net/index.php?section=problems&id=8
 */


#include <iostream>
#include <fstream>
#include <cstdlib>

using namespace std ;

int main() 
{
	//array
	char num[1] ;
	
	//variables
	long int max_product=0 , product ;
	int i , f_num , count=1 , max_pos ;
	
	//open file stream
	fstream inputF("file.txt" , ios::in) ;
	
	while( !inputF.eof() )
	{
		product=1 ;
		
		for(i=0 ; i<5 ; i++)
		{
			num[0] = inputF.get() ;
			
			f_num = atoi(num) ;
			
			product = product * f_num ;
		}
		
		cout << "Product#" << count << " : " << product << endl ;
		
		if(product > max_product)
		{
			max_pos = count ;
			max_product = product ;
		}
		
		count++ ;
	}	//end of While loop
	
	//show the results
	cout << "\nMAX PRODUCT IS : " << max_product ;
	cout << "\nPOSITION : " << max_pos ;
	cout << endl ;
	
	//close file file.txt
	inputF.close() ;
	
	return 0 ;
}

```

so if anyone can help,you are welcomed

---

### Post by falconindy on 2010-04-04
There's a flaw in your logic here. Your while loop will do a maximum of 200 iterations:

0-4
5-9
10-14
...

In reality, there's 995 necessary iterations:

0-4
1-5
2-6
3-7
...

Consider reading the entire file into an array first so that it's easier to pick and choose the range of numbers without worrying about rewinding the stream. An outer loop (OL) then advances one element at a time, and an inner loop advances from OL to OL+4.

Also, because you're dealing with single digits, atoi isn't necessary. I think if you look at a chart of ascii values (man ascii) it should be fairly easy to figure out how to convert an ascii digit to its numerical equivalent.

---

### Post by fasoulas on 2010-04-05
> **falconindy said:**
> There's a flaw in your logic here. Your while loop will do a maximum of 200 iterations:

0-4
5-9
10-14
...

In reality, there's 995 necessary iterations:

0-4
1-5
2-6
3-7
...

Consider reading the entire file into an array first so that it's easier to pick and choose the range of numbers without worrying about rewinding the stream. An outer loop (OL) then advances one element at a time, and an inner loop advances from OL to OL+4.

Also, because you're dealing with single digits, atoi isn't necessary. I think if you look at a chart of ascii values (man ascii) it should be fairly easy to figure out how to convert an ascii digit to its numerical equivalent.

thanks for replying

i tried to save the numbers in the array, but because they are one after the other without whitespaces i couldn't do it

how can i save the numbers in an array?

as for the itterations you are right

---

### Post by falconindy on 2010-04-05
I'm not too familiar with C++ (I prefer C). See [here](http://www.cplusplus.com/reference/iostream/istream/read/) for reading a stream into memory. I would suggest stripping out the newlines from the input file to make this simpler.

---

### Post by Cracauer on 2010-04-05
One big problem right there is char foo[1]. This can only store a zero-length string since you need space for the trailing '\0'. You cannot call atoi(3) on that if you stuffed a character into foo[0], it will run over the end of the string unless you are lucky enough to have a preexisting zero floating around right after it.

As mentioned you also lose on the newlines, presumably you need to silently ignore them. That's where you 5 additional iterations come from.

Optimizations are the point here but let's get the thing base working first.

---


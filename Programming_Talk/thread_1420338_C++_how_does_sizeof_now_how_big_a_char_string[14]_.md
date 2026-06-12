---
title: "C++ how does sizeof now how big a char string[14] is?"
date: 2010-03-02
forum: Programming Talk
---

### Post by Jonas thomas on 2010-03-02
I was going through my chapter in my C++ class on strings and saw this section code that got me thinking.
```

char string1[13]="Hello ";
char string2[14]="World!";
if(sizeof(string1)>=(strlen(string1)+strlen(string2)+1))
    strcat(string1,string2);
else
    cout<<"string1 is not larger enough for both strings";

```

I know what the code is doing, the thing that got me curious is how it does it.

string1 is 13 consecutive spaces in memory where there is a pointer somewhere to that spot in memory. Got that.

strlen makes sense to me, start at the pointer keep going till you hit a \0 you got your length. Easy enough to understand.

sizeof knows how big you string1 is.  How does it know??
Is there a designated stop in memory point to variable and how big they are??  I know there probably a special term that describes this... Just don't know what it is...  This is a beginners C++ class so I suppose that don't want to saute the brain but not melt it. This does have me curious though.  

How does sizeof know how big the string is? I started googling but I wasn't really finding what I needed.  What's the magic search term I need to try?

---

### Post by Simon17 on 2010-03-02
sizeof knows how big the *array* is.

You might want to search "difference between pointers and arrays C++" or something like that.

---

### Post by NovaAesa on 2010-03-02
If I remember correctly, sizeof is evaluated at compile time. So it knows that your array is of type char (so 8 bits) and it's length is x. From that it can work out the size in memory.

---

### Post by NovaAesa on 2010-03-03
Take a look at this [http://en.wikipedia.org/wiki/Sizeof](http://en.wikipedia.org/wiki/Sizeof)

Specifically under the 'Implementation' heading, it explains how it is done.

---

### Post by babyhuey on 2010-03-03
An automatic array such as char string[14] can be easily calculated because both number of and the size of characters on your platform are known. 
However, if the array was dynamic it would be a different story.

Because the size is known at compile time, the compiler replaces "sizeof" with the actual value. I don't believe it runs on the CPU at run-time.

---

### Post by dribeas on 2010-03-03
In C++ it is implemented at compile time. The compiler has to reserve space for each variable, and thus knows the size of that variable. No real magic there.

---

### Post by Jonas thomas on 2010-03-03
> **NovaAesa said:**
> Take a look at this [http://en.wikipedia.org/wiki/Sizeof](http://en.wikipedia.org/wiki/Sizeof)

Specifically under the 'Implementation' heading, it explains how it is done.

Gotta love wikipedia..

> It is the responsibility of the compiler's author to implement the sizeof operator in a way specific and correct for a given implementation of the language. The sizeof operator must take into account the implementation of the underlying memory allocation scheme to obtain the sizes of various datatypes. sizeof is usually a compile-time operator, which means that during compilation, sizeof and its operand get replaced by the result-value. This is evident in the assembly language code produced by a C or C++ compiler. For this reason, sizeof qualifies as an operator, even though its use sometimes looks like a function call. Applying sizeof to dynamic arrays, introduced in C99 is an exception to this rule.

Thank you everyone.  I was playing around with a dynamically sized array in one of my homework assignments but I didn't use sizeof. I'm going to plug a sizeof into it and see what happens in Linux and Windows.  Wiki is a little cryptic there whether or not sizeof works with Dynamic arrays.

---

### Post by dwhitney67 on 2010-03-03
> **Jonas thomas said:**
> Gotta love wikipedia..



Thank you everyone.  I was playing around with a dynamically sized array in one of my homework assignments but I didn't use sizeof. I'm going to plug a sizeof into it and see what happens in Linux and Windows.  Wiki is a little cryptic there whether or not sizeof works with Dynamic arrays.

Can you please define what you mean by "Dynamic" array?

Or chose from one of the following:

1.  char array[14];

2.  char* array = new char[14];

3.  std::vector<char> array;  array.reserve(14);

---

### Post by MadCow108 on 2010-03-03
as where taking of sizeof where probably taking about the fourth variant:

int a[N] // where N is runtime determined

and yes sizeof also works on these in C99 (and I'm pretty sure also in C++98 )
but its not anymore compile time only
the compiler will probably add the same code you would write when using dynamic memory
Remember array convert to pointers when passed into function, thus sizeof then gives a different result.

the code for these kind of allocations is also in glibc
[http://www.gnu.org/s/libc/manual/html_node/Variable-Size-Automatic.html#Variable-Size-Automatic](http://www.gnu.org/s/libc/manual/html_node/Variable-Size-Automatic.html#Variable-Size-Automatic)
But you don't need that anymore since variable sized arrays are standard

---

### Post by Jonas thomas on 2010-03-03
> **dwhitney67 said:**
> Can you please define what you mean by "Dynamic" array?

Or chose from one of the following:

1.  char array[14];

2.  char* array = new char[14];

3.  std::vector<char> array;  array.reserve(14);

Well....
hears some modified homework.

```

int figureOutTotaldaysOff(int numOfEmployees)
{
	//This routine is not bullet proof.
	//It is not designed to handle employee counts greater than the length of the screen
	//Not really a requirement for this example
	// I tried to code like I would in vb. Doesn't work.
	// Needed Dynamic Memory Allocation
	// Ref pgs 534-538 of text book
	// Used: http://www.cplusplus.com/doc/tutorial/dynamic/
	//// Also, in hind site I think I would have use the vector class.
	
	char inputLine[255];
	char inputLine2[255];
	int employeeNum;
    
	int * daysOffForEmployee;
	int totalDaysOff = 0;
	bool canLeaveDo=false;   
	daysOffForEmployee= new (nothrow) int[numOfEmployees]; // nothrow is discussed here:http://www.cplusplus.com/reference/std/new/nothrow/
	cout <<" this is a test to see how size of behaves with a dynamic array" <<endl;
	cout << " sizeof(daysOffForEmployee)  "<< sizeof(daysOffForEmployee) << "    numOfEmployees = "<< numOfEmployees <<endl;
	pauseTheProgamRegardlessOfOs();
	
	
	if (daysOffForEmployee == 0) //With nothrow new operator returns a null pointer instead of throwing an exception
	{
		cout << "Error 20100222630: memory could not be allocated\nZ0 will be returned\nPress Enter to continue"<<endl;
		cin.getline(inputLine,255);
	}
	else
	{
		for (employeeNum=0; employeeNum<numOfEmployees; employeeNum++)
		{
			daysOffForEmployee[employeeNum]=0;//Set everything to zero
		}
		
		// This is a pain... goes alot easier in vb
 		do
		{
				clearScreenRegardlessOfOS();
			cout <<"Employee#  Days Off"<<endl;
			cout <<"---------  --------"<<endl;
			for (employeeNum=0; employeeNum<(numOfEmployees);employeeNum++)
			{
				cout<<setw(5)<<employeeNum<<setw(15)<<daysOffForEmployee[employeeNum]<<endl;
			}
			cout<<"Please enter Employee# or 'Q' to quit\n Employee#";
			cin.getline(inputLine,255);
			if ((strcmp(inputLine,"Q")==0)||(strcmp(inputLine,"q")==0))
			{
				canLeaveDo=true;   
			}
			else 
			{
				if(1 != sscanf(inputLine, "%d", &employeeNum))	   
				{
					cout<< "Was expecting a numeric input!!\n Not >"<<inputLine<<"<"<<endl;
				}
				else
				{
				//we have a valid number in input number at this point
				//we know we have a number lets see if it's between 0 and 100
				if ((employeeNum)>=0 && (employeeNum)<numOfEmployees)
				{
					//we are within an acceptable range.
					bool canLeaveNow=false;
					int daysoff=0;
					do
					{
						cout<<"Please enter days off for employee#"<<employeeNum<<": ";
						cin.getline(inputLine2,255);
						
						if(1 != sscanf(inputLine2, "%d", &daysoff))	   
						{
							cout<< "Was expecting a numeric input!!\n Not >"<<inputLine<<"<"<<endl;
						}
						else
						{
							if (daysoff>=0)
							{
								canLeaveNow=true;
							}
							else
								cout<<"Please end a positive number"<<endl;
						}
					}
					while(canLeaveNow==false);
					daysOffForEmployee[employeeNum]=daysoff;
					
				}
				else
				{
					cout<< "You are outside the range of employee Id's"<<endl;
					cout<<"You entered >"<<inputLine<<"<\n"<<endl;
					//one more round through the loop
				}
			}
		}
	}
	while (canLeaveDo ==false);
		
		for (employeeNum=0; employeeNum<(numOfEmployees);employeeNum++)
			totalDaysOff +=daysOffForEmployee[employeeNum];
		
		if (totalDaysOff != 0)
		{
		
		}
		else
			cout <<"Holly cow no one took a day off"<<endl;
	}
	delete [] daysOffForEmployee;
	return(totalDaysOff);
}	



```

I need to think about this a bit.
Seems like sizeof of allways returns 4 no matter what the input is.
In linux anyway....

---

### Post by dwhitney67 on 2010-03-03
A pointer to a data object, on a 32-bit CPU, will always be 4 bytes long; on a 64-bit CPU, it is 8 bytes long.

Remember the basics... the pointer object contains the address that references the actual data.  The data could be a million bytes in size, but the size of the pointer will always remain constant.

P.S.  In C++, it is customary to declare and initialize your variables at the same time.  For example:
```

int* daysOffForEmployee = new (nothrow) int[numOfEmployees];

```

---

### Post by Jonas thomas on 2010-03-04
> **MadCow108 said:**
> as where taking of sizeof where probably taking about the fourth variant:

int a[N] // where N is runtime determined



Hmmm... I thought I tried that(without success). I need to finish up my project at hand and try this again... when I have a moment.

---


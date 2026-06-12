---
title: "Looping string arrays"
date: 2009-01-15
forum: Programming Talk
---

### Post by jorgeberber on 2009-01-15
ok here it goes, 
What im trying to do is to search in a array for a result, so far so good;
i type a code it will give me a price,  
code1 - price1
code2 - price2
code3 - price3

but then if i want to repeat  
code1 - price1 just wont show 
what im doing wrong here? please help!!!
here is the code 
oh an im a beginner!!!
here is the code

#include <iostream>

using namespace std;
int main()
     {
	int	i=0;
	char str[80];
	char prices[6][80] ={
		"rb38ssw500x500", "200",
		"rb38ssw600x600", "300",
		"rb38ssw700x700", "400"};
	
	
	for( ; ; )
	      {	
		cout<<"Enter Product:";
		cin>> str;
		
		if(!strcmp(str, prices[i]))
		cout<< "Price is :"<< prices[i+1]<< "\n ";
		i+=2;
	}

}


i've tried with do-while loops, while loops, and the for loops was my last try. but they all do the same thing .
thank you.

---

### Post by jpkotta on 2009-01-15
Your "for loop" is a while loop, which is actually probably what you want.  You need another for loop to search through the list.

```

for (i = 0; i < length_of_list; i += 2) {
    if (!strcmp(str, prices[i])) {
        cout<< "Price is :"<< prices[i+1]<< "\n ";
        break;
    }
}

```

---

### Post by jorgeberber on 2009-01-15
so what you saying is that i have to replace this part with the code you posted?
thanks
	
	for( ; ; )
	      {	
		cout<<"Enter Product:";
		cin>> str;
		
		if(!strcmp(str, prices[i]))
		cout<< "Price is :"<< prices[i+1]<< "\n ";
		i+=2;
	}

}

---

### Post by jorgeberber on 2009-01-15
> **jpkotta said:**
> Your "for loop" is a while loop, which is actually probably what you want.  You need another for loop to search through the list.

```

for (i = 0; i < length_of_list; i += 2) {
    if (!strcmp(str, prices[i])) {
        cout<< "Price is :"<< prices[i+1]<< "\n ";
        break;
    }
}

```

This code you gave was actually the first one ive tried, but once i type the first search  it finds and logout , but what i want its to keep going , thats why i used the for( ; ; ) to be infinite , at least i thought it would be;

---

### Post by dwhitney67 on 2009-01-15
@ OP:

Consider declaring a structure to hold your data.  The approach you have chosen is IMPO, poor.  You should design your application to be more flexible, so that if another requirement where thrown at you (e.g. to store the quantity of items in stock per product), then you can easily change your application.

Consider the following, which meets your original requirements as specified in your opening post.
[php]
#include <iostream>
#include <string>

struct CodeInfo
{
  std::string  productCode;
  unsigned int price;          // or use double if you wish
};

int main()
{
  CodeInfo items[3] = { {"rb38ssw500x500", 200},
                        {"rb38ssw600x600", 300},
                        {"rb38ssw700x700", 400}
                      };

  do
  {
    std::string code;

    std::cout << "Enter product code (or ctrl-D to exit): ";
    std::cin  >> code;

    for (size_t i = 0; i < sizeof(items) / sizeof(CodeInfo); ++i)
    {
      if (code == items[i].productCode)
      {
        std::cout << "Price is: " << items[i].price << std::endl;
        break;
      }
    }
  } while (!std::cin.eof());

  return 0;
}
[/php]
With the code shown above, the structure can be augmented as you wish.  You can also add additional fields to the structure as you wish, and perhaps obtain your product information from a file or database so as to populate the structure.

Also, when writing C++ applications, never use the C-style arrays for storing strings; use the STL string.  It is more powerful and helps mitigate silly mistakes that many programmers make (e.g. forgetting to insert a null at the end of the string).

---

### Post by Martin Witte on 2009-01-15
when I compile your program as it is I get error
```
[martin@sony ~]$ cat test.cpp
#include <iostream>

using namespace std;

int main()
{
	int i=0;
	char str[80];
	char prices[6][80] ={
	"rb38ssw500x500", "200",
	"rb38ssw600x600", "300",
	"rb38ssw700x700", "400"};


	for( ; ; )
	{
		cout<<"Enter Product:";
		cin>> str;

		if(!strcmp(str, prices[i]))
		{
			cout<< "Price is :"<< prices[i+1]<< "\n ";
		}
		i+=2;
	}
}
[martin@sony ~]$ g++ test.cpp
test.cpp: In function &#8216;int main()&#8217;:
test.cpp:20: error: &#8216;strcmp&#8217; was not declared in this scope
[martin@sony ~]$ 

```
strcmp can be found in string.h, so adding
```

#include <string.h>

```
fixes this, but it is a better approach to go with dwhitney67 approach of using the stl string class as he did. I would use a map instead of a struct when you have a one to one lookup table, maybe this is a more advanced topic however  
```

#include <iostream>
#include <string>
#include <map>

int main()
{
	std::map<std::string, unsigned int> CodeInfo;
	std::map<std::string, unsigned int>::iterator iter;

	CodeInfo["rb38ssw500x500"] = 200;
	CodeInfo["rb38ssw600x600"] = 300;
	CodeInfo["rb38ssw700x700"] = 400;
	do
	{
		std::string code;

		std::cout << "Enter product code (or ctrl-D to exit): ";
		std::cin  >> code;

		for (iter = CodeInfo.begin(); iter != CodeInfo.end(); ++iter)
		{
			if (code == iter->first)
			{
				std::cout << "Price is: " << iter->second << std::endl;
				break;
			}
		}
	} while (!std::cin.eof());

	std::cout << std::endl;

	return 0;
}
```

---

### Post by Cracauer on 2009-01-16
> **jorgeberber said:**
> 
```

#include <iostream>

using namespace std;
int main()
     {
	int	i=0;
	char str[80];
	char prices[6][80] ={
		"rb38ssw500x500", "200",
		"rb38ssw600x600", "300",
		"rb38ssw700x700", "400"};
	
	
	for( ; ; )
	      {	
		cout<<"Enter Product:";
		cin>> str;
		
		if(!strcmp(str, prices[i]))
		cout<< "Price is :"<< prices[i+1]<< "\n ";
		i+=2;
	}

}

```

i've tried with do-while loops, while loops, and the for loops was my last try. but they all do the same thing .
thank you.

If you want "C-style" looping here's how I would do it.

The point here is not to keep a separate count around. You use an end marker inside the array. That reduces programming errors.

```

#include <stdio.h>

int main(void)
{
  struct names_and_prices {
    char *name;
    char *price;
  } data[] =  {
    {"rb38ssw500x500", "200"},
    {"rb38ssw600x600", "300"},
    {"rb38ssw700x700", "400"},
    {NULL} // end marker
  }, *iterator;


  for (iterator = data; iterator->name; iterator++) {
    printf("%s -> %s\n", iterator->name, iterator->price);
  }

  return 0;
}

```

Note that there are no hardcoded things you can screw up. No hardcoded array size, no hardcoded string lengths, nothing.

Editing the literal data is now completely safe as long as you leave the end marker in.

---


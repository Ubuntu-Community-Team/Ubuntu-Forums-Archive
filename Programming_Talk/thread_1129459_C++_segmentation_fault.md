---
title: "C++ segmentation fault"
date: 2009-04-18
forum: Programming Talk
---

### Post by RunnerBri24 on 2009-04-18
I have to read in a file that has a stock name, the dimension of an array for that stock, then values for that stock. It is a very large file with almost 4,000 stocks. I get a segmentation fault and know that has to do with memory, but beyond that I am clueless. Here is my code followed by the valgrind check which shows what went wrong. I can't tell exactly where the error occurs. Any help on what I am doing wrong and/or where in my code is the problem would be appreciated.

#include <string.h>
#include <stddef.h>
#include <stdio.h>
#include <stdlib.h>
#include "../include/function.h"
#include "../sorting/mergesort.cc"

#define linemax 700 
void merge_sort(int numStocks) {

FILE *fp;   
     fp = fopen("../output/pfChart.txt", "r");   

     if(fp==NULL) {
     printf("Error: can't open file ../output/pfChart.\n");
     exit(1);
     }

  	 char tmpchar;
		 printf("\n");
		 printf("%d \n", numStocks);
     printf("%s \n", "Press any key to move on to mergesort");
		 tmpchar=getchar();
   
     char delimiters[] = " ,";
     char line[linemax];
     int  count=0;
		 int sizeArr;

     char *token;

			int* growth = new int[numStocks];
			int* extra = new int[numStocks];

			char** names = new char* [numStocks];
			char** extra2 = new char* [numStocks];

       while( fgets(line, linemax, fp) !=NULL){
          token=strtok (line, delimiters);   //name
					names[count] = strdup(token);
					token=strtok (NULL, delimiters);   //size
					sizeArr = atof(token);
					growth[count] = 0;
					for(int i = 0; i < sizeArr; i++){
						token=strtok (NULL, delimiters);   //data
						growth[count] += atof(token);
					}				
					count++;
      }

     fclose(fp);


	printf("%-20s", "Original Array:");
      for(int i=0; i<=numStocks-1; i++) printf("%5s", names[i]);

	mergesort(growth, extra, 0, numStocks-1, names, extra2);

		printf("\n");
     printf("%-20s", "Sorted Array:");
     for(int i=0; i<=numStocks-1; i++) printf("%5s", names[i]);
     printf("\n");

}


3817 
Press any key to move on to mergesort 
==5931== Invalid read of size 1
==5931==    at 0x418F933: (within /lib/tls/i686/cmov/libc-2.8.90.so)
==5931==    by 0x418CDC8: strtod (in /lib/tls/i686/cmov/libc-2.8.90.so)
==5931==    by 0x80495AC: merge_sort(int) (in /home/bunty/Desktop/sample_attempt/main/run)
==5931==    by 0x8049140: go() (in /home/bunty/Desktop/sample_attempt/main/run)
==5931==    by 0x8048995: main (in /home/bunty/Desktop/sample_attempt/main/run)
==5931==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==5931== 
==5931== Process terminating with default action of signal 11 (SIGSEGV)
==5931==  Access not within mapped region at address 0x0
==5931==    at 0x418F933: (within /lib/tls/i686/cmov/libc-2.8.90.so)
==5931==    by 0x418CDC8: strtod (in /lib/tls/i686/cmov/libc-2.8.90.so)
==5931==    by 0x80495AC: merge_sort(int) (in /home/bunty/Desktop/sample_attempt/main/run)
==5931==    by 0x8049140: go() (in /home/bunty/Desktop/sample_attempt/main/run)
==5931==    by 0x8048995: main (in /home/bunty/Desktop/sample_attempt/main/run)
==5931== 
==5931== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 17 from 1)
==5931== malloc/free: in use at exit: 61,815 bytes in 93 blocks.
==5931== malloc/free: 11,547 allocs, 11,454 frees, 4,093,623 bytes allocated.
==5931== For counts of detected errors, rerun with: -v
==5931== searching for pointers to 93 not-freed blocks.
==5931== checked 118,572 bytes.
==5931== 
==5931== LEAK SUMMARY:
==5931==    definitely lost: 0 bytes in 0 blocks.
==5931==      possibly lost: 0 bytes in 0 blocks.
==5931==    still reachable: 61,815 bytes in 93 blocks.
==5931==         suppressed: 0 bytes in 0 blocks.
==5931== Reachable blocks (those to which a pointer was found) are not shown.
==5931== To see them, rerun with: --leak-check=full --show-reachable=yes
Segmentation fault

---

### Post by Firestom on 2009-04-18
Where is your code when you get the segmentation fault? It can't help only to say that you have a segmentation fault.

---

### Post by Jiraiya_sama on 2009-04-18
Why are you using 99% C code in C++?  Also, not sure if it would help, but compiling with -g and running the program in gdb usually gives me a ballpark figure of where the segfault occured.

---

### Post by dwhitney67 on 2009-04-18
> **RunnerBri24 said:**
> I have to read in a file that has a stock name, the dimension of an array for that stock, then values for that stock. It is a very large file with almost 4,000 stocks. I get a segmentation fault and know that has to do with memory, but beyond that I am clueless. Here is my code followed by the valgrind check which shows what went wrong. I can't tell exactly where the error occurs. Any help on what I am doing wrong and/or where in my code is the problem would be appreciated.

#include <string.h>
#include <stddef.h>
#include <stdio.h>
#include <stdlib.h>
#include "../include/function.h"
#include "../sorting/mergesort.cc"

#define linemax 700 
void merge_sort(int numStocks) {

FILE *fp;   
     fp = fopen("../output/pfChart.txt", "r");   

     if(fp==NULL) {
     printf("Error: can't open file ../output/pfChart.\n");
     exit(1);
     }

  	 char tmpchar;
		 printf("\n");
		 printf("%d \n", numStocks);
     printf("%s \n", "Press any key to move on to mergesort");
		 tmpchar=getchar();
   
     char delimiters[] = " ,";
     char line[linemax];
     int  count=0;
		 int sizeArr;

     char *token;

			int* growth = new int[numStocks];
			int* extra = new int[numStocks];

			char** names = new char* [numStocks];
			char** extra2 = new char* [numStocks];

       while( fgets(line, linemax, fp) !=NULL){
          token=strtok (line, delimiters);   //name
					names[count] = strdup(token);
					token=strtok (NULL, delimiters);   //size
					sizeArr = atof(token);
					growth[count] = 0;
					for(int i = 0; i < sizeArr; i++){
						token=strtok (NULL, delimiters);   //data
						growth[count] += atof(token);
					}				
					count++;
      }

     fclose(fp);


	printf("%-20s", "Original Array:");
      for(int i=0; i<=numStocks-1; i++) printf("%5s", names[i]);

	mergesort(growth, extra, 0, numStocks-1, names, extra2);

		printf("\n");
     printf("%-20s", "Sorted Array:");
     for(int i=0; i<=numStocks-1; i++) printf("%5s", names[i]);
     printf("\n");

}


3817 
Press any key to move on to mergesort 
==5931== Invalid read of size 1
==5931==    at 0x418F933: (within /lib/tls/i686/cmov/libc-2.8.90.so)
==5931==    by 0x418CDC8: strtod (in /lib/tls/i686/cmov/libc-2.8.90.so)
==5931==    by 0x80495AC: merge_sort(int) (in /home/bunty/Desktop/sample_attempt/main/run)
==5931==    by 0x8049140: go() (in /home/bunty/Desktop/sample_attempt/main/run)
==5931==    by 0x8048995: main (in /home/bunty/Desktop/sample_attempt/main/run)
==5931==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==5931== 
==5931== Process terminating with default action of signal 11 (SIGSEGV)
==5931==  Access not within mapped region at address 0x0
==5931==    at 0x418F933: (within /lib/tls/i686/cmov/libc-2.8.90.so)
==5931==    by 0x418CDC8: strtod (in /lib/tls/i686/cmov/libc-2.8.90.so)
==5931==    by 0x80495AC: merge_sort(int) (in /home/bunty/Desktop/sample_attempt/main/run)
==5931==    by 0x8049140: go() (in /home/bunty/Desktop/sample_attempt/main/run)
==5931==    by 0x8048995: main (in /home/bunty/Desktop/sample_attempt/main/run)
==5931== 
==5931== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 17 from 1)
==5931== malloc/free: in use at exit: 61,815 bytes in 93 blocks.
==5931== malloc/free: 11,547 allocs, 11,454 frees, 4,093,623 bytes allocated.
==5931== For counts of detected errors, rerun with: -v
==5931== searching for pointers to 93 not-freed blocks.
==5931== checked 118,572 bytes.
==5931== 
==5931== LEAK SUMMARY:
==5931==    definitely lost: 0 bytes in 0 blocks.
==5931==      possibly lost: 0 bytes in 0 blocks.
==5931==    still reachable: 61,815 bytes in 93 blocks.
==5931==         suppressed: 0 bytes in 0 blocks.
==5931== Reachable blocks (those to which a pointer was found) are not shown.
==5931== To see them, rerun with: --leak-check=full --show-reachable=yes
Segmentation fault

I second Jiraiya_sama comments; why don't you either stick to programming in C in lieu of C++.  If this little project is for a C++ course, then dispense with the C library calls.  These include:  fopen(), fgets(), strok(), strdup(), atof(), and printf().

Also, it would be helpful if that instead of dealing with 4000 stocks, that you reduce the problem set to say, 10 stocks.

You also stated that for each stock, you have a name (symbol?), the quantity of stocks, and the values (NAVs?).  Would it not be prudent to define a structure to hold this information (for each stock) rather than declare independent arrays.

And while on the topic of arrays, why are you not using an STL container?  Typically an STL vector is a good substitute for a C-style array, but since you need to sort the listing of your stocks, I would recommend either an STL list or an STL map.

If this assignment is for a class, then hopefully the code below is advanced enough so that you won't be able to use it.

```

#include <string>
#include <map>
#include <fstream>
#include <sstream>
#include <algorithm>
#include <tr1/memory>
#include <iostream>


struct Stock
{
  std::string  symbol;
  unsigned int numShares;
  float        value;


  friend std::ostream& operator<<(std::ostream& os, const Stock& s)
  {
    os << "Stock symbol    : " << s.symbol    << '\n'
       << "Number of shares: " << s.numShares << '\n'
       << "Value of Asset  : " << s.value;
    return os;
  }
};

typedef std::tr1::shared_ptr<Stock>     StockPtr;
typedef std::map<std::string, StockPtr> Stocks;    // key = stock symbol, value = StockPtr


void displayStock(const std::pair<std::string, StockPtr>& sp)
{
  std::cout << *(sp.second) << '\n' << std::endl;
}

int main()
{
  std::fstream ifs("stock.dat", std::ios::in);

  if (ifs)
  {
    Stocks      stocks;
    std::string line;

    while (getline(ifs, line))
    {
      StockPtr          stock = StockPtr(new Stock);
      std::stringstream iss(line);
      std::string       strValue;

      getline(iss, stock->symbol, ',');
      iss >> stock->numShares;

      stock->value = 0;

      for (unsigned int ns = 0; ns < stock->numShares; ++ns)
      {
        char  comma;
        float nav;
        iss >> comma >> nav;

        stock->value += nav;
      }

      stocks.insert(std::pair<std::string, StockPtr>(stock->symbol, stock));
    }

    std::cout << "Stock Listings...\n\n";
    std::for_each(stocks.begin(), stocks.end(), displayStock);
  }
}

```

The data file (stock.dat) looks like:
```

MSFT,10,1,2,3,4,5,6,7,8,9,10
CSCO,5,1,2,3,4,5
V,2,1,2

```
Sorry, I was too lazy to type in meaningful data for the stock values.


[COLOR="White"]#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <assert.h>

struct Stock
{
  char         symbol[5];
  unsigned int numShares;
  float        nav;
};

void displayStockPortfolio(const struct Stock* stocks, const unsigned int numStocks);

int main()
{
  unsigned int  numStocks = 0;
  struct Stock* stocks = 0;
  FILE*         fp = fopen("stock.dat", "r");

  if (fp)
  {
    char        line[256] = {0};
    const char* delims    = ",\n";

    while (fgets(line, sizeof(line) - 1, fp))
    {
      if (line[0] == '\n' || line[0] == '#') continue;

      ++numStocks;

      if (numStocks == 1)
      {
        stocks = malloc(sizeof(struct Stock));
      }
      else
      {
        stocks = realloc(stocks, numStocks * sizeof(struct Stock));
      }
      memset(stocks + numStocks - 1, 0, sizeof(struct Stock));

      // get stock symbol
      char* token = strtok(line, delims);
      assert(token != 0);
      strncpy(stocks[numStocks - 1].symbol, token, sizeof(stocks[numStocks - 1].symbol));

      // get number of shares
      token = strtok(0, delims);
      assert(token != 0);
      stocks[numStocks - 1].numShares = atoi(token);

      // compute the total NAV for the shares
      for (unsigned int ns = 0; ns < stocks[numStocks - 1].numShares; ++ns)
      {
        token = strtok(0, delims);
        assert(token != 0);

        stocks[numStocks - 1].nav += atof(token);
      }
    }

    displayStockPortfolio(stocks, numStocks);

    free(stocks);
    fclose(fp);
  }
  else
  {
    return 1;
  }

  return 0;
}


void displayStockPortfolio(const struct Stock* stocks, const unsigned int numStocks)
{
  printf("Stock Portfolio:\n");

  for (unsigned int ns = 0; ns < numStocks; ++ns)
  {
    printf("Symbol      : %s\n"
           "Shares Owned: %u\n"
           "NAV         : %f\n\n",
           stocks[ns].symbol, stocks[ns].numShares, stocks[ns].nav);
  }
}[/COLOR]

---

### Post by RunnerBri24 on 2009-04-19
No the program is supposed to be in C. I guess I'm still confused on the differences between c and c++. I have run the program with only ten stocks and I don't get a segmentation fault. Thats why im so confused

---

### Post by dwhitney67 on 2009-04-19
Well, if you are supposed to write the s/w app in C, replace the 'new' with 'malloc'.  Also, use 'gcc', not 'g++' to compile your application.  If you have issues with your code comments, then compile with the -std=gnu99 option.

If I had to guess what is causing your seg-fault, I would wager that the issue lies within your data file.  There is probably a row of data that indicates a particular number of shares, but for which there is not a corresponding number of values (NAVs).  This will cause strtok() to return null, and thus crash your app when it attempts to perform an atof().

Add the following to your code to verify my theory:
```

...
#include <assert.h>

...
token = strtok(NULL, delimiters);
assert(token != NULL);             /* add this */
sizeArr = atof(token);
...
for(int i = 0; i < sizeArr; i++){
token=strtok (NULL, delimiters); //data
assert(token != NULL);            /* add this */
growth[count] += atof(token);
}
...

```

Go with the idea I provided concerning the use of a structure to represent your data.  It will make your life a lot easier.  If the stock names are indeed stock symbols, then make your stock name a fixed array, say of 5 or 6 characters.  I am not aware of a stock symbol that is more than 4 characters long, but I could be wrong.  Btw, the add't space is for the null termination character.

---

### Post by stroyan on 2009-04-19
A line with over 'linemax' characters would also cause strtok to
return NULL.  Your fgets call would truncate the line.

---

### Post by RunnerBri24 on 2009-04-19
Yeah it was the linemax that did it. I was completely overlooking that. 

Thanks so much for everyones help and I might be on here more in the next next few day.

---

### Post by dwhitney67 on 2009-04-19
> **RunnerBri24 said:**
> Yeah it was the linemax that did it. I was completely overlooking that. 

Thanks so much for everyones help and I might be on here more in the next next few day.

Wow!  You had lines in your data file that were more than 700 characters?  I guess it is possible if the array size for the stock is large.

---

### Post by RunnerBri24 on 2009-04-19
yeah. we were given the last 10 years worth of data on almost 4,000 stocks. we have to open the data, find the closing value, and once the stocks value changes by a certain percent, you record that. for instance if you read in this:

IBM,date,open,10.0,volume
IBM,date,open,10.1,volume
IBM,date,open,10.2,volume
IBM,date,open,10.3,volume
IBM,date,open,10.4,volume
IBM,date,open,10.5,volume

for 5% change, then at the 10.5 day you would add 1 to an array. if it went down 5% you would subtract 1. every time is changes between an increase or decrease the 1 is stored in the next column of an array. so the more a stock fluctuates, the larger the array's length will be. that has to be stored for a point figure chart. I output that array for every stock to the text file that is being read in in the code I have above. so 10 years worth of data, ends up one of them had over 1,000 columns of change.

then we have to compare the difference of time it takes to sort all of the stocks with mergesort and quicksort. so I'm off to implement quicksort now.

thanks again for everyones help

---


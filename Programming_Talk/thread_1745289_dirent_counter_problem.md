---
title: "dirent counter problem"
date: 2011-04-30
forum: Programming Talk
---

### Post by chris200x9 on 2011-04-30
I'm using dirent to parse every file in a directory like so:

```
#include<stdio.h>
#include<cstdlib>
#include<iostream>
#include<string.h>
#include<fstream>
#include<dirent.h>
#include "AvlTree.h"
//#include "AvlTree.cxx"

int setArticleNumber(string, int);

using namespace std;
int main(int argc, char **argv)
{
	int counter = 0;
	AvlTree<string> keywords;
	int articlenumber;
	ifstream infile;
string x;
		DIR *pDIR;
        struct dirent *entry;
        if( pDIR=opendir("/home/chris200x9/documents") ){
                while(entry = readdir(pDIR)){    
	 if( strcmp(entry->d_name, ".") != 0 && strcmp(entry->d_name, "..") != 0 )
                        
                        infile.open (entry->d_name, ifstream::in);
                        setArticleNumber(entry->d_name, counter);  
                        while (!infile.eof()) 
                        {
							infile >> x;
							keywords.insert(x, counter);
							
							
						
					}

  infile.close();
  counter++;
                }
                closedir(pDIR);

                cout << keywords.find("propeller");
        }

	
	return 0;
}

int setArticleNumber(string article, int count)
{
	string articles[50];
	
	articles[count] = article;
	
}

```

Dirent is listing all files in a random order so I thought why not put a counter that makes each file corrispond to the file name, I'm making a mini search engine. I'm trying to increase count by one everytime a single file closes, but not after the whole directory is read. It seams no matter where I put count++ I get a seg fault. Any help is much appreciated.

---

### Post by PaulM1985 on 2011-05-01
It does not look like your counter actually does anything useful.  You have a setArticleNumber which creates an array and adds a string at a certain index and then array is deleted because it falls out of scope.

It looks like the counter is incremented in the right position for you to increment after every file closes.

Have you added print statements to find where the code gets to and the general flow of you application?

Paul

---

### Post by chris200x9 on 2011-05-01
yes I've added to the code I have this now ```
#include<stdio.h>
#include<cstdlib>
#include<iostream>
#include<string.h>
#include<fstream>
#include<dirent.h>
#include "AvlTree.h"
//#include "AvlTree.cxx"

int setArticleNumber(string, int);

using namespace std;
int main(int argc, char **argv)
{
	int counter = 0;
	AvlTree<string> keywords;
	int articlenumber;
	ifstream infile;
string x;
		DIR *pDIR;
        struct dirent *entry;
        if( pDIR=opendir("/home/chris200x9/documents") ){
                while(entry = readdir(pDIR)){    
	 if( strcmp(entry->d_name, ".") != 0 && strcmp(entry->d_name, "..") != 0 )
                        
                        infile.open (entry->d_name, ifstream::in);
                        setArticleNumber(entry->d_name, counter);  
                        while (!infile.eof()) 
                        {
							infile >> x;
							keywords.insert(x, counter);
							
							
						
					}

  infile.close();
  //counter++;
                }
                closedir(pDIR);

                //cout << keywords.find("propeller");
        }

	
	return 0;
}

int setArticleNumber(string article, int count)
{
	string articles[50];
	
	articles[count] = article;
	cout << endl;
	cout << articles[0];
	
}

```

it prints out every article name since articles[0]] is rewritten an printed out for every article, it works fine. But I want to uncomment counter++ so that it increments so article 1 is associated with articles[0] article 2 articles[1] and so on. However just uncommenting counter++ ends in a seg fault, I have no idea why.

---

### Post by chris200x9 on 2011-05-01
```
#include<stdio.h>
#include<cstdlib>
#include<iostream>
#include<string.h>
#include<fstream>
#include<dirent.h>
#include "AvlTree.h"
//#include "AvlTree.cxx"

int setArticleNumber(string, int);

using namespace std;
int main(int argc, char **argv)
{
	int counter = 0;
	AvlTree<string> keywords;
	int articlenumber;
	ifstream infile;
string x;
		DIR *pDIR;
        struct dirent *entry;
        if( pDIR=opendir("/home/chris200x9/documents") ){
                while(entry = readdir(pDIR)){    
	 if( strcmp(entry->d_name, ".") != 0 && strcmp(entry->d_name, "..") != 0 )
                     {   
                        infile.open (entry->d_name, ifstream::in);
                        setArticleNumber(entry->d_name, counter);
					}  
                        while (!infile.eof()) 
                        {
							infile >> x;
							keywords.insert(x, counter);
							
							
						
					}

  infile.close();
  counter++;
                }
                closedir(pDIR);

                //cout << keywords.find("propeller");
        }

	
	return 0;
}

int setArticleNumber(string article, int count)
{
	string articles[52];
	
	articles[count] = article;
	cout << endl;
	cout << articles[count];
	
	
}
```

I have it worked out, but Iwould like someone to explain to me why I need an array of 52 when I only have 50 articles. I thought because of my if . and .. shouldn't be inclued?

---

### Post by dwhitney67 on 2011-05-01
> **chris200x9 said:**
> ```

I have it worked out, but Iwould like someone to explain to me why I need an array of 52 when I only have 50 articles. I thought because of my if . and .. shouldn't be inclued?

What have you *worked* out??

You function declares a local variable, which is an array that is dependent on the value of a variable (counter) that is passed in.  The function serves no purpose other than to output to standard-out some string that you pass in to the function.  What's the purpose of this?

Take this less than ideal piece of code:
[code]
int setArticleNumber(string article, int count)
{
	string articles[52];          // local variable; gets destroyed when function exits
	
	articles[count] = article;    // ho-hum; what's the point.
	cout << endl;                 // here a newline is printed, and stream is flushed.
	cout << articles[count];      // here a string is printed, but stream is NOT flushed.
}

```
and reduce it to:
```

int setArticleNumber(const string& article)
{
	cout << article << endl;      // cut to the chase... print string and newline.
}

```
Now ask  yourself... are the results significantly different?

Try fixing the indentation on your code, thus making it easier to analyse.  Also consider whether it is really necessary to have the setArticleNumber() function.  From what is discussed above, it would appear that is serves no real purpose.

---

### Post by Arndt on 2011-05-02
> **chris200x9 said:**
> ```
#include<stdio.h>
#include<cstdlib>
#include<iostream>
#include<string.h>
#include<fstream>
#include<dirent.h>
#include "AvlTree.h"
//#include "AvlTree.cxx"

int setArticleNumber(string, int);

using namespace std;
int main(int argc, char **argv)
{
	int counter = 0;
	AvlTree<string> keywords;
	int articlenumber;
	ifstream infile;
string x;
		DIR *pDIR;
        struct dirent *entry;
        if( pDIR=opendir("/home/chris200x9/documents") ){
                while(entry = readdir(pDIR)){    
	 if( strcmp(entry->d_name, ".") != 0 && strcmp(entry->d_name, "..") != 0 )
                     {   
                        infile.open (entry->d_name, ifstream::in);
                        setArticleNumber(entry->d_name, counter);
					}  
                        while (!infile.eof()) 
                        {
							infile >> x;
							keywords.insert(x, counter);
							
							
						
					}

  infile.close();
  counter++;
                }
                closedir(pDIR);

                //cout << keywords.find("propeller");
        }

	
	return 0;
}

int setArticleNumber(string article, int count)
{
	string articles[52];
	
	articles[count] = article;
	cout << endl;
	cout << articles[count];
	
	
}
```

I have it worked out, but Iwould like someone to explain to me why I need an array of 52 when I only have 50 articles. I thought because of my if . and .. shouldn't be inclued?

The indentation of the code is insane. If you fix it, you will see that your test for . and .. does not affect the counter incrementing.

---


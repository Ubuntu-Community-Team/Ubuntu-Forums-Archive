---
title: "c++ read from file question"
date: 2008-03-13
forum: Programming Talk
---

### Post by mordi05 on 2008-03-13
Hi.
I am quite new to c++, but I figured I'd like to learn it so I'm playing around with some things.

Currently I am trying to read from a text file with the following content:

"city1", "city2", "city3"...

i.e. a file with several strings in "" separated with commas. I would like to store each of these strings into a cell in an array. (Rewriting the text file format is out of the question, because really there are thousands of strings in it).

So far I am using this code:

> ifstream inFile;  // Declaring an input file stream (ifstream) variable.
	
	inFile.open("/home/..../test2.txt");
		
               if (!inFile) {                                                       // Checking that the file could be read
    		cerr << "Unable to open file test2.txt";
    		exit(1);                                                             // call system to stop
		}
	
	while (inFile >>  x){ // read from the stream
  	
	}
		
	inFile.close(); // Closing the input stream to free memory

Now, the problem is obviously the (inFile >>) command. I dont know how to use syntax so the that I load each string from the file into a separate array cell. All I have been able to do is load all the text in the textfile into a single variable at once. (of course, while using another, shorter  textfile).

Any help is appreciated, thanks.

---

### Post by LaRoza on 2008-03-13
Any reason you are using C++? That is not the most useful language for text processing...

---

### Post by mordi05 on 2008-03-13
Not for this, no.
I want to learn some c++, and this is just part of one of many different "problems" i found on a website.

---

### Post by dempl_dempl on 2008-03-13
```

while (   !inFile.eof()  ){ // read from the stream
inFile >> x;
}

```


You don't need the following :  
```

inFile.close(); // Closing the input stream to free memory

```

ifstream destructor does the job when exiting from function.  

You should get used to close files without  *close()*  method , for example in the stuff like **try/catch** blocks. But,   don't worry about that for now ,   you'll see it  yourself in practice .

---

### Post by mordi05 on 2008-03-13
Thanks a lot. That gets me further.
But, should it not be  **!** inFile.eof() ?

This function reads one character at a time, right. I would like to be able to read an entire string at time. i.e first read out: "Washington", second read out: "Chicago" etc. They are separated with commas in the file.

If I'm missing something obvious, please bear with me.

---

### Post by dempl_dempl on 2008-03-13
Yeap, sorry, my bad :-)  .
I've corrected the post.


Show me the file.txt , the way it looks like .
(1) If the names are placed in sequence :
 e.g.      :

```

  Belgrade Washington Paris Moscow 

```
 
You can do this:

```


string str;
ifstream fin ( "myfile");
while ( !fin.eof()  )
{
   fin >> str;
 /*do something usefull here :-)*/
}

```


In the case cities are  separated by  quotes and commas , I can give you this hint  : 
I believe you don't need commas when you have quotes, and you don't need quotes when you have commas , because both of them are good separators.  I would use the commas or newlines ( "\n" )

I haven't checked the code, please post if you find something wrong .  Spelling and grammar errors are exception :-)   .

Drop the file , the way it looks like, in order to give you precise instructions.

Cheers!

---

### Post by mordi05 on 2008-03-13
```
"Kaneohe","Kapolei","Salt Lake","Ewa Beach","Manoa"
```
This is what the file looks like. And it goes on of course.

EDIT: And all the text is in one line.

---

### Post by SledgeHammer_999 on 2008-03-13
look here for more info on I/O with C++ [link](http://cplusplus.com/doc/tutorial/files.html).

If you try the above example then you will read the text file line-by-line. Each time you read a line into a "string" variable you should parse the string variable. Eg search the string for **,** and **"**.

More info for string's method [here](http://cplusplus.com/reference/string/string/)

---

### Post by mordi05 on 2008-03-13
Thanks, I will definitely check that out.

I guess I was just hoping that since

char *cities[3]={"bergen","london","madrid"};

is a valid statement, and on the same format as my file, I could in a crude way get my file to be loaded as those initializers.

I'll get some sleep now, but if anyone has a great idea, I'd love to wake up to it.

---

### Post by dempl_dempl on 2008-03-13
Ok, I thought there were spaces between the cities. 

Here's the code that will work:

```


#include <list>
#include <string>
#include <fstream>

using namespace std;

char ch;


ifstream fin ( " myfile.txt" );
list<string> cities;

string tmp_str;

while(  !fin.eof() ) 
{
 fin.read(&c,1);
 
 if( c == ',') 
 {
   tmp_str.erase( tmp_str.begin() ) ; // erase the first character ( the opening quote )
   tmp_str.erase( tmp_str.end() ) ; // erase the lase character ( the closing quote )

   cities.push_back(  tmp_str );
   tmp_str.clear();
   
 }

tmp_str = tmp_str + c;

}


```


Example usage of those strings : 

```

for(  list< string >::iterator  ii = cities.begin() ; ii != cities.end() ; ii++ )
  cout << *ii  << endl; // print the current city


```

---

### Post by mordi05 on 2008-03-14
Thank you very much, sir. That works quite well.

I had to make some minor adjustments to the **if** loop though.

```
 if( c == ',') 
 {	
   	tmp_str.erase( tmp_str.begin() ) ; // erase the first character ( the opening quote )
  	tmp_str.erase( tmp_str.begin() ) ;
	tmp_str.erase( tmp_str.end()-1 ) ; // erase the lase character ( the closing quote )
 	cities.push_back(  tmp_str );
	tmp_str.clear();
  
 }
```
I added the -1 because it turns out that it is the last character of the string. And I added an extra erase( tmp_str.begin() ), because the "," is also added to the start of the next string. This only pose a problem for the very first string now, but I'll be able to solve that.

Again thanks a lot for taking the time to provide a clever solution.

---

### Post by dempl_dempl on 2008-03-14
He he, I can hardly be a sir, I'm only 22 years old :-) . You're welcome  :-)

and , I almost forgot, 

Yeah, don forget to add last    
addition to list after a while loop ( Add a last city )

```


#include <list>
#include <string>
#include <fstream>

using namespace std;

char ch;


ifstream fin ( " myfile.txt" );
list<string> cities;

string tmp_str;

while(  !fin.eof() ) 
{
 fin.read(&c,1);
 
 if( c == ',') 
 {
   tmp_str.erase( tmp_str.begin() ) ; // erase the first character ( the opening quote )
   tmp_str.erase( tmp_str.end() ) ; // erase the lase character ( the closing quote )

   cities.push_back(  tmp_str );
   tmp_str.clear();
   
 }

tmp_str = tmp_str + c;

}

**cities.push_back( tmp_str ); **    //  <<-- this is a new thingie. LAst city doesn't end with    ","  



```

---


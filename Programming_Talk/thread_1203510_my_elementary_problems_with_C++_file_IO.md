---
title: "my elementary problems with C++ file IO"
date: 2009-07-03
forum: Programming Talk
---

### Post by sp0tz on 2009-07-03
so I've made a simple game here and there; nothing fancy. The most impressive thing I've got is a dude that walks around a map at a steady 60 fps. oh and there are doors that lead to other maps.

Anyways, I'd like to be able to store data in files, so as to have some stuff persist after the program closes. This is what I've got so far:

```
#include <fstream>
#include <iostream>
using namespace std;

int main()
{

	FILE *fp;
	fp = fopen ("config_file.cfg","a+");/*using a+ becuase r , w , r+ and w+ blank the file out before writing to it.*/

	fprintf(fp,"I dunno, whatever.\n");/*for some reason, this ALWAYS writes to the end of the file, even if you call rewind(fp) right before calling this command. I was curious, so I used several commands to move the pointer around, and then cout-ed the pointer's position. All of these cout calls return the same value.*/
	cout<<fp<<endl;
	rewind(fp);
	cout<<fp<<endl;
	fseek(fp,0,0);
	cout<<fp<<endl;
	fseek(fp,0,1);
	cout<<fp<<endl;
	fseek(fp,0,2);
	cout<<fp<<endl;


	fclose (fp);

	cout << "\n\n";
	cout<< "success! I think. \n";
	return 0;
}

 
```

Clearly I'm having trouble writing to anywhere but the end of the file. So currently I can make a file that looks like this:
```

name = dude
total_correct_answers = 4
total_questions_answered = 5
```
but I cannot change just one line of it without rewriting the whole thing. Also, how do you, for instance, at the beginning of the program, set int total_correct_answers to whatever the correlating entry is in the config file?

---

### Post by MadCow108 on 2009-07-03
why not use c++ streams? its much easier.

```

using namespace std;
int main()
{
	int value=5;
	string str="bla";
	ofstream file ("file.txt");
	file << "identifier " << value << endl;
	file << "identifier2 " << str<<" " << 53 << endl;
        file.close();
	
	int readint1=0,readint2=0;
	string readstr="";
	ifstream file2 ("file.txt");
	string dummy;
	while(file2>>dummy)
	{
		if (dummy == "identifier") file2 >> readint1;
		if (dummy == "identifier2") file2 >> readstr >> readint2;
	}
        file2.close();
	std::cout << readint1<<" "<<readstr<<" "<<readint2 << std::endl;
}

```
also note the std::getline() function to read whole lines into a c++ string
the streams and getline(..,delimiter) are also very useful to tokenize your strings (->stringstreams)

here's a tutorial for random access files in c++
[http://cplus.about.com/od/learning1/ss/random.htm](http://cplus.about.com/od/learning1/ss/random.htm)
but rewritting the whole file is mostly the easiest way and enough for configuration files.
for bigger amounts of data you might also consider using a database

---

### Post by sp0tz on 2009-07-03
Cool. Thanks for the link, I'll check that out. The syntax of fprintf, fopen, etc looked simpler, but I'll take a look at this binary file method.

---

### Post by unknownPoster on 2009-07-03
> **sp0tz said:**
> Cool. Thanks for the link, I'll check that out. The syntax of fprintf, fopen, etc looked simpler, but I'll take a look at this binary file method.

fprintf, fopen, etc. are all valid C "verbs" not C++ :)

---

### Post by nvteighen on 2009-07-04
> **unknownPoster said:**
> fprintf, fopen, etc. are all valid C "verbs" not C++ :)
Also, mixing C and C++ like that can be really bad... Just stick to C++ streams.

---

### Post by sp0tz on 2009-07-04
hey can someone point me in the right direction as to how to tell the two apart? I've read several books and such, and all I know is that 

C strings are different than C++ strings (c ones are like char arrays, i think)

C++ is object oriented (though I haven't gotten deep enough in the pool to use structs(c) classes(c++) or objects(c++))

source files are named whatever.c or whatever.cpp for c/c++ respectively

---


---
title: "stat() - casting string as const char * array[]"
date: 2010-10-06
forum: Programming Talk
---

### Post by akvino on 2010-10-06
I would like a user to specify the file, then I can use it in the stat() command. Bottom line thus far is converting string to char array[]. I can do it with array, but it would be unwise to use char array[1024] to just take the name of the file before sending it to stat().

How do I make this work with string:
[PHP]#include <sys/stat.h>
#include <unistd.h>
#include <time.h>
#include <iostream>
#include <string>

using namespace std;

int main(){
		
	struct tm* clock;				// create a time structure
	
	struct stat attrib;			// create a file attribute structure
        
	stat("seconds", &attrib);		// get the attributes of afile.txt
	
	//clock = gmtime(&(attrib.st_mtime));	// Get the last modified time and put it into the time structure
	
	cout << "Stat returns "<< attrib.st_mtime<<endl ;

	char filename[20]={0};
	cout<<"\nEneter filename: "<<endl;
	cin>>filename;
	cout<<"\nYou enetered "<< filename << endl;
	stat(filename, &attrib);
	cout<<"\nFilename mod time is "<<attrib.st_mtime<<endl;
	

	
	
	
	return 0;
}[/PHP]

---

### Post by spjackson on 2010-10-06
```

    std::string filename = "afile.txt";

    stat(filename.c_str(), &attrib);

```

---

### Post by akvino on 2010-10-06
It works - thanks.




[PHP]
#include <sys/stat.h>
#include <unistd.h>
#include <time.h>
#include <iostream>
#include <string>


using namespace std;

int main(){
		
	struct tm* clock;				// create a time structure
	
	struct stat attrib;			// create a file attribute structure
        
	stat("seconds", &attrib);		// get the attributes of afile.txt
	
	//clock = gmtime(&(attrib.st_mtime));	// Get the last modified time and put it into the time structure
	
	cout << "Stat returns "<< attrib.st_mtime<<endl ;
	
// clock->tm_year returns the year (since 1900)
	
// clock->tm_mon returns the month (January = 0)
	
// clock->tm_mday returns the day of the month

	char filename[20]={0};
	cout<<"\nEneter filename: "<<endl;
	cin>>filename;
	cout<<"\nYou enetered "<< filename << endl;
	stat(filename, &attrib);
	cout<<"\nFilename mod time is "<<attrib.st_mtime<<endl;
	
	string file2;
	cout<<"\nEneter filename: "<<endl;
	cin>>file2;
	cout<<"\nYou enetered "<< file2 << endl;
	stat(file2.c_str(), &attrib);
	cout<<"\nFilename mod time is "<<attrib.st_mtime<<endl;
	
	return 0;
}

[/PHP]

---


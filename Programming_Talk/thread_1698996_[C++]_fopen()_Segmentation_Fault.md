---
title: "[C++] fopen() Segmentation Fault"
date: 2011-03-03
forum: Programming Talk
---

### Post by dodle on 2011-03-03
According to the [documentation of fopen](http://www.cplusplus.com/reference/clibrary/cstdio/fopen/) if it cannot open a file a NULL pointer is returned. But my program crashes with a segmentation fault if I try to open a file that doesn't exist. Shouldn't it just return the NULL pointer? Do I have to test for the file's existence before I can use fopen?

[php]// Opening a binary file

#include <iostream>
#include <stdio.h>
using namespace std;

int main()
{
    FILE *file;
    if (file = fopen("dogs", "rb")) // Crashes here because "dogs" does not exist
    {
        cout << "Opened file\n";
        fclose(file);
        return 0;
    }
    
    cout << "Failed to open file\n";
    fclose(file);
    return 1;
}[/php]

[quote=C++ Reference http://www.cplusplus.com][SIZE="4"]
Return Value[/SIZE]

If the file has been succesfully opened the function will return a pointer to a FILE object that is used to identify the stream on all further operations involving it. Otherwise, a null pointer is returned.[/quote]


**[size=4][color=red]SOLVED:[/color][/size]** Okay, I see in the documentation that when using the "r" mode in fopen the file must exist:

> Mode:
"r" | Open a file for reading. The file must exist.

---

### Post by mdurham on 2011-03-03
> **[size=4][color=red]SOLVED:[/color][/size]** Okay, I see in the documentation that when using the "r" mode in fopen the file must exist:

Which documentation says that it 'must' exist? I think if the file doesn't exist fopen() will fail. Could the problem be that you are trying to fclose(NULL) ?

---

### Post by ve4cib on 2011-03-03
> **mdurham said:**
> Which documentation says that it 'must' exist? I think if the file doesn't exist fopen() will fail. Could the problem be that you are trying to fclose(NULL) ?

If you are opening a file for *reading* and the file does not exist fopen will fail (return NULL).  If you are opening a file for *writing* then the file will be created if it does not exist.  Different behaviour for different modes.

---

### Post by stchman on 2011-03-03
This will work better for you:


[php]
// Opening a binary file 

#include <iostream> 
#include <stdio.h> 
using namespace std; 

int main( int argc, char *argv[] ) 
{ 
    FILE *file; 
    if( ( file = fopen( "dogs", "rb" ) ) == NULL ) // checks to see if file dogs exists
    { 
        cout << "File not found\n";
        
        // exit the program
        return 1; 
    }
    else
    {
        cout << "File opened\n";
    }
    
    // close the file
    fclose( file ); 
    return 0; 
}  
[/php]I have compiled this program ( g++ -o <program_name> <program_source> ) and it does indeed run.

---

### Post by dodle on 2011-03-03
You are all right. I could have sworn the segfault was coming from fopen.

---


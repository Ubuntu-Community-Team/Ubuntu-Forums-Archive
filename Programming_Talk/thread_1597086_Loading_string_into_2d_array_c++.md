---
title: "Loading string into 2d array c++"
date: 2010-10-14
forum: Programming Talk
---

### Post by shawnjones on 2010-10-14
Hello everyone.

I am trying to load a text file and load each line into an array. There is an example of the text file below. I am trying to load each line into an array element and add another row to the array every 8 lines. Essentially add a row each time the date is changed in the text file. (Sorry, having problems explaining) 

The ultimate goal is to find the numbers the occur the most in the text file. I would like to keep the date in the array but I feel that I should start just getting the numbers in the array. 

Thanks for any ideas and I'm sorry for the ugly code.

- Shawn


Example of the text file, this has a few thousand lines to it:

```
10/13/10
1
2
32
35
38
47
X3
04/14/10
7
9
10
24
32
52
X4
```

Here is the ugly code, mainly cut and paste from different sources. The comments is usually the voice in my head. :)

```
#include <iostream>
#include <stdio.h>
#include <stdlib.h>
#include <fstream>
#include <string>

using namespace std;

int numLines; // Number of lines in the text file
int ch;
const int maxChar = 7; // Max number of col in each row

int countLines() // function to count the line in the text file
{
    int ch = 0; numLines = 0;
    FILE *fd;

    if (!(fd = fopen("../../../lottery/inFile.txt", "r")))
    {
        fputs("Could not open file!\n", stderr);
        exit(EXIT_FAILURE);
    }

    while ((ch = fgetc(fd)) !=EOF)
    {
        if (ch == '\n'); ++numLines;
    }

    fprintf(stdout, "The Number of Lines->%d\n", numLines);

    fclose(fd);
    return(numLines);

}


int main()
{
    countLines();
    fprintf(stdout, "Now print from main->%d\n", numLines); // Just to make sure the function is passing numLines to main

    int GetIntVal()
    string str[maxChar][numLines];
    ifstream myfile("../../../lottery/inFile.txt");
    int a = 0;
    int b = 0;
    if(!myfile) //Always test the file open.
    {
                cout<<"Error opening output file"<<endl;
                system("pause");
                return -1;
    }
    while(!myfile.eof()) // I think this is while myfile is NOT at eof "end of file"
    {
      getline(myfile,str[a][b],' '); // Is this where we are loading into the array?
      if(a == maxChar) // Check if we should have more to do
      {
           a=0; // Reset to first col
           ++b; // add a new row
           getline(myfile,str[a][b],' '); // Are we loading the array again?
      }
      a++; // Go to next element in the row
    }









    return 0;
}


```

---


---
title: "Help with displaying struct contents"
date: 2007-04-05
forum: Programming Talk
---

### Post by n0dl on 2007-04-05
Hello there, Im playing with structs in order further my skills in c++ and so far it seems pretty strait forward. So far my program seems to work fine until the very end where I have to display the contents of the structs. The contents display just fine but, when I try to format the output it works for the first item but subsequent items are simply displayed with no format. Here is the data file that the program reads from, the source code, and a sample of the output (which is at the bottom of the source).
The Data file:
```

John | 25 | 2.5
Bill | 33 | 3.3
Jack | 18 | 2.8
Mary | 19 | 3.1
Tom | 27 | 2.7

```
The Source and sample output
```

#include <iostream>
#include <cstring>
#include <iomanip>
#include <fstream>

using namespace std;

struct Person
{
    char Name[10];
    int Age;
    float GPA;
};

void DisplayData(char filename[]);
void CopyToArray(Person a[], char filename[]);
void DisplayRecords(Person a[]);
int FindTeens(Person a[]);
void DisplayHighGPA(Person a[]);
void FindMaxMin(Person a[], int & mxage, int & mnage);

int main()
{
    //Display file data.txt
        cout<<"This is the content of the file\n";
        DisplayData("data.txt");

    //Copy records from file to array Students
        Person Students[5];
        CopyToArray(Students, "data.txt");

    //Display array Students
        cout<<"This is the content of array\n";
        DisplayRecords(Students);

    //Count and return the number of teenagers
        int NumOfTeens = FindTeens(Students);
        cout<<"\nThere are "<<NumOfTeens<<" teenagers\n";

    //Display the name and GPA of students with GPA>=3.0
        DisplayHighGPA(Students);

    //Find the max and min age
        int MaxAge, MinAge;
        FindMaxMin(Students, MaxAge, MinAge);
        cout<<"Oldest age is: "<<MaxAge;
        cout<<" and the yougear is: "<<MinAge<<endl;
    //terminate program
        return 0;
}

//---------------------------DisplayData-------------------------------
//This function displays content of the file data.txt
//---------------------------------------------------------------------
void DisplayData(char filename[])
{
    ifstream f;
    f.open(filename);
    string name; int age; float GPA;
    cout<<"\t  Name\tAge\tGPA\n";
    cout<<"\t----------------------------\n";
    while(true)
    {
        f>>name; f.ignore(80, '|');
        f>>age; f.ignore(80,'|');
        f>>GPA;
        
        if(f.fail())
        {
            break;
        }
 
        
        cout<<"\t  "<<name<<"\t"<<age<<"\t"<<GPA<<endl;
     }
    f.close();
    cout<<endl;
}

//-------------------Copy To Array--------------------------------------
//This function copies data from the file "data.txt" to an array
//----------------------------------------------------------------------
void CopyToArray(Person a[], char filename[])
{
    int i; ifstream f;
    f.open(filename);
    for(i = 0; i < 5; ++i)
    {
        f.getline(a[i].Name, 10, '|');
        f>>a[i].Age; f.ignore(80, '|');
        f>>a[i].GPA;
    }
}

//-------------------Display records------------------------------------
//This function displays the contents of the a given struct
//----------------------------------------------------------------------
void DisplayRecords(Person a[])
{
     int i;
     cout<<"\t  Name\tAge\tGPA\n";
     cout<<"\t-------------------------";
     for(i = 0; i < 5; ++i)
     {
          cout<<"\t  "<<a[i].Name<<"\t"<<a[i].Age<<"\t"<<a[i].GPA;
     }
     cout<<endl;
}

//-------------------FindTeens-----------------------------------------
//This funcion counts how many teens there are in a group of people
//---------------------------------------------------------------------
int FindTeens(Person a[])
{
    int i, teen_counter;
    teen_counter = 0;
    for(i = 0; i < 5; ++i)
    {
        if(a[i].Age >= 13 && a[i].Age <= 19)
        {
            ++teen_counter;
        }
    }
    return teen_counter;
}

//------------------DisplayHighGPA------------------------------------
//This function displays students who's GPA is higher than 3.0
//--------------------------------------------------------------------
void DisplayHighGPA(Person a[])
{
    int i;
    cout<<"List of students with GPA>=3.0\n";
    cout<<"\t  Name\tGPA\n";
    cout<<"\t-----------------------\n";
    for(i = 0; i < 5; ++i)
    {
        if(a[i].GPA >= 3.0)
        {
            cout<<"\t"<<a[i].Name<<"\t"<<a[i].GPA;
        }
    }
    cout<<"\n";
} 

//----------------Find Maximum and Minimum---------------------------
//This function displays the oldest and youngest students
//-------------------------------------------------------------------
void FindMaxMin(Person a[], int & mxage, int & mnage)
{
    int i;
    mxage = a[0].Age;
    mnage = a[0].Age;
    for(i = 1; i < 5; ++i)
    {
        if(a[i].Age > mxage)
        {
            mxage = a[i].Age;
        }
        if(a[i].Age < mnage)
        {
            mnage = a[i].Age;
        }
    }
}

/*---------------------output---------------------------------------
This is the content of the file
          Name  Age     GPA
        ----------------------------
          John  25      2.5
          Bill  33      3.3
          Jack  18      2.8
          Mary  19      3.1
          Tom   27      2.7

This is the content of array
          Name  Age     GPA
        -------------------------
          John  25      2.5       
Bill    33      3.3       
Jack    18      2.8       
Mary    19      3.1       
Tom     27      2.7
There are 2 teenagers
          Name  GPA
        -----------------------

Bill    3.3
Mary    3.1

Oldest age is: 33 and the yougear is: 18
------------------------------------------------------------------*/

```
As you can see when displaying the contents of the array John's information displays just fine but the other elements are not displayed. Furthermore when it comes to displaying the Highest GPAs (Bill and Mary) it doesnt even format the first. Some of the things I have tried is changing the \t escape character with plain spaces, adding a cout<<"\t" after the output statement in the forloop in functions DisplayRecords and the GPA function. Ive been looking at the source trying to figure out whats wrong for quite some time now. Any help would be appreciated

EDIT:Fixed

---

### Post by WW on 2007-04-05
Instead of the **quote** environment, enclose your program and your sample output in a **code** environment.  That should preserve the spacing.

I don't think using '\t' is a useful method for formatting the output.  Instead, use the **setw(width)** IO manipulator.  See, for example,
[http://www.cprogramming.com/tutorial/iomanip.html](http://www.cprogramming.com/tutorial/iomanip.html)
or
[http://www.fredosaurus.com/notes-cpp/io/omanipulators.html](http://www.fredosaurus.com/notes-cpp/io/omanipulators.html)

---

### Post by n0dl on 2007-04-06
alright thanks ill try it out

---

### Post by n0dl on 2007-04-06
Using setw and other iomanip operators didnt really help although it was a viable solution. In any case I have discovered that when copying structs from a file to an array, the compiler adds a new line character to the end of the last element of the struct, I realized this when I ran a test on another file called test.cpp by which I added a \n to the end of the printed statement:
```

for (i=0; i<4; ++i)
{
    cout<<"\t"<<a[i].name<<"\t"<<a[i].gpa<<"\t"<<a[i].age<<endl; \\The change
}

```
When I compiled and ran this I noticed that there was an extra newline between each element
```

       Name        Gpa        Age
      ---------------------------------------
       John          25          3.0

Bill        33        3.1

Mary.... //Etc etc.

```
So in order to remedy this I put a delimeter at the beginning of each entry in the data.txt file
e.g.
```

| John | 25 | 3.0
| Bill | 33 | 3.1
etc etc

```
and then adding a f,ignore(80, '|') before copying the elements into the array.
Hindsight, adding a delimeter to the end of the entry may have resulted in the same thing. I have yet to test this.

---

### Post by WW on 2007-04-06
Use lower case **/code**, not \CODE, to close the **code** environment. (You can edit a previous post.)

---


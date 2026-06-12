---
title: "G++ Pointer Segmentation Fault at runtime"
date: 2007-01-06
forum: Programming Talk
---

### Post by Canis familiaris on 2007-01-06
Hi there
I tried compiling the following code in g++:

It does compile correctly without problems with the command:
```
g++ arr00.cpp
```

However when i execute a.out
It runs correctly for first three variables but then before the fourth variable is set to be entered, it issues segementation fault!
```

anurag@amita-pc:~/dev$ g++ arr00.cpp
anurag@amita-pc:~/dev$ ./a.out
ENTER: 1
ENTER: 2
ENTER: 3
ENTER: 4
Segmentation fault
anurag@amita-pc:~/dev$
```

```

#include<iostream.h>

int main()
{

int j,k;

int** arr;

arr = new int*[3];
*arr = new int[3];

for(j=0; j<3; j++)
{
for(k=0; k<3; k++)
{
cout<<"ENTER: ";
cin>>*(*(arr+j)+k);
}
}

return 0;
}

```

This program worked all right in Turbo C++ 3.0 in DOS.
This is a a snippet of the actual file i wanted to compile shown below indicating same error.
I know I can accomplish the same with arrays but i require to do them with pointers in another program issueing same error requiring flexible pointers.

Can anybody tell me the reason of the error and tell me what extra command or syntax I have to change.

Please help

---

### Post by Canis familiaris on 2007-01-06
And Is there any diffference in GCC's pointer handling?

---

### Post by Canis familiaris on 2007-01-06
Please help, I'm waiting

Also suggest me a good IDE for learning C++/G++ in Ubuntu/Linux.
Also can you suggest a good free reference material!

---

### Post by gpolo on 2007-01-06
first, i suggest you to use:
#include <iostream>
using namespace std;

instead of #include <iostream.h>

second, this line is the problem:
cin>>*(*(arr+j)+k);

it should be:

cin >> *(*(arr)+j+k);

second suggestion would be to use delete before leaving the program, I suppose you already doing ;)

---

### Post by houshdaran on 2010-05-07
Hello.I get a segmentation fault too, g++'ed my file in uuntu 9.10
*'Student and 'SUPV' are two classes
> int main() 
{ 
     
       
    char             pfName[20] = {0}; 
    char             pfLastName[20] = {0}; 
    char             pfCode[10] = {0}; 
    char             pfAddr[100] = {0}; 
    char             pfPhone[10] = {0};
    char             title[100] = {0};    
    char            stdName[20];
    char            stdLastName[20]; 
    char             prName[30] = { 0 };
    char            oldStdID[10] = {0};
    short             stdProjectGrade; 
    short            pfmaxstd; 
    int                 option; 
     
    cout << "*********************Menu*************************************************"
       "\nSelect an option:\n 1)Recruit a professor\n 2)Enroll a student" <<
      "\n3)add a project \n 4)Edit an student's information\n5)Edit a project's information" 
    <<"\n  6)edit a professor's info\n7)Report on a professor" << endl;
    cin >>option; 
     
     
    switch(option){
    case 1:
              {
                 system("clear");
                cout << "****************************************Recruiting a professor***********************************\n\n\n\n\n\n\n" << endl;
                cout << "Enter Professor's Name and LastName(seperated by spaces)" << endl; 
                cin >> pfName >> pfLastName; 
                cout << "Enter Professor's personal code:" << endl;  
                cin >> pfCode;
                
                cout << "here" << endl;               
               SUPV        *Professor = new SUPV(pfName, pfLastName, pfCode );//    !!SEGMENTATION FAULT!! 
               
                supervisorList.push_back(*Professor);
             }
              break; 
    case 2:   
           {
               system("clear");
              cout << "Enter student's name and last name(seperated by space):" << endl; 
              cin >> stdName >> stdLastName; 
               
               cout << "here" << endl;
               Student                            *objPupil =  new Student(stdName, stdLastName);//  !!SEGMENTATION FAULT!!
              
              //    studentList.push_back(*objPupil);
           } 
            break;    
   case 3:
          system("clear");
          cout << "*****************************************Enrolling a student**************************************\n\n\n\n\n\n\n\n\n\n\n\n" << endl;
          cout << "Enter the personal Code of the teacher who wants to add the project:" << endl;
          cin >> pfCode;  

          for( list<SUPV>::iterator it = supervisorList.begin();it != supervisorList.end();++it )
             if( strcmp(it->objPupil.getStdNo(), oldStdID) == 0 )     
             {
            it->addProject();
         break;
         }
   case 4:
          system("clear");
          cout << "************************************Edit a Student\'s Information*********************************\n\n\n\n\n\n\n\n\n\n" << endl; 
      cout << "Attempting to find the specified student................" << endl;
      for( list<Student>::iterator it = studentList.begin();it != studentList.end();++it )
             if( strcmp(it->getStdNo(), oldStdID) == 0 )     
             {

                 cout << "found the specified student" << endl;
         it->edit();
         break;
         }
           break;
   case 5:
          system("clear");
          cout << "********************************************Edit a Project\'s Information******************************\n\n\n\n\n\n\n\n\n\n\n" << endl; 
          cout << "Enter the name of the project you want to edit:" << endl;
          cin >> prName;
          cout << "Attempting to find the specified project................" << endl;
      for( list<Project>::iterator it = projectList.begin();it != projectList.end();++it )
             if( strcmp(it->getProjectName(), prName) == 0)
         {
        cout << "found the specified project" << endl;
        it->edit();
        break;
         }
  case 6:
     system("clear");
         cout << "************************************Edit a professor\'s Information*********************************\n\n\n\n\n\n\n\n\n\n" << endl; 
          cout << "Enter the personal code of the professor you want to edit:" << endl;
         cin >> pfCode;
         cout << "Attempting to find the specified professor................" << endl; 
         for( list<SUPV>::iterator it = supervisorList.begin();it != supervisorList.end();++it )
           if( strcmp(it->getPersonalCode(), pfCode) == 0)
       {
         cout << "found the specified professor" << endl;
         it->edit();
         break;
       }
    break;
 case 7:
    system("clear");
        cout << "*****************************************Report on a professor******************************\n\n\n\n\n\n\n\n\n\n\n" << endl;
        cout << "Enter the personal code of the professor you want to edit:" << endl;
        cin >> pfCode;
        cout << "Attempting to find the specified professor................" << endl; 
        for( list<SUPV>::iterator it = supervisorList.begin();it != supervisorList.end();++it )               
           if( strcmp(it->getPersonalCode(), pfCode) == 0)
          {
                cout << "found the specified professor" << endl;
                 it->report();
                break;
          }  
    }//end switch 
    return 0; 
}

---

### Post by Zugzwang on 2010-05-07
First of all, please start your own new thread for new stuff (even though it's the same class of errors).

Second, if the following line segfaults:
```

SUPV *Professor = new SUPV(pfName, pfLastName, pfCode );// !!SEGMENTATION FAULT!!

```

Then I see the following possibilities:
[LIST=1]
[*]pfName is NULL or points to an invalid memory region or is not properly '\0'-terminated (if applicable)
[*]pfLastName is NULL or points to an invalid memory region or is not properly '\0'-terminated (if applicable)
[*]pfCode is NULL or points to an invalid memory region or is not properly '\0'-terminated (if applicable)
[*]Your SUPV class constructor has an error.
[/LIST]

Check which it is. Is it possible that the data you input is too long for the fields? I personally find "valgrind --tool=memcheck ./your_program" helpful for finding the cause of segfaults. This is often quicker than debugging and finds some problems introduced by "wild pointers". 

Note that you forget to delete your Professor after pushing it into the list. Also, it is bad style to allocate it on the heap, just to copy it into the list and drop it afterwards. I would rather do the following:
```

SUPV Professor(pfName, pfLastName, pfCode );
supervisorList.push_back(Professor);

```

Also, use CODE-tags instead of QUOTE-tags in your next post. It makes stuff easier to read.

---

### Post by dwhitney67 on 2010-05-07
Avoid using the following nonsense when developing in C++:
```

char pfName[20] = {0};
char pfLastName[20] = {0};
char pfCode[10] = {0};
char pfAddr[100] = {0};
char pfPhone[10] = {0};
char title[100] = {0};
char stdName[20];
char stdLastName[20];
char prName[30] = { 0 };
char oldStdID[10] = {0};

```

Use the STL string class instead:
```

#include <string>

...

std::string pfName;
std::string pfLastName;
std::string pfCode;
std::string pfAddr;
std::string pfPhone;
std::string title;
std::string stdName;
std::string stdLastName;
std::string prName;
std::string oldStdID;

```

---

### Post by Ackowa on 2010-05-08
> **Canis familiaris said:**
> 
```

#include<iostream.h>

int main()
{

int j,k;

int** arr;

arr = new int*[3];
*arr = new int[3];

for(j=0; j<3; j++)
{
for(k=0; k<3; k++)
{
cout<<"ENTER: ";
cin>>*(*(arr+j)+k);
}
}

return 0;
}

```


Problem here is that *arr is the same as arr[0], so arr[1] and arr[2] aren't allocatied, so when you reach j+k >=4 you point to uninitialized memory.
Change 
```

*arr = new int[3];

```
to
```

for(j=0; j<3; j++)
{
    arr[j] = new int[3];
}

```
and it should work without Segmentation Fault, shouldn't work with Turbo C++ either since your are using uninitalized memory in that code sequence.

---


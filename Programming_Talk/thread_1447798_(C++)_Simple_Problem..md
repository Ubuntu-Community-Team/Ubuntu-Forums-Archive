---
title: "(C++) Simple Problem."
date: 2010-04-05
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-04-05
Trying to write a file to a vector<structure> It compiles but then the while loop runs forever. Not sure why,
[PHP]
/*
*/

#include <cstdlib>
#include <iostream>
#include <vector>
#include <string>
#include <fstream>

using namespace std;

struct something{
    string str;
    int integer;
    double decimal;      
};




int main(int argc, char *argv[])
{
    //declaring variables
    ifstream finp;
    vector<something> vect;
    something temp;    


    finp.open("filename");

    while (!finp.eof()){

        getline(finp, temp.str);
        finp >> temp.integer;
        finp >> temp.decimal;
        
        vect.push_back(temp);

    }
    




system("PAUSE");
return EXIT_SUCCESS;
}



[/PHP]So heres the problem --

---

### Post by Cracauer on 2010-04-05
Hmmm, did you just say you got an error when compiling but you don't tell use what it is?

---

### Post by YourMomsASmurph on 2010-04-05
UPDATED -- 

I figured out the original problem but have another one. It is in the main post now.

---

### Post by MadCow108 on 2010-04-06
if the formatet input operators encounter a problem (e.g. encountering something which is not an int or double) they set the badbit or failbit and not the eof bit
[http://www.cplusplus.com/reference/iostream/istream/operator%3E%3E/](http://www.cplusplus.com/reference/iostream/istream/operator%3E%3E/)
check finp.good() in the loop and it should stop at the problem

you'll have to post what you input if you want help debugging that.

---

### Post by YourMomsASmurph on 2010-04-06
here is the format input file

[PHP]
My Name
1234
12.3
My Name2
5678
45.6
[/PHP]If I print (within the while loop)

[PHP]

        index=0;
        cout << vect[index].str <<endl << vect[index].integer << endl << vect[index].double <<endl;
        index++;


[/PHP]I should expect to see (if it was working proper)

```

My Name
1234
12.3
My Name2
5678
45.6

```but instead I get:

```

My Name
 1234
 12.3
My Name
 1234
 12.3
My Name
 1234
 12.3
My Name
 1234
 12.3
My Name
 1234
 12.3
My Name
 1234
 12.3
My Name
 1234
 12.3
...
...
...
My Name
 1234
 12.3
...

```So I've concluded that it keeps going back to the begining of the file when the loop restarts :. it never reaches eof, and it runs forever.

---

### Post by Tony Flury on 2010-04-06
if you are actually adding the code 
```

        index=0;
        cout << vect[index].str <<endl << vect[index].integer << endl << vect[index].double <<endl;
        index++;  

```
in your loop - then the problem is not in reading the file, the problem here is that you are reseting index to zero each time round the loop - and therefore you will always print out the first (index zero) entry in your vector.

try this loop instead 
```


    index = 0 ; 

    while (!finp.eof()){

        getline(finp, temp.str);
        finp >> temp.integer;
        finp >> temp.decimal;
        
        vect.push_back(temp);

        cout << vect[index].str <<endl << vect[index].integer << endl << vect[index].double <<endl;
        index++;  

    }


```
so you don't reset index each time round the loop.

Now what output do you get ?

---

### Post by YourMomsASmurph on 2010-04-06
Heh.. yea I feel like an idiot now :P.

BUT the new output makes less sense.

```

 
 1234
 12.3
 
 1234
 12.3
 
 1234
 12.3
 
 1234
 12.3
 
 1234
 12.3
 
 1234
 12.3
 
 1234
 12.3
...
...
...
 
 1234
 12.3
...


```------------------------------------------------------------------------------------------------------

Since its seeming hard to diagnose the problem, im subbmitting the actual code. These alot of stuff int here that has nothing to do with the problem.


(Yes it is part of homework but I DO NOT want anyone to give me the answer on how to write the program.) As far as I can tell, this program should work. But for some reason the  the file is not advancing everytime the extraction operator (>>) is used. (And as far as i know that is how it should work.)


[PHP]
#include <cstdlib>
#include <iostream>
#include <vector>
#include <string>
#include <fstream>

using namespace std;

//this is the def'n of a struct to hold the student info
struct student{
    string name;
    int idnum;
    double grade;      
};

//prototypes
void addStudent(string newname,int newidnum,double newgrade,vector <student> & list); 
int getIndex(int id,vector <student> list);
void removeStudent(int index,vector <student>& list);
void swapStudent(int index1, int index2, vector <student> & list);
void changeGrade(int index,double mark, vector <student> & list);
void printList(vector <student> list);
double average(vector <student> list);
void sort(int sortBy, vector <student>& list);




//note: need a project file to check current directory, otherwise you have to enter the full path tot he file
int main(int argc, char *argv[])
{

    string filenm, Name;
    ifstream iClst;
    ofstream oClst;
    vector<student> ClssLst, ClssLstBckup;
    int Oprtn, ID, index(0);
    double Mark;
    student ClssLstTemp;
    
    
    
    cout << "Please enter the name of the file that the class list is in:" ;
    getline (cin , filenm); // Just in case the file name contains a space.
        
    iClst.open((filenm + ".txt").c_str()); // adds strings together, and converts to cstring.

    
    if (iClst.fail()) {
        cout << "Could not open file.";
        return 0;
    }
    

    // HERE IS THE PROBLEM
    while (!iClst.eof()){

        getline(iClst, ClssLstTemp.name);
        iClst >> ClssLstTemp.idnum;
        iClst >> ClssLstTemp.grade;
        
        ClssLst.push_back(ClssLstTemp);
        
        cout << ClssLst[index].name <<endl << ClssLst[index].idnum << endl << ClssLst[index].grade <<endl;

        index++;
    }
    //Problem ends here, Ignore the rest.
    
    
    iClst.close();
    
    while (true) {
        
        cout <<"Please select the operation you wish to perform.\n";
        cout <<"1) Add a new student to the list \n"
             <<"2) Remove a student from the list \n"
             <<"3) Change the mark of a student\n"
             <<"4) Print the class list on screen\n"
             <<"5) Print the average mark on screen\n"
             <<"6) Sort the class list\n"
             <<"7) Undo the last operation\n"
             <<"0) Save the list to a file, and quit\n";
                
        cout << "\nOperation:";
        cin >> Oprtn;
        cout <<endl;
    
    
        switch (Oprtn)
        {
        
            case 1: // Adds Student
                cout << "Enter the students name:";
                cin >> Name;
                cout << "Enter the student ID:";
                cin >>ID;
                cout << "Enter the student's mark:";
                cin >> Mark;
                
                addStudent(Name, ID, Mark, ClssLst);
                break;
                
            case 2: //Removes Student
                cout <<"Please enter the ID number:";
                cin >> ID;
                
                index = getIndex(ID, ClssLst); // get index of student so we know which to remove
                
                if (index == -1) { // -1 is returned if number is not found, the case will then tell us this and then break, nothing below it will occur.
                    cout << "That id number is not in the list.";
                    break;
                }
                
                removeStudent(index, ClssLst);
                break;
                
            case 3: // Changes Mark
                cout <<"Please enter the ID number:";
                cin >> ID;                
                index = getIndex(ID, ClssLst);
                
                if (index == -1) { // -1 is returned if number is not found, the case will then tell us this and then break, nothing below it will occur.
                    cout << "That id number is not in the list.";
                    break;
                }
                
                cout <<"Please enter the student's mark:";
                cin >> Mark;
                
                changeGrade(index, Mark, ClssLst);
                break;
                
            case 4: // Prints list
                printList(ClssLst);
                break;
                
            case 5: // Finds Average Mark
                average(ClssLst);
                break;
                
            case 6:
                cout << "    1)Sort by Name"
                     << "    2)Sort by Grade";
                cin >> Oprtn;
                sort(Oprtn, ClssLst);
                break;
    
            case 7:
            case 0:
            
            
            default:
                cout << "Invalid Operation.";
            
        }    
    
    
    }
   

system("PAUSE");
return EXIT_SUCCESS;
}//end main program



void addStudent(string newname,int newidnum,double newgrade,vector <student>& list){

    student StuInfo = { newname, newidnum, newgrade };
    list.push_back(StuInfo);
    
}


int getIndex(int id,vector <student> list){

    for (int i = 0 ; i < list.size() ; i++)
        if (list[i].idnum == id)
            return i;
    return (-1);
    
}


void removeStudent(int index,vector <student>& list){
    int size;
    size = list.size();
    
    for (int i = index; i < size ; i++)
        list[i] = list [i+1]; // when vector gets to the last name the vector list[i] will take the value of the next cell which should be the null character./??     
    
}


//this function swaps the information of 2 students, including their name, id and grade.
//The index1 passed in is the location in the vector of the first student, and index2 is the location of the second student.
//The vector is passed by reference so the changes will stick
void swapStudent(int index1, int index2, vector <student>& list){
     student temp;

     //store temp
     temp=list[index1];
     //swap
     list[index1]=list[index2];
     list[index2]=temp;
}//end swapStudent


void changeGrade(int index,double mark, vector <student> & list){

    list[index].grade = mark;

}


void printList(vector <student> list){

    for (int i = 0; i < list.size(); i++)
        cout << list[i].name <<endl <<list[i].idnum <<endl <<list[i].grade;
}

double average(vector <student> list){
    double average(0);
    
    for (int i = 0 ; i < list.size() ; i++) {
        average += list[i].grade;
    }
    
    average /= list.size();
    return average;
}


void sort(int sortBy, vector <student>& list){

}

 [/PHP]


Origonal File:

```

Jake Simmons
1234
67.8
Jane Doe
678
82.5
Abe Ginger
903
56.8
Zenobia Windsor
2348
90.0
Andy Andrews
9999
95.6

```


Output:
```


1234
67.8

1234
67.8

1234
67.8

1234
67.8

...

1234
67.8

...


```

---

### Post by Tony Flury on 2010-04-06
you might want (i.e. you need definitely) to double check what the >> operator does and check the error flags - for instance the "fail" flag ? Do the actual reads work ?

You also might find that numerical input maybe does not consume all the characters you think it does - See : 
[http://www.parashift.com/c++-faq-lite](http://www.parashift.com/c++-faq-lite) for more info.

---


---
title: "Visual C++ 6.0, runtime problems, multifile programs"
date: 2008-04-14
forum: Programming Talk
---

### Post by atsukoarai86 on 2008-04-14
Okay. This is a complicated one. I've written this entire program originally in ONE FILE, driver.cpp (driver1.txt attached), and it works splendidly. 

Now, I have to separate the function prototypes into a .h header file and the function definitions into a separate .cpp file and include them in the driver.cpp function. Upon separating the files, I have the following:

(this is a lot of code)
functions.h
_________________________________________
```
#include<iostream>		// input/output functions
#include <fstream>
#include<iomanip>		// i/o manipulation functions - setw(), setiosflage()
#include<string>		// string functions


using namespace std;

#ifndef FUNCTIONS_H   // functions.h header for function prototypes
#define FUNCTIONS_H

struct CityData												// structure containing data from file records
{
	char name[20];											// name of city
	int pop,												// population as of 4/1/2005
		popGrow;											// populatino growth from 1990 to 2000
} CityArray[25];											// declare struct array to hold all file records



void Open(ifstream&);	// test for failure opening file
void Load(ifstream&, struct CityData*p);					
int Highest_Pop(struct CityData*p);							
int Greatest(struct CityData*p);							
int Average(struct CityData*p);								
void Write(ofstream&, string&, struct CityData [], int,		
		   int, int);

#endif
```
fbody.cpp
_____________________________________
```
#include <fstream>
#include<cstdlib>		// stardard library functions
#include<iostream>		// input/output functions
#include<iomanip>		// i/o manipulation functions - setw(), setiosflage()
#include<string>		// string functions


#include "functions.h"


using namespace std;

// FUNCTION DEFINITIONS // 

/***************************************************************/
/* Function name: Open                                         */
/* Purpose:       Test for failure to open indicated file path */
/*                and if so, terminate program.                */
/* Paramaters:    ifstream &ins (inData) - stream to read data */
/*                from file indicated.                         */
/***************************************************************/   
void Open(ifstream &ins)								// BEGIN Open
{
	if(!ins)											// test for failure
	{													// begin if statement
		cerr<<"File could not be opened."<<endl;		// print error
		exit(1);										// exit program
	}													// end if structure
	
	return;												// return to main
}														// END Open


/***************************************************************/
/* Function name: Load                                         */
/* Purpose:       Read data from file and store within the mem-*/
/*                bers of the elements of the struct array.    */
/* Paramaters:    ifstream &ins (inData) - stream to read data */
/*                from file indicated.                         */
/*                struct CityData *p (arrayPtr) - type struct  */
/*                CityData pointer to struct array CityArray[0]*/
/***************************************************************/ 
void Load(ifstream &ins, struct CityData *p)			// BEGIN Load
{

	while(ins)						// While object ins returns true (file is open)
	{								// begin while loop
		int i=0;					// declare variable local to while loop
	
		ins>>(p->name);				// read first column to CityArray.name, through pointer *p
		ins>>(p->pop);				// read second column to CityArray.pop, through pointer *p
		ins>>(p->popGrow);			// read third column to CityArray.popGrow, through pointer *p

		p++;						// incrementer pointer to next element in CityArray
	}								// end while loop

		return;						// return to main
}									// END Load


/***************************************************************/
/* Function name: Highest_Pop                                  */
/* Purpose:       Step through CityArray[] through pointer, us-*/
/*                ing for-loop to determine the greatest value */
/*                of CityArray[].pop.                          */ 
/* Paramaters:    struct CityData *p (arrayPtr) - type struct  */
/*                CityData pointer to struct array CityArray[0]*/
/***************************************************************/ 
int Highest_Pop(struct CityData *p)				// BEGIN Highest_Pop
{
	// LOCAL VARIABLES //
 			
	int max=0;						// variable to store maximum value
	int i;							// for-loop variable


	for(i=0;i<25;i++)				// for-loop initialization, condition, incrementation
        {							// begin for-loop							
		if((p+i)->pop>max)			// if CityArray[i].pop is greater than value of max
			max=(p+i)->pop;			// set max equal to CityArray[i].pop
	}								// end for-loop

	return max;						// return value of max to variable HighPop in main()
}




/***************************************************************/
/* Function name: Greatest                                     */
/* Purpose:       Step through CityArray[] through pointer, us-*/
/*                ing for-loop to determine the greatest value */
/*                of CityArray[].popGrow                       */ 
/* Paramaters:    struct CityData *p (arrayPtr) - type struct  */
/*                CityData pointer to struct array CityArray[0]*/
/***************************************************************/
int Greatest(struct CityData *p)				// BEGIN Greatest
{
	// LOCAL VARIABLES //

	int temp=0;						// variable to store maximum value
	int i;							// for-loop variable


	for(i=0;i<25;i++)				// for-loop initialization, condition, incrementation
        {							// begin for-loop		
		if((p+i)->popGrow>temp)		// if CityArray[i].popGrow is greater than value of temp
			temp=(p+i)->popGrow;	// set max equal to CityArray[i].popGrow
	}								// end for-loop

	return temp;					// return value of temp to variable Growth in main()
}									// END Greatest










/***************************************************************/
/* Function name: Average                                      */
/* Purpose:       Step through CityArray[] through pointer, us-*/
/*                ing for-loop to determine the average value  */
/*                of CityArray[].pop                           */ 
/* Paramaters:    struct CityData *p (arrayPtr) - type struct  */
/*                CityData pointer to struct array CityArray[0]*/
/***************************************************************/
int Average(struct CityData *p)					// BEGIN Average
{
	// LOCAL VARIABLES // 

	int avg=0;						// average population in April 2005
	int i;							// for-loop variable
	int temp=0;						// temp variable to accumulate total



	for(i=0;i<25;i++)				// for-loop initialization, condition, incrementation
	{								// begin for-loop
		temp+=(p+i)->pop;			// assign the calculation (temp+CityArray[i].pop) to temp		
	}								// end for-loop
	
	avg=temp/25;					// calculate average

	return avg;						// return value of avg to variable Avg in main()
}									// END Average










/***************************************************************/
/* Function name: Write                                        */
/* Purpose:       write data to user-defined output file       */
/* Paramaters:    ofstream &out (write) - ofstream object      */
/*                string &name (Fname) - user defined file name*/
/*                struct CityData *p (arrayPtr) - type struct  */
/*                CityData pointer to struct array CityArray[0]*/
/*                int h (HighPop) - highest population in April*/
/*                2005                                         */
/*                int g (Growth) - Greatest growth from 1990 to*/
/*                2000.                                        */
/*                int avg (Avg) - Average population in 4/2005 */
/***************************************************************/
void Write(ofstream& out, string &name, struct CityData a[],
		   int h, int g, int avg)
{								// BEGIN Write
	// LOCAL VARIABLES //
	int i;											// for-loop variable


	cout<<endl<<"Enter file name to create: "<<endl;// prompt user for input
	getline(cin,name);								// input file name

	out.open(name.c_str(), ios::out);				// open file, cast user-input to c-type string
													// ios set for output
	if(out.fail())									// if file can not be opened
	{												// begin if statement
		cerr<<"File cannot be opened."<<endl;		// print error message
		system("pause");							// pause execution
		exit(1);									// terminate program
	}												// end if statement


	out<<setiosflags(ios::left)						// formatting output
		<<setw(20)<<"City Name"						// formatting output
		<<setw(15)<<"Population"					// formatting output
		<<setw(15)<<"Growth"<<endl;					// formatting output
	out<<setiosflags(ios::left)						// formatting output
		<<setw(20)<<" "								// formatting output
		<<setw(15)<<"in 4/2005"						// formatting output
		<<setw(15)<<"from '90-2000"<<endl<<endl;	// formatting output
	out<<"--------------------------------------------------"<<endl;

	for(i=0;i<25;i++)								// prepare to loop
	{												// begin for-loop
		out<<setiosflags(ios::left)					// formatting output
			<<setw(20)<<a[i].name					// output CityArray[i].name
			<<setw(15)<<a[i].pop					// output CityArray[i].pop
			<<setw(15)<<a[i].popGrow<<endl;			// output CityArray[i].popGrow
	}												// end for-loop

	out<<endl<<"Highest population: "<<setw(10)<<h<<endl	// output results
		<<"Greatest pop. growth: "<<setw(10)<<g<<endl		// output results
		<<"Average population: "<<setw(10)<<avg<<endl;		// output results

	return;													// return to main
}															// END write

```

Okay. This is the problem. I get 0 errors, 0 warnings when I compile the code, so I know it isn't a compilation problem. But, when I try to build the .exe file, I get the following:

--------------------Configuration: AshermanFINAL - Win32 Debug--------------------
Compiling...
Skipping... (no relevant changes detected)
fbody.cpp
Linking...
fbody.obj : error LNK2005: "void __cdecl Open(class std::basic_ifstream<char,struct std::char_traits<char> > &)" (?Open@@YAXAAV?$basic_ifstream@DU?$char_traits@D@std@@@std@@@Z) already defined in driver.obj
fbody.obj : error LNK2005: "void __cdecl Load(class std::basic_ifstream<char,struct std::char_traits<char> > &,struct CityData *)" (?Load@@YAXAAV?$basic_ifstream@DU?$char_traits@D@std@@@std@@PAUCityData@@@Z) already defined in driver.obj
fbody.obj : error LNK2005: "int __cdecl Highest_Pop(struct CityData *)" (?Highest_Pop@@YAHPAUCityData@@@Z) already defined in driver.obj
fbody.obj : error LNK2005: "int __cdecl Greatest(struct CityData *)" (?Greatest@@YAHPAUCityData@@@Z) already defined in driver.obj
fbody.obj : error LNK2005: "int __cdecl Average(struct CityData *)" (?Average@@YAHPAUCityData@@@Z) already defined in driver.obj
fbody.obj : error LNK2005: "void __cdecl Write(class std::basic_ofstream<char,struct std::char_traits<char> > &,class std::basic_string<char,struct std::char_traits<char>,class std::allocator<char> > &,struct CityData * const,int,int,int)" (?Write@@
YAXAAV?$basic_ofstream@DU?$char_traits@D@std@@@std@@AAV?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@2@QAUCityData@@HHH@Z) already defined in driver.obj
fbody.obj : error LNK2005: "struct CityData * CityArray" (?CityArray@@3PAUCityData@@A) already defined in driver.obj
Debug/AshermanFINAL.exe : fatal error LNK1169: one or more multiply defined symbols found
Error executing link.exe.

AshermanFINAL.exe - 8 error(s), 0 warning(s)
___________________________________________

driver.cpp
```
#include<iostream>		// input/output functions
#include<cstdlib>		// stardard library functions
#include<fstream>		// file stream - ifstream, ofstream .open, .close
#include<iomanip>		// i/o manipulation functions - setw(), setiosflage()
#include<string>		// string functions

#include "functions.h"
#include "fbody.cpp"



using namespace std;	// using namespace from stdlib.h (cstdlib)

												
int main()													// BEGIN MAIN //
{
	
	// LOCAL VARIABLES // 

	string Fname;											// user created file name for output
	int HighPop,											// highest population in April 2005
	Growth;													// highest growth from 1990 to 2000
	int Avg;												// average population in April 2005	
	
	// STRUCT DECLARATIONS // 
	
	struct CityData *arrayPtr = CityArray;					// declare pointer and assign to array
	
	// FSTREAM OBJECTS // 
	
	ifstream inData;										// declare ifstream object
	ofstream write;											// declare ofstream objeect
	
	
						// BEGIN CODING //

	// INPUT DATA // 
	
	inData.open("rawdata.txt");								// open data file
	Open(inData);											// test for failure opening file
	Load(inData, arrayPtr);									// load data into struct array
	


	// CALCULATIONS // 
		
	arrayPtr=CityArray;										// reset pointer to CityArray[0]
	HighPop=Highest_Pop(arrayPtr);							// analyze data
	Growth=Greatest(arrayPtr);								// analyze data
	Avg=Average(arrayPtr);									// analyze data


	// OUTPUT DATA // 

	Write(write, Fname, CityArray, HighPop, Growth, Avg);	// create new file for output
	write.close();											// explicitly close filestream to new file

	cout<<endl<<"File created successfully."<<endl<<endl;	// print confirmation
	system("pause");										// pause program execution
	

	
	return 0;												// indicate successful completion
}															// END OF MAIN // 

```

Dear god in heaven. I know this has SOMETHING to do with that stinking struct, and I know, I KNOW, I shouldn't use global stuff, but that's how it was declared and the entire program is built around it. I don't want to re-write the entire program... 

If anyone has any suggestions, my ears are open. I was planning on asking my teacher tomorrow, and if he can't help, I was planning on asking the head of the computer science department. However, if I could avoid asking either of them, and just turn in a brilliant, working, multi-file program, that would be better. heh... 

Thank you, all of you more brilliant than I, in advance. :D

---

### Post by LaRoza on 2008-04-14
> **atsukoarai86 said:**
> Okay. This is a complicated one. I've written this entire program originally in ONE FILE, driver.cpp (driver1.txt attached), and it works splendidly. 

Now, I have to separate the function prototypes into a .h header file and the function definitions into a separate .cpp file and include them in the driver.cpp function. Upon separating the files, I have the following:

Why is the struct in the header? It doesn't have to be.

Why do you **have** to separate the function prototypes and definitions? Is this for school?

There is a sticky on asking questions about school work.

Here is the only hint you will get: **extern**

The rest is up to you.

You have odd requirements, you have a programming style that you must have picked up elsewhere, you are using Visual Studio. Probability is high that you are doing this for school. Thread closed.

**Thread Temporarily reopened**

---

### Post by dwhitney67 on 2008-04-15
Start by cleaning up your code. Here's some hints:

In header file:

    * The multiple-inclusion guard in your header file should be stated first... not after you have included the header files.
    * Remove the include statements for iomanip and iostream from your header file; they are not needed.
    * In C++, a struct and a class are the same, with the exception that in a class, all member data defined are by default considered 'private', unless otherwise indicated. You do not need to use 'struct CityData' in your declarations; 'CityData' will suffice. Rather than pass pointers of CityData, pass it in by reference. Move all of the function declarations into the 'struct CityData' definition.
    * Unless you have a compelling reason, define 'name' in CityData as an std::string.
    * Remove the 'using namespace std;' from the header file.


In .cpp file:

    * You need a white-space between the #include and the opening '<'.
    * Local header files (i.e. function.h) should be included before system header file(s).
    * If the functions are part of the CityData structure, then precede function names with 'CityData::'.
    * Declare _and_ initialize local variable at a point closest to where it is needed (i.e. not necessary at the top of the function).

---

### Post by LaRoza on 2008-04-15
OP doesn't even know what Ubuntu is and is using this forum for free school help.

Threads closed.

---


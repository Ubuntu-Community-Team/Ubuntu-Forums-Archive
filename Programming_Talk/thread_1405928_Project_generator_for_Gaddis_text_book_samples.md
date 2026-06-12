---
title: "Project generator for Gaddis text book samples"
date: 2010-02-13
forum: Programming Talk
---

### Post by Jonas thomas on 2010-02-13
I'm thinking about writing an App, but I wonder if there is already a solution out there.

I've been taking a class which uses Tony Gaddis's "Starting out with C++ From Control Structure through Objects"
The book comes with a CD which includes the source for the examples used in the book.
I find it helpful to copy the code and hack it up a bit.  I'm currently use Linux/Codelite at home and Windows at school/work.

Basically the examples are all single file .CPP in a directory structure
like.

```

jonas@jonas5:/media/GADDIS_SOC_CSO_6/Book_resources/SourceCode/Chapter 05$ ls -1
LineUp.dat
NestedLoopClockSimulation.cpp
numbers.txt
people.dat
Pr5-10.cpp
Pr5-11.cpp
Pr5-12.cpp
Pr5-13.cpp
Pr5-14.cpp
Pr5-15.cpp
Pr5-16.cpp
Pr5-17.cpp
Pr5-18.cpp
Pr5-19.cpp
Pr5-1.cpp
Pr5-2.cpp
Pr5-3.cpp
Pr5-4.cpp
Pr5-5.cpp
Pr5-6.cpp
Pr5-7.cpp
Pr5-8.cpp
Pr5-9.cpp
random.txt

```

I want to automatically set up folders/sub-folders for each chapter and Pr* example, create workspace and project files and copy the source files to the appropriate stop.

On my first manual iteration, I tried to setup the workspace/project files through the IDE. (Yech.... very tedius)

Second iteration I used gedit to copy/modify the workspace/project XML files.  Much easier but still a bit tedius. This gave me the idea of automating the process.

Third? I like to just push a button and have all the manual stuff done automatically.  (Been a bit of research on this it seems like dirent.h is the way to go on this)

Is there a utility out there that does this sort of thing?  Otherwise it would be fun and within my current skill sets to take this on.  It just that I have a bunch of irons in the fire at the moment and I not sure I have the time for this "fun" distraction...

Btw... In no way shape or form is a homework assignment it's just something I want to do.

Thanks,
JT

---

### Post by Jonas thomas on 2010-02-14
(EDIT figure out my error... Duhh..
if ((s.substr(1,int(PROJECT_FOLDER_PREFIX.length)))==(char(PROJECT_FOLDER_PREFIX)))
should have been
if ((s.substr(1,int(PROJECT_FOLDER_PREFIX.length())))==(char(PROJECT_FOLDER_PREFIX)))


//My little project C++ project is giving me a headache.
//If I was doing this in vb6.. I would have been done in 5 minutes.
Ok... This is amusing... I'm starting to write in comments....
I spent about the last couple of hours trying to find the c++ equivalent to the vb mid$ function.   It seems like it's not very straight forward.  So far in my class we only covered "char" we haven't gotten into string... I'm trying match the folder name to a prefined prefix.  Seems like this should work.. I'm missing something obvious... Anyone?


```

    // #include <stddef.h>
     #include <stdio.h>
     //#include <sys/types.h>
     #include <dirent.h> // This works in Posix compliant in linux but MS doesn't support it.
     #include <iostream>
     //#include <cstring>
	 #include <string>
	 using namespace std;


int main ()
{
 	   const char chaptersamplecode[]="//home/jonas/.codelite/CodCppClass/Chapter6/SampleCode/";
	   char foldername[256];
	   const string PROJECT_FOLDER_PREFIX("Pr6")  ;
	   DIR *dp;
       struct dirent *ep;
	   dp = opendir (chaptersamplecode); // Linux only
       if (dp != NULL)
         {
           while (ep = readdir (dp))
                
			{
				ep->d_name; //only for linux
				string s(ep->d_name);//Well this has been covered either.
				//cout<< PROJECT_FOLDER_PREFIX.length()<<endl;
				//cout << s.substr(1,int(PROJECT_FOLDER_PREFIX.length()))<<endl;
				cout <<s;
				if ((s.substr(1,int(PROJECT_FOLDER_PREFIX.length)))==(char(PROJECT_FOLDER_PREFIX))) // !!! THIS IS BOMBING !!!! I'm Missing something obvious.
					cout << "match"<<endl;
					//Need to put a project file in this folder
				else
				   cout<<"No match"<<endl;
				
			//	cout<< strcmp(PROJECT_FOLDER_PREFIX,ep->d_name)<< " ";
				cout<< (ep->d_name)<<" "<< s <<endl;
			
			
			} 
		   (void) closedir (dp);
         }
       else
         perror ("Couldn't open the directory");
 
}




```

---


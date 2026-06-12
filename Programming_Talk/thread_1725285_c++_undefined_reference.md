---
title: "c++ undefined reference"
date: 2011-04-09
forum: Programming Talk
---

### Post by Ghostmn on 2011-04-09
I'm working on a game, and i recently just started separating c++ files to be header and c++ for one class. I get the undefined reference when making an object to call a function from one class to another
```

#include <iostream>
#include "mainmenu.h"


int main(int argc, char **argv)
{
    //initiates the main menu at start up
    mainzmenu menu;
    menu.mainmenu();
    return 0;
}

```Here is my main file, I have to go quickly. Thanks for replies.

---

### Post by simeon87 on 2011-04-09
You typed "mainzmenu", surely you meant "mainmenu"?

---

### Post by Ghostmn on 2011-04-09
I'm making a game with a few friends, one of them made the mainmenu and he named the class mainzmenu. Any ways i just posted the main function because it's the smallest compared to the rest. All of my .c++ files have header files. And all of them have the same error "undefined reference" to a function.Any idea? I'll post the mainzmenu class in a sec.

```
main.c++:(.text+0x17): undefined reference to `mainzmenu::mainmenu()'
```

---

### Post by Ghostmn on 2011-04-09
Here is the header and the class. I made the header, a friend made the .c++ file

```

#ifndef MAINMENU_H
#define MAINMENU_H

class mainzmenu{
    private:
    char tri;
    public:
    void mainmenu();
    void loadselect();
    void creditsselect();
    void credit();
    };
#endif

``````

#include <iostream>
#include <cstdlib>
#include "mainmenu.h"
#include "player.h"
#include "mygetch.h"

    
    void mainzmenu::mainmenu(){
        std::cout <<
        "    {}++++++++++++++++{}\n"
        "    {}=Midnight Cloud={}\n"
        "    {}++++++++++++++++{}\n"
        "          Welcome...\n\n"                        
        "    ####################\n"
        "    #                  #\n"
        "    #   >:New Game:<   #\n"
        "    #                  #\n"
        "    #    :Load Game:   #\n"
        "    #                  #\n"
        "    #    :Credits:     #\n"
        "    #                  #\n"
        "    ####################\n"
        "    |  Use w and s to  |\n"
        "    | scroll and ENTER |\n"
        "    |    to select     |\n"
        "     ==================\n";
        tri=mygetch();
        system("clear");
        switch (tri){
            case 'w':
    creditsselect();
                break;
            case '\n':
                //calls for a new game
                player newch;
                newch.name();
                system("clear");
    mainmenu();
                break;
            case 's':
    loadselect();
                break;
        }
    mainmenu();
    }
    
    void mainzmenu::loadselect(){
        std::cout <<
        "    {}++++++++++++++++{}\n"
        "    {}=Midnight Cloud={}\n"
        "    {}++++++++++++++++{}\n"
        "          Welcome...\n\n"                        
        "    ####################\n"
        "    #                  #\n"
        "    #    :New Game:    #\n"
        "    #                  #\n"
        "    #   >:Load Game:<  #\n"
        "    #                  #\n"
        "    #    :Credits:     #\n"
        "    #                  #\n"
        "    ####################\n"
        "    |  Use w and s to  |\n"
        "    | scroll and ENTER |\n"
        "    |    to select     |\n"
        "     ==================\n";
        tri=mygetch();
        system("clear");
        switch (tri){
            case 'w':
    mainmenu();
                break;
            case '\n':
                //Load screen forward point
                std::cout<< "Loading Screen Coming Soon!"
                "\n\nPress ENTER to continue.";
                std::cin.get();
                system("clear");
    mainmenu();
                break;
            case 's':
    creditsselect();
                break;
            }
    loadselect();
    }
    
    void mainzmenu::creditsselect(){
        std::cout <<
        "    {}++++++++++++++++{}\n"
        "    {}=Midnight Cloud={}\n"
        "    {}++++++++++++++++{}\n"
        "          Welcome...\n\n"                        
        "    ####################\n"
        "    #                  #\n"
        "    #    :New Game:    #\n"
        "    #                  #\n"
        "    #    :Load Game:   #\n"
        "    #                  #\n"
        "    #   >:Credits:<    #\n"
        "    #                  #\n"
        "    ####################\n"
        "    |  Use w and s to  |\n"
        "    | scroll and ENTER |\n"
        "    |    to select     |\n"
        "     ==================\n";
        tri=mygetch();
        system("clear");
        switch (tri){
            case 'w':
    loadselect();
                break;
            case '\n':
    credit();
                break;
            case 's':
    mainmenu();
                break;
        }
    creditsselect();
    }

    void mainzmenu::credit(){
            std::cout << 
    " ############\n"
    "# Developers #\n"
    " ############\n\n"
     
    "#LP-Michael Davenport\n\n"

    "#HP-Alex Fatum\n\n"

    "#SAG-Max Mitchell\n"
    "______________\n"
    ".Contact us at.\n\n"

    "mcindevelopment@gmail.com\n\n\n"
    "Press ENTER to return to the Main Menu.";
        std::cin.get();
        system("clear");
    mainmenu();
    }


```

---

### Post by Some Penguin on 2011-04-09
You aren't specifying the command you use to compile and link them.

---

### Post by Ghostmn on 2011-04-09
oh sorry! umm I don't use the terminal for compiling. I use Geany for convenience of the build/compile button.

---

### Post by Jonas thomas on 2011-04-09
I tried to compile your code, but I'm missing "player.h", "mygetch.h" 
I commented out everything that was missing,and it seems to run. So I'm not sure where the problem lies.
So... you guys going throw this up on sourceforge or github when you move it along a bit more?;)

---

### Post by Ghostmn on 2011-04-09
We have it up on google code. It's of course ascii based since we are working on getting a better understanding of c++. Once we finish it we'll move onto SDL for it's sequel, and hopefully get into opengl on it's 3rd iteration.

---

### Post by Ghostmn on 2011-04-09
I'm going to upload all of my source to google code right now, can Someone look at it and see if you get the same problems? Link provided. Unstable is the package
[URL="http://code.google.com/p/midnight-cloud/downloads/list?saved=1&ts=1302386973"]http://code.google.com/p/midnight-cloud/downloads/detail?name=0.0.3%20Experimental.tar.gz&can=2&q=
[/URL]

---

### Post by Jonas thomas on 2011-04-09
well... Tried to down load your code.  My code blocks didn't like your c++ extension so I changed c++ to cpp. Not a mistake just my preference.
First error I get is this.
/home/jonas/MidnightCloud/Ascii.cpp||In member function &#8216;void ascii::lvl1()&#8217;:|
/home/jonas/MidnightCloud/Ascii.cpp|59|error: &#8216;mygetch&#8217; was not declared in this scope|
... You need to include "mygetch.h"
/home/jonas/MidnightCloud/mainmenu.cpp||In member function &#8216;void mainzmenu::mainmenu()&#8217;:|
/home/jonas/MidnightCloud/mainmenu.cpp|60|error: jump to case label|
/home/jonas/MidnightCloud/mainmenu.cpp|55|error:   enters scope of non-POD &#8216;player newch&#8217;|
||=== Build finished: 2 errors, 0 warnings (0 minutes, 2 seconds) ===|

Then need Brackets after your'e 
void mainzmenu::mainmenu(){
....
case '\n':
{
}

Ohhhh.... Then I get this...
obj/Debug/combat.o||In function `mygetch()':|
/home/jonas/MidnightCloud/mygetch.h|26|multiple definition of `mygetch()'|
obj/Debug/Ascii.o:/home/jonas/MidnightCloud/mygetch.h|26|first defined here|
obj/Debug/mainmenu.o||In function `mygetch()':|
/home/jonas/MidnightCloud/mygetch.h|26|multiple definition of `mygetch()'|
obj/Debug/Ascii.o:/home/jonas/MidnightCloud/mygetch.h|26|first defined here|
||=== Build finished: 4 errors, 0 warnings (0 minutes, 1 seconds) ===|

I think what's going on there is that you have implementation in a header file.  Oh... Why not change your getch from a struct to a class and move the implementation to a CPP?

---

### Post by Ghostmn on 2011-04-10
Jonas I must thank you for helping me. Ok I changed mygetch.h to a cpp file. included it in ascii. Now i'm just left with the same thing before "undefined reference"

I'm not sure what you meant by include braces mainzmenu::mainmenu{}

---

### Post by Jonas thomas on 2011-04-10
[QUOTE=Ghostmn;10659236]Jonas I must thank you for helping me. Ok I changed mygetch.h to a cpp file. included it in ascii. Now i'm just left with the same thing before "undefined reference"

Errr... Forget I said that about the {}.:redface: Its not required for the switch case. [http://www.cplusplus.com/doc/tutorial/control/]("http://www.cplusplus.com/doc/tutorial/control/")  I just like to use them but it's not required.

I think the root of your problems is that you have you mygetch defined as a function and not as a class. When you have implementation code in a header weird things happen.  If you have it in a cpp,the other functions won't find it.  You should be able to globally define a function, but I'm brain farting on that at the moment. Plus I think globally defining stuff is generally looked down upon.

I think your heading with this is that your going to want keyboard input with out a carriage return eventually..

But since your doing a carriage return at the moment perhaps something like this might work.

```
#include "employee.h"
#include <fstream>
#include <iostream>

int main()
{
    payroll proll;
    string initialEmployeeFileName;
    string line;
        cout << "Please enter initial employee data file:";

	//initialEmployeeFileName="payroll.dat";
    getline(cin,initialEmployeeFileName);
    cout << initialEmployeeFileName << endl;


    ifstream employeeIDDataFile(initialEmployeeFileName.c_str());
    if (employeeIDDataFile.is_open())
    {
        employee temp;
        while (employeeIDDataFile.good() )
        {
            employeeIDDataFile>>temp;
            proll.employeeHire(temp);
        }
        employeeIDDataFile.close();
        //cout<<proll.displayAllEmployeeData(false,true);
        cout <<"##########################################\n";
        cout <<"EMPLOYEE DATA FILE HAS BEEN READ IN \n";
        cout <<"##########################################\n";
    }
    else
    {
        cout << "Unable to open "<< initialEmployeeFileName  <<endl;
        return 0;
    }

    string programOption;
    do
    {

        cout << "**** Payroll Menu *****\n";
        cout <<"1. Process Weekly File\n";
        cout <<"2. Print Out Payroll\n";
        cout <<"3. Exit"<<endl;
        cout <<"Enter your choice:";
        getline(cin,programOption);
        //cout <<programOption.length()<<endl;

        switch (programOption[0])
        {

            case '1':
            {
                string filename ;
                cout << "Please enter the file name for the weekly input file:";
                getline(cin,filename);
                //cout <<filename<<endl;
                proll.clearWeeklyPayRollData();
                try
                {
                    proll.readWeeklyPayrollFile(filename);
                }
                catch (const rangeError &re)
                    {
                        cerr<<re.what() << endl;
                    }
                proll.sortEmployeesbySSN();
                break;
            }
            case '2':
            {
                cout<<"Do you wish to print to file (y\\n):";
                string print2file;
				getline(cin,print2file);
                switch (print2file[0])
				{
					case 'y':
					case 'Y':
					{
						cout<<"Please enter your output filename:";
						string outputfilename;
						getline(cin,outputfilename);
						ofstream outputDataStream(outputfilename.c_str());
						outputDataStream<<proll.displayAllEmployeeData(false,false);
                		break;
					}
					default:
					{
						bool boolDisplayLaborDetail =false;
						bool boolDisplayNoLabor =false;
						string StrDisplayLaborTransaction;
						cout <<"\n Would you like to see individual Labor Transactions? (y\\n)";
						getline(cin,StrDisplayLaborTransaction);
						switch (StrDisplayLaborTransaction[0])
						{
							case 'Y':
							case 'y':
							{
								boolDisplayLaborDetail  =true;
								break;
							}
						}


						string StrShowNoLabor;
						cout <<"\n Include Employees with no Labor? (y\\n)";
						getline(cin,StrShowNoLabor);
						switch (StrShowNoLabor[0])
						{
							case 'Y':
							case 'y':
							{
								boolDisplayNoLabor =true;
								break;
							}
						}
						cout<<proll.displayAllEmployeeData(boolDisplayLaborDetail,boolDisplayNoLabor );
						break;
					}
				}
            }
            case '3':
            {
                break;
            }
            default:
            {
                break;
            }
        }
    }
    while (programOption[0]!='3');

```

This was a easy way to read the whole line and just read the first character.  It's somewhat bullet proof your app in case someone decides to enter more than one character.  Brains are gone... Need to get to bed.. Sorry.

---

### Post by Linteg on 2011-04-10
Defining functions in the header is not the greatest idea, unless you plan on making them inline (i.e. inline int mygetch() {...}). If you include it from several cpp-files you will end up with multiple definitions of the same function which will cause trouble for the linker, hence the "multiple definition"-errors.
You should split the declaration and definition instead, in your case you would simply need to rename your .h-file .cpp and create a new mygetch.h
```

#ifndef MYGETCH_H
#define MYGETCH_H
int mygetch();
#endif

```

N.B. The reason why it is possible to define functions in c++ class declarations is that they are implicit inline functions.

---

### Post by Jonas thomas on 2011-04-10
> **Linteg said:**
> Defining functions in the header is not the greatest idea, unless you plan on making them inline (i.e. inline int mygetch() {...}). If you include it from several cpp-files you will end up with multiple definitions of the same function which will cause trouble for the linker, hence the "multiple definition"-errors.
You should split the declaration and definition instead, in your case you would simply need to rename your .h-file .cpp and create a new mygetch.h
```

#ifndef MYGETCH_H
#define MYGETCH_H
int mygetch();
#endif

```

N.B. The reason why it is possible to define functions in c++ class declarations is that they are implicit inline functions.

+1 (wish I said it as eloquently) 
Do what he just said and it will bring you to your next error
> void mainzmenu::mainmenu(){
		std::cout <<
		"	{}++++++++++++++++{}\n"
		"	{}=Midnight Cloud={}\n"
		"	{}++++++++++++++++{}\n"
		"	      Welcome...\n\n"
		"	####################\n"
		"	#                  #\n"
		"	#   >:New Game:<   #\n"
		"	#                  #\n"
		"	#    :Load Game:   #\n"
		"	#                  #\n"
		"	#    :Credits:     #\n"
		"	#                  #\n"
		"	####################\n"
		"	|  Use w and s to  |\n"
		"	| scroll and ENTER |\n"
		"	|    to select     |\n"
		"	 ==================\n";
		tri=mygetch();
		system("clear");
		switch (tri){
			case 'w':
                creditsselect();
				break;
			case '\n':
				//calls for a new game
				player newch;
				newch.name();
				system("clear");
                **mainmenu();**
				break;
			case 's':
                loadselect();
				break;
		}
        mainmenu();
}

This is what threw me yesterday night. The program was bombing until I put {} around it (which should not be needed) and moved the error elsewhere.  Looking at this a little closer I think what you got going is some type of recursion. For what your doing here, I don't think that's what you want.

Also you may want to rethink what your doing with the 
player newch;  It looks like it's locally defined. IOW it goes bye bye as soon as the switch goes out of scope.

This stuff... I catch... How to define a simple function... throws me for a loop... Geeez... 

Btw... if you guys stick with it you may want to get up your files into separate source and cpp's
something like this: [http://code.google.com/p/heekscad/source/browse/#svn%2Ftrunk%2Fsrc]("http://code.google.com/p/heekscad/source/browse/#svn%2Ftrunk%2Fsrc")

Perhaps find out game on google code and study how they're doing it.

One of the things I have on my todo list is to write a game for my daughter. I've been studying has been this website. [http://www.videotutorialsrock.com/]("http://www.videotutorialsrock.com/").  I don't think your ready for that just quite yet. But at some point, it may come in useful.

---

### Post by Ghostmn on 2011-04-10
I haven't really looked into mainmenu, but I've been wanting to change everything into an array like I did in ascii.c++. That would take away the recursion found in mainmenu. Ok so I separated mygetch into a .h .c++. I'll still get "undefined reference" which is interesting since i've only gotten them once i started introducing headers.(read that it isn't recommended to keep everything in a c.++ file) Also moved player newch.

[Edit] I'll take a look at that website once we get into opengl :P probably won't be until early next year or the year after. Can Someone check my latest build I took care of the recursion found in mainmenu and made it an array (saved 67 lines ^^).  I'm working on getting src available on google code so you don't have to download everything. I marked the previous two packages deprecated so you should only see the latest one.   
[http://code.google.com/p/midnight-cloud/downloads/list](http://code.google.com/p/midnight-cloud/downloads/list)

---

### Post by Jonas thomas on 2011-04-10
> **Ghostmn said:**
> I haven't really looked into mainmenu, but I've been wanting to change everything into an array like I did in ascii.c++. That would take away the recursion found in mainmenu. Ok so I separated mygetch into a .h .c++. I'll still get "undefined reference" which is interesting since i've only gotten them once i started introducing headers.(read that it isn't recommended to keep everything in a c.++ file) Also moved player newch.

[Edit] I'll take a look at that website once we get into opengl :P probably won't be until early next year or the year after. Can Someone check my latest build I took care of the recursion found in mainmenu and made it an array (saved 67 lines ^^).  I'm working on getting src available on google code so you don't have to download everything. I marked the previous two packages deprecated so you should only see the latest one.   
[http://code.google.com/p/midnight-cloud/downloads/list](http://code.google.com/p/midnight-cloud/downloads/list)

A little rough, but I seemed to get it running.  I added had a weird issue going on(might have been some prior build residue.  You may want to consider moving you includes except for the file your working on into your .h
for example in
combat.h just have
#include "combat.h"

In combat.h have:
#ifndef	COMBAT_H
#define COMBAT_H
#include <iostream>
#include <cstdlib>
#include <string>
#include "mygetch.h"
#include "enemies.h"

class check0{
	private:
	void picture(int x);
	public:
	void combat(int x);

	};
#endif

You don't have to do this, but it can prevent some future weirdness from occurring.  You'll probably reach a point where you'll need library for your class definition which you will have the definition already there.

Also, may want to consider modifing your function from
void mainzmenu::mainmenu()....
to
char mainzmenu::mainmenu()

Have the function return your choice so you know what to do from there in your main loop.

---

### Post by Ghostmn on 2011-04-10
So move my includes into .h? Do I still leave the includes in the .cpp?

---

### Post by Jonas thomas on 2011-04-10
> **Ghostmn said:**
> So move my includes into .h? Do I still leave the includes in the .cpp?

No. Take them out.
combat.h is the only thing that needs to be in combat.cpp

You can stick all the other stuff in combat.h  when you include combat.h in combat.cpp you have the other stuff you need already included (pun intended) ;)

---

### Post by Linteg on 2011-04-10
Are you compiling with gcc and not with g++? 
Renaming mygetch.h to mygetch.cpp and creating a new mygetch.h as mentioned above, and adding *#include "mygetch.h"* in Ascii.h was all I needed to make the code compile with:
```
g++ -Wall -pedantic -o mc *.c++
```
When I accidentally attempted to compile the code with gcc I did on the other hand get a lot of of "undefined reference" errors regarding functions in the c++ std namepace.

---

### Post by Ghostmn on 2011-04-10
Linteg thank you, that helped me compile. Now i can move on with development. Thanks to everyone who gave advice it's all been very helpful.[Edit] Added both of you to the special thanks section in credits, and in the release notes.

---


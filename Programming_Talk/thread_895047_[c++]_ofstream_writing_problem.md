---
title: "[c++] ofstream writing problem"
date: 2008-08-19
forum: Programming Talk
---

### Post by Pyro.699 on 2008-08-19
Hello,

Although I'm sure that my C++ code could use some improvements, I'm still learning and want to get to know the language a bit better. The first practice program I'm making reads from a file, takes 10 of those lines and then adds them to a new file, and then will close that file and open a new one. This is what i have so far:

[php]
// Includes
#include <sstream>
#include <string>
#include <iomanip>
#include <iostream>
#include <fstream>
#include <bitset>

//Tell g++ were using the C Libary
using namespace std;

string myFunc(int x){
    //Create String Stream
    ostringstream oss;
    
    //Set the fill type
    oss << setfill('0');
    //Create the new string
    oss << setw(10) << x ;
    
    //Return the string type
    return oss.str();
}

int main () {
    
    //In File
    string fline;
    ifstream inFile ("this.pi");
    
    //Declare outFile Variable
    ofstream outFile;
    
    //Declare counters
    int line=10;
    int lvl=0;
    
    //Read from In File
    if (inFile.is_open())
    {
        //Do until End of File
        while ( !inFile.eof() )
        {
            //Create new file
            if(line==10)
            {
                //Close previous file
                if(outFile.is_open()){
                    outFile.close();
                }
                
                //Announce new file
                cout << "New File!" << endl;
                
                //Get new file name
                ostringstream oss;
                oss << "./pi/pi." << myFunc(lvl) << ".txt";
                
                //Open new File
                ofstream outFile(oss.str().c_str());                
                
                //Set/Add counters
                line = 0;
                lvl += 1;
                
                outFile << "Works"; //This line will print
            }
            outFile << "Dosent work"; //But this line will not print, for some reason it has to be before that if statement
            
            //Get the line and place it in vatiable 'line'
            getline (inFile,fline);
                        
            //Print that line to the file
            outFile << fline;
            
            //Print that line to the stream
            cout << fline << endl;
            line += 1;
        }
        
        //Close the files
        outFile.close();
        inFile.close();
    }

    //Opening Failed
    else cout << "Unable to open file"; 

    //End main
    return 0;
}

[/php]The problem im running into is clearly displayed in the code, it will write anything thats inside of that if statement, and will only do it once because its set to run once every 10 lines.

Thanks for any advice
~Cody Woolaver

---

### Post by mike_g on 2008-08-19
I think that your problem has to do with outFile going out of scope. This is beacuse you are delclaring it inside a set of braces, so the variable wont be available after the closing brace; a bit like how variables from main arent available in functions. If you move the output stream declaration to the blue line I think it should work.
```

            [COLOR="Navy"]ostream oss;       [/COLOR]     
            //Create new file
            if(line==10)
            {
                //Close previous file
                if(outFile.is_open()){
                    outFile.close();
                }
                
                //Announce new file
                cout << "New File!" << endl;
                
                //Get new file name
                ostringstream oss;
                oss << "./pi/pi." << myFunc(lvl) << ".txt";
                
                //Open new File
                [COLOR="DarkGreen"]
//ofstream would have a limited scope here
//ofstream outFile(oss.str().c_str());     [/COLOR]           
                
                //Set/Add counters
                line = 0;
                lvl += 1;
                
                outFile << "Works"; //This line will print
           [COLOR="DarkRed"] }// <- goes out of scope at closinng brace[/COLOR]
            outFile << "Dosent work"; //But this line will not print, for some reason it has to be before that if statement
```

---

### Post by Pyro.699 on 2008-08-19
No, that didn't work. Note that i need to have the outFile be redeclared inside those braces because the file name will be constantly changing. Here is the updated code:

[php]
// Includes
#include <sstream>
#include <string>
#include <iomanip>
#include <iostream>
#include <fstream>
#include <bitset>

//Tell g++ were using the C Libary
using namespace std;

string myFunc(int x){
    //Create String Stream
    ostringstream oss;
    
    //Set the fill type
    oss << setfill('0');
    //Create the new string
    oss << setw(10) << x ;
    
    //Return the string type
    return oss.str();
}

int main () {
    
    //In File
    string fline;
    ifstream inFile ("this.pi");
    
    //Declare outFile Variable
    ofstream outFile;
    ostringstream oss;
    
    //Declare counters
    int line=10;
    int lvl=0;
    
    //Read from In File
    if (inFile.is_open())
    {
        //Do until End of File
        while ( !inFile.eof() )
        {
            //Create new file
            if(line==10)
            {
                //Close previous file
                if(outFile.is_open()){
                    outFile.close();
                }
                
                //Announce new file
                cout << "New File!" << endl;
                
                //Get new file name
                oss << "./pi/pi." << myFunc(lvl) << ".txt";
                
                //Open new File
                ofstream outFile(oss.str().c_str());                
                
                //Set/Add counters
                line = 0;
                lvl += 1;
                
                outFile << "Works"; //This line will print
            }
            outFile << "Dosent work"; //But this line will not print, for some reason it has to be before that if statement
            
            //Get the line and place it in vatiable 'line'
            getline (inFile,fline);
                        
            //Print that line to the file
            outFile << fline;
            
            //Print that line to the stream
            cout << fline << endl;
            line += 1;
        }
        
        //Close the files
        outFile.close();
        inFile.close();
    }

    //Opening Failed
    else cout << "Unable to open file"; 

    //End main
    return 0;
}
[/php]

Thanks
~Cody Woolaver

---

### Post by mike_g on 2008-08-19
Hmm, well youre still decaring it inside your loop so it will go out of scope at the closing brace.

I take it that if you change this;
```
                //Open new File
                ofstream outFile(oss.str().c_str());
```
To this:
```
                //Open new File
                outFile(oss.str().c_str());
```
It does not work?

---

### Post by Pyro.699 on 2008-08-19
Ok, i did that and only that change and was returned this error:

> 
Cody@jolteon ~/c++
$ g++ massive_file.cpp -o massive_file
massive_file.cpp: In function `int main()':
massive_file.cpp:60: error: no match for call to `(std::ofstream) (const char*)'


---

### Post by mike_g on 2008-08-19
>_< Now I get what you were saying, as you were closing the file before withing the if statement.

I think that you could declare it inside your if statement as:
```
  static ofstream outFile;
```
So it wont go out of scope (or at least you could do that in C) but its a bit of an ugly fix.

---

### Post by Pyro.699 on 2008-08-19
After making those changed i ended up getting the right number of files with only the text "Works" in each of them (once)

[php]
// Includes
#include <sstream>
#include <string>
#include <iomanip>
#include <iostream>
#include <fstream>
#include <bitset>

//Tell g++ were using the C Libary
using namespace std;

string myFunc(int x){
    //Create String Stream
    ostringstream oss;
    
    //Set the fill type
    oss << setfill('0');
    //Create the new string
    oss << setw(10) << x ;
    
    //Return the string type
    return oss.str();
}

int main () {
    
    //In File
    string fline;
    ifstream inFile ("this.pi");
    
    //Declare outFile Variable
    static ofstream outFile;
    
    //Declare counters
    int line=10;
    int lvl=0;
    
    //Read from In File
    if (inFile.is_open())
    {
        //Do until End of File
        while ( !inFile.eof() )
        {
            //Create new file
            if(line==10)
            {
                //Close previous file
                if(outFile.is_open()){
                    outFile.close();
                }
                
                //Announce new file
                cout << "New File!" << endl;
                
                //Get new file name
                ostringstream oss;
                oss << "./pi/pi." << myFunc(lvl) << ".txt";
                
                //Open new File
                ofstream outFile(oss.str().c_str());                
                
                //Set/Add counters
                line = 0;
                lvl += 1;
                
                outFile << "Works"; //This line will print
            }
            outFile << "Dosent work"; //But this line will not print, for some reason it has to be before that if statement
            
            //Get the line and place it in vatiable 'line'
            getline (inFile,fline);
                        
            //Print that line to the file
            outFile << fline;
            
            //Print that line to the stream
            cout << fline << endl;
            line += 1;
        }
        
        //Close the files
        outFile.close();
        inFile.close();
    }

    //Opening Failed
    else cout << "Unable to open file"; 

    //End main
    return 0;
}
[/php]

---

### Post by mike_g on 2008-08-19
Sorry, I meant to say declare it as static within the if statement. I edited my post, but it seems you read it before I did the edit.

---

### Post by Pyro.699 on 2008-08-19
No, I still get the same problem.

"Works"

Appears in all the files once

---

### Post by mike_g on 2008-08-20
Apparently ofstream class has an open function:
[http://www.cplusplus.com/reference/iostream/ofstream/open.html](http://www.cplusplus.com/reference/iostream/ofstream/open.html)

What you are doing at the moment is creating a new ofstream object instance each time you open a file. I think that you may be able to get this to work by reusing the original. For example:
```
int main () {
    
    //In File
    string fline;
    ifstream inFile ("this.pi");
    
[COLOR="DarkGreen"]    //Declare outFile Variable and call constructor
    ofstream outFile(oss.str().c_str()); //replace parameters somehow[/COLOR]
    
    //Declare counters
    int line=10;
    int lvl=0;
    
    //Read from In File
    if (inFile.is_open())
    {
        //Do until End of File
        while ( !inFile.eof() )
        {
            //Create new file
            if(line==10)
            {
                //Close previous file
                if(outFile.is_open()){
                    outFile.close();
                }
                
                //Announce new file
                cout << "New File!" << endl;
                
                //Get new file name
                ostringstream oss;
                oss << "./pi/pi." << myFunc(lvl) << ".txt";
                
[COLOR="DarkGreen"]                //Open new File calling member function
                outFile.open(oss.str().c_str());  [/COLOR]              
                
                //Set/Add counters
                line = 0;
                lvl += 1;
                
                outFile << "Works"; //This line will print
            }
            outFile << "Dosent work"; //But this line will not print, for some reason it has to be before that if statement
            
            //Get the line and place it in vatiable 'line'
            getline (inFile,fline);
                        
            //Print that line to the file
            outFile << fline;
            
            //Print that line to the stream
            cout << fline << endl;
            line += 1;
        }
        
        //Close the files
        outFile.close();
        inFile.close();
    }

    //Opening Failed
    else cout << "Unable to open file"; 

    //End main
    return 0;
}  
```

---

### Post by Pyro.699 on 2008-08-20
Thank you very much, this does work :) i have one final question. In notepad there seems to be a character which I'm guessing represents a new line, except it stays on the same line and is represented by a square. In other applications this is represented as a new line, any ideas how to fix that?

---

### Post by dribeas on 2008-08-20
> **Pyro.699 said:**
> Thank you very much, this does work :) i have one final question. In notepad there seems to be a character which I'm guessing represents a new line, except it stays on the same line and is represented by a square. In other applications this is represented as a new line, any ideas how to fix that?

The problem is that in windows a newline is represented by two characters 0x10 0x13 while in unix it is represented by just 0x13. Notepad does not recognize 0x13 as a newline but as a non-printable character.

Many editors allow both options, and I would advise you to not use notepad, anyway you can correct the problem with unix2dos utility (or make your own program that reads a char at a time and when it finds \n writes \r\n 0x10 0x13).

   David

---

### Post by mike_g on 2008-08-20
Yeah, I'd second that. If you havent tried it yet Notepad++ is a nice simple text editor with syntax hilighting:
[http://notepad-plus.sourceforge.net/uk/site.htm](http://notepad-plus.sourceforge.net/uk/site.htm)

---

### Post by Pyro.699 on 2008-08-20
Look closely at the screenshot ;) Thats the other editor i used

---

### Post by Pyro.699 on 2008-08-20
Using that code, i was given an error that i dont quite understand.

Error:
> 
    264 [sig] massive_file 6140 _cygtls::handle_exceptions: Error while dumping state (probably corrupted stack)
Segmentation fault (core dumped)
Code:
[php]
// Includes
#include <sstream>
#include <string>
#include <iomanip>
#include <iostream>
#include <fstream>
#include <bitset>

//Tell g++ were using the C Libary
using namespace std;

string myFunc(int x){
    //Create String Stream
    ostringstream oss;
    
    //Set the fill type
    oss << setfill('0');
    //Create the new string
    oss << setw(6) << x ;
    
    //Return the string type
    return oss.str();
}

int main () {
    
    //In File
    string fline;
    ifstream inFile ("pi.txt");
    
    //Declare outFile Variable and call constructor
    ofstream outFile;
    
    //Allow printing to the files
    bool pass = false;
    
    //Declare counters
    int line=5000;
    int lvl=0;
    
    //Read from In File
    if (inFile.is_open())
    {
        //Do until End of File
        while ( !inFile.eof() )
        {
            //Get the line and place it in vatiable 'line'
            getline (inFile,fline);
    
            //Create new file
            if(line==5000)
            {
                
                //Close previous file
                if(outFile.is_open()){
                    outFile.close();
                }
                
                //Announce new file
                cout << "New File!" << endl;
                
                //Get new file name
                ostringstream oss;
                oss << "./pi/pi." << myFunc(lvl) << ".txt";
                
                //Open new File calling member function
                outFile.open(oss.str().c_str());                
                
                //Set/Add counters
                line = 0;
                lvl += 1;
                
            }
            
            //This is the set line
            if(lvl == 1 && line == 26 && pass == false)
            {
                fline = "3." + fline;
                line = 0;
                pass = true;
            }
            
            //This means we can print to the line
            if(pass == true)
            {
                int x = fline.find(' ');
                fline.replace( x, x+1, "");
                
                            
                //Print that line to the file
                outFile << fline;
                
                //Print that line to the stream
                cout << fline << endl;
            }
            line += 1;
        }
        
        //Close the files
        outFile.close();
        inFile.close();
    }

    //Opening Failed
    else cout << "Unable to open file"; 

    //End main
    return 0;
}
[/php]Stackdump:
> 
Stack trace:
Frame     Function  Args
0022C3C8  7C802542  (00000730, 0000EA60, 000000A4, 0022C410)
0022C4E8  61097F54  (00000000, 7C802600, 7C802542, 000000A4)
0022C5D8  61095AEB  (00000000, 003B0023, 00230000, 0022CE68)
0022C638  61095FCB  (0022C650, 00000000, 00000094, 610253F0)
0022C6F8  61096182  (000017FC, 00000006, 0022C728, 61096383)
0022C708  610961AC  (00000006, 0022CE88, 0022C778, 00404933)
0022C728  61096383  (0022C758, 006B08F8, 0022C7BC, 00000001)
0022C778  00404947  (006B08F8, 0022C7BC, 0022C838, 0040B045)
0022C788  00404B76  (006B08F8, 004481D0, 00432C34, 0022C820)
0022C838  0040B045  (0044713B, 00000000, 611030E8, 00411B10)
0022C8F8  004306B4  (0022CCC0, FFFFFFFF, 00000000, 00447022)
0022C928  00430495  (0022CCC0, FFFFFFFF, 00000000, 00447022)
0022CCE8  004017E9  (00000001, 6116B690, 006A0090, 0022CC70)
0022CD98  610060D8  (00000000, 0022CDD0, 61005450, 0022CDD0)
61005450  61004416  (0000009C, A02404C7, E8611021, FFFFFF48)
Exception: STATUS_ACCESS_VIOLATION at eip=61016583
eax=EC815356 ebx=61108148 ecx=00000000 edx=57E58959 esi=0000000F edi=00000001
ebp=0069C8B8 esp=0069C8B0 program=C:\cygwin\home\Cody\c++\massive_file.exe, pid 6140, thread sig
cs=001B ds=0023 es=0023 fs=003B gs=0000 ss=0023
Stack trace:
Frame     Function  Args
0069C8B8  61016583  (61108148, 6111C19B, FFFFFF48, 00000000)
0069C8D8  610166EC  (00000001, 00000000, 00000000, 0069C960)
0069C918  61017FD5  (000007B8, 0069C960, 00000000, 00000000)
0069CC58  61018638  (00000744, 0069CC90, 000000A4, 0069CC8C)
0069CD58  61099F57  (61106F00, 00000000, 00000000, 00000000)
0069CD88  61002F32  (0069CE64, 61018970, 00001074, 00000000)
61003650  61003769  (04A16430, 89000000, FFDA90B0, 24468BFF)
    264 [sig] massive_file 6140 _cygtls::handle_exceptions: Error while dumping state (probably corrupted stack)
Thanks
~Cody Woolaver

---

### Post by mike_g on 2008-08-20
A segfault error occurs when a program tries to access memory that does not belong to it. I'm not all that familiar with g++ error messages, but it seems as if you may be blowing the stack.

When you call a function it has a set amount of memory set aside for the variables in it. IIRC on windows this is 1MB. If you then try and create a very large array it will use up more memory than the stack and your prog will crash.

To avoid blowing the stack you can use **new** to allocate memory that will reside elsewhere. Each time you call new you need to remember to delete the allocated memory when youre done with it. I'm not sure how to go about fixing the code atm, (been a while snce i used c++) but my best guess is that you may be buffering a lot of data from a file and thats blowing the stack.

---

### Post by Pyro.699 on 2008-08-20
Yeah.... xD would reading 1 billion lines from a text file do that? because thats what is going on. No editor could open the data, so im splitting it into several files. Using my code above, how would you do that?

---

### Post by mike_g on 2008-08-20
Hmm.. have you tried reducing the line size here:
```
            if(line==5000)
            {
                
```
If a line is 100 chars long on average then thats going to eat up around ~50KB

---

### Post by Pyro.699 on 2008-08-20
The file is layed out like this. There is about 1 billion lines, at around 100 characters long per line (its ALOT of numbers). It will take 5000 lines and put them into a new file, then close that file and make a new one. If i lower the number it will make more files, which is what im trying to avoid. At the moment they are all placed into one file which i around 1gb large (unable to be opened by any application).

---

### Post by mike_g on 2008-08-20
In that case I think that you are going to have to allocate inFile and outFile dynamically. Alternatively, to test if its the problem could try delcaring them as globals - as globals dont reside within the stack. To do that just declare your ofstream and ifstream before main. If youre still haveing problems then it could be something else.

Edit: or, you could try flushing the buffers once you have finished reading/writing bits:
[http://www.cplusplus.com/reference/iostream/ostream/flush.html](http://www.cplusplus.com/reference/iostream/ostream/flush.html)
That might be the best wayto go about it.

---

### Post by Pyro.699 on 2008-08-20
Nope, i still get this error

  25017 [sig] massive_file 3916 _cygtls::handle_exceptions: Error while dumping state (probably corrupted stack)
Segmentation fault (core dumped)

EDIT: i did use the flush method btw

---


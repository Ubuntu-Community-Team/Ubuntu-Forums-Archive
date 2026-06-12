---
title: "C++ Search a line from text file for a string."
date: 2010-09-24
forum: Programming Talk
---

### Post by cgroza on 2010-09-24
Hello, i am trying to build my address book search function. What I am asking is that i can use a for loop to loop through the text file and search for a specific word. In python this is easily made with:

fob = open("file.txt",r)
>> for line in fob:
>>>>       if search in line:
>>>>>>>>>># do something

But how can i get  a similar effect in C++?
Thanks.

---

### Post by James78 on 2010-09-24
String::find may help you get started.

[http://www.cplusplus.com/reference/string/string/find/](http://www.cplusplus.com/reference/string/string/find/)

---

### Post by cgroza on 2010-09-24
I will take a look, thanks.

---

### Post by cgroza on 2010-09-24
im stuck, could some one give me the code please?

---

### Post by dwhitney67 on 2010-09-25
> **cgroza said:**
> im stuck, could some one give me the code please?

How stuck are you?  Please _show_ what you have.  Surely you have managed to open the file, and read each line (into a string object), right?

The Ubuntu forums is not a place for asking for help on homework assignments, and with the simpleness of the task you are asking about, it sure does seem like homework.

---

### Post by cgroza on 2010-09-26
Actually i have no idea how to do it. i have no code now because i tried so many methods described but they were for single word lines... not for lines that contain more words.

---

### Post by dwhitney67 on 2010-09-26
> **cgroza said:**
> Actually i have no idea how to do it. i have no code now because i tried so many methods described but they were for single word lines... not for lines that contain more words.

Use std::getline().  For example:
```

#include <iostream>
#include <string>

int main()
{
   std::string fullname;

   std::cout << "Enter your full name: ";
   std::getline(std::cin, fullname);

   std::cout << "Hello " << fullname << "!" << std::endl;
}

```

P.S.  If you are reading from a file (eg. an ifstream), substitute the std::cin above with the file handle.

---

### Post by Sub101 on 2010-09-26
> **dwhitney67 said:**
> Use std::getline().  For example:
```

#include <iostream>
#include <string>

int main()
{
   std::string fullname;

   std::cout << "Enter your full name: ";
   std::getline(std::cin, fullname);

   std::cout << "Hello " << fullname << "!" << std::endl;
}

```

P.S.  If you are reading from a file (eg. an ifstream), substitute the std::cin above with the file handle.

In this case I wouldnt even bother with getline. Something simply like;

```

std::string myString;
while(!instream.eof()){ 
         instream >> myString;
}

```
(I know the file constructor is missing, that is intentional)

---

### Post by cgroza on 2010-09-26
Thank you very much for your understanding.

---

### Post by dwhitney67 on 2010-09-26
> **Sub101 said:**
> In this case I wouldnt even bother with getline. Something simply like;

```

std::string myString;
while(!instream.eof()){ 
         instream >> myString;
}

```
(I know the file constructor is missing, that is intentional)

Do you ever test your code before shooting off a response?

If you have trouble formulating an answer, let me help... NO.

---

### Post by Sub101 on 2010-09-26
> **dwhitney67 said:**
> Do you ever test your code before shooting off a response?

If you have trouble formulating an answer, let me help... NO.

As I have clearly said I know parts are missing. This is purely to ensure the OP does some of his own research rather than copying and pasting my work.

With the file constructor the code would work.

---

### Post by dwhitney67 on 2010-09-26
> **Sub101 said:**
> As I have clearly said I know parts are missing. This is purely to ensure the OP does some of his own research rather than copying and pasting my work.

With the file constructor the code would work.

I was not referring to the file constructor.  Test your code out!  Replace the file stream handle with std::cin (or use a file stream handle if you wish), but your code will only save off the last word entered.

So if you run the program and enter, for example, "Mary had a little lamb", the myString will be assigned the last word ("lamb").  All of the preceding words are lost.

P.S.  To generate an EOF with std::cin, use ctrl-d.

---

### Post by Sub101 on 2010-09-26
> **dwhitney67 said:**
> I was not referring to the file constructor.  Test your code out!  Replace the file stream handle with std::cin (or use a file stream handle if you wish), but your code will only save off the last word entered.

So if you run the program and enter, for example, "Mary had a little lamb", the myString will be assigned the last word ("lamb").  All of the preceding words are lost.

P.S.  To generate an EOF with std::cin, use ctrl-d.

Yes I am aware of that... If the user wants to find a certain word in a file is there really any purpose in storing the entire file?

Naturally if I were to use the code myself I would add in the if statement within the while loop and a few other controls to ensure speed depending on the usage. Yet I will repeat what I have said before. I did not wish to give the OP perfectly usable code but just a basis of understanding, as I am sure, based on your code, was your wish also.

---

### Post by dwhitney67 on 2010-09-26
> **Sub101 said:**
> Yes I am aware of that... If the user wants to find a certain word in a file is there really any purpose in storing the entire file?

Naturally if I were to use the code myself I would add in the if statement within the while loop and a few other controls to ensure speed depending on the usage. Yet I will repeat what I have said before. I did not wish to give the OP perfectly usable code but just a basis of understanding, as I am sure, based on your code, was your wish also.

I don't think you have a clue what the OP was asking about.  From what I understood, he wanted to know how to read in an entire line of (ASCII) data into a string -- without trickery of using while-loops or conditional checks; getline offers this functionality, whether reading from a file or standard-in.

---

### Post by Sub101 on 2010-09-26
> **cgroza said:**
> What I am asking is that i can use a for loop to loop through the text file and search for a specific word. 


Ok?

---

### Post by dwhitney67 on 2010-09-26
> **cgroza said:**
> Actually i have no idea how to do it. i have no code now because i tried so many methods described but they were for single word lines... not for lines that contain more words.

Ok, you got me.  I was focused on this post, not the first in the thread.

---

### Post by cgroza on 2010-09-26
> **Sub101 said:**
> As I have clearly said I know parts are missing. This is purely to ensure the OP does some of his own research rather than copying and pasting my work.

With the file constructor the code would work.

Thank you for that, i appreciate it.

---

### Post by cgroza on 2010-09-26
> **Sub101 said:**
> In this case I wouldnt even bother with getline. Something simply like;

```

std::string myString;
while(!instream.eof()){ 
         instream >> myString;
}

```(I know the file constructor is missing, that is intentional)


May i know what !instream.eof does in line 2?
or is should replace that with my file object?

---

### Post by dwhitney67 on 2010-09-26
> **cgroza said:**
> May i know what !instream.eof does in line 2?
or is should replace that with my file object?

Read this: [http://www.cplusplus.com/reference/iostream/ios/eof/](http://www.cplusplus.com/reference/iostream/ios/eof/)

---

### Post by cgroza on 2010-09-26
Ok, so far i think its ok. The code looks like this now : 


```
using namespace sdt;
ifstream dafi;
dafi.open("/home/cgroza/.contactsc")

string search;
cout <<"Enter the search criteria:"<<endl;
cin >> search;
std::string line;
while(!dafi.eof()){ 
         dafi >> line;
         strstr(line,search)
         
}
```

Now how do i make an if statement to check if the strstr() funtion found something? Note that im learning C++ for about 1 week and i am trying to create a simple address book.

---

### Post by dwhitney67 on 2010-09-26
> **cgroza said:**
> 
Now how do i make an if statement to check if the strstr() funtion found something? Note that im learning C++ for about 1 week and i am trying to create a simple address book.

Have you ever programmed in pure C?  Because it would appear that you are familiar with the C library function strstr().  You should avoid using that low-level function in C++ applications.  Instead use the available methods associated with the STL string class (eg. find()).

```

...
   if (line.find(search) != std::string::npos)
   {
      // sub-string was found in line.
   }
...

```

Read here for more information about the STL string:  [http://www.cplusplus.com/reference/string/string/](http://www.cplusplus.com/reference/string/string/)

---

### Post by cgroza on 2010-09-26
So there is a much simple way to do it? ok, thanks... ill be around for a while. Thanks for your help.

---

### Post by cgroza on 2010-09-26
So far here is the results:

```
using namespace std;
ifstream dafi;
dafi.open("/home/cgroza/.contactsc");

string search;
cout <<"Enter the search criteria: \n"; 
cin >> search;
std::string line;
while(!dafi.eof()){ 
         dafi >> line;
         if (line.find(search) != std::string::npos)
         {
           cout << line << endl;                    
                               }
                                         
}

```

---

### Post by dwhitney67 on 2010-09-26
And does it work?  In other words, when you display the "line", does it show the entire line of where the string 'search' occurred?


[SIZE="1"]
P.S.  I bet it doesn't[/SIZE].

---

### Post by Geek10 on 2010-09-27
You may or may not find this useful (some of it is exactly applicable to your question), but this is some code I did recently to search in a large text file for the word "image" to extract the integer after the word "image". Once I had the correct number, I could then extract the data for that image number which came in a block of numbers.

Note that since it was such a large text file, I searched backwards because I knew the number I wanted was likely to be at the end of the file.

```

#include <iostream>
#include <string>
#include <conio.h> //needed for getch()
#include <sstream>
#include <fstream>
using namespace std;
#define numLidarBeams 529                    // Total LIDAR beams per scan

int* loadLogData(int desiredImageNumber)
{
    //Initialisation
    float GPSeasting;
    float GPSnorthing;
    float GPSaltitude;
    float GPSspeed;
    
    float IMUyaw;
    float IMUpitch;
    float IMUroll;

    int *Readings = new int[numLidarBeams];

    int imgNum = -1;                // Initialise the integer for the found image number value
    int bufferSize = 500;
    string searchString("image");
    long int currentPtrPosn; // Where the pointer is up to searching
    int eofPtrPosn;
    char * buffer;         // to store search search block of code
    buffer = new char [bufferSize]; // allocate memory
    
    ifstream inFile;    // Initiate the input file stream
    inFile.open("C:\\datafile.txt", ifstream::in);

    inFile.seekg (0, ios::end);    // Go to the end of the file
    eofPtrPosn = inFile.tellg();    // Store the end of file address to an integer
    currentPtrPosn = eofPtrPosn;
    while (desiredImageNumber != imgNum){

        // go back one buffer size in the text file (the 11 accounts for the possible overlap
        // of "image #####" across the buffer ends except for the first read at the end of file
        if(eofPtrPosn == currentPtrPosn){
            currentPtrPosn = eofPtrPosn - bufferSize;
        }else{
            currentPtrPosn = currentPtrPosn - bufferSize + 11;
        }
        inFile.seekg (currentPtrPosn);
        currentPtrPosn = inFile.tellg();
        // read data into buffer
        inFile.read (buffer,bufferSize);
        
        //display buffer read
        cout << "The contents of the buffer are: " << endl;
        cout << "________________________________________" << endl;
        cout.write (buffer,bufferSize);
        cout << endl << "________________________________________" << endl;
        
        // Put contents of buffer into a string
        string bufferString(buffer);    
        
        // size_type imageStringAddr is the location of the first string matching searchString 
        //IN the string bufferStringfound by .find
        string::size_type imageStringAddr = bufferString.find(searchString, 0);
        //cout << "imageStringAddr: " << imageStringAddr << endl;
        //cout << "imageNumInTextPosn: " << imageNumInTextPosn << endl;
        //cout << "(currentPtrPosn + imageStringAddr): " << (currentPtrPosn + imageStringAddr) << endl;
        if (imageStringAddr != string::npos){    // If the location of the first string is not at the end of the string
            // This makes a string out of the characters following the space after "image"
            string numberString = bufferString.substr(imageStringAddr + searchString.size() + 1);
            // stringstream provides an interface to manipulate strings as if they were input/output streams.
            stringstream numberStream(numberString);
            if((numberStream >> imgNum).fail()){    // Convert stream to integer
                cout << "ERROR: Failed string to integer conversion";
            }
            cout << "imgNum integer: " << imgNum << endl;
            
            // Find the number of digits in imgNum
            int imgNumDigits = 0;
            int step = 1;
            while (step <= imgNum) {
                imgNumDigits++;
                step *= 10;
            }        
            // The "+2" accounts for buffer overlap, not sure why - "\n"? perhaps?
            inFile.seekg (currentPtrPosn + imageStringAddr + searchString.size() + imgNumDigits + 2);
        }
    }
    delete[] buffer;    // Do this outside the loop to avoid unnecessary thrashing of the heap
    inFile >> GPSeasting;
    cout << "GPSeasting: " << GPSeasting << endl;
    inFile >> GPSnorthing;
    cout << "GPSnorthing: " << GPSnorthing << endl;
    inFile >> GPSaltitude;
    cout << "GPSaltitude: " << GPSaltitude << endl;
    inFile >> GPSspeed;
    cout << "GPSspeed: " << GPSspeed << endl;
    inFile >> IMUyaw;
    cout << "IMUyaw: " << IMUyaw << endl;
    inFile >> IMUpitch;
    cout << "IMUpitch: " << IMUpitch << endl;
    inFile >> IMUroll;
    cout << "IMUroll: " << IMUroll << endl;
    
    for(int i=0; i<numLidarBeams; i++){
      inFile >> Readings[i];
    }
    cout << "curData.curLidar.Readings[0]: " << Readings[0] << endl;
    
    inFile.close();
    //getch();
   return Readings;
}

```And dwhitney67, you seem to be hot on the trail of any code-posters for errors from the looks of a number of threads. If you feel like it, I would genuinely appreciate any suggestions I can learn from you about the readability/style/function/thinking of my code.:)

---

### Post by dwhitney67 on 2010-09-27
> **Geek10 said:**
> And dwhitney67, you seem to be hot on the trail of any code-posters for errors from the looks of a number of threads. If you feel like it, I would genuinely appreciate any suggestions I can learn from you about the readability/style/function/thinking of my code.:)

Everybody has their own style of coding; what I like to see when I read code is a little more separation of code statements, so that individual sections of the code appear as "blocks", as opposed to one contiguous chunk of code.

At first glance of the code you posted, some vertical white-space (ie. newlines) would be nice; and remove dead/commented-out code.

Also, avoid declaring a variable until it is needed, and consider initializing the variable when it is declared.

Btw, for whatever reason, I cannot comprehend why you manually computed the number of digits in the number that was found.  If you had a number, say "1234", in string format, using the size() method would have told you that there are 4-digits in that number.  Anyhow, maybe because of the lack of vertical separation of code, I may have missed something that justifies what you did.

---

### Post by Geek10 on 2010-09-27
Sorry OP, it might seem I am hijacking your post, but you admitted you were a beginner like me, so I am sure you would appreciate learning from more experienced programmer's answers to my questions on dwhitney67's comments.

> **dwhitney67 said:**
> Everybody has their own style of coding; what I like to see when I read code is a little more separation of code statements, so that individual sections of the code appear as "blocks", as opposed to one contiguous chunk of code.

At first glance of the code you posted, some vertical white-space (ie. newlines) would be nice; and remove dead/commented-out code.

Ah. I see what you mean. It must be a bit confusing to a first time reader.

> **dwhitney67 said:**
> Also, avoid declaring a variable until it is needed, and consider initializing the variable when it is declared.
What do you mean exactly by this? It looks highly important for the rest of my career!
Do you mean:
Instead of:
```

variable = 1;    // Initialisation so it is not garbage
variable = AnotherVariable*2;

```just do this?
```

variable = AnotherVariable*2;

```
> **dwhitney67 said:**
> Btw, for whatever reason, I cannot comprehend why you manually computed the number of digits in the number that was found.  If you had a number, say "1234", in string format, using the size() method would have told you that there are 4-digits in that number.  Anyhow, maybe because of the lack of vertical separation of code, I may have missed something that justifies what you did.

Your keen eyes didn't miss a thing. Pure lack of programming experience on my part. size() is the better way to go, I just didn't think of it!

---

### Post by dwhitney67 on 2010-09-27
For example, to initialize a variable...
```

double var1 = 0.0;

std::cout << "Enter a floating point number: ";
std::cin  >> var1;

double var2 = pow(var1, 2.0);
...

```
For complex objects, surely there is a constructor that is called to initialize the object; for example, the STL string or the STL fstream.

Still, with the STL fstream, one can do:
```

std::fstream file("myfile", std::ios::in);

// as opposed to

std::fstream file;
file.open("myfile", std::ios::in);

```
But regardless, both styles yield the same result.

---

### Post by Geek10 on 2010-09-27
> **dwhitney67 said:**
> Also, avoid declaring a variable until it is needed, and consider initializing the variable when it is declared.
:idea: Aha! So you mean, rather than declaring all of my variables at the start of the program, I just declare them as I need them. This means people following my code (and myself when I review it) don't have to recall if it was initialised in the first place, and don't see lines of unrelated declarations at the start of the code. Is that it?

Also, people would see why the variable was initialised, and as long as I am sensible with naming, they can see why it was named that way.

And thanks for those 2 examples above. Your comments with the code have turned on the light for me! You are a legend!:KS

---

### Post by dwhitney67 on 2010-09-27
> **Geek10 said:**
> :idea: Aha! So you mean, rather than declaring all of my variables at the start of the program, I just declare them as I need them. This means people following my code (and myself when I review it) don't have to recall if it was initialised in the first place, and don't see lines of unrelated declarations at the start of the code. Is that it?

Jackpot!

> **Geek10 said:**
> 
Also, people would see why the variable was initialised, and as long as I am sensible with naming, they can see why it was named that way.

Another jackpot!

> **Geek10 said:**
> 
And thanks for those 2 examples above. Your comments with the code have turned on the light for me! You are a legend!:KS
You're welcome.

Now, hopefully the OP will chime in to let us know the progress of his assignment.

---

### Post by cgroza on 2010-09-27
Ok, you are right, it asks me for the input but after i press enter it returns nothing. It just stays there.
Could you suggest me what should i do?
There is the code again.

```
void read() 
{ 
using namespace std; 
ifstream dafi; 
dafi.open("/home/cgroza/.contactsc"); 
 
string search; 
cout <<"Enter the search criteria: \n";  
cin >> search; 
std::string line; 
while(!dafi.eof()){  
         dafi >> line; 
         if (line.find(search) !=string::npos)          
          cout << line << endl;                     
                                                                         
} 
}
```

---

### Post by dwhitney67 on 2010-09-27
> **cgroza said:**
> Ok, you are right, it asks me for the input but after i press enter it returns nothing. It just stays there.
Could you suggest me what should i do?
There is the code again.


```

#include <fstream>
#include <string>
#include <iostream>

int main()
{
   using namespace std;

   string filename = "/home/cgroza/.contactsc";

   ifstream dafi(filename.c_str());

   if (dafi)
   {
      string search;
      string line;

      cout << "Enter the search criteria: ";
      cin  >> search;

      while (getline(dafi, line))
      {
         if (line.find(search) != std::string::npos)
         {
            cout << line << endl;
         }
      }
   }
   else
   {
      cerr << "Cannot open file " << filename << endl;
      return -1;
   }

   return 0;
}

```

---

### Post by cgroza on 2010-09-27
Great, you rock!

---

### Post by cgroza on 2010-09-27
I'm back. This time with a different error. Its in this function and I am trying to call some functions ad it says that they are not declared in this scope. Here is the code: 

```

void choose() 
{ 
    using namespace std;
     
    char choice;
    cout <<"Enter:\n1 to Add and entry.\n2 to Search an entry.\n3 to Remove an entry.\n4 to Show All.\n5 to IMPORT\EXPORT.\n6 to DESTROY ALL DATA.\nq to QUIT.1/2/3/4/5/6/q/: ";         
    cin >> choice;
    switch (choice)
    {
        case 1:
        create();
        break;
         
        case 2:
        read();
        break;
         
        case 4:
        show();
        break;
         
        case 6:
        destroy();
        break;
         
        }
     
    }
```

---

### Post by Sub101 on 2010-09-27
> **cgroza said:**
> I'm back. This time with a different error. Its in this function and I am trying to call some functions ad it says that they are not declared in this scope. Here is the code: 

```

void choose() 
{ 
    using namespace std;
     
    char choice;
    cout <<"Enter:\n1 to Add and entry.\n2 to Search an entry.\n3 to Remove an entry.\n4 to Show All.\n5 to IMPORT\EXPORT.\n6 to DESTROY ALL DATA.\nq to QUIT.1/2/3/4/5/6/q/: ";         
    cin >> choice;
    switch (choice)
    {
        case 1:
        create();
        break;
         
        case 2:
        read();
        break;
         
        case 4:
        show();
        break;
         
        case 6:
        destroy();
        break;
         
        }
     
    }
```

If I understand your question properly then you need to ensure methods are declared in the header file.

I really think you need to take a look at a c++ book or any of the online resources available.

---

### Post by cgroza on 2010-09-27
> **Sub101 said:**
> If I understand your question properly then you need to ensure methods are declared in the header file.

I really think you need to take a look at a c++ book or any of the online resources available.

You are right because i am following video tutorials and it seems they don't teach everything.

---

### Post by cgroza on 2010-09-27
Could you explain me how to do that because i have problems finding information about how to do this.

---

### Post by Sub101 on 2010-09-27
> **cgroza said:**
> Could you explain me how to do that because i have problems finding information about how to do this.

[http://en.wikipedia.org/wiki/Header_file](http://en.wikipedia.org/wiki/Header_file)

Essentially they make the methods visible to other methods. The examples in the wiki are fairly good examples.

---

### Post by cgroza on 2010-09-27
Ohh, i found the problem... i moved the definitions at the top of the file and now it works. Thanks . I will take a look.

---

### Post by cgroza on 2010-09-27
Its me again... I am trying to make a function that removes a line from a text file based on the my search function and i never got a chance to test it because i get this 2 errors:

adrook.cpp:136: error: expected initializer before ‘}’ token
adrook.cpp:136: error: expected declaration before ‘}’ token


Here is the code again:

```
void remover() 
} 
 
   using namespace std; 
 
   string filename = "/home/cgroza/.contactsc"; 
 
   ifstream dafi(filename.c_str()); 
   ofstream newdafi; 
   newdafi.open("/home/cgroza/.tempcontactsc",ios::app) 
    
   if (dafi) 
   { 
      string toremove; 
      string line; 
 
      cout << "Enter the entry name to delete: "; 
      cin  >> toremove; 
 
      while (getline(dafi, line)) 
      { 
         if (line.find(toremove) != std::string::npos) 
         { 
            cout <<""; 
         } 
         else 
         newdafi<<line; 
           
      } 
   } 
   else 
    
      cerr << "Cannot open file " << filename << endl; 
           
   rename("/home/cgroza/.tempcontactsc","/home/cgroza/.contactsc")   
   }     
    

```

---

### Post by Sub101 on 2010-09-27
```
   newdafi.open("/home/cgroza/.tempcontactsc",ios::app) 
```

Needs a semi-colon - I expect thats the problem. Otherwise go to line 136 as the compiler says and take a look.

And the first semi colon after the method declaration is reversed.

Please take some time before posting.

---

### Post by cgroza on 2010-09-27
Right , didnt developed my wild programmer instincts yet. LOL, Thank you very much.

EDIT: i put a semicolon at the end of that line and i still get the error.

---

### Post by cgroza on 2010-09-27
I solved the the initializer error. Thank you for your quick reply and  help.

---

### Post by cgroza on 2010-09-28
So now i'm trying to insert a variable into a system("") line. This is the code:


```
void importer() 
{ 
    using namespace std;     
    string ask; 
    cout<<"Enter tha path of the file to import: "<<endl; 
    cin>>ask; 
     
    system("cp "+ask+" /home/cgroza/.contactsc"); 
    cout << ask <<endl;       
    }
```

But i get this error when i compile:

error: cannot convert ‘std::basic_string<char, std::char_traits<char>, std::allocator<char> >’ to ‘const char*’ for argument ‘1’ to ‘int system(const char*)’

Is anyone patient enough to indicate me what is the problem?

---

### Post by GeneralZod on 2010-09-28
```

void importer() 
{ 
    using namespace std;     
    string ask; 
    cout<<"Enter tha path of the file to import: "<<endl; 
    cin>>ask; 
     
    system("cp "+ask+" /home/cgroza/.contactsc"); 
    cout << ask <<endl;       
}

```

"system" is a C function and takes a char*.  The result of "cp "+ask+" /home/cgroza/.contactsc", however, is a C++ string, and there is no implict conversion from a C++ string to a C char*.

Something like:

```

system(("cp "+ask+" /home/cgroza/.contactsc").c_str()); 

```

would work, but is ugly: maybe something like

```

const string copyCommand = "cp "+ask+" /home/cgroza/.contactsc";
system(copyCommand.c_str()); 

```

would be a little better.

---

### Post by cgroza on 2010-09-28
Thanks for your time. I actually prefer the first solution.

---

### Post by cgroza on 2010-09-28
Just one more thing. My address book is finished now but it works just for me.  How can i find the users home folder and store it under a string variable? I don't need the exact code, just if there are some libs that allow me to do this.

---

### Post by dwhitney67 on 2010-09-28
Typically the HOME environment variable will suffice.

```

#include <cstdlib>
...
const char* homedir = getenv("HOME");

if (!home)
{
   // environment variable not defined.

   // exit or do something creative. 
}

// otherwise continue...

```

---

### Post by cgroza on 2010-09-28
Thanks, I lost the count of how many times you helped me.

---

### Post by cgroza on 2010-09-28
Oh, its me again. :(. Here is the code:

```
void homefolder(){
using namespace std;
const char* datafile = getenv("HOME");
const char* tempfile = getenv("HOME");
string homedir;
string homedir2;
homedir = datafile+".contactsc";
homedir2 =tempfile+".tempcontacstc";
}
```

 I guess the code explains what im trying to do. I get these errors:
invalid operands of types ‘const char*’ and ‘const char [11]’ to binary ‘operator+’|

invalid operands of types ‘const char*’ and ‘const char [15]’ to binary ‘operator+’|

---

### Post by GeneralZod on 2010-09-29
You can't concatenate C-style strings (char*'s and char arrays) using "+".

```

void homefolder(){
using namespace std;
const string datafile = getenv("HOME");
const string tempfile = getenv("HOME");
const string homedir = datafile+".contactsc";;
const string homedir2 = tempfile+".tempcontacstc";;
}

```

(NB: the const's aren't necessary in my snippet: it's a stylistic choice).

Edit: VVV

Oops - didn't think of that :)

---

### Post by dwhitney67 on 2010-09-29
> **GeneralZod said:**
> You can't concatenate C-style strings (char*'s and char arrays) using "+".

```

void homefolder(){
using namespace std;
const string datafile = getenv("HOME");
const string tempfile = getenv("HOME");
const string homedir = datafile+".contactsc";;
const string homedir2 = tempfile+".tempcontacstc";;
}

```

(NB: the const's aren't necessary in my snippet: it's a stylistic choice).

Be wary of assigning the results of getenv() directly to an STL string.  If getenv() returns a NULL value, the app will go "poof!"; actually, an exception is thrown.

```

#include <cstdlib>
#include <string>
#include <stdexcept>
#include <iostream>


int main()
{
   try
   {
      std::string foo = getenv("FOO");
   }
   catch (std::exception& e)
   {
      std::cerr << "FOO is not defined, and furthermore " << e.what() << std::endl;
   }
}

```

---

### Post by cgroza on 2010-09-29
I get his now when i try to use the variable:

error: no matching function for call to ‘std::basic_ifstream<char, std::char_traits<char> >::basic_ifstream(const std::string&)’|

---

### Post by dwhitney67 on 2010-09-29
Oh please bookmark this page:  [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)


If you examine the constructor for fstream, or specifically ifstream, you will see that it accepts a const char* string, not an STL string.

Details:  [http://www.cplusplus.com/reference/iostream/ifstream/ifstream/](http://www.cplusplus.com/reference/iostream/ifstream/ifstream/)


Use the STL string's c_str() method to derive the const char*.

---

### Post by GeneralZod on 2010-09-29
> **cgroza said:**
> I get his now when i try to use the variable:

error: no matching function for call to ‘std::basic_ifstream<char, std::char_traits<char> >::basic_ifstream(const std::string&)’|

Please post code - I'm having to guess what you're doing, here!

Rather confusingly (IMO), ifstream does not have a constructor that takes a string, so you need to use c_str() e.g. instead of 

```

const string someFileName = "sausage";
ifstream fileinStream(someFileName);

```

one must do


```

const string someFileName = "sausage";
ifstream fileinStream(someFileName.c_str());

```

---

### Post by cgroza on 2010-09-29
Ohh, you are right, i was having an idea to do this from previous code but i never tried it. Thanks.

---


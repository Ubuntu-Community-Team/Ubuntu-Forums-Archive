---
title: "C++ std::length_error when deleting array..."
date: 2010-03-07
forum: Programming Talk
---

### Post by OVERPOWER8 on 2010-03-07
The program is correct, although it throws an exception. What's the problem?

Here's the output:
```

./program
I 5 6
X
terminate called after throwing an instance of 'std::length_error'
  what():  basic_string::_S_create
Aborted

```

And here's the code:
```
#include <sstream>
#include <cstring>
#include <iostream>
using namespace std;

char** PixelsArray;
int g_M, g_N;                        // M, N 

void CreateImage(int M, int N)        // cols, rows
{
    PixelsArray = new char*[M+1];
    
    for(int i=0; i<=M; i++)
        PixelsArray[i] = new char[N+1];
    
    g_M = M;            g_N = N;
}

void DeleteImage()
{    
    for(int i=0; i<=g_M; i++)
        delete [] PixelsArray[i];
    
    delete [] PixelsArray;
}

int main()
{
    string input;
    
    int var1, var2;
    char cmd;

    for(;;)
    {
        getline(cin, input);
        
        cmd = input[0];
        input.erase(input.begin(), input.begin()+2);
        
        switch(cmd)
        {
            case 'I':
            {
                stringstream(input) >> var1 >> var2;
                CreateImage(var1, var2);
                break;
            }
            
            case 'X':
            {
                DeleteImage();
                return 1;
            }
        }
    }

    return 0;
}

```

---

### Post by Queue29 on 2010-03-07
```
cmd = input[0];
        input.erase(input.begin(), input.begin()+2);
```

What are you doing?

---

### Post by dwhitney67 on 2010-03-07
Could you possible write any worse code?

Where's the prompt for the input?

Why are you allocating an additional array item than the user requested?

Why are you using global variables?

Why the infinite loop in main()?

What is this supposed to do?
```

        getline(cin, input);
        
        cmd = input[0];
        input.erase(input.begin(), input.begin()+2);

```

The list goes on and on......



P.S.  A simple program to assist you with learning:
```

#include <iostream>

int main()
{
   using namespace std;

   int num = 0;

   cout << "How many elements to create: ";
   cin  >> num;

   // create
   //
   char** pixelArray = new char*[num];    // no need for the +1

   for (size_t n = 0; n < num; ++n)       // no need for the <=
   {
      pixelArray[n] = new char[num];      // no need for the +1
   }


   // destroy
   //
   for (size_t n = 0; n < num; ++n)
   {
      delete [] pixelArray[n];
   }
   delete [] pixelArray;
   
}

```

---

### Post by MadCow108 on 2010-03-07
in other words:
when you input X (or something smaller 2) your end iterator used in erase is invalid.

---

### Post by OVERPOWER8 on 2010-03-07
[Queue29]("http://ubuntuforums.org/member.php?u=342869") and [dwhitney67]("http://ubuntuforums.org/member.php?u=322753") :
learn to read bash code first!

[MadCow108]("http://ubuntuforums.org/member.php?u=804725") can read it, and he had no silly questions, Quickly found the mistake.
Big thanks to him.


P. S. I have posted only structure of my program.

Here's the entire code, may be you'll understand it:

```
#include <iostream>
#include <cstring>
#include <sstream>
using namespace std;

char** PixelsArray;
int g_M, g_N;                        // M, N 

bool CheckCmd(char cmd)
{
    char Approvable[] = "IMCLVHKFSX";
    
    for(int i=0; i<strlen(Approvable); i++)
        if(cmd == Approvable[i])
            return true;
    
    return false;
}

void ClearImage();

void CreateImage(int M, int N)        // cols, rows
{
    PixelsArray = new char*[M+1];
    
    for(int i=0; i<=M; i++)
        PixelsArray[i] = new char[N+1];
    
    g_M = M;
    g_N = N;
    
    ClearImage();
    
}

void DeleteImage()
{    
    for(int i=0; i<=g_M; i++)
        delete [] PixelsArray[i];
    
    delete [] PixelsArray;
}

void ClearImage()
{
    for(int i=1; i<=g_M; i++)
        for(int j=1; j<=g_N; j++)
            PixelsArray[i][j] = 'O';
}

void PaintPixel(int X, int Y, char c)
{
    PixelsArray[X][Y] = c;
}

void VerticalLine(int X, int Y1, int Y2, char c)
{
    for(int i = Y1; i <= Y2; i++)
        PixelsArray[X][i] = c;
}

void PrintImage()
{
    int i, j;
    
    for(i=1; i<=g_N; i++)
    {
        for(j=1; j<=g_M; j++)
            cout << PixelsArray[j][i] << " ";
        cout << endl;
    }
}

void HorizontalLine(int X1, int X2, int Y, char c)
{
    for(int i=X1; i<=X2; i++)
        PixelsArray[i][Y] = c;
}

void DrawRectangle(int X1, int X2, int Y1, int Y2, char c)
{
    int i, j;
    
    for(i = X1; i <= X2; i++)
        for(j = Y1; j <= Y2; j++)
            PixelsArray[i][j] = c;
}

void Rec_Fill(int X, int Y, char from, char to)
{
    PixelsArray[X][Y] = to;
    
    if(X-1 > 0 && PixelsArray[X-1][Y] == from)    
        Rec_Fill(X-1, Y, from, to);        // Checking left pixel
    
    if(Y-1 > 0 && PixelsArray[X][Y-1] == from)
        Rec_Fill(X, Y-1, from, to);        // Checking upper pixel
    
    if(X+1 <= g_M && PixelsArray[X+1][Y] == from)
        Rec_Fill(X+1, Y, from, to);        // Checking right pixel

    if(Y+1 <= g_N && PixelsArray[X][Y+1] == from)
        Rec_Fill(X, Y+1, from, to);        // Checking lower pixel
}

void FillArea(int X, int Y, char c)
{
    char temp = PixelsArray[X][Y];
    
    Rec_Fill(X, Y, temp, c);
}

int main()
{    
    string input;
    char cmd;
    
    int var1, var2, var3, var4;
    char color;
    
    for(;;)
    {
        getline(cin, input);
        cmd = input[0];
        
        if(!CheckCmd(cmd))
            continue;
        
        if(cmd == 'X')
        {
            DeleteImage();
            return 0;
        }
        
        input.erase(input.begin(), input.begin()+2);
        
        switch(cmd)
        {
            case 'I':
            {
                stringstream(input) >> var1 >> var2;
                CreateImage(var1, var2);
                break;
            }

            case 'C':
            {
                ClearImage();
                break;
            }
            
            case 'L':
            {
                stringstream(input) >> var1 >> var2 >> color;
                PaintPixel(var1, var2, color);
                break;
            }
            
            case 'S':
            {
                cout << input << endl;
                PrintImage();
                break;
            }
            
            case 'V':
            {
                stringstream(input) >> var1 >> var2 >> var3 >> color;
                VerticalLine(var1, var2, var3, color);
                break;
            }
            
            case 'H':
            {
                stringstream(input) >> var1 >> var2 >> var3 >> color;
                HorizontalLine(var1, var2, var3, color);
                break;
            }
            
            case 'K':
            {
                stringstream(input) >> var1 >> var2 >> var3 >> var4 >> color;
                DrawRectangle(var1, var2, var3, var3, color);
                break;
            }
            
            case 'F':
            {
                stringstream(input) >> var1 >> var2 >> color;
                FillArea(var1, var2, color);
                break;
            }
            
        }

    }

    return 0;
}
```

---

### Post by dwhitney67 on 2010-03-07
> **OVERPOWER8 said:**
> 
learn to read bash code first!


I spend 5 days a week reading/porting C++ code... and I get paid to do it.

Your code, based on the experience I have gathered during the last 22 years, is not written using the best programming practices (ie. stuff that you rarely learn from a book or even this forum).  I'm sorry you can't accept what I stated earlier, but just because something "works", it doesn't mean that it was done well.


P.S.  What does reading bash scripts have to do with C++?  Perhaps that is your problem... you are confusing the two.

---

### Post by OVERPOWER8 on 2010-03-07
>> **[dwhitney67]("http://ubuntuforums.org/member.php?u=322753")**

Alright, alright.

Now that you do know what does my program do, could you write something from my code that isn't good?

And how should it look like?

BTW I don't believe that you program in C++ more that 20 years, cos you couldn't find this simple mistake:

input.erase(input.begin(), input.begin()+2);    when input is only 1 char long (contains 'X').

Bash Code:

./program
I 5 6
X                  <- Only 1 symbol is entered!
terminate called after throwing an instance of 'std::length_error'
  what():  basic_string::_S_create
Aborted

---

### Post by Queue29 on 2010-03-07
> Queue29 and dwhitney67 :
learn to read bash code first!

It's clearly you who doesn't know what you're talking about. This has absolutely nothing to do with bash, other than bash may or may not be the shell being used. Though I am not as experienced as dwhitney67, this is easily some of the worst code I have ever seen. 

The reason I didn't immediately tell you what was wrong (notice I emphasized the problematic line in my first post) is because even making it "right" wouldn't help the fact that this is just terrible programming practice.

---

### Post by OVERPOWER8 on 2010-03-07
>> **[Queue29]("http://ubuntuforums.org/member.php?u=342869")**

You think so coz you don't know the exercise!
If you would know, you would tell that it's the best solution.

P. S. this is not my program, this is just a programming exercise from a book.

Anyway, where do you see "terrible programming practice"?

---

### Post by MadCow108 on 2010-03-07
it is a terrible piece of code. It's far from something I would consider a best solution (code-wise)
it may work but it is a huge mess. Hard to read, hard to maintain, bugprone, not making use of C++'s features etc.

a minor addition to already mentioned problems:
don't use <= in loops using primitives as counting variables. The compiler can't optimize these possible infinite loops at all (except you explicitly tell it too which may introduce subtle bugs).

---

### Post by LKjell on 2010-03-07
I am not going to bash you further on. But have you consider what happen if you delete before you create an image?

---

### Post by dwhitney67 on 2010-03-07
> **OVERPOWER8 said:**
> 
input.erase(input.begin(), input.begin()+2);


The erase() command above is one that I personally am not familiar with, but if needed, I would know where to find the documentation on it.

I would have approached the solution to your application slightly differently; for example, for getting the command:
```

using namespace std;

char getCommand()
{
   string cmd;

   while (true)
   {
      cout << "\nEnter command: ";
      cin  >> cmd;

      if (cin.good() && cmd.length() == 1) break;

      cin.clear();
      cin.ignore(1024, '\n');
      cout << "Invalid input; try again." << endl;
   };

   return cmd[0];
}

```

Another, more practical way of getting user input is to use a generic method that can read any type of data type.  For example:
```

#include <string>
#include <iostream>

using namespace std;

template <typename T>
T getInput(const char* prompt)
{
   using namespace std;

   T input;

   while (true) {
      // prompt user and attempt to read input
      cout << prompt;
      cin  >> input;

      // check if valid input given; break from loop if so.
      if (cin.peek() == '\n' && cin.good()) break;

      // user gave bad input; let them know about it.
      cout << "Invalid input!  Try again...\n" << endl;
      cin.clear();
      do { cin.ignore(1024, '\n'); } while (!cin);
   }

   return input;
}

char** createImage(const size_t dim1, const size_t dim2)
{
   char** image = new char*[dim1];

   for (size_t i = 0; i < dim1; ++i)
   {
      image[i] = new char[dim2];
   }

   return image;
}

void destroyImage(char** image, const size_t dim1)
{
   if (image == 0 || dim1 == 0) return;

   for (size_t i = 0; i < dim1; ++i)
   {
      delete [] image[i];
   }
   delete [] image;
}

int main(void)
{
   size_t      dim1 = 0;
   size_t      dim2 = 0;
   char**      pixelImage = 0;
   bool        done = false;

   while (!done)
   {
      std::string cmd = getInput<std::string>("Enter command: ");

      switch (cmd[0])
      {
         case 'q':
             done = true;
             break;

         case 'I':
             dim1 = getInput<size_t>("Enter first dimension: ");
             dim2 = getInput<size_t>("Enter second dimension: ");

             pixelImage = createImage(dim1, dim2);
             break;

         case 'D':
             destroyImage(pixelImage, dim1);
             break;

         default:
             cerr << "Error: Unreconized command option." << endl;
      }
   }
}

```

Anyhow, notice in the examples above... not a single global variable.  Also, note that it would have been better if a pixel image would be defined as an object, thus collectively keeping all of it's attributes together as one, and thus negating the need to pass multiple arguments to functions.  All one would need to do is pass the PixelData object:
```

struct PixelData
{
   size_t rows;
   size_t cols;

   char** data;
};

```

---

### Post by OVERPOWER8 on 2010-03-07
Thanks, [B][dwhitney67]("http://ubuntuforums.org/member.php?u=322753")

[/B]I have been learning C++ for less than 1 year.
Of course, after 22 years I will code much better...

The command *erase* is applied to string objects:
[http://cplusplus.com/reference/string/string/erase/](http://cplusplus.com/reference/string/string/erase/)

---

### Post by LKjell on 2010-03-07
> **OVERPOWER8 said:**
> Thanks, [B][dwhitney67]("http://ubuntuforums.org/member.php?u=322753")

[/B]I have been learning C++ for less than 1 year.
Of course, after 22 years I will code much better...

The command *erase* is applied to string objects:
[http://cplusplus.com/reference/string/string/erase/](http://cplusplus.com/reference/string/string/erase/)

I feel that coding is like an art. I seen programmers that has long experience but they write in a cryptic way it is too hard to follow. And there are those who write too descriptive so the whole code gets too bloated to read. So when to write codes I have this mentality to write it less clear so that another person can read and understand. 

If you can write codes without comments and be able to read what you wrote for 6 months old without problems then maybe it is good codes. Since in this world codes that other people cannot understand is useless for a job related issue.

---


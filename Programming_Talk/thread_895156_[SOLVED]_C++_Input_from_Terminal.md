---
title: "[SOLVED] C++ Input from Terminal?"
date: 2008-08-19
forum: Programming Talk
---

### Post by Caged on 2008-08-19
Hi. I am wondering if it is possible to get an output from terminal stored in a variable in a C++ program?

string myVar;
myVar = system("df -l -k /tmp | tail -1 | cut -c44-50");

That doesn't work of course, but I think it kinda shows my intention.

---

### Post by PaulFr on 2008-08-20
Could you redirect the output of the command into a file, and then read the file ?

---

### Post by jinksys on 2008-08-20
What you are looking for is POPEN (process open) 

[http://linux.die.net/man/3/popen](http://linux.die.net/man/3/popen)

---

### Post by Caged on 2008-08-20
Thanks for the replies. I want to avoid creating a file if I can for now. I am very new to programming in general though so I am quite lost at the face of the man page you linked. I'll see about trying it when I can access my machine tomrrow.

---

### Post by dwhitney67 on 2008-08-20
> **Caged said:**
> Hi. I am wondering if it is possible to get an output from terminal stored in a variable in a C++ program?

string myVar;
myVar = system("df -l -k /tmp | tail -1 | cut -c44-50");

That doesn't work of course, but I think it kinda shows my intention.
Look at this link for some code that I wrote:  [http://ubuntuforums.org/showpost.php?p=5507024&postcount=12](http://ubuntuforums.org/showpost.php?p=5507024&postcount=12)

If you save the code to a file called execcmd.cpp, you can then build and test the program such as:
```
$ g++ execcmd.cpp -o execcmd
$ execcmd df -l -k /tmp | tail -1 | cut -c44-50
```
or using whatever command you want.

P.S.  Note that this program only supports one-way communications with system commands/utilities.  Thus this program will not work with an interactive terminal applications, such as 'vi' or 'bc'.

---

### Post by Caged on 2008-08-21
That is all awfully complicated for me... There were several commands I had never seen before so I couldn't predict in my mind what each line was doing. I guess I was hoping for a simple command that would let me use the output. The most important thing I need done is to get the output stored as a string variable in C++.

---

### Post by jinksys on 2008-08-21
> **Caged said:**
> That is all awfully complicated for me... There were several commands I had never seen before so I couldn't predict in my mind what each line was doing. I guess I was hoping for a simple command that would let me use the output. The most important thing I need done is to get the output stored as a string variable in C++.

Did you even look at popen?

---

### Post by Caged on 2008-08-21
I was responding to dwhitney67 but I am guilty of not having tried popen yet. I admit I  am perhaps not as enthusiastic as I should be about experimentation but I will get around to it soon.

---

### Post by Caged on 2008-08-21
Okay I've made some progress. The following code appears to do what I want:

```

#include <iostream>
#include <cstdio>
#include <string>

using namespace std;

int main()
   {
   FILE *fp = popen("df -l -k /tmp | tail -1 | cut -c44-50", "r");

   string word;
   if(fp != NULL)
      {
      for(int i = 0; i < 7; i++)
         {
         word += fgetc(fp);
         }
      cout << word << "\n";
      }

   pclose(fp);


   return 0;
   }

```

I can probably trim it down with a few more experiments but alas the time I have each day to program is short. Particularly, I would like to know what is read at the end of *fp because I used a while(fp != EOF) and while(fp != NULL) before and it went into a freeze. Like an infinite loop I think. Thank you for your patience. I will try to be a better student.

---

### Post by jinksys on 2008-08-21
> **Caged said:**
> 
I can probably trim it down with a few more experiments but alas the time I have each day to program is short. Particularly, I would like to know what is read at the end of *fp because I used a while(fp != EOF) and while(fp != NULL) before and it went into a freeze. Like an infinite loop I think. Thank you for your patience. I will try to be a better student.

Here is some working code:

```



#include <iostream>
#include <cstdio>
#include <string>

using namespace std;

int main()
   {
char c;
string word;
FILE *fp = popen("df -l -k /tmp | tail -1 | cut -c44-50", "r");
   
while(c != EOF)
      {
        c = fgetc(fp);
        if(c!=EOF){word += c;}
      }

   cout << word << endl;
   pclose(fp);

   return 0;
   }

```

You had an infinite loop before because fp is the pointer to your file stream.  You need to check fgetc's return value for an EOF, not fp.  When in doubt, read the man page [here](http://linux.die.net/man/3/fgetc).  

I hope you understand the above code, it simply:

1) uses popen to open a stream to the output of your command.

2) uses fgetc to run through the stream and append the returned characters to "word".  When the returned character is EOF, the loop terminates.

3) "word" is outputted, our stream is closed and return gracefully.

If you are a beginner I must say that for a first attempt, it was pretty good.

---

### Post by dwhitney67 on 2008-08-21
> **Caged said:**
> I was responding to dwhitney67 but I am guilty of not having tried popen yet. I admit I  am perhaps not as enthusiastic as I should be about experimentation but I will get around to it soon.
The example that I referred you to look at uses popen().  It also collects each line of output (from the command) into an STL vector that you can use as you wish.

I commend you on your attempt to solve this problem on your own.  But since you are programming in C++, you should start thinking in terms of objects, and in developing code that can be reused again and again.

---

### Post by Caged on 2008-08-21
This exercise is going to be a method of an object actually.

Before I can call this solved though, it seems there is an enter character right before EOF, which will screw up the output somewhat (I want a single line output). Does anyone know what it is stored as in char? Apparently it is not "\n" or endl...

---

### Post by jinksys on 2008-08-21
> **Caged said:**
> 
Before I can call this solved though, it seems there is an enter character right before EOF, which will screw up the output somewhat (I want a single line output). Does anyone know what it is stored as in char? Apparently it is not "\n" or endl...

The "enter" character, actually a newline, is due to the endl in my code, and the "\n" in yours.  The "word" variable doesn't contain this character.

Also, if you are going to go the C++ route, take a serious look at dwhitney67's code.  Neither one of our codes are more right than the other, mine is essentially C (minus the cout business) and his actual C++.

---

### Post by Caged on 2008-08-21
I am pretty positive there is an 'endline' right before EOF. I tested it by incrementing the upper limit of i. For my case, at i = 7, the numbers were printed on screen and immediately followed by the user command line. At i = 8, the numbers were printed on screen and the command line was one line under it.

---

### Post by jinksys on 2008-08-21
> **Caged said:**
> I am pretty positive there is an 'endline' right before EOF. I tested it by incrementing the upper limit of i. For my case, at i = 7, the numbers were printed on screen and immediately followed by the user command line. At i = 8, the numbers were printed on screen and the command line was one line under it. 

Why are you hardcoding the length of output?  That is a very bad practice.  You cannot assume that the output will be X characters long.  That is why I completely rewrote your code, it was wrong.  The filestream will issue an EOF character when there is no more data to read.

---

### Post by dwhitney67 on 2008-08-21
> **Caged said:**
> I am pretty positive there is an 'endline' right before EOF. I tested it by incrementing the upper limit of i. For my case, at i = 7, the numbers were printed on screen and immediately followed by the user command line. At i = 8, the numbers were printed on screen and the command line was one line under it.
I'm sorry, I fail to understand your question/problem described above.

When examining argc/argv, always keep in mind that the first argument (index 0) is the program's name. This program will dump the cmd-line args (if any) and the program name (which is ALWAYS there at index 0)...
[PHP]int main( int argc, char **argv )
{
  // For argv[ 1...argc ] should be the remaining cmd-line args.
  //
  for ( int i = 1; i < argc; ++i )
  {
    std::cout << "arg " << i << " = " << argv[i] << std::endl;
  }

  std::cout << "'" << argv[0] << "' is done!" << std::endl;
}[/PHP]

---

### Post by dwhitney67 on 2008-08-21
> **Caged said:**
> I am pretty positive there is an 'endline' right before EOF. I tested it by incrementing the upper limit of i. For my case, at i = 7, the numbers were printed on screen and immediately followed by the user command line. At i = 8, the numbers were printed on screen and the command line was one line under it.
And you are right... there is an 'endline' (newline)... because the output from a command (such as 'ls') will contain such.  If you do not want such, then replace it with a null-character.

---

### Post by jinksys on 2008-08-21
> **dwhitney67 said:**
> I'm sorry, I fail to understand your question/problem described above.


From what I gather, he wants to run this command in his program:

df -l -k /tmp | tail -1 | cut -c44-50

and save the output as a variable, which happens to be a 7 or 8 digit number usually.

---

### Post by dwhitney67 on 2008-08-21
> **jinksys said:**
> From what I gather, he wants to run this command in his program:

df -l -k /tmp | tail -1 | cut -c44-50

and save the output as a variable, which happens to be a 7 or 8 digit number usually.
Yes perhaps, but in the desire to write reusable code, what would be the result if the program had issued an "ls" command.

The code I threw together in the post I referred to earlier is "cheesy".  It is definitely only C++ compatible, and unfortunately it only handles one-way interaction with the shell.  For $ I would provide something more elaborate.

The example I provided captures the output from a shell command, and stores each line of output into an STL string.  Each string is then stored into an STL vector (a glorified array).

An application could use the object (ExecCmd, or whatever I called it) to obtain this vector.  It is possible that each string contains a newline (a '\n'), but big deal... just modify the code I provided so that it changes/converts that character to a null-character ('\0').

*** Damn I hate typing!  Quotes and parens... arg!!!! ***

The bottom line is that when you issue a shell command, it may issue multiple lines of results, each of which is newline-terminated.  If you don't believe me, then run "ls -l" in your favorite terminal.

P.S.  Jinksys - thank you for your support concerning my (cheesy) C++ solution.

---

### Post by jinksys on 2008-08-21
> **dwhitney67 said:**
> Yes perhaps, but in the desire to write reusable code, what would be the result if the program had issued an "ls" command.

. . .For $ I would provide something more elaborate. . . .

P.S.  Jinksys - thank you for your support concerning my (cheesy) C++ solution.

My code is reusable, as long as the command is non-interactive.  His code, however, reads a set amount of characters then bails out.  

For $ yes, I would fly your computer to the moon and back, but this is pro bono :)

---

### Post by Caged on 2008-08-21
I guess I have enough difficulty just handling this one case to think about reusing stuff. Perhaps I should have mentioned this earlier but I'm putting the code so far into a function and the main() will be taking arguments for other purposes. As far as I can tell, dwhitney67's code won't be able to be used like this. Unless I misunderstood, which is so often the case.

Regarding jinksys' code: I think it is more elegant than mine but I really need to get rid of the 'newline' before EOF. Strange how that happened because if there was a 'newline' at the end of a command like, say, 'ls'(as there should be), then it would have been cut away when I piped it into cut -44-50. Yet there it is.

---

### Post by jinksys on 2008-08-22
> **Caged said:**
> I guess I have enough difficulty just handling this one case to think about reusing stuff. Perhaps I should have mentioned this earlier but I'm putting the code so far into a function and the main() will be taking arguments for other purposes. As far as I can tell, dwhitney67's code won't be able to be used like this. Unless I misunderstood, which is so often the case.

Regarding jinksys' code: I think it is more elegant than mine but I really need to get rid of the 'newline' before EOF. Strange how that happened because if there was a 'newline' at the end of a command like, say, 'ls'(as there should be), then it would have been cut away when I piped it into cut -44-50. Yet there it is.

If you remove this line:

cout << word << endl;

and replace it with:

cout << word;

do you still get the newline?

---

### Post by Caged on 2008-08-22
Yes, the newline is still there. I noticed because the output looked like this:

commandLineOfCaged>./testing
1234567

commandLineOfCaged>




Removing the << endl gave me this:

commandLineOfCaged>./testing
1234567
commandLineOfCaged>

---

### Post by dwhitney67 on 2008-08-22
> **Caged said:**
> Yes, the newline is still there. I noticed because the output looked like this:

commandLineOfCaged>./testing
1234567

commandLineOfCaged>




Removing the << endl gave me this:

commandLineOfCaged>./testing
1234567
commandLineOfCaged>
And the problem is??  The newline is going to be there, similarly to when you issue the command from the command-line of your terminal.

If you still happen to be using the code I provided earlier, insert the following lines to remove the newline:
[PHP]...
      while ( !feof(pfd) )
      {
        char buf[ 1024 ] = {0};

        if ( fgets(buf, sizeof(buf), pfd) > 0 )
        {
          std::string str(buf);    // <---  this and the mod below
          m_results.push_back( str.substr(0, str.length()-1) );
        }
      }
...[/PHP]
If you are writing your code in C-style (and this would work in my code too!), then you can try something like:
[PHP]buf[ strlen(buf)-1 ] = '\0';   // replaces newline w/ null-character[/PHP]

---

### Post by jinksys on 2008-08-22
I just noticed something.  Watch what happens when I run that command on my machine with and without the cut command...

```

steve@jnote:~$ df -l -k /tmp | tail -1
/dev/sda1            113672068   3327284 104616008   4% /
steve@jnote:~$ df -l -k /tmp | tail -1 | cut -c44-50
4616004

```

You get 4616004 and not 104616004.  If you are trying to extract out 104616004 its better to use SED and not CUT.

But regarding the newline, it does look like one of the commands is printing the newline character.  That's easy to fix, do as dwhitney recommends and remove it from the string after the command is run.

---

### Post by Caged on 2008-08-22
I am told this number is the Free Disk Space on the computer so for my case, it is usually around 2GB. Or 200000 kB.

I can't seem to get SED to work. Is it alright if you show me an example?

@dwhitney67: I feel kind of guilty because you are trying to help but I haven't used your code...

---

### Post by dwhitney67 on 2008-08-22
> **Caged said:**
> I am told this number is the Free Disk Space on the computer so for my case, it is usually around 2GB. Or 200000 kB.

I can't seem to get SED to work. Is it alright if you show me an example?

@dwhitney67: I feel kind of guilty because you are trying to help but I haven't used your code...
No worries; even if you used my code, the output you desire might still be incorrect due to the findings discovered by **jinksys**.

P.S.  Maybe this will work for you:
```
df -l -k /tmp | tail -1 | cut -d ' ' -f20
```

---

### Post by Caged on 2008-08-22
> **dwhitney67 said:**
> P.S.  Maybe this will work for you:
```
df -l -k /tmp | tail -1 | cut -d ' ' -f20
```

It returns a 0 for me. Unfortunately that's not the desired output. But I want to thank you anyway for trying to help!

---

### Post by dwhitney67 on 2008-08-22
Well, try using the two files below.  Build them using:
```
$ g++ Main.cpp -o runcmd
```
Then run the application such as:
```
$ runcmd "df -l -k /tmp | tail -1"
```

Main.cpp:
[PHP]
#include "ExecCommand.hpp"
#include <string>
#include <sstream>
#include <iostream>


int main( int argc, char **argv )
{
  try
  {
    std::string cmd;

    for ( int i = 1; i < argc; ++i )
    {
      cmd += argv[i];
      cmd += " ";
    }

    ExecCommand exec( cmd );

    const ExecCommand::CmdResults results = exec.getResults();

    // Get fields from result per requirements from Caged...
    //
    std::istringstream iss( results[0] );

    std::string field1;
    size_t      field2 = 0;
    size_t      field3 = 0;
    size_t      field4 = 0;
    size_t      field5 = 0;
    char        field6;
    std::string field7;

    iss >> field1 >> field2 >> field3 >> field4 >> field5 >> field6 >> field7;

    std::cout << "Result(s):" << std::endl;
    //std::cout << "field1 = " << field1 << std::endl;
    //std::cout << "field2 = " << field2 << std::endl;
    //std::cout << "field3 = " << field3 << std::endl;
    std::cout << "field4 = " << field4 << std::endl;
    //std::cout << "field5 = " << field5 << std::endl;
    //std::cout << "field6 = " << field6 << std::endl;
    //std::cout << "field7 = " << field7 << std::endl;
  }
  catch ( std::exception &ex )
  {
    std::cerr << "Error: " << ex.what() << std::endl;
  }

  return 0;
}
[/PHP]

ExecCommand.hpp:
[PHP]
#include <string>
#include <vector>
#include <algorithm>
#include <stdexcept>
#include <iostream>


class ExecCommand
{
  public:
    typedef std::vector<std::string> CmdResults;

    ExecCommand( const std::string &cmd )
    {
      FILE *pfd = popen( cmd.c_str(), "r" );

      if ( pfd == 0 )
      {
        throw std::runtime_error( "Command or process could not be executed." );
      }

      while ( !feof(pfd) )
      {
        char buf[ 1024 ] = {0};

        if ( fgets(buf, sizeof(buf), pfd) > 0 )
        {
          std::string str(buf);
          m_results.push_back( str.substr(0, str.length()-1) );
        }
      }
      pclose( pfd );
    }

    const CmdResults getResults() const
    {
      return m_results;
    }

    friend std::ostream & operator<<( std::ostream &os, const ExecCommand &exec )
    {
      std::for_each( exec.m_results.begin(), exec.m_results.end(), ExecCommand::Displayer(os) );
      return os;
    }

  private:
    class Displayer
    {
      public:
        Displayer( std::ostream &os ) : m_os(os) {}

        void operator()( const std::string &str )
        {
          m_os << str << std::endl;
        }

      private:
        std::ostream &m_os;
    };

    CmdResults m_results;
};
[/PHP]

---

### Post by jinksys on 2008-08-23
Ok, so the command you need is...

```

df -l -k /tmp | tail -1 | awk '{print $4}'

```

That should pull out the available disk space.

---

### Post by Caged on 2008-08-23
That's even better than the cut because if I suddenly free up lots of memory, I won't have them cut off important digits. But the pesky newline is still there. It wouldn't be such a big deal if it didn't ruin the layout of some other code that prints the information to screen. (that other code assembles stuff gotten from here and other places and assembles them into a single sentence, which will be destroyed by the new line in the middle)

---

### Post by slavik on 2008-08-23
> **jinksys said:**
> 
...
int main()
   {
char c;
string word;
FILE *fp = popen("df -l -k /tmp | tail -1 | cut -c44-50", "r");
   
while(c != EOF)
...


there is a problem with this. c is never initialized to something which !=EOF ... it is possible for c to be EOF and thus you skip the loop that you need.

---

### Post by Caged on 2008-08-23
I present you the ugly solution I have which will guarantee(I think) the output I had in mind:

```
// This loop exists solely to get rid of the newline at the end of word.
for(int i = 0; i < (word.size() - 1); i++)
   {
   wordFinal += word[i];
   }

```

Feel free to lambast its ugliness.

@slavik: I don't understand. If it never initialises as EOF, then the loop will never be missed.

---

### Post by jinksys on 2008-08-23
> **Caged said:**
> 
@slavik: I don't understand. If it never initialises as EOF, then the loop will never be missed.

He's saying that since c is not initialized to a value, it is possible that c is initialized to EOF (small chance, but possible) and the loop will be skipped.

Change the line to something like

char c = 'x';

Good catch, slavik.

Also, the newline loop is unnecessary.  You can just use this...

word[word.size() -1]='\0';

---

### Post by Caged on 2008-08-23
Ok, I've followed the suggestions. I've initialised c and got rid of the loop in favour of simply replacing that one character in the string. I think I can call this little problem solved. Thanks!

---

### Post by dwhitney67 on 2008-08-23
Jeez Christ... thank god/jupiter/buddha.

---

### Post by Caged on 2008-08-24
You know what they say. No rest till perfection. In this case, a silly 'newline' just had to be gotten rid of.

---


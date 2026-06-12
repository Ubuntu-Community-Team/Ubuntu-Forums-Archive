---
title: "c++ cgi convert argv[x] to query_string ???"
date: 2011-04-20
forum: Programming Talk
---

### Post by highspider on 2011-04-20
any who...
  I wrote program to make a picture gallery. I'm pretty good with c++ but I have never wrote a cgi.  I can't really phrase my question in Terms of what im attempting other then [COLOR=Red]how do I convert command line args to cgi env variables[/COLOR] .  I don understand cgi and the help files via google need a base 64 coverter to phrase the correct question with out getting "static_cast<good>(crap)," 

I tested it using ye~old "myprog PICFILE > my.html"

```
#include <iostream>
    using std::cout;
    using std::cin;
     using std::endl;

#include <fstream>          //for files
    using std::ifstream;      //open read only mode

#include <cstring>
       using std::strlen;
       using std::strcpy;

#include <string>
      using std::string;

//main uses commandline arguments!
int main(int argc, char* argv[]) {

 //check for args and avoid use of ../ for looking back in dirs
 if ( argc == 2 ){

         //parinoid at string file name being /var/www/cgi-bin/../../../etc/passwd
         //Mite not be possible but lets check and panic error R1
         if (static_cast<string>(argv[1]).find ("..") != string::npos) {
           cout << "<h1>ERROR #1</h1>" << endl
                << "<h3>This program was not called correctly</h3>" << endl
                << "<p>Error Opening the file " <<  argv[1] << " </p>" << endl;
         return 1;
         }
   [COLOR=RoyalBlue]--my giant program--[/COLOR]            
   return 0;
  }//end if commandline arg's
  else{
    cout << "<h1>ERROR #3</h1>" << endl 
         << "<h3>This program was not called correctly</h3>" << endl;
    return 3;
  }//end else commandline arg's
}
```


NOTE: question2 if any "wtf" is the Linux equivalent to mem leaks for MS-VS
Y: the full program I wrote uses dynamic allocation of memory

#define _CRTDBG_MAP_ALLOC 
#include <crtdbg.h> 
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );

---

### Post by Bakerconspiracy on 2011-04-20
Just real quick q,

why didn't you just use the std namespace?

---

### Post by Bakerconspiracy on 2011-04-20
Hey, it is really important about what you mean by command line arguments to be converted to CGI vars.

Do you mean you just want to convert the text into output-able text in html ? (thus the base 64 encoder)
Or, do the arguments point to something else that needs to be converted into something you can use?

---

### Post by highspider on 2011-04-20
> **Bakerconspiracy said:**
> Just real quick q,

why didn't you just use the std namespace?

I mean instead of /home/unloved/myprogram thetextfile.txt
using /var/www/cgi-bin/myprogram?/gallery/thetextfile.txt

[COLOR=Green]Base 64 decoder was a joke[/COLOR]
[COLOR=Blue]the base 64 part was just a joke for I cant understand the lame stuff on google (related to my search) with out a translation.[/COLOR]

And Y I use std::whatever is just the way I was thought in college
OIT ([Oregon Institute of Technology]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CCAQFjAA&url=http%3A%2F%2Fwww.oit.edu%2F&ei=RGuuTZ_KBavPiALB4LXPDA&usg=AFQjCNFdMZfwhNx5O9wCYkj4DsySMBiecQ&sig2=JstfFfhgSG7Zw_vBDic18A")) 
  my professors student book they authored  "C++ An Active Learning Approach"
       by Professor Randal Albert OIT
        &  Todd Breedlove OIT

---

### Post by highspider on 2011-04-20
> **Bakerconspiracy said:**
> Hey, it is really important about what you mean by command line arguments to be converted to CGI vars.

Do you mean you just want to convert the text into output-able text in html ? (thus the base 64 encoder)
Or, do the arguments point to something else that needs to be converted into something you can use?


if you download the .cpp.txt and rename it to .ccp then complie and run I'm trying to make it work as a .cgi with "env variables" instead of command line arguments

and the name in the file is 
* Filename:                chp12_PX_4.cpp
because I overwrote an old home work assingment for chapter 12 program exrisce 4 "dynamic allocate memory" as the base for this program

---

### Post by myrtle1908 on 2011-04-20
Are you simply trying to receive arguments to your program via the common gateway interface ... so that you can run your program on a webserver?

If so, use a library.

How about this one [http://cgi.sourceforge.net/docs/fastcgi___cgi/tutorial/cgi.html](http://cgi.sourceforge.net/docs/fastcgi___cgi/tutorial/cgi.html)

---

### Post by highspider on 2011-04-20
> **myrtle1908 said:**
> Are you simply trying to receive arguments to your program via the common gateway interface ... so that you can run your program on a webserver?

If so, use a library.

How about this one [http://cgi.sourceforge.net/docs/fastcgi___cgi/tutorial/cgi.html](http://cgi.sourceforge.net/docs/fastcgi___cgi/tutorial/cgi.html)

Thank's it got me point in the right direction.

here is what I was Looking to do
(working source code)
 ```

/****************************************
 *TITLE: Hello world on crack
 *Author: Highspider
 *Filename: hello.cpp 
*Location: /cgi-bin/hello.cgi
*Purposs: Down and dirty cgi getenv() test program
 *****************************************/
 #include <iostream>
 #include <string>
 #include <cstdlib>
 
 int main()
 {
 std::string parma = std::getenv("QUERY_STRING");
 
 std::cout << "Content-Type: text/html\n\n"
           << "<html>\n"
           << " <head>\n"
           << " <p> Hello world!<br /> You passed </p>"
           << "<p>" << parma << "<br /></br> to this program</p>"
           << " </body>\n"
           << "</html>\n" << std::endl;

return 0;
 }
 
```

---

### Post by dwhitney67 on 2011-04-20
Using getenv(), as you have it below, is not very wise.
```

std::string parma = std::getenv("QUERY_STRING");

```
Consider what will happen if QUERY_STRING is not defined!

Try something like this instead:
```

const char* query_str = std::getenv("QUERY_STRING");

if (query_str != NULL)
{
   // output message
}
else
{
   // error
}

```

---

### Post by highspider on 2011-04-20
> **dwhitney67 said:**
> Using getenv(), as you have it below, is not very wise.
```

std::string parma = std::getenv("QUERY_STRING");

```Consider what will happen if QUERY_STRING is not defined!

Try something like this instead:
```

const char* query_str = std::getenv("QUERY_STRING");

if (query_str != NULL)
{
   // output message
}
else
{
   // error
}

```


I thought it was just return 'null'
moving '\0' to the  beginning of string param

string param with querystring of "sometext"
real contents [sometext\0]
string param with querystring empty
real contents [\0]

im I wrong I haven't debugged it.  I don't have code::blocks installed on this pc.

I ran it as cgi and both worked fine

---

### Post by dwhitney67 on 2011-04-20
> **highspider said:**
> I thought it was just return 'null'


Indeed it does; test this program...
```

#include <cstdlib>
#include <string>

int main()
{
   std::string env = std::getenv("FOO");
}

```
If the environment variable FOO is not defined, this program will crash.

---

### Post by highspider on 2011-04-20
> **dwhitney67 said:**
> Indeed it does; test this program...
```

#include <cstdlib>
#include <string>

int main()
{
   std::string env = std::getenv("FOO");
}

```If the environment variable FOO is not defined, this program will crash.
O Joy a new 500 for server logs... LOL
 
 OK could u help me better understand what FOO and QUERY_STRING
  I know i get them from <cstdlib> and iknow 
[http://www.cplusplus.com/reference/clibrary/cstdlib/](http://www.cplusplus.com/reference/clibrary/cstdlib/)
 but I don't exactly where the come from or what they are other than environmental variables?
where is the environment list of possible vars

YOUR RIGHT! I shall make changes

---

### Post by dwhitney67 on 2011-04-20
> **highspider said:**
> I don't exactly where the come from...

From a terminal (e.g. gnome-terminal), run the following command:
```

env

```
If you want the value associated with a specific environment variable, say QUERY_STRING, then do this:
```

env | grep QUERY_STRING

```

---

### Post by highspider on 2011-04-20
Thanks a bunch.
[COLOR=Red]edited:: wait I dont have one ?
[/COLOR]env | grep QUERY_STRING
  
I'M calling the file @ /var/www/cgi-bin/hello.cgi on my server
It isn't there on the server


```

/****************************************
*TITLE: Hello world on crack
*EDITED: 1.1v 
*Author: Highspider
*Purposs: Down and dirty cgi getenv() test program
*****************************************/
#include <iostream>
#include <string>
#include <cstdlib>

const char* parma = std::getenv("QUERY_STRING");

int main()
{
std::cout << "Content-Type: text/html\n\n"
          << "<html>\n"
          << " <head>\n";

if (*parma != '\0')  {
  std::cout << " <p> Hello world!<br /> You passed </p>"
            << "<p>" << parma << "<br /></br> to this program</p>"
            << " </body>\n</html>\n" << std::endl;
   return 0;
}else{
  std::cout << " <p> ERROR #1<br />Called with No Parameter!</p>"
            << " </body>\n</html>\n" << std::endl;
   return 1;
}
}//end main

```

---

### Post by dwhitney67 on 2011-04-20
> **highspider said:**
> 
[COLOR=Red]edited:: wait I dont have one ?


It (QUERY_STRING) is probably defined, but it is a string with a null-character in it.  This is different from a null-pointer.

Try the following program to deduce all of the environment variables available to CGI "scripts" for your particular system:
```

#include <sstream>
#include <iostream>
#include <cstdlib>


const char* env_vars[] = { "DOCUMENT_ROOT",
                           "HTTP_COOKIE",
                           "HTTP_HOST",
                           "HTTP_REFERER",
                           "HTTP_USER_AGENT",
                           "HTTPS",
                           "PATH",
                           "QUERY_STRING",
                           "REMOTE_ADDR",
                           "REMOTE_HOST",
                           "REMOTE_PORT",
                           "REMOTE_USER",
                           "REQUEST_METHOD",
                           "REQUEST_URI",
                           "SCRIPT_FILENAME",
                           "SCRIPT_NAME",
                           "SERVER_ADMIN",
                           "SERVER_NAME",
                           "SERVER_PORT",
                           "SERVER_SOFTWARE"
                         };


int main(void)
{
   std::stringstream ss;

   ss << "Content-Type: text/html\n\n"
      << "<html>\n"
      << "<head><title>CGI Script using C++</title></head>\n"
      << "<body>\n";

   for (size_t i = 0; i < sizeof(env_vars) / sizeof(const char*); ++i)
   {
      const char* env_str = std::getenv(env_vars[i]);

      ss << "<p>" << env_vars[i] << ": " << (env_str ? env_str : "Not defined") << "</p>\n";
   }

   ss << "</body>\n"
      << "</html>\n";

   std::cout << ss.str() << std::endl;

   return 0;
}

```

---

### Post by highspider on 2011-04-21
THANK YOU :)
That code helps a bunch. 
> **dwhitney67 said:**
> It (QUERY_STRING) is probably defined, but it is a string with a null-character in it. This is different from a null-pointer.



  Now my program can run!  
```

[COLOR=Black][COLOR=Blue]// EDIT: v1.2
[/COLOR]#include <iostream>
#include <string>
#include <cstdlib>

 const char* param = std::getenv("QUERY_STRING");

int main()
{
std::cout << "Content-Type: text/html\n\n"
          << "<html>\n"
          << " <head>\n";

[COLOR=Blue]//check if param and if param defined w/ Terminator '\0'
//avoids a segment fault when called from a command line yet still functions for
//empty "Query_String" as return 1;
//NOTE: check NULL will not work correctly for both shell and cgi![/COLOR]
[COLOR=Red]if (param && *param != '\0')  {[/COLOR]
  std::cout << " <p> Hello world!<br /> You passed </p>"
            << "<p>" << param << "<br /></br> to this program</p>"
            << " </body>\n</html>\n" << std::endl;
   return 0;
}else{
  std::cout << " <p> ERROR #1<br />Called With No Parameter!</p>"
            << " </body>\n</html>\n" << std::endl;
   return 1;
}
}//end main[/COLOR]

```

---


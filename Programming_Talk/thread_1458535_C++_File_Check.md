---
title: "C++ File Check?"
date: 2010-04-20
forum: Programming Talk
---

### Post by fallenshadow on 2010-04-20
Ok guys I already know how to read and write files with C++. 

However I have no idea how I would check to see if a certain type of file exists at a certain path. I know how to do this with Bash but thats not very useful. :P

Here is a simple algorithm:

```

Check to see if *.whatever exists at $HOME/Desktop/

If(filecheck = TRUE)
{
   DO ACTION
}

Else
{
   DO ACTION
}

```

I need to know this to fix a current problem with one of my applications. The good news is that whoever posts up code that helps me I will list you in the credits of the application. (its being released in the summer.)

---

### Post by heikaman on 2010-04-20
[PHP]  
struct stat st;

if( !stat("/path/to/file", &st) && S_ISREG(st.st_mode))
{
    //do something
}
else
{
    //do something else       
}
[/PHP]

---

### Post by fallenshadow on 2010-04-20
Ok correct me if Im wrong but the code you posted does not look like its checking to see if a certain filetype exists.

It should check if files exist by its type. EG: .bin, .png, .something...

Please note I am not a H4rdc0r3 developer! :)

---

### Post by fallenshadow on 2010-04-20
Ok I am trying to use the code anyway but I think it must be missing something. A header maybe? (declaration)

Can somebody confirm if this code is for searching for a filetype?

Im getting about 7 errors at the moment... all of them to do with this code.
---

Now I have added this header: #include <sys/stat.h> (which I think is correct)

Doing more tests at the moment... down to 3 errors. 

---

No errors now but this code is useless unless I can understand if it can search for a certain filetype.

---

### Post by fallenshadow on 2010-04-20
My main confusion is over this line...

Does this look right or wrong to you:

[PHP]
if( !stat("$HOME/Desktop/*.jar", &st) && S_ISREG(st.st_mode)) 
[/PHP]

Please let me know.

---

### Post by PaulM1985 on 2010-04-20
Hi

This tutorial shows how to open directories for reading.

[http://www.gnu.org/s/libc/manual/html_node/Accessing-Directories.html#Accessing-Directories](http://www.gnu.org/s/libc/manual/html_node/Accessing-Directories.html#Accessing-Directories)

You can read a directory, get a file list as an array of strings and then you can check each string in the array to see if that last characters are the same as the file type(s) that you are looking for.

Paul

---

### Post by heikaman on 2010-04-20
> **fallenshadow said:**
> Ok correct me if Im wrong but the code you posted does not look like its checking to see if a certain filetype exists.


I thought you wanted to check if a certain file exists, my bad :).

In this case follow PaulM1985's advice.

---

### Post by fallenshadow on 2010-04-20
Ok I got the code for reading directories and it works... on its own.

When I put the code into my project I got 3 errors. Not sure how to sort them.

> 
project.cc:132: error: a function-definition is not allowed here before &#8216;{&#8217; token
project.cc:138: error: a function-definition is not allowed here before &#8216;{&#8217; token
project.cc:322: error: expected `}' at end of input


Here is line 131 to 140:
[PHP]
131:	 static int
132:     one (const struct dirent *unused)
133:     {
134:       return 1;
135:     }
136:     
137:     int main (void)
138:     {
139:       struct dirent **eps;
140:       int n;

[/PHP]

All of the code is here:
[http://www.gnu.org/s/libc/manual/html_node/Simple-Directory-Lister-Mark-II.html#Simple-Directory-Lister-Mark-II](http://www.gnu.org/s/libc/manual/html_node/Simple-Directory-Lister-Mark-II.html#Simple-Directory-Lister-Mark-II)

Anyone have an idea as to why im getting errors? The error messages make no sense to me.

---

### Post by MindSz on 2010-04-20
> **fallenshadow said:**
> 
All of the code is here:
[http://www.gnu.org/s/libc/manual/html_node/Simple-Directory-Lister-Mark-II.html#Simple-Directory-Lister-Mark-II](http://www.gnu.org/s/libc/manual/html_node/Simple-Directory-Lister-Mark-II.html#Simple-Directory-Lister-Mark-II)


I just compiled the code with no errors. Make sure you're not leaving open brackets or that you have forgotten semi-colons in your code before this.

---

### Post by fallenshadow on 2010-04-20
>> Make sure you're not leaving open brackets or that you have forgotten semi-colons in your code before this.

My code before it works fine.

Its strange... the code works fine on its own.

Then all I did was copy and paste the code into my project. I commented out everything else so when I click a button it will just run this code only.

However when inside my project it fails on me. :confused:

---

### Post by fallenshadow on 2010-04-20
Ok since the code works on its own maybe I will be able to run it from my project and then read if its TRUE or FALSE for .jar existing.

I am just working on that code for file listing at the moment. I am going to try and implement code to find .jar files from the output of file listing.

I will post back any results or if I get stuck.

---

### Post by fallenshadow on 2010-04-20
Ok I have combined my own string reading code with the file listing code. Here is the result:

[PHP]
#include <stdio.h>
#include <dirent.h>
#include <iostream>
#include <string>
using namespace std;
     
     static int
     one (const struct dirent *unused)
     {
       return 1;
     }
     
     int
     main (void)
     {
       struct dirent **eps;
       int n;
     
       n = scandir ("./", &eps, one, alphasort);
       if (n >= 0)
         {
           int cnt;
           for (cnt = 0; cnt < n; ++cnt)
             puts (eps[cnt]->d_name);
             
  string str (d_name);
  string str2 (".jar");
  size_t found;

  // Output 
  found=str.find(str2);
  if (found!=string::npos)
    cout << ".Jar files found " << int(found) << endl;
         }
         
       else
         perror ("Couldn't open the directory");
     
       return 0;
     }
[/PHP]

Only problem is I still have to declare the "d_name" variable as something for string. What would I declare it as?

---

### Post by PaulM1985 on 2010-04-20
I have not tested this, but something like this might work for your while loop:

```

size_t found = string::npos;
for (cnt = 0; cnt < n && found == string::npos; ++cnt)
{
  string str (eps[cnt]->d_name);
  string str2 (".jar");

  // Output 
  found=str.find(str2);
}

```

---

### Post by fallenshadow on 2010-04-20
Updated my code:
[PHP]
#include <stdio.h>
#include <dirent.h>
#include <iostream>
#include <string>
using namespace std;
     
     static int
     one (const struct dirent *unused)
     {
       return 1;
     }
     
     int
     main (void)
     {
       struct dirent **eps;
       int n;
     
       n = scandir ("./", &eps, one, alphasort);
       if (n >= 0)
         {
           int cnt;
           for (cnt = 0; cnt < n; ++cnt)
             puts (eps[cnt]->d_name);
             
  size_t found = string::npos;
for (cnt = 0; cnt < n && found == string::npos; ++cnt)
{
  string str (eps[cnt]->d_name);
  string str2 (".jar");

  // Output 
  found=str.find(str2);
}
  }   
       else
         perror ("Couldn't open the directory");
     
       return 0;
     }

[/PHP]

However its just listing files, the string stuff seems to have no effect on the file listing output.

---

### Post by PaulM1985 on 2010-04-21
I meant remove the for loop you had currently and use the one I added in my previous post.  Something like:

```

#include <stdio.h>
#include <dirent.h>
#include <iostream>
#include <string>
using namespace std;
     
     static int
     one (const struct dirent *unused)
     {
       return 1;
     }
     
     int
     main (void)
     {
       struct dirent **eps;
       int n;
     
       n = scandir ("./", &eps, one, alphasort);
       if (n >= 0)
         {
           int cnt;
           size_t found = string::npos;
           for (cnt = 0; cnt < n && found == string::npos; ++cnt)
           {
             string str (eps[cnt]->d_name);
             string str2 (".jar");

             // Output 
             found=str.find(str2);
           }            

         if (found!=string::npos)
         {
           cout << ".Jar files found " << int(found) << endl;
         }
         else
         {
           cout << "Didn't find any .Jar files" << endl;
         }
       }
       else
       {
         cout << "Couldn't open directoy" << endl;
       }
     
       return 0;
     }  

```

(This is untested)

---

### Post by fallenshadow on 2010-04-21
Well the great news is that this lets me know if there are .jars there or not! :)

 It does not count properly but that doesn't matter to me. (it said there was 20 .jar files found when there was 1 file) :lolflag:

I will try to integrate this code into my project and report back later.

---

### Post by fallenshadow on 2010-04-21
Ok when I paste it into my project I still get the same 3 errors that I got before.

Can someone help find a solution to these errors?

> 
project.cc:132: error: a function-definition is not allowed here before &#8216;{&#8217; token
project.cc:138: error: a function-definition is not allowed here before &#8216;{&#8217; token
project.cc:322: error: expected `}' at end of input


---
Ok I think the "function-definition" could be solved by moving some of these lines up to the top. 

> 
static int
     one (const struct dirent *unused)
     {
       return 1;
     }
     
     int
     main (void)
     {
       struct dirent **eps;
       int n;


Im not sure which lines though...

---

### Post by fallenshadow on 2010-04-21
Ok is there some way I can use that code in a separate .cc file to my project?

It works just fine on its own but I would need to be able to read a value such as TRUE or FALSE from that separate .cc file into my project.

---

### Post by PaulM1985 on 2010-04-21
Have you tried looking on Google?  There is plenty information about how to do this.  Also, this can be found in many C programming books.

---

### Post by fallenshadow on 2010-04-21
My general knowledge of C++ is actually quite bad. so thats why I ask stupid questions.

So I create a header file for the separate file?

Then I would have separate.cc separate.h.

Then in my project.cc do "#include separate.h".

Then call my function by doing: void filecheck() in my project.cc?

Is this right up until now?

---

### Post by fallenshadow on 2010-04-21
Ok I tried compiling with my filecheck code in separate files linked to my project files... however Im still coming up against the same 3 errors as before. I can't believe something that should be so simple is so hard. ](*,)

Ok Im gonna take this from a different approach. 

Can C++ read output from Bash? :)

---

### Post by PaulM1985 on 2010-04-21
From your compiler errors it looks like you have not put a } to close a function.  This makes the compiler think you are defining a function within a function.  Try to use indentation to make it clearer between { and } so it is obvious if something has been opened and not closed.  Somewhere (I think in the project.cc) you have a function which isn't closed.

Paul

---

### Post by fallenshadow on 2010-04-21
I have searched my project code from top to bottom and everything is closed the way it should be.

My project actually compiles and runs fine _without_ the code for filechecking.

That leads me to believe that the problem lies with the filechecking code. It must be conflicting with something in my project.

To make things easier you can download my project (excluding certain un-needed things) and see the code as a whole. I am 99 percent sure that there is nothing wrong with my project code.

Heres a [Link]("http://www.photofiltre-lx.org/Jadmaker.tar.gz").

---

### Post by PaulM1985 on 2010-04-21
In the file jadmaker.cc you have a function called on_action_file_run().  Inside this function you have declared two functions.  These are one() and main(). You can't declare functions in functions.

---

### Post by fallenshadow on 2010-04-21
Oh right... I didn't understand those as functions.

So I guess what you are trying to tell me is move those to the top of jadmaker.cc. (underneath the #include stuff)

Is that correct? or should I be doing something else?

---

### Post by PaulM1985 on 2010-04-21
Take the one() function out of that function so that it is its own function and then remove the declaration for the main function and the "}" which ends the main function.  This will then invoke the code which was the main function in the on_action_file_run() function.  Instead of returning a value, maybe create a member variable on the class and set that.

---

### Post by fallenshadow on 2010-04-22
I tried to do what you said... now I have just one error.

Uploaded it... link is [_here_]("http://www.photofiltre-lx.org/Jadmaker.tar.gz").

---

### Post by fallenshadow on 2010-04-22
Ok I updated the code and put all the code into a separate function.

Please help me get over this final hurdle somebody. Im getting frustrated because Im so damn close to getting this to work. ](*,)

The link is above this post.

---

### Post by fallenshadow on 2010-04-23
Ok I have contacted a developer of one of my projects to see can he help me out with that last error. Fingers crossed! :)

Even if he can't, Paul your name will go down in the list of contributors for getting me this far.

If this fails it doesn't really matter because my Jadmaker does work. Its just a bit stupid because it will tell you that .jad files have been created even when no .jar files existed in the first place! :lolflag:

---

### Post by fallenshadow on 2010-04-23
Seems like he couldn't figure out that error either.

I will probably give up on this error checking code unless I can figure out that error fairly soon.

The filechecking code is in a separate function called "void filecheck();.

This is the error message:
> 
jadmaker.cc:116: error: expected unqualified-id before &#8216;{&#8217; token


---


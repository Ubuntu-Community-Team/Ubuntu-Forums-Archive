---
title: "Simple API for C++ file manipulation?"
date: 2008-10-05
forum: Programming Talk
---

### Post by Calmatory on 2008-10-05
I am not too familar with the "traditional" way of handling files with standard library, and I've found it complex for my needs. Something I don't want to use.

Is there any alternative API with easy/simple file handling?

---

### Post by LaRoza on 2008-10-05
What sort of manipulation?

The C library (I am not so familiar with the C++ ways anymore) is quite simple.

---

### Post by dwhitney67 on 2008-10-05
What are your needs?  Are they that unique?  The Standard Template Library (STL) has an easy API for managing files.  The other option is to use Boost's Filesystem library.

STL info:      [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)
Boost info:    [http://www.boost.org/doc/libs/1_34_1/libs/filesystem/doc/index.htm](http://www.boost.org/doc/libs/1_34_1/libs/filesystem/doc/index.htm)

---

### Post by nvteighen on 2008-10-05
Moreover, C's I/O library was designed to fit UNIX's filesystem (well, C was designed to fit UNIX), which Linux emulates. So, C has a very natural way to do things with files in such operating systems...

---

### Post by Calmatory on 2008-10-05
Hmm, my intention was to save character maps. two dimensional arrays to a file and then be able to read them.

Simple example of such a map:

```

#### #  ### #          ##
# # ##     #### ##  # ###
###  #  #   ##   #  ##  #
 #    # #      #  ##  # #
# #  ##   ##    ## #    #

```

Something like that, everyone knows if they have played ADOM or nethack. :)

The best way to do this must be to stick with C STL approach, even though I find it a bit complex for this task. I am just too used to higher level stuff. :)

---

### Post by dwhitney67 on 2008-10-05
> **Calmatory said:**
> Hmm, my intention was to save character maps. two dimensional arrays to a file and then be able to read them.

Simple example of such a map:

```

#### #  ### #          ##
# # ##     #### ##  # ###
###  #  #   ##   #  ##  #
 #    # #      #  ##  # #
# #  ##   ##    ## #    #

```

Something like that, everyone knows if they have played ADOM or nethack. :)

The best way to do this must be to stick with C STL approach, even though I find it a bit complex for this task. I am just too used to higher level stuff. :)
STL is part of C++, not C.  C does have a library as well, that is usable in C++ code.

Anyhow, the "image" you presented above is merely 5 strings.  You can either manage the strings, or store values in a two-dimensional array to indicate where a '#' mark goes, and where a ' ' character is needed.

Opening the file and writing to it is a breeze.
[PHP]
#include <fstream>
#include <string>

int main()
{
  std::fstream ofs( "myFile.txt", std::ios::out );    // open the file

  std::string str1( "#### #  ### #          ##" );
  std::string str2( "# # ##     #### ##  # ###" );
  std::string str3( "###  #  #   ##   #  ##  #" );
  std::string str4( " #    # #      #  ##  # #" );
  std::string str5( "# #  ##   ##    ## #    #" );

  if ( ofs )    // verify the file is open
  {
    ofs << str1 << std::endl;    // write string one
    ofs << str2 << std::endl;    // write string two
    ofs << str3 << std::endl;    // write string three
    ofs << str4 << std::endl;    // write string four
    ofs << str5 << std::endl;    // write string five

    ofs.close();   // close the file
  }

  return 0;
}[/PHP]

Of course, the above is merely an example with a "static" image.  As I stated earlier, you probably want to maintain a two-dimensional array (or a vector containing another vector of bools) to keep track where there is a "#" mark and where there isn't.

For the vector:
[PHP]#include <vector>

int main()
{
  typedef std::vector< std::vector<bool> > Mapping;

  Mapping hashMarkMap;

  ...

  return 0;
}[/PHP]

---

### Post by gnusci on 2008-10-07
Just for completenesses to the **dwhitney67** answer, I am adding the reading part:

[PHP]
#include <iostream>
#include <fstream>
#include <string>

int main(void){
  std::string str;
  // the code
  str = "#### #  ### #          ## \
  \n# # ##     #### ##  # ### \
  \n###  #  #   ##   #  ##  # \
  \n #    # #      #  ##  # # \
  \n# #  ##   ##    ## #    #";

  std::ofstream ofs("myFile.txt"); // open the file
  if ( ofs )                       // verify the file is open
  {
    ofs << str << std::endl;       // write the string
    ofs.close();                   // close the file
  }

  char buff[1204];
  std::ifstream ifs("myFile.txt"); // open the file
  if ( ifs )                       // verify the file is open
  {
    while(!ifs.eof()){             // read till the file finish
       ifs.getline(buff,1024);
       std::cout<<buff<<std::endl; // read line by line
    }
    ifs.close();                   // close the file
  }
  return 0;                        // bye bye
}

[/PHP]

---

### Post by joy pabuhat on 2008-10-07
Hi,

maybe anybody can help me. I can see that OO basic can help me do my price quotations faster by using function commands in Macro.

I found this line and tried one item and it display the description I want

Sub Main
   Print PT134( "1-3/4 x 4 Plain Tube" )
End Sub

__

When I type =PT134() let say on cell "A2" it will display "1-3/4 x 4 Plain Tube"

My question now is what command should I use in order to display the price on the same row but on different column "A7" once I press the function =PT134(). 

Hope you can help me.

Thank you in advance.

God bless you all.

---

### Post by dwhitney67 on 2008-10-07
> **joy pabuhat said:**
> Hi,

maybe anybody can help me. I can see that OO basic can help me do my price quotations faster by using function commands in Macro.

I found this line and tried one item and it display the description I want

Sub Main
   Print PT134( "1-3/4 x 4 Plain Tube" )
End Sub

__

When I type =PT134() let say on cell "A2" it will display "1-3/4 x 4 Plain Tube"

My question now is what command should I use in order to display the price on the same row but on different column "A7" once I press the function =PT134(). 

Hope you can help me.

Thank you in advance.

God bless you all.

Wow, I think this earns a Gold Medal for an attempt at thread hijacking.

Unfortunately your questions has nothing to do with C++, much less with the query presented in the OP.

---

### Post by gnusci on 2008-10-07
> **joy pabuhat said:**
> Hi,

maybe anybody can help me. I can see that OO basic can help me do my price quotations faster by using function commands in Macro.

I found this line and tried one item and it display the description I want

Sub Main
   Print PT134( "1-3/4 x 4 Plain Tube" )
End Sub

__

When I type =PT134() let say on cell "A2" it will display "1-3/4 x 4 Plain Tube"

My question now is what command should I use in order to display the price on the same row but on different column "A7" once I press the function =PT134(). 

Hope you can help me.

Thank you in advance.

God bless you all.

I agree with **dwhitney67**, please open a new thread, and make a programming question... Anyway, I couldn't get the point of your question.

---

### Post by dribeas on 2008-10-07
> **dwhitney67 said:**
> [PHP]int main()
{
  typedef std::vector< std::vector<bool> > Mapping;

  Mapping hashMarkMap;

  ...

  return 0;
}[/PHP]

[Beware]("http://209.85.135.104/search?q=cache:ziddr4SHt9YJ:www.gotw.ca/publications/N1211.pdf&hl=es&ct=clnk&cd=6&gl=es&client=firefox-a") of std::vector<bool> ([pdf]("http://www.gotw.ca/publications/N1211.pdf")), or a more recent [article]("http://www.informit.com/guides/content.aspx?g=cplusplus&seqNum=98") that considers the C++0x standard draft. If you are not in desperate need for memory, you will be better off with std::vector<char> storing 1's and 0's.

---

### Post by gnusci on 2008-10-08
Thanks **dribeas**, interesting and useful information.

---


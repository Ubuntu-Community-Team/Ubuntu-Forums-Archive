---
title: "Errors in installing program"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by cdlam on 2012-11-04
Hello,
  As part of a bioinformatics project I'm using a program called MED2. I'm not going to lie, it's obscure (developed by a Chinese theoretical biology lab) and oldish (the website was last updated around 2007), so there isn't much hope for support. The readme says that to install I should run "build" in the main directory (it contains a shell script called "build".

Just to give you some bearings, there is a main directory called LINUX_UNIX, which contains the subdirectories: bin, MED, TISModel. The bin is empty and the MED and TISModel directories have a bunch of files, including makefiles.

Here is what is in the "build" file:

> #!/bin/bash
cd MED2
make
cp MED2 ../bin
cd ..
cd TISModel
make
cp TISModel ../bin
cd ..
cd bin
chmod a+x MED2 TISModel
cd ..

So I do that and this happens:
> 
chris@ubuntu:~/Documents/IS/Bioinformatics-Software/MED/LINUX_UNIX$ perl build
g++ GeneInfo.cpp -c
In file included from TypeDef.h:4:0,
                 from GeneInfo.h:3,
                 from GeneInfo.cpp:5:
TypeDefBase.h:7:21: error: ‘string’ is not a member of ‘std’
TypeDefBase.h:7:21: error: ‘string’ is not a member of ‘std’
TypeDefBase.h:7:32: error: template argument 1 is invalid
TypeDefBase.h:7:32: error: template argument 2 is invalid
TypeDefBase.h:7:40: error: invalid type in declaration before ‘;’ token
TypeDefBase.h:17:32: error: ‘string’ is not a member of ‘std’
TypeDefBase.h:17:32: error: ‘string’ is not a member of ‘std’
TypeDefBase.h:17:48: error: template argument 1 is invalid
TypeDefBase.h:17:50: error: template argument 1 is invalid
TypeDefBase.h:17:50: error: template argument 2 is invalid
TypeDefBase.h:17:63: error: invalid type in declaration before ‘;’ token
In file included from TypeDef.h:6:0,
                 from GeneInfo.h:3,
                 from GeneInfo.cpp:5:
Matrix.h:34:87: warning: friend declaration ‘Matrix_T<Type_T> operator-(Matrix_T<Type_T>&, Matrix_T<Type_T>&)’ declares a non-template function [-Wnon-template-friend]
Matrix.h:34:87: note: (if this is not what you intended, make sure the function template has already been declared and add <> after the function name here) 
Matrix.h: In member function ‘Matrix_T<Type_T>& Matrix_T<Type_T>::toBeLogo()’:
Matrix.h:119:22: error: there are no arguments to ‘log’ that depend on a template parameter, so a declaration of ‘log’ must be available [-fpermissive]
Matrix.h:119:22: note: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
Matrix.h:119:29: error: there are no arguments to ‘log’ that depend on a template parameter, so a declaration of ‘log’ must be available [-fpermissive]
Matrix.h:123:58: error: there are no arguments to ‘log’ that depend on a template parameter, so a declaration of ‘log’ must be available [-fpermissive]
Matrix.h: In member function ‘void Matrix_T<Type_T>::rand()’:
Matrix.h:174:20: error: there are no arguments to ‘Random’ that depend on a template parameter, so a declaration of ‘Random’ must be available [-fpermissive]
make: *** [GeneInfo.o] Error 1
cp: cannot stat `MED2': No such file or directory
g++ GeneInfo.cpp -c
In file included from TypeDef.h:4:0,
                 from GeneInfo.h:3,
                 from GeneInfo.cpp:1:
TypeDefBase.h:7:21: error: ‘string’ is not a member of ‘std’
TypeDefBase.h:7:21: error: ‘string’ is not a member of ‘std’
TypeDefBase.h:7:32: error: template argument 1 is invalid
TypeDefBase.h:7:32: error: template argument 2 is invalid
TypeDefBase.h:7:40: error: invalid type in declaration before ‘;’ token
TypeDefBase.h:17:32: error: ‘string’ is not a member of ‘std’
TypeDefBase.h:17:32: error: ‘string’ is not a member of ‘std’
TypeDefBase.h:17:48: error: template argument 1 is invalid
TypeDefBase.h:17:50: error: template argument 1 is invalid
TypeDefBase.h:17:50: error: template argument 2 is invalid
TypeDefBase.h:17:63: error: invalid type in declaration before ‘;’ token
In file included from TypeDef.h:6:0,
                 from GeneInfo.h:3,
                 from GeneInfo.cpp:1:
Matrix.h: In member function ‘double Matrix_T<Type_T>::getInfo(int, int, Ve_D&)’:
Matrix.h:36:53: error: there are no arguments to ‘log’ that depend on a template parameter, so a declaration of ‘log’ must be available [-fpermissive]
Matrix.h:36:53: note: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
make: *** [GeneInfo.o] Error 1
cp: cannot stat `TISModel': No such file or directory
chmod: cannot access `MED2': No such file or directory
chmod: cannot access `TISModel': No such file or directory

The end result of running "build" is that two progam files are available in the bin directory of the MED folder: MED2 and TISModel. Needless to say, neither is there after I run build. I get the same errors when I run "make" inside the subdirectories.

I'm kind of hoping there's something I can do myself that will fix this. If not I'll reevaluate what I'm doing. Any help anyone can give me would be greatly appreciated, thanks.

--Chris

---

### Post by squakie on 2012-11-04
Removed - I misread the opening post and therefore what I had posted here was invalid.

---

### Post by Kevin McCready on 2012-11-04
Bump for Chris. I have also been having problems figuring out make, build etc. 

Chris, it so happens that I am a scientific translator (from Chinese into English). I like to contribute to science, sometimes for free, so get in touch if you need translations.

---

### Post by newb85 on 2012-11-04
I'm definitely out of my league, here, but it strikes me as odd that you tried to run build with perl.  If build is a shell script (you said it is, and it definitely looks like one), then why not run it as a shell script?

Instead of 
```
perl build
```
that would be
```
./build
```

---

### Post by squakie on 2012-11-05
Removed - misread initial post.

Given the script (and it is indeed a shell script - notice the $!/bin/bash)  you should indeed do as newb85 suggested:

./build

if you get permission errors:

chmod +x build

and try again.

If you get errors about needing to have root permissions, run with sudo.

I checked the website and indeed it's old and apparently not being updated.  The info there said to run the script and then mentions where things are/go after that.

---

### Post by cdlam on 2012-11-05
Hey guys, thanks for the replies.

I'm not sure why I used "perl build", but I did try ./build and got the  same errors. I emailed the authors of the software, so maybe I'll get  some help there. Possibly.

Kevin - thanks for the offer, I haven't needed any translating as of yet  but I'll keep it in mind if I need any help in the future.

There is a windows version that comes with MED2.exe, TISModel.exe and two .txt files required for running the program, however when I run them the program starts but then hit's an unexpected error and stops. Eh. 

thanks for the replies

---

### Post by cdlam on 2012-11-06
Hey so the author contacted me and directed me to the current version: [http://bioinfo.ctb.pku.edu.cn/med2_1/MED2.htm](http://bioinfo.ctb.pku.edu.cn/med2_1/MED2.htm)

Very disappointingly I get the same exact errors when running ./build (and the Windows version still doesn't work either). Apparently the original program was written in MSVS C++ 6.0, which I guess is pretty old. Would that have anything to do with it?

In this error
> chris@ubuntu:~/Documents/IS/Bioinformatics-Software/MED/LINUX$ ./build
g++ GeneInfo.cpp -c 
In file included from TypeDef.h:4:0,
                 from GeneInfo.h:3,
                 from GeneInfo.cpp:5:
TypeDefBase.h:7:21: error: &#8216;string&#8217; is not a member of &#8216;std&#8217;
TypeDefBase.h:7:21: error: &#8216;string&#8217; is not a member of &#8216;std&#8217;
TypeDefBase.h:7:32: error: template argument 1 is invalid
TypeDefBase.h:7:32: error: template argument 2 is invalid
TypeDefBase.h:7:40: error: invalid type in declaration before &#8216;;&#8217; token
TypeDefBase.h:17:32: error: &#8216;string&#8217; is not a member of &#8216;std&#8217;
TypeDefBase.h:17:32: error: &#8216;string&#8217; is not a member of &#8216;std&#8217;
TypeDefBase.h:17:48: error: template argument 1 is invalid
TypeDefBase.h:17:50: error: template argument 1 is invalid
TypeDefBase.h:17:50: error: template argument 2 is invalid
TypeDefBase.h:17:63: error: invalid type in declaration before &#8216;;&#8217; token
In file included from TypeDef.h:6:0,
                 from GeneInfo.h:3,
                 from GeneInfo.cpp:5:


Seems to be corresponding to these lines:
```
#ifndef TYPEDEFBASE_H
#define TYPEDEFBASE_H

#include<vector>
#include<utility>
typedef std::vector<int> Ve_I;
typedef std::vector**<std::string> Ve_Str;**
typedef const std::vector<int> con_Ve_I;
typedef std::vector< std::pair<int,int> > Ve_Pa_I_I;
typedef std::vector<double> Ve_D;
typedef const std::vector<double> con_Ve_D;
typedef std::vector< std::vector<int> > Ve_Ve_I;
typedef std::vector< std::vector<double> > Ve_Ve_D;
typedef std::vector< double* > Ve_D_Ptr;
typedef std::vector< std::vector<double>* > Ve_Ve_D_Ptr;
typedef const std::vector< std::vector<double> > con_Ve_Ve_D;
**typedef std::vector< std::pair<std::string, int> > Ve_Pa_Str_I;**
typedef std::pair<int, int> Pa_I_I;
typedef std::pair<int, double> Pa_I_D;
typedef std::pair<bool, double> Pa_B_D;
typedef std::pair<bool, int> Pa_B_I;
typedef std::pair<double, double> Pa_D_D;
typedef std::pair<double, int> Pa_D_I;
typedef const std::pair<int, int> con_Pa_I_I;
typedef std::vector< std::pair< double, double > > Ve_Pa_D_D;
typedef std::vector< std::pair< double, int > > Ve_Pa_D_I;
typedef std::pair<std::vector<double>,std::vector<int> > Pa_Ve_D_Ve_I;
#include<fstream>
typedef std::ifstream ifstream;
typedef std::ofstream ofstream;
typedef std::ostream ostream;
typedef std::istream istream;

#include<string>
typedef std::string Str;
typedef const std::string con_Str;

#include<deque>
typedef const std::deque<int> con_De_I; 
typedef std::deque<int> De_I; 

#include<map>
typedef std::map< int, int > Map_I_I;
typedef std::map< int, std::string > Map_I_Str;

#include<set>
typedef std::set<int> Set_I;
typedef std::set<Str> Set_Str;
typedef std::set<double> Set_D;

#include<limits>
typedef std::numeric_limits<int> int_limits;

#include<list>
typedef std::list< std::pair< double, double > > List_Pa_D_D;
typedef std::list< int > List_I;

#include<iostream>
#include<iomanip>
#include<list>
#include"assert.h"
#include<algorithm>
#endif //TYPEDEFBASE_H


```I mean, they apparently use this so it should work. Ahh this is so irritating.

---

### Post by spjackson on 2012-11-06
```

#include <string>

``` needs to be up at the top, with vector, not further down. It's hard to say why it worked in some other environment.

---

### Post by cdlam on 2012-11-06
You, sir, are a gentleman and a scholar...

Haha well it seems to have built alright. I get new and interesting errors now.

```
chris@ubuntu:~/Desktop/LINUX/bin$ ./MED2 chlamydia.fna
Wellcome to MED2.0
Genome file is chlamydia.fna
sequence size: 1386
GC%: 0.436508

Number of exactcted ORFs: 9
Select root ORFs and first running of TIS model...
 iteration      Selected as coding    rejected as non-coding
       0                        0                        0
Selected root coding ORFs number: 0
Rejected non-coding ORFs number: 0
Remaining ORFs number: 9
sh: 1: del: not found
Segmentation fault (core dumped)
```

Perhaps I should make a new post for this? It's not really on the original topic I don't think. Unless there was some error with how it installed?

---

### Post by squakie on 2012-11-06
The del sounds like the Dos/Windows "delete command" - look at that script and see if you see someline that says del <somefilename>.  If so, you'd need to change that to rm <somefilename> for Linux.

---

### Post by squakie on 2012-11-07
Found the problem.  In the MED2.0 folder is source file MED_start.cpp.

In the program is a function called MED_start.

In that functions is a system call - i.e., a call to the OS.  It is using the Windows "del" while building the string for the system call.  Just change that "del" to "rm".

```
void MED_start::findHitMotifs( int mutNum )
{
    ifstream in( (m_motifsPath+"motifs.txt").data() );
    assert( in.good() );
    std::map<double,std::string,std::greater<double> > sig;
    while( !in.eof() )
    {
        Str signal;
        double times;
        in>>signal>>times;
        if( !signal.empty() )
            sig[times] = signal;//see MED_start.err
    };
    in.close();
//    system( Str("del \"" + m_motifsPath+"motifs.txt\"" ).data() );
    system( Str("rm \"" + m_motifsPath+"motifs.txt\"" ).data() );        //  changed here
.
.
.
.

```

---

### Post by cdlam on 2012-11-27
I forgot to reply,

this worked - thanks a lot man.

---


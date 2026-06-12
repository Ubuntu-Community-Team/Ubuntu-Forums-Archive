---
title: "wxWidgets - Hello world not compiling"
date: 2008-02-15
forum: Packaging and Compiling Programs
---

### Post by piotroxp on 2008-02-15
I've been digging around forums for the last week and still cannot find a solution:

intro: 
using g++ / eclipse ide / ubuntu 7.10 / all the stuff needed for wx installed

need:
want to start using wxwidgets as a base for my gui operations

wanted solution:
so the hello world app will compile


My app includes only wx/wx.h. I've added directories of the wx headers, then added all the built binaries to the project, afterwards added 'wx-config --libs' 'wx-config --cxxflags' to the linker commands. I have wxWidgets 2.6, 2.8 , 2.8.7 installed on my machine, I am using the latter in my development. Is installed in a specific folder, compiled without errors, SHOULD work without a glimpse.

Does not - I recieve 226 errors while I'm trying to build my application, a simple hello world, all of them lookin similair to this: 

```

Severity and Description	Path	Resource	Location	Creation Time	Id
/home/piotro/Desktop/ P1.Installs/wxWidgets/include/wx/chkconf.h #error "wxMessageBox is always needed"		Wx	line 1765	1203097962170	5731

```

and

```

Severity and Description	Path	Resource	Location	Creation Time	Id
/home/piotro/Desktop/ P1.Installs/wxWidgets/include/wx/app.h ‘wxApp’ has not been declared		Wx	line 630	1203097962174	5747

```

Full source code of my hello world with wx:

```

#include<wx_pb.h>
#include<wx/wx.h>


int main(){

}


```


I'm helpless right here.
Will keep on digging until I've succesfully compiled my program, but this may prove useful as long as someone will answer please.

---

### Post by piotroxp on 2008-02-16
Ok, I've found the solution.  posting it for anyone who has ever had/ is going to have problems with this:

If one is using eclipse 4<cdt<3, one must follow these steps after succesfully installing wxwidgets: 

create a project, create a random named cpp file in that project, enter the projects properties, go to c++ build -> settings and there accomplish this:


1. type wx-config --cppflags in your terminal, copy the output into the place that has g++ in it (g++ [your output of wx-config --cppflags) < in GCC C++ COMPILER

2. type wx-config --libs in terminal, copy the output after g++ in your GCC C++ LINKER

voila, works!

---

### Post by bkuhns on 2008-12-22
Thanks for returning and posting your solution! Saved me a headache, for sure :)

---

### Post by lwhitmore on 2009-02-01
Great, thanks - saved me a headache too..

I found I could use the following shortcuts, which saves going to terminal and copying and pasting the output.

For Compiler:

g++ `wx-config --cppflags`

For Linker:

g++ `wx-config --libs`

---

### Post by lunar_wire on 2009-11-20
Your Brilliant!!
Thanks:D

---

### Post by Mike_Longbow on 2010-09-14
You made my day, man.

Well, my night, actually...

This helped me solve an issue in Code::Blocks in wich I had already given up.

Cheers!

---


---
title: "C++ converting string into char*"
date: 2011-11-23
forum: Programming Talk
---

### Post by baldiehead on 2011-11-23
```
#include "cv.h" //main OpenCV header
#include "highgui.h" //GUI header
#include <iostream>
#include <fstream>
#include <string>
#include "DisplayImageClass.h"

using namespace std;

int Display::initiate_display()
{
    string line;
      ifstream myfile ("document.txt");
      if (myfile.is_open())
      {
        while ( myfile.good() )
        {
          getline (myfile,line);
          cout << line << endl;
      
    IplImage* img = cvLoadImage(line);
    cvNamedWindow( "Viva La Vida", CV_WINDOW_AUTOSIZE );
    cvShowImage("Viva La Vida", img);
    cvWaitKey(0);
    cvReleaseImage( &img );
    cvDestroyWindow( "Viva La Vida" );
    return 0;  
    }
        myfile.close();
    }
};


```

Basically, it's a combination of the OpenCV image loader and a document reader. Documents.txt holds the absolute path to the image. So the idea is that, the document reader reads the absolute path of the image, generates a string, then feeds it to OpenCV for it to load the image. Only problem now, is that cvLoadImage only accepts either const char* or int. 

Anyone knows how to convert string to const char* or int? It's a newbie question, but I rarely deal with C++, so i'm kinda lost.

---

### Post by crdlb on 2011-11-23
I think you're looking for ```
line.c_str()
```

---

### Post by cgroza on 2011-11-23
The first step to do in such a situation is to check the documentation:
[http://www.cplusplus.com/reference/string/string/](http://www.cplusplus.com/reference/string/string/)

You can see that std::string has a c_str method that returns a char* representation of it.
Be careful though, the returned char* still belongs to the string and it is not recommended to delete it.
You will have to copy it first if you will need to change it.

---

### Post by baldiehead on 2011-11-23
Ok guys, I'll go give it a try, and see how it goes......

---

### Post by baldiehead on 2011-11-23
More complicated than the one-liner given, but it helps that I have a starting point to work from. Good example here :[http://www.cplusplus.com/reference/string/string/c_str/](http://www.cplusplus.com/reference/string/string/c_str/)

But just in case, here's the corrected code which works now.

```
#include "cv.h" //main OpenCV header
#include "highgui.h" //GUI header
#include <iostream>
#include <fstream>
#include <string>
#include "DisplayImageClass.h"

using namespace std;

int Display::initiate_display()
{
    char * cstr, *p;
    string str;
    cstr = new char [str.size()+1];
         ifstream myfile ("document.txt");
      if (myfile.is_open())
      {
        while ( myfile.good() )
        {
          getline (myfile,str);
          cout << str << endl;
         
          strcpy (cstr, str.c_str());
      
    IplImage* img = cvLoadImage(cstr);
    cvNamedWindow( "Viva La Vida", CV_WINDOW_AUTOSIZE );
    cvShowImage("Viva La Vida", img);
    cvWaitKey(0);
    cvReleaseImage( &img );
    cvDestroyWindow( "Viva La Vida" );
    return 0;  
    }
        myfile.close();
    }
};

```

Thanks people. Free popcorn! :popcorn:

---

### Post by gateway67 on 2011-11-23
Don't celebrate too quickly...

Please look at this code, and tell me what's wrong with it.  The comments should offer you some hints.
```

#include <string>
#include <iostream>

int main()
{
   std::string str;

   std::cout << "str.size() + 1   = " << (str.size() + 1) << std::endl;

   char* cstr = new char[str.size() + 1];

   str = "foo.gif";   //An arbitrary image name.

   std::cout << "str.size() = " << str.size() << std::endl;

   strcpy(cstr, str.c_str());   // OOPS!  Buffer overrun.

   //and let's forget to delete cstr; We love memory leaks!
}

```As for your original code, why did something as the following not work?
```

IplImage* img = cvLoadImage(str.c_str());

```Also, it should be noted that when an fstream object is used as a conditional value, it will automatically be treated as a boolean value, thanks to the operator bool() method that is associated with streams.  So your code probably will work better if you employ something like:
```

ifstream myfile ("document.txt");

if (myfile)   // stream converted to bool value
{
   while (getline(myfile, str))  // getline() returns stream, which is then converted to bool value
   {
      IplImage* img = cvLoadImage(str.c_str());
      ...
   }
}


```

---

### Post by baldiehead on 2011-11-24
Before I try to answer the problem, I got to tell you, I have almost zero experience with C++, i deal more with Java. But anyways......

OK, so evidently, the code will not delete off whatever it finished using, causing the memory to be trapped and cannot be released for other stuff, and may cause program to crash, hang, stuff like that. I'm not used to it, cause java more or less automates the deletion of whatever is unnecessary.

As for the second question, I think that I left the things separately so it would be easier for me (a guy who's c++ is limited to taking examples and modifying it for personal use) to trouble shoot and easier if i ever look back to try to understand the code.

Thanks for the constructive feedback though. Time to go modify the program a bit more......xD

---


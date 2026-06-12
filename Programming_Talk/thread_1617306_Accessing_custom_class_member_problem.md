---
title: "Accessing custom class member problem"
date: 2010-11-09
forum: Programming Talk
---

### Post by erupter on 2010-11-09
Declarations
```

#include <string>
#define NAME_LENGTH 10

class Axis3
{
  private:
    float _angleX;
    float _angleY;
    float _angleZ;
    
  public:
    Axis3 (void);
    Axis3 (float val1, float val2, float val3);
    bool IsEmpty (void);
    float setAngleX (void);
    void getAngleX (float x);
    float setAngleY (void);
    void getAngleY (float x);
    float setAngleZ (void);
    void getAngleZ (float x);
    void Empty (void);
};

class PointLatLng
{
  private:
    float _lat;
    float _lng;
  public:
    PointLatLng (void);
    PointLatLng(float val1, float val2);
    bool IsEmpty(void);
    float getLat (void);
    void setLat (float x);
    float getLng (void);
    void setLng (float x);
  
};


class InertialModel
{
  
  private:    
    Axis3 _attitude;
    float _speed;
    float _heading;
    PointLatLng _position;
    std::string _name;
    bool _isupdated;  
    
  public:
    InertialModel (void);
    bool IsUpdated (void);
    void setUpdated (bool x);
    std::string Name (void);
    PointLatLng getPosition (void);
    void setPosition (PointLatLng x);
    Axis3 getAttitude (void);
    void setAttitude (Axis3 x);
    float getSpeed (void);
    void setSpeed (float x);
    float getHeading (void);
    void setHeading (float x);
  
  
};

```Definitions
```

#include <stdlib.h>
#include <stdio.h>
#include <cmath>
#include <string>
#include "library.h"
#include <time.h>

Axis3::Axis3 (void)
{
  _angleX=0;
  _angleY=0;
  _angleZ=0;
};

Axis3::Axis3(float val1, float val2, float val3)
{
    _angleX = val1;
    _angleY = val2;
    _angleZ = val3;
};


bool Axis3::IsEmpty(void)
{
  return ((_angleX && 0) && (_angleY && 0) && (_angleZ && 0));
};

float Axis3::getAngleX (void)
{
  return _angleX;
};

void Axis3::setAngleX (float x)
{
  _angleX = x;
};

float Axis3::getAngleY (void)
{
  return _angleY;
};

void Axis3::setAngleY (float x)
{
  _angleY = x;
};

float Axis3::getAngleZ (void)
{
  return _angleZ;
};

void Axis3::setAngleZ (float x)
{
  _angleZ = x;
};

void Axis3::Empty(void)
{
  _angleX = 0;
  _angleY = 0;
  _angleZ = 0;
};


PointLatLng::PointLatLng (void)
{
  _lat=0;
  _lng=0;
};

PointLatLng::PointLatLng(float val1, float val2)
{
    _lat = val1;
    _lng = val2;
};

bool PointLatLng::IsEmpty(void)
{
  return ((_lat && 0) && (_lng && 0));
};

float PointLatLng::getLat (void)
{
  return _lat;
};

void PointLatLng::setLat (float x)
{
  _lat = x;
};

float PointLatLng::getLng (void)
{
  return _lng;
};

void PointLatLng::setLng (float x)
{
  _lng = x;
};


bool InertialModel::IsUpdated (void)
{
  return _isupdated;
};

void InertialModel::setUpdated (bool x)
{
  _isupdated = x;
};

std::string InertialModel::Name (void)
{
  return _name;
};

PointLatLng InertialModel::getPosition (void)
{
  return _position;
};

void InertialModel::setPosition (PointLatLng x)
{
  _position = x;
};

Axis3 InertialModel::getAttitude (void)
{
  return _attitude;
};

void InertialModel::setAttitude (Axis3 x)
{
  _attitude = x;
};

float InertialModel::getSpeed (void)
{
  return _speed;
};

void InertialModel::setSpeed (float x)
{
  _speed = x;
};

float InertialModel::getHeading (void)
{
  return _heading;
};

void InertialModel::setHeading (float x)
{
  _heading = x;
};

InertialModel::InertialModel(void )
{
  int i,j;
  std::string builder;
  srand(time(NULL));
  char ch;
  for (i=0; i < NAME_LENGTH;i++)
  {
    j=rand() % 3;
    switch (j)
    {
      case 0:
    ch = char ((rand() % 10 )+48);
    builder.append(&ch);
    break;
      case 1:
    ch = char((rand() % 26 )+65);
    builder.append(&ch);
    break;
      case 2:
    ch = ((rand() % 26 )+97);
    builder.append(&ch);
    break;
    }
  }
  
  
}
```Actual program
```

#include <iostream>
#include <string>
#include <stdio.h>
#include <stdlib.h>
#include "library.h"

int main(int argc, char **argv) {

  InertialModel test;
  std::string mystr;
**==>   mystr.insert(test.Name); <==**
  printf("Test is : %s\n",mystr);
  return 0;
}

```The line giving me problems is in bold.
I tried every conceivable way, but it never compiles.
The class member Name returns a std::string as per the declaration so a direct copy should be possibile.
I tried
mystr=test.Name
string.append
string.assign
string.copy
string.data
string.insert
string.replace

but all failed.
Error is
"No matching function to call to 'std::basic_string**[BIGMESS]**"

What am I doing wrong?

---

### Post by vikas.sood on 2010-11-09
Try a function call this way.

mystr.insert(test.Name());

---

### Post by vikas.sood on 2010-11-09
And i dont think std::string::insert does what you are trying to do.
Am not sure of what you actually want. But if you are trying to get string returned by Name() method than this is all you need 
std::string mystr = test.Name();

---

### Post by erupter on 2010-11-09
> **vikas.sood said:**
> And i dont think std::string::insert does what you are trying to do.
Am not sure of what you actually want. But if you are trying to get string returned by Name() method than this is all you need 
std::string mystr = test.Name();

I've tried this.
Was my 1st choice.
Here is the result
```

main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:14: warning: cannot pass objects of non-POD type &#8216;struct std::string&#8217; through &#8216;...&#8217;; call will abort at runtime
main.cpp:14: warning: format &#8216;%s&#8217; expects type &#8216;char*&#8217;, but argument 2 has type &#8216;int&#8217;
/tmp/ccgP7YqD.o: In function `main':
main.cpp:(.text+0x1a): undefined reference to `InertialModel::InertialModel()'
main.cpp:(.text+0x68): undefined reference to `InertialModel::Name()'
collect2: ld returned 1 exit status

```And again i don't understand the error.

Edit:
ok looks like somehow Kdevelop isn't linking the library.
But by doing it manually, the **Undefined Reference** error goes away, but not the one at line 14.
Which i cannot understand.

---

### Post by spjackson on 2010-11-09
> **erupter said:**
> I've tried this.
Was my 1st choice.
Here is the result
```

main.cpp: In function ‘int main(int, char**)’:
main.cpp:14: warning: cannot pass objects of non-POD type ‘struct std::string’ through ‘...’; call will abort at runtime
main.cpp:14: warning: format ‘%s’ expects type ‘char*’, but argument 2 has type ‘int’
/tmp/ccgP7YqD.o: In function `main':
main.cpp:(.text+0x1a): undefined reference to `InertialModel::InertialModel()'
main.cpp:(.text+0x68): undefined reference to `InertialModel::Name()'
collect2: ld returned 1 exit status

```And again i don't understand the error.

```

#include <iostream>
#include <string>
#include <stdio.h>
#include <stdlib.h>
#include "library.h"

int main(int argc, char **argv) {

  InertialModel test;
  std::string mystr = test.Name();

  /* Can't do this  printf("Test is : %s\n",mystr); */
  printf("Test is : %s\n",mystr.c_str()); /* Method 1 */
  std::cout << "Test is : " << mystr << "\n"; /* Method 2 */

  return 0;

}
```Your "undefined reference" is because you are trying to link main.cpp without including your other module in the link.

---

### Post by erupter on 2010-11-09
Ok now it just got weirder.
It compiles.
It works in Windows, it doesn't work in Ubuntu.

Declarations
```

#include <string>
#define NAME_LENGTH 10

class Axis3
{
  private:
    float _angleX;
    float _angleY;
    float _angleZ;
    
  public:
    Axis3 (void);
    Axis3 (float val1, float val2, float val3);
    bool IsEmpty (void);
    float getAngleX (void);
    void setAngleX (float x);
    float getAngleY (void);
    void setAngleY (float x);
    float getAngleZ (void);
    void setAngleZ (float x);
    void Empty (void);
};

class PointLatLng
{
  private:
    float _lat;
    float _lng;
  public:
    PointLatLng (void);
    PointLatLng(float val1, float val2);
    bool IsEmpty(void);
    float getLat (void);
    void setLat (float x);
    float getLng (void);
    void setLng (float x);
  
};


class InertialModel
{
  
  private:    
    Axis3 _attitude;
    float _speed;
    float _heading;
    PointLatLng _position;
    std::string _name;
    bool _isupdated;  
    
  public:
    InertialModel (void);
    bool IsUpdated (void);
    void setUpdated (bool x);
    std::string Name (void);
    PointLatLng getPosition (void);
    void setPosition (PointLatLng x);
    Axis3 getAttitude (void);
    void setAttitude (Axis3 x);
    float getSpeed (void);
    void setSpeed (float x);
    float getHeading (void);
    void setHeading (float x);
  
  
};

```

Definitions
```

#include <stdlib.h>
#include <stdio.h>
#include <cmath>
#include <string>
#include "library.hh"
#include <time.h>

Axis3::Axis3 (void)
{
  _angleX=0;
  _angleY=0;
  _angleZ=0;
};

Axis3::Axis3(float val1, float val2, float val3)
{
    _angleX = val1;
    _angleY = val2;
    _angleZ = val3;
};


bool Axis3::IsEmpty(void)
{
  return ((_angleX && 0) && (_angleY && 0) && (_angleZ && 0));
};

float Axis3::getAngleX (void)
{
  return _angleX;
};

void Axis3::setAngleX (float x)
{
  _angleX = x;
};

float Axis3::getAngleY (void)
{
  return _angleY;
};

void Axis3::setAngleY (float x)
{
  _angleY = x;
};

float Axis3::getAngleZ (void)
{
  return _angleZ;
};

void Axis3::setAngleZ (float x)
{
  _angleZ = x;
};

void Axis3::Empty(void)
{
  _angleX = 0;
  _angleY = 0;
  _angleZ = 0;
};


PointLatLng::PointLatLng (void)
{
  _lat=0;
  _lng=0;
};

PointLatLng::PointLatLng(float val1, float val2)
{
    _lat = val1;
    _lng = val2;
};

bool PointLatLng::IsEmpty(void)
{
  return ((_lat && 0) && (_lng && 0));
};

float PointLatLng::getLat (void)
{
  return _lat;
};

void PointLatLng::setLat (float x)
{
  _lat = x;
};

float PointLatLng::getLng (void)
{
  return _lng;
};

void PointLatLng::setLng (float x)
{
  _lng = x;
};


bool InertialModel::IsUpdated (void)
{
  return _isupdated;
};

void InertialModel::setUpdated (bool x)
{
  _isupdated = x;
};

std::string InertialModel::Name (void)
{
  return _name;
};

PointLatLng InertialModel::getPosition (void)
{
  return _position;
};

void InertialModel::setPosition (PointLatLng x)
{
  _position = x;
};

Axis3 InertialModel::getAttitude (void)
{
  return _attitude;
};

void InertialModel::setAttitude (Axis3 x)
{
  _attitude = x;
};

float InertialModel::getSpeed (void)
{
  return _speed;
};

void InertialModel::setSpeed (float x)
{
  _speed = x;
};

float InertialModel::getHeading (void)
{
  return _heading;
};

void InertialModel::setHeading (float x)
{
  _heading = x;
};

InertialModel::InertialModel(void )
{
  int i,j;
  std::string builder;
  srand(time(NULL));
  char ch;
  for (i=0; i < NAME_LENGTH;i++)
  {
    j=rand() % 3;
    switch (j)
    {
      case 0:
    ch = char ((rand() % 10 )+48);
    InertialModel::_name.append(&ch,1);
    break;
      case 1:
    ch = char((rand() % 26 )+65);
    InertialModel::_name.append(&ch,1);
    break;
      case 2:
    ch = ((rand() % 26 )+97);
    InertialModel::_name.append(&ch,1);
    break;
    //InertialModel::_name.copy(&(builder.cbegin),NAME_LENGTH,0);
    }
  }
  
  
}

```

Main
```

#include <iostream>
#include <string>
#include <stdio.h>
#include <stdlib.h>
#include "library.h"

int main(int argc, char **argv) {

  InertialModel *test = new InertialModel;
  std::string mystr1, mystr2;
  mystr1 = "test";
  mystr2 = "appa";
  mystr1=test->Name();
  std::cout << "Name is : " << mystr1 << std::endl;
  getchar();
  return 0;
}


```

---

### Post by dwhitney67 on 2010-11-09
There's nothing to indicate that it would fail.  Can you please elaborate?

---

### Post by erupter on 2010-11-09
> **dwhitney67 said:**
> There's nothing to indicate that it would fail.  Can you please elaborate?

I don't know.
Now it works.
What i changed it that now all the elements in the function definitions bear the parent name (probably this isn't the right way to call it, but I don't know the standard name):

instead of
return _name;

it's
return InertialModel::_name;

I changed all of them in this way reflecting each class belonging.
This way of writing code seems to me quite unreadable.
I think that keeping in the function definition all the class structure would make it a lot more readable and maintainable.

Instead of

InertialModel:: getAttitude
return InertialModel::_attitude

class InertialModel
getAttitude
return _attitude

This seems much more reasonable, especially when the class becomes big with lots of whistles.
But when i tried doing this the compiler lamented about function redefinition.
Was only a warning but still present.
So how should i do it?
Typing the class each time seems consuming and makes for a less readable code.
Is it just me thinking this way?

---

### Post by dwhitney67 on 2010-11-09
> **erupter said:**
> 
it's
return InertialModel::_name;

This should not make a difference.

You only need to reference an object or constant using a class name (or namespace name) when referring to said object/constant from outside of the class (or namespace).

Here's your program, whittled down to the bare minimum:
```

#include <ctime>
#include <cstdlib>
#include <string>
#include <iostream>

class InertialModel
{
public:
   static const int NAME_LENGTH = 10;

   InertialModel()
   {
      srand(time(NULL));
      char ch;
      for (int i = 0; i < NAME_LENGTH; ++i)
      {
         int j = rand() % 3;

         switch (j)
         {
            case 0:
                ch = char ((rand() % 10 )+48);
                _name.append(&ch,1);
                break;
            case 1:
                ch = char((rand() % 26 )+65);
                _name.append(&ch,1);
                break;
            case 2:
                ch = ((rand() % 26 )+97);
                _name.append(&ch,1);
                break;
         }
      }
   }

   std::string Name() const { return _name; }

private:
   std::string _name;
};

int main()
{
   InertialModel* im = new InertialModel;

   std::cout << im->Name() << std::endl;
}

```

---


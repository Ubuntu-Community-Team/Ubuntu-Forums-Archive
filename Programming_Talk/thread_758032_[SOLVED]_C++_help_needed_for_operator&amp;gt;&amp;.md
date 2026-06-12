---
title: "[SOLVED] C++ help needed for operator&amp;gt;&amp;gt; usage"
date: 2008-04-17
forum: Programming Talk
---

### Post by dwhitney67 on 2008-04-17
I have the code below, which I could have swore compiled fine back in the "old days" when I was using Fedora Core 5.  However, now it fails to compile because of the operator>> method.

Can someone help me sort this out.  Here's the error message and following that is the code:

```
> g++ fstreamOpenClose.cpp 
fstreamOpenClose.cpp: In function ‘void operator>>(std::ostream&, EventLog&)’:
fstreamOpenClose.cpp:20: error: no match for ‘operator>>’ in ‘os >> val’
```

[PHP]#include <fstream>
#include <iostream>

using namespace std;

class EventLog
{
  public:
    EventLog( int value = 0 ) : value(value) {}

    friend ostream& operator<< (ostream &os, const EventLog &log)
    {
      os << log.value;
      return os;
    }

    friend void operator>> (ostream &os, EventLog &log)
    {
      int val;
      os >> val;
      log = EventLog(val);
    }

  private:
    int value;
};

int main()
{
  EventLog log(10);

  string   fileName( "foo" );
  fstream  fs;

  // open for writing/appending
  //
  fs.open( fileName.c_str(), ios::out | ios::app | ios::binary );
  cout << log << endl;
  fs << log << endl;
  fs.close();


  // open for reading
  //
  EventLog newLog;
  fs.open( fileName.c_str(), ios::in | ios::binary );
  fs >> newLog;
  cout << newLog << endl;
  fs.close();

  return 0;
}[/PHP]

P.S.  Here's the version of GCC I am using:
```
> g++ --version
g++ (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE
```

---

### Post by Mickeysofine1972 on 2008-04-17
> **dwhitney67 said:**
> I have the code below, which I could have swore compiled fine back in the "old days" when I was using Fedora Core 5.  However, now it fails to compile because of the operator>> method.

Can someone help me sort this out.  Here's the error message and following that is the code:

```
> g++ fstreamOpenClose.cpp 
fstreamOpenClose.cpp: In function ‘void operator>>(std::ostream&, EventLog&)’:
fstreamOpenClose.cpp:20: error: no match for ‘operator>>’ in ‘os >> val’
```

[PHP]#include <fstream>
#include <iostream>

using namespace std;

class EventLog
{
  public:
    EventLog( int value = 0 ) : value(value) {}

    friend ostream& operator<< (ostream &os, const EventLog &log)
    {
      os << log.value;
      return os;
    }

    friend void operator>> (ostream &os, EventLog &log)
    {
      int val;
      os >> val;
      log = EventLog(val);
    }

  private:
    int value;
};

int main()
{
  EventLog log(10);

  string   fileName( "foo" );
  fstream  fs;

  // open for writing/appending
  //
  fs.open( fileName.c_str(), ios::out | ios::app | ios::binary );
  cout << log << endl;
  fs << log << endl;
  fs.close();


  // open for reading
  //
  EventLog newLog;
  fs.open( fileName.c_str(), ios::in | ios::binary );
  fs >> newLog;
  cout << newLog << endl;
  fs.close();

  return 0;
}[/PHP]

P.S.  Here's the version of GCC I am using:
```
> g++ --version
g++ (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE
```

i dunno about your problem but the first thing you b=need to do is rename that value arg for the ctor to something different like a_Value and you member value to something like m_Value

that might make a difference

Mike

---

### Post by mike_g on 2008-04-17
Here:
```
    friend ostream& operator<< (ostream &os, const EventLog &log)
    {
      os << log.value;
      return os;
    } 
```
It looks as if you want to shift 'os' left in which case I guess you want:
```
os <<= log.value;
```

---

### Post by themusicwave on 2008-04-17
I don't think it's a bit shift is it?

I think what he is doing is overloading the << and >> operators for his class.  He is trying to use them as a "stream operator"  essentially just like you can do:

cout >> "Somethin"
cin << x

Something is wrogn with the overloading though so that it doesn't know how to associate the << operator with and Ostream object perhaps?

I haven't done C++ in awhile and I haven't used those friend functions in a long time either.  

That's what it looks like to me, but then again I am trying to remember back to Intro to programmer(yeah they made us use C++ and friend functions in an intro class)

Good luck!

---

### Post by mike_g on 2008-04-17
Yeah no I'm an idiot. Ignore what I said, lol.

---

### Post by dwhitney67 on 2008-04-17
Sorry for the tardy reply, but I just sorted out the issue.  The solution came to me when I was out for a drive.  In the operator>>() method, I should have specified an istream, not an ostream.  Thus the method signature should be:

[PHP]friend void operator>> ( istream &os, EventLog &log )
{
  //...
}[/PHP].

---

### Post by dwhitney67 on 2008-04-17
> **Mickeysofine1972 said:**
> i dunno about your problem but the first thing you b=need to do is rename that value arg for the ctor to something different like a_Value and you member value to something like m_Value

that might make a difference

Mike
I could implement this suggestion, but it doesn't make a difference.  The compiler is smart enough to distinguish the local variable from the class variable.  Of course, if I had implemented the assignment within the constructor body, then I would have to preface the member data with a "this->".

---

### Post by Mickeysofine1972 on 2008-04-19
> **dwhitney67 said:**
> I could implement this suggestion, but it doesn't make a difference.  The compiler is smart enough to distinguish the local variable from the class variable.  Of course, if I had implemented the assignment within the constructor body, then I would have to preface the member data with a "this->".

Well thats true but what about you own mind? 

Can you say that you wont ever get confused with this sort of naming convention? after all what happens in a large project when you haven't looked at it for 3 months?

Have mercy on yourself and others when writing your code and you will be able to manage large amounts of code with much less effort.

Apps hungarian is there for just this purpose, and it pays to develop good coding habits, it what sets good programmers apart.

Thats my 2 cents anyhoo, keep up the good learning though, the world needs good programmers.

Mike

---


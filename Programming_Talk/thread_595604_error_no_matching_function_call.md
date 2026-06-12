---
title: "error: no matching function call"
date: 2007-10-28
forum: Programming Talk
---

### Post by JupiterV2 on 2007-10-28
I am getting the error:

virtualinherit.cpp: In constructor ‘ErrorMessage::ErrorMessage(const std::string&, const std::string&, const std::string&)’:
virtualinherit.cpp:33: error: no matching function for call to ‘Message::Message()’
virtualinherit.cpp:15: note: candidates are: Message::Message(const std::string&, const std::string&)
virtualinherit.cpp:8: note:                 Message::Message(const Message&)

Code is as follows:

```

#include <iostream>

using std::cout;
using std::cin;
using std::string;

class Message 
{
protected:
          string source;     // Source of message
          string message;    // text in message

public:
       // constructor
       Message (const string& src, const string& msg) {
               source = src;
               message = msg;
       }

       // member function: convert message to string
       virtual string getMessage() const {
               return source + ": " + message;
       }
};



class ErrorMessage : public Message 
{
protected:
          string errorCode;
          
public:
       // constructor
       ErrorMessage (const string& ec, const string& src, const string& msg) {
            errorCode = ec;     // init error code
            source = src;       // init source
            message = msg;      // init message
       }
       
       // member function
       virtual string getMessage() const {
               return "ERROR: " + errorCode + ": " + source + ": " + message;
       }
};

int main() {
    ErrorMessage error ("1234", "Hard Drive", "Insufficient space.");

    return 0;
}

```

---

### Post by dwhitney67 on 2007-10-29
Try changing your ErrorMessage constructor to look like:

```
       // constructor
       ErrorMessage (const string& ec, const string& src, const string& msg)
          : Message( src, msg ) {
            errorCode = ec;     // init error code
       }
```

I should point out that in your original code, the ErrorMessage constructor is attempting to call the default constructor for Message, which takes no args, and which you have not implemented (but implicitly defined).  If you do not plan to have a default constructor, you should explicitly define one in the private section, but don't implement it.  Ditto for other constructors (e.g. copy constructor).

---

### Post by JupiterV2 on 2007-10-29
Thank you very much! I was able to solve the issue immediately by creating a no-argument constructor. I appreciate the help!

---


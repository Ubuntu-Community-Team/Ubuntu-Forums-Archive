---
title: "mimetic compilation problem after upgrading ubuntu 9.10"
date: 2009-11-18
forum: Programming Talk
---

### Post by trb61 on 2009-11-18
Hi All,

I recently upgraded to Ubuntu 9.10 from 9.04.

However, I started to get the following compilation error when I attempt to compile a C++ source file which uses mimetic library:

In file included from mimetic-0.9.6/mimetic/rfc822/header.h:27,
                 from mimetic-0.9.6/mimetic/header.h:20,
                 from mimetic-0.9.6/mimetic/mimetic.h:27,
                 from src/MySoftware.cpp:5:
mimetic-0.9.6/mimetic/rfc822/messageid.h:38: error: expected ‘)’ before ‘thread_id’

Below is the content of messageid.h:

#ifndef _MIMETIC_MESSAGEID_H_
#define _MIMETIC_MESSAGEID_H_
#ifdef HAVE_STDINT_H
#include <stdint.h>
#endif
#include <string>
#include <mimetic/libconfig.h>
#ifdef HAVE_INTTYPES_H
#include <inttypes.h>
#endif
#include <mimetic/utils.h>
#include <mimetic/os/utils.h>
#include <mimetic/rfc822/fieldvalue.h>

namespace mimetic
{


/// Message-ID field value 
/// On Win32 Winsock library must be initialized before using this class.
struct MessageId: public FieldValue
{
    MessageId(uint32_t thread_id = 0 ); //line 38 corresponds to this one
    MessageId(const std::string&);
    std::string str() const;
    void set(const std::string&);
protected:
    FieldValue* clone() const;
private:
    static unsigned int ms_sequence_number;
    std::string m_msgid;
};


}

#endif

To compile the code above, I use gcc with -Wall -c -g options enabled.

My previous gcc version was gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3

What  should I do to make the code above compile ?

What may have happened after upgrading ?

Thanks.

---

### Post by Arndt on 2009-11-18
> **trb61 said:**
> Hi All,

I recently upgraded to Ubuntu 9.10 from 9.04.

However, I started to get the following compilation error when I attempt to compile a C++ source file which uses mimetic library:

In file included from mimetic-0.9.6/mimetic/rfc822/header.h:27,
                 from mimetic-0.9.6/mimetic/header.h:20,
                 from mimetic-0.9.6/mimetic/mimetic.h:27,
                 from src/MySoftware.cpp:5:
mimetic-0.9.6/mimetic/rfc822/messageid.h:38: error: expected ‘)’ before ‘thread_id’

Below is the content of messageid.h:

#ifndef _MIMETIC_MESSAGEID_H_
#define _MIMETIC_MESSAGEID_H_
#ifdef HAVE_STDINT_H
#include <stdint.h>
#endif
#include <string>
#include <mimetic/libconfig.h>
#ifdef HAVE_INTTYPES_H
#include <inttypes.h>
#endif
#include <mimetic/utils.h>
#include <mimetic/os/utils.h>
#include <mimetic/rfc822/fieldvalue.h>

namespace mimetic
{


/// Message-ID field value 
/// On Win32 Winsock library must be initialized before using this class.
struct MessageId: public FieldValue
{
    MessageId(uint32_t thread_id = 0 ); //line 38 corresponds to this one
    MessageId(const std::string&);
    std::string str() const;
    void set(const std::string&);
protected:
    FieldValue* clone() const;
private:
    static unsigned int ms_sequence_number;
    std::string m_msgid;
};


}

#endif

To compile the code above, I use gcc with -Wall -c -g options enabled.

My previous gcc version was gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3

What  should I do to make the code above compile ?

What may have happened after upgrading ?

Thanks.

I don't know why it stopped working, but should you be using gcc for C++ code? What happens if you use g++?

---


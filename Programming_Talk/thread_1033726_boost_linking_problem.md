---
title: "boost linking problem"
date: 2009-01-07
forum: Programming Talk
---

### Post by abacabus on 2009-01-07
I recently installed Ubuntu 8.10, and are now programming (C++) using KDevelop. A project has been created that uses CMake for building the project. I installed boost using the Synaptic package manager.

In my program I use boost::mutex, and when building I get the error "undefined reference to 'boost::lock_error::lock_error()", clearly some boost lib is missing. 
When I used boost libraries on Windows and Visual Studio, it linked the necessary lib files automatically due to #pragma directives in the boost headers. It seem not to work now for some reason.

So my question is, why does it not link automatically, and what can I do to make it link considering I am using CMake (there is a CMakeList.txt file with a TARGET_LINK_LIBRARIES entry where I added "libboost_thread", but that did not work either)?

Thanks in advance

---

### Post by dwhitney67 on 2009-01-07
Try linking with -lboost_thread-mt

If you are still having trouble, please post some code on how you are using boost::mutex.  The easiest way I have found to use it is in conjunction with boost::scoped_lock.

For example:
[php]
#include <boost/thread/mutex.hpp>

class ThreadSafeObject
{
  public:
    ...

    void access()
    {
      boost::scoped_lock scopedLock(m_mutex);

      // critical section
    }

  private:
    boost::mutex m_mutex;
};
[/php]

P.S.  I never use an IDE to develop s/w.  I use vim to create my source file(s) and Makefile.

---

### Post by jmartrican on 2009-01-07
From my Makefile.  I am ussing g++ and regular old make.

LIBS = -L/usr/lib/ -lpq -lpthread -L/usr/local/lib/ -lboost_system-gcc42-mt -L/usr/local/lib/ -lboost_thread-gcc42-mt -L/usr/local/lib/ -lboost_date_time-gcc42-mt

You probably only need:  -L/usr/local/lib/ -lboost_thread-gcc42-mt
if compiling on g++.

---

### Post by abacabus on 2009-01-08
The code I use is similar to the one you showed. I dropped KDevelop and use NetBeans instead (I am an IDE addict :-), and there I could easily add "libboost_thread" and it worked nice.

Still, why does it not link automatically? 
I think that is a very nice feature with boost... (when it works)

---

### Post by cash191 on 2009-01-08
Why Easy Forex™?Now Join for Free & Making Billionaire by happy in dollars.

>>Start trading with as little as US$100

>>Credit Card use for instant Deposit

>>Guaranteed Stop-Loss Rate

>>Freeze the Rate you see (Freeze&Trade)

>>No hidden costs, Competitive spreads

>>Special Terms for frequent traders

>>No download of software

>>Live Quotes, real-time

>>Free $50,000 Practice Account With Real-Time Charts, News & Research,One on One Trainnig.

>>Who is Domain registrant?

[http://www.verio.com/whois/whois_results.cfm?fuseaction=whois_results&domain=easy-forex.com](http://www.verio.com/whois/whois_results.cfm?fuseaction=whois_results&domain=easy-forex.com)


>>Your tracking link for promoting Easy Forex™ is:(Free Joins & Free Registrations)

[http://ads.easy-forex.com/Gateway.aspx?gid=87792](http://ads.easy-forex.com/Gateway.aspx?gid=87792)

---


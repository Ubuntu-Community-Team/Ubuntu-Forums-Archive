---
title: "C++ Socket Library"
date: 2008-10-12
forum: Programming Talk
---

### Post by dwhitney67 on 2008-10-12
About 5 years ago I developed a Socket library (in C++) that attempts to encapsulate the tediousness of setting up and using TCP/UDP sockets.  (See attachment below for the source code).

While I could not anticipate every possible application that one might create that employs the use of sockets, I have attempted to provide the basic capabilities so that one can can quickly set up an application server and/or client.

If you have any comments, please let me know.

Thank you.

P.S.  Currently the Socket library is only supported under Linux (tested only on Fedora and Ubuntu systems).  I have no plans to port it to Windoze.

---

### Post by StOoZ on 2008-10-12
downloaded , will take a look at it later. thanks ! :KS

---

### Post by sillv0r on 2008-10-12
downloaded. it looks really clean.  Thanks!

---

### Post by dwhitney67 on 2008-10-12
To simplify the management of clients that connect to a server, I have included another class object called ClientTable.  This table is (hopefully) thread-safe and can be used by a multi-threaded server application.

Now the downside... because of my laziness, I opted to employ the use of the Boost library to provide the protective mutex to guard against concurrent access to the table.  So if you do not have Boost on your system, then the new updated version of the Socket Library will not compile.

Refer to the attachment below for the new version.

---

### Post by dribeas on 2008-10-13
I have downloaded the code and gave it a fast read. The one design issue I don't really understand is why users should derive from IOBuffer for reading. It seems as if a callback mechanism should suffice.

---

### Post by dwhitney67 on 2008-10-14
> **dribeas said:**
> I have downloaded the code and gave it a fast read. The one design issue I don't really understand is why users should derive from IOBuffer for reading. It seems as if a callback mechanism should suffice.

IOBuffer is not required for reading data; it is optional to use, but handy when dealing with large messages that can (possibly) be truncated by the underlying TCP protocol, and hence not receivable using a single recv() call.

IOBuffer uses recv() to receive/collect data, and can be summoned to acquire more data when the server (or client) have been notified (via select() or other tool) that there is more data to be received.  IOBuffer will report back whether a complete message (or other condition) has occurred when a process calls getNextMsg().

It is up to those who subclass IOBuffer to add the criteria (in their implementation of the extractMsg() method) that will be used to judge whether a complete message has been received or not.  In some implementations, messages maybe fixed-length, whereas in other implementations they may be newline terminated or even contain variable-length data; in the latter case, perhaps the message header contains the expected length of the message.

Anyhow, as I stated earlier, IOBuffer is not required to be used.  If you know of a better, cleaner, way to handle the data collection and reporting, please do share it.  :)

Each time I play around implementing a client/server application,  I have been testing with short messages that are newline-terminated.  My focus in these cases was not the Socket Library, but with other libraries such as the C-library's pthread functions or with Boost's thread library.  Thus I personally haven't used IOBuffer in a long time.

---

### Post by dribeas on 2008-10-15
> **dwhitney67 said:**
> Anyhow, as I stated earlier, IOBuffer is not required to be used.  If you know of a better, cleaner, way to handle the data collection and reporting, please do share it.  :)


I have not had (and don't plan on it either) time to look deeper into the problem. To me it seems awkward using inheritance as it is the second most strong relationship when the only need is making a function call. Lets say that you make a simple change into the IOBuffer class, then all inheriting classes must be recompiled when in fact they don't even have access to anything from IOBuffer, so they don't care about the change.

Now, what other options are there. The simplest form would be providing a classical callback mechanism (as can be done in about any language):
```

class IOBufferCallback
{
public:
   virtual unsigned int extractMsg(const char* buf,
                                    const size_t bufLen,
                                    const size_t msgSize = 0) = 0;
};
class IOBuffer
{
public:
   IOBuffer(const size_t maxBufLen, const int fd, IOBufferCallback* callback);

   void setCallback( IOBufferCallback* callback ); 

private:
   IOBufferCallback* callback_;
};

class MyProcessor : public IOBufferCallback
{
// implement the callback method
};

```

Registering the callback could be done in the construction or with an specific method. If it is performed during construction, then you can use references instead of pointers.

Another option is using libraries to further ease restrictions. For example you could use boost::function to define the callback, and with boost::bing your processing class would not need to derive from the interface, not even use the same method name:

```

class IOBuffer
{
public:
   void registerCallback( boost::function<unsigned int (const char*, const size_t, const size_t )>* f );

private:
   boost::function<unsigned int (const char*, const size_t, const size_t )>* functor_;
};
class MyProcessor
{
public: 
   unsigned int readMessage(const char* buf,
                           const size_t bufLen,
                           const size_t msgSize );
};
// callback registry
IOBuffer buffer(...);
MyProcessor proc;
buffer.registerCallback( 
   new boost::function<unsigned int (const char*, const size_t, const size_t )>( 
      boost::bind( &MyProcessor::readMessage, &proc, _1, _2, _3 ) ) );

```

With the code above, memory management for the callback object would be required, I would use std::auto_ptr to hold the boost::function so that it releases itself durint IOBuffer destruction. I did not include it trying to avoid obfuscating the code anymore :)

Also you can consider different approaches, for example a boost::signal, combined with boost::bind give a slightly different approach for registration and callback:

```

class IOBuffer
{
public:
   boost::signal<unsigned int (const char*, const size_t, const size_t )>& signal() { return signal_; }

private:
   boost::signal<unsigned int (const char*, const size_t, const size_t )> signal_;
};

class MyProcessor
{
public:
   unsigned int readMessage(const char* buf,
                           const size_t bufLen,
                           const size_t msgSize );
   unsigned int read2( const size_t length,
                              const char* buffer,
                              const size_t size );
};

// register:
IOBuffer buffer(...);
MyProcessor processor;
buffer.signal().connect( boost::bind( &MyProcessor::readMessage1, &processor, _1, _2, _3 ) );

```

Note that here coupling has almost gone away: You must still provide the same method parameters and return value, but you can even change the name. With connection management you could even swap the processing from one method to another.

You can even connect the second method:
```

buffer.signal().connect( boost::bind( &MyProcessor::read2, &processor, _2, _1, _3 ) );

```

The bad part is that you have added dependencies on boost libs. To me this is not a problem, as I use boost extensively, so I already have those dependencies for other reasons.

---

### Post by dwhitney67 on 2008-10-18
Dribeas -

Thank you for your input.  I have taken your suggestion concerning IOBuffer to "improve" on the interface.

In lieu of the examples you provided, I decided to go with the callback mechanism that requires both the instance of the class implementing the callback and the address of the callback method itself.

I have also made some minor cosmetic changes to the overall library (mainly to cleanup stuff), and also I revamped some of the examples to use the changes I have made (wrt to IOBuffer).

See attachments below for the most recent release of the library.

---


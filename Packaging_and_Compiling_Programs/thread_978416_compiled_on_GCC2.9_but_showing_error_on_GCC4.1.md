---
title: "compiled on GCC2.9 but showing error on GCC4.1"
date: 2008-11-11
forum: Packaging and Compiling Programs
---

### Post by trilokas on 2008-11-11
:guitar:
this is my project of testing the code at different compilers I am a learner of testing. My master starts with this task. but he also struck with this point.

Now I clearly explain the scenario.

compiling **fib_msg.cpp** . It is including header files like** fib_msg.h, hf_logger.h, hf_looger_impl.h and hf_list.h **. I have taken preprocessor output for fib_msg.cpp. I found that all the files r included one after another. 
** step 1. In fib_msg.h **
```

#include "hf_logger.h"
#include "hf_list.h
inline
void trace(LogBuffer& msgBuffer, fib_msg_reqHeader_t& data) 
{
    msgBuffer << "cbHandle=0x";
    msgBuffer << hex << setw(8) << setfill('0') << data.cbHandle << endl; // **error : instantiated from here **
    msgBuffer << "cbCorrelator=0x";
    msgBuffer << hex << setw(8) << setfill('0') << data.cbCorrelator << endl; 
    msgBuffer << "errorReporting=";
    msgBuffer << fib_trace_value(g_fib_trace_errorReportingTypes,
                                 data.errorReporting,
                                 "unknown type");
    msgBuffer << endl;
    msgBuffer << "msgSubId=" << data.msgSubId << endl;          
}


```
[B]step 2. first is the hf_logger.h where u can see the function call on a definition of overloading operator function.
[/B]
```
class LogBuffer
{
public:

    LogBuffer(LoggerFunctor& loggerFunctor);
    ~LogBuffer();
    uint8_t*     GetStart(); 
    size_t       GetProcessedSize();
    void        Flush();
    void        SetFormat(ios::fmtflags flags, ios::fmtflags mask); 
    uint8_t     GetIndent();
    void        SetIndent(uint8_t indent);
   // Basic types
    LogBuffer& operator<<(int8_t&   data);       // a character, not a number
    LogBuffer& operator<<(const int8_t&   data); // a character, not a number
    LogBuffer& operator<<(uint8_t&  data);       // a character, not a number
    LogBuffer& operator<<(const uint8_t&  data); // a character, not a number
        // C strings
    LogBuffer& operator<<(const char* data);
    LogBuffer& operator<<(char data[]);      
    // std::string
    LogBuffer& operator<<(std::string& data);
    LogBuffer& operator<<(const std::string& data);
    
    [B]// Generic flat type this function is current issue generator  
    template <class T>
    LogBuffer& operator<<(T& data);[/B]
    
    // Single element pointer
    template <class T>
    LogBuffer& operator<<(T* & data);
    // Array
    template <class T>
    LogBuffer& operator<<(const MsgBufferArray<T>& data); 
    // Manipulators
    LogBuffer& operator<<(ios& (*fct)(ios& iosArg));
};
[B]template <class T>
void trace(LogBuffer& msgBuffer, T& data)  
{
    data.trace(msgBuffer);
}// this is the function call from which we got an error i.e. {request for member 'trace' in 'data', which is of non-class type 'std::ios_base& ()(std::ios_base&)'}
[/B]
inline
void trace(LogBuffer& msgBuffer, HF_int8_t& data) 
{
    msgBuffer << data;
}//and so on trace functions definitions..


```

**step 3.  then we have hf_logger_impl.h **
```

template <class T>
inline
LogBuffer& LogBuffer::operator<<(T& data)
{
    trace(*this, data);//  **error: instantiated from 'LogBuffer& LogBuffer::operator<<(T&) [with T = std::ios_base& ()(std::ios_base&)]'**
    return *this;
}

```

**step 4. Finally with hf_list.h**
```

#include "hf_logger.h"

template <class T, class Alloc=BufferChunkAllocator>
class MsgBufferList
{
public:
    MsgBufferList(Alloc& alloc) {init(alloc);} 
    void init(Alloc& alloc)
    {
        _n         = 0;
        _first     = 0;
        _last      = 0;
        _allocator = &alloc;
    }
    uint32_t size() {return _n;}
       
        
   [B] void trace(LogBuffer& msgBuffer)
    {
        MsgBufferListElem<T>* elemP = _first;

        for (NPF_uint32_t i = 0; (i < _n) && elemP; i++)
        {
            msgBuffer << elemP;
            elemP = elemP->_next;
        }
    }[/B]

    uint32_t              _n;
    MsgBufferListElem<T>* _first;
    MsgBufferListElem<T>* _last;
};

``` 

// So now U can understand.

---


---
title: "ACE TAO Corba Ubuntu 10.4"
date: 2010-06-09
forum: Programming Talk
---

### Post by VoidNoise on 2010-06-09
Hi,

I am having a few problems getting the example programs that come with the libTao provided in the package manager. I have used ace tao in the past with windows so have some experience with it already.

So far I have all the environment variables set, created a new projects for the "Simple Client" example. I can compile the .idl fine. When I then try to compile the client I get a linker error ...

Building target: CorbaTest
Invoking: GCC C++ Linker
g++ -Xlinker -Map -Xlinker txt.txt -Xlinker --cref -o"CorbaTest"  ./src/EchoC.o ./src/EchoS.o ./src/Echo_Client_i.o ./src/Echo_I.o ./src/client.o   -lACE -lTAO -lTAO_AnyTypeCode -lTAO_BiDirGIOP -lTAO_CodecFactory -lTAO_CosNaming -lTAO_DynamicAny -lTAO_EndpointPolicy -lTAO_DynamicInterface -lTAO_IFR_Client -lTAO_ImR_Client -lTAO_IORInterceptor -lTAO_IORTable -lTAO_Messaging -lTAO_ObjRefTemplate -lTAO_PI -lTAO_RTCORBA -lTAO_RTPortableServer -lTAO_PortableServer -lTAO_SmartProxies -lTAO_Strategies -lTAO_TypeCodeFactory -lTAO_Utils -lTAO_Valuetype -lTAO_CSD_ThreadPool -lTAO_TC -lTAO_TC_IIOP -lTAO_Compression -lTAO_ZlibCompressor
./src/EchoC.o:(.rodata._ZTV4Echo[vtable for Echo]+0xe0): undefined reference to `CORBA::Object::_refcount_value() const'
collect2: ld returned 1 exit status
make: *** [CorbaTest] Error 1

I cannot find anything online with regards to CORBA::OBbject_refcount_value() to point me in the direction of a library I might be missing. I have included all the recomended libraries from here [http://www.dre.vanderbilt.edu/~schmidt/DOC_ROOT/TAO/docs/libraries.html](http://www.dre.vanderbilt.edu/~schmidt/DOC_ROOT/TAO/docs/libraries.html) and still get the same error. This is example code that should compile and link against the supplied Tao distribution. Any ideas what I am missing? Oh and im using eclipse if it makes any difference.

Thanks :)

---


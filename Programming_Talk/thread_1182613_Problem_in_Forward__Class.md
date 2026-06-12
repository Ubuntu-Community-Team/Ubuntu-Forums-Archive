---
title: "Problem in Forward  Class"
date: 2009-06-09
forum: Programming Talk
---

### Post by rajeche on 2009-06-09
I have used a Forward Class in my Project and while I am Compiling using G++ 4.2 Version in UBUNTU 8.04.02, getting Undefined Reference.
[SIZE=1]**Master Library is DeviceManager:**[/SIZE]
**[SIZE=1]has [/SIZE]**
[SIZE=1]protocolHandler.cpp- I attached it as SngSnmpProtocolHandlercpp.txt[/SIZE]
[SIZE=1]protocolHandler.h- I attached it as SngSnmpProtocolHandlerh.txt[/SIZE]
[SIZE=1]-----------------------[/SIZE]
[SIZE=1][/SIZE] 
**Second Library which uses Master Library(DeviceManager)**
[SIZE=1]ABUCProtocolHandler.h - I attached file as SngSnmpABUCProtocolHandlerh.txt[/SIZE]
[SIZE=1]ABUCProtocolHandler.cpp - I attached file as SngSnmpABUCProtocolHandlercpp.txt[/SIZE]
 
finally these two libraries will be used in another EXE project. while compiling that project i am getting the error, the error messageas given below
 
I am also positing the Makefile which i have used in EXE project. 
Makefile name as attached is Makefile.NMSBUC.EXE
 
**Error Message:**
[SIZE=1]/usr/sngsnmp/Lib/Lib/libABUC.a(SngSnmpABUC_V1_3_0_ProtocolHandler.o):(.rodata._ZTV34SngSnmpABUC_V1_3_0_ProtocolHandler[vtable for SngSnmpABUC_V1_3_0_ProtocolHandler]+0x10): undefined reference to `SngSnmpProtocolHandler::Write(SngSnmpCommand&)'[/SIZE]
[SIZE=1]/usr/sngsnmp/Lib/Lib/libABUC.a(SngSnmpABUC_V1_3_0_ProtocolHandler.o):(.rodata._ZTV34SngSnmpABUC_V1_3_0_ProtocolHandler[vtable for SngSnmpABUC_V1_3_0_ProtocolHandler]+0x14): undefined reference to `SngSnmpProtocolHandler::Read(SngSnmpCommand&)'[/SIZE]
[SIZE=1]/usr/sngsnmp/Lib/Lib/libABUC.a(SngSnmpABUCProtocolHandler.o): In function `SngSnmpABUCProtocolHandler::~SngSnmpABUCProtocolHandler()':
SngSnmpABUCProtocolHandler.cpp:(.text+0x234): undefined reference to `SngSnmpProtocolHandler::~SngSnmpProtocolHandler()'[/SIZE]
[SIZE=1]/usr/sngsnmp/Lib/Lib/libABUC.a(SngSnmpABUCProtocolHandler.o): In function `SngSnmpABUCProtocolHandler::SngSnmpABUCProtocolHandler()':
SngSnmpABUCProtocolHandler.cpp:(.text+0x29e): undefined reference to `SngSnmpProtocolHandler::SngSnmpProtocolHandler()[/SIZE]
 
It will be appreciated if anyone helps me.. I have spent more time on time on it and am clueless.
There was no sintax or any logical problems.

---

### Post by dwhitney67 on 2009-06-09
You are having linking issues, not compiling.  Forward declarations are used to inform the compiler of the existence of a class.  These types of declarations can be used when either a reference or a pointer to a class has been declared; in such case, the compiler treats such variables as 4-byte pointers to an object, and it knows the type.

When your application gets around to actually using the reference (or pointer) variable to access member data or methods of the forwarded class, well then you need to include the header file that actually defines that class.

You will also need to ensure that the class implements each of the methods that are being called.

Lastly, you will need to link in the object file or static/shared library that contains the class' methods with your application.  Otherwise, you will get the "undefined reference" error(s).

Here is an example of a method that either 1) has not been implemented, or 2) is not being linked together with your application:
```

SngSnmpProtocolHandler::Write(SngSnmpCommand&)

```

---

### Post by dwhitney67 on 2009-06-09
Oh, and btw, some of your Makefile statements look odd, and some are just outright wrong.

Consider the following:
```

# This you will have to fix; the 'lib' portion of the name and the extension of the file name are NOT needed.
NDMIBH = libNDMibH$(shell if [ ! -f $(NUDESIGNLIBDIR)/libNDMibH.so.0 ];then echo E;fi)

LDFLAGS  += -L$(SNGSNMPLIBDIR) -L$(NUDESIGNLIBDIR)

NUDESIGN_LIBS = -lNDMibHX \
                -lNDVacm \
                -lNDNVol \
                -lNDSAgent \
                -lNDSUdp \
                -lNDSocket \
                -lNDSocketLinux \
                -lNDSnmp\
                -lNDSCryp \
                -l$(NDMIBH) \
                -lNDSys \
                -lNDSysLinux \
                -lNDSubAg


LIB_NAMES = -lSngSnmpDeviceMgr \
            -lSngSnmpDeviceFactory \
            -lABUC \
            -lNMSBUC

...

%.o:%.cpp $(StdAfx_h_DEPENDENCIES)
	$(CXX) $(CPPFLAGS) -c $<


clean:
        $(RM) $(SNGSNMPNMSBUCEXEOBJECTDIR)/*.o
        $(RM) $(SNGSNMPNMSBUCEXESRCDIR)/*.o
        $(RM) $(EXE_NAME)


#archive creation
$(EXE_NAME): $(EXE_OBJECTS)
	$(CXX) $(STRIP_FLAG) $(EXE_OBJECTS) $(LDFLAGS) $(NUDESIGN_LIBS) $(LIB_NAMES) -o $@

```
If you still have issues, you may need to swap the ordering of NUDESIGN_LIBS with LIB_NAMES.

---

### Post by rajeche on 2009-06-10
Still I am Facing the same problem even the Make file changes has been done
then i have replaced the NUDESIGN_LIB and LIB_NAMES also in the MakeFile
but still it Shows the Same error.. no changes in the error message
 
I have found the same problem complained before.. but that problem not explained well so there was no proper reply for that
here is the link for the same problem reported previously
[SIZE=2]https://bugs.launchpad.net/ubuntu/+source/gtkmm2.4/+bug/192528
[/SIZE]

---

### Post by dwhitney67 on 2009-06-10
Take a look at your Makefile; the source of the problem is undoubtedly in there.  Either you are not specifying a library, or you are, but doing so incorrectly.

I took a moment to examine your originally posted Makefile, and I must say that it appears awfully complex.  Is your application really using each of these libraries?
[LIST]
[*]libNDMibHX.so.0
[*]libNDVacm.so.0
[*]libNDNVol.so.0
[*]libNDSAgent.so.0
[*]libNDSUdp.so.0
[*]libNDSocket.so.0
[*]libNDSocketLinux.so.0
[*]libNDSnmp.so.0
[*]libNDSCryp.so.0
[*]$(NDMIBH).so.0
[*]libNDSys.so.0
[*]libNDSysLinux.so.0
[*]libNDSubAg.so.0
[/LIST]

I've worked on a project in the past that used SNMP, and if I recall correctly, only one (maybe two) libraries where needed for the SNMP stuff, and another libsocket.so (because I was developing under Solaris)... or was it libnsl.so??.

The SNMP library used was [Agent++/SNMP++]("http://www.agentpp.com/").

Anyhow, once you determine which libraries you require, the format for specifying their location is to assign one or more directory locations to LDFLAGS, and then specify your libraries.  Personally, I prefer separating the paths from the libraries.  Thus for example:
```

LDFLAGS = -L/usr/local/SNMPdir \
          -L../ProjectDir

LIBS    = -lsnmp \
          -lproject

```
Note that the specified library names do NOT have the 'lib' prefix, nor the '.so' (or '.a') extension.

If your libraries have only the '.so.0' extension, then the linker will not find the library.  You will need to create symbolic links to a similar filename, but with the '.so' extension.  So for example, if you have libsnmp.so.0, you would need to do the following:
```

ln -s libsnmp.so.0 libsnmp.so

```

---

### Post by rajeche on 2009-07-01
hi
   sorry for delayed reply, i have solved that problem trmporarily
actualy the problem is with archive, i am directly giving the object files and its started worked, i know its just a temporary fix, but when i get the time i will find the actual fix for this...
thanks for ur support
 
rajeche

---


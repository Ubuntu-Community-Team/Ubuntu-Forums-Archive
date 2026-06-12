---
title: "Make problems?"
date: 2012-09-10
forum: Packaging and Compiling Programs
---

### Post by Marawaa on 2012-09-10
I'm having problems with an 'install.sh' intended to automate the compiling of plugins, found by checking out this svn rep: 

```

svn co http://nwn.virusman.ru/svn/nwnx2-linux/trunk/ .

```I have posted more information on their website but I'm not sure if there's much activity there, some of the threads don't ever seem to find a conclusion. I'm on Ubuntu 12.04 with GCC 4.6.3. I run svn checkout in the directory home/upunpu/Desktop/test, then ./install.sh

```
 make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/functions' 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o C2DA.o C2DA.cpp 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CNWSScriptVarTable.o CNWSScriptVarTable.cpp 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CExoLinkedList.o CExoLinkedList.cpp 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CItemRepository.o CItemRepository.cpp 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CExoLocString.o CExoLocString.cpp 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o FunctionHooks.o FunctionHooks.cpp 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXFunction.o NWNXFunction.cpp 
NWNXFunction.cpp: In member function ‘char* CNWNXFunction::GetGroundHeight(char*)’: 
NWNXFunction.cpp:380:53: warning: format ‘%x’ expects argument of type  ‘unsigned int*’, but argument 3 has type ‘dword* {aka long unsigned  int*}’ [-Wformat] 
NWNXFunction.cpp: In member function ‘void CNWNXFunction::GetIsWalkableHL(char*)’: 
NWNXFunction.cpp:402:53: warning: format ‘%x’ expects argument of type  ‘unsigned int*’, but argument 3 has type ‘dword* {aka long unsigned  int*}’ [-Wformat] 
NWNXFunction.cpp: In member function ‘void CNWNXFunction::ActUseItem(char*)’: 
NWNXFunction.cpp:547:84: warning: format ‘%x’ expects argument of type  ‘unsigned int*’, but argument 3 has type ‘dword* {aka long unsigned  int*}’ [-Wformat] 
NWNXFunction.cpp:547:84: warning: format ‘%x’ expects argument of type  ‘unsigned int*’, but argument 4 has type ‘dword* {aka long unsigned  int*}’ [-Wformat] 
NWNXFunction.cpp:547:84: warning: format ‘%d’ expects argument of type  ‘int*’, but argument 8 has type ‘dword* {aka long unsigned int*}’  [-Wformat] 
NWNXFunction.cpp: In member function ‘void CNWNXFunction::GetPCPort(char*)’: 
NWNXFunction.cpp:560:28: warning: format ‘%d’ expects argument of type  ‘int’, but argument 3 has type ‘dword {aka long unsigned int}’  [-Wformat] 
NWNXFunction.cpp: In member function ‘char* CNWNXFunction::GetNextLocalVariable(char*)’: 
NWNXFunction.cpp:601:95: warning: format ‘%d’ expects argument of type  ‘int’, but argument 5 has type ‘dword {aka long unsigned int}’  [-Wformat] 
NWNXFunction.cpp:621:98: warning: format ‘%d’ expects argument of type  ‘int’, but argument 5 has type ‘dword {aka long unsigned int}’  [-Wformat] 
NWNXFunction.cpp: In member function ‘void CNWNXFunction::GetItemCount_Ext(char*)’: 
NWNXFunction.cpp:635:29: warning: format ‘%d’ expects argument of type  ‘int’, but argument 3 has type ‘dword {aka long unsigned int}’  [-Wformat] 
NWNXFunction.cpp: In member function ‘void CNWNXFunction::ObjDump(char*)’: 
NWNXFunction.cpp:672:43: warning: '0' flag used with ‘%p’ gnu_printf format [-Wformat] 
NWNXFunction.cpp:676:60: warning: '0' flag used with ‘%p’ gnu_printf format [-Wformat] 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-functions.o plugin-functions.cpp 
g++ -m32 -w -fPIC -shared -W -Wall  -o nwnx_functions.so C2DA.o  CNWSScriptVarTable.o CExoLinkedList.o CItemRepository.o CExoLocString.o  FunctionHooks.o NWNXFunction.o plugin-functions.o  
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/functions' 
make -C plugins/hashset PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -m32  -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -m32  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-m32 -w -fPIC -shared -W -Wall  " 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/hashset' 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXHashSet.o NWNXHashSet.cpp 
NWNXHashSet.cpp: In member function ‘bool CNWNXHashSet::ParseParam(char*, char*, std::string&, std::string*, std::string*)’: 
NWNXHashSet.cpp:161:35: warning: format ‘%x’ expects argument of type  ‘unsigned int’, but argument 3 has type ‘long unsigned int’ [-Wformat] 
NWNXHashSet.cpp: In member function ‘char* CNWNXHashSet::Lookup(char*, char*)’: 
NWNXHashSet.cpp:250:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:255:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp: In member function ‘char* CNWNXHashSet::Valid(char*, char*)’: 
NWNXHashSet.cpp:265:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:269:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:272:9: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp: In member function ‘char* CNWNXHashSet::Exists(char*, char*)’: 
NWNXHashSet.cpp:279:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:284:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:287:9: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp: In member function ‘char* CNWNXHashSet::GetSize(char*, char*)’: 
NWNXHashSet.cpp:296:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:301:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp: In member function ‘char* CNWNXHashSet::GetFirstKey(char*, char*)’: 
NWNXHashSet.cpp:313:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:318:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:325:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp: In member function ‘char* CNWNXHashSet::GetNextKey(char*, char*)’: 
NWNXHashSet.cpp:334:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:339:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:344:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp: In member function ‘char* CNWNXHashSet::GetCurrentKey(char*, char*)’: 
NWNXHashSet.cpp:353:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:358:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:363:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp: In member function ‘char* CNWNXHashSet::GetNthKey(char*, char*)’: 
NWNXHashSet.cpp:377:9: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp: In member function ‘char* CNWNXHashSet::HasNext(char*, char*)’: 
NWNXHashSet.cpp:384:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:389:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:396:10: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
NWNXHashSet.cpp:398:9: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-hashset.o plugin-hashset.cpp 
g++ -m32 -w -fPIC -shared -W -Wall  -o nwnx_hashset.so NWNXHashSet.o plugin-hashset.o  
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/hashset' 
make -C plugins/mnx PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -m32  -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -m32  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-m32 -w -fPIC -shared -W -Wall  " 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx' 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXmnx.o NWNXmnx.cpp 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-mnx.o plugin-mnx.cpp 
g++ -m32 -w -fPIC -shared -W -Wall  -o nwnx_mnx.so NWNXmnx.o plugin-mnx.o  
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx' 
make -C plugins/names PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -m32  -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -m32  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-m32 -w -fPIC -shared -W -Wall  " 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names' 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CCustomNames.o CCustomNames.cpp 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o HookFunc.o HookFunc.cpp 
HookFunc.cpp: In function ‘char* GetServerFuncName(dword)’: 
HookFunc.cpp:227:56: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:228:41: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:229:41: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:230:56: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:231:56: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:232:56: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:233:71: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:234:56: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:235:41: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:237:54: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:238:41: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:239:56: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:240:56: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:241:56: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:243:55: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:245:54: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:246:41: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:247:41: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:261:9: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp: In function ‘void SendDataHookProc(void*, int, int, int, char*, int)’: 
HookFunc.cpp:311:90: warning: format ‘%lX’ expects argument of type  ‘long unsigned int’, but argument 3 has type ‘unsigned char***’  [-Wformat] 
HookFunc.cpp:311:90: warning: format ‘%lX’ expects argument of type  ‘long unsigned int’, but argument 4 has type ‘int’ [-Wformat] 
HookFunc.cpp:311:90: warning: format ‘%lX’ expects argument of type  ‘long unsigned int’, but argument 5 has type ‘int’ [-Wformat] 
HookFunc.cpp:311:90: warning: format ‘%lX’ expects argument of type  ‘long unsigned int’, but argument 6 has type ‘int’ [-Wformat] 
HookFunc.cpp: In function ‘int GetNameHookProc(void*, int, char*, int)’: 
HookFunc.cpp:704:15: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:710:38: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:711:20: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:715:15: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:719:15: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp:730:17: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings] 
HookFunc.cpp: Assembler messages: 
HookFunc.cpp:319: Warning: indirect jmp without `*' 
HookFunc.cpp:756: Warning: indirect call without `*' 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXNames.o NWNXNames.cpp 
NWNXNames.cpp: In member function ‘void CNWNXNames::SetDynamicName(char*)’: 
NWNXNames.cpp:133:43: warning: format ‘%x’ expects argument of type  ‘unsigned int*’, but argument 3 has type ‘dword* {aka long unsigned  int*}’ [-Wformat] 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-names.o plugin-names.cpp 
g++ -m32 -w -fPIC -shared -W -Wall  -shared -o nwnx_names.so  CCustomNames.o HookFunc.o NWNXNames.o plugin-names.o ../../NWNXBase.o  ../../gline.o   
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names' 
make -C plugins/odmbc PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -m32  -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -m32  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-m32 -w -fPIC -shared -W -Wall  " 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc' 
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o HookSCORCO.o HookSCORCO.cpp 
In file included from NWNXodbc.h:29:0, 
                 from HookSCORCO.cpp:30: 
mysql.h:27:25: fatal error: mysql/mysql.h: No such file or directory 
compilation terminated. 
make[1]: *** [HookSCORCO.o] Error 1 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc' 
make: *** [plugins/odmbc] Error 2 
for i in plugins/areas plugins/chat plugins/defenses plugins/events  plugins/fixes plugins/funcs plugins/functions plugins/hashset  plugins/mnx plugins/names plugins/odmbc plugins/profiler plugins/reset  plugins/resman plugins/spells plugins/structs plugins/system plugins/tmi  plugins/tweaks plugins/visibility plugins/weapons ; do make -C $i  clean; done 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/areas' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/areas' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/chat' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/chat' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/defenses' 
/bin/rm -f *.o */*.o *.so 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/defenses' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/events' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/events' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/fixes' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/fixes' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/funcs' 
/bin/rm -f *.o *.so funcs/*/*.o 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/funcs' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/functions' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/functions' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/hashset' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/hashset' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/profiler' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/profiler' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/reset' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/reset' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/resman' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/resman' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/spells' 
/bin/rm -f *.o */*.o *.so 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/spells' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/structs' 
/bin/rm -f *.o */*.o *.so 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/structs' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/system' 
/bin/rm -f *.o */*.o *.so 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/system' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tmi' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tmi' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tweaks' 
/bin/rm -f *.o */*.o *.so 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tweaks' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/visibility' 
/bin/rm -f *.o *.so *~ 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/visibility' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/weapons' 
/bin/rm -f *.o */*.o *.so 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/weapons' 
/bin/rm -f *.o *.so lib/*.o *~ 
for i in plugins/areas plugins/chat plugins/defenses plugins/events  plugins/fixes plugins/funcs plugins/functions plugins/hashset  plugins/mnx plugins/names plugins/odmbc plugins/profiler plugins/reset  plugins/resman plugins/spells plugins/structs plugins/system plugins/tmi  plugins/tweaks plugins/visibility plugins/weapons ; do make -C $i  distclean; done 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/areas' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/areas' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/chat' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/chat' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/defenses' 
/bin/rm -f *.o */*.o *.so 
/bin/rm -f .depend DefensesStrCmds.h DefensesObjCmds.h 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/defenses' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/events' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/events' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/fixes' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/fixes' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/funcs' 
/bin/rm -f *.o *.so funcs/*/*.o 
/bin/rm -f .depend FuncsStrCmds.h FuncsObjCmds.h 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/funcs' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/functions' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/functions' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/hashset' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/hashset' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/profiler' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/profiler' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/reset' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/reset' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/resman' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/resman' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/spells' 
/bin/rm -f *.o */*.o *.so 
/bin/rm -f .depend SpellsStrCmds.h SpellsObjCmds.h 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/spells' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/structs' 
/bin/rm -f *.o */*.o *.so 
/bin/rm -f .depend StructsStrCmds.h StructsObjCmds.h 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/structs' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/system' 
/bin/rm -f *.o */*.o *.so 
/bin/rm -f .depend SystemStrCmds.h SystemObjCmds.h 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/system' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tmi' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tmi' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tweaks' 
/bin/rm -f *.o */*.o *.so 
/bin/rm -f .depend TweaksStrCmds.h TweaksObjCmds.h 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tweaks' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/visibility' 
/bin/rm -f *.o *.so *~ 
/bin/rm -f Makefile 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/visibility' 
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/weapons' 
/bin/rm -f *.o */*.o *.so 
/bin/rm -f .depend WeaponsStrCmds.h WeaponsObjCmds.h 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/weapons' 
/bin/rm -f Makefile config.h config.status config.cache config.log *.o *.so lib/*.o *~ 
NWNX has been compiled. Look in the 'compiled' directory for the  libraries - these should be copied into your NWN directory. Change  NWNX2.ini and nwnstartup.sh to match your server's settings. 
```I hope this is a general problem that can be fixed and not something specific to this code. It doesn't require anything else to set up, so hopefully someone could try the same steps if they have some time. Thanks! :(

[http://www.nwnx.org/phpBB2/viewtopic.php?p=15816#15816](http://www.nwnx.org/phpBB2/viewtopic.php?p=15816#15816)

This Ubuntu install is literally a day old, and was made only for this program so it's baffling to me as I don't understand much about Linux in general.

---

### Post by sandyd on 2012-09-10
missing mysql dev libs
```

sudo apt-get install  mysql-devel
```

---

### Post by Marawaa on 2012-09-10
Thanks for the INCREDIBLY quick reply. However when I try to run that command I get this:

```

upunpu@ubuntu:~$ sudo apt-get install  mysql-devel
[sudo] password for upunpu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mysql-devel

```edit:
Did some Googling and found a thread which offered
```
 apt-get install mysql-client mysql-server 
```as a possible fix.

So I ran that and am going through the installation.

edit: seems obvious now I think about it but that's the server package and not the development, which I assume is what I need?

---

### Post by Cheesemill on 2012-09-10
I think the package you are after is libmysql++-dev

---

### Post by steeldriver on 2012-09-10
it seems to be libmysqlclient-dev on my 12.04 system

```
$ apt-file search -x '\/mysql\.h$'
libmysqlclient-dev: /usr/include/mysql/mysql.h
pike7.8-mysql: /usr/lib/pike7.8/7.4/include/mysql.h

```

---

### Post by Marawaa on 2012-09-10
Going to try it out now, I got libmysql++-dev and libmysqlclient-dev reports as installed too.

edit: It gets further than it did before, but there are still multiple errors. It also doesn't compile every plugin - there are 8 plugins still not compiled, and I think it's because there isn't a 'make' run for each of them, but that's just a guess.

```

NWNXHashSet.cpp:325:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::GetNextKey(char*, char*)&#8217;:
NWNXHashSet.cpp:334:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:339:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:344:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::GetCurrentKey(char*, char*)&#8217;:
NWNXHashSet.cpp:353:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:358:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:363:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::GetNthKey(char*, char*)&#8217;:
NWNXHashSet.cpp:377:9: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::HasNext(char*, char*)&#8217;:
NWNXHashSet.cpp:384:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:389:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:396:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:398:9: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-hashset.o plugin-hashset.cpp
g++ -m32 -w -fPIC -shared -W -Wall  -o nwnx_hashset.so NWNXHashSet.o plugin-hashset.o 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/hashset'
make -C plugins/mnx PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-m32 -w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx'
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXmnx.o NWNXmnx.cpp
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-mnx.o plugin-mnx.cpp
g++ -m32 -w -fPIC -shared -W -Wall  -o nwnx_mnx.so NWNXmnx.o plugin-mnx.o 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx'
make -C plugins/names PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-m32 -w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names'
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CCustomNames.o CCustomNames.cpp
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o HookFunc.o HookFunc.cpp
HookFunc.cpp: In function &#8216;char* GetServerFuncName(dword)&#8217;:
HookFunc.cpp:227:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:228:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:229:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:230:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:231:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:232:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:233:71: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:234:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:235:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:237:54: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:238:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:239:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:240:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:241:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:243:55: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:245:54: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:246:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:247:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:261:9: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp: In function &#8216;void SendDataHookProc(void*, int, int, int, char*, int)&#8217;:
HookFunc.cpp:311:90: warning: format &#8216;%lX&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 3 has type &#8216;unsigned char***&#8217; [-Wformat]
HookFunc.cpp:311:90: warning: format &#8216;%lX&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 4 has type &#8216;int&#8217; [-Wformat]
HookFunc.cpp:311:90: warning: format &#8216;%lX&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
HookFunc.cpp:311:90: warning: format &#8216;%lX&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 6 has type &#8216;int&#8217; [-Wformat]
HookFunc.cpp: In function &#8216;int GetNameHookProc(void*, int, char*, int)&#8217;:
HookFunc.cpp:704:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:710:38: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:711:20: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:715:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:719:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:730:17: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp: Assembler messages:
HookFunc.cpp:319: Warning: indirect jmp without `*'
HookFunc.cpp:756: Warning: indirect call without `*'
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXNames.o NWNXNames.cpp
NWNXNames.cpp: In member function &#8216;void CNWNXNames::SetDynamicName(char*)&#8217;:
NWNXNames.cpp:133:43: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int*&#8217;, but argument 3 has type &#8216;dword* {aka long unsigned int*}&#8217; [-Wformat]
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-names.o plugin-names.cpp
g++ -m32 -w -fPIC -shared -W -Wall  -shared -o nwnx_names.so CCustomNames.o HookFunc.o NWNXNames.o plugin-names.o ../../NWNXBase.o ../../gline.o  
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names'
make -C plugins/odmbc PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-m32 -w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc'
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o HookSCORCO.o HookSCORCO.cpp
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CExoString.o CExoString.cpp
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o ObjectStorage.o ObjectStorage.cpp
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXodbc.o NWNXodbc.cpp
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o mysql.o mysql.cpp
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-odbc.o plugin-odbc.cpp
g++ -m32 -w -fPIC -shared -W -Wall  -o nwnx_odbc.so HookSCORCO.o CExoString.o ObjectStorage.o NWNXodbc.o mysql.o plugin-odbc.o -L/usr/lib/mysql -lmysqlclient -lz
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc'
make -C plugins/profiler PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-m32 -w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/profiler'
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o hash.o hash.cpp
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o HookRunScript.o HookRunScript.cpp
HookRunScript.cpp: Assembler messages:
HookRunScript.cpp:301: Warning: indirect call without `*'
HookRunScript.cpp:318: Warning: indirect call without `*'
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXProfiler.o NWNXProfiler.cpp
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-profiler.o plugin-profiler.cpp
g++ -m32 -w -fPIC -shared -W -Wall  -o nwnx_profiler.so hash.o HookRunScript.o NWNXProfiler.o plugin-profiler.o 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/profiler'
make -C plugins/reset PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-m32 -w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/reset'
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXReset.o NWNXReset.cpp
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-reset.o plugin-reset.cpp
g++ -m32 -w -fPIC -shared -W -Wall  -o nwnx_resetplugin.so NWNXReset.o plugin-reset.o  
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/reset'
make -C plugins/resman PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-m32 -w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/resman'
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o HookDemandRes.o HookDemandRes.cpp
In file included from /usr/include/c++/4.6/ext/hash_map:61:0,
                 from NWNXResMan.h:27,
                 from HookDemandRes.cpp:31:
/usr/include/c++/4.6/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated. [-Wcpp]
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NwnDefines.o NwnDefines.cpp
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXResMan.o NWNXResMan.cpp
In file included from /usr/include/c++/4.6/ext/hash_map:61:0,
                 from NWNXResMan.h:27,
                 from NWNXResMan.cpp:21:
/usr/include/c++/4.6/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated. [-Wcpp]
g++  -mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-resman.o plugin-resman.cpp
In file included from /usr/include/c++/4.6/ext/hash_map:61:0,
                 from NWNXResMan.h:27,
                 from plugin-resman.cpp:21:
/usr/include/c++/4.6/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated. [-Wcpp]
g++ -m32 -w -fPIC -shared -W -Wall  -o nwnx_resman.so HookDemandRes.o NwnDefines.o NWNXResMan.o plugin-resman.o 
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/resman'
make -C plugins/spells PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -m32 -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-m32 -w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/spells'
gcc -mtune=i386 -pipe -g -O2 -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include -mtune=i386 -pipe  -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include  -c -o funcs/f_GetSpellOption.o funcs/f_GetSpellOption.c
gcc -mtune=i386 -pipe -g -O2 -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include -mtune=i386 -pipe  -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include  -c -o funcs/f_IntToObject.o funcs/f_IntToObject.c
gcc -mtune=i386 -pipe -g -O2 -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include -mtune=i386 -pipe  -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include  -c -o funcs/f_SetSpellOption.o funcs/f_SetSpellOption.c
gcc -mtune=i386 -pipe -g -O2 -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include -mtune=i386 -pipe  -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include  -c -o hooks/h_ComputeSpellRange.o hooks/h_ComputeSpellRange.c
hooks/h_ComputeSpellRange.c: In function &#8216;Hook_GetSpellRange&#8217;:
hooks/h_ComputeSpellRange.c:36:10: error: variable &#8216;no_bonus&#8217; set but not used [-Werror=unused-but-set-variable]
cc1: all warnings being treated as errors
make[1]: *** [hooks/h_ComputeSpellRange.o] Error 1
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/spells'
make: *** [plugins/spells] Error 2
for i in plugins/areas plugins/chat plugins/defenses plugins/events plugins/fixes plugins/funcs plugins/functions plugins/hashset plugins/mnx plugins/names plugins/odmbc plugins/profiler plugins/reset plugins/resman plugins/spells plugins/structs plugins/system plugins/tmi plugins/tweaks plugins/visibility plugins/weapons ; do make -C $i clean; done
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/areas'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/areas'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/chat'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/chat'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/defenses'
/bin/rm -f *.o */*.o *.so
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/defenses'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/events'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/events'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/fixes'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/fixes'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/funcs'
/bin/rm -f *.o *.so funcs/*/*.o
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/funcs'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/functions'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/functions'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/hashset'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/hashset'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/profiler'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/profiler'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/reset'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/reset'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/resman'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/resman'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/spells'
/bin/rm -f *.o */*.o *.so
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/spells'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/structs'
/bin/rm -f *.o */*.o *.so
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/structs'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/system'
/bin/rm -f *.o */*.o *.so
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/system'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tmi'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tmi'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tweaks'
/bin/rm -f *.o */*.o *.so
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tweaks'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/visibility'
/bin/rm -f *.o *.so *~
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/visibility'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/weapons'
/bin/rm -f *.o */*.o *.so
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/weapons'
/bin/rm -f *.o *.so lib/*.o *~
for i in plugins/areas plugins/chat plugins/defenses plugins/events plugins/fixes plugins/funcs plugins/functions plugins/hashset plugins/mnx plugins/names plugins/odmbc plugins/profiler plugins/reset plugins/resman plugins/spells plugins/structs plugins/system plugins/tmi plugins/tweaks plugins/visibility plugins/weapons ; do make -C $i distclean; done
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/areas'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/areas'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/chat'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/chat'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/defenses'
/bin/rm -f *.o */*.o *.so
/bin/rm -f .depend DefensesStrCmds.h DefensesObjCmds.h
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/defenses'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/events'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/events'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/fixes'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/fixes'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/funcs'
/bin/rm -f *.o *.so funcs/*/*.o
/bin/rm -f .depend FuncsStrCmds.h FuncsObjCmds.h
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/funcs'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/functions'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/functions'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/hashset'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/hashset'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/mnx'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/names'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/odmbc'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/profiler'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/profiler'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/reset'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/reset'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/resman'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/resman'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/spells'
/bin/rm -f *.o */*.o *.so
/bin/rm -f .depend SpellsStrCmds.h SpellsObjCmds.h
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/spells'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/structs'
/bin/rm -f *.o */*.o *.so
/bin/rm -f .depend StructsStrCmds.h StructsObjCmds.h
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/structs'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/system'
/bin/rm -f *.o */*.o *.so
/bin/rm -f .depend SystemStrCmds.h SystemObjCmds.h
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/system'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tmi'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tmi'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tweaks'
/bin/rm -f *.o */*.o *.so
/bin/rm -f .depend TweaksStrCmds.h TweaksObjCmds.h
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/tweaks'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/visibility'
/bin/rm -f *.o *.so *~
/bin/rm -f Makefile
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/visibility'
make[1]: Entering directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/weapons'
/bin/rm -f *.o */*.o *.so
/bin/rm -f .depend WeaponsStrCmds.h WeaponsObjCmds.h
make[1]: Leaving directory `/home/upunpu/Desktop/Untitled Folder/nwnx2-linux/trunk/plugins/weapons'
/bin/rm -f Makefile config.h config.status config.cache config.log *.o *.so lib/*.o *~

```

---

### Post by Marawaa on 2012-09-11
Many thanks for helping me get this far! I think the issue is either something wrong on my end or an actual error in the spells plugin, guessing from the Terminal result. I'm going to remove the spells plugin and try again. If that doesn't work, I'll try run without -Werror, but it's baffling to me, as there's been no reports on the site about issues compiling lately.

---

### Post by oldos2er on 2012-09-11
Moved to Packaging and Compiling Programs.

---

### Post by Marawaa on 2012-09-11
Yeah, still no luck. Removing the Spells plugin code did nothing. :(

I don't know where to go from this point, I think I'll have to give it a rethink if I can't set this server up as I initially planned. Thanks for the help and suggestions, though. :)

edit: here's my last compile attempt

```

NWNXFuncsExt.cpp:80:35: warning: zero-length gnu_printf format string [-Wformat-zero-length]
NWNXFuncsExt.cpp:80:35: warning: zero-length gnu_printf format string [-Wformat-zero-length]
NWNXFuncsExt.cpp: In member function &#8216;void CNWNXFuncsExt::Set_IsGenericTrigger(CGameObject*, char*)&#8217;:
NWNXFuncsExt.cpp:146:35: warning: zero-length gnu_printf format string [-Wformat-zero-length]
NWNXFuncsExt.cpp:146:35: warning: zero-length gnu_printf format string [-Wformat-zero-length]
NWNXFuncsExt.cpp: In member function &#8216;void CNWNXFuncsExt::Set_IsAreaTransition(CGameObject*, char*)&#8217;:
NWNXFuncsExt.cpp:160:35: warning: zero-length gnu_printf format string [-Wformat-zero-length]
NWNXFuncsExt.cpp:160:35: warning: zero-length gnu_printf format string [-Wformat-zero-length]
gcc  -mtune=i386 -pipe  -Wall -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include  -c -o plugin-funcsext.o plugin-funcsext.cpp
gcc -w -fPIC -shared -rdynamic -o nwnx_funcsext.so FunctionHooks.o NWNXFuncsExt.o plugin-funcsext.o -L/usr/local/lib -lm -lz
make[1]: Leaving directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/funcsext'
make -C plugins/functions PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/functions'
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o C2DA.o C2DA.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CNWSScriptVarTable.o CNWSScriptVarTable.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CExoLinkedList.o CExoLinkedList.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CItemRepository.o CItemRepository.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CExoLocString.o CExoLocString.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o FunctionHooks.o FunctionHooks.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXFunction.o NWNXFunction.cpp
NWNXFunction.cpp: In constructor &#8216;CNWNXFunction::CNWNXFunction()&#8217;:
NWNXFunction.cpp:34:12: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXFunction.cpp: In member function &#8216;char* CNWNXFunction::GetGroundHeight(char*)&#8217;:
NWNXFunction.cpp:380:53: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int*&#8217;, but argument 3 has type &#8216;dword* {aka long unsigned int*}&#8217; [-Wformat]
NWNXFunction.cpp: In member function &#8216;void CNWNXFunction::GetIsWalkableHL(char*)&#8217;:
NWNXFunction.cpp:402:53: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int*&#8217;, but argument 3 has type &#8216;dword* {aka long unsigned int*}&#8217; [-Wformat]
NWNXFunction.cpp: In member function &#8216;void CNWNXFunction::ActUseItem(char*)&#8217;:
NWNXFunction.cpp:547:84: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int*&#8217;, but argument 3 has type &#8216;dword* {aka long unsigned int*}&#8217; [-Wformat]
NWNXFunction.cpp:547:84: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int*&#8217;, but argument 4 has type &#8216;dword* {aka long unsigned int*}&#8217; [-Wformat]
NWNXFunction.cpp:547:84: warning: format &#8216;%d&#8217; expects argument of type &#8216;int*&#8217;, but argument 8 has type &#8216;dword* {aka long unsigned int*}&#8217; [-Wformat]
NWNXFunction.cpp: In member function &#8216;void CNWNXFunction::GetPCPort(char*)&#8217;:
NWNXFunction.cpp:560:28: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;dword {aka long unsigned int}&#8217; [-Wformat]
NWNXFunction.cpp: In member function &#8216;char* CNWNXFunction::GetNextLocalVariable(char*)&#8217;:
NWNXFunction.cpp:601:95: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 5 has type &#8216;dword {aka long unsigned int}&#8217; [-Wformat]
NWNXFunction.cpp:621:98: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 5 has type &#8216;dword {aka long unsigned int}&#8217; [-Wformat]
NWNXFunction.cpp: In member function &#8216;void CNWNXFunction::GetItemCount_Ext(char*)&#8217;:
NWNXFunction.cpp:635:29: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;dword {aka long unsigned int}&#8217; [-Wformat]
NWNXFunction.cpp: In member function &#8216;void CNWNXFunction::ObjDump(char*)&#8217;:
NWNXFunction.cpp:672:43: warning: '0' flag used with &#8216;%p&#8217; gnu_printf format [-Wformat]
NWNXFunction.cpp:676:60: warning: '0' flag used with &#8216;%p&#8217; gnu_printf format [-Wformat]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-functions.o plugin-functions.cpp
g++ -w -fPIC -shared -W -Wall  -o nwnx_functions.so C2DA.o CNWSScriptVarTable.o CExoLinkedList.o CItemRepository.o CExoLocString.o FunctionHooks.o NWNXFunction.o plugin-functions.o 
make[1]: Leaving directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/functions'
make -C plugins/hashset PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/hashset'
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXHashSet.o NWNXHashSet.cpp
NWNXHashSet.cpp: In constructor &#8216;CNWNXHashSet::CNWNXHashSet()&#8217;:
NWNXHashSet.cpp:32:12: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::Lookup(char*, char*)&#8217;:
NWNXHashSet.cpp:250:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:255:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::Valid(char*, char*)&#8217;:
NWNXHashSet.cpp:265:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:269:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:272:9: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::Exists(char*, char*)&#8217;:
NWNXHashSet.cpp:279:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:284:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:287:9: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::GetSize(char*, char*)&#8217;:
NWNXHashSet.cpp:296:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:301:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::GetFirstKey(char*, char*)&#8217;:
NWNXHashSet.cpp:313:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:318:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:325:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::GetNextKey(char*, char*)&#8217;:
NWNXHashSet.cpp:334:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:339:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:344:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::GetCurrentKey(char*, char*)&#8217;:
NWNXHashSet.cpp:353:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:358:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:363:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::GetNthKey(char*, char*)&#8217;:
NWNXHashSet.cpp:377:9: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp: In member function &#8216;char* CNWNXHashSet::HasNext(char*, char*)&#8217;:
NWNXHashSet.cpp:384:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:389:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:396:10: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXHashSet.cpp:398:9: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-hashset.o plugin-hashset.cpp
g++ -w -fPIC -shared -W -Wall  -o nwnx_hashset.so NWNXHashSet.o plugin-hashset.o 
make[1]: Leaving directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/hashset'
make -C plugins/mnx PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/mnx'
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXmnx.o NWNXmnx.cpp
NWNXmnx.cpp: In constructor &#8216;CNWNXmnx::CNWNXmnx()&#8217;:
NWNXmnx.cpp:27:12: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-mnx.o plugin-mnx.cpp
g++ -w -fPIC -shared -W -Wall  -o nwnx_mnx.so NWNXmnx.o plugin-mnx.o 
make[1]: Leaving directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/mnx'
make -C plugins/names PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/names'
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o CCustomNames.o CCustomNames.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o HookFunc.o HookFunc.cpp
HookFunc.cpp: In function &#8216;char* GetServerFuncName(dword)&#8217;:
HookFunc.cpp:227:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:228:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:229:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:230:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:231:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:232:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:233:71: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:234:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:235:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:237:54: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:238:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:239:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:240:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:241:56: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:243:55: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:245:54: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:246:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:247:41: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:261:9: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp: In function &#8216;int GetNameHookProc(void*, int, char*, int)&#8217;:
HookFunc.cpp:704:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:710:38: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:711:20: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:715:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:719:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:730:17: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXNames.o NWNXNames.cpp
NWNXNames.cpp: In constructor &#8216;CNWNXNames::CNWNXNames()&#8217;:
NWNXNames.cpp:36:12: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-names.o plugin-names.cpp
g++ -w -fPIC -shared -W -Wall  -shared -o nwnx_names.so CCustomNames.o HookFunc.o NWNXNames.o plugin-names.o ../../NWNXBase.o ../../gline.o  
make[1]: Leaving directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/names'
make -C plugins/odmbc PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/odmbc'
rm *.o
rm: cannot remove `*.o': No such file or directory
make[1]: [all] Error 1 (ignored)
make SQLITE_SUPPORT=1 nwnx_odbc_sqlite_dynamic.so nwnx_odbc_sqlite_static.so
make[2]: Entering directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/odmbc'
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../.. -DSQLITE_SUPPORT  -c -o HookSCORCO.o HookSCORCO.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../.. -DSQLITE_SUPPORT  -c -o CExoString.o CExoString.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../.. -DSQLITE_SUPPORT  -c -o ObjectStorage.o ObjectStorage.cpp
ObjectStorage.cpp: In function &#8216;char* SaveObject(dword, int&)&#8217;:
ObjectStorage.cpp:121:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
ObjectStorage.cpp:126:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
ObjectStorage.cpp:131:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../.. -DSQLITE_SUPPORT  -c -o NWNXodbc.o NWNXodbc.cpp
NWNXodbc.cpp: In constructor &#8216;CNWNXODBC::CNWNXODBC()&#8217;:
NWNXodbc.cpp:37:12: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXodbc.cpp: In member function &#8216;virtual char* CNWNXODBC::OnRequest(char*, char*, char*)&#8217;:
NWNXodbc.cpp:193:62: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXodbc.cpp:193:62: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXodbc.cpp:193:62: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXodbc.cpp:211:66: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXodbc.cpp:211:66: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXodbc.cpp:211:66: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXodbc.cpp: In member function &#8216;virtual long unsigned int CNWNXODBC::OnRequestObject(char*, char*)&#8217;:
NWNXodbc.cpp:228:9: warning: converting to non-pointer type &#8216;long unsigned int&#8217; from NULL [-Wconversion-null]
NWNXodbc.cpp: In member function &#8216;unsigned char* CNWNXODBC::ReadSCO(char*, char*, char*, int*, int*)&#8217;:
NWNXodbc.cpp:397:2: warning: converting to non-pointer type &#8216;int&#8217; from NULL [-Wconversion-null]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../.. -DSQLITE_SUPPORT  -c -o plugin-odbc.o plugin-odbc.cpp
plugin-odbc.cpp:35:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
plugin-odbc.cpp:35:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
plugin-odbc.cpp:35:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
plugin-odbc.cpp:35:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
plugin-odbc.cpp:35:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
plugin-odbc.cpp:35:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../.. -DSQLITE_SUPPORT  -c -o sqlite.o sqlite.cpp
sqlite.cpp: In member function &#8216;virtual BOOL CSQLite::Connect()&#8217;:
sqlite.cpp:39:28: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
g++ -w -fPIC -shared -W -Wall  -o nwnx_odbc_sqlite_dynamic.so HookSCORCO.o CExoString.o ObjectStorage.o NWNXodbc.o plugin-odbc.o sqlite.o -lz -lsqlite3
g++ -w -fPIC -shared -W -Wall  -o nwnx_odbc_sqlite_static.so HookSCORCO.o CExoString.o ObjectStorage.o NWNXodbc.o plugin-odbc.o sqlite.o /usr/lib/i386-linux-gnu/libsqlite3.a -lz
make[2]: Leaving directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/odmbc'
make[1]: Leaving directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/odmbc'
make -C plugins/profiler PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/profiler'
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o hash.o hash.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o HookRunScript.o HookRunScript.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXProfiler.o NWNXProfiler.cpp
NWNXProfiler.cpp: In constructor &#8216;CNWNXProfiler::CNWNXProfiler()&#8217;:
NWNXProfiler.cpp:36:12: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-profiler.o plugin-profiler.cpp
g++ -w -fPIC -shared -W -Wall  -o nwnx_profiler.so hash.o HookRunScript.o NWNXProfiler.o plugin-profiler.o 
make[1]: Leaving directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/profiler'
make -C plugins/reset PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/reset'
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXReset.o NWNXReset.cpp
NWNXReset.cpp: In constructor &#8216;CNWNXReset::CNWNXReset()&#8217;:
NWNXReset.cpp:35:12: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-reset.o plugin-reset.cpp
g++ -w -fPIC -shared -W -Wall  -o nwnx_reset.so NWNXReset.o plugin-reset.o  
make[1]: Leaving directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/reset'
make -C plugins/resman PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/resman'
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o HookDemandRes.o HookDemandRes.cpp
In file included from /usr/include/c++/4.6/ext/hash_map:61:0,
                 from NWNXResMan.h:27,
                 from HookDemandRes.cpp:31:
/usr/include/c++/4.6/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated. [-Wcpp]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NwnDefines.o NwnDefines.cpp
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o NWNXResMan.o NWNXResMan.cpp
In file included from /usr/include/c++/4.6/ext/hash_map:61:0,
                 from NWNXResMan.h:27,
                 from NWNXResMan.cpp:21:
/usr/include/c++/4.6/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated. [-Wcpp]
NWNXResMan.cpp: In constructor &#8216;CNWNXResMan::CNWNXResMan()&#8217;:
NWNXResMan.cpp:32:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
NWNXResMan.cpp: In member function &#8216;char* CNWNXResMan::DemandRes(CExoResMan*, CResStruct*, char*, NwnResType)&#8217;:
NWNXResMan.cpp:89:5: warning: converting to non-pointer type &#8216;int&#8217; from NULL [-Wconversion-null]
g++  -mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H -I../..  -c -o plugin-resman.o plugin-resman.cpp
In file included from /usr/include/c++/4.6/ext/hash_map:61:0,
                 from NWNXResMan.h:27,
                 from plugin-resman.cpp:21:
/usr/include/c++/4.6/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated. [-Wcpp]
plugin-resman.cpp:36:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
plugin-resman.cpp:36:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
plugin-resman.cpp:36:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
plugin-resman.cpp:36:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
plugin-resman.cpp:36:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
plugin-resman.cpp:36:1: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
g++ -w -fPIC -shared -W -Wall  -o nwnx_resman.so HookDemandRes.o NwnDefines.o NWNXResMan.o plugin-resman.o 
make[1]: Leaving directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/resman'
make -C plugins/spells PLUGIN_CFLAGS="-mtune=i386 -pipe -g -O2 -Iinclude -DHAVE_CONFIG_H" PLUGIN_CPPFLAGS="-mtune=i386 -pipe  -Iinclude -DHAVE_CONFIG_H" PLUGIN_LFLAGS="-w -fPIC -shared -W -Wall "
make[1]: Entering directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/spells'
gcc -mtune=i386 -pipe -g -O2 -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include -mtune=i386 -pipe  -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include  -c -o funcs/f_GetSpellOption.o funcs/f_GetSpellOption.c
gcc -mtune=i386 -pipe -g -O2 -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include -mtune=i386 -pipe  -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include  -c -o funcs/f_IntToObject.o funcs/f_IntToObject.c
gcc -mtune=i386 -pipe -g -O2 -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include -mtune=i386 -pipe  -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include  -c -o funcs/f_SetSpellOption.o funcs/f_SetSpellOption.c
gcc -mtune=i386 -pipe -g -O2 -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include -mtune=i386 -pipe  -Wall -Werror -D_REENTRANT -D_THREAD_SAFE -I. -I.. -I../.. -I ../../include -I/usr/local/include  -c -o hooks/h_ComputeSpellRange.o hooks/h_ComputeSpellRange.c
hooks/h_ComputeSpellRange.c: In function &#8216;Hook_GetSpellRange&#8217;:
hooks/h_ComputeSpellRange.c:36:10: error: variable &#8216;no_bonus&#8217; set but not used [-Werror=unused-but-set-variable]
cc1: all warnings being treated as errors
make[1]: *** [hooks/h_ComputeSpellRange.o] Error 1
make[1]: Leaving directory `/home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe/NWNX-nwnx2-linux-e0583fe/plugins/spells'
make: *** [plugins/spells] Error 2

```

Could these problems be caused by running a too new version of gcc or similar?

---

### Post by Marawaa on 2012-09-11
```

-- Build files have been written to: /home/upunpu/Desktop/NWNX-nwnx2-linux-e0583fe
upunpu@ubuntu:~/Desktop/NWNX-nwnx2-linux-e0583fe$ make
[  3%] Built target nwnx2
[  3%] Generating TweaksObjCmds.h
/bin/sh: 1: ../../NWNX-nwnx2-linux-e0583fe/plugins/gperf_gen.sh: Permission denied
make[2]: *** [plugins/tweaks/TweaksObjCmds.h] Error 126
make[1]: *** [plugins/tweaks/CMakeFiles/tweaks.dir/all] Error 2
make: *** [all] Error 2

```I installed CMAKE and tried to compile from here
```

http://ci.swordcoast.net/job/nwnx2-linux/

```but it still throws errors. I can't find any results for the 'make error 2' anywhere.

---

### Post by Marawaa on 2012-09-12
Since I still haven't managed to get this working, would it be too much to ask if someone could compile some custom plugin code for me? I can provide all of the code which should just work with the NWNX ./install.sh, except in my case. :)

---

### Post by opensshd on 2012-09-12
I see you're getting a permission error there...

[http://nwn.virusman.ru/svn/nwnx2-linux/trunk/README](http://nwn.virusman.ru/svn/nwnx2-linux/trunk/README)

seems there is an autoconf script and then a ./configure command you need to execute before make install.

Also, make sure you clean out the "stuff" of failed attempts before reattempting the compilation. Thus, keep the source code around and redecompress (that should be a word) it for every build attempt.

---

### Post by Marawaa on 2012-09-13
Thanks, I'm going to give that a try now.

I was trying to follow this page's instructions:
```
 http://www.nwnx.org/index.php?id=doc_nwnx_linux 
```And couldn't find anything updated.

edit: So far, so good. ./configure with prefix directory of the downloaded files appears fine!

```

checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking size of void *... 4
checking for a sed that does not truncate output... /bin/sed
checking whether the C compiler accepts the -mtune=i386 flag... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for bzero... yes
checking for getspnam... yes
checking for inflateEnd in -lz... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating plugins/areas/Makefile
config.status: creating plugins/chat/Makefile
config.status: creating plugins/defenses/Makefile
config.status: creating plugins/events/Makefile
config.status: creating plugins/fixes/Makefile
config.status: creating plugins/funcs/Makefile
config.status: creating plugins/functions/Makefile
config.status: creating plugins/hashset/Makefile
config.status: creating plugins/mnx/Makefile
config.status: creating plugins/names/Makefile
config.status: creating plugins/odmbc/Makefile
config.status: creating plugins/profiler/Makefile
config.status: creating plugins/reset/Makefile
config.status: creating plugins/resman/Makefile
config.status: creating plugins/ruby/Makefile
config.status: creating plugins/spells/Makefile
config.status: creating plugins/structs/Makefile
config.status: creating plugins/system/Makefile
config.status: creating plugins/tmi/Makefile
config.status: creating plugins/tweaks/Makefile
config.status: creating plugins/visibility/Makefile
config.status: creating plugins/weapons/Makefile
config.status: creating config.h

```[B]

edit: Spoke too soon. Same problem. Still only compiles up to "Resman", and still throws armfuls of errors and warnings at me. Thanks for trying, though. I'm going to try and individually "make" each one and see if it's still just as broken.

update: Same problem. I tried compiling "nwnx_weapons" just because it was the last plugin in the list: its compiled size is 1.6MB, when the precompiled builds are less than 100KB. It crashes the server instantly with a seg fault when I try to access any of the functions in it, so it definitely doesn't compile properly.
[/B]

---

### Post by Marawaa on 2012-09-13
This might sound dumb: is there a way to stop feedback of errors like this? I assumed it would be in the install.sh but it isn't. **edit: done with -werror in the makefile**

```

cc1: all warnings being treated as errors
make[1]: *** [hooks/h_ComputeSpellRange.o] Error 1
make[1]: Leaving directory `/home/upunpu/Desktop/untitfold/plugins/spells'
make: *** [plugins/spells] Error 2

```I've got no other ideas so I'm just going to hide the errors and see if it continues compiling after ResMan/Spells.

I think I really am going to have to ask someone else to compile the edited ones for me. I'm almost completely sure I have everything installed, there's no errors to do with that, most of the errors are these:

```

HookFunc.cpp:715:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:719:15: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]
HookFunc.cpp:730:17: warning: deprecated conversion from string constant to &#8216;char*&#8217; [-Wwrite-strings]

HookFunc.cpp: Assembler messages:
HookFunc.cpp:319: Warning: indirect jmp without `*'
HookFunc.cpp:756: Warning: indirect call without `*'

HookFunc.cpp:311:90: warning: format &#8216;%lX&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 4 has type &#8216;int&#8217; [-Wformat]
HookFunc.cpp:311:90: warning: format &#8216;%lX&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
HookFunc.cpp:311:90: warning: format &#8216;%lX&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 6 has type &#8216;int&#8217; [-Wformat]

 from NWNXResMan.cpp:21:
/usr/include/c++/4.6/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated. [-Wcpp]


```

---

### Post by Marawaa on 2012-09-14
Removing -Werror now lets every plugin compile, but the sizes are still WAY off. Going to try them anyway.

edit: And it still throws lots of errors. I'm not concerned with the Ruby/SQL ones, but Spells and Events throw errors, and it still SegFaults.

```

* Searching for signatures...
* Loading modules...
NWNX Lua Initialized
LUA plugin registered.
FIXES plugin registered.
VISIBILITY plugin registered.
ERROR: ODMBC_SQLITE: OnCreate() failed.
SYSTEM plugin registered.
TWEAKS plugin registered.
EXTEND plugin registered.
DMACTIONS plugin registered.
PROFILER plugin registered.
ERROR: dlopen: ./nwnx_ruby.so: libruby.so.1.9: cannot open shared object file: No such file or directory
HAKS plugin registered.
RESETPLUGIN plugin registered.
STRUCTS plugin registered.
OPTIMIZATIONS plugin registered.
FUNCSEXT plugin registered.
CHAT plugin registered.
ERROR: ODBC: OnCreate() failed.
HASHSET plugin registered.
ERROR: EVENTS: OnCreate() failed.
ERROR: dlopen: ./nwnx_spells.so: ./nwnx_spells.so: undefined symbol: Hook_SPR_Caster
AREAS plugin registered.
TMI plugin registered.
NAMES plugin registered.
WEAPONS plugin registered.
RESMAN plugin registered.
FUNCS plugin registered.
RESET plugin registered.
MNX plugin registered.
FUNCTIONS plugin registered.
DEFENSES plugin registered.
* NWNX2 activated.
Neverwinter Nights Server
Build:8109
Copyright BioWare Corp 1998-2004

Server: Loading...
Server: Running...

Server: Loading module "module000".Segmentation fault (core dumped)

```

I might just try reinstalling Ubuntu and the packages. I assume the svn source works for everyone else but not me. Odd since this install is only a little older than this thread. :(

---

### Post by Marawaa on 2012-09-15
Even reinstalling didn't work. I would have concluded that the svn files are at fault but it appears to work for others, or that's my assumption at least. I now have two Ubuntu installations and neither work.

```

autoconf is already the newest version. 
g++ is already the newest version. 
gcc is already the newest version. 
make is already the newest version. 
zlib1g-dev is already the newest version. 
build-essential is already the newest version. 
libmysqlclient-dev is already the newest version. 
libmysqlclient18 is already the newest version. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 

```[http://www.nwnx.org/phpBB2/viewtopic.php?p=15852#15852](http://www.nwnx.org/phpBB2/viewtopic.php?p=15852#15852)

---

### Post by Marawaa on 2012-09-16
edit: I think I  can conclude that the issue lies with version 12.04 of Ubuntu or a newer  version of the packages on it. Two fresh installs, almost the same  installs with whichever version differences are on the respective  flavors, compile works correctly on Debian but segfaults on Ubuntu. Many, /many/ thanks for the suggestions or I would have given up a long time ago.

---


---
title: "Please help out with this qmetatype.h error"
date: 2011-07-25
forum: Packaging and Compiling Programs
---

### Post by rickrvo on 2011-07-25
Hi,

I'm trying to get passed this error but still no luck...

 	 		 			 			 				 ```
../../../necessitas/android-ndk-r5c/platforms/android-3/arch-arm/usr/include/sys/limits.h:172:1:  warning: "_POSIX_CHOWN_RESTRICTED" redefined
In file included from /usr/include/unistd.h:203,
                 from  ../../../necessitas/android-ndk-r5c/sources/cxx-stl/gnu-libstdc++/libs/armeabi/include/bits/gthr-default.h:55,
                 from ../../../necessitas/android-ndk-r5c/sources/cxx-stl/gnu-libstdc++/libs/armeabi/include/bits/gthr.h:162,
                 from ../../../necessitas/android-ndk-r5c/sources/cxx-stl/gnu-libstdc++/include/ext/atomicity.h:34,
                 from ../../../necessitas/android-ndk-r5c/sources/cxx-stl/gnu-libstdc++/include/bits/basic_string.h:41,
                 from ../../../necessitas/android-ndk-r5c/sources/cxx-stl/gnu-libstdc++/include/string:53,
                 from ../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qstring.h:54,
                 from ../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qobject.h:48,
                 from ../../../necessitas/Android/Qt/4762/armeabi/include/QtGui/qwidget.h:46,
                 from ../../../necessitas/Android/Qt/4762/armeabi/include/QtGui/QWidget:1,
                 from ../staticlib/include/lock_widget.h:30,
                 from ../staticlib/src/lock_widget.cpp:25:
/usr/include/bits/posix_opt.h:51:1: warning: this is the location of the previous definition
In file included from ../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qvariant.h:48,
                 from ../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/QVariant:1,
                 from ../staticlib/include/isd_base.h:27,
                 from ../staticlib/include/local_system.h:31,
                 from ../staticlib/src/lock_widget.cpp:26:
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:53:2:  error: #error qmetatype.h must be included before any header file that  defines Bool
In file included from ../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qvariant.h:48,
                 from ../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/QVariant:1,
                 from ../staticlib/include/isd_base.h:27,
                 from ../staticlib/include/local_system.h:31,
                 from ../staticlib/src/lock_widget.cpp:26:
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:66: error: expected identifier before 'int'
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:66: error: expected '}' before 'int'
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:66: error: expected unqualified-id before '=' token
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:129: error: expected declaration before '}' token
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:110:  warning: 'void registerStreamOperators(const char*, void  (*)(QDataStream&, const void*), void (*)(QDataStream&, void*))'  declared 'static' but never defined
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:112:  warning: 'void registerStreamOperators(int, void (*)(QDataStream&,  const void*), void (*)(QDataStream&, void*))' declared 'static' but  never defined
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:115:  warning: 'int registerType(const char*, void (*)(void*), void*  (*)(const void*))' declared 'static' but never defined
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:117:  warning: 'int registerTypedef(const char*, int)' declared 'static' but  never defined
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:118:  warning: 'int type(const char*)' declared 'static' but never defined
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:119:  warning: 'const char* typeName(int)' declared 'static' but never  defined
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:120:  warning: 'bool isRegistered(int)' declared 'static' but never defined
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:121:  warning: 'void* construct(int, const void*)' declared 'static' but  never defined
make[1]: Leaving directory `/home/hormonde/uni_net-student-android-tablet/uni_net-project/staticlib-build-android'
make: Leaving directory `/home/hormonde/uni_net-student-android-tablet/uni_net-project/staticlib-build-android'
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:122:  warning: 'void destroy(int, void*)' declared 'static' but never defined
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:123:  warning: 'void unregisterType(const char*)' declared 'static' but never  defined
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:126:  warning: 'bool save(QDataStream&, int, const void*)' declared  'static' but never defined
../../../necessitas/Android/Qt/4762/armeabi/include/QtCore/qmetatype.h:127:  warning: 'bool load(QDataStream&, int, void*)' declared 'static'  but never defined
make[1]: *** [release/lock_widget.o] Error 1
make: *** [release] Error 2
The process "/usr/bin/make" exited with code 2.
Error while building project staticlib (target: Android)
When executing build step 'Make'
```



 	
 
 i have this include paths in the .pro file:

   	Qt Code:             [RIGHT]  
             [/RIGHT]
         
 	
[LIST=1]
[*]INCLUDEPATH [COLOR=#000000]=[/COLOR] ..[COLOR=#000000]/[/COLOR]nsserver \
[*]        ..[COLOR=#000000]/[/COLOR]plugins[COLOR=#000000]/[/COLOR]attendees[COLOR=#000000]/[/COLOR]include \
[*]        include[COLOR=#000000]/[/COLOR]rfb \
[*]        x11[COLOR=#000000]/[/COLOR]rfb \
[*]        include \
[*]        ..[COLOR=#000000]/[/COLOR]..[COLOR=#000000]/[/COLOR]uni_net[COLOR=#000000]/[/COLOR]include[COLOR=#000000]/[/COLOR]openssl \
[*]        [COLOR=#000000]/[/COLOR]usr[COLOR=#000000]/[/COLOR]include \
[*]        [COLOR=#000000]/[/COLOR]home[COLOR=#000000]/[/COLOR]hormonde[COLOR=#000000]/[/COLOR]necessitas[COLOR=#000000]/[/COLOR]android[COLOR=#000000]-[/COLOR]ndk[COLOR=#000000]-[/COLOR]r5c[COLOR=#000000]/[/COLOR]platforms[COLOR=#000000]/[/COLOR]android[COLOR=#000000]-[/COLOR][COLOR=#0000dd]3[/COLOR][COLOR=#000000]/[/COLOR]arch[COLOR=#000000]-[/COLOR]arm[COLOR=#000000]/[/COLOR]usr[COLOR=#000000]/[/COLOR]include \
[/LIST]
          [RIGHT][COLOR=#aaa][/COLOR][/RIGHT]
 
  if I change the order of the last 2 lines, the error becomes this:

 	 		 			 			 				```
In file included from ../staticlib/include/local_system.h:31,
                 from ../staticlib/src/messagebox.cpp:27:
../staticlib/include/isd_base.h:62: warning: type qualifiers ignored on function return type
../staticlib/include/isd_base.h:72: error: expected unqualified-id before '__extension__'
../staticlib/include/isd_base.h:72: error: expected unqualified-id before ')' token
../staticlib/include/isd_base.h:81: warning: type qualifiers ignored on function return type
../staticlib/include/isd_base.h:88: warning: type qualifiers ignored on function return type
make[1]: Leaving directory `/home/hormonde/uni_net-student-android-tablet/uni_net-project/staticlib-build-android'
make[1]: *** [release/messagebox.o] Error 1
make: Leaving directory `/home/hormonde/uni_net-student-android-tablet/uni_net-project/staticlib-build-android'
make: *** [release] Error 2
The process "/usr/bin/make" exited with code 2.
Error while building project staticlib (target: Android)
When executing build step 'Make' 			 		
```

---

### Post by rickrvo on 2011-08-02
Can anyone help me on how to proceed?

thx

---


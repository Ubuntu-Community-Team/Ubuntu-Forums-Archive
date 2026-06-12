---
title: "how to recompile c++ files under SSH"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by warmsuns on 2013-04-17
&#65321;was asked to recompile a c++ fileswhich has the connection with database and use some files and libraries other place
the following is what I tried and the reply :
Can someone tell me what I should do with this?
are there someone who lives in Montreal ,maybe I can get help for what I am doing:)
Thanks a lot!

[dumbo.encs.concordia.ca:cplus] 86 => g++ -I /usr/local/mysql/include -L /usr/local/mysql/lib Key_imp_ext.cpp key_class.c catalog.c stack.c -o test
In file included from /usr/lib/gcc/i386-redhat-linux/4.1.2/../../../../include/c++/4.1.2/backward/iostream.h:31,
                 from Key_imp_ext.cpp:29:
/usr/lib/gcc/i386-redhat-linux/4.1.2/../../../../include/c++/4.1.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
In file included from Key_imp_ext.cpp:32:
key_class.h:16:19: error: mysql.h: No such file or directory
Key_imp_ext.cpp:35: error: âMYSQLâ does not name a type
Key_imp_ext.cpp:36: error: expected initializer before â*â token
Key_imp_ext.cpp:37: error: âMYSQL_ROWâ does not name a type
Key_imp_ext.cpp: In function âint main(int, char**)â:
Key_imp_ext.cpp:102: error: âmy_connectionâ was not declared in this scope
Key_imp_ext.cpp:102: error: âmysql_initâ was not declared in this scope
Key_imp_ext.cpp:103: error: âCLIENT_FOUND_ROWSâ was not declared in this scope
Key_imp_ext.cpp:103: error: âmysql_real_connectâ was not declared in this scope
Key_imp_ext.cpp:152: error: âmysql_closeâ was not declared in this scope
In file included from /usr/lib/gcc/i386-redhat-linux/4.1.2/../../../../include/c++/4.1.2/backward/fstream.h:31,
                 from key_class.h:14,
                 from key_class.c:9:
/usr/lib/gcc/i386-redhat-linux/4.1.2/../../../../include/c++/4.1.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
In file included from key_class.c:9:
key_class.h:16:19: error: mysql.h: No such file or directory
key_class.c:14: error: âMYSQLâ does not name a type
key_class.c:15: error: expected initializer before â*â token
key_class.c:16: error: âMYSQL_ROWâ does not name a type
key_class.c: In member function âint Keyword::isKey(char*)â:
key_class.c:52: error: âmy_connectionâ was not declared in this scope
key_class.c:52: error: âmysql_queryâ was not declared in this scope
key_class.c:54: error: âmysql_errorâ was not declared in this scope
key_class.c:57: error: âresultâ was not declared in this scope
key_class.c:57: error: âmysql_store_resultâ was not declared in this scope
key_class.c:60: error: âmysql_num_rowsâ was not declared in this scope
key_class.c:62: error: âmysql_free_resultâ was not declared in this scope
key_class.c:66: error: âmysql_free_resultâ was not declared in this scope
key_class.c:72: error: âmysql_errnoâ was not declared in this scope
key_class.c:73: error: âmysql_errorâ was not declared in this scope
key_class.c:77: error: âmysql_free_resultâ was not declared in this scope
key_class.c: In member function âvoid Keyword::storetodb()â:
key_class.c:272: error: âmy_connectionâ was not declared in this scope
key_class.c:272: error: âmysql_queryâ was not declared in this scope
In file included from catalog.c:5:
catalog.h:11:19: error: mysql.h: No such file or directory
catalog.c:7: error: âMYSQLâ does not name a type
catalog.c:8: error: expected constructor, destructor, or type conversion before â*â token
catalog.c:9: error: âMYSQL_ROWâ does not name a type
catalog.c: In member function âvoid Level_0::list_all_level_0()â:
catalog.c:25: error: âmy_connectionâ was not declared in this scope
catalog.c:25: error: âmysql_queryâ was not declared in this scope
catalog.c:27: error: âmysql_errorâ was not declared in this scope
catalog.c:30: error: âresultâ was not declared in this scope
catalog.c:30: error: âmysql_store_resultâ was not declared in this scope
catalog.c:34: error: ârowâ was not declared in this scope
catalog.c:34: error: âmysql_fetch_rowâ was not declared in this scope
catalog.c:38: error: âmysql_errnoâ was not declared in this scope
catalog.c:39: error: âmysql_errorâ was not declared in this scope
catalog.c:43: error: âmysql_free_resultâ was not declared in this scope
catalog.c: In member function âint Level_0::isLevel_0(char*)â:
catalog.c:56: error: âmy_connectionâ was not declared in this scope
catalog.c:56: error: âmysql_queryâ was not declared in this scope
catalog.c:58: error: âmysql_errorâ was not declared in this scope
catalog.c:61: error: âresultâ was not declared in this scope
catalog.c:61: error: âmysql_store_resultâ was not declared in this scope
catalog.c:64: error: âmysql_num_rowsâ was not declared in this scope
catalog.c:65: error: âmysql_free_resultâ was not declared in this scope
catalog.c:68: error: âmysql_free_resultâ was not declared in this scope
catalog.c:74: error: âmysql_errnoâ was not declared in this scope
catalog.c:75: error: âmysql_errorâ was not declared in this scope
catalog.c: In member function âvoid Level_1::RetrieveLevel_1(char*)â:
catalog.c:99: error: âmy_connectionâ was not declared in this scope
catalog.c:99: error: âmysql_queryâ was not declared in this scope
catalog.c:101: error: âmysql_errorâ was not declared in this scope
catalog.c:104: error: âresultâ was not declared in this scope
catalog.c:104: error: âmysql_store_resultâ was not declared in this scope
catalog.c:108: error: ârowâ was not declared in this scope
catalog.c:108: error: âmysql_fetch_rowâ was not declared in this scope
catalog.c:112: error: âmysql_free_resultâ was not declared in this scope
catalog.c:116: error: âmysql_errnoâ was not declared in this scope
catalog.c:117: error: âmysql_errorâ was not declared in this scope
catalog.c: In member function âvoid Level_1::list_all_level_1(char*)â:
catalog.c:146: error: âmy_connectionâ was not declared in this scope
catalog.c:146: error: âmysql_queryâ was not declared in this scope
catalog.c:148: error: âmysql_errorâ was not declared in this scope
catalog.c:151: error: âresultâ was not declared in this scope
catalog.c:151: error: âmysql_store_resultâ was not declared in this scope
catalog.c:156: error: ârowâ was not declared in this scope
catalog.c:156: error: âmysql_fetch_rowâ was not declared in this scope
catalog.c:161: error: âmysql_errnoâ was not declared in this scope
catalog.c:162: error: âmysql_errorâ was not declared in this scope
catalog.c:166: error: âmysql_free_resultâ was not declared in this scope
catalog.c: In member function âint Level_1::isLevel_1(char*)â:
catalog.c:181: error: âmy_connectionâ was not declared in this scope
catalog.c:181: error: âmysql_queryâ was not declared in this scope
catalog.c:183: error: âmysql_errorâ was not declared in this scope
catalog.c:186: error: âresultâ was not declared in this scope
catalog.c:186: error: âmysql_store_resultâ was not declared in this scope
catalog.c:189: error: âmysql_num_rowsâ was not declared in this scope
catalog.c:190: error: âmysql_free_resultâ was not declared in this scope
catalog.c:193: error: âmysql_free_resultâ was not declared in this scope
catalog.c:199: error: âmysql_errnoâ was not declared in this scope
catalog.c:200: error: âmysql_errorâ was not declared in this scope
catalog.c: In member function âchar* Level_1::get_subject_0(char*)â:
catalog.c:216: error: âmy_connectionâ was not declared in this scope
catalog.c:216: error: âmysql_queryâ was not declared in this scope
catalog.c:218: error: âmysql_errorâ was not declared in this scope
catalog.c:221: error: âresultâ was not declared in this scope
catalog.c:221: error: âmysql_store_resultâ was not declared in this scope
catalog.c:227: error: ârowâ was not declared in this scope
catalog.c:227: error: âmysql_fetch_rowâ was not declared in this scope
catalog.c:236: error: âmysql_free_resultâ was not declared in this scope
catalog.c:241: error: âmysql_errnoâ was not declared in this scope
catalog.c:242: error: âmysql_errorâ was not declared in this scope
catalog.c:246: error: âmysql_free_resultâ was not declared in this scope
catalog.c: In member function âvoid Level_2::RetrieveLevel_2(char*)â:
catalog.c:269: error: âmy_connectionâ was not declared in this scope
catalog.c:269: error: âmysql_queryâ was not declared in this scope
catalog.c:271: error: âmysql_errorâ was not declared in this scope
catalog.c:274: error: âresultâ was not declared in this scope
catalog.c:274: error: âmysql_store_resultâ was not declared in this scope
catalog.c:278: error: ârowâ was not declared in this scope
catalog.c:278: error: âmysql_fetch_rowâ was not declared in this scope
catalog.c:283: error: âmysql_free_resultâ was not declared in this scope
catalog.c:287: error: âmysql_errnoâ was not declared in this scope
catalog.c:288: error: âmysql_errorâ was not declared in this scope
catalog.c: In member function âvoid Level_2::list_all_level_2(char*, char*)â:
catalog.c:317: error: âmy_connectionâ was not declared in this scope
catalog.c:317: error: âmysql_queryâ was not declared in this scope
catalog.c:320: error: âmysql_errorâ was not declared in this scope
catalog.c:323: error: âresultâ was not declared in this scope
catalog.c:323: error: âmysql_store_resultâ was not declared in this scope
catalog.c:328: error: ârowâ was not declared in this scope
catalog.c:328: error: âmysql_fetch_rowâ was not declared in this scope
catalog.c:333: error: âmysql_errnoâ was not declared in this scope
catalog.c:334: error: âmysql_errorâ was not declared in this scope
catalog.c:338: error: âmysql_free_resultâ was not declared in this scope
catalog.c: In member function âint Level_2::isLevel_2(char*)â:
catalog.c:361: error: âmy_connectionâ was not declared in this scope
catalog.c:361: error: âmysql_queryâ was not declared in this scope
catalog.c:367: error: âmysql_errorâ was not declared in this scope
catalog.c:370: error: âresultâ was not declared in this scope
catalog.c:370: error: âmysql_store_resultâ was not declared in this scope
catalog.c:373: error: âmysql_num_rowsâ was not declared in this scope
catalog.c:374: error: âmysql_free_resultâ was not declared in this scope
catalog.c:377: error: âmysql_free_resultâ was not declared in this scope
catalog.c:383: error: âmysql_errnoâ was not declared in this scope
catalog.c:384: error: âmysql_errorâ was not declared in this scope
catalog.c: In member function âchar* Level_2::get_subject_1(char*)â:
catalog.c:401: error: âmy_connectionâ was not declared in this scope
catalog.c:401: error: âmysql_queryâ was not declared in this scope
catalog.c:403: error: âmysql_errorâ was not declared in this scope
catalog.c:406: error: âresultâ was not declared in this scope
catalog.c:406: error: âmysql_store_resultâ was not declared in this scope
catalog.c:412: error: ârowâ was not declared in this scope
catalog.c:412: error: âmysql_fetch_rowâ was not declared in this scope
catalog.c:421: error: âmysql_free_resultâ was not declared in this scope
catalog.c:426: error: âmysql_errnoâ was not declared in this scope
catalog.c:427: error: âmysql_errorâ was not declared in this scope
catalog.c:431: error: âmysql_free_resultâ was not declared in this scope
In file included from stack.h:12,
                 from stack.c:9:
catalog.h:11:19: error: mysql.h: No such file or directory
In file included from /usr/lib/gcc/i386-redhat-linux/4.1.2/../../../../include/c++/4.1.2/backward/iostream.h:31,
                 from stack.c:10:
/usr/lib/gcc/i386-redhat-linux/4.1.2/../../../../include/c++/4.1.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
stack.c:14: error: âMYSQLâ does not name a type
stack.c:15: error: expected initializer before â*â token
stack.c:16: error: âMYSQL_ROWâ does not name a type
stack.c: In member function âvoid stack_array_0::get_all(char*)â:
stack.c:146: error: âmy_connectionâ was not declared in this scope
stack.c:146: error: âmysql_queryâ was not declared in this scope
stack.c:151: error: âresultâ was not declared in this scope
stack.c:151: error: âmysql_store_resultâ was not declared in this scope
stack.c:153: error: ârowâ was not declared in this scope
stack.c:153: error: âmysql_fetch_rowâ was not declared in this scope
stack.c:158: error: âmysql_errnoâ was not declared in this scope
stack.c:160: error: âmysql_free_resultâ was not declared in this scope
stack.c:164: error: âmysql_free_resultâ was not declared in this scope
stack.c: In member function âvoid stack_array_0::store_all(char*)â:
stack.c:182: error: âmy_connectionâ was not declared in this scope
stack.c:182: error: âmysql_queryâ was not declared in this scope
stack.c:187: error: âresultâ was not declared in this scope
stack.c:187: error: âmysql_store_resultâ was not declared in this scope
stack.c:189: error: ârowâ was not declared in this scope
stack.c:189: error: âmysql_fetch_rowâ was not declared in this scope
stack.c:192: error: âmysql_errnoâ was not declared in this scope
stack.c:194: error: âmysql_free_resultâ was not declared in this scope
stack.c:198: error: âmysql_free_resultâ was not declared in this scope
stack.c: In member function âvoid stack_array_1::get_all(char*)â:
stack.c:331: error: âmy_connectionâ was not declared in this scope
stack.c:331: error: âmysql_queryâ was not declared in this scope
stack.c:336: error: âresultâ was not declared in this scope
stack.c:336: error: âmysql_store_resultâ was not declared in this scope
stack.c:338: error: âmysql_num_rowsâ was not declared in this scope
stack.c:340: error: ârowâ was not declared in this scope
stack.c:340: error: âmysql_fetch_rowâ was not declared in this scope
stack.c:348: error: âmysql_errnoâ was not declared in this scope
stack.c:350: error: âmysql_free_resultâ was not declared in this scope
stack.c:354: error: âmysql_free_resultâ was not declared in this scope
stack.c: In member function âvoid stack_array_1::store_all(char*)â:
stack.c:374: error: âmy_connectionâ was not declared in this scope
stack.c:374: error: âmysql_queryâ was not declared in this scope
stack.c:379: error: âresultâ was not declared in this scope
stack.c:379: error: âmysql_store_resultâ was not declared in this scope
stack.c:381: error: ârowâ was not declared in this scope
stack.c:381: error: âmysql_fetch_rowâ was not declared in this scope
stack.c:384: error: âmysql_errnoâ was not declared in this scope
stack.c:386: error: âmysql_free_resultâ was not declared in this scope
stack.c:390: error: âmysql_free_resultâ was not declared in this scope
stack.c: In member function âvoid stack_array_2::get_all(char*)â:
stack.c:522: error: âmy_connectionâ was not declared in this scope
stack.c:522: error: âmysql_queryâ was not declared in this scope
stack.c:527: error: âresultâ was not declared in this scope
stack.c:527: error: âmysql_store_resultâ was not declared in this scope
stack.c:529: error: âmysql_num_rowsâ was not declared in this scope
stack.c:531: error: ârowâ was not declared in this scope
stack.c:531: error: âmysql_fetch_rowâ was not declared in this scope
stack.c:539: error: âmysql_errnoâ was not declared in this scope
stack.c:541: error: âmysql_free_resultâ was not declared in this scope
stack.c:545: error: âmysql_free_resultâ was not declared in this scope
stack.c: In member function âvoid stack_array_2::store_all(char*)â:
stack.c:565: error: âmy_connectionâ was not declared in this scope
stack.c:565: error: âmysql_queryâ was not declared in this scope
stack.c:570: error: âresultâ was not declared in this scope
stack.c:570: error: âmysql_store_resultâ was not declared in this scope
stack.c:572: error: ârowâ was not declared in this scope
stack.c:572: error: âmysql_fetch_rowâ was not declared in this scope
stack.c:575: error: âmysql_errnoâ was not declared in this scope
stack.c:577: error: âmysql_free_resultâ was not declared in this scope
stack.c:581: error: âmysql_free_resultâ was not declared in this scope
[dumbo.encs.concordia.ca:cplus] 87 =

---

### Post by TheFu on 2013-04-17
Are you certain that all the required dependencies have been met?
Is there a makefile available? 
Is there an autoconf file available?
Is there an INSTALL file available?

It is extremely unlikely that ssh has anything at all to do with this specific issue. Whatever the normal CLI method used to build the software is what you should be using.

From the error messages, it appears that dependencies have not been met. I suspect strongly there is a README or INSTALL file provided with the code you are attempting to build which outlines those dependencies to some level.  There is a difference between installing mysql and installing mysql development headers and libraries, as an example.

Sorry that I don't have an exact solution, more information is needed. If we understood your level of expertise with C/C++, then we'd have a better chance of helping at the correct level too.

---

### Post by steeldriver on 2013-04-17
IF this is Ubuntu then I'd suspect you are missing the libmysqlclient-dev package (and possibly others) ... BUT it looks like you are in some kind of RedHat toolchain?

---


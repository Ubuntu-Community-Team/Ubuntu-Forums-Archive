---
title: "mysql++ trouble when compiling project"
date: 2006-06-07
forum: Programming Talk
---

### Post by chromex on 2006-06-07
I'm building a program which needs to interface with an on machine mysql server. The machine runs Dapper and has the latest mysql and mysql++ lib via apt. Now, when I compile my program I get the following error block:

```

In file included from /usr/local/include/mysql++/connection.h:40,
                 from /usr/local/include/mysql++/mysql++.h:52,
                 from database.h:4,
                 from main.cpp:6:
/usr/local/include/mysql++/defs.h:34:19: error: mysql.h: No such file or directory
/usr/local/include/mysql++/defs.h:66: error: ‘MYSQL_FIELD’ does not name a type
/usr/local/include/mysql++/connection.h:146: error: ‘my_bool’ has not been declared
/usr/local/include/mysql++/connection.h:163: error: ‘my_bool’ has not been declared
/usr/local/include/mysql++/connection.h:360: error: ‘st_mysql_options’ does not name a type
/usr/local/include/mysql++/connection.h:427: error: ‘my_ulonglong’ does not name a type
/usr/local/include/mysql++/connection.h:438: error: ‘my_ulonglong’ does not name a type
/usr/local/include/mysql++/connection.h:488: error: ‘mysql_option’ has not been declared
/usr/local/include/mysql++/connection.h:545: error: ‘MYSQL’ does not name a type
/usr/local/include/mysql++/connection.h: In member function ‘void mysqlpp::Connection::close()’:
/usr/local/include/mysql++/connection.h:171: error: ‘mysql_’ was not declared in this scope
/usr/local/include/mysql++/connection.h:171: error: ‘mysql_close’ was not declared in this scope
/usr/local/include/mysql++/connection.h: In member function ‘const char* mysqlpp::Connection::error()’:
/usr/local/include/mysql++/connection.h:228: error: ‘mysql_’ was not declared in this scope
/usr/local/include/mysql++/connection.h:228: error: ‘mysql_error’ was not declared in this scope
/usr/local/include/mysql++/connection.h: In member function ‘int mysqlpp::Connection::errnum()’:
/usr/local/include/mysql++/connection.h:235: error: ‘mysql_’ was not declared in this scope
/usr/local/include/mysql++/connection.h:235: error: ‘mysql_errno’ was not declared in this scope
/usr/local/include/mysql++/connection.h: In member function ‘int mysqlpp::Connection::refresh(unsigned int)’:/usr/local/include/mysql++/connection.h:247: error: ‘mysql_’ was not declared in this scope
/usr/local/include/mysql++/connection.h:247: error: ‘mysql_refresh’ was not declared in this scope
/usr/local/include/mysql++/connection.h: In member function ‘int mysqlpp::Connection::kill(long unsigned int)’:
/usr/local/include/mysql++/connection.h:270: error: ‘mysql_’ was not declared in this scope
/usr/local/include/mysql++/connection.h:270: error: ‘mysql_kill’ was not declared in this scope
/usr/local/include/mysql++/connection.h: In member function ‘std::string mysqlpp::Connection::client_info()’:/usr/local/include/mysql++/connection.h:278: error: ‘mysql_get_client_info’ was not declared in this scope
/usr/local/include/mysql++/connection.h: In member function ‘std::string mysqlpp::Connection::host_info()’:
/usr/local/include/mysql++/connection.h:289: error: ‘mysql_’ was not declared in this scope
/usr/local/include/mysql++/connection.h:289: error: ‘mysql_get_host_info’ was not declared in this scope
/usr/local/include/mysql++/connection.h: In member function ‘int mysqlpp::Connection::proto_info()’:
/usr/local/include/mysql++/connection.h:298: error: ‘mysql_’ was not declared in this scope
/usr/local/include/mysql++/connection.h:298: error: ‘mysql_get_proto_info’ was not declared in this scope
/usr/local/include/mysql++/connection.h: In member function ‘std::string mysqlpp::Connection::server_info()’:/usr/local/include/mysql++/connection.h:306: error: ‘mysql_’ was not declared in this scope
/usr/local/include/mysql++/connection.h:306: error: ‘mysql_get_server_info’ was not declared in this scope
/usr/local/include/mysql++/connection.h: In member function ‘std::string mysqlpp::Connection::stat()’:
/usr/local/include/mysql++/connection.h:317: error: ‘mysql_’ was not declared in this scope
/usr/local/include/mysql++/connection.h:317: error: ‘mysql_stat’ was not declared in this scope
/usr/local/include/mysql++/fields.h: At global scope:
/usr/local/include/mysql++/fields.h:41: error: ‘Field’ was not declared in this scope
/usr/local/include/mysql++/fields.h:41: error: template argument 2 is invalid
/usr/local/include/mysql++/fields.h:41: error: template argument 3 is invalid
/usr/local/include/mysql++/fields.h:54: error: expected ‘;’ before ‘&’ token
/usr/local/include/mysql++/fields.h:57: error: expected ‘;’ before ‘&’ token
/usr/local/include/mysql++/fields.h:62: error: expected `;' before ‘size_type’
/usr/local/include/mysql++/fields.h:62: error: ‘size_type’ does not name a type
/usr/local/include/mysql++/type_info.h:142: error: expected `)' before ‘t’
/usr/local/include/mysql++/type_info.h:148: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/mysql++/type_info.h:299: error: ‘enum_field_types’ has not been declared
/usr/local/include/mysql++/type_info.h:340: error: expected `)' before ‘t’
/usr/local/include/mysql++/type_info.h:346: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/mysql++/type_info.h: In constructor ‘mysqlpp::mysql_type_info::mysql_type_info(int)’:
/usr/local/include/mysql++/type_info.h:348: error: ‘f’ was not declared in this scope
/usr/local/include/mysql++/type_info.h:348: error: ‘UNSIGNED_FLAG’ was not declared in this scope
/usr/local/include/mysql++/type_info.h:349: error: ‘NOT_NULL_FLAG’ was not declared in this scope
/usr/local/include/mysql++/row.h: At global scope:
/usr/local/include/mysql++/row.h:66: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/mysql++/result.h:77: error: expected `)' before ‘*’ token
/usr/local/include/mysql++/result.h:95: error: expected ‘;’ before ‘*’ token
/usr/local/include/mysql++/result.h:104: error: expected `;' before ‘Row’
/usr/local/include/mysql++/result.h:134: error: expected ‘;’ before ‘&’ token
/usr/local/include/mysql++/result.h:140: error: expected `;' before ‘void’
/usr/local/include/mysql++/result.h:296: error: expected ‘;’ before ‘&’ token
/usr/local/include/mysql++/result.h:306: error: expected `;' before ‘bool’
/usr/local/include/mysql++/result.h:320: error: expected ‘;’ before ‘*’ token
/usr/local/include/mysql++/result.h: In constructor ‘mysqlpp::ResUse::ResUse()’:
/usr/local/include/mysql++/result.h:68: error: class ‘mysqlpp::ResUse’ does not have any field named ‘result_’
/usr/local/include/mysql++/result.h: In copy constructor ‘mysqlpp::ResUse::ResUse(const mysqlpp::ResUse&)’:
/usr/local/include/mysql++/result.h:85: error: ‘const class mysqlpp::ResUse’ has no member named ‘result_’
/usr/local/include/mysql++/result.h: In member function ‘mysqlpp::Row mysqlpp::ResUse::fetch_row()’:
/usr/local/include/mysql++/result.h:106: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h:114: error: ‘MYSQL_ROW’ was not declared in this scope
/usr/local/include/mysql++/result.h:114: error: expected `;' before ‘row’
/usr/local/include/mysql++/result.h:115: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h:115: error: ‘mysql_fetch_lengths’ was not declared in this scope
/usr/local/include/mysql++/result.h:116: error: ‘row’ was not declared in this scope
/usr/local/include/mysql++/result.h:124: error: ‘row’ was not declared in this scope
/usr/local/include/mysql++/result.h: In member function ‘long unsigned int* mysqlpp::ResUse::fetch_lengths() const’:
/usr/local/include/mysql++/result.h:130: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h:130: error: ‘mysql_fetch_lengths’ was not declared in this scope
/usr/local/include/mysql++/result.h: In member function ‘void mysqlpp::ResUse::field_seek(int)’:
/usr/local/include/mysql++/result.h:142: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h:142: error: ‘mysql_field_seek’ was not declared in this scope
/usr/local/include/mysql++/result.h: In member function ‘int mysqlpp::ResUse::num_fields() const’:
/usr/local/include/mysql++/result.h:148: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h:148: error: ‘mysql_num_fields’ was not declared in this scope
/usr/local/include/mysql++/result.h: In member function ‘void mysqlpp::ResUse::purge()’:
/usr/local/include/mysql++/result.h:164: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h:165: error: ‘mysql_free_result’ was not declared in this scope
/usr/local/include/mysql++/result.h: In member function ‘mysqlpp::ResUse::operator bool() const’:
/usr/local/include/mysql++/result.h:193: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h: In member function ‘bool mysqlpp::ResUse::operator==(const mysqlpp::ResUse&) const’:
/usr/local/include/mysql++/result.h:308: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h:308: error: ‘const class mysqlpp::ResUse’ has no member named ‘result_’
/usr/local/include/mysql++/result.h: In member function ‘bool mysqlpp::ResUse::operator!=(const mysqlpp::ResUse&) const’:
/usr/local/include/mysql++/result.h:315: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h:315: error: ‘const class mysqlpp::ResUse’ has no member named ‘result_’
/usr/local/include/mysql++/result.h: At global scope:
/usr/local/include/mysql++/result.h:356: error: expected `)' before ‘*’ token
/usr/local/include/mysql++/result.h:401: error: ‘my_ulonglong’ does not name a type
/usr/local/include/mysql++/result.h: In member function ‘const mysqlpp::Row mysqlpp::Result::fetch_row() const’:
/usr/local/include/mysql++/result.h:379: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h:387: error: ‘MYSQL_ROW’ was not declared in this scope
/usr/local/include/mysql++/result.h:387: error: expected `;' before ‘row’
/usr/local/include/mysql++/result.h:388: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h:388: error: ‘mysql_fetch_lengths’ was not declared in this scope
/usr/local/include/mysql++/result.h:389: error: ‘row’ was not declared in this scope
/usr/local/include/mysql++/result.h:397: error: ‘row’ was not declared in this scope
/usr/local/include/mysql++/result.h: In member function ‘void mysqlpp::Result::data_seek(mysqlpp::uint) const’:
/usr/local/include/mysql++/result.h:412: error: ‘result_’ was not declared in this scope
/usr/local/include/mysql++/result.h:412: error: ‘mysql_data_seek’ was not declared in this scope
/usr/local/include/mysql++/result.h: In member function ‘virtual unsigned int mysqlpp::Result::size() const’:/usr/local/include/mysql++/result.h:418: error: ‘num_rows’ was not declared in this scope
/usr/local/include/mysql++/result.h: In member function ‘unsigned int mysqlpp::Result::rows() const’:
/usr/local/include/mysql++/result.h:424: error: ‘num_rows’ was not declared in this scope
/usr/local/include/mysql++/result.h: At global scope:
/usr/local/include/mysql++/result.h:458: error: ‘my_ulonglong’ does not name a type
/usr/local/include/mysql++/result.h:459: error: ‘my_ulonglong’ does not name a type
/usr/local/include/mysql++/result.h: In member function ‘mysqlpp::ResUse& mysqlpp::ResUse::operator=(const mysqlpp::ResUse&)’:
/usr/local/include/mysql++/result.h:628: error: ‘const class mysqlpp::ResUse’ has no member named ‘result_’
/usr/local/include/mysql++/query.h: At global scope:
/usr/local/include/mysql++/query.h:639: error: ‘my_ulonglong’ does not name a type
/usr/local/include/mysql++/query.h:640: error: ‘my_ulonglong’ does not name a type
/usr/local/include/mysql++/query.h: In member function ‘void mysqlpp::Query::storein_sequence(Sequence&, const char*)’:
/usr/local/include/mysql++/query.h:671: error: ‘MYSQL_ROW’ was not declared in this scope
/usr/local/include/mysql++/query.h:671: error: expected `;' before ‘d’
/usr/local/include/mysql++/query.h:672: error: ‘d’ was not declared in this scope
/usr/local/include/mysql++/query.h:674: error: ‘d’ was not declared in this scope
/usr/local/include/mysql++/query.h:674: error: ‘class mysqlpp::ResUse’ has no member named ‘raw_result’
/usr/local/include/mysql++/query.h:674: error: there are no arguments to ‘mysql_fetch_lengths’ that depend on a template parameter, so a declaration of ‘mysql_fetch_lengths’ must be available
/usr/local/include/mysql++/query.h:674: error: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
/usr/local/include/mysql++/query.h: In member function ‘void mysqlpp::Query::storein_set(Set&, const char*)’:/usr/local/include/mysql++/query.h:696: error: ‘MYSQL_ROW’ was not declared in this scope
/usr/local/include/mysql++/query.h:696: error: expected `;' before ‘d’
/usr/local/include/mysql++/query.h:697: error: ‘d’ was not declared in this scope
/usr/local/include/mysql++/query.h:699: error: ‘d’ was not declared in this scope
/usr/local/include/mysql++/query.h:699: error: ‘class mysqlpp::ResUse’ has no member named ‘raw_result’
/usr/local/include/mysql++/query.h:699: error: there are no arguments to ‘mysql_fetch_lengths’ that depend on a template parameter, so a declaration of ‘mysql_fetch_lengths’ must be available
make: *** [main.o] Error 1

```

Now, from what I've been able to gather this is due to the fact that my mysql server was not a source install. Does anyone know if this is right, and if so, how to get apt to do a source install?

---

### Post by Adam83 on 2006-06-12
To state the obvious, it seems the problem starts with not being able to locate "mysql.h".  All the definitions after are hitting errors and they might all be resulting from that issue.  While it may be true that installing from source might fix the problem, it would probably only be because the directories for the installation might be different than the directories used with the package installer.  If I were you, I would look for the reference to "mysql.h" and try to correct that specific problem.  That would probably be a matter of changing a configuration in your IDE (if you are using one), or adding the path of your mysql.h file to your library paths for your compiler or as a command line option.  That should fix the problem, or at least allow you to see what other problems there may be.  Compiling from source for the MySQL installation might be more of a headache.  Good luck.

---

### Post by -PTM- on 2007-01-19
Hi!

i have a similar problem. It's first time I work with C++. I installed mysql++ from mysql.com.
after that I try to include mysql++.h with
```
#include "mysql++.h"
```
and
```
g++ -o mysql1 mysql1.cpp -I /usr/include/mysql++
```

I get the following error messages:
```

In file included from /usr/include/mysql++/connection.h:40,
                 from /usr/include/mysql++/mysql++.h:54,
                 from mysql1.cpp:1:
/usr/include/mysql++/defs.h:34:19: error: mysql.h: No such file or directory
/usr/include/mysql++/defs.h:66: error: 'MYSQL_FIELD' does not name a type
/usr/include/mysql++/connection.h:142: error: 'my_bool' has not been declared
/usr/include/mysql++/connection.h:159: error: 'my_bool' has not been declared
/usr/include/mysql++/connection.h:355: error: 'st_mysql_options' does not name a type
/usr/include/mysql++/connection.h:422: error: 'my_ulonglong' does not name a type
/usr/include/mysql++/connection.h:433: error: 'my_ulonglong' does not name a type
/usr/include/mysql++/connection.h:483: error: 'mysql_option' has not been declared
/usr/include/mysql++/connection.h:540: error: 'MYSQL' does not name a type
/usr/include/mysql++/connection.h: In member function 'void mysqlpp::Connection::close()':
/usr/include/mysql++/connection.h:167: error: 'mysql_' was not declared in this scope
/usr/include/mysql++/connection.h:167: error: 'mysql_close' was not declared in this scope
/usr/include/mysql++/connection.h: In member function 'const char* mysqlpp::Connection::error()':
/usr/include/mysql++/connection.h:224: error: 'mysql_' was not declared in this scope
/usr/include/mysql++/connection.h:224: error: 'mysql_error' was not declared in this scope
/usr/include/mysql++/connection.h: In member function 'int mysqlpp::Connection::errnum()':
/usr/include/mysql++/connection.h:231: error: 'mysql_' was not declared in this scope
/usr/include/mysql++/connection.h:231: error: 'mysql_errno' was not declared in this scope
/usr/include/mysql++/connection.h: In member function 'int mysqlpp::Connection::refresh(unsigned int)':
/usr/include/mysql++/connection.h:243: error: 'mysql_' was not declared in this scope
/usr/include/mysql++/connection.h:243: error: 'mysql_refresh' was not declared in this scope
/usr/include/mysql++/connection.h: In member function 'int mysqlpp::Connection::ping()':
/usr/include/mysql++/connection.h:256: error: 'mysql_' was not declared in this scope
/usr/include/mysql++/connection.h:256: error: 'mysql_ping' was not declared in this scope
/usr/include/mysql++/connection.h: In member function 'int mysqlpp::Connection::kill(long unsigned int)':
/usr/include/mysql++/connection.h:265: error: 'mysql_' was not declared in this scope
/usr/include/mysql++/connection.h:265: error: 'mysql_kill' was not declared in this scope
/usr/include/mysql++/connection.h: In member function 'std::string mysqlpp::Connection::client_info()':
/usr/include/mysql++/connection.h:273: error: 'mysql_get_client_info' was not declared in this scope
/usr/include/mysql++/connection.h: In member function 'std::string mysqlpp::Connection::host_info()':
/usr/include/mysql++/connection.h:284: error: 'mysql_' was not declared in this scope
/usr/include/mysql++/connection.h:284: error: 'mysql_get_host_info' was not declared in this scope
/usr/include/mysql++/connection.h: In member function 'int mysqlpp::Connection::proto_info()':
/usr/include/mysql++/connection.h:293: error: 'mysql_' was not declared in this scope
/usr/include/mysql++/connection.h:293: error: 'mysql_get_proto_info' was not declared in this scope
/usr/include/mysql++/connection.h: In member function 'std::string mysqlpp::Connection::server_info()':
/usr/include/mysql++/connection.h:301: error: 'mysql_' was not declared in this scope
/usr/include/mysql++/connection.h:301: error: 'mysql_get_server_info' was not declared in this scope
/usr/include/mysql++/connection.h: In member function 'std::string mysqlpp::Connection::stat()':
/usr/include/mysql++/connection.h:312: error: 'mysql_' was not declared in this scope
/usr/include/mysql++/connection.h:312: error: 'mysql_stat' was not declared in this scope
/usr/include/mysql++/fields.h: At global scope:
/usr/include/mysql++/fields.h:41: error: 'Field' was not declared in this scope
/usr/include/mysql++/fields.h:41: error: template argument 2 is invalid
/usr/include/mysql++/fields.h:41: error: template argument 3 is invalid
/usr/include/mysql++/fields.h:54: error: ISO C++ forbids declaration of 'Field' with no type
/usr/include/mysql++/fields.h:54: error: expected ';' before '&' token
/usr/include/mysql++/fields.h:57: error: ISO C++ forbids declaration of 'Field' with no type
/usr/include/mysql++/fields.h:57: error: expected ';' before '&' token
/usr/include/mysql++/fields.h:62: error: expected `;' before 'size_type'
/usr/include/mysql++/fields.h:62: error: 'size_type' does not name a type
/usr/include/mysql++/type_info.h:142: error: expected `)' before 't'
/usr/include/mysql++/type_info.h:148: error: expected ',' or '...' before '&' token
/usr/include/mysql++/type_info.h:148: error: ISO C++ forbids declaration of 'MYSQL_FIELD' with no type
/usr/include/mysql++/type_info.h:299: error: 'enum_field_types' has not been declared
/usr/include/mysql++/type_info.h:340: error: expected `)' before 't'
/usr/include/mysql++/type_info.h:346: error: expected ',' or '...' before '&' token
/usr/include/mysql++/type_info.h:346: error: ISO C++ forbids declaration of 'MYSQL_FIELD' with no type
/usr/include/mysql++/type_info.h: In constructor 'mysqlpp::mysql_type_info::mysql_type_info(int)':
/usr/include/mysql++/type_info.h:348: error: 'f' was not declared in this scope
/usr/include/mysql++/type_info.h:348: error: 'UNSIGNED_FLAG' was not declared in this scope
/usr/include/mysql++/type_info.h:349: error: 'NOT_NULL_FLAG' was not declared in this scope
/usr/include/mysql++/row.h: At global scope:
/usr/include/mysql++/row.h:66: error: expected ',' or '...' before '&' token
/usr/include/mysql++/row.h:67: error: ISO C++ forbids declaration of 'MYSQL_ROW' with no type
/usr/include/mysql++/result.h:77: error: expected `)' before '*' token
/usr/include/mysql++/result.h:94: error: ISO C++ forbids declaration of 'MYSQL_RES' with no type
/usr/include/mysql++/result.h:94: error: expected ';' before '*' token
/usr/include/mysql++/result.h:103: error: expected `;' before 'Row'
/usr/include/mysql++/result.h:133: error: ISO C++ forbids declaration of 'Field' with no type
/usr/include/mysql++/result.h:133: error: expected ';' before '&' token
/usr/include/mysql++/result.h:139: error: expected `;' before 'void'
/usr/include/mysql++/result.h:295: error: ISO C++ forbids declaration of 'Field' with no type
/usr/include/mysql++/result.h:295: error: expected ';' before '&' token
/usr/include/mysql++/result.h:305: error: expected `;' before 'bool'
/usr/include/mysql++/result.h:319: error: ISO C++ forbids declaration of 'MYSQL_RES' with no type
/usr/include/mysql++/result.h:319: error: expected ';' before '*' token
/usr/include/mysql++/result.h: In constructor 'mysqlpp::ResUse::ResUse()':
/usr/include/mysql++/result.h:68: error: class 'mysqlpp::ResUse' does not have any field named 'result_'
/usr/include/mysql++/result.h: In member function 'mysqlpp::Row mysqlpp::ResUse::fetch_row()':
/usr/include/mysql++/result.h:105: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h:113: error: 'MYSQL_ROW' was not declared in this scope
/usr/include/mysql++/result.h:113: error: expected `;' before 'row'
/usr/include/mysql++/result.h:114: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h:114: error: 'mysql_fetch_lengths' was not declared in this scope
/usr/include/mysql++/result.h:115: error: 'row' was not declared in this scope
/usr/include/mysql++/result.h:123: error: 'row' was not declared in this scope
/usr/include/mysql++/result.h: In member function 'long unsigned int* mysqlpp::ResUse::fetch_lengths() const':
/usr/include/mysql++/result.h:129: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h:129: error: 'mysql_fetch_lengths' was not declared in this scope
/usr/include/mysql++/result.h: In member function 'void mysqlpp::ResUse::field_seek(int)':
/usr/include/mysql++/result.h:141: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h:141: error: 'mysql_field_seek' was not declared in this scope
/usr/include/mysql++/result.h: In member function 'int mysqlpp::ResUse::num_fields() const':
/usr/include/mysql++/result.h:147: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h:147: error: 'mysql_num_fields' was not declared in this scope
/usr/include/mysql++/result.h: In member function 'void mysqlpp::ResUse::purge()':
/usr/include/mysql++/result.h:163: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h:164: error: 'mysql_free_result' was not declared in this scope
/usr/include/mysql++/result.h: In member function 'mysqlpp::ResUse::operator bool() const':
/usr/include/mysql++/result.h:192: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h: In member function 'bool mysqlpp::ResUse::operator==(const mysqlpp::ResUse&) const':
/usr/include/mysql++/result.h:307: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h:307: error: 'const class mysqlpp::ResUse' has no member named 'result_'
/usr/include/mysql++/result.h: In member function 'bool mysqlpp::ResUse::operator!=(const mysqlpp::ResUse&) const':
/usr/include/mysql++/result.h:314: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h:314: error: 'const class mysqlpp::ResUse' has no member named 'result_'
/usr/include/mysql++/result.h: At global scope:
/usr/include/mysql++/result.h:355: error: expected `)' before '*' token
/usr/include/mysql++/result.h:400: error: 'my_ulonglong' does not name a type
/usr/include/mysql++/result.h: In member function 'const mysqlpp::Row mysqlpp::Result::fetch_row() const':
/usr/include/mysql++/result.h:378: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h:386: error: 'MYSQL_ROW' was not declared in this scope
/usr/include/mysql++/result.h:386: error: expected `;' before 'row'
/usr/include/mysql++/result.h:387: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h:387: error: 'mysql_fetch_lengths' was not declared in this scope
/usr/include/mysql++/result.h:388: error: 'row' was not declared in this scope
/usr/include/mysql++/result.h:396: error: 'row' was not declared in this scope
/usr/include/mysql++/result.h: In member function 'void mysqlpp::Result::data_seek(mysqlpp::uint) const':
/usr/include/mysql++/result.h:411: error: 'result_' was not declared in this scope
/usr/include/mysql++/result.h:411: error: 'mysql_data_seek' was not declared in this scope
/usr/include/mysql++/result.h: In member function 'virtual unsigned int mysqlpp::Result::size() const':
/usr/include/mysql++/result.h:417: error: 'num_rows' was not declared in this scope
/usr/include/mysql++/result.h: In member function 'unsigned int mysqlpp::Result::rows() const':
/usr/include/mysql++/result.h:423: error: 'num_rows' was not declared in this scope
/usr/include/mysql++/result.h: At global scope:
/usr/include/mysql++/result.h:457: error: 'my_ulonglong' does not name a type
/usr/include/mysql++/result.h:458: error: 'my_ulonglong' does not name a type
/usr/include/mysql++/result.h: In member function 'mysqlpp::ResUse& mysqlpp::ResUse::operator=(const mysqlpp::ResUse&)':
/usr/include/mysql++/result.h:627: error: 'const class mysqlpp::ResUse' has no member named 'result_'
/usr/include/mysql++/query.h: At global scope:
/usr/include/mysql++/query.h:700: error: 'my_ulonglong' does not name a type
/usr/include/mysql++/query.h:701: error: 'my_ulonglong' does not name a type
/usr/include/mysql++/query.h: In member function 'void mysqlpp::Query::storein_sequence(Sequence&, const char*)':
/usr/include/mysql++/query.h:732: error: 'MYSQL_ROW' was not declared in this scope
/usr/include/mysql++/query.h:732: error: expected `;' before 'd'
/usr/include/mysql++/query.h:733: error: 'd' was not declared in this scope
/usr/include/mysql++/query.h:735: error: 'd' was not declared in this scope
/usr/include/mysql++/query.h:735: error: 'class mysqlpp::ResUse' has no member named 'raw_result'
/usr/include/mysql++/query.h:735: error: there are no arguments to 'mysql_fetch_lengths' that depend on a template parameter, so a declaration of 'mysql_fetch_lengths' must be available
/usr/include/mysql++/query.h:735: error: (if you use '-fpermissive', G++ will accept your code, but allowing the use of an undeclared name is deprecated)
/usr/include/mysql++/query.h: In member function 'void mysqlpp::Query::storein_set(Set&, const char*)':
/usr/include/mysql++/query.h:757: error: 'MYSQL_ROW' was not declared in this scope
/usr/include/mysql++/query.h:757: error: expected `;' before 'd'
/usr/include/mysql++/query.h:758: error: 'd' was not declared in this scope
/usr/include/mysql++/query.h:760: error: 'd' was not declared in this scope
/usr/include/mysql++/query.h:760: error: 'class mysqlpp::ResUse' has no member named 'raw_result'
/usr/include/mysql++/query.h:760: error: there are no arguments to 'mysql_fetch_lengths' that depend on a template parameter, so a declaration of 'mysql_fetch_lengths' must be available
mysql1.cpp: In function 'int main()':
mysql1.cpp:5: error: 'Database' was not declared in this scope
mysql1.cpp:5: error: expected `;' before 'db'
mysql1.cpp:6: error: 'db' was not declared in this scope

```

---

### Post by everweb on 2007-03-06
You'll see in the Makefile for mysql++ that it has settings similar to the following:
CPPFLAGS =  -I/usr/include/mysql
LDFLAGS =  -L/usr/lib/mysql

which means that in mysql++.h they can say "#include <mysql.h>" instead of "#include <mysql/mysql.h>".

If your build doesn't have the same compiler & linker flags, the compiler (and linker) won't be able to find 'mysql.h'.

You may be able to get away with the following in your own source code:
   #include <mysql/mysql.h>
   #include <mysql++/mysql++.h> 

...but I recommend changing your build to include the same flags as mysql++ or you'll get linker prblems, too.

---

### Post by Nonplay on 2007-03-16
Try to copile in this manner:
```
g++ -I/usr/include/mysql++ -I/usr/include/mysql
``` 
Np

---


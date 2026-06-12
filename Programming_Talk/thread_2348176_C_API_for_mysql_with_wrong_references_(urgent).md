---
title: "C API for mysql with wrong references (urgent)"
date: 2017-01-01
forum: Programming Talk
---

### Post by geohei on 2017-01-01
Hi.

I'm programming in C and would like to add MySQL code.
So I installed libmysqlclient-dev, which installs mysql.h and all other header files.

Unfortunately, these header files are all installed in /usr/include/mysql instead of /usr/include.
Cross references between the header files all expect them to be in /usr/include.
Changing of all references can't be the solution.
Nor can it be copying /usr/include/mysql to /usr/include.

So ... something is wrong here.

Please advise.

Thanks,

---

### Post by steeldriver on 2017-01-01
Are you using `pkg-config` to automatically include the appropriate flags? if not, you probably should be:

```

$ pkg-config --cflags mysqlclient
-fabi-version=2 -fno-omit-frame-pointer -I/usr/include/mysql

```

---

### Post by Rocket2DMn on 2017-01-01
+1 for using tools like pkg-config.  You can run pkg-config in your Makefile which is more dynamic. Something like:
```

CFLAGS+=$(shell pkg-config --cflags mysqlclient)

```
and of course use the CFLAGS variable in your build command where you would normally put such options/flags.

If you're building with CMake, you can also use FindMySQL.  I haven't tested it, but your CMakeLists.txt would include something like:
```

find_package(MySql REQUIRED)
include_directories(${MYSQL_INCLUDE_DIR})
target_link_libraries(my_app ${MYSQL_LIBRARIES})

```

---

### Post by geohei on 2017-01-02
Many thanks for the quick answers!

In order to make it work fast, I use Code::Blocks IDE.
There, I can append the path where header files are being looked for.

Project build options
Search Directories
Compiler
Append target options to project options
/usr/include/mysql

This does the job inside Code::Blocks.
I'll dig my way through the solution with CMake (described in the answers above).

Many thanks!

---


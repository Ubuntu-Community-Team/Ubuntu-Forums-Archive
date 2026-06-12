---
title: "linking issues"
date: 2012-07-24
forum: Programming Talk
---

### Post by Hetepeperfan on 2012-07-24
Hi there,

I've got a problem with compiling a program that has to link against libraries in:
/opt/pylon/lib64. This is not a standard location for the runtime linker.
In my make file I export LD_LIBRARY_PATH to the path above. Then the program compiles pretty well. However at run time I thought to be smart and have my program set the LD_LIBRARY_PATH before using my pylon library. However as a www search engine search has thought me the libraries are linked at runtime before main function, therefore it isn't usefull to have my program to set the LD_LIBRARY_PATH. Are there any tricks to tell my executabe to load the libraries from / link at runtime against libraries in /opt/pylon/lib64?
Ofcourse I can set LD_LIBRARY_FLAG before running my program then it runs, however I would like avoid using the LD_LIBRARY_PATH since it's not really a good fix.

any help is most welcome

cheers,

Maarten

---

### Post by spjackson on 2012-07-24
I don't recall all the fine details, but see
```
man ld
``` You can use the -rpath linker option, or LD_RUN_PATH (environment variable read at link time).

---

### Post by Bachstelze on 2012-07-24
First, you shouldn't use LD_LIBRARY_PATH during compilation, that's what the -L flag is for.

Second, to set it at run time, the obvious (and by far the simplest) way is to create a shell script (or an alias) that will set it and then run your executable.

---

### Post by Hetepeperfan on 2012-07-25
> **spjackson said:**
> I don't recall all the fine details, but see
```
man ld
``` You can use the -rpath linker option, or LD_RUN_PATH (environment variable read at link time).

Thanks I used g++ for linking but now I specify the  -Wl,-rpath=/opt/pylon/lib64 which sends  -rpath=libpath to the linker. And runs the my program perfectly.

> **Bachstelze said:**
> First, you shouldn't use LD_LIBRARY_PATH during compilation, that's what the -L flag is for.

Second, to set it at run time, the obvious (and by far the simplest) way is to create a shell script (or an alias) that will set it and then run your executable.

Also thanks Bachstelze, I already thought exporting LD_LIBRARY_PATH in a makefile is a bit weird.  However I noted that I already included the -L/opt/pylon/lib64 in my makefile.
I suspect my pylon library that links to libxerces (an apache XML parsing library, that I do not directly use myself). 
Do you also think that using the  -Wl,-rpath=libpath might be a useful option to consider here?

```
/usr/bin/ld: warning: libicuuc.so.36, needed by //opt/pylon/lib64/libxerces-c.so.27, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libicudata.so.36, needed by //opt/pylon/lib64/libxerces-c.so.27, not found (try using -rpath or -rpath-link)
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `UCNV_FROM_U_CALLBACK_STOP_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `u_init_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `u_isspace_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `ucnv_getMinCharSize_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `u_foldCase_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `u_tolower_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `ucnv_open_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `ucnv_toUnicode_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `ucnv_getMaxCharSize_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `u_totitle_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `ucnv_close_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `UCNV_FROM_U_CALLBACK_SUBSTITUTE_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `ucnv_toUChars_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `ucnv_setFromUCallBack_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `ucnv_fromUChars_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `ucnv_openU_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `u_charType_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `u_toupper_3_6'
//opt/pylon/lib64/libxerces-c.so.27: undefined reference to `ucnv_fromUnicode_3_6'
collect2: ld returned 1 exit status
```I'm sorry I should have posted this output in my original post.

Thanks for your help.

---

### Post by dwhitney67 on 2012-07-25
> **Hetepeperfan said:**
> ...

any help is most welcome

cheers,

Maarten

If the library (-ies) in /opt/pylon/lib64 are meant to be available to all users on your system, you can consider either adding this path to the file /etc/ld.so.conf, or preferably within a new file in /etc/ld.so.conf.d.  If you choose the latter option, the file must have a '.conf' file name extension.  For example:
```

$ sudo -i

# echo /opt/pylon/lib64 > /etc/ld.so.conf.d/pylon.conf

# /sbin/ldconfig

# exit

```
After performing these steps, you will not have to rely on setting LD_LIBRARY_PATH when running your application.

However, you will still need to specify the library path, using the -L option, when building your application.

---

### Post by Bachstelze on 2012-07-25
I was assuming he doesn't have root access, because if he does, the obvious thing to do is to put them into /usr/local/lib...

About libicuuc.so.36 and libicudata.so.36, they are very old versions (the version of libicudata shipped in Ubuntu 12.04 for example is libicudata.so.48). If you don't want to recompile your library, you will need to find those verisons of libicu and link with them.

---

### Post by dwhitney67 on 2012-07-25
> **Bachstelze said:**
> I was assuming he doesn't have root access...
I assumed he did since the library is stored in /opt.  :-)

---

### Post by Hetepeperfan on 2012-07-25
> **Bachstelze said:**
> I was assuming he doesn't have root access, because if he does, the obvious thing to do is to put them into /usr/local/lib...

I do have root acces, but the manual with the library says put the library in /opt/pylon. and thus as their advise i put them in the specified directory.

> **Bachstelze said:**
> About libicuuc.so.36 and libicudata.so.36, they are very old versions (the version of libicudata shipped in Ubuntu 12.04 for example is libicudata.so.48). If you don't want to recompile your library, you will need to find those verisons of libicu and link with them.

recompiling is not an option because it's a header only library to link against their .so files and their .so files are probably linked against the old libicuuc.so.36 and libicudata.so.36 you mentionned.

---

### Post by Bachstelze on 2012-07-25
> **dwhitney67 said:**
> I assumed he did since the library is stored in /opt.  :-)

It could very well have been the work of an incompetent sysadmin in a school or company setting. :p

---

### Post by Hetepeperfan on 2012-07-25
Well many thanks to all! :-) I think i've found quite a few good ideas to get rid of my linking problem

cheers and thanks!

maarten

---


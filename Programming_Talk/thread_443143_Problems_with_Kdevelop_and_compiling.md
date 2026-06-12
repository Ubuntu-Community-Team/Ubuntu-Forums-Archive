---
title: "Problems with Kdevelop and compiling"
date: 2007-05-14
forum: Programming Talk
---

### Post by dempl_dempl on 2007-05-14
Ok,here it goes: 

 I have problems with compiling Basic KDE App with KDevelop.
when I run ./configure I get the output :


---------------------------------------------------------------------------------------------------------------------------
checking for Qt... 
configure: error: Qt (>= Qt 3.2 and < 4.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!
*** Exited with status: 1 ***
--------------------------------------------------------------------------------------------------------------------------

Only thing is , I've installed Qt , both versions 3 and 4 using "apt-get install".

I've searched the forum but I couldn't find anything directly concerning this problem.

Now , when I type the following:

$apt-cache search libqt | grep mt

I get theese results:
----------------------------------------------------------------------------------------------------------------
libqt3-mt - Qt GUI Library (Threaded runtime version), Version 3
libqt3-mt-dev - Qt development files (Threaded)
libqt3-mt-mysql - MySQL database driver for Qt3 (Threaded)
libqt3-mt-odbc - ODBC database driver for Qt3 (Threaded)
libqt3-mt-psql - PostgreSQL database driver for Qt3 (Threaded)
libqt3-mt-sqlite - SQLite database driver for Qt3 (Threaded)
----------------------------------------------------------------------------------------------------------------

$apt-cache search libqt | grep qt4 

I get theese:

----------------------------------------------------------------------------------------------------------------
libqt4-core - Qt 4 core non-GUI functionality runtime library
libqt4-debug - Qt 4 library debugging symbols
libqt4-dev - Qt 4 development files
libqt4-gui - Qt 4 core GUI functionality runtime library
libqt4-qt3support - Qt 3 compatibility library for Qt 4
libqt4-sql - Qt 4 SQL database module
libqt0-ruby1.8-qt4 - Qt4 bindings for Ruby
libqt4-core-kdecopy - Qt 4 core non-GUI functionality runtime library
libqt4-debug-dev-kdecopy - Qt 4 debugging development files
libqt4-debug-kdecopy - Qt 4 debugging runtime libraries
libqt4-dev-kdecopy - Qt 4 development files
libqt4-gui-kdecopy - Qt 4 core GUI functionality runtime library
libqt4-qt3support-kdecopy - Qt 3 compatibility library for Qt 4
libqt4-ruby - ruby bindings for the Qt4 GUI library
libqt4-ruby1.8 - ruby bindings for the Qt4 GUI library
libqt4-sql-kdecopy - Qt 4 SQL database module
----------------------------------------------------------------------------------------------------------------


Is there something missing or wrong here?
Should I simply try to install Anjuta? :)

BTW, I use Kubuntu feisty, and compiling terminal c++ apps works.
Kdevelop is 3.4.0.

---

### Post by GeneralZod on 2007-05-14
> **dempl_dempl said:**
> 
libqt3-mt-dev - Qt development files (Threaded)


Whenever a "configure" script complains of missing libraries, it's usually the -dev headers that they require.  Install the package above, and the error should go away, but there may be more missing -dev files - you should be able to figure out which, though! :)

Oh, and this technically isn't a problem with KDevelop - it's at the level of autotools and missing libraries, so switching to another IDE likely wouldn't make any difference :)

---

### Post by dempl_dempl on 2007-05-15
Thanks :) 
I've started downloading couple of *-dev libs and it really worked. 
This apt-get thingie makes life rally easier.

Thanks to your help Linux is ready to  get some coolest programs ever. 

BTW, why all OpenSource Developers never compile their programs with as static ?Or why  they never suply needed packages in one archive, in order you don't have to go into package chasing all over the Net.

---

### Post by bpbailey on 2008-02-27
Probably because "Linux...it just works" is largely a myth if you want to do anything beyond the basics. No OS is perfect, but Linux seems to suffer from its own form of "DLL Hell" more often than any other OS I've used. That said, though, I do enjoy using it. Probably because I'm a masochistic rebel at heart.

---

### Post by bpbailey on 2008-02-27
But...Thanks!...This thread has solved my problem.

---


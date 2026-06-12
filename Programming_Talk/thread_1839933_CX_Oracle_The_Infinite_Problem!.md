---
title: "CX_Oracle The Infinite Problem!"
date: 2011-09-06
forum: Programming Talk
---

### Post by robtrance on 2011-09-06
Hi guys, first sorry my english.

Well i write cause im new user in python and ubuntu, im trying to make an aplication in python that connect to oracle using the cx_oracle.

If i run it on the terminal its run and works FINE, but if i run it on SPE or in Geany i got the f***ing message:

ImportError: libclntsh.so.10.1: cannot open shared object file: No such file or directory


Ok, i know in the web are a lot of threads about this, i do almost ALL and no solution.


This is my path of oracle:
/user/lib/oracle/10.2.0.4/client


This is what i have written in the /etc/environment file:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/oracle/10.2.0.4/client/bin"
ORACLE_HOME="/usr/lib/oracle/10.2.0.4/client"


This is what i have written in the oracle.so.conf file on /etc/ld.so.conf.d :

/usr/lib/oracle/10.2.0.4/client/lib

(of course i restart ubuntu everytime i made a change)


I try on SPE, i try on Geany, i try on Eclipse with Pydev and NOTHING, SPE and Geany the same message, Eclipse just dont do anything.


So PLEASE guys, what cant be wrong???? im about 3 weeks with this.


Thanks.

---

### Post by karlson on 2011-09-06
> **robtrance said:**
> Hi guys, first sorry my english.

Well i write cause im new user in python and ubuntu, im trying to make an aplication in python that connect to oracle using the cx_oracle.

If i run it on the terminal its run and works FINE, but if i run it on SPE or in Geany i got the f***ing message:


Language.

What about ipython?

> 
This is what i have written in the /etc/environment file:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/oracle/10.2.0.4/client/bin"
ORACLE_HOME="/usr/lib/oracle/10.2.0.4/client"


LD_LIBRARY_PATH?

> 
This is what i have written in the oracle.so.conf file on /etc/ld.so.conf.d :

/usr/lib/oracle/10.2.0.4/client/lib

(of course i restart ubuntu everytime i made a change)


Ummmmm.  Why?
```

sudo ldconfig -v

```

> 
I try on SPE, i try on Geany, i try on Eclipse with Pydev and NOTHING, SPE and Geany the same message, Eclipse just dont do anything.


So PLEASE guys, what cant be wrong???? im about 3 weeks with this.


Thanks.

Have you configured Eclipse/SPE/Geany to use library and have the library in the linker path of the code you execute?  If not that would be your problem.

---

### Post by WitchCraft on 2011-09-07
In the terminal:
```

EXPORT LD_LIBRARY_PATH="/user/lib/oracle/10.2.0.4/client/"
EXPORT LD_PRELOAD="/user/lib/oracle/10.2.0.4/client/libclntsh.so.10.1"
geany

```

---


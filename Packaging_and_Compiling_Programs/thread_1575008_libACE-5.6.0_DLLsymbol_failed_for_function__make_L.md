---
title: "libACE-5.6.0 DLL::symbol failed for function _make_Logger: Error: check log for detai"
date: 2010-09-15
forum: Packaging and Compiling Programs
---

### Post by pchero on 2010-09-15
Hello,

 I'm using Ubuntu-10.04 Desktop on my LG laptop.

 Recently, I tried to compiled libACE-5.6.0. It was hard, but it succeed.

 But, problem happened different point.

 When I tried to run the some program using a libACE, happened some error.


DLL::symbol failed for function _make_Logger: Error: check log for details.
ACE (1685|3078821584) Unable to create service object for logger
DLL::symbol failed for function _make_Logger: Error: check log for details.
ACE (1687|3078723280) Unable to create service object for logger
ACE (1685|3078821584) LN::open_dll - Failed to open admin: Error: check log for details.
ACE (1685|3078821584) Unable to create service object for admin
ACE (1687|3078723280) LN::open_dll - Failed to open ../lib/messenger: Error: check log for details.
ACE (1687|3078723280) Unable to create service object for messenger
DLL::symbol failed for function _make_Logger: Error: check log for details.
ACE (1689|3078547152) Unable to create service object for logger
DLL::symbol failed for function _make_Logger: Error: check log for details.
ACE (1691|3079128784) Unable to create service object for logger
ACE (1689|3078547152) LN::open_dll - Failed to open ../lib/personal: Error: check log for details.
ACE (1689|3078547152) Unable to create service object for personal
DLL::symbol failed for function _make_Logger: Error: check log for details.
ACE (1693|3078256336) Unable to create service object for logger
ACE (1691|3079128784) LN::open_dll - Failed to open ../lib/insight: Error: check log for details.
ACE (1691|3079128784) Unable to create service object for insight
ACE (1693|3078256336) LN::open_dll - Failed to open ../lib/scenario: Error: check log for details.
ACE (1693|3078256336) Unable to create service object for scenario
DLL::symbol failed for function _make_Logger: Error: check log for details.
ACE (1695|3079378640) Unable to create service object for logger
ACE (1695|3079378640) LN::open_dll - Failed to open ../lib/report: Error: check log for details.
ACE (1695|3079378640) Unable to create service object for report


 The program is similar ..like a libACE tutorial program

 The main function is consist of like this...
```

 int main(int argc, char **argv)
{
   .....
   ACE_Service_Config::open(argc, argv) != -1
   .....
}

```
And.. program used like this,


```
main -f ../conf/test.conf
```


```

/* test.conf */
dynamic logger Service_Object * logger:_make_Logger() "-t admin"
dynamic admin Service_Object * admin:_make_Acceptor() "-p 21000 -c"
```


 When... another co-worker compliled and run in the CentOS use a GCC-4.1.2 and G++-4.1.2, it worked well. But I couldn't.

 And my G++ and GCC version is 4.1.3

 What should I do to solved this problem on my Ubuntu?

 Plz, help me.

---


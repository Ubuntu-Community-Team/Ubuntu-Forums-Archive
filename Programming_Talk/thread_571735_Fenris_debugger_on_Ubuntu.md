---
title: "Fenris debugger on Ubuntu?"
date: 2007-10-09
forum: Programming Talk
---

### Post by VoidOfNothingness on 2007-10-09
Hello,

I have been trying to compile [Fenris]("http://lcamtuf.coredump.cx/fenris/") on Ubuntu for quite some time... But to avail. Is there someone who had succeeded in this task?

When I do try to compile Fenris, I do fail in a GDB related check:

> [+] Library mapping address: problems executing gdb!
[-] I need gdb to determine your defaults. Please consult documentation.


The code in the building script that causes such error is the following:

> 
echo -n "[+] Library mapping address: "

echo "break main" >.testerr 2>/dev/null
echo "x/2w getuid" >>.testerr 2>/dev/null
echo "x/10w __do_global_ctors_aux" >>.testerr 2>/dev/null
echo "x/10w __do_global_ctors_aux+1" >>.testerr 2>/dev/null
echo "x/10w __do_global_ctors_aux+2" >>.testerr 2>/dev/null
echo "x/10w __do_global_ctors_aux+3" >>.testerr 2>/dev/null
echo "x/10w __do_global_ctors_aux+4" >>.testerr 2>/dev/null
echo "x/10w __do_global_ctors_aux+5" >>.testerr 2>/dev/null
echo "x/10w __do_global_ctors_aux+6" >>.testerr 2>/dev/null
echo "x/10w __do_global_ctors_aux+7" >>.testerr 2>/dev/null

echo "run" >>.testerr 2>/dev/null
echo "x open" >>.testerr 2>/dev/null
echo "x/2w _dl_runtime_resolve+16" >>.testerr 2>/dev/null

gdb -batch -x .testerr ./.testme >.gtmp 2>/dev/null

ADDR=`grep open .gtmp 2>/dev/null|grep ^0x 2>/dev/null | awk '{print $1}' 2>/de$

RES=`grep -F resolve .gtmp 2>/dev/null`
JMP=`grep -F getuid .gtmp 2>/dev/null`

rm -f .testerr .testme

if [ "$ADDR" = "" ]; then
  rm -f .gtmp
  echo "problems executing gdb!"
  echo "[-] I need gdb to determine your defaults. Please consult documentation$
  echo
  exit 1
fi


From what I can understand from the above code, the script is building some test "binary" to be debugged using GDB, and then evaluates the debugging session's results... 
Can someone shed some light over this?

---

### Post by babil on 2008-05-28
**[=] Patch "build" **

it's basically one line, move ***echo "run" >>.testerr 2>/dev/null ***after ***echo "break main" >.testerr 2>/dev/null***

> 
--- build       2008-05-28 18:27:06.000000000 +1000
+++ build.patched       2008-05-28 18:24:00.000000000 +1000
@@ -384,6 +384,7 @@
 echo -n "[+] Library mapping address: "

 echo "break main" >.testerr 2>/dev/null
+echo "run" >>.testerr 2>/dev/null
 echo "x/2w getuid" >>.testerr 2>/dev/null
 echo "x/10w __do_global_ctors_aux" >>.testerr 2>/dev/null
 echo "x/10w __do_global_ctors_aux+1" >>.testerr 2>/dev/null
@@ -395,7 +396,6 @@
 echo "x/10w __do_global_ctors_aux+7" >>.testerr 2>/dev/null
 echo "x/10w __do_global_ctors_aux+8" >>.testerr 2>/dev/null

-echo "run" >>.testerr 2>/dev/null
 echo "x open" >>.testerr 2>/dev/null
 echo "x/2w _dl_runtime_resolve+16" >>.testerr 2>/dev/null


---


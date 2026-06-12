---
title: "Extract all the global variables , data structures and sub-structures from a core du"
date: 2013-05-17
forum: Programming Talk
---

### Post by Baijnath Jaiswal on 2013-05-17
[COLOR=#000000][FONT=Arial]I am trying to extract all the global symbols (with name and corresponding values) of a C code from core file (core.pid file, generated when the code crashes). 

This is one way to do, but it extracts symbols while code is executing: For example, we have list_globals.py script, and any C code which is crashing. suppose c_code.c. 

import gdb 
block = gdb.block_for_pc(long(gdb.parse_and_eval('$pc'))).global_block 
for symbol in block: 
gdb.write('SYMBOL: %20s,\tTYPE: %20s,\tValue: %20s\n' % (symbol.print_name, symbol.type, symbol.value())) 
This script is tested in this way: 

gcc -g c_code.c 

./a.out 

gdb a.out core.pid 

(gdb) start 

(gdb) source list_globals.py 

This will print all the global symbols with name,type and values. But here, (gdb) start is must because symbols are extracted by executing the c_code again. i want to extract the same information from core file without executing the C code again. How to do this..? Thanks[/FONT][/COLOR]

---


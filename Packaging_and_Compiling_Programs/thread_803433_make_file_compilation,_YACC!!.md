---
title: "make file compilation, YACC!!"
date: 2008-05-22
forum: Packaging and Compiling Programs
---

### Post by leo83 on 2008-05-22
Hi,

trying to compile a makefile and recv following error, the following is only part of the code,where i recv error. 
I have set the path to YACC, grammar.y is located at correct location, checked with basic makefile rules like TAB and no 8spaces, have downloaded YACC.Declarations are made correct.I really dont understand whats the issue. I tried the command YACC -d grammar.y from terminal and it works fine. The output y.tab.c is created.

Where am I going wrong? 

PARSER_SRC_DIR= $(BASEDIR)/applications/cli

```
 all:	y.tab.c lex.config.c $(STATICLIB) $(SHAREDLIBV)

y.tab.c: $(PARSER_SRC_DIR)/grammar.y

	yacc -d -t -v -p config $(PARSER_SRC_DIR)/grammar.y
```

make[2]: Entering directory `/srv/krone/Mini-Controller/Codebase_2.5.0.0/PoE/lib_source/poe'
./applications/cli/grammar.y
make[2]: ./applications/cli/grammar.y: Command not found
make[2]: *** [y.tab.c] Error 127
make[2]: Leaving directory `/srv/krone/Mini-Controller/Codebase_2.5.0.0/PoE/lib_source/poe'
make[2]: Entering directory `/srv/krone/Mini-Controller/Codebase_2.5.0.0/PoE/lib_source/poe'
./applications/cli/grammar.y
make[2]: ./applications/cli/grammar.y: Command not found
make[2]: *** [y.tab.c] Error 127


Thanks,
Abhi

---


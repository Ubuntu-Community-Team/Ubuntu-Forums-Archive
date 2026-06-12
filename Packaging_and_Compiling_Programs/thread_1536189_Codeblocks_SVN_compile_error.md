---
title: "Codeblocks SVN compile error"
date: 2010-07-21
forum: Packaging and Compiling Programs
---

### Post by Eragon0605 on 2010-07-21
I just moved from Kubuntu back to Ubuntu (Gnome is awesome) and, first things first, tried to build codeblocks from SVN. I installed all the dependencies and stuff, and bootstrap and configure ran fine. When I run make, however, it goes ok for a while, but then I get the following errors:
```
CParser.cpp:5:44: error: boost/spirit/include/classic.hpp: No such file or directory
CParser.cpp:6:49: error: boost/spirit/include/classic_core.hpp: No such file or directory
CParser.cpp:7:52: error: boost/spirit/include/classic_symbols.hpp: No such file or directory
CParser.cpp:8:51: error: boost/spirit/include/classic_confix.hpp: No such file or directory
CParser.cpp:10: error: ‘boost’ has not been declared
CParser.cpp:10: error: ‘classic’ is not a namespace-name
CParser.cpp:10: error: expected namespace-name before ‘;’ token
CParser.cpp: In member function ‘bool NassiEditorPanel::ParseC(const wxString&)’:
CParser.cpp:24: error: expected initializer before ‘<’ token
CParser.cpp:29: error: ‘rule_t’ was not declared in this scope
CParser.cpp:29: error: expected ‘;’ before ‘preprocessor’
CParser.cpp:30: error: expected ‘;’ before ‘cpp_comment’
CParser.cpp:31: error: expected ‘;’ before ‘c_comment’
CParser.cpp:32: error: expected ‘;’ before ‘cstr’
CParser.cpp:33: error: expected ‘;’ before ‘comment’
CParser.cpp:34: error: expected ‘;’ before ‘comment_collected’
CParser.cpp:35: error: expected ‘;’ before ‘parentheseshelper’
CParser.cpp:39: error: expected ‘;’ before ‘parentheses’
CParser.cpp:41: error: expected ‘;’ before ‘keywordend’
CParser.cpp:45: error: expected ‘;’ before ‘spaces’
CParser.cpp:47: error: expected ‘;’ before ‘instruction’
CParser.cpp:48: error: expected ‘;’ before ‘break_instr’
CParser.cpp:49: error: expected ‘;’ before ‘switch_instr’
CParser.cpp:50: error: ‘break_instr’ was not declared in this scope
CParser.cpp:50: error: ‘str_p’ was not declared in this scope
CParser.cpp:50: error: ‘keywordend’ was not declared in this scope
CParser.cpp:50: error: ‘spaces’ was not declared in this scope
CParser.cpp:50: error: ‘ch_p’ was not declared in this scope
CParser.cpp:51: error: ‘continue_instr’ was not declared in this scope
CParser.cpp:52: error: ‘return_instr’ was not declared in this scope
CParser.cpp:53: error: ‘comment_collected’ was not declared in this scope
CParser.cpp:53: error: ‘cstr’ was not declared in this scope
CParser.cpp:53: error: ‘anychar_p’ was not declared in this scope
CParser.cpp:54: error: ‘confix_p’ was not declared in this scope
CParser.cpp:55: error: ‘block’ was not declared in this scope
CParser.cpp:55: error: ‘space_p’ was not declared in this scope
CParser.cpp:57: error: ‘instruction’ was not declared in this scope
CParser.cpp:61: error: ‘if_instr’ was not declared in this scope
CParser.cpp:62: error: ‘parentheses’ was not declared in this scope
CParser.cpp:63: error: ‘eps_p’ was not declared in this scope
CParser.cpp:67: error: ‘for_instr’ was not declared in this scope
CParser.cpp:71: error: ‘while_instr’ was not declared in this scope
CParser.cpp:75: error: ‘dowhile_instr’ was not declared in this scope
CParser.cpp:80: error: ‘switch_instr’ was not declared in this scope
CParser.cpp:80: error: ‘switch_head’ was not declared in this scope
CParser.cpp:81: error: ‘switch_body’ was not declared in this scope
CParser.cpp:86: error: ‘switch_case’ was not declared in this scope
CParser.cpp:99: error: expected ‘;’ before ‘special_w’
CParser.cpp:111: error: ‘other_instr’ was not declared in this scope
CParser.cpp:111: error: ‘preprocessor’ was not declared in this scope
CParser.cpp:115: error: ‘comment’ was not declared in this scope
CParser.cpp:119: error: ‘special_w’ was not declared in this scope
CParser.cpp:145: error: ‘parse_info’ was not declared in this scope
CParser.cpp:145: error: expected primary-expression before ‘const’
CParser.cpp:145: error: expected ‘;’ before ‘const’
CParser.cpp:151: error: ‘info’ was not declared in this scope
make[4]: *** [CParser.lo] Error 1
make[4]: Leaving directory `/home/dck/trunk/src/plugins/contrib/NassiShneiderman'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/dck/trunk/src/plugins/contrib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dck/trunk/src/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dck/trunk/src'
make: *** [all-recursive] Error 1
```It seems that some files are missing. I tried downloading the SVN again, and the same thing happened. I have complied codeblocks from SVN many times on Ubuntu 10.04 before, and I have never had this problem. I have updated my computer and installed build-essential and the codeblocks dependencies.

---

### Post by SevenMachines on 2010-07-22
looks like codeblocks is missing a dependency on the boost libraries. try
$sudo apt-get install libboost-dev

that should install the boost-spirit stuff

---

### Post by Eragon0605 on 2010-07-22
Ah, thanks!

---


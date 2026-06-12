---
title: "Trying to compile a program"
date: 2014-09-18
forum: Packaging and Compiling Programs
---

### Post by nikhil6 on 2014-09-18
Hi guys. So as the title state, I'm trying to compile this program [HTML]https://github.com/wsong83/Asynchronous-Verilog-Synthesiser[/HTML] The readme lists all the dependencies that I have solved as I kept moving along. Now I've come to a problem I cant seem to figure out. Here is the output where it's exiting:
```
make -j2 -C cppsaif
make[1]: Entering directory `/home/nikhil/Asynchronous-Verilog-Synthesiser/cppsaif'
ccache g++ -I./  -std=c++0x -Wall -Wextra -g3 -c saif.cc -o saif.o
saif.y:271:38: error: &#8216;location&#8217; in namespace &#8216;saif&#8217; does not name a type
 void saif::saif_parser::error (const saif::location& loc, const std::string& msg) {
                                      ^
saif.y:271:54: error: ISO C++ forbids declaration of &#8216;loc&#8217; with no type [-fpermissive]
 void saif::saif_parser::error (const saif::location& loc, const std::string& msg) {
                                                      ^
saif.y:271:6: error: prototype for &#8216;void saif::saif_parser::error(const int&, const string&)&#8217; does not match any in class &#8216;saif::saif_parser&#8217;
 void saif::saif_parser::error (const saif::location& loc, const std::string& msg) {
      ^
saif.cc:980:3: error: candidates are: void saif::saif_parser::error(const saif::saif_parser::syntax_error&)
   saif_parser::error (const syntax_error& yyexc)
   ^
In file included from saif.cc:84:0:
saif.hh:274:18: error:                 virtual void saif::saif_parser::error(const string&)
     virtual void error (const std::string& msg);
                  ^
make[1]: *** [saif.o] Error 1
make[1]: Leaving directory `/home/nikhil/Asynchronous-Verilog-Synthesiser/cppsaif'
make: *** [cppsaif] Error 2
nikhil@deep-blue:~/Asynchronous-Verilog-Synthesiser$ 


```

Any help as to why this is happening? Thanks a lot!

---


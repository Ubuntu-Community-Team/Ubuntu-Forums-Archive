---
title: "KDevelop qmake application debugging - No source"
date: 2006-09-14
forum: Programming Talk
---

### Post by whizzoman on 2006-09-14
Hi!

I have problem debugging qmake based C++ projects in KDevelop. The debugger can't see the source.

Using KDevelop 3.2.3 I can build and debug a C++ program based on the "Simple Hello world program" template.

In a project based on the "qmake application" project template I can set a breakpoint in the first line after int main(...) in main.cpp and the debugger stops there:
```
int main( int argc, char ** argv ) {
    QApplication a( argc, argv ); //Breakpoint here
    ...
}
```
When I click the button "Step over the next line" I get a brief message "Stopped due to shared library event" and then "No source ..."

In QMake Manager the subproject has build mode "Debug" activated, and I have libqt3-mt-dbg installed.

What should I look for in order to be able to debug qmake based applications, please?

Regards,
Erik

---


---
title: "g++ trouble, problem with structure"
date: 2010-07-21
forum: Programming Talk
---

### Post by lordbux on 2010-07-21
I am having severe trouble with g++;

i was compiling a program and it contained a structure (c++)

```
struct conf{
                //stores all configs required for the program
    int set;
    char wdir[120];
    char kind; //working dir and config type
    char sdir[120];       //server dir
    char pnam[120];       //program name
};
```


but if you notice you will see a error 
(int the belove g++ output **[IN BOLD]**saying that it doesn't have a member called 'set' tho i had declared it.

+ i had compiled this program before many times without any trouble

please help me it is an emergency. 

```
^[[AINSTALLER.cpp: In function &#8216;int termrun(char*)&#8217;:
INSTALLER.cpp:6: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:7: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp: In function &#8216;int termconf()&#8217;:
INSTALLER.cpp:20: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:21: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:36: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:39: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:39: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:47: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:52: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:52: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:63: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:63: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:70: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:70: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:79: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:79: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:81: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp: In function &#8216;int servconf()&#8217;:
INSTALLER.cpp:119: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:120: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:140: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:145: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:145: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:147: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:147: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:149: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:149: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:151: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:151: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:153: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:153: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:155: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:155: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:157: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:157: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:165: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:170: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:170: warning: deprecated conversion from string constant to &#8216;char*&#8217;
**[COLOR="Red"]INSTALLER.cpp:177: error: &#8216;struct conf&#8217; has no member named &#8216;set&#8217;[/COLOR]**
INSTALLER.cpp:184: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:184: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:206: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:206: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:214: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:219: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:219: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:241: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:241: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:247: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:247: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:253: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:253: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:254: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:260: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:260: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:272: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:272: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:274: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:274: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:277: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:278: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp: In function &#8216;int config()&#8217;:
INSTALLER.cpp:301: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp: In function &#8216;void start()&#8217;:
INSTALLER.cpp:324: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:325: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:328: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:329: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:330: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:332: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:333: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:334: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp: In function &#8216;int main()&#8217;:
INSTALLER.cpp:372: warning: deprecated conversion from string constant to &#8216;char*&#8217;
INSTALLER.cpp:377: warning: deprecated conversion from string constant to &#8216;char*&#8217;

```

---

### Post by lordbux on 2010-07-22
BUMP ..........
Its an emergency guys

---

### Post by lordbux on 2010-07-22
Emergency bump

---

### Post by lisati on 2010-07-22
First of all, one bump no earlier than a day after the last post is usually appropriate.

Now to your problem. 
I'm not a C++ programmer but a little bit of research shows that "set" has a special meaning. Have a look here: [http://www.cplusplus.com/reference/stl/set/set/](http://www.cplusplus.com/reference/stl/set/set/)

You might also want to investigate why you are getting the warnings as well.


edit: moved to "Programming Talk"

---

### Post by NovaAesa on 2010-07-22
You're going to have to post more code. It appears to me that struct conf does in fact contain the member 'set' thus the problem must be somewhere else.

---

### Post by dwhitney67 on 2010-07-22
Agreed, don't use *set*, because it is a reserved container name in the STL (std namespace).

If you have a "using namespace std" statement in your header file, then remove it.  It is considered bad practice to include such statements in header files.

As for the warnings, they are caused by defining char pointers to string literals.  For example:
```

char* hw = "Hello World";

```
The appropriate way to declare this is:
```

**const** char* hw = "Hello World";

```
Also, since you are using C++, when appropriate, consider using the STL string versus using predefined sized character arrays.

---


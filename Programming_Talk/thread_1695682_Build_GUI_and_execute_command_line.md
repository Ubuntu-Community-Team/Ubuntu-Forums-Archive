---
title: "Build GUI and execute command line"
date: 2011-02-26
forum: Programming Talk
---

### Post by sid.mallya on 2011-02-26
I am a complete newbie at Linux Development and have no idea how to go about this.

I am using Festival for TTS and using the text2wave function to create an audio file for a given text file. 

What language can I use to build the GUI ? and how do I execute command line statements in it.

I am sorry if these questions are beyond dumb. :popcorn:

---

### Post by hakermania on 2011-02-26
You can use anything you want.
I would suggest Qt Creator (C++).
As for command line executions see the system() function or the QProcess

---

### Post by sid.mallya on 2011-02-26
Thanks for the quick reply ! Okay .. So I got system() working in C++. Can I pass arguments in system tho ? I mean, say I want the name of the input and output files; can I pass them in the system statement ?

---

### Post by cgroza on 2011-02-26
Yes, just build you command line string and then convert it to a C string and execute the system().

---

### Post by sid.mallya on 2011-02-27
```
char command[100];
    strcpy (command, "text2wave ");
    strcat (command, ui->lineEdit->text());
    strcat (command, " -o ");
    strcat (command, ui->lineEdit_2->text());
    if (system(NULL)) {

    system(command);

```

Hey when I use this, I get the error 

```
/home/siddharth/TTS/TactileReader/mainwindow.cpp:34: error: cannot convert &#8216;QString&#8217; to &#8216;const char*&#8217; for argument &#8216;2&#8217; to &#8216;char* strcat(char*, const char*)&#8217;
```

What should I do ?

---

### Post by sid.mallya on 2011-02-27
Nevermind. I got it

---

### Post by hakermania on 2011-02-27
It is better to post your solutions here too :) For anyone following this topic, a google search will definitely help. It helped me at least when searching my own issues with qt  ;P

---

### Post by sid.mallya on 2011-02-27
The QString of QT Creative is native to it and hence does NOT work in the same manner as const char * <name>

The way to convert QString to char string is simply this, (in my example)

const char * command = ui->lineEdit->text().toLocal8Bit().constData();

Done !

---

### Post by juancarlospaco on 2011-02-27
if you dont want to code using a programing language, you can use Zenity and 9Menu...

---


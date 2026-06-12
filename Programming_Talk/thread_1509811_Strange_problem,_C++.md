---
title: "Strange problem, C++"
date: 2010-06-14
forum: Programming Talk
---

### Post by hakermania on 2010-06-14
I am currently working in a GUI program... When pushbutton 6 is clicked this is what it is done:
```
 system("if [ -d /IVS/ ]; then cd /IVS/; else gksudo mkdir /IVS/; cd /IVS/; fi");
    char st1[200]="gksudo \"airodump-ng -w  /IVS/";
    char st2[5]=" -i ";
    char st3[5]=" -c ";
    char st5[50]="echo Done, saved in /IVS; sleep 3";
    char st4[100]="xterm -bg black -fg green -e '";
    strcat(st1,ui->lineEdit_2->text().toAscii());
    strcat(st1,st2);
    strcat(st1,ui->comboBox->currentText().toAscii());
    strcat(st1,st3);
    strcat(st1,ui->comboBox_4->currentText().toAscii());
    strcat(st1,"\"");
    strcat(st1,l);
    strcat(st4,st1);
    system(st4);
    system(st5);

```I have checked it several and several times and system(st4) will be
```
xterm -bg black -fg green -e 'gksudo "airodump-ng -w /IVS/wepnethack  -i wlan0 -c 11"'
```[B]where wepnethack the lineEdit_2->text().toAscii());
where wlan0 the comboBox->currentText().toAscii());
where 11 the comboBox_4->currentText().toAscii());
where l is a char l="'" (a quote)
[/B]If you run this from your gnome-terminal all will be OK, a pop-up asking for your passwd will be poped-up and the program will start (to do this you have to have aircrack-ng installed)... Unfortunately when I push the button the xterm pop-ups with the message "airodump-ng --help", means that there is an error in the airodump-ng command syntax, but believe me, there is no error! I've checked it over 10 times...If there is an error and I cannot see it plz let me know...Oh, and something else, the wrong is maybe in quotes and double quotes...

---

### Post by dwhitney67 on 2010-06-14
Definitely not C++ code.

Read here about the [STL string]("http://www.cplusplus.com/reference/string/string/").

Why don't you use mkdir() to create the directory.  Use stat() to see if it actually exists.  Rather than create the directory relative to the root-dir of your system, place it in the user's home directory.

And the use of the gksudo is disgraceful.  Just run the application as root.  Period.  If the user does not have the elevated privileges of root, then either 1) don't let the user run the program, or 2) present them a version of the application with fewer capabilities.  A good example of option 2 is "wireshark".

---

### Post by nvteighen on 2010-06-15
Please, avoid system() as much as you can, as it makes your program shell-dependent... If you code a call to system(), you may introduce, e.g. bash code that a system using sh by default may not be able to run properly (or run at all)... No, don't tell me this is a personal project because even if it is, that's no excuse to do things wrongly... It's important to get into the good habits.

Use APIs as much as you can. dwhitney67 told you about mkdir(), which is a function in the POSIX API. But not only that, avoid calling programs like you've done with airodump-ng-w, use their APIs... if it's a program written in the tradition of UNIX modularity, it will have a library to link against.

---


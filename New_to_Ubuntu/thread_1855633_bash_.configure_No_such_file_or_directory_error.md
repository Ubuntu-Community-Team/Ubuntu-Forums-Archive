---
title: "bash: ./configure: No such file or directory error"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by insanity werks on 2011-10-06
when trying to install the a canon pixma mp480 which i found the code for I enter what the web site says to enter which is ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var I consequently keep getting this error bash: ./configure: No such file or directory i have look everywhere and cant seem to find an answer and by the way very new to ubuntu and love it so far anyhelp would be appreciated thank you

---

### Post by nothingspecial on 2011-10-06
Hi

Please post the instructions you are following so users can help you.

---

### Post by dniMretsaM on 2011-10-06
You need to be in the correct directory (the directory with the configure file in it):
```
cd /path/to/source/code/
```

Then run
```
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
```

---

### Post by qkall on 2011-10-06
> **insanity werks said:**
> when trying to install the a canon pixma mp480 which i found the code for I enter what the web site says to enter which is ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var I consequently keep getting this error bash: ./configure: No such file or directory i have look everywhere and cant seem to find an answer and by the way very new to ubuntu and love it so far anyhelp would be appreciated thank you

oh this sounds actually kind of simple... i think i can help. you need to move into the directory with said folder.

like 

cd /home/awesomeguy/downloads/canoncrap/

then you should be able to do your command.

---

### Post by m_duck on 2011-10-06
> **qkall said:**
> [COLOR=Red]**cd**[/COLOR] /home/awesomeguy/downloads/canoncrap/

But yes, the ***./configure*** part means execute the configure script which is in the current directory. If you are not in the directory which contains said script, BASH will not be able to find it, hence the error.

---

### Post by qkall on 2011-10-06
> **m_duck said:**
> But yes, the ***./configure*** part means execute the configure script which is in the current directory. If you are not in the directory which contains said script, BASH will not be able to find it, hence the error.

fixed thanks :KS

---

### Post by insanity werks on 2011-10-06
ok what I uderstand is that cd/path to directory would be the directory where the configure script is in . Ok dumb question where is that located in or is there a way of finding it by searching?

---

### Post by insanity werks on 2011-10-06
[LIST]
[*]this is what I'm trying to accomplish I got this off [http://mp610.blogspot.com/](http://mp610.blogspot.com/)    :D:D:D:D:D:D
****
[*]**Build Sane**

Enter the directory [FONT=courier new]sane-backends [/FONT]created after downloading Sane git.

The  procedure is then “almost” classical, with a few points to take into  account instead of running a trivial ./configure, make, make install.

According to your Linux distribution, [COLOR=#FF0000]you need to run the [/COLOR][COLOR=#FF0000][FONT=courier new]./configure[/FONT][/COLOR][COLOR=#FF0000] command with a set of parameters[/COLOR].

As it is not possible to cover here all existing distributions, details are given for Ubuntu and Mandriva, as samples.

For these 2 distributions:
[LIST]
[*][COLOR=#660000]Check first that the development libusb library is present and installed. [/COLOR]

On Mandriva, the rpm is called something like:

*libusb0.1_x-**devel**-...  *

on Ubuntu, it is called: libusb-**dev**.

Install the package, if not already installed.

[COLOR=#FF0000]*Be warned that if not installed, compilation will success, but the backend will not work, and no error message will be prompted!*[/COLOR]
[*][COLOR=#660000]On both distributions, run the .[FONT=courier new]/configure[/FONT] command like this:[/COLOR]

[FONT=courier new]$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var[/FONT]

This will choose [FONT=courier new]/usr/lib/sane[/FONT] as SANE lib directory, [FONT=courier new]/etc/sane.d[/FONT] as SANE config files dir, and [FONT=courier new]/var/lock/sane[/FONT] as state directory: The ones that are used by Mandriva and Ubuntu.

Check in the logs coming in the terminal window, at the end of the configure, that it will compile with usb support.
[*][COLOR=#660000]Then compile as usual[/COLOR]

[FONT=courier new]$ make[/FONT]

This will take ... a significative amount of time ... Can have a cup of coffee.
[*][COLOR=#660000]Install on Ubuntu[/COLOR]

[FONT=courier new]$ sudo make install[/FONT]
[*][COLOR=#660000]Or install on Mandriva[/COLOR]

[FONT=courier new]$ su[/FONT]
[FONT=courier new]# make install[/FONT]
[/LIST]
[/LIST]
****

---

### Post by mutley89 on 2011-10-06
> **insanity werks said:**
> ok what I uderstand is that cd/path to directory would be the directory where the configure script is in . Ok dumb question where is that located in or is there a way of finding it by searching?

When you downloaded it where did you save it to?  If your'e not sure firefox will show recent downloads with ctrl-shift-y.  Then, assuming it's a tarball cd to that directory, run 
```
tar -xvf file
```cd into the directory just extracted then run the configure script.

---


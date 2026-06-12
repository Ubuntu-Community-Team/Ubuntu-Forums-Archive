---
title: "Guide to software install"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by Illusionistik on 2013-03-01
I am trying to install a program for auto typing, but I am so inadequeted. I just need someone to try to explain what to do step by step.

This is the link of the install (autotyper):
[http://www.garyshood.com/rsclient_linux/](http://www.garyshood.com/rsclient_linux/)

Also in the site, but I will link the 'instructions' to download a requirement(xvkbd) here:
[http://homepage3.nifty.com/tsato/xvkbd/#download](http://homepage3.nifty.com/tsato/xvkbd/#download)

It says I also need GTS+ 2.x so an explaination for that would be greatly appreciated.

THANK you so much ahead of time.

---

### Post by Illusionistik on 2013-03-01
I am trying to install a program for auto typing, but I am so  inadequeted. I just need someone to try to explain what to do step by  step.

This is the link of the install (autotyper):
[http://www.garyshood.com/rsclient_linux/](http://www.garyshood.com/rsclient_linux/)

Also in the site, but I will link the 'instructions' to download a requirement(xvkbd) here:
[http://homepage3.nifty.com/tsato/xvkbd/#download](http://homepage3.nifty.com/tsato/xvkbd/#download)

It says I also need GTS+ 2.x so an explaination for that would be greatly appreciated.

THANK you so much ahead of time.

---

### Post by fdrake on 2013-03-01
> **Illusionistik said:**
> I am trying to install a program for auto typing, but I am so  inadequeted. I just need someone to try to explain what to do step by  step.

This is the link of the install (autotyper):
[http://www.garyshood.com/rsclient_linux/](http://www.garyshood.com/rsclient_linux/)

Also in the site, but I will link the 'instructions' to download a requirement(xvkbd) here:
[http://homepage3.nifty.com/tsato/xvkbd/#download](http://homepage3.nifty.com/tsato/xvkbd/#download)

It says I also need GTS+ 2.x so an explaination for that would be greatly appreciated.

THANK you so much ahead of time.

the package in question is available from the repo. Press "ctrl"+ "alt"+"t" and type:
```

sudo apt-get install xvkbd

```
to run check  in the program list for "xvkbd"  or  from the terminal, type
```

xvkbd

```

---

### Post by fdrake on 2013-03-01
don't creat double threads1

---

### Post by lisati on 2013-03-01
*Threads merged*

Please do not start multiple threads for the same support request, it dilutes the forum's ability to help.

---

### Post by Illusionistik on 2013-03-02
yeah sorry, about the posting. 

Now I installed and ran it but I only get the virtual keyboard, which is nice (because I dont think ubuntu has one). Bu the actual program i was trying to install was the autotyper. and the xvkdb was the requirement, so maybe thats just 1 step.

Again thanks sofar, just need help doing the next (final?) step of installing the actual autotyper at the top of the first link:
[http://www.garyshood.com/rsclient_linux/](http://www.garyshood.com/rsclient_linux/)

AKA which one do I install? and how would I do it.

---

### Post by fdrake on 2013-03-02
> **Illusionistik said:**
> yeah sorry, about the posting. 

Now I installed and ran it but I only get the virtual keyboard, which is nice (because I dont think ubuntu has one). Bu the actual program i was trying to install was the autotyper. and the xvkdb was the requirement, so maybe thats just 1 step.

Again thanks sofar, just need help doing the next (final?) step of installing the actual autotyper at the top of the first link:
[http://www.garyshood.com/rsclient_linux/](http://www.garyshood.com/rsclient_linux/)

AKA which one do I install? and how would I do it.
 
METHOD -1
we need to know about your system first:
give as the result of these command:
```

uname -a

```




METHOD-2 (Not suggested)

If you know waht you are doing you can build it from source.
Long way : build from source
always in the terminal , follow these comands: (just copy and paste exactly like here; do not try to type it, you may mistype it)
```

wget -O autotyper.c "http://www.garyshood.com/rsclient_linux/download.php?d=source"
gcc -Wall -g autotyper.c -o autotyper `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`

```

---

### Post by Illusionistik on 2013-03-02
Linux Beast 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:05:29 UTC 2013 i686 i686 i686 GNU/Linux

the results, and yeah I would prefer going the easier route.

---

### Post by fdrake on 2013-03-02
> **Illusionistik said:**
> Linux Beast 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:05:29 UTC 2013 i686 i686 i686 GNU/Linux

the results, and yeah I would prefer going the easier route.

download autotyper-x86.tar.gz 
and then type into the terminal
```

tar xvzf ~/Downloads/autotyper-x86.tar.gz
(###output) autotyper
./autotyper

```

---

### Post by fdrake on 2013-03-02
you can run the program by typing "~/autotyper". Or just doubloe click it in your home directory.

---

### Post by Illusionistik on 2013-03-02
beast@Beast:~$ tar xvzf ~/Downloads/autotyper-x86.tar.gz
tar (child): /home/beast/Downloads/autotyper-x86.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now



^ what i get when I only type in first cmd. (sorry wasn't sure if you wantd me to copy/paste 1 line or all 3 you gave me)

and this is what i got when I tried to put all commands in:

beast@Beast:~$ tar xvzf ~/Downloads/autotyper-x86.tar.gz (###output) autotyper ./autotyper
bash: syntax error near unexpected token `('
beast@Beast:~$ tar xvzf ~/Downloads/autotyper-x86.tar.gz
tar (child): /home/beast/Downloads/autotyper-x86.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

maybe I am doing something wrong?

---

### Post by Illusionistik on 2013-03-02
nvm i got it withj your last post, what was with the other commands you wanted me to put in?

THANK YOU by the way!

---

### Post by Illusionistik on 2013-03-02
Well on your last post I did it and the program ran, but it looks like it isn't working, but i posted my errors on my last post, didnt want to edit it incase you wouldnt see this. 

I am pretty sure I downloaded it wrong, thats my main thing with linux I don't know how to extract the file or place it into a correct directory? maybe thats what i did wrong for your commands to not be working. Possibly we skipped the install requirement of GTK 2. (?) because the app run just doesnt work.


beast@Beast:~$ ~/autotyper
Process 31312 about to fork a child.
Created child process 31315.
xvkbd -text "2
\r"
Warning: Cannot convert string "-*-lucidatypewriter-bold-r-*-*-12-*-*-*-*-*-iso8859-1" to type FontStruct
xvkbd: Mode_switch not available as a modifier
xvkbd: although ISO_Level3_Shift is used instead, AltGr may not work correctly
Dupe detected.
Process 31315 about to fork a child.
Created child process 31318.
Cannot open file.
Cannot open file.

what i got when i opened the autotyper with ~/autotyper then tried using it.

---

### Post by fdrake on 2013-03-02
> **Illusionistik said:**
> 
It says I also need GTS+ 2.x so an explaination for that would be greatly appreciated.


what is GTS+ 2.x? are you talking about gtk? I am not an expert of this software .. where did you get that info? post link or quote the text.

I do not know why is not working, but you need to give us all the info you can about this program.

---

### Post by Illusionistik on 2013-03-02
[http://www.garyshood.com/rsclient_linux/](http://www.garyshood.com/rsclient_linux/)

^ in the requirements you helped me get the xvkbd software. (check)
then we got the actual app I needed (but it looks like we skipped the other requirement) 
its the GTS right under the requirements section, it says its required but no link to a download path. thats probably what I am missing and will try searching for it.

---

### Post by fdrake on 2013-03-02
> **Illusionistik said:**
> [http://www.garyshood.com/rsclient_linux/](http://www.garyshood.com/rsclient_linux/)

^ in the requirements you helped me get the xvkbd software. (check)
then we got the actual app I needed (but it looks like we skipped the other requirement) 
its the GTS right under the requirements section, it says its required but no link to a download path. thats probably what I am missing and will try searching for it.

the link says GTK, not GTS!
> 
You will also need GTK+ 2.x. Once you have those two requirements, you can run the auto typer. It will work in any X program, and can be used as an alternative to the Windows Runescape Auto Typer. Future updates will be located here. 


check the version that you are using , but still there is no why to be sure that this is the error.
```

dpkg -l | grep libgtk


```
probably version 3 is not recognized by the program... have you tried contacting/emailing the developer?

---

### Post by Illusionistik on 2013-03-02
beast@Beast:~$ dpkg -l | grep libgtk
ii  libgtk-3-0:i386                           3.6.0-0ubuntu3.2                          i386         GTK+ graphical user interface library
ii  libgtk-3-bin                              3.6.0-0ubuntu3.2                          i386         programs for the GTK+ graphical user interface library
ii  libgtk-3-common                           3.6.0-0ubuntu3.2                          all          common files for the GTK+ graphical user interface library
ii  libgtk2-perl                              2:1.244-1ubuntu1                          i386         Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0:i386                          2.24.13-0ubuntu2                          i386         GTK+ graphical user interface library
ii  libgtk2.0-bin                             2.24.13-0ubuntu2                          i386         programs for the GTK+ graphical user interface library
ii  libgtk2.0-common                          2.24.13-0ubuntu2                          all          common files for the GTK+ graphical user interface library
ii  libgtkmm-2.4-1c2a:i386                    1:2.24.2-1ubuntu2                         i386         C++ wrappers for GTK+ (shared libraries)
ii  libgtkmm-3.0-1:i386                       3.5.13-0ubuntu1                           i386         C++ wrappers for GTK+ (shared libraries)
ii  libgtksourceview-3.0-0:i386               3.6.0-0ubuntu1                            i386         shared libraries for the GTK+ syntax highlighting widget
ii  libgtksourceview-3.0-common               3.6.0-0ubuntu1                            all          common files for the GTK+ syntax highlighting widget
ii  libgtkspell-3-0                           3.0.0~hg20110814-1build1                  i386         spell-checking addon for GTK's TextView widget


thats what I got ^

and haven't contacted them yet, just wanna see if I can get it working before I have to waste more peoples time like yours =[

edit: another problem that could be wrong is just how I downloaded it. all i did was download it and opened the folder and dragged it to my desktop, could have done something wrong there?

---

### Post by fdrake on 2013-03-02
i will take a look at the source code of "autotyper.c" and see if by changing some values does the trick.  BTW they did not put any comments, in the code , it will take some time to figure it out . I'll let you know tonight if I find something....

---

### Post by Illusionistik on 2013-03-02
yeah I am in no rush I will be on for a bit longer also so if you need me to do anything post away.

---

### Post by Illusionistik on 2013-03-02
> **fdrake said:**
> i will take a look at the source code of "autotyper.c" and see if by changing some values does the trick.  BTW they did not put any comments, in the code , it will take some time to figure it out . I'll let you know tonight if I find something....

Look at my earlier post when I pasted what I got from my terminal  with your command " tar xvzf ~/Downloads/autotyper-x86.tar.gz "

beast@Beast:~$ tar xvzf ~/Downloads/autotyper-x86.tar.gz

tar (child): /home/beast/Downloads/autotyper-x86.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now 

I am pretty sure that is where the error may lie, just me downloading the file incorrectily or just not putting it in the correct directory?

---


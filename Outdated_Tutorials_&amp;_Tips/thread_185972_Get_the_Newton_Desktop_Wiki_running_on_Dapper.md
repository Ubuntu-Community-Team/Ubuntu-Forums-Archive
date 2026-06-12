---
title: "Get the Newton Desktop Wiki running on Dapper"
date: 2006-06-01
forum: Outdated Tutorials &amp; Tips
---

### Post by dpm on 2006-06-01
[SIZE=5][B][U][COLOR=black]Introduction

[/COLOR][/U][/B][/SIZE] Quoting the project's homepage ([http://newton.sourceforge.net](http://newton.sourceforge.net)) : Newton is a desktop wiki applet for the GNOME2 desktop environment. You enter your notes and information in a simple wiki-like syntax and Newton formats it in rich HTML for you! It is designed to make the creation of richly formatted documents of any type as simple and quick as possible.

The author provided a .deb package for ubuntu of the stable version of Newton some time ago, which used to work very well on Breezy. However, due to this bug ([https://launchpad.net/bugs/26436](https://launchpad.net/bugs/26436)) in the ***gtkmozembed*** widget, which Newton uses to display HTML content, Newton does not work anymore in Dapper -it simply exits with a segmentation fault upon start.

Well, it seems that the bug will not be fixed before Dapper release, so after reading the comments on the bug report in Malone, I found out that there is a workaround (not a fix) to get Newton running in Dapper. The purpose of this guide is to give some instructions on how to apply this simple workaround.

This will work for both the stable version of Newton, available as a .deb package as already mentioned, and also for the current development version. The workaround implies creating a custom launcher on the gnome panel that will launch a script which will ultimately invoke Newton. 

Notice that I'm not making any claims that this will work for everybody. At least it seems to work on the two computers where I've tested it. Therefore, I would appreciate any feedback on whether it is working for other people or not. Thanks.

[B][U][SIZE=5]Stable Version

[/SIZE][/U][/B] You can get the stable ubuntu package here: [http://prdownloads.sourceforge.net/newton/newton_0.0.9-2_all.deb?download](http://prdownloads.sourceforge.net/newton/newton_0.0.9-2_all.deb?download) 

Since in the stable version Newton is initially launched as a gnome applet, it is maybe not so nice to invoke it from a custom launcher, as it will first create a tiny window containing the applet, which will have to be clicked once more to launch the Newton GUI.

Anyway, first create the script to invoke Newton (copy the following text to a file named **newton.sh**):

```
#!/usr/bin/env bash
  
export LD_LIBRARY_PATH=/usr/lib/firefox && newton test
``` 
Once the file has been saved, make it executable by executing the following command at the terminal:
```
chmod 755 newton.sh
``` 
That's it. Now you can jump to the '**Creating a Custom Launcher for Newton on the GNOME Panel**' section.


[SIZE=5][U][B] Development Snapshot in SVN
[SIZE=4]
[/SIZE] [/B] [/U][/SIZE][SIZE=4]**Getting and installing the development snapshot**[/SIZE] 

If you feel that the development version is better suited to your needs, here are the instructions necessary to get it working. The advantages of this version are the ability to create categorised pages, wiki syntax highlight and the possibility to launch Newton as a standalone application from the custom application launcher in the gnome panel. This, of course, at the potential risk of running a development version -which seems to be quite stable for me so far. 

You'll be better off following the excellent Newton installation instructions ([http://newton.sourceforge.net/install.html](http://newton.sourceforge.net/install.html)) from the project's site, but in case you've got subversion and the necessary development packages for compilation already installed, you can just quickly type this in order to compile and install Newton:

```
svn co [http://arker.homelinux.org/Pub/newton/trunk](http://arker.homelinux.org/Pub/newton/trunk) newton
``` 
```
./autogen.sh --prefix=/usr 
  sudo make install
``` 
[SIZE=4]**Creating the script**[/SIZE]

Create the script to invoke Newton (copy the following text to a file named **newton.sh**):
  
```
#!/usr/bin/env bash
  
export LD_LIBRARY_PATH=/usr/lib/firefox && newton
``` 
Once the file has been saved, make it executable by executing the following command at the terminal:
```
chmod 755 newton.sh
``` 
_[SIZE=5]**Creating a Custom Launcher for Newton on the GNOME Panel**[/SIZE]_[LIST=1]
[*] Right-click on the panel and select 'Add to Panel...'
[*]On the 'Add to Panel' dialogue, click on the 'Custom Application Launcher' button (or press ALT+L)
[*]Type "Newton" (without quotes) in the 'Name' text field
[*]Type the location of the **newton.sh**  script we previously created in the 'Command' text field.
[*]Optionally, choose /usr/share/newton/pixmaps/newton.svg as the custom launcher's icon.
[*]Click 'Ok'. The custom application launcher is ready for use.[/LIST]That's it, now you should be able to click on the newly-created Newton application launcher on the gnome panel and start Newton as usual.

Here's a screenshot of Newton running on Dapper:

---

### Post by mcarlson on 2006-06-02
This worked for me with the 0.9.2 deb package available from the Newton site.
I might try the svn version soon.

Thank you

---

### Post by dcraven on 2006-06-03
Nice job desp, thanks for that. Now if we can only figure out how to get the applet to work too. It seems setting env variables in a parent process is a no go, so it doesn't look like it'll work through some added Python code.

Thanks again :)
~djc

---

### Post by spanella47 on 2006-06-03
script doesnt run here. 

getting the following when compiling: (just a snippet, rest looks fine)

```
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize...
Running aclocal-1.7...
Running autoconf...

```

ideas?

---

### Post by dcraven on 2006-06-03
[QUOTE=spanella47]script doesnt run here. 

getting the following when compiling: (just a snippet, rest looks fine)

[...]
ideas?[/QUOTE]

Try apt-getting the "gettext" package. I think that might help. This is the SVN version I assume?

Cheers,
~djc

---

### Post by spanella47 on 2006-06-03
yeah this is the svn.

and i've apparently already got the newest gettext.  also got gnulib thinking that might help because it has more macros, but no dice.

either way, sounds like a useful program, hopefully the devs can get it working regularly soon.

---

### Post by dcraven on 2006-06-03
[QUOTE=spanella47]yeah this is the svn.

and i've apparently already got the newest gettext.  also got gnulib thinking that might help because it has more macros, but no dice.

either way, sounds like a useful program, hopefully the devs can get it working regularly soon.[/QUOTE]
I **am** the dev (singular) :). To be honest, I don't really see an error in your original quoted text. I just assumed you took the "Please add these files.." bit as an error or something and I saw that iconv.m4 comes with gettext, so I suggested installing it :).

How do you know there is an error? As I said, your original quote doesn't indicate a failure unless I'm missing something.

Cheers,
~djc

---

### Post by spanella47 on 2006-06-03
ok, didnt know if by missing those files it wasnt compiling correctly.  still doesnt work, but could be something else.  Is there a way to run in the terminal so I can see the output and be more specific?

---

### Post by dcraven on 2006-06-04
[QUOTE=spanella47]Is there a way to run in the terminal so I can see the output and be more specific?[/QUOTE]
Sure. If the suggested solution works on your system then you can run Newton by typing the following at a terminal:
```
LD_LIBRARY_PATH=/usr/lib/firefox newton
```

Cheers,
~djc

---

### Post by dpm on 2006-06-04
[quote=mcarlson]This worked for me with the 0.9.2 deb package available from the Newton site.
I might try the svn version soon.

Thank you[/quote] 
Glad to hear that.

[quote=dcraven]Nice job desp, thanks for that. Now if we can only figure out how to get the applet to work too. It seems setting env variables in a parent process is a no go, so it doesn't look like it'll work through some added Python code.

Thanks again :)
~djc[/quote] 
Thanks. Just a minor contribution to your great app. 

I've been thinking about that, but I just can't figure out how to do it. Call me a dreamer, but I'm still hoping that the ubuntu dev's will figure a way how to solve the gtkmozembed bug. And if we're lucky, some security bug will be found in the python-gnome2-extras package, which will ultimately lead to the package being security-updated and made available to us.

Now that was some wishful thinking... :-?

Anyway, I'm glad to hear this howto made someone's Newton resuscitate on Dapper.

Cheers.

---

### Post by spanella47 on 2006-06-04
[QUOTE=dcraven]Sure. If the suggested solution works on your system then you can run Newton by typing the following at a terminal:
```
LD_LIBRARY_PATH=/usr/lib/firefox newton
```

Cheers,
~djc[/QUOTE]

that works, thanks.  script still doesn't do anything though.

---

### Post by dcraven on 2006-06-04
[QUOTE=spanella47]that works, thanks.  script still doesn't do anything though.[/QUOTE]
Hmmm.. That line that works for you essentially *is* the script :).

Cheers,
~djc

---

### Post by Teddy_P on 2006-07-15
Thank you I just downloaded 0.0.9 and it works now I can start learning.

Thanks again
Teddy

---

### Post by joecomstock on 2006-07-16
I am getting a error when running the custom launcher   

Details: Failed to execute child process "/home/joe/newton.sh" (Permission denied)

I created the file as my normal user without sudo......

not sure where the permission issue is cropping up.....if it matters I am using XGL and Compiz

Thanks

---

### Post by ak47surve on 2006-07-17
Thnks it wrkd for me !

[www.akshaysurve.com]("http://www.akshaysurve.com")

---

### Post by dpm on 2006-07-17
> **joecomstock said:**
> I am getting a error when running the custom launcher   

Details: Failed to execute child process "/home/joe/newton.sh" (Permission denied)

I created the file as my normal user without sudo......

not sure where the permission issue is cropping up.....if it matters I am using XGL and Compiz

Thanks

What are the permissions of the script?

What happens when you execute the script from the terminal?

What version of Newton did you install and how?

Otherwise, if this is really an issue with xgl/compiz, I'm afraid I can't help you there. I gave up trying to get xgl running a long time ago. Now I'm waiting for it to get stable before giving it another go.

Cheers.

---

### Post by LKRaider on 2006-07-28
I cannot get it to build inside a pbuilder environment.

Firstly, the debian/control was missing the cdbs package. Also, the svn doesn't contains ./configure, but adding a ./autogen.sh rule to the debian file made it complain about missing m4 macros.
I copied *only* the missing configure files from the stable release, it compiled, but after installation and trying to run from the terminal (with the script you posted), it complains like this:
```
Traceback (most recent call last):
  File "/usr/bin/newton", line 3, in ?
    from newton import NewtonMain
ImportError: cannot import name NewtonMain
```

Is there a way to make it build correctly under pbuilder?

---

### Post by kvalis on 2006-08-16
Tried your advice.

In the command field I entered /home/tore/newton.sh

Got a popup window with the following message:

> Could not launch application

Details: Failed to execute child process "/home/tore/newton.sh" (Permission denied)

What can I do??

Kvalis

---

### Post by kvalis on 2006-08-19
Apparently I had to make the script executable!

The commannd:

> root@ubuntu:~# chmod 755 /home/tore/newton.sh

Thanks to Dennis Craven


Kvalis

---

### Post by dpm on 2006-08-29
> **kvalis said:**
> Apparently I had to make the script executable!

The commannd:


Thanks to Dennis Craven


Kvalis

I updated the HOW-TO accordingly -added a note on how to make the script executable.

Thanks.

---

### Post by shemminga on 2007-03-04
An easier fix is to add /usr/lib/firefox to /etc/ld.so.conf and to run ldconfig (as root). This will also work for the applet. (Tested that for SVN.)

I've added a more detailed description to the bug report in Launchpad: [https://launchpad.net/ubuntu/+source/firefox/+bug/26436](https://launchpad.net/ubuntu/+source/firefox/+bug/26436)

---


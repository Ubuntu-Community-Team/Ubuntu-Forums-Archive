---
title: "Help creating a &quot;program&quot;..."
date: 2009-01-14
forum: Programming Talk
---

### Post by gjoellee on 2009-01-14
Hi! I have just started making a "program" which will act just as some kind of website. You install it bu running a bash script, and you launch it from any web browser that can launch .html files form a directory. You do not require Internet to use the program, it installs to a directory on your machine.

What the "program" will do is helping configuring your Ubuntu installation in an advanced way or easy way. I do however have some questions for the program I am going to make:

1. Is there any way to make the terminal open and launch a bash script automatically just by clicking on a button/link in the web browser?

2. Is there any way to make a bash script simply edit a file, ie: the xorg.conf? When I mean edit I mean like edding a few lines to the files, and not replacing it with an other file).

Any links, tips would be greatful...

---

### Post by jimi_hendrix on 2009-01-14
1. you will need to mod your browser afaik
2. yes but i dont know how to do it easily (other then echo "foo" > bar.txt)

---

### Post by eye208 on 2009-01-14
1. No, because this would be a HUGE security hole.
2. There are probably ways to do that, but the script would require root privileges. That would make the above security issue even worse.

---

### Post by alxlabs on 2009-01-14
You have to create your own server which will be able handling requests from your browser and do what you need to modifying the files. Look into this - [http://www.linuxhowtos.org/C_C++/socket.htm](http://www.linuxhowtos.org/C_C++/socket.htm)

---

### Post by alxlabs on 2009-01-14
...Well...then why not to create a program which will help tweaking .conf files instead of creating client-server thing?

---

### Post by eye208 on 2009-01-14
> **alxlabs said:**
> You have to create your own server which will be able handling requests from your browser and do what you need to modifying the files. Look into this - [http://www.linuxhowtos.org/C_C++/socket.htm](http://www.linuxhowtos.org/C_C++/socket.htm)
Regular Apache + CGI could be configured to do that too, but it just sounds like a very very bad idea.

---

### Post by alxlabs on 2009-01-14
> **eye208 said:**
> Regular Apache + CGI could be configured to do that too, but it just sounds like a very very bad idea.

well..it means that person whom author wants to help has to have apache installed and running it as root :D 
Personally I wouldn't do it that way...it is better idea to write own app without messing up with http...i guess

---

### Post by eye208 on 2009-01-14
> **alxlabs said:**
> well..it means that person whom author wants to help has to have apache installed and running it as root :D
Not Apache itself, but the CGI program would require the suid flag to be set. Anyway, it's still dangerous.

---

### Post by mssever on 2009-01-14
> **alxlabs said:**
> You have to create your own server which will be able handling requests from your browser and do what you need to modifying the files. Look into this - [http://www.linuxhowtos.org/C_C++/socket.htm](http://www.linuxhowtos.org/C_C++/socket.htm)
While I agree with the others that setting up a webserver for this task doesn't make a whole lot of sense, it also doesn't make sense to recommend a tutorial on C and C++ sockets when you can write a complete basic HTTP server in ~4 lines of Python. Much easier.
> **kiloraw said:**
> Hello, I am having some trouble with the school work that i m doing. This is my assignment below: 
Your shell script needs to contain a hashpling and comments. It should perform the following tasks:

1Displays a list of currently logged in users 
2Displays the time and date 
3Displays the current working directory 
4Asks the user their name, reads in their name 
5Creates a directory under /home with the user’s name 
6Changes the permissions for the new directory to rwx 
I am having problems with four, five, and six. the others i used the echo command......is that right? i will post later this evening after work what I have done. Hope this was ok to post, my teacher said i could use the forums for help.And since i use Linux(ubuntu) now, I thought this would be the best place for help.
You should post this in its own thread instead of hijacking a thread for an unrelated question.

---

### Post by Tomosaur on 2009-01-14
It would be far easier to just write a normal (compiled) program to do this than doing it in such a roundabout and convoluted way. Forget about the browser idea - it's going to give you headaches on a massive scale.

> **mssever said:**
> 
You should post this in its own thread instead of hijacking a thread for an unrelated question.

Or he should do his own homework :P

---

### Post by eye208 on 2009-01-15
> **mssever said:**
> While I agree with the others that setting up a webserver for this task doesn't make a whole lot of sense, it also doesn't make sense to recommend a tutorial on C and C++ sockets when you can write a complete basic HTTP server in ~4 lines of Python. Much easier.
Why is it that every time someone mentions writing code in C/C++, a Python fanboy chimes in?

You can't write a web server in ~4 lines of Python. All you can do is import *someone else's webserver* in ~4 lines of Python. And guess what, you can do the same thing in any other language. For example, in C you would use [libmicrohttpd](http://www.gnu.org/software/libmicrohttpd/):
> GNU libmicrohttpd is a small C library that is supposed to make it easy to run an HTTP server as part of another application. GNU libmicrohttpd is free software and part of the GNU project. Key features that distinguish libmicrohttpd from other projects are:

    * C library: fast and small
    * API is simple, expressive and fully reentrant
    * Implementation is http 1.1 compliant
    * HTTP server can listen on multiple ports
    * Support for IPv6
    * Support for incremental processing of POST data
    * Creates binary of only 30k (without TLS/SSL support)
    * Three different threading models
    * Supported platforms include GNU/Linux, FreeBSD, OpenBSD, NetBSD, OS X, W32 and z/OS

libmicrohttpd was started because the author needed an easy way to add a concurrent HTTP server to other projects. Existing alternatives were either non-free, not reentrant, standalone, of terrible code quality or a combination thereof. Do not use libmicrohttpd if you are looking for a standalone http server, there are many other projects out there that provide that kind of functionality already. However, if you want to be able to serve simple WWW pages from within your C or C++ application, check it out.

---

### Post by jpkotta on 2009-01-15
You mean like [webmin]("http://www.webmin.com/")?

---

### Post by mssever on 2009-01-15
> **eye208 said:**
> Why is it that every time someone mentions writing code in C/C++, a Python fanboy chimes in?

You can't write a web server in ~4 lines of Python. All you can do is import *someone else's webserver* in ~4 lines of Python. And guess what, you can do the same thing in any other language. For example, in C you would use [libmicrohttpd]("http://www.gnu.org/software/libmicrohttpd/"):
Wow. That's the first time I've been called a Python fanboy. Python isn't even my favorite language.

My point is that it doesn't make sense to write something (a webserver in this case) from scratch when a library exists to do the same thing. Using only the standard library, you can write a webserver in only a few lines of code (I stand by the term "write" since the ratio of my code to library code is unimportant). You mentioned a C library that apparantly does the same type of thing, though it isn't part of the standard library (because C doesn't really work that way). Great. That doesn't change my point at all, because my point wasn't to advocate Python; it was to say that mucking about with sockets and other such stuff was unnecessary if the goal was to make a basic webserver.

---

### Post by gjoellee on 2009-01-15
> **jpkotta said:**
> You mean like [webmin]("http://www.webmin.com/")?

Interesting... I am taking a look at this at the moment!

---

### Post by gjoellee on 2009-01-15
Webmin is something that ain't to far away from what I want to create. However a friend told me about server running just on the machine, I think it was called "localhost". That would make me able to use PHP instead of HTML which will spare me for a lot of time!

Can anyone give some howtos on how to set up "lockalhost"? NOTE: I am running Arch Linux. I will be Googleing some about this now as well...

---

### Post by mssever on 2009-01-15
> **gjoellee said:**
> Can anyone give some howtos on how to set up "lockalhost"? NOTE: I am running Arch Linux. I will be Googleing some about this now as well...
localhost is your computer. There's nothing to set up.

---

### Post by jespdj on 2009-01-15
> **kiloraw said:**
> Hello, I am having some trouble with the school work that i m doing. This is my assignment below: 
Your shell script needs to contain a hashpling and comments. It should perform the following tasks:
Don't hijack someone else's forum thread.

---

### Post by simz on 2009-01-16
> **gjoellee said:**
> Webmin is something that ain't to far away from what I want to create. However a friend told me about server running just on the machine, I think it was called "localhost". That would make me able to use PHP instead of HTML which will spare me for a lot of time!

Can anyone give some howtos on how to set up "lockalhost"? NOTE: I am running Arch Linux. I will be Googleing some about this now as well...

What I said was that if you installed XAMPP for Linux (LAMPP) you would be able to access a page made with PHP via localhost, port 80 because that is where the webserver usually puts itself.

-simz

---

### Post by mssever on 2009-01-16
> **simz said:**
> What I said was that if you installed XAMPP for Linux (LAMPP) you would be able to access a page made with PHP via localhost, port 80 because that is where the webserver usually puts itself.

-simz
XAMPP is fine on Windows, but it's kind of pointless on Linux. Why install something non-packaged, in a non-standard location, with wide-open security holes, when installing a *real* server is so easy in Linux? And, you get updates automatically. ```
sudo tasksel
```Choose LAMP Server.

---

### Post by gjoellee on 2009-01-16
> **mssever said:**
> XAMPP is fine on Windows, but it's kind of pointless on Linux. Why install something non-packaged, in a non-standard location, with wide-open security holes, when installing a *real* server is so easy in Linux? And, you get updates automatically. ```
sudo tasksel
```Choose LAMP Server.

```

$ sudo tasksel
sudo: tasksel: command not found

```

wondering...

---

### Post by mssever on 2009-01-16
> **gjoellee said:**
> ```

$ sudo tasksel
sudo: tasksel: command not found

```wondering...
Oh, I just noticed that you're running Arch. tasksel is Ubuntu-specific. For Arch, just install your Arch packages for the various components (Apache, MySQL, PHP, etc.).

---

### Post by gjoellee on 2009-01-16
I followed this tutorial: [http://wiki.archlinux.org/index.php/LAMP](http://wiki.archlinux.org/index.php/LAMP) it is the right one, right?

However I got into a problem...localhost runs fine, but when I add the design which is found here: [http://www.oswd.org/design/preview/id/3515](http://www.oswd.org/design/preview/id/3515) (which is a good template to customize, and it already kind of looks good). I renamed the file to "index.php" and when the page loads, I get a white screen, no, nothing!

I am no master at debugging, but from my experience it might have something to do with the first lines in the code for the file "index.php". They look like this:
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<html>

```

---

### Post by mssever on 2009-01-16
> **gjoellee said:**
> I followed this tutorial: [http://wiki.archlinux.org/index.php/LAMP](http://wiki.archlinux.org/index.php/LAMP) it is the right one, right?I'm not an Arch user, so I have no idea.

> However I got into a problem...localhost runs fine, but when I add the design which is found here: [http://www.oswd.org/design/preview/id/3515](http://www.oswd.org/design/preview/id/3515) (which is a good template to customize, and it already kind of looks good). I renamed the file to "index.php" and when the page loads, I get a white screen, no, nothing!

I am no master at debugging, but from my experience it might have something to do with the first lines in the code for the file "index.php". They look like this:
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<html>

```
Have you viewed the page source in your browser? Do you know PHP? Perhaps you could post the problem file.

---

### Post by gjoellee on 2009-01-20
> **mssever said:**
> I'm not an Arch user, so I have no idea.


Have you viewed the page source in your browser? Do you know PHP? Perhaps you could post the problem file.

I do not know a lot of PHP, but I am willing to take the challenge. The page source contains nothing. I have however changed my plans...Instead of creating all those files and so on...why not use Drupal? So I am going to use Drupal. I am Googeling around a little to find some answer....however thanks for the help so far.

I might come asking mroe quesitons soon...

---

### Post by gjoellee on 2009-01-21
> **jimi_hendrix said:**
> 
2. yes but i dont know how to do it easily (other then echo "foo" > bar.txt)

I didn't really catch that one. If anyone could give a full script where I must add this line:
```
ILoveCady
```into this file like you see under the OPTIONS tag: 
```
#
# /etc/pacman.conf
#
# See the pacman manpage for option directives

#
# GENERAL OPTIONS
#
[options]
ILoveCandy
# The following paths are commented out with their default values listed.
# If you wish to use different paths, uncomment and update the paths.
#RootDir     = /
#DBPath      = /var/lib/pacman/
#CacheDir    = /var/cache/pacman/pkg/
#LogFile     = /var/log/pacman.log
HoldPkg     = pacman glibc
#XferCommand = /usr/bin/wget --passive-ftp -c -O %o %u

#
# REPOSITORIES
#   - can be defined here or included from another file
#   - pacman will search repositories in the order defined here
#   - local/custom mirrors can be added here or in separate files
#   - repositories listed first will take precedence when packages
#     have identical names, regardless of version number
#
# Repository entries are of the format:
#       [repo-name]
#       Server = ServerName
#       Include = IncludePath
#
# The header [repo-name] is crucial - it must be present and
# uncommented to enable the repo.
#

# Testing is disabled by default.  To enable, uncomment the following
# two lines.  You can add preferred servers immediately after the header,
# and they will be used before the default mirrors.
[testing]
Server = ftp://ftp.gigabit.nu/testing/os/i686/

[core]
Server = ftp://ftp.gigabit.nu/core/os/i686/

[extra]
Server = ftp://ftp.gigabit.nu/extra/os/i686/

[community]
Server = ftp://ftp.gigabit.nu/community/os/i686/

[muflax-xfce4-svn]
Server = http://www.stud.uni-karlsruhe.de/~uvcal/xfce4-svn/i686/

[archlinuxfr]
Server = http://repo.archlinux.fr/i686

[compiz-fusion]
Server = http://compiz.dreamz-box.de/i686

# Unstable is disabled by default.  To enable, uncomment the following
# two lines.  You can add preferred servers immediately after the header,
# and they will be used before the default mirrors.
#[unstable]
#Include = /etc/pacman.d/mirrorlist

```

Note: I cannot replace the file, because a lot of people have a lot of different configurations for it.

---

### Post by mssever on 2009-01-21
> **gjoellee said:**
> I didn't really catch that one. If anyone could give a full script where I must add this line:
```
ILoveCady
```into this file like you see under the OPTIONS tag: 
jimi_hendrix's example only works if you're writing the entire file, overwriting everything that was already there. Google for how to do redirection in Bash.

But to do what you want, you really need a tool that knows how to parse and modify your file. Of course, for each file format, you need a different parser. Some cases are simple enough to handle, such as the case where you need to append something to the end of the file without regerd for whatever else might be in the file. Other cases are more complex. In those cases, there probably aren't any pre-made tools available for Bash, since anyone who tries something like that in Bash is probably mildly insane.

---

### Post by gjoellee on 2009-01-22
Thanks for the tip, I have been searching in Google, but for the wrong things. I found a really nice website with bash tutorials.

---


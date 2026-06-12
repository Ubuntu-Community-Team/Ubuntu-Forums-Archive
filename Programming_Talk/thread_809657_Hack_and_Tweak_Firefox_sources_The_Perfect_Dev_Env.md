---
title: "Hack and Tweak Firefox sources: The Perfect Dev Environment"
date: 2008-05-27
forum: Programming Talk
---

### Post by skaber on 2008-05-27
Here is a tutorial I wrote to get you setup quickly in a complete development environment to hack or tweak Firefox's source code. These steps should also work for any other mozilla product. The difference would only be changing the debugged application and the working directory.

This post was originally posted on [The Perfect Firefox (Mozilla) Development Environment]("http://www.francisrobichaud.com/index.php/2008/05/27/the-perfect-firefox-devenv/")

Here are some pretty straight forward steps to quickly get a development environment based on the Eclipse IDE. The tools in this environment are

    * Eclipse with the Eclipse-CDT platform
    * Distcc - a distributed C/C++ compiler
    * Mozilla Framework - the base framework used for Mozilla projects

Note: Mozilla has great documentation to help building any of their application. Please have a look there before posting any question. The #developers irc.mozilla.org channel is also a good start.

This tutorial assumes you&#8217;re using Ubuntu or a similar distro.

**Build and configure Firefox**

1. Install required tools and Firefox dependencies

```
sudo apt-get install cvs distcc eclipse eclipse-cdt libcurl4-openssl-dev distccmon-gnome
sudo apt-get build-dep firefox

```

2. Get the Firefox source

TAR :

```
wget [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.0b5/source/firefox-3.0b5-source.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.0b5/source/firefox-3.0b5-source.tar.bz2)
tar -xjf firefox-3.0b5-source.tar
```

CVS :

```
export CVSROOT=:pserver:anonymous@cvs-mirror.mozilla.org:/cvsroot
cvs login
cvs -d :pserver:anonymous@cvs-mirror.mozilla.org:/cvsroot co mozilla/client.mk
cd mozilla
make -f client.mk checkout
```

Note: Mozilla MXR offers a quick web search engine for source code

3. Create the Mozilla config file to build firefox

```
cd mozilla
echo &#8220;mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/../obj-@CONFIG_GUESS@&#8221; >> .mozconfig
echo &#8220;ac_add_options &#8211;enable-application=browser&#8221; >> .mozconfig
echo &#8220;mk_add_options MOZ_CO_PROJECT=browser&#8221; >> .mozconfig
echo &#8220;ac_add_options &#8211;enable-debug&#8221; >> .mozconfig
echo &#8220;ac_add_options &#8211;disable-optimize&#8221; >> .mozconfig
echo &#8220;mk_add_options MOZ_MAKE_FLAGS=\&#8221;CC=&#8217;distcc gcc&#8217; CXX=&#8217;distcc g++&#8217; -j4\&#8221;" >> .mozconfig
```

Note: Add the last line only if you plan to use distcc. Also, replace the &#8216;j4&#8242; parameter by the number of available processors (or cores) +2. Ex: if you have a total of 4 cores connected to your distcc server, use j6.

**Install and configure distcc**

1. Edit /etc/default/distcc

```
STARTDISTCC=&#8221;true&#8221;
ALLOWEDNETS=&#8221;10.145.0.0/16&#8243;
LISTENER=&#8221;0.0.0.0&#8243;
```

2. Add distcc hosts

```
mkdir ~/.distcc
echo &#8220;localhost build-machine&#8221; > ~/distcc/hosts
chmod 666 ~/.distcc/hosts
```

3. Restart the service

```
sudo /etc/init.d/distcc restart
```

**Build Firefox**

    ```
make -f client.mk build
```

**Configure the Eclipse project**

1. Create the project
```

File->New->Project&#8230;
C/C++ Project->Standard Make C++ Project
Project Name: Firefox
Location : (select the extracted mozilla folder)
Click &#8220;Finish&#8221;
```

2. Configure the project

```
Right-click on the new Firefox project in Eclipse&#8217;s left column
Click &#8220;Properties&#8221;
Select &#8220;Make C++ Project&#8221;
Change &#8220;Build command&#8221; to &#8220;make -f client.mk&#8221;
Change &#8220;Build (incremental build)&#8221; from &#8220;all&#8221; to &#8220;build&#8221;
```

3.  Build Firefox from Eclipse

You should remove the &#8220;Build automatically&#8221; option from the Project menu and build the application by right-clicking on the Firefox project and selecting &#8220;Build Project&#8221;
If you do not see the &#8220;Build Project&#8221; option, make sure you are using the C/C++ perspective.
This operation always takes a while since all subfolders and files need to be parsed (around 30k files)

**Debugging Firefox**

1. Create the Debug/Run configuration

```
Select Run->Debug&#8230; from the Eclipse menu
Right-click on C/C++ Local Application and select New
Project: firefox
C/C++ Application: (select browse and choose mozilla/../obj-i686-pc-linux-gnu/dist/bin/firefox-bin)
```

2. Add specific configuration

[INDENT]In the Arguments tab, change the working directory to mozilla/../obj-i686-pc-linux-gnu/dist/bin/

In the Environment tab, create two variables,

one with name LD_LIBRARY_PATH and value .:./plugins:.
one with name LIBRARY_PATH and value .:./components:.

In the Debugger tab, remove the checkbox on &#8220;Stop on startup at:&#8221;[/INDENT]

3. Click Apply and hit Debug to start debugging Firefox. If you face any issue, you can try to switch the debugger from gdb/mi to gdb Debugger.

**Troubleshooting**

If you get a GDB timeout error when debugging, open the debug configuration (Run->Debug...->firefox) and remove any entry in the Sources tab. I had this problem after adding my mozilla folder to a svn repository. GDB tries to "cache" every mozilla subfolder (without exclusion).

Now time to read [Introduction to Mozilla Source Code]("http://www.mozilla.org/hacking/coding-introduction.html"). I might one day create a similar tutorial for a Visual Studio environment. Enjoy !

---


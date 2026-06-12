---
title: "PyLucene JCC vs GCJ"
date: 2007-10-27
forum: Programming Talk
---

### Post by alef13 on 2007-10-27
I'm writing because after spending days with PyLucene versions (GCJ and JCC),I decided to share the story.

About 5 days ago I didn't even know about the existence of Lucene. I was having many difficulties indexing full-text data on MySQL - it took like 90 hours indexing ~64 million records in a single varchar(96) field. And when I tough it was finishing, I got a reboot on the development computer.

Surfing the web and talking with friends, I was trying to use something better (and faster) to get my data indexed in a smart way, making it easy to search. Since I don't have heavy inserts and updates, I decided to use Lucene.

Well, I chose PyLucene because much of my work was already written in python, and also because I prefer python over java. It's pretty simple to install pre-compiled binary packages for ubuntu, available from PyLucene's website:

[http://downloads.osafoundation.org/PyLucene/linux/ubuntu/7.04/](http://downloads.osafoundation.org/PyLucene/linux/ubuntu/7.04/)

That *PyLucene-2.2.0-1.tar.gz* is the GCJ version of PyLucene, and it's pretty simple to install. After decompressing the tarball, you can copy the contents of *PyLucene-2.2.0-1/python/* directory into python's site-packages, like this:

```
sudo cp -a PyLucene-2.2.0-1/python/* /usr/local/lib/python2.5/site-packages/
```

You could copy it directly into */usr/lib/python2.5/site-packages/*, but as there's a lot of files there, it could be difficult to remove or upgrade PyLucene after a while - at least for me, and that's why I always place unpackaged files in /usr/local/. If you're like me, you'll also need to create a symlink to make GCJ work:

```
sudo ln -s /usr/local/lib/python2.5/site-packages/security /usr/lib/python2.5/site-packages 
```

It's also needed to copy some libraries, needed by GCJ:

```
sudo cp -a PyLucene-2.2.0-1/gcj/* /usr/local/lib/
sudo ldconfig
```

That's it. As I told you, the GCJ version of PyLucene is pretty simple to install, and you can try it from python's console:

```
$ python
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import PyLucene
>>>

```

Continuing my story... I successfully installed PyLucene and wrote some scripts to parse a bunch of TXT files into a new Lucene's Index. Worked like a charm, and much faster than MySQL. It took like 24 hours importing everything, already indexed, allowing me to search the records (docs in Lucene) while importing.

But, as nothing is perfect, I started getting issues with that. After importing data to Lucene, it's needed to "optimize" the index. Sample programs shipped with PyLucene works perfect, as well as some test programs I wrote to become more familiar with the API. When I added the first 13 million records of data (~3.5GB), I got an exception while running optimize(): "java.io.IOException: File too large". Still couldn't figure out how to fix, and it seems to be a limit of GGJ.

I was writing a web application using Django, and, unfortunately, GCJ has threading mechanism incompatible with everything else - including mod-python. I couldn't find a way to use it together with Django, Apache and mod-python. With Django's development server it works fine, with a small fix, but that's not recommended for production systems. By the way, if you want to try it, replace "import thread" with "import PyLucene.PythonThread as thread" in django/utils/autoreload.py. Without that, the development server don't even start when you "import PyLucene" in your code - and, guess what: it doesn't print ANY error or warning message.

To use PyLucene, I had to abandon Django, and write it using python's cgi module, and the jinja (also new for me) html template engine. As jinja's syntax is very similar to Django's template engine, I could use all existing templates.

After talking with some friends and reading articles on the web, I decided to try the JCC version of PyLucene. My hope was to get better results, no silly thread issues, and, at least be able to optimize my index.

PyLucene's JCC version is available from:

[http://downloads.osafoundation.org/PyLucene/jcc/PyLucene-2.2.0-1-src-jcc.tar.gz](http://downloads.osafoundation.org/PyLucene/jcc/PyLucene-2.2.0-1-src-jcc.tar.gz)

To compile the source code you need:
1. Decompress the tarball
2. Install Java, Ant and svn: sudo apt-get install sun-java6-jdk ant subversion
3. Make sure you already have build-essential (devel stuff) properly installed

Then you run the following:

```
sudo update-java-alternatives --set java-6-sun
export LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/
```

Inside the "jcc" directory, you need to edit setup.py and change INCLUDES and LFLAGS of "linux2", because the original file is prepared for java-1.5.

```
INCLUDES = {
    'darwin': ['/System/Library/Frameworks/JavaVM.framework/Versions/1.5.0/Headers'],
    'linux2': ['/usr/lib/jvm/java-6-sun-1.6.0.00/include/',
               '/usr/lib/jvm/java-6-sun-1.6.0.00/include/linux/'],
    'win32': ['o:/Java/jdk1.6.0_02/include',
              'o:/Java/jdk1.6.0_02/include/win32'],
}

LFLAGS = {
    'darwin': ['-framework', 'JavaVM'],
    'linux2': ['-L/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/', '-ljava'],
    'win32': ['/LIBPATH:o:/Java/jdk1.6.0_02/lib', 'jvm.lib']
}

```

After that you can compile and install it:

```
python setup.py build
sudo python setup.py install
```

JCC is ready. It's already ready to "import jcc" from the python console. But remember to export that LD_LIBRARY_PATH everytime you want to use it, because without that JCC won't be able to find java shared libraries.

Once you have JCC working, go back to the root of the tarball and edit the Makefile. You need to uncomment some variables for the Linux system:

```
PREFIX_PYTHON=/usr
ANT=ant
PYTHON=$(PREFIX_PYTHON)/bin/python
JCC=$(PYTHON) $(PREFIX_PYTHON)/lib/python2.5/site-packages/jcc/__init__.py
NUM_FILES=1

```

Note that the original Makefile has "python2.4" and you'll need to fix it.
If you compile it as user just by typing "make", when you use sudo to install, it won't work. That happens because "ant" (java builder, like gnu make) will try to recompile everything and LD_LIBRARY_PATH won't be set. That's ridiculous. To avoid problems, you can compile the sourcecode and install it as root, by running:

```
sudo su
export LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/
make
make install
```

Ah, done. It's normal to get tons of warnings. Just don't care.
Now, sample and test programs won't work. You'll see that the API is a little bit different from the GCJ version. For example, now it's "import lucene" instead of "import PyLucene", and some exceptions have changed - because JCC version  throws exceptions directly from java. Nobody tells you that the JCC version needs to start java VM before you can make calls to PyLucene's methods - that's why samples and tests won't work. Again, without LD_LIBRARY_PATH it doesn't work - because it cannot find java shared libraries. If you're using apache2, you'll need to SetEnv that in the appropriate VirtualHost.

In any code, after "import lucene" you need to start the VM, by calling:

```
lucene.initVM(lucene.CLASSPATH)
```

The good news is that this version successfully optimized my index. It took 38 minutes to optimize 64 millions of records, and left one big file (12GB) in the index directory. Before optimizing, there was about 10 smaller files.

But the bad news was about to come. After some changes in the CGI, it started saying "java.lang.OutOfMemoryError: Java heap space". I spend some time again on the web, and discovered that the problem was related with the default amount of memory of java's heap. Many posts explaining to use "java -Xmx512m", and so on. I tried to add that to /etc/java-6-sun/jvm.cfg, tried to export JAVA_OPTS with that option. No success.

Then I decided to look at the JCC's source code, because JCC python module has the same "initVM()" method and I tough PyLucene was using or inheriting that. I was right. Not in the documentation, but in the sourcecode (jcc.cpp)I found this:

```
if (!PyArg_ParseTupleAndKeywords(args, kwds, "|zzzzzO", kwnames,
                                 &classpath,
                                 &initialheap, &maxheap, &maxstack,
                                 &vmargs, &jccenv))
        return NULL;

```

Pretty simple now. I just changed the call to initVM, adding the new heap size needed for my application and everything worked fine!

```
import lucene
lucene.initVM(lucene.CLASSPATH, maxheap='512m')
```

Now it's working, but the JCC version is about 3 times slower than the GCJ version. I found that:

1. GCJ version seems to be incompatible with python web frameworks, as well as mod-python
2. GCJ has limits regarding file size for indexes, and sometimes cannot optimize your data
3. GCJ is very, very fast making search
4. JCC is more complicated to install and require java installed (at least jre)
5. Programs using JCC version always need LD_LIBRARY_PATH
6. JCC needs to start java VM everytime you run the program, so in cases like mine (cgi application) it's a bit slower
7. JCC is about 3 times slower than GCJ when searching records, but seems to be fast importing data
8. JCC seems to be more stable and can optimize indexes bigger than 2.4GB

That's it, enjoy.

---

### Post by pfein on 2007-11-02
The author of PyLucene responded on the mailing list: [http://lists.osafoundation.org/pipermail/pylucene-dev/2007-November/001970.html](http://lists.osafoundation.org/pipermail/pylucene-dev/2007-November/001970.html)

---


---
title: "How to compile PHP-Qt with Zend Server 4.x?"
date: 2009-12-18
forum: Programming Talk
---

### Post by Hellkeepa on 2009-12-18
HELLo!

I've searched around a bit, and spotted this on the [Zend Forum](http://forums.zend.com/viewtopic.php?f=44&t=4644). However, there doesn't seem to be any activity in there. Thus I'm asking here, in the hopes that someone in here might be able to help us out. I'm sure there are plenty of other people with this issue.

If you look at that thread, you'll see the exact issue I have. Though, I'm running the trial version of the full Zend Server. Don't know if that makes a difference, but better safe than sorry.
In short, the issue is that the Zend Server stack seems to be missing the config files, for the PHP headers, that cmake is looking for. Installing the PHP headers that comes with Ubuntu is a no-go, due to conflicts with the Zend Server package.

Any ideas?

Happy codin'!

---

### Post by Hellkeepa on 2009-12-22
HELLo!

*Bump with puppy eyes*

Happy codin'!

---

### Post by CyberJack on 2009-12-22
If you download the source of php_qt ([http://www.php-qt.org/](http://www.php-qt.org/)) you find the FindPHP5.cmake file (and other cmake files) in the cmake/modules directory.

Make sure cmake can find the files using the sollution provided by the error message. :-?
> Adjust CMAKE_MODULE_PATH to find FindPHP5.cmake or set PHP5_DIR to the directory containing a CMake configuration file for PHP5.

I don't run zend-server so I can't check if this solution works, but I hope it does.

---

### Post by Hellkeepa on 2009-12-22
HELLo!

Hmm.. That seemed to work a bit better, the SVN doesn't seem to be quite complete. Tried using the "./build.sh" script too, but then it complained about another .cmake file being missing.

Anyway, downloaded the tarball, untarred it, and went ahead with the common installation procedures. Only to get the following error:
```
CMake Error at cmake/modules/FindPHP5.cmake:137 (LIST):
  list index: 0 out of range (-0, 18446744073709551615)
Call Stack (most recent call first):
  CMakeLists.txt:13 (include)


-- /main
CMake Error at CMakeLists.txt:16 (MESSAGE):
  PHP5 could not be found!
```
Tried to add the path to Zend Server's header files manually, by adding "/usr/local/zend/include/php" to the "PHP5_POSSIBLE_INCLUDE_PATHS" defintion in the abovementioned file. No go. :-\
Unfortunately, I'm not proficient in Python so I'm quite lost here.

PS: Line 137 is this line:
```
LIST(GET PHP5_INCLUDES 0 PHP5_INCLUDE_DIR)
```

*Edit, added:*
Just did a comparison towards the php5-dev package on my laptop (standard Ubuntu PHP package), and except for the "mbstring" and "gd" folders (both in the ext folder), only these files were missing on my local (Zend Server) installation:
> ext/standard/dns.h
ext/standard/url_scanner.h
main/suhosin_globals.h
main/suhosin_logo.h
main/suhosin_patch.h
Of course, most other files were different, and the local installation had a couple more files and folders. But no indication as to why the above error was encountered.

Happy codin'!

---

### Post by CyberJack on 2009-12-22
It complains about not finding php5.

I tried to compile the php-qt source and got the same error.
cmake found my php version after making the following changes to the FindPHP5.cmake file.

Remove all the paths from the "PHP5_POSSIBLE_INCLUDE_PATHS" section and add the path where your php5 souce is located.
```

SET(PHP5_POSSIBLE_INCLUDE_PATHS
  /usr/include/php5
  /usr/local/include/php5
  /usr/include/php
  /usr/local/include/php
  /usr/local/apache/php
  )

```
to
```

SET(PHP5_POSSIBLE_INCLUDE_PATHS
  /path/to/php5/source
  }

```

Then I had a problem with php-config. After installing the php5-dev packages the php-config file could not be executed as user, and it throws an error when executing as root. However I found a php-config5 executable which does the job.

I had to change
```

FIND_PROGRAM(PHP5_CONFIG_EXECUTABLE
  NAMES php5-config php-config
  )

```
to
```

FIND_PROGRAM(PHP5_CONFIG_EXECUTABLE
  NAMES php-config5 php5-config php-config
  )

```
If the php-config executable you are using is called "php-config" or "php5-config" you should not have to change this.

Afterward cmake output gave me this:
```

-- /usr/include/php5/main
-- Found PHP5-Version 5.2.6-3ubuntu4.4

```

I you have the QT 4 dev packages installed it should compile (I didn't install them so it didn't build)

---

### Post by Hellkeepa on 2009-12-22
HELLo!

Yeah, that it was complaining about not finding PHP I did understand. It was the "why" it didn't, that had me perplexed. As I mentioned in my post above, I did indeed point it to the folder where Zend Server had installed the contents of its dev-package. Without it helping at all, even if I removed all other paths in the cmake file it gave me the same error.

The location of the "php-config" executable is as follows:
"/usr/local/zend/bin/php-config"

I could try and make a symlink from "/usr/local/bin" to it, but I would much rather just be able to point the cmake script at the right locations in the first place. Lest I'll be adding symlinks in a patchwork like manner. Thus I tried to update all three path variables I could find in the file, with the correct ones for Zend Server, but still I got the same error:
```
$ cmake ..
-- Found Qt-Version 4.5.2
CMake Error at cmake/modules/FindPHP5.cmake:139 (LIST):
  list index: 0 out of range (-0, 18446744073709551615)
Call Stack (most recent call first):
  CMakeLists.txt:13 (include)


-- /main
CMake Error at CMakeLists.txt:16 (MESSAGE):
  PHP5 could not be found!
```
For me this looks like a bug with the function that's supposed to find the correct path, as it complains about index 0 being out of range for the list.

Here's the current version of the cmake file: [http://pastebin.com/m21ac876b](http://pastebin.com/m21ac876b)

BTW: Tested "php-config", just to be sure it's working, which it did indeed look like for me.
```
$ /usr/local/zend/bin/php-config
Usage: /usr/local/zend/bin/php-config [OPTION]
Options:
  --prefix            [/usr/local/zend]
  --includes          [-I/usr/local/zend/include/php -I/usr/local/zend/include/php/main -I/usr/local/zend/include/php/TSRM -I/usr/local/zend/include/php/Zend -I/usr/local/zend/include/php/ext -I/usr/local/zend/include/php/ext/date/lib]
  --ldflags           [ -L/usr/local/libxml2-2.7.3/lib -L/usr/local/zlib-1.2.3/lib -L/usr/local/openssl-0.9.8k/lib -L/usr/local/readline-5.2/lib]
  --libs              [-lcrypt   -lcrypt -lreadline -lncurses -lrt -lz -lssl -lcrypto -lresolv -lm -ldl -lnsl  -lxml2 -lz -lm -lxml2 -lz -lm -lxml2 -lz -lm -lcrypt -lxml2 -lz -lm -lcrypt ]
  --extension-dir     [//usr/local/zend/lib/php_extensions]
  --include-dir       [/usr/local/zend/include/php]
  --php-binary        [/usr/local/zend/bin/php]
  --php-sapis         [cli apache2handler]
  --configure-options [--prefix=/usr/local/zend --with-config-file-path=/usr/local/zend/etc --with-config-file-scan-dir=/usr/local/zend/etc/conf.d --disable-debug --enable-inline-optimization --disable-all --enable-libxml --enable-session --enable-spl --enable-xml --enable-hash --enable-reflection --with-pear --with-apxs2=/usr/local/zend/apache2/bin/apxs --with-layout=GNU --enable-filter --with-pcre-regex --with-zlib=/usr/local/zlib-1.2.3 --enable-simplexml --enable-dom --with-libxml-dir=/usr/local/libxml-2.7.3 --with-openssl=/usr/local/openssl-0.9.8k --enable-pdo --with-pdo-sqlite --with-readline=/usr/local/readline-5.2 --with-iconv --with-sqlite3 --disable-phar]
  --version           [5.2.11]
  --vernum            [50211]

```
I'm at a loss here, I'm afraid. Worst part is, that if the cmake had used perl scripts instead of Python, I'm almost certain I could have picked out the error, seeing I'm much more familiar with the Perl syntax than I'm with Python. :-\

Happy codin'!

---

### Post by CyberJack on 2009-12-22
You can try to add a "PATH" part to the PHP5_CONFIG_EXECUTABLE section.
I don't know of this works, but I give it a fair chance.

```
FIND_PROGRAM(PHP5_CONFIG_EXECUTABLE
  NAMES php5-config php-config
  )
```
to
```
FIND_PROGRAM(PHP5_CONFIG_EXECUTABLE
  NAMES php5-config php-config
  PATHS
  /path/to/php-config
  )
```

otherwise use "which" to make sure php-config in your path is pointing to the correct file or run "php-config5 --includes". You should get output like:
```

-I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
```

---

### Post by Hellkeepa on 2009-12-22
HELLo!

That did it, thanks! Actually tried to add the /usr/local/zend/bin" to the path enviroment variable, just before reading this post. Nice to see we were on the same page on this at least. :-)
Now, to inform the PHP-Qt developers to test for the executable before trying to run it. Or at the very least give a proper error message instead of just assuming everything went OK.

Again, thanks for all your help. :) I've added the diff to this post, and I'll send it to the developers. Hopefully other people might find it useful too.

*Edit, added: *Sigh* compiling errors against smokeQt. This is not meant to be easy, I gather...*

Happy codin'!

---


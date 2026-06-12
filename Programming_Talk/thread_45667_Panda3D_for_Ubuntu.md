---
title: "Panda3D for Ubuntu"
date: 2005-07-01
forum: Programming Talk
---

### Post by MappyH on 2005-07-01
I found this on my travels. It's good for noobs like me  :-P 

What is Panda3D?

Panda3D is a 3D engine: a library of subroutines for 3D rendering and game development. The library is C++ with a set of Python bindings. Game development with Panda3D usually consists of writing a Python program that controls the the Panda3D library.

[http://www.panda3d.org/](http://www.panda3d.org/)

[http://www.panda3d.org/download/panda3d_1.0.5-ubuntuhoary_i386.deb](http://www.panda3d.org/download/panda3d_1.0.5-ubuntuhoary_i386.deb)

sudo dpkg -i panda3d_1.0.5-ubuntuhoary_i386.deb

Sorry if i posted this in the wrong place.

---

### Post by fierarul on 2005-07-01
The site appears broken on my Firefox (the JS menu).

Otherwise, looks like a nice project. Do you have any info comparing it with Ogre or other engines ?

The screenshots look quite simple, was it really used for some multiplayer game ? I would also like some engine good enough for >3000 objects worlds _and_ with a simple API.

---

### Post by MappyH on 2005-07-01
I'm very new to this stuff, it has a very easy learning curve thats all I know sorry.

Your better to ask in the forums [http://panda3d.org/forum/index.php](http://panda3d.org/forum/index.php)

edit: disney [http://toontown.com](http://toontown.com) is the game. now that wont work in firefox, my kid wanted to play :(

---

### Post by Gnobody on 2005-07-05
The examples don't seem to work, are there any other dependancies?

---

### Post by italomaia on 2008-05-21
No 64bits hardy for it yet.

---

### Post by MojoX on 2008-07-27
Just wanted to share that as of May 28, 2008 Panda3D is available under the revised BSD license.  The older Panda3D license was an problem for many interested folks and developers.

Pand3D is a robust, well-documented, and easy to approach engine requiring only Python to create some (to me) impressive gaming projects.  The community resembles the Ubuntu community in its welcoming nature and responsiveness to questions and newbies.  There is a large collection of user-contributed libraries to be found via the forums, including PandaSteer, an implementation of Craig Reynold's OpenSteer.

Panda3D is providing free web hosting for Panda3D projects at [http://www.p3dp.com/](http://www.p3dp.com/).

I've been using it myself for a few months now and have enjoyed the experience.  Just wanted to spread the love (especially since my programming sojourn began with some newbie questions in this very forum).

---

### Post by Kadrus on 2008-07-27
*Resurrection of old threads.*
I've used it too and I have found it to be very good,and can be moded easily since it's open source.

---

### Post by Kadrus on 2008-07-27
Double post.Please Moderators delete this.

---

### Post by Vadi on 2008-07-28
Very nice, thanks for bringing this up.

---

### Post by magick.crow on 2008-08-04
Panda3d is used for lots of pro projects! It is made by Disney and used by them for lots of their products.

It has a new free licence and I think should be in Ubuntu!

Comparing it to OGRE3d in not correct because Ogre is a graphics engine but Panda3d is a game engine with the graphics engine being just a small part of it. It is also one of the easiest python game engines to use.

Here is a list from Wikipedia.

"Here is a partial list of companies and commercial products that utilize Panda3D:

    * Disney's Toontown
    * Disney's Pirates of the Caribbean Online
    * SimOps Studios: Code3D
    * MSA's Thermal Enforcer
    * Little Mermaid Pinball, Aladdin Pinball, and Pirates Pinball

Here is an incomplete list of free software projects building on Panda3D:

    * Angels Fall First: Second Antarean War
    * La Granja de Los Poderosos
    * HeartSeed
    * Herdelia
    * Vikings
"

---

### Post by moma on 2008-08-04
This text may help if you cannot find a ready-made package for the Panda3d on Ubuntu 8.04 (Hardy Heron).

EDIT: Banda3D provides now ready-made packages for Ubuntu 8.10/9.04. 
See [http://www.panda3d.org/download.php](http://www.panda3d.org/download.php)



----- this is obsolete, old guide -----
Compiling Banda3D on [COLOR=Red]Ubuntu 8.04[/COLOR] !
I compiled Panda3d from the source code. This was my procedure 

**Step -1)** Install a proper display diriver as instructed in step 5) of this [guide...]("http://www.futuredesktop.org"). Then check if OpenGL works well.

Glxinfo sould report "*direct rendering: Yes*"
$ [COLOR=DarkGreen]glxinfo | grep -i direct[/COLOR]
[COLOR=Gray]direct rendering: Yes[/COLOR]

Then continue 

**Step 0)** Install some pre-requirements
$ [COLOR=DarkGreen]sudo apt-get install build-essential bison flex python-dev [/COLOR]
$ [COLOR=DarkGreen]sudo apt-get install freeglut-dev libglu-dev libgl1-mesa-dev libfreetype6-dev libosmesa-dev [/COLOR]
$ [COLOR=DarkGreen]sudo apt-get install libgtk2.0-dev libpng-dev libjpeg-dev libtiff-dev libxft-dev libssl-dev[/COLOR]

(The makepanda in step 4) will tell you if there are other dependencies)

**Step 2)** Download the Panda3D source from 
[http://www.panda3d.org/download.php](http://www.panda3d.org/download.php)

Take the "Panda3D Complete Source Code".
In my space-time the most recent tar-ball is "panda3d-1.5.2.tar.gz".

**Step 3)** Unpack the files to your home folder.

**Step 4)** Cd into the source directory and compile the code
$ [COLOR=DarkGreen]cd panda3d-1.5* [/COLOR]

$ [COLOR=DarkGreen]makepanda/makepanda.py --everything  [/COLOR]
(please wait..., the compilation may take upto 10 - 30 minutes)

**Step 5)** Create a Debian (.deb) package which you can install. 
[COLOR=Red]Why?[/COLOR] Because it is easier to upgrade and remove if you installed via the Apt package system.
$ [COLOR=DarkGreen]makepanda/makepanda.py --everything --installer[/COLOR]

**Step 6)** Then install the .deb package. It should be in the panda3d-1.5.2/ base directory.  Install it
$ [COLOR=DarkGreen]sudo dpkg -i panda3d_1.5.2_i386.deb[/COLOR]
-------------

**Step 7)** Test Panda3d
The installer copies some examples to /usr/share/panda3d/samples/ directory. You can run them from that location or from your local source folder (where you d/l the source).

$ [COLOR=DarkGreen]cd /usr/share/panda3d/samples/[/COLOR]

List all examples
$ [COLOR=DarkGreen]ls -l [/COLOR]

[COLOR=Gray]dr-xr-xr-x 5 moma moma 4096 2008-08-04 17:55 Asteroids
dr-xr-xr-x 4 moma moma 4096 2008-08-04 17:55 Ball-in-Maze
...
dr-xr-xr-x 3 moma moma 4096 2008-08-04 17:55 Teapot-on-TV
dr-xr-xr-x 7 moma moma 4096 2008-08-04 17:55 Texture-Swapping[/COLOR]

Ok, let's try the Ball-in-Maze game. 
$ [COLOR=DarkGreen]cd Ball-in-Maze[/COLOR]

Check the directory. Where are we? (pwd, print working dir)
$ [COLOR=DarkGreen]pwd [/COLOR]
/usr/share/panda3d/samples/Ball-in-Maze

Run it 
$ [COLOR=DarkGreen]python Tut-Ball-in-Maze.py[/COLOR]

[[IMG]http://bildr.no/thumb/235907.jpeg[/IMG]]("http://bildr.no/view/235907")

Check the the other examples too.
-----------

Because we compiled Panda3d from source code the demos are also in your local source directory.
Study the python (.py) code in there. You have read/write access to the code.

$ [COLOR=DarkGreen]cd $HOME[/COLOR]
$ [COLOR=DarkGreen]cd panda3d-1.5*[/COLOR]
$ [COLOR=DarkGreen]cd samples [/COLOR]

List them all 
$ [COLOR=DarkGreen]ls -l [/COLOR]
...

I want to test the Media-Player demo. It's so cool.
$ [COLOR=DarkGreen]cd Media-Player[/COLOR]

Where am I now?
$ [COLOR=DarkGreen]pwd [/COLOR]
/home/moma/panda3d-1.5.2/samples/Media-Player

Looks good. Run it (press P to start the media ;-)
$ [COLOR=DarkGreen]python Tut-Media-Player.py[/COLOR]
-------------

If you have problems running the demos, set the LIBRARY PATH first. It may help.
$ [COLOR=DarkGreen]export LD_LIBRARY_PATH=/home/xxx/panda3d-1.5.2/built/lib[/COLOR]
Replace the xxx with correct path. Then run the examples.
--------------

EDIT: Needs also "python-dev" package.
EDIT: On Ubuntu 8.10(alpha2): The compilation reports an error because it cannot find the memset(...) function. It misses some standard header files (afaik: gcc/g++4.3 does not add'em automatically). 
The fix is easy. Edit the **dtool/src/dtoolbase/dtoolbase.h** file and add 
[I]#include <string.h>
#include <stdlib.h>
#include <limits.h>[/I]
around the line 94.  The result should look like **[this...]("http://bildr.no/view/235456")**(picture)

EDIT: This is a very similar guide: [http://panda3d.org/phpbb2/viewtopic.php?t=4205](http://panda3d.org/phpbb2/viewtopic.php?t=4205)

Happy hacking
And read the manual [http://www.panda3d.org/wiki/index.php/Main_Page](http://www.panda3d.org/wiki/index.php/Main_Page)  !

---

### Post by Vadi on 2008-08-04
Could you submit this to launchpad.net/getdeb.net so they'll make .debs?

---

### Post by moma on 2008-08-05
I will try to do that later today.
EDIT: Ok, I posted a request to Launchpad.net. See [https://bugs.launchpad.net/ubuntu/+bug/254978](https://bugs.launchpad.net/ubuntu/+bug/254978)
Sent also a message to Getdeb.net.

Do you think that the license has earlier been a hindrance to include panda3d in Ubuntu? 
They changed the license very recently (28-May-2008 ) to the BSD license which is very liberal.

---

### Post by Perk on 2008-09-05
Hi, I'm getting some errors when I try to install it. Some of the errors has smiley faces because the error had symbols that made up a smiley face. Not sure how to avoid that.

Thanks!

EDIT: Nevermind, I just forgot to install ssl

Makepanda Initial Status Report
Makepanda: Compiler: LINUX
Makepanda: Optimize: 3
Makepanda: Keep Pkg: PYTHON ZLIB PNG JPEG TIFF VRPN FMOD FMODEX OPENAL NVIDIACG OPENSSL FREETYPE FFTW ARTOOLKIT FFMPEG PANDATOOL PANDAAPP 
Makepanda: Omit Pkg: MAYA6 MAYA65 MAYA7 MAYA8 MAYA85 MAYA2008 MAX6 MAX7 MAX8 MAX9 DX8 DX9 DIRECTCAM 
Makepanda: Verbose vs. Quiet Level: 1
Makepanda: Don't generate API reference manual
Makepanda: Version ID: 1.5.2
Makepanda: I cannot locate SDK for DX8
Makepanda: I have automatically added this command-line option: --no-dx8
Makepanda: I cannot locate SDK for DX9
Makepanda: I have automatically added this command-line option: --no-dx9
Makepanda: I cannot locate SDK for DIRECTCAM
Makepanda: I have automatically added this command-line option: --no-directcam
Makepanda: MAYA6 not yet supported under linux
Makepanda: I have automatically added this command-line option: --no-maya6
Makepanda: MAYA65 not yet supported under linux
Makepanda: I have automatically added this command-line option: --no-maya65
Makepanda: MAYA7 not yet supported under linux
Makepanda: I have automatically added this command-line option: --no-maya7
Makepanda: MAYA8 not yet supported under linux
Makepanda: I have automatically added this command-line option: --no-maya8
Makepanda: MAYA85 not yet supported under linux
Makepanda: I have automatically added this command-line option: --no-maya85
Makepanda: MAYA2008 not yet supported under linux
Makepanda: I have automatically added this command-line option: --no-maya2008
Makepanda: MAX6 not yet supported under linux
Makepanda: I have automatically added this command-line option: --no-max6
Makepanda: MAX7 not yet supported under linux
Makepanda: I have automatically added this command-line option: --no-max7
Makepanda: MAX8 not yet supported under linux
Makepanda: I have automatically added this command-line option: --no-max8
Makepanda: MAX9 not yet supported under linux
Makepanda: I have automatically added this command-line option: --no-max9
Makepanda: Caution: the built/lib directory is not in LD_LIBRARY_PATH
Makepanda: or /etc/ld.so.conf.  You must add it before using panda.
-------------------------------------------------------------------

cp --recursive --force thirdparty/Pmw built/Pmw
Generating dependencies...
g++ -ftemplate-depth-30 -fPIC -c -o built/tmp/dtoolbase_composite1.o -I"/usr/include/python2.5" -I"built/tmp" -I"built/include" -Idtool/src/dtoolbase -O2 -DBUILDING_DTOOL dtool/src/dtoolbase/dtoolbase_composite1.cxx
g++ -ftemplate-depth-30 -fPIC -c -o built/tmp/dtoolbase_composite2.o -I"/usr/include/python2.5" -I"built/tmp" -I"built/include" -Idtool/src/dtoolbase -O2 -DBUILDING_DTOOL dtool/src/dtoolbase/dtoolbase_composite2.cxx
gcc -fPIC -c -o built/tmp/dtoolbase_lookup3.o -I"/usr/include/python2.5" -I"built/tmp" -I"built/include" -Idtool/src/dtoolbase -O2 -DBUILDING_DTOOL dtool/src/dtoolbase/lookup3.c
g++ -ftemplate-depth-30 -fPIC -c -o built/tmp/dtoolbase_indent.o -I"/usr/include/python2.5" -I"built/tmp" -I"built/include" -Idtool/src/dtoolbase -O2 -DBUILDING_DTOOL dtool/src/dtoolbase/indent.cxx
gcc -fPIC -c -o built/tmp/dtoolutil_gnu_getopt.o -I"/usr/include/python2.5" -I"built/tmp" -I"built/include" -Idtool/src/dtoolutil -O2 -DBUILDING_DTOOL dtool/src/dtoolutil/gnu_getopt.c
gcc -fPIC -c -o built/tmp/dtoolutil_gnu_getopt1.o -I"/usr/include/python2.5" -I"built/tmp" -I"built/include" -Idtool/src/dtoolutil -O2 -DBUILDING_DTOOL dtool/src/dtoolutil/gnu_getopt1.c
g++ -ftemplate-depth-30 -fPIC -c -o built/tmp/dtoolutil_composite.o -I"/usr/include/python2.5" -I"built/tmp" -I"built/include" -Idtool/src/dtoolutil -O2 -DBUILDING_DTOOL dtool/src/dtoolutil/dtoolutil_composite.cxx
g++ -ftemplate-depth-30 -fPIC -c -o built/tmp/dtool_dtool.o -I"/usr/include/python2.5" -I"built/tmp" -I"built/include" -Idtool/metalibs/dtool -O2 -DBUILDING_DTOOL dtool/metalibs/dtool/dtool.cxx
g++ -shared -o built/lib/libp3dtool.so -Lbuilt/lib -L/usr/X11R6/lib built/tmp/dtool_dtool.o built/tmp/dtoolutil_gnu_getopt.o built/tmp/dtoolutil_gnu_getopt1.o built/tmp/dtoolutil_composite.o built/tmp/dtoolbase_composite1.o built/tmp/dtoolbase_composite2.o built/tmp/dtoolbase_indent.o built/tmp/dtoolbase_lookup3.o -lpthread -ldl
bison -y -d -obuilt/tmp/cppBison.yxx.c -p cppyy dtool/src/cppparser/cppBison.yxx
g++ -ftemplate-depth-30 -fPIC -c -o built/tmp/cppParser_cppBison.o -I"/usr/include/python2.5" -I"built/tmp" -I"built/include" -Idtool/src/cppparser -O2 built/tmp/cppBison.yxx.cxx
CAUTION: file dependencies changed: ['built/include/cppBison.h']
g++ -ftemplate-depth-30 -fPIC -c -o built/tmp/cppParser_composite.o -I"/usr/include/python2.5" -I"built/tmp" -I"built/include" -Idtool/src/cppparser -O2 dtool/src/cppparser/cppParser_composite.cxx
ar cru built/tmp/libcppParser.a built/tmp/cppParser_composite.o built/tmp/cppParser_cppBison.o
g++ -ftemplate-depth-30 -fPIC -c -o built/tmp/prc_composite.o -I"/usr/include/python2.5" -I"built/tmp" -I"built/include" -Idtool/src/prc -O2 -DBUILDING_DTOOLCONFIG dtool/src/prc/prc_composite.cxx
In file included from dtool/src/prc/configPage.cxx:23,
                 from dtool/src/prc/prc_composite1.cxx:4,
                 from dtool/src/prc/prc_composite.cxx:1:
dtool/src/prc/prcKeyRegistry.h:31:25: error: openssl/evp.h: No such file or directory
In file included from dtool/src/prc/prc_composite2.cxx:4,
                 from dtool/src/prc/prc_composite.cxx:2:
dtool/src/prc/encryptStreamBuf.cxx:28:26: error: openssl/rand.h: No such file or directory
In file included from dtool/src/prc/prc_composite2.cxx:11,
                 from dtool/src/prc/prc_composite.cxx:2:
dtool/src/prc/prcKeyRegistry.cxx:28:25: error: openssl/pem.h: No such file or directory
In file included from dtool/src/prc/configPage.cxx:23,
                 from dtool/src/prc/prc_composite1.cxx:4,
                 from dtool/src/prc/prc_composite.cxx:1:
dtool/src/prc/prcKeyRegistry.h:60: error: &#8216;EVP_PKEY&#8217; has not been declared
dtool/src/prc/prcKeyRegistry.h:63: error: ISO C++ forbids declaration of &#8216;EVP_PKEY&#8217; with no type
dtool/src/prc/prcKeyRegistry.h:63: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
dtool/src/prc/prcKeyRegistry.h:73: error: ISO C++ forbids declaration of &#8216;EVP_PKEY&#8217; with no type
dtool/src/prc/prcKeyRegistry.h:73: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
In file included from dtool/src/prc/encryptStream.h:27,
                 from dtool/src/prc/configPage.cxx:25,
                 from dtool/src/prc/prc_composite1.cxx:4,
                 from dtool/src/prc/prc_composite.cxx:1:
dtool/src/prc/encryptStreamBuf.h:75: error: &#8216;EVP_CIPHER_CTX&#8217; does not name a type
dtool/src/prc/encryptStreamBuf.h:81: error: &#8216;EVP_CIPHER_CTX&#8217; does not name a type
In file included from dtool/src/prc/prc_composite1.cxx:4,
                 from dtool/src/prc/prc_composite.cxx:1:
dtool/src/prc/configPage.cxx: In member function &#8216;bool ConfigPage::read_prc(std::istream&)&#8217;:
dtool/src/prc/configPage.cxx:143: error: expected type-specifier before &#8216;EVP_MD_CTX&#8217;
dtool/src/prc/configPage.cxx:143: error: expected `;' before &#8216;EVP_MD_CTX&#8217;
dtool/src/prc/configPage.cxx:145: error: &#8216;EVP_MD_CTX&#8217; was not declared in this scope
dtool/src/prc/configPage.cxx:145: error: expected primary-expression before &#8216;)&#8217; token
dtool/src/prc/configPage.cxx:145: error: &#8216;EVP_sha1&#8217; was not declared in this scope
dtool/src/prc/configPage.cxx:145: error: &#8216;EVP_VerifyInit&#8217; was not declared in this scope
dtool/src/prc/configPage.cxx:204: error: &#8216;EVP_PKEY&#8217; was not declared in this scope
dtool/src/prc/configPage.cxx:204: error: &#8216;pkey&#8217; was not declared in this scope
dtool/src/prc/configPage.cxx:204: error: &#8216;class PrcKeyRegistry&#8217; has no member named &#8216;get_key&#8217;
dtool/src/prc/configPage.cxx:205: error: expected primary-expression before &#8216;)&#8217; token
dtool/src/prc/configPage.cxx:205: error: expected `)' before &#8216;__null&#8217;
dtool/src/prc/configPage.cxx:207: error: expected primary-expression before &#8216;)&#8217; token
dtool/src/prc/configPage.cxx:209: error: &#8216;EVP_VerifyFinal&#8217; was not declared in this scope
dtool/src/prc/configPage.cxx:223: error: expected primary-expression before &#8216;)&#8217; token
dtool/src/prc/configPage.cxx:223: error: expected `;' before &#8216;_md_ctx&#8217;
dtool/src/prc/configPage.cxx: In member function &#8216;void ConfigPage::read_prc_line(const std::string&)&#8217;:
dtool/src/prc/configPage.cxx:405: error: &#8216;EVP_MD_CTX&#8217; was not declared in this scope
dtool/src/prc/configPage.cxx:405: error: expected primary-expression before &#8216;)&#8217; token
dtool/src/prc/configPage.cxx:405: error: &#8216;EVP_VerifyUpdate&#8217; was not declared in this scope
In file included from dtool/src/prc/prc_composite2.cxx:4,
                 from dtool/src/prc/prc_composite.cxx:2:
dtool/src/prc/encryptStreamBuf.cxx: In member function &#8216;void EncryptStreamBuf::open_read(std::istream*, bool, const std::string&)&#8217;:
dtool/src/prc/encryptStreamBuf.cxx:121: error: &#8216;OpenSSL_add_all_algorithms&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:133: error: expected initializer before &#8216;*&#8217; token
dtool/src/prc/encryptStreamBuf.cxx:135: error: &#8216;cipher&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:141: error: &#8216;OBJ_nid2sn&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:153: error: &#8216;cipher&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:153: error: &#8216;EVP_CIPHER_iv_length&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:154: error: &#8216;EVP_CIPHER_block_size&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:160: error: &#8216;_read_ctx&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:160: error: &#8216;EVP_DecryptInit&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:163: error: &#8216;EVP_CIPHER_CTX_set_key_length&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:168: error: &#8216;EVP_CIPHER_CTX_cleanup&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:178: error: &#8216;PKCS5_PBKDF2_HMAC_SHA1&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx: In member function &#8216;void EncryptStreamBuf::close_read()&#8217;:
dtool/src/prc/encryptStreamBuf.cxx:200: error: &#8216;_read_ctx&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:200: error: &#8216;EVP_CIPHER_CTX_cleanup&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx: In member function &#8216;void EncryptStreamBuf::open_write(std::ostream*, bool, const std::string&)&#8217;:
dtool/src/prc/encryptStreamBuf.cxx:225: error: &#8216;OpenSSL_add_all_algorithms&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:232: error: expected initializer before &#8216;*&#8217; token
dtool/src/prc/encryptStreamBuf.cxx:235: error: &#8216;cipher&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:241: error: &#8216;cipher&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:241: error: &#8216;EVP_CIPHER_nid&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:243: error: &#8216;EVP_CIPHER_iv_length&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:244: error: &#8216;EVP_CIPHER_block_size&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:250: error: &#8216;RAND_pseudo_bytes&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:253: error: &#8216;_write_ctx&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:253: error: &#8216;EVP_EncryptInit&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:259: error: &#8216;EVP_CIPHER_key_length&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:261: error: &#8216;EVP_CIPHER_CTX_set_key_length&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:265: error: &#8216;OBJ_nid2sn&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:266: error: &#8216;EVP_CIPHER_CTX_cleanup&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:274: error: &#8216;OBJ_nid2sn&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:286: error: &#8216;PKCS5_PBKDF2_HMAC_SHA1&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx: In member function &#8216;void EncryptStreamBuf::close_write()&#8217;:
dtool/src/prc/encryptStreamBuf.cxx:322: error: &#8216;_write_ctx&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:322: error: &#8216;EVP_EncryptFinal&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx: In member function &#8216;size_t EncryptStreamBuf::read_chars(char*, size_t)&#8217;:
dtool/src/prc/encryptStreamBuf.cxx:453: error: &#8216;_read_ctx&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:454: error: &#8216;EVP_DecryptUpdate&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:457: error: &#8216;_read_ctx&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:457: error: &#8216;EVP_DecryptFinal&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:465: error: &#8216;_read_ctx&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:465: error: &#8216;EVP_CIPHER_CTX_cleanup&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx: In member function &#8216;void EncryptStreamBuf::write_chars(const char*, size_t)&#8217;:
dtool/src/prc/encryptStreamBuf.cxx:505: error: &#8216;_write_ctx&#8217; was not declared in this scope
dtool/src/prc/encryptStreamBuf.cxx:506: error: &#8216;EVP_EncryptUpdate&#8217; was not declared in this scope
In file included from dtool/src/prc/prc_composite2.cxx:11,
                 from dtool/src/prc/prc_composite.cxx:2:
dtool/src/prc/prcKeyRegistry.cxx: In member function &#8216;void PrcKeyRegistry::record_keys(const PrcKeyRegistry::KeyDef*, int)&#8217;:
dtool/src/prc/prcKeyRegistry.cxx:74: error: &#8216;class PrcKeyRegistry::Key&#8217; has no member named &#8216;_pkey&#8217;
dtool/src/prc/prcKeyRegistry.cxx:79: error: &#8216;class PrcKeyRegistry::Key&#8217; has no member named &#8216;_pkey&#8217;
dtool/src/prc/prcKeyRegistry.cxx:79: error: &#8216;EVP_PKEY&#8217; was not declared in this scope
dtool/src/prc/prcKeyRegistry.cxx:79: error: expected primary-expression before &#8216;)&#8217; token
dtool/src/prc/prcKeyRegistry.cxx:79: error: expected `)' before &#8216;__null&#8217;
dtool/src/prc/prcKeyRegistry.cxx:80: error: &#8216;class PrcKeyRegistry::Key&#8217; has no member named &#8216;_pkey&#8217;
dtool/src/prc/prcKeyRegistry.cxx:80: error: &#8216;EVP_PKEY_free&#8217; was not declared in this scope
dtool/src/prc/prcKeyRegistry.cxx:81: error: &#8216;class PrcKeyRegistry::Key&#8217; has no member named &#8216;_pkey&#8217;
dtool/src/prc/prcKeyRegistry.cxx: At global scope:
dtool/src/prc/prcKeyRegistry.cxx:100: error: &#8216;EVP_PKEY&#8217; has not been declared
dtool/src/prc/prcKeyRegistry.cxx: In member function &#8216;void PrcKeyRegistry::set_key(int, int*, time_t)&#8217;:
dtool/src/prc/prcKeyRegistry.cxx:105: error: &#8216;class PrcKeyRegistry::Key&#8217; has no member named &#8216;_pkey&#8217;
dtool/src/prc/prcKeyRegistry.cxx:110: error: &#8216;class PrcKeyRegistry::Key&#8217; has no member named &#8216;_pkey&#8217;
dtool/src/prc/prcKeyRegistry.cxx:110: error: &#8216;EVP_PKEY&#8217; was not declared in this scope
dtool/src/prc/prcKeyRegistry.cxx:110: error: expected primary-expression before &#8216;)&#8217; token
dtool/src/prc/prcKeyRegistry.cxx:110: error: expected `)' before &#8216;__null&#8217;
dtool/src/prc/prcKeyRegistry.cxx:111: error: &#8216;class PrcKeyRegistry::Key&#8217; has no member named &#8216;_pkey&#8217;
dtool/src/prc/prcKeyRegistry.cxx:111: error: &#8216;EVP_PKEY_free&#8217; was not declared in this scope
dtool/src/prc/prcKeyRegistry.cxx:112: error: &#8216;class PrcKeyRegistry::Key&#8217; has no member named &#8216;_pkey&#8217;
dtool/src/prc/prcKeyRegistry.cxx:114: error: &#8216;class PrcKeyRegistry::Key&#8217; has no member named &#8216;_pkey&#8217;
dtool/src/prc/prcKeyRegistry.cxx: At global scope:
dtool/src/prc/prcKeyRegistry.cxx:137: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
Storing dependency cache.
Elapsed Time: 37 sec

---

### Post by Vadi on 2008-09-05
You can use the code tags next time to avoid the smileys.

---

### Post by sanderDrost on 2008-10-27
when i try to install the panda3D.deb hardy i 386 i get an error message
error: wrong architecture 'i386' how do i know what version to download..? same thing happens with skype.

Im new to linux so i came here for help thanks in advance :)


Sander

EDIT: nvm i got it, apparently my laptop is 64bit :p

---


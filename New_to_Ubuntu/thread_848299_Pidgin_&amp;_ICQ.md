---
title: "Pidgin &amp; ICQ"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by SVWander on 2008-07-03
Has anyone been having trouble with Pidgin and ICQ? I have been having trouble connecting to ICQ. I get this message:
disabled
You have been connecting to and disconnecting too frequently. Wait ten minutes and try again....

At other times I get a message saying that:
The client version you are using is too old. Please upgrade at [http://pidgin.im/](http://pidgin.im/)

I went to that site but couldn't figure out how to update and wondered if I was doing something wrong.

Tim

---

### Post by LinuxRocks713 on 2008-07-03
Download this file to your desktop: [http://voxel.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.4.3.tar.bz2](http://voxel.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.4.3.tar.bz2)

Then open a terminal and type:

cd $HOME/Desktop
tar jxvf pidgin-2.4.3.tar.bz2
cd pidgin-*
./configure --prefix=/usr
make
sudo make install

After that, start Pidgin with the command pidgin.

*EDIT*:
Before doing any of these, uninstall the pidgin that came with ubuntu:

sudo apt-get remove pidgin

---

### Post by Golem XIV on 2008-07-03
No need to compile, the fix is already in the repository.  I updated this morning and the problem was fixed.

---

### Post by SVWander on 2008-07-03
> **Golem XIV said:**
> No need to compile, the fix is already in the repository.  I updated this morning and the problem was fixed.

I did the same but still got the error messages. When I uninstalled I did a complete removal and then reinstalled. I did try to compile it but ran into trouble there also. Did you just update yours? I have reinstalled twice.
Tim

---

### Post by SVWander on 2008-07-03
> **LinuxRocks713 said:**
> Download this file to your desktop: [http://voxel.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.4.3.tar.bz2](http://voxel.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.4.3.tar.bz2)

Then open a terminal and type:

cd $HOME/Desktop
tar jfvf pidgin-2.4.3.tar.bz2
cd pidgin-*
./configure --prefix=/usr
make
sudo make install

After that, start Pidgin with the command pidgin.

*EDIT*:
Before doing any of these, uninstall the pidgin that came with ubuntu:

sudo apt-get remove pidgin

I ran into problems compiling. The config.log reads:
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "pidgin"
| #define PACKAGE_TARNAME "pidgin"
| #define PACKAGE_VERSION "2.4.3"
| #define PACKAGE_STRING "pidgin 2.4.3"
| #define PACKAGE_BUGREPORT "devel@pidgin.im"
| #define PACKAGE "pidgin"
| #define VERSION "2.4.3"
| #define CONFIG_ARGS " '--prefix=/usr'"
| /* end confdefs.h.  */
| 
I am not sure what that means or even if I copied information that is useful to help me figure it out. Oh the terminal error message was as follows:
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables

I haven't had a lot of experience compiling . . . but I would like to learn a little bit about it if I can.

tm

---

### Post by Golem XIV on 2008-07-03
try first
```
sudo apt-get install build-essential
```
and then compile

---

### Post by Jenda on 2008-07-03
Same problem here. Fortunately, I'm too busy to worry about ICQ :)

---

### Post by RomeReactor on 2008-07-03
> **SVWander said:**
> Has anyone been having trouble with Pidgin and ICQ? I have been having trouble connecting to ICQ. I get this message:
disabled
You have been connecting to and disconnecting too frequently. Wait ten minutes and try again....

At other times I get a message saying that:
The client version you are using is too old. Please upgrade at [http://pidgin.im/](http://pidgin.im/)

I went to that site but couldn't figure out how to update and wondered if I was doing something wrong.

Tim

Hi. That likely has to do [with this]("http://slashdot.org/article.pl?sid=08/07/02/1331224"). Pidgin [2.4.3 fixes it]("http://developer.pidgin.im/ticket/6220") ([Download]("http://www.pidgin.im/"))

---

### Post by SVWander on 2008-07-03
> **Golem XIV said:**
> try first
```
sudo apt-get install build-essential
```
and then compile

Damn! I had forgotten I had reinstalled the system and didn't reinstall build-essential. However now I am getting another error message:

configure: error:

You must have the GLib 2.0 development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.

both of these programs are installed. I deleted all the files in that directory that I expanded the downloaded file in and started over. Sorry for being such a pain. 
tm

---

### Post by Sean Heron on 2008-07-03
If anybodies still having problems, you might want to look at the last page (page 12) of the following thread : [http://ubuntuforums.org/showthread.php?p=5313090#post5313090](http://ubuntuforums.org/showthread.php?p=5313090#post5313090)

---

### Post by SVWander on 2008-07-03
> **Sean Heron said:**
> If anybodies still having problems, you might want to look at the last page (page 12) of the following thread : [http://ubuntuforums.org/showthread.php?p=5313090#post5313090](http://ubuntuforums.org/showthread.php?p=5313090#post5313090)
Thanks! that seems to have done the trick.
Tim

---

### Post by aIexxx on 2011-07-30
Hi! I had the same problem for quite a while. The solution is to change the server name in your account settings to "login.icq.com" and uncheck "use SSL" and "use clientLogin". It worked for me!

---

### Post by ka55o5 on 2012-07-03
> **aIexxx said:**
> The solution is to change the server name in your account settings to "login.icq.com" and uncheck "use SSL" and "use clientLogin".

Sry guys, had to bump it again. You can do that if you're using the default port 5190, or you can leave everything the same and just change the port to 443 which should let it fetch the certificate np.

P.S.
The message I was getting is:
> You have been connecting and disconnecting too frequently. Wait ten minutes and try again. If you continue to try, you will need to wait even longer.

---


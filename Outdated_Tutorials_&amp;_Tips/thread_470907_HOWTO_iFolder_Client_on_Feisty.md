---
title: "HOWTO: iFolder Client on Feisty"
date: 2007-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by flar on 2007-06-11
From the iFolder website: "iFolder is a simple and secure storage solution that can increase your productivity by enabling you to back up, access and manage your personal files-from anywhere, at any time."

Basically it synchronizes files between computers, anywhere (ie: over the internet).  Clients are available for Linux, Mac, and Windows.  To use iFolder, you will need to have an iFolder server.  
Go to the iFolder main page for info on building the server:

[http://www.ifolder.com/index.php/Main_Page]("http://www.ifolder.com/index.php/Main_Page")

The iFolder Enterprise Server is now open source so you can build that if you want.  I use the older SimpleServer because it is lighter and simpler.  This howto describes how to build an iFolder client on Linux that will work with both the Enterprise and Simple iFolder servers.

The client-server setup of iFolder has a big advantage (at least for me):  I can sync files between my home computer and my office computer despite the highly restrictive firewall at my office. 

I've been using iFolder for a couple years (most recently with Dapper), but recently upgraded to Feisty. I built and tested several versions of the iFolder client on Feisty without success (usually the client ran but did not work properly, sometimes would not compile). Finally, after much effort,  I found a version of the iFolder client that compiles and works on Feisty:

[B]
1. Install dependencies [/B]

Dependencies (that I know of, there might be more):  libmono-dev   mono-xsp  mono-gmcs libflaim-dev libflaim4.1  liblog4net1.2-cil build-essential

```
sudo apt-get install libmono-dev   mono-xsp  mono-gmcs libflaim-dev libflaim4.1  liblog4net1.2-cil build-essential
```



**2.  Download the source code using subversion:**

Make a directory for your iFolder source code (can be wherever you want)

```
mkdir ifolder
cd ifolder
```

Download the source code:

iFolder:
```
svn co https://forgesvn1.novell.com/svn/ifolder/branches/ifolder_3_4_sled10sp1/ifolder
```

Simias:
```
svn co https://forgesvn1.novell.com/svn/simias/branches/ifolder_3_4_sled10sp1/simias
```

Nautilus-iFolder (optional):
```
svn co https://forgesvn1.novell.com/svn/ifolder/branches/ifolder_3_4_sled10sp1/nautilus-ifolder/
```



**3. Build Simias**

Simias must be built first because it is a dependency for iFolder.  It is recommended that you install it in /opt/ifolder so as not to contaminate your /usr directory.  Simias and iFolder, like many Novell apps, spread files all over so it's best to keep them all in /opt/iFolder.  This will make it easier to uninstall

```
cd simias
./configure --prefix=/opt/ifolder
make 
sudo make install

```



**4. Patch and build iFolder **

To get ifolder to build, you'll  have to change two instances of  TrayIcon to Egg.TrayIcon in the file src/LinuxClient/application/iFolderApplication.cs.  This can be done with a patch.

first, change to the directory where you put the iFolder source code.  If you're still in the simias directory, then
```
cd ../ifolder
```


This following is the code for the patch file, paste it into a text editor and save the file in your ifolder directory, e.g.: save it as trayicon.patch.


```
--- src/LinuxClient/application/iFolderApplication.cs	2007-06-15 09:13:11.000000000 -0400
+++ src/LinuxClient/application/iFolderApplication.cs.new	2007-06-11 12:42:17.000000000 -0400
@@ -65,7 +65,7 @@
 		private Gdk.Pixbuf			DownloadingPixbuf;
 		private Gdk.Pixbuf			UploadingPixbuf;
 		private Gtk.EventBox		eBox;
-		private TrayIcon			tIcon;
+		private Egg.TrayIcon			tIcon;
 		private iFolderWebService	ifws;
 		private SimiasWebService	simws;
 		private iFolderData			ifdata;
@@ -141,7 +141,7 @@
 			
 			Util.SetQuitiFolderDelegate(new QuitiFolderDelegate(QuitiFolder));
 
-			tIcon = new TrayIcon("iFolder");
+			tIcon = new Egg.TrayIcon("iFolder");
 
 			currentIconAnimationDirection = 0;
```


Now apply the patch:
```
patch -p0 < trayicon.patch
```

Now we're ready to build iFolder:

```
./configure --prefix=/opt/ifolder
make 
sudo make install
```

Note that it is essential that iFolder be installed in the same place as simias so it can find the simias files.   In our case both will be install in /opt/ifolder



**5. Build nautilus-ifolder** (OPTIONAL)

iFolder also comes with an optional extension for Nautilus.  You don't need this, but it will allow you to manage iFolders from the right click context menu in Nautilus. 
```

cd ../nautilus-ifolder
./configure --prefix=/opt/ifolder
make
sudo make install
```

Now everything should be installed and ready to connect to an iFolder server.



**Other things you should know:**

iFolder's user settings are stored in 
```
~/.local/share/simias
```

If you screw up the client's configuration, simply delete this directory to start fresh.


To execute iFolder, you have to type in the full path ( unless you added the path "/opt/ifolder/bin to your profile).  Assuming that you compiled using --prefix=/opt/ifolder, then the command to execute iFolder is:
```
/opt/ifolder/bin/ifolder
```


You could also make a menu entry with the menu editor.
The iFolder icon is located at:
```
/opt/ifolder/share/ifolder3/images/ifolder128.png
```

---

### Post by flar on 2007-06-12
.

---

### Post by flar on 2007-06-12
.

---

### Post by flar on 2007-06-15
I've been running iFolder under heavy usage all week, no problems at all.

---

### Post by suoko on 2007-06-25
can I just suggest to use CHECKINSTALL instead of "make install" so that you end up with a .deb instead of files scattered around?

---

### Post by suoko on 2007-06-25
problem when installed compiled ifolder

tempted overwrite of `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is in libgconf2-4

solution?

---

### Post by flar on 2007-06-25
> **suoko said:**
> problem when installed compiled ifolder

tempted overwrite of `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is in libgconf2-4

solution?

hmm, "make install" would overwrite that file.  That's what I did and have had no problems.  I'm not sure what that file does.  If you want to go the checkinstall route, you could force dpkg  to overwrite the file.  If you wanted the original version of the file back you could reinstall libgconf2-4.

---

### Post by drobinson on 2007-07-03
I was following these directions right up to the point where I need to build simias.  After checking out simias there is no configure script.  There is an autogen.sh script to build the make file and I assume a configure script.  When I run autogen.sh I am required to install additional packages.  I was able to install these except for libxml2-devel.  Apt-get was unable to find this package.  Any ideas on where I can get this?

Thanks

---

### Post by drobinson on 2007-07-03
I figured out the libxml2-devel problem.  For debian the package is called libxml2-dev.  After I got that installed I still had problems with the autogen.sh script.  It was looking for Makefile.in files and the source has Makefile.am files everywhere.  I used find to change the name to Makefile.in and ran autogen.sh without error.  Now when I run make it says: 
make
Makefile:34: *** missing separator.  Stop.

Line 34 looks like this:
if WINDOWS

Its been a while since I've actually looked at make files.  I'm not sure what to do next and I'm not sure if I should have renamed all the Makefile.am files.

Anybody tried this recently and gotten it working?  I'm assuming the source has changed since these instructions were posted.

---

### Post by flar on 2007-07-03
EDIT: look at my next post


The version has changed.  I re-downloaded the source using the commands above and got revision 6898.

The versions I got to compile successfully:

ifolder:  3.4.7162.1 (basically, iFolder 3.4 revision 7162)
simias: 1.4.7162.1  (simias 1.4 revision 7162)


Maybe if you search around forgesvn1.novell.com/svn/ you can find revision 7162.

---

### Post by flar on 2007-07-03
drobinson:  try downloading the source again, because I just ran ./autogen.sh and make and simias compiled successfully without changing anything

---

### Post by mt@ut on 2007-08-13
To build successfully, you also need the following packages (some of which may be installed already in Ubuntu with gnome but weren't in the default install of Kubuntu):

subversion
automake1.9
libgtk2.0-dev
gnome-sharp2
gtk-sharp2
libtool


Automake in feisty is by default 1.10 and doesn't work with novell's makefile templates.  (ifolder build closes with error "can't find Makefile.in").  1.9 appears to get automatically selected when it's installed and it works fine.  The other stuff just comes up in errors as you build.

---

### Post by makzy on 2007-08-16
I also needed to install uuid-dev before being able to build simias.

---

### Post by makzy on 2007-08-16
... as well as a lot of mono junk (libmono-winforms1.0-cil and libmono-ldap1.0-cil (and 2.0, just in case)). will make gutsy packages of this if I ever get it compiled all right... ;)

---

### Post by fizgig on 2007-10-11
I found I couldn't compile simias until I installed the "libstdc++5" package.

Also, ./configure doesn't exist in the ifolder directory anymore.  You have to run 
./autogen --prefix=/opt/ifolder

When autogen calls the configure script it created, I then get the next error:

> ./configure: line 4327: syntax error near unexpected token `external'
./configure: line 4327: `     AM_GNU_GETTEXT(external)'I edit the configure script at line 4327 to change it from 

[B]AM_GNU_GETTEXT(external)

[/B]to

**AM_GNU_GETTEXT="external"**

---

### Post by ikus060 on 2007-11-08
fizgig -> I want to know if you install it on feisty or on Gusty.

With subversion I got the revision 6988 and ./configure doesn't exist any more. So I run ./autogen.sh. I receive this error : 
```

checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
./configure: line 6076: AM_PROG_LIBTOOL: command not found
NDOC_CMD=
configure: checking whether a location for the simias data directory was specified...
checking for pkg-config... /usr/bin/pkg-config
checking for xml2-config... /usr/bin/xml2-config
configure: updating cache config.cache
configure: creating ./config.status
**config.status: error: cannot find input file: Makefile.in**

```

---

### Post by elvar on 2008-12-12
> **ikus060 said:**
> fizgig -> I want to know if you install it on feisty or on Gusty.

With subversion I got the revision 6988 and ./configure doesn't exist any more. So I run ./autogen.sh. I receive this error : 
```

checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
./configure: line 6076: AM_PROG_LIBTOOL: command not found
NDOC_CMD=
configure: checking whether a location for the simias data directory was specified...
checking for pkg-config... /usr/bin/pkg-config
checking for xml2-config... /usr/bin/xml2-config
configure: updating cache config.cache
configure: creating ./config.status
**config.status: error: cannot find input file: Makefile.in**

```


I too am getting the 'config.status: error: cannot find input file: Makefile.in' error. I really would like to use this but after six hours of trying to get around this error I'm giving up.

---

### Post by flar on 2009-01-19
If I recall correctly, I think I just copied Makefile.in from the simias tree and it worked fine.  I kept the compiled source and it installs and works perfectly on hardy and intrepid as well. 

Ifolder is an extremely useful and reliable program.  The code is a bit heavy handed and the requirements are strange, but it runs well.  I've never had a crash or slowdown and it has always performed flawlessly.  I use it to sync my laptop and desktop and also as a backup utility on my server.  Some people might say that other tools such as unison make ifolder unnecessary, but that's not true.  Ifolder is much, much better, easier to use, more reliable and predictable and works through strange firewall and vpn situations. It's too bad that the project seems dead.

---


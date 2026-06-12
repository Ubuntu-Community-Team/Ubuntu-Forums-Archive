---
title: "Create a config folder in home (deb package)"
date: 2009-04-30
forum: Packaging and Compiling Programs
---

### Post by poisonkiller on 2009-04-30
How can I make my deb package to create a config folder in home? I tried putting this into my rules file, just before copying the real program:
# Add here commands to install the package into debian/program.
mkdir $(CURDIR)/debian/program/home
mkdir $(CURDIR)/debian/program$(HOME)
mkdir $(CURDIR)/debian/program$(HOME)/.program
cp $(CURDIR)/src/bin/Release/some_file.txt $(CURDIR)/debian/program$(HOME)/.program
cp $(CURDIR)/src/bin/Release/program $(CURDIR)/debian/program/usr/bin

That doesn't work quite correctly, because if I want to uninstall the deb package, it tries to delete my real home folder. So, what do I have to do?

---

### Post by poisonkiller on 2009-05-07
Anybody? I really need help with this... :(

---

### Post by grantbuntu on 2009-05-10
I'm a deb packaging newbie and I came across your post because I wanted to do the same thing - add files and folders to the installing user's home directory.

After reading [http://ubuntuforums.org/archive/index.php/t-513933.html]("http://ubuntuforums.org/archive/index.php/t-513933.html") I have changed plans.

I will now install everything in /usr/share etc including a menu item under /usr/share/applications.  As different users open the application, any necessary installation of files into their home folder will (quickly) take place.  I can make my python application check for local installation on startup and using os.getenv('HOME') create the necessary folders and copy files from /usr/... as required.  My mistake was thinking of Linux as a single-user system.

I could be wrong about the correct approach so please take this with a grain of salt.  Hopefully it is of some help.

---

### Post by poisonkiller on 2009-05-11
> **grantbuntu said:**
> I'm a deb packaging newbie and I came across your post because I wanted to do the same thing - add files and folders to the installing user's home directory.

After reading [http://ubuntuforums.org/archive/index.php/t-513933.html]("http://ubuntuforums.org/archive/index.php/t-513933.html") I have changed plans.

I will now install everything in /usr/share etc including a menu item under /usr/share/applications.  As different users open the application, any necessary installation of files into their home folder will (quickly) take place.  I can make my python application check for local installation on startup and using os.getenv('HOME') create the necessary folders and copy files from /usr/... as required.  My mistake was thinking of Linux as a single-user system.

I could be wrong about the correct approach so please take this with a grain of salt.  Hopefully it is of some help.

Thank you so much for the idea to copy files from /usr/share! I always thought, that the deb file copies files into the home directory, but now I know better. :P

---


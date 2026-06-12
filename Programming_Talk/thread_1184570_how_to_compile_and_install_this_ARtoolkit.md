---
title: "how to compile and install this ARtoolkit?"
date: 2009-06-11
forum: Programming Talk
---

### Post by abhilashm86 on 2009-06-11
when i downloaded ARtoolkit, the instructions were found, but i din't understand first step, what does this means, when i export and type make
```
abhilash@abhilash:~/Desktop/ARToolKitPlus_2.1.1$ make
make: *** No rule to make target `/usr/lib/qt3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.
abhilash@abhilash:~/Desktop/ARToolKitPlus_2.1.1$ 


```

Compile Steps:
--------------

- Modify build/linux/options.pro to your needs
- Set ARTKP environment variable to source tree

  for bash: export ARTKP='<path_to_artoolkitplus_source_tree>'
  for tcsh: setenv ARTKP '<path_to_artoolkitplus_source_tree>'

- Start compilation with

  make

- You should end up with

  ./lib ... ARToolKitPlus shared libraries
  ./bin ... 
	    simple   ... Sample program
	    idpatgen ... For generating ID markers

- For executing, do not forget to update your LD_LIBRARY_PATH

please help me install this.........

---

### Post by Zugzwang on 2009-06-11
Dear OP (original poster),

[LIST]
[*] You have ran into the problem that some files are missing on your system. This can be seen more or less directly from the error message. Since Ubuntu uses package management, it is worthwhile searching for a package containing that file. In order to do so, redirect your web browser to "http://packages.ubuntu.com", type in the name of the file you are missing (qmake.conf) in the section "Search the contents of packages", select "packages that contain files whose names contain the keyword" and choose your distribution. Then hit search and have a look at the answers. You should get a list of packages containing a respective file. Examine the package names and remember the names of the packages that look promising. Then install them by entering "sudo apt-get install " plus a space-separated list of packages in the terminal. You will need "sudo"-rights for this. Afterwards, see if your problem has vanished. If not, come back reporting what you did (including what you actually searched for) and ask for further help.
[/LIST]

---


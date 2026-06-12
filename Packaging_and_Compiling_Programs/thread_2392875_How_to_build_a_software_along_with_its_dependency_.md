---
title: "How to build a software along with its dependency from source?"
date: 2018-05-26
forum: Packaging and Compiling Programs
---

### Post by asim.qayyum on 2018-05-26
I want to build/install SILE typesetter, which depends on **-dev* packages of some other software. Although these dev packages are available from repositories, I want to use their *sources* available from their websites/github.
Can building static (.a) or dynamic (.so) libraries of these dependencies be a possible path to go? Or some other/better route is necessary/recommended?
Reasons of why I want to build dependencies from source are:

[LIST]
[*]One of the dependencies is **libharfbuzz-dev**. But the version available from repositories is very old; while newer version is available in source.
[*]Another dependency is **libtexpdf** which, although installed, is not working for some reason I don't know.
[/LIST]

---

### Post by monkeybrain20122 on 2018-05-26
You make a folder and install your program and all your dependencies in it (so or the lib and include directories are in this folder) you do this by specifying the prefix (in autoconf, it would be ./configure --prefix=/path/to/your/folder. in cmake it would be cmake -DCMAKE_INSTALL_PREFIX=/path/to/your/folder and there are similar options depending on your build tools)

Then you can set the environmental variables in a startup script for your program so it will use those local dependencies. Basically using export  LD_LIBRARY_PATH=$PREFIX/lib:$LD_LIBRARY_PATH

I have installed gimp-2.10.2 in Ubuntu 16.04 this way (as system libs are too old and not keen on flatpak or snap)

P.S while installing your dependencies you need to build shared libs or enable-shared or the likes depending on your build tools to have the header files (correspond to the -dev packages)

---

### Post by Impavidus on 2018-05-26
Adding to that, the normal directory for manually installed stuff is /usr/local/ and various subdirectories, but you can put it in your home directory if you prefer.

---

### Post by bijayalaxmi1808 on 2018-05-27
From my experience, you can remove the old builds and install a build from the sources you have downloaded.
Sometimes you need to take care of the dependency libraries which might also have to be upgraded.

A standard build which has the following steps to build an executable binary:
- configure by executing the following command in the source directory
```
./configure
```
- Build the executable
```
make
```
- Finally install the new build
```
make install
```

I don't know what is static and dynamic building of the libraries, so can't comment on that.

Probably other experts have better suggestion for you.

---

### Post by oldos2er on 2018-05-27
Moved to Packaging & Compiling Programs.

---

### Post by asim.qayyum on 2018-05-29
> **monkeybrain20122 said:**
> You make a folder and install your program and all your dependencies in it (so or the lib and include directories are in this folder) you do this by specifying the prefix (in autoconf, it would be ./configure --prefix=/path/to/your/folder. in cmake it would be cmake -DCMAKE_INSTALL_PREFIX=/path/to/your/folder and there are similar options depending on your build tools)

Then you can set the environmental variables in a startup script for your program so it will use those local dependencies. Basically using export  LD_LIBRARY_PATH=$PREFIX/lib:$LD_LIBRARY_PATH

I have installed gimp-2.10.2 in Ubuntu 16.04 this way (as system libs are too old and not keen on flatpak or snap)

P.S while installing your dependencies you need to build shared libs or enable-shared or the likes depending on your build tools to have the header files (correspond to the -dev packages)
[COLOR=#000000]So, I would build shared libraries of the dependencies in a folder of my choice, and then I would install the main program in the same folder. Now to use the built libraries at runtime, I would have to set the envronment variable LD_LIBRARY_PATH to this folder. Right?[/COLOR]

---

### Post by monkeybrain20122 on 2018-05-29
> **asim.qayyum said:**
> [COLOR=#000000]So, I would build shared libraries of the dependencies in a folder of my choice, and then I would install the main program in the same folder. Now to use the built libraries at runtime, I would have set the envronment variable LD_LIBRARY_PATH to the this folder. Right?[/COLOR]

Yes, so to avoid repeatedly typing the same directory

you start with 
```

export PREFIX=/path/to/folder/you/install/everything/in
```

Then you have to compile the dependencies in order (say dependency B may depend on A, so have to do A before B etc)
If you use a ./configure script, then for everything
```

./configure --prefix=$PREFIX --other options
``` 
(adjust if use other build methods like cmake or qmake etc)

This way the program you build will find and use version of dependencies already installed in your folder

To run the program you need to load the environmental variables 
e.g you can make a script, call it your program's name, make it executable, put it in your $PATH, say /home/your_user_name/bin (if bin  doesn't exist, create it)

```

#! /bin/bash

export PREFIX=/path/to/folder/you/install/everything/in

export LD_LIBRARY_PATH=$PREFIX/lib:$LD_LIBARY_PATH

export PATH=$PREFIX/bin:$PATH

$PREFIX/bin/my_program_name


``` (modify as needed)

Then you can start the program by just typing the script's name (which is your program's name in this example) in the terminal, you can even create a launcher for it by making a .desktop file with the EXEC= line pointing to the script if it is a gui application.


As Impavidus said, you should put your $PREFIX (the folder where you install everything in) in your $HOME. that way it is isolated from the system in case of conflicting library versions and you don't need sudo.

---


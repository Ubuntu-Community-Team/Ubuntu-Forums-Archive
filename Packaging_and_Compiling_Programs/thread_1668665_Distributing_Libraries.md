---
title: "Distributing Libraries"
date: 2011-01-16
forum: Packaging and Compiling Programs
---

### Post by roadkillguy on 2011-01-16
Quick question, does linux have a distributable library equivalent to the .dll on windows?  Or does the user have to sudo apt-get install all the libraries my application requires?

Thanks.

I apologize for these duplicate topics. I pressed the submit new thread button multiple times assuming it would simply resend the request rather than create new topics.  Sorry for the inconvenience.

---

### Post by Simian Man on 2011-01-16
You should not distribute libraries required by your application as you would with a Windows programs.  If you are providing your program as source, leave it to the users to install the libraries (either from source or a package manager).  If you are providing packages, then you should list the libraries as dependencies.

---

### Post by roadkillguy on 2011-01-16
Alright, thanks for the info.

---

### Post by roadkillguy on 2011-01-20
Could I also use the -static option under g++ to bring the required libraries straight into the executable? Or should I create a .deb package with my project and dependencies in it?

---

### Post by Cheesehead on 2011-01-20
Try it both ways, and see which you prefer.

In package-based communities like Ubuntu, it's considered rude to bloat your final product with a lot of libraries that duplicate what the user already has installed. One of the biggest advantages of package management in distributions like Ubuntu is the power it gives you to keep your final product small and focused, and the user's system light and modular. So if you plan to distribute to Ubuntu or Debian users, the best choice is to create a .deb and dependencies.

Of course, if you need a specific version of a library for a very good reason, and it conflicts with Ubuntu's version, then go right ahead and include it. That's how Java-based packages in Ubuntu do it. But few (if any) others.

---

### Post by SevenMachines on 2011-01-21
Libraries should be dependencies and not statically linked if at all avoided. 

* It increases size

* Security risks unless you manually keep these libraries updated with security fixes. Best have library maintainers do that than have to do it all yourself ( This is very important! )

* Need to manually update the program if the library changes to fix some breakage on distribution version

I can imagine theres a few more good reasons not to do it but those come quickly to mind. All in all, statically linking libraries means more work for you, dynamic linking means getting the benefit of authors and maintainers work for no extra effort ( usually :) ). Less maintenance work all round, less security risk, everyone's a winner!

---

### Post by roadkillguy on 2011-01-21
Now that I know I'm creating a .deb package, where should I place the different files in the user's computer?  
Config files?
Binaries? (That should be in usr/games/ correct?)
Textures and other data? (I want it to be easily editable by the user.)

---

### Post by SevenMachines on 2011-01-21
The resource for what directories are for what is
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

Its worth a read for a basic understanding but is also handy for reference 

The following should be fairly true although i've always been a bit hazy on this stuff :)
Imagine you have a program called 'myapp', then the most common directories you'll probably use are

/usr/bin = binaries for users, put the myapp binary here
/usr/games = same as above but for games

/etc/myapp  = myapp's system wide configuration files if needed

/usr/share/myapp =  architecture independent data, put *static* textures and data in here
/usr/share/games/myapp = same as above but for games

/var/lib/myapp = variable program data, data myapp changes
/var/games/myapp = same as above but for games

Stuff you want to change while running the app but should be done on a per-user basis should go in the users home directory and not in the system hierarchy

You might want to find a similar app or game and look at where it installs its files as an example too

---


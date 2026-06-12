---
title: "Help with GTKmm 2.4"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by rajaram_s on 2008-04-29
Hey.. can anyone guide me how to compile a program which uses gtkmm 2.4. I tried the foll program;

#include<gtkmm.h>	

int main(int argc,char *argv[])
{
	Gtk::Main kit(argc, argv);

    Gtk::Window window;

    Gtk::Main::run(window);
    
    return 0;

}

When I complile the program with g++, with the command,

 g++ gttk.cc `pkg-config gtkmm-2.4 --cflags --libs`
Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.4' found
gttk.cc:1:19: error: gtkmm.h: No such file or directory
gttk.cc: In function ‘int main(int, char**)’:
gttk.cc:5: error: ‘Gtk’ has not been declared
gttk.cc:5: error: expected `;' before ‘kit’
gttk.cc:7: error: ‘Gtk’ has not been declared
gttk.cc:7: error: expected `;' before ‘window’
gttk.cc:9: error: ‘Gtk’ has not been declared
gttk.cc:9: error: ‘window’ was not declared in this scope

Does it mean I dont have gtkmm on my computer? I just made an update, and it instlled an update for libgtkmm too. What could be the problem? If its not installed, how can I make a direct install using apt-get instead of downloading the binary packages?

---

### Post by mavl4219 on 2008-05-05
Well, you didn't provide object file name:

```
g++ simple.cc -o simple `pkg-config gtkmm-2.4 --cflags --libs`
```

This is from gtkmm [tutorial chapter 3]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html#sec-basics-simple-example"):

But i think your problem is in missing dependencies.

Are you sure you've installed the libgtkmm-2.4-dev package?

Search for the gtkmm.h file. It is most probably in the /usr/include/gtkmm-2.4/ dir.

Best Regards,
Mario

---


---
title: "Errors while compiling gtkmm 3.0 programs"
date: 2012-12-05
forum: Programming Talk
---

### Post by Searock on 2012-12-05
I've recently downloaded and installed gtkmm 3.0 and tried to compile hello world example from their [documentation]("http://developer.gnome.org/gtkmm-tutorial/3.4/sec-basics-simple-example.html.en")

[PHP]
#include <gtkmm.h>

int main(int argc, char *argv[])
{
  Glib::RefPtr<Gtk::Application> app =
    Gtk::Application::create(argc, argv,
      "org.gtkmm.examples.base");

  Gtk::ApplicationWindow window;

  return app->run(window);
}
[/PHP]


but it fails to compile and I get the following errors

> searock@searock:~/snippets$ g++ test.cc -o test `pkg-config gtkmm-3.0 --cflags --libs`
test.cc: In function ‘int main(int, char**)’:
test.cc:5:16: error: ‘Application’ is not a member of ‘Gtk’
test.cc:5:16: error: ‘Application’ is not a member of ‘Gtk’
test.cc:5:32: error: template argument 1 is invalid
test.cc:5:38: error: invalid type in declaration before ‘=’ token
test.cc:6:10: error: ‘Gtk::Application’ has not been declared
test.cc:9:3: error: ‘ApplicationWindow’ is not a member of ‘Gtk’
test.cc:9:26: error: expected ‘;’ before ‘window’
test.cc:11:13: error: base operand of ‘->’ is not a pointer
test.cc:11:19: error: ‘window’ was not declared in this scope

When I tried searching for the errors I found that Gtk::Application::create method is available from gtkmm 3.4 and my version is gtkmm 3.0

And I also found another snippet which compiled and ran successfully.

[PHP]#include <gtkmm.h>

int main(int argc, char *argv[]) {
    Gtk::Main kit(argc, argv);
    Gtk::Window window;
    Gtk::Main::run(window);
    return 0;
}[/PHP]

Does this mean that examples in official gtkmm documentation will only work in 3.4 or above?

Do they have a documentation for 3.0 version?

I'm confused as they have only released unstable version upto gtkmm 3.1

---

### Post by Hetepeperfan on 2012-12-05
You can run:

```
$pkg-config --modversion gtkmm-3.0
```

to see which version of gtkmm you use. And indeed, Gtk::Application is introduced in version 3.4 and since that version using Gtk::Main is deprecated.
Recent versions of ubuntu ship with a recent version of gtkmm, at least 12.04 does.

---

### Post by bird1500 on 2012-12-06
If you download and install Gtk(mm) yourself then you either love pain or hacking.
Spare yourself hours/days/weeks of troubles and install a recent version of Ubuntu which comes with a recent version of gtk(mm). Ubuntu 10.04 is history.

---

### Post by Searock on 2012-12-06
> **Hetepeperfan said:**
> You can run:

```
$pkg-config --modversion gtkmm-3.0
```

to see which version of gtkmm you use. And indeed, Gtk::Application is introduced in version 3.4 and since that version using Gtk::Main is deprecated.
Recent versions of ubuntu ship with a recent version of gtkmm, at least 12.04 does.

I've two machines one with 11.10 and other with 12.10 (gnome remix)

So I've downloaded and installed gtkmm 3.0 in 11.10 and I get the three versions for ```
$pkg-config --modversion gtkmm-3.0
``` 

gtkmm 2.4
gtkmm 3.0
gtkmm 3.0-dev

(I guess it was prefixed with lib-)

while in 12.10 it says 

> Package gtkmm-3.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-3.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-3.0' found


I even tried running ```
dpkg -l |grep gtkmm
``` and it shows me the following output in 12.10

> libgtkmm-3.0-1:amd64                      3.5.13-0ubuntu1                            amd64        C++ wrappers for GTK+ (shared libraries)

I can't compile the program in 12.10 as it says 

```
Package gtkmm-3.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-3.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-3.0' found
test.cc:1:20: fatal error: gtkmm.h: No such file or directory
compilation terminated.

```
> **bird1500 said:**
> If you download and install Gtk(mm) yourself then you either love pain or hacking.
Spare yourself hours/days/weeks of troubles and install a recent version of Ubuntu which comes with a recent version of gtk(mm). Ubuntu 10.04 is history.

I didn't know it would be such a pain :)

Is it possible to run the programs on 12.10 (gnome remix)?

---

### Post by SledgeHammer_999 on 2012-12-06
In 12.10 do a:

[php]pkg-config --list-all | grep -i gtkmm[/php]

Does it return anything?

Have you installed the **libgtkmm-3.0-dev** package?

---

### Post by Searock on 2012-12-07
> **SledgeHammer_999 said:**
> In 12.10 do a:

[php]pkg-config --list-all | grep -i gtkmm[/php]

Does it return anything?

Have you installed the **libgtkmm-3.0-dev** package?

It displays nothing for 12.10 and I get the following result for 11.10

> gtkmm-3.0    gtkmm - C++ binding for the GTK+ toolkit

---

### Post by SledgeHammer_999 on 2012-12-08
I installed 12.10 in a Virtual Machine to check this out.

You should:
1. Run "sudo apt-get update"
2. Run "sudo apt-get install libgtkmm-3.0-dev"
3. Now "pkg-config --list-all | grep -i gtkmm" should give a 3.0 entry

If you cannot find the "libgtkmm-3.0-dev" package you should try to change the mirror apt/synaptic/software center uses. The default mirror may be corrupted.
If you already have installed the "libgtkmm-3.0-dev" package you should try reinstalling it.

If all this fail I don't know what else could be wrong with your install.

---

### Post by Searock on 2012-12-08
> **SledgeHammer_999 said:**
> I installed 12.10 in a Virtual Machine to check this out.

You should:
1. Run "sudo apt-get update"
2. Run "sudo apt-get install libgtkmm-3.0-dev"
3. Now "pkg-config --list-all | grep -i gtkmm" should give a 3.0 entry

If you cannot find the "libgtkmm-3.0-dev" package you should try to change the mirror apt/synaptic/software center uses. The default mirror may be corrupted.
If you already have installed the "libgtkmm-3.0-dev" package you should try reinstalling it.

If all this fail I don't know what else could be wrong with your install.

Thanks a lot SledgeHammer. Its working as expected. Thanks for all the help :)

---

### Post by SledgeHammer_999 on 2012-12-08
What did you do to fix it?

---

### Post by Searock on 2012-12-11
> **SledgeHammer_999 said:**
> What did you do to fix it?

Installing libgtkmm-3.0-dev solved my problem. Thanks for the help.

---


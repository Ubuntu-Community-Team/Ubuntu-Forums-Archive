---
title: "C++: Getting home directory and setting path?"
date: 2012-12-25
forum: Programming Talk
---

### Post by fallenshadow on 2012-12-25
Hi guys/gals,

Recently I have been packaging a program of mine. However for things like the preferences config I needed to change the path to:

$HOME/.config/.myApp

However I can't find a way to do this without errors. First I tried just setting a path like this:

mkdir("$HOME/.config/.photofiltrelx", 0770

Then I tried this (as I read $HOME is not recognized in C++):

    ```
struct stat st;
    struct passwd *pw = getpwuid(getuid());

	const char *homedir = pw->pw_dir;
	std::string h = std::string(homedir);
	std::string path = h + "/.config/.photofiltrelx";
	
    if(stat(path,&st) == 0)
    //etc...
```

Error:
> cannot convert ‘std::string {aka std::basic_string<char>}’ to ‘const char*’ for argument ‘1’ to ‘int stat(const char*, stat*)

Any ideas of a good way to do this?

---

### Post by dwhitney67 on 2012-12-25
> **fallenshadow said:**
> 
Any ideas of a good way to do this?

Works just fine:
```

#include <pwd.h>
#include <string>

int main()
{
    passwd* pw = getpwuid(getuid());
    std::string path(pw->pw_dir);
    path += "/.config/.photofiltrelx";

    //...
}

```
An alternative, but not trustworthy, way to obtain one's home directory is to examine the value of the environment variable HOME.  This value can be spoofed, and hence the reason it is not considered worthy of using.

An example:
```

#include <cstdlib>
#include <string>

int main()
{
    const char* home = getenv("HOME");

    if (home)
    {
        std::string path(home);
        path += "/.config/.photofiltrelx";

        //...
    }
}

```

---

### Post by SledgeHammer_999 on 2012-12-26
Since you're using gtkmm:

[Glib::get_home_dir()](http://developer.gnome.org/glibmm/unstable/group__MiscUtils.html#ga9412ea70c7fea058c03211dac318f8e6) gets you the HOME directory.
[Glib::get_user_config_dir()](http://developer.gnome.org/glibmm/unstable/group__MiscUtils.html#gae517b931f4753abcd48adb2769a8fc48) gets you the XDG config directory

---

### Post by fallenshadow on 2012-12-26
I started with your method Dwhitney, I got kinda far with it but ran into trouble with fstream for some reason:

```

prefs.cc: In member function &#8216;void prefsDialog::on_prefs_dialog_response(gint)&#8217;:
prefs.cc:113:45: error: no matching function for call to &#8216;std::basic_ifstream<char>::basic_ifstream(std::string&, const openmode&)&#8217;
prefs.cc:113:45: note: candidates are:
/usr/include/c++/4.6/fstream:460:7: note: std::basic_ifstream<_CharT, _Traits>::basic_ifstream(const char*, std::ios_base::openmode) [with _CharT = char, _Traits = std::char_traits<char>, std::ios_base::openmode = std::_Ios_Openmode]
/usr/include/c++/4.6/fstream:460:7: note:   no known conversion for argument 1 from &#8216;std::string {aka std::basic_string<char>}&#8217; to &#8216;const char*&#8217;
/usr/include/c++/4.6/fstream:446:7: note: std::basic_ifstream<_CharT, _Traits>::basic_ifstream() [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.6/fstream:446:7: note:   candidate expects 0 arguments, 2 provided
/usr/include/c++/4.6/fstream:420:11: note: std::basic_ifstream<char>::basic_ifstream(const std::basic_ifstream<char>&)
/usr/include/c++/4.6/fstream:420:11: note:   candidate expects 1 argument, 2 provided
prefs.cc:131:28: error: no matching function for call to &#8216;std::basic_ofstream<char>::basic_ofstream(std::string&)&#8217;
prefs.cc:131:28: note: candidates are:
/usr/include/c++/4.6/fstream:629:7: note: std::basic_ofstream<_CharT, _Traits>::basic_ofstream(const char*, std::ios_base::openmode) [with _CharT = char, _Traits = std::char_traits<char>, std::ios_base::openmode = std::_Ios_Openmode]
/usr/include/c++/4.6/fstream:629:7: note:   no known conversion for argument 1 from &#8216;std::string {aka std::basic_string<char>}&#8217; to &#8216;const char*&#8217;
/usr/include/c++/4.6/fstream:614:7: note: std::basic_ofstream<_CharT, _Traits>::basic_ofstream() [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.6/fstream:614:7: note:   candidate expects 0 arguments, 1 provided
/usr/include/c++/4.6/fstream:588:11: note: std::basic_ofstream<char>::basic_ofstream(const std::basic_ofstream<char>&)
/usr/include/c++/4.6/fstream:588:11: note:   no known conversion for argument 1 from &#8216;std::string {aka std::basic_string<char>}&#8217; to &#8216;const std::basic_ofstream<char>&&#8217;

```

passwd* pw = getpwuid(getuid());
std::string path(pw->pw_dir);
path += "/.config/.photofiltrelx/prefs.conf";

Line 113:     std::ifstream ifile(path,std::ios::binary);

Any ideas?

---

### Post by dwhitney67 on 2012-12-26
the constructor for fstream (ofstream or ifstream) takes a const char* for the path, not an STL string.

Get the const char* reference of the underlying string within the STL string using c_str().

For example:
```

std::ifstream ifile(path.c_str(), std::ios::binary);

```

---

### Post by SledgeHammer_999 on 2012-12-26
@fallenshadow see my method too. It's easier.

---

### Post by fallenshadow on 2012-12-26
Ah I got it working now. Didn't seem to work on my netbook but I started again on my PC and it works. I probably just did it a bit different the second time around.

However thanks for the responses! Really helped! @SledgeHammer I might switch to this method if I can see an advantage to it. :)

---

### Post by SledgeHammer_999 on 2012-12-26
**@fallenshadow**
your application(and any other one) should use the freedesktop.org standards as much as possible. There is already the [XDG Base Directory Standard](http://standards.freedesktop.org/basedir-spec/latest/) which already defines the path to where applications should save the configurations files. By default it is $HOME/.config but the user can change it by specifying the XDG_CONFIG_HOME environment variable. You should take this possibility in consideration too.

(and yes the functions I linked to adhere to the XDG standard.)

---

### Post by dwhitney67 on 2012-12-26
> **SledgeHammer_999 said:**
> **@fallenshadow**
your application(and any other one) should use the freedesktop.org standards as much as possible. There is already the [XDG Base Directory Standard](http://standards.freedesktop.org/basedir-spec/latest/) which already defines the path to where applications should save the configurations files. By default it is $HOME/.config but the user can change it by specifying the XDG_CONFIG_HOME environment variable. You should take this possibility in consideration too.

(and yes the functions I linked to adhere to the XDG standard.)
From the FreeDesktop.org main page:
"freedesktop.org is not a formal standards organization..."

Whereas it might be interesting to employ the XDG "standard" in a project, I would not think of it as being an absolute requisite/necessity.

---

### Post by SledgeHammer_999 on 2012-12-26
You are right, but I have seen many projects switching to it. I think it has become a de facto standard.

Of course everyone can use whatever he wants.

---


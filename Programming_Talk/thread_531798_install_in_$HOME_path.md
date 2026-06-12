---
title: "install in $HOME path"
date: 2007-08-22
forum: Programming Talk
---

### Post by munna_dude on 2007-08-22
hi all
how to specify the $HOME path in spec file,
to install the files in $HOME..

is it possible..
if yes,
please tell me the way..
am very glad to send an appropriate spec file..
coz, i read some spec file nobudy given the path of $HOME...

please help me 

thank you in advance

---

### Post by jfinkels on 2007-08-22
> **munna_dude said:**
> hi all
how to specify the $HOME path in spec file,
to install the files in $HOME..

is it possible..
if yes,
please tell me the way..
am very glad to send an appropriate spec file..
coz, i read some spec file nobudy given the path of $HOME...

please help me 

thank you in advance

I don't really understand what you are trying to ask exactly, but if you want to execute a program using the $HOME environment variable, which specifies the current user's home directory, just put in ```
$HOME
``` wherever you might have put in ```
/home/username
```

For example, if I want to list the contents of the directory specified by $HOME, I would do:```
ls $HOME
```

---

### Post by munna_dude on 2007-08-22
> **jfinkels said:**
> I don't really understand what you are trying to ask exactly, but if you want to execute a program using the $HOME environment variable, which specifies the current user's home directory, just put in ```
$HOME
``` wherever you might have put in ```
/home/username
```

For example, if I want to list the contents of the directory specified by $HOME, I would do:```
ls $HOME
```

sorry...
i am asking about...
```

Summary: GNU Globe7VOIP
Name: munna
Version: Beta
Release: FC7
Group: Utilities/System
Source0: %{name}-%{version}.tar.gz
Packager: {%Packager}
BuildRoot: %{_tmppath}/%{name}-%{version}-buildroot
URL: http://blabla.com/
License: GPL
Requires: smart
BuildArch: noarch

%description
The GNU indent program reformats C code to any of a variety of
formatting standards, or you can define your own.
%prep
%setup -q
%build
make
%install
%clean
rm -rf %{buildroot}
%files 
**/home/munna/**one/ramesh

```

please observe the bold text...
the path oh $HOME=/home/munna

have to give dynamically...

means..
i created an rpm ...
i have to install all file in the $HOME/one path..

then how to specify this path in spec file...

i think you understood what am asking..

please help me 

thank you in advance

---

### Post by jfinkels on 2007-08-22
> **munna_dude said:**
> sorry...
i am asking about...
```

Summary: GNU Globe7VOIP
Name: munna
Version: Beta
Release: FC7
Group: Utilities/System
Source0: %{name}-%{version}.tar.gz
Packager: {%Packager}
BuildRoot: %{_tmppath}/%{name}-%{version}-buildroot
URL: http://blabla.com/
License: GPL
Requires: smart
BuildArch: noarch

%description
The GNU indent program reformats C code to any of a variety of
formatting standards, or you can define your own.
%prep
%setup -q
%build
make
%install
%clean
rm -rf %{buildroot}
%files 
**/home/munna/**one/ramesh

```

please observe the bold text...
the path oh $HOME=/home/munna

have to give dynamically...

means..
i created an rpm ...
i have to install all file in the $HOME/one path..

then how to specify this path in spec file...

i think you understood what am asking..

please help me 

thank you in advance

I don't really know what a 'spec' file is, but have you tried putting in '$HOME' in place of '/home/munna'?

---

### Post by jordanmthomas on 2007-08-23
Thing is, if you're installing an rpm, wouldn't root always be the one installing it and not your standard user (munna in your example)?

---


---
title: "Dedicated CS Server"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by StukonLinux on 2013-03-29
[COLOR=#ff0000]Running Ubuntu 12.04. I'm trying to setup a VPS CS. 1.6 server to the latest Steampipe beta. It seems like im on a 64 bit and need to install the 32bit lib. I'm getting this error but I followed the steps and it's stating this....[/COLOR][B]

[COLOR=#CCCCCC][FONT=Arial]sudo dpkg --add-architecture i386[/FONT][/COLOR]
[COLOR=#CCCCCC][FONT=Arial]dpkg: error: unknown option --add-architecture[/FONT][/COLOR]

[COLOR=#CCCCCC][FONT=Arial]Type dpkg --help for help about installing and deinstalling packages[/FONT][/COLOR][/B]
[LIST]
[*][B];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked[/B]
[*][B]produce a lot of output - pipe it through `less' or `more' !

If there is something else that may be needed please let me know...thanks BTW i searched hence the reason I posted this in this forum post...sorry[/B]
[/LIST]

---

### Post by tgalati4 on 2013-03-30
What steps did you follow?  I don't see a switch for --add-architecture i386.

```
man dpkg
```

Normally you would install:

ia32-libs - ia32 shared libraries - transitional package

But, there are probably a few more things you need to do to get it working.

---

### Post by StukonLinux on 2013-03-30
> **tgalati4 said:**
> What steps did you follow?  I don't see a switch for --add-architecture i386.

```
man dpkg
```

Normally you would install:

ia32-libs - ia32 shared libraries - transitional package

But, there are probably a few more things you need to do to get it working.

Well I followed all the directions just until this part...then I get the error..Pls help. I'd really like to get this going..thanks

[https://developer.valvesoftware.com/wiki/SteamCMD#32-bit_libraries_on_64-bit_Linux_systems](https://developer.valvesoftware.com/wiki/SteamCMD#32-bit_libraries_on_64-bit_Linux_systems)

---

### Post by tgalati4 on 2013-04-04
```
sudo apt-get install ia32-libs
```

---


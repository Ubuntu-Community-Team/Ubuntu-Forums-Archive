---
title: "Publishing a simple project in KDevelop"
date: 2006-08-02
forum: Programming Talk
---

### Post by Randomskk on 2006-08-02
I'm making some (fairly simple) programs in C++, and while I have been using Kate to write the code, I've decided to swap to KDevelop for when the programs start having more than one file :P

One of the nice things I've noticed is that KDevelop can export a .tar.gz of (supposedly) all the files you need to send someone for them to do a simple "./configure, make, make install". However, I've noticed if I make a "Simple Hello World" project, which seems to be the only pure console-based project option for C++, the files that are included in the .tar.gz are not enough to ./configure it!

When I extract the tar file, and try to run configure, I get this:
adam@random:~/cpp/test/linkedlists$ ./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..


However, configure runs fine in the actual source directory.
On the Distribution and Publishing screen, there's a file list of what gets included - but I can't find a way to edit this list.

How can I either add the required files onto the list, or use a different project type which will make a correct .tar.gz, and is still console-based?

Thanks

---

### Post by cro.smiley on 2006-08-04
> **Randomskk said:**
> 
When I extract the tar file, and try to run configure, I get this:
adam@random:~/cpp/test/linkedlists$ ./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..


I have the same problem. I found somewhere that this thing is broken and it doesn't work as it should. Maybe you could try latest Kdevelop release.

> **Randomskk said:**
> 
How can I either add the required files onto the list, or use a different project type which will make a correct .tar.gz, and is still console-based?
Thanks
I don't think you can add files to list, but what you can do is:

```
make distclean
make dist
```

You must be in your project directory (not src one).
If all goes well you should get tar.gz package in your project directory.
You need make distclean to remove executable files, so that they don't end in package.

And this is it.
If you want to change package name and version, open configure.in and change line: AM_INIT_AUTOMAKE(yourproject, version)

This is what i'm doing with my project: TimeSaver

---


---
title: "Install RPM on Ubuntu"
date: 2018-10-11
forum: New to Ubuntu
---

### Post by llmunro on 2018-10-11
Hi forum!

This is basic, but I can't get it working.

The company I work for uses Blue Jeans for meetings. The Blue Jeans website only offers an RPM file, which I don't really know how to install on my Ubuntu set up (18.04).


I have found instructions here, but can't make them work. [https://medium.com/@ijeyanthan/howto-install-bluejeans-app-on-ubuntu-e719edbc65f1](https://medium.com/@ijeyanthan/howto-install-bluejeans-app-on-ubuntu-e719edbc65f1)

I appear to have been able to install alien, which from what I understand would convert the RPM file into a DEB for installation? I've downloaded the RPM file. And then things start going wrong.

```
sudo alien&#8202;&#8212;&#8202;to-deb bluejeans-*.rpm
```

Gives me the following error: ```
sudo: alien&#8202;&#8212;&#8202;to-deb: command not found
```

How to solve? Or can someone walk me through installing an RPM? 

Thank you!

Lisa

---

### Post by deadflowr on 2018-10-11
try 
```
alien --to-deb
```
space it between alien and the double dash --

Ubuntu's alien man page probably shows it clearer:
[http://manpages.ubuntu.com/manpages/bionic/man1/alien.1p.html]("http://manpages.ubuntu.com/manpages/bionic/man1/alien.1p.html")

---

### Post by llmunro on 2018-10-11
Not quite sure what to do with the following? 



 [HTML]Option to is ambiguous (to-deb, to-lsb, to-pkg, to-rpm, to-slp, to-tgz)
Usage: alien [options] file [...]
  file [...]                Package file or files to convert.
  -d, --to-deb              Generate a Debian deb package (default).
     Enables these options:
       --patch=<patch>      Specify patch file to use instead of automatically
                            looking for patch in /var/lib/alien.
       --nopatch        Do not use patches.
       --anypatch           Use even old version os patches.
       -s, --single         Like --generate, but do not create .orig
                            directory.
       --fixperms           Munge/fix permissions and owners.
       --test               Test generated packages with lintian.
  -r, --to-rpm              Generate a Red Hat rpm package.
      --to-slp              Generate a Stampede slp package.
  -l, --to-lsb              Generate a LSB package.
  -t, --to-tgz              Generate a Slackware tgz package.
     Enables these options:
       --description=<desc> Specify package description.
       --version=<version>  Specify package version.
  -p, --to-pkg              Generate a Solaris pkg package.
  -i, --install             Install generated package.
  -g, --generate            Generate build tree, but do not build package.
  -c, --scripts             Include scripts in package.
      --target=<arch>       Set architecture of the generated package.
  -v, --verbose             Display each command alien runs.
      --veryverbose         Be verbose, and also display output of run commands.
  -k, --keep-version        Do not change version of generated package.
      --bump=number         Increment package version by this number.
  -h, --help                Display this help message.
  -V, --version            Display[/HTML]

---

### Post by mastablasta on 2018-10-12
whats is the full command you wrote?

it is quite clear. it says you need to type in "alien" then "-d" or "--to-deb" and then the "file name". and at option you can even add a few others in there if you need them.

---

### Post by deadflowr on 2018-10-12
Nothing ambiguous about it
your command was
```
sudo alien&#8202;&#8212;&#8202;to-deb bluejeans-*.rpm
```
but it should be
```
sudo alien --&#8202;to-deb bluejeans-*.rpm
```
or alternately
```
sudo alien -d bluejeans-*.rpm
```

The spacing and the dashes are key and important.

---


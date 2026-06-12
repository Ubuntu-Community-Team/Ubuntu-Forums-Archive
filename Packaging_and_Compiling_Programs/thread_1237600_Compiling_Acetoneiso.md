---
title: "Compiling Acetoneiso"
date: 2009-08-11
forum: Packaging and Compiling Programs
---

### Post by s3a on 2009-08-11
Yes, I know there are .debs but I'd like to learn how to make the .deb files myself.

I've succesfully created .deb files before with other programs by doing:

1) cd /home/deniz/Acetoneiso_2.0.3.2
2) dh_make --createorig
3) sudo apt-get build-dep *packagename*
4) dpkg-buildpackage

I know that step 3 would not work since an older version of acetoneiso is not in the repositories (acetoneiso is not in the repositories at all) so I added the dependencies manually from the readme file.

A problem arises as of step 2. Could anyone figure out what I am doing wrong?:

[I]deniz@debian:~$ cd /home/deniz/Desktop/Acetoneiso_2.0.3.2
deniz@debian:~/Desktop/Acetoneiso_2.0.3.2$ ls
acetoneiso.pro  AUTHORS    FEATURES  LICENSE  manual  README   ui
acetoneiso.qrc  CHANGELOG  images    locale   menu    sources
deniz@debian:~/Desktop/Acetoneiso_2.0.3.2$ dh_make --createorig
The directory name must be <package>-<version> for dh_make to work!
I cannot understand the directory name or you have an invalid directory name!

Your current directory is /home/deniz/Desktop/Acetoneiso_2.0.3.2, perhaps you could try going to
directory where the sources are?

Please note that this change is necessary ONLY during the initial
Debianization with dh_make.  When building the package, dpkg-source
will gracefully handle almost any upstream tarball.

deniz@debian:~/Desktop/Acetoneiso_2.0.3.2$ cd sources
deniz@debian:~/Desktop/Acetoneiso_2.0.3.2/sources$ dh_make --createorig
The directory name must be <package>-<version> for dh_make to work!
I cannot understand the directory name or you have an invalid directory name!

Your current directory is /home/deniz/Desktop/Acetoneiso_2.0.3.2/sources, perhaps you could try going to
directory where the sources are?

Please note that this change is necessary ONLY during the initial
Debianization with dh_make.  When building the package, dpkg-source
will gracefully handle almost any upstream tarball.

deniz@debian:~/Desktop/Acetoneiso_2.0.3.2/sources$[/I]

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by zackiv31 on 2009-08-13
Since you're helping me :) ...

i just did a 'man dh_make' and came across this:

```

dh_make must be  invoked  within  a  directory  containing  the
       source  code,  which  must be named <packagename>-<version>. The <packagename> must be all lowercase, digits and dashes. If the directory name does not conform to this scheme, you must rename it
       before using dh_make.  Alternatively, you may be able to use the --packagename option to force the package name.

```

So maybe renaming the actual directory you're in to:

acetoneiso-2.0.3.2

will do the trick?

---

### Post by s3a on 2009-08-13
Thanks but that doesn't help. For details:

[I]deniz@debian:~$ cd /home/deniz/Desktop/acetoneiso_2.0.3.2
deniz@debian:~/Desktop/acetoneiso_2.0.3.2$ dh_make --createorig
The directory name must be <package>-<version> for dh_make to work!
I cannot understand the directory name or you have an invalid directory name!

Your current directory is /home/deniz/Desktop/acetoneiso_2.0.3.2, perhaps you could try going to
directory where the sources are?

Please note that this change is necessary ONLY during the initial
Debianization with dh_make.  When building the package, dpkg-source
will gracefully handle almost any upstream tarball.

deniz@debian:~/Desktop/acetoneiso_2.0.3.2$ cd sources
deniz@debian:~/Desktop/acetoneiso_2.0.3.2/sources$ dh_make --createorig
The directory name must be <package>-<version> for dh_make to work!
I cannot understand the directory name or you have an invalid directory name!

Your current directory is /home/deniz/Desktop/acetoneiso_2.0.3.2/sources, perhaps you could try going to
directory where the sources are?

Please note that this change is necessary ONLY during the initial
Debianization with dh_make.  When building the package, dpkg-source
will gracefully handle almost any upstream tarball.

deniz@debian:~/Desktop/acetoneiso_2.0.3.2/sources$[/I]

Basically - the exact same issue.

---

### Post by mc4man on 2009-08-13
my idiocy at times

---

### Post by s3a on 2009-08-18
I do have the archived source in the same directory.

---

### Post by mc4man on 2009-08-18
Sorry, missed what you were working with. (was late and not paying att.) After extracting rename the extracted source to 
acetoneiso-2.0.3.2

(( you obviously don't need the tar.gz in the dir. w/createorig

---

### Post by zackiv31 on 2009-08-19
umm... s4a... ya, you need to rename the directory and replace all underscores "_" with hyphens "-"

---


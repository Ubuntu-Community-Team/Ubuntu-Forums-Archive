---
title: "Environment variables in debhelper."
date: 2011-10-07
forum: Packaging and Compiling Programs
---

### Post by MG&amp;TL on 2011-10-07
I have quite a simple question: In makefiles and BASH, you can use environment variables like $(USER) or $(DESTDIR), or in BASH, without the brackets.

It does not seem to be possible in debhelper, however. If, for example I wanted to install something to someone's homefolder, I would use debian/<package>.install:

```
<mybitofprogram> /home/$USER/<where it's meant to go>
```

for example.

However, if I do this, what actually happens is that my filesystem looks like this after build and install:

```
</>
  <home>
    <$USER>
      <mybitofcode>
    <myname>
      <Documents>
      ....
```

How would I go about this?

(I don't actually want to do this, I want a symbolic link from /usr/ to home/username/ but I need to do it with dh_link and a debian/package.links)

Thank you.

---

### Post by Bachstelze on 2011-10-07
It's generally considered rude to put stuff in someone else's home folder. Either have your program create the files when the user first runs it, or put them into /usr/share for the user to copy in their home folder. Also, what did you expect the value of $USER to be? Whatever it is, if those files are necessary to run the program, only this use would be able to run the program.

Your strategy is wrong, what are you trying to do?

---

### Post by MG&amp;TL on 2011-10-07
I need to have a read/write to the folder it is in, that's the point so they can access it easily (I 'understand', it's not my program). However, I realise putting a huge amount of stuff in somebody's homefolder is rude ;), so I thought a symbolic link from /usr/share to to the homefolder backup would be a good thing (The actual byte-age would be under a MB, encrypted text). I have suggested that the program be rewritten, but that has not come about yet.

I didn't offer to package the program because I thought I was good at it, I offered because I wanted the experience and he was even less experienced. (and did not have the time). Just so you don't think I'm getting too big for my boots. :)

Alternatively, if you could tell me where read/write/execute for a normal user is meant to go other than /home, please do. I don't really want to *chmod* a directory (and it doesn't work, really) Although I'd still like to know how the variables work.

And thank you, bachstelze, I seem to recognize you from somewhere. ;)

$USER is an environment variable (or it is normally, doesn't seem to be in fakeroot or root access levels) Like $DESTDIR, which I remember so well from my previous encounters.

---

### Post by Bachstelze on 2011-10-07
I still don't understand what you want to do. If you could explain exactly why you need to put something in a user's home dir, maybe I or someone else could suggest a more Debian-friendly way to achieve the same thing.

---

### Post by MG&amp;TL on 2011-10-07
I have a java application in a .jar format; a BASH script that runs the java, and I also need a backup folder for the java's files. The java source code needs constant read/write access to the backup folder. The Java is NOT to be run as root (it's a password-storing program).

My thinking was that the java needs r/w-therefore it must be /home. But I can't just dump the source code in /home-that's not done, especially if you have separate /home partitions. So I thought a single hidden file in /home (like all the other config r/w ones like ssh and thunderbird) , symlinked to the java source directory.


Source directory is probably going to be /opt. The BASH will be in /usr/bin or similiar; I need that for the exec statements in the desktop files. (I suppose I don't have to, but it's convenient)

---

### Post by MG&amp;TL on 2011-10-07
I can post key files (debian/*) and "ls" return values if it helps.

And thank you, bachstelze, and others. You've been very patient. I get programming, that's logical, but it seems as if somebody's made a slightly half-hearted attempt to make debian simple. (although I appreciate it, I can't imagine life without dh_*)

---

### Post by Bachstelze on 2011-10-07
Just have the script check at run time whether the directory is there, and create it if it is not. That's how virtually everyone does it, this does not belong in the packaging.

And it's something the program should do, not you, but patching the shell script is a much better way to go than whatever you were thinking of

---

### Post by MG&amp;TL on 2011-10-08
The program requires that the backup folder be in its current directory, if it's not there it tried to create one.

Okay, thank you. I shall relay that I need an absolute path to a read/write location. For future reference, how DO I use environment variables in debhelper? Or is it not designed for that?

---

### Post by Bachstelze on 2011-10-08
I don't think you can.

---

### Post by MG&amp;TL on 2011-10-08
Seems a bit odd...but okay, thank you. :)

---

### Post by Bachstelze on 2011-10-08
> **MG&TL said:**
> Seems a bit odd...but okay, thank you. :)

The point of packaging is reproducibility. If you have the same source package, you should be able to run [font=monospace]debuild[/font] on any system and get the same result. This is what allows packagers to develop and test packages on their own machine before sending the source package to the archive build servers.

Since environment variables by definition depend on the environment, they would break the reproducibility, so what you want is not possible for a very good reason.

---

### Post by MG&amp;TL on 2011-10-08
Right...but then what is the point of environment variables in compiling/building at all, by that argument? 

You see CXXFLAGS used a lot, for instance. And DESTDIR.

---

### Post by Bachstelze on 2011-10-08
> **MG&TL said:**
> Right...but then what is the point of environment variables in compiling/building at all, by that argument? 

You see CXXFLAGS used a lot, for instance. And DESTDIR.

Because CXXFLAGS or DESTDIR are set by the build system and are not used otherwise, so you can control their values in your configure script or Makefile. USER, however, really depends on the system. You can't just set it at will, or your program will behave weirdly.

---

### Post by MG&amp;TL on 2011-10-08
Okay. so how do the programs that handle things like ssh or gpg do it?

---

### Post by Bachstelze on 2011-10-08
> **MG&TL said:**
> Okay. so how do the programs that handle things like ssh or gpg do it?

Do what?

---

### Post by MG&amp;TL on 2011-10-09
Well, if you do:

```
ls -a
```

in your home folder, there is folders like .mozilla. Presumably they are there after installing firefox, but how they can do that if they don't use environment variables.

---

### Post by Bachstelze on 2011-10-09
As I said, those folders are created by the program when the user first runs it, not by the package. If you look into your home folder right after installing Firefox, you will not have .mozilla.

*EDIT:* If you think about it for a minute, you will realize it just doesn't make sense to do it in the package. As I said, whar should the value of USER be? Whatever it is, only this user would be able to use the program. And even if you could somehow create it for all users, what about users created after the package was installed ?

---

### Post by MG&amp;TL on 2011-10-10
Well, I gave up in the end, I gave the package to the myapps guys, I will get the package and see how they did it.

I will post here. :)

---


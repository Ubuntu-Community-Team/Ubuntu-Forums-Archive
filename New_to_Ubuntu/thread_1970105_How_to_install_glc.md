---
title: "How to install glc?"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by wilson888888888 on 2012-04-30
I'm trying to some minecraft videos, but recordmydesktop does a really horrible job. Now I'm trying to install glc by following the instructions in here: [https://github.com/nullkey/glc/wiki/Install](https://github.com/nullkey/glc/wiki/Install)
When i type ./glc-build.sh after installing all the necessary packages, it gives me this:

info  : Welcome to glc install script!
        Enter path where glc will be installed.
          (leave blank to install to root directory)
      > 
        Enter compiler optimizations.
          (-O2 -msse -mmmx -fomit-frame-pointer)
      > 
        Use git (y/n)
          (git contains latest unstable development version)
      > n
info  : Fetching sources...
error : Can't fetch elfhacks

Can I continue installing it even with the error?

---

### Post by jtarin on 2012-04-30
Here's a [link]("http://www.secretmaryo.org/phpBB3/viewtopic.php?t=5446") that might give some insight.

---

### Post by wilson888888888 on 2012-04-30
I ran sudo apt-get install git core, then ./glcbuild.sh
It says that it can't compile 32 bit glc, but I already used all the commands necessary for 64 bit.

---

### Post by wilson888888888 on 2012-05-01
I successfully installed glc by adding it to the repository. When I enter glc-capture <executable> to start recording, it gives me this:

bash: syntax error near unexpected token `newline'

---

### Post by jtarin on 2012-05-01
Look [here]("http://ubuntuforums.org/showthread.php?t=1255606") then examine your script.

---

### Post by wilson888888888 on 2012-05-01
I tried the command glc-capture executable, but it gave me:
can't execute "executable"

Also, I entered glc-capture --help, and couldn't find executable in it, even though that's what they used here: [http://www.dedoimedo.com/computers/glc.html](http://www.dedoimedo.com/computers/glc.html)

---

### Post by jtarin on 2012-05-02
You should only have to type "glc-capture"...... The executable bit should be your applications executable that you want to record. Now I'm only guessing at this as I don't use this, but the logic is there. :)

---

### Post by wilson888888888 on 2012-05-03
I tried this, and it just shows the same thing as glc-capture --help. Sorry for the delayed response, I was busy with school stuff.

---


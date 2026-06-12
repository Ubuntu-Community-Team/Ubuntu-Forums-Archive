---
title: "Automate debianization of your source packages."
date: 2011-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by d3v1150m471c on 2011-04-04
A lot of times we will want to compile certain software to get more out of our system. Many source packages, especially those found in launchpad are able to be compiled and debianized so you can install them as a .deb and properly manage your installs/uninstalls. This isn't the most difficult thing to do but it can be time consuming and has to be done by hand. However, this is how I've been doing it. 

First, well need to make a directory called `Build' in our home folder. So:
```

mkdir /home/$USER/Build

```Next, copy this bash script and place it somewhere like a personal bin, or where you'd store your useful scripts. For this tutorial let's name the script `buildit'.
```

#!/bin/bash
redir="$PWD"
cd /home/$USER/Build
for i in `ls | grep -i "tar"`; do
 tar -xf "$i"
done

for i in `ls`; do
 if [[ "$i" != *'tar'* ]]; then
  if [[ $(ls "$i") == *debian* ]]; then
   echo ""
   echo "     *** DEBIANIZING: $i ***     "
   cd "$i"
   dpkg-buildpackage -rfakeroot
   cd $OLDPWD
   echo "     --- End Log For: $i ---     "
   echo ""
  else
   echo "package: $i  is not suited for debianization"
   echo ""
  fi
 fi
done

cd "$redir"

```Next, open .bashrc in your home folder and append the following line to it:
```

alias buildit="/path/to/buildit/script"

```Now enter the following in your terminal:
```

chmod +x /path/to/buildit/script
. .profile

```Now you can download your source.tar.gz packages that are setup for debianization, and download them directory to the Build folder, or drag and drop them in it, and enter the following:
```

buildit

```And you're done! Look inside the Build folder and there's your new .deb packages. I set the script up with easy to read "logs" incase you're compiling several packages and one or more of them doesn't build. Happy hacking :)

---


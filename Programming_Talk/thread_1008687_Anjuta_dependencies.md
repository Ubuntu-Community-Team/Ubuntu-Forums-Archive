---
title: "Anjuta dependencies"
date: 2008-12-11
forum: Programming Talk
---

### Post by DrPepper836 on 2008-12-11
First of all, I'd like to say that I'm new to Linux and so I don't know a whole lot about the community. I recently got a new computer and put Ubuntu on it to do my main programming work in because Vista runs very slowly on it. I found that Anjuta looks like the best kind of IDE for what I'm used to, but I'm having issues with installing all of the dependencies that you need to write all of the programs for Gnome, etc, as the links on their website don't work and I can't figure out any of the other places to download them. Does anyone here know how to set that stuff up?

---

### Post by Zugzwang on 2008-12-12
Dear OP (original poster),

[LIST]
[*] It looks like as if you are frequently running into the problem that some files are missing on your system. Since Ubuntu uses package management, it is worthwhile searching for a package containing the specific files. For example if "#include <zlib.h>" raises a file-not-found error, then you know what's missing. In order to install the missing packages, redirect your web browser to "http://packages.ubuntu.com", type in the name of the file you are missing (note that the error message may contain parts of paths special to your system, like your home path if it is searched for the missing file there - make sure to strip them beforehand) in the section "Search the contents of packages", select "packages that contain files whose names contain the keyword" and choose your distribution. Then hit search and have a look at the answers. You should get a list of packages containing a respective file. Examine the package names and remember the names of the packages that look promising. Then install them by entering "sudo apt-get install " plus a space-separated list of packages in the terminal. You will need "sudo"-rights for this. Afterwards, see if your problem has vanished. If not, come back reporting what you did (including what you actually searched for) and ask for further help.
[/LIST]

---


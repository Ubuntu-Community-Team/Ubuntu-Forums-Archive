---
title: "How do i start building .deb ? (Is it necessary  in this case)"
date: 2009-08-21
forum: Packaging and Compiling Programs
---

### Post by wrapster on 2009-08-21
Hi all,

Due to some issues I have to build .deb pkgs from the beginning...
But I do not have the source.. so that I could have done apt-get source <pkg name>

Here is the story.
I have a few svr4 pkgs(with the pkgmap and the pkginfo and the rest) available with me..
I used 'alien' to convert it to .deb.

#alien -d SUNWonbld
(after a few warning the .deb pkg was generated)
#dpkg -i SUNWonbld.deb
Dependency problems prevented from configuring sunwonbld.
<depedency list give was>
sunwbizp
sunwgzip
sunwzlib

Now My question is how to Fist of all procure these pkgs and should i manually construct the .deb pkg out of it? If so im a newbie to deb so can anyone please direct me to pointers..

Secondly would like to know if alien is a good enough too to be used to convert the .pkg---> .deb .
(In which case it will only be a matter of finding out the resource to get these .pkgs from)

Please help..

---

### Post by arky on 2009-08-23
sudo apt-get build-dep <package-name> will get you all the dependency pacakges

---


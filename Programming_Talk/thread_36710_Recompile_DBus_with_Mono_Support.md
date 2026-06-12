---
title: "Recompile DBus with Mono Support"
date: 2005-05-24
forum: Programming Talk
---

### Post by jaboo on 2005-05-24
I really like Mono as a dev platform, and I want to stay up-to-date with the latest versions. I want to have the benefits of the bug fixes, new class methods and/or properties, and the Windows.Forms namespace. I also want to be able to use some of the mainstream applications like beagle and muine.

In the past I have used checkinstall to create standalone debs for the various packages that one has to build. This is problematic when one has to use some of the sources from SVN where one has to use autogen. Invariably a file called INSTALL will want to replace a file of the same name from another package, and I have to force the package to overwrite, which I consider to be a bad thing. I wanted Mono though. This works just fine for getting Mono as a dev platform, but there are problems with getting something like muine to compile, as it wants dbus-sharp.

 I am using the Hoary release. I tried a dist-upgrade the other day to find that X was severely borked. The way debian packages dbus splits it up into several different deb packages. There is a libdbus-cil package, but it depends on having deb packages for Mono. Is there a way to recompile the dbus packages to include the configure option for Mono support? Am I wanting too much with this? Thanks for reading and any help.

---


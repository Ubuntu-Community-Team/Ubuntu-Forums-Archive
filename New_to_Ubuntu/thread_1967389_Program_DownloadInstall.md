---
title: "Program Download/Install"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by Bryrim on 2012-04-28
OK, so I noticed this when I downloaded Adobe Flash, and now I'm seeing it with Avast! Anti-virus. When I click the 'Download' link, it gives me three separate options for download. 'RPM', 'DEB', and 'TAR GZ'.

So which should I download and/or which is the best? Or does it even matter which one?

---

### Post by xedi on 2012-04-28
Generally for Ubuntu .deb packages are the best for a beginner, because they are the easiest to install (double click on the .deb file -> click on install -> input password -> done). tar.gz often works too but is less straight forward and .rpm is for other Linux distributions which use different package managers (e.g. Fedora).

---

### Post by Bryrim on 2012-04-28
Great. Now I downloaded the DEB file, opened it, and in the Software Center it says 'Wrong architecture 'i386'' and when I click 'Install' it doesn't do anything...

---

### Post by xedi on 2012-04-28
Was there an option to download it for a 64bit system? (which I assume you are using). If not, then it is possible to force an installation of 32bit packages on a 64bit operating system. However, before we try that out, according to this guy [http://askubuntu.com/questions/119884/avast-antivirus-for-ubuntu](http://askubuntu.com/questions/119884/avast-antivirus-for-ubuntu)

it should be enough to just run  

```
cd ./Downloads
sudo dpkg -i avast4workstation_1.3.0-2_i386.deb
```

in the terminal assuming the .deb is in your Donwloads folder.

To access the terminal, open the dash (the ubuntu sign in the corner or push super/windows key) and type in terminal or skip all that and use the ctrl + alt + t shortcut.

Then type in the lines (or copy and paste with ctrl + shift + v) in one by one and press enter after each line.

What I didn't think about before, though, is the following: Why do you want an anti-virus in Ubuntu? For average users this is unnecessary, which is one of the advantages of Linux, that it is virus free.

---


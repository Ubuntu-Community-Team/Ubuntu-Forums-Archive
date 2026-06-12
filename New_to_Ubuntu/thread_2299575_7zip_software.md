---
title: "7zip software"
date: 2015-10-19
forum: New to Ubuntu
---

### Post by fund_raiser on 2015-10-19
Hello

I have a **rar** file. It is compressed. I tried installing 7zip from repositiories to unrar it, but after installing 7zip this software is nowhere to find. It is not in **accessories.  **How to find 7zip and unpack the rar file. Where can I find 7zip on my system? It is already installed on my OS. 

thx

---

### Post by slickymaster on 2015-10-19
7zip is a command line application. Once installed it will be available in the Archive Manager. Just right-click a file and extract it, or use the archive manager to make archives.

---

### Post by sudodus on 2015-10-19
***7z*** is a command line program

```
7z
```

There are instructions in the manual page

```
man 7z
```

But I think that it's tools will also be available via the GUI archiver ***file-roller***, for example the ability to manage different compression formats.

---

### Post by Geoffrey_Arndt on 2015-10-20
The key thing to do is as Slicky wrote "right-click" on the compressed file.    7zip actually adds functionality to the standard nautilus based archive tools - for example, one way you can tell it's installed is you get the option to encrypt (and decrypt) files using 7z AES strong encryption.   That option is not available upon right-click if 7zip is not installed.

---


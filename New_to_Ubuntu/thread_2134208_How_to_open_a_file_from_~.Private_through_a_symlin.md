---
title: "How to open a file from ~/.Private through a symlink on my Desktop?"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by some1at127001 on 2013-04-10
Hello, everyone.

I am using an application (TrueCrypt) every time I need to access some really sensitive information (that is my username and password to the Ubuntu forums) :). The file-container where I keep this info is seriously encrypted and that is enough for any regular person. But not for me. So I want to have that file in ~/.Private, and not on my Desktop or Documents or any other folder.

So I did this:

```

~/Desktop$ cp /Destop/myfile ~/.Private/myfile
~/Desktop$ rm myfile
~/Desktop$ ln -s ~/.Private/myfile /Desktop/myfile

```

The problem is that the program can't open the file located in ~./Private through the link from my Desktop, because it says "Please choose and existing file".

Any idea about how to solve this?

Thank you!

---


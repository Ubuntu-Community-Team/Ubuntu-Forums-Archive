---
title: "Privoxy - how to update?"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by vasa1 on 2012-01-04
The version of Privoxy available from the Ubuntu Software Center is 3.0.17-1 but the latest version is 3.0.19.

Has anyone updated to the latest version and is it a simple thing to do for beginners?

---

### Post by Anstice on 2012-01-04
Go to the link below and choose the file you need. When it downloads it should ask you whether you want to save the file or open it in Ubuntu Software Centre. Use the Software Centre. It will display a message about it being a later version than the one in the centre, ignore it and just install it anyway.

Now I did not have an option in the menu to launch but it did launch from the terminal by simply typing privoxy and hitting enter. Here is where I ran into an error about a missing configuration file. I assume from the fact that you said you are wanting to update that you already have it installed so I would think you would have the required config file.

[http://sourceforge.net/projects/ijbswa/files/Debian/3.0.19%20%28stable%29%20squeeze/](http://sourceforge.net/projects/ijbswa/files/Debian/3.0.19%20%28stable%29%20squeeze/)

---

### Post by Anstice on 2012-01-04
I did a little digging around regarding the config file issue. Privoxy requires you to specify the location of the config file when you start it so you'll just have to point to it when you run it.

---

### Post by vasa1 on 2012-01-04
Hi and thanks for replying!

I went to that link. The stable version is a **tar** file. The other (experimental) versions are debs and about half the size.

I want to use the stable version so I downloaded the tar file and, on double-clicking it, it opens in Archive Manager and not in Ubuntu Software Center. So I have not proceeded further. I guess I'll just have to wait until it's offered by the Ubuntu Software Center since I'm not having any problems (that I can see) with the current version.

---

### Post by vasa1 on 2012-01-08
> **Anstice said:**
> Go to the link below and choose the file you need. When it downloads it should ask you whether you want to save the file or open it in Ubuntu Software Centre. Use the Software Centre. ...
[http://sourceforge.net/projects/ijbswa/files/Debian/3.0.19%20%28stable%29%20squeeze/](http://sourceforge.net/projects/ijbswa/files/Debian/3.0.19%20%28stable%29%20squeeze/)
I followed your instructions but I chose the unstable version since that was a .deb file. Smooth and marking as Solved. Thanks!

---


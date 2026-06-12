---
title: "backing up"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by arnav803 on 2012-11-09
hi i have ubuntu 11.10 and I am completely new to linux  and due to some reason i have to reformat my system i have huge numbers of packages and apps that i dont want to loose and i dont have a fast internet connection so how can i make back up of those programs (specially wine 1.3) and install it on new System.Thanks in advance

---

### Post by lukeiamyourfather on 2012-11-09
As far as I know there's not a good way to backup software installed from packages. If you just backup the installed files and put them on a new system then the new system won't know what packages are installed (since the copied files wouldn't have been installed by the package manager). If you still have the original packages that's what you need to back up and then install them on the new system through the package manager. I think by default packages installed through repositories are thrown away after the install so there might not be any packages to backup unless you manually downloaded them from websites. If there are any from the package manager they would probably be in /var/cache/apt/archives.

---

### Post by ibjsb4 on 2012-11-09
A possibility would be APTonCD

[https://help.ubuntu.com/10.04/add-applications/C/offline.html](https://help.ubuntu.com/10.04/add-applications/C/offline.html)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+copy+and+install+all+software+without+internet&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+copy+and+install+all+software+without+internet&as_qdr=all&sa=Google+Search&lang=en")

And as already mention var/cache/apt/archives is another possibility

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=var%2Fcache%2Fapt%2Farchives+backup&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=var%2Fcache%2Fapt%2Farchives+backup&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

And welcome to the forum  :)

---

### Post by arnav803 on 2012-11-11
Thanks for your quick reply  that helped me.

---


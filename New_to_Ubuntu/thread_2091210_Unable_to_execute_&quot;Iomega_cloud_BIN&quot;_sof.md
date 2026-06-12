---
title: "Unable to execute &quot;Iomega cloud BIN&quot; software"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by cvgx on 2012-12-04
I'm a first time user who Recently installed Ubuntu 12.04 LTS
After reading several Forums I was able to install Iomega Cloud Software xxx.BIN ([https://iomega-na-en.custhelp.com/app/answers/detail/a_id/26108](https://iomega-na-en.custhelp.com/app/answers/detail/a_id/26108)).
However how exactly can I Locate & then execute the program?
In terminal 'mode' I tried GKSU and entered the name of file I thought it may be. Nothing.
IOMEGA Support states its software is compatible up to version 11... however im afraid that if I downgrade to version 11 I still wont know how to run the application.

---

### Post by COMECON on 2012-12-04
> **cvgx said:**
> I'm a first time user who Recently installed Ubuntu 12.04 LTS
After reading several Forums I was able to install Iomega Cloud Software xxx.BIN ([https://iomega-na-en.custhelp.com/app/answers/detail/a_id/26108](https://iomega-na-en.custhelp.com/app/answers/detail/a_id/26108)).
However how exactly can I Locate & then execute the program?
In terminal 'mode' I tried GKSU and entered the name of file I thought it may be. Nothing.
IOMEGA Support states its software is compatible up to version 11... however im afraid that if I downgrade to version 11 I still wont know how to run the application.

It's easy. Open a terminal, switch to the directory where the file is (say /home/cvgx/Downloads) and run this commands:
[b] $ chmod +x xxx.bin
$ ./xxx.bin[/b]
(Of course, replace xxx.bin with the name of the file)

I hope it works to you!
Catbuntu

---

### Post by cvgx on 2012-12-06
I was able to install BIN file, however how to I start the program? 
I searched through folder application is installed and did not recognize program name.
Any help would be appreciated

---


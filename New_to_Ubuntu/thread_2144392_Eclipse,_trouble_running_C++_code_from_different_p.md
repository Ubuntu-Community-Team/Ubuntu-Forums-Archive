---
title: "Eclipse, trouble running C++ code from different partition"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by ClarkH85 on 2013-05-12
I have a few partitions on a new laptop. One partition is /media/storage, where I'm saving files that I may access from either my Ubuntu or Windows 7 partition.

I've installed I think everything I need to in order to compile and run C++ projects (eclipse/g++/other things I can't remember). I'm trying to get hello_world.cpp up and running and having errors. I believe it's due to the fact that I'm saving the code on the /media/storage partition, while Eclipse and all the add-ons are on the Ubuntu partition. 

While opening Eclipse the first time, I specified to set the Workspace folder to be saved to the /media/storage partition. Besides that, I haven't changed any other settings. I think there must still be some configuration changes I must make. If you know of any such settings, could you please help?

Here's a screenshot of the error:

[IMG]http://s21.postimg.org/5kuwhl7ra/Screenshot_from_2013_05_11_23_00_04.jpg[/IMG]

Thank you!

---

### Post by Archit88 on 2013-05-12
can you post compiler output?

---

### Post by ClarkH85 on 2013-05-12
OR, if you have another solution, I would be willing to try something else.

For example, I wouldn't mind having separate workspaces on each of my Ubuntu and Windows partitions, if there were some way I could conveniently share code between them.

---

### Post by ClarkH85 on 2013-05-12
> **Archit88 said:**
> can you post compiler output?

How would I get that output? I've already installed build-essentials too.

Thanks.

---

### Post by Impavidus on 2013-05-12
You put your program on a storage partition that is also readable from Windows. That must be an NTFS partition. NTFS doesn't know about Linux permissions, so you can't make your files there executable.

You can put your executables somewhere else, like in your home directory. They are not executable by windows anyway, so putting them in a shared partition doesn't serve much purpose. I don't know how you can instruct Eclipse to put executables in a different directory than the source code.

---


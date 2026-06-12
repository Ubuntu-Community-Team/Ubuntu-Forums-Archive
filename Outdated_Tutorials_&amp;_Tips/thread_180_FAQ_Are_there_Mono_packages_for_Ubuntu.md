---
title: "FAQ: Are there Mono packages for Ubuntu?"
date: 2004-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-11
At the momoent mono is not in universe. If you want to use mono you can add tseng's mono-repository to your sources.list.

Add the following lines to your /etc/apt/sources.list

> #Mono
deb [http://www.getsweaaa.com/~tseng/ubuntu/debs](http://www.getsweaaa.com/~tseng/ubuntu/debs) ./
deb-src [http://www.getsweaaa.com/~tseng/ubuntu/debs](http://www.getsweaaa.com/~tseng/ubuntu/debs) ./

Save the file and run: sudo apt-get update

---

### Post by Telep on 2004-10-14
I'd like to know whether there is a gtk-sharp developer package available for Ubuntu. I installed everything seemingly related to Mono from tseng's repository, but could not compile gtk# apps. I believe a package called "gtk-sharp" and the corresponding dev package is needed?

---

### Post by tanari on 2004-10-20
i installed mono from universe repository, but i still can't compile MUINE player :(

```


checking for mono &gt;= 0.95... Package mono was not found in the pkg-config search path.
Perhaps you should add the directory containing `mono.pc'
to the PKG_CONFIG_PATH environment variable
No package 'mono' found

configure&#58; error&#58; Library requirements &#40;mono &gt;= 0.95&#41; not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


```

---

### Post by Burgundavia on 2004-10-20
If you just want muine, there is a package already compiled. I think it is with the mono in tsengs

Burgundavia

---

### Post by graham on 2004-10-26
[QUOTE=Burgundavia]If you just want muine, there is a package already compiled. I think it is with the mono in tsengs[/QUOTE]  Sure, but what do you do if you want to compile other apps, or even do some Mono development yourself?
 
 From the Wiki I worked out that I should be able to do:
  ```
sudo apt-get build-dep tomboy
``` 
 but it can't find libmono-dev in any of my repositories. I added universe to my respositories and tried the build-dep again, and it's currently downloading lots of stuff.
 
 Not sure if this was the right thing to do though...

---

### Post by kamstrup on 2004-10-29
Yes. You do need gtk-sharp, but I couldn't find it in universe... I think you can find links to it from the mono homepage.

---

### Post by kamstrup on 2004-10-29
Yes... Here in fact ;) :

[http://mono-project.com/downloads/](http://mono-project.com/downloads/)

---

### Post by andrey_hey on 2006-12-14
> **tanari said:**
> i installed mono from universe repository, but i still can't compile MUINE player :(

```


checking for mono &gt;= 0.95... Package mono was not found in the pkg-config search path.
Perhaps you should add the directory containing `mono.pc'
to the PKG_CONFIG_PATH environment variable
No package 'mono' found

configure: error: Library requirements (mono &gt;= 0.95) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


```


Thought the thread is very old, it could be helpful for somebody to know that you need the 'libmono-dev' package to get that 'mono.pc' file in order for the 'pkg-config' to "find" the mono package during configuration

---

### Post by registerdown on 2008-07-19
> **andrey_hey said:**
> Thought the thread is very old, it could be helpful for somebody to know that you need the 'libmono-dev' package to get that 'mono.pc' file in order for the 'pkg-config' to "find" the mono package during configuration

Thanks andrey_hey, 

I got an error: 
No package 'mono' found
When trying to compile mono-zeroconf in order to get the latest banshee on my ubuntu 7.10. Installing libmono-dev package ad you pointed out solved the problem :)

---

### Post by Zularan on 2008-10-29
> **andrey_hey said:**
> Thought the thread is very old, it could be helpful for somebody to know that you need the 'libmono-dev' package to get that 'mono.pc' file in order for the 'pkg-config' to "find" the mono package during configuration

Thanks for the tip !
(I know it's an old thread but this was giving me a headache)

---


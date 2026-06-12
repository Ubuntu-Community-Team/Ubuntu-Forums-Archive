---
title: "[SOLVED] Swiftweasel"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by loyaleagle on 2008-11-19
Hello everyone,

Is Swiftweasel available for ubuntu 8.10 (AMD64)

An what repository could I add to install it....?

Thanks!

---

### Post by loyaleagle on 2008-11-19
Found Swiftfox..... Just the same for AMD64

Thanks!

---

### Post by aeiah on 2008-11-19
it doesnt look like there is one beyond gutsy (7.10)
[http://swiftweasel.wiki.sourceforge.net/Apt](http://swiftweasel.wiki.sourceforge.net/Apt)

there are deb files though on the sourceforge page. i dont know much about swiftweasel. perhaps there isnt even a .deb for version 3, but there is a tar.gz by the looks. it seems its only maintained by one person so it perhaps isnt as simple as your normal firefox or iceweasel.

---

### Post by drs305 on 2008-11-19
On the home page the creator says an Intrepid version is in the works. If you put the cursor on the Main Menu icon it will expand and there is a link to the repositories and how to add them.
[http://swiftweasel.tuxfamily.org/]("http://swiftweasel.tuxfamily.org/")

---

### Post by MountainX on 2009-08-13
> **loyaleagle said:**
> Found Swiftfox..... Just the same for AMD64

Thanks!

All SwiftFox builds are 32bit, even the AMD64 ones. So use SwiftWeasel instead.

---

### Post by armagedonc on 2009-08-14
> **MountainX said:**
> All SwiftFox builds are 32bit, even the AMD64 ones. So use SwiftWeasel instead.

how can I install swiftweasel, I try downloading the tar packages form the source but when I install them  nothing seems to change.

---

### Post by MountainX on 2009-08-14
> **armagedonc said:**
> how can I install swiftweasel, I try downloading the tar packages form the source but when I install them  nothing seems to change.

There is no need to install anything. Just extract the files and make a launcher. 

There are probably better ways to do it than the steps I used, but here are my steps to get you started:

I downloaded the tar archive and extracted it into /opt/swiftweasel/

(I put all the packages that are not managed by the Ubuntu package management system into /opt.)

The extraction process made a folder and I renamed it to swiftweasel-3.5.2, so my full path is /opt/swiftweasel/swiftweasel-3.5.2/

Then I used the menu edit tool to make a new application launcher. (I think you can just right click the panel and select "add to panel", but I don't remember how I did it.) The command I used in the laucher is:

/opt/swiftweasel/swiftweasel-3.5.2/swiftweasel -no-remote -P "default"

You could use a much simpler command (e.g., /opt/swiftweasel/swiftweasel-3.5.2/swiftweasel)

I also made a hidden directory under my home for my profiles, but I think this will be done automatically in most cases.

/home/myuser/.sw35/swiftweasel

Swiftweasel put a default profile under the above path.

Someone else could probably tell you how to make Swiftweasel replace Firefox 3 as the default browser in Jaunty. I know it can be done, but I don't know the right steps.

Swiftweasel 3.5 is awesome. Everything works better, especially videos.

---

### Post by commonplace on 2009-10-03
I can't get Swiftweasel to work. I downloaded the file, extracted it, and then ran:

```
./swiftweasel
```

and then I also tried:

```
./swiftweasel -no-remote -P "default"
```


Both had the same result:

```
./swiftweasel-bin: symbol lookup error: ./libxpcom.so: undefined symbol: NS_CycleCollectorSuspect2_P
```


Any ideas?

/Kevin

---

### Post by whit on 2009-10-06
```
./swiftweasel-bin: symbol lookup error: ./libxpcom.so: undefined symbol: NS_CycleCollectorSuspect2_P
```

Same here with 3.5.3_amd35-pgo_x86_64-ubuntu. 3.5.1 doesn't have that problem. Must be a different version of whatever library libxpcom.so comes in that it expects to find.

---

### Post by MountainX on 2009-10-07
> **whit said:**
> ```
./swiftweasel-bin: symbol lookup error: ./libxpcom.so: undefined symbol: NS_CycleCollectorSuspect2_P
```Same here with 3.5.3_amd35-pgo_x86_64-ubuntu. 3.5.1 doesn't have that problem. Must be a different version of whatever library libxpcom.so comes in that it expects to find.

3.5.2 was no problem for me. I didn't try any later version yet.

---

### Post by drink on 2009-11-10
You can make 3.5.3 work on Jaunty with some symlinks, but the same fix fails on Karmic.

---

### Post by jdcnosse on 2009-12-02
I got Swiftweasel 3.5.2 to run using the menu editor steps under Karmic...

---


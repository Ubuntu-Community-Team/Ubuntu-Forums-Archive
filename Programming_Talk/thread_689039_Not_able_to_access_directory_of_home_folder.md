---
title: "Not able to access directory of home folder"
date: 2008-02-06
forum: Programming Talk
---

### Post by bargi on 2008-02-06
Hi,

I am trap in a strange problem........

Today when I log in to my PC I was not able to access my home folder directory .

My home folder is :
```

/home/bargi

```

When I run command :
```

cd /home/bargi

```

It show me :
```

bargi@bargi-desktop:~$ cd /home/bargi
bargi@bargi-desktop:~$ 

```

when I run ls command it show me my home folder content........

when I try to switch to directory :

```

cd /home/bargi/Test

```

It give me error :
```

bash: cd: Test: No such file or directory

```

This occurs only when I cd Test....rest of directory are easily accessible.

Last night I have created a C++ project in Test folder.

Also when I run command :

```

sudo -s

``` 

And login as root and run ls command ,it is showing the content of /home/bargi folder.....

Why this is happening ????

Is this is due to that I have created that C++ project ?????

Please help me  :(

Thanks

---

### Post by bargi on 2008-02-06
Hey I solve the problem........

The problem was due to the space ......... Actually I have given a single space after naming 

"Test(Space) ".......When I remove this space it runs.............

But I am confused that in linux it should show me Test folder like this :

```

cd Test\ /

```

If there is space in name. ............????????

Thanks IcemanV9 for your Time :)

---


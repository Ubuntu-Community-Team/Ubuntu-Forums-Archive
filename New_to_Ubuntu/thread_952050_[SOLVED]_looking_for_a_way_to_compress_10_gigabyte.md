---
title: "[SOLVED] looking for a way to compress 10 gigabyte file to 4 gigabye files for burnin"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by stinger30au on 2008-10-18
i have a data file im working with and id like to make a backup of it. the file is a single file that is 10 gigabyte in length and id like to create a few 4 gigabyte files so i can burn them to single layer dvd discs

is there a command i can run that will look at my 10 gig file and create smaller files from it and i can specify what size i want them to be??

eg - filechopper "name of my file" 4000
       program                               kilobyte sizes


clear as mud???

thanks

---

### Post by bsharp on 2008-10-18
> **stinger30au said:**
> i have a data file im working with and id like to make a backup of it. the file is a single file that is 10 gigabyte in length and id like to create a few 4 gigabyte files so i can burn them to single layer dvd discs

is there a command i can run that will look at my 10 gig file and create smaller files from it and i can specify what size i want them to be??

eg - filechopper "name of my file" 4000
       program                               kilobyte sizes


clear as mud???

thanks

```
split --b=4000*4000*4000 input_file
```

Join them with:
```
join file1 file2 file3
```

You might want to test that before deleting your original though.

---

### Post by jerome1232 on 2008-10-18
Use split, man split to learn more about it.

You use cat to put the file back together.

```
split -b 4G filetosplit
```

This will split the file up and add a suffix to it (aa, ab, ac etc..) To put it back together: it'll put it all back together as <filename>

```
cat filenamewithoutsuffix* filename
```

i've found you can't burn 4G files to dvd, though and have made them 2G in size and just stuck 2 on each dvd.

---

### Post by stinger30au on 2008-10-18
sweet thanks for the info guys. 


man this forum rocks


yes you can burn 4 gig files to dvd you need to make you you burn as UDF files. if not oyu will not do it.

K3B is smart enough to do this by default anyhow and i had a lookie at nero 3 for linux it also has a dvd option for burning UDF files as well


out of interest the files once they are split can they be joined together at a windows xp machine at all.
not that  i think i will ever need this, but more for my own curiosity sake

---

### Post by stinger30au on 2008-10-23
> **stinger30au said:**
> 
out of interest the files once they are split can they be joined together at a windows xp machine at all.
not that  i think i will ever need this, but more for my own curiosity sake


after some reading i have learnt if i install wine and install [izarc]("http://www.izarc.org/") i can do all of this and more via gui....

groovy

---

### Post by _sAm_ on 2008-10-23
Ubuntu 8.10 will let you do this with gui using Fileroller.

---

### Post by stinger30au on 2008-10-23
> **_sAm_ said:**
> Ubuntu 8.10 will let you do this with gui using Fileroller.


apparently 8.04 will as well so long as you install p7zip

---

### Post by stinger30au on 2008-10-27
after some reading i have found the best way to do it is to install.rar

instructions here

[http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html](http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html)

---


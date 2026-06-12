---
title: "[Help] List Directory Contents"
date: 2008-08-24
forum: Programming Talk
---

### Post by loganwm on 2008-08-24
I'm programming an app that generates thumbnails for the picture files in a directory, should I use a system call to 'ls' or is there a better way?

---

### Post by jinksys on 2008-08-24
> **loganwm said:**
> I'm programming an app that generates thumbnails for the picture files in a directory, should I use a system call to 'ls' or is there a better way?

Depends, what language?

If C, then you could do this.

```

#include <dirent.h>
#include <stdio.h>
int main(int argc, char **argv){
DIR *dir_ptr;
struct dirent *dirent_ptr;

dir_ptr = opendir(argv[1]);

while((dirent_ptr = readdir(dir_ptr)) != NULL)
      {
        printf("%s\n", dirent_ptr->d_name);
      }

closedir(dir_ptr);

}

```

*[SIZE="1"]Adapted from Pg 5. Advanced Programming in the Unix Environment[/SIZE]*

---

### Post by loganwm on 2008-08-24
> **jinksys said:**
> Depends, what language?

If C, then you could do this.

```

#include <dirent.h>
#include <stdio.h>
int main(int argc, char **argv){
DIR *dir_ptr;
struct dirent *dirent_ptr;

dir_ptr = opendir(argv[1]);

while((dirent_ptr = readdir(dir_ptr)) != NULL)
      {
        printf("%s\n", dirent_ptr->d_name);
      }

closedir(dir_ptr);

}

```

*[SIZE="1"]Adapted from Pg 5. Advanced Programming in the Unix Environment[/SIZE]*

Yes it is C.

I'm not sure if that will work with my current set up, I'll try and implement it though.

Once I get it to a decent prototype I might post the app.

---

### Post by ghostdog74 on 2008-08-24
what tools are you using to generate thumbnails?  If C is not a must, and you have the convert tool from ImageMagick, a little shell script will do
```

for files in *.jpg
do
 /usr/bin/convert -thumbnail 200 $i thumb.${i}
done

```

---

### Post by loganwm on 2008-08-24
> **ghostdog74 said:**
> what tools are you using to generate thumbnails?  If C is not a must, and you have the convert tool from ImageMagick, a little shell script will do
```

for files in *.jpg
do
 /usr/bin/convert -thumbnail 200 $i thumb.${i}
done

```

It's not to "permanently" convert the images, it's for a little viewer that I'm working on with SDL to test my knowledge.

it takes a directory of images, render's a handful of them in small thumbnails and a smaller range of potential "focused" thumbnails that changes as you cycle.

---


---
title: "problem opening a file from inside program."
date: 2011-09-23
forum: Programming Talk
---

### Post by avee137 on 2011-09-23
hello,
I created a char file in my home directory with following command :

```
 mknod myi2c c 256 0

```
then changed permissions on it using :
```
chmod a+rw myi2c 
```


Now i try to open the device file using following code
```
#include<stdio.h>
#include<unistd.h>
#include<fcntl.h>
#include<sys/types.h>
#include<sys/stat.h>


int main(){

int fd , ret ;
fd = open("/home/sccc/myi2c",O_RDWR) ;
if(fd < 0){
perror("myi2c open error :");
}
else
printf("myi2c opened : fd = %d\n",fd );

return 0;
}

```

it throws an error :
```
myi2c open error :: No such file or directory
```


please point out where am i going wrong.

---

### Post by ofnuts on 2011-09-23
> **avee137 said:**
> hello,
I created a char file in my home directory with following command :

```
 mknod myi2c c 256 0

```First check if your code is OK on a regular file?

---


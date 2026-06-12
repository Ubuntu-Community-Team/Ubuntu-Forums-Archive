---
title: "Creating device file in init_module"
date: 2010-11-26
forum: Programming Talk
---

### Post by pswin on 2010-11-26
hi

how can i create a device file in initialization function of module with returned major number from register_chrdev?

my code is:
```
int init_module(void)
{
    Major = register_chrdev(0,DEVICE_NAME,&fops);
    
    if (Major < 0 )
    {
        printk(KERN_ALERT "Registering char device failed with %d\n", Major);
        return Major;
    }

    // creating device file
    int ret = mknod(DEVICE_FILE_NAME, S_IFCHR|S_IRUSR|S_IWUSR|S_IRGRP|S_IWGRP|S_IROTH|S_IWOTH, makedev(Major,0) );

return 0;
}
```

but i can't compile it! what is wrong?

---

### Post by spjackson on 2010-11-27
What errors do you get? Have you included the relevant headers?

---

### Post by pswin on 2010-11-27
> Have you included the relevant headers

headers:
```

#include <linux/module.h>      // Needed by all modules
#include <linux/kernel.h>
#include <linux/fs.h>
#include <asm/uaccess.h>
```


and errors:

> workspace/linux/module/test.c: In function ‘init_module’:
/workspace/linux/module/test.c:68: error: implicit declaration of function ‘mknod’
/workspace/linux/module/test.c:68: error: implicit declaration of function ‘makedev’
...


---


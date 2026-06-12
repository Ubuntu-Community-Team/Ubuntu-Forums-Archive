---
title: "GCC Defining Preprocessor Constant as pwd"
date: 2012-03-25
forum: Programming Talk
---

### Post by ThesaurusRex on 2012-03-25
I've got a project where I use images in a certain directory and whenever I reference the images I use "./". This makes it so I can't run the application from anywhere except that directory where the "./" makes sense. I'd really rather not hard code the full path into the application, but instead create a define using gcc. So I use "gcc main.c -DMY_DIR=`pwd`", but this gives me an error for each level of directory telling me that each identifier is not declared in that scope. For example, an error for 'home,' 'usr,' 'Documents,' and so on. My guess is that gcc is not sending the define in as a string. Ideas on how I can do this?

---

### Post by r-senior on 2012-03-25
You need to quote the string and escape the quotes, e.g.:

```
gcc -DPWD=\"/home/rex/Pictures/\" -o main main.c
```

But you still need to recompile to change the value of the variable. Wouldn't it be better to use a shell variable so that you can alter the path without recompiling:

```
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv)
{
        char *image_path;
        
        if ((image_path = getenv("IMAGE_PATH")) == NULL) {
                /* You could use a default instead of exit with error */
                fprintf(stderr, "Image path not defined\n");
                exit(EXIT_FAILURE);
        }
        
        puts(image_path);
                
        exit(EXIT_SUCCESS);
}

```

Then create a shell variable to define where the images are picked from.

```
$ export IMAGE_PATH=~/Pictures
```

---

### Post by ThesaurusRex on 2012-03-25
Both options work! Thanks for the quick and accurate response.

---

### Post by jwbrase on 2012-03-26
> **r-senior said:**
> ```

        if ((image_path = getenv("IMAGE_PATH")) == NULL) {
                /* You could use a default instead of exit with error */
                fprintf(stderr, "Image path not defined\n");
                exit(EXIT_FAILURE);
        }

```

Wouldn't it be better to fall back on a default path if the variable isn't defined rather than just exiting?

---


---
title: "[Python] Batch rescale images"
date: 2008-09-15
forum: Programming Talk
---

### Post by Slity on 2008-09-15
I'm looking for a simple script what looking for images files like .jpg and png in an folder and all subfolders of that folder, and if the image width an height is bigger than 200x200 resize it to 200x200. Is it a simple task to do? I read the python docs but i don't understand too much... thanks!

---

### Post by ghostdog74 on 2008-09-15
```

find /path -name "*.jpeg" -exec convert  -identify "{}" temp \; |awk '{
    split($3,arr,"x")
    if ( arr[1] > 200 && arr[2] > 200 ) {
        cmd = "convert -resize 200x200 " $1" "$1
        #system(cmd) #uncomment to use
    }
}'


```
The above is a shell script. You can follow the same concept in Python. Use os.walk to recurse directory. Use glob module, or use simple string index to get files with ".jpeg" extension. either you go find a Python image module that can allow you to get information from image files, or if you have the convert command from ImageMagick, issue a system call to "convert".

---

### Post by Slity on 2008-09-15
> **ghostdog74 said:**
> ```

find /path -name "*.jpeg" -exec convert  -identify "{}" temp \; |awk '{
    split($3,arr,"x")
    if ( arr[1] > 200 && arr[2] > 200 ) {
        cmd = "convert -resize 200x200 " $1" "$1
        #system(cmd) #uncomment to use
    }
}'


```
The above is a shell script. You can follow the same concept in Python. Use os.walk to recurse directory. Use glob module, or use simple string index to get files with ".jpeg" extension. either you go find a Python image module that can allow you to get information from image files, or if you have the convert command from ImageMagick, issue a system call to "convert".

Thank you so much! :)

---

### Post by marcel17 on 2009-06-29
I'm looking for an email script that extracts the jpg's attachments from an email; then rescale it to standard width 500; then rename the jpg starting with today's date and removing spaces from the rest of the name; and finally send it back to the email adress from which it was sent from.

That would save me hours of work each month and make my life so much easier.

---


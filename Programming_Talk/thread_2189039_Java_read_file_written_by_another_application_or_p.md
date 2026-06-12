---
title: "Java: read file written by another application or process"
date: 2013-11-20
forum: Programming Talk
---

### Post by erotavlas on 2013-11-20
Hi,

I have an application written in Java that "only" read a file written by another application or process. What I want is to read a file only if it is not in writing by the other application or process. How can I do it?  
Thank you

---

### Post by ofnuts on 2013-11-20
[http://examples.javacodegeeks.com/core-java/nio/filelock/create-file-lock-on-file/](http://examples.javacodegeeks.com/core-java/nio/filelock/create-file-lock-on-file/)

---

### Post by erotavlas on 2013-11-20
Ok, but does this example work also for locking file that are written by non Java application? The other application, the one that writes the files, does not know the existence of the Java application that read the files. Is it ok?

---

### Post by ofnuts on 2013-11-21
You can never tell if that application has set a lock... the locking mechanism is "cooperative". This method uses the system locking mechanism so it will interact with non-Java apps, as long as they do their part.

---

### Post by erotavlas on 2013-11-21
Could something like this work?
The part that write the file is an application in a server typically linux/unix while the part that read the file can be whatever devices that is able to run Java.
```

private boolean isUnderWriting(File file) {
    RandomAccessFile raFile = null;
    try {
        raFile = new RandomAccessFile(file, "r");
        return false;
    } catch (Exception e) {
        System.out.println("Skipping file " + file.getName() + " the file is under writing");
    } finally {
        if (raFile != null) {
            try {
                raFile.close();
            } catch (IOException e) {
                System.out.println("Exception during closing file " + file.getName());
            }
        }
    }
    return true;
}

```

---


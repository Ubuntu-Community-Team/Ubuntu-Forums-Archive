---
title: "Custom File Types?"
date: 2009-05-24
forum: Programming Talk
---

### Post by TheRigger on 2009-05-24
Hello ALL!

Hello I am TheRigger and I am new to this forum. Anyways I am creating a c++ terminal program and i want to have my own file type for some code. How would i go about programming this? Any help or input would be greatly appreciated!!! Thanks in advance!!! :p

---

### Post by soltanis on 2009-05-24
That's pretty simple. If you are asking how to read this kind of file, it's the same way you read any kind of file:

```

FILE *fp = fopen(file, "r+");
if (fp) {
      do_stuff(fp);
      fclose(fp);
} else {
      fprintf(stderr, "error\n");
      exit(1);
}

```

If you are asking how you should organize your file format, then post additional details on what kind of information you are trying to store.

Reading file formats is not a complicated thing; a format is just what it's name suggests, the way data is layed out inside files.
When reading or writing files in a specific format, the idea is that your program be able to read the data structures represented inside the file into variables in memory, so that it can then be able to work with them.

---

### Post by lisati on 2009-05-24
At the end of the day, it's up to you to decide how to organize the data your program produces. There are a handful of conventions to keep in mind (examples: ".txt" files normally contain text data, ".rtf" files contain text formatting information in addition to the text, ".exe" files are generally program files for MS-DOS or Windows, ".deb" files contain packages for debian-based Linux systems) - beyond that, the choice is yours.

---


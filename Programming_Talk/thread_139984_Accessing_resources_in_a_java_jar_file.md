---
title: "Accessing resources in a java jar file"
date: 2006-03-05
forum: Programming Talk
---

### Post by maitreya on 2006-03-05
```
RandomAccessFile inFile;
inFile = new RandomAccessFile(textfile, "r");
```

Packaging the application into a jar file with the textfile. However running the jar file gives the error of "file not found". It seems that it tries to find the file outside the jar package. Any idea on how to fix this.

---

### Post by LordHunter317 on 2006-03-05
You have to open the JAR resource stream:```
InputStream stream = MyClass.class.getResourceAsStream(textfile);
```Have a party.

---

### Post by maitreya on 2006-03-05
Thank you for your help. I managed to get it working:

```
BufferedReader inFile;
InputStream stream;
stream = MyClass.class.getResourceAsStream(textfile);
inFile = new BufferedReader(new InputStreamReader(stream));
```

wrapping it into the BufferedReader.

---


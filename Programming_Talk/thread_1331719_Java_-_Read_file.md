---
title: "Java - Read file"
date: 2009-11-19
forum: Programming Talk
---

### Post by SpinningAround on 2009-11-19
I'm having a little trouble reading a file in java, a file that is selected by the user by entering a file name. Problem is that it look like the program fail to read the given by the user.

```

Scanner inFil = new Scanner(System.in);
System.out.println("File?");
String pathFile = inFil.nextLine();
File fil = new File(pathFile); 
int arr[] = new int[100];
if(!fil.exists()){
	System.out.println("File don't exist");
	System.exit(0);
}

```

---

### Post by Arndt on 2009-11-19
> **SpinningAround said:**
> I'm having a little trouble reading a file in java, a file that is selected by the user by entering a file name. Problem is that it look like the program fail to read the given by the user.

```

Scanner inFil = new Scanner(System.in);
System.out.println("File?");
String pathFile = inFil.nextLine();
File fil = new File(pathFile); 
int arr[] = new int[100];
if(!fil.exists()){
	System.out.println("File don't exist");
	System.exit(0);
}

```

How far does it get?

---

### Post by jimi_hendrix on 2009-11-19
You are not actually reading anything by the looks of it, just opening a file and checking if it exists.

---

### Post by froggyswamp on 2009-11-20
Google "java read file".
```

package readfile;

import java.io.*;

public class Main {

    public static void main(String[] args) {
        System.out.println(readFile("/home/fox/testfile.txt"));
    }

    public static final String readFile(String filePath) {
        File f = new File(filePath);
        if(!f.exists()) {
            System.err.println("File " + f.getName() + " not found");
            return null;
        }

        StringBuilder buffer = new StringBuilder();
        byte[] bytes = new byte[1024];
        int readBytesCount = 0;
        try {
            InputStream in = new BufferedInputStream(new FileInputStream(f));
            while( (readBytesCount = in.read(bytes)) != -1) {
                buffer.append(new String(bytes, 0, readBytesCount));
            }
        } catch(Exception exc) {
            exc.printStackTrace();
            return null;
        }
        return buffer.toString();
    }
}

```

---


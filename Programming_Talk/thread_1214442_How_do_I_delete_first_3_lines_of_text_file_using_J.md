---
title: "How do I delete first 3 lines of text file using Java?"
date: 2009-07-15
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-07-15
I am writing a Java program and I want to call another application with a file.  But I always want to delete the first 3 lines of this file before calling the application.  I know how to do this by reading the file and creating a new file, but is there a way to do it by editing the file without creating a new file?  Just simply delete the first 3 lines of file.

---

### Post by manualqr on 2009-07-15
unless you read the file, strip the first 3 lines of the buffer, and pass the buffer to your other app - I think writing to disk is inevitable.

---

### Post by Finalfantasykid on 2009-07-16
```

// I'm ignoring exception handling because this is just an example, and I'm lazy :P
File file = new File("file.txt");
BufferedReader reader = new BufferedReader(new FileReader(file));
reader.readLine();
reader.readLine();
reader.readLine();
String line;
Vector<String> text = new Vector<String>();
while((line=reader.readLine()) != null){
   text.addElement(line);
}
sendText(text); // this is a method that you would define.  It will send the vector the the file minux the first 3 lines

```Not sure if this is what you wanted, but it's probably what I would do...

---

### Post by croto on 2009-07-16
And good old ed?
```

echo -e "1d\n1d\n1d\nw" | ed -s - $FILENAME

```

---

### Post by SNYP40A1 on 2009-07-16
Ok, that's fine, I can create a new file then.  Just wanted to make sure I was not overlooking a simple way to edit a file in place (without writing to a new file and then deleting the old one).  It's not that big of a deal, just comes up a lot.

---


---
title: "Java(Android): Write XML to file from internet?"
date: 2013-01-07
forum: Programming Talk
---

### Post by fallenshadow on 2013-01-07
Hi all,

I have been trying to write xml to a file for an Android app but Im not quite sure if im doing it correctly.

```

String Path = Environment.getExternalStorageDirectory().getPath() + "/MYAPP/test.xml";
File f = new File(Path);
System.out.println(Path);
					  
//f.createNewFile();
FileOutputStream fOut = new FileOutputStream(f);
OutputStreamWriter myOutWriter = new OutputStreamWriter(fOut);
myOutWriter.append(sb.toString());
myOutWriter.close();
fOut.close();
					  
System.out.println("File written to " + Path);
```

Any ideas?

---

### Post by ofnuts on 2013-01-07
> **fallenshadow said:**
> Hi all,

I have been trying to write xml to a file for an Android app but Im not quite sure if im doing it correctly.

```

String Path = Environment.getExternalStorageDirectory().getPath() + "/MYAPP/test.xml";
File f = new File(Path);
System.out.println(Path);
                      
//f.createNewFile();
FileOutputStream fOut = new FileOutputStream(f);
OutputStreamWriter myOutWriter = new OutputStreamWriter(fOut);
myOutWriter.append(sb.toString());
myOutWriter.close();
fOut.close();
                      
System.out.println("File written to " + Path);
```Any ideas?

You should specify a "Charset' in the constructor, coherent with what you use in the XML (likely 'UTF-8') 
To write stuff you use the write() methods.
You can make a BufferedWriter from your writer

But... normally you don't do it yourself. You handle the XML as a Document and use the right API to write the document to file: [http://stackoverflow.com/questions/4561734/how-to-save-parsed-and-changed-dom-document-in-xml-file](http://stackoverflow.com/questions/4561734/how-to-save-parsed-and-changed-dom-document-in-xml-file)

---

### Post by fallenshadow on 2013-01-08
Ah my writing actually worked it was my reading code that was the problem. All solved now anyway! :)

---


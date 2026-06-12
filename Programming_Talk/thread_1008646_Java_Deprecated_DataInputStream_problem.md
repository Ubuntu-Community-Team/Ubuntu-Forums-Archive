---
title: "Java: Deprecated DataInputStream problem"
date: 2008-12-11
forum: Programming Talk
---

### Post by Igniteflow on 2008-12-11
I have a problem with the DataInputStream throwing a deprecated warning when I compile.  The file does actually compile and run, but it gives the following output after compiling:

Note: Duplicate.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.

[php]
FileInputStream fileInputStream = null;

    BufferedInputStream bufferedInputStream = null;

    DataInputStream dataInputStream = null;



    try 
    {
    // Make file IO available

    fileInputStream = new FileInputStream(file);

	bufferedInputStream = new BufferedInputStream(fileInputStream);

    dataInputStream = new DataInputStream(bufferedInputStream);

      	
      	// While the line is not empty process the line
      	while (dataInputStream.available() != 0) 
      	{

     	String string = null;

        string = dataInputStream.readLine();

        number = Integer.parseInt(string);
[/php]

Does anyone know how I can substitute the buffered reader here without breaking the code??

---

### Post by tinny on 2008-12-11
This is explained in the javadocs

[http://java.sun.com/j2se/1.5.0/docs/api/java/io/DataInputStream.html#readLine()](http://java.sun.com/j2se/1.5.0/docs/api/java/io/DataInputStream.html#readLine())
> 
readLine()
          Deprecated. This method does not properly convert bytes to characters. As of JDK 1.1, the preferred way to read lines of text is via the BufferedReader.readLine() method. Programs that use the DataInputStream class to read lines can be converted to use the BufferedReader class by replacing code of the form:

         DataInputStream d = new DataInputStream(in);
     

with:

         BufferedReader d
              = new BufferedReader(new InputStreamReader(in));
     


Use a BufferedReader (readLine method)

---


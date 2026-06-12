---
title: "Java and using named pipes"
date: 2007-02-28
forum: Programming Talk
---

### Post by Ramses de Norre on 2007-02-28
Yesterday I was shown the concept of named pipes (also called fifos), but it seems that java can't handle them?
I made a fifo in my home directory with **mkfifo clip** and wrote a little script to link a purpose to it: ```
#!/bin/bash

LOC=/home/ramses/clip

if [ -p $LOC ]
then
        while(true)
        do
                xclip -in < $LOC > out
        done
else
        echo "$LOC doesn't exist or is no named pipe, exiting"
        exit 1
fi

```
This all works perfect, but now the problem:
When I write this in java: ```
PrintWriter pW=new PrintWriter(new BufferedOutputStream(new FileOutputStream(new File("/home/ramses/clip"))));
``` the application just hangs on that line... No extensive cpu load, no exceptions, just nothing...
If I create just an OutputStream it works, but not with a PrintWriter.
The same line does work on a regular file.

Anyone who can explain this and maybe knows a workaround?
And the file permissions are set to 777 so that isn't the problem, I can also perfectly write to it from the command line.

---

### Post by Ramses de Norre on 2007-03-01
Someone?

---

### Post by Ragazzo on 2007-03-01
This works for me:

mkfifo pipe
cat < pipe

```

import java.io.*;

class Test {
  public static void main(String[] args) throws Exception {
    PrintWriter pw = new PrintWriter(new BufferedOutputStream(new FileOutputStream("/home/jukka/pipe")));
    pw.println("hello");
    pw.close();
  }
}

```

And then **java Test** in another terminal.

Edit: Don't forget to flush the stream

---

### Post by Ramses de Norre on 2007-03-02
Strange, I didn't try for a few days and now suddenly it does work...
I activated the fifo with ```
while(true); do xclip -in < clip > out; done;
```
And wrote this little java app (it's just a test, I know it isn't good:p)
```
package ogpTest;

import java.io.BufferedOutputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.PrintWriter;

import javax.swing.JOptionPane;

public class Clipboard
{
	public static void main(String[] args) throws IOException
	{
		String s;
		PrintWriter pW=new PrintWriter(new BufferedOutputStream(new FileOutputStream("/home/ramses/clip")));
		
		while (true)
		{
			s = JOptionPane.showInputDialog("Give string to put on clipboard");
			pW.print(s);
			pW.flush();
		}
	}
}

```

It doesn't work as it should though... The things pasted on the clipboard aren't always altered, I guess I'll need to look a bit deeper into this.

---

### Post by beligum on 2010-02-18
Use printLN instead of print, the newline is important.

---


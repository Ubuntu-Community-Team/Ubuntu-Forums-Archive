---
title: "Seeking possible in Java streams?"
date: 2008-09-07
forum: Programming Talk
---

### Post by Habbit on 2008-09-07
Hi there,

I'm facing a problem I had not anticipated in the design of "input plugins" for a Java application. This plugins have the general structure of a canRead method that, given an InputStream, tries to guess whether that particular class can parse the whole stream; and methods to actually perform the import.

However, the point is that the canRead method should, if possible, leave the Stream effectively untouched, i.e. in the same position. I have noticed that there is no "seek" method in Java input streams; I had assumed there would be by similarity with .NET streams, but it seems that I am wrong. Googling for it shows nearly nothing, and maybe the solution is obvious because the question was only asked a few times in thousands of results. Some of the solutions I've been offered include the usage of file-input-specific classes such as RandomAccessFile or FileChannel in the java.nio package (that I don't understand too well o_O), but I don't want to limit myself to files, as "memory streams" can be sources for my "plugins" too.

Thus, how could I, given a simple InputStream, know whether or not it can seek (and do it if possible)?. As an example of what I want, this would be the equivalent c# code: ```

public bool CanRead(Stream is) {
    bool retVal;
    long startPos = is.CanSeek ? is.Position : -1;

    // Check whether this plugin can parse "is" - read from it

    if (is.CanSeek)
        is.Position = startPos;
    return retVal;
}
```

---

### Post by tinny on 2008-09-08
I believe you want to have a look at the InputStream classes "markSupported()", "mark(int readlimit)" and "reset()" methods.

[http://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html](http://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html)

E.g. your implementation may look something like this...

[PHP]
/**
     * Check if a supplied input stream can be parsed.
     * @param is input stream
     * @return true if it can be parsed
     */
    public boolean canParse(InputStream is) throws IOException {
        boolean result = false;
        //Check if this stream can be inspected
        if (is.markSupported()) {
            is.mark(Integer.MAX_VALUE);
            // Check whether this plugin can parse "is" - read from it
            result = inspect(is);
            is.reset();
        } else {
            //Cant predit
            result = false;
        }
        return result;
    }

    /**
     * Inspect this steam to check if it can be parsed.
     * @param is
     * @return true if this stream can be parsed.
     */
    private boolean inspect(InputStream is) {
        //Now read whatever you need to from the stream to determine if your 
        //class can parse this stream.
        //E.g.
        //is.read();
        //is.read(arg0);
        //is.skip(arg0);
        //is.available();
        //etc...
        return true; //can parse
        //return false cant parse
    }
[/PHP]

Hope this helps :)

---

### Post by Habbit on 2008-09-08
Sorry, I forgot to mention that I had already looked into the mark and reset methods. They look more or less like what I want, but FileInputStream does not support them in "Java 5" or the OpenJDK (wtf??). Thus, they are useless to me becase they'd force me to change the prototype of canRead to accept only BufferedInputStream. Thanks anyway :KS

---


---
title: "java new line character"
date: 2012-04-25
forum: Programming Talk
---

### Post by abraxas334 on 2012-04-25
Hi,
I am trying to read a file which has a few new line characters as lines.
It basically looks like this:
10 6\n
23 5\n
34 6\n
34 6\n
\n
\n

If i scan over the file, I don't want the last two lines to be counted, so I define a white space pattern like this:
[PHP]public static Pattern whiteSpacePattern = Pattern.compile("\\s+");[/PHP]

then I want to loop over the lines and disregard the ones which are just empty lines
[PHP]
 while ((textline = randomAccessFile.readLine()) != null) {
                // save old position
                oldPos = currentPos;

                // if commentPattern active, then read away comment lines
                if (usedCommentPattern != null && whiteSpacePattern != null) {

                    if (usedCommentPattern.matcher(textline).matches()) {
                        currentPos = randomAccessFile.getFilePointer();
                        continue;
                    } else if (whiteSpacePattern.matcher(textline).matches()) {
                        currentPos = randomAccessFile.getFilePointer();
                        continue;

                    }
                }
}


[/PHP]

If I look up pattern on this site: [http://docs.oracle.com/javase/1.4.2/docs/api/java/util/regex/Pattern.html]("http://docs.oracle.com/javase/1.4.2/docs/api/java/util/regex/Pattern.html")
\s	is whitespace character: [ \t\n\x0B\f\r]
so \s should contain a new line character, but there is never a match between the whiteSpacePattern and the textline
the line with the new line character can be read. How can i get java to print, what kind of string the line is, because if I do a soutprint of the line with the new line character I don't get anything. How can I check it actually is a new line character i am trying to match. Also did I chose the correct pattern?
The comment line matching works very well. So I don't understand why the white space matching does not work.

Thanks for any help!

---

### Post by trent.josephsen on 2012-04-25
You're not using BufferedReader by any chance?

[http://docs.oracle.com/javase/1.5.0/docs/api/java/io/BufferedReader.html#readLine()](http://docs.oracle.com/javase/1.5.0/docs/api/java/io/BufferedReader.html#readLine())

> public String readLine()
                throws IOException
Read a line of text. A line is considered to be terminated by any one of a line feed ('\n'), a carriage return ('\r'), or a carriage return followed immediately by a linefeed.
Returns:
A String containing the contents of the line, **not including any line-termination characters**, or null if the end of the stream has been reached

---

### Post by abraxas334 on 2012-04-25
No I am not using Buffered Reader. I cannot use the buffered reader now instead either, so I need to somehow do this manually.

---

### Post by abraxas334 on 2012-04-25
Problem solved: 
A quick if(textline.length==0) check actually does the trick!

---


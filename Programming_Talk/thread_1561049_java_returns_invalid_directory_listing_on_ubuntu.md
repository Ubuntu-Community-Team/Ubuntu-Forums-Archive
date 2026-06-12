---
title: "java returns invalid directory listing on ubuntu"
date: 2010-08-25
forum: Programming Talk
---

### Post by stu31 on 2010-08-25
I have a program that does a directory listing in java using:

[http://download.oracle.com/javase/1.5.0/docs/api/java/io/File.html#listFiles%28%29](http://download.oracle.com/javase/1.5.0/docs/api/java/io/File.html#listFiles%28%29)

(File.listFiles)

I then iterate over the list and do some processing.
Pretty vanilla stuff.

I also do a file.exists() test before I use the file.

However, on some files, this fails.
I check, and the file does in fact still exist (it hasn't been deleted), and permissions are fine.

The problem appears to have to do with java trying to "fix" the filenames with different or invalid character sets, for example, one file that fails is:

128-test$ ls -l
total 904
-rw-rw-rw- 1 stu stu 914432 2010-08-08 17:22 Ã?Â©Ã?Ã?Â³Â¡Â¿Ã¬Ã?Ã?Ã?Ã©Â¹Â¤Â¾Ã?4.5.exe
-rw-rw-rw- 1 stu stu    180 2010-05-19 16:17 QQÂ°Ã©Ã?Ã?,QQÂ°Ã©Ã?Ã?Â¹Ã?Â·Â½Ã?Ã¸Ã?Â¾,Ã?Ã?Ã?Ã?Ã?Ã¸,Â·Ã?Ã?Ã*Ã?Ã£ÂµÃ?Ã?Ã?Ã?Ã?Ã?Ã?Ã?Â·Â¸Â¨Ã?ÃºÃ?Ã*Â¼Ã¾Â£Â¡ - Powered by.url

However, other programs can open the file fine (GVIM):

128-test$ gvim QQÂ°Ã©Ã‚Ã‚\,QQÂ°Ã©Ã‚Ã‚Â¹Ã™Â·Â½ÃÃ¸Ã•Â¾\,Ã“Ã†Ã“Ã†ÃÃ¸\,Â·Ã–ÃÃ*Ã„Ã£ÂµÃ„Ã“Ã†ÃÃÃ“ÃŽÃÂ·Â¸Â¨Ã–ÃºÃˆÃ*Â¼Ã¾Â£Â¡\ -\ Powered\ by.url

And when I try to print the filename (when the exist call fails), it looks like java has tried to "fix up" the filename using unicode replacement characters:

????????????????????????-???????????????????????? - Powered by.url does not exist? (in processArchiveFile.extract())

So it appears to be a java-specific issue. Is there a way to tell java to just treat the filename as a byte array, and don't try to "fix" (break) things? Or is that not the issue?

Any guidance is appreciated.

Take care,
  -stu

---

### Post by interval1066 on 2010-08-25
> **stu31 said:**
> I have a program that does a directory listing in java using:

[http://download.oracle.com/javase/1.5.0/docs/api/java/io/File.html#listFiles%28%29](http://download.oracle.com/javase/1.5.0/docs/api/java/io/File.html#listFiles%28%29)

(File.listFiles)

I then iterate over the list and do some processing.
Pretty vanilla stuff.

I also do a file.exists() test before I use the file.

However, on some files, this fails.
I check, and the file does in fact still exist (it hasn't been deleted), and permissions are fine.

The problem appears to have to do with java trying to "fix" the filenames with different or invalid character sets, for example, one file that fails is:

128-test$ ls -l
total 904
-rw-rw-rw- 1 stu stu 914432 2010-08-08 17:22 Ã?Â©Ã?Ã?Â³Â¡Â¿Ã¬Ã?Ã?Ã?Ã©Â¹Â¤Â¾Ã?4.5.exe
-rw-rw-rw- 1 stu stu    180 2010-05-19 16:17 QQÂ°Ã©Ã?Ã?,QQÂ°Ã©Ã?Ã?Â¹Ã?Â·Â½Ã?Ã¸Ã?Â¾,Ã?Ã?Ã?Ã?Ã?Ã¸,Â·Ã?Ã?Ã*Ã?Ã£ÂµÃ?Ã?Ã?Ã?Ã?Ã?Ã?Ã?Â·Â¸Â¨Ã?ÃºÃ?Ã*Â¼Ã¾Â£Â¡ - Powered by.url

However, other programs can open the file fine (GVIM):

128-test$ gvim QQÂ°Ã©Ã‚Ã‚\,QQÂ°Ã©Ã‚Ã‚Â¹Ã™Â·Â½ÃÃ¸Ã•Â¾\,Ã“Ã†Ã“Ã†ÃÃ¸\,Â·Ã–ÃÃ*Ã„Ã£ÂµÃ„Ã“Ã†ÃÃÃ“ÃŽÃÂ·Â¸Â¨Ã–ÃºÃˆÃ*Â¼Ã¾Â£Â¡\ -\ Powered\ by.url

And when I try to print the filename (when the exist call fails), it looks like java has tried to "fix up" the filename using unicode replacement characters:

????????????????????????-???????????????????????? - Powered by.url does not exist? (in processArchiveFile.extract())

So it appears to be a java-specific issue. Is there a way to tell java to just treat the filename as a byte array, and don't try to "fix" (break) things? Or is that not the issue?

Any guidance is appreciated.

Take care,
  -stu

Just a guess, have you tried passing the file name through the URLencode/Decode class (I forget the full class path to that class, or even if its "URLencode/...", but I know there's such a class. Its been a while.

Those file "names" are completely insane and look like they contain escape sequences, the jvm may be trying to interpret those as having escaped characters and doing the wrong thing.

What are you doing polluting your file system with files with bad names like that?  Probing for 'sploits?

---

### Post by kahumba on 2010-08-25
In case it's a bug in Java and if you can afford moving to the current JDK7 snapshot I'd suggest checking whether [the new NIO2]("http://openjdk.java.net/projects/nio/javadoc/java/nio/file/DirectoryStream.html") approach fixes it.

```

Path dir = ... 
DirectoryStream<Path> stream = dir.newDirectoryStream();
try {
    for (Path entry : stream) {
        ..
    }
} finally {
    stream.close();
}

```

---

### Post by stu31 on 2010-08-25
> Those file "names" are completely insane

Indeed.

> What are you doing polluting your file system with files with bad names like that?  Probing for 'sploits?

I don't have control over the filenames. I just get a bunch of archives and whatever name the files have in the archive, they have :(

---

### Post by stu31 on 2010-08-25
> In case it's a bug in Java and if you can afford moving to the current JDK7 snapshot I'd suggest checking whether [the new NIO2]("http://openjdk.java.net/projects/nio/javadoc/java/nio/file/DirectoryStream.html") approach fixes it.

Thanks! Actually, I haven't even tried NIO (1) let alone NIO2. I'm using it in other places, just not for the directory listing. I don't know if I can do the JDK7 snapshot, but I'll try the current NIO.

---

### Post by kahumba on 2010-08-25
I've used JDK7 and it's been pretty stable so far.
[http://dlc.sun.com.edgesuite.net/jdk7/binaries/index.html](http://dlc.sun.com.edgesuite.net/jdk7/binaries/index.html)

---

### Post by stu31 on 2010-08-27
Actually, I might be able to upgrade the one machine to 1.7 and give it a try. 

Also, the bug was in a large, threaded program with lots of stuff going on, so I've been trying to duplicate it in the small to convince myself it was some other mistake. Which I've done. This program:

[HTML]
    public static void main( String[] args )
    {
        System.out.println( "Hello World" );
        if( args.length > 0 )
        {
            System.out.println( args[0] );
            File f = new File( args[0] );
            if( f.isDirectory() )
            {
                File[] filelist = f.listFiles();
                for( File t : filelist )
                {
                    System.out.println( t.getAbsolutePath() );
                    System.out.println( t.exists() );
                }
            }
            else
            {
                System.out.println( f.getAbsolutePath() );
                System.out.println( f.exists() );
            }
        }
    }
[/HTML]Prints out:

[HTML]
Hello World
/tmp/archive_transfer/***/tmp/archive_transfer/***/Ar/
/tmp/archive_transfer/***/tmp/archive_transfer/***/Ar/Prï¿½to
false
[/HTML]So, yah. I'll try java 1.7 & streams.

I have a feeling it might be "the way it's supposed to be" according to the java people though.

I think what might be happening is that it stores the file path as a String, and every String in java has to be encoded with a particular charset. It probably falls back to the default charset for a File() object (since I'm not supplying one). But since these files are being unarchived, and possibly originating from a computer with different charset (or even an illegal one), java decides to insert replacement characters or whatever the default UTF-8 error handling happens to be. 

And, I think, this might be related to this:

[https://bugs.launchpad.net/ubuntu/+source/zip/+bug/396605](https://bugs.launchpad.net/ubuntu/+source/zip/+bug/396605)

BUT! like I said, I can just tab-complete the filename in the shell, and it opens fine in  GVIM or whichever program, which means the file is there, and can be opened, if java could just stop trying to encode the filename as a proper String.

---

### Post by kahumba on 2010-08-27
I created a file with the crazy name from post #1 in my home dir and Java works fine, particularly it says that file exists:
QQÂ°Ã©Ã?Ã?,QQÂ°Ã©Ã?Ã?Â¹Ã?Â·Â½Ã?Ã¸Ã?Â¾,Ã?Ã?Ã?Ã?Ã?Ã¸ ,Â·Ã?Ã?Ã*Ã?Ã£ÂµÃ?Ã?Ã?Ã?Ã?Ã?Ã?Ã?Â·Â¸Â¨Ã?ÃºÃ?Ã*Â¼Ã¾Â £Â¡ - Powered by.url, exists: true

```

import java.io.*;

public class Main {

    public static void main(String[] args) {
        try {
            File dir = new File(System.getProperty("user.home"));
            File[] list = dir.listFiles();
            for(File file : list) {
                System.out.println(file.getName() + ", exists: " + file.exists());
            }
        } catch(Exception exc) {
            exc.printStackTrace();
        }

    }
}

```I guess if you're working with an archive you should post the archive itself for people to be able to replicate your issue.

---

### Post by stu31 on 2010-09-01
Unfortunately, it's not OK for me to make the archives public :(
I'll try writing out a file with just random bytes..

---

### Post by stu31 on 2010-09-01
Oh, and yeah, I think we I copied & pasted the names they got "cleaned up" by the process somehow - they didn't quite look the same.. probably got unicode escape characters added in, which made them OK for java.

---


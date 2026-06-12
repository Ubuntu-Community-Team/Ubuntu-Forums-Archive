---
title: "Using alsaplayer api in Java"
date: 2011-07-30
forum: Programming Talk
---

### Post by minerbog on 2011-07-30
Morning,

Now I completely stumped here and all googled out!! I have spent the best part of 3 days trying to work out what the problem is here but I can't :(

I'm trying to use the alsaplayer api in my java code as its plays nicer with alsa than java sound. I have installed the libalsaplayer.so and dev files from apt-get and the relevent files are where they should be.... I think!

My code is below followed by the error. I know the ap_version call is in the api as I have the source code and it is well documented that it is there, but nothing! Please help......

```


import java.io.*;



public class AlsaPlayer {

        static {
        String libalsaplayerFileName=null;
        try
        {
            // try loading native library from system lib (library path)
            System.loadLibrary("libalsaplayer");
            System.out.println("libalsaplayer library loaded using system library path");
           

        } catch(Throwable e) {
            try {
                File file = new File("lib/"+System.getProperty("os.arch")+"/"+System.getProperty("os.name")+"/libalsaplayer.so");
                libalsaplayerFileName = file.getAbsolutePath();
                System.load(libalsaplayerFileName);
                System.out.println("loaded libalsaplayer native library "+ libalsaplayerFileName );

            } catch (Throwable e2) {
                System.out.println("Could not load libalsaplayer native library");
                System.out.println("Tried system library path and " + libalsaplayerFileName);
                //e.printStackTrace();
                //e2.printStackTrace();
            }
        }
    }

        private static native int ap_version();

    /**
     * Constructor for creating a Alsaplayer object
     *
     */
    public AlsaPlayer(){
       
    }

    public static void main (String[] args){
        
        int ver = 0;

        ver = ap_version();
        System.out.println(ver);
    }

}

```

And the error created (in netbeans 6.9)

```

run:
loaded libalsaplayer native library /home/gavin/NetBeansProjects/ListerPlayer/lib/i386/Linux/libalsaplayer.so
Exception in thread "main" java.lang.UnsatisfiedLinkError: listerplayer.AlsaPlayer.ap_version()I
        at listerplayer.AlsaPlayer.ap_version(Native Method)
        at listerplayer.AlsaPlayer.main(AlsaPlayer.java:56)
Java Result: 1
BUILD SUCCESSFUL (total time: 1 second)

```

---

### Post by soltanis on 2011-07-30
As I understand it you cannot use native methods in Java unless you wrap them with a [Java Native Interface]("http://en.wikipedia.org/wiki/Java_Native_Interface") wrapper. Unless libalsaplayer has that already implemented, you'll need to implement it yourself (and make calls through that).

---

### Post by minerbog on 2011-08-05
> **soltanis said:**
> As I understand it you cannot use native methods in Java unless you wrap them with a [Java Native Interface]("http://en.wikipedia.org/wiki/Java_Native_Interface") wrapper. Unless libalsaplayer has that already implemented, you'll need to implement it yourself (and make calls through that).

Thanks soltanis, After much reading on JNI that is exactly what I needed.  I now have a class communicating via JNI to a C package and controlling the AlsaPlayer daemon! :)

However!!, yes there is always a however!

On its own it works fine. If I include it in to a package so I can create a object from it it produces an unsatisfied link error, but I cannot use it without adding it to a package?? What do I do??

Please help?

---

### Post by minerbog on 2011-08-17
> **minerbog said:**
> Thanks soltanis, After much reading on JNI that is exactly what I needed.  I now have a class communicating via JNI to a C package and controlling the AlsaPlayer daemon! :)

However!!, yes there is always a however!

On its own it works fine. If I include it in to a package so I can create a object from it it produces an unsatisfied link error, but I cannot use it without adding it to a package?? What do I do??

Please help?

Opps, you must generate the header file from the java class that already has the package information in it. You cannot just add a class to a package and expect it to work (like I thought!!).

---


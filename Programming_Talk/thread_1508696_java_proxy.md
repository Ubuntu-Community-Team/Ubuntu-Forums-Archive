---
title: "java proxy"
date: 2010-06-13
forum: Programming Talk
---

### Post by JakeFrederix on 2010-06-13
URL url = new URL("http://userserve-ak.last.fm/serve/126/8636005.jpg");
    Image img = ImageIO.read(url);
    System.out.println(img);

above piece of code is valid, and compiles. Yet when I execute it,
it keeps throwing  "java.net.ConnectException: Connection timed out".

The url exists, and when I open it in firefox, it clearly shows the image
I wish to download.

After having watched a similar post by me die on stackoverflow.com,
I was hoping perhaps this forum would be the one to solve it.

The most common answer seems to be "put a proxy between it" or "increase the timeout".
It still hangs after a timeout of 5 minutes, so that's not it.

I know how to set a proxy, but what settings should I use? (especially since firefox says it's not using a proxy)

Also, if I change my internet-connection to use my neighbour's network, this code suddenly behaves as expected.
Wget is also able to fetch the image.

Kind regards,
Jake

---

### Post by JakeFrederix on 2010-06-14
bump

---

### Post by xsandz on 2010-06-14
have you disabled your antivirus and firewall while running this code??sometimes these elements can make probs!

---

### Post by slavik on 2010-06-14
have you tried reading it as a file?

try putting an image one your disk and getting that, URLs don't have to be http:// ;)

---

### Post by JakeFrederix on 2010-06-14
I don't have a firewall set, or antivirus (unless these are built in). Use latest version of Ubuntu.

Reading an image of of my hard-drive is not a problem. Other code in the same project even uses a file containing a cache of the previous queries as to minimize the strain on LastFM.

Kind regards,
Jake

---

### Post by JakeFrederix on 2010-06-14
File f = new File("/home/jake/Pictures/mazetemplates/flowers/leaf.gif");
        URL url = new URL(f.toURI().toURL().toString());
        URLConnection con = url.openConnection();
        con.setConnectTimeout(50000);

        Scanner sc = new Scanner(url.openStream());
        while(sc.hasNext())
            System.out.println(sc.next());

above code for instance works fine. It reads a file on the local filesystem. I did use the File object, but only to construct a valid url to the file.

 File f = new File("/home/jake/Pictures/mazetemplates/flowers/leaf.gif");
        URL url = new URL(f.toURI().toURL().toString());
        URLConnection con = url.openConnection();
        con.setConnectTimeout(50000);

        ImageIO.read(url);

also works, and uses ImageIO and the url pointing to the local filesystem.

It must be an internet-related issue.

---

### Post by Some Penguin on 2010-06-14
Consider using the httpclient build from Apache Commons, if ImageIO isn't working for you.  Just because ImageIO is a built-in doesn't mean that it works...

---

### Post by JakeFrederix on 2010-06-14
1) I don't like importing external libraries when there is a class at hand that should do what I ask.
2) I'm awfully stubborn, it should work. And I don't intend on avoiding the problem, I intend on solving it.

---

### Post by slavik on 2010-06-14
it appears that the code has nothing to do with the class but with where the file is.

what's interesting is that you are trying to read a file, but have a separate connection open. have you looked at urlconnection's read methods if there are any?

---

### Post by JakeFrederix on 2010-06-15
URL url = new URL("http://userserve-ak.last.fm/serve/126/8636005.jpg");
        InputStream is = url.openStream();

        int res = is.read();
        while(res!=-1){
                System.out.println(res);
                res=is.read();
        }

fails too.

 URL url = new URL("http://userserve-ak.last.fm/serve/126/8636005.jpg");
        URLConnection con = url.openConnection();
        con.setConnectTimeout(50000);

        InputStream is = con.getInputStream();

        int res = is.read();
        while(res!=-1){
                System.out.println(res);
                res=is.read();
        }

will take a while, but will also fail.

---

### Post by Some Penguin on 2010-06-15
Interesting.   Are you running this in something like a Tomcat servlet container or something else that might have a particular not-very-permissive security policy?

---

### Post by JakeFrederix on 2010-06-15
I run this code in plain old NetBeans ide.
But even when I execute the code by opening the .jar, it will fail.

---

### Post by Some Penguin on 2010-06-15
Hmmmm.

1) You may also need to set the read timeout -- this is separate, and may be the actual issue if the server is slow.

2) Without checking the URLConnection source, I'm not sure that it will actually call connect() for you when you call getInputStream().  It might seem a reasonable thing to do, but that doesn't mean that it was done...

---

### Post by JakeFrederix on 2010-06-16
URL url = new URL("http://userserve-ak.last.fm/serve/126/8636005.jpg");
        URLConnection con = url.openConnection();
        con.connect();
        con.setReadTimeout(50000);
        con.setConnectTimeout(50000);

        InputStream is = con.getInputStream();

        int res = is.read();
        while(res!=-1){
                System.out.println(res);
                res=is.read();
        }

is another variation of the same code (this time set both connectTimeout and readTimeout). Also called connect() before reading data.

and again, it fails.

Also, I tried using the apache httpclient, that frustrated me. The example code uses 
HttpClient client = new HttpClient()

and when I copy-paste that (and yes, I included the .jars), it spat out
HttpClient is abstract and can not be instantiated.

ergh.

---

### Post by JakeFrederix on 2010-06-18
bump.

---

### Post by myrtle1908 on 2010-06-18
OpenJDK perhaps?  Seems like a very strange phenomenon for which OpenJDK could be to blame.

---

### Post by JakeFrederix on 2010-06-18
And what can I change then?

---

### Post by myrtle1908 on 2010-06-18
Can you check which JDK you are using?  I use Eclipse so not sure with Netbeans.

---

### Post by Zugzwang on 2010-06-18
@OP: Have you tried reading some image from somewhere else on the web? (e.g. the image on google.com or something like that?) Possibly the last.fm website filters out requests from some client types (which identify themselves to the webserver in a HTTP request)?

---

### Post by JakeFrederix on 2010-06-18
But, if it was merely lastfm filtering out httpclients, then I wouldn't be able to get the data using another internet-connection. As it is, when I use my neighbour's internet, it works. The exact same code (and all variations of the code I've already posted in this thread)

---

### Post by JakeFrederix on 2010-06-18
Also, come to think of it, if it was an openJDK problem, then it should manifest itself regardless of what internet-connection I use.

---

### Post by JakeFrederix on 2010-06-21
bump.

---

### Post by JakeFrederix on 2010-06-21
Also, and I have only just noticed this. The netbeans IDE is unable to show it's content (which it downloads from internet) at startup.
I'm assuming this means it's a problem with the internet connection.

---

### Post by JakeFrederix on 2010-06-21
On the forums of netbeans, it is said that this can be solved by changing the file[FONT=monospace]
[/FONT]/etc/sysctl.d/bindv6only.conf

Problem is, I don't have that file. It just isn't there.
Does anyone else have it? If so, could you cat /etc/sysctl.d/bindv6only.conf ?

Thanks in advance,
Jake

---

### Post by dwhitney67 on 2010-06-21
Did something like the following not work for you?

```

import java.net.URL;
import java.net.MalformedURLException;
import java.io.InputStream;
import java.io.IOException;


public class GetHttp
{
   public static void main(String[] args)
   {
      try {
         URL url = new URL(args[0]);
         InputStream is = url.openStream();

         byte[] data  = new byte[1024];
         int    bytes = 0;

         while ((bytes = is.read(data, 0, data.length)) != -1) {
            System.out.write(data, 0, bytes);
         }
      }
      catch (MalformedURLException e) {
          System.err.println(e.toString());
      }
      catch (IOException e) {
          System.err.println(e.toString());
      }
   }
}

```

Save the code above to GetHttp.java, and then:
```

javac GetHttp.java

java GetHttp http://userserve-ak.last.fm/serve/126/8636005.jpg > Maroon5.jpg

```
Your JPG image should be in Maroon5.jpg.

---

### Post by JakeFrederix on 2010-06-21
No, it does not work.
Yes, I have tried that (and all other possible variations of opening a URL).

The problem is that jre seems unable to make an internet connection. As shown by netbeans inability to load the content featured under "my netbeans" at startup.

I have already tried re-installing the JRE, the JDK and Netbeans itself.
Nothing works.

Sadly, this is one of the things that did work on Windows.
Say what you will, but when things fail in linux, it is hell to even begin to comprehend where the fault lies.

Kind regards,
Jake

---

### Post by dwhitney67 on 2010-06-22
Try analyzing the problem before you give up; for starters, I would not use NetBeans.  Run the application from the command line... but more importantly, run the application using the 'strace' utility.

For example:
```

javac GetHttp.java   # this is the app I supplied earlier

strace -o tmp.txt -f java GetHttp http://userserve-ak.last.fm/serve/126/8636005.jpg > pic.jpg

```
Examine the output generated by strace to see what direction the application took that made it fail.  To do this, open the tmp.txt file (that was generated above) and search for the following:
```

...

socket(PF_INET, SOCK_DGRAM, IPPROTO_IP) = 4
connect(4, {sa_family=AF_INET, sin_port=htons(0), sin_addr=inet_addr("96.17.171.41")}, 16) = 0

...

8482  send(4, "GET /serve/126/8636005.jpg HTTP/"..., 180, 0) = 180

...

8482  ioctl(4, FIONREAD, [16802])       = 0
8482  recv(4, "\331U\3351*m\345\216:\303\315\255\272\256\204\226\235Z\361\345\226\5\3513\272\337\336\322f\261{\26"..., 6744, 0) = 6744

...

```
The two main things to look for here in these statements is the socket descriptor (above it is 4), and also whether you were able to successfully connect; that is denoted by the "= 0" at the end of the connect() call.  Note that you may have a difference socket descriptor on your system.

If all goes well, then later you will see the recv() calls, using the same socket descriptor, and then the writing of the data to standard-out (this uses a descriptor of 1).

Anyhow, I would be curious to know what status you got from the connect() calls (yep, there might be more than one of them).


P.S.  You can use the same java app to download, say, the main page of [http://www.google.com](http://www.google.com).  You may want to try your luck with a different URL.  It could be that your ISP blocks access to this site: [http://userserve-ak.last.fm](http://userserve-ak.last.fm)

---

### Post by JakeFrederix on 2010-06-22
In attachment the result of trying to read [http://www.google.com](http://www.google.com) (which also failed).

Also, I had to split them because of the size-limitations.

Kind regards,
Jake

---

### Post by dwhitney67 on 2010-06-22
I see from the files that you posted that your system is using Open-JDK.  Perhaps you could consider removing it from your system and installing Sun's JDK?

You may want to read this: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Zugzwang on 2010-06-22
> **dwhitney67 said:**
> I see from the files that you posted that your system is using Open-JDK.  Perhaps you could consider removing it from your system and installing Sun's JDK?


Actually, in Ubuntu 10.04, the Sun JDK doesn't exist anymore (as a package).

@JakeFrederix: size limitations can be "circumvented" by gzipping the text file beforehand.

---

### Post by dwhitney67 on 2010-06-22
> **Zugzwang said:**
> Actually, in Ubuntu 10.04, the Sun JDK doesn't exist anymore (as a package).

Yes; this blog seems to confirm that:  [http://gabenell.blogspot.com/2010/04/installing-sun-java-6-on-ubuntu-104.html](http://gabenell.blogspot.com/2010/04/installing-sun-java-6-on-ubuntu-104.html)

Seems like there's a work-around though.

---

### Post by JakeFrederix on 2010-06-22
I've followed the instructions on the aforementioned website.
Removed openjdk (it does not show up anymore at the software-center)
installed jre and jdk

Again, the proposed GetHTTP failed.
In attachment the stacktrace.

@whomever  said I could gzip the files instead of splitting it;
I was tired as hell, both mentally, and physically. I design mostly in java, you cannot imagine how much of an inconvenience this problem is. Like dying of a million papercuts.

Kind regards,
Jake

---

### Post by dwhitney67 on 2010-06-22
Perhaps the most distinctive difference I found between your strace output and mine is the search paths that the Java VM (Virtual Machine) is examining.

In your file, it is most interested in searching the /usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/i386/**server** path, whereas on my system the focus is on /usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/i386/**client**.

Another difference, which must be important, is that your file indicates that your process ended prematurely (for whatever reason):
```

...

clone(child_stack=0xb69bb494, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0xb69bbbd8, {entry_number:6, base_addr:0xb69bbb70, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb69bbbd8) = 14735
futex(0xb69bbbd8, FUTEX_WAIT, 14735, NULL) = 0
exit_group(0) 

```

Mine on the other hand has:
```

...

clone(child_stack=0xb6c96494, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0xb6c96bd8, {entry_number:6, base_addr:0xb6c96b70, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb6c96bd8) = 13096
set_robust_list(0xb6c96be0, 0xc)  = 0
open("/sys/devices/system/cpu", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 3
getdents64(3, /* 10 entries */, 32768) = 304

...

```
So this might explain why your system is not yielding the desired results; your application is terminating prematurely.

As for what all this means, and how to resolve it, I haven't a clue.

Btw, out of curiosity, what are the contents of the following file on your system:  **/etc/java-6-sun/jvm.cfg**

Mine looks like:
```

...

-client IF_SERVER_CLASS -server
-server KNOWN
-hotspot ALIASED_TO -client
-classic WARN
-native ERROR
-green ERROR

```

---

### Post by JakeFrederix on 2010-06-22
My version of /etc/java-6-sun/jvm.cfg is exactly the same (or at least the part you've shown).

---

### Post by JakeFrederix on 2010-06-22
I've reinstalled Ubuntu. And again, (no surprises there) the same code fails under the same circumstances.
OpenJDK isn't installed, only Sun's versions of the jre and jdk.

I am very close to throwing the entire thing against the wall, and relocating to a deserted island where computers are unheard of.

Kind regards,
Jake

---

### Post by JakeFrederix on 2010-06-22
I try the CLI-approach, and "javac" is not installed.
Odd, seeing as Netbeans has no problems compiling and running code.

---

### Post by JakeFrederix on 2010-06-22
I fixed aforementioned post.
export PATH was needed.

If that got you rolling your eyes, keep in mind that until 10 months ago I hadn't even so much as seen a terminal.

---

### Post by JakeFrederix on 2010-06-22
Apparently, that also fixed the entire problem.
I have no idea why.

I am so happy right now :-)

---

### Post by JakeFrederix on 2010-06-22
Scratch that; it works some of the time.
Conditions that I am unaware of.
It might work twice in a row, it might not.
Perhaps it has to do with the exact alignment of Uranus and Jupiter.

---

### Post by JakeFrederix on 2010-06-22
The only thing I can think of is;

whilst I was trying out the code, the software-center was downloading programs (I had just reinstalled my entire system).

Now that I am not downloading through the software-center anymore, the code doesn't work anymore.

But even this is mere conjecture.

---

### Post by JakeFrederix on 2010-06-22
The problem lies with LastFM, I think.
Whenever I change connections, My IP changes, and so my request are granted.
Then I hit the limit, and the connection times out. 

I'll send an email to LastFM,
I'll mark this thread as solved if they confirm this suspicion.

---


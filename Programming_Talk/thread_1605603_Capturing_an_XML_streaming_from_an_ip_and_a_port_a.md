---
title: "Capturing an XML streaming from an ip and a port and store it in csv"
date: 2010-10-25
forum: Programming Talk
---

### Post by LtPitt on 2010-10-25
Hail, fellows programmers!

I am a sysadmin from the dark side (Windows) fallen in love with Linux.
I'm happy, curious and satisfied on my part of the IT but when it comes to programming I am a complete chump.
I have the need to read an Xml stream from a 3com nbx that comes from port 1024 of a certain ip...
I've found a little code a programmer did in .net:

[http://forums.asp.net/p/1148515/1871312.aspx](http://forums.asp.net/p/1148515/1871312.aspx)

Of course I can install vbstudio 2010 express and try it but...

Can I try anything in Ubuntu that doesn't need a lot of skills more than reading with accuracy a tutorial or manual?
Which kind of language would you suggest for this task?
And which tools to develop it?

Thanks a lot for your time and attention :)

---

### Post by Zymus on 2010-10-25
SO to clarify, you want to read the xml input from a certain port, and write that data to a file?

---

### Post by LtPitt on 2010-10-25
Yessir!

Excuse me if I express myself in a cloudy way :)

---

### Post by Zymus on 2010-10-25
here's a brief example of this in Java:

```

public static void main(String[] args) {
        try {
            ServerSocket server = new ServerSocket(1024);
            Socket s = server.accept();
            InputStream input = s.getInputStream();
            FileOutputStream output = new FileOutputStream("output.txt");//Change to where ever you want to output
            int read;
            byte[] buffer = new byte[1024];
            while((read = input.read(buffer)) != -1) {//While the EOS hasn't been reached
                output.write(buffer, 0, read);//Write the data to the stream
                output.flush();//Append the stream contents to the file
            }
            input.close();//release resources
            output.close();//release resources
        } catch(Exception e) {
            e.printStackTrace();
        }
    }
```

---

### Post by LtPitt on 2010-10-25
=:O

Way more than I'd ever dream!

And...

What kind of tools would you suggest me to use to develop and compile software?
Thanks a lot! :D

---

### Post by Zymus on 2010-10-25
Depends on the programming language. If you plan on using multiple languages, I'd suggest Eclipse. For Java-Only I'd suggest Netbeans, and for C/C++ i'd suggest Code::Blocks. Python: iPython, etc. You can also browse the various IDEs in the Ubuntu Software Center.

---

### Post by LtPitt on 2010-10-25
Ubuntu sounds like a winner all the time! :D

I'll try the Netbeans option you've suggested for this kind of work.

I am really thankful.

I'm gonna play with it right away...
Thanks once again :)

---

### Post by Zymus on 2010-10-25
One more think, You can also use XStream([http://xstream.codehaus.org/](http://xstream.codehaus.org/)) to serialize the objects inside the xml file. THe only stipulation is that you have to manually check when the end of the object has been reached. A simple way to do that is to basically create a string from the data that was read from the stream, check if it contains the end of object ("</object>" or whatever the end of the object actually is), and if it is, create the object. But that's at your discretion.

---

### Post by LtPitt on 2010-10-25
My ignorance is eating me right now, while I download netbeans :)

I'm reading XStream documentation to understand you better.
Thanks thanks thanks.

---

### Post by LtPitt on 2010-10-25
mmmh...

I'm reading and scratching my head...

I have no clues about the xml stream that's from my 10.0.0.1:1024 nbx...
It's a 3com voip hardware that streams from that port data about user logged, answered calls, lost calls and stuff like that but I have no clues about fields name and lenght...
Can I use XStream or anything like a sniffer to understand how is the xml file and then decide how to work on it?

---

### Post by Zymus on 2010-10-26
Well you could echo what's being read to the screen:

```

public static void main(String[] args) {
        try {
            ServerSocket server = new ServerSocket(1024);
            Socket s = server.accept();
            InputStream input = s.getInputStream();
            int read;
            byte[] buffer = new byte[1024];
            String line;
            while((read = input.read(buffer)) != -1) {//While the EOS hasn't been reached
                line = new String(buffer, 0, read);
                System.out.println(line);
            }
            input.close();//release resources
        } catch(Exception e) {
            e.printStackTrace();
        }
    }


```

---


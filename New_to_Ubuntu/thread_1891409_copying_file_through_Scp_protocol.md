---
title: "copying file through Scp protocol"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by dayanik.e on 2011-12-05
Hi guys ; 
I am a person who want to get a file through scp from computer lab. at my university. I stay at dormitory now and &#305; need a file it is said that i could get a file trough scp in terminal is there anyone to help me ? 

File's name  &#305; want to get is "alides.txt" my computer name is erenay@erenayinki and file is in a computer named e1819192@divan

---

### Post by Lars Noodén on 2011-12-05
The computer name looks odd, it should have dots in it rather than an at (@) sign.  

But the syntax for [scp](http://manpages.ubuntu.com/manpages/precise/en/man1/scp.1.html) is [font=Courier New]scp source destination[/font]

So if you can figure out the right hostname for the remote computer, [font=Courier New]scp [/font] will look something like this:

```

scp [email]erenay@divan:alides.txt[/email] .

```

But that won't work until you figure out the proper host name for the remote computer.

---

### Post by marinara on 2011-12-05
if he has sftp you can use filezilla

also this:
[http://www.google.com/url?sa=t&rct=j&q=graphical%20scp%20client%20ubuntu&source=web&cd=2&ved=0CCwQFjAB&url=http%3A%2F%2Fsuperuser.com%2Fquestions%2F40999%2Fwinscp-client-for-ubuntu&ei=ODzdTveNBoTw0gHw6JnmDQ&usg=AFQjCNEGe8DGSUERrZnxhoXknm9OCaxw6g&sig2=pclzffU6m-UL9A3QK4jf0w&cad=rja]("http://www.google.com/url?sa=t&rct=j&q=graphical%20scp%20client%20ubuntu&source=web&cd=2&ved=0CCwQFjAB&url=http%3A%2F%2Fsuperuser.com%2Fquestions%2F40999%2Fwinscp-client-for-ubuntu&ei=ODzdTveNBoTw0gHw6JnmDQ&usg=AFQjCNEGe8DGSUERrZnxhoXknm9OCaxw6g&sig2=pclzffU6m-UL9A3QK4jf0w&cad=rja")

also erenay is the username

erenayinki is the computer name

---

### Post by Lars Noodén on 2011-12-06
+1 for FileZilla

Also Nautilus works with SFTP.  In Nautilus:

File->Connect to Server->Type->SSH

---


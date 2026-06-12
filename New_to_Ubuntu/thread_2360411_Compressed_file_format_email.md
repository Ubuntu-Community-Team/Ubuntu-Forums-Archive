---
title: "Compressed file format email"
date: 2017-05-04
forum: New to Ubuntu
---

### Post by johnny7oak on 2017-05-04
Hi...

I am probably the only guy that bought win zip like multiple times, but I liked the win zip courier which allowed me to send compressed file formats over the email.  Is there a Linux version of that kind of Win zip courier?  Er what is the Compressed file format in email anyways?

---

### Post by TheFu on 2017-05-04
So you were the guy? ;)  I paid for Netscape Navigator in the mid-90s.

SMTP supports either 7-bit ASCII or MIME-attachments (which are uuencoded into 7-bit ascii).  Those are the choices.  HTML email is a mime-attachment.  Word-Documents are mime-attachments.  Similarly, compressed files would be some sort of mime-attachment.

Of course, nobody else will be able to trivially see the compressed data, though uudecoding is automatic these days.

There is a built-in **archive manager** for most Linux desktops. It is usually available from the GUI file manager.  
[https://apps.ubuntu.com/cat/applications/file-roller/](https://apps.ubuntu.com/cat/applications/file-roller/)
[https://help.ubuntu.com/community/File%20Roller](https://help.ubuntu.com/community/File%20Roller)
[https://ubuntuforums.org/showthread.php?t=1958526](https://ubuntuforums.org/showthread.php?t=1958526)

---

### Post by DuckHook on 2017-05-04
> **johnny7oak said:**
> …what is the Compressed file format in email anyways?
There is no default compression format in email. The email protocol is a highly standardized and rather primitive one (in a good way) that is designed to be simple, easily parsed and therefore accessible to the most uncomplicated email reader. This means that it just transmits everything in plain ASCII text. Any compression technology must be done independently of the email protocol itself and is simply a process—whether an independent app or an add-on to your email client—which transcodes the original content into an ASCII attachment by way of a compression algorithm. The email protocol doesn't know and doesn't care about content: whether it is clear text or that it's been transcoded. It just transmits what it is given.
> Is there a Linux version of that kind of Win zip courier?
Since I don't use Windows, I have no idea what Win zip courier is or how it works. I would suggest that you look for such an add-on in your email client. If you can't find one, it is simple enough to zip the file using standard standalone Linux apps before sending.

It bears noting that emailing compressed files is often overdone, superfluous and a security concern. Most attachments these days are already compressed formats that will gain nothing from being compressed a second time. Most audio and video formats are already compressed. So are common photo files like JPEG and GIF. PDFs can be compressed within the PDF itself and the downloadable sort usually are. Almost all PDF readers will decompress such files transparently without even asking for your input. The only files that might justify independent compression are data files like large spreadsheets and word processing documents that are larger than 1 MB.

The biggest concern with zipped files is security. This is a common attack vector used by scumbags who either hide or spoof malware as zip attachments. It's gotten so bad that I don't open zipped files anymore. If I get one that I think is legitimate, I will only open it within a properly sandboxed VM. This means that your sending a zipped file to a security-conscious friend may be either inconvenient or potentially troublesome.

This combination of lack of need and security exposure makes the old habit of sending zipped files rather problematic these days, but you are the one best placed to decide on your own usage.

---

### Post by KenUBF on 2017-05-05
I personally like compressing files via the command line. You can also give the percentage of compression you desire so you can be sure your email client will be able to successfully attach the file. If you feel comfortable using the command line try this. cd to the directory where your file/files are that you want to compress. For example, if your file is on the desktop type in the command line: cd Desktop. Then type:

```
 zip -r -[the percentage of compression here] [name of file you want compressed] [name of the compressed file] 
```

Type that without the brackets and you should have a nice zip file on your desktop, or wherever you'd like to put it. I hope this works for you too.

---


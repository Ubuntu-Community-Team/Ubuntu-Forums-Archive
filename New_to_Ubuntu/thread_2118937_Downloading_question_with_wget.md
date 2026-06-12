---
title: "Downloading question with wget"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by bentoman1974 on 2013-02-22
This is my first post so please forgive me if this is in the wrong section; mods please move if incorrect.  I am using wget in the terminal to download flash videos off of a site.  I use firebug to get the url of the video file then paste it into the terminal command to start the download.  My first question is whether or not firebug is an unnecessary step and if there is a faster/quicker way for me to obtain the url.  Also, each download takes quite a bit of time and currently I have to wait for one download to finish, then get the url of the second file, type a new command to start another download and so on.  If I have the url's of all the files I need, is there any sort of batch command that I can use so that I don't have to download each file individually?  Thank you in advance for any help that can be offered.

Oh and I'm using Ubuntu 12.10.

---

### Post by schragge on 2013-02-22
> **bentoman1974 said:**
>  My first question is whether or not firebug is an unnecessary step and if there is a faster/quicker way for me to obtain the url.It depends. Sometimes, a simple look at the source (**Ctrl**+**U**) is enough, sometimes not. There is also
[http://www.downloadhelper.net/](http://www.downloadhelper.net/)

> **bentoman1974 said:**
> If I have the url's of all the files I need, is there any sort of batch command that I can use so that I don't have to download each file individually?
```
wget -i [color=blue]file_with_URLs[/color]
```

---

### Post by bentoman1974 on 2013-02-22
Thank you.  I will try that tonight and report back with any issues, if any.

---

### Post by bentoman1974 on 2013-03-15
I'm sure this was a fairly noob question, but I found a convenient method at:

[http://www.thegeekstuff.com/2009/09/the-ultimate-wget-download-guide-with-15-awesome-examples/](http://www.thegeekstuff.com/2009/09/the-ultimate-wget-download-guide-with-15-awesome-examples/)

[COLOR=#111111][FONT=Helvetica Neue]First, store all the download files or URLs in a text file as:[/FONT][/COLOR]

$ cat > download-file-list.txtURL1URL2URL3URL4[COLOR=#111111][FONT=Helvetica Neue]Next, give the download-file-list.txt as argument to wget using -i option as shown below.[/FONT][/COLOR]

$ wget -i download-file-list.txt

---


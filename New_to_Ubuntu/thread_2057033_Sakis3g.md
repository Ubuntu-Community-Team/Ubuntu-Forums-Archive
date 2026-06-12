---
title: "Sakis3g"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-09-12
This is driving me nuts, especially as I have installed and reinstalled Sakis before. I can get to tar.gz and extract the files but as soon as I run in the terminal I have problems. 

My guess is there is an error in what I copied and pasted. I did that from my previous thread about a dongle. Basically there are mistakes in the bit to copy into the terminal.


Can anyone put here the exact and correct stuff to put into the terminal to get Sakis3g on an Acer Aspire 6930g....

I can't do anything much else till that is sorted.....I know what to do but something is wrong in the script (if that is what you call it.)

Thanks, J

---

### Post by Jackalyn on 2012-09-12
wget "[http://www.sakis3g.org/versions/latest/i386/sakis3g.gz](http://www.sakis3g.org/versions/latest/i386/sakis3g.gz)"
echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c
gunzip sakis3g.gz
chmod +x sakis3g
./sakis3g --interactive

This is what I am using and it works till you get the gzip file extracted and then run in terminal.......then it gives you the options but if you click on any the terminal disapears and there is nothing at all. Gedit file says some of it is wrong and also, when you click y to overwrite the file in the terminal it just says 'not overwritten' in the next line,

---

### Post by Jackalyn on 2012-09-12
jacky@jacky-Aspire-6930G:~$ wget "http://www.sakis3g.org/versions/latest/i386/sakis3g.gz"
--2012-09-13 00:49:18--  [http://www.sakis3g.org/versions/latest/i386/sakis3g.gz](http://www.sakis3g.org/versions/latest/i386/sakis3g.gz)
Resolving [www.sakis3g.org](www.sakis3g.org) ([www.sakis3g.org](www.sakis3g.org))... failed: Name or service not known.
wget: unable to resolve host address `[www.sakis3g.org](www.sakis3g.org)'
jacky@jacky-Aspire-6930G:~$ echo "dda70fd95fb952dbb979af88790d3f6e sakis3g.gz" | md5sum -c
md5sum: standard input: no properly formatted MD5 checksum lines found
jacky@jacky-Aspire-6930G:~$ gunzip sakis3g.gz
gzip: sakis3g already exists; do you wish to overwrite (y or n)? y
    not overwritten
jacky@jacky-Aspire-6930G:~$

---

### Post by NikTh on 2012-09-12
Hi , 
you must have an active Internet connection to use the command ```
**wget** "http://www.sakis3g.org/versions/latest/i386/sakis3g.gz"
```either connect via Ethernet cable (if you have) or 
download the file via another PC with Internet connection and then transfer the file (through USB stick) to you current /home partition and then proceed with other commands.

**Tip:** You must have in mind that the version you attempted download is for 32bit system architecture 
```
http://www.sakis3g.org/versions/latest/**i386**/sakis3g.gz
```Thanks

---

### Post by Jackalyn on 2012-09-13
Thanks, the Penguin finally back on my desktop, but although it tries to connect, I just get 'connection failed.' I just don't know what setting I have wrong. Using a fairly old 3 dongle and before the system crash it worked fine with Sakis.

---


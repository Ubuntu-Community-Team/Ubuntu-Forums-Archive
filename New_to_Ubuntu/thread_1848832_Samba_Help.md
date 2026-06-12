---
title: "Samba Help"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by P05TMAN on 2011-09-23
Is there a way to pipe the out put of a command as a file using samba?

Here's the scenario to hopefully illustrate my question: 

I've samba'd to a node: 

```

smbclient //10.0.0.51/GUM 'passwd' -U uname {Enter}

```Then I'm in to the shared directory. I want to see what's in the shared directory

```
 
dir

```That lists the content of said directory. 

Is there a command that would be similar to redirecting out put in Linux?
As in I wanted to list the contents of a directory named 'Test' & pipe it to a file named 'sample1'. In Linux, all I'd have to do is
```

ls Test | sample1

```Is there a command that will pipe the output of 'dir' while connected via samba to a file names sample1 on my Linux machine? Or even pipe the output to a file I created & put on the samba share & later retrieve, like with 'get' ?

Sorry in advance if I confused my question more, let me know if I can clarify & thank you!

---

### Post by HermanAB on 2011-09-23
Hmm, can't think of a way to to that, but I would just highlight and middle click paste what I want into a text editor.

Otherwise, mount the directory and then just use ls.

---

### Post by P05TMAN on 2011-09-23
> **HermanAB said:**
> Hmm, can't think of a way to to that, but I would just highlight and middle click paste what I want into a text editor.

Otherwise, mount the directory and then just use ls.
That's a good idea! I'm still going to leave this open in case anyone does have the command line solution I was originally seeking though.

---

### Post by Morbius1 on 2011-09-23
I think it follows the ftp convention:
```
ls [remote-directory] [local-file]
```So:
```
 ls /Test /home/morbius/Desktop/sample1
```

---

### Post by Morbius1 on 2011-09-23
Um ...:redface: ...  that doesn't work does it.

While I look back into my notes try this:

gvfs-mount smb://10.0.0.51/GUM 
gvfs-ls smb://10.0.0.51/GUM/Test > /home/morbius/Desktop/sample1

---

### Post by P05TMAN on 2011-09-23
> **Morbius1 said:**
> Um ...:redface: ...  that doesn't work does it.

While I look back into my notes try this:

gvfs-mount smb://10.0.0.51/GUM 
gvfs-ls smb://10.0.0.51/GUM/Test > /home/morbius/Desktop/sample1
Not at my pc now, but I will try this & post my results! Thanks!

---

### Post by P05TMAN on 2011-09-24
I couldn't get your last suggestion to work either. :( 

It was a valiant effort though. +1

---

### Post by Morbius1 on 2011-09-24
Hmmm.....

gvfs-mount smb://192.168.0.100/j
gvfs-ls smb://192.168.0.100/j/JreePad
> cardfile.hjt
TreePad.png
Jreepad-1.5.jar
TreePad.ico
Linux_Install.txtgvfs-ls smb://192.168.0.100/j/JreePad > /home/morbius/Desktop/ls.txt
cat /home/morbius/Desktop/ls.txt
> cardfile.hjt
TreePad.png
Jreepad-1.5.jar
TreePad.ico
Linux_Install.txtI hate it when people say this to me on the forums but .... It works for me.

---


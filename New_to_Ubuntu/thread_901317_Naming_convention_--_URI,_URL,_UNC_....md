---
title: "Naming convention -- URI, URL, UNC ..."
date: 2008-08-26
forum: New to Ubuntu
---

### Post by cwmoser on 2008-08-26
Please clarify this for me ...

URL is like [http://www.google.com](http://www.google.com), [ftp://lucent.com](ftp://lucent.com), etc.

UNC is like \\server1\Windows\System32\drivers\etc\hosts

Questions:

Does Ubuntu Linux support copying from machine to machine?
Can you provide an example?

Does Ubuntu Linux support copying from/to Windows machine?
Can you provide an example?

What is URI versus URL?

Thanks

Carl

---

### Post by cwmoser on 2008-08-26
Does this work with Linux?

Say 2 computers:  Server1 and Server2

On Server1, you want to do directory of /home on Server2.

Will this work?

Server1 $>  ls  -l  Server2:/home


Would it work like this to a Windows PC:

Server1 $>  ls  -l  Server2:/Program Files


Carl
(I'm confused)

---

### Post by croniksoft on 2008-08-26
In order to have access to windows share you must first set up SMB,

Here is a post that can help you out on that [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

I am not sure you can ls in the share unless you mount it!!
But the link that I have gave you above will show you how to mount it

---

### Post by cwmoser on 2008-08-28
That was a very good reference on Samba.

Thanks,

Carl

---

### Post by aeiah on 2008-08-28
depending on what you want to do, simply using scp from the command line might be sufficient. you could write a script for it. this would be useful if all you're doing is occasionally wanting to copy over an entire folder or a few specific files. scp works much like a normal copy command but goes through a secure ssh tunnel, so you could use it over the internet, or just over a network / vpn. you wouldnt need to mount network shares and such with this, just have an ssh server running on the target server.

---

### Post by cwmoser on 2008-08-28
Did a little research on this -- a URL is a subset of the URI schema.

Interesting.

Carl

---

### Post by cwmoser on 2008-08-28
On Windows, you can use the Explorer to drill down to find a computer and then click on the shared resource.

On Windows, we often use the command line form \\servername\C$ like this:
Start  ->  Run and in the Open window enter \\servername\C$ to get access to the files on another networked computer.

Is there a short cut like this with Linux?  The only way I know to do something like this is to mount a share.

Carl

---


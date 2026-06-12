---
title: "[SOLVED] Won't extract pass protected rar file..."
date: 2008-11-27
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-11-27
I'm trying to extract a pass protected split archive in Ubuntu 8.10 but I get an error:

```

7-Zip  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=en_GB.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: /home/carl/Desktop/stuff.part1.rar

Extracting  stuff/somemorestuff.url
Enter password (will not be echoed) :

```

whats wrong:confused:

Thanks in advance!

---

### Post by binbash on 2008-11-27
THere is not any error there.You will enter the password of the rar file. or you can try 

unrar e /home/carl/Desktop/stuff.part1.rar
enterpasswordwhen asked

---

### Post by handydan918 on 2008-11-27
> **kamitsukai said:**
> I'm trying to extract a pass protected split archive in Ubuntu 8.10 but I get an error:

```

7-Zip  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=en_GB.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: /home/carl/Desktop/stuff.part1.rar

Extracting  stuff/somemorestuff.url
Enter password (will not be echoed) :

```

whats wrong:confused:

Thanks in advance!

What error? It's just prompting for the password, and telling you that it will not be displayed on the screen as you type it.

---

### Post by kamitsukai on 2008-11-27
I right click on the file and select "extract here" it starts to extract and then I get the above in an error box...

---

### Post by bcd87 on 2008-11-27
Try extracting in the console as reply #2 said.

---

### Post by gandaran on 2008-11-27
if you install **rar** in synaptic then you just double click or right click (extract here) the rar file and the file manager window will pop up asking for the password, it's easier than using the command line

---

### Post by kamitsukai on 2008-11-27
> **gandaran said:**
> if you install **rar** in synaptic then you just double click or right click (extract here) the rar file and the file manager window will pop up asking for the password, it's easier than using the command line

thats what I've done, and it extracted fine from the console i just want to know why it wouldn't extract from the gui or actually why it didn't ask for a password?

---

### Post by gandaran on 2008-11-27
> **kamitsukai said:**
> thats what I've done, and it extracted fine from the console i just want to know why it wouldn't extract from the gui or actually why it didn't ask for a password?
which rar package did you install? I believe you can find three of them in synaptic

---

### Post by bcd87 on 2008-11-27
It seems 7zip doesn't handle multi-volume archives very well according to [this](https://help.ubuntu.com/community/File%20Roller) page. That could be the problem I guess?

---

### Post by kamitsukai on 2008-11-27
dunno it's not a problem now anyway :)

---


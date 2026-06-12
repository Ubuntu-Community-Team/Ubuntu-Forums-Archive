---
title: "Installing from .tar.bz2"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-06-13
I have downloaded a .tar.bz2 file from  the internet. I want to install the software which is in that file. 

How should i do it.

---

### Post by _sphinx_ on 2008-06-13
First of all extract the contents of the zip. Just right click and do extract here. Post here the contents of the extracted directory. Usually the procedure is
```

./configure
make
make install

```

---

### Post by bikeboy on 2008-06-13
Make your way though the following guide, but feel free to ask questions if you get stuck.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by hyper_ch on 2008-06-13
isn't the program in the repos? what is it?

---

### Post by 7raTEYdCql on 2008-06-13
According to the help.ubuntu.com site that was just told i can't change the ownership to my name.
I can't past my .tar.bz2 into this folder, even whel the long listing in terminal tells me that i can rwx the /usr/local/src folder.

---

### Post by 7raTEYdCql on 2008-06-13
I tried the sudo apt-file update.
It prompted for Gutsy cd:/ insertion.
After inserting the cd rom it says that /media/cdrom0 is busy.
what should i do??

---

### Post by 7raTEYdCql on 2008-06-13
I bunked the apt-file update command and went on with the installing.

I then copied the .tar.bz2 into a newly created directory ~/mount.
After that i extracted the contents of the directory.
How do i get the configure file in the directory.
???

I am seriously confused.

---

### Post by 7raTEYdCql on 2008-06-13
Can someone please help me.

---

### Post by balachandarlinks on 2008-06-13
Extract it and read the read me file....U ll get knock dude........

---

### Post by _sphinx_ on 2008-06-13
Is there some readme type of file in the directory you have extracted? If there is than go for it. Any ways can you find file called configure in the directory?

---

### Post by 7raTEYdCql on 2008-06-13
After extracting the tar.bz2 i got a .app folder.

In that folder there itself there are many folders. You dont expect me to go through all of them to find the readme text file.

---

### Post by _sphinx_ on 2008-06-13
Actually just a wild look to all the floder will not take much time. Is there any folder called bin or src in the .app folder. I would be good if you post the output of ```
ls
``` in .app folder here.

---

### Post by balachandarlinks on 2008-06-13
never

---

### Post by 3rdalbum on 2008-06-13
What program is it? We **need** to know this! Have you looked in the Synaptic Package Manager to see if the program (or something similar) is available from there?

---

### Post by 7raTEYdCql on 2008-06-14
This is Filezilla and i downloaded the .tar.bz2 from the sourcefourge website.It isnt there on my synaptic.

---

### Post by ramjet_1953 on 2008-06-14
[COLOR="Blue"]filezilla[/COLOR] IS in the repositories and you should be able to install it via Synaptic.
 If it isn't appearing, you probably haven't enabled the extra repositories.

To do this, open Synaptic, click on [COLOR="Blue"]Settings>Repositorie[/COLOR]s and put a tick in everything, except Source Code.

You really could have saved yourself some grief right from the start by being more specific with your question.

If you had said that you wanted to install filezilla right from the start it probably would have been solved for you immediately.

Regards,
Roger :cool:

---


---
title: "How to install Internet Explorer"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by Lakeside5 on 2008-11-25
Hi. I`m wondering if someone can help me figure out how to install Internet Explorer as my alternate web browser ( I prefer Firefox, but I`m developing a website using the Hardy Heron server and Joomla, and want to see how it appears in IE as well). I downloaded the IE application but I don`t have permission or something to open it.  I do have wine on here too.  thanks for any help.

---

### Post by Elfy on 2008-11-25
You can install IEs4Linux

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by Olivier2371 on 2008-11-25
Personally I much prefer to use wine.

---

### Post by Lakeside5 on 2008-11-25
Thanks ForestPixie, that`s funny as I stumbled across thing in my googling, and installed IE with the terminal, but am stumped at this part: 7. Then go into the directory, and run the installation script.
cd ies4linux-*
./ies4linux
(done, and I see this at command prompt: ~/ies4linux-2.99.0.1$ ./ies4linux


8. Now you can run the Internet Explore anytime with this command:
/root/bin/ie6
I typed that in at the end of the above line, but am told `no such file or directory`.  so I tried it at the root (-desktop:~$) and am told the same thing. I am a noob is is unsure what to do lol.  thanks. Hi Oliver..I tried to use wine, I clicked on the downloaded ie file but it wouldn`t let me open it. thanks.

---

### Post by UbuntuNerd on 2008-11-25
[http://wiki.jswindle.com/index.php/Internet_Explorer#Installation_Scripts]("http://wiki.jswindle.com/index.php/Internet_Explorer#Installation_Scripts")

[http://www.winehq.org/site/howto]("http://www.winehq.org/site/howto")

---

### Post by aysiu on 2008-11-25
Here are screenshot-laden instructions on how to install IEs4Linux on Ubuntu:
[http://psychocats.net/ubuntu/ies4linux](http://psychocats.net/ubuntu/ies4linux)

---

### Post by madsc89 on 2008-11-25
> **Lakeside5 said:**
> Thanks ForestPixie, that`s funny as I stumbled across thing in my googling, and installed IE with the terminal, but am stumped at this part: 7. Then go into the directory, and run the installation script.
cd ies4linux-*
./ies4linux
(done, and I see this at command prompt: ~/ies4linux-2.99.0.1$ ./ies4linux


8. Now you can run the Internet Explore anytime with this command:
/root/bin/ie6
I typed that in at the end of the above line, but am told `no such file or directory`.  so I tried it at the root (-desktop:~$) and am told the same thing. I am a noob is is unsure what to do lol.  thanks. Hi Oliver..I tried to use wine, I clicked on the downloaded ie file but it wouldn`t let me open it. thanks.

I'm not that familiar with ubuntu myself, yet, but try: ```
wine /root/bin/ie6
```

---

### Post by dr.silly on 2008-11-25
> **Olivier2371 said:**
> Personally I much prefer to use wine.

IEs4Linux does use wine.

---

### Post by Lakeside5 on 2008-11-25
To madsc90: Just wondering where exactly to type in this command, I typed it in at -desktop:~$ and got `wine: cannot find '/root/bin/ie6'` Sorry to be so dense, thanks for your patience:)

---

### Post by Olivier2371 on 2008-11-25
dr.silly,

Sorry I didn't know.

I never eared IEs4Linux before.
I run my windows programs using only wine.

---

### Post by pluckypigeon on 2008-11-25
in a terminal type ```
locate ie6 | more
```

copy and paste the address of the file from the output of the code in a terminal

e.g:
my output has this line

/home/pluckypigeon/bin/ie6 

I'd paste that in to a terminal and it will start

yours may be something similar depending on where you installed it

---

### Post by Lakeside5 on 2008-11-25
Thanks everyone for the suggestions :)  I went  the `screenshot-laden instructions` route, for a noob like me (thanks aysiu). I now have IE7, and can see that my website doesn`t look too different, only the black text is not as black for some reason, more of a grey.

---

### Post by Orographic on 2008-11-26
Let us know how you go with it, ie: if its pretty stable etc. I run a few websites and also need IE to test in, not that I ever use it as a browser myself. At the moment I just plug in my other internal sata drive with XP on it or start up an old computer with IE7 on it.

I already have Wine installed so may just follow the instructions you mentioned, they looked well described to me.

Thanks for this thread.

---

### Post by Orographic on 2008-11-26
Well, I followed the screenshot laden instructions (I'm using Intrepid) and when I double clicked on the downloaded ies4linux file and chose 'run in terminal' nothing much happened after initially saying something like 'downloading all we need'. I was also told as I selected the 'run in terminal'  option that my version of Wine was perhaps too old and to update but I have '1.0.1-0ubuntu2' which is apparently the latest version for Intrepid from Synaptic.

I fiddled about for a while (reinstalling Wine and Cabextract) and then double clicked the ies4linux file again but chose 'display' instead and it installed fine.

Just to be safe, I then restored an image of my OS made last night and re-installed using the way I just explained, using 'display' instead of 'run in terminal'. The script downloaded something for about five minutes but there was no icon on the desktop so I just clicked on the file again and selected 'display' and it installed fine.

It was a bit fiddly but IE loads perfectly at present but I am not sure I want to keep it on my system as it did seem a bit buggy to install with the latest version of Wine - or the latest in Synaptic anyway.

---

### Post by dr.silly on 2008-11-26
> **Olivier2371 said:**
> dr.silly,

Sorry I didn't know.

I never eared IEs4Linux before.
I run my windows programs using only wine.

Yep it all works the same

I'm not sure how often ies4linux is updated so just installing it in wine manually may be easier

---

### Post by ComputerHermit on 2008-11-26
I call internet explorer Internet Exploder :) I had lots of bad with internet exploder 8 it really stinks

---

### Post by Orographic on 2008-11-26
One other thought I am having is, how would I know if a bug in a web page was because of IE6 or a bug/problem with Wine that is running it?

I certainly don't use IE for browsing or anything at all, just a bit of testing only, as about 70% of my site traffic uses it.

---


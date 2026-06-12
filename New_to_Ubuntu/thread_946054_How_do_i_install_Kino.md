---
title: "How do i install Kino?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by sin1984 on 2008-10-12
i'm confused on how to instal kino-1.3.2. all of the other programs i've gotten are pretty straight forward, due to instructions from other linux users on this forum. however since i am still new, and i am trying to install kino, i am confused. Here is why:

its talking about shell commands'./configure; make; make install' but i dont understand where to enter any of these commands, in what order, etc. etc. so if anyone has a solution to my problem, or has installed kino. please let me know :)

---

### Post by epidemiks on 2008-10-13
```
sudo apt-get install kino
```

i'm not sure if its in the standard repositories, but if it is, that command should download and install it for you.

---

### Post by crazyness003 on 2008-10-13
As of right now, Kino 1.3.0 is available from the repositories (synaptic). All you gotta do is open Synaptic, look for it and mark it for installation, or just open a terminal and type this
```
sudo apt-get install kino
``` It will prompt you for a password (and remember, it needs root priveleges so be careful how you use sudo). And bam, you have kino 1.3.0

As for the ./configure and all that stuff, its giving you instructions on compiling from source. You basically downloaded the source-code (compressed in a "tarball" or .tar file and now you must compile it to run it. Its not as hard as it sounds. If you want the newer version, like 1.3.2 or whatever you need to compile and install it

I HIGHLY RECOMEND YOU USE THE REPO VERSION SINCE ITS EASIER TO INSTALL
But if you must install the newer version, here you go:

all you gotta do is extract your .tar to your home folder for example. Then use the terminal to navigate to that folder. Just follow these steps

1. So you downloaded kino-1.3.2.tar.gz to your home folder (eg */home/your_user_name*).
2. Open a terminal and type "[FONT=Courier New]ls[/FONT]". You should see an entry there that says "[FONT=Courier New]kino-1.3.2.tar.gz[/FONT]"
3. Now run this: [FONT=Courier New]tar zxvf kino-1.3.2.tar.gz[/FONT]
4. then type: [FONT=Courier New]cd kino-1.3.2[/FONT]
5. Here You may wanna read any file that says "readme". type: [FONT=Courier New]gedit README[/FONT]
6. It wil tell you all the dependencies and stuff. make sure you have all of them. Install them by running each one with a "[FONT=Courier New]sudo apt-get install xxxx[/FONT]". Then look at where it says "Install Kino". The rest of the instructions are there.
7. in terminal type[FONT=Courier New]: ./configure[/FONT]
8. then: [FONT=Courier New]make[/FONT]
9. then: [FONT=Courier New]sudo make install[/FONT]
Done
to run, just type [FONT=Courier New]kino[/FONT] in the terminal or use the menu (applications -> Sound and Video -> Kino)

---

### Post by ad_267 on 2008-10-13
[Installing software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by jpangamarca on 2008-10-13
> **crazyness003 said:**
> As of right now, Kino 1.3.0 is available from the repositories (synaptic). All you gotta do is open Synaptic, look for it and mark it for installation, or just open a terminal and type this
```
sudo apt-get install kino
``` It will prompt you for a password (and remember, it needs root priveleges so be careful how you use sudo). And bam, you have kino 1.3.0

As for the ./configure and all that stuff, its giving you instructions on compiling from source. You basically downloaded the source-code (compressed in a "tarball" or .tar file and now you must compile it to run it. Its not as hard as it sounds. If you want the newer version, like 1.3.2 or whatever you need to compile and install it

I HIGHLY RECOMEND YOU USE THE REPO VERSION SINCE ITS EASIER TO INSTALL
But if you must install the newer version, here you go:

all you gotta do is extract your .tar to your home folder for example. Then use the terminal to navigate to that folder. Just follow these steps

1. So you downloaded kino-1.3.2.tar.gz to your home folder (eg */home/your_user_name*).
2. Open a terminal and type "[FONT=Courier New]ls[/FONT]". You should see an entry there that says "[FONT=Courier New]kino-1.3.2.tar.gz[/FONT]"
3. Now run this: [FONT=Courier New]tar zxvf kino-1.3.2.tar.gz[/FONT]
4. then type: [FONT=Courier New]cd kino-1.3.2[/FONT]
5. Here You may wanna read any file that says "readme". type: [FONT=Courier New]gedit README[/FONT]
6. It wil tell you all the dependencies and stuff. make sure you have all of them. Install them by running each one with a "[FONT=Courier New]sudo apt-get install xxxx[/FONT]". Then look at where it says "Install Kino". The rest of the instructions are there.
7. in terminal type[FONT=Courier New]: ./configure[/FONT]
8. then: [FONT=Courier New]make[/FONT]
9. then: [FONT=Courier New]sudo make install[/FONT]
Done
to run, just type [FONT=Courier New]kino[/FONT] in the terminal or use the menu (applications -> Sound and Video -> Kino)

If you get some weird message like "abcxyz library required but not found" when installing software by compiling from source, search for "abcxyz dev" library on Synaptic and install it.

---

### Post by sin1984 on 2008-10-13
hey guys, thanks for the help, i got it up and runnin, then i was sadly dissapointed. basically i'm looking for a program that is very similar to windows movie maker. kino, from what i've tried, doesnt allow me to import pictures, only video. or am i doing something wrong?

any other program suggestions would be helpful :D thanks

---

### Post by ad_267 on 2008-10-13
Edit: Never mind, I misread your post. I'm not sure how to import pictures with Kino.

---


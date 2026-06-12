---
title: "Error message when trying to migrate wubi-ubuntu to /dev/sda3 partition"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by kkamka on 2013-05-23
Hello!
I am brand-spanking-new at using any form of linux and, after accidently deleting my windows partition *from inside wubi*, reformatting my little Aspire One's hard-drive, and re-installing windows and wubi, I am nearly ready to migrate my wubi into its own partition. The only problem is that I am such a beginner that I don't know precisely what I am doing enough to solve a seemingly basic error message. I have successfully extracted wubi-move-2.4 to my downloads and entered 

konnorkamka@ubuntu:~$ ~/Downloads/wubi-move-2.4 3$ sudo bash wubi-move.sh /dev/sda3
bash: /home/konnorkamka/Downloads/wubi-move-2.4: Is a directory

Could someone help me understand what's going on? Isn't the point of the migration code to find the directory first and the wubi-move.sh? I greatly appreciate the help. I to someday understand what is going on well enough to be the person on the helping end.;)

---

### Post by kkamka on 2013-05-23
So, I successfully figured out what I was doing. I did some further research and discovered a couple of things-most importantly being the cd command. I was not specifying the directory path is what it would seem to come down to. Flash foward to today and I've already been having fun with trying to figure out how to resize my main partition without a CD drive and a, for the moment, suboptimal internet connection. In other words, time to post more specific questions! I already feel a spiral into the world of ubuntu...

---

### Post by kkamka on 2013-05-23
Now the question is: 
How do I mark this thread as solved? :)

---

### Post by Bucky Ball on 2013-05-23
Welcome to the forums and well done. Follow the link in my thread to mark as solved and enjoy Linux and the learning curve. Say, that's not a bad name for a book! ;)

You're getting the picture as far as the forums go; post a new thread with a descriptive title in the appropriate sub-forum and include as much info as relevant for any further issue (like resizing the partition). Cheers and good luck.

Incidentally, you can't install Wubi to it's own partition. It is specifically designed to run *in* Windows like any other Win app. If you have Ubuntu now on a separate partition and you can choose Win or Ubuntu at boot you are running a fully-fledged Win/Ubuntu dual boot. The Wubi/dual-boot may be a point of confusion for you and that may help.

There are not many (any?) Wubi gurus here as not used for long before a proper install but from my understanding, isn't there an icon on the Wubi desktop that offers 'Install Ubuntu'? I've never heard of the steps you're taking, but like I say, not many Wubi experts here and I'm certainly not one. (Wubi designed to 'try before full install' and not regarded a permanent solution.)

---

### Post by kkamka on 2013-05-23
Figured it out. All done with this thread.

---

### Post by kkamka on 2013-05-24
Thanks so much for your reply! I'm just a little sorry that I had to keep replying to my own thread. 
To be completely honest, I know nothing about wubi either.:D I know nothing about any of this, really! What I have learned I will be happy to share with others in my situation.

---

### Post by Bucky Ball on 2013-05-24
All good. You will/should find a full install a lot more satisfying. Have fun and post a new thread if you hit any brickwalls.

PS: It happens occasionally. I've solved quite a number of my own issues having a conversation with myself on my own thread but good for others in future. ;)

Enjoy!

---


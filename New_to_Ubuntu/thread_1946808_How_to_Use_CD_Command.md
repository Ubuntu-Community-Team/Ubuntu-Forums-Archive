---
title: "How to Use CD Command?"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by ChannelZ28 on 2012-03-25
i hope this is an easy one. every time i try to use the cd command in terminal i get "no such file or directory."

i have some wmv video i want to convert to avi. so to use ffmpeg, i need to get to the folder the videos are in. so i type cd /videos. always the error message. i have tried it as cd /home/user/videos and all kinds of other combinations. i have tried to get into other random directories. all i ever get is the same error. what am i doing wrong?

---

### Post by Cheesemill on 2012-03-25
Commands in linux are case sensitive, try:
```
cd Videos
```
or
```
cd /home/<username>/Videos
```

---

### Post by PaulW2U on 2012-03-25
I think you need either cd Videos or cd ~/Videos depending on your current directory. Note the capital letter V. Does that help?

---

### Post by oldos2er on 2012-03-25
Linux is case-sensitive, If the folder is in your home user's folder, use ```
cd ~/Videos
```

```
cd /videos
``` would tell the shell to look for a folder named 'videos' from the root directory /

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by ChannelZ28 on 2012-03-25
duuuuuh...wow. thanks!

---

### Post by Bobhuber on 2012-03-25
> **ChannelZ28 said:**
> i hope this is an easy one. every time i try to use the cd command in terminal i get "no such file or directory."

i have some wmv video i want to convert to avi. so to use ffmpeg, i need to get to the folder the videos are in. so i type cd /videos. always the error message. i have tried it as cd /home/user/videos and all kinds of other combinations. i have tried to get into other random directories. all i ever get is the same error. what am i doing wrong?
Linux is case sensitive. Replace user with your login name.
cd /home/ChannelZ28/Videos
If you opened a terminal you should already be in your home directory and not need the full path.
cd Videos

---

### Post by GMachine_24 on 2012-03-25
If the folder you want to open is in the folder where you are located, you simply do a

```


cd Videos


```

because you don't need to tell the computer where to find the folder.

What previous posters have suggested is probably your other problem: the Videos file in the home directory is capitalized. So it would be:

```


cd /home/username/Videos


```

Hope this helps.

PS - If your problem has been solved, please edit your subject line and add [SOLVED]

---


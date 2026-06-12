---
title: "Chromium Browser?"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by Yezinki on 2012-09-21
It won't sync with my gmail account or with G Chrome browser?

---

### Post by FiremanEd on 2012-09-21
Can you provide a bit more specific to your issue?  What are you tying to do?  How are you doing this procedure? etc.

Ed

---

### Post by Yezinki on 2012-09-21
Transfer book marks, passswords etc. like i do for G Chrome on another system.

Thanks.

---

### Post by Yezinki on 2012-09-22
Does Chromium needs a flash player?

---

### Post by kazoni on 2012-09-22
Go to <Wrench Menu> -> Settings. The sign in section should be the first thing in the list.

---

### Post by Yezinki on 2012-09-22
Thanks kazoni is this for the sync or flash palyer........tried syncing but wont stop..........G Chrome takes a few mins.

---

### Post by kazoni on 2012-09-22
Sync.  

From what I understand, Flash is baked into Chrome but disabled.  Chromium requires you install it separately.

---

### Post by carl4926 on 2012-09-22
I doubt flash is required for the sync
But you will need it for the Chromium browser
Flash is installed when you install the ubuntu-restricted-extras

---

### Post by Yezinki on 2012-09-22
carl4926

Shall Chromium browser sync?

Can flash player be installed from adobe's site?

Thanks.

---

### Post by carl4926 on 2012-09-22
Chromium will sync - of course

Flash will install if you install the ubuntu-restricted-extras

---

### Post by Yezinki on 2012-09-22
carl4926, it isn't syncing.......shows in progress but never end, any ideas?

---

### Post by carl4926 on 2012-09-22
Close everything reboot
Then try again

If it still fails, I'd try deleting the hidden folder /chromium in the path ~>.config/

You press Ctrl+H to see hidden files and folders

---

### Post by Yezinki on 2012-09-22
Thanks carl4926 ill keep you updated.

Do you think I should run Bleach bit?

---

### Post by carl4926 on 2012-09-22
> **Yezinki said:**
> Thanks carl4926 ill keep you updated.

Do you think I should run Bleach bit?
No
Please don't!

---

### Post by Yezinki on 2012-09-22
Ok Boss.

---

### Post by Yezinki on 2012-09-22
carl4926 same thing........could you suggest a screen capture app so that I can post the shots.

G Chrome hardly takes a min............

---

### Post by carl4926 on 2012-09-22
If you want images. Just press PrtSc

Or you can capture the whole scene with video. But you need ffmpeg installed.

Use this in a terminal
```
ffmpeg -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -r 25 -i :0.0 -sameq output.mkv
```

---

### Post by Yezinki on 2012-09-22
Can't sync Chromium even after I changhed my google account password.......any suggestions?

Thanks.

---

### Post by Yezinki on 2012-09-22
to sync Bookmarks etc in Chromium used in ubuntu?

Thanks.

---

### Post by daslinkard on 2012-09-22
I'm assuming you are wanting to sync Google bookmarks with Chromium?  Chromium has the sync option, just enter your email and  password.It will sync everything From Google Chrome. I am using Chromium  this way.  

Go to preferences - personal stuff :

---

### Post by mörgæs on 2012-09-22
Please use a more informative thread title. 
Changed.

---

### Post by Yezinki on 2012-09-22
> **daslinkard said:**
> I'm assuming you are wanting to sync Google bookmarks with Chromium?  Chromium has the sync option, just enter your email and  password.It will sync everything From Google Chrome. I am using Chromium  this way.  

Go to preferences - personal stuff :

Exactly thats what I want & am having difficulty with........for that shall have to install G Chrome 1st?

Thanks.

---

### Post by daslinkard on 2012-09-22
If you do not have Google Chrome already installed....where are you going to be syncing from?

---

### Post by Yezinki on 2012-09-22
True..........I was assuming my other machine's google might help.

Thanks.

---

### Post by daslinkard on 2012-09-22
Once you install Chromium and you enter in your email and password this should sync your Google info.

---

### Post by Yezinki on 2012-09-22
Thanks.

---

### Post by daslinkard on 2012-09-22
No worries....Good Luck!

---

### Post by oldos2er on 2012-09-22
> **Yezinki said:**
> Can't sync Chromium even after I changhed my google account password.......any suggestions?

Thanks.

You already have a thread asking that question [here]("http://ubuntuforums.org/showthread.php?p=12254740").
It's very confusing to have two or more threads where you are asking the same questions. PLEASE, reserve each thread for one question, when the question is answered mark the thread as 'Solved' under thread tools. If you have a different question start a new thread.

---


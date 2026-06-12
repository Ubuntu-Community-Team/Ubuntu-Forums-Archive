---
title: "I'm an absolute newbie and need help fixing my trackpad (macbook 4,1)"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by richyw on 2012-04-20
Hi, So I just installed Ubuntu for the very firth time on my macbook. The trackpad does not work well at all. It only works with a lot of finger surface area and is very annoying. I really want how to learn how to use this OS but I literally cannot accomplish anything with a mouse like this. 

Does anyone know how to fix this and would be able to tell me step by step, from a blank screen, how to increase the sensitivity? On google I have already found out my macbook is the "4,1" and I have tried to change setting in a file but I could not because I did not have permission to save it. I really want to learn this but the mouse issue is a dealbreaker!:icon_frown:

---

### Post by flurospar on 2012-04-20
> **richyw said:**
> 
I have already found out my macbook is the "4,1" and I have tried to change setting in a file but I could not because I did not have permission to save it.

You generally don't have permission to save system files (e.g. the files in /usr, /var, /opt, /bin etc.) unless you use sudo.

Use```
sudo gedit <filename>
``` and provide your password. You should be able to edit and successfully save the file.

Make backups of these configuration files before you make changes to them, as a preventive measure against further screw up. For this, you can simply copy the file and save them in your home folder before you edit them.

You can restore these files (if necessary) by using:```
sudo nautilus
``` and placing back the originals files in their respective locations.

---

### Post by richyw on 2012-04-20
thanks but I still have literally no idea what I am doing to fix my mouse. It takes so long to do anything. Even write on this forum. I need step by step. I don't know how to copy and paste or do anything. I can figure it all out but I just need a functioning mouse.

---

### Post by flurospar on 2012-04-20
I can't help you very far with this, but could you tell us which file you are talking about?

---

### Post by richyw on 2012-04-20
I have actually seemed to fix it by going into the terminal and fixing it from their. Thanks for your help though! I didn't even know how to open terminal before because the control and command stuff is different. 

Now that I have a mouse I can really play around and see how linux is!

thanks again

---

### Post by flurospar on 2012-04-20
If you can, please post how you fixed your mouse here and marked the thread as solved from Thread tools.

---

### Post by richyw on 2012-04-20
To fix it I opened terminal and typed

Command:   synclient FingerLow=01 && synclient FingerHigh=10

It fixed the problem. 

I must say though my initial thoughts on this system are not great. I heard this was a great customizable OS. well so far the things that I have wanted to change are not readily done. I mean like basic stuff like moving my dock, or stopping the top bar from hiding the links, (I don't even get the point of that). Plus this dash home button, I mean I don't need a giant box that takes up my whole screen to appear when I just want to see a list of apps to open!

I'll give it a chance though

---


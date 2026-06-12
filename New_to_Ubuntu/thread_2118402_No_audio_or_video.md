---
title: "No audio or video"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by fifthwheel on 2013-02-21
Hi all, have taken the plunge and installed 12.04 learning slowly. I am having problems with youtube. I get the black screen which disappears then returns and no audio. Using Firefox but its the same in Chrome, thanks

---

### Post by NikTh on 2013-02-21
Hi ,
as you are a new user in Ubuntu , you can read some help documents such as 
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
[https://help.ubuntu.com/12.04/ubuntu-help/index.html.en](https://help.ubuntu.com/12.04/ubuntu-help/index.html.en)

Probably you will need to install some restricted programs in order to play videos and audio correctly.

You can open a terminal (CTRL+ALT+T) and issue the following command

```
sudo apt-get install -y ubuntu-restricted-extras
```it will ask for your password , write it carefully because nothing will show up (like no write anything)

Hit [Enter] and let the installation finish. 

You can copy-paste the command from here to the terminal for more accuracy. 

Thank you.

---

### Post by fifthwheel on 2013-02-21
Thanks for the reply, have done as you suggested but just the same. I tried Epiphany and it works. Chrome and Firefox says could not load shockwave and couldnt load plugin.

---

### Post by fifthwheel on 2013-02-21
> **fifthwheel said:**
> Thanks for the reply, have done as you suggested but just the same. I tried Epiphany and it works. Chrome and Firefox says could not load shockwave and couldnt load plugin.

I can only open some videos in youtube and some say I need flashplayer. I have downloaded adobe flashplayer and can see it in recent downloads but its not in the installed list in the software centre. I am trying to help myself with the problem and have been googling for answers for what seems like hours any more suggestions. thanks john.

---

### Post by NikTh on 2013-02-22
Hi,
this is strange
> **fifthwheel said:**
>  I tried Epiphany and it works. Chrome and Firefox says could not load shockwave and couldnt load plugin.

Can you give the results of the following commands ? 

```
dpkg -l | egrep -i "flash|gnash"
lspci -nnk | grep -iA2 vga
lsb_release -rcd ; uname -r
lscpu 
free -m
```_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by fifthwheel on 2013-02-22
Sorry for not replying but I gave up and have just installed Mint.I really did try with Ubuntu but what with other things to do I just had to solve the problems I was having. It does everything out of the box and to a non tech old timer it is just what I was looking for. When I get problems can I still post here or do I have to go to another forum. Many thanks for all your help.

---

### Post by fifthwheel on 2013-02-24
> **fifthwheel said:**
> Sorry for not replying but I gave up and have just installed Mint.I really did try with Ubuntu but what with other things to do I just had to solve the problems I was having. It does everything out of the box and to a non tech old timer it is just what I was looking for. When I get problems can I still post here or do I have to go to another forum. Many thanks for all your help.

Well I spoke too soon after shutting down at night with all ok next morning I had the same problems as before. The only thing I think I did was to install adblock, even when I dissabled adblock I still had no sound or video. I did another clean install of Mint and everything is ok again but I really would like rid of the adds. I am not sure about downloading anything now.

---


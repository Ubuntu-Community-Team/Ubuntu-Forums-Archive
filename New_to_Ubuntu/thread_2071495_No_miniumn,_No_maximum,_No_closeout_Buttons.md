---
title: "No miniumn, No maximum, No closeout Buttons"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by vegas89 on 2012-10-15
Probably a small issue, I'm running Ubuntu 12.4. I no longer have the buttons in the top left corner of the screen used for closing out a page or to minimize a page. Please advise:confused:

---

### Post by NikTh on 2012-10-15
Hi , 
my advise , besides your problem , is to read (if you not already discovered) this remarkable [COLOR=Blue]**[Lubuntu Wiki.]("https://wiki.ubuntu.com/Lubuntu")**[/COLOR]

Now , goto Home (Lubuntu button) > Preferences > Openbox configuration manager > click on the "Appearence" tab and take a look there about your buttons. 

Thanks

---

### Post by Autodave on 2012-10-15
> **vegas89 said:**
> Probably a small issue, I'm running Ubuntu 12.4. I no longer have the buttons in the top left corner of the screen used for closing out a page or to minimize a page. Please advise:confused:

I may be wrong here, but with the exception of Unity, all the rest have the buttons in the top RIGHT hand corner.........

---

### Post by Paddy Landau on 2012-10-15
Oops! I was talking rubbish. Please ignore this post. Sorry.

---

### Post by audiomick on 2012-10-15
That's not like you, Paddy. ;)

---

### Post by lazarojhr16 on 2012-10-15
type gconf-editor on terminal, then go to apps, metacity, general. check if maybe where it says button layout is deleted. if it is then type close,minimize,maximize:menu
hope that helps.

---

### Post by furtom on 2012-10-15
> **vegas89 said:**
> Probably a small issue, I'm running Ubuntu 12.4. I no longer have the buttons in the top left corner of the screen used for closing out a page or to minimize a page. Please advise:confused:

Are you running Unity or another desktop environment?

I suspect your WM is crashing. It could be as simple as starting it up again (this used to happen often in XFCE due to some bug or other.)

---

### Post by vasa1 on 2012-10-15
I suspect that *something* causes the occasional thread to be labelled "Lubuntu" unintentionally.
It has happened quite a few times in the past.

---

### Post by daslinkard on 2012-10-15
> **vegas89 said:**
> Probably a small issue, I'm running Ubuntu 12.4. I no longer have the buttons in the top left corner of the screen used for closing out a page or to minimize a page. Please advise:confused:
It could be in with your Compiz crashing.  You can try

```
compiz --replace &
```

---

### Post by vegas89 on 2012-10-15
To Nikth, I read the lubuntu wiki you referred to, now I'm wondering that since I am using an Intel DH61WWb3 S1155 Main board with an Intel SH2 1155 dual core with 2.7gz. Should I be using a different OS besides ubuntu

---

### Post by NikTh on 2012-10-16
Hi , 

can you open a terminal and provide some info ? 

Give the results of bellow commands 

```
lspci -nnk | grep -iA2 vga
echo $DESKTOP_SESSION
cat /etc/lsb-release 
uname -a
``` 

Thanks

---

### Post by vegas89 on 2012-10-16
vegas@vegas-desktop:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)
    Subsystem: Intel Corporation Device [8086:2017]
    Kernel driver in use: i915
vegas@vegas-desktop:~$ echo $DESKTOP_SESSION
ubuntu
vegas@vegas-desktop:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
vegas@vegas-desktop:~$ uname -a

---

### Post by nothingspecial on 2012-10-16
Prefix changed from lubuntu to ubuntu.

---

### Post by Paddy Landau on 2012-10-16
> **nothingspecial said:**
> Prefix changed from lubuntu to ubuntu.
Hence the confusion in this thread, including [post=12297565]my "rubbish" post[/post]!

vegas89: Ignore the posts about Lubuntu. We thought you were using Lubuntu because you had (probably accidentally) labelled the thread as such.

Are your windows maximised? If so, the window buttons are hidden until you move your mouse to the very top of the screen! And, if you are using full-screen mode (usually by pressing F11), the buttons disappear completely.

---

### Post by NikTh on 2012-10-16
> **Paddy Landau said:**
> Hence the confusion in this thread[/post]!

vegas89: Ignore the posts about Lubuntu. We thought you were using Lubuntu because you had (probably accidentally) labelled the thread as such..

Agreed. 


vegas89 open a terminal and give this command 

```
gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'
```are the buttons OK, now ?

If not , logout and login.

Thanks

---

### Post by vegas89 on 2012-10-16
Thanks everyone for your valued support. Perhaps I 'm being too picky with my windows layout. I'm learning new things everyday! I may have issues with my CompizConfig Manager.  I look forward to your continued help with matters yet unknown:rolleyes:

---

### Post by xlyz on 2012-10-17
> **daslinkard said:**
> It could be in with your Compiz crashing.  You can try

```
compiz --replace &
```

tx

you saved my day

---


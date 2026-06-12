---
title: "Issues with VLC (DVDs)"
date: 2014-11-30
forum: New to Ubuntu
---

### Post by derek28 on 2014-11-30
I have done the best googling I can to try and resolve this issue without wasting someone else's time, but I'm not as computer-savvy as the old people in my family think I am. 

I'm using an acer laptop, 14.04, and VLC. I've downloaded/installed ubuntu-restricted-extras. 

When I try to play any DVD I get the same results. When I press play VLC displays the total duration of the video as 00:00-00:00 and stops playing (obviously because it thinks it's 0 seconds long). 

I don't know much about computers, I hate windows and don't want to use Mac, so I'm left with Ubuntu, which I think is a great operating system, I just need to learn how to use it. 

Please help me figure out how to watch DVDs on my computer, thank you. 

You can either post in this topic or reach me at [EMAIL="GadDerek@gmail.com"]GadDerek@gmail.com[/EMAIL]

---

### Post by nerdtron on 2014-11-30
You already installed ubuntu-restricted-extras right? You may need to install the libdvdcss for restricted DVDs.

Then next step:

[LIST]
[*]Then open a terminal window and execute: 
[/LIST]
```
sudo /usr/share/doc/libdvdread4/install-css.sh 
```
[LIST]
[*]Rebooting may be necessary. 
[/LIST]
After this, VLC will automatically use it. 

Try to play your dvd again.

---

### Post by derek28 on 2014-11-30
Thank you, so much! It works just fine now. :)

---


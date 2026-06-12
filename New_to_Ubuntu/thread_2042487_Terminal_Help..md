---
title: "Terminal Help."
date: 2012-08-14
forum: New to Ubuntu
---

### Post by BlueKite on 2012-08-14
Hello,
 
I'm having a problem in my terminal and I'm hoping someone can help.
I'm using lubuntu 11.10(the ocelot one), on an Acer Aspire One AOA150 netbook.
 
I've been trying to install lubuntu-restricted-extras by using
 
```
 
sudo apt-get install lubuntu-restricted-extras

```
 
and it all seems to go well until my terminal turns blue with a 'read me' screen about microsoft fonts. It ends with an ok in pointed brackets - <ok>
 
At this point I'm not sure what I'm supposed to do. I pressed the return button - nothing happened. I typed ok - nothing happened. So I closed the terminal, assuming the installation had finished.
 
Later, I ran 
```
 
sudo apt-get install lubuntu-restricted-extras

```
again to see if it would tell me if it was installed. Instead it told me I had to manually run
```
 
sudo dpkg --configure -a

```
 
to fix the problem it had encountered. I typed this into the terminal, and after a few lines or so the blue screen appeared again.
 
I closed the terminal again hoping it had worked. I don't think it has because I then tried to get into Synaptic Package Manager, and a message popped up telling it couldn't establish an exclusive lock on something, was another process using it?
 
I have also tried
```
sudo apt-get -f intsall
```
but it too couldn't work.
 
Any guidance or fixes for what I've done wrong would be gratefully appreciated. 
 
Many thanks,
 
BlueKite. 
 
PS: I tried to find a System Restore option on the menu but couldn't find one - is it possible to do this?

---

### Post by papibe on 2012-08-14
Hi BlueKite.

Does the problem remains if you close and open another terminal?

Have you tried reseting the terminal using the terminal's menu (Terminal -> Reset)?

Regards.

---

### Post by steeldriver on 2012-08-14
You probably need to use the tab key to highlight the OK 'button' - and the use space or enter to 'click' it - see here

[http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-in-a-terminal-like-for-ttf-mscorefonts-installer](http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-in-a-terminal-like-for-ttf-mscorefonts-installer)

Try running the apt-get --configure command again and following those instructions when you get to the ms fonts license screen

---

### Post by Bucky Ball on 2012-08-14
> **steeldriver said:**
> You probably need to use the tab key to highlight the OK 'button' - and the use space or enter to 'click' it

+1. MSfonts is one of the restricted extras. ;)

---

### Post by 25tom on 2012-08-15
> **steeldriver said:**
> You probably need to use the tab key to highlight the OK 'button' - and the use space or enter to 'click' it - see here

[http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-in-a-terminal-like-for-ttf-mscorefonts-installer](http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-in-a-terminal-like-for-ttf-mscorefonts-installer)

Try running the apt-get --configure command again and following those instructions when you get to the ms fonts license screen

Quite right, just hit Tab to highlight the OK button and then hit return.

---

### Post by BlueKite on 2012-08-15
Hello,

Many thanks for the advice!

You were quite right - I did have to hit the tab button to highlight the ok.

Everything seems to have gone smoothly now.

Just to clear up something for other users: In my first post I wrote

```
sudo apt-get --configure -a
``` this is wrong. It should have been

```
sudo dpkg --configure -a
```

I hope this hasn't confused anyone.

Many thanks for the help,

BlueKite:D

---

### Post by Bucky Ball on 2012-08-15
Good news. Could you mark thread as solved from thread tools to help others?

Also, you might like to edit your first post and correct the command you mention to avoid confusion. ;)

---


---
title: "Boot in Text CLI Mode ... with hidden X.ORG in TTY2 ..."
date: 2014-03-01
forum: New to Ubuntu
---

### Post by 3kynox2 on 2014-03-01
Hello Folks !

For a strange and dark reason (that is locked in my head) I wish to boot my box into Text CLI Mode.
I found a great way to do this simply, add 'text' after 'quiet' in '/etc/default/grub', that works pretty well !

But the trick now is to get X.ORG starts (with a display manager) hiddenly on tty2 for example.

The reason I need X starts hiddenly is : 
[LIST=1]
[*]I wish to start my box in text mode, like I said, to get the best and nicest 'oh my zsh' terminal.
[*]I would like to be able to use X when I need it (by switching ctrl+alt+f2 or any other tty)
[*]X is required to startup while I'm using my console because ati drivers have to be loaded to permit me doing some crypto-currency mining while I'm in text mode.
[/LIST]

I just passed some hours finding a way to do this, and nothing was a real answer to do this.
Anyway, I'm ready to get any help on informations regarding this.

Thanks a lot !

---

### Post by sudodus on 2014-03-02
Welcome to the Ubuntu Forums :-)

1. possible with the text boot option (as you already know)


2. easy enough with the command

```
sudo service lightdm start
```


3. but if you really need X for the mining, I don't know, except that you can boot as usual (in graphical mode) and press the hotkey combination

***ctrl + alt + F1*** or*** ctrl + alt + F2 ... ctrl + alt + F6*** (and if you do not get the login prompt, the ***Enter*** key afterwards)

at the log in screen to get the text screen and then

***ctrl + alt + F7*** to quickly return to the GUI screen.

---

### Post by 3kynox2 on 2014-03-02
Hello and Thanks for your answer sudodus !

2. I tried your workaround and the problem is I need Lightdm starts, but hiddenly (on tty2 or tty7, anyway). By using that command, it starts X manually and show up the graphical inteface loading. If there is a way as it can be done in the background, that would be perfect.
3. If I refer to AMD documents, X need just to be started to be able to use ATI drivers in text cli console, no matter I'm using X or not. So switching tty is not needed.

Thanks again sudodus !

---


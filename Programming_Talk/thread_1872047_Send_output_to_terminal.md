---
title: "Send output to terminal"
date: 2011-10-30
forum: Programming Talk
---

### Post by RedSingularity on 2011-10-30
Looking for a way to send a message to a terminal even if the logged in user does not have a terminal open.  I would like the message to pop up in a terminal window or something similar.  

For example, 

echo "TEST" | wall 

Only displays the message if I have a terminal open.  If i dont have a terminal open, I dont get a message.  

Thanks.

---

### Post by Bachstelze on 2011-10-30
You can set the DISPLAY environment variable and open a popup with e.g. zenity (see screenshot). Of course you can also run a terminal with an echo command in it but it seems a bit overkill.

---

### Post by ofnuts on 2011-10-30
> **RedSingularity said:**
> Looking for a way to send a message to a terminal even if the logged in user does not have a terminal open.  I would like the message to pop up in a terminal window or something similar.  

For example, 

echo "TEST" | wall 

Only displays the message if I have a terminal open.  If i dont have a terminal open, I dont get a message.  

Thanks.Better use notify-send to send notifications to the notification widget on the user's desktop:
```

notify-send 'Hello, world!'

```

---

### Post by RedSingularity on 2011-10-31
> **ofnuts said:**
> Better use notify-send to send notifications to the notification widget on the user's desktop:
```

notify-send 'Hello, world!'

```


Thats a nice clean looking one.  Is there a way to have the message stay up until i click it closed?  By default it looks like it stays up for a few seconds before fading away.

---

### Post by RedSingularity on 2011-10-31
> **Bachstelze said:**
> You can set the DISPLAY environment variable and open a popup with e.g. zenity (see screenshot). Of course you can also run a terminal with an echo command in it but it seems a bit overkill.


Actually, this is perfect!  Nice clean window that stays open until i close it.  

One question, can I have the message be sent over my LAN to another computer?  Is there a display variable for that or should I 'mix' the command with another command?

---

### Post by Bachstelze on 2011-10-31
You can SSH into the computer and run the command from there. If you look carefully, the machine I took the screenshot on is a Mac, and I had ssh and VNC open on a remote Linux machine (itsuki). Be sure to ge the correct value for DISPLAY (echo $DISPLAY in a xterm).

---

### Post by ofnuts on 2011-10-31
> **RedSingularity said:**
> Thats a nice clean looking one.  Is there a way to have the message stay up until i click it closed?  By default it looks like it stays up for a few seconds before fading away.
See "man notify-send" for options. There is a -t option that tells how long the message remains available in the notification widget (but not how long the widget says up when popped out...).

---

### Post by RedSingularity on 2011-10-31
Thank you both! :)

---

### Post by emiller12345 on 2011-11-01
> **Bachstelze said:**
> Be sure to ge the correct value for DISPLAY (echo $DISPLAY in a xterm).
if you don't know the display setting, you can...
 ```
DISPLAY="$(echo -ne "$DISPLAY")" zenity --info --text='Hello World!'
```

---

### Post by Bachstelze on 2011-11-01
> **emiller12345 said:**
> if you don't know the display setting, you can...
 ```
DISPLAY="$(echo -ne "$DISPLAY")" zenity --info --text='Hello World!'
```

You can't do that because DISPLAY is only defined in X, so you have to get the value in a xterm. If you do echo $DISPLAY in SSH, it will be blank.

---


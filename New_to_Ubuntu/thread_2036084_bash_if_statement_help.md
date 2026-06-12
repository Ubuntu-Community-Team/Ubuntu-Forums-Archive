---
title: "bash if statement help"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by djyoung4 on 2012-08-01
So I am working on a short if statement that switchs the sound between the speaker output and the hdmi output depending on where .asoundrc is.  I want the script to move .asoundrc back and forth between two locations but I can only get it to do one or the other.  I think somewhere in my syntax is wrong and I was hoping another set of eyes may be able to help.  Any help is greatly appreciated
```
#!/bin/bash
#switches sound between hdmi and speakers 
if [ -f `~/Documents/.asoundrc`]; then
mv ~/Documents/.asoundrc ~/.asoundrc
sudo rc.d force-restart alsa
notify-send hdmi sound
else
mv ~/.asoundrc ~/Documents/.asoundrc
sudo rc.d force-restart alsa
notify-send laptop sound
fi
```

---

### Post by Blackbird_13 on 2012-08-01
In the third line I think you need a space before ] .

---

### Post by hakermania on 2012-08-01
> **Blackbird_13 said:**
> In the third line I think you need a space before ] .

This!
Also, your styling code:
```
#!/bin/bash
#switches sound between hdmi and speakers 
if [ -f `~/Documents/.asoundrc`]; then
mv ~/Documents/.asoundrc ~/.asoundrc
sudo rc.d force-restart alsa
notify-send hdmi sound
else
mv ~/.asoundrc ~/Documents/.asoundrc
sudo rc.d force-restart alsa
notify-send laptop sound
fi
```
can easily become this one:
```

#!/bin/bash
#switches sound between hdmi and speakers 
if [ -f "~/Documents/.asoundrc" ]; then
   mv ~/Documents/.asoundrc ~/.asoundrc
   sudo rc.d force-restart alsa
   notify-send hdmi sound
else
   mv ~/.asoundrc ~/Documents/.asoundrc
   sudo rc.d force-restart alsa
   notify-send laptop sound
fi

```
which is more easy for everyone to read :)

---


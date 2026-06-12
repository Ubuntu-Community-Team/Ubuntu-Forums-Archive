---
title: "once i download bash script... what happens?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Mic_Droz on 2008-08-23
Hey guys, feeling a bit retarded here...

i downloaded a bash scripts called flac2mp3, but now that i have the file, I don't actually know where to put it in order for it to actually work!

I've been reading around (googling, etc) and have come to the conclusion that i put it in /bin/ (or tried) but no dice - how can I get this to work?

---

### Post by eightmillion on 2008-08-23
You can run it from any directory. Just run it like this: **./flac2mp3**
The dot slash in front of the script name tells bash to look in the current directory for a script named flac2mp3. If you want to be able to call it from anywhere without the preceeding ./, I would put it in **/usr/local/bin** .

Edit: You'll probably have to make sure it's executable also:
> chmod +x ./flac2mp3

---

### Post by crispy_420 on 2008-08-23
Is it a nautilus script that you plan on using via a right click?

Then: /home/"your user name"/.gnome2/nautilus-scripts

---

### Post by Mic_Droz on 2008-08-23
Brilliant, thanks. feeling slightly less retarded now that it finds the script... and now, to make it work

I'll just dig up that thread again...

Cheers, Thanks!

---


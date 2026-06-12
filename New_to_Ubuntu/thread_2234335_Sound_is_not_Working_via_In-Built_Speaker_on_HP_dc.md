---
title: "Sound is not Working via In-Built Speaker on HP dc7100cmt Desktop"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by Ishant_Tayal on 2014-07-14
Hello All,

Yesterday, I have installed Xubuntu on my HP Desktop which is dc7100cmt. P4 system with 4 GB RAM.

I have updated OS and installed couple of other software like Libre Office, VLC Player etc.

But i noticed that the Sound is not working. I checked the sound icon and looks like Sound Driver is installed.

Earlier to this, i had installed Windows Xp and Sound was working very fine.

Then i connected my external Speaker which worked like a charm.

Can anyone help me to fix the Sound issue on In-Built Speaker.

My email ID is <snip>

---

### Post by newb85 on 2014-07-14
Welcome!  Help in the forums is posted to the forums, rather than sent through personal messages or email.

I'm not familiar with the GUI of Xubuntu, so I'll start from a different angle.  Open a terminal (I believe Ctrl+Alt+T will do the trick), type the following and hit enter:
```
alsamixer
```

In the alsamixer, you can use the left and right arrows to switch which slider is selected, and the up and down arrows to adjust the levels.  The ones that are muted have "MM" at the bottom.  Pay special attention to the "Master" and "Speaker" sliders.  When you're finished, you can exit the alsamixer with Ctrl+C.

---

### Post by Ishant_Tayal on 2014-07-14
ok i will try when i go home and let you know an update. thanks your your suggestion.

---


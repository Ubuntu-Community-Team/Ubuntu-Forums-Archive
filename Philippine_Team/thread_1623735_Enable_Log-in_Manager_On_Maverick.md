---
title: "Enable Log-in Manager On Maverick"
date: 2010-11-17
forum: Philippine Team
---

### Post by ysNoi on 2010-11-17
Mga bro, patulong naman kung paano enable ang Log-In Manager sa Maverick...

Nag-search ako sa Google hindi na daw enabled ang Log-In Manager sa Maverick...Totoo po ba..?

---

### Post by Jechem on 2010-11-18
try mo Ubuntu Tweak. pwede ka mag change ng login background. pero kung guto mo pang itweak ung mga fonts and colors type mo sa terminal:

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

logout then tweak the fonts and colors sa gusto mo then login.

type in terminal again:

sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

to remove the appearance properties from popping up during login

---


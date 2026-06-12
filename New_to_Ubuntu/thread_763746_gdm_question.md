---
title: "gdm question"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by imT on 2008-04-23
how do i choose my gdm theme?, i have choose at the "login window preferences" the plain style; and every time i'm at the login screen i see the human theme even thow i choose another one before...what to do to have a custom theme as default ?

p.s. i like the new ubuntuforums look :)

---

### Post by markjensen on 2008-04-23
The gdmthemechooser has worked for me.  I prefer a face browser with icons for my account, and the kids' account, so they just click their image and enter their password.

Does it not come up for you and let you select?

---

### Post by Martje_001 on 2008-04-23
Copy your theme to '/usr/share/gdm/themes' and go to Login Window Settings (in your menu).

---

### Post by ponx on 2008-05-22
I have the same problem, I use the 'plain' login window and in its menu I select the 'Industrial' theme, but it reverts back to 'Human' when I next boot up..!?

The themes for the plain login window are in /usr/share/themes; I tried copying it into /usr/share/gdm/themes, but it doesn't show up in the login window settings..!?

Can anyone shed light on this, is there a config file I need to edit..?

Cheers.

ponx

---

### Post by farsight on 2008-05-22
In 8.04 go to system at the top and then choose administration. Click on the login window and insert your password. Click on local at the top (2nd tab along). Click on it (should show you the gdm themes there). From here click add and then direct the popup window to the place in which you saved your GDM theme.

I did this to install the orbital GDM theme, which in my opinion gives you a sleek start to a sleek operating system :)

Hope this help you :)

EDIT: By the way I put my themes in to a directory I named "theme" :) If you direct it here you can leave your theme in this folder and have the GDM working :)

---


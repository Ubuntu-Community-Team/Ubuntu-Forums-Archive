---
title: "Problem downloading photos."
date: 2008-09-08
forum: New to Ubuntu
---

### Post by L Campbell on 2008-09-08
I'm running Hardy 8.04 on a PC and am having trouble downloading pix from my camera flash card.

The 'Compact card reader' is in the USB port and I have a 512MB 'Compact flash card'.

As per the camera (Olympus E-20) instructions I formatted the card in the camera and took some photos but, when the card shows up on the desktop it appears as 'No Name'.

When I go to 'Permissions it tells me,'The permissions of 'No Name' could not be determined and the folder shows in the No Name - File Browser with the dreaded padlock on it.

I would appreciate it if someone could advise me what to try here.

TIA.

---

### Post by Sealbhach on 2008-09-08
Perhaps try to exctract them using F-Spot photo manager.

Just a suggestion.


.

---

### Post by t0p on 2008-09-08
Have you tried accessing the card as root?  Press **Alt+F2**, and in the Run box type

```
gksudo nautilus
```

Use the file manager window that opens to navigate to the card.

---


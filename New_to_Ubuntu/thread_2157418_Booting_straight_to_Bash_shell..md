---
title: "Booting straight to Bash shell."
date: 2013-06-25
forum: New to Ubuntu
---

### Post by peterdac on 2013-06-25
Can anyone advise on how to boot straight to the BASH shell in version 12.04.  The ¨Introducing Ubuntu Linux¨ 3rd ed. gives some details, though I can´t make sense of them.

---

### Post by Cheesemill on 2013-06-25
To always boot into CLI mode run the following command...
```
echo "manual" | sudo tee -a /etc/init/lightdm.override
```

Once you are logged in you can start the GUI by running...
```
startx
```

---

### Post by dino99 on 2013-06-25
you need to select the "recovery mode" inside the grub menu (2d line choice) (hold "shift" key down at bios end process to get the grub menu on a single OS system)

---


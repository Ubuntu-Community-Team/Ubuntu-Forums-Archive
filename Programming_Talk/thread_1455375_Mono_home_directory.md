---
title: "Mono home directory"
date: 2010-04-15
forum: Programming Talk
---

### Post by toogooda on 2010-04-15
I am wanting to find out what the users home directory/folder is IE /home/andrew
In shell I usually use ~ but this does not seem to work using System.Diagnostics

Is there a way of finding out inside mono what the users linux/ubuntu home directory is?

---

### Post by SKLP on 2010-04-16
Environment.GetFolderPath(Environment.SpecialFolder.Personal)

Also you can use Environment.SpecialFolder.ApplicationData to get ~/.config on *nix, and also the correct dir on windows

---

### Post by toogooda on 2010-04-17
> **SKLP said:**
> Environment.GetFolderPath(Environment.SpecialFolder.Personal)

Also you can use Environment.SpecialFolder.ApplicationData to get ~/.config on *nix, and also the correct dir on windows

Thanks works perfectly thank you very much!

---


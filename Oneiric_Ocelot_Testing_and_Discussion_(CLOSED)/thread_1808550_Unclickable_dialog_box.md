---
title: "Unclickable dialog box"
date: 2011-07-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-07-20
Has anyone else run into this (see the screenshot), and if they have, what have you done to fix it?

As you can see the dialog box is in the upper right workspace, in the lower left corner, when I click on the workspace the dialog box isn't visble.

---

### Post by seeker5528 on 2011-07-20
> **cariboo907 said:**
> Has anyone else run into this (see the screenshot), and if they have, what have you done to fix it?

As you can see the dialog box is in the upper right workspace, in the lower left corner, when I click on the workspace the dialog box isn't visble.

Did you try dragging it to the center of one of the desktops, before switching to that desktop?

Later, Seeker

---

### Post by cariboo on 2011-07-20
That's the problem, I can't drag the dialog box anywhere, usually it's in the middle of the 4 workspaces, and I can at least click the OK or Cancel button, but his time the only way to close the program was to kill it.

So far this has only happened when using qBittorrent

---

### Post by godhika on 2011-07-20
Just had an idea as this happens also with texworks for me. The culprit is the new modal dialogs. Deactivating them and the problem is gone

---

### Post by cariboo on 2011-07-20
> **godhika said:**
> Just had an idea as this happens also with texworks for me. The culprit is the new modal dialogs. Deactivating them and the problem is gone

Thanks, that solved the problem. I think it may be time to create a bug.

**Edit:** Bug #[lpbug]813891[/lpbug]

---


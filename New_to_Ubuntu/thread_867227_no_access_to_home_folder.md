---
title: "no access to home folder"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by bob_hilton on 2008-07-22
I'm having a nightmare with my home folder.

how do i take ownership/give myself permission?

i had permission this morning and have used transmission, sound converter and firefox. which of these would screw folder permissions?

---

### Post by Xerp on 2008-07-22
```
sudo chown -R yourlogon ~
```

---

### Post by bodhi.zazen on 2008-07-22
> **bob_hilton said:**
> I'm having a nightmare with my home folder.

how do i take ownership/give myself permission?

i had permission this morning and have used transmission, sound converter and firefox. which of these would screw folder permissions?

What kind of problem ? error message ?

You can run into these problems running graphical applications as root using su.

---

### Post by bob_hilton on 2008-07-22
no error message but no bookmarks in firefox, transmission stopped downloading and the power button closed all gnome panels but didn't shutdown. there was an error when i logged back in but i didn't manage copy it. i'll post it later (when i get chance). also, using nautilus as root and changing the permissions on the folder wont let me enable read/write on it, it changes back to display '--' (without quotes) after a few seconds.

---

### Post by bodhi.zazen on 2008-07-22
Is your disk full or mounted as ro ?

---

### Post by bob_hilton on 2008-07-23
my disk isnt full but i think it may be owned by root. How do i check?

---

### Post by bodhi.zazen on 2008-07-23
Can you post the output of :

```
ls -l /home
```

---

### Post by RuleMaker on 2008-07-25
This will give all users full access:
```
sudo chmod a+x+r+w ~/<your_username>
```

---


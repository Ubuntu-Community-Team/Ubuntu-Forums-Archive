---
title: "Changing password &amp; a few other things…"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Dissident85 on 2008-05-26
Hi all, I just wanted to know how to do a few things…

1)When I installed ubuntu, I used the alternate install CD and set up an encrypted vlm. Now I want to change the password to that how could I do that??? 
2)I would also like to change the root password??? How do I do that… 
3)I am creating a guest account which I want to either lock in their home folder… or at least lock them out of mine. I know to lock them out of my home folder I will need to use chmod… but im not to sure how??? 

Any help would be greatly appreciated…

Cheers.

---

### Post by shifty_powers on 2008-05-26
well as fo number 3, a guest account will, by default, not be able to see into your home folder...

---

### Post by Dissident85 on 2008-05-26
> **shifty_powers said:**
> well as fo number 3, a guest account will, by default, not be able to see into your home folder...

mmmm perhaps i didn't create the account correctly. because it can :S

---

### Post by Sinkingships7 on 2008-05-26
They'll be able to see into it, but they won't be able to modify your files. To lock them out, right-click on your home folder, go to properties, go to permissions, and change Others to 'None' so no one else but you and people in your group have access to the folder.

EDIT: No, you didn't mess anything up :]   They can see it by default, just not modify it.

---

### Post by Dissident85 on 2008-05-26
cool thanks, that works... anyone know how to do one and two?????

---

### Post by spiderbatdad on 2008-05-26
> **Dissident85 said:**
> cool thanks, that works... anyone know how to do one and two?????

By default there is no root password. It is best to leave the system that way. Get a root shell using ```
sudo -i
```from your user account.
To go against good advice, run ```
sudo passwd
```

```
your_username passwd
```will change the password of a user named "your_username."

---

### Post by Dissident85 on 2008-05-26
ok, thanks for that... anyone got an answer for number one???

---


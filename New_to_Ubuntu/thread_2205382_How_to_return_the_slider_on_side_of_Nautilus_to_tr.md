---
title: "How to return the slider on side of Nautilus to traditional type?"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-02-13
I really find the new slider in Nautilus and gedit to be clumsy. How can I reconfigure it to present the normal slider?

---

### Post by monkeybrain20122 on 2014-02-13
Remove overlay-scrollbar, overlay-scrollbar-gtk2, overlay-scrollbar-gtk3

---

### Post by Odyssey1942 on 2014-02-13
Thanks MB, Is that code to run in terminal?

---

### Post by monkeybrain20122 on 2014-02-13
```
sudo apt-get remove overlay-scrollbar*
```

However the easy way to manage packages would be through a gui. I don't like the Ubuntu Software Centre since it is too slow and doesn't have too many fine grained control. I would install synaptic, it is a great piece of software I can't do without.

```
sudo apt-get install synaptic
```

---

### Post by Odyssey1942 on 2014-02-13
Installing synaptic as I write.

Ran the remove code, but the slider is still there.

Do I need to run each of the three, restart or what?

---

### Post by monkeybrain20122 on 2014-02-13
The command should have removed all three (because of the * and also because the two gtk ones depend on the first ,I think)May need to restart, or just logout and login again.

BTW, each time when you use synaptic you should always click "Reload" to update the database first to reflect the latest changes. This is the same as running in the terminal
```
sudo apt-get update
```

---

### Post by Odyssey1942 on 2014-02-13
have lots of in-progress docs and windows open so will restart when i get these closed. Thanks for your guidance.

---

### Post by monkeybrain20122 on 2014-02-13
Well if you have in progress docs then of course it won't go away. :)

---

### Post by Odyssey1942 on 2014-02-13
Aha! Did not realize that.

also ran the update above and it got very busy indeed. So this should be done after every install, or code run?

---

### Post by monkeybrain20122 on 2014-02-13
Just reload every time you launch synaptic, the point is to update the information for the repositories which may have changed since your last job. But don't have to reload after working with it, just closing the program is fine.

---

### Post by Odyssey1942 on 2014-02-13
Have restarted and behold, I have my old slider back. Many thanks.

---


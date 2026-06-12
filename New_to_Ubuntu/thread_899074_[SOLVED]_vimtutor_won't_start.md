---
title: "[SOLVED] vimtutor won't start"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by tombo465 on 2008-08-24
hello , I've used vimtutor a while back and just had to type it in the terminal and it started . since then I've switched from ubuntu 7.10 to 8.04 and now when I type "vimtutor" vim starts but is empty . I went into synaptic  and searched for vimtutor and it's supposed to bundled with vim .   Thank You tombo465

---

### Post by overdrank on 2008-08-24
Moved to ABT (Absolute Beginner Talk)  :)

---

### Post by kjohansen on 2008-08-24
you could try to remove vim and then reinstall incase the tutor file was somehow lost in the upgrade.

i just ran vimtutor on 8.04 so it does work on it.

```

sudo apt-get remove vim

sudo apt-get install vim

```

---

### Post by Nepherte on 2008-08-24
Vimtutor gets his file from this location: /usr/share/vim/vim71/tutor/tutor

I think it comes along with the vim-full package:
```
sudo apt-get install vim-full
```

---

### Post by tombo465 on 2008-09-02
Thanks Nepherte that was the ticket !! kind of strange, when i loaded vim from synaptic i looked and looked for anything else vim related that might have been missed and i do not recall seeing vim-full . must have missed it i guess . Thanks again for your help I'm quite the newb!

---


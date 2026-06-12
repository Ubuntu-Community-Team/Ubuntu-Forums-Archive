---
title: "Vim not formatting code"
date: 2010-12-06
forum: Programming Talk
---

### Post by mongoose_za on 2010-12-06
Hi there,

I'm on Ubuntu Maverick and just installed vim(7.2.330) via the repos.
I've also installed cream via the repos.

Launching vim via terminal I opened an html file. 
I put in *ESCgg=G*. I've also tried *ESCggVG=*. On my windows machine these commands format the html nicely but is not working here on my linux. Any suggestions?

Btw if I use cream then the formatting works fine. But obviously I'd prefer to have this work in vim itself.


Thanks

---

### Post by DaithiF on 2010-12-06
you need to tell vim to load indent expressions based on the type of file being edited.
add:
```
filetype indent on

```
to your .vimrc, restart vim, and it should then work.

---

### Post by mongoose_za on 2010-12-06
That was quick and easy. Thanks a lot DaithiF.

---


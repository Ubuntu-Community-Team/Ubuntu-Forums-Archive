---
title: "a small text script"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by sketzski on 2008-05-07
i need to write a script to edit a text file. basically i want to move playlists over to my mp3 player only the directoy is slightly different then on my computer so i would like a script to run through and change the lines.
ex.
/home/user/music/Oasis/(Whats the Story) Morning Glory/03. Wonderwall.m4a

would change to

RBmusic/Oasis/(Whats the Story) Morning Glory/03. Wonderwall.m4a

could anyone point me in the right direction or show me how to do this. thanks so much

---

### Post by glennric on 2008-05-07
Try the command
```
sed -i 's/\/home\/user\/music/RBmusic/g' filename
```

---

### Post by sketzski on 2008-05-08
thanks! works perfect

---


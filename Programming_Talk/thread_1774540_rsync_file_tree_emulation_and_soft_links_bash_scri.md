---
title: "rsync file tree emulation and soft links bash script"
date: 2011-06-03
forum: Programming Talk
---

### Post by j_arquimbau on 2011-06-03
Hello everybody,

I come to you to see if I can get any idea on how to begin o do the next, and may be, developing it :)

My idea is the next; I've got a encfs folder synced with Dropbox. I'd loke to create a folder insede it where there was the same tree as in home (except the folder itself). for instance:
/home/user
[LIST]
[*]Images
[*]Documents
[*]Desktop
[*]Music
[*]Video
[*]Public
[*]Dropbox
[/LIST]

And now the folder inside the Dropbox:

/home/user/Dropbox/Encrypted
[LIST]
[*]Images
[*]Documents
[*]Desktop
[*]Music
[*]Video
[*]Public
[/LIST]

Now, what I'd like to do is that if I saved something in the ~/Dropbox/Encrypted , a link would automaticly be created to the real path of the home folder.

My needs would then be two:
1) A daemon that would check for any new folder created in the home tree that would create that folder in the Dropbox Encrypted tree.

2) A daemon that would automaticly create links to the correspondent path everytime a file is written in the Dropbox Link.

Thas anyone have a clue on how I should begin this?

---

### Post by j_arquimbau on 2011-06-03
I got a clue to create the tree:

```
rsync -av --exclude='Dropbox/' --include='*/' --exclude='*' /home/user/ . /home/user/Dropbox/BACKUPS_PC
```

Not a daemon though, but nice to be the first step...

---


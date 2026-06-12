---
title: "Help with meaning of &quot;[nvpy]&quot; in terminal"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by eWzczyM on 2014-05-07
Hello, I am a novice with Ubuntu. I am trying to install NVpy and change the settings for the database. I do not understand what the following command requires me to do:

[nvpy]

I have installed fine and NVpy launches fine, though as yet with no database.

The relevant section is:

"Then edit the configuration file to write to plain text files instead of
 json, to write to your dropbox folder and to keep SimpleNote off:

# cat .nvpy.cfg 
[nvpy]
notes_as_txt = 1
txt_path = /home/miguel/Dropbox/nv/
simplenote_sync = 0"

See the following link: [http://mylinuxlife.com/installing-notational-velocity-and-its-cousin-nvpy/](http://mylinuxlife.com/installing-notational-velocity-and-its-cousin-nvpy/)

Any help would be most welcome!

---

### Post by steeldriver on 2014-05-07
it's just telling you how the contents of your .nvpy.cfg file should look when you're done editing, I think. The [nvpy] is just a section name in the file (in the style of a Windows '.ini' file).

```

[nvpy]
notes_as_txt = 1
txt_path = /home/miguel/Dropbox/nv/
simplenote_sync = 0

```

The 'cat .nvpy.cfg' part is just the command that was used to show the file contents. You can use any text editor to create / modify the file e.g.

```
gedit ~/.nvpy.cfg
```

---

### Post by eWzczyM on 2014-05-07
OK, I think I understand. The command you provided launches a text editor of the blank file, which I can then edit or paste in the relevant text. When I save it, I am assuming that the settings for the program nvpy will change. Thank you very much!

---


---
title: "Bash script - New mail with attachment"
date: 2010-05-28
forum: Programming Talk
---

### Post by Klau3 on 2010-05-28
How can I add a file to a new mail? I have written a bash script that enables  me to resize pictures to a certain custom MB size. Next step is, that I  want to add the ZIPed images to a new mail message (&#8594; standard mail program of the user). I tried with: ```
gnome-open mailto:max.example@example.org
``` ... but couldn't find a way how to manage it. A tip would be  nice.

Klau3

---

### Post by Klau3 on 2010-05-31
I still don't know how to send mail attachments with gnome-open from Terminal.

For [Thunderbird]("http://kb.mozillazine.org/Command_line_arguments_-_Thunderbird") it works this way:[FONT=monospace]

[/FONT]```
thunderbird -compose "attachment=/home/[username]/..."

```

---

### Post by gmargo on 2010-05-31
A quick glance at the source makes me think it is not possible with gnome-open.  gnome-open looks like it only pays attention to the first argument, and only processes gnome-specific options.  But I may be wrong. Check it out yourself in the libgnome2-0 source.

---


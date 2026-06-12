---
title: "How to change mass groups of filenames of mp3's?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by kramer65 on 2008-06-27
Hello,

I recently switched from xmms to Audacious for my music playing. It is a little better than xmms, but Audacious has one drawback. It doesn't play mp3's which have an '&' sign in the filename. Now I need to edit all my mp3's names to change '&' to 'and'. 

How would I be able to do that?

---

### Post by bluefrog on 2008-06-27
for i in *.mp3; do mv "$i" "${i//&/and}"; done

---

### Post by kramer65 on 2008-06-27
Sorry. That's a bit too fast. 

Ehm. I guess this is with the command line. So I need to 'cd' to the folder and than use that line?

---

### Post by bluefrog on 2008-06-27
yes or if your music is in the /home/$USER/Music folder you could also:

for i in $(find ~/Music -name *.mp3); do mv "$i" "${i//&/and}"; done

---

### Post by logos34 on 2008-06-27
> **kramer65 said:**
> Audacious has one drawback. It doesn't play mp3's which have an '&' sign in the filename. 

didn't know that.  that's some oversight on the devs part!

---

### Post by jay019 on 2008-06-27
> **logos34 said:**
> didn't know that.  that's some oversight on the devs part!

Wow, news to me to. I try to avoid any non alphanumeric characters in filenames as a general rule tho.

Some programs in the "Add/Remove Applications" that do mass/batch file renaming:
KRename
GwenRename
Bulk Rename
Purrr
PrefixSuffix

Hope that helps

---

### Post by Inxsible on 2008-06-27
install EasyTag. its in the repos..

you can not only change filenames but also edit id3v tags using it.

---

### Post by kramer65 on 2008-06-27
Great!

The command line thingy worked perfect!

All the programs will come in handy as well!

Thanks for all the tips!

---


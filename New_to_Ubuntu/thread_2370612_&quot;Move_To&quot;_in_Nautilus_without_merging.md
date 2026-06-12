---
title: "&quot;Move To&quot; in Nautilus without merging?"
date: 2017-09-05
forum: New to Ubuntu
---

### Post by sonicwind on 2017-09-05
Unless I'm missing something, you can't move data to another location in Nautilus without merging it with the data that's already there. Unless the destination is empty of course. Is this correct? There's no option to overwrite. You can only merge, skip or cancel.

If this is the case, can someone recommend another GUI file manager that works with Unity that allows overwriting?

I know there are CLI options, but until I'm more familiar with all the switches in things like rsync, I'd like a GUI alternative.

Thanks. Ubuntu 16.04 LTS

---

### Post by ajgreeny on 2017-09-05
Can you give us some examples of exactly what you mean; I am a bit confused.  Are trying to move a folder or a file, and from where to where?

If I try to move a file called **test.txt** from one folder to another folder that also contains a file called **test.txt**, the options I see are as shown in the screenshot; there is no option to merge, hence my confusion.

---

### Post by sonicwind on 2017-09-05
Thanks for responding ajgreeny.

OK, I tried again and now  it's only happening to me for both copying & moving directories.  From where to where doesn't seem to matter. I've done it with both  directories in folders in the home directory, and also with the other location being  on another ext4 partition. See the attached image.

---

### Post by ajgreeny on 2017-09-05
I have never sen that, perhaps because I have not moved folders in the same way as you have, so I can not help with any real answer for you.

---

### Post by sonicwind on 2017-09-05
I think I've figured this out. I misunderstood the second sentence in my attachment.

If you copy one directory into another location with a directory of the same name, my attachment dialog pops up.

If you then tell it to merge, if there are any files inside that have duplicate names, it will still pop up your attachment dialog.

I'll mark this solved. Thanks for your attention ajgreeny.

---


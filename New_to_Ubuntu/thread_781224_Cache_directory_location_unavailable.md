---
title: "Cache directory location unavailable ???"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Innernet on 2008-05-04
What do I do now ?
Was going to burn a CD, clicked on "Write to disc" and this message which I do not know how to handle shows up :

---

### Post by quirks on 2008-05-04
Most likely you do not have enough space in your home directory. Serpentine caches the data it burns on CD in a subdirectory in your home directory. Make sure, you have at least 700MB free disk space in your home directory.

If this is not the case, you will have to redirect the cache directory to some other location. According to this thread [http://ubuntuforums.org/showthread.php?t=488971]("http://ubuntuforums.org/showthread.php?t=488971"), the gconf key is located here: ```
/apps/nautilus-cd-burner/temp_iso_dir
```

It could also be that you messed up somehow with the permissions of the cache directory, but this is less likely.


Besides, I must say this error message is quite misleading for a "not enough disk space" condition.

---

### Post by Innernet on 2008-05-04
Hello quirks.
Thanks for your very precise diagnostics. =D>  As you said, simply out of hard drive space to shuffle the files to prepare the burning.
Moved files to an auxiliary drive and all went fine !

Yes, if the wording for some messages was more understandable for beginners, life could be simpler.	;)
I could say "Not enough space to prepare the files to be burned" :rolleyes:

---


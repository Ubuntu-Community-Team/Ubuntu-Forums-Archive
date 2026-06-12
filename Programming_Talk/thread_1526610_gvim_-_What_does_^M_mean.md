---
title: "gvim - What does ^M mean?"
date: 2010-07-08
forum: Programming Talk
---

### Post by adit on 2010-07-08
I opened a text file in gvim.  It shows ^M at the end of each line.  I didn't type these characters.  What do they mean?

---

### Post by Arand on 2010-07-08
Carriage return (Control-M or \r) as opposed to newline \n. If I've understood things correctly.

- arand

---

### Post by ja660k on 2010-07-08
theres a command dos2unix
[http://linux.softpedia.com/get/Utilities/Dos2Unix-5519.shtml](http://linux.softpedia.com/get/Utilities/Dos2Unix-5519.shtml)

strange that ubuntu doesnt have this installed out of the box.
(unless there is one im not familiar with)

---

### Post by wmcbrine on 2010-07-08
And in case it wasn't clear from the previous posts... the reason you're seeing these is that you've opened a file that was created to the DOS/Windows standard for text files, where every line ends with a pair of characters: CR (AKA carriage return, \r, ^M, 13, or 0x0D), then LF (AKA line feed, \n, ^J, 10, or 0x0A). The Unix standard is just LF. (The old-time Mac standard, also used on a few other systems, was just CR, but current Macs are Unix-based and favor LF.)

Many editors (e.g., nano) will handle any of these line endings, and convert automatically.

---

### Post by gmargo on 2010-07-09
Actually gvim/vim will handle files with DOS-format (CR-LF) line endings just fine, as well as files with the default UNIX-format (LF) line endings (and also MAC-format (CR)).  A problem pops up when a file is not entirely consistent in it's line endings - then (g)vim guesses UNIX, and shows the bonus carriage returns as ^M characters.

The simple (g)vim command to remove the ^M characters is:
```

:%s/^M//

```NOTE: Type control-V control-M to enter the ^M character.

You can view (g)vim's current idea of the file format with the command
```

:set ff?

```which will show "fileformat=unix" or "fileformat=dos" or "fileformat=mac".

---


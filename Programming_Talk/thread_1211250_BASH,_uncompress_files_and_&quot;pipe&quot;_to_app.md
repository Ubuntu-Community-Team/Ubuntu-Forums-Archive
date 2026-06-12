---
title: "BASH, uncompress files and &quot;pipe&quot; to app"
date: 2009-07-12
forum: Programming Talk
---

### Post by BoyOfDestiny on 2009-07-12
I apologize if the title was a bit vague. You know how certain applications support opening files that are .zip, gz, etc, without needing to be uncompressed by the user beforehand...

What is the most elegant way to simulate that for programs that cannot open archives? Extract the file(s) to RAM, or to /tmp, and then rm them when finished?

I'd like to be able to take `someprogram "$1"` either a zip, rar, 7z, gz, extract the file then pass the file or files extracted as the parameter, and if not just pass the parameter unchanged.

I could manage this with kind of sloppy folder, extract file, run program with parameter (or somehow pass multiple files that were in the archive, a `for in`), if no unarchiving needed, just pass the parameter. 

So I would drop a script in ~/bin, with the same name as the app, that would act as a middle man.

To reiterate, the use case is: progams, such as music players or emulators, to open with the command normally used to launch them, but uncompressing an archive if not supported by said software, and have it play those files as if uncompressed, then clean up the cruft when closed.

It should seamlessly simulate applications that can handle compressed archives, without needing the user to manually uncompress beforehand.

Just seeing a simple example, i.e. uncompress the file, and launch the files as paramters, would do the trick (in the least disk wear and tear kind of way...)

---

### Post by c0mput3r_n3rD on 2009-07-12
zcat and zmore are commands that display the contents of compressed files.  I'm not sure if you're just talking about text files or if zcat and zmore only work with text files (which I think it does) but hopefully this will help you.

---

### Post by BoyOfDestiny on 2009-07-12
*Removed* Double posted by accident...

---

### Post by BoyOfDestiny on 2009-07-12
Here, its better if I show some code I guess. This is what I have so far, I was just wondering the best method of holding files in a temporary location (hard drive or mem?)

```
#!/bin/bash
tempFolder="/tmp/audaciousTemp"
mkdir "$tempFolder";

case "$1" in
  *.rar | *.rsn)
    cd "$tempFolder"
    unrar x "$1";
    audacious2 *
    break;
  ;;

  *.7z)
    cd "$tempFolder"
    7zr e "$1";
    audacious2 *
    break;
  ;;

  *.zip)
    cd "$tempFolder"
    unzip "$1";
    audacious2 *
    break;
  ;;
  
  *)
    audacious2 "$1"
  ;;
esac

rm -rf "$tempFolder";

exit
```
Consider this script GPL'd... Though I've often wondered, what is the best license for a bash script... As it would be funny to include the full text of the gpl...

So anyway, not perfect, but allows an archive to be loaded as if it had been uncompressed beforehand. If anything that isn't a 7z, rar, or zip is passed, audacious opens it as it normally would... You can see how this would work for other software, that doesn't "read" these formats by default.

---


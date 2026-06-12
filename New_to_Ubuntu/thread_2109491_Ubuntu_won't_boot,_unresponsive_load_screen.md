---
title: "Ubuntu won't boot, unresponsive load screen"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by PianoManEDTA on 2013-01-27
I recently attempted to install a package using its source files instead of apt-get. The rabbit hole (read: dependencies) grew to an enormous length, and I went too deep. Believe me, I've learned my lesson, and will, in all circumstances, use apt-get over configure;make;make install from here on out. 

However, this wasn't without its consequences: I can no longer boot normally. The purple "Ubuntu" load screen appears, the bar/dots "load", and then sometimes the whole thing turns blue and completely unresponsive (except for the power button, which brings up the suspend, restart... options). Otherwise it remains completely unresponsive on the purple load screen. Booting from failsafe graphics, low-graphics mode works, thankfully. I've tried uninstalling my work to no avail. 

I sincerely appreciate any help in patching this self-inflicted wound.

---

### Post by HiImTye on 2013-01-27
have you tried using the uninstall script? there is usually one included for each of the packages you compile. I'd check those folders for one

otherwise, you'll need to figure out what files went where and then remove/replace them as needed.

for future reference, use checkinstall if you are going to compile, that way you know where the files are and can undo your mistakes if needed with a simple *sudo apt-get remove package*

---

### Post by PianoManEDTA on 2013-01-27
I have, yes. "make uninstall"ed everything I remembered installing. I'm guessing one of these programs installed over some system library, and, as you say, I need to replace it. I will certainly use "checkinstall" in future situations, thanks for the tip, very useful!

What I attempted was, after uninstalling everything, using apt-get to install the package I was originally after, hoping that it would re-make the broken parts of the system. No luck. Any suggestions for how I comb through folders for the missing/broken file(s)? Thanks!

---

### Post by HiImTye on 2013-01-27
you could try reinstalling everything. it will take a while, but it should at least fix everything. note: you will lose any changes that you made to system files.
```

sudo apt-get install aptitude
while read -r _ p1 p2 _; do
if [ "$p2" = "-" ]; then
 sudo apt-get install --reinstall $p1
else
 sudo apt-get install --reinstall $p2
fi
done < <(aptitude search ~i)

```

edit: add the --reinstall switch, otherwise it won't do anything ;)

---

### Post by tgalati4 on 2013-01-27
Another method, but this is unbelieveably tedious, is to check the files for dates in /usr/bin and /usr/lib.  Any files changed today have been messed with and are possible candidates for repair.

When you built the original program, it should have a directory structure.  Examine that structure and print out the list of files generated.  The "make install" simply copies those binaries and libraries to their correct locations in the file system.

Do you have a link for the package that you tried to build?

---

### Post by PianoManEDTA on 2013-01-27
Thank you both for your help, I've not yet tried re-installing everything; I'll let that run while I sleep. I did look at the recently modified binaries, but the list was 10+ long, and I'd rather not chase each one down (tedious, as you said).

As far as specific packages, I was really after ibus-pinyin. This required GTK, which required Glib, Pango, and ATK, some of which required Cairo, which needed freetype, which, if I recall correctly, needed gettext, which certainly wouldn't run without flex or bison or both. There are many I'm forgetting. As I said, I followed the rabbit hole too deep, and have paid gravely for it.

---


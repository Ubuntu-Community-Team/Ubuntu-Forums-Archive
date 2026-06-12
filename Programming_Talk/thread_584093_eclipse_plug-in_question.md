---
title: "eclipse plug-in question"
date: 2007-10-20
forum: Programming Talk
---

### Post by jack handy on 2007-10-20
hey guys,

i saw this screenshot on one of the blogs about gutsy, and i was wondering if anyone knew what plug-in or add-on is being used in eclipse to have the gui wysiwyg stuff

[IMG]http://img86.imageshack.us/img86/723/1016eclipsegui550x413vk5.jpg[/IMG]

thank you in advance

---

### Post by tenmillionmilesaway on 2007-10-21
Its the eclipse visual editor.  [http://www.eclipse.org/vep/WebContent/main.php](http://www.eclipse.org/vep/WebContent/main.php)

Richard

---

### Post by jack handy on 2007-10-21
> **tenmillionmilesaway said:**
> Its the eclipse visual editor.  [http://www.eclipse.org/vep/WebContent/main.php](http://www.eclipse.org/vep/WebContent/main.php)

Richard

thanks!

now, my ubuntu newbieness will come out.  with windows, we just copied and pasted the stuff from the zip file into the respective folders..  

is it the same idea under ubuntu?  if so, where is the source folder?

---

### Post by tenmillionmilesaway on 2007-10-21
The easiest way to install is from eclipses update manager.  This can be found under on one of the menus (second to last one i think) i don't have eclipse running yet cos I just did a fresh install of gutsy.

[http://help.eclipse.org/help33/index.jsp](http://help.eclipse.org/help33/index.jsp)

Richard

Edit: what version of eclipse is it? 3.2 or 3.3?

---

### Post by jack handy on 2007-10-21
3.2.2

cant seem to get it working.. :(  

and now i think i've gone and messed something up..

---

### Post by jack handy on 2007-10-21
[IMG]http://img339.imageshack.us/img339/467/screenshotsa1.png[/IMG]

---

### Post by jack handy on 2007-10-21
i then wanted to do a fresh install of eclipse to start over from scratch, but it seems that ubuntu caches the entire installation.  any way to really start from scratch?

---

### Post by tenmillionmilesaway on 2007-10-21
Are you using the sun java version of Java?  java -version will tell you this.  If not ```
sudo apt-get install sun-javaX-jdk
``` and then ```
sudo upadte-alternatives --config java
```  Replace X with desired version number.

I personally don't bother with the ubuntu eclipse and use the latest version from eclipse.org running out of my home directory.

If you go into synaptic you can force it to delete completely any package, do that with eclipse and it *should* get rid of it.

---

### Post by jack handy on 2007-10-21
alright, thanks.  i've completely removed the eclipse installation..  i'll give it one more shot with the ubuntu install..  then if that still doesnt work, i'll just go nuts

thanks for all the help so far, i really appreciate it

---


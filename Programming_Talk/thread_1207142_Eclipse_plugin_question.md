---
title: "Eclipse plugin question"
date: 2009-07-07
forum: Programming Talk
---

### Post by Mirge on 2009-07-07
Is it possible to extract a .jar file, edit some plain-text files (.tpl)... and then re-jar them and make it work with Eclipse? Plugin in question is [http://pdt.plugins.e-surf.pl/updates/features/pl.esurf.php.source_1.0.0.jar](http://pdt.plugins.e-surf.pl/updates/features/pl.esurf.php.source_1.0.0.jar)

---

### Post by myrtle1908 on 2009-07-08
I don't see why not.  After all a JAR file is basically a ZIP archive. So just go ahead and explode it like you would a zip file, make your changes then re-zip and rename back to .jar.

BTW.  The JAR you linked to contained no *.tpl files.

---

### Post by Mirge on 2009-07-08
> **myrtle1908 said:**
> I don't see why not.  After all a JAR file is basically a ZIP archive. So just go ahead and explode it like you would a zip file, make your changes then re-zip and rename back to .jar.

BTW.  The JAR you linked to contained no *.tpl files.

Tried that, and when I moved the .jar into the eclipse plugins directory, eclipse refuses to load... it spits out some error that just flashes too fast to read. Nothing on console either...

And you're right.. it wasn't in that .jar file... I had to install it first, and then get the .jar from my plugins/ directory... I've attached the .jar file, renamed to .zip...

---

### Post by Mirge on 2009-07-08
Thanks Myrtle! I got it :).

I just renamed to .zip, unzipped... edited the templates (buried deep down in several directories under bin/)... re-zipped... renamed back to a .jar..... backed up original, pasted my modified version over. Restarted Eclipse. VOILA!!

Last time I was trying to use jar -cf blahblah... I had never really messed with java before, but that's what I was able to gather by google'ing around. Directory structure was probably messed up before or something simple. Anyway, it works now and you just saved me $399 (zend studio 7)... pdt 2.1.0 now does everything I used ZS 7 for :).

Cheers!

---

### Post by myrtle1908 on 2009-07-08
Strange.  I assume the plugin works if you don't edit those tpl files?  Perhaps your editing of the JAR has somehow invalidated it?  I often open JAR files as ZIPs to inspect them but not sure if I've ever edited and re-zipped as I suggested above.

Perhaps you should use the Java jar program to re-create rather than re-zip/rename.

Edit: Ah, seems like you got it sorted.

---

### Post by Mirge on 2009-07-08
See above :KS

---

### Post by jespdj on 2009-07-08
So what exactly did you change, something in the PHP development tools? If it's something that could be useful to other people, you might want to contact the developers of the Eclipse PHP development tools and tell them about it, and they might add your change to the official version.

---

### Post by Mirge on 2009-07-08
No I changed the "PHP Source" plugin templates. It was strictly PHP5, I needed to modify the templates to make it PHP4 compatible because a lengthy project I'm working on for a client right now uses PHP4.

I contacted the plugin authors before I tried to edit it the first time, and they said they "might" get around to it in the next few months. I needed a solution much quicker..

---


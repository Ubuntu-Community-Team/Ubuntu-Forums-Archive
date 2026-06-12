---
title: "custom syntax in gedit"
date: 2007-02-23
forum: Programming Talk
---

### Post by kippertoffee on 2007-02-23
Hello, 

I'm using gedit as my matlab editor, as i can have matlab loaded in the shell at the bottom - nice. Gedit also has syntax highlighting for Octave files, which is similar enough to matlab to be fine, but Gedit interpretes my .m files a C, not octave code. A

Does anyone know how i can change Gedit's behaviour and make it see .m files as octave code?

Thanks a lot, pete.

---

### Post by xtacocorex on 2007-02-23
Here is a page that has stuff for Scilab, which is similar to Matlab.
[http://www.scilab.org/contrib/index_contrib.php?page=listdyn.php&order=alpha](http://www.scilab.org/contrib/index_contrib.php?page=listdyn.php&order=alpha)
It's listed alphabetically and there is a syntax file for Scilab in there (under G), you may or may not have to modify it.

I haven't used thi, but hope it helps.

---

### Post by predaeus on 2007-04-04
Ok, I finally found a work arround that could be improved upon:


Gnome uses mime types defined in /usr/share/mime/packages/freedesktop.org.xml.
If you open that file you will see that *.m is also recognized as Objective-C files (look at the end of <mime-type type="text/x-objcsrc">).
To fix this you can just comment the whole Objective-C section with the XML "<!-- " and  "-->" tags.

Like this
```

<!--  <mime-type type="text/x-objcsrc">
    <sub-class-of type="text/x-csrc"/>
    <comment>Objective-C source code</comment>
    <comment xml:lang="bg">&#1048;&#1079;&#1093;&#1086;&#1076;&#1077;&#1085; &#1082;&#1086;&#1076; &#1085;&#1072; Objective C</comment>
    <comment xml:lang="cs">Zdrojový kód v Objective-C</comment>
    <comment xml:lang="da">Objektiv C-kildekode</comment>
    <comment xml:lang="de">Objective-C-Quelltext</comment>
    <comment xml:lang="el">&#960;&#951;&#947;&#945;&#943;&#959;&#962; &#954;&#974;&#948;&#953;&#954;&#945;&#962; Objective-C</comment>
    <comment xml:lang="eo">fontkodo en Objective-C</comment>
    <comment xml:lang="es">Código fuente en Objective-C</comment>
    <comment xml:lang="eu">Objective-C iturburu-kodea</comment>
    <comment xml:lang="fi">Objective-C-lähdekoodi</comment>
    <comment xml:lang="fr">code source Objective-C</comment>
    <comment xml:lang="hu">Objective-C forráskód</comment>
    <comment xml:lang="it">Codice sorgente Objective-C</comment>
    <comment xml:lang="ja">Objective-C &#12477;&#12540;&#12473;&#12467;&#12540;&#12489;</comment>
    <comment xml:lang="ko">Objective-C &#49548;&#49828; &#53076;&#46300;</comment>
    <comment xml:lang="lt">Objective-C pradinis kodas</comment>
    <comment xml:lang="ms">Kod sumber Objective-C</comment>
    <comment xml:lang="nb">Objective-C-kildekode</comment>
    <comment xml:lang="nl">Objective-C-broncode</comment>
    <comment xml:lang="nn">Objective-C-kjeldekode</comment>
    <comment xml:lang="pl">Kod &#378;ród&#322;owy w Obiektowym C</comment>
    <comment xml:lang="pt">código fonte Objective-C</comment>
    <comment xml:lang="pt_BR">Código fonte Objective-C</comment>
    <comment xml:lang="ru">&#1080;&#1089;&#1093;&#1086;&#1076;&#1085;&#1099;&#1081; &#1082;&#1086;&#1076; Objective-C </comment>
    <comment xml:lang="sq">Kod burues C objekt</comment>
    <comment xml:lang="sr">&#1054;&#1073;&#1112;&#1077;&#1082;&#1090;&#1085;&#1080;-C &#1080;&#1079;&#1074;&#1086;&#1088;&#1085;&#1080; &#1082;&#1086;&#770;&#1076;</comment>
    <comment xml:lang="sv">Objective-C-källkod</comment>
    <comment xml:lang="uk">&#1042;&#1080;&#1093;&#1110;&#1076;&#1085;&#1080;&#1081; &#1082;&#1086;&#1076; &#1085;&#1072; &#1084;&#1086;&#1074;&#1110; Objective-C</comment>
    <comment xml:lang="vi">Mã ngu&#7891;n Objective-C</comment>
    <comment xml:lang="zh_CN">Objective-C &#28304;&#20195;&#30721;</comment>
    <comment xml:lang="zh_TW">Objective-C &#28304;&#20195;&#30908;</comment>
    <magic priority="30">
      <match value="#import" type="string" offset="0"/>
    </magic>
    <glob pattern="*.m"/>
  </mime-type>-->

```

Right after this section is the text/x-matlab section.

Now to make gnome recognize the new settings, run 
```

sudo update-mime-database /usr/share/mime

```

Verify by typing
```

gnomevfs-info matlabfile.m

```
it should show
```

...
MIME type         : text/x-matlab
...

```

This should cause gedit to highlight .m files as matlab files.

Thanks to Juhaz in the freenode ##gnome channel for pointing out the relevant file.

---

### Post by jehosephat on 2007-09-25
Actually, I just tried the above method, but simply switched the mime-type block for matlab so it was ahead of the one for objective c ... this worked for me - gedit  fired right up with octave highlighting - and maybe it avoids future problems with something else that needs to recognize .m files as obj c?

---

### Post by kolesarm on 2008-04-13
> **jehosephat said:**
> Actually, I just tried the above method, but simply switched the mime-type block for matlab so it was ahead of the one for objective c ... this worked for me - gedit  fired right up with octave highlighting - and maybe it avoids future problems with something else that needs to recognize .m files as obj c?

Neat!

---

### Post by Endolith on 2008-09-08
Will this be overwritten by future updates?  Is there a more user-friendly way to modify it?

---

### Post by john.m.lang on 2009-01-28
> **kippertoffee said:**
> I'm using gedit as my matlab editor, as i can have matlab loaded in the shell at the bottom - nice. 

May I ask how you do that?  I'd like to set gedit up as my MatLab editor too.

I've tried playing around with the external commands plugin, unfortunately my knowledge of shell scripting is fairly small and I can't seem to find a command that works.

Any help would be appreciated.

Thanks,

~John

---

### Post by nitro_n2o on 2009-01-28
> **john.m.lang said:**
> May I ask how you do that?  I'd like to set gedit up as my MatLab editor too.

I've tried playing around with the external commands plugin, unfortunately my knowledge of shell scripting is fairly small and I can't seem to find a command that works.

Any help would be appreciated.

Thanks,

~John
I think that he means a matlab session is started in the terminal with the command matlab -nojvm (or matlab -nodesktop) then any editor could be used to edit the *.m file 

as for syntax in gedit, this might be helpful [http://blogs.ethz.ch/ubuntu/](http://blogs.ethz.ch/ubuntu/)

finally, use gvim.. gvim can give you more options

---

### Post by Tibuda on 2009-01-29
Have you tried the Octave syntax?

---

### Post by john.m.lang on 2009-01-29
I'm sorry for confusing the issue here.  I probably should have started a new thread.

I am not having trouble with syntax highlighting, gedit is correctly identifying my *.m files as Octave and using the correct syntax highlighting.

My post was regarding this quote from the original poster:

> **kippertoffee said:**
> I'm using gedit as my matlab editor, as i can have matlab loaded in the shell at the bottom - nice.

I would like to load matlab in the console on the bottom pane of gedit.  I assumed this was using the external tools plugin, but I haven't written a command that will work.

My question is: **How can I load matlab in the shell in the bottom pane of gedit?**

Thanks,

~John

---

### Post by john.m.lang on 2009-02-19
I finally got gedit working with Matlab the way I wanted.  In case anyone else was curious this is the external tool I created.  It will display the output of your m-file in the bottom pane.

```
#!/bin/bash

matlab -nojvm -nosplash -r ${GEDIT_CURRENT_DOCUMENT_NAME%.m}
```

Input: Nothing.
Output: Display in bottom pane.
Applicability:  All documents except untitled ones.

---

### Post by hellsdottir on 2009-08-05
This breaks more for me in 9.04. It seems that gedit does not regard the mime-types. I removed the Objective-C type from my xml definitions, updated, started up gedit, made a new .m file, and bang... it thought it was Objective-C.

What I did was remove the Objective-C highlighting option from gedit. If it doesn't have it, it can't use it.

from:
[https://help.ubuntu.com/community/gedit#Syntax%20Highlighting](https://help.ubuntu.com/community/gedit#Syntax%20Highlighting)
> 
The .lang file for a specific programing language is located in the /usr/share/gtksourceview-2.0/language-specs/ folder.

So, I moved the objc.lang file to a new name within the folder without the.lang extension and restarted gedit. Now I have no highlighting problems because it doesn't have the option to highlight as Objective-C and it matches up matlab with octave highlighting just fine.

N.B.: I tried making a new matlab.lang definition first... no dice. It still hung on to Objective-C like a limpet.

---

### Post by fcastillo on 2009-12-01
Thanks so much for posting this!!! I had the same problem as you did in Ubuntu 9.10, and by removing the objc.lang everything works fine now... THANKS!!!

> **hellsdottir said:**
> This breaks more for me in 9.04. It seems that gedit does not regard the mime-types. I removed the Objective-C type from my xml definitions, updated, started up gedit, made a new .m file, and bang... it thought it was Objective-C.

What I did was remove the Objective-C highlighting option from gedit. If it doesn't have it, it can't use it.

from:
[https://help.ubuntu.com/community/gedit#Syntax%20Highlighting](https://help.ubuntu.com/community/gedit#Syntax%20Highlighting)


So, I moved the objc.lang file to a new name within the folder without the.lang extension and restarted gedit. Now I have no highlighting problems because it doesn't have the option to highlight as Objective-C and it matches up matlab with octave highlighting just fine.

N.B.: I tried making a new matlab.lang definition first... no dice. It still hung on to Objective-C like a limpet.

---

### Post by ed.b.ak on 2010-01-16
> **kippertoffee said:**
> Hello, 

I'm using gedit as my matlab editor, as i can have matlab loaded in the shell at the bottom - nice. Gedit also has syntax highlighting for Octave files, which is similar enough to matlab to be fine, but Gedit interpretes my .m files a C, not octave code. A

Does anyone know how i can change Gedit's behaviour and make it see .m files as octave code?

Thanks a lot, pete.
In karmic (9.10) the way gedit gets the highlight mode from the file extension seems to have changed.

I did this to get files *.m to automatically get the octave highlighting mode:

cd /usr/share/gtksourceview-2.0/language-specs
sudo mv objc.lang objc.lang.cant_find

This removed the Objective-C highlight mode entirely, and Octave is next alphabetically.  At least I think that's how it worked.

---

### Post by Endolith on 2010-01-16
[https://bugs.launchpad.net/ubuntu/+source/gtksourceview2/+bug/418199](https://bugs.launchpad.net/ubuntu/+source/gtksourceview2/+bug/418199)

---


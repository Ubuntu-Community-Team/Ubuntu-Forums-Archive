---
title: "A tiny problem:can't open tex file with texmaker from nautilus"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by zhangxi1982 on 2008-04-30
I am trying to work with latex, and I choose to install texmaker as the latex editor. However, I have a problem to open tex file with texmaker from nautilus. Everytime I double click the foo.tex, the texmaker just run without opening the file. 

the texmaker.desktop shows
```

cat /usr/share/applications/texmaker.desktop
[Desktop Entry]
Version=0.9.4
Name=Texmaker
GenericName=LaTeX Editor
GenericName[fr]=Editeur LaTeX
Comment=LaTeX Editor
Comment[fr]=Editeur LaTeX
Exec=texmaker
Icon=texmaker
MimeType=text/x-tex;
Terminal=false
Type=Application
Categories=Utility;TextEditor;Publishing;

```

and I tried to change the Exec to 
```
Exec=texmaker %f
```
but it didn't help.

Of course I can open the tex file in the texmaker program, or just type 
```
texmaker foo.tex
```
in the terminal.
But still, I am curious how to fix this tiny problem.

---

### Post by novalja on 2008-11-22
Hello! 
I have the same problem on Windows Vista, so I think its not only Ubuntu problem. In Ubuntu HH I have no problems with Texmaker...

> **zhangxi1982 said:**
> I am trying to work with latex, and I choose to install texmaker as the latex editor. However, I have a problem to open tex file with texmaker from nautilus. Everytime I double click the foo.tex, the texmaker just run without opening the file. 

the texmaker.desktop shows
```

cat /usr/share/applications/texmaker.desktop
[Desktop Entry]
Version=0.9.4
Name=Texmaker
GenericName=LaTeX Editor
GenericName[fr]=Editeur LaTeX
Comment=LaTeX Editor
Comment[fr]=Editeur LaTeX
Exec=texmaker
Icon=texmaker
MimeType=text/x-tex;
Terminal=false
Type=Application
Categories=Utility;TextEditor;Publishing;

```

and I tried to change the Exec to 
```
Exec=texmaker %f
```
but it didn't help.

Of course I can open the tex file in the texmaker program, or just type 
```
texmaker foo.tex
```
in the terminal.
But still, I am curious how to fix this tiny problem.

---

### Post by silbar on 2009-05-07
> **zhangxi1982 said:**
> I am trying to work with latex, and I choose to install texmaker as the latex editor. However, I have a problem to open tex file with texmaker from nautilus. Everytime I double click the foo.tex, the texmaker just runs without opening the file. 

I have the same problem (but didn't use to).  Except that I don't even see it start up texmaker.
In contrast with Zhangxi's texmaker.desktop
```

cat /usr/share/applications/texmaker.desktop
[Desktop Entry]
Version=0.9.4
Name=Texmaker
GenericName=LaTeX Editor
GenericName[fr]=Editeur LaTeX
Comment=LaTeX Editor
Comment[fr]=Editeur LaTeX
Exec=texmaker
Icon=texmaker
MimeType=text/x-tex;
Terminal=false
Type=Application
Categories=Utility;TextEditor;Publishing;

```

I have 
```

silbar@Lynx:/usr/share/applications$ cat texmaker.desktop 
[Desktop Entry]
Categories=Application;Office;Publishing;X-SuSE-Core-Office;X-Mandriva-Office-Publishing;Qt;X-Misc;
Comment=
Comment[fr]=
DocPath=
Encoding=UTF-8
Exec=texmaker
GenericName=LaTeX Editor
GenericName[fr]=Editeur LaTeX
Icon=texmaker
MimeType=text/x-tex
Name=Texmaker
Name[fr]=Texmaker
Path=
StartupNotify=false
Terminal=false
Type=Application

```

Is it significant that neither of us has the Path set?

> **zhangxi1982 said:**
> 
Of course I can open the tex file in the texmaker program, or just type 
'texmaker foo.tex' in the terminal.
But still, I am curious how to fix this tiny problem.

Also true for me.  Unlike novalja, I _do_ have this problem (running Gnome in Hardy Heron 8.0.4).

   Dick Silbar

---


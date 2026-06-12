---
title: "Tulong sa pag-compile"
date: 2008-11-01
forum: Philippine Team
---

### Post by gimmejimmy on 2008-11-01
Nag-download ako ng source ng gthumb kasi may gusto akong baguhin sa software.  So nung nabago ko na at nasave sinubukan ko mag-compile.  First two steps "sudo ./configure" at "sudo make" ok naman.  Kaya lang pagdating sa "sudo checkinstall -D" error na.

> chmod 644 /usr/local/lib/libgthumb.a
chmod: changing permissions of `/usr/local/lib/libgthumb.a': No such file or directory
make[3]: *** [install-libgthumbLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/moral/gthumb-2.10.8/libgthumb'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/moral/gthumb-2.10.8/libgthumb'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/moral/gthumb-2.10.8/libgthumb'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Paano po ba ayusin ito?  Pwede ko ba irun lang yung binary kahit hindi nainstall?

---

### Post by loell on 2008-11-01
aba, kay madaling araw nag-kokompile? :D

paano mo pala kinompile? unang sulyap, parang permission ang problema.

---

### Post by dodimar on 2008-11-01
Geeks don't sleep??? 
:lolflag:
:guitar:

---

### Post by gimmejimmy on 2008-11-02
Hehe, ganoon talaga.  Pag hindi gumagana parang ayaw mong tigilan.

> paano mo pala kinompile? unang sulyap, parang permission ang problema. 

Hindi ko masyadong naintindihan yung tanong sir.  Una "sudo ./configure" tapos "sudo make" tapos "sudo checkinstall".  Sinubukan ko yung "make install" walang error pero pag-type ng "gthumb" hindi raw niya mahanap yung "libgthumb.so".  First time ko lang s pag-install from source.

Chineck ko pala yung "libgthumb.a" na sinasabi niya.  Pag ginamit yung "locate libgthumb.a" nasa /usr/local/lib at /opt/lib daw.  Pero pag nag "ls" sa mga directory na iyon wala naman.  Kahit sa file browser wala.

---

### Post by loell on 2008-11-02
usually it's

./configure
make
sudo make install


huwag mo munang gamitin ang checkisntall.

---

### Post by gimmejimmy on 2008-11-02
Pag "make install" naman, tapos run program from the menu walang nangyayari.  Pag type ng "gthumb" sa terminal kulang daw yung libraries.

---

### Post by loell on 2008-11-02
ang gthumb ay may ganitong dependencies, na-install mo ba ang mga ito?

No package 'glib-2.0' found
No package 'gthread-2.0' found
No package 'gmodule-2.0' found
No package 'gtk+-2.0' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libgnomecanvas-2.0' found
No package 'libbonobo-2.0' found
No package 'libbonoboui-2.0' found
No package 'bonobo-activation-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'libexif' found
No package 'libxml-2.0' found
No package 'libglade-2.0' found

---

### Post by gimmejimmy on 2008-11-02
Iba pa po ba 'yan sa "sudo apt-get build-dep gthumb"?

Sir, kung hindi naman masyadong abala, pwede po ba niyo itest yung pag-compile?  Para maconfirm lang na may ginagawa talaga akong mali?

---

### Post by loell on 2008-11-02
oo nga, dapat yung **build dep** ay nag install na nung mga dependencies na yon.

attach mo lang dito yung packed source. susubukan ko mamayang gabi.

matanong lang, ano ba yung binago mo? para saan sana?

---

### Post by rjmdomingo2003 on 2008-11-02
> **gimmejimmy said:**
> Pag "make install" naman, tapos run program from the menu walang nangyayari.  Pag type ng "gthumb" sa terminal kulang daw yung libraries.
Subukan mo
```
sudo make install
```
not
```
make install
```

Baka di rin latest yung checkinstall mo.

---

### Post by gimmejimmy on 2008-11-02
Ok na po sa "sudo checkinstall".  Ang ginawa ko manual ko na lang kinopya yung hinahanap niyang files.  Successful daw.  Pero pag type ng "gthumb" may error na "error loading library: libgthumb.so" di raw niya mahanap yung file.  Saan ba dapat nakalagay?  Nakita ko na siya doon sa source archive.

@loell
Sa ngayon sir wala pa akong binabago.  Pero ang gusto ko mabago yung default margins, layout at paper size.  Tapos gusto ko rin baguhin yung available na layouts at paper size.  Hehe mahigit 3MB pala, hindi pwede i-attach.

@rjm
Yup, sudo make install po.  Paano ba icheck yung checkinstall?  Pero this weekend ko lang ininstall yun.

---

### Post by rjmdomingo2003 on 2008-11-02
> **gimmejimmy said:**
> @rjm
Yup, sudo make install po.  Paano ba icheck yung checkinstall?  Pero this weekend ko lang ininstall yun.
Install mo na lang yung .deb file from here: [http://www.asic-linux.com.mx/~izto/checkinstall/download.php](http://www.asic-linux.com.mx/~izto/checkinstall/download.php)

---

### Post by gimmejimmy on 2008-11-06
Ok na.  Kailangan lang pala mag "sudo ldconfig" after installation (either "sudo make install" or "sudo checkinstall").  Salamat sa lahat ng nag-post.

---


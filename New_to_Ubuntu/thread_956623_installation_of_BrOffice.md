---
title: "installation of BrOffice"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by antalves on 2008-10-23
[FONT="Georgia"]I'm trying to install BrOffice 3.0. I can not to surpass the level shown in my anex. Can someone give me some help??[/FONT]

---

### Post by Victormd on 2008-10-23
Your command is wrong, you should use:
```
sudo dpkg -i broffice.org3.0-debian-menus_3.0-9354_all.deb
```
(no seu comando original tem um espaço no "- i" quando deveria ser "-i")
Since installing Oo3 has so many debs, you can also use:
```
sudo dpkg -i *.deb
```
(não sei se o forum acha ruim de escrever em outra lingua, por isso estou misturando... hehehe)

---

### Post by antalves on 2008-10-24
fiz o recomendado, o resultado está no anexo. Continuo sem saida!
I did what you said, see anex please. No way out!:confused:

---

### Post by Victormd on 2008-10-24
Let's try to narrow down or eliminate possible problems...
What version of openoffice do you currently have installed? Is it the portuguese version?

Where did you download your DEB files from (or did you convert from RPM using alien)? The latest version in portuguese is 2.4.1, see [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US).

If you converted from RPM, that might be the problem and you should download and use the debs available [here]("http://download.openoffice.org/other.html#en-US"). 

An alternative is to remove the existing openoffice before installing the updated version (this will eliminate any package conflicts), but I would use this as a last resort.

---

### Post by antalves on 2008-10-24
I got from [URL="http://http://www.broffice.org/instrucoes_basicas_de_instalacao#instalacaolinux"]
there is the release 3.0 I got DEB files. Prior, I uninstalled Open Oficce english version:(

---

### Post by Victormd on 2008-10-24
Try the version from the official openoffice download website (previous link).

---

### Post by Victormd on 2008-10-25
E aí, tentou? Deu certo?

---


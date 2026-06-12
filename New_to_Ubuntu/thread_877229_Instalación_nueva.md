---
title: "Instalación nueva"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by emscolnik on 2008-08-01
Tengo una computadora nueva basada en un microprocesador AMD 5200X2 y con un disco de 250 Gb. El disco aún no tiene particiones de ningún tipo.Sistemas Operativos a utilizar  : Windows XP Professional y Ubuntu 8.04 LTS.
Preguntas :
1.-¿ debo crear particiones con sistema de archivos FAT32 o
   NTFS ? 
2.-Tamaños recomendados de las particiones.
3.-¿ Primero instalo Windows y luego Ubuntu ?
Por supuesto que hay varios documentos sobre el tema pero no
está claro a qué versión de Ubuntu se refieren. ¿ La nueva es compatible con NTFS ?
Muchas gracias

---

### Post by LowSky on 2008-08-01
Mi espanol horrible: hope this helps

1. FAT32 (trabajo bueno)
2. con ubuntu: / (root), /home, swap
3. Si primero instalo Windows y luego ubuntu

Si Ubuntu leído NTFS

---

### Post by Ryadt on 2008-08-01
Hi...This is an English speaking forum..You wont have much luck asking question in a different language. There are spanish ubuntu forums.
Try this link
[http://www.ubuntu.com/support/community/webforums](http://www.ubuntu.com/support/community/webforums)
:)

---

### Post by Ryadt on 2008-08-01
> **LowSky said:**
> Mi espanol horrible: hope this helps

1. FAT32 (trabajo bueno)
2. con ubuntu: / (root), /home, swap
3. Si primero instalo Windows y luego ubuntu

And am proved wrong again...:lolflag:

---

### Post by jualin on 2008-08-01
1. FAT32 era el antiguo sistema de archivos de Windows para discos duros chicos. NTFS es para los discos mas grandes (creo que mas de 10 GB). Windows usaria una particion NTFS y Ubuntu usaria 2 particiones una particion principal EXT3 (Sistema de Archivos de Linux) y una particion SWAP (Algo similar al cache virtual de Windows lo cual debe ser el doble del tamano del RAM).
2. El tamano tu lo decides. Tambien puedes hacer una particion para tus archivos personales (musica, fotos, documentos) en Linux (Particion "home")
3. Debes instalar primero Windows y despues Ubuntu. Cuando instales Windows crea una particion NTFS y deja el resto de espacio sin particion (Ubuntu se encargara de hacer la otra particion).

---

### Post by jualin on 2008-08-01
> **Ryadt said:**
> And am proved wrong again...:lolflag:

And one more here. :lol:

---

### Post by Ryadt on 2008-08-01
> **jualin said:**
> And one more here. :lol:

Keep rubbing it...:lolflag:

---

### Post by LowSky on 2008-08-01
> **Ryadt said:**
> And am proved wrong again...:lolflag:

el español es la dos lengua de los E.E.U.U. Ayudan a saber poco de vez en cuando

Babelfish ayuda también

---

### Post by jualin on 2008-08-01
Si tienes alguna duda, dejamelo saber. Aunque este es un foro en ingles hay mucha gente que habla muchos idiomas. Tambien tenemos los foros locales (LoCos) para diferentes regiones del mundo. Yo vivo en Miami asi que se Espanol e Ingles. Suerte!

---

### Post by overdrank on 2008-08-01
Hi and from the COC
# Please strive to communicate with other users as effectively as possible:

    * Please try to write your posts in English unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries that visit here and English is the common language of these forums.

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

---

### Post by bobnutfield on 2008-08-01
> **emscolnik said:**
> Tengo una computadora nueva basada en un microprocesador AMD 5200X2 y con un disco de 250 Gb. El disco aún no tiene particiones de ningún tipo.Sistemas Operativos a utilizar  : Windows XP Professional y Ubuntu 8.04 LTS.
Preguntas :
1.-¿ debo crear particiones con sistema de archivos FAT32 o
   NTFS ? 
2.-Tamaños recomendados de las particiones.
3.-¿ Primero instalo Windows y luego Ubuntu ?
Por supuesto que hay varios documentos sobre el tema pero no
está claro a qué versión de Ubuntu se refieren. ¿ La nueva es compatible con NTFS ?
Muchas gracias

1. Linux tiene ext3 o ext2, yo prefiero ext3.  FAT32 o NTFS esta solo para Windows.

2.  Hace uno particione para /home, y uno particione para /

3. Instale Windows premiero, y Linux segundo.  El Grub "bootloader" conocere' y permite selecto el OS quierre.

Espero que entiende y que eso ayudarle

---


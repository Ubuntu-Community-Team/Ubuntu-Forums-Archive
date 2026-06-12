---
title: "[SOLVED] Need help with a bash script"
date: 2008-03-04
forum: Programming Talk
---

### Post by Tuxon86 on 2008-03-04
Hi!

I need a bit of help with my project. I don't even know if it's possible to do this with bash.

I want to write a script that would do the following:


[LIST=1]
[*]Read a file that has a list of file name in it.
[*]For each of those filename run my application with the filename as a     parameter ex.: MyProg File_1
[*]Do this until the end of the file containing the list of filename.
[/LIST]

If somebody could help me with this I would greatly appreciate it since for the moment I have to cut and paste then modify the line calling my application to fit the list of file to be process and mistake can be made.

Thank you.

---

### Post by Martin Witte on 2008-03-04
these links should give you some food for thuoght: [http://www.google.com/search?q=bash+read+file+line+by+line](http://www.google.com/search?q=bash+read+file+line+by+line)

---

### Post by WW on 2008-03-04
You can do it with a one-liner.  Suppose the file containing the file names is called **filenames**.  Try this:
> 
$ xargs -a filenames -L 1 MyProg

To see what commands are executed, add the **-t** option.

---

### Post by Tuxon86 on 2008-03-04
Thanks guys.

With your help I was able to finish my script. :KS

Here is the result.

```
#!/bin/bash

#**************************************************************************************
#  BatchEncode v.1.0
#
#  par: Alain Ménard
#   le: 4, Mars 2008
#
#  www.epsilon-3.info
#
#  Ce script est disponible pour toutes les personnes désirant l'utiliser ou le modifier.
#  J'apprécierai en échange que vous me fesiez parvenir vos commentaires ou modification afin que je puisse les inclures dans la version en ligne.
#  
#  Ce script sert à encoder des fichier vidéo au format Xvid. Il a la particuliarité de traiter en lot l'ensemble des fichier se trouvant dans un répertoire.
#  Il ne gère pas pour le moment le cas des sous-répertoires. Vous devez donc mettre tout les fichiers au même niveau. Il faut aussi éviter de mettre des fichiers 
#  autre que des vidéos car le script va se terminer avec une erreur (il n'y a pas de validation du type de fichier pour le moment).
#
#  Vous devez définir le répertoire source et celui de sortie auprès des variables SCRDIR et DONEDIR respectivement.
#
#  Pour le "bitrate" vidéo et audio utiliser les variables VIDEOBR et AUDIOBR. L'udio s'encode en MP3 et en "constant bit rate" pour des raison de performances et
#  de compatibilité.
#
#  Si vous désirez faire sauté les barre noire de la source afin d'ammélioré la compressibilité du fichier et la qualité finale il suffit d'exécuter la commande suivante
#  dans une fenètre de terminal: mplayer -vf cropdetect <fichier>
#  <fichier> = fichier source.
#  
#  Laisse le film joué quelque minute et terminé l'exécution par un <ctrl-c>
#  Prenez note des 4 nombre au bout de la ligne qui ressemble à celle-ci: [CROP] Crop area: X: 0..719  Y: 104..377  (-vf crop=720:272:0:106)
#  Inscrivez ces 4 nombre à la variable CROP (ne pas effacer ou remplacer les ":" car ils sont nécessaire).
#  Si vous ne désirez pas utiliser le "crop" vous devrez effacer les options "-vf crop=$CROP" des deux lignes de commande.
#
#  Comme ce fichier sera modifier régulièrement il est recommandé de garder une version de ce fichier dans son état initiale et de travailler avec une copie.
#

#Définition des répertoires d'entrées et sorties.
SRCDIR="/home/alain/Video/src"
DONEDIR="/home/alain/Video/done"

#Définition des paramêtre d'encodage
VIDEOBR=-1500000	#Entrez une valeur positive pour un bitrate absolue ex.:4000 pour 4mb/s ou une valeur négative si on désire une taille de fichier maximum.
AUDIOBR=192		#Bitrate de la partie audio. L'audio est encodé en CBR avec ce script mais pourrait être modifier pour du VBR si désiré.
CROP="000:000:0:000"    #Remplacer les valeurs par défaut par celles fournie par MPlayer -vf cropdetect. Si non effacer la référence dans les lignes de commande.

cd $SRCDIR
ls *.avi > dir.txt

processLine(){
	line="$@"
}

FILE="dir.txt"
exec 3<&0
exec 0<$FILE
while read line
do
      processLine $line 
      nice -n 1 mencoder $line -vf crop=$CROP -oac mp3lame -ovc xvid -xvidencopts pass=1:quant_type=mpeg:qpel:chroma_me:chroma_opt:hq_ac:vhq=4 -o /dev/null
      nice -n 1 mencoder $line -vf crop=$CROP -ovc xvid -xvidencopts pass=2:quant_type=mpeg:qpel:chroma_me:chroma_opt:hq_ac:vhq=4:bitrate=-1500000 -oac mp3lame -lameopts cbr:br=192 -o $DONEDIR/$line
      done
      rm -f dir.txt
      exec 0<&3
exit 0

```

---


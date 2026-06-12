---
title: "Quick question about batch renaming..."
date: 2009-04-09
forum: Programming Talk
---

### Post by Pierre-Alexandre on 2009-04-09
I have to create a script which takes 3 command line args in order to rename all .ppm files in a folder. The first arg is the name of the files. The second is the base and the third is the increment. So let's say I enter Duplq.sh Hello 1 3, the script would rename all .ppm files to Hello1.ppm, Hello4.ppm, Hello7.ppm, etc.

The script must check if a file with the new name already exists. If it does, it copies it to a temp file and brings it back on the following iteration.

This, however, doesnt work at all... It's totaly broken. And I really dont know why!

Here is the code so far:


```
#!/bin/bash
###note: Mon systeme utilise le shell Dash par défaut, c'est pour ca que j'ai du mettre #!/bin/bash au lieu de sh.
if [ $# -ne 3 ]; then
	echo "ERREUR: Ce script prend 3 arguments passés a la ligne de commande. USAGE: Duplq.sh NOM DEPART INCREMENT. Ex: Dupliq Allo 0 3"
	exit 1
elif [ ! $(echo "$2" | grep -E "^[0-9]+$") ]; then
	echo "ERREUR: $2 n'est pas un entier"
	exit 1
elif [ ! $(echo "$3" | grep -E "^[0-9]+$") ]; then
        echo "ERREUR: $3 n'est pas un entier"
        exit 1
fi
ETAPE=$2
REFAIRE=false	
for FICHIER in *.ppm
do
       NFICHIER="${1}${ETAPE}.ppm"
	if [ $REFAIRE == true ]
	then
		mv $TEMP $NFICHIER
		ETAPE=$(($ETAPE+$3))
		REFAIRE=false
	else

		if [ -e $NFICHIER ]
		then
			TEMP="${NFICHIER}.BAK"
			cp $NFICHIER $TEMP
			mv $FICHIER $NFICHIER
			REFAIRE=true
		else
			mv $FICHIER $NFICHIER
			ETAPE=$(($ETAPE+$3))
		fi
	fi
done
```

ETAPE = the current file were at.
NFICHIER = New file to be created
FICHIER = File in the for loop


Thanks!!


edit:

I must add that there is no verbrose output. Files simply disapear when I do another pass on them!

---

### Post by knattlhuber on 2009-04-09
To get more insight into what's going on, you could run your script with the bash debugging option (-x) on:

```
bash -x Duplq.sh hello 1 3
```

---

### Post by lloyd_b on 2009-04-09
Could you please explain exactly how you expect the $REFAIRE check to operate.  It appears that if, for example, "FILE3.ppm" exists, it will be backed up, and then moved back to overwrite the "FILE3.ppm" that you just created in the previous iteration.  I don't see the point.

In addition, each time this occurs, the for loop reads a new $FICHIER, which is then discarded.  So on a rerun (with the same parameters) it will be discarding every other file...

You really need to rewrite this, so that ALL of the operations required for a given $FICHIER are performed without iterating the loop:```
for FICHIER in *.ppm; do
   REFAIRE=false
   NFICHIER="${1}${ETAPE}.ppm"

   # Check to see if destination file exists
   if [ -e "$NFICHIER" ]; then
      REFAIRE=true
      TEMP="$NFICHIER.BAK"
      mv "$NFICHIER" "$TEMP"
   fi

   # Move target to destination and increment file counter
   mv "$FICHIER" "$NFICHIER"
   ETAPE=$(($ETAPE+$3))

   # If we created a backup file earlier, deal with it here
   if [ $REFAIRE == true ]; then
      mv "$TEMP" "$NFICHIER"
      REFAIRE=false
   fi
done
```

Note: I have NOT tested this code - it's just provided for illustration.  Also note that I've put quotation marks around all filename variables - this will save you if any of them happen to have spaces in the name (though spaces in filenames will also cause trouble in the "for" loop).

For future reference - you may want to include some debugging "echo" commands (for instance, 'echo "Creating Backup of $NFICHIER"').  This is helpful in sorting out what's going on with the script.  Of course, you can do the "bash -x ..." recommended by a previous poster as well.

---


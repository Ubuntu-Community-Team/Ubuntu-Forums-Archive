---
title: "Mass file rename/manipulate based on inherited directory name - help please!"
date: 2009-01-08
forum: Programming Talk
---

### Post by zorblart on 2009-01-08
Hi all,

I am wanting to write/adapt a little piece of code to clean up my media files that does the following:
-enters a directory
-renames all .avi and .nfo files according to the name of the directory they are in
-if there are two .avi files, then rename one blah-1.avi, and the other blah2.avi
-deletes everything else in the directory, preserving all .idx, .sub. and .srt files

After UTFSE, I came across [http://ubuntuforums.org/showthread.php?t=398983](http://ubuntuforums.org/showthread.php?t=398983), and have done a partial adaption to suit the above requirements.

Thus far I have the command:
find -type d | while read d; do cd "$d"; c=1; for i in *.avi; do if [ ! -f "$i" ]; then continue; fi; r="${PWD##*/}.avi"; mv -f "$i" "$r"; rm -rf Sample; ((c++)); done; cd "$OLDPWD"; done

Unfortunately I am way out of my depth, having only intermediate experience with some of the finer points the bash command line.

Any help would be appreciated.

Cheers,
zorblart

---

### Post by slavik on 2009-01-08
start with a script that does it in a single directory. then work from there. baby steps :)

---

### Post by ghostdog74 on 2009-01-08
you can try the -execdir option of gnu find command. check the man page for more info.

---

### Post by zorblart on 2009-01-09
Thanks for the replies guys.

I have settled on a rather crude appropriation of that code i mentioned earlier.

Thus:

## avi
find -type d | while read d; do cd "$d"; c=1; for i in *.avi; do if [ ! -f "$i" ]; then continue; fi; r="${PWD##*/}.avi"; mv -f "$i" "$r"; ((c++)); done; cd "$OLDPWD"; done
## nfo
find -type d | while read d; do cd "$d"; c=1; for n in *.nfo; do if [ ! -f "$n" ]; then continue; fi; r="${PWD##*/}.nfo"; mv -f "$n" "$r"; ((c++)); done; cd "$OLDPWD"; done
## sub
find -type d | while read d; do cd "$d"; c=1; for s in *.sub; do if [ ! -f "$s" ]; then continue; fi; r="${PWD##*/}.sub"; mv -f "$s" "$r"; ((c++)); done; cd "$OLDPWD"; done
## idx
find -type d | while read d; do cd "$d"; c=1; for x in *.idx; do if [ ! -f "$x" ]; then continue; fi; r="${PWD##*/}.idx"; mv -f "$x" "$r"; ((c++)); done; cd "$OLDPWD"; done
## srt
find -type d | while read d; do cd "$d"; c=1; for t in *.srt; do if [ ! -f "$t" ]; then continue; fi; r="${PWD##*/}.srt"; mv -f "$t" "$r"; ((c++)); done; cd "$OLDPWD"; done

The sticking points for me now are, directories with two .avi files, and the removal of all non avi/sub/idx/srt.

I checked out the execdir option, and it seems useful - but i will need to say something like 'all files/folders that do not have an avi/sub/idx/srt option must be deleted'.

I think this would be run after that batch of commands I have listed above. I was thinking about a for-do loop that says something similar. Would this be a good idea?

My only concerns here being the inordinate amount of time i have already spent manually renaming all the directories :) i.e. i'd like to hack up a script/set of commands rather quickly.

Thanks again.

---

### Post by zorblart on 2009-01-10
After much reading, I am thinking of an if condition that does basically 'if there are more than one of files *.avi, then append integers beginning with 1 to the end of the directory name; else proceed with standard rename'. After this portion of the script completes, I'm thinking that it is then I insert something that 'recursively delete all files not having extension X Y or Z'.

Am totally stuck as to how to do/integrate this though.

---

### Post by slavik on 2009-01-10
simple way: (syntax may be wrong)

```

if (( $(ls *.avi | wc -l) <= 2 )) then
  #standard rename;
else
  #numbered rename;
fi;

```

---

### Post by zorblart on 2009-01-11
Am now having syntax problems - arr!


```
#!/bin/bash


find -type d | while read d; do	
	cd "$d"
	 if (( $(ls ./*.avi | wc -l) <= 2 )); then

		i="$ls *.avi"
		r="${PWD##*/}.avi"
		mv -i "$i" "$r"
		((c++))
#fi
fi
done

```
 and i get 
mv: cannot stat ` *.avi': No such file or directory

for each directory
i.e. it grabs the dir list, but cannot cd into the dir - even when i cut down the script!

Any help would be cool.

---

### Post by Cracauer on 2009-01-11
You want 
i="$(ls *.avi)"

Not $ls

---


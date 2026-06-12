---
title: "Script to extract the domain names out of emails"
date: 2007-06-12
forum: Programming Talk
---

### Post by Ago12 on 2007-06-12
Hi, I'm at work right now, and I have at my right my Ubuntu lappy.

I have a list of email adresses (a few hundreds) in an html file, and they are extracted from a list in Outlook or TB, whatever, this way:

[email]name1@ltd1.com[/email]; [email]name2@ltd2.com[/email]; etc...

The ltd name are prettu elocants, since they are compagny adresses.

I would like to get a list as following:

name1 ltd1
name1 ltd2

It should be pretty easy with grep, exho and sed. I have some basis in bash, but not enough for this I think :/

If someone could help me or knows a similar script that I could modify, it would be nice to show it to me ;)

Thanks in advance :)

---

### Post by Mr. C. on 2007-06-12
You don't say if there are variations of the input, but here's a quick sed script for you:

```
sed 's/\([^@]*\)@\([^;.]*\)\.[^;]*;[ ]*/\1 \2\n/g'  
```

Test with:
```

echo 'name1@ltd1.com; name2@ltd2.com;' | sed 's/\([^@]*\)@\([^;.]*\)\.[^;]*;[ ]*/\1 \2\n/g'  
name1 ltd1.com
name2 ltd2.com

```

MrC

---

### Post by Ago12 on 2007-06-12
Finally, I did it by myself, playing around :)

The final thing is close to what you were talking about...

Here is the script (sorry for french speaking):

```
#!/bin/bash

## Script bash crÃ©Ã© par Fabien ( noir@exalead.com ; f.noir@yaho.com ). 
## Permet d'organiser une liste d'adresses emails (typiquement un copier/coller depuis Thunderbird ou Outlook).
## On part d'une liste de type:
## personne1@ndd1.com; personne2@ndd2.org; ...
## en
## personne1 ndd1
## personne2 ndd2
## Ce qui permettra ensuite d'importer cette liste dans un tableur. Ã€ noter que c'est surtout utile lorsque les contacts 
## ont des adresses professionelles (type exalead.com pour Exalead)
## La plupart des lignes de type html devraient Ãªtre supprimÃ©es, et les lignes de moins de 2 caractÃ¨res ne sont pas affichÃ©es.

## ToDo: beaucoup, le script est absoluement crado pour l'instant. Il doit exister un moyen simple pour Ã©viter la double extension
## qui n'est peut-Ãªtre pas trÃ¨s apprÃ©ciÃ© sur un OS non-Unix... Pouvoir aligner tous les noms des personnes serait un plus Ã©galement.

clear;
read -p "Quel fichier? : " fichier
touch $fichier.txt
clear
cat $fichier |cut -d ' ' -f1 | sort | sed 's/^[ \t]*//;s/[ \t]*$//' | sed 's/@/ /' |sed 's/.com;//;s/.fr;//;s/.org;//;s/.net;//;s/.gouv;//;s/.gouv.fr;//' |sed '/</,/>/d' |sed '/{/,/}/d' |sed -n '/^.\{2\}/p' >> $fichier.txt
## ,/{/,/}/
echo La liste est prÃªte dans le fichier $fichier.txt 
exit 0

```

The only thing is that you have to type the filename, wich is not very easy...

If anyone know how to make an ls in the cuurent directory and ask to choose the file, just by giving the number of the file (1, 2, 3 ...)

Anyway, I hope it will help. The script is of course under the GPL V2, or any compatible licence :)

---

### Post by ankursethi on 2007-06-12
I think passing the files as parameters is a more UNIXy way of doing it. Keep it as it is. It'll be helpful in case you have to use this script in a bigger script or with other utilities.

---

### Post by Mr. C. on 2007-06-12
Use the shell's autocomplete to list the files for you.  Start typing the name of a file, and then hit TAB once to complete the name for you.  If the name is ambiguous (eg. a, aa, aaaa), hit TAB twice and it will list the possibe completions.  Type more letters and TAB again.

You don't need to call sed | sed | sed.  Use sed -e 'expr1' -e 'expr2' -e 'expr3'.

Your sed expressions, while they may work in your current case, certainly are not generic enough to be successful in all cases.  Did my general sed expression not meet your needs?

MrC

---


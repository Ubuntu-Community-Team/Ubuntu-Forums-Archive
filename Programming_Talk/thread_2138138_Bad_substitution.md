---
title: "Bad substitution"
date: 2013-04-23
forum: Programming Talk
---

### Post by Akhryl on 2013-04-23
Hello guys, nice to meet you,

I noticed an error on one of my shell script a couple of days, and I can't definately understand this. So, here I am :

Here is the message I got when I try to execute the script

```
/var/scripts/import_declinaison.sh: 38: /var/scripts/import_declinaison.sh: Bad substitution
```

And here is the shell code (line 38 in red)

```
#!/bin/bash

#email=denis.deleval@gmail.com
email=david.foot@bside.be

#passwd=xxx
passwd=pswd

tab=Import # Onglet

admintab='Admin'$tab # Les scripts de prestashop vont chercher les onglets avec Admin devant

# urladminsite=http://localhost/test/prestashop_1.4.7.3/admin78500/ # L'url de la partie administration de prestashop
urladminsite=http://www.pepindepomme.be/administrator/ # L'url de la partie administration de prestashop

csvfile=$1 # Le nom de votre fichier csv se trouvant dans le rértoire 'import' de la partie adminxxx

# Les type de valeur pour chaque colonne de votre CSV :

# /!\ ATTENTION /!\ N'oubliez pas de bien renseigner cette partie car c'est ce qui va être utilisé pour mettre à jour la BD

typevalue='type_value[0]=id&type_value[1]=id_product&type_value[2]=options&type_value[3]=reference&type_value[4]=price&type_value[5]=quantity'
#typevalue='type_value[0]=id_product&type_value[1]=options&type_value[2]=reference&type_value[3]=price&type_value[4]=quantity'

####################### IDENTIFICATION #######################
# Identification et répétion du cookie
 wget --save-cookies=cookie.txt --post-data='email='$email'&passwd='$passwd'&Submit=submit' --keep-session-cookies -q -O login.php $urladminsite'login.php'
if [ -n "$(grep 'error' login.php)" ]
then
  error=$(grep '<li>.*</li>' login.php | sed 's/.*<li>\(.*\)<\/li>/\1/g')
  echo 'ERREUR : '$error
else
  # Si pas d'erreur premier accès partie administration
  wget --load-cookies=cookie.txt --keep-session-cookies -q -O index.php $urladminsite'index.php' # Accès partie administration
# token=$(grep 'index.php?tab='$admintab'\&token=' index.php | sed 's/.*token=\(.*\)\">'$tab'.*/\1/g')
  token=$(grep 'index.php?tab='$admintab'\&token=' index.php | sed 's/.*token=\([a-z0-9]*\)\">'$tab'.*/\1/g')
  # Extraction du token de la page index.php pour l'onglet qui nous intéresse
  [COLOR=#ff0000]**token=${token:0:32} #ok, sinon met un pseudo espace à la fin**[/COLOR]
   
fi

####################### IMPORTATION CSV #######################
# params : entity=2 : fichier déclinaisons
if [ -n "$(echo $token | grep ^[a-z0-9]*)" ]
then
  wget --load-cookies=cookie.txt --keep-session-cookies --post-data='tab='$admintab'&token='$token'&skip=0&csv='$csvfile'&entity=2&iso_lang=fr&separator=;&multiple_value_separator=,&'$typevalue'&match_ref=1&import=Import CSV data' -q -O maj.php $urladminsite'index.php'
#  echo 'TOKEN : '$token # Affichage du token répé
  echo ' ---> batch déclinaisons terminé'
else
  echo 'ERREUR : Pas de token'
fi


```

Well, I really hope to have some help please.

Thanks.

Steve.

---

### Post by Vaphell on 2013-04-23
are you sure you don't use sh to run this script?

```
$ sh
$ x=adgsfghasfhasfhasfhasf
$ echo ${x:0:10}    
**sh: Bad substitution**
$ bash
$ x=adgsfghasfhasfhasfhasf
$ echo ${x:0:10}
adgsfghasf
```

---

### Post by schragge on 2013-04-23
+1
TBH, I'm not sure bash substring expansion is needed here at all, since this
```
token=$(grep 'index.php?tab='$admintab'\&token=' index.php | sed 's/.*token=\([a-z0-9]*\)\">'$tab'.*/\1/g')
```
probably can be rewritten as
```
token=$(sed -r '/index.php\?tab='$admintab'&token=/s/.*token=([a-z0-9]{32}).*">'$tab'.*/\1/' index.php)
```
or even
```
token=$(awk -F'&token=|">'$tab '/index.php\?tab='$admintab'&token=/ {print substr($2,0,32)}' index.php)
```
(this will select the first token on the line if there are many, replace *$2* with *$(NF-1)* for it to behave more like the *sed *expression above).

---


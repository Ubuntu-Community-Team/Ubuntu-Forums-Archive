---
title: "Big problem in executing a modified script in shell"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by fouadd on 2013-05-17
Hello , 
please i have a big problem in ubuntu, the probleme didn't let me to move on in my project for 3 days :confused::confused:

the probleme is when i modify in the script which i program , the results don't change 

simple example ! 

[PHP]
#!/bin/sh

# Je définis une première fonction

ecrire_sur_une_ligne () {
  echo -n $*
}

# Je définis une deuxième fonction qui appelle la première

saluer_utilisateur () {
  ecrire_sur_une_ligne "aaaaaaaa "
  echo $USER
}


# J'appelle la deuxième fonction
saluer_utilisateur

[/PHP]

[COLOR=#ff0000]the result is aaaaaaafouad[/COLOR]

and when i modify it like this :

[PHP]

#!/bin/sh

# Je définis une première fonction

ecrire_sur_une_ligne () {
  echo -n $*
}

# Je définis une deuxième fonction qui appelle la première

saluer_utilisateur () {
  ecrire_sur_une_ligne "bbbbbbbbbb "
  echo $USER
}


# J'appelle la deuxième fonction
saluer_utilisateur
[/PHP]

and when i execute the script with ./test.sh the result don't change to [COLOR=#ff0000]bbbbbbbbbfouad [/COLOR]it still [COLOR=#ff0000]aaaaaaaafouad[/COLOR]  :(:(:(:(:(:(

by the way i use shell sh in ubuntu 12.10 and the TERMINAL that i found it default with ubuntu 

it's the first time that i see it !!!!!!!!!!! it's make me complety crazy ! 

please help meee

---

### Post by fj401971 on 2013-05-19
I just tried your script and changing the value actually works.  I would make sure that you actually saved your changes and that you actually executed the correct script that you modified.

I often just hit the up arrow and execute the old script even though I saved the modified script to a different filename.  Thus causing the same results to be produced despite having "changed" it.

---


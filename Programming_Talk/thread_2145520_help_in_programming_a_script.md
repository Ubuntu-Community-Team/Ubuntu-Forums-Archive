---
title: "help in programming a script"
date: 2013-05-15
forum: Programming Talk
---

### Post by fouadd on 2013-05-15
Hello, 
please i need a help in programming a script to complete a work that i have to do 
the idea of the script is to add a new user and ask him to fill in some information and save it in a file char.txt
i tried to program this one but it doesn't work, i don't know what's the problem 
[PHP]
#!/bin/sh
newplayer() { 
 nb=0 
 while read ligne ; do 
  affichage[$nb]=$ligne  
  nb=$nb+1 
 done < "/home/fouad/Documents/char.txt"
echo  "Fiche de personnage :  
 Nom : $affichage[0] 
 Description : $affichage[1] 
 PV Max : $affichage[2] 
 PV Courrant : $affichage[3] 
 Arme :  $affichage[4]" 
}
newplayer

[/PHP]

please can i have a help with that

---

### Post by steeldriver on 2013-05-15
What system are you programming this on? if you are using /bin/sh on an Ubuntu system then it likely invokes a **dash** shell - I'm not sure that array variables are supported in dash

You could do the array read in more recent versions of **bash** with

```

#!/bin/bash

while read ligne ; do
  affichage+=( "$ligne" )
done < " *yourfile* "

```

or even just 

```
#!/bin/bash

readarray affichage < " *yourfile* "
```

You can get the values by

```
echo "$**{**affichage[0]**}**"
```

(note the curly brackets) - but I don't think your multi-line echo is going to work, if you want to use echo you will need to embed newlines explicitly e.g.

```
echo  **-e **"Fiche de personnage :**\n** Nom: ${affichage[0]}"
```

---

### Post by Vaphell on 2013-05-16
> but I don't think your multi-line echo is going to work, if you want to use echo you will need to embed newlines explicitly

nah, multiline strings work just fine
```
$ a=( 1 2 3 4 )
$ echo "a0 = ${a[0]}
a3 = ${a[3]}"
a0 = 1
a3 = 4
```

---

### Post by fouadd on 2013-05-16
> **steeldriver said:**
> What system are you programming this on? if you are using /bin/sh on an Ubuntu system then it likely invokes a **dash** shell - I'm not sure that array variables are supported in dash

You could do the array read in more recent versions of **bash** with

```

#!/bin/bash

while read ligne ; do
  affichage+=( "$ligne" )
done < " *yourfile* "

```

or even just 

```
#!/bin/bash

readarray affichage < " *yourfile* "
```

You can get the values by

```
echo "$**{**affichage[0]**}**"
```

(note the curly brackets) - but I don't think your multi-line echo is going to work, if you want to use echo you will need to embed newlines explicitly e.g.

```
echo  **-e **"Fiche de personnage :**\n** Nom: ${affichage[0]}"
```

thanks man it's working !!!! 

can you please explain me the difference betwen echo and echo -e , i didn't get what you said very much ! i am just a beginner 

and by the way i am working in ubunto yes on the shel sh    #!/bin/sh

---

### Post by steeldriver on 2013-05-16
Sorry, I was wrong about that - 'echo -e' enables backslash escape charaters but you don't need it - see Vaphell's answer above

---


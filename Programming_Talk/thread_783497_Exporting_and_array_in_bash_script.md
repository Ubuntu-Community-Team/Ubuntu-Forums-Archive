---
title: "Exporting and array in bash script"
date: 2008-05-05
forum: Programming Talk
---

### Post by eldoctor on 2008-05-05
Hi everyone I have a bit of a problem here, is driving me mad. The code is the following:

```
while read LINEA; do
	strstr $LINEA $USER
	if [ $? -eq 1 ]; then
	 	(( P += 1 ))
		PERIODICOS[P]=${LINEA%%:*}
	fi
done < /etc/michelle/modulos/modulosperiodicos.cfg
J=1
while [ $J -le $P ]; do
	export ${PERIODICOS[J]}
	(( J += 1))
done
```

Each line in the "modulosperiodicos.cfg" is as follows:

/etc/michelle/modulos/limitaciones/limitaciones.sh:guest:guest2

A path to a script, after the ":" come the users but it does not matter because they are cut out, so each array position is assigned a line like this one:

/etc/michelle/modulos/limitaciones/limitaciones.sh

The problem comes when I try to export the array, I keep getting this error message:

```
/usr/bin/michelle.sh: line 154: export: `/etc/michelle/modulos/loadControl/loadControl.sh': not a valid identifier
```

I did this kind of "array exportation" in another script of my program and it worked fine with the only difference that the contents of the other array where not paths.
So my question is... how can I get this to work?? how can I export this array??

Thanks!!

---

### Post by stroyan on 2008-05-05
Your previous script wasn't doing what you think it was.
There is no good way to represent an array as an environment variable.
Bash will not export an array.  That was covered by the bash author
Chet Ramey at [http://www.mail-archive.com/bug-bash@gnu.org/msg01774.html](http://www.mail-archive.com/bug-bash@gnu.org/msg01774.html)

You could export the contents of an array as multiple environment variables.
This code would create variables with names like PERIODICOS_2 for PERIODICOS[2].
```

for i in ${!PERIODICOS[*]};do export PERIODICOS_$i="${PERIODICOS[$i]}";done

```
Then in a child shell script you could use-
```

for v in ${!PERIODICOS_*};do PERIODICOS[${v#PERIODICOS_}]="${!v}"; done

```
to set a PERIODICOS array from all the environment variables that match the PERIODICOS_* pattern.

---

### Post by eldoctor on 2008-05-05
Thanks for your reply stroyan, It worked!!! I will check my previous script and see what happens there (strange that it does not produce any errors)
I will fully implement this with the other proyects modules and see how it works

Thanks again!

---

### Post by jdmader on 2010-12-08
You could just source the environment of the child script, thus inheriting the arrays into the parent script's environment.

> source <child_script>.sh 
(works on Solaris, will have to try my Ubuntu instance @home)

OR

> . <child_script>.sh

Obviously I dont have code highlighting figured out for this forum.

---


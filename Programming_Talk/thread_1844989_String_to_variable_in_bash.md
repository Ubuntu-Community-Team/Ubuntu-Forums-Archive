---
title: "String to variable in bash"
date: 2011-09-16
forum: Programming Talk
---

### Post by Senplanet on 2011-09-16
Hello, 
I have a set of files which name looks like this:
fnl_20100610_00_00_c 
fnl_20100610_06_00_c
fnl_20100610_12_00_c
................................
Now I would like to read just part of the file name (00;06;12;.....etc) and use as variable in "if" statement. I tried:
echo $dhm | cut -d'_' -f3       >This can take the wanted part and print out. So I tried create a variable "i" :
i=$dhm | cut -d'_' -f3            > Doesnt work. I tried several combinations but couldnt fix it yet. It seems to be just simple task but I have no idea. Please, can someone give some suggestion here?

---

### Post by Arndt on 2011-09-16
> **Senplanet said:**
> Hello, 
I have a set of files which name looks like this:
fnl_20100610_00_00_c 
fnl_20100610_06_00_c
fnl_20100610_12_00_c
................................
Now I would like to read just part of the file name (00;06;12;.....etc) and use as variable in "if" statement. I tried:
echo $dhm | cut -d'_' -f3       >This can take the wanted part and print out. So I tried create a variable "i" :
i=$dhm | cut -d'_' -f3            > Doesnt work. I tried several combinations but couldnt fix it yet. It seems to be just simple task but I have no idea. Please, can someone give some suggestion here?

I think you want

```
i=`echo $dhm | cut -d'_' -f3`
```

---

### Post by ofnuts on 2011-09-16
> **Senplanet said:**
> Hello, 
I have a set of files which name looks like this:
fnl_20100610_00_00_c 
fnl_20100610_06_00_c
fnl_20100610_12_00_c
................................
Now I would like to read just part of the file name (00;06;12;.....etc) and use as variable in "if" statement. I tried:
echo $dhm | cut -d'_' -f3       >This can take the wanted part and print out. So I tried create a variable "i" :
i=$dhm | cut -d'_' -f3            > Doesnt work. I tried several combinations but couldnt fix it yet. It seems to be just simple task but I have no idea. Please, can someone give some suggestion here?
Besides the echo/cut method, in bash you can also extract substrings using brace expansion:
```
->x="abcdefghi"
->echo ${x:3:4}
**defg**
```See: [http://www.gnu.org/s/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/s/bash/manual/bash.html#Shell-Parameter-Expansion)

---

### Post by Vaphell on 2011-09-16
> **Arndt said:**
> I think you want

```
i=`echo $dhm | cut -d'_' -f3`
```

backticks are passe ;-), use $() instead

---

### Post by Senplanet on 2011-09-17
hmmm. That was really simple, Thanks

---


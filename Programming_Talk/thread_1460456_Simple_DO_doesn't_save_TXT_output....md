---
title: "Simple DO doesn't save TXT output..."
date: 2010-04-22
forum: Programming Talk
---

### Post by jfca283 on 2010-04-22
Hi
i'm  genereting some ulr to download later...

```
#!/bin/bash
#LT

cd $HOME/Desktop
> LT.txt

for i in $(seq 1 9) 
do
echo
http://www.papeldigital.info/lt/paginas/00$i.pdf  >>LT.txt
done

for i in $(seq 10 100)
do
http://www.papeldigital.info/lt/paginas/0$i.pdf
done
>> LT.txt
```
in the console i can see the links whn i run it...but they are not saved in the TXT file created
what am i doing wrong?
thanks by the way

---

### Post by tookyourtime on 2010-04-22
I'm not quite sure what you want to do. But to get the addresses in the text file use the line.
```
echo "http://www.papeldigital.info/lt/paginas/00$i.pdf"  >> LT.txt
```

I don't know what you're trying to do with lines 14 and 16 either?

---

### Post by jfca283 on 2010-04-22
```
#!/bin/bash
#LT

cd $HOME/Desktop
> LT.txt
#http://papeldigital.info/lt/2010/04/22/01/paginas/001.pdf
FF=$(date +%Y/%d/%m)

for i in $(seq 1 9) 
do
echo "http://www.papeldigital.info/lt/$FF/01/paginas/00$i.pdf"  >>LT.txt
done

for i in $(seq 10 99)
do
echo "http://www.papeldigital.info/lt/$FF/01/paginas/0$i.pdf"  >> LT.txt
done

```

it worked!!!
by the way...i'm generating links to download with wget
it's better than save one by one link on pdf format...(50-100 pages)
thanks

---

### Post by Bachstelze on 2010-04-22
You could also just do

```
for i in $(seq 1 9); do wget "http://www.papeldigital.info/lt/$(date +%Y/%d/%m)/01/paginas/00$i.pdf"; done
```

No need to write a script for that, you can type it directly on the command line.

---

### Post by slavik on 2010-04-22
or point wget to a webpage and tell it to DL anything that looks like [http://.*\.pdf](http://.*\.pdf) or some such.

---

### Post by Bachstelze on 2010-04-22
> **slavik said:**
> or point wget to a webpage and tell it to DL anything that looks like [http://.*\.pdf](http://.*\.pdf) or some such.

Only works if there is a webpage with links to every file, though.

---

### Post by jfca283 on 2010-04-23
i download the linka and then i printen in one PDF file
thanks

---


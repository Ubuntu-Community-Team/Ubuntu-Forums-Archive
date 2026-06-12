---
title: "Random numbers, bash script, etc."
date: 2010-06-12
forum: Programming Talk
---

### Post by j_arquimbau on 2010-06-12
I aimed to get a script which function is to choose 5 random words and display them (I want to copy a spanish TV show called Password).

The thing is that when I had a full dictionary (almost 50000 words), the /dev/urandom function worked perfectly and words weren't repeated. Now, I've changed the dictionary to work with just 780 words (the game consists on guessing the words whith three clues and, otherwise it is too difficult to guess some words) and with /dev/urandom or /dev/random the last word ('zumo' which means juice) appears almost all the times and in some cases several times in the five-words display.

So, my questions are:

Is there any way to display the ramdom words without them being repeated in the 5-words-set? 

Why isn't random working properly? Is there any way to make random work better?

I'm going to show you part of the script here:

```
if [ $respuesta = 1 ]; then
		

l=$(cat diccionario);n=$(( 100+(`od -An -N2 -i /dev/random` )%(780-0+1) ));cat diccionario | head -n$n | tail -n1 

l=$(cat diccionario);n=$(( 100+(`od -An -N2 -i /dev/random` )%(780-0+1) ));cat diccionario | head -n$n | tail -n1 

l=$(cat diccionario);n=$(( 100+(`od -An -N2 -i /dev/random` )%(780-0+1) ));cat diccionario | head -n$n | tail -n1 

l=$(cat diccionario);n=$(( 100+(`od -An -N2 -i /dev/random` )%(780-0+1) ));cat diccionario | head -n$n | tail -n1 

l=$(cat diccionario);n=$(( 100+(`od -An -N2 -i /dev/random` )%(780-0+1) ));cat diccionario |  head -n$n | tail -n1

echo "

Tiempo restante:  " 
countdown "00:00:30"
clear
for i in {1..5}
do
echo "
############################################
############################################
####					####
####		TIME OUT		####
####					####
############################################
############################################
"
sleep 0.5
clear
sleep 0.5
done

```

Thank you everybody!

---

### Post by j_arquimbau on 2010-06-12
I kind of solved it by

```
sort -R diccionario
``` at the beggining of the script...

---

### Post by geirha on 2010-06-12
That's not a bad way to do it.
```
sort -R diccionario | head -n 5 | iconv -f iso-8859-15
```

---

### Post by j_arquimbau on 2010-06-12
Thank you again geirha!

---


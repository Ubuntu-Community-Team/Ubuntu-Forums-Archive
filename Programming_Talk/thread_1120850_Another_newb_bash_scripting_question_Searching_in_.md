---
title: "Another newb bash scripting question: Searching in a text file ?"
date: 2009-04-09
forum: Programming Talk
---

### Post by Pierre-Alexandre on 2009-04-09
Hi folks,

I need to create a script which generates the average of a student's notes which are located in a text file similar to:

```
:NOM Prenom:CODE                :.Tp1 :.Intra:.Tp2 :.Tp3 :.Final :.TP4 :.Moy:.Lettre:
actarusx:Actarus  :ACTA28658105 : 45.5: 75.00:100.0: 95.0:  48.50: 90.0:     
alcorxxx:Alcor    :ALCO18083408 : 83.0: 64.75: 95.0: 87.5:  74.00: 97.0:  
venusiax:Venusia  :VENU13097708 : 83.0: 55.00: 95.0: 87.5:  41.50: 97.0:       
phenicia:Phenicia :PHEN14100790 : 94.0: 50.50: 95.0: 95.0:  59.50: 99.0:   
mizarxxx:Mizar    :MIZA22128106 : 98.0: 95.50: 95.0:100.0:  80.50: 90.0:     
procyonx:Procyon  :PROC01033701 : 99.0: 99.50:100.0: 95.0:  98.00:100.0:       
flamxxxx:Flam     :FLAM26077904 : 89.0: 37.25: 97.5: 87.5:  63.50: 97.0:     
johannxx:johann   :JOHA23058000 : 94.0: 99.25:100.0: 95.0:  36.00:100.0:     
wrightxx:Wright   :WRIG21058103 : 99.0: 100.0:100.0:100.0:  100.0: 97.0:    
cragxxxx:Grag     :CRAG05018002 : 99.0: 90.00: 90.0:100.0:  97.00: 99.0:      
malaxxxx:Mala     :MALA09557914 : 96.0: 69.50:100.0:100.0:  34.00: 47.0:    
``` 

My first idea was to use IFS to change the separator and then use the command cut, but after testing various settings I couldn't achieve the requested result. 

For testing purposes,

```
#!/bin/sh
a=0
IFS=:
for line in `cat $1`
do 
    VAR=`cut -c "[0-9]" $line`
    echo $VAR
done

```

I couldnt get it to work. All I really want is to get the notes. Is there any easier way to do it? I'm confused :/

---

### Post by shel-hall on 2009-04-09
> **Pierre-Alexandre said:**
> Hi folks,

I need to create a script which generates the average of a student's notes which are located in a text file similar to:

```
:NOM Prenom:CODE                :.Tp1 :.Intra:.Tp2 :.Tp3 :.Final :.TP4 :.Moy:.Lettre:
actarusx:Actarus  :ACTA28658105 : 45.5: 75.00:100.0: 95.0:  48.50: 90.0:     
alcorxxx:Alcor    :ALCO18083408 : 83.0: 64.75: 95.0: 87.5:  74.00: 97.0:  
venusiax:Venusia  :VENU13097708 : 83.0: 55.00: 95.0: 87.5:  41.50: 97.0:       
phenicia:Phenicia :PHEN14100790 : 94.0: 50.50: 95.0: 95.0:  59.50: 99.0:   
mizarxxx:Mizar    :MIZA22128106 : 98.0: 95.50: 95.0:100.0:  80.50: 90.0:     
procyonx:Procyon  :PROC01033701 : 99.0: 99.50:100.0: 95.0:  98.00:100.0:       
flamxxxx:Flam     :FLAM26077904 : 89.0: 37.25: 97.5: 87.5:  63.50: 97.0:     
johannxx:johann   :JOHA23058000 : 94.0: 99.25:100.0: 95.0:  36.00:100.0:     
wrightxx:Wright   :WRIG21058103 : 99.0: 100.0:100.0:100.0:  100.0: 97.0:    
cragxxxx:Grag     :CRAG05018002 : 99.0: 90.00: 90.0:100.0:  97.00: 99.0:      
malaxxxx:Mala     :MALA09557914 : 96.0: 69.50:100.0:100.0:  34.00: 47.0:    
``` 


awk is the classic solution for this.  "man awk" for details, I suppose, but I'll bet there's a skeleton awk script on the 'net that's already close to what you need.  There's probably one in O'Reilly's "sed and awk" book, too, but I'm 8,000 miles from my copy of it.

-Shel

---

### Post by Arndt on 2009-04-09
> **Pierre-Alexandre said:**
> Hi folks,

I need to create a script which generates the average of a student's notes which are located in a text file similar to:

```
:NOM Prenom:CODE                :.Tp1 :.Intra:.Tp2 :.Tp3 :.Final :.TP4 :.Moy:.Lettre:
actarusx:Actarus  :ACTA28658105 : 45.5: 75.00:100.0: 95.0:  48.50: 90.0:     
alcorxxx:Alcor    :ALCO18083408 : 83.0: 64.75: 95.0: 87.5:  74.00: 97.0:  
venusiax:Venusia  :VENU13097708 : 83.0: 55.00: 95.0: 87.5:  41.50: 97.0:       
phenicia:Phenicia :PHEN14100790 : 94.0: 50.50: 95.0: 95.0:  59.50: 99.0:   
mizarxxx:Mizar    :MIZA22128106 : 98.0: 95.50: 95.0:100.0:  80.50: 90.0:     
procyonx:Procyon  :PROC01033701 : 99.0: 99.50:100.0: 95.0:  98.00:100.0:       
flamxxxx:Flam     :FLAM26077904 : 89.0: 37.25: 97.5: 87.5:  63.50: 97.0:     
johannxx:johann   :JOHA23058000 : 94.0: 99.25:100.0: 95.0:  36.00:100.0:     
wrightxx:Wright   :WRIG21058103 : 99.0: 100.0:100.0:100.0:  100.0: 97.0:    
cragxxxx:Grag     :CRAG05018002 : 99.0: 90.00: 90.0:100.0:  97.00: 99.0:      
malaxxxx:Mala     :MALA09557914 : 96.0: 69.50:100.0:100.0:  34.00: 47.0:    
``` 

My first idea was to use IFS to change the separator and then use the command cut, but after testing various settings I couldn't achieve the requested result. 

For testing purposes,

```
#!/bin/sh
a=0
IFS=:
for line in `cat $1`
do 
    VAR=`cut -c "[0-9]" $line`
    echo $VAR
done

```

I couldnt get it to work. All I really want is to get the notes. Is there any easier way to do it? I'm confused :/

'cut' apparently doesn't use IFS - I think only the shell itself does.

Do you want the average of all numeric columns or one specific column? Anyway, this prints out one of the columns:

```
tr : ' ' < /tmp/notes | awk '{print $8;}'
```

---

### Post by Pierre-Alexandre on 2009-04-09
Hi and thanks for the quick reply

I need to calculate the average from the line following the student's name. For example:

actarusx:Actarus  :ACTA28658105 : 45.5: 75.00:100.0: 95.0:  48.50: 90.0:
The data I need is: 45.5, 75.00, 100.0, etc.

I need to extract this data line per line. I can manage the rest of the script (average calculation using BC, etc.) but I'm totally oblivious to this specific part of the task.

AWK seems interesting, but is there any other way to do it ?

---

### Post by Pierre-Alexandre on 2009-04-09
Kindly ignore this thread. I got it to work using cut :)

Thanks, folks.

---

### Post by ghostdog74 on 2009-04-09
> **Arndt said:**
> 

```
tr : ' ' < /tmp/notes | awk '{print $8;}'
```

```

awk -F"[:]" '{print $8;}' file

```

---


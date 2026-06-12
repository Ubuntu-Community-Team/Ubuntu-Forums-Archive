---
title: "A shell to create folders"
date: 2008-08-19
forum: Programming Talk
---

### Post by VitroBlue on 2008-08-19
Hi, I'm new at Linux
I've been using if for about 48 non-continuos hours, 40 of which had been used to make it run properly in my virtual machine.
I had this assignment on my OS class. It was about writting a shell capable of automatically create folders anywhere according to the user preferences. The due time is already over, so I'd be hell of a lucky girl if I get my homework accepted, and graded with a 60%. 
The point is that I need to know how to do this coz I fear this is nothing copared to what will be next and I'm already freaking out about it.

The least it should do was to create 3 folders in a new-folder-1 and from 01h to 0Fh folders in new-folder-2. these new-folders where supposed to be created in any random VALID given path.

So... this is my lame piece of code

#!/bin/sh

carpeta1="Tareas"
carpetaT="sesion_"
carpetaTN="1 2 3 4 5 6 7 8 9 A B C D F"
carpeta2="Examenes"
carpetaE="second tird final"
ruta="Tareas/sesion_3"

echo "HW no. 2"
echo "Shell Example"
echo "Folders Automata"
echo ""
echo "Shell checks up folders..."

#this was supposed to verify that the folders I want to create does not already exist...

listacarpeta=$(ls ~/$ruta) #here my intention was to save the list of folders into a... variable so i can work on that list

echo "$listacarpeta" #show me the list

#the next stuff is commented because it didn't work, obviously

#  for existecarpeta in $listacarpeta  # for x element in the list of folders...

#  do

#    echo "$existecarpeta"   #show me which element we are talking about 

#    if [$existecarpeta != $carpeta1] && [$existecarpeta != $carpeta2]  #if the name is neithr the ones i want to create

#    then  # it means i can create it without problem

#this part is worth a 50% of the assignment... if something
     echo "Shell creates folders"
        mkdir ~/$ruta/$carpeta1
        for numero in $carpetaTN
        do
          mkdir ~/$ruta/$carpeta1/$carpetaT$numero
        done
        mkdir ~/$ruta/$carpeta2
        for nombreE in $carpetaE
        do
          mkdir ~/$ruta/$carpeta2/$nombreE
        done
#    else     #it means there are folders with the same names in the specified path
#      echo "Warning: there are folders with the same names in the specified path"
#    fi
#  done



how can I make the ### part work? that would have given a 70%
other thing it had to do was to ask the user for the actual values for carpeta1 (folder name), carpeta2 (folder name) and ruta (path) and verify this path is valid (if not, send an error and ask again), that would have made 80%
another was not only to warn me about existing folders with the same name but to ask the user wether overwrite them or not, 90%
the 100% meant that it could create not only two initial folders with this amount of subfolders but a whole dammed hierarchical three in whatever specified path... pretty damn crazy, if you ask me, considering I discovered just today at 9 am during class what a shell is, so don't even bother with that one

but i find that 90% still "possible" (considering I sent my homework 3 server minutes late, I already have an automatically generated zero). Can anyone help my ego not to hurt so damn badly? I felt it was blown at point-blank range with this...

Tnx a lot.

---

### Post by jpeddicord on 2008-08-22
Moved to Programming Talk: not a tutorial.

---


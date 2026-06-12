---
title: "problem with read command (in bash)"
date: 2009-01-03
forum: Programming Talk
---

### Post by davidtuti on 2009-01-03
Hi,




The problem that I have it's that the command read the first time make it  ok (waiting the input from the user) but the second time doesn't wait that the user input the string, and continue without wait a input :o

I have the read command  in a function:

CogerOpcion ()
{
echo "Teclee la Opcion que desee reproducir"
read
echo " el valor es $REPLY"
}


Any help?

---

### Post by ghostdog74 on 2009-01-03
i have problem understanding your problem. Is that all the code you have? Where is your read for the second time?

---

### Post by davidtuti on 2009-01-03
> **ghostdog74 said:**
> i have problem understanding your problem. Is that all the code you have? Where is your read for the second time?

Sorry, this is a function that I have. The code is:
```

david@defekas:~$ cat menu.sh
set -x                      
contador=0                  
typeset numero=0            
echo "MENU PARA REPRODUCIR PELICULAS"

Ruta_pelis=/home/david/windows_descargas/completadas/PELIS
ls -rt1 $Ruta_pelis | grep -v Thumbs > ListaPeli          
sed "s/ /_/g" ListaPeli > ListaPelis                      

clear

while read -r Line
do                
  let "contador++"
  echo $contador $Line >> ListaPelisNum
  echo $contador >> ListaNum           
done < ListaPelis                      

MostrarMenu ()
{             
set -x        
echo "el valor de rely es ...$REPLY"
#clear                              
while read -r Line                  
do                                  
  echo $Line | awk '{print $1"-------"$2}' 
done < ListaPelisNum                       
CogerOpcion                                
Comprobar                                  
}                                          

BorrarTemporales ()
{                  
rm -f ListaPelisNum
rm -f ListaNum     
rm -f ListaPelis   
}                  

CogerOpcion ()
{             
echo "El valor de rely es ...$REPLY"
echo "Teclee la Opcion que desee reproducir"
read                                        
echo " el valor es $REPLY"                  
}                                           
Reproducir ()                               
{                                           
# vlc                                       
sleep 3                                     
echo "el valor de rely es ...$REPLY"        

cd windows_descargas/completadas/PELIS/$VideoCon
if [[ -n `ls *.avi 2>/dev/null` ]]              
    then                                        
      echo "existe"                             
    else                                        
      echo "No existe el fichero en la ruta adecuadaº"
      cd $HOME                                        
      echo "No existe el fichero en la ruta adecuada" 
      MostrarMenu                                     
fi                                                    
if [[ -n `ls *2*.avi 2>/dev/null` ]]                  
     then                                             
         if [[ -n `ls *1*.avi 2>/dev/null` ]]         
            then                                      
                echo "el fichero es de 2 partes"      
         else                                         
                echo "la pelicula es de 1 parte"      
         fi                                           
else                                                  
      echo "el fichero es deuna parte"                

fi
vlc *.avi

if [[ $? != 0 ]]
  then          
    echo "salida anomala"
  else                   
    echo "bien"          
fi                       


}

Comprobar ()
{
set -x
while read -r Line
do
   if [[ $REPLY -eq `echo $Line | awk '{print $1}'` ]]
     then
     echo "Encontrado"
     Video=`echo $Line | awk '{print $2'}`
     echo " el fichero de video es ... $Video"

sleep 3
VideoCon=`echo $Video | sed "s/_/\*/g" | sed "s/\[/\*/g" | sed "s/\]/\*/g"`


     Reproducir
  else
    echo "NO ENCONTRADO"
    sleep 3
   fi
done < ListaPelisNum
echo "No ha encontrado el numero solicitado"
MostrarMenu
}


MostrarMenu
BorrarTemporales


```

The problem is that when the program shows me the menu again because for example doesn't find a file that I search in the program, it must be ask me again for other option but the command read doesn't works and doesn't wait a input

Thanks!

---

### Post by ghostdog74 on 2009-01-03
what i would suggest is to give your read command a variable, and then use return in your functions to return values.
eg
```

read variable 

```
in your functions
```

function() {
 ....
 ...
 read variable
 return variable
}

```

Always remember to return values if necessary when using functions.

---

### Post by davidtuti on 2009-01-03
> **ghostdog74 said:**
> what i would suggest is to give your read command a variable, and then use return in your functions to return values.
eg
```

read variable 

```
in your functions
```

function() {
 ....
 ...
 read variable
 return variable
}

```

Always remember to return values if necessary when using functions.

Many thanks but it doen't works! when I input a number thant inside the directory doesn't have a file *.avi the program shows me the menu again and then it goes to the function "CogerOpcion" where is the command read but the command read doesnt wait the input, the value $REPLY gets the first line of the file ListaNumPelis  :(


...
...
El valor de rely es ...46
++ echo 'Teclee la Opcion que desee reproducir'
Teclee la Opcion que desee reproducir
++ read
++ echo ' el valor es 1 [Rec]_[DVDRIP][Spanish][2007][[www.newpct.com]](www.newpct.com])'
...........


Many thanks!

---

### Post by stroyan on 2009-01-03
Your Comprobar function calls the Reproducir function inside
of a while loop that has stdin redirected from ListaPelisNum.
If you are going to nest redirections you should use different
file descriptors for the different files.  You could try something like this using "read -u 3" and "3< ListaPelisNum".

```
Comprobar ()
{
set -x
while read -u 3 -r Line
do
   if [[ $REPLY -eq `echo $Line | awk '{print $1}'` ]]
     then
     echo "Encontrado"
     Video=`echo $Line | awk '{print $2'}`
     echo " el fichero de video es ... $Video"

sleep 3
VideoCon=`echo $Video | sed "s/_/\*/g" | sed "s/\[/\*/g" | sed "s/\]/\*/g"`


     Reproducir
  else
    echo "NO ENCONTRADO"
    sleep 3
   fi
done 3< ListaPelisNum
echo "No ha encontrado el numero solicitado"
MostrarMenu
}

```

---

### Post by davidtuti on 2009-01-04
> **stroyan said:**
> Your Comprobar function calls the Reproducir function inside
of a while loop that has stdin redirected from ListaPelisNum.
If you are going to nest redirections you should use different
file descriptors for the different files.  You could try something like this using "read -u 3" and "3< ListaPelisNum".

```
Comprobar ()
{
set -x
while read -u 3 -r Line
do
   if [[ $REPLY -eq `echo $Line | awk '{print $1}'` ]]
     then
     echo "Encontrado"
     Video=`echo $Line | awk '{print $2'}`
     echo " el fichero de video es ... $Video"

sleep 3
VideoCon=`echo $Video | sed "s/_/\*/g" | sed "s/\[/\*/g" | sed "s/\]/\*/g"`


     Reproducir
  else
    echo "NO ENCONTRADO"
    sleep 3
   fi
done 3< ListaPelisNum
echo "No ha encontrado el numero solicitado"
MostrarMenu
}

```


Many thanks! It works!!!

Thank you very much...
:D:D:D:D:D:D

---


---
title: "Problem in my Bash script"
date: 2009-04-12
forum: Programming Talk
---

### Post by Rany Albeg on 2009-04-12
Hi all , this is a part of a script im writing:
---------------------------

   while [ "$i" -ne "${#SEL_ARRAY[*]}" -a "$SKIP" == "false" ]
   do
   	if [[ "${SEL_ARRAY["$i"]}" = **.* ]] ; then
   		
   		ARRAY_TO_COMP[$i]="${SEL_ARRAY[$i]}"
   	else
   		ARRAY_TO_COMP[$i]="${ARRAY["${SEL_ARRAY[$i]}"]}"
   	fi
   	
   	i=i+1
   done

tar -czvf "$NAME" "${ARRAY_TO_COMP[@]}"
---------------------------

i'll explain my variables :

ARRAY 
-----
      contain a list of dirs and files.

SEL_ARRAY ( selection array ) 
-----------------------------

      contain numbers and string

ARRAY_TO_COMP ( array to compress )
-----------------------------------
      the array i'll pass to tar for compression.

How the script runs now:
------------------------

now , if i insert numbers to SEL_ARRAY it all fine,

but when i insert *.mp3 i get an error message:

***** tar: *.mp3: Cannot stat: No such file or directory ******

How i tried to solve this:
--------------------------

if i changed the last line to

$(echo "${ARRAY_TO_COMP[@]}")

*.mp3 works fine! but now if i will insert numbers into SEL_ARRAY
i wont be able to compress files that their names contain spaces.

i google for information and read about splitting strings , spaces etc
but i just cant get the job done.

Thanks in advance for your time and help.

---

### Post by Rany Albeg on 2009-04-12
Problem is solved.
changed to this:

   while [ "$i" -ne "${#SEL_ARRAY[*]}" -a "$SKIP" == "false" ]
   do
   	if [[ "${SEL_ARRAY["$i"]}" = **.* ]] ; then
   		
   		ARRAY_TO_COMP+=( ${SEL_ARRAY[$i]} ) 
   		
   	else
   	      ARRAY_TO_COMP[${#ARRAY_TO_COMP[@]}]="${ARRAY["${SEL_ARRAY[$i]}"]}"
   	fi
   	
   	i=i+1
   done

---


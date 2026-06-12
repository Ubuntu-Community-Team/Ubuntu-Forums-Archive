---
title: "while loop to get names from another table"
date: 2016-07-07
forum: Programming Talk
---

### Post by tho4 on 2016-07-07
Hi,

 I try to get the names associated with a reference number (variable $LEP_ref hereunder) from a table (Artenliste) to add it to my table TL_dissections. I wrote the following script, but apparently it is not possible to cat another file when doing a while loop. Would someone have the solution?
Here is the script:

cat TL_dissections | while read line; [INDENT]do LEP_ref=$(cut -f 7); 
species_name=$(cat Artenliste | grep $LEP_ref | cut -f 2,3); 
echo -e "$LEP_ref \t $species_name";
[/INDENT]
done

Thank you for your help!
Théo

---

### Post by steeldriver on 2016-07-07
Sure it's possible. What is

```

do LEP_ref=$(cut -f 7);

```

supposed to be cutting?

If you want specific help, it would be good to post samples of the relevant files.

---

### Post by tho4 on 2016-07-07
Hi Steeldriver,

here is the file I want to complete: [https://www.dropbox.com/s/q0szbqdlo32bwcg/TL_dissections?dl=0](https://www.dropbox.com/s/q0szbqdlo32bwcg/TL_dissections?dl=0)
Here is the file where the names should be retrieved: [https://www.dropbox.com/s/3mpwuprih7sh2gk/Artenliste?dl=0](https://www.dropbox.com/s/3mpwuprih7sh2gk/Artenliste?dl=0)
LEP_ref=$(cut -f 7) cuts the LEP reference number ("LEP" followed by 3 or 4 digits: LEP569, LEP2671, etc) which is located on the 7th column.

Thank you for the help!

---

### Post by Rocket2DMn on 2016-07-07
I think you don't want the semicolons at the end of the lines within the loop (just after the while statement, before "do").  I'd write this a little differently:

```

while read line; do
    LEP_ref=$(cut -f 7)
    species_name=$(grep $LEP_ref Artenliste | cut -f 2,3)
    echo -e "$LEP_ref \t $species_name"
done < dissections

```

---

### Post by steeldriver on 2016-07-07
The semicolons are optional when commands are split over lines

Your version is still not passing any input to 'cut' - I haven't bothered to follow the dropbox links but I suspect the intent is probably to cut fields from the read line i.e.

```

while read line; do
    LEP_ref="$(cut -f 7 [COLOR=#0000ff]<<< "$line"[/COLOR])"
    .
    .
    .
done

```

---

### Post by tho4 on 2016-07-08
Hi,

thank you for the reply. I still dont get what I want. To make it easier, here is part of my TL_dissections file (tab as field separator in both files):
TL 162    M LEP2324            
TL 163    M                    LEP2325            
TL 164    F                    LEP2326            
TL 165    F                    LEP2645            
TL 166    M                    LEP2646

Here is part of my Artenliste file: 
LEP2322    Xubida    linearella    USA, FL, Ala. Co. Goethe SF, Watermelon Pond, 20.vii.2014 (J.H.)    MTD    Crambinae
LEP2323    Diatraea    evanescens    USA, FL, Ala. Co. Gainesville, UVL/95 % bucket trap on lawn behind Mc Guire Center, 12-13.vii.2014 (J. H.)    MTD    Crambinae
LEP2324    Fissicrambus    haytiellus    USA, FL, Ala. Co. Gainesville, UVL/95 % bucket trap on lawn behind Mc Guire Center, 12-13.vii.2014 (J. H.)    MTD    Crambinae
LEP2325    Fissicrambus    profanellus    USA, FL, Ala. Co. Gainesville, UVL/95 % bucket trap on lawn behind Mc Guire Center, 12-13.vii.2014 (J. H.)    MTD    Crambinae
LEP2326    Raphiptera    argillaceella    USA, FL, Ala. Co. Gainesville, Paynes Prairies Pres. St. Pk., 26.ix.2014 (J. H.)    MTD    Crambinae

I want to retrieve the species name associated to this LEP reference number from Artenliste to complete my TL_dissections file.

---

### Post by steeldriver on 2016-07-08
I'd probably use awk for something like that

```

$ awk 'NR==FNR {LEP_refs[$1]=$2" "$3; next} $4 in LEP_refs {print $4"\t"LEP_refs[$4]}' Artenliste TL_dissections 
LEP2324    Fissicrambus haytiellus
LEP2325    Fissicrambus profanellus
LEP2326    Raphiptera argillaceella

```

or, since your files appears to be sorted on the LEP field, use 'join'

```

$ join -14 -21 TL_dissections Artenliste -o 0,2.2,2.3
LEP2324 Fissicrambus haytiellus
LEP2325 Fissicrambus profanellus
LEP2326 Raphiptera argillaceella

```

If you still want to use a shell loop (which I don't recommend), then

```

while read -r line; do
  LEP_ref="$(cut -f 4 <<< "$line")"
  species_name="$(grep -F "$LEP_ref" Artenliste | cut -f2,3)"
  printf '%s\t%s\n' "$LEP_ref" "$species_name"
done < TL_dissections 
LEP2324    Fissicrambus    haytiellus
LEP2325    Fissicrambus    profanellus
LEP2326    Raphiptera    argillaceella
LEP2645    
LEP2646    

```

---

### Post by tho4 on 2016-07-08
Thanks a lot, I tried the awk command and it works! I will now try to understand how it actually works ;-)

---


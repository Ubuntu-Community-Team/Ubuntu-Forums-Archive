---
title: "Keyword string match.  grep?"
date: 2009-11-11
forum: Programming Talk
---

### Post by dolphy on 2009-11-11
I posted the same over at ARS Technica but I thought this might be a better forum.  Basically the problem is as follows:
 
[LIST]
[*]I have a field that contains Company name correctly.
[*]I have another field that contains a partial name of the company or the full name with extra characters.
[/LIST]

What I need to do is match the partial name with the correct name and then use that info to update the database. I have used LIKE in a SQL statement and only got 16 records.  I need to update thousands of records or ask the boss to hire a temp to do it by hand.  I'm lazy so I'd rather come up with a solution that makes the computer do the work.

Can I use grep to match them together, next to each other? Basically export each to a text file, then compare the files against each other. I can then import the result into a table and update my database.  

Example:

Partial Name  ______             Correct Name
CompanyA3321 ______             CompanyA
34CompanyBx  ______             CompanyB

etc..

Any help with this would be greatly appreciated.

---

### Post by ghostdog74 on 2009-11-11
show sample input files, describe clearly what you want as output.

---

### Post by dolphy on 2009-11-11
So the example file of the partial names would look something like this:

--example partial names:
IBM #299
Micro_soft
321 Ubuntu 
..the list would go on for about 3000 distinct partial names 

The example file of full names would look something like this:
--example full names:
Microsoft
Ubuntu
IBM
...there are about 200 full names

What I need to do is match the partial name with the full name and achieve and output like this:

IBM #299 = IBM
Micro_soft = Microsoft
321 Ubuntu = Ubuntu

I would then import the output into a staging table with a column for the partial name and a column for the related full name. This way I can link them together and update my database. 

Hope this makes sense and thanks for your efforts.

---

### Post by ghostdog74 on 2009-11-11
gawk
```

awk 'FNR==NR{
  full[tolower($1)]=$1
  next
}
{
  o=$0
  gsub(/[[:cntrl:]]|[[:punct:]]|[[:digit:]]| +/,"",o)  
  f=tolower(o)
  if ( f in full ){
    print $0,full[f]
  }   
}' file1 file

```

output
```

$ more file1
Microsoft
Ubuntu
IBM

$ more file
IBM #299
Micro_soft
321 Ubuntu

$ ./shell.sh
IBM #299 IBM
Micro_soft Microsoft
321 Ubuntu  Ubuntu


```

---

### Post by dolphy on 2009-11-11
WOW!!  Now I just need to decipher your code to set it to my files.  I'll let you know how it goes.  Thanks a ton!

---

### Post by dolphy on 2009-11-11
Ok.  I execute the first part of the code based on my two text files but my output was different, only got three results:

```

awk 'FNR==NR{
>   full[tolower($1)]=$1
>   next
> }
> {
>   o=$0
>   gsub(/[[:cntrl:]]|[[:punct:]]|[[:digit:]]| +/,"",o)  
>   f=tolower(o)
>   if ( f in full ){
>     print $0,full[f]
>   }   
> }' partial.txt full.txt
 ASTRAZENECA
 GLAXOSMITHKLINE
 IMMUNEX


```

I'm not too sure what I'm supposed to do with your output code.

---

### Post by ghostdog74 on 2009-11-12
my code works with your initial sample. If it doesn't work for you, that's no my problem since you didn't give possible scenarios as close as possible.

also, i don't want to guess what your partial.txt and full.txt looks like in your latest post. you should post their samples

---

### Post by Arndt on 2009-11-12
> **dolphy said:**
> Ok.  I execute the first part of the code based on my two text files but my output was different, only got three results:

```

awk 'FNR==NR{
>   full[tolower($1)]=$1
>   next
> }
> {
>   o=$0
>   gsub(/[[:cntrl:]]|[[:punct:]]|[[:digit:]]| +/,"",o)  
>   f=tolower(o)
>   if ( f in full ){
>     print $0,full[f]
>   }   
> }' partial.txt full.txt
 ASTRAZENECA
 GLAXOSMITHKLINE
 IMMUNEX


```

I'm not too sure what I'm supposed to do with your output code.

Maybe you switched the file names. I'm not sure why "partial" and "full" are named the way they are, but try giving them in the order full.txt partial.txt instead. What the code does is: for each line in the second file, throw away everything but letters, and then look for an exact match for the remaining name in the first file, disregarding case. Then it outputs the matching entries (with the original line from the second file).

---

### Post by dolphy on 2009-11-12
> **ghostdog74 said:**
> my code works with your initial sample. If it doesn't work for you, that's no my problem since you didn't give possible scenarios as close as possible.

also, i don't want to guess what your partial.txt and full.txt looks like in your latest post. you should post their samples

ghostdog74- I truly appreciate your code as it has opened my eyes as to what is possible with gawk.  Unfortunately, the partial names list contains some sensitive information...account numbers etc, that I cannot post online.  The best thing for me to do is learn how awk works so that I can write code that will better match my partial list.

If you have any suggestions as to best way to go about this, please let me know.

Thanks again for all your help.

---

### Post by ghostdog74 on 2009-11-12
> **dolphy said:**
>   Unfortunately, the partial names list contains some sensitive information...account numbers etc, that I cannot post online.  

what i need is just the format. Just give fictional numbers to those account numbers. Leave punctuations etc as it is...etc..For names, just put in some fictitious names.... and have you tried reversing the order of your files passed to awk?

---

### Post by dolphy on 2009-11-12
The majority of the records are formatted as follows:

Bose Labs. YH#23-555
or
Bose Labs, Inc (NHC 08-352)

Also, sometimes they could be in all CAPS but I think, from reading your code that you account for that.

I was thinking that if I remove all the spaces and then go from there.  Doesn't AWK treat spaces as columns?

Thanks

---

### Post by ghostdog74 on 2009-11-12
why don't you show what does not work for you. modify your partial.txt and full.txt to contain fictitious data but close to actual format as possible. run the code , show your output and any error messages.

---

### Post by dolphy on 2009-11-12
So I have compressed the text together for my partial.txt file.  As sample is as follows:
```
MERCK        6213 
IMCLONE/    6214 
ASTELLAS    6216 
AMGEM FE    6217 
Novartis    6221 
CEPHALON    6269 
GENENTEC    6270 
ASTRAZE        6271 
Exelixis    6323 
PfizerS        6324 
Genentec    6325 
BMS(Imcl    6326 
Genentec    6327 
Amgen-Pr    6328 
Novartis    6329 
Sunesis     6372 
Pfizer      6373

The numbers are unique record identifiers that I will need to update our table.



```

Here's a sample of my full.txt:
```

Pfizer, Inc.
AstraZeneca
Bayer Corporation
Genentech, Inc.
Genzyme Corporation
...and so on

```

Is there is a way to create something like: Genentec 6327  =   Genetech, Inc.

---

### Post by ghostdog74 on 2009-11-12
why are there so many "Genentec" in partial. and what criteria do you want to get id 6327 for "Genentech, Inc" , since there are other ids like 6270 and 6325 as well? what if you have "Genentech ,Ltd" or other similar cases ?

---

### Post by dolphy on 2009-11-18
I was able to solve my problem using AWK.  ghostdog74 - Thank you so much for all of your help.  Always feels good to learn something new.

Cheers!

---


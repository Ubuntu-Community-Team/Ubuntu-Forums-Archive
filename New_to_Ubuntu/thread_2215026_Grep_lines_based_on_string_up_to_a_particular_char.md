---
title: "Grep lines based on string up to a particular character"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by Muriel_Gros-Baltha on 2014-04-04
Hello !

I have a file containing sequence names (line starting with >) followed by lines containing the sequence itself. It is maybe imporant to notice that the sequence lines are seperated by \n.

```
>rnd-2_family-26#Unknown/L1 ( Recon Family Size = 124, Final Multiple Alignment Size = 96 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
>rnd-2_family-16#LTR/Copia ( Recon Family Size = 80, Final Multiple Alignment Size = 67 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
>rnd-2_family-141#Unknown/Copia ( Recon Family Size = 49, Final Multiple Alignment Size = 42 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
>rnd-2_family-9#DNA/PIF-Harbinger ( Recon Family Size = 34, Final Multiple Alignment Size = 27 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
```

I would like to seperate it into two files. I want the sequences with the name containing "Unknown" going to 1 file and all the other going to another file. And I also want the name of the sequence (starting with >) included : 

File 1 : Sequence name contains "Unknown"
```
>rnd-2_family-26#Unknown/L1 ( Recon Family Size = 124, Final Multiple Alignment Size = 96 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
>rnd-2_family-141#Unknown/Copia ( Recon Family Size = 49, Final Multiple Alignment Size = 42 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
```

and File 2 : Sequence name DOES'NT  contains "Unknown"
```
>rnd-2_family-16#LTR/Copia ( Recon Family Size = 80, Final Multiple Alignment Size = 67 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
>rnd-2_family-9#DNA/PIF-Harbinger ( Recon Family Size = 34, Final Multiple Alignment Size = 27 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
```

I don't know how to tell grep to take the line containing "Unknown", but also all the following lines until the ">" signs which is a new sequence.

Maybe I have to use sed or awk ???

Any help ?!!

Thanks a lot !!

Muriel

---

### Post by steeldriver on 2014-04-04
If all the records had the same number of lines, you could use grep with the -A option to get a fixed number of lines of *following context*. However with a variable number of following lines perhaps using awk to split them into records based on the > as a record separator?

```

$ awk -v RS='>' -v ORS='>' -F'\n' '$1 ~ /Unknown/ {print}' sequences.txt
rnd-2_family-26#Unknown/L1 ( Recon Family Size = 124, Final Multiple Alignment Size = 96 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
>rnd-2_family-141#Unknown/Copia ( Recon Family Size = 49, Final Multiple Alignment Size = 42 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA

```

```

$ awk -v RS='>' -v ORS='>' -F'\n' '$1 !~ /Unknown/ {print}' sequences.txt
>rnd-2_family-16#LTR/Copia ( Recon Family Size = 80, Final Multiple Alignment Size = 67 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
>rnd-2_family-9#DNA/PIF-Harbinger ( Recon Family Size = 34, Final Multiple Alignment Size = 27 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA

```

EDIT: oops sorry - I just noticed it 'eats' the first record separator (>) - let me think about that ...

---

### Post by Muriel_Gros-Baltha on 2014-04-04
Hey !

Thanks a lot for your answer !

So yes using grep is not possible as sequences have different length !

I tried what you told me and it works.
But yes, there is > missing beginning of the file and an extra > at the end of the file.
Since these are not big file I just edit them with gedit.

But if you find a solution it would be great as I may have to do it several times and with bigger files !

Let me know, thanks a lot again !!

Muriel

---

### Post by steeldriver on 2014-04-04
OK this is much simpler I think (no messing with records / separators etc.):

```

$ awk '$1 ~ /^>/ {if ($1 ~ /Unknown/) outfile="file1"; else outfile="file2"}; {print > outfile}' sequences.txt 

```

```

$ cat file1
>rnd-2_family-26#Unknown/L1 ( Recon Family Size = 124, Final Multiple Alignment Size = 96 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
>rnd-2_family-141#Unknown/Copia ( Recon Family Size = 49, Final Multiple Alignment Size = 42 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
$ 
$ cat file2
>rnd-2_family-16#LTR/Copia ( Recon Family Size = 80, Final Multiple Alignment Size = 67 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
>rnd-2_family-9#DNA/PIF-Harbinger ( Recon Family Size = 34, Final Multiple Alignment Size = 27 )
TTTTTTTGGTNAAAACGGCGATTCATACAACTCTAGCGTGAGTACATCCAACAAA
$ 

```

Don't know why I didn't think of that before...

---


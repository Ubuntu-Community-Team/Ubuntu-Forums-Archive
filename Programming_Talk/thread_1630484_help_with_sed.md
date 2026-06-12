---
title: "help with sed"
date: 2010-11-25
forum: Programming Talk
---

### Post by Drenriza on 2010-11-25
I have a server, where on it i have used a command to extract some information. The output is

> ### Start of FILM list
# FILM 
FILM 
FILM 
FILM 
FILM 
FILM 
FILM 
FILM 
### End of FILM list
textI then want to use a series of commands to delete & rename some lines in the output, and then make them permanent. The commands are as follows

```

#sed '1,2d' /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test
#sed '/### End of FILM list/d' /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test
#sed '/text/d' /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test
#sed 's/FILM/#FILM/' /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test

```But how do i make these changes permanent in the text-file? which is called [test]

Hope you know what i mean.
Thanks on advance.

---

### Post by Hippytaff on 2010-11-25
I thought sed overwrote the original, and were permienent changes!? are the hashes removed in the actual script?

---

### Post by Drenriza on 2010-11-25
> **hippytaff said:**
> are the hashes removed in the actual script?

yes :)

I just made the hashes to test the lines one by one and forgot to move when i posted here

> I thought sed overwrote the original, and were permienent changes!?No, aparently sed only writes to the file if you (export) the > output to the text file. but i dont know how to export it, without changing my changes :p if that makes sense.

---

### Post by Hippytaff on 2010-11-25
Cool - Then I will butt out at this point, and let someone with more bash experience advise you :-)

---

### Post by DaithiF on 2010-11-25
sed -i is what you want to make changes in-place to a file.

by the way, more efficient to chain several commands together in a single sed command than run sed multiple times.

e.g.
```
sed -i '1,2d;/### End of FILM list/d;/text/d;s/FILM/#FILM/' yourfile

```

---

### Post by Drenriza on 2010-11-25
> **DaithiF said:**
> sed -i is what you want to make changes in-place to a file.

by the way, more efficient to chain several commands together in a single sed command than run sed multiple times.

e.g.
```
sed -i '1,2d;/### End of FILM list/d;/text/d;s/FILM/#FILM/' yourfile

```

I havnt used sed alot, and dont have the experience to chain the commands together :p

But thanks, i got the result that i wanted

---

### Post by apmcd47 on 2010-11-25
> **Drenriza said:**
> I have a server, where on it i have used a command to extract some information. The output is

I then want to use a series of commands to delete & rename some lines in the output, and then make them permanent. The commands are as follows

```

#sed '1,2d' /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test
#sed '/### End of FILM list/d' /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test
#sed '/text/d' /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test
#sed 's/FILM/#FILM/' /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test

```But how do i make these changes permanent in the text-file? which is called [test]



Hope you know what i mean.
Thanks on advance.

Piping the output of one sed into the next reduces the number of times your file needs to be changed for this one operation:

```
prompt$ < /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test sed '1,2d' | sed '/### End of FILM list/d' | sed '/text/d' | sed 's/FILM/#FILM/' > /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test.new
prompt$ mv test.new test 
```

I think you can use a single sed with -e:

```
prompt$ < /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test sed -e '1,2d' -e '/### End of FILM list/d' -e '/text/d' -e 's/FILM/#FILM/' > /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test.new
prompt$ mv test.new test 
```

and to overwrite the file:
```
prompt$ sed -i.bak -e '1,2d' -e '/### End of FILM list/d' -e '/text/d' -e 's/FILM/#FILM/' /home/cristian/Skrivebord/Scripts/Movie-scripts/igang/test

```will put the original version in the file test.bak

Andrew

---

### Post by Hippytaff on 2010-11-25
apart from the previous posts being far superior to this, this may come in useful in furture. Doing >> will add to a text file rather than > which will just over write it, if that makes sense too!? :-)

---

### Post by Drenriza on 2010-11-25
Is their another option that does the same as -i ?

This is because i work on sometimes old servers, and apparently the -i is not valid on them.

Thanks for the advanced replys, i will definitely look into them and learn :p

---

### Post by Arndt on 2010-11-25
> **Drenriza said:**
> Is their another option that does the same as -i ?

This is because i work on sometimes old servers, and apparently the -i is not valid on them.

Thanks for the advanced replys, i will definitely look into them and learn :p

On other versions of Unix, the -i option to 'sed' may not exist. I think it is specific to GNU sed. Then you have to write the output to a temporary file and then rename that file to the original name:

```
sed something infile >tmpfile
mv tmpfile infile

```

---


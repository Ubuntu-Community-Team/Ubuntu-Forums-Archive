---
title: "Problem with shell script"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by irwingcg on 2013-02-15
hello guys.

I have a problem in a shell script, already tried the solution here in the forum, but to no avail so far.

ps.: I have the same script on 2 machines, one works, the other does not.

-------------------- SCRIPT --------------
#!/bin/bash
MES=`date +%m`
ANO=`date +%Y`
if [ $MES -eq 12 ]; then
ANO_PASTA=$(($ANO+1))
MES_ARQUIVO=01
else
ANO_PASTA=$ANO
MES_ARQUIVO=$(($MES+1))
fi
PASTA_TEMP=/var/www/tgnet/boletos/$ANO_PASTA/temp
PASTA_SEG=/var/www/tgnet/boletos/$ANO_PASTA/segunda-via
PASTA=/var/www/tgnet/boletos/$ANO_PASTA/
ARQUIVO=$PASTA$MES_ARQUIVO.pdf
GRUPO_A_CONVERTER=""
mkdir -p $PASTA
chmod 0777 $PASTA
mkdir -p $PASTA_TEMP
chmod 0777 $PASTA_TEMP
mkdir -p $PASTA_SEG
chmod 0777 $PASTA_SEG
cd $PASTA_TEMP
curl -s -u tgnetSys:senhaDoSys [http://localhost:7979/eng/gera_boleto.php](http://localhost:7979/eng/gera_boleto.php)
for PDF in *.pdf;
do
GRUPO_A_CONVERTER=$GRUPO_A_CONVERTER' '$PDF
done
pdftk $GRUPO_A_CONVERTER cat output $ARQUIVO
for PDF2 in *.pdf;
do
rm $PDF2
done
rmdir $PASTA_TEMP


------- ERROR -------------
gera_boleto.sh: 24: gera_boleto.sh: Syntax error: word unexpected (expecting "do")

---

### Post by sudodus on 2013-02-15
> ```
for PDF in *.pdf;
 do
```

I think you should not have both ; and new line
```

for PDF in *.pdf
do

```
might work better

---

### Post by irwingcg on 2013-02-15
also failed =/

---

### Post by schragge on 2013-02-15
No, semicolon is not a problem, even if it's redundant here.

I guess it's how one of your PDF files is named what makes bash unhappy. Maybe an unusual character like # or parenthesis. Something like this.

Place *set -x* before loop and watch how the script runs.

---

### Post by sudodus on 2013-02-15
> **schragge said:**
> No, semicolon is not a problem, even if it's redundant here.

I guess it's how one of your PDF files is named what makes bash unhappy. Maybe an unusual character like # or parenthesis. Something like this.

Place *set -x* before loop and watch how the script runs.
I see your point :-)

Maybe I can add that it might be a problem with space in a name, try [FONT="Courier New"]"$PDF"[/FONT] instead of [FONT="Courier New"]$PDF[/FONT] and [FONT="Courier New"]"$PDF2"[/FONT] instead of [FONT="Courier New"]$PDF2[/FONT]

---

### Post by schragge on 2013-02-15
No, it's not space. Spaces are valid delimiters in the list.

---

### Post by irwingcg on 2013-02-15
I think the problem lies elsewhere, because this script also did not work, returned the same error.

----SCRIPT -------
#!/bin/bash
for i in 1 2 3 4 5
do
echo "teste $i"
done

---- ERROR ---
ts.sh: 3: ts.sh: Syntax error: word unexpected (expecting "do")

---

### Post by schragge on 2013-02-15
Check permissions of the script, see [thread=1130892]this thread[/thread].

[highlight]Update[/highlight].
Now I think it has nothing to do with permissions either. Ensure that the script doesn't contains **CR** (aka **\r**) characters. Either open it in vim, or do
```

od -c [color=green]script.sh[/color]

```
or try 
```

tr '\r' @ < [color=green]script.sh[/color]

```
and watch for @

---

### Post by irwingcg on 2013-02-15
I'm logged in with User "servidor" and the file has the User "sistema" as owner.

how do I change the file owner?

---

### Post by schragge on 2013-02-15
```

sudo chown servidor *file*

```

---

### Post by irwingcg on 2013-02-15
also did not work, but I recreated the script from the User I'm logged in, and apparently it worked, the script is running, I expect to finish to see if it worked.

---

### Post by schragge on 2013-02-15
Just curious, the hash-bang line says it's a bash script, but judging from the error message you invoked it as
```

[color=green]$[/color] sh [color=blue]script[/color]

```
 Why? While I easily can imagine the opposite, i.e. invoking a */bin/sh* script as
```

[color=green]$[/color] bash [color=blue]script[/color]

``` e.g. in order to get more comprehensible error messages, your way of invoking the script seems very strange and confusing to me.

[highlight]Update.[/highlight]
This actually has nothing to do with the problem, but I'd rewrite your script in more concise manner avoiding the loops at all.
```

#!/bin/bash
MES=`date -d '+1 month' +%m` ANO=`date -d '+1 month' +%Y`
PASTA=/var/www/tgnet/boletos/$ANO
PASTA_TEMP=$PASTA/temp
PASTA_SEG=$PASTA/segunda-via
ARQUIVO=$PASTA/$MES.pdf
mkdir -p -m 0777 $PASTA $PASTA_TEMP $PASTA_SEG
cd $PASTA_TEMP
curl -s -u tgnetSys:senhaDoSys http://localhost:7979/eng/gera_boleto.php
pdftk *.pdf cat output $ARQUIVO
rm -r $PASTA_TEMP

```

---


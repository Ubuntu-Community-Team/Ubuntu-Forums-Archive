---
title: "[SOLVED] How can i read lots of files and find the last post?"
date: 2008-03-27
forum: Programming Talk
---

### Post by hopelessone on 2008-03-27
Hi,

I come from vb6 so don't know much..

i have a folder with 1300 files... it was posts in a forum..

i want to search the files for the last of these:

posted whatever date whatever time
e.g.
posted[COLOR="Red"] 04-30-2000[/COLOR][COLOR="YellowGreen"] 03:17 AM[/COLOR]

<TITLE>[COLOR="DarkOrange"]Whatever[/COLOR] - The Archives</title>

remove the " - The Archives" part

<FONT SIZE="2" face="Verdana, Arial"><B>[COLOR="SeaGreen"]Username[/COLOR]</B>

copy the name of the file[COLOR="Lime"] 003247.html[/COLOR]
add ../Forum6/HTML/

and add them all in 1 file to look like:

<TR>
<TD bgcolor="#F7F7F7">
<IMG SRC="../images/closed.gif" BORDER=0></td>
<TD bgcolor="#F7F7F7"><FONT SIZE="2" FACE="Verdana, Arial">
<A HREF="../Forum6/HTML/[COLOR="Lime"]003247.html[/COLOR]">[COLOR="DarkOrange"]Whatever[/COLOR]</A>
</FONT>
</td>
<td bgcolor="#DEDFDF">
<FONT SIZE="2" FACE="Verdana, Arial">[COLOR="SeaGreen"]Username[/COLOR]</FONT>
</td>
<td align=center bgcolor="#F7F7F7">
<FONT SIZE="2" FACE="Verdana, Arial">1</FONT>
</td>
<td NOWRAP bgcolor="#DEDFDF">
<FONT SIZE="2" FACE="Verdana, Arial">[COLOR="Red"]04-30-2000[/COLOR] <FONT SIZE="2" FACE="Verdana, Arial" COLOR="#800080">[COLOR="YellowGreen"]03:10 AM[/COLOR]</FONT></FONT>
</td></tr>

<TR>
<TD bgcolor="#F7F7F7">
Etc....
</td></tr>

<TR>
<TD bgcolor="#F7F7F7">
Etc....
</td></tr>

How can I achieve this?

thanks for reading.. :)

---

### Post by ghostdog74 on 2008-03-27
not tested, since you didn't provide samples.
```

awk 'BEGIN{ IGNORECASE=1; onefile="newfile.html"}
/posted/{
  date=$2
  time=$3
}
/<TITLE>/{
  gsub(/<TITLE>|<\/TITLE>|- The Archives/,"")
  title=$0
}

END {
    print "<TR>" > onefile
    print "<TD bgcolor=\"#F7F7F7\">" > onefile
    print "<IMG SRC=\"../images/closed.gif\" BORDER=0></td>" > onefile
    print "<TD bgcolor=\"#F7F7F7\"><FONT SIZE=\"2\" FACE=\"Verdana, Arial\">" > onefile
    print "<A HREF=\"../Forum6/HTML/" FILENAME "\">" title "</A>"  > onefile
    print "</FONT>" > onefile
    print "</td>" > onefile
    print "<td bgcolor=\"#DEDFDF\">" > onefile
    print "<FONT SIZE=\"2\" FACE=\"Verdana, Arial\">Username</FONT>" > onefile
    print "</td>" > onefile
    print "<td align=center bgcolor=\"#F7F7F7\">" > onefile
    print "<FONT SIZE=\"2\" FACE=\"Verdana, Arial\">1</FONT>" > onefile
    print "</td>" > onefile
    print "<td NOWRAP bgcolor=\"#DEDFDF\">" > onefile
    print "<FONT SIZE=\"2\" FACE=\"Verdana, Arial\">" date "<FONT SIZE=\"2\" FACE=\"Verdana, Arial\" COLOR=\"#800080\">" time "</FONT></FONT>" > onefile
    print "</td></tr>" > onefile

}' file

```

---

### Post by tgalati4 on 2008-03-27
>man grep
>man perl
>man awk

>grep "Whatever I'm Looking For" *.html > mylist.txt

---

### Post by hopelessone on 2008-03-28
ghostdog74 - I really appreciate what you did for me...(sorry about the no sample file)

the line

/<TITLE>/{
  gsub(/<TITLE>|<\/TITLE>|- The Archives/,"")
  title=$0

Original file:
<TITLE>Whatever - The Archives</title><META HTTP-EQUIV="Pragma" CONTENT="no-cache">

generated file:
<A HREF="../Forum6/HTML/003247.html">Whatever - The  Archives[COLOR="Red"]<META HTTP-EQUIV="Pragma" CONTENT="no-cache">[/COLOR]</A>

Would like:
<A HREF="../Forum6/HTML/003247.html">Whatever</A>

+ just noticed the files sometimes change from "The Archives" to "The BB"

thanks for trying to help me on this...

---

### Post by ghostdog74 on 2008-03-28
provide your sample file!

---

### Post by hopelessone on 2008-03-28
It's the third line

sometimes says:

- The Archives or - The BB

in this case says - The BB

Thanks for helpin..!!

---

### Post by ghostdog74 on 2008-03-28
this is not the original file, right?
it has 
```

<TITLE>Whatever - the BB</title><META HTTP-EQUIV="Pragma" CONTENT="no-cache">

```

if your original file has
```

<TITLE>Whatever - The Archives</title><META HTTP-EQUIV="Pragma" CONTENT="no-cache">

```
then this part
```
gsub(/<TITLE>|<\/TITLE>|- The Archives/,"")
```
will remove the TITLEs and the word "- The Archives" from the line, and gives you "Whatever" as the final title.

because you do not have " - The Archives" in 
```

<TITLE>Whatever - the BB</title><META HTTP-EQUIV="Pragma" CONTENT="no-cache">

```
what you will get is the whole title itself, unchanged

If  "- the BB" is also what you don't need, just add it into gsub 
```

gsub(/<TITLE>|<\/TITLE>|- The Archives|- the BB/,"")

```

---

### Post by hopelessone on 2008-03-28
Wow thats great was trying to get that working...

still gives me [COLOR="Red"]<META HTTP-EQUIV="Pragma" CONTENT="no-cache">[/COLOR] after it though...

any way to trim this off?

thanks..:KS

---

### Post by ghostdog74 on 2008-03-29
```

gsub(/<TITLE>|<\/TITLE>|- The Archives|<META.*\"no-cache\">/,"")

```

---

### Post by hopelessone on 2008-03-29
Ahhh i see how it works now...

Thanks...

i'm trying to figure out how to count how many times  the words posted appears and minus 1 from it...

so far i got:

/posted/{
  date=$6
  time=$7
  am=$8
  [COLOR="Red"]twords += wc +1[/COLOR]

gives me the total posts not -1

thank Q for your patience..

---

### Post by ghostdog74 on 2008-03-29
> **hopelessone said:**
> Ahhh i see how it works now...

Thanks...

i'm trying to figure out how to count how many times  the words posted appears and minus 1 from it...

so far i got:

/posted/{
  date=$6
  time=$7
  am=$8
  [COLOR="Red"]twords += wc +1[/COLOR]

gives me the total posts not -1

thank Q for your patience..
just increment a counter. 

```

/posted/ [
 ...
 ..
 p++
}

```
then print out at the END block

```

END {
 ...
 ... 
 ... 
 print "How many times posted appears : " p - 1
}

```


learn some [shell, awk]("http://www.grymoire.com/Unix/") here.

---

### Post by hopelessone on 2008-03-29
Thanks !!!!

:KS :KS :KS

---

### Post by hopelessone on 2008-03-29
Doh !!!

i just tried to do it for all 1300 files in  the folder..

just gives one posting...and not:

<TR>
<TD bgcolor="#F7F7F7">
Etc....
</td></tr>

<TR>
<TD bgcolor="#F7F7F7">
Etc....
</td></tr>

I changed the last line from }' 001345.html to:

}' *.html

sniff sniff...

Ideas?

---

### Post by ghostdog74 on 2008-03-29
change the ">" to ">>"

---

### Post by hopelessone on 2008-03-29
Hi,

I get the same thing twice, but with a total of 121210 posts with p++.. << how to reset this after each file

you meant this right?

from this** print "<TR>" > onefile** to **print "<TR>" >> onefile**?

thanks

---

### Post by ghostdog74 on 2008-03-29
> **hopelessone said:**
> Hi,

I get the same thing twice, but with a total of 121210 posts with p++.. << how to reset this after each file

store it in an associative array
```

/posted/ {
...
 store[FILENAME]+=1
..
}

```
then at the  END block
```

END {
 ...
 ....
 for ( i in store ) { 
      print "total number of posted for file " i " is " store[i]
 }
}

```
> 
you meant this 

from this** print "<TR>" > onefile** to **print "<TR>" >> onefile**?

thanks

yes, also, since you want to output to only 1 file, you can remove all the "> onefile" , and redirect to the newfile on the command line instead
```

# ./script.sh > onefile

```

you should spend some time going over the materials i gave you.

---

### Post by hopelessone on 2008-03-30
thanks..

i have to do it to all of them so i don't keep getting the same thing twice...

title[FILENAME]=$0 <-----is this correct?

END {
	for ( i in title,store ) {

I'm getting a syntax error on the comma line title,store? whats the separator?

thanks..:popcorn:

---

### Post by ghostdog74 on 2008-03-30
> **hopelessone said:**
> thanks..

i have to do it to all of them so i don't keep getting the same thing twice...

title[FILENAME]=$0 <-----is this correct?


yes

> 
END {
	for ( i in title,store ) {

I'm getting a syntax error on the comma line title,store? whats the separator?

thanks..:popcorn:
you can't use it like that. Check the awk link i gave you for the for loop syntax. Alternative, you can go [here.]("http://www.gnu.org/software/gawk/manual/gawk.html")

---

### Post by hopelessone on 2008-03-30
Hi,

in the links it goes:

for (i in u_count) {
				if (i != "") {
        	        print u_size[i], u_count[i], i;
				}
        }
        for (i in g_count) {
				if (i != "") {
        	        print g_size[i], g_count[i], i;
				}
        }
        for (i in ug_count) {
				if (i != "") {
        	        print ug_size[i], ug_count[i], i;
				}
        }
        for (i in all_count) {
				if (i != "") {
        	        print all_size[i], all_count[i], i;
				}

if i follow these exaples i get each line x 1300 not all together...

I know it's to do with where i put the for command...if i put it at the top i can get one field only...if i put the for command within the other for command i get a huge file...e.g.

for ( i in title ) {
for ( i in user ) {
    		print "<TR>" 
    		print "<TD bgcolor=\"#F7F7F7\">" 
    		print "<IMG SRC=\"../images/closed.gif\" BORDER=0></td>" 
    		print "<TD bgcolor=\"#F7F7F7\"><FONT SIZE=\"2\" FACE=\"Verdana, Arial\">" 
    		print "<A HREF=\"../Forum6/HTML/" FILENAME "\">" title[i] "</A>"  
    		print "</FONT>" 
   		print "</td>" 
   		print "<td bgcolor=\"#DEDFDF\">" 
    		print "<FONT SIZE=\"2\" FACE=\"Verdana, Arial\">" user[i] "</FONT>" 
    		print "</td>" 
    		print "<td align=center bgcolor=\"#F7F7F7\">" 
               etc...
	}
}

so where would be the correct place to put all of them? :confused:

thanks..

---

### Post by hopelessone on 2008-03-30
What about a IF statement within the FOR statement?

for ( i in title ) {
  if(i=i) {
    print "<A HREF=\"../Forum6/HTML/" FILENAME "\">" title[i] "</A>"
    etc...
  title[i]=""
}
}

Worked !!!

---

### Post by hopelessone on 2008-03-30
next i will figure out how to sort from most recent date and time...(any hints?)

thanks ghostdog74 :KS:KS:KS

---

### Post by ghostdog74 on 2008-03-30
> **hopelessone said:**
> next i will figure out how to sort from most recent date and time...(any hints?)

thanks ghostdog74 :KS:KS:KS

pls read the [manual ]("http://www.gnu.org/manual/gawk/html_node/Array-Sorting.html")!

---

### Post by hopelessone on 2008-03-30
so far i got:

END {
	n = asorti(date, time)
        for (i = 1; i <= n; i++) {
	for ( i in title ) {

	  if (i=i) {
    		print "<TR>" 
                etc...

doesn't seem to work...workin on it... :popcorn:

---

### Post by hopelessone on 2008-03-30
hi,

does awk get all the values for all the files first then write to file? or each file then write to file?

thanks

---

### Post by hopelessone on 2008-03-31
i still don't get why this wont work?

dates are either:
12-25-1999
12-25-99

END {
   n = asort(date)
     for (i = 1; i <= n; i++)
        
	for ( i in title ) {

	  if (i=i) {

    		etc...
    		print "<FONT SIZE=\"2\" FACE=\"Verdana, Arial\">" date[i] " <FONT SIZE=\"2\" FACE=\"Verdana, Arial\" COLOR=\"#800080\">" time[i] " " am[i] "</FONT></FONT>" 
etc...

---

### Post by hopelessone on 2008-03-31
Given up...will do the rest by hand...

anyway thanks ...learned alot...

---


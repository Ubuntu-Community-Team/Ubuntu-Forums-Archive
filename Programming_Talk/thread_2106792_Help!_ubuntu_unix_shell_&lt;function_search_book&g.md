---
title: "Help! ubuntu unix shell &lt;function search_book&gt;"
date: 2013-01-20
forum: Programming Talk
---

### Post by vincdec on 2013-01-20
Below is my coding for search function.

```

{
    echo -n "Title: "
        read title
        echo ""
    echo -n "Author: "
        read author
        echo ""

    if [ "$title" = "" ] && [ "$author" = "" ] ; then
    echo "Error! Please enter Book Title or Book Author..."
    return
    fi

    by_title=`grep "$title" "BookDB.txt" | wc -l`

    x=$by_title

    if [ "$title" != "" ] && [ "$author" = "" ] && [ "$by_title" -le "0" ] ; then
    echo "No such existing Book Title - '$title' found!"
    fi

    if [ "$title" != "" ] && [ "$author" = "" ] && [ "$by_title" -gt "0" ] ; then
    echo "Found $x record(s):"
    grep "$title" "BookDB.txt" | tr ':' ',' | awk '{ print }'
    fi
}
```I have a problem for search function.

[COLOR=#000000][FONT=times new roman]e.g.[/FONT][/COLOR]
Title: _Mary_

Author: [COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]They will print out the record(s) as follows:[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Found 2 record(s):
Catch Me If You Can,**_Mary_** Ann,23.60,6,2
Happy Day,**_Mary_** Ann,12.99,194,104[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]As you can see they search for Mary which is an author.
[/FONT][/COLOR]

[COLOR=#000000][FONT=times new roman]Is there any way to restrict the column, to search the title column only  rather than the whole line?[/FONT][/COLOR]

---

### Post by greenpeace on 2013-01-20
If your data is formatted regularly, and reliably, you can look for occurrences of the string between the start of the line, and the first comma... 

Perhaps try something like the following:

```
grep -i "^[^,]*$title" BookDB.txt
```

the -i option makes the grep search case-insensitive, so "mary" would match "MARY" and "Mary".

I tested it as follows:

```
gp@mariachi:~/test$ cat BookDB.txt 
Catch Me If You Can,Mary Ann,23.60,6,2
Happy Day,Mary Ann,12.99,194,104
Mary,author,12.89,123,123

gp@mariachi:~/test$ grep -i "^[^,]*mary" BookDB.txt
Mary,author,12.89,123,123
```

Of course you'll have problems if there are commas in the book titles... because the expression assumes that there won't be!

hope it helps!

---

### Post by vincdec on 2013-01-20
Thanks, I ran your code. Well, the same problem still occurred during the 2nd input.

```
    echo -n "Title: "
        read title
        echo ""
    echo -n "Author: "
        read author
        echo ""

    if [ "$title" = "" ] && [ "$author" = "" ] ; then
    echo "Error! Please enter Book Title or Book Author..."
    return
    fi

    by_title=`grep "$title" "BookDB.txt" | wc -l`

    x=$by_title

    if [ "$title" != "" ] && [ "$author" = "" ] && [ "$by_title" -le "0" ] ; then
    echo "No such existing Book Title - '$title' found!"
    fi

    if [ "$title" != "" ] && [ "$author" = "" ] && [ "$by_title" -gt "0" ] ; then
    echo "Found $x record(s):"
    grep -i "^[^,]*$title" "BookDB.txt"
    fi

```Results:
<1st input> was a success!
Title: mary

Author: 

No such existing Book Title - 'mary' found!

while the
<2nd input> ( ':' did not changed to ',') & ('Mary' <author> is still printed out)
Qns:Why do they catch Mary in $title and output _Mary_ Ann<author>?

Title: _Mary_

Author: 

Found 2 record(s):
<title>:<author>:<price>:<stock>:<sold>
Catch Me If You Can:_Mary_ Ann:23.60:6:2
Happy Day:_Mary_ Ann:12.99:194:104

<3rd input> (case insensitive doesn't work on word with spacing)
Title: happy day

Author: 

No such existing Book Title - 'happy day' found!

<4th input>(success!)
Title: Happy Day

Author: 

Found 1 record(s):
Happy Day:Mary Ann:12.99:194:104

---

### Post by steeldriver on 2013-01-20
if you have a text file containing structured records, then imho you would be far better using something like awk to search them in a structured way based on records + fields, rather than just grepping for bits and pieces of text

---

### Post by vincdec on 2013-01-20
Well I don't really get what you are trying to say? Something like

```
awk  -F: '{if ($1=='$title' && $2=='$author') <do something> } ' BookDB.txt`
```

---

### Post by steeldriver on 2013-01-20
if your BookDB.txt file looks like this

```
$ cat BookDB.txt
Catch Me If You Can:Mary Ann:23.60:6:2

Catch Me If You Can:Peggy Sue:23.60:6:2

Happy Day:mary ann:12.99:194:104

```then something like this

```
$ awk 'BEGIN {RS="";FS=":"}; $2 ~ /[Mm]ary/ { print; }' BookDB.txt 
Catch Me If You Can:Mary Ann:23.60:6:2
Happy Day:mary ann:12.99:194:104

```

---

### Post by vincdec on 2013-01-20
I test and tried your code. These came out. Not sure what went wrong.

```
user@ubuntu904desktop:~/Desktop$ cat 1.txt
Catch Me If You Can:Mary Ann:23.60:6:2
Catch Me If You Can:Peggy Sue:23.60:6:2
Happy Day:mary ann:12.99:194:104

user@ubuntu904desktop:~/Desktop$ awk 'BEGIN {RS="";FS=":"}; $2 ~ /[Mm]ary/ { print; }' 1.txt 
Catch Me If You Can:Mary Ann:23.60:6:2
Catch Me If You Can:Peggy Sue:23.60:6:2
Happy Day:mary ann:12.99:194:104

user@ubuntu904desktop:~/Desktop$ 

```

---

### Post by steeldriver on 2013-01-20
The difference is I used a record separator RS="" which works when the records are separated by a blank line - if they are separated by plain old single newlines then try

```
awk 'BEGIN {[COLOR=Red]RS="\n"[/COLOR];FS=":";}; $2 ~ /[Mm]ary/ { print; }' BookDB.txt
```As always the solution gets easier the better you define the problem

---

### Post by vincdec on 2013-01-20
> **steeldriver said:**
> The difference is I used a record separator RS="" which works when the records are separated by a blank line - if they are separated by plain old single newlines then try

```
awk 'BEGIN {[COLOR=Red]RS="\n"[/COLOR];FS=":";}; $2 ~ /[Mm]ary/ { print; }' BookDB.txt
```As always the solution gets easier the better you define the problem

RS is record separator. FS is filed separator. 

So let me get this straight. I can replace [Mm]ary with $title <which is the input from the user>, am I correct to say that?

---

### Post by steeldriver on 2013-01-20
my bad, I was trying something to make the case-insensitivity less clunky - it turns out that if you use 'gawk' instead of 'awk' you can specify case-insensitivity globally by setting IGNORECASE=1 in the BEGIN stanza i.e.

```
$ [COLOR=Red]gawk[/COLOR] 'BEGIN {RS="\n";FS=":";[COLOR=Red]IGNORECASE=1[/COLOR]}; $2 ~ /[COLOR=Red]Mary[/COLOR]/ { print; }' BookDB.txt 
Catch Me If You Can:[COLOR=Red]Mary[/COLOR] Ann:23.60:6:2
Happy Day:[COLOR=Red]mary[/COLOR] ann:12.99:194:104
```If you use plain 'awk' you need to do something like I showed with the [Mm] character range - or convert everything e.g. using toupper()

---

### Post by steeldriver on 2013-01-20
... also you'll probably want to know about the awk -v option for passing variable values into the awk expression e.g. 

```
$ gawk -v author="mary" -v title="catch" 'BEGIN {RS="\n";FS=":";IGNORECASE=1}; \
> $1 ~ title && $2 !~ author { print; }' \
> BookDB.txt
Catch Me If You Can:Peggy Sue:23.60:6:2

```

---

### Post by vincdec on 2013-01-20
> **steeldriver said:**
> my bad, I was trying something to make the case-insensitivity less clunky - it turns out that if you use 'gawk' instead of 'awk' you can specify case-insensitivity globally by setting IGNORECASE=1 in the BEGIN stanza i.e.

```
$ [COLOR=Red]gawk[/COLOR] 'BEGIN {RS="\n";FS=":";[COLOR=Red]IGNORECASE=1[/COLOR]}; $2 ~ /[COLOR=Red]Mary[/COLOR]/ { print; }' BookDB.txt 
Catch Me If You Can:[COLOR=Red]Mary[/COLOR] Ann:23.60:6:2
Happy Day:[COLOR=Red]mary[/COLOR] ann:12.99:194:104
```If you use plain 'awk' you need to do something like I showed with the [Mm] character range - or convert everything e.g. using toupper()

Oh I see! I learnt something new! AWESOME! :D

Alright here is the thing. On terminal, it's not a problem. I'm trying to insert/register that line into a _.sh_ by reading the input $title. 

I did this, which it ain't printing any record(s):
```
    by_title=`grep "$title" "BookDB.txt" | wc -l`
    x=$by_title


    if [ "$title" != "" ] && [ "$author" = "" ] && [ "$by_title" -le "0" ] ; then
    echo "No such existing Book Title - '$title' found!"
    fi

    if [ "$title" != "" ] && [ "$author" = "" ] && [ "$by_title" -gt "0" ] ; then
    echo "Found $x record(s):"    
    awk 'BEGIN {RS="\n"; FS=":"} ; $1==$title { print; }' "BookDB.txt"
  
    fi 
```

---

### Post by steeldriver on 2013-01-20
You need to do it in 2 stages - assign the shell variable to an awk variable using -v, and then use the awk variable inside awk:

```
$ author="mary"; title="catch" # shell variables
$ gawk -v author="$author" -v title="$title" \
> 'BEGIN {RS="\n";FS=":";IGNORECASE=1}; $1 ~ title && $2 !~ author { print; }' \
> BookDB.txt
Catch Me If You Can:Peggy Sue:23.60:6:2

```

---


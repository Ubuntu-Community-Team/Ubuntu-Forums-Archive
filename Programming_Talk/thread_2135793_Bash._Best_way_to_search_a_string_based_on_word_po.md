---
title: "Bash. Best way to search a string based on word position?"
date: 2013-04-15
forum: Programming Talk
---

### Post by fr0s7y on 2013-04-15
I'm building some more options into my address book application, written in bash.

At the minute I can search for an entry in my .txt based on the users input, its pretty much a wildcard search though, i'll explain.

The data is stored in the following format:

[forename] ; [surname] ; [1st line of address] ; [postcode] ; [phone number]

when I run 

```
searchOutput=$(grep -i $searchTerm*. $ADDRESSBOOK | sort)

        echo "$searchOutput"
```

I receive relevant results although it means I can pretty much type *anything *in ie. the letter 'd' and it will provide results.

I would like to give the user the option of searching by forename or surname or postcode etc.

I have read up on greps many commands though I'm struggling with the best way to read in the data.

In a previous thread the data was pulled into an array, would this be the best method? ie. is there a way to re-grep grepped data stored in an array?

Surely there is a simple grep command to search for the nth word on a single line?

And I'm pretty sure the above grep command isn't wholly correct as a search string anyway, just a hunch :(


edit:

this command is actually better, I can pull strings matching exact words now:

```
searchOutput=$(grep -w -i $searchForename. $ADDRESSBOOK | sort)

        echo "$searchOutput"
```

Result! so -w matches whole words, how to specify the position of the word?

I also have a feeling the ';'s in the text file may interfere with this function.

---

### Post by schragge on 2013-04-15
> **fr0s7y said:**
> Surely there is a simple grep command to search for the nth word on a single line? which is called *awk* :). E.g. searching by first names:
```

awk -F';' '$1~/'"$searchForename"/ "$ADDRESSBOOK"

```

---

### Post by Vaphell on 2013-04-15
you'd do yourself a favor if you looked at python because you are slowly going beyond the scope of shell. More elaborate data structures quickly become a pain in the back.

that said...

test file:
```
John;Smith;111 WutWutWut Ave;21111;6666
Jonathan;White;23 Downing Str;12345;111
Ann;Watson;Junkyard;34567;999888777
```

```
$ declare -A field
$ field=( [all]=0 [forename]=1 [surname]=2 [address]=3 [postcode]=4 [phone]=5 )
$ search_in_address_book() { awk -F';' -v n=${field[$1]} -v s=${2,,} 'tolower($n)~s { print; }' "$3";  }

$ search_in_address_book all j addressbook.txt
John;Smith;111 WutWutWut Ave;21111;6666
Jonathan;White;23 Downing Str;12345;111
Ann;Watson;Junkyard;34567;999888777

$ search_in_address_book forename jo addressbook.txt
John;Smith;111 WutWutWut Ave;21111;6666
Jonathan;White;23 Downing Str;12345;111

$ search_in_address_book forename joh addressbook.txt
John;Smith;111 WutWutWut Ave;21111;6666
```

i wrapped awk in shell function for convenience, but you can use it directly

```
awk -F';' -v n=${field[$search_by]} -v s="${phrase,,}" 'tolower($n)~s { print; }' "$address_book";
```
in awk $0 is the whole line, $1+ are individual fields (field separator set to ; with -F)
associative array field translates word to number so it's not necessary to use numbers all the time, all=>0 so awk gets to check if lowercase($0) matches given phrase anywhere, forename will do the same with $1 only, etc.

---

### Post by fr0s7y on 2013-04-15
arrrgh, a new command to get to grips with!

This is how im (trying..) to integrate it into my existing code,

this is the script thus far...
```

#!/bin/bash -       
#title           :find.sh
#description     :This script will find an entry in the Address Book
#date            :March 2013
#version         :0.1
#==============================================================================
ADDRESSBOOK=~/Documents/Address-Book/add_data.txt

export ADDRESSBOOK

declare -A field
field=( [all]=0 [forename]=1 [surname]=2 [address]=3 [postcode]=4 [phone]=5 )
search_in_address_book() { awk -F';' -v n=${field[$1]} -v s=${2,,} 'tolower($n)~s { print; }' "$3";  }

exit=0
wildcard(){
while [ $exit -ne 1 ]
        do

        
        echo -n "Enter something for me to find> "

        read searchTerm
    if [ "$searchTerm" = "exit" ]
    then 
        exit=1
    else

        searchOutput=$(grep -i $searchTerm*. $ADDRESSBOOK | sort)

        echo "$searchOutput"
    fi
    done

exit 0
}
searchOptions(){
while [ $exit -ne 1 ]
        do
        echo " ============= Type a number corresponding to the option you want. ============= 
         
                        1. Perform a wildcard search
                    2. Search based on (first) name
                        3. Search by Surname
                4. Search By Postcode
                         "
    echo -n "-----------------> Yes/No: "
    read searchType
    if [ "$searchType" = "1" ]
    then    
        wildcard 
        
    elif [ "$searchType" = "2" ] 
    then
        searchForename
    elif [ "$searchType" = "3" ] 
    then
        searchSurname
    elif [ "$searchType" = "4" ] 
    then
        searchPostcode
    else

    echo " I dont understand"
    
    fi
done
}

searchForename(){


while [ $exit -ne 1 ]
        do

        
        echo -n "Enter forename>"

        read searchForename
    if [ "$searchForename" = "exit" ]
    then 
        exit=1
    else
         
        searchOutput=$(search_in_address_book forename $searchForename $ADDRESSBOOK)
        
        echo $searchOutput

        
    fi
    done

exit 0
}





echo "=============================== Search a Record ==============================="
echo "==============================================================================="
echo "=================== Enter a search Term, Type 'exit' to exit ==================

"

searchOptions
```

sorry if its a bit long i thought it would make more sense to see how the script ties together, I figured i would place each menu item into its own function, is this the best way, I know in other languages there
are switch/case statements etc.

So far the output is null.

---

### Post by Vaphell on 2013-04-15
what is that wildcard option supposed to do exactly? support regular expressions?

---

### Post by fr0s7y on 2013-04-15
> **Vaphell said:**
> what is that wildcard option supposed to do exactly? support regular expressions?

Um, does it not perform a search using whatever the user inputs and then adds the '*' wildcard to the end of it? so i could type in say 'fr' and it would show all results beginning with 'fr'.

Or am I gravely mistaken.

Surely just grep $searchTerms $ADDRESSBOOK is wildcard enough?

how do i delete a duplicate post???

---

### Post by fr0s7y on 2013-04-15
Um, does it not perform a search using whatever the user inputs and then adds the '*' wildcard to the end of it? so i could type in say 'fr' and it would show all results beginning with 'fr'.

Or am I gravely mistaken.

Surely just 

```
grep $searchTerms $ADDRESSBOOK
``` is wildcard enough?

---

### Post by Vaphell on 2013-04-15
*grep $searchTerms file* will return anything that has the expression, you don't have to add filler. I'd also quote the variable, space would mess things up. Also grep works with regular expressions which are governed by different rules than globs used with files so your current code is slightly wrong. 
'something*' in glob is equivalent to 'something.*' in regex. In glob * is a standalone symbol for char sequence, while in regular expression * is merely a quantifier attached to the element before it. Dot is a symbol for any-char so .* = any-char any-number-of-times, [abc]* = a-or-b-or-c any-number-of-times

Awk code achieves the same result you want from grep too (as shown in my examples: 'J' alone was enough to return rows) so grep becomes kinda superfluous
If you want match from start in regexes: ^pattern, at the end: pattern$, exactly: ^pattern$


Another thing: if you don't work with files directly never leave * hanging around outside the quotes because you will have a glob.
*grep $var* file* will try to expand unquoted $var* to the list of files that match the description of [value of $var][anything] and then pass the list to grep. It will work if there are no matches (glob will fall back to the literal string), but when there are, you will get a very different grep than the one you planned.

---

### Post by fr0s7y on 2013-04-15
> **Vaphell said:**
> *grep $searchTerms file* will return anything that has the expression, you don't have to add filler. I'd also quote the variable, space would mess things up. Also grep works with regular expressions which are governed by different rules than globs used with files so your current code is slightly wrong. 
'something*' in glob is equivalent to 'something.*' in regex. In glob * is a standalone symbol for char sequence, while in regular expression * is merely a quantifier attached to the element before it. Dot is a symbol for any-char so .* = any-char any-number-of-times, [abc]* = a-or-b-or-c any-number-of-times

Awk code achieves the same result you want from grep too (as shown in my examples: 'J' alone was enough to return rows) so grep becomes kinda superfluous
If you want match from start in regexes: ^pattern, at the end: pattern$, exactly: ^pattern$


Another thing: if you don't work with files directly never leave * hanging around outside the quotes because you will have a glob.
*grep $var* file* will try to expand unquoted $var* to the list of files that match the description of [value of $var][anything] and then pass the list to grep. It will work if there are no matches (glob will fall back to the literal string), but when there are, you will get a very different grep than the one you planned.

```

grep '$searchTerms' $ADDRESSBOOK
```
or 
```

grep $'searchTerms' $ADDRESSBOOK
```

I just assumed * was a universal expression for wildcard, curse you mySQL.

That explains the outright weird grep results I was getting, thanks.

Still struggling to get awk to run though, just repeats the prompt without pulling any results. Between yours and **schragge**'s examples i havent been successful in getting it work with the current code :(

---

### Post by schragge on 2013-04-15
Pay attention to quoting. You examples do quite different things.
```
grep '$searchTerms'
``` searches for the literal string [COLOR=blue]$searchTerms[/COLOR], most probably not what you want.
```
grep $'searchTerms'
``` searches for the literal string [COLOR=blue]searchTerms[/COLOR]. This kind of quoting is used in bash to interpolate escape sequences introduced with backslash:
```
$'one\ntwo'
``` is equivalent to
```
'one
two'
```
What you want is double-quotes to interpolate variables:
```
grep "$searchTerms" "$ADDRESSBOOK"
```

---


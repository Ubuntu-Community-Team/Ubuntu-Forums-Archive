---
title: "Is it possible to colorize text that is output with cat or tac?"
date: 2016-06-03
forum: Programming Talk
---

### Post by rebeltaz on 2016-06-03
I know how to use escape characters and tput with echo, but that doesn't work line by line with the tac output of a standard text file. I guess I could pipe the output of tac into a new file and then echo that out line by line, but that seems more complicated than it needs to be. 

Let's say my text file reads:
```

https://www.site.com/product-page.php?id=1228850
  >Mosiso MacBook Case for iPad Pro 12.9/MacBook...     $1.95      
https://www.site.com/product-page.php?id=1228766
  >Cotton Bath Towel Pool Towel Red - Easy Care ...        $6.11      
https://www.site.com/product-page.php?id=1228763
  >Cotton Bath Towel Pool Towel Brown - Easy Car...        $6.11      
https://www.site.com/product-page.php?id=1228741
  >Barry's Whiskey Glass Drink Cup, XL 10 oz Dri...        $0.75 

```

I am using several grep and sed commands (to process the original file down to that) and then tac to print that to the screen in reverse order. What I would like is for the URL to be a light grey color, the product name another color (not sure what color yet) and the price yet another color. 

Thanks.

---

### Post by steeldriver on 2016-06-03
It's usually the source program (i.e. what's on the LHS of the pipe) that determines what happens - for example, grep doesn't colorize its output when it detects that its output is going to something other than a tty

Depending exactly what your sequence of commands is, you may be able to override that behavior explicitly e.g. for grep, setting the `--color=always` option

```

grep --color=always PATTERN file | tac

```

---

### Post by rebeltaz on 2016-06-06
> **steeldriver said:**
> It's usually the source program (i.e. what's on the LHS of the pipe) that determines what happens - for example, grep doesn't colorize its output when it detects that its output is going to something other than a tty

Depending exactly what your sequence of commands is, you may be able to override that behavior explicitly e.g. for grep, setting the `--color=always` option

```

grep --color=always PATTERN file | tac

```

OK... I tried that, but it wants to colorize the whole line. What I would like this to look like is this:

```
  
  [COLOR="#0000FF"]>Barry's Whiskey Glass Drink Cup, XL 10 oz Dri...[/COLOR]        [COLOR="#FF0000"]$0.75[/COLOR]
[COLOR="#D3D3D3"]https://www.site.com/product-page.php?id=1228741[/COLOR]

  [COLOR="#0000FF"]>Cotton Bath Towel Pool Towel Brown - Easy Car...[/COLOR]        [COLOR="#FF0000"]$6.11 [/COLOR]     
[COLOR="#D3D3D3"]https://www.site.com/product-page.php?id=1228763[/COLOR]

  [COLOR="#0000FF"]>Cotton Bath Towel Pool Towel Red - Easy Care ...[/COLOR]        [COLOR="#FF0000"]$6.11[/COLOR]      
[COLOR="#D3D3D3"]https://www.site.com/product-page.php?id=1228766[/COLOR]

  [COLOR="#0000FF"]>Mosiso MacBook Case for iPad Pro 12.9/MacBook...[/COLOR]     [COLOR="#FF0000"]$1.95[/COLOR]      
[COLOR="#D3D3D3"]https://www.site.com/product-page.php?id=1228850[/COLOR]

```

I guess I am going to have to read each line and echo it out, aren't I?

---

### Post by steeldriver on 2016-06-06
I dunno - it's hard to suggest anything without seeing what commands you're actually using

---

### Post by rebeltaz on 2016-06-06
> **steeldriver said:**
> I dunno - it's hard to suggest anything without seeing what commands you're actually using

That, I can help you with :) :

```

#! /bin/bash

# Quick and Dirty Script used to pull  new items from 
# AMZ Review Trader every 10 minutes and display the 
# results in a terminal window along with the prices
#
# edit the "product_group" to modify categories selected
# CTRL-click on product link to open in browser
#
# coded by Derek Tombrello (rebeltaz - KM4JAG)
# email = rebeltaz@RobotsAndComputers.com

while :
   do
      clear
      rm amzrt-wget.txt amzrt-tempfile.txt amzrt-newlist.txt
      wget --post-data "domain=www.amazon.com&product_group=Appliances*Industrial+%26amp%3B+Scientific*Appstore+for+Android*Arts%2C+Crafts+%26amp%3B+Sewing*Automotive*Kitchen+%26amp%3B+Dining*Movies+%26amp%3B+TV*Musical+Instruments*Books*Office+Products*Camera+%26amp%3B+Photo*Patio%2C+Lawn+%26amp%3B+Garden*Computers*Software*Electronics*Sports+%26amp%3B+Outdoors*Grocery+%26amp%3B+Gourmet+Food*Toys+%26amp%3B+Games*Health+%26amp%3B+Personal+Care*Home+%26amp%3B+Kitchen&page=0&sort=Newest+products+first&search=&best_discounts=false" https://www.amzreviewtrader.com/product_grid.php -O amzrt-wget.txt

      grep -e '<p class="title"  onclick="show_product' -e '<\/span>' amzrt-wget.txt > amzrt-tempfile.txt

      sed -i '/<span class="currency">.*<\/span>/d' amzrt-tempfile.txt

      sed -i ':a;N;$!ba;s/<\/p>\r\n//g' amzrt-tempfile.txt

      sed -i 's/<\/span>//g' amzrt-tempfile.txt

      grep '<p class="title"  onclick="show_product' amzrt-tempfile.txt | grep -o  '([0-9]*).*' | sed 's/(//' | sed 's/)//' | sed 's/^/https:\/\/www.amzreviewtrader.com\/product-page.php?id=/' | sed 's/" >/\r\n   >/' > amzrt-newlist.txt

      sed -i 's/  / /g' amzrt-newlist.txt

      tac amzrt-newlist.txt | sed 's/ >/\r\n   >/'

      echo ""
      echo "   ... waiting 10 minutes for next update ... "
      sleep 10m
   done


```

---

### Post by rebeltaz on 2016-06-06
I guess something like this:

```

      tac amzrt-newlist.txt | sed 's/ >/\r\n   >/' > amzrt-bwtext.txt
      sed 's/>/\033[0;34m>/g' amzrt-bwtext.txt
      sed 's/\$/\033[0;33m\$/g' amzrt-bwtext.txt
      sed 's/http/\033[0;37mhttp/g' amzrt-bwtext.txt

```

and then echo that file line by line?

Nope... I replaced:

```
      tac amzrt-newlist.txt | sed 's/ >/\r\n   >/' 
```

with:

```

      tac amzrt-newlist.txt | sed 's/ >/\r\n   >/' > amzrt-bwtext.txt

      sed -i 's/>/>\\033\[0;34m/g' amzrt-bwtext.txt
      sed -i 's/\$/\$\\033\[0;33m/g' amzrt-bwtext.txt
      sed -i 's/http/\\033\[0;37mhttp/g' amzrt-bwtext.txt

      while read line
         do
            echo -e "${line}"
         done < amzrt-bwtext.txt

```

That adds the correct codes to the text file, but in addition to messing up the two lines text, one blank line format, more importantly, it prints the actual codes instead of acting on them:

```

>033[0;34mFor Fitbit Alta Accessory Band, Silicone Repl...        $033[0;33m1.96      
033[0;37mhttps://www.amzreviewtrader.com/product-page.php?id=1247363

>033[0;34mFor Fitbit Alta Accessory Band, Silicone Repl...        $033[0;33m1.97      
033[0;37mhttps://www.amzreviewtrader.com/product-page.php?id=1247364

>033[0;34mTattify Gradient Nail Wraps - Love Like a Sun...        $033[0;33m0.99      
033[0;37mhttps://www.amzreviewtrader.com/product-page.php?id=1247367

>033[0;34mEA AromaCare Eucalyptus Essential Oil 120ml/4...        $033[0;33m3.00      
033[0;37mhttps://www.amzreviewtrader.com/product-page.php?id=1247370

   ... waiting 10 minutes for next update ... 
^C

```

---

### Post by steeldriver on 2016-06-06
I don't really understand what you're trying to do, however I think your issue is that sed doesn't "do" backslash escaped sequences like that (unlike, say `echo -e`)

There are some suggestions here: [http://unix.stackexchange.com/questions/19248/bash-color-output-fails](http://unix.stackexchange.com/questions/19248/bash-color-output-fails)

For example using bash's $'   ' string expansion construct:

```

echo '>Description in blue and $7.99 in red' | sed $'s/\(>[^$]*\)\($.*\)/\033[1;34m\\1\033[1;31m\\2\033[m/'

```

or
```

sed $'s/\(>[^$]*\)\($.*\)/\033[1;34m\\1\033[1;31m\\2\033[m/' amzrt-newlist.txt | tac

```

(note the need to double-escape the capture group references \\1 and \\2 in place of the usual \1 and \2 when you have everything inside the $'   ' sequence)

---

### Post by rebeltaz on 2016-06-06
That actually works! Well, with the exception of the last two line for some reason, which remain white, but I can fix that.

I looked at the link you provided but I don't think it really explained what you did. I'm not the kind who is just looking for someone to write my homework for me. I truly want to learn. If possible, could you explain what that command is doing? I don't know/understand the "capture group references" for example. 

I really appreciate your time and patience!

---

### Post by steeldriver on 2016-06-06
In sed (and other regular expression tools) we can capture parts of a pattern using parentheses and then substitute them back in to the replacement text

The first group (from left to right) gets numbered 1 and the second 2 and so on, and in sed the substitutions are done using references like \1, \2 (in other tools - like perl - you will see $1, $2 etc.)

Here's a version that may be clearer

First we define some handy string expansion variables for the colors:
```

BLU=$'\033[1;34m'; RED=$'\033[1;31m'; CLR=$'\033[m'

```

Then we can match everything from a (literal) > up to but not including (literal) $ as group #1, and the remainder of the line (including the $) into capture group #2, and re-substitute them between our "color codes":
```

echo '>Description in blue and $7.99 in red' | sed "s/\(>[^$]*\)\($.*\)/$BLU\1$RED\2$CLR/"

```

Note the change from single quotes to double quotes around the sed expression - which allows our variables "$BLU", "$RED" etc. to be expanded to their values by the shell.

Hope this helps - fyi this is my go-to reference for regular expressions: [http://www.regular-expressions.info/refcapture.html](http://www.regular-expressions.info/refcapture.html)

---

### Post by rebeltaz on 2016-06-06
That does makes sense. Thank you. I always wondered why I couldn't get ()$1 substitutions to work in sed like they do in rename. That is another mystery solved for me!

I bookmarked that link. I think I have actually used that site before when trying to figure out regex.

---

### Post by rebeltaz on 2016-06-06
One thing... what is the $ before the variable definition and before the first (single line) sed command?

Well, I thought I understood it. When I try:

```
sed $"s/\(>[^$]*\)\($.*\)\(https.*\)/$DESC\1$COST\2$LINK\3/" amzrt-bwtext.txt | cat
```

where DESC = blue code, COST = red color, and LINK = grey color, everything turns back white. If I use the code like you had it:

```
 sed $"s/\(>[^$]*\)\($.*\)/$DESC\1$COST\2$LINK/" amzrt-bwtext.txt | cat 
```

It does give me the right output (except the "...waiting..." text is in grey, too) . Just curious why adding the third group doesn't work? I have to use a grey color instead of clear to get it to work like I expect.


-=[ EDIT ]=- 

Got it:

```
sed $"s/\(>[^$]*\)\($.*\)/$DESC\1$COST\2/" amzrt-reversed.txt | sed $"s/\(http.*\)/$LINK\1$CLR/" | sed $"s/\(FREE\)/$FREE\1$CLR/"
```

Since the http was on different line, I had to work it separately. Thank you again!

---

### Post by steeldriver on 2016-06-06
I don't know what the construct is called exactly - the bash manual just says

```

    Words of the form $'string' are treated specially.  The word expands to
    string,  with backslash-escaped characters replaced as specified by the
    ANSI C standard.

```

---


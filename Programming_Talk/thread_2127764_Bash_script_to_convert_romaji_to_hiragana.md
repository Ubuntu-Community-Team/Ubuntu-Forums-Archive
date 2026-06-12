---
title: "Bash script to convert romaji to hiragana"
date: 2013-03-21
forum: Programming Talk
---

### Post by Stonecold1995 on 2013-03-21
I started learning Japanese not too long ago, and I'm tired of Anki, so I'm making my own, simple flash card program.  I want to be able to have the option to read the Japanese in romaji (e.g. "mizu" instead of "water"), or have it automatically converted to hiragana (e.g. "&#12415;&#12378;" instead of "mizu").  Is there a way for me to use bash to convert the romaji to hiragana (or possibly katakana)?

Basically, how hiragana works is that each letter represents a syllable, such as "da" (&#12384;), with a single vowel, usually preceeded by a single consonant.  So any word in romaji must be able to be broken down by the consonants, so "anata" must be separated into "a na ta", with the break at the start of the consonant, and then turned into &#12354;&#12394;&#12383;.  However there are a few problems that make this more difficult.  Hiragana like "shi" (&#12375;) have two consonant letters, but only one consonant sound, and the bash script must be able to recognize that.  Even worse, in some situations the hiragana are pronounced differently depending on context, such as "wa" (&#12431;) being spelled as "ha" (&#12399;) if it's being used as a particle, such as the "wa" in the sentence "anata wa shin setsu desu" (&#12354;&#12394;&#12383;&#12399;&#12375;&#12435;&#12379;&#12388;&#12391;&#12377;) being spelled with "ha" (&#12399; instead of &#12431;), as if it were "anata ha shin setsu desu".

Is there any (relatively easy) way to use bash to do this, or is it just too complicated for a simple script and I should just suck it up and create a third array for hiragana?
 
```
#!/bin/bash

# &#12525;&#12540;&#12510;&#23383;array
nihongo[1]='Itadakimasu'
nihongo[2]='Oishii'
nihongo[3]='Mama'
nihongo[4]='Natto'
nihongo[5]='Kanpai'
nihongo[6]='Hajimemasite'
nihongo[7]='Hajimeru'
(etc...)

# English array
english[1]='Always used before eating, roughly means "I am about to receive".'
english[2]='Delicious'
english[3]='I don'\''t like this food (it'\''s so-so).'
english[4]='Fermented soy beans with a very strong smell.'
english[5]='Equivalent to the English "Cheers!" said before a drink.'
english[6]='Roughly "Nice to meet you." (lit. "for the first time").'
english[7]='To begin'
(etc...)

# There must be the same number of Japanese and English translations
if [ ${#nihongo
[*]} -ne ${#english
[*]} ]; then
    echo 'Error, length of array variables "nihongo" and "english" do not match.'
    exit 1
fi

correct=0
incorrect=0

# Display stats and exit
function finished() {
    if ! [ $correct -eq 0 -a $incorrect -eq 0 ]; then
        clear
        let total=$correct+$incorrect
        percent=$(echo "scale=2; ($correct/$total)*100" | bc)
        echo -e "Correct: $correct\nIncorrect: $incorrect\nTotal: $total\nPercent: $percent%"
    else
        echo
    fi
    tput cnorm normal
    exit 0
}
trap finished SIGHUP SIGINT SIGTERM

while true; do
    clear
    last_rand=$rand
    # Make sure the same card isn't done twice in a row
    until [ "$rand" != "$last_rand" ]; do
        rand=$(shuf -i 1-${#nihongo
[*]} -n 1)
    done
    echo "Nihongo: ${nihongo[$rand]}"
    read
    tput cup 1 # Dirty workaround because I'm too stupid to not echo a new line when enter is pressed
    echo "English: ${english[$rand]}"
    unset yn
    until [ "$yn" = y -o "$yn" = n ]; do
        echo
        read -p "Did you get it right? [y/n] " yn
        if [ "$yn" = y ]; then
            ((correct++))
            echo 'Good job!'
            sleep 1
        elif [ "$yn" = n ]; then
            ((incorrect++))
            echo 'Oh well, maybe next time.'
            sleep 1
        fi
    done
done
```

---

### Post by sisco311 on 2013-03-21
Thread moved to **Programming Talk. **

There is a perl module which can do this: [http://search.cpan.org/~dankogai/Lingua-JA-Kana-0.07/lib/Lingua/JA/Kana.pm](http://search.cpan.org/~dankogai/Lingua-JA-Kana-0.07/lib/Lingua/JA/Kana.pm)

---

### Post by Vaphell on 2013-03-22
if python is more to your liking
romkan

[https://pypi.python.org/pypi/romkan](https://pypi.python.org/pypi/romkan)

```
sudo pip install romkan
```
there is also ruby version of romkan, directly in the repos

you can easily inline it in your bash script
```
$ txt="anata wa shin setsu desu"
$ python -c "import sys; import romkan; print( romkan.to_hiragana(sys.argv[1]))" "$txt"
&#12354;&#12394;&#12383; &#12431; &#12375;&#12435; &#12379;&#12388; &#12391;&#12377;
```
or create a small py script that translates the string

```
#!/usr/bin/env python

import sys
import romkan
print( romkan.to_hiragana( sys.argv[1] ).encode('utf8') ) # had to use encode because it complained
```

btw, you should put your dictionary in a separate file in some easily parseable format where data is separated by some obscure char, eg
```
Itadakimasu|Always used before eating, roughly means "I am about to receive"|commentary
Oishii|Delicious|or something else
```

```
#!/bin/bash

while IFS="|" read -r jp en comment
do
  nihongo+=( "$jp" )
  english+=( "$en" )
  ...
done < dict.txt

for(( i=0; i<${#nihongo[@]}; i++ ))
do
  printf "%s (%s): %s\n" "${nihongo[i]}" "$( python romaji2hiragana "${nihongo[i]}" )" "${english[i]}"
done

```

```
$ ./jp_dict.sh 
Itadakimasu (&#12356;&#12383;&#12384;&#12365;&#12414;&#12377;): Always used before eating, roughly means "I am about to receive"
Oishii (&#12362;&#12356;&#12375;&#12356;): Delicious
```
as a bonus you can have multiple easily customizable dicts that can be read by the parametrized script with no effort.

---

### Post by Stonecold1995 on 2013-03-22
> **Vaphell said:**
> if python is more to your liking
romkan

[https://pypi.python.org/pypi/romkan](https://pypi.python.org/pypi/romkan)

Yes thank you.

> **Vaphell said:**
> btw, you should put your dictionary in a separate file in some easily parseable format where data is separated by some obscure char, eg
```
Itadakimasu|Always used before eating, roughly means "I am about to receive"|commentary
Oishii|Delicious|or something else
```

```
#!/bin/bash

while IFS="|" read -r jp en comment
do
  nihongo+=( "$jp" )
  english+=( "$en" )
  ...
done < dict.txt

for(( i=0; i<${#nihongo[@]}; i++ ))
do
  printf "%s (%s): %s\n" "${nihongo[i]}" "$( python romaji2hiragana "${nihongo[i]}" )" "${english[i]}"
done

```

Yeah I know hard-coding is bad practise, and I'm planning to use a separate file as you say.  The problem is that I tend to spend more time on the script than I actually do actually using it to learn, so if it's in the same file it'll help me remember more easily because I'll see it more often.  Because putting it in a separate file is so easy, I'm planning on leaving that until the very end, when the rest of the script has all the features I want it to.

---

### Post by Stonecold1995 on 2013-03-22
Hm, I just tried romkan and it's not working correctly.  As I said in the OP, it can't just blindly translate, it has to use at least a little contextual information to tell what to do.

```
alex@kubuntu:~$ txt='Sore wa dosa shimasen'
alex@kubuntu:~$ python -c "import sys; import romkan; print(romkan.to_hiragana(sys.argv[1]))" "$txt"
&#12381;&#12428; &#12431; &#12393;&#12373; &#12375;&#12414;&#12379;&#12435;
```

The output *should* be this:
```
&#12381;&#12428;**&#12399;**&#12393;&#12373;&#12375;&#12414;&#12379;&#12435;
```

Hiragana has no spaces, and the "wa" (&#12431;) should have been written as "ha" (&#12399;) instead, because it's being used alone as a particle rather than part of a different word.

It seems romkan only does a very literal (and very erroneous) translation.  That's something I could have easily done in bash alone, my problem is that there are a few rules hiragana follows that aren't as easy to make a bash script with.

---

### Post by Vaphell on 2013-03-22
are there many such exceptions?
you could pass the string through some regex that would replace standalone 'wa' to 'ha' and then do the dumb translation eg

```
$ txt='wa wawa' #some junk
$ temp=$( echo "$txt" | sed -r 's/\<wa\>/ha/g' )
$ python -c "import sys; import romkan; print( romkan.to_hiragana(sys.argv[1]).encode('utf8'))" "$temp"
&#12399; &#12431;&#12431;

$ txt='Sore wa dosa shimasen'
$ temp=$( echo "$txt" | sed -r 's/\<wa\>/ha/g' )
$ python -c "import sys; import romkan; print( romkan.to_hiragana(sys.argv[1]).encode('utf8'))" "$temp"
&#12381;&#12428; &#12399; &#12393;&#12373; &#12375;&#12414;&#12379;&#12435;
```

you could compile a file with *sed* expressions and feed it to *sed* via *-f* switch

if preprocessing with a bunch of easy rules is not viable you could always have an additional array only for exceptions and use it when it's not empty
```
$ nihongo='wa wawa'
$ exception=''
$ [ -z "$exception" ] && python -c "import sys; import romkan; print( romkan.to_hiragana(sys.argv[1]).encode('utf8'))" "$nihongo" || echo "$exception"
&#12431; &#12431;&#12431;
$ nihongo='wa wawa'
$ exception='&#12399; &#12431;&#12431;'
$ [ -z "$exception" ] && python -c "import sys; import romkan; print( romkan.to_hiragana(sys.argv[1]).encode('utf8'))" "$nihongo" || echo "$exception"
&#12399; &#12431;&#12431;
```

the advantage of data separated from code shows up in this case. Now to extend script you have to not only add the code by also add additional arrays with much more unwieldy syntax than in case of simple well formatted external file where relevant pieces of data are next to each other. No off-by-one errors and other crap plaguing programmers.

---

### Post by Stonecold1995 on 2013-03-22
> **Vaphell said:**
> are there many such exceptions?
you could pass the string through some regex that would replace standalone 'wa' to 'ha' and then do the dumb translation eg

```
$ txt='wa wawa' #some junk
$ temp=$( echo "$txt" | sed -r 's/\<wa\>/ha/g' )
$ python -c "import sys; import romkan; print( romkan.to_hiragana(sys.argv[1]).encode('utf8'))" "$temp"
&#12399; &#12431;&#12431;

$ txt='Sore wa dosa shimasen'
$ temp=$( echo "$txt" | sed -r 's/\<wa\>/ha/g' )
$ python -c "import sys; import romkan; print( romkan.to_hiragana(sys.argv[1]).encode('utf8'))" "$temp"
&#12381;&#12428; &#12399; &#12393;&#12373; &#12375;&#12414;&#12379;&#12435;
```

I don't think there are too many exceptions, but more context is needed than "is it alone or part of a word".  While that's a good heuristic, I think there are other times when "wa" is alone but is NOT spelled as "ha" because it is not functioning as a particle in the same way. So "wa" is only written as &#12399; if it's being used as a topic marker, but if it's used at the end of a sentence to show an emotional connection, it's written as &#12431;.

However, lots of romaji will not add spaces between it and the word it relates to, for example, "konbanwa" is spelled &#12371;&#12435;&#12400;&#12435;&#12399; (ko nn ba nn ha), because the "wa" and the end is actually a topic marker, but it's not often spelled "konban wa" in romaji so the script wouldn't change the "wa" to "ha" as it should.

So I don't think simple rules would work, something like romkan would be good if only it actually used some kind of japanese dictionary.

---

### Post by Vaphell on 2013-03-22
such ambiguities are nasty to program around, it's hard to do anything smart with when context matters that much.
Having an accurate list of exceptions would be useful to estimate viability of possible solutions. 

are there cases where wa becomes ha even at the end of the sentence? 
are there many such cases where wa is glued to the end of the word and becomes ha either way?

---

### Post by trent.josephsen on 2013-03-22
You keep saying "I think ... I don't think ... I think". That's too vague. You must define the problem before you can expect to find a solution. I don't know any Japanese, so I couldn't say how hard this problem is going to be. Maybe you could find out whether it's possible to exhaustively list all the exceptions, or determine from syntax alone whether they apply -- those are questions for a Japanese language expert, not for a programmer.

Can you list the rules and the exceptions completely and concisely in English? That would be a good place to start. If not, well, you're out of luck anyway.

Have you tried the Perl module? Does it do the same thing as the Python one?

---

### Post by Stonecold1995 on 2013-03-23
> **Vaphell said:**
> are there cases where wa becomes ha even at the end of the sentence? 
Yes, with words like "konbanwa".

> **Vaphell said:**
> are there many such cases where wa is glued to the end of the word and becomes ha either way?
There are multiple types of romaji, some glue many things together, some don't (e.g. "konbanwa" is almost always one word in romaji, but "watashi wa" is not as commonly spelled "watashiwa").


> **trent.josephsen said:**
> Can you list the rules and the exceptions completely and concisely in English? That would be a good place to start. If not, well, you're out of luck anyway.
I couldn't, but there may be a dictionary somewhere that could.  There must be because Google Translate is able to do it with good accuracy (but for most other things Google Translate is terrible at languages, *especialy* Japanese).

> **trent.josephsen said:**
> Have you tried the Perl module? Does it do the same thing as the Python one?
Ah, I forgot.  I'll try that.  If that doesn't work, are there any other such ways to do this?

I'll rephrase my original question a little...  I don't care if it's in *pure* bash, for all I care it could use Google Translate (although I heard they shut down their API).

I'm not able to list too many exceptions, I *am* still fairly new to Japanese after all, so if I can't provide much more information I guess I'll just look around more forums maybe I'll find something I could run under Wine.  Perhaps there's a dictionary somewhere I can find.

---

### Post by Stonecold1995 on 2013-03-23
> **sisco311 said:**
> Thread moved to **Programming Talk. **

There is a perl module which can do this: [http://search.cpan.org/~dankogai/Lingua-JA-Kana-0.07/lib/Lingua/JA/Kana.pm](http://search.cpan.org/~dankogai/Lingua-JA-Kana-0.07/lib/Lingua/JA/Kana.pm)
How do I put Perl in a bash script?  Or do I have to write a Perl script (I don't know any Perl though)?

---

### Post by Vaphell on 2013-03-23
just like with python
inline: python -c / perl -e
or external .py /.pl scripts

some knowledge of perl would be nice because it's not exactly intuitive when compared to python, but i think the general idea would be the same: pass the string, use a function provided by a module on it, voila.

on that page you have short snippets showing how to use it.

---

### Post by ntzrmtthihu777 on 2013-03-23
Whole nother note, but I stumbled onto this post by chance, and as an anime-loving, japanese learning ubuntu-user, I should greatly like to make your acquaintance, &#23506;&#30707;&#12373;&#12435; :D
Also, this Vaphell character is very knowledgable, he was of great assistance (read: did 99% of) in making a tool for UTAU-associated file conversion.

---

### Post by Stonecold1995 on 2013-03-23
> **Vaphell said:**
> just like with python
inline: python -c / perl -e
or external .py /.pl scripts

some knowledge of perl would be nice because it's not exactly intuitive when compared to python, but i think the general idea would be the same: pass the string, use a function provided by a module on it, voila.

on that page you have short snippets showing how to use it.
How do I install it?  It says to run "perl Makefile.PL" but the only downloadable file is Kana.pm.

---

### Post by Vaphell on 2013-03-24
[http://www.cpan.org/modules/INSTALL.html](http://www.cpan.org/modules/INSTALL.html)

i went with cpan+cpanm <module>

```
sudo cpan App::cpanminus
sudo cpanm Lingua::JA::Kana
```

but...

```
#! /usr/bin/perl -w

use strict;
use Encode;
use Lingua::JA::Kana;

my @str = ( "anata wa shin setsu desu", "konbanwa" );
foreach (@str)
{
  print $_.' => '.encode_utf8( Lingua::JA::Kana::romaji2hiragana($_) )."\n"; 
}
```

```
$ ./test.pl
anata wa shin setsu desu => &#12354;&#12394;&#12383; &#12431; &#12375;&#12435; &#12379;&#12388; &#12391;&#12377;
konbanwa => &#12371;&#12435;&#12400;&#12435;&#12431;
```

---

### Post by schragge on 2013-03-24
If that perl module doesn't do what you want, you can try ruby, too. There are two packages for it in the official Ubuntu repositories: [ruby-romkan]("http://0xcc.net/ruby-romkan/index.html.en") and [libsuikyo-ruby1.8]("http://prime.sourceforge.jp/src/suikyo/ruby/doc/"). Having been created by a Japanese, I guess ruby should have decent Japanese language conversion tools.
```

[COLOR=green]$[/COLOR] irb1.8
[COLOR=green]irb(main):001:0>[/COLOR] $KCODE='e'
[COLOR=green]=> "e"
irb(main):002:0>[/COLOR] require 'romkan'
[COLOR=green]=> true
irb(main):003:0>[/COLOR] 'konbanwa'.to_kana
[COLOR=green]=> "&#12371;&#12435;&#12400;&#12435;&#12431;"
irb(main):004:0>[/COLOR] 'anata wa shin setsu desu'.to_kana
[color=green]=> "&#12354;&#12394;&#12383; &#12431; &#12375;&#12435; &#12379;&#12388; &#12391;&#12377;"
irb(main):005:0>[/color]

```

---

### Post by Vaphell on 2013-03-24
it seems to be the same romkan package python has but made for ruby and the result is the same for 'wa' &#12431; that is supposed to be 'ha' &#12399;

---

### Post by schragge on 2013-03-24
Yep, you're right. I also get the same results with suikyo, only that it removes all spaces. I've tried it with *romaji* conversion table. Below are all conversion tables suikyo installs:
```

[COLOR=#008000]$[/COLOR] ls /usr/share/suikyo/conv-table/
[COLOR=#008000]ascii-wideascii        kana                    skk-mark
azik                   kana_reverse            skk-mark_reverse
azik-all               kana-romaji             tcode
azik-all_reverse       katakana-halfkatakana   tcode-dvorak
azik_reverse           katakana-hiragana       tcode-dvorak_reverse
egg-mark               kuten                   tcode_reverse
egg-mark_reverse       kuten_reverse           tutcode
halfkatakana-hiragana  romaji                  tutcode_reverse
halfkatakana-katakana  romaji-hepburn_reverse  wideascii-ascii
hiragana-halfkatakana  romaji-kana
hiragana-katakana      romaji_reverse[/COLOR]

```TBH, I don't know what most of them mean.

---

### Post by Vaphell on 2013-03-24
i guess these are conversions between 2 native writing schemes, between codepages and different romanization rules. Usual mess with huge syllabic/picturesque writing systems.

---

### Post by Stonecold1995 on 2013-03-24
I think I know what the problem is...  If these were made specifically for the Japanese, it would make sense that it doesn't automatically convert.  When typing Japanese on a computer, you'd type "konban*ha*" and would know it's pronounced "wa", but for someone like me who is NOT Japanese, I read romaji the way it's pronounced, as konban*wa*.

So if these modules are strictly for Japanese people converting characters from a western keyboard to hiragana, then that explains it.  I think what I'd need is something designed for people learning Japanese.

Well, if nothing like that's out there maybe I should just use only hiragana.  Romaji is a bad habit to get into if you use it too often anyways...

I suppose this is kind of like someone from Japan going to a Japanese forum and asking for a script which converts katakana to romaji so he can learn English, but all the scripts out there are designed for English use specifically.  Of course the script won't know how to convert &#12467;&#12531;&#12500;&#12517;&#12540;&#12479; to "computer", because &#12467;&#12531;&#12500;&#12517;&#12540;&#12479; is "konpyuta" in romaji.

Thanks for the help anyways.

---


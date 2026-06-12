---
title: "Replace declinated phrases"
date: 2009-05-28
forum: Programming Talk
---

### Post by rubystallion on 2009-05-28
Hi

I am supposed to replace the occurrence of a German word in several documents (replace "Anzeige" with "Angebot").

Two aspects make this problem time consuming:
1. The word "Anzeige" has different meanings, so not every occurrence should be replaced. 
2. Several other words in the sentence often have to be changed, too, because "Anzeige" is feminine and "Angebot" is neuter.

Examples: 
Anzeige der Anzeige --> Anzeige des Angebots
zu der Anzeige --> zu dem Angebot

How can I approach this task more efficiently? I'm thinking about recording some editor macros for the most frequent cases, how would you do it?


Thanks in advance

rubystallion

---

### Post by Zugzwang on 2009-05-28
Search for all occurrences of "Anzeige" using your favorite editor and replace everything by hand. Even if you create some rules for the most common cases, you will almost surely forget about some exceptions where the rule must not be applied, rendering your approach erroneous.

---

### Post by soltanis on 2009-05-28
Use cool predictive things like Hidden Markov Models or Bayesian chains (note: I haven't the faintest how you actually do this).

---

### Post by nvteighen on 2009-05-28
And use a language with decent regexp support. IMO, the best for this would be Perl.

---

### Post by Elfy on 2009-05-28
Thread reopened following pm - for the moment I am convinced ;)

> it sounds suspiciously like that <homework>, but it's actually the most boring internship assignment ever. My boss noticed that when he searched for "Angebot" in the requirements tool, he didn't find all the requirements, because for some there was written "Anzeige" instead of "Angebot". Now he wants me to replace all of these occurrences, but by hand it's rather slow and boring
 

---

### Post by rubystallion on 2009-06-03
Sorry I forgot to answer for such a long time. Although Zugzwang might be right that just manually replacing everything would be the fastest solution, I actually used editor macros to decrease manual effort and managed to replace every occurrence. Still it took me two working days :(

For anyone, who's interested, here's what I thought of:

I wanted to have simple key mapping rules for every grammatical case, singular/plural and definitive/indefinitive/no article. Even though there is a lot of redundancy in the regexps, this makes the key combinations easier to remember for me. What the regexps basically do is find an occurrence of the stem Anzeige and the article closest before it, then change 
1. the declinated form of Anzeige to the declinated form of Angebot. 
2. the declinated article

For the concerned articles the 4th case equals the 1st case, so I didn't use separate key mappings for it. Also I noticed, that often the word directly before an occurrence of Anzeige needs to have a new suffix, so I wrote a key mapping to jump right there. Another special case is compound nouns like "Anzeigengestaltung", which must be transformed to "Angebotsgestaltung". 
For the keybindings I used:
first key: q
second key: q,w,e: with article and {definitive sg, definitive pl, indefinitive)
second key: a,s: without article and {singular, plural}
third key: q,w,e: {1st/4th case, 2nd case, 3rd case}

```
map qqq :s/\([Dd]\)ie\>\(\%(\%(\<[Dd]ie\>\)\@!.\)\{-}\)Anzeige/\1as\2Angebot/
map qqw :s/\([Dd]\)er\>\(\%(\%(\<[Dd]er\>\)\@!.\)\{-}\)Anzeige/\1es\2Angebots/
map qqe :s/\([Dd]e\\|[Zz]u\)r\>\(\%(\%(\%([Dd]e\\|[Zz]u\)r\)\@!.\)\{-}\)Anzeige/\1m\2Angebot/

map qwq :s/\([Dd]\)ie\>\(\%(\%(\<[Dd]ie\>\)\@!.\)\{-}\)Anzeigen/\1ie\2Angebote/
map qww :s/\([Dd]\)er\>\(\%(\%(\<[Dd]er\>\)\@!.\)\{-}\)Anzeigen/\1er\2Angebote/
map qwe :s/\([Dd]\)en\>\(\%(\%(\<[Dd]en\>\)\@!.\)\{-}\)Anzeigen/\/1en\2Angeboten/

map qeq :s/\([Ee]\)ine\>\(\%(\%(\<[Ee]ine\>\)\@!.\)\{-}\)Anzeige/\1in\2Angebot/
map qew :s/\([Ee]\)iner\>\(\%(\%(\<[Ee]iner\>\)\@!.\)\{-}\)Anzeige/\1ines\2Angebots/
map qee :s/\([Ee]\)iner\>\(\%(\%(\<[Ee]iner\>\)\@!.\)\{-}\)Anzeige/\1inem\2Angebot/

map qaq :s/\([Aa]\)nzeige/\1ngebot/
map qaw :s/\([Aa]\)nzeige/\1ngebots/
map qae :s/\([Aa]\)nzeige/\1ngebot/

map qsq :s/\([Aa]\)nzeigen/\1ngebote/
map qsw :s/\([Aa]\)nzeigen/\1ngebote/
map qse :s/\([Aa]\)nzeigen/\1ngeboten/

map n /Anzeige
map o ngea
map z gg"+yG
map ] ggdG"+P
map qf fn;rsqaq
map qr ^osqaq
```

Hope this can convince people that it's not homework and maybe even help some ;-)

With kind regards

rubystallion

---


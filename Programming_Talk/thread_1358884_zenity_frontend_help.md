---
title: "zenity frontend help"
date: 2009-12-18
forum: Programming Talk
---

### Post by forgetclosure on 2009-12-18
i'm trying to create some front-ends to some random command-line programs just for ease of use. i've never used any programming language before and even messing around with the command line in this way is kind of different for me, but i haven't been able to get this to work.. can anyone possibly help me out with this?

this is a front-end for bchunk that i've been trying to make. bchunk's correct syntax is as follows: bchunk [options(-r,-p,-w,-s)] <image.bin> <image.cue> <basename>

```
#!/bin/bash

optionsConvert=~

  while [ "$optionsConvert" != "" ]; do
    optionsConver=$(zenity 

cueConvert=~

  while [ "$cueConvert" != "" ]; do
    cueConvert=$(zenity --file-selection --title "Pick The *.cue File" --file-filter=*.cue);

binConvert=~

  while [ "$binConvert" != "" ]; do
    binConvert=$(zenity --file-selection --title "Pick The *.bin File" --file-filter=*.bin);

baseNameConvert=~

  while [ "$baseNameConvert" !="" ]; do
    baseNameConvert=$(zenity --entry --text="Enter The Base Name For The Outputted Files");

      if [ "$cueConvert" != "" || "$binConvert" != "" || "$baseNameConvert" != "" ]; then
        bchunk $optionsConvert "$cueConvert" "$binConvert" "$baseNameConvert"

```

i just don't fully understand the proper way of going about this, but hopefully someone can show me how to do this. thanks in advance for any help! :)

---

### Post by forgetclosure on 2009-12-21
hello?

---


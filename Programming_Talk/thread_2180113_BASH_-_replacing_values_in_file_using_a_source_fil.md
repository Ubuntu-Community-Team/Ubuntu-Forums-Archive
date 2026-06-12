---
title: "BASH - replacing values in file using a source file"
date: 2013-10-11
forum: Programming Talk
---

### Post by majikins2 on 2013-10-11
Hi

I have a file which has values in each line:

MP304,d40000
MP310,ff0000
etc

I have another file which as the first value in it and is unique in the  file(not repeated).  I need to replace a string with the second value  above. The second file contents is as follows[IMG]http://linux.unix.com/images/smilies/frown.gif[/IMG]snippet)

<g
         transform="translate(-312.51946,80.94618)"
         id="MP302"
         style="fill:#ff0000;fill-opacity:1">
        <title
           id="title4028">Msukaligwa</title>
        <path
           d="m 1282,344 1,-1 1,0 1,0 3,0 1,0 1,0 1,0 1,1 1,1 -1,2 -1,0  1,0 0,1 1,0 0,1 1,1 0,1 -2,0 -2,0 0,1 -1,0 0,1 1,3 0,1 1,1 -1,1 -2,1  -1,0 -1,1 -1,-1 0,-1 -1,0 -1,-1 -1,0 -1,0 -1,0 -1,0 -1,0 -1,0 0,1 -1,0  -1,1 -1,0 -1,1 -1,0 0,1 -1,0 1,1 1,1 1,1 0,1 1,0 0,1 1,0 1,1 1,0 1,0 2,0  1,0 0,1 -1,0 -1,0 -1,0 -1,1 0,1 0,1 -1,0 1,0 0,1 -1,0 0,1 -1,0 0,1 0,-1  0,1 -1,0 -1,0 -1,0 0,1 -1,0 -1,0 1,0 0,1 -1,0 -1,0 -1,0 -1,0 -1,0 -1,0  0,1 0,-1 0,1 -1,0 -1,0 -1,0 -1,0 -1,0 0,1 0,1 -1,2 -1,0 -2,0 -2,0 -1,0  -1,0 -1,0 -2,0 0,1 0,1 1,1 -1,0 -1,0 -1,-2 -1,0 -1,0 0,-1 0,-1 -1,0 0,-2  2,-1 -1,-1 -1,-2 -1,1 -2,-2 -2,0 0,-1 -1,0 0,1 -1,0 -1,-1 -1,0 -1,0  -1,1 0,1 -1,2 0,1 -1,0 -1,0 -1,0 0,1 -1,0 0,1 0,-1 0,1 -1,0 0,-1 0,1  -1,0 0,-1 0,1 -1,0 0,-1 -1,0 0,1 1,0 -1,0 0,1 1,0 -1,0 -1,0 0,-1 -1,0  0,-1 1,-1 0,-1 0,-1 0,-1 0,-1 0,-1 1,0 0,-1 0,-1 0,-1 1,-1 -1,0 -1,1  -1,0 -1,0 -1,0 -1,-1 -1,0 -1,0 -1,0 -1,0 -2,0 -1,0 -1,-1 -1,0 -1,0 -1,0  0,-1 -1,0 0,-1 0,-1 0,-1 0,-1 0,-1 0,-2 -1,0 -1,0 0,-1 1,0 0,-1 0,-1  0,-1 0,-1 0,-1 -1,0 -1,-1 -1,0 -1,0 -1,0 0,-1 -1,-1 -1,-1 -1,0 0,-1 -1,0  0,-1 1,0 1,-2 -1,0 -1,0 -1,0 -1,0 -1,0 0,-1 0,-1 0,-1 0,-1 1,0 1,0 1,0  1,0 0,-1 1,-1 1,0 -1,-1 2,0 1,0 1,0 0,-1 1,0 1,0 1,0 1,0 1,0 1,0 2,-1  1,0 0,-1 1,-1 2,1 1,1 0,-1 2,-1 1,-1 1,0 0,1 1,1 0,1 1,1 0,-1 1,-1 1,0  1,0 1,0 1,0 1,0 1,0 1,0 1,1 1,0 0,1 1,-1 1,0 0,-1 1,0 0,-1 2,0 0,-1 1,0  1,1 1,0 2,0 0,1 1,0 1,0 1,0 1,0 0,1 0,1 0,1 1,0 1,-1 1,-1 1,-2 0,1 1,0  1,0 1,-1 1,0 2,0 2,-1 1,-1 0,1 1,1 0,1 1,0 1,-1 -1,-1 1,-2 2,1 1,1 1,0  1,0 3,2 1,1 1,0 1,0 1,0 1,-1 1,0 1,0 1,0 1,-1 1,0 0,1 1,1 1,2 0,1 0,-1  0,1 0,-1 0,1 -1,2 0,2"
           id="path446"
           style="fill:#ff0000;fill-opacity:1" />
      </g>
      <g
         transform="translate(-312.51946,80.94618)"
         id="MP303"
         style="fill:#d40000;fill-opacity:1">
        <title
           id="title4034">Mkhondo </title>
        <path
           d="m 1279,409 -2,0 -1,0 -1,0 -1,0 -1,0 -1,1 -1,0 -1,1 -2,1  -1,0 -1,0 0,-1 0,1 -1,0 -1,0 -1,-1 -1,-1 -1,0 -1,0 1,-1 0,-1 -1,-1 -1,0  1,-1 1,-1 1,0 1,0 1,0 1,-1 0,-1 0,-2 1,0 -1,-1 1,-1 0,-1 0,-1 -1,-2  -1,-1 -1,-1 -1,1 -1,0 0,1 -1,1 -1,0 -1,1 -1,0 -1,-1 0,-1 0,-1 0,-2 0,-1  0,-1 -1,-1 0,-1 0,-1 -1,-1 0,-1 1,-3 2,0 2,0 1,0 1,-2 0,-1 0,-1 1,0 1,0  1,0 1,0 1,0 0,-1 0,1 0,-1 1,0 1,0 1,0 1,0 1,0 1,0 0,-1 -1,0 1,0 1,0 0,-1  1,0 1,0 1,0 0,-1 0,1 0,-1 1,0 0,-1 1,0 0,-1 -1,0 1,0 0,-1 0,-1 1,-1 1,0  1,0 1,0 0,-1 -1,0 -2,0 -1,0 -1,0 -1,-1 -1,0 0,-1 -1,0 0,-1 -1,-1 -1,-1  -1,-1 1,0 0,-1 1,0 1,-1 1,0 1,-1 1,0 0,-1 1,0 1,0 1,0 1,0 1,0 1,0 1,1  1,0 0,1 1,1 1,-1 1,0 2,-1 1,-1 -1,-1 0,-1 2,1 2,0 1,0 1,1 0,2 0,1 0,2  0,1 0,2 0,1 0,1 0,1 0,1 0,1 0,1 0,1 0,1 0,1 0,1 0,1 0,1 0,1 0,1 0,1 1,0  0,1 0,1 0,1 1,0 0,-1 1,0 0,-1 1,0 1,0 1,-1 1,0 0,-1 0,-1 1,2 0,1 0,2 1,0  0,1 1,0 0,1 1,0 0,1 1,0 0,1 1,0 0,1 1,0 0,1 0,1 0,1 0,1 -1,0 0,1 0,1  0,1 0,1 2,1 2,3 2,1 1,1 1,1 1,1 1,1 1,1 0,1 1,1 2,2 1,0 4,2 1,0 3,1 1,0  -1,0 0,1 -1,0 0,1 -1,1 -1,1 -2,2 0,1 -1,0 0,1 -1,1 -1,1 -2,-1 -1,0 0,-1  -1,0 0,-1 -1,0 -1,0 0,1 -1,0 0,-1 -1,0 0,1 -1,0 0,1 0,-1 -1,0 0,1 -1,0  0,-1 -1,0 0,1 -1,0 -1,0 -1,0 0,1 0,-1 -1,0 0,1 -1,0 0,-1 0,-1 -1,0 0,-1  0,-1 0,-1 -1,0 -1,0 -1,0 0,1 -1,0 0,-1 -1,0 0,1 0,1 0,1 0,-1 0,1 -1,0  0,1 0,-1 -1,0 -1,0 0,1 0,-1 1,0 -1,0 0,-1 0,1 -1,0 0,-1 0,-1 -1,0 0,1  0,-1 0,-1 0,1 -1,0 -1,0 0,1 0,-1 -1,0 0,-1 1,0 -1,0 0,-1 0,1 -1,0 0,-1  -1,0 -1,0 0,-1 -1,0 -1,0 -1,1 -1,0 -1,0 -1,0 -1,1 -1,0 0,1 -1,0 -1,0  -1,0 0,1 -1,0 0,-1 -1,0 -1,0 0,-1 0,-1 -1,0 -1,-1 2,-2 -1,-1 1,0 1,-2  0,-1 1,-1 1,-1"
           id="path449"
           style="fill:#d40000;fill-opacity:1" />
      </g>
      <g
         transform="translate(-312.51946,80.94618)"
         id="MP304"
         style="fill:#d40000;fill-opacity:1">
        <title
           id="title4040">Pixley Ka Seme</title>
        <path
           d="m 1265,400 1,1 -1,0 0,2 0,1 -1,1 -1,0 -1,0 -1,0 -1,1 -1,1  1,0 1,1 0,1 -1,1 1,0 1,0 1,1 1,1 1,0 1,0 0,-1 0,1 1,0 1,0 2,-1 1,-1 1,0  1,-1 1,0 1,0 1,0 1,0 2,0 -1,1 -1,1 0,1 -1,2 -1,0 1,1 -2,2 1,1 1,0 0,1  0,1 -1,0 -1,0 0,-1 -1,0 0,1 -1,0 -1,0 0,1 0,-1 0,1 -1,0 0,-1 0,1 -1,0  0,-1 -1,0 0,-1 0,-1 0,-1 0,-1 -1,0 -1,0 0,1 0,-1 -1,0 -1,0 -1,0 1,0 0,1  0,1 -1,0 0,1 -1,0 -1,0 -1,-1 0,1 -1,0 0,1 -1,0 -1,0 0,1 0,1 0,1 0,1 -1,0  -1,0 -1,0 0,1 -1,0 0,-1 0,-1 -1,0 -1,0 -1,0 0,1 -1,0 0,1 -1,0 -1,0 0,1  0,1 -1,0 -1,-1 -1,0 0,-1 -1,0 0,-1 -1,0 -1,0 -1,0 0,1 -1,0 -1,0 -1,1  -1,0 0,-1 -1,0 -1,0 0,-1 -1,0 -1,0 0,-1 -1,0 -1,0 -1,0 0,1 -1,0 0,1 -1,0  0,-1 -1,0 0,1 -1,0 -1,0 -1,0 0,1 0,1 -1,0 0,1 -1,0 0,1 0,1 -1,0 0,1  -1,0 0,-1 -1,0 -1,0 0,-1 -1,0 -1,0 -1,0 -1,0 0,1 -1,0 1,0 -1,0 1,0 0,1  -1,0 1,0 -1,1 1,0 0,1 -1,0 -1,0 1,0 0,1 -1,0 -1,0 0,-1 0,1 0,-1 0,1 0,-1  0,1 0,-1 -1,0 0,1 -1,0 -1,0 -1,0 0,-1 -1,1 0,-1 0,-1 0,-1 -1,0 -1,0  0,-1 0,-1 -1,0 -1,0 0,-1 0,-1 0,-1 -1,0 0,-1 0,1 -1,0 0,-1 1,0 -1,0 0,-1  0,1 -1,0 0,-1 0,-1 -1,0 -1,0 0,-1 1,0 0,-1 -1,0 0,1 0,-1 -1,0 0,-1 0,-1  0,-1 -1,0 1,0 -1,0 0,-1 0,1 0,-1 -1,0 1,0 -1,0 0,-1 -1,0 0,-1 -1,0 1,-1  1,-1 1,0 3,-3 -1,-1 1,0 1,0 1,0 1,1 1,0 0,-1 1,-1 0,-1 0,-1 0,-1 1,-1  1,0 1,-1 1,0 1,0 0,-1 -1,-1 1,0 0,-1 1,-2 1,0 0,-1 0,-1 0,-1 0,-1 0,-1  0,-1 1,0 0,-1 0,-2 0,-1 0,-1 -1,-1 0,-1 1,0 1,0 1,0 0,-1 0,1 1,0 0,-1  1,0 0,-1 0,1 1,0 0,1 0,-1 1,0 0,-1 1,0 0,1 1,0 0,1 0,-1 1,0 1,0 0,-1  -1,0 0,-1 1,0 0,1 0,-1 1,0 -1,0 0,-1 1,0 0,1 1,0 0,1 1,0 0,-1 1,0 -1,0  0,-1 1,0 -1,0 1,0 -1,0 0,-1 1,0 0,1 1,0 1,0 -1,0 0,-1 1,0 -1,0 0,-1 1,0  0,1 1,0 0,-1 0,1 1,0 0,-1 0,1 1,0 0,-1 0,1 0,-1 1,0 0,-1 1,0 1,0 1,0  0,-1 1,-2 0,-1 1,-1 1,0 1,0 1,1 1,0 0,-1 1,0 0,1 2,0 2,2 1,-1 1,2 1,1  -2,1 0,2 1,0 0,1 0,1 1,0 1,0 1,2 1,0 1,0 -1,-1 0,-1 0,-1 2,0 1,0 1,0 1,0  -1,3 0,1 1,1 0,1 0,1 1,1 0,1 0,1 0,2 0,1 0,1 1,1 1,0 1,-1 1,0 1,-1 0,-1  1,0 1,-1 1,1 1,1 1,2 0,1 0,1 -1,1"
           id="path452"
           style="fill:#d40000;fill-opacity:1" />
      </g>

Somehow I have to search for the first value in the reference file -  then change the fill property just before the </g> in each of the  paragraphs.  So I have to identify the correct style to change then  iterate to the next row in the source file until end.   So I have to find the value MP304 - then in the "paragraph" where MP304  is ie between the <g and /g>, change the style value of that code  tag to what the source file says for that MP304 value.  Then I have to  iterate - go to next line in source file and search for MP305, and do  the same for its value.

Can someone point me in the direction of commands to use please?

---

### Post by Vaphell on 2013-10-11
please wrap your snippet in [noparse]```

```[/noparse] tags to preserve original format and indentation and maybe use colors to mark points of interest.

---

### Post by steeldriver on 2013-10-11
To do the actual text substitution you could maybe use awk to split file2 into records delimited by the </g> and then do a sub on the penultimate newline-delimited field

```
awk -v key="$key" -v val="$val" 'BEGIN{FS="\n"; RS="</g>\n"; OFS=FS; ORS=RS}; $3 ~ key {sub("#[a-f0-9]+",val,$(NF-1))}; {print}'
```

I'm not sure the best way to loop over the key-val pairs in your file1 - this would probably work (NB uses a tmpfile) but one of the experts can probably suggest something better

```

$ cp file2 newfile
$ 
$ while IFS=',' read -r key val; do 
    awk -v key="$key" -v val="$val" 'BEGIN{FS="\n"; RS="</g>\n"; OFS=FS; ORS=RS}; $3 ~ key {sub("#[a-f0-9]+",val,$(NF-1))}; {print}' newfile > tmpfile
    mv tmpfile newfile
done < file1

```

---

### Post by Vaphell on 2013-10-11
i'd go with a proper xml parser, it's too easy to trip up quick and dirty solutions based on 'stupid' string manipulations.

---

### Post by majikins2 on 2013-10-12
kind soul on Unix.com posted this for me:
> awk -F, 'FNR==NR{A["\""$1"\""]=$2;next}{for(i in A)if($0~i)R=A[i];if(R && $0~/style/){j++;if(j==2){gsub(/#.*;/,"#"R";");R=j=""}}}1'  file1 file2 > file3

Works great!

---

### Post by majikins2 on 2013-10-12
Thank you - will try this as well.

---

### Post by majikins2 on 2013-10-12
Will do next time - apologies for noob error.

---


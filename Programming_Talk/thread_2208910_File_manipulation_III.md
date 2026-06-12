---
title: "File manipulation III"
date: 2014-03-02
forum: Programming Talk
---

### Post by Herbon on 2014-03-02
Greeting 

I was working on my mp3 collection (backup copy), using some commands I found on line. These command locates all files counts and arranges them

```

find ./media/herbon/9c6cc0c7-549f-4a54-8618-eb9fa9ae05d0 -type f | gawk -F/ '{print $NF}' | gawk -F. '/\./{print $NF}' | sort | uniq -c | sort -rn

```

Here is the output:

```

  53433 mp3
   3685 jpg
   2127 m4a
    631 wma
    535 MP3
    445 part
    350 m3u
    275 flac
      1 MP4
      1 mp3FA3A2B
      1 mp3F89863
      1 mp3F2CF42
      1 mp3F25A05
      1 mp3EFE8E9
      1 mp3EEB441
      1 mp3ECA9FD
      1 mp3EB4226
      1 mp3E85C00
      1 mp3E63B69
      1 mp3E5AF43
      1 mp3E4F709
      1 mp3E49B35
      1 mp3E39DB7
      1 mp3E3378D
      1 mp3E2A168
      1 mp3DC3928
      1 mp3DBF20F
      1 mp3DBEF32
      1 mp3D94486
      1 mp3D87807
      1 mp3CDE460
      1 mp3C5D4B2
      1 mp3C41DB9
      1 mp3BF171D
      1 mp3BE8C78
      1 mp3B5AECB
      1 mp3B0D98F
      1 mp3AF366C
      1 mp3ACD722
      1 mp3AB9823
      1 mp3AA9B94
      1 mp3AA31B2
      1 mp3A6B57A
      1 mp3A46364
      1 mp3A44203
      1 mp3A2534D
      1 mp398764D
      1 mp393DB4E
      1 mp3896760
      1 mp3864227
      1 mp38136F6
      1 mp3807EA5
      1 mp37B0DBC
      1 mp37A9EBC
      1 mp376A4BB
      1 mp3763AD0
      1 mp37631EF
      1 mp373FBBD
      1 mp371A3A6
      1 mp36BFB15
      1 mp36B98B2
      1 mp3684D94
      1 mp367868F
      1 mp3662527
      1 mp3655C27
      1 mp364E33D
      1 mp3557A26
      1 mp354489A
      1 mp353C70B
      1 mp34F35D5
      1 mp34E71AA
      1 mp34B3FA1
      1 mp347DD08
      1 mp34743B7
      1 mp345869A
      1 mp341CD07
      1 mp340873A
      1 mp33FC693
      1 mp33436A9
      1 mp3314086
      1 mp330C5BE
      1 mp32AAF73
      1 mp329CB55
      1 mp32807A5
      1 mp324F7D7
      1 mp3249835
      1 mp31D9496
      1 mp31A43A5
      1 mp319B2A5
      1 mp3199AA5
      1 mp3183DF0
      1 mp316CD3B
      1 mp3163BA8
      1 mp315E4FA
      1 mp30D0DB2
      1 mp30C75F9
      1 mp30B930F
      1 mp307899C
      1 mp3060AB8
      1 mp3007C3D
      1 m4aF76B17
      1 m4a02EC2B

```

I found a group of oddly named mp3 files with number after the extenstion  ie *.mp3FA3A2B, *.mp3F89863 etc etc
How do I rename them from "*.mp3FA3A2B" to "*.mp3"???

Thanks

---

### Post by Vaphell on 2014-03-03
```
rename -v 's/.{6}$//' *.{mp3,m4a}[0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F]
```
add -n for dry run to see the results before actually doing the operation.

If they are scattered all over the place consider using
```
shopt -s [COLOR="#0000FF"]globstar[/COLOR]
rename -v 's/.{6}$//' [COLOR="#0000FF"]**[/COLOR]/*.{mp3,m4a}[0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F]
```
bash ** matches any dir at any depth so it's very convenient in these kinds of situations


btw if you don't want case sensitive mp3 and MP3 in your list, use print tolower($NF) in awk to normalize.

---

### Post by Herbon on 2014-03-04
Thanks 

I will let you know how this turns out.

---

### Post by Herbon on 2014-03-04
So attempt to run the following command in my mp3 folder

```

rename -v 's/.{6}$//' *.{mp3,m4a}[0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F]

```

and I received the following error

```

Can't rename *./{mp3}[0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F] *./{mp3}[0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0: No such file or directory

```

---

### Post by Vaphell on 2014-03-04
add -n switch, so if something goes wrong you get to see it before actually committing to changes. Mass renames going bad are often very nasty to fix.

the error message doesn't really fit the command - *.{mp3,m4a}... glob wouldn't yield *.[COLOR="#0000FF"]/[/COLOR]{mp3} in error message.
Most likely you added slash and got rid of m4a even though your listing has 2 of them that require fixing.
btw if you intend to have a single option, you don't need {}. It's used to produce 'branches', eg. ***.{wav,avi,mp3}** = ***.wav *.avi *.mp3**

Can you post the relevant part of the terminal text verbatim? ctrl+shift+c and paste it here in ```
 tags.
Are you in proper directory when calling the command?


That said, such error messages happen when there are no matching files and they are rather harmless. The glob is not translated to the list of proper filenames because there are none matching, but being passed literally and the command tries to find the glob-named file and obviously fails. If that's the case here and it rustles your jimmies for whatever reason, you can disable that 'feature' of empty globs with
[code]shopt -s nullglob
```

```
$ touch file1.txt file2.txt
$ echo *.txc [COLOR="#ADD8E6"]<- no glob expansion, literal glob passed as parameter[/COLOR]
*.txc
$ echo *.txt
file1.txt file2.txt
$ shopt -s nullglob
$ echo *.txc [COLOR="#ADD8E6"]<- no parameters due to empty expansion with nullglob[/COLOR]

$
```

---


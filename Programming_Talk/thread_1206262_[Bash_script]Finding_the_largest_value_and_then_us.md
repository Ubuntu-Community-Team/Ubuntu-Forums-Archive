---
title: "[Bash script]Finding the largest value and then using it"
date: 2009-07-07
forum: Programming Talk
---

### Post by Moustacha on 2009-07-07
Hi, I'm trying to write a bash script to make extracting the audio from some music DVDs I've got easier. One thing has me stumped though, finding which title has the concert and how many chapters there are.

Using lsdvd it tells me which the longest track is but I don't know how to get that value into a variable for me to use, and also finding getting how many chapters there are into a variable.

Output of lsdvd is
```
$ lsdvd dio.iso
libdvdread: Using libdvdcss version 1.2.10 for DVD access
Disc Title: DIO
Title: 01, Length: 00:00:18.240 Chapters: 02, Cells: 03, Audio streams: 01, Subpictures: 00

Title: 02, Length: 00:03:00.000 Chapters: 01, Cells: 01, Audio streams: 01, Subpictures: 00

Title: 03, Length: 01:53:59.210 Chapters: 18, Cells: 18, Audio streams: 03, Subpictures: 00

Title: 04, Length: 00:11:40.000 Chapters: 02, Cells: 02, Audio streams: 03, Subpictures: 00

Longest track: 03

```

What I've got so far in my script

```
#!/bin/bash
	for j in $( ls /media/sdc1/Music\ DVDs/)
	do
		lsdvdOutput=$(lsdvd $j)
		longestTrack=$(something)
		numberOfChapters=$(somethingelse)

		for i in `seq 1 $numberOfChapters`;
		do
			transcode -i $j -x dvd -T $longestTrack,$i -a 0 -y wav -m chpt$i.wav
		done

```

Thanks for any help

---

### Post by c0mput3r_n3rD on 2009-07-07
Dude, you need to look a little harder at your code before you ask help. It's like right there in there face.

---

### Post by ghostdog74 on 2009-07-07
```

for i in /path/*
do
    lsdvd "$i" | awk 'BEGIN{
    FS=": |," 
    }
    /Title/ && $5>=temp{
        t[$2]=$0    
    }
    /Longest track/{ 
    gsub(/.*Chapters: /,"",t[$2])
    gsub(/,.*/,"",t[$2])
    for(i=1;i<=t[$2];i++){
        cmd = "transcode -i "$0" -x dvd -T "longestchap" ,"i" a 0 -y wav -m chpt"i".wav"
        print cmd
        system(cmd)
    }
    next
    }' 
done

```

---

### Post by geirha on 2009-07-07
First off, never use ls with for, and always quote "$variables" containing pathnames

```

#!/bin/bash
for j in "/media/sdc1/Music DVDs"/*; do
    read longestTrack numberOfChapters < <(lsdvd "$j" | awk '/^Title/{if($4>max){max=$4;t=$2;c=$6;}}END{print int(t),int(c)}')
    for ((i=1; i<=numberOfChapters; ++i)); do
        transcode -i "$j" -x dvd -T $longestTrack,$i -a 0 -y wav -m "$(printf "chpt%02d.wav" "$i")"
    done
done

```

---

### Post by Moustacha on 2009-07-07
> **geirha said:**
> First off, never use ls with for, and always quote "$variables" containing pathnames


Thanks for that geirha. I didn't know about awk, I'll have to learn how to use it in case I need to do something like this again.
Also, I understand why you should put variables containing pathnames in quotation marks, but why shouldn't you use ls with for? Is it because ls will pick up folders too but the way you used doesn't?

---

### Post by geirha on 2009-07-07
> **Moustacha said:**
> Thanks for that geirha. I didn't know about awk, I'll have to learn how to use it in case I need to do something like this again.
Also, I understand why you should put variables containing pathnames in quotation marks, but why shouldn't you use ls with for? Is it because ls will pick up folders too but the way you used doesn't?

No because whitespace that separates pathnames and whitespace that is contained inside pathnames gets treated the same, as separators of pathnames.

```

$ mkdir /tmp/test
$ touch /tmp/test/{"file with spaces","file_without_spaces"}
$ for file in $(ls /tmp/test/*); do echo "$file"; done
/tmp/test/file_without_spaces
/tmp/test/file
with
spaces
$ for file in /tmp/test/*; do echo "$file"; done
/tmp/test/file_without_spaces
/tmp/test/file with spaces

```

See [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls) for other common pitfalls.

---


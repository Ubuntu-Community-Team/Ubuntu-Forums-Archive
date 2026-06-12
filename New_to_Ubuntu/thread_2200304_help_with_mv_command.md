---
title: "help with mv command"
date: 2014-01-18
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2014-01-18
Hi friends,

I have photos and videos in "Pictures" directory. I want to separate photos and videos. So I used following command

```
find Pictures/ | grep mp4 > allvids.txt
```

Now I have path of all video files stored in file allvids.txt

Can I read these path and pass the input to mv command to move files to other location? Can I maintain directory structure as it is while moving? I mean if path of a mp4 file is say Pictures/2013/Dec/001.mp4 can I move the file to say /Desktop/2013/Dec/001,mp4?

Please help me frame proper command for above said objective. 

Thanks in advance

---

### Post by Vaphell on 2014-01-18
bash script
```
#!/bin/bash

src=~/Pictures
dest=~/Desktop

while read -rd $'\0' f
do
  fn=${f/#$src/$dest}
  mkdir -p ${fn%/*}
  mv -v -- "$f" "$fn"
done < <( find "$src" -iname "*.mp4" -type f -print0 )
```

test it first on some dummy files, i typed it here without checking.

---

### Post by sujitrjadhav on 2014-01-18
It Worked perfect!! Your script did exactly what I wished. Thanks very much vaphell

---

### Post by varunendra on 2014-01-18
> **sujitrjadhav said:**
> Can I maintain directory structure as it is while moving? I mean if path of a mp4 file is say Pictures/2013/Dec/001.mp4 can I move the file to say /Desktop/2013/Dec/001,mp4?

There is an option in cp command to preserve the directory structure, but no such option in mv. So you can either cp the files, THEN delete them in next cycle (when you are satisfied, and that's why I strongly recommend this method), or combine the cp and rm commands in the same run of 'find' command ([COLOR="#FF0000"]destructive without verification ![/COLOR] so not recommended).

To copy them to Desktop -
```
find ./Pictures -type f -iname *.mp4 -exec cp --parents "{}" ./Desktop/ \;
```
After verification, to delete the source files -
```
find ./Pictures -type f -iname *.mp4 -exec rm "{}" \;
```
Note that this will leave the containing directories. If you need to delete them as well, we'd have to modify the above command or use a script.

To do everything in one go -
```
find ./Pictures -type f -iname *.mp4 -exec cp --parents "{}" ./Desktop/ \; -exec rm "{}" \;
```

**[COLOR="#FF0000"]CAUTION ![/COLOR]** I haven't tested the "rm" part myself here, only the cp part. Same security advice as Vaphell :P
> test it first on some dummy files, i typed it here without checking.

**EDIT:**
Eh, late, as usual.. :|

---

### Post by sujitrjadhav on 2014-01-18
Hi Varun,

Thanks very much for your reply.

Even though my problem was already solved with the help of vaphells script, I thought I would like to try solution offered by you as it looked little simple than the shell script and I thought it as a chance to learn something new. So I recreated the problem. Backed up my files as it involved rm and a \ too. Honestly whenever I was little afraid due to there being both rm and \ :). 

Your solution too worked and did exactly what I wanted but I observed one point- your solution took longer time due to huge size of video files and as your solution involved first copy and then remove rather than move.

Any way thanks very much. 

As I found that you were an Indian, I searched your name in google; found your wiki page on ubuntu and liked whatever you have written there. Like you I am also a big fan of ubuntu and have not used windows for anything except nokia pc suit in last 3 years though I am not an expert like you.

---

### Post by Vaphell on 2014-01-18
indeed moving by copy+delete is not really a feasible approach. Move operation within the same partition means simply reassigning the file to another directory which is near instant, while copy+delete means duplicating the file. Obviously how much it takes depends on the file size and disk transfer speeds
Between partitions move and copy+delete are essentially the same thing and there is no way around it.

---

### Post by varunendra on 2014-01-19
> **sujitrjadhav said:**
> As I found that you were an Indian, I searched your name in google; found your wiki page on ubuntu and liked whatever you have written there.
Yay !! Me got popula.. :P

> **Vaphell said:**
> indeed moving by copy+delete is not really a feasible approach.
Yeah, I overlooked/ignored that while suggesting. And a long one liner would probably be more complex than the simple script you proposed. :-\"

---


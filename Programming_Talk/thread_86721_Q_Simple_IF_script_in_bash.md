---
title: "Q: Simple IF script in bash"
date: 2005-11-06
forum: Programming Talk
---

### Post by Berkut on 2005-11-06
Hi,
I was hoping if someone could help me with an easy script (I have almost no programming experience). I am recording an ogg stream to an mp3 file on my harddrive (so I can listen to it on my non-ogg-supported player). 
```
ogg123 http://stream.ogg -d wav -f - | lame -h --abr 196 - test.mp3
```
What I would like to ask you, is how to make a script which will stop recordnig when the filesize of the file is 255 MB (the size of my players memory)?

I think it should be an IF command but I have no idea how it can check the size of the file.

TNX in advance

---

### Post by nagilum on 2005-11-06
I don't see how an IF statement would work here since it's just one command piping its output to another. There's no point where an IF could snap in and start recording to another file or stop the recording altogether.
There's an application called mp3splt which does what you are looking for (didn't use it myself, but the manpage looks promising). Just pipe the output from lame to this one and let it create several mp3-files of a fixed length.

---

### Post by 23meg on 2005-11-16
Maybe the bash command [split]("http://www.ss64.com/bash/split.html") will help you.

---

### Post by bignate on 2005-11-19
This is a kludge but it *should* work.

```
#!/bin/bash

ogg123 http://stream.ogg -d wav -f - | lame -h --abr 196 - test.mp3 &

SIZE=0
while [ $SIZE -lt 268435456 ]
    do
    SIZE=`du -b test.mp3 | awk -F" " '{print$1}'`
    continue
done

killall -9 ogg123
```

Of course you'll have to change the file name, and url to suit your needs.

---


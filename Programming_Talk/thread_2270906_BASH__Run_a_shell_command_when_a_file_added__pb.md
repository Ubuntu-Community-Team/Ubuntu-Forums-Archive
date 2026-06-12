---
title: "BASH / Run a shell command when a file added / pb"
date: 2015-03-26
forum: Programming Talk
---

### Post by hoop2 on 2015-03-26
[COLOR=#333333][FONT=Helvetica Neue]Hi all, thanks to take time to read this. [/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]I want to do something special : when a file is added (by ftp) to a specific folder, a script launch a command. I found a good script but maybe i made a mistake and i don't understand fully what each line said. [/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]the trick is to watch /var/log/vsftpd.log [/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]when a file is uploaded correctly, vsftpd return a line with "OK UPLOAD"

```
[/FONT][/COLOR]tail -f /var/log/vsftpd.log | while read line; do
  if echo "$line" | grep -q "OK UPLOAD:"; then
    filename=$(echo "$line" | cut -d, -f2)
    if [ -s "$filename" ]; then
        echo "hello"
 fi
  fi
done[COLOR=#333333][FONT=Helvetica Neue]
```

[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]- why it doesn't print hello when i upload a file ? [/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]- and i want to print hello also when the file uploaded contained RG14 in its filename. [/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]If someone call help me, i spent all night on that...[/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]Thanks[/FONT][/COLOR]

---

### Post by Lars Noodén on 2015-03-26
It's probably because [cut](http://manpages.ubuntu.com/manpages/trusty/en/man1/cut.1posix.html) does not trim the quotes and the [test](http://manpages.ubuntu.com/manpages/trusty/en/man1/test.1.html) -s takes $filename literally.  Try printing $filename after the line with cut and you'll see it.  

One way around that would be to use **awk**.

```

#!/bin/sh

tail -f /var/log/vsftpd.log | while read line; do
  if echo "$line" | grep "OK UPLOAD:"; then
    filename=$(echo "$line" | awk -F , '{ sub(/^[^"]*"/, "", $2); sub( /"[^"]*$/, "", $2 ); print $2 }')
    if [ -s "$filename" ]; then
        echo "hello"
    fi
  fi
done

```

The line *awk -F , '{ sub(/^[^"]*"/, "", $2); sub( /"[^"]*$/, "", $2 ); print $2 }')* does four things.

The *-F ,* sets the field separator to be a comma

 The *sub(/[color=blue]^[^"]*"[/color]/, "", $2)* finds everything at the start of field $2 up to and including the first double quote and substitutes it with an empty string.

 The *sub( /[color=blue]"[^"]*$[/color]/, "", $2 )* finds everything after and including the last double quote and substitutes it with an empty string.

 Then it prints out what's left of the second field.  


However, if you want a script to be run whenever a file is added to a particular directory, then a better way might be to use **incron** and set up and [incrontab](http://manpages.ubuntu.com/manpages/trusty/en/man5/incrontab.5.html) to watch for additions.  That can then launch a script and pass the filename in question as a parameter to the script.

---

### Post by hoop2 on 2015-03-26
Thanks for your answer. Your script works. But print also the last lines stored in /var/log/vsftpd.log

When you said "[COLOR=#000000]It's probably because [/COLOR][cut]("http://manpages.ubuntu.com/manpages/trusty/en/man1/cut.1posix.html")[COLOR=#000000] does not trim the quotes and the [/COLOR][test]("http://manpages.ubuntu.com/manpages/trusty/en/man1/test.1.html")[COLOR=#000000] -s takes $filename literally. Try printing $filename after the line with cut and you'll see it." 
[/COLOR]I don't understand what i have to do, i tried to write [COLOR=#000000][FONT=Ubuntu Mono] filename=$(echo "$line" | cut -d, -f2, echo "hello") [/FONT][/COLOR]but with no success. Sorry for being new in bash... 

i put RG14 in strings also "RG14" to only do the search but it doesn't work...

---

### Post by Lars Noodén on 2015-03-26
Try adding a line like *echo $filename*  You'll see that it prints *"/a.php"* with quotes instead of */a.php* without quotes.  Since the real file name does not contain quotes, the -s test will not find it.  

That reminds me that you might need to precede $filename with some real path if vsftp is using a chroot.

Again, I'd suggest looking at incron for this.  There are a lot of advantages.

---

### Post by Lars Noodén on 2015-03-26
> **hoop2 said:**
> But print also the last lines stored in /var/log/vsftpd.log


I forgot to put the -q back in [grep](http://manpages.ubuntu.com/manpages/trusty/en/man1/grep.1.html).  I took it out so I could see what was going on there, but if you want it quiet again, add -q to it.

---

### Post by hoop2 on 2015-03-26
Ok thanks a lot to you and for your time. 
I will look at incron, i used it but with no success, not success i expected.

Thanks to you

---

### Post by ofnuts on 2015-03-26
In modern Linux you would use [inotify-tools]("http://techarena51.com/index.php/inotify-tools-example/") for this.

Note: never used myself...

Edit: that would be something like:

```

while true
do
   createdFile=$(inotifywait --format %f -e create $monitored_directory)
  [[ $createdFile == RG4* ]] && echo "Yet another bloody RG4 file"
done

```

---

### Post by hoop2 on 2015-03-27
Thanks to you for this solution but it doesn't work for me. It returns the error : 
[FONT=Menlo]Couldn't watch create: No such file or directory[/FONT]

this is what i did : 
[COLOR=#34BBC7][FONT=Menlo]#!/bin/bash[/FONT][/COLOR]
[FONT=Menlo]
[/FONT]
[COLOR=#AFAD24][FONT=Menlo][COLOR=#000000]monitored_directory[/COLOR][COLOR=#34bd26]=([/COLOR][COLOR=#5330e1]**cd**[/COLOR][COLOR=#000000] [/COLOR]**"/home/horus-ekla/RTRG/UPLOAD/"**[COLOR=#34bd26])[/COLOR][/FONT][/COLOR]
[FONT=Menlo]
[/FONT]
[FONT=Menlo][COLOR=#34bd26]while[/COLOR] true[/FONT]
[COLOR=#34BD26][FONT=Menlo]do[/FONT][/COLOR]
[FONT=Menlo]        createdFile[COLOR=#34bd26]=$([/COLOR]inotifywait --format [COLOR=#c33720]**$f**[/COLOR] [COLOR=#34bd26]-e[/COLOR] create [COLOR=#c33720]**$monitored_directory**[/COLOR][COLOR=#34bd26])[/COLOR][/FONT]
[COLOR=#AFAD24][FONT=Menlo][COLOR=#000000]        [/COLOR][COLOR=#34bd26][[[/COLOR][COLOR=#000000] [/COLOR][COLOR=#c33720]**$createdFile**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#34bd26]==[/COLOR][COLOR=#000000] RG14* [/COLOR][COLOR=#34bd26]]][/COLOR][COLOR=#000000] [/COLOR][COLOR=#34bd26]&&[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5330e1]**echo**[/COLOR][COLOR=#000000] [/COLOR]**"Yet another bloody RG14 file"**[/FONT][/COLOR]
[COLOR=#34BD26][FONT=Menlo]done[/FONT][/COLOR]
[FONT=Menlo]
as you can see, i'm very new for writing shell script
Thanks in advance to help me ! [/FONT]

---

### Post by Lars Noodén on 2015-03-27
Only the equal sign is needed when setting an environment variable:

```

monitored_directory="/home/horus-ekla/RTRG/UPLOAD/"

```

---

### Post by hoop2 on 2015-03-27
thanks lars, that what i did first but i got same error. 
i added -m after inotifywait and now i don't have the same error, inotifywait seems to work correctly. 
but when i add a file like RG14_LOCK-ENG-SST.MP4 to the specific folder, i should see [B]"Yet another bloody RG14 file" 
[/B]But no... 

i tried with moved_to for inotifywait but no success too...

---

### Post by Lars Noodén on 2015-03-28
The $f you have there should be %f instead.  Check #7 above for the exampel.

---

### Post by hoop2 on 2015-03-28
it's working !!! 

thanks Lars, i changed $f to %f but no success too. 
i did without -m and %f and it's working
thanks for your time and answer each time

[COLOR=#34BBC7][FONT=Menlo]#!/bin/bash[/FONT][/COLOR]
[FONT=Menlo]
[/FONT]
[COLOR=#AFAD24][FONT=Menlo][COLOR=#000000]monitored_directory[/COLOR][COLOR=#34bd26]=[/COLOR]**"/home/horus-ekla/RTRG/UPLOAD/"**[/FONT][/COLOR]
[FONT=Menlo]
[/FONT]
[FONT=Menlo][COLOR=#34bd26]while[/COLOR] true[/FONT]
[COLOR=#34BD26][FONT=Menlo]do[/FONT][/COLOR]
[FONT=Menlo]        createdFile[COLOR=#34bd26]=$([/COLOR]inotifywait [COLOR=#34bd26]-e[/COLOR] create [COLOR=#c33720]**$monitored_directory**[/COLOR][COLOR=#34bd26])[/COLOR][/FONT]
[COLOR=#AFAD24][FONT=Menlo][COLOR=#000000]        [/COLOR][COLOR=#34bd26][[[/COLOR][COLOR=#000000] [/COLOR][COLOR=#c33720]**$createdFile**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#34bd26]==[/COLOR][COLOR=#000000] *RG14* [/COLOR][COLOR=#34bd26]]][/COLOR][COLOR=#000000] [/COLOR][COLOR=#34bd26]&&[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5330e1]**echo**[/COLOR][COLOR=#000000] [/COLOR]**"Yet another bloody RG14 file"**[/FONT][/COLOR]
[COLOR=#34BD26][FONT=Menlo]done[/FONT][/COLOR]

---


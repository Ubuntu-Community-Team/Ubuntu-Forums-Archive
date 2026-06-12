---
title: "[SOLVED] Need to Automate a Script - Interactive input"
date: 2008-12-11
forum: Programming Talk
---

### Post by navneeth on 2008-12-11
**Disclaimer**: I have no prior experience in shell scripting, and I have just begun learning a thing or two. 

I have script called RunRadioRip.sh, which when executed asks for the URL of a Real audio stream, and then it asks for the name of the (mp3) file  under which this audio stream will be stored later. Also, I have to press Enter/Return key each time after providing the information. 

I want to download a set of four streams, and I want that to happen after a certain time and while I'm asleep; but don't bother about the "certain time" part... I'll start it and then go to sleep. :)

I know that I have to call this conversion script four times, but how do I provided the input -- I tried echo, but that seemed silly later -- and also "press" Enter?

I'd appreciate any help.

---

### Post by mssever on 2008-12-11
> **navneeth said:**
> **Disclaimer**: I have no prior experience in shell scripting, and I have just begun learning a thing or two. 

I have script called RunRadioRip.sh, which when executed asks for the URL of a Real audio stream, and then it asks for the name of the (mp3) file  under which this audio stream will be stored later. Also, I have to press Enter/Return key each time after providing the information. 

I want to download a set of four streams, and I want that to happen after a certain time and while I'm asleep; but don't bother about the "certain time" part... I'll start it and then go to sleep. :)

I know that I have to call this conversion script four times, but how do I provided the input -- I tried echo, but that seemed silly later -- and also "press" Enter?

I'd appreciate any help.
The right way is to modify the script to accept command-line parameters. Otherwise, running ```
echo -e "the_url\nfile_name" | your_script
```will probably work, assuming that the script is a bash script which uses [FONT=Courier New]read[/FONT] to get user input. Finally, expect is designed for these kinds of things and it's guaranteed to work.

Oh, and once you get a working script, you can make it a cron job so you don't have to remember to start it manually.

---

### Post by navneeth on 2008-12-11
> **mssever said:**
> Otherwise, running ```
echo -e "the_url\nfile_name" | your_script
```will probably work, assuming that the script is a bash script which uses [FONT=Courier New]read[/FONT] to get user input.
Yes, it's a bash script, and yes, it uses read to get the input. 

Looking at the script, it seems that I can modify it with a for loop-like structure (whatever it is known bash) for the task at hand, but I'm not very familiar with the syntax - yet. 

**RunRadioRip.sh**
```
#!/bin/bash
# This script will rip real media streams from the internet.
# The first parameter is the lame encoder options see http://www.hydrogenaudio.org/forums/index.php?showtopic=28124 for a full list.

lameop=${1:- --preset voice} # Sets the default lame options to be "--preset voice"  
echo -e "\n********************************************************************\nOutput will be an .mp3 file using lame ${lameop}\n********************************************************************\n"

echo "Type the url of the ram file (e.g. http://www.news.com/radio/news.ram), followed by [ENTER]:"
read url
echo "Type the desired mp3 file name (e.g. OldNews), followed by [ENTER]:"
read fileName

mplayer -playlist ${url} -dumpstream -dumpfile ${fileName}.ram
mplayer ${fileName}.ram -ao pcm:file=${fileName}.wav
lame ${lameop} -f ${fileName}.wav ${fileName}.mp3
rm ${fileName}.ram ${fileName}.wav
echo "Exiting."

exit;
```

I write a script (let's call it download.sh), should it look like this?

```

#!/bin/bash
#download.sh

RunRadioRip.sh

echo -e "the_url\nfile_name" | **your_script**


```

With regard to the code you provided, what do I substitute for your_script? RunRadioRip.sh returns a Command Not Found error. 




> Finally, expect is designed for these kinds of things 
and it's guaranteed to work.

Thanks... will look into once I grasp the basics of bash. 

> Oh, and once you get a working script, you can make it a cron job so you don't have to remember to start it manually.

Although that went over my head, I'll remember that. :)

---

### Post by navneeth on 2008-12-11
Oh, never mind. It didn't have the proper permissions, I guess. 

I added 'bash' before RunRadioRip.sh.

Thanks.

---

### Post by mssever on 2008-12-11
> **navneeth said:**
> Yes, it's a bash script, and yes, it uses read to get the input. 

Looking at the script, it seems that I can modify it with a for loop-like structure (whatever it is known bash) for the task at hand, but I'm not very familiar with the syntax - yet.The for loop syntax is ```
for some_variable in space- or newline-separated list of things to loop over; do
  # loop body goes here
done
```> With regard to the code you provided, what do I substitute for your_script? RunRadioRip.sh returns a Command Not Found error. ```
echo -e "the_url\nfile_name" | /path/to/RunRadioRip.sh
```Don't just copy and paste. Change it to fit your situation (i.e., the_url and file_name should be changed to contain the URL and filename you want, and the path to RunRadioRip.sh should be self-explanitory).> Although that went over my head, I'll remember that. :)cron is a program that automatically executes processes based on a schedule. Use ```
crontab -e
```to edit the crontab, where cron is configured. See ```
man 1 crontab
``` and ```
man 5 crontab
```for documentation.

---

### Post by navneeth on 2008-12-11
Thanks a bunch for providing all the syntax. Yes, I knew I had to put in my URL and stuff... I just didn't see it as a necessity when I asked the question. :)

Re: crontab... I was searching for something else and I came across a page on the basics of cron(tab). [http://goinglinux.com/articles/Scripts.html](http://goinglinux.com/articles/Scripts.html) 

Great! Scripting is wonderful! :D

---

### Post by rex_the_first on 2011-05-13
Sorry to resurrect an old post but I put up a new version of the scrip at
[http://ubuntuforums.org/showthread.php?p=10786066#post10786066](http://ubuntuforums.org/showthread.php?p=10786066#post10786066) if you are interested.

Cheers

---


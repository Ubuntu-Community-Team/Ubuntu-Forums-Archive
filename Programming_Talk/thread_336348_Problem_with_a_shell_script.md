---
title: "Problem with a shell script"
date: 2007-01-11
forum: Programming Talk
---

### Post by Trickyphillips on 2007-01-11
```
ron@tpzlaptop:~/Desktop/ghotel$ sh grab.sh 86
grab.sh: 21: Syntax error: end of file unexpected (expecting "then")

```

```
#!/bin/sh
NUM=${1:-error}
if [ "$NUM" == "error" ]; then
  echo "Syntax: scriptname.sh SoundTrackNumber"
  echo "Sound track number from http://gh.ffshrine.org/soundtracks.php"
  echo "http://gh.ffshrine.org/soundtracks/NUMBER-HERE"
  exit 1
fi

TEMPDIR=`mktemp -d`
pushd $TEMPDIR
wget -c -R .css,.txt,.gif,.jpg,.png,.jpeg -r -l 1 -np http://gh.ffshrine.org/soundtracks/$$
cd gh.ffshrine.org/soundtracks/$NUM
egrep 'href[^>]+mp3' * | sed 's#.\+"\(http://[^"]\+\.mp3\)".\+#\1#' | wget -i -
egrep 'href[^>]+jpg' * | sed 's#.\+"\(http://[^"]\+\.jpg\)".\+#\1#' | wget -i -
popd
mkdir $NUM
mv $TEMPDIR/gh.ffshrine.org/soundtracks/$NUM/*.mp3 $NUM
mv $TEMPDIR/gh.ffshrine.org/soundtracks/$NUM/*.jpg $NUM
rm --preserve-root -rf $TEMPDIR
```

I've never really worked with shell scripts before this, other than using them for simple CRON tasks. I don't see where the problem is. My only if statement is on line 3, and it isn't missing "then". Anyone notice the problem?

---

### Post by tpg on 2007-01-11
In the if statement, try using a single equals sign for comparison of strings, as below.

```

NUM=${1:-error}
if [ "$NUM" = "error" ]; then
  echo "Syntax: scriptname.sh SoundTrackNumber"

```

Hope this works!

---

### Post by Trickyphillips on 2007-01-11
> **tpg said:**
> In the if statement, try using a single equals sign for comparison of strings, as below.

```

NUM=${1:-error}
if [ "$NUM" = "error" ]; then
  echo "Syntax: scriptname.sh SoundTrackNumber"

```

Hope this works!

No luck with this. Thanks for the response.

---

### Post by pizzutz on 2007-01-11
I don't think the error has anything to do with the if statement, the error is unexpected end of file on line 21 (your script is 20 lines long).  It might be as simple as putting exit 0 at the end.

(I think.... I don't do much scripting myself.)

---

### Post by Trickyphillips on 2007-01-12
If I comment out my 'if' statement and everything within it, the problem goes away. I wonder what I'm doing wrong with that if statement.

---

### Post by po0f on 2007-01-12
Trickyphillips,

Try changing the hash-bang to "#!/bin/bash" and using bash to execute it.

---

### Post by Arndt on 2007-01-12
> **Trickyphillips said:**
> If I comment out my 'if' statement and everything within it, the problem goes away. I wonder what I'm doing wrong with that if statement.

Maybe there is an invisible garbage character somewhere there (in your script, not here in the forum). Comment out a bit at a time to try to find exactly where the problem is. The 'if' statement works fine for me when I copy it from here and run it.

---

### Post by misterpms on 2007-01-12
Have you tried using the -v and -x flags to aid with debugging ? -v will show you what the shell is seeing and -x will place '+' before each line that is executed in your script.

```

#!/bin/sh

set -v on
set -x on

NUM=${1:-error}
if [ "$NUM" == "error" ]; then
  echo "Syntax: scriptname.sh SoundTrackNumber"
  echo "Sound track number from http://gh.ffshrine.org/soundtracks.php"
  echo "http://gh.ffshrine.org/soundtracks/NUMBER-HERE"
  exit 1
fi

set -v off
set -x off

```

---

### Post by tpg on 2007-01-12
I've tried running the script on my machine, and it seems to work, at least it doesn't spit out any error messages like the ones you're getting. I wonder if it's something to do with your version of bash?

---

### Post by tpg on 2007-01-12
Just another thought: have you tried moving the "then" statement to a new line, or fiddle around with the spacing between the "]", ";" and "then"? It's just I seem to remember that bash is rather picky about spacing.

---

### Post by Trickyphillips on 2007-01-12
> **tpg said:**
> I've tried running the script on my machine, and it seems to work, at least it doesn't spit out any error messages like the ones you're getting. I wonder if it's something to do with your version of bash?

Interesting that you should mention this. I've found that when I use ./ instead of 'sh' to run my script, I get this error:

> ron@tpzlaptop:~/Desktop/ghotel$ ls -l
total 4
-rwxr-xr-x 1 ron ron 760 2007-01-12 10:37 grab.sh
ron@tpzlaptop:~/Desktop/ghotel$ ./grab.sh
bash: ./grab.sh: /bin/sh^M: bad interpreter: No such file or directory


And look at what happens when I try as root...

> 
ron@tpzlaptop:~/Desktop/ghotel$ sudo ./grab.sh
sudo: unable to execute ./grab.sh: No such file or directory


---

### Post by po0f on 2007-01-12
Trickyphillips,

Install [tofrodos](http://packages.ubuntu.com/edgy/utils/tofrodos); run dos2unix on your script; remember to *not* download scripts onto your Windows box for transfer to your Linux box.  :)

---

### Post by Trickyphillips on 2007-01-12
> **po0f said:**
> Trickyphillips,

Install [tofrodos](http://packages.ubuntu.com/edgy/utils/tofrodos); run dos2unix on your script; remember to *not* download scripts onto your Windows box for transfer to your Linux box.  :)

Haha, thank you. I had sent the script to my Windows box, to show to a friend over Skype (I usually IM on my WinXP machine) and sent it back to Ubuntu to overwrite the old one, when I was done changing it. I can't believe that was the problem. ](*,) 

So was it an issue with charsets, or what? I see that dos2unix "converts  plain text files in DOS/MAC format to UNIX format.", but didn't realize there was a difference in the first place.

Thanks again for the help!


EDIT: Hmm. You know.... I remember taking a Java class a couple years ago, when I didn't have Windows installed on any of my machines, and always wondered why the return carriages would be messed up when I brought my code into class. I had to use Notepad's 'Replace' function to fix all of my code during the whole semester. I suppose that issue was similar. Thanks again!

---

### Post by Arndt on 2007-01-15
> **Trickyphillips said:**
> Haha, thank you. I had sent the script to my Windows box, to show to a friend over Skype (I usually IM on my WinXP machine) and sent it back to Ubuntu to overwrite the old one, when I was done changing it. I can't believe that was the problem. ](*,) 

So was it an issue with charsets, or what? I see that dos2unix "converts  plain text files in DOS/MAC format to UNIX format.", but didn't realize there was a difference in the first place.

Thanks again for the help!


EDIT: Hmm. You know.... I remember taking a Java class a couple years ago, when I didn't have Windows installed on any of my machines, and always wondered why the return carriages would be messed up when I brought my code into class. I had to use Notepad's 'Replace' function to fix all of my code during the whole semester. I suppose that issue was similar. Thanks again!

The crucial difference is that DOS/Windows uses ^M ^J as a line terminator, while Unix uses only ^J. Unix tools typically regard ^M as garbage.

---


---
title: "Simple problem that I have yet to find a Linux solution for"
date: 2006-12-09
forum: Programming Talk
---

### Post by JHawk24821 on 2006-12-09
Pretty much all MP3 ID3 tag editors operate in the same manner:  They read parts of the parent file structure and/or filename of the MP3 as variables that can be entered into the file's ID3 tag.

For example, this file...```


/MP3s/Albums/Rock/Crash Test Dummies/God Shuffled His Feet/02. Afternoons And Coffeespoons.mp3
```

... could be read as:```


/MP3s/**<comment>**/**<genre>**/**<artist>**/**<album>**/**<track>**. **<title>**.mp3
```

So far so good, but what about this file, which is part of an audiobook:```


/home/user/MP3s/Audiobooks/Michael Crichton/Next/01. Next.mp3
```

If you apply the same tagging scheme, your result is several (sometime hundreds, as audiobooks are often several hours long) tracks that have the same track name.  When you add these to a playlist, it's very hard to make sense of where you are in a book.  Imagine your RhythmBox playlist filled with around 300 tracks that are all named "Next".  It's not the best way to keep track of what track you are listening to, especially if you copy it over to an iPod.

What I used to use, way back in my Windows days, was a program caled TagScanner.  It was and still is the defacto MP3 I3D editing program for that platform.  An all around great program (and it's free! :o ), one feature rose above all the others: *It treats file structure and filename variables as real variables*.  In a nut shell, this means that you can use the same variable more than once, and in any order when generating the I3D tag.  This is a much more powerful method of generating ID3 tags as it allows true flexibility and puts the contol in the user's hands, without limiting them to "templates".  Hate to break it to whoever wrote most *uix tag editors, but *not everyone uses the same MP3 file naming convention*. :evil: 

Using the same audiobook file, I could use TagScanner to make the follow ID3 tag:```


Comment = <parent_folder:3>
Artist = <parent_folder:2>
Album = <parent_folder:1>
Track = <filename:1>
Title = <filename:2> [<filename:1>]

```

This would give me the following ID3 tag as a result:```


Comment = Audiobooks
Artist = Michael Crichton
Album = Next
Track = 01
Title = Next [01]  <-- lookie, two variable in one tag, *and* the track number is used twice!
```

Much better, now each file has the track number embedded in the title as well as the actual track number field.  Makes digging though my iPod much, much easier.  :cool:  Despite my best efforts, I can't find a *uix utility that will do this.  ](*,)   Can anyone point me in the right direction or, better yet, make something that can do this?  The community could really use this IMHO.

For reference, here is the TagScanner home page.  Be patient, it runs like it's hosted on a freaking pocket calculator (one of the downsides of just giving away such a great prouct, I guess): [http://xdev.narod.ru/tagscan_e.htm](http://xdev.narod.ru/tagscan_e.htm)  (Google Cache of the homepage: [http://tinyurl.com/yhmk9j](http://tinyurl.com/yhmk9j))

Thank for your time.

---

### Post by duff on 2006-12-09
just for you..

install python-mutagen, and here's a script that will just do what you asked for,

```
#!/bin/sh

fn=$(readlink -f "$1")

comment=$(basename "$(dirname "$(dirname "$(dirname "$fn")")")")
artist=$(basename "$(dirname "$(dirname "$fn")")")
album=$(basename "$(dirname "$fn")")
basename=$(basename "$fn" .mp3)
track=${basename:0:2}
title=${basename: (-4)}

mid3v2 "$1" \
   --comment="$comment" \
   --artist="$artist" \
   --album="$album" \
   --track="$track" \
   --song="$title [$track]"
```

---

### Post by JHawk24821 on 2006-12-09
Excuse my noobyness, but how do I use this?  I seem to already have python-mutagen according to apt-get:```


**sudo apt-get install python-mutagen**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-mutagen is already the newest version.
The following packages were automatically installed and are no longer required:
  python-pyogg python-pyvorbis python-mutagen python-ctypes
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

And I am guessing that I edit the script that you posted to my likings, save is as *something.sh*, and run it as *./something.sh <filename>*, correct?

As for the editing part, where can I get a complete list of the available variables?

Thanks for the quick reply!

---

### Post by duff on 2006-12-09
yep. save it to a file, set the exectuable flag, and run it with the file you want.  run "mid3v2" for the options.

---

### Post by JHawk24821 on 2006-12-09
Most excellent.  I still think that a GUI-based utility would be nice.  Hmm, wonder if Wine will run TagScanner...

Either way, your help is greatly appreciated.  :KS

UPDATE:: Wine does not run TagScanner.  It loads, mostly, but freezes and has to be killed from the console.

---

### Post by JHawk24821 on 2006-12-11
I did as you directed, however I ran into an error.  Here are my steps:

```


hawk@hawk-desktop:~$**nano run.sh**
*pasted code as typed above in your post, saved, exited*
hawk@hawk-desktop:~$**ls run.sh **
[COLOR="SlateGray"]run.sh[/COLOR]
hawk@hawk-desktop:~$**chmod 775 ./run.sh**
hawk@hawk-desktop:~$**ls run.sh **
[COLOR="Lime"]run.sh[/COLOR]
hawk@hawk-desktop:~$**./run.sh **
./run.sh: 9: Syntax error: Bad substitution
```

I also tried using another "set executable" method I think is correct, **chmod +x <filename>**, however the results are the same.

Any ideas?  Actually, as I type this I wonder if it's failing because it's not intended to run without arguments...

Finally, can this script be made to go thought subdirectories recursively?  I would like to run it in the root of, say, the Audiobooks folder, and have it touch every MP3 under the subdirectories within.

---

### Post by yabbadabbadont on 2006-12-11
> **JHawk24821 said:**
> I did as you directed, however I ran into an error.  Here are my steps:

```


hawk@hawk-desktop:~$**nano run.sh**
*pasted code as typed above in your post, saved, exited*
hawk@hawk-desktop:~$**ls run.sh **
[COLOR="SlateGray"]run.sh[/COLOR]
hawk@hawk-desktop:~$**chmod 775 ./run.sh**
hawk@hawk-desktop:~$**ls run.sh **
[COLOR="Lime"]run.sh[/COLOR]
hawk@hawk-desktop:~$**./run.sh **
./run.sh: 9: Syntax error: Bad substitution
```

I also tried using another "set executable" method I think is correct, **chmod +x <filename>**, however the results are the same.

Any ideas?  Actually, as I type this I wonder if it's failing because it's not intended to run without arguments...

Finally, can this script be made to go thought subdirectories recursively?  I would like to run it in the root of, say, the Audiobooks folder, and have it touch every MP3 under the subdirectories within.
That script appears to require that you pass a parameter "$1" which, I guess, would be the full path and filename of the mp3 file you wish to tag.  Try adding that to it and see if it helps.

Edit: Also, if the script works when you pass it the correct parameter, the you can get it to handle an entire tree of files using the find command.  If the script works, and you need help with the find command, just post back here and I will try to help.

---

### Post by duff on 2006-12-11
> **JHawk24821 said:**
> 
Any ideas?  Actually, as I type this I wonder if it's failing because it's not intended to run without arguments...
that would be correct.
> 
Finally, can this script be made to go thought subdirectories recursively?  I would like to run it in the root of, say, the Audiobooks folder, and have it touch every MP3 under the subdirectories within.

you can actually do that yourself (from the same directory you saved run.sh in):
```
# find /path/to/my/music/Audiobooks -name '*.mp3' -exec ./run.sh {} \;
```

nice coloring, btw.

---

### Post by duff on 2006-12-11
> **yabbadabbadont said:**
> I guess, would be the full path and filename of the mp3 file you wish to tag.
full path not needed, that's what the **readlink -f** does.

---

### Post by yabbadabbadont on 2006-12-11
> **duff said:**
> full path not needed, that's what the **readlink -f** does.

Cool.  Even after all these years, I still learn new shell scripting related commands.  :D   (a little over 10 years using Linux by they way. ;))

---

### Post by JHawk24821 on 2006-12-11
> nice coloring, btw.

Thanks!  :mrgreen: 

As for the code, I will give it a try, thanks to both of you.

---

### Post by JHawk24821 on 2006-12-11
I think I got the hang of it, however the script is still producing errors.  Here are my steps below:

```


hawk@hawk-desktop:~$ **cat run.sh**
[COLOR="SlateGray"]#!/bin/sh

fn=$(readlink -f "$1")

comment=$(basename "$(dirname "$(dirname "$(dirname "$fn")")")")
artist=$(basename "$(dirname "$(dirname "$fn")")")
album=$(basename "$(dirname "$fn")")
basename=$(basename "$fn" .mp3)
track=${basename:0:2}
title=${basename: (-4)}

mid3v2 "$1" \
   --comment="$comment" \
   --artist="$artist" \
   --album="$album" \
   --track="$track" \
   --song="$title [$track]"[/COLOR]
hawk@hawk-desktop:~$ **ls MP3s/Audiobooks/**
[COLOR="Blue"]Bill Gates - Business @ The Speed of Thought[/COLOR]
hawk@hawk-desktop:~$ **find MP3s/Audiobooks -name '*.mp3'**
[COLOR="SlateGray"]MP3s/Audiobooks/Bill Gates - Business @ The Speed of Thought/Bill Gates - Business @ The Speed of Thought - (0001).mp3
     [...]
MP3s/Audiobooks/Bill Gates - Business @ The Speed of Thought/Bill Gates - Business @ The Speed of Thought - (0039).mp3[/COLOR]
hawk@hawk-desktop:~$ **find MP3s/Audiobooks -name '*.mp3' -exec ./run.sh {} \;**
[COLOR="SlateGray"]./run.sh: 9: Syntax error: Bad substitution
     [...]
./run.sh: 9: Syntax error: Bad substitution[/COLOR]
hawk@hawk-desktop:~$
```

Thanks again for all the help!

---

### Post by yabbadabbadont on 2006-12-11
Try changing:

basename=$(basename "$fn" .mp3)

To something like:

basefilename=$(basename "$fn" .mp3)

---

### Post by JHawk24821 on 2006-12-11
> Try changing:

basename=$(basename "$fn" .mp3)

To something like:

basefilename=$(basename "$fn" .mp3)

Drat, that made no difference.  :-k

---

### Post by yabbadabbadont on 2006-12-11
What happens if you just manually run it on one file?

---

### Post by JHawk24821 on 2006-12-11
I have traced the problem to this line:

```
#!/bin/sh

fn=$(readlink -f "$1")

comment=$(basename "$(dirname "$(dirname "$(dirname "$fn")")")")
artist=$(basename "$(dirname "$(dirname "$fn")")")
album=$(basename "$(dirname "$fn")")
basename=$(basename "$fn" .mp3)
[COLOR="Red"]track=${basename:0:2}[/COLOR]
title=${basename: (-4)}

mid3v2 "$1" \
   --comment="$comment" \
   --artist="$artist" \
   --album="$album" \
   --track="$track" \
   --song="$title [$track]"
```

Is there a syntax error here?  It's safe to assume that the line after it is buggy as well.  I tried adjusting the variable names, after yabbadabbadont pointed me that way:

```
fn1=$(readlink -f "$1")
fn2=$(basename "$fn1" .mp3)


comment=&(basename "$(dirname "$(dirname "$fn1")")")
artist=$(basename "$(dirname "$fn1")")
album=$(basename "$(dirname "$fn1")")
track=${fn2:0:2}
title=${fn2: (-4)}

mid3v2 "$1" \
   --comment="$comment" \
   --artist="$artist" \
   --album="$album" \
   --track="$track" \
   --song="$title [$track]"
```

Alas, it still fails on the same line.  ](*,)

---

### Post by JHawk24821 on 2006-12-11
> What happens if you just manually run it on one file?

I get one error instead of a slew of them. ;)

---

### Post by yabbadabbadont on 2006-12-12
I think I know what's going on now.  It stems from the script trying to use the name of an external program as a variable.  Now that I've looked at it a bit more closely, I believe it should probably look like this:
```
#!/bin/sh

fn=$(readlink -f "$1")

comment=$(basename "$(dirname "$(dirname "$(dirname "$fn")")")")
artist=$(basename "$(dirname "$(dirname "$fn")")")
album=$(basename "$(dirname "$fn")")
filename=$(basename "$fn" .mp3)
track=${filename:0:2}
title=${filename: (-4)}

mid3v2 "$1" \
   --comment="$comment" \
   --artist="$artist" \
   --album="$album" \
   --track="$track" \
   --song="$title [$track]"

```

I think that this will get rid of the errors, but I'm not sure if it is building the tags the way that you want.  Be sure to only test it on one file that you have copied to a test directory tree that has the same structure as your normal one.  Then run it on just that file and check the tags afterwards to be sure that they are what you want.  If not, post what they ended up being and how that differs from what you wanted.

---

### Post by JHawk24821 on 2006-12-12
This is one tough bugger to sort out!  The error still originates at line 9.  Seems we keep butting our head against this - perhaps going a different route entirely is the right answer?  If was a more talented scripter (read: if I had any talent at all in scripting) I would just find another way to do it.  :)

```
hawk@hawk-desktop:~/MP3s/Audiobooks/Bill Bryson - I'm a Stranger Here Myself$ **ls -l**
[COLOR="SlateGray"]total 160912
-rwxrwxrwx 1 hawk hawk 21928646 2006-12-11 17:10 Bill Bryson - I'm a Stranger Here Myself - (0001).mp3
-rwxrwxrwx 1 hawk hawk 21144764 2006-12-11 17:10 Bill Bryson - I'm a Stranger Here Myself - (0002).mp3
-rwxrwxrwx 1 hawk hawk 21129090 2006-12-11 17:10 Bill Bryson - I'm a Stranger Here Myself - (0003).mp3
-rwxrwxrwx 1 hawk hawk 20999105 2006-12-11 17:10 Bill Bryson - I'm a Stranger Here Myself - (0004).mp3
-rwxrwxrwx 1 hawk hawk 21598667 2006-12-11 17:10 Bill Bryson - I'm a Stranger Here Myself - (0005).mp3
-rwxrwxrwx 1 hawk hawk 20965668 2006-12-11 17:10 Bill Bryson - I'm a Stranger Here Myself - (0006).mp3
-rwxrwxrwx 1 hawk hawk 20784483 2006-12-11 17:10 Bill Bryson - I'm a Stranger Here Myself - (0007).mp3
-rwxrwxrwx 1 hawk hawk 15992252 2006-12-11 17:10 Bill Bryson - I'm a Stranger Here Myself - (0008).mp3
-rwxr-xr-x 1 hawk hawk      403 2006-12-12 01:16 run.sh[/COLOR]
hawk@hawk-desktop:~/MP3s/Audiobooks/Bill Bryson - I'm a Stranger Here Myself$ **cat run.sh **
[COLOR="SlateGray"]#!/bin/sh

fn=$(readlink -f "$1")

comment=$(basename "$(dirname "$(dirname "$(dirname "$fn")")")")
artist=$(basename "$(dirname "$(dirname "$fn")")")
album=$(basename "$(dirname "$fn")")
filename=$(basename "$fn" .mp3)
track=${filename:0:2}
title=${filename: (-4)}

mid3v2 "$1" \
   --comment="$comment" \
   --artist="$artist" \
   --album="$album" \
   --track="$track" \
   --song="$title [$track]"[/COLOR]
hawk@hawk-desktop:~/MP3s/Audiobooks/Bill Bryson - I'm a Stranger Here Myself$ **./run.sh Bill\ Bryson\ -\ I\'m\ a\ Stranger\ Here\ Myself\ -\ \(0001\).mp3 **
[COLOR="SlateGray"]./run.sh: 9: Syntax error: Bad substitution[/COLOR]
hawk@hawk-desktop:~/MP3s/Audiobooks/Bill Bryson - I'm a Stranger Here Myself$
```

---

### Post by po0f on 2006-12-12
JHawk24821,

```
[FONT="Courier New"]$ sudo dpkg-reconfigure dash[/FONT]
```
Does running this command help any?  It would only help if you are running Edgy, Dapper's shell interpreter is still the sane default of Bash.  :)

---

### Post by duff on 2006-12-12
Hey! You can't change the format of the filename and then blame the script for not picking up the difference.  It's only checking for "track - title.mp3", you're giving it "title - (track).mp3".

Try these two changes
```
track=${filename:(-5):4}
title=$(basename "${filename}" " - ($track)")
```

Oh, and poof just made me realize I have /bin/sh symlinked to bash, not dash.  In case some of this is bash specific, change the first line to ```
#!/bin/bash
```

---

### Post by JHawk24821 on 2006-12-12
```
hawk@hawk-desktop:~$** sudo dpkg-reconfigure dash**
      *I answered Yes to sent bash as bin/sh*
hawk@hawk-desktop:~$ **./run.sh MP3s/Audiobooks/Bill\ Bryson\ -\ I\'m\ a\ Stranger\ Here\ Myself/Bill\ Bryson\ -\ I\'m\ a\ Stranger\ Here\ Myself\ -\ \(0001\).mp3**
[COLOR="SlateGray"]./run.sh: 9: Syntax error: Bad substitution[/COLOR]
```

(pulls hair out)

---

### Post by JHawk24821 on 2006-12-12
> Hey! You can't change the format of the filename and then blame the script for not picking up the difference. It's only checking for "track - title.mp3", you're giving it "title - (track).mp3".

?!  You mean I can't go changing things on my end and just expect your script to magically work anyways!?  Tsk tsk.  :rolleyes:  Can't believe I didn't catch that.  Thanks, I am pretty sure this will fix it, updates soon.

---

### Post by JHawk24821 on 2006-12-12
Whooooopie!

```
hawk@hawk-desktop:~$ **./run.sh MP3s/Audiobooks/Bill\ Bryson\ -\ I\'m\ a\ Stranger\ Here\ Myself/Bill\ Bryson\ -\ I\'m\ a\ Stranger\ Here\ Myself\ -\ \(0001\).mp3**
[COLOR="SlateGray"]Writing MP3s/Audiobooks/Bill Bryson - I'm a Stranger Here Myself/Bill Bryson - I'm a Stranger Here Myself - (0001).mp3
No ID3 header found; creating a new tag[/COLOR]
```

Now to tweak the code so that it writes the correct information.  Thanks for all your help!

*Victory is sweetest when you've known defeat.*
- Malcolm S. Forbes

---

### Post by cgrebeld on 2006-12-12
Hey, Amarok has a built in tagging in 'track information'-> Filename Schemes, with syntax like:

(%artist) %title (%comment)

It also has a scripting interface, so there is probably an easy way to batch rename some files.

---


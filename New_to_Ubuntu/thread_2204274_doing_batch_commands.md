---
title: "doing batch commands"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by 118118 on 2014-02-07
i have about 200 wav files, created thru wavbreaker. i want to use sox to convert to sph, then run a program on them (sphinx).

i then want to create 200 short speech files, from those results. i have been using espeak.

finally, i want to "stretch" those newly generated sound files to 2 seconds.

the problem is that i don't know how to do bactch commands!

thanks for any help...

---

### Post by sudodus on 2014-02-07
In principle, a shell-script is a list of commands, that you can run manually in a terminal window. If you want to repeat them for all files in a directory, you need some kind of loop command. In this case a for-loop might work well.

So make a file which contains something like the following, make it executable and run it (test it first in a test directory with some copies, so that you won't destroy anything, when running with the real files).

```

#!/bin/bash

for i in *.wav
do
   command1 (where you refer to the current file as "$i")
   command2 ...
   ...
done

```

---

### Post by tgalati4 on 2014-02-07
First work out the precise *sox* command needed to operate on your files.  Be sure to include all of the correct switches.  Post that command.

Then plug the command into *sudodus'* script and save it as a file called *speech_converter.sh*.

Give it executable privilege:

```
sudo chmod +x speech_converter.sh
```

Then run it:

```
./speech_converter.sh
```

The dot and forward slash are important and this assumes that your script is in the same directory as your sound files.  Otherwise make a directory called *bin* in your home directory and put it there.  Then you can just call it without using the dot and slash.

---

### Post by 118118 on 2014-02-08
> **sudodus said:**
> In principle, a shell-script is a list of commands, that you can run manually in a terminal window. If you want to repeat them for all files in a directory, you need some kind of loop command. In this case a for-loop might work well.

So make a file which contains something like the following, make it executable and run it (test it first in a test directory with some copies, so that you won't destroy anything, when running with the real files).

```

#!/bin/bash

for i in *.wav
do
   command1 (where you refer to the current file as "$i")
   command2 ...
   ...
done

```this worked well, thanks.

the output from sphinx will be a single file like the following

dog  <A.wav>
cat  <B.wav>
sound  <C.wav>

etc. what's the best way do text to speech on each line, and output each line to a different file?

---

### Post by sudodus on 2014-02-08
You have used ***espeak***, and if you are happy with it, continue using it also in the batch file.

I mean you can use espeak to create a wave file, but you can also use it the 'speak' the work directly.

There are many programs that can convert wav files to compressed formats. There are many command line programs, than can play an audio file, for example ***mplayer***. Use one that works well for you. Use a more advanced program to mix different soundtracks, for example ***audacity***.

---

### Post by 118118 on 2014-02-09
working great so far...

finally, i need a) a command line timestretching app that will stretch to a desired length (2 seconds for every file).
b) a way to merge 200 .wavs alphabetically.


:) ?

---

### Post by 118118 on 2014-02-09
i'm happy to write something that will use sox to read the length of the wav, then work out what arguments to add say - soundstretcher. but how do i automate that?

good exercise :) !

---

### Post by 118118 on 2014-02-09
it's a pretty straightforward thing

```
for i in A*.wav
do
soundstretch $i B$i -tempo=n
done
```

except in place of n i need the % change.
which i think is (2/(soxi -D $i)-1)*100, but i don't know how to code that

---

### Post by tgalati4 on 2014-02-10
Use a variable to hold the time in seconds:

(Written in pseudo code to gloss over any errors.)

```

# Super cheesy script to stretch clips to 2 seconds
#
for i in A*.wav
do
     clip_time_in_seconds=soxi -D $i
     tempo=(2/($clip_time_in_seconds)-1)*100
     soundstretch $i B$i -tempo=$tempo
done

```

---

### Post by 118118 on 2014-02-10
hi,
thanks for replying but i don't know how to write the code in question - i'm new to ubuntu.
?

---

### Post by 118118 on 2014-02-10
```
echo "((2/`soxi -D $i`)-1)*100" | bc -l
```

gives me the value i need, but i don't know how to add that to the script

```
for i in A*.wav
do
soundstretch $i B$i -tempo=n
done
```

---

### Post by tgalati4 on 2014-02-10
I'm not sure how you are using *bc*, but the script would look like:

```
#!/bin/bash
for i in A*.wav
    do
     length=exec soxi -D $i 
     tempo=((2/$length)-1)*100
     soundstretch $i B$i -tempo=$tempo
    done

exit 0

```

Scripting guide:  [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

---

### Post by 118118 on 2014-02-11
i get the following error with your script

./runme.txt: line 5: syntax error near unexpected token `('
./runme.txt: line 5: `     tempo=((2/$length)-1)*100'

---

### Post by tgalati4 on 2014-02-11
Put in some echo statements to see what the values are:

echo $length
echo $tempo

Because you are dividing by length, it's possible that it could be 0, and that would cause it to blow up. So we need a 0 check in there as well.

---

### Post by tgalati4 on 2014-02-11
This is closer:  Bash doesn't do floating point math!

```

#!/bin/bash
for wave_file in A*.wav
    do
     echo "Filename" $wave_file
     length=`soxi -D $wave_file`
     echo "Length in seconds" $length
     tempo=`echo "((2.0/$length)-1.0)*100.0" | bc -l`
     echo "Percentage expansion--tempo" $tempo
     soundstretch $wave_file B$wave_file -tempo=$tempo
    done

exit 0


```

Now I understand why you are using *bc*.

---


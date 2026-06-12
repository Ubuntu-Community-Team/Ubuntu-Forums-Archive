---
title: "python script to convert flac to mp3"
date: 2008-08-11
forum: Programming Talk
---

### Post by magicplayr2000 on 2008-08-11
I'm trying to convert all of my flac files to mp3 (there are a lot of them in my over 13k music files) so that I can copy them to my iPod.  I'm having a hard time finding anything that can do this for lots of files across multiple directories, so I've decided I'm going to use it as a chance to practice with python.  Moving through the directories and checking to see if the file is *.flac or not will be easy enough, but I'm not sure how to go about converting.  I kinda doubt it, but does python have anything built in to do this?  And if not, does anyone know of a library out there that will handle this?

---

### Post by mssever on 2008-08-11
> **magicplayr2000 said:**
> I'm trying to convert all of my flac files to mp3 (there are a lot of them in my over 13k music files) so that I can copy them to my iPod.  I'm having a hard time finding anything that can do this for lots of files across multiple directories, so I've decided I'm going to use it as a chance to practice with python.  Moving through the directories and checking to see if the file is *.flac or not will be easy enough, but I'm not sure how to go about converting.  I kinda doubt it, but does python have anything built in to do this?  And if not, does anyone know of a library out there that will handle this?
I don't know about Python, but this is trivial in Bash:
```
for i in *.flac; do
    sox "$i" "${i/.flac/}".mp3
done
```

---

### Post by magicplayr2000 on 2008-08-11
Will that walk through every folder recusively?  I would also like it do dump everything out to a seperate folder from my normal music collection so that I don't have duplicates of all my flac files in my normal media player.

To get an idea of how my files are set up, here's an example:
```

Music
|_A
  |_Audioslave
  | |_stuff.flac
  | |_morestuff.flac
  |_Aquabats
    |_mp3file.mp3
```

Not everything in my music directory is flac, so it'd need to avoid those.

---

### Post by mssever on 2008-08-11
> **magicplayr2000 said:**
> Will that walk through every folder recusively?
No, that script only operates on *.flac files in the current directory. Here's some untested code to hopefully do what you want:
```
#!/bin/bash
output_dir="/some/dir"
input_dir="/some/other/dir"

function converter {
  local directory="$1"
  local i
  for i in "$directory"/*; do
    if [ "$i" = . -o "$i" = .. ]; then continue
    elif [ -d "$i" ]; then converter "$directory/$i"
    elif [[ "$i" =~ \.flac$ ]]; then sox "$i" "$output_dir/${i/.flac/}.mp3"
    fi
  done
}

converter "$input_dir"
```

---

### Post by ghostdog74 on 2008-08-11
to do recursive, you can use find
```

find /path -name "*.flac" -printf "%p %f\n" | while read a b ; do echo "sox $a ${a/.flac/.mp3}"; done

```
to do it in Python, you can use os.walk. See [here](http://docs.python.org/lib/os-file-dir.html) for example.

---

### Post by mssever on 2008-08-11
> **ghostdog74 said:**
> to do recursive, you can use find
```

find /path -name "*.flac" -printf "%p %f\n" | while read a b ; do echo "sox $a ${a/.flac/.mp3}"; done

```to do it in Python, you can use os.walk. See [here]("http://docs.python.org/lib/os-file-dir.html") for example.
I never thought of using find. On problem, though: Your code doesn't save the converted files to a different directory tree, as the OP requested.

---

### Post by magicplayr2000 on 2008-08-11
Thanks for that.  I'm trying to get it to work, but I've done next to nothing with bash.  So far, I've noticed that elif should be else if, and now I'm getting an error on the second else if clause near the "=~" operator.  It says syntax error in conditional expression near '=~'.

---

### Post by magicplayr2000 on 2008-08-11
> **ghostdog74 said:**
> to do recursive, you can use find
```

find /path -name "*.flac" -printf "%p %f\n" | while read a b ; do echo "sox $a ${a/.flac/.mp3}"; done

```
to do it in Python, you can use os.walk. See [here](http://docs.python.org/lib/os-file-dir.html) for example.
Yeah I was gonna use os.walk in python to walk through everything, but the problem was converting the files.  I guess I could use exec() to run sox though.  But now that I've started with the bash thing, it's kinda fun to try to follow along :P.

I really appreciate the help on this.

---

### Post by mssever on 2008-08-11
> **magicplayr2000 said:**
> So far, I've noticed that elif should be else if, and now I'm getting an error on the second else if clause near the "=~" operator.  It says syntax error in conditional expression near '=~'.
Sounds like you aren't using Bash. Remember, sh is not equivalent to bash. Either make the file executable, and call it as ./filename, or run it as bash filename.

EDIT: elif and =~ are valid in bash, but not necessarily in other shells.

---

### Post by magicplayr2000 on 2008-08-11
OK, I mistyped something.  Now it's running, but not actually converting the files.

After throwing in a print statement, it looks like it's a problem with how I jump to the next file:
```

Error: no such file "/home/user/Test//home/user/Test/Cake - Comfort Eagle (FLAC)"

```
I fixed this by getting rid of calling $directory over again in the recursive call, and now it's coming up with a sox problem.  All of my .flac files are coming up as unknown file type `flac'.  Do I need anything special for sox to work with flac files?  I'm running ubuntu server edition, so it may not have certain things needed to handle music normally...

EDIT:  After looking at sox's supported file formats, it looks like flac isn't supported:

SUPPORTED FILE FORMATS: 8svx aif aifc aiff aiffc al alsa au auto avr cdda cdr cvs cvsd dat dvms fssd hcom ima ircam la lpc lpc10 lu m3u maud nist nul null pls prc raw s1 s2 s3 s4 sb sf sl smp snd sndt sou sph sw txw u1 u2 u3 u4 ub ul uw vms voc vox wav wavpcm wve xa

---

### Post by ghostdog74 on 2008-08-11
> **mssever said:**
> I never thought of using find. On problem, though: Your code doesn't save the converted files to a different directory tree, as the OP requested.

The trick will be to use variable $b. I will leave it to OP to play with it.
@OP. since sox doesn't have flac support as you said, you can try ffmpeg. From some other thread.
```

ffmpeg -i input.flac -ab 196k -ac 2 -ar 48000 output.mp3

```

---

### Post by magicplayr2000 on 2008-08-11
OK, so I've made some modifications to the script, and here's what I've got:
```

#!/bin/bash
output_dir="/home/keith/TestResults"
input_dir="/home/keith/Test"

function converter {
        local directory="$1"
        local i
        for i in "$directory"/*; do
                if [ "$i" = . -o "$i" = .. ]; then continue
                elif [ -d "$i" ]; then converter "$i"
#               elif [[ "$i" =~ \.flac$ ]]; then sox "$i" "$output_dir/${i/.flac/}.mp3"
                else
                        for file in "$i"; do
                                if [[ "$file" =~ \.flac$ ]]; then
                                        echo "$i"
                                        flac -cd "$file" | lame -h - "$output_dir/${file%.flac}.mp3";
                                fi
                        done
                fi
        done
}

```
I decided to use flac and lame (found a site that suggested it) to do the conversion, and it runs through now, but now I get this problem:
```

/home/keith/Test/Cake - Comfort Eagle (FLAC)/01 - Opera Singer.flac

flac 1.2.1, Copyright (C) 2000,2001,2002,2003,2004,2005,2006,2007  Josh Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Can't init outfile '/home/keith/TestResults//home/keith/Test/Cake - Comfort Eagle (FLAC)/01 - Opera Singer.mp3'
/home/keith/Test/Cake - Comfort Eagle (FLAC)/02 - Meanwhile, Rick James....flac

#lots more of the same as above.

```
Not sure what it means by "Can't init outfile".  My guess is that it can't start to create the output file.

Actually, i see the problem I think... it's the same problem I was having earlier.  $file returns the absolute file path, so when I join that with $output_dir it makes it weird.  Is there any way to just isolate the filename instead of the entire filepath?

---

### Post by mssever on 2008-08-11
> **magicplayr2000 said:**
> Actually, i see the problem I think... it's the same problem I was having earlier.  $file returns the absolute file path, so when I join that with $output_dir it makes it weird.  Is there any way to just isolate the filename instead of the entire filepath?
You can use the basename command for that, though I'm not convinced that's your problem, since two consecutive slashes in a filename should be automatically converted into one. However, I don't have any better explanation...

---

### Post by ghostdog74 on 2008-08-11
> **magicplayr2000 said:**
> 
Actually, i see the problem I think... it's the same problem I was having earlier.  $file returns the absolute file path, so when I join that with $output_dir it makes it weird.  Is there any way to just isolate the filename instead of the entire filepath?

try this
```


${output_dir}/${i/.flac/}.mp3

```

---

### Post by magicplayr2000 on 2008-08-13
Sorry to bump an old post, but I've made a little progress on this.  I'm using basedir to get just the filename, but now I'm getting this error:

```

Test/Cake - Comfort Eagle (FLAC)/11 - World of Two.flac

flac 1.2.1, Copyright (C) 2000,2001,2002,2003,2004,2005,2006,2007  Josh Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.


*.flac: ERROR initializing decoder
        init status = FLAC__STREAM_DECODER_INIT_STATUS_ERROR_OPENING_FILE

An error occurred opening the input file; it is likely that it does not exist
or is not readable.
Assuming raw pcm input file
LAME 3.97 32bits (http://www.mp3dev.org/)
CPU features: MMX (ASM used), SSE, SSE2
Using polyphase lowpass filter, transition band: 17249 Hz - 17782 Hz
Encoding <stdin> to /home/keith/TestResults/11 - World of Two.mp3
Encoding as 44.1 kHz VBR(q=4) j-stereo MPEG-1 Layer III (ca. 10x) qval=2

```
It looks like it's trying to encode (it makes the mp3 file, but it's empty).

Also, $i prints out as Test/Cake - Comfort Eagle (FLAC)/10 - Pretty Pink Ribbon.flac/*.flac.  I'm not sure what to do with the /*.flac on the end, or even how it got there.

---

### Post by mssever on 2008-08-15
> **magicplayr2000 said:**
> It looks like it's trying to encode (it makes the mp3 file, but it's empty).

Also, $i prints out as Test/Cake - Comfort Eagle (FLAC)/10 - Pretty Pink Ribbon.flac/*.flac.  I'm not sure what to do with the /*.flac on the end, or even how it got there.
Please show your current code. It appears that you're doing something incorrect in some for loop, but that's speculation since I don't know what your code is.

---


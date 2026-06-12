---
title: "How to pack 1 TB of wav audio files"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by Erik Kaiser on 2014-04-29
Dear community !
This is a request how to pack  approx. 1 TB of audio .wav files. The program Soundconverter has been  used to create some MP3s but the big amount of data can not be handled  with it. Whereas the previous version of Soundconverter has written the  mp3 files into the original folder as .mp3 directly under the wav file,  the new version writes the converted files into an automatically created  new folder with the name "unknown", a change in the preferences is impossible. The following problems occur : The  original files have many subfolders with similar file names. Ubuntu  overwrites similar file names, song 1 to song ..., a few hundred CDs,  always the same file names. All these are lost because already the  conversion of the second CD overwrites the first conversion due to equal file names. Also the  CDs have some DVD content disturbing the conversion if just added to  Soundvonverter in one command. The duration of the file conversion is  much too long, it does take up to 15 minutes per CD. It should be  possible to run a command for all files, go to bed, and check the work  in the morning. Just one command should erase every .wav file and the  remaining data should be compressed to perhaps 8 percent of its original  size. Eventually the former external TB drive now just needs a storage  medium in the size of a 64 GB USB flash drive. My Linux versions are Mint and Trusty Tahr. :guitar::guitar::guitar:Can you also recommend an efficient packing program  for the complete amount of files ? I could not get through with 7zip,  certainly this is a brilliant program, but a graphical user surface  would make our day, even better.

Have a nice day

Erik

---

### Post by sudodus on 2014-04-30
I think a shell-script with command line tools can do the job for you. Are you ready to

- use the terminal window and
- test some command line converting programs
- write a shell-script (a text file with commands)?

Otherwise, let us hope someone can suggest a tool with a graphical user interface.

-o-

Also, if there is no reply, you can bump the thread once a day (write 'bump' in a reply after 24 hours).

---

### Post by squakie on 2014-05-01
You're going to hate my suggestion:  be sure everything is organized as 1 album/CD per folder.  Name the folder something signifiant.  If you have multiple albums/CDs from the group/artist, create a folder first with that artist/group name, then create subfolders within each of those for each album/CD.

In this manner there can't be any way to confuse, as an example, ~/my-albums/artist1/CD1/track1  with ~/my-albums/artist1/CD2/track1 (song 1 if that's what you're calling them).  I would think there should be a way to specify that the output paths match the input paths or at least the naming conventions.

I may try soundconverter just to see if I can figure any of that out.

When you've created the mp3's, you are probably going to use one of the tools to insert/edit the album/track information for each track.

---

### Post by squakie on 2014-05-01
Well, tried soundrecorder myself but didn't figure out much.  There is a way to do it with a script, finding all *.wav files in a given path and using lame to convert the .wav files to .mp3 files, leaving the .wav files in place (you can always use another script to remove them).

I've been working on such a script but don't have it finished yet.

---

### Post by squakie on 2014-05-01
If you read this in the last 5 minutes, I made some changes to what is included here so it hopefully be clearer.

Ok, here's a sample script I came up.  Based on $INPATH, it searches that folder and all subfolders for any file with type of .wav.  It currently just echoes the lame statement so you can test.  If you remove the echo from the front of the lame statement then it will convert the input .wav file to .mp3 and write out a file with the same name but extension .mp3 in the same folder.

I'm not great at scripting, so someone can tell us if I'm doing somethin wrong.  Test it out by changing the text after INPATH to what ever the root path of your wav folders is.  Save this in a file called convert-wav-to-mp3.sh and  be sure to make it executable:  chmod convert-wav-to-mp3.sh.  After that you can execute it with ./convert-wav-to-mp3.sh and watch the output echoed on the screen to see if it would do what you want.

```
#!/bin/bash
INPATH=~/test
find $INPATH/* -name "*.wav" | while read FILE; do
        filename=$FILE
        extension=${filename##*.}
        filename=${filename%.*}
echo lame -V2 $filename.wav $filename.mp3 
done 

```


I tested this with a folder and subfolder both containing .wav files.  This is the output:```
dave@davelaptop:~/test$ cat convert-wav-to-mp3.sh
#!/bin/bash
INPATH=~/test
find $INPATH/* -name "*.wav" | while read FILE; do
        filename=$FILE
        extension=${filename##*.}
        filename=${filename%.*}
echo lame -V2 $filename.wav $filename.mp3 
done 

dave@davelaptop:~/test$ 
dave@davelaptop:~/test$ ls -al
total 28
drwxrwxr-x  3 dave dave 4096 May  1 05:06 .
drwxr-xr-x 36 dave dave 4096 May  1 04:38 ..
-rwxrwxr-x  1 dave dave  216 May  1 04:59 convert-wav-to-mp3.sh
-rw-rw-r--  1 dave dave  133 May  1 00:49 convert-wav-to-mp3.sh~
-rw-rw-r--  1 dave dave    0 May  1 04:44 junk.wav
drwxrwxr-x  2 dave dave 4096 May  1 05:06 sub1
-rwxrwxr-x  1 dave dave  215 May  1 04:53 test.sh~
-rwxrwxr-x  1 dave dave  216 May  1 04:59 test.wav
dave@davelaptop:~/test$ 
dave@davelaptop:~/test$ ls -al sub1
total 12
drwxrwxr-x 2 dave dave 4096 May  1 05:06 .
drwxrwxr-x 3 dave dave 4096 May  1 05:06 ..
-rwxrwxr-x 1 dave dave  255 May  1 01:53 test.wav
dave@davelaptop:~/test$ 
dave@davelaptop:~/test$ 
dave@davelaptop:~/test$ ./convert-wav-to-mp3.sh
lame -V2 /home/dave/test/junk.wav /home/dave/test/junk.mp3
lame -V2 /home/dave/test/sub1/test.wav /home/dave/test/sub1/test.mp3
lame -V2 /home/dave/test/test.wav /home/dave/test/test.mp3
dave@davelaptop:~/test$ 

```

---

### Post by sudodus on 2014-05-01
> **squakie said:**
> If you read this in the last 5 minutes, I made some changes to what is included here so it hopefully be clearer.

Ok, here's a sample script I came up.  Based on $INPATH, it searches that folder and all subfolders for any file with type of .wav.  It currently just echoes the lame statement so you can test.  If you remove the echo from the front of the lame statement then it will convert the input .wav file to .mp3 and write out a file with the same name but extension .mp3 in the same folder.

I'm not great at scripting, so someone can tell us if I'm doing somethin wrong.  Test it out by changing the text after INPATH to what ever the root path of your wav folders is.  Save this in a file called convert-wav-to-mp3.sh and  be sure to make it executable:  chmod convert-wav-to-mp3.sh.  After that you can execute it with ./convert-wav-to-mp3.sh and watch the output echoed on the screen to see if it would do what you want.

```
#!/bin/bash
INPATH=~/test
find $INPATH/* -name "*.wav" | while read FILE; do
        filename=$FILE
        extension=${filename##*.}
        filename=${filename%.*}
echo lame -V2 $filename.wav $filename.mp3 
done 

```

0. Yes, it works to use find and a while loop :-)

1. I suggest using lower-case names for your own variables to avoid conflicts with system shell variables (which are upper-case)

2. Double-quote the shell variables, otherwise file names with spaces will create problems

3. It will be simpler to use **/home/$USER/test** and  **filename** directly

```
#!/bin/bash
find "/home/$USER/test" -name "*.wav" | while read filename; do
  echo lame -V2 "$filename" "${filename/.wav}.mp3"
done 

```

---

### Post by squakie on 2014-05-01
Thanks!  I've got to learn more about scripting  - I understand everything until I get to the part in braces :)

I didn't think about spaces in the filename - thanks again!

Thanks for looking at my feeble attempt and making something usable!

Dave :)

---

### Post by Vaphell on 2014-05-01
technically home/$USER doesn't have to point to user's home if it's been set up otherwise, not to mention the root's home is /root not /home/root. $HOME is the real deal.

I'd also say that feeding data to while loop via pipe is suboptimal. 
```
while read filename
do
    echo lame -V2 "$filename" "${filename/.wav}.mp3"
done < <( find "$HOME/test" -name "*.wav" )
```

is more like it. No meaningful difference in this particular case but consider this example

```
$ x=0; while read l; do ((x++)); done < <( echo $'a\nb\nc' ); echo $x
3
$ x=0; echo $'a\nb\nc' | while read l; do ((x++)); done; echo $x
0
```
the version with pipes spawns a subprocess where the value gets updated but then discarded at the end and the parent scope doesn't know any better. Values updated in the version using redirection stick.

tl;dr: kosher way of using while loops in bash
```
while read x; do ....; done < file
while read x; do ....; done < <( cmd )
while read x; do ....; done <<< "string"
```

---

### Post by squakie on 2014-05-01
Well, I hope the OP is still following this so they can try these out to fix their problem.

There are a few things I don't understand about the latest posted version of the script:

- I thought the path on the find needed a trailing "/*" in order to pick up subfiles

- in my testing, the pieces that are "parsing" the filename are copies from something I found on the net.  I don't understand those, and I don't understand the one here as well.  I haven't learned, nor do I know where to find a simple beginners guide, how to make those kinds of statements and what they are doing.

So, what I was thinking was:


- even though this thread is not about scripting per se, a script is needed to perform the action.  Given that, perhaps it would greatly benefit the OP, definetly me, and perhaps others following or who may read this later, to give a simple break down of the script and what each piece is doing.

---

### Post by sudodus on 2014-05-02
This expression

```
"${filename/.wav}.mp3"
```

is removing the string .wav from filename and then adding .mp3 to it.

See the paragraph about parameter expansion in ```
man bash
```

```
       ${parameter/pattern/string}
              Pattern substitution.  The pattern is expanded to produce a pattern just as in  pathname
              expansion.   Parameter is expanded and the longest match of pattern against its value is
              replaced with string.  If pattern begins with /, all matches  of  pattern  are  replaced
              with  string.   Normally only the first match is replaced.  If pattern begins with #, it
              must match at the beginning of the expanded value of parameter.  If pattern begins  with
              %,  it  must  match  at  the end of the expanded value of parameter.  [COLOR=#0000ff]If string is null,
              matches of pattern are deleted and the / following pattern may be omitted.[/COLOR]  If parameter
              is  @  or *, the substitution operation is applied to each positional parameter in turn,
              and the expansion is the resultant list.  If parameter is an array variable  subscripted
              with  @ or *, the substitution operation is applied to each member of the array in turn,
              and the expansion is the resultant list.

```

---

### Post by sudodus on 2014-05-02
Thanks *Vaphell* for showing better ways to write while scripts :-)

Do you know a good tutorial for these things?

---

### Post by Vaphell on 2014-05-02
the best way to learn is to bait sisco311 into coming to your thread and flaming your ass ;-) Sadly he seems to be less active recently. I learned 95% of what i know about bash on this forum reading stuff.

Bash FAQ shows and explains commonly used patterns, including their caveats. Bash pitfalls is another must read. Both in my signature.


btw, stripping extension is more reliable with ${var%pattern} or with ${var/%pattern/substitution}, preferably the former. % makes sure the pattern is matched only at the very end.

```
$ file=/some/dir/tidal[COLOR="#0000FF"].wav[/COLOR]e/1[COLOR="#0000FF"].wav[/COLOR]
$ echo ${file/.wav}.mp3
/some/dir/[COLOR="#FF0000"]tidale[/COLOR]/1[COLOR="#FF0000"].wav[/COLOR].mp3    # wrong
$ echo ${file//.wav}.mp3
/some/dir/[COLOR="#FF0000"]tidale[/COLOR]/1.mp3    # wrong
$ echo ${file/%.wav/.mp3}
/some/dir/tidal.wave/1.mp3
$ echo ${file%.*}.mp3
/some/dir/tidal.wave/1.mp3
```

[http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html)
this chapter is pure gold. With these simple operations you can cut down the use of external tools for trivial text operations by 90%.
I don't know why ${var~} or ${var~~} are not mentioned in there (invert case on first chars of words, invert case on everything)

---

### Post by squakie on 2014-05-02
Thanks very much!  It's been over 25 years since I had any real knowledge of all of this.  I knew from then how powerful the shell is, but I can't for the life of me remember anything from back then.  I guess that's a plus since it's like starting over.  I have the opposite problem with programming - I knew C, assembler, etc., back then.  Now when I try to program I remember things - unfortunately usually incorrectly.  Sure the program compiles, and runs for a little while, until I find out I've got pointers, data types, memory allocation, variable initialization , etc., all goofed up! ;)

---

### Post by sudodus on 2014-05-02
Thanks again *Vaphell* :-)

Let us hope that our OP, *Erik Kaiser*, will also benefit from these tips.

---

### Post by squakie on 2014-05-02
Also, for me and others who may need to know:  could you explain the function of the 2 "<" and the find being in brackets does what?  I know when I had it on the front end that it was taking each file found and running it through the while statement.  i'm not familiar with having the find at the end nor "piping" it that way into the while loop.  I can only assume that I understand it, but that would get me in trouble ;)

---

### Post by Vaphell on 2014-05-02
> Also, for me and others who may need to know: could you explain the function of the 2 "<" and the find being in brackets does what?

Find does what it does.
These 2 <'s are a simple file redirection, but with a fake file created out of the command output, which removes the need for piping and tempfiles.
< is a standard [COLOR="#0000FF"]redirection[/COLOR], <( cmd ) is the [COLOR="#008000"]process substitution[/COLOR] which creates the pseudo-file.
The space between these 2 elements is required.

```
while read x; do ...; done [COLOR="#0000FF"]<[/COLOR][COLOR="#ADD8E6"]_[/COLOR][COLOR="#008000"]<( ... )[/COLOR]
```

If any command claims it accepts files as params, **<( cmd )** can be used there, eg

```
$ paste --help
Usage: paste [OPTION]... [FILE]...
Write lines consisting of the sequentially corresponding lines from
each FILE, separated by TABs, to standard output.
With no FILE, or when FILE is -, read standard input.
....
$ paste **[COLOR="#0000FF"]<( echo $'a\nb' )[/COLOR]** **[COLOR="#008000"]<( echo $'1\n2' )[/COLOR]**
[COLOR="#0000FF"]a[/COLOR]	[COLOR="#008000"]1[/COLOR]
[COLOR="#0000FF"]b[/COLOR]	[COLOR="#008000"]2[/COLOR]
```

---

### Post by squakie on 2014-05-03
Great!  Thanks!

---


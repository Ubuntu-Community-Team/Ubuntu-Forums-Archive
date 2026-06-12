---
title: "Bash add 2 digit Numbers"
date: 2011-07-05
forum: Programming Talk
---

### Post by jim2013 on 2011-07-05
I have a massive archive of audio recordings of church worship services in mp3 format. They are in a folder structure by year and each week has its own subfolder. Inside each week, there are between 18-29 mp3 files of that weeks audio split up into tracks as the service was burned to CD. the file names are as follows:

Track 1.mp3
Track 2.mp3
Track 11.mp3
Track 22.mp3

I am looking for a way to add a zero to the tracks under number 10 so they all have a 2 digit number.  I want the final result to look like this:

Track 01.mp3
Track 02.mp3
Track 11.mp3
Track 22.mp3

I just picked a few numbers to use as examples, the track numbers are all sequential. Can anyone help me rename these files. I would like a way to do this recursively, as there are thousands of files.

Thanks for your help,
Jim2013

---

### Post by pafoo on 2011-07-05
I will add more tomorrow because I am short on time tonight. This command can start you off, it will get you a list of all the files and there directories that are less than 10, then you can output that 2 a file and use that as your basis for a for loop ex for item in `cat list`; do

```

# $DIR, type in the root directory of where those mp3's are ex /music/
find $DIR -type f -name Track" "[0][0-9].mp3 > music list

```I realized that you must be a windows user because you put a space in your file name!! Which makes it more difficult to do with a shell script.

---

### Post by jim2013 on 2011-07-05
I didn't create the files myself, I just kind of got dumped a mess and told "Here you Go!" I'm not a windows fan. I do not like the spaces in the file names. If it would be possible, I would like to remove the spaces anyway. It will make actually implementing the files a whole lot easier. The files are all split into subdirectories, would that interfere with the find command you provided. Will this interfere at all?
Jim2013

---

### Post by pafoo on 2011-07-06
No, if you put the main directory to where the music is at, find will pull all of it, including which directory to each file that is less than 10. Try it without the > and you can see the output first. Just dont forget the space in between the " "

---

### Post by pafoo on 2011-07-06
By the way, the "Dumped on you and Here you go!" Statment is what gets most of us Linux/Unix administrators started! Mine started with a, hey Build me a LAMP Linux server from scratch. I was like, huh whats that LOL. Lots of googling and research and you would be surprised what you end up learning! Best way to learn programming is to get a project and just figure it out from there lol.

---

### Post by geirha on 2011-07-06
```
find . -type f -name "Track [0-9].mp3" -exec sh -c 'for file; do mv "$file" "${file%[0-9].mp3}0${file##* }"; done' _ {} +
```

See [http://mywiki.wooledge.org/BashFAQ/030](http://mywiki.wooledge.org/BashFAQ/030) for other approaches.

---

### Post by Habitual on 2011-07-06
> **pafoo said:**
> By the way, the "Dumped on you and Here you go!" Statment is what gets most of us Linux/Unix administrators started!...

Exactly! "Here's a keyboard and a password, GO!"
What a ride. ;)

---

### Post by jim2013 on 2011-07-06
Thanks for the prompt replys, the previous reply worked.
Thanks,
Jim2013

---

### Post by pafoo on 2011-07-06
> **geirha said:**
> ```
find . -type f -name "Track [0-9].mp3" -exec sh -c 'for file; do mv "$file" "${file%[0-9].mp3}0${file##* }"; done' _ {} +
```See [http://mywiki.wooledge.org/BashFAQ/030](http://mywiki.wooledge.org/BashFAQ/030) for other approaches.

Brilliant

---

### Post by stylishpants on 2011-07-07
The rename utility bundled with perl can do this too, and is much shorter.
This is installed by default on Ubuntu.  You may need to call it as 'prename' on some systems though.


```
bob@cob:/tmp/junk$ for i in `seq 1 22`; do touch "Track $i.mp3"; done

bob@cob:/tmp/junk$ ls
Track 10.mp3  Track 15.mp3  Track 1.mp3   Track 3.mp3  Track 8.mp3
Track 11.mp3  Track 16.mp3  Track 20.mp3  Track 4.mp3  Track 9.mp3
Track 12.mp3  Track 17.mp3  Track 21.mp3  Track 5.mp3
Track 13.mp3  Track 18.mp3  Track 22.mp3  Track 6.mp3
Track 14.mp3  Track 19.mp3  Track 2.mp3   Track 7.mp3

bob@cob:/tmp/junk$ rename 's/\d+/sprintf("%03d",$&)/e' *.mp3

bob@cob:/tmp/junk$ ls
Track 001.mp3  Track 006.mp3  Track 011.mp3  Track 016.mp3  Track 021.mp3
Track 002.mp3  Track 007.mp3  Track 012.mp3  Track 017.mp3  Track 022.mp3
Track 003.mp3  Track 008.mp3  Track 013.mp3  Track 018.mp3
Track 004.mp3  Track 009.mp3  Track 014.mp3  Track 019.mp3
Track 005.mp3  Track 010.mp3  Track 015.mp3  Track 020.mp3
```

Or with subdirectory support:
```
find . -type f -name \*.mp3 -print0|xargs -0 rename 's/\d+/sprintf("%03d",$&)/e'
```

---

### Post by mlsfit138 on 2011-08-17
OK, I have a very similar problem.  The only difference is that I have not named each file "track ##.mp3, but I have actually named each file for it's song title as well.  Here is an example:

-rw-r--r-- 1 convergence users 4923817 Apr 17 20:18 14 - John Woo (demo).mp3
-rw-r--r-- 1 convergence users 6385212 Apr 17 20:18 1 - Hutton's Great Heat Engine.mp3
-rw-r--r-- 1 convergence users 4679311 Apr 17 20:18 2 - John Woo.mp3


I just don't have the knowledge to alter either of the above solutions to fit my naming scheme (they don't seem to do anything at all).

I guess that it wouldn't kill me to rename all of the files to use the same layout that was used above, but I'd rather not if possible.

Any help would be appreciated.

---

### Post by mlsfit138 on 2011-08-17
I probably should have mentioned that there are a ton of files involved in a directory tree very similar to the one used above, so recursion will be important.

---

### Post by mlsfit138 on 2011-08-17
> **stylishpants said:**
> The rename utility bundled with perl can do this too, and is much shorter.
This is installed by default on Ubuntu.  You may need to call it as 'prename' on some systems though.


```
bob@cob:/tmp/junk$ for i in `seq 1 22`; do touch "Track $i.mp3"; done

bob@cob:/tmp/junk$ ls
Track 10.mp3  Track 15.mp3  Track 1.mp3   Track 3.mp3  Track 8.mp3
Track 11.mp3  Track 16.mp3  Track 20.mp3  Track 4.mp3  Track 9.mp3
Track 12.mp3  Track 17.mp3  Track 21.mp3  Track 5.mp3
Track 13.mp3  Track 18.mp3  Track 22.mp3  Track 6.mp3
Track 14.mp3  Track 19.mp3  Track 2.mp3   Track 7.mp3

bob@cob:/tmp/junk$ rename 's/\d+/sprintf("%03d",$&)/e' *.mp3

bob@cob:/tmp/junk$ ls
Track 001.mp3  Track 006.mp3  Track 011.mp3  Track 016.mp3  Track 021.mp3
Track 002.mp3  Track 007.mp3  Track 012.mp3  Track 017.mp3  Track 022.mp3
Track 003.mp3  Track 008.mp3  Track 013.mp3  Track 018.mp3
Track 004.mp3  Track 009.mp3  Track 014.mp3  Track 019.mp3
Track 005.mp3  Track 010.mp3  Track 015.mp3  Track 020.mp3
```Or with subdirectory support:
```
find . -type f -name \*.mp3 -print0|xargs -0 rename 's/\d+/sprintf("%03d",$&)/e'
```
  
Ok, I've read this post a bit closer, and it seems like this solution should actually work for me, but it doesn't.  From my best attempt at understanding these commands, they seem to act only on the relevant parts of each file name (the numbered part), so that the rest of each filename doesn't matter.  I think that the problem may be that I am using the wrong "rename" program.  I am on arch linux, and I do have perl installed but "man rename" says that rename is a part of the util-linux package (that doesn't sound like it would have been bundled with perl).  There doesn't seem to be an executable called "prename" on my computer, and a search of the arch repositories only lists gprename.

Is it likely that I am using the wrong "rename" command?

---

### Post by mlsfit138 on 2011-08-17
I've tried to duplicate what you've done:

```

for i in `seq 1 22`; do touch "Track $i.mp3"; done
[convergence@t1000 test]$ ls
Track 10.mp3  Track 13.mp3  Track 16.mp3  Track 19.mp3  Track 21.mp3  Track 3.mp3  Track 6.mp3  Track 9.mp3
Track 11.mp3  Track 14.mp3  Track 17.mp3  Track 1.mp3   Track 22.mp3  Track 4.mp3  Track 7.mp3
Track 12.mp3  Track 15.mp3  Track 18.mp3  Track 20.mp3  Track 2.mp3   Track 5.mp3  Track 8.mp3
[convergence@t1000 test]$ rename 's/\d+/sprintf("%03d",$&)/e' *.mp3
[convergence@t1000 test]$ ls
Track 10.mp3  Track 13.mp3  Track 16.mp3  Track 19.mp3  Track 21.mp3  Track 3.mp3  Track 6.mp3  Track 9.mp3
Track 11.mp3  Track 14.mp3  Track 17.mp3  Track 1.mp3   Track 22.mp3  Track 4.mp3  Track 7.mp3
Track 12.mp3  Track 15.mp3  Track 18.mp3  Track 20.mp3  Track 2.mp3   Track 5.mp3  Track 8.mp3

```

So as you can see, it did not rename the files.

---

### Post by geirha on 2011-08-17
> **mlsfit138 said:**
> I've tried to duplicate what you've done:

So as you can see, it did not rename the files.

Are you running that on Ubuntu? There are several different rename commands, using completely different syntaxes. The default rename command in Ubuntu is perl rename, with which stylishpants' rename command will work. It looks like you might have the util-linux rename command there.

---

### Post by mlsfit138 on 2011-08-17
Yeah, that's what I figured.  I guess my options are try to figure out the syntax of the util-linux version of rename, or swap rename utilities.

---

### Post by mlsfit138 on 2011-08-17
someone was kind enough to write this up for me:
```
find . -type f -name '[[:digit:]] *' -execdir bash -c 'for f in "${@##*/}"; do mv "./$f" "./0$f"; done' _ {} + 
```which worked like a charm.

---


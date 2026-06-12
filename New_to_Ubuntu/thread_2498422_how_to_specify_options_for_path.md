---
title: "how to specify options for path?"
date: 2024-06-13
forum: New to Ubuntu
---

### Post by ainurftn on 2024-06-13
I cannot figure out how to specify the options for the path, i tried multiple times but it still doesn't work.

Can someone please help?


```
sudo spades.py -k 127 --careful -1 /Documents/AINUR/MYD/MYD_1.clean.fq -2 /Documents/AINUR/MYD/MYD_2.clean.fq -o /Documents/AINUR/MYD/spades_MYD_output_denovo_assembly -t 16

= Error ==  Please specify option (e.g. -1, -2, -s, etc) for the following paths: /Documents/AINUR/MYD/MYD_1.clean.fq
```

---

### Post by TheFu on 2024-06-13
There are two types of paths to files and directories. Seems you haven't learned this, though it works exactly the same on MacOS, MS-Windows, MS-DOS, and all Unix-like OSes.

1. Relative paths.  These are relative to the pwd/cwd - present workding directory aka the current working directory.  These types of paths begin with anything other than a '/' character.  Typically, they would be with a ../ or no directory separator at all.   For example, if your PWD is /tmp/ and you want to see the files listed there, you'd type **ls**.  Or **ls /tmp**

You can also type **ls /home/ainurftn** to see the files in your HOME directory.  Similarly, **ls ~/** or **ls $HOME** or **ls ~ainurftn** are the same.

2. Absolute paths.  These always begin with a '/' character. Your example above, /Documents/AINUR/MYD/MYD_1.clean.fq is an absolute path.  It may exist, but likely does not, as it would not be normal for "Documents" to be outside a "HOME" directory.  I can only make an educated guess (30+ yrs of education, and there are lots of exceptions, but ... )   that you really want to use **ls ~/Documents/AINUR/MYD/MYD_1.clean.fq** as the shortest way.  However, ~/ is dependent on the current userid.  If your pwd is ~/ainurftn, then you can just use Documents/AINUR/MYD/MYD_1.clean.fq without the leading '/' character.

Any beginning Unix book would explain this.  Get one here: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) - free, no-hassle, download.  You can walk into any bookstore and buy a copy, if you like or just download the PDF.

Anyway, I hope that is clear and doesn't confuse things.  If you also learn to use tab-completion, then you'll never attempt to run a command with the wrong inputfile again. Tab-completion will only fill in existing paths/filenames.  It is one of those shell tools that is hard to explain in words, but simple to see and learn to use in less than 20 seconds watching a video.  There must be 5000 of them on YT. Spend the time to learn this part of your shell. It will save you thousands of hours and prevent millions of mistakes.

---

### Post by ActionParsnip on 2024-06-13
Should it not be
```

sudo spades.py -k 127 --careful -1 $HOME/Documents/AINUR/MYD/MYD_1.clean.fq -2 $HOME/Documents/AINUR/MYD/MYD_2.clean.fq -o $HOME/Documents/AINUR/MYD/spades_MYD_output_denovo_assembly -t 16

```
I assume the files are in /home/$USER/Documents.... etc

TheFU's explanaition is very succinct and explains it well. "/" is the root of the file system, not your user's home folder.

---

### Post by ainurftn on 2024-06-13
I tried the **/home/Documents/AINUR/MYD/MYD_1.clean.fq **but it still doesn't work.

spades.py -k 127 --careful -1 --pe1 -1/home/colfax/Documents/AINUR/MYD/MYD_1.clean.fq -2 --pe1-2 -2/home/colfax/Documents/AINUR/MYD/MYD_2.clean.fq -o .home/colfax/Documents/AINUR/MYD/spades_MYD_output_denovo_assembly -t 16



== Error ==  Please specify option (e.g. -1, -2, -s, etc) for the following paths: /home/colfax/Documents/AINUR/MYD/MYD_1.clean.fq, /home/colfax/Documents/AINUR/MYD/MYD_2.clean.fq

---

### Post by TheFu on 2024-06-13
/home/Documents/AINUR/MYD/MYD_1.clean.fq
is not
$HOME/Documents/AINUR/MYD/MYD_1.clean.fq

Details matter!

spades.py -k 127 --careful -1 --pe1 -1/home/colfax/Documents/AINUR/MYD/MYD_1.clean.fq -2 --pe1-2 -2/home/colfax/Documents/AINUR/MYD/MYD_2.clean.fq -o .home/colfax/Documents/AINUR/MYD/spades_MYD_output_denovo_assembly -t 16

Shows inconsistencies.  You are missing spaces between the different options.  
```
--pe1 [COLOR="#FF0000"]-1/h[/COLOR]ome/colfax/Documents/AINUR/MYD/MYD_1.clean.fq 

```is not
```
--pe1     -1     /home/colfax/Documents/AINUR/MYD/MYD_1.clean.fq 
```
Spaces matter.

$HOME is an environment variable.  Did you get that PDF book and start reading?

---

### Post by deadflowr on 2024-06-13
Looks like -pe1 needs to be connected to the last number so it should read as pe1-1 with no space.
see: [https://ablab.github.io/spades/running.html](https://ablab.github.io/spades/running.html)

---

### Post by TheFu on 2024-06-13
> **deadflowr said:**
> Looks like -pe1 needs to be connected to the last number so it should read as pe1-1 with no space.
see: [https://ablab.github.io/spades/running.html](https://ablab.github.io/spades/running.html)

Good catch.  There are examples in that link. Here's one.
```
spades.py --pe1-1 lib1_forward_1.fastq --pe1-2 lib1_reverse_1.fastq \
          --pe1-1 lib1_forward_2.fastq --pe1-2 lib1_reverse_2.fastq \
          -o spades_output

```

Note where spaces ARE and where spaces ARE NOT.  It matters.

---


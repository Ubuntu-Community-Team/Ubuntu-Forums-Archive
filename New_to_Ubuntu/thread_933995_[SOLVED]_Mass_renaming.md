---
title: "[SOLVED] Mass renaming"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by echo314 on 2008-09-30
I have some ogg's that I would like to have renamed. Right now, the first part of the file names all consists of the same string of characters. Right now it generally follows the format 

```
01 - Jun Senoue, Kenichi Tokoi, Masaru Setsumaru, Fumie Kumatani - Introduction ~ feat Open Your Heart.ogg
02 - Jun Senoue, Kenichi Tokoi, Masaru Setsumaru, Fumie Kumatani - Welcome to Station Square.ogg
```

N - A - S

Where N is the Track number, 

A is the artist (which is super long, so on my mp3 player I would not be able to see the actual song title.) Note, this is the same for every track

S is the song title, thats the part I want to keep, along with the numbers I guess. 

So I just want to take out the Artist string in the filenames. Is the quickest way to do this a script?

I'm a bit of a Sonic Adventure fan.

---

### Post by walkingthecow on 2008-09-30
Just write a shell script with a regular expression.

---

### Post by walkingthecow on 2008-09-30
or use awk...

---

### Post by echo314 on 2008-09-30
I love you both. Just try to treat me more like an idiot next time, I need the extra clarification! 

Lets start with the shell script. How might I write this expression? I just might be able to write a script for doing one file, but I don't know anything about making it recursive.

---

### Post by walkingthecow on 2008-09-30
for file in *.ogg; do your code here; done

That is how to deal with all *.ogg files in the directory. The code, I think you can figure that out. I personally would use awk:

ls *.ogg | awk ' {printf("mv setup regex delmiter here", $x, $x) | "bash"}'

$x and $x being the fields, and you'll need to setup the regular expression that states the format of the files.

---

### Post by kpkeerthi on 2008-09-30
Try **exfalso** if you prefer a GUI. 

To install, open a terminal and run this command:
```
sudo apt-get update && sudo apt-get install exfalso
```

Open exfalso, browse to the folder containing your oggs (keep a back up, just in case). Select all files in the bottom pane. Now go to Rename Files tab and choose the format. Click Preview to see how the files will be renamed and change the format suit your need. Finally click Save. Done.

---

### Post by walkingthecow on 2008-09-30
Go with CLI. Actually try to learn Linux rather than treating it like it is Windows. It's unbelievable how many people run Linux now and don't even know how to create a directory without the use of their mouse.

---

### Post by MrFSL on 2008-09-30
Well for the sake of the community at large I will throw in my 2 cents and recommend a perl script. (Gotta love those perl regular expressions)

---

### Post by walkingthecow on 2008-09-30
Totally agree, I would also recommend doing this with a perl script. I am not trying to be holier than thou, but part of the fun of using linux is overcoming challenges, and doing everything with the simple click-click of a GUI just seems like such a waste of a great OS. Hey, maybe you'll enjoy figuring out how to script this, stick with it and become a contributor some day... who knows?

---

### Post by davidryder on 2008-09-30
pyRenamer has been my favorite batch renamer. It's in the standard repository.

---

### Post by ghostdog74 on 2008-09-30
> **echo314 said:**
> 
So I just want to take out the Artist string in the filenames. Is the quickest way to do this a script?


if you have Python, you can use my script in my sig called File Renamer.
eg usage
```

# python filerenamer.py -p "(.*)-(.*)-(.*)" -e "\\1\\3" -l "*.ogg"

```
remove -l to commit.

---

### Post by echo314 on 2008-09-30
Alright guys thanks for your help. I think I've got this figured out now.

---

### Post by KIAaze on 2008-09-30
You can also use Thunar Bulk Rename: [http://thunar.xfce.org/pwiki/documentation/bulk_renamer](http://thunar.xfce.org/pwiki/documentation/bulk_renamer)

Just install thunar:
```
sudo apt-get install thunar
```

And run:
```
Thunar -B
```

> **walkingthecow said:**
> Just write a shell script with a regular expression.
> **walkingthecow said:**
> or use awk...
> **walkingthecow said:**
> Totally agree, I would also recommend doing this with a perl script. I am not trying to be holier than thou, but part of the fun of using linux is overcoming challenges, and doing everything with the simple click-click of a GUI just seems like such a waste of a great OS. Hey, maybe you'll enjoy figuring out how to script this, stick with it and become a contributor some day... who knows?

Not everybody has time to overcome challenges.
Not everybody wants to overcome challenges.
Not everybody has fun trying to overcome challenges/write scripts.
Not everybody uses GNU/Linux for fun. (and among those that do, they may have another idea of fun)

I have nothing against you suggesting using a script or command-line instead of using a GUI, but if you are experienced in writing such sed/awk/perl/python/etc scripts, the least you could do is write one and post it here.

This will save other users a lot of time and those who are interested in scripting might learn from this script.
Or did you learn scripting without looking at any examples?

If you know a command-line way to do it, it's the same. You post the command-line.

If you don't know how to write a corresponding script or don't have time to do so, instead of just saying "use awk", "use perl", you could at least have linked to good tutorials for them if you want to help him learn them. (unless you really had no time at all...)

I spend a lot of time playing around with scripts, more than I should, because I enjoy it.
But I can perfectly understand others prefering a GUI or a copy/pasted script. Because some people have other things to do!

> Hey, maybe you'll enjoy figuring out how to script this, stick with it and become a contributor some day... who knows?
Hey, maybe he'll rather enjoy contributing to documentation/art/music/translations/etc of Free Open-source projects.
Maybe he'll rather enjoy contributing to science.

Not everybody is a computer geek.
And even computer geeks are sometimes happy to have GUIs to get certain tasks done faster:
IDE, RAD tools, graphical browsers?, etc
Most terminals are GUIs too, unless you don't use any X server at all...

And Ubuntu is a distro meant for "human beings" (all of them and therefore meant to be usable without scripting/programming knowledge). It isn't gentoo, slackware, Linux from scratch or other similar distros.

Additionally, this is the "Absolute beginner" section, not the "Programmer section".

edit: Sorry for the rant, but I got carried away a bit.
In walkingthecow's defense, I must say he did give some more help on the scripting part. ;)

---


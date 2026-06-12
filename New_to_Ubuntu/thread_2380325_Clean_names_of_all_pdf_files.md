---
title: "Clean names of all pdf files"
date: 2017-12-15
forum: New to Ubuntu
---

### Post by sed_faster on 2017-12-15
Hello folks,

I intend remove all accents, spaces and weird things of the names of all pdf files I have on a server.

I need to guarantee two things:

1-all spaces, accents and weird things are remove and all spaces are replaced by underline (also_like_this);
2-That doesn't make a mistake and delete some files pdf;

I created several scripts, each with a different method:
```

for i in *.pdf
do
    j=`echo "$i" | sed 'y/áÁàÀãÃâÂéÉêÊíÍóÓõÕôÔúÚçÇ/aAaAaAaAeEeEiIoOoOoOuUcC/'`
    mv "$i" "$j"
done

```

```

for i in *.pdf
do
    j=`echo "$i" | sed 's/[^A-Za-z0-9_.]//g'`
    mv "$i" "$j"
done

```

```

text_to_ascii(){
    echo "$(iconv -t  "ASCII//IGNORE" <<< "$1")"
} #//end text_to_asci()

for filename in ./*
do
    clean_filename="$(text_to_ascii "$filename")"
    mv -iv "$filename" "$clean_filename"
done

rename -v 'y/ /_/' *.*

```

Which of this script do you think it is better?
Thanks

---

### Post by vasa1 on 2017-12-15
What about the possibility that two or more initially different filenames are converted to the same one? In such a case, only the last one will survive. For example, see point #4 in this comment: [https://unix.stackexchange.com/questions/6460/bulk-rename-or-correctly-display-files-with-special-characters?rq=1#comment497996_285827](https://unix.stackexchange.com/questions/6460/bulk-rename-or-correctly-display-files-with-special-characters?rq=1#comment497996_285827)

---

### Post by vasa1 on 2017-12-15
Did you look at detox? The online man page is here: [http://manpages.ubuntu.com/manpages/xenial/en/man1/detox.1.html](http://manpages.ubuntu.com/manpages/xenial/en/man1/detox.1.html)

Of note is:```
BUGS

     [B]If, after the translation of a filename is finished, a file already
     exists with that same name, detox will not rename the file[/B].  This could
     cause a problem with the max_length filter, if it was imperative that the
     files be cut down to a certain length.

     Long options don't work under Solaris or Darwin.

     An error in the config file will cause a segfault as it's going to print
     the offending word within the config file.

```

---

### Post by sed_faster on 2017-12-16
Hello,

I didn't know the program Detox. I intend install this program on the server without connection with internet. On my system, lubuntu, I install detox program, from apt-get. I copy the archive present on (cp -r /var/cache/apt/archives/detox_1.2.0-6_amd64.deb /home/xxx/Desktop/).

What do you suggest? Install on my server from this archive .deb or install from this version present in this website? [https://sourceforge.net/projects/detox/files/detox/](https://sourceforge.net/projects/detox/files/detox/) From file .tar.bz2?

---

### Post by Holger_Gehrke on 2017-12-16
That .tar.bz file on sourceforge is source code. Unless you've got make, a compiler and the necessary header files on your server it won't do you much good. The .deb file from your cache is probably a better bet, as long as your server has the same version number of Ubuntu and the same processor architecture as your desktop.

Holger

---

### Post by sed_faster on 2017-12-16
I download detox version to I386 (32bits) from this link: [https://launchpad.net/ubuntu/xenial/i386/detox/1.2.0-6](https://launchpad.net/ubuntu/xenial/i386/detox/1.2.0-6)
Installed on ubuntu server and works very well.

I was test some commands on server, before run finally command over all my server, and I can't execute detox command over subdirectories. I use this command:
```

$ detox -r -v /sd/ret/test_pdf/*.pdf # the files pdf inside /test_pdf/folder weren't reached by this command

```

Maybe this happen because I choose only *.pdf on first directory, test_pdf, and this limits subsequent folders. Right?
Thanks

---

### Post by Holger_Gehrke on 2017-12-17
> **Edgar_Oliveira said:**
> Maybe this happen because I choose only *.pdf on first directory, test_pdf, and this limits subsequent folders. Right?


Exactly. It would recurse into subdirectories with names ending in '.pdf', but you probably don't have any like that ...
I'd probably use a find xargs combo like so:
```
find . -iname '*pdf' -print0|xargs -0 detox -v
```The '-print0' and '-0' options of find and xargs are meant to be used together (those are number zero, not capital o). find with '-print0' prints a list of found files separated by NULL characters and xargs with the option '-0' expects a list like that and can handle filenames that contain all kinds of unusual characters including space and newline.

Holger

---


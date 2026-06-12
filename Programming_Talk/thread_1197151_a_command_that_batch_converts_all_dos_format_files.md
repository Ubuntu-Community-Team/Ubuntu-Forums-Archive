---
title: "a command that batch converts all dos format files to unix format files... ..."
date: 2009-06-25
forum: Programming Talk
---

### Post by zpzpzp on 2009-06-25
Hi

Could anyone provide a command or a shell script that batch converts all dos format files to unix format files (i.e. get rid of the ^M character) for ALL files in the same directory?

I searched online and found this one:
find . -type f -exec dos2unix {} \;
but it prints the unix version of every line of each file to the screen, instead of converting the file itself.

Thanks a lot.

Tom

---

### Post by lisati on 2009-06-25
I'm sure that others can come up with a better idea, but here is a link to one of my efforts: [http://ubuntuforums.org/showpost.php?p=7435161&postcount=5](http://ubuntuforums.org/showpost.php?p=7435161&postcount=5)

---

### Post by ad_267 on 2009-06-25
Hmm the default behaviour of dos2unix should be to overwrite the file. Have a look at "man dos2unix". You might need to add the -o option to overwrite the original file.

The command you posted worked for me. What version of Ubuntu do you have and how did you install dos2unix? From the tofrodos package?

---

### Post by zpzpzp on 2009-06-25
> **lisati said:**
> I'm sure that others can come up with a better idea, but here is a link to one of my efforts: [http://ubuntuforums.org/showpost.php?p=7435161&postcount=5](http://ubuntuforums.org/showpost.php?p=7435161&postcount=5)

Thanks but I am looking for a command or script that does the conversion to all files in the same directory...

---

### Post by zpzpzp on 2009-06-25
> **ad_267 said:**
> Hmm the default behaviour of dos2unix should be to overwrite the file. Have a look at "man dos2unix". You might need to add the -o option to overwrite the original file.

The command you posted worked for me. What version of Ubuntu do you have and how did you install dos2unix? From the tofrodos package?


Thanks for your reply ad_267 but nope... I am actually using KDE, dos2unix requires old and new file names, and does not have a -0 option...

---

### Post by ad_267 on 2009-06-25
> **zpzpzp said:**
> Thanks for your reply ad_267 but nope... I am actually using KDE, dos2unix requires old and new file names, and does not have a -0 option...

Your desktop enviroment has nothing to do with command line tools like dos2unix, if you are using Kubuntu it will have come from the same repository as Ubuntu with Gnome. The option is a small o for overwrite, not a zero. Have a look at the man page to see what options you can use, ie "man dos2unix".

Also, I should mention that using find will also convert files in subdirectories. If you only want to convert files in the current directory you can use "dos2unix *".

---

### Post by zpzpzp on 2009-06-25
Sorry this is actually a remote Sun 5.8 machine...

But the man page looks like follows, there is no -o option...


NAME
     dos2unix - convert text file from DOS format to ISO format

SYNOPSIS
     dos2unix [ -ascii ]  [ -iso ]  [ -7 ]  originalfile  conver-
     tedfile

DESCRIPTION
...

OPTIONS
     -ascii
           Removes extra carriage returns  and  converts  end  of
           file   characters  in DOS format text files to conform
           to SunOS requirements.

     -iso  This is the default.  It converts  characters  in  the
           DOS  extended  character set to the corresponding  ISO
           standard characters.

     -7    Convert 8 bit DOS graphics characters to 7  bit  space
           characters so that  SunOS can read the file.

---

### Post by ad_267 on 2009-06-25
Well that explains a lot, the Unix tools are often quite different than the Gnu ones used in Linux.

You can just set the output file name to be the same as the input file and it will overwrite it:
find . -type f -exec dos2unix {} {} \;

---

### Post by zpzpzp on 2009-06-25
Worked!

Thanks a lot ad_267!

Tom

---


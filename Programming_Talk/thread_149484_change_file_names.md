---
title: "change file names"
date: 2006-03-24
forum: Programming Talk
---

### Post by chocolatetoothpaste on 2006-03-24
Here is a simple quesion.  I have a script for importing pics from my digital camera.  When I download pics, it creates a folder with the date on it, and it copies the pictures from my camera.  If you download twice in one day, the first set of pics will be overwritten.  To avoid this, here is my question:
How can I modify the file names, as they are imported?  What I want to do is this:
the pics are in the format:
DSCF0001.jpg
DSCF0002.jpg
etc.
I want to drop the extension, add one to the last picture from the previous import, then convert the extension to lowercase.  It is in uppercase on the cam, but I want it lower case for convenience.  The whole filename could be lowercase I guess.

IE
in the morning, I import DSCF0001.jpg - DSCF0016.jpg.  I delete my card and my camera starts back at DSCF0001.jpg.  But when I import I want it to copy the files as DSCF0017.jpg - whatever.   Anyone have some ideas?

---

### Post by gerbman on 2006-03-24
Hi,

I was bored and it sounded like potentially useful thing, so I wrote a perl script (attached) to do what you wanted. Usage: ```
./xfer.pl /path/to/camera/directory /path/to/base/picture/directory
```The base directory is where today's picture folder should be created if this is the first transfer today. For example, it would be /home/gerb/pics on my machine. If the script has been run today then it copies pics into today's directory with renumbered file names. 

DISCLAIMER:  I tested the script and it seems to work, but assume that it doesn't. I'm not responsible for the loss of any spectacular pics ;-) Use it on some junk pics first and make sure it transfers those correctly.

EDIT: Guess it doesn't like executable attachments...here's the script:
```
#!/usr/bin/perl -w

use strict;
my($cam_folder,$base_dir,$to_folder,$largest,$prefix,$new_name,$day,$month,$year);

($cam_folder, $base_dir)=@ARGV;

($day, $month, $year) = (localtime)[3,4,5];
$year += 1900;
$to_folder = "$base_dir/$day-$month-$year";
mkdir($to_folder);

system("ls $to_folder > ./tmp_files");
open(FILES,"tmp_files");
$largest = 0;
$prefix = "";
while(<FILES>)
{
    $_ =~ m/(.*)(\d+)\.(.*)/;
    if( $2 > $largest )
    {
        $largest = $2;
        $prefix = $1;
    }
}
close(FILES);

system("ls $cam_folder > ./tmp_files");
open(FILES,"tmp_files");
while(<FILES>)
{
    chomp($_);
    ++$largest;
    $_ =~ m/(.*)(\d+)\.(.*)/;
    $new_name = $1 . $largest . "." . lc($3);
    system("mv $cam_folder/$_ $to_folder/$new_name");
}
close(FILES);
system("rm ./tmp_files");
```

---

### Post by chocolatetoothpaste on 2006-03-24
Thank you for your script.  I will try it out.  I guess I should have mentioned, the script I have is a shell script, so I would like to tie everything into that one if I can.  How would your code translate to bash?

---

### Post by gerbman on 2006-03-24
[QUOTE=chocolatetoothpaste]Thank you for your script.  I will try it out.  I guess I should have mentioned, the script I have is a shell script, so I would like to tie everything into that one if I can.  How would your code translate to bash?[/QUOTE]

Yeah, I assumed yours was a shell script, and I looked for an easy way to do it in Bash but I'm a total noob at that. You could call my script from yours if you wanted to, but as for doing the whole thing in Bash I have no clue :-k 

Good luck.

---

### Post by chocolatetoothpaste on 2006-03-24
for anyone interested here is the code that others have helped me write.  Thanks gerbman for your perl script.  I will keep working at it until I come up with something
```

#!/bin/sh

picdir=`date +%m-%d-%y`
usage="Options: [-c camera name] [-d delete source pictures]"

while getopts ":c:d" options; do
  case $options in
    c ) newcam=$OPTARG;;
    d ) delsrc=$OPTIND;;
    h ) echo $usage;;
    \? ) echo $usage

         exit 1;;
    * ) echo $usage
          exit 1;;
  esac
done

if [ $newcam ]; then
camdir=$newcam
else
camdir='fuji-a303'
fi

mkdir -p "$camdir"
mkdir -p ~/"$camdir/$picdir"
cp -r /media/usbdisk/DCIM/100_FUJI/* ~/"$camdir/$picdir"

if [ $delsrc ]; then
rm /media/usbdisk/DCIM/100_FUJI/*
fi

```
I mean not to criticize, but that perl script just looks really complicated.  Especially when you don't know it.  Part of the reason I like the code I have is it takes a couple args, or if none are passed it just defuats. Can perl take agrs from the command line?  like script.pl -c kodak2300 -d    <- can it do that?
Perl is on my todo list, but getting this pic transfer thing working is ahead of it unfortunately.

---

### Post by gerbman on 2006-03-24
> I mean not to criticize, but that perl script just looks really complicated. Especially when you don't know it.
Perl is kinda ugly in some ways, I agree, but learn a little and it becomes elegant.

> Can perl take agrs from the command line? like script.pl -c kodak2300 -d <- can it do that?
The script I wrote takes two arguments from the command line, the camera directory and your pics directory (see my first post if you haven't yet). It'd be very simple to add default directories.

> Perl is on my todo list, but getting this pic transfer thing working is ahead of it unfortunately.
I would totally encourage you to take it up :-)

Cheers!

---


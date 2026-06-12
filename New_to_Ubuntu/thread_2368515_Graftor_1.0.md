---
title: "Graftor 1.0"
date: 2017-08-11
forum: New to Ubuntu
---

### Post by sed_faster on 2017-08-11
Hello folks,

Anyone know this software: [http://www.naskita.com/linux/graftor/graftor.shtml](http://www.naskita.com/linux/graftor/graftor.shtml)
On this page I found this script ([http://www.naskita.com/linux/graftor/graftor-download.shtml):](http://www.naskita.com/linux/graftor/graftor-download.shtml):)

```

#!/bin/sh

usage()
{
    echo "USAGE : graftor.install [-h] [-b gftbase] [-w wishxdir]"
    echo
    echo -e "\t-h :\tGive a short explanation of the options"
    echo
    echo -e "\t-b gftbase :\tGftbase will be the base directory where to install Graftor."
    echo -e "\t\t\tA sub-directory gftbase/graftor$ver will be created." 
    echo -e "\t\t\tAll the files will be copied in gftbase/graftor$ver"
    echo -e "\t\t\tThe Graftor program itself will be gftbase/graftor$ver/bin/graftor"
    echo -e "\t\t\tFor example, if you type :"
    echo -e "\t\t\tgraftor.install -b /var"
    echo -e "\t\t\tthe script will :"
    echo -e "\t\t\t\t- create /var/graftor$ver" 
    echo -e "\t\t\t\t- install Graftor in /var/graftor$ver"
    echo -e "\t\t\tgftbase defaults to /usr/local"
    echo
    echo -e "\t-w wishxdir :\tUsed to indicate the absolute path for wishx."
    echo -e "\t\t\twishxdir defaults to /usr/bin"

    exit 0
}


x=$#

dir=/usr/bin/wishx
gftbase=/usr/local
ver=1.0

clear

echo
echo "************************************"
echo "Graftor Version $ver"
echo "by Marie Caroline Pavoine"
echo "November 23, 2000"
echo "************************************"
echo


while [ $x -gt 0 ];
do
case $1 in
    -h)    usage
        ;;
    -b)    if [ $x -gt 1 ];
        then
            gftbase=$2
            shift
            shift
        else
            usage
        fi
        ;;
    -w)    if [ $x -gt 1 ];
        then
            dir=$2
            shift
            shift
        else
            usage
        fi
        ;;
    *)    usage
        ;;
esac
x=$#
done
    

if [ ! -e $gftbase ];
then
    mkdir -p $gftbase
fi

if [ ! -w $gftbase ];
then
    echo "Unable to write into $gftbase"
    echo "Try to install Graftor in another directory or install it as root"
    exit 1
fi



echo Copying components in $gftbase/graftor$ver...

if [ ! -x $dir ];
then
    echo "$dir is not a valid wishx program"
    exit 1
fi


current=`dirname $0`
cur=`pwd`



mkdir $gftbase/graftor$ver
cp $current/graftor.install $current/README $current/LICENSE $gftbase/graftor$ver
mkdir $gftbase/graftor$ver/bin
cp $current/bin/* $gftbase/graftor$ver/bin
mkdir $gftbase/graftor$ver/bitmaps $gftbase/graftor$ver/lib 
cp $current/bitmaps/* $gftbase/graftor$ver/bitmaps
cp $current/lib/* $gftbase/graftor$ver/lib

cd $gftbase/graftor$ver/bin
awk -v aa=$dir -v bb=$gftbase/graftor$ver/bin -v cc=$gftbase/graftor$ver/bitmaps -v dd=$gftbase/graftor$ver/lib 'NR==1{$0="";printf("#!%s",aa);print}NR==3{$0="";printf("set BINPATH %s",bb);print}NR==4{$0="";printf("set BITPATH %s",cc);print}NR==5{$0="";printf("set LIBPATH %s",dd);print}NR>5{print}' $gftbase/graftor$ver/bin/graftor >$gftbase/graftor$ver/bin/graftor.tmp

mv $gftbase/graftor$ver/bin/graftor.tmp $gftbase/graftor$ver/bin/graftor

chmod 755 $gftbase/graftor$ver/bin/graftor




cd $cur

echo "#!/bin/sh" >$gftbase/graftor$ver/graftor.uninstall
echo "rm -ri $gftbase/graftor$ver" >>$gftbase/graftor$ver/graftor.uninstall
chmod 755 $gftbase/graftor$ver/graftor.uninstall

echo "Installation completed"
echo "Graftor is located at $gftbase/graftor$ver/bin/graftor"

```

How can I know if this is a secure installation?
I tried found this soft through terminal:
```

sudo apt-cache search graftor

```
but I didn't found anything.
Thanks

---

### Post by vocx on 2017-08-11
> **Edgar_Oliveira said:**
> Hello folks,

Anyone know this software: [http://www.naskita.com/linux/graftor/graftor.shtml](http://www.naskita.com/linux/graftor/graftor.shtml)
On this page I found this script ([http://www.naskita.com/linux/graftor/graftor-download.shtml):](http://www.naskita.com/linux/graftor/graftor-download.shtml):)

How can I know if this is **a secure installation?**
I tried found this soft through terminal:
```

sudo apt-cache search graftor

```
but **I didn't found anything.**
Thanks
Not every program in existence is in the Ubuntu repositories. The developers themselves or somebody that uses the program needs to make an effort to package it into a distributable .deb package. Then it can be added to the repositories after following the Debian and Ubuntu procedures.

However, programs that are too old, or not widely known, or that don't have a strong community of users around them probably will never be packaged.

So, there is no way for you to know if this is a secure installation or not. You basically have to trust the author that he or she has done everything in good faith.

---

### Post by sed_faster on 2017-08-11
I understand!
I am trying install on Lubuntu 16.04 and when I was execute this script I receive this error:

```

/usr/bin/wishx is not a valid wishx program

```

Do you know what problem can I have?
Thanks
[B]
[UPDATE][/B]
One more time I don't found this program on central software: sudo apt-cache search wishx

---

### Post by #&amp;thj^% on 2017-08-11
> **Edgar_Oliveira said:**
> Hello folks,

Anyone know this software: [http://www.naskita.com/linux/graftor/graftor.shtml](http://www.naskita.com/linux/graftor/graftor.shtml)
On this page I found this script ([http://www.naskita.com/linux/graftor/graftor-download.shtml):](http://www.naskita.com/linux/graftor/graftor-download.shtml):)



How can I know if this is a secure installation?
I tried found this soft through terminal:
```

sudo apt-cache search graftor

```
but I didn't found anything.
Thanks
Never heard of it myself,  And it quite old as shown here>>"Graftor Version 1.0
by Marie Caroline Pavoine
November 23, 2000"
But a few checks with scanners
First Check installer : [https://www.virustotal.com/#/file/270144e1a6af2b76f6b3f46b40d66d566adba4f32cdd3620c81914c6c57a1a5b/detection](https://www.virustotal.com/#/file/270144e1a6af2b76f6b3f46b40d66d566adba4f32cdd3620c81914c6c57a1a5b/detection)
Second Check on bin: [https://www.virustotal.com/#/file/40b1a0b74897e51ea003410167679e785fb08ba64ee5cfd87338ee7ad24df86b/detection:](https://www.virustotal.com/#/file/40b1a0b74897e51ea003410167679e785fb08ba64ee5cfd87338ee7ad24df86b/detection:)
You do have Uninstall instructions provided if needed. (One of the first things I look for)


```
cd $cur

echo "#!/bin/sh" >$gftbase/graftor$ver/graftor.uninstall
echo "rm -ri $gftbase/graftor$ver" >>$gftbase/graftor$ver/graftor.uninstall
chmod 755 $gftbase/graftor$ver/graftor.uninstall
```
But like vocx states you are putting your trust in their hands. (System Breakage)

---

### Post by vocx on 2017-08-11
> **Edgar_Oliveira said:**
> I understand!
I am trying install on Lubuntu 16.04 and when I was execute this script I receive this error:

```

/usr/bin/wishx is not a valid wishx program

```

Do you know what problem can I have?
Thanks
[B]
[UPDATE][/B]
One more time I don't found this program on central software: sudo apt-cache search wishx
The program that you are trying to install seems to be very old, from the year 2000.

It is possible that at the time there was a program called "wishx", but maybe this program doesn't exist anymore. In other words, the Graftor program that you try to install may be obsolete, or depend on other obsolete programs.

This is just a guess, the program "wishx" may actually be the one now simply called "wish", which comes with the Tcl/Tk programming language.

You need to go to the installer file, and change this line
```

dir=/usr/bin/wishx

```
to
```

dir=/usr/bin/wish

```

Will that work? Maybe. Maybe not.

---

### Post by sed_faster on 2017-08-12
Hooo, I do not know this webstie.
This means the graftor software has not virus? Or at least do not identify which virus?

[Https://snag.gy/KlNeO3.jpg](Https://snag.gy/KlNeO3.jpg)

How should I use this website to scan virus to software "graftor", for example. If I put graftor on textbox and play scan I will receive this webpage: [https://www.virustotal.com/#/search/graftor](https://www.virustotal.com/#/search/graftor)


Thanks

---

### Post by #&amp;thj^% on 2017-08-12
Two different  "graftor" names here>>>Graftor for your use is not the malware mentioned by your link. ;)
On that page [https://www.virustotal.com](https://www.virustotal.com) just upload the file/folder you wished scanned.
I uploaded the installer/file/script and the bin file for scanning in my post above.
Again your putting your faith in their results. (But pay attention to names claiming the results, are they credible?)

---


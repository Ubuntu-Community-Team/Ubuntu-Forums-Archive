---
title: "Bash Script help"
date: 2013-04-04
forum: Programming Talk
---

### Post by lanmonster on 2013-04-04
Sorry for the ambiguous title, it was the best I could come up with.
I am trying to make script that will sync the source of an android ROM and build it.
I have the base of the script down and all of the instructions to sync source and build.
Here is the code I have now:
```
#!/bin/bashclear
mkdir ~/RomBuilder
cd ~/RomBuilder
mkdir AOKP
mkdir CM
mkdir BAMF
clear
echo
echo
echo
echo
echo
echo
echo
echo
echo -e "\t\t*******************************************"
echo -e "\t\t*      Hello, welcome to ROM Builder!     *"
echo -e "\t\t* Choose the ROM you would like to build  *"
echo -e "\t\t*******************************************"
echo -e "\t\t*       Developed by: Lanmonster          *"
echo -e "\t\t*******************************************"
echo -e "\t\t*   Follow me on Twitter @Lanmonster14    *"
echo -e "\t\t*******************************************"
read -p "Press [Enter]"
clear
echo
echo
echo
echo
echo
echo
echo
echo
echo -e "\t\t*******************************************"
echo -e "\t\t*            Supported ROMs               *"
echo -e "\t\t*******************************************"
echo -e "\t\t*1. Android Open Kang Project             *"
echo -e "\t\t*******************************************"
echo -e "\t\t*2. CyanogenMod                           *"
echo -e "\t\t*******************************************"
echo -e "\t\t*3. BAMF Paradigm                         *"
echo -e "\t\t*******************************************"
```

I need help getting the input from the user and I need help getting the text centered.

[AOKP build instructions]("http://rootzwiki.com/topic/31166-tutorial-so-you-want-to-build-aokp-jb-ubuntu-1204/")

[CM build instructions]("http://forum.xda-developers.com/showthread.php?t=2047981")
[URL="http://www.teambamf.net/topic/4253-how-to-building-paradigm-from-source/"]
BAMF build instructions[/URL]

---

### Post by r-senior on 2013-04-04
In Bash, you can use "select" to create simple menus:

```
#!/bin/bash

echo "Choose build (Ctrl-D to quit)"
select choice in "Android Open Kang" "CyanogenMod" "BAMF Paradigm"
do
    case $choice in
    "Android Open Kang")
        rom=aokp
        break
        ;;
    "CyanogenMod")
        rom=cm
        break
        ;;
    "BAMF Paradigm")
        rom=bamf
        break
        ;;
    *)
        echo 'Invalid choice'
        ;;
    esac
done

if [ $rom ]
then
    echo "Do the processing for $rom ..."
fi

```

Refer to the bash manual page for more details on select. The above is for illustration only.

I'd drop the banner and forget the centering idea. GNU command line tools tend not to announce themselves (unless a --help or --version option is used) and any output tends to be simple and left-justified. If you want to add command line options, refer to the section on "getopts" in the manual.

---

### Post by schragge on 2013-04-04
To center lines, you can try this
```

#!/bin/bash
: ${COLUMNS:=`tput cols`}
string='Hello world!'
((pwidth=(COLUMNS-${#string})/2))
printf "%${pwidth}s%-.${COLUMNS}s\n" '' "$string"

```
If you want to pad with something other than space, change the code above to
```

#!/bin/bash
: ${COLUMNS:=`tput cols`}
string='Hello world!'
printf -vpadding %$(( (COLUMNS-${#string})/2 ))s
padding=${padding// /*}
echo "$padding${string::$COLUMNS}$padding"

```
If you need to center lines being read from a file, see [this example]("http://www.gnu.org/software/sed/manual/html_node/Centering-lines.html") in the GNU sed documentation. To understand the idea, try
```
echo test%%%%%%%%%%%%%|sed -r 's/(\w+)%(.*)\2/\2\1\2/'
```

---

### Post by lanmonster on 2013-04-04
Thanks for your help!

---

### Post by lanmonster on 2013-04-05
> **r-senior said:**
>  *snip* 

In the aokp build instructions, there is a set of commands that only need to be done once. How do I get the script to know whether or not those commands have been run yet? Like the first time it would do all the mkdir's and whatnot but after that, it is unnecessary.

---

### Post by schragge on 2013-04-05
Something like
```

if ! test -f AOKP_build_stamp
then
# configure and build AOKP
touch AOKP_build_stamp
fi

```

---

### Post by lanmonster on 2013-04-08
> **schragge said:**
> Something like
```

if ! test -f AOKP_build_stamp
then
# configure and build AOKP
touch AOKP_build_stamp
fi

```
would you mind explaining what is going on in the code for learning purposes?

---

### Post by CharlesA on 2013-04-08
> **lanmonster said:**
> would you mind explaining what is going on in the code for learning purposes?

It is testing to see if AOKP_build_stamp exists and is a file. If it does not exist it creates it.

See here: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)

---


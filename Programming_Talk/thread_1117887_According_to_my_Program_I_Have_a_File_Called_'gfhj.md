---
title: "According to my Program I Have a File Called 'gfhjrhdg' - Help!"
date: 2009-04-06
forum: Programming Talk
---

### Post by Penguin Guy on 2009-04-06
**Solved**
> **Penguin Guy said:**
> Here is the fixed code if anybody wants it (click on the square above)

**This is my program:** /home/share/bin/sys_info
```
#!/bin/bash
# A script to produce an HTML file containing system information





##### Constants
PROGNAME="Sys_Info"
TITLE="System Information - $HOSTNAME"
FOOTER="Compiled on $(date +"%x") by $USER"
filename="System_Information"
overwright=
interactive=





##### Functions
function display_help
{
 echo "Usage: $PROGNAME [[[[-f file ] [-o]] [-i]] | [-h]]"
 echo "Compile a HTML file containing system information"
 echo ""
 echo "Short   Long            Description"
 echo "-f      --file          Specify a filename for output"
 echo "-o      --overwright    Overwright any existing file without warning"
 echo "-i      --interactive   Activates interactive mode."
 echo "-h      --help          Shows this help list"
}

function basic_info
{
 echo "<h2>Basic System Imformation (uname)</h2>"
 echo "<pre>"
 uname
 echo "</pre>"
}

function show_uptime
{
 echo "<h2>System Uptime (uptime)</h2>"
 echo "<pre>"
 uptime
 echo "</pre>"
}

function drive_space
{
 echo "<h2>Filesystem Space (df)</h2>"
 echo "<pre>"
 df
 echo "</pre>"
}

function main
{
cat <<- _EOF_
<HTML>
 <HEAD>
  <TITLE>$TITLE</TITLE>
 </HEAD>

 <BODY>
  <H1>$TITLE</H1>
  $(basic_info)
  $(show_uptime)
  $(drive_space)
  <P>$FOOTER</P>
 </BODY>
</HTML>
_EOF_
}





##### Start
while [ "$1" != "" ]; do
 case $1 in
  -f | --file )            shift
                           filename=$1
                           ;;
  -o | --overwright )      shift
                           overwright=1
                           ;;
  -i | --interactive )     interactive=1
                           ;;
  -h | --help )            display_help
                           exit
                           ;;
  * )                      usage
                           exit 1
  esac
 shift
done

if [ "$interactive" = "1" ]; then
 
 response=

 echo -n "Enter name of output file (default $filename) > "
 read response
 if [ -n "$response" ]; then
  filename=$response
 else
  echo "Use $filename as output file? (y/n)"
  read response
  if [ "$response" != "y" ]; then
   echo "Exiting program."
   exit 1
  fi
 fi
fi

if [ -f "$filename" ] & [ "$overwright" != "1" ]; then
 echo -n "Output file exists. Overwrite? (y/n) > "
 read response
 if [ "$response" != "y" ]; then
  echo "Exiting program."
  exit 1
 fi
fi

main > $filename

exit 0





##### Info
# Based off:
# http://linuxcommand.org/writing_shell_scripts.php
```


**This is my output:**
```
~$ sys_info -f "gfhjrhdg"
Output file exists. Overwrite? (y/n) > n
Exiting program.
```
```
~$ sys_info -f "ghardk"
Output file exists. Overwrite? (y/n) > n
Exiting program.
```


**This is my home directory:**
```
~$ ls
bin        Music              Pictures       System_Information   Videos
Desktop    My Music           Program Files  System_Information~
Documents  Optical Illusions  Programming    The Rofl Folder
```


**This shows that my '/home/share/bin' directory is listed in PATH:**
```
~$ echo $PATH
/home/josh/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/share/bin
```


Can anyone tell me what broke? - Thanks.

---

### Post by dwhitney67 on 2009-04-06
Try this:
```

if [ -f "$filename" ] && [ "$overwright" != "1" ]; then

```
Note the double-ampersand.

Also note that the correct spelling for 'overwright' is 'overwrite'.

---

### Post by Penguin Guy on 2009-04-06
> **dwhitney67 said:**
> Try this:
```

if [ -f "$filename" ] && [ "$overwright" != "1" ]; then

```
Note the double-ampersand.

Also note that the correct spelling for 'overwright' is 'overwrite'

I used a single ampersand because of this:
> There is a simpler way of writing if statements: The && and || commands give code to run if the result is true.
Clearly I misunderstood.
It works fine now: Thanks! 

```
~$ sys_info -f "gfhjrhdg"
~$ 
```

---

### Post by Penguin Guy on 2009-04-06
Here is the fixed code if anybody wants it:
```
#!/bin/bash
# A script to produce an HTML file containing system information





##### Constants #####
PROGNAME="Sys_Info"
TITLE="System Information - $HOSTNAME"
FOOTER="Compiled on $(date +"%x") by $USER"
filename="System_Information"
overwrite=
interactive=





##### Functions #####
function display_help
{
 echo "Usage: $PROGNAME [[[[-f file ] [-o]] [-i]] | [-h]]"
 echo "Compile a HTML file containing system information"
 echo ""
 echo "Short   Long            Description"
 echo "-f      --file          Specify a filename for output"
 echo "-o      --overwrite     Overwrite any existing file without warning"
 echo "-i      --interactive   Activates interactive mode."
 echo "-h      --help          Shows this help list"
}

function basic_info
{
 echo "<h2>Basic System Imformation (uname)</h2>"
 echo "<pre>"
 uname
 echo "</pre>"
}

function show_uptime
{
 echo "<h2>System Uptime (uptime)</h2>"
 echo "<pre>"
 uptime
 echo "</pre>"
}

function drive_space
{
 echo "<h2>Filesystem Space (df)</h2>"
 echo "<pre>"
 df
 echo "</pre>"
}

function main
{
cat <<- _EOF_
<HTML>
 <HEAD>
  <TITLE>$TITLE</TITLE>
 </HEAD>

 <BODY>
  <H1>$TITLE</H1>
  $(basic_info)
  $(show_uptime)
  $(drive_space)
  <P>$FOOTER</P>
 </BODY>
</HTML>
_EOF_
}





##### Start #####
while [ "$1" != "" ]; do
 case $1 in
  -f | --file )            shift
                           filename=$1
                           ;;
  -o | --overwrite )       shift
                           overwrite=1
                           ;;
  -i | --interactive )     interactive=1
                           ;;
  -h | --help )            display_help
                           exit
                           ;;
  * )                      usage
                           exit 1
  esac
 shift
done

if [ "$interactive" = "1" ]; then
 
 response=

 echo -n "Enter name of output file (default $filename) > "
 read response
 if [ -n "$response" ]; then
  filename=$response
 else
  echo "Use $filename as output file? (y/n)"
  read response
  if [ "$response" != "y" ]; then
   echo "Exiting program."
   exit 1
  fi
 fi
fi

if [ -f "$filename" ] && [ "$overwrite" != "1" ]; then
 echo -n "Output file exists. Overwrite? (y/n) > "
 read response
 if [ "$response" != "y" ]; then
  echo "Exiting program."
  exit 1
 fi
fi

main > $filename
echo "$filename document created successfully!"

exit 0





##### Info
# Based off:
# [http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)
```

---


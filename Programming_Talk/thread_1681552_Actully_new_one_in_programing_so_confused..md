---
title: "Actully new one in programing so confused."
date: 2011-02-04
forum: Programming Talk
---

### Post by adeee on 2011-02-04
Actually totally new i am.so dont mind. :p

i create a folder [COLOR=Red]bin[/COLOR] in home directory. and then file create [COLOR=Red]my_script[/COLOR]
paste this script.
```

#!/bin/bash

# make_page - A script to produce an HTML file

echo "<HTML>"
echo "<HEAD>"
echo "  <TITLE>"
echo "  The title of your page"
echo "  </TITLE>"
echo "</HEAD>"
echo ""
echo "<BODY>"
echo "  Your page content goes here."
echo "</BODY>"
echo "</HTML>"


cat << _ADEEE_
<HTML>
<HEAD>
    <TITLE>
    The title of your page
    </TITLE>
</HEAD>

<BODY>
    Your page content goes here.
</BODY>
</HTML>
_ADEEE_
```

then i paste this command. 

```
make_page > page.html
```
Then it 
says
```
make_page: command not found
```
but page.html create in bin directory. 
and when i double click it there is no output.totally blank.

any idea. :mad:
please reply me as quick as possible if you dont mind because if i face start up problem then i cant learn more.:confused:

------------------------------------------------------------------------------------------
this is my mega thread so if i face any problem in programming then i ask here.admin dont mind. ):P

---

### Post by johnl on 2011-02-04
You need to either specify the exact path of the script (option 1), or add the directory to your PATH environmental variable (option 2)

For either one, you will need to make the script executable.

To make the script executable, navigate to the folder it is in, and type 'chmod +x ./make_page'


option 1 (from /home/yourname/bin)
```

$ ./make_page > page.html # this will work
$ /home/yourname/make_page > page.html # this will work
$ make_page > page.html # this will not 

```


option 2:

add the following to the end of your ~/.bashrc file and save it:
```
export PATH="$PATH:/home/yourname/bin"
```

open a new terminal or type 'source ~/.bashrc' in an existing terminal

now you can type 'make_page > page.html'

---

### Post by trent.josephsen on 2011-02-04
Make sure the script is marked executable (chmod +x make_page) and call it like this:
```
./make_page >page.html
```

---

### Post by Vaphell on 2011-02-04
doesn't ubuntu add ~/bin automatically to PATH variable?

~/.profile
```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

---

### Post by Some Penguin on 2011-02-04
Decide whether you want to call it my_script or make_page.

---

### Post by forrestcupp on 2011-02-04
> **Some Penguin said:**
> Decide whether you want to call it my_script or make_page.

+1. You said you named the file my_script. If that's the name of the file, then that's the name of the script. Just because you put make_page in the comments doesn't mean that's the script's name. You have to go by the file name.

Also, you need to chmod +x the file like trent.joshepsen said, only use the actual filename.

---


---
title: "Howto:  Set Konqueror or FireFox Native as default browser for Dreamweaver 8 (wine)"
date: 2007-05-04
forum: Outdated Tutorials &amp; Tips
---

### Post by lachild on 2007-05-04
It's hard to teach on old dog new tricks and I am no exception to that rule.  As such I needed to find a way to get Konqueror and FireFox set as my default browsers for Dreamweaver 8.  Sure you can install a windows copy of FireFox but what's the point?  You already have it installed on your desktop by default.  Why not use it instead?

The trick is this....  You cant run windows batch files in Wine, but I'll be damned if Bash scripts don't work.

This how-to assumes that you already have Dreamweaver 8 installed and running through Wine.  If you dont a great how-to can be found   [here]("http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/") (This howto also works in Festy Fawn)

Ok now that we got Dreamweaver installed and everything appears to be working there two keys that will not work by default.  The F12 and Cntl+F12 Keys.  To get these to work follow these step-by-step instructions.

1) Open up a terminal window
2) Change the directory to your (fake) windows directory.  This is usually located in ~/.wine/drive_c/
3) type in the following:
```
gedit firefox
```

4) Copy and Paste the following into your editor.
```

#!/bin/bash

#Set This to the Path of Your fake c drive.  
#Usually /home/YOURHOME/.wine/drive_c/  
#LEAVE OFF THE TRAILING SLASH
myPath='/home/YOURHOME/.wine/drive_c'

###########################################
###     Do Not Edit Below This line     ###
###########################################

#Get Query Data
a=$1 

#Bash doesn't handle the spaces in the directory well
#here we convert the spaces to something we can
#convert back later
a=${a// / ~space~ }

#Split String
b=$( echo $a | awk 'BEGIN{ FS="\\" } { for (i=1; i<NF+1; i++){ print $(i) "\n" } }' )

#Setup Array For Use With Bash
c=($b) # create an array from b

#Set Pattern to locate so we can convert spaces back into spaces
mySpace='~space~'

#Put the new Path back together again including the FULL path to windows
#And converted Spaces
for (( i = 1 ; i < ${#c[@]} ; i++ ))
  do
    myTemp=${c[$i]}
      if [ "$myTemp" = "$mySpace" ]
        then
          ((i=i + 1))
          myTemp=${c[$i]}
          newpath=$newpath" "$myTemp
	  continue
        else
          newpath=$newpath"/"$myTemp
      fi
  done

#Fix for Direct Editing and FTP connections
if [ -z "$newpath" ]
 then
     fixpath=$1
else
 fixpath=$myPath$newpath
fi

#Start FireFox with new path
firefox "$fixpath "

```

5) change the line at the beginning of your new script that reads
```

myPath='/home/YOURHOME/.wine/drive_c'

```

to the path of your windows directory leaving off he trailing slash.

6) Save and Exit.
7) Type the following into your termanal
```
chmod 755 firefox
```

8. Next open up Dreamweever.
9) Locate the "Preview in browser" icon and select "Edit Browser List"
10) Hit the plus sign to add a new browser
11) Hit the "Browse" button and point it to your new bash script
12) Check Primary or Secondary to active your shortcut keys (F12 and ctrl-F12)
13) Hit OK
14) Test it out.

That should get FireFox working. Now on to Konqueror

1) Open up a termal window and change to the directory you installed your firefox scipt.
2) type in 
```
 cp firefox konqueror
```
3) Followed by
```
gedit konqueror
```
4) next go to the last line in the script that reads
```

#Start FireFox with new path
firefox "$fixpath"

```

Change this line to:
```

#Start Konqueror with new path
kfmclient openProfile webbrowsing "$fixpath "

```

5) Save and Exit
6) type in 
```
chmod 755 konqueror
```

7) Next open up Dreamweever.
8. Locate the "Preview in browser" icon and select "Edit Browser List"
9) Hit the plus sign to add a new browser
10) Hit the "Browse" button and point it to your new bash script
11) Check Primary or Secondary to active your shortcut keys (F12 and ctrl-F12)
12) Hit OK
13) Test it out.

Enjoy!

Edit:  Changed code to work around a firefox bug found in Hardy.  See post below for explaination

---

### Post by NumPy on 2007-05-13
Very nice mod .. thank you.

---

### Post by adewale on 2007-05-29
thanks very much can you tell me how to set it for opera?

---

### Post by lachild on 2007-06-02
Well I dont use Opera, but all you should need to do is to change This line of the script
```
#Start FireFox with new path
firefox "$fixpath"
```

to

```

CommandToOpenOpera "$fixpath" 
```

---

### Post by canalegrande on 2007-09-20
Hi,
thanks a lot for this marvellous script!
I use dreamweaver mostly in connection with php/mysql server model. This is why I have my web directory in 
/var/www
So my path for firefox looks like this:
myPath='/'
pressing F12 works perfectly.
(use gutsy pre-release with LAMP server install, one of the reasons I got rid of XP/Vista, which is a pain, even with xampp)

---

### Post by justtech on 2007-10-22
sorry guys... for me it does pull up firefox and trys to load my .html file.  But the location of the file is all off.  It is looking for my file at /home/myusername/.wine/drive_c/media/sda5/Clients/clientsname/site/index.html instead of Z:\media\sda5\Clients\clientsname\site\index.html....  How can I get it to go straight to my file?

---

### Post by mdpalow on 2007-10-28
U da man LACHILD.

Thanks very much for this. 

Racking my brain on this. When will I learn to just come to the forum first...

---

### Post by lachild on 2007-11-19
> **justtech said:**
> sorry guys... for me it does pull up firefox and trys to load my .html file.  But the location of the file is all off.  It is looking for my file at /home/myusername/.wine/drive_c/media/sda5/Clients/clientsname/site/index.html instead of Z:\media\sda5\Clients\clientsname\site\index.html....  How can I get it to go straight to my file?

Sorry for the delay.  I didn't know there was a question sitting here, until just now.

To fix your problem change the line in the script that reads

```
myPath='/home/YOURHOME/.wine/drive_c'
```

myPath should equal what ever the absoute path to z: is...  So if I had Z: maped to /usr/local/www/mysite/ then myPath would now be set to this directory.

---

### Post by justtech on 2007-11-19
Just for future knowledge to anyone else that may have this problem.....

The fix for my problem was to make the code look like this:
```
myPath='/'
```

I had it set like stated above with no luck in getting it to work.  Thanks for your help and the wonderful script.

---

### Post by lemmor27 on 2008-02-17
hi,

i followed everything in this post for the firefox part.

but when i tried to press f12 i got an error "acces denied"

any help will be greatly appreciated.

thanks in advance

---

### Post by lachild on 2008-07-19
Hey Guys,

I just went through the instructions again as I just upgraded to Hardy.  I found one small bug (that took FOREVER to find).  It appears that if you add a period to the filepath firfox is opening it will fail to load.  For instance, the following does NOT work:

```
$!/bin/bash

##Set Path
a= "/home/myhome/.wine/drive_c/windows/profiles/myhome/somesite/index.html"

##Run Firefox
firefox "$a"
```


Oddly enough this next one DOES work.

```
$!/bin/bash

##Set Path
a= "/home/myhome/.wine/drive_c/windows/profiles/myhome/somesite/index.html"

##Run Firefox
firefox "$a "
```

It only happend when you set your path in the script to .wine which is where is should point (unless you've changed your save directory for the site).

I have edited the instructions to work around the issue and they should work now for Hardy.  

Hope this helps anyone still having problems.

---


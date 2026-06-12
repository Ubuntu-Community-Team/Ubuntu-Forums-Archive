---
title: "HOWTO: Get a &quot;new-mail&quot; notification with very small RAM use"
date: 2006-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Stefan_hb on 2006-04-14
(Please excuse my insufficient english, I´m not a native speaker.)

Maybe you don´t want to invest 50 MB of Ram -usage to an eye-candy mail-notification-applet, but still want to be informed about new mails arriving, then - this may be a good solution for you: 
This is a screenshot of how it looks like in the end, look at the top border of the screen with the writing "Du hast  neue Mail." (->"you have new mail.")
[http://img135.imageshack.us/my.php?image=bildschirmfoto2fb.jpg](http://img135.imageshack.us/my.php?image=bildschirmfoto2fb.jpg)

It will use about 3 Megs of Ram, this is how it´s done:
1. create the file .fetchmailrc in ~ with the following content, replace the terms in capitals:
```
poll SERVERNAME protocol PROTOKOL user USERNAME password PASSWORD is LOCAL_USERNAME
```
SERVERNAME: the name of your mail-server
PROTOKOL: the mail-protokol (probably POP3)
USERNAME: the username for your mail-server
PASSWORD: the password for your mail-server
LOCAL_USERNAME: your username on your machine
It should look like that afterwards:
```
mail.gmx.de protocol POP3 user 1367073 password secret13 is peter
```
2. to prevent others from reading your password inside this file, change it´s rights with
```
chmod 600 .fetchmailrc
```
in a terminal.
3. if you don´t already have "osd_cat" install it with "sudo apt-get install xosd-bin" (tiny application)
4 . Create this script named "Mailchecker.sh" in ~/bin 
```
#!/bin/bash

fetchmail -c

if [ "$?" -eq 0 ]
  then
    VARMAIL1=$(fetchmail -c); VARMAIL2=$(echo $VARMAIL1 | cut -c 0-2); echo "You have new mail ($VARMAIL2)" | osd_cat -c white -o 6 -i 680 -d 10
  else
    echo Nothing! | osd_cat -c grey -o 6 -i 680 -d 5
  fi 
sleep 600
sh /home/stefan/bin/MailChecker.sh&
exit
```
5. if you want "osd_cat" to display a nicer font, choose one you have on your system with "xfontsel", and add the option -f [fontname] to osd_cat, like this
```
osd_cat -c white -o 6 -i 680 -d 5 -f -microsoft-verdana-*-r-*-*-*-*-0-*-*-*-*-*
```

6. you can adjust the exact position of the message with the -o and -i switches

7. Do a ```
chmod +x ~/bin/MailChecker.sh
``` to make it executable

8. Go to "System/Settings/Sessions/Startapplications" (my version of Gnome is german, I don´t know the exact name of this in the english version), and add the script Mailchecker.sh to the list

--------
That was it, another good idea is to make a starter in the task bar to check on click, in case you are waiting for mail to arrive, with this starter you start a second script:
```
#!/bin/bash

fetchmail -c

if [ "$?" -eq 0 ]
  then
    VARMAIL1=$(fetchmail -c); VARMAIL2=$(echo $VARMAIL1 | cut -c 0-2); echo "You have new mail. ($VARMAIL2)" | osd_cat -c white -o 6 -i 680 -d 10 
  else
    echo Nothing! | osd_cat -c white -o 6 -i 680 -d 5 
  fi  

exit
```

---

### Post by Efwis on 2006-04-24
works great.
Is there anyway that you could set the first script up so that it checks the server automatically every few minutes?

---

### Post by girishv on 2007-05-10
Hi,

you can use conky. It will do many other things in addition to checking the mail. And, also, you can use the above script with conky and adjust the frequency of execution

Girish

---

### Post by edmondt on 2007-05-10
Good Stuff....I got mine working using lucida font, took me a while to find the real font name :P

*To make it look smoother, I used an outline color, you can find all the color names here:

[http://halflife.ukrpack.net/csfiles/help/colors.shtml](http://halflife.ukrpack.net/csfiles/help/colors.shtml)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32221&stc=1&d=1178807036[/IMG]

```

#!/bin/bash

fetchmail -c

if [ "$?" -eq 0 ]
  then
    VARMAIL1=$(fetchmail -c); VARMAIL2=$(echo $VARMAIL1 | cut -c 0-2); echo "You have new mail ($VARMAIL2)" | osd_cat -c dimgray -o 5 -O 1 -u gainsboro -i 980 -d 500 --font='-b&h-lucida-medium-r-normal-*-12-*-*-*-p-*-iso10646-1'

  else
    echo Nothing! | osd_cat -c dimgray -o 5 -O 1 -u gainsboro -i 980 -d 500 --font='-b&h-lucida-medium-r-normal-*-12-*-*-*-p-*-iso10646-1'
  fi 
sleep 600
sh /home/**<username>**/bin/MailChecker.sh&
exit

```


By the way, fetchmail is also needed: "sudo apt-get install fetchmail" 

And to get it working with gmail I entered the following in .fetchmailrc:

```

poll pop.gmail.com
proto POP3
port 995
user '**<username>**@gmail.com'
pass 'password'
ssl

```

---


---
title: "How would I do this in Windows XP and/or Vista?"
date: 2009-02-18
forum: Programming Talk
---

### Post by Nevon on 2009-02-18
I've made this bash script that logs onto a certain site, checks if I have any unread messages (among other things) and then prints the result. It's fairly well commented, and should be easy enough to understand. I use this in combination with Conky to constantly be able to see if I have any messages or unread forum posts, directly on my desktop.

Now, I'd like to be able to share this among the rest of the members of that forum (the ones not using Linux). So, does anyone have any idea how I could make this work/recreate this so that it would work in Windows? It's also quite important that it's easy to use. Having to install cygwin is not an option. What language should I use, and how would I go about doing it? How would I be able to show the result directly on the desktop in both XP and Vista. I guess it would be okay to have one version for XP and one for Vista, if necessary. 

Feel free to ask questions. 

```
#!/bin/bash
# Ungdomar.se script
#
# Detta script skriver ut hur många PM, Bloggkommentarer, gästboksinlägg, etc.
# som är olästa.
#-------------------------------------------------

# Write your username and password here. Needs to be urlencoded.
# http://lajm.eu/emil/dump/stringfunctions.php
MY_USERNAME=<username> #without <>
MY_PASSWORD=<password> #without <>
REFRESH_TIME=100 #allowed age for um.htm in seconds
TEMP_DIR=~/.umscript

# No editing beyond this point.
#-------------------------------------------------

#Checks to see if TEMP_DIR exists and is writable. 
dirCheck () 
{
    if [ ! -d "$TEMP_DIR" ]; then
        mkdir $TEMP_DIR
    fi
    if [ ! -w "$TEMP_DIR" ]; then
        echo "$TEMP_DIR is not writable. Run chmod a+w $TEMP_DIR as root."; exit 1;
    fi
}

fileDownloader()
{
        #Check if um.htm exists, and if it does check if
        # um.htm's timestamp is less than current timestamp - $REFRESH_TIME
        if [ ! -e "$TEMP_DIR/um.htm" ] || [ "$(date -r $TEMP_DIR +%s)" -lt "$(($(date +%s) - $REFRESH_TIME))" ]; then 
            wget --quiet --save-cookies cookiejar --keep-session-cookies --post-data $LOGIN_DATA --user-agent 'Firefox' -O um.htm http://ungdomar.se/index.php
        fi
}

# Extracts the number of unread posts/comments, appends empty strings and
# prints the result
getNumber ()
{
    case "$1" in
        pm)
            # Extract the number of PM:s
            PM_NUMBER=`cat um.htm | LANG=sv_SE.iso88591 sed -n 's/.*ol.st.*pm.*count..\([0-9]*\).*/\1/p'`
            echo "${PM_NUMBER:=0}"
        ;;
        blog)
            # Extract the number of blog comments
            BLOGG_NUMBER=`cat um.htm | LANG=sv_SE.iso88591 sed -n 's/.*bloggkommentar.*count..\([0-9]*\).*/\1/p'`  
            echo "${BLOGG_NUMBER:=0}"
        ;;
        quotes)
            # Extracts the number of forum comments
            FORUM_NUMBER=`cat um.htm | LANG=sv_SE.iso88591 sed -n 's/.*forumkommentar.*count..\([0-9]*\).*/\1/p'`
            echo "${FORUM_NUMBER:=0}"    
        ;;
        comments)
            # Extract the number of image comments
            IMAGE_NUMBER=`cat um.htm | LANG=sv_SE.iso88591 sed -n 's/.*albumkommentar.*count..\([0-9]*\).*/\1/p'`
            echo "${IMAGE_NUMBER:=0}"
        ;;
        guestbook)
            #Extract the number of guestbook posts
            GUESTBOOK_NUMBER=`cat um.htm | LANG=sv_SE.iso88591 sed -n 's/.*g.stbok.*count..\([0-9]*\).*/\1/p'`
            echo "${GUESTBOOK_NUMBER:=0}"
        ;;
        subscribed)
            # Extract the number of unread subscribed threads 
            SUBSCRIBED_NUMBER=`cat um.htm | LANG=sv_SE.iso88591 sed -n 's/.*bevakade.*count..\([0-9]*\).*/\1/p'`
            echo "${SUBSCRIBED_NUMBER:=0}"
        ;;
        *)        
            echo $"Usage: $0 {pm|blog|quotes|comments|guestbook|subscribed}"
            exit 1
    esac        
}

#-------------------------------------------------

LOGIN_DATA="action=login&login_nick=$MY_USERNAME&login_pwd=$MY_PASSWORD"

dirCheck

# Changes working directory to TEMP_DIR
cd $TEMP_DIR

# Downloads the first page you get when you log in
fileDownloader

# Extract the number of unread posts/comments
getNumber $1
```

---

### Post by thomasaaron on 2009-02-18
Well you could re-write it in another language -- maybe Python.

Or, you could try to install a linux shell emulator on Windows. See...

[http://eightpence.com/getting-a-linux-shell-on-windows-cygwin-rxvt/](http://eightpence.com/getting-a-linux-shell-on-windows-cygwin-rxvt/)

You may have to tweak your script a little, but it might be easier than a rewrite.

---

### Post by Nevon on 2009-02-18
> **thomasaaron said:**
> Well you could re-write it in another language -- maybe Python.

Or, you could try to install a linux shell emulator on Windows. See...

[http://eightpence.com/getting-a-linux-shell-on-windows-cygwin-rxvt/](http://eightpence.com/getting-a-linux-shell-on-windows-cygwin-rxvt/)

You may have to tweak your script a little, but it might be easier than a rewrite.

The biggest problem isn't rewriting the script. It's finding a way to display the result graphically on the desktop, in some way. Maybe an Adobe Air application, Vista sidebar-thingy, system tray applet, Samurize. I don't know, as I don't have any real experience programming GUI applications. Also, cygwin is not an option.

---


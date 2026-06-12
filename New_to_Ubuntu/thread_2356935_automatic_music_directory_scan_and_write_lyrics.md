---
title: "automatic music directory scan and write lyrics"
date: 2017-03-28
forum: New to Ubuntu
---

### Post by sn0m on 2017-03-28
Hi guys/girls
I found this fantastic script to automatically write lyrics to a directory. ie execute the script to /path/directory/files.mp3 to write lyrics on.
script:

#!/bin/bash

_TPL='http://makeitpersonal.co/lyrics?artist=<artist>&title=<title>'
_SRY="Sorry, We don't have lyrics for this song yet."

[ "$1" ] && _PATH="$1" || _PATH=$PWD

cd $_PATH

for _FILE in {*.mp3,*.m4a}; do
    if [[ -r $_FILE ]]; then
        _SONG=$(eyeD3 --no-color "$_FILE" | grep title)

        _ARTIST="${_SONG#*"artist: "}"
        _TITLE="${_SONG%"artist: "*}"
        _TITLE="${_TITLE#"title: "}"

        echo -n "$_ARTIST - $_TITLE"

        _ARTIST="${_ARTIST// /+}"
        _TITLE="${_TITLE// /+}"
        _URL="${_TPL//"<artist>"/$_ARTIST}"
        _URL="${_URL//"<title>"/$_TITLE}"

        _LYRICS=$(wget -qO- $_URL)

        if [ "$_LYRICS" != "$_SRY" ]; then
            eyeD3 --lyrics=eng:Lyrics:"$_LYRICS" "$_FILE" 1>/dev/null
        else
            echo "No lyrics found... skipping!"
        fi
    fi
done

cd $OLDPWD

Is there a way to automise it, ie to run this script in a way that it scans my music library, enters to all directories and writes the lyrics on all songs on that directory, than it comes out and scans the next directory, all this within my music directory?
Many thanks for your help
sn0m

---

### Post by Keith_Helms on 2017-03-28
makeitpersonal.co?  I'm not sure I'd trust some website in Colombia.

---

### Post by leunam12 on 2017-03-28
Do you mean Colombia?

---

### Post by milkness on 2017-05-13
Interesting idea, I would love to see the end product, It just needs a piece of code that list all the files recursively to a file, ls command with some options > a txt tile.
It should then create a log file or something where to store completed songs after extracting the meta data from the songs and write the lyrics file, after which it simply moves the first line of the list of all the files to the log and then does the process all over again. Sorry I could not write you some code to do this but it is 1:12 in the morning and I need sleep, just thought I would get the ball rolling.

---


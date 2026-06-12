---
title: "script info to text file"
date: 2022-11-24
forum: New to Ubuntu
---

### Post by phillip1882 on 2022-11-24
i want to run the script info program and automatically save the output to a text file.
what command prompt should i use?

---

### Post by TheFu on 2022-11-24
```
/path/to/script  > /tmp/the-file-I-want
```

Or 

```
/path/to/script  |tee  /tmp/the-file-I-want
```

That will get stdout. If you need stderr, that's a different redirection.  If you want both stdout and stderr, that's a different redirection.

Using 'redirection' is a basic computing skill.  Every Unix-like OS supports it and so does PC/MS/DR-DOS since the olden times.

By asking this question, perhaps you are ready to learn The Art of the  Command LIne?
[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)

Set a calendar reminder to re-read it each year.  Read it today. You'll see a few things that make sense and will be useful, but lots of things won't make sense or seem useful because you aren't ready.  But next year, you'll be ready to use and learn more, which is why re-reading it is strongly suggested.

Plus ... 
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a basic textbook for these things too.

---

### Post by phillip1882 on 2022-11-24
what i'm asking is this: what should i add to the following to have it save to a  text file
```
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/system-info/raw/main/system-info](https://github.com/UbuntuForums/system-info/raw/main/system-info) && \
 chmod +x system-info && \
 ./system-info
```

the whole command.

---

### Post by ajgreeny on 2022-11-24
TheFu has already shown you what to add at the end of your final line.
```
./system-info > /tmp/filename.txt
```
I think you can save the text file to your /home folder if you wish but I've never done so.

---

### Post by TheFu on 2022-11-24
I'm pretty certain that the official Ubuntu Forums system-info script saves the output to a file automatically.  In all that output, but probably at the top or bottom, will be the location and filename created.

---

### Post by #&amp;thj^% on 2022-11-24
> **TheFu said:**
> I'm pretty certain that the official Ubuntu Forums system-info script saves the output to a file automatically.  In all that output, but probably at the top or bottom, will be the location and filename created.

Yes it do..:) It will land in the user home directory, "The result is stored in '/home/me/**_system-info.txt'_**
"

---

### Post by MAFoElffen on 2022-11-24
Yes. The command line I posted on the README.md at the repo is to run it the first time... or to update the script to the latest version... 

That command downloads the script to the folder you executed the command from. Personally, I create a folder in my home directory called "Scripts" and download it from that directory. I add that directory to my  user path '.profile' file. I know that $HOME/bin & $HOME/.local/bin is the usual for user scripts, but I its just a me thing.

Now that you bring that up... I should write a startup option to the script to refresh the version of the script to the latest, capturing the directory it was started from so that a download would overwrite it (replace)... In a future version.

And alternately, if you put this script in the same folder as the 'system-info' script, it will change to  that directory to download/refresh and execute the script. (A short-time fix until I can add that feature...)
```

#!/bash/bin
## MAFoElffen, <mafoelffen@ubuntu.com>, 2022.11.24
# Script Name: RefreshScript
#

SOURCE=${BASH_SOURCE[0]}

while [ -L "$SOURCE" ]
do # resolve $SOURCE until the file is no longer a symlink
    DIR=$( cd -P "$( dirname "$SOURCE" )" > /dev/null 2>&1 && pwd )
    SOURCE=$(readlink "$SOURCE")
    [[ $SOURCE != /* ]] && SOURCE=$DIR/$SOURCE 
done

DIR=$( cd -P "$( dirname "$SOURCE" )" > /dev/null 2>&1 && pwd )

cd $DIR

wget -N -t 5 -T 10 https://github.com/UbuntuForums/syst...in/system-info
chmod +x system-info
./system-info

```

EDIT: The script itself already creates a text report file at  $HOME/system-info.txt and an upload transmission log at $HOME/system-info-link.log

EDIT2: The above code is me thinking out, figuring out what I would do to add that as a feature in the script itself... 

*** Thank you for keeping me thinking about improvements.

---

### Post by mIk3_08 on 2022-11-25
Yes. MAFoElffen is the guru of this system-info script. It will  automatically create a  "system-info.txt" under in your HOME directory.  Regards and cheers.
To be exact address:
```
/home/username/system-info.txt
```

---

### Post by MAFoElffen on 2022-11-25
I added the RefreshScript() new feature to the script as a startup option (-r or --refresh)... New version is now in the DEV Repo to get tested before it gets moved to STABLE.

---

### Post by mIk3_08 on 2022-11-25
> **MAFoElffen said:**
> I added the RefreshScript() new feature to the script as a startup option (-r or --refresh)... New version is now in the DEV Repo to get tested before it gets moved to STABLE. Wow. This is good news. I might test the script soon. Thanks MAFoElffen. Regards and cheers.

---


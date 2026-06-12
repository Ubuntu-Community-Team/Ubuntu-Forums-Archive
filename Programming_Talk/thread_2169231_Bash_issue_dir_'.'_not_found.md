---
title: "Bash issue dir '.' not found"
date: 2013-08-21
forum: Programming Talk
---

### Post by ivan6 on 2013-08-21
Hi,

I new in bash scripting, and having the following problem. When I run script I get the message "dir '.' not found"
[ATTACH=CONFIG]245525[/ATTACH]

But when I enter the same command manually, everything works perfect
[ATTACH=CONFIG]245524[/ATTACH]

```
#!/bin/bashBASEDIR=`dirname "$0"`
source "$BASEDIR/environment.sh"
if [[ $? != 0 ]]; then exit 1; fi


QUERY_VIDEO="$1"
FNAME=`basename "$QUERY_VIDEO"`


QUERY_DATA_DIR="$BIN_DIR/data_$FNAME"
QUERY_SEGMENTATION_CODE="SEGCTE_1/3_SEG"
QUERY_SEGMENTATION_ALIAS="3fps"
QUERY_DESCRIPTOR_CODE="PROM_1U_EHD_4x4_8x8_5_K10_8F"
QUERY_DESCRIPTOR_ALIAS="EHD_3fps"


REFERENCE_DATA_DIR="$BIN_DIR/reference_data"
REFERENCE_DESCRIPTOR_ALIAS="EHD_3fps"


SEARCH_DIR="$BIN_DIR/search_$FNAME"
DISTANCE_FUNCTION="DESC,L1"


#manualy define query video
QUERY_VIDEO="/home/alex/Videos/1_1_Y.flv"


RUN "$BIN_DIR/pvcd_db" -new     -db "$QUERY_DATA_DIR" -fileType video -recursiveDirs -checkVideoFrames "$QUERY_VIDEO"
RUN "$BIN_DIR/pvcd_db" -segment -db "$QUERY_DATA_DIR" -seg "$QUERY_SEGMENTATION_CODE" -alias "$QUERY_SEGMENTATION_ALIAS"
RUN "$BIN_DIR/pvcd_db" -extract -db "$QUERY_DATA_DIR" -seg "$QUERY_SEGMENTATION_ALIAS" -desc "$QUERY_DESCRIPTOR_CODE" -alias "$QUERY_DESCRIPTOR_ALIAS"


RUN "$BIN_DIR/pvcd_search" -new -profile "$SEARCH_DIR" -query "$QUERY_DATA_DIR" -descQ "$QUERY_DESCRIPTOR_ALIAS" -reference "$REFERENCE_DATA_DIR" -descR "$REFERENCE_DESCRIPTOR_ALIAS" -dist "$DISTANCE_FUNCTION"
RUN "$BIN_DIR/pvcd_search" -ss  -profile "$SEARCH_DIR" -knn 3 -searchID SEARCH
RUN "$BIN_DIR/pvcd_localization" "$SEARCH_DIR\ss,SEARCH.txt" -maxDetections 10 -multiDetection -out "$SEARCH_DIR\ss,SEARCH.detections" -outVLC "$SEARCH_DIR\results.sh"
```

---

### Post by Vaphell on 2013-08-21
what is RUN? what happens when you drop it?

---

### Post by ivan6 on 2013-08-21
I didn't entered RUN in terminal, because it is not recognized, anyway, the script is not mine, and when i drop the RUN command in bash script I get just:
> dir '.' not found
[ATTACH=CONFIG]245526[/ATTACH]

---

### Post by dwhitney67 on 2013-08-21
What's defined in environment.sh?

Also, when you ran to script in the terminal (e.g. $ bash Search.sh), it would seem that you neglected to supply a second argument to the bash statement.  Early in the Search.sh script, there's a reference to value of $1, which does not appear to be set.

---

### Post by Vaphell on 2013-08-21
yes, missing param might be it

you don't have to post printscreens, you can copy text from terminal and paste it.
highlight to copy, middleclick to paste or ctrl+shift+c, ctrl+v (terminal needs additional shift because 'standard' shortcuts are taken)

---

### Post by ivan6 on 2013-08-21
No, it's not missing parametar. For testing I have added the line to define variable (path):
```
QUERY_VIDEO="$1"
.
.
.
#manualy define query video
QUERY_VIDEO="/home/alex/Videos/1_1_Y.flv"
```


> **dwhitney67 said:**
> What's defined in environment.sh?

```
#!/bin/bashBASEDIR=`dirname "$0"`


A=`$BASEDIR/pvcd_db`

if [[ $? -ne 0 ]]; then exit 1; fi


export BIN_DIR="$BASEDIR"
export PVCD_NUM_CORES=`cat /proc/cpuinfo | grep '^processor' | wc -l`
export PVCD_NUM_CORES=`cat /proc/cpuinfo | grep '^processor' | wc -l`
export PVCD_PATH_TEMP="$BASEDIR"


function RUN {
        echo
        echo "$@"
        "$@"
        if [[ $? -ne 0 ]]; then exit 1; fi
}
```

---

### Post by dwhitney67 on 2013-08-21
> **ivan6 said:**
> No, it's not missing parametar. For testing I have added the line to define variable (path):
```
QUERY_VIDEO="$1"
.
.
.
#manualy define query video
QUERY_VIDEO="/home/alex/Videos/1_1_Y.flv"
```

The script is executed sequentially.  Thus with $1 undefined, what do you suppose will be the ultimate value for FNAME, if the value of QUERY_VIDEO is not set to nothing?

I'm not saying that this is the root cause of the issue you are experiencing with these scripts, but could be merely symptom that leads to the problem.  As for the scripts, they are not bulletproof.  You should add statements to Search.sh to ensure that the user (you) has entered all of the expected inputs before the script executes any other command.

Similar for 'environment.sh'; you should modify it to check whether pvcd_db is executable, not that you can run it!
```

A="/home/alex/Downloads/pvcd-0.2a/linux/pvcd_db"
if [ ! -x $A ]; then exit 1; fi

```

Lastly, if pvcd_db is deep in the bowels of your Downloads directory, should that not be the same path assigned to BIN_DIR?  As is, BIN_DIR is assigned to the current directory in which you run the scripts (ie. dot, .).

---

### Post by ivan6 on 2013-08-21
Sorry for confusion, paths /home/alex/Downloads/pvcd-0.2a/linux/pvcd_db and ~/Desktop/P-VCD are the same, the second is just link to the previous one. Anyway to avoid that i environment.sh changed to

 ```

A=`$BASEDIR/pvcd_db`if [[ ! -x $A ]]; then exit 1; fi



```

And bingo, it's not passing, so the file pvcd_db is not [COLOR=#000000]executable. So I tried 
[/COLOR]```
sudo chmod a+x ./pvcd_db
```[COLOR=#000000]

And again it's not working. But permission window it is ticked as [/COLOR][COLOR=#000000]executable
[/COLOR][ATTACH=CONFIG]245529[/ATTACH]

I also have 2nd script without "$1" argument, and the situation is the same **dir '.' not found**

```

#!/bin/bash
#BASEDIR=`dirname "$0"`
source "./environment.sh"
if [[ $? != 0 ]]; then exit 1; fi


REFERENCE_VIDEOS="$HOME"
REFERENCE_DATA_DIR="$HOME/reference_data"
REFERENCE_SEGMENTATION_CODE="SEGCTE_1/3_SEG"
REFERENCE_SEGMENTATION_ALIAS="3fps"
REFERENCE_DESCRIPTOR_CODE="PROM_1U_EHD_4x4_8x8_5_K10_8F"
REFERENCE_DESCRIPTOR_ALIAS="EHD_3fps"


RUN "$BIN_DIR/pvcd_db" -new     -db "$REFERENCE_DATA_DIR" -fileType video -recursiveDirs -checkVideoFrames "$REFERENCE_VIDEOS"
RUN "$BIN_DIR/pvcd_db" -segment -db "$REFERENCE_DATA_DIR" -seg "$REFERENCE_SEGMENTATION_CODE" -alias "$REFERENCE_SEGMENTATION_ALIAS"
RUN "$BIN_DIR/pvcd_db" -extract -db "$REFERENCE_DATA_DIR" -seg "$REFERENCE_SEGMENTATION_ALIAS" -desc "$REFERENCE_DESCRIPTOR_CODE" -alias "$REFERENCE_DESCRIPTOR_ALIAS"
```

ps. I've tried to run scripts with as the root (sudo...)

---

### Post by dwhitney67 on 2013-08-21
You do not want to execute pvcd_db here:
```

A=`$BASEDIR/pvcd_db`

```
Those back ticks are used for executing a program; some people (myself included) prefer to use $() in lieu of the back ticks.  Regardless, you don't want to execute the command; just let the if-statement check if the file exists and is executable; the -x option will cover that.

So please, copy/paste exactly what you see below into the environment.sh script (and remove what you currently have, which looks similar, but is not the same):
```

A="/home/alex/Downloads/pvcd-0.2a/linux/pvcd_db"
if [ ! -x $A ]; then exit 1; fi

# alternatively

if [ ! -x "/home/alex/Downloads/pvcd-0.2a/linux/pvcd_db" ]; then exit 1; fi

```

---

### Post by ivan6 on 2013-08-21
Thank you. I've replaced the suggested lines, but that was not the real problem, anyway, I've played a little bit and managed to find out that in [COLOR=#000000]environment.sh line[/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Mono]export PVCD_PATH_TEMP="$BASEDIR"[/FONT][/COLOR]
``` is the problem and I replaced with
```
export PVCD_PATH_TEMP="./"
```
And everyrhing works fine.

---

